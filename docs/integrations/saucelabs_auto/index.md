# Integrating Sauce Labs with Bluemix DevOps Services 

###### Last updated: 29 September 2015

You can integrate automated functional tests that run on Sauce Labs into the IBM&reg; Bluemix&trade; DevOps Services pipeline. When configured as a test job in a pipeline, a Sauce Labs test suite can run Java or JavaScript tests against your web or mobile application as part of your continuous delivery process. These tests can provide valuable flow control for your projects, acting as gates to prevent the deployment of bad code.

**Important**: The Sauce Labs integration is a Beta feature. After you [enable this Beta feature](#enabling_the_beta_features), you cannot disable or modify it. To test the Sauce Labs integration in a copy of your project without changing the original version, [fork an existing DevOps Services project](#forking_a_devops_services_project). Otherwise, click the **Deploy to Bluemix** button from within a [sample](https://hub.jazz.net/project/idsorg/sample-java-cloudant/overview) to deploy sample code and create a tool chain that you can test the Sauce Labs integration in.


* [Forking a project](#forking_a_devops_services_project)
* [Enabling the Beta features](#enabling_the_beta_features)
* [Configuring the Sauce Labs integration](#configuring_the_sauce_labs_integration)


## Before you begin
* [Register for DevOps Services](https://hub.jazz.net).
* [Register for Bluemix](http://bluemix.net/). 
* [Register for a Sauce Labs account](https://saucelabs.com/) if you don't already have one. Sauce Labs offers 14-day trials for new accounts. If you want to learn how to use Sauce Labs, [see the official Sauce Labs documentation](https://docs.saucelabs.com/). 
* Ensure that you have at least one existing DevOps Services project with a pipeline set up that you can use to deploy your app. Otherwise, you can click the **Deploy to Bluemix** button from within a [sample](https://hub.jazz.net/project/idsorg/sample-java-cloudant/overview) to deploy sample code and create a tool chain that does not already integrate with Sauce Labs.

<a name='forking_a_devops_services_project'></a>
##Forking a project

You can fork an existing DevOps Services project to test the Sauce Labs integration in a copy of your project without changing the original version.

1. [Log in to DevOps Services](https://hub.jazz.net). The My Projects page opens.

2. Click **EXPLORE**, find the project to start from, and click its name.

3. Click **FORK PROJECT**. When you fork a project, the original project's source is copied into a new DevOps Services project that you own.

4. In the Fork Project window that opens, type your project name, review the contents of the window, and specify options as needed. For more information about the options, [see Starting a Bluemix DevOps Services project](/docs/startproject#starting_a_devops_services_project).
![Bluemix DevOps Services new user landing page][1]
 
5. Click **CREATE**.


<a name='enabling_the_beta_features'></a>
## Enabling the Beta features

Before you can configure the Sauce Labs integration, you must enable the Beta features for your project.

1. Open the forked version of the project that you just created.

2. On the project's Overview page, click the **Settings** icon.
![Project settings icon][2]

3. Click **BETA FEATURES**.

4. Select the **Enable this project to integrate with more tools** check box.

5. Click **SAVE**.


<a name='configuring_the_sauce_labs_integration'></a>
## Configuring the Sauce Labs integration

1. On the project's Overview page, click **Integrate with a tool** in the Integrated Tools section. 
![Project Overview page integrations section][3]

2. Click **SAUCE LABS**.
![Sauce Labs integration page][4]

3. Enter the API key for your Sauce Labs account. You can [locate this key in the bottom-left corner of your Sauce Labs account page](https://saucelabs.com/account).

4. Enter the user name for your Sauce Labs account. You can [locate your user name in the welcome message at the top of your Sauce Labs account page](https://saucelabs.com/account).

5. Configure a test Sauce Labs job. You can run, build, and deploy test Sauce Labs jobs to Bluemix. Use either of the following methods to configure the test job:

   a. Select the **Add a Sauce Labs test job in my Build & Deploy pipeline** check box to automatically configure a test Sauce Labs job.
   b. On the project's Overview page, click **BUILD & DEPLOY**, and then navigate to the Build & Deploy Pipeline page to add jobs to a specific stage. 
   
6. Click **SAVE**.

7. On the project's Overview page, click **BUILD & DEPLOY**, and then navigate to the Build & Deploy Pipeline page to verify that the test job was created.

8. On the Build Stage tile, click the **Run Stage** icon <img  class="inline" src="./images/run_stage.png" alt="The Run Stage icon"> to manually run the stage. The build is added to the queue, is run, and then is deployed to Bluemix.
![The project's configured pipeline][5]

9. View the Sauce Labs test results to verify that they are green. You can use either of the following methods to view the results:

   a. After the Deploy Stage tile indicates that your app is running, in the LAST EXECUTION RESULT section, click the URL that is under the app name.
   b. In the project's Overview page, click **MORE** > **Sauce Labs**.
  

**Tip**: To view the Sauce Labs test results at any time, in the project’s Overview page click **MORE** > **Sauce Labs**.




[1]: images/restyle_newprojectwindow.png
[2]: images/project_settings_icon.png
[3]: images/integrations.png
[4]: images/integrate_sauce_labs.png
[5]: images/configured_pipeline.png