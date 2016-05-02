# Integrating Slack with Bluemix DevOps Services <em><span style="color: #35b2d5">Beta</span></em>

###### Last updated: 14 October 2015

Slack provides real-time messaging for team communications. You can integrate Slack with your IBM&reg; Bluemix&trade; DevOps Services project so that notifications about build results from your Build &amp; Deploy pipeline are posted on a Slack channel. 

**Important:** This integration feature is beta quality. After you [enable your project to use the integration feature](#enabling_the_beta_features), you cannot disable or modify it. To test the Slack integration in a copy of your project, [fork another DevOps Services project](#forking_a_devops_services_project). Otherwise, open a [sample](https://hub.jazz.net/project/idsorg/sample-java-cloudant/overview) and click the **Deploy to Bluemix** button to deploy sample code and create a toolchain that you can test the Slack integration in.


* [Forking a project](#forking_a_devops_services_project)
* [Enabling the beta integration feature](#enabling_the_beta_features)
* [Configuring the Slack integration](#configuring_the_slack_integration)


## Before you begin
* You must have accounts with these services and tools:
   * [DevOps Services](https://hub.jazz.net) 
   * [IBM Bluemix](http://bluemix.net/)
   * [Slack](https://slack.com/) 
* You must have at least one DevOps Services project with a pipeline that you can use to deploy your app. Otherwise, open a [sample](https://hub.jazz.net/project/idsorg/sample-java-cloudant/overview) and click the **Deploy to Bluemix** button to deploy sample code and create a toolchain that does not already integrate with Slack.

<a name='forking_a_devops_services_project'></a>
##Forking a project

You can test the Slack integration in a copy of your project without changing the original version by forking a DevOps Services project.

1. [Log in to DevOps Services](https://hub.jazz.net). The My Projects page opens.

2. Click **EXPLORE**, find the project to start from, and click its name.

3. Click **FORK PROJECT**. When you fork a project, the original project's source is copied into a new DevOps Services project that you own.

4. In the Fork Project window that opens, type your project name, review the project information, and specify options as needed. For more information, [see Creating a project from DevOps Services](/docs/startproject#starting_a_devops_services_project).
![Bluemix DevOps Services new user landing page][1]
 
5. Click **CREATE**.


<a name='enabling_the_beta_features'></a>
## Enabling the beta integration feature

Before you can configure the Slack integration, you must enable your project to use the beta integration feature.

1. Open the forked version of the project that you created.

2. On the project's Overview page, in the upper-right corner, click the **Settings** icon.
![Project settings icon][2]

3. Click **BETA FEATURES**.

4. Select the **Enable beta integration features for this project** check box.

5. Click **SAVE**.


<a name='configuring_the_slack_integration'></a>
## Configuring the Slack integration

1. On the project's Overview page, in the Integrated Tools section, click **Integrate with a tool**. 
![Project Overview page integrations section][3]

2. Click **SLACK**.
![Slack integration page][4]

3. Type the API authentication token for your Slack account. You must use a generated full-access token to authenticate with Slack. For instructions about how to find this token, see [Slack authentication](https://api.slack.com/web#authentication).

4. Type the name of the Slack channel that you want pipeline notifications to be sent to. You can use an existing, archived, or new channel. If the specified Slack channel doesn't exist, it is created. If the specified Slack channel is archived, it is reactivated.

5. Click **SAVE**.

**Tip**: To open the configured Slack channel at any time, go to the project’s Overview page and click **MORE** > **Slack**.



[1]: images/restyle_newprojectwindow.png
[2]: images/project_settings_icon.png
[3]: images/integrations.png
[4]: images/integrate_slack.png
