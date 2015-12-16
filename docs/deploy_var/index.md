#Delivery pipeline environment variables and resources

###### Last updated: 16 December 2015

You can use any of the following environment variables and pre-installed resources to interact with the delivery pipeline environment. For example, you might use them in a job script or test command. 

##Contents
* Environment variables
    * General purpose variables
    * Runtime and tool variables
    * Deployment variables
* Pre-installed resources
    * Runtimes and tools
    * Node modules

## Environment variables

###General purpose variables

| Environment variable | Description |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| ARCHIVE_DIR | The directory that will be archived or that archives are downloaded into. |
| BUILD_ID | The unique ID for the current job execution.  |
| BUILD_DISPLAY_NAME | The BUILD_ID value prefixed with "#". |
| BUILD_NUMBER | The incremental stage ID that appears in the pipeline UI.  |
| GIT_BRANCH | The Git branch used as input by the job. Only available in jobs that use a Git repository as input. |
| GIT_COMMIT | The Git commit used as input by the job. Only available in jobs that use a Git repository as input. |
| GIT_PREVIOUS_COMMIT | The Git commit value of the last successful execution of the job. Only available in jobs that use a Git repository as input. |
| GIT_URL | The Git repository URL used as input by the job. Only available in jobs that use a Git repository as input. |
| IDS_JOB_ID | The unique ID of the job's configuration. |
| IDS_JOB_NAME | The name of the job's configuration. |
| IDS_OUTPUT_PROPS | Comma-separated names of your stage environment properties. |
| IDS_PROJECT_NAME | The name of the project, e.g. <code>Owner &#124; Project Name</code>. |
| IDS_STAGE_NAME | The name of the current stage. |
| IDS_URL | The URL for the current pipeline. |
| JOB_NAME | The unique job ID in the context of the current pipeline. |
| PIPELINE_STAGE_INPUT_JOB_ID | The ID of the job that is input for the current stage. |
| PIPELINE_STAGE_INPUT_REV | The revision of the input for the current stage. |
| PIPELINE_INITIAL_STAGE_EXECUTION_ID | The unique ID for the run of the pipeline. |
| TASK_ID | The unique ID of the current job execution. |
| TMPDIR | A directory location where temporary files are stored. |
| WORKSPACE | The path for the current working directory. |

###Runtime and tool variables

| Environment variable | Description |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| ANT_HOME | The path to Apache Ant 1.9.2. |
| GRADLE_HOME | The path to Gradle 1.11. |
| JAVA_HOME | The path to IBM Java 7. |
| JAVA7_HOME | The path to IBM Java 7. |
| JAVA8_HOME | The path to IBM Java 8. |
| MAVEN_HOME | The path to Apache Maven 3.2.1. |
| NODE_HOME | The path to Node.js 0.10.29. |

###Deployment variables

| Environment variable | Description |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| CF_APP | For deployments, the name of the application to deploy. |
| CF_ORG | For deployments, the name of the organization to deploy to. |
| CF_ORGANIZATION_ID | For deployments, the ID of the organization to deploy to. |
| CF_SPACE | For deployments, the name of the space to deploy to. |
| CF_SPACE_ID | For deployments, the ID of the space to deploy to.  |
| CF_TARGET_URL | For deployments, the URL of Bluemix/Cloud Foundry. |
| IDS_VERSION | For deployments, the version of the app that is being deployed or the source identifier. |

##Pre-installed resources

Several runtimes, tools, and Node modules are pre-installed in every pipeline. 

###Runtimes and tools

*Note:* All links are in the home directory. 

| Resource | Link name | Path |
|----------|-----------|-----------|
|Apache Ant 1.9.2|ant |/opt/IBM/ant |
|Cloud Foundry CLI 6.7 |cf | /opt/IBM/cf |
|Gradle 1.12|gradle |/opt/IBM/gradle |
|Gradle 2.9 |gradle2 |/opt/IBM/gradle2 |
|IBM Java (default)|java |/opt/IBM/java |
|IBM Java 7 x86_64-71 |java7 |/opt/IBM/java7 |
|IBM Java 8 x86_64-80|java8 |/opt/IBM/java8 |
|Apache Maven 3.2.1 |maven |/opt/IBM/maven |
|IBM Node |node |/opt/IBM/node |
|RTM SCM Tools |RTM-SCM-Tools |/opt/IBM/RTC-SCM-Tools |

*Note:* 64-bit versions of IBM Node 0.10.40, 0.12.7, and 4.2.2 are available by default in the pipeline environment. 

###Node modules

The following Node modules are globally installed in the pipeline environment:

* grunt@0.4.5
* grunt-cli@0.1.13
* grunt-contrib-concat@0.4.0
* grunt-contrib-jshint@0.10.0
* grunt-contrib-nodeunit@0.4.1
* grunt-contrib-qunit@0.5.1
* grunt-contrib-uglify@0.5.0
* grunt-contrib-watch@0.6.1
* karma@0.12.23
* karma-cli@0.0.4
* karma-jasmine@0.1.5
* karma-phantomjs-launcher@0.1.4
* phantomjs@1.9.10


<!--<a href="#" target="_blank">Back to the Build & Deploy reference page</a>-->