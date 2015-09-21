# Integrating Slack with Bluemix DevOps Services 

###### Last updated: 21 September 2015

You can integrate Slack communications into the IBM&reg; Bluemix&trade; DevOps Services pipeline. When configured, you can use Slack to send notifications about build results from your delivery pipeline to your Slack channels. 


* [Forking a project](#forking_a_devops_services_project)
* [Enabling the Beta features](#enabling_the_beta_features)
* [Configuring the Slack integration](#configuring_the_slack_integration)


## Before you begin
* [Register for DevOps Services](https://hub.jazz.net). 
* [Register for a Slack account](https://slack.com/) if you don't already have one.
* Ensure that you have at least one existing DevOps Services project. Otherwise, click the **Deploy to Bluemix** button from within a sample to deploy sample code and create a tool chain that does not already integrate with Slack.

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

Before you can configure the Slack integration, you must enable the Beta features for your project.

1. Click EXPLORE to find the original DevOps Services project that you forked. Open the original project (not the forked version).

2. On the project's Overview page, click the **Settings** icon.
![Project settings icon][2]

3. Click **BETA FEATURES**.

4. Select the **Enable integration features** check box.

5. Click **SAVE**.


<a name='configuring_the_slack_integration'></a>
## Configuring the Slack integration

1. On the project's Overview page, click **Integrate with a tool** in the Integrated Tools section. 
![Project Overview page integrations section][3]

2. Click **SLACK**.
![Slack integration page][4]

3. Enter the authentication token for your Slack account.

4. Enter the name of the Slack channel to send notifications to about build results from your delivery pipeline.

5. Click **SAVE**.

6. Notify your team about the new Slack feature available for your project.



[1]: images/restyle_newprojectwindow.png
[2]: images/project_settings_icon.png
[3]: images/integrations.png
[4]: images/integrate_slack.png