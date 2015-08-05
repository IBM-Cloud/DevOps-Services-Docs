#Extending Build and Deploy pipeline capabilities

###### Last updated: 3 August 2015

**Note:** These topics are specific to containers and do not include instructions for general use of the Delivery Pipeline. To see the full Delivery Pipeline documentation, [see the Build & Deploy How To topic][1].

* [Running static code scans by using the Delivery Pipeline](#scan)
* [Globalizing strings by using the Delivery Pipeline](#globalize)

<a name="scan"></a>
##Running static code scans by using the Delivery Pipeline

Find security issues in your code before the app is deployed. Run an automated check against your Java™ app's static `.war`, `.ear`, `.jar`, or `.class` built binary files by using the IBM® Static Analyzer for Bluemix™ service as part of your pipeline.

Before you begin, [review the Terms of Use for the service][4].

A common pipeline setup that includes this scan:
* Build stage to build the source files
* Processing stage, which includes the following jobs:
  * A build job to run the Static Analyzer
  * A build job to run a container build
* Deploy stage to deploy the container

<iframe width="640" height="360" src="https://www.youtube.com/embed/38DgKxT189s?feature=player_embedded" frameborder="0" allowfullscreen></iframe>

To create the static code scan:

1. Create a rpcoessing stage.
  a. Click **ADD STAGE**.
  b. Name the stage. Example: `Processing`
  c. For the **Input type**, select **Build Artifacts**.
  d. For the stage and job, verify the values and update, if necessary.
2. In the processing stage, add a build job to run the code scan.
  a. In the **JOBS** tab, click **ADD JOB**.
  b. Select the **Test** job type.
  c. For the **Tester type**, select **IBM Security Static Analyzer**.
  d. For the organization and space, verify the values and update, if necessary.
  e. For **Set up service and space for me**, select or clear the checkbox.
    * When this field is selected, the pipeline checks your Bluemix space for the service and an application that binds the service to the container. If the service or bound application do not exist, the pipeline adds the free plan of the service to your space for you. The bound application that is created is named `pipeline_bridge_app`. Then, the pipeline uses the credentials from `pipeline_bridge_app` to access the bound services.
    * Leave this field cleared if you either configured the service and bound application in your Bluemix space already or [you want to configure these requirements yourself][5].
  f. For **Minutes to wait for analysis to complete**, enter a value 0 - 59 minutes. The default value is 5 minutes. A URL to the Static Analyzer dashboard is provided in the console logs at the end of the job. 
If the Static Analyzer scan is not complete before this time ends, the job fails, but the scan analysis continues to run and can be viewed on the Static Analyzer dashboard. After the Static Analyzer scan is complete, if you rerun the job, the scan request is not resubmitted and the pipeline job can complete successfully. Alternatively, you can configure the pipeline not to be blocked on a successful scan result, which is described in the next step.
  g. To determine the behavior on timeout, select or clear **Stop stage execution on job failure**.
You can configure the job to block both later jobs in the stage and later stages from running if this job fails, or you can configure the stage to continue without blocking later jobs and stages. The state of the job is determined by the existence of high vulnerabilities.
High vulnerabilities cause the job to fail. Depending on the selection for **Stop stage execution on job failure**, a failed job either stops the stage and pipeline from progressing or allows them to continue. If you know that the report includes many issues to process, you might configure the stage to continue because the scan can take a long time. In this scenario, you might not want the rest of your jobs and stages to stop only because the scan is taking too long.
  h. Click **SAVE**.

When the job finishes, you can click **View logs and history** to review the job results.

If the analysis succeeds or times out, a URL is displayed in the **View logs and history** results of the scan. From that page, if the scan status is pending, you can wait for the full results after the scan is complete.

The Processing stage can be run again before the analysis finished. A new analysis is not resubmitted and previous results are used in the following situation:
* The Processing stage is still running and when a new one is started
* A scan was submitted already for the build
* A new source build has not run yet

To start a new analysis, you can choose one of the following options:
* Run the Build stage that inputs into the Processing stage, and then run the Processing stage again.
* Open the URL for the results of the scan and click the Trash icon. Then, run the Processing stage again.

Console output examples:

* Successful scan:
![Example successful scan][]
* Pending scan:
![Example pending scan][]

To learn more about how to use the service from the Bluemix dashboard, see the [Static Analyzer documentation][6].
    
##Globalizing strings by using the Delivery Pipeline

As a part of your delivery pipeline, you can use the IBM Globalization service to translate strings automatically into other languages. The Globalization service uses machine translation to translate your source files as part of the pipeline build and deploy process. Also, with the Globalization service, you can update the machine translated strings within the globalization project. This configuration allows for a quick translation of any new strings, with the additional value and quality that is provided by a human verification of the translated strings.

Before you begin, put all of your English translatable strings in one or more `filename_en.properties` or `filename_en.json` files that all have the same name. Example: `messages_en.properties`

A common pipeline setup that includes globalization:

<iframe width="640" height="360" src="https://www.youtube.com/embed/UToj7FIomCg?feature=player_embedded" frameborder="0" allowfullscreen></iframe>

To create a globalization stage and job:

1. Create a globalziation stage.
  a. Click **ADD STAGE**.
  b. Name the stage. Example: `Globalization`
  c. For the **Input type**, select **SCM repository**.
  
2. In the globalization stage, add a job to translate the source files.
  a. In the **JOBS** tab, click **ADD JOB**.
  b. Select the **Build job type.
  c. For the **Builder type**, select **IBM Globalization**.
  d. For the organization and space, verify the values and update, if necessary.
  e. For the **Source file name**, enter the name and the extension for the `.properties` or `.json` input files. If you have multiple files in different sub directories to translate that all have the same name, you can enter the name one time. For example, if you have a `messages_en.properties` file in each of three different directories, enter `messages_en.properties` for the source file name so that all of them are translated.
  f. For **Set up service and space for me**, select or clear the checkbox.
    * When this field is selected, the pipeline checks your Bluemix space for the service and an application that binds the service to the container. If the service or bound application do not exist, the pipeline adds the free plan of the service to your space for you. The bound application that is created is named `pipeline_bridge_app`. Then, the pipeline uses the credentials from `pipeline_bridge_app` to access the bound services.
    * Leave this field cleared if you either configured the service and bound application in your Bluemix space already or [you want to configure these requirements yourself][9].
  g. For the **Globalization project prefix**, enter a prefix for the project name, which is structured in the format `[globalization_project_prefix].path.to.source.file`. The pipeline job creates this Globalization project for you in the Globalization service. It is good to use the DevOps Services project name in the prefix so that the project can be identified easily in the Globalization service.
  h. Click **SAVE**. 
3. **Required:** Create another stage to package your application. Use the Globalization job from the previous stage as the input to this job rather than using the source as the input. The Globalization job augments the source files with machine translated content. To ensure that this content is included in the packaged application, package the application in a separate stage and include the Globalization job as input to that stage.

The machine translated files are placed in the same directory as the source `.properties` or `.json` file and can be viewed under **Job > Artifacts**.

After the stage completes successfully, in the console output, you can access a link to the service to review the translated files. From that user interface, translators can review the machine translation output and provide revisions to improve the quality. Those revisions are stored in a Cloudant™ database and take precedence over any future machine translations of the same strings.

To learn more about how to use the service from the Bluemix dashboard, [see the Globalization documentation][10].

[1]: https://hub.jazz.net/docs/deploy
[2]: https://www.ng.bluemix.net/docs/containers/container_single_pipeline_ov.html#container_single_pipeline_ov
[3]: https://www.ng.bluemix.net/docs/containers/container_group_pipeline_ov.html#container_group_pipeline_ov 
[4]: http://www-03.ibm.com/software/sla/sladb.nsf/sla/bm-6814-01
[5]: https://www.ng.bluemix.net/docs/containers/container_group_pipeline_ov.html#container_binding_pipeline
[6]: https://www.ng.bluemix.net/docs/services/StaticAnalyzer/index.html
[7]: ./images/analyzer_success.png
[8]: ./images/analyzer_pending.png
[9]: https://www.ng.bluemix.net/docs/containers/container_group_pipeline_ov.html#container_binding_pipeline
[10]: https://www.ng.bluemix.net/docs/services/Globalization/index.html
