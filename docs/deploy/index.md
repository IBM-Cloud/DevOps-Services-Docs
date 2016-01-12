#Build and deploy

###### Last updated: 12 January 2016


The IBM&reg; Bluemix&reg; DevOps Services Build &amp; Deploy feature, also known as the pipeline, automates the continuous deployment of your projects. In a project's pipeline, sequences of stages retrieve input and run jobs, such as builds, tests, and deployments.

* [Stages](#stages)
* [Jobs](#jobs)
* [Manifest files](#manifests)
* [An example pipeline](#example)
* [Adding a stage](#add_stage)
* [Adding a job to a stage](#add_job)
* [Running a stage](#run_stage)
* [Deploying an app](#deploy)
* [Viewing logs](#logs)
* [Controlling access](#access)
* [Environment properties and resources](#env)
* [Extending the capabilities of your pipeline](#ext)

<a name="stages"></a>
##Stages

Stages organize input and jobs as your code is built, deployed, and tested. Stages accept input from either source control repositories or build jobs in other stages. When you create your first stage, the default settings are set for you on the **INPUT** tab.

A stage's input is passed to the jobs it contains, and each job is given a clean container to run in. The jobs in a stage can't pass artifacts to each other. However, you can define stage environment properties that can be used in all jobs. For example, you could define a `TEST_URL` property that passes a single URL to deploy and test jobs in a single stage. The deploy job would deploy to that URL, and the test job would test the running app at the URL. 

To learn how to add a stage, [see Adding a stage][19].

By default in a stage, builds and deployments are triggered automatically every time changes are delivered to a project's source control repository. Stages and jobs run serially; they enable flow control for your work. For example, you might place a test stage before a deployment stage. If the tests in the test stage fail, the deployment stage won't run. 

You might want tighter control of a specific stage. If you do not want a stage to run every time a change occurs at its input, you can disable the capability. On the **INPUT** tab, in the Stage Trigger section, click **Run jobs only when this stage is run manually**. 



![The INPUT tab][8]

<a name="jobs"></a>
##Jobs
A job is an execution unit within a stage. A stage can contain multiple jobs, and the jobs in a stage run sequentially. By default, if a job fails, subsequent jobs in the stage do not run.

![Build and test jobs within a stage][15]

Jobs run in discrete working directories that are created by the pipeline. Before a job is run, its working directory is populated with input that is defined at the stage level. For example, you might have a stage that contains a test job and a deploy job. If you install dependencies on one job, the dependencies are not available to the other job. However, if you make the dependencies available in the stage's input, they are available to both jobs.

**Note**: Jobs can run for up to 60 minutes. When jobs exceed that limit, they fail. If a job is exceeding the limit, break it into multiple jobs. For example, if a job performs three tasks, you might break it into three jobs: one for each task.

To learn how to add a job to a stage, [see Adding a job to a stage][20].

<a name="builds"></a>
###Build jobs

Build jobs compile your project in preparation for deployment. They generate artifacts that can be sent to a build archive directory, although by default, the artifacts are placed in the project's root directory.

Jobs that take input from build jobs must reference build artifacts in the same structure that they were created in. For example, if a build job archives build artifacts to an `output` directory, a deploy script would refer to the `output` directory rather than the project root directory to deploy the compiled project.

**Note**: If you select the **Simple** builder type for a build job, you skip the build process. In that case, your code is not compiled, but is sent to the deployment stage as is. To both build and deploy, select a builder type other than **Simple**. 

<a name="builds_var"></a>
####Environment properties for build scripts
You can include environment properties within a build job's build shell commands. The properties provide access to information about the job's execution environment. For more information, [see Environment properties and resources for the Build &amp; Deploy pipeline][25].

<a name="deploys"></a>
###Deploy jobs

Deploy jobs upload your project to Bluemix as an app and are accessible from a URL. After a project is deployed, you can find the deployed app on your Bluemix Dashboard. You can configure the build and deploy jobs as separate stages or add them to the same stage to run automatically.

Deploy jobs can deploy new apps or update existing apps. Even if you first deployed an app by using another method, such as the Cloud Foundry command line interface or the run bar in the Web IDE, you can update the app by using a deploy job. To update an app, in the deploy job, use that app's name.

<a name="deploys_var"></a>
####Environment properties for deployment scripts

You can include environment properties within a deploy job's deployment script. These properties provide access to information about the job's execution environment. For more information, [see Environment properties and resources for the Build &amp; Deploy pipeline][25].

<a name="tests"></a>
###Test jobs
If you want to require that certain conditions are met, include test jobs before or after your build and deploy jobs. Test jobs are highly customizable. For example, you might run tests on your project code and a deployed instance of your app. 

<a name="manifests"></a>
##Manifest files
Manifest files, which are named `manifest.yml` and stored in a project's root directory, control how your project is deployed to Bluemix. For information about creating manifest files for a project, [see the Bluemix documentation about application manifests][1]. To integrate with Bluemix, your project must have a manifest file in its root directory. However, you are not required to deploy based on the information in the file. 

In the pipeline, you can specify everything that a manifest file can by using `cf push` command arguments. The `cf push` command arguments are helpful in projects that have multiple deployment targets. If multiple deploy jobs all try to use the route that is specified in the project manifest file, a conflict occurs. 

To avoid conflicts, you can specify a route by using `cf push` followed by the host name argument, `-n`, and a route name. By modifying the deployment script for individual stages, you can avoid route conflicts when you deploy to multiple targets.

To use the `cf push` command arguments, open the configuration settings for a deploy job and modify the **Deploy Script** field. For more information, [see the Cloud Foundry Push documentation][3]. 

<a name="example"></a>
##An example pipeline

The simplest possible pipeline contains two stages. First, there is a stage that contains a build job and takes input from a Git repository. When that build job runs, the app is built and sent to a build archive directory. If the first stage runs, a second stage that contains a deploy job runs. The second stage takes input from the earlier build job and deploys the app to Bluemix.

![A two-stage pipeline][12]

<a name="add_stage"></a>
##Adding a stage

1. On the Build & Deploy Pipeline page, click **ADD STAGE**. The Stage Configuration page opens. 
2. Configure the stage.
  1. On the **INPUT** tab, select an input for the stage.
  2. On the **JOBS** tab, add and configure at least one job. The first stage usually has at least a build job.
3. Click **SAVE**.

![Adding a stage to a pipeline][13]

<a name="add_job"></a>
##Adding a job to a stage

1. On the stage, click the **Stage Configuration** icon, and then click **Configure Stage**. 
2. Click the **JOBS** tab.
3. Click **ADD JOB**. Select the type of job to add. 
4. Configure the job.
5. Click **SAVE**.

![Adding a job to a stage][14]

<a name="run_stage"></a>
##Running a stage

You can manually run a stage by clicking the **Run Stage** icon on the Build &amp; Deploy Pipeline page. 

![Clicking the Run Stage icon on a stage][16]

You can also request on-demand builds and deployments from the build history page in one of two ways:
* Drag a build to the box that is under a configured stage.
* Next to a build, click the **Execute stage with this build** icon and then select a space to deploy to.
  ![The Execute stage with this build icon][9]

To cancel a running stage, on the stage, click **View logs and history**. In the list on the left, click the running job's number and then click **CANCEL**. You can also cancel jobs individually by clicking a job and then clicking **CANCEL**, or by clicking the **Stop** icon next to a job on its stage.
  
<a name="deploy"></a>
##Deploying an app

A properly configured deploy job deploys your app to your target whenever the job is run. To manually run a deploy job, click the **Run Stage** icon of the stage that the job is in.

###Input revisions
When you run a stage manually, or if it runs because the stage before it is completed, the running stage selects its input revision. Usually, the input revision is a build number. To select the input revision, the stage follows this process:

1. If a specific revision is selected, use it.
2. If a specific revision is not specified, search previous stages until a stage is found that uses the same input. Find and use the last successfully run revision of that input.
3. If a specific revision is not specified and no other stages use the specified source as input, use the latest revision of the input.

**Tip:** You can deploy a previous build. On the stage that contains the build, click **View logs and history**. On the page that opens, select the build. Click **SEND TO**, and select a target.

###Adding services to apps
You can add services to your apps and manage those services from your Bluemix Dashboard or the Cloud Foundry command line interface (CLI). You can also issue Cloud Foundry CLI commands in scripts for DevOps Services pipeline jobs. For example, you can add a service to an app in the script of a deploy job. For more information about adding services, see [see Adding a service to your application][24].

<a name="logs"></a>
##Viewing logs

You can view the logs for jobs and view stages as they are running on the Stage History page. 

To view a job's log, click the job. Alternatively, on a stage, click **View logs and history**.

To view the runtime log, click **View runtime log**.

![Areas in a stage tile that can be clicked to open relevant logs][10]

In addition to job logs, you can view unit test results, generated artifacts, and code changes for any build job.

You can also run, cancel, or configure a stage from the Stage History page. At the top of the page, click **RUN** to run a stage or **CONFIGURE** to configure a stage. While a stage is running, you can cancel it by clicking the run number and then clicking CANCEL.

![Clicking a stage run number to select it on the Stage History page][26]

<a name="access"></a>
##Controlling access

You can restrict who is able to run stages or modify a pipeline. To do so, go to the Pipeline Settings page, which you can reach by clicking the **Stage Configuration** icon on the Pipeline: All Stages page. 
![The pipeline settings gear icon][22]

<a name="env"></a>
##Environment properties and resources

You can use environment properties and pre-installed resources to interact with the Build &amp; Deploy pipeline. For example, you might incorporate them into a job script or test command. For more information, [see Environment properties and resources for the Build &amp; Deploy pipeline][25].

<a name="ext"></a>
##Extending the capabilities of your pipeline
You can extend the capabilities of your Build & Deploy pipeline by configuring your jobs to use supported services. For example, test jobs can run static code scans and build jobs can globalize strings.

For more information on extending pipeline capabilities, [see Extending the capabilities of your Build & Deploy pipeline][21].
 
[1]: https://www.ng.bluemix.net/docs/manageapps/deployingapps.html#appmanifest
[2]: https://www.ng.bluemix.net/docs/#services/DeliveryPipeline/index.html#getstartwithCD
[3]: http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html#push
[4]: https://console.ng.bluemix.net/?ace_base=true/#/pricing/cloudOEPaneId=pricing
[5]: ./images/open_logs.png
[6]: #manifests
[7]: ./images/runbar-annotated-dark.png
[8]: ./images/input_tab_only_execute.png
[9]: ./images/deploy_to.png
[10]: ./images/view_logs_and_history.png
[11]: ./images/play_button.png
[12]: ./images/basicAnimate.gif
[13]: ./images/AddStage.png
[14]: ./images/AddJob.png
[15]: ./images/jobs.png
[16]: ./images/RunStage.png
[17]: https://www.ng.bluemix.net/docs/starters/container_pipeline.html#container_pipeline
[18]: ../../../tutorials/basicbuild
[19]: #add_stage
[20]: #add_job
[21]: ../deploy_ext
[22]: ./images/pipeline_settings_icon.png
[23]: ./images/pipeline_settings.png
[24]: https://www.ng.bluemix.net/docs/services/reqnsi.html#add_service
[25]: ../deploy_var
[26]: ./images/click_stage_run_number.png
