#Build & Deploy reference

Last modified: 23 April 2015

The Bluemix DevOps Services Build & Deploy feature, also known as Pipeline, automates the continuous deployment of your projects. In a project's Pipeline, sequences of stages retrieve input and run jobs, such as builds, tests, and deployments.

---
##Contents
* [Bluemix and the Delivery Pipeline service](#service)
* [Deployment using the Bluemix DevOps Services Pipeline](#auto)
  * [Stages](#key)
    * [Stage triggers](#pipeline_automatic)
    * [Multistage deployments](#multi)
    * [Environment properties](#env_props)
  * [Jobs](#jobs)
    * [Build jobs](#builds)
    * [Deploy jobs](#deploys)
    * [Test jobs](#tests)
  * [Simple configuration exxample](#example)
  * [Logging](#logs)
* [Deployment using the Web IDE](#manual)
  * [The run bar](#runbar)
* [Manifest files](#manifests)

---

<a name="service"></a>
##Bluemix and the Delivery Pipeline service

The Build & Deploy feature uses the IBM Delivery Pipeline for Bluemix (the Delivery Pipeline service). To make the most of Pipeline's integration with Bluemix, add the service to your targeted Bluemix spaces. For more information about the service, [see Getting started with IBM Continuous Delivery Pipeline for Bluemix][2]. For information about possible charges to your account, [see the Bluemix Pricing page][4].

---

<a name="auto"></a>
##Deployment using the Bluemix DevOps Services Pipeline


<a name="key"></a>

###Stages
Stages organize input and output as your code is built, deployed, and tested. When you create your first stage, typically, the default settings are set for you in the Input page. 

One decision you must make for the stage is whether you want the stage to be triggered automatically or manually.

<a name="pipeline_automatic"></a>
####Stage triggers
By default in a stage, builds and deployments are triggered automatically every time changes are delivered to a project's source control repository. 

However, you might want tighter control of a specific build or deployment stage. If you do not want builds to occur every time a change is pushed to the repository, you can disable the capability. On the **Input** tab, in the **Stage Trigger** section, click **Only execute jobs when a user manually runs this stage**. 

Then, you can request on-demand builds and deployments from the build history page in one of two ways:
* Drag a build to the box that is under a configured space.
* Next to a build, click the **Deploy to** icon and then select a space to deploy to.

<a name="multi"></a>
####Multistage deployments

You might create a multistage deployment when you want to the same project to multiple Bluemix spaces. For example, you might configure three stages: 
* Stage 1: Deploy to a development space
* Stage 2: Deploy to a staging space
* Stage 3: Deploy to a production space

By default, every time a a stage completes in Pipeline, the next stage begins automatically. In later stages, automatic deployment happens only when all of the preceding stages succeed. 

**Important**: If your deployment stages all try to use the route that is specified in your project manifest file, a route collision occurs. For more information about preventing route collisions when you deploy to multiple stages, [see the Manifest files section][6].

<a name="env_props"></a>
####Environment properties

Environment properties are variables whose values can be accessed by any job in a stage. These properties are useful when run scripts within stages. For example, you might have a test script that refers to a `URL` variable. You can reuse that script across many stages that run jobs to test a particular web app deployment. For each stage, only the `URL` variable would need to be created; the script itself would just refer to its stage's `URL` environment property. 

You can create environment properties for a stage when you are configuring the stage. Enter the properties individually on the **Environment Properties** tab. You can also provide a stage with a properties file by entering the path relative to the stage input. 

<a name="jobs"></a>
###Jobs
A job is an execution unit that is within a stage. A stage can contain multiple jobs, and the jobs in a stage run sequentially. All of the jobs in a stage must be completed successfully in order for the stage to be completed successfully. If a job fails, subsequent jobs in the stage do not run.

<a name="builds"></a>
####Build jobs

Builds jobs compile your project in preparation for deployment. 

**Note**: If you select the **Simple** builder type for a build job, you skip the build process. Your code will not be compiled, but will be sent to the deploy stage as is. To both build and deploy, select a builder type other than **Simple**. 

<a name="deploys"></a>
####Deploy jobs
Deploy jobs upload your project to Bluemix as an app and are accessible from a URL. After a project is deployed, you can locate the deployed app on your Bluemix dashboard. You can configure the build and deploy jobs as separate stages or add them to the same stage to run automatically.

<a name="tests"></a>
####Test jobs
You can require that certain conditions are met by including test jobs before or after build and deployment jobs.

<a name="example"></a>
###Simple configuration example
A simple Delivery Pipeline configuration might contain a Build stage that takes input from a Git repository.  By running build and test jobs, the Build stage builds a project and runs unit tests against it. If the build and test jobs both run successfully, the compiled project is output to a Deploy stage that contains a job that pushes the app to Bluemix.




<a name="logs"></a>
###Logging

You can view the logs for your Build & Deploy jobs on the Stage Job History page. Click a job, or click **View logs and history**.

In addition to logs, you can view unit test results, generated artifacts, and code changes for any build job.




---
<a name="manual"></a>
##Deployment using the Web IDE

While you're working in the directory that contains your `manifest.yml` file, you can deploy whatever is in the Web IDE workspace to Bluemix by clicking the **Play** icon on the run bar.  The Web IDE deploys whatever is in your working directory when you push.

**Remember:** By clicking the **Play** icon, you deploy the current state of your code in the Web IDE workspace. To deploy the code that is checked in to the repository, use Pipeline.

You can configure Web IDE deployment and Build & Deploy's Pipeline to use different app names. Then, you can use the Web IDE deployment for a personal test environment and Pipeline for a team integration environment. The Web IDE saves deployment launch configurations; you can access them from the menu on the run bar. 

Whether you are using command-line tools or the Web IDE, both methods are effective for rapid, solo development. 


<a name="runbar"></a>
###The run bar

![Annotated Run Bar screenshot][7]

1. **Status area:** Shows which launch configuration is selected and the deployment status of your app. If your project doesn't contain a launch configuration, create one by clicking the menu and then clicking **CREATE NEW**.
2. **Play icon:** Deploys your app manually by using the currently selected launch configuration.
3. **Stop icon:** Stops a running app. 
4. **Open URL icon:** Opens a running app. 

---

<a name="manifests"></a>
###Manifest files

Manifest files, which are named `manifest.yml` in a project's root directory, control how your project is deployed to Bluemix. For information about creating manifest files for a project, [see the Bluemix documentation about application manifests][1]. To integrate with Bluemix, your project must have a manifest file in its root directory. However, you are not required to deploy based on the information in the file. 

In the Pipeline, you can specify everything in a manifest file by using `cf push` command arguments. To learn about the arguments, [see the Cloud Foundry Push documentation][3]. To use the arguments, modify the **Script** field in a deployer job's configuration menu.

One case where the `cf push` command arguments are helpful is in a project that has multiple deployment targets. If multiple deploy jobs try to use the same route, as specified in the project manifest, a conflict occurs. 

To avoid conflicts, you can use `cf push` followed by the host name argument `-n` and a route name to specify a route. By modifying the deployment script for individual stages, you can avoid conflicts without using the manifest file.

 
[1]: https://www.ng.bluemix.net/docs/#manageapps/index-gentopic2.html#appmanifest
[2]: https://www.ng.bluemix.net/docs/#services/DeliveryPipeline/index.html#getstartwithCD
[3]: http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html#push
[4]: https://console.ng.bluemix.net/?ace_base=true/#/pricing/cloudOEPaneId=pricing
[5]: ./images/open_logs.png
[6]: #manifests
[7]: ./images/runbar-annotated.png
