#Extending the capabilities of your Build & Deploy pipeline

###### Last updated: 7 August 2015

You can extend the capabilities of your Build & Deploy pipeline with test jobs, such as jobs to run static code scans or globalize strings.

* [Running static code scans by using the Delivery Pipeline](#scan)
* [Globalizing strings by using the Delivery Pipeline](#globalize)

<a name="scan"></a>
##Running static code scans by using the Delivery Pipeline
Want to find security issues in your code before you deploy it? When you use the IBM® Static Analyzer for Bluemix™ as part of your pipeline, you can run automated checks against your  Java™ app's static `.war`, `.ear`, `.jar`, or `.class` build binary files.

A pipeline that uses the Static Analyzer service typically includes these stages:
  
* A build stage to build the source files

* A processing stage that includes these jobs:

  * A build job to run the Static Analyzer service
  
  * A build job to run a container build
  
* A deploy stage to deploy the container

<iframe width="640" height="360" src="https://www.youtube.com/embed/38DgKxT189s?feature=player_embedded" frameborder="0" allowfullscreen></iframe>

###Creating a static code scan

Before you begin, [review the Terms of Use for the service][4].

1. Create a processing stage.

  a. Click **ADD STAGE**.
  
  b. Name the stage; for example, `Processing`
  
  c. For the input type, select **Build Artifacts**.
  
  d. For the stage and job, verify the values and update them if needed.
  
2. In the processing stage, add a build job to run the code scan.

  a. On the **JOBS** tab, click **ADD JOB**.
  
  b. For the job type, select the **Test**.
  
  c. For the **Tester type**, select **IBM Security Static Analyzer**.
  
  d. For the organization and space, verify the values and update them if needed.
  
  e. Select or clear the **Set up service and space for me** check box as needed.
  
    * If you want the pipeline to check your Bluemix space for the service and an app that binds the service to the container, select the check box. If the service or bound app does not exist, the pipeline adds the free plan of the service to your space. The bound app that is created is named `pipeline_bridge_app`. Then, the pipeline uses the credentials from pipeline_bridge_app to access the bound services.
    
    * If you already configured the service and bound app in your Bluemix space already, or if you want to [configure these requirements manually][5], leave the check box cleared.
  
  f. In the **Minutes to wait for analysis to complete** field, type a value of 0 - 59 minutes. The default value is 5 minutes. A URL to the Static Analyzer dashboard is in the console logs at the end of the job. 
  
     If the Static Analyzer scan is not complete before the time that you specified, the job fails. However, the scan analysis continues to run and you can view it on the Static Analyzer dashboard. After the Static Analyzer scan is complete, if you rerun the job, the scan request is not resubmitted and the pipeline job can be completed. Alternatively, you can configure the pipeline not to be blocked on a successful scan result. For instructions, see the next step.
 
  g. Select or clear the **Stop stage execution on job failure** check box depending on what you want to happen if this job fails or times out. Jobs can fail when vulnerabilities are high. 

    * If you select the check box and the job fails, later jobs in the stage and later stages do not run.
  
    * If you clear the check box and the job fails, the stage continues without blocking later jobs and stages. For example, if you know that the report includes many issues to process, you might configure the stage to continue because the scan can take a long time. In this scenario, you might not want the rest of your jobs and stages to stop only because the scan is taking too long.

  h. Click **SAVE**.

3. When the job finishes, view the results by clicking **View logs and history**. If the analysis succeeds or times out, a URL is shown in the scan results. If the scan status is pending, wait until the scan is complete to see the full results.

4. If you need to run the processing stage again before the analysis is finished, you can. In the following situations, a new analysis is not resubmitted and the previous results are used:
  * The processing stage was still running when you started a new analysis
  * A scan was already submitted for the build
  * A new source build hasn't run yet
  
5. To start a new analysis, complete one of these steps:
  * Run the build stage that inputs into the processing stage, and then run the processing stage again.
  * Open the URL for the scan results and click the **Trash** icon. Then, run the processing stage again.

###Console output examples:

#####Successful scan:
![Example successful scan][7]

####Pending scan:
![Example pending scan][8]

For more information about using the Static Analyzer service from the Bluemix Dashboard, [see the Static Analyzer service docs][6].
    
##Globalizing strings by using the Delivery Pipeline

You can translate strings automatically into other languages when you use the IBM Globalization service with your pipeline. The Globalization service uses machine translation to translate your source files as part of the pipeline's build and deployment process.

You can also update the machine-translated strings within the globalization project. A translator can then review the machine-translated strings to ensure that they are high quality.

To see an example of a typical pipeline that uses the Globalization service, watch this video:

<iframe width="640" height="360" src="https://www.youtube.com/embed/UToj7FIomCg?feature=player_embedded" frameborder="0" allowfullscreen></iframe>

###Creating a globalization stage and job
Before you begin, put all of your English-translatable strings in one or more `filename_en.properties` or `filename_en.json` files that all have the same name. For example: `messages_en.properties`.

1. Create a globalization stage.

  a. Click **ADD STAGE**.
  
  b. Name the stage; for example, `Globalization`.
  
  c. For the input type, select **SCM repository**.
  
2. In the globalization stage, add a job to translate the source files.

  a. On the **JOBS** tab, click **ADD JOB**.
  
  b. For the job type, select **Build**.
  
  c. For the builder type, select **IBM Globalization**.
  
  d. For the organization and space, verify the values and update them if needed.
  
  e. In the **Source file name** field, type the name and extension of the `.properties` or `.json` input file. If you have files in different subdirectories and all of the files have the same name, you can type the name only one time. For example, if you have a `messages_en.properties` file in three directories, type `messages_en.properties` for the source file name so that all of them are translated.
  
  f. Determine whether to select the **Set up service and space for me** check box.
  
    * If you want the pipeline to check your Bluemix space for the service and an app that binds the service to the container, select this check box. If the service or bound app does not exist, the pipeline adds the free plan of the service to your space for you. The bound app that is created is named `pipeline_bridge_app`. Then, the pipeline uses the credentials from pipeline_bridge_app to access the bound services.
    
    * If you configured the service and bound app in your Bluemix space already or if you want to [configure these requirements manually][9], leave this check box cleared.
    
  g. For the Globalization project prefix, enter a prefix for the project name, which is structured in this format: `<globalization_project_prefix>.path.to.source.file`. The pipeline job creates this Globalization project for you in the Globalization service.
  
    **Tip:** Use the DevOps Services project name in the prefix so that the project can be identified easily in the Globalization service.
  
  h. Click **SAVE**. 
  
3. Create another stage to package your app. For the input of the job in this stage, use the Globalization job from the previous stage. Do not use the source as the input. The Globalization job augments the source files with machine-translated content. 

4. To ensure that the machine-translated content is included in the packaged app, create another stage to package the app in. For the input to that stage, include the Globalization job. 

The machine translated files are placed in the same directory as the source `.properties` or `.json` file. To view the files, click **Job > Artifacts**.

After the stage is completed, you can review the translated files from the console output. You can also direct translators to the files so that they can review the machine-translation output and provide revisions to improve quality. The revisions are stored in a Cloudant™ database and take precedence over any future machine translations of the same strings.

For more information about using the Globalization service from the Bluemix Dashboard, [see the Globalization service documentation][10].

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
