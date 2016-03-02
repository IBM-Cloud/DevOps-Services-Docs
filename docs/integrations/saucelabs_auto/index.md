# Integrating Sauce Labs with Bluemix DevOps Services <em><span style="color: #35b2d5">BETA</span></em>

###### Last updated: 2 March 2016

Sauce Labs provides automated functional tests that run Java™ or JavaScript tests against your web or mobile app as part of a continuous delivery process. You can integrate Sauce Labs with your IBM&reg; Bluemix&trade; DevOps Services project so that a Sauce Labs test suite can run as a test job in your Build &amp; Deploy pipeline. These tests can provide valuable flow control for your project as they act as gates to prevent the deployment of bad code..

**Important:** This integration feature is currently beta quality. After you [enable your project to use the integration feature](#enabling_the_beta_features), you cannot disable or modify it. To test the Sauce Labs integration in a copy of your project, [fork another DevOps Services project](#forking_a_devops_services_project). Otherwise, open a [sample](https://hub.jazz.net/project/idsorg/sample-java-cloudant/overview) and click the **Deploy to Bluemix** button to deploy sample code and create a toolchain that you can test the Sauce Labs integration in.


* [Forking a project](#forking_a_devops_services_project)
* [Enabling the beta feature](#enabling_the_beta_features)
* [Configuring the Sauce Labs integration](#configuring_the_sauce_labs_integration)


## Before you begin
* You must have accounts with these services and tools:
   * [DevOps Services](https://hub.jazz.net). 
   * [IBM Bluemix](http://bluemix.net/).
   * [Sauce Labs](https://saucelabs.com/). Sauce Labs offers 14-day trials for new accounts. If you want to learn how to use Sauce Labs, [see the official Sauce Labs documentation](https://docs.saucelabs.com/). 
* You must have at least one DevOps Services project with a pipeline that you can use to deploy your app. Otherwise, open a [sample](https://hub.jazz.net/project/idsorg/sample-java-cloudant/overview) and click the **Deploy to Bluemix** button to deploy sample code and create a toolchain that does not already integrate with Sauce Labs.

<a name='forking_a_devops_services_project'></a>
##Forking a project

You can test the Sauce Labs integration in a copy of your project without changing the original version by forking a DevOps Services project.

1. [Log in to DevOps Services](https://hub.jazz.net). The My Projects page opens.

2. Click **EXPLORE**, find the project to start from, and click its name.

3. Click **FORK PROJECT**. When you fork a project, the original project's source is copied into a new DevOps Services project that you own.

4. In the Fork Project window that opens, type your project name, review the project information, and specify options as needed. For more information, [see Creating a project from DevOps Services](/docs/startproject#starting_a_devops_services_project).
![Bluemix DevOps Services new user landing page][1]
 
5. Click **CREATE**.


<a name='enabling_the_beta_features'></a>
## Enabling the beta feature

Before you can configure the Sauce Labs integration, you must enable your project to use the beta integration feature.

1. Open the forked version of the project that you just created.

2. On the project's Overview page, in the upper-right corner, click the **Settings** icon.
![Project settings icon][2]

3. Click **BETA FEATURES**.

4. Select the **Enable beta integration features for this project** check box.

5. Click **SAVE**.


<a name='configuring_the_sauce_labs_integration'></a>
## Configuring the Sauce Labs integration

1. On the project's Overview page, in the Integrated Tools section, click **Integrate with a tool**. 
![Project Overview page integrations section][3]

2. Click **SAUCE LABS**.
![Sauce Labs integration page][4]

3. Type the user name for your Sauce Labs account. You can [find your user name in the welcome message at the top of your Sauce Labs account page](https://saucelabs.com/account).

4. Type the access key for your Sauce Labs account. You can [find the key in the lower-left corner of your Sauce Labs account page](https://saucelabs.com/account).

5. Click **SAVE**.

6. Click **ADD JOB** to automatically configure a test Sauce Labs job. You can run and build Sauce Labs jobs, and you can deploy them to Bluemix.

7. On the project's Overview page, click **BUILD &amp; DEPLOY**, and then verify that the test job was created.

8. Customize the test job for your app:

 a. On the Build stage tile, click the **Stage Configuration** icon.
 b. Click **Configure Stage**.
 c. Click **ENVIRONMENT PROPERTIES**.
 d. Create an environment property named CF_*APP_NAME* where *APP_NAME* is the name of the app to be tested.

9. On the Build stage tile, click the **Run Stage** icon <img  class="inline" src="./images/run_stage.png" alt="The Run Stage icon"> to manually run the stage. The build is added to the queue, is run, and is deployed to Bluemix.

10. View the Sauce Labs test results to verify that they are green. When the Deploy stage tile indicates that your app is running, in the LAST EXECUTION RESULT section, click the URL that is under the app name.
![The project's configured pipeline][5]
  
**Tip:** To view the Sauce Labs test results at any time, on the project's Overview page, click **MORE** &gt; **Sauce Labs**.




[1]: images/restyle_newprojectwindow.png
[2]: images/project_settings_icon.png
[3]: images/integrations.png
[4]: images/integrate_sauce_labs.png
[5]: images/configured_pipeline.png
