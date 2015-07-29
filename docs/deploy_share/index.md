#Sharing text-defined pipelines in sample projects

Last modified: 29 July 2015

For sample projects that are deployed to Bluemix through the Deploy to Bluemix button, you can define pipeline configurations as YAML files. Pipelines that are defined as text can be shared so that the people who fork your project don't have to configure their own pipelines. To learn more about the Deploy to Bluemix button, [see Creating a Deploy to Bluemix button][1].

This feature is under development: the YAML format and implementation might change at any time. Currently, this feature is available only for projects with Git and GitHub repositories that target Bluemix.

---
##Contents
* [Prerequisites](#prerequisites)
* [YAML file format](#yaml)
* [API for interacting with pipelines by using a YAML file](#api)

---

<a name="prerequisites"></a>
##Prerequisites
In the sample project's root directory, you must have a folder named `.bluemix` that contains a `pipeline.yml` file.

When a project is cloned by using the **Deploy to Bluemix** button, IBM&reg; Bluemix&trade; DevOps Services creates a pipeline that is based on the `pipeline.yml` file.

```
<sample root>
    .bluemix
        pipeline.yml
    <other sample content>
```

<a name="yaml"></a>
##YAML file format

The YAML file format is a single YAML document that contains a pipeline specification. 

The following sample pipeline builds a Java app with Ant in one stage. Then, in another stage, the pipeline deploys the app to Bluemix.

```
---
stages:
- name: Build Stage
  inputs:
  - type: git
    branch: master
  triggers:
  - type: commit
  properties:
  - name: APP_VERSION
    value: '1.0'
    type: text
  jobs:
  - name: Build
    type: builder
    artifact_dir: output
    build_type: ant
    script: |-
      #!/bin/bash
      ant
    enable_tests: true
    test_file_pattern: tests/TEST-*.xml
- name: Deploy Stage
  inputs:
  - type: job
    stage: Build Stage
    job: Build
  triggers:
  - type: stage
  jobs:
  - name: Deploy to dev
    type: deployer
    target:
      url: https://api.ng.bluemix.net
      organization: uateam@ca.ibm.com
      space: dev
      application: JavaSampleUnitTest
    script: |
      cf push "${CF_APP}"
      # View logs
      #cf logs "${CF_APP}" --recent
```

###YAML file syntax

####Pipeline
``` 
---
stages:
<sequence of stages>
```

####Stage
```
name: <name>
[inputs:
  <sequence of inputs>]
[triggers:
  <sequence of triggers>]
[properties:
  <sequence of properties>]]
[jobs:
  <sequence of jobs>]
```

####Input
```
type: 'git' | 'job'
[branch: <branch name>]   ; only for Git inputs
stage: <stage name>       ; only for job inputs
job: <job name>           ; only for job inputs
```

####Trigger
``` 
type: 'commit' | 'stage'
[enabled: 'true' | 'false']   ; true is assumed if not specified
``` 

####Property
```
name: <property name>
value: <property value>
[type: 'text' | 'secure' | 'text_area' | 'file']  ; text is assumed if not specified
```

####Job
```
[name: <job name>]
type: 'builder' | 'deployer' | 'tester'
fail_stage: 'true' | 'false'
[extension_id: <extension id>]          ; extension jobs only
[working_dir: <working dir path>]       ; builder and tester only
[artifact_dir: <artifact path>]         ; builder only
[build_type: <build type>]              ; builder only
[script: <script>]                      ; not for extension jobs
[enable_tests: 'true' | 'false']        ; builder and tester only
[test_file_pattern: <pattern>]          ; builder and tester only
[target: <target>]                      ; deployer and extension jobs only
*[<extension property name> : <value>]  ; extension jobs only
```

####Target
```
url: <target url>
organization: <org name>
space: <space name>
[application: <app name>]
```

###Extension jobs and extension definitions

Extension definitions define the set of properties that are available to extension jobs. A job is treated as an extension job when the `extension_id` property is specified. To find out which properties are available for an extension, consult its documentation.

###Environment variables
The YAML file can contain environment variables from a predefined set. These variables are supported:

| Variable           | Description |
|--------------------|--------------------|
| CF_TARGET_URL      | Bluemix target URL |
| CF_ORGANIZATION    | Org name  |
| CF_ORGANIZATION_ID | Org GUID  |
| CF_SPACE           | Space name         |
| CF_SPACE_ID        | Space GUID         |
| CF_APP             | App name   |

<a name="api"></a>
##API for interacting with pipelines by using a YAML file

###Creating a pipeline by using a YAML file

To create a pipeline by using a YAML file, use this API:
```
POST /pipeline/pipelines
{
  "project_id": "<project id>",
  "env": {
     "<variable 1 name>" : "<value 1>"
     "<variable 2 name>" : "<value 2>"
},
  "config": {
    "format" : "yaml",
    "content" : "<yaml>"
  }
}
```

If the pipeline is created, the response code is 201 and the body is the pipeline resource in JSON. Any other response code indicates a failure. 

Note: To be a valid JSON string value, the YAML content must be escaped.

####Environment variables and resolution

Before the pipeline is created, the environment variables that are passed in the `env` property are resolved and the substituted values are used in the configuration. YAML values are substituted only if they solely consist of an environment variable. For example:
```
{
  "project_id": "_ljkahfliasdlk",
  "env": {
     "CF_ORGANIZATION" : "user@se.ibm.com"
  },
  "config": {
    "format" : "yaml",
    "content" : "
      ...
        target:
          url: http://api.ng.bluemix.net
          organization: ${CF_ORGANIZATION}
        script: \"echo ${CF_ORGANIZATION}\"                
      ...
    "
  }
}
```
In that example, the target org is resolved against the target URL, and the value that persists in the pipeline configuration is the org GUID. The occurrence inside of the deployment script is not substituted.

The target URL must be specified as an environment variable or a real value, and either the GUIDs or the names of the org and space must be provided.If one value is provided, the other is also substituted. For example, if a YAML file contains both `CF_SPACE` and `CF_SPACE_ID`, the API call has to pass only one of them as an environment variable.

Currently in the Deploy to Bluemix flow, this set of variables is passed: `CF_TARGET_URL`, `CF_ORGANIZATION_ID`, `CF_SPACE_ID`. `CF_APP` is not substituted; use it only in scripts or in extension properties that are used only in scripts.

###Generating a YAML file from a pipeline

You can generate a YAML file from a pipeline. The API is as follows:

```
GET /pipeline/pipelines/<pipeline id>
Accept: application/x-yaml
```
The response on success is 200, and the response body is the YAML file in UTF-8-encoded text form. Any other status code indicates an error. Errors can happen and are typically caused by external problems, such as connectivity issues.

This API is also exposed through the UI through the following URL:
```
GET <jazzhub url>/pipeline/user/project/yaml
```

This call does not require an accept header. You can use this call from a browser.

*Note:* For safety reasons, secure-stage environment property values are omitted from generated pipeline YAML files.

[1]: https://www.ng.bluemix.net/docs/manageapps/deployingapps.html#deploy_button

