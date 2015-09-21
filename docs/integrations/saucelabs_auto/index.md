# Integrating Sauce Labs with Bluemix DevOps Services 

###### Last updated: 21 September 2015

You can integrate autmotated functional tests that run on Sauce Labs into the IBM&reg; Bluemix&trade; DevOps Services pipeline. When configured as a test job in a pipeline, a Sauce Labs test suite can run Java or JavaScript tests against your web or mobile application as part of your continuous delivery process. These tests can provide valuable flow control for your projects, acting as gates to prevent the deployment of bad code.



* [Forking a project](#forking_a_devops_services_project)
* [Enabling the Beta features](#enabling_the_beta_features)
* [Configuring the Sauce Labs integration](#configuring_the_sauce_labs_integration)
* [Testing the Sauce Labs integration](#testing_the_sauce_labs_integration)


## Before you begin
* [Register for DevOps Services](https://hub.jazz.net). 
* [Register for a Sauce Labs account](https://saucelabs.com/) if you don't already have one. Sauce Labs offers 14-day trials for new accounts. If you want to learn how to use Sauce Labs, [see the official Sauce Labs documentation](https://docs.saucelabs.com/). 
* Ensure that you have at least one existing DevOps Services project. Otherwise, click the **Deploy to Bluemix** button from within a sample to deploy sample code and create a tool chain that does not already integrate with Sauce Labs.

<a name='forking_a_devops_services_project'></a>
##Forking a project

1. [Log in to DevOps Services](https://hub.jazz.net). The My Projects page opens.

2. Click **EXPLORE**, find the project to start from, and click its name.
![Bluemix DevOps Services new user landing page][1]

3. Click **FORK PROJECT**. When you fork a project, the original project's source is copied into a new DevOps Services project that you own.

4. In the Fork Project window that opens, type your project name, review the contents of the window, and specify options as needed. For more information about the options, [see Starting a Bluemix DevOps Services project](#starting_a_devops_services_project).
 
5. Click **CREATE**.


<a name='enabling_the_beta_features'></a>
## Enabling the Beta features

Before you can configure the Sauce Labs integration, you must enable the Beta features for your project.

1. Click EXPLORE to find the original DevOps Services project that you forked. Open the original project (not the forked version).

2. On the project's Overview page, click the **Settings** icon.
![Project settings icon][2]

3. Click **BETA FEATURES**.

4. Select the **Enable integration features** check box.

5. Click **SAVE**.


<a name='configuring_the_sauce_labs_integration'></a>
## Configuring the Sauce Labs integration

1. On the project's Overview page, click **Integrate with a tool** in the Integrated Tools section. 
![Project Overview page integrations section][3]

2. Click **SAUCE LABS**.
![Sauce Labs integration page][4]

3. Enter the user name for your Sauce Labs account. You can [locate your user name in the welcome message at the top of your Sauce Labs account page].(https://saucelabs.com/account)

4. Enter the API key for your Sauce Labs account. You can [locate this key in the bottom-left corner of your Sauce Labs account page].(https://saucelabs.com/account)

5. Optional. Select the **Add a Sauce Labs test job in my Build & Deploy pipeline** check box to run, build, and deploy test Sauce Labs jobs to Bluemix.

6. Click **SAVE**.

7. Notify your team about the new Sauce Labs feature available for your project.


<a name='testing_the_sauce_labs_integration'></a>
## Testing the Sauce Labs integration

1. On the project's Overview page, click **MORE**.
![The MORE button][5]

2. Click **Sauce Labs**.

3. Enter your Sauce Labs user credentials to automatically configure a test job.
	
4. On the project's Overview page, click **BUILD & DEPLOY**, and then navigate to the Build & Deploy Pipeline page to verify that the test job was created.

5. On the Build Stage tile, click the **Run Stage** icon <img  class="inline" src="/sidecar/images/run_stage.png" alt="The Run Stage icon"> to manually run the stage. The build is added to the queue, is run, and then is deployed to Bluemix.
![The project's configured pipeline][6]

6. View the Sauce Labs test results using either of the following methods:
a. After the Deploy Stage tile indicates that your app is running, in the LAST EXECUTION RESULT section, click the URL that is under the app name.
b. In the project’s Overview page, click **MORE** > **Sauce Labs**.

7. Verify that the Sauce Labs test results are green.



[1]: images/restyle_newprojectwindow.png
[2]: images/project_settings_icon.png
[3]: images/integrations.png
[4]: images/integrate_sauce_labs.png
[5]: images/more.png
[6]: images/configured_pipeline.png