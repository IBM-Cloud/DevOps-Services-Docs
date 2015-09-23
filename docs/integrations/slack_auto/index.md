# Integrating Slack with Bluemix DevOps Services 

###### Last updated: 23 September 2015

You can integrate Slack communications into the IBM&reg; Bluemix&trade; DevOps Services pipeline. When configured, you can use Slack to send notifications about build results from your delivery pipeline to your Slack channels. 

**Important**: The Slack integration is a Beta feature. After you [enable this Beta feature](#enabling_the_beta_features), you cannot disable or modify it. To test the Slack integration in a copy of your project without changing the original version, [fork an existing DevOps Services project](#forking_a_devops_services_project). Otherwise, click the **Deploy to Bluemix** button from within a [sample](https://hub.jazz.net/project/idsorg/sample-java-cloudant/overview) to deploy sample code and create a tool chain that you can test the Slack integration in.


* [Forking a project](#forking_a_devops_services_project)
* [Enabling the Beta features](#enabling_the_beta_features)
* [Configuring the Slack integration](#configuring_the_slack_integration)


## Before you begin
* [Register for DevOps Services](https://hub.jazz.net). 
* [Register for Bluemix](http://bluemix.net/). 
* [Register for a Slack account](https://slack.com/) if you don't already have one.
* Ensure that you have at least one existing DevOps Services project with a pipeline set up that you can use to deploy your app. Otherwise, you can click the **Deploy to Bluemix** button from within a [sample](https://hub.jazz.net/project/idsorg/sample-java-cloudant/overview) to deploy sample code and create a tool chain that does not already integrate with Slack.

<a name='forking_a_devops_services_project'></a>
##Forking a project

You can fork an existing DevOps Services project to test the Slack integration in a copy of your project without changing the original version.

1. [Log in to DevOps Services](https://hub.jazz.net). The My Projects page opens.

2. Click **EXPLORE**, find the project to start from, and click its name.
![Bluemix DevOps Services new user landing page][1]

3. Click **FORK PROJECT**. When you fork a project, the original project's source is copied into a new DevOps Services project that you own.

4. In the Fork Project window that opens, type your project name, review the contents of the window, and specify options as needed. For more information about the options, [see Starting a Bluemix DevOps Services project](#starting_a_devops_services_project).
 
5. Click **CREATE**.


<a name='enabling_the_beta_features'></a>
## Enabling the Beta features

Before you can configure the Slack integration, you must enable the Beta features for your project.

1. Open the forked version of the project that you just created.

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

3. Enter the authentication token for your Slack account. For instructions about how to locate this token, see [Slack authentication](https://api.slack.com/docs/oauth).

4. Enter the name of the Slack channel to send notifications to about build results from your delivery pipeline. You can use an existing, archived, or new channel. If the specified Slack channel doesn't already exist, it is created. If the specified Slack channel is currently archived, it is reactivated.

5. Click **SAVE**.

**Tip**: To open the configured Slack channel at any time, in the project’s Overview page click **MORE** > **Slack**.



[1]: images/restyle_newprojectwindow.png
[2]: images/project_settings_icon.png
[3]: images/integrations.png
[4]: images/integrate_slack.png