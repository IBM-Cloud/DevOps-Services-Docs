#Integrate Sauce Labs and Slack with Bluemix DevOps Services

######Last modified: 29 September 2015

Time: 15 minutes 

In this tutorial, you learn how to deploy a copy of a sample application in your IBM&reg; Bluemix&trade; account that is managed by an IBM Bluemix&trade; DevOps Services tool chain. This tool chain is automatically pre-configured with Sauce Labs and Slack integrations. The tool chain is also pre-configured with existing DevOps Services such as Track and Plan, Git, the web integrated development environment (Web IDE), and Delivery Pipeline.

This DevOps Services tool chain integrates automated functional tests run on Sauce Labs into the DevOps Services pipeline. These tests can provide valuable flow control for your projects, acting as gates to prevent the deployment of bad code.

The tool chain also integrates Slack messaging into the DevOps Services pipeline. You can send notifications about build and deploy activities to your Slack channels. 

**Important**: This is a Beta feature. After you [deploy your app](#deploy_app), you cannot modify or remove the configured integrations from the generated project.

<div class="table-of-contents">
 <table>
   <tr>
     <td colspan="6"><h4>Summary of steps</h4></td>
   </tr>
   <tr>
     <td><a href="#prereq">Before you begin</a></td>
     <td><a href="#app_details">Specify the app details</a></td>
     <td><a href="#configure_slack">Configure the Slack integration</a></td>
     <td><a href="#configure_sauce_labs">Configure the Sauce Labs integration</a></td>
     <td><a href="#deploy_app">Deploy your app</a></td>
     <td><a href="#view_results">View logs and test results</a></td>
   </tr>
 </table>
</div>

<a name='prereq'></a>
## Before you begin

To do this tutorial, you need a DevOps Services account and a Bluemix account. The accounts are free and provide access to everything you need to develop, track, plan, and deploy apps. Signing up is simple: when you sign up for DevOps Services, you can also sign up for a trial of Bluemix.
<h5> </h5>
<div class="container-fluid small_bottom_space">
   <div class="row pbl button-links" id="overview-links">
		<a href="https://login.jazz.net/psso/proxy/jazzregister?redirect_uri=https%3A%2F%2Fhub.jazz.net%2F" target="_blank" alt-text="Sign up"> 
			<div class="hollowButton">SIGN UP<div class="extra-title">for DevOps Services </div>
			</div>
		</a>
   </div>
</div>

If you don't already have a Sauce Labs account, [register for one](https://saucelabs.com/). Sauce Labs offers 14-day trials for new accounts.

If you don't already have a Slack account, [register for one](https://slack.com/).

Review [DevOps Tutorial Application](https://github.com/oneibmcloud/devops-tutorial-1) for guidance and a tool chain recommendation for IBM Bluemix. The tool chain recommendation includes a Build and Deploy Delivery Pipeline, Sauce Labs, Git, Web IDE, and Track and Plan.

<a name='app_details'></a>
## Specify the app details

1. In the [DevOps Tutorial Application](https://github.com/oneibmcloud/devops-tutorial-1), click <img class="inline" src="./images/deploy-button.png"  alt="Deploy to Bluemix"> to fork the sample into DevOps Services. 
2. [Log in to or sign up for Bluemix](http://bluemix.net/) to start the Deploy to Bluemix flow.
3. Click **App Details**. 
![App Details page][1]
4. Review the default information for the APP NAME and destination (REGION, ORGANIZATION, and SPACE). Change these settings, as required.
5. The Integrations section shows information that is specific to the Slack and Sauce Labs integrations. For information about configuring these integrations, see [Configure the Slack integration](#configure_slack) and [Configure the Sauce Labs integation](#configure_sauce_labs).


<a name='configure_slack'></a>
## Configure the Slack integration

1. In the App Details page, navigate to the Integrations section. 
2. Expand the **SLACK** section.
3. Enter the authentication token for your Slack account. For instructions about how to locate this token, see [Slack authentication](https://api.slack.com/web#authentication).
4. Enter the name of the Slack channel to send notifications to about build results from your delivery pipleine. You can use an existing, archived, or new channel. If the specified Slack channel doesn't already exist, it is created. If the specified Slack channel is currently archived, it is reactivated.
	

<a name='configure_sauce_labs'></a>
## Configure the Sauce Labs integration

1. In the App Details page, navigate to the Integrations section. 
2. Expand the **SAUCE LABS** section.
3. Enter the API key for your Sauce Labs account. You can [locate this key in the bottom-left corner of your Sauce Labs account page](https://saucelabs.com/account).
4. Enter the user name that is associated with your Sauce Labs account. You can [locate your user name in the welcome message at the top of your Sauce Labs account page](https://saucelabs.com/account).


<a name='deploy_app'></a>
## Deploy your app

1. In the App Details page, click **DEPLOY**. The following steps run to set up the automated tool chain:

   a. Create the project.
   
   b. Clone the repository.
   
   c. Configure the pipeline to run.
   
   d. Configure the Sauce Labs integration to add a job to the pipeline and run tests.
   
   e. Configure the Slack integration to send notifications to the channel that you configured in Slack. These notifications indicate the progress of the deployment, such as "Connected with Project XYZ", "Pipeline Configured", and "Stage 'build" started".
   
   f. Deploy the app to Bluemix.
   ![Deploy success dialog][2] 
   
2. To view your running application in Bluemix, click **VIEW YOUR APP**. 

3. To view or modify the code for the sample that you just deployed, click **EDIT CODE**. Your new project opens in the DevOps Services Web IDE.
 


<a name='view_results'></a>
## View logs and test results

1. On the project's Overview page in DevOps Services, click **MORE**. 
![MORE button][3]

2. From the list of available integrations, select any of the following options:  

  a. Click **Sauce Labs** to view all of your activity, including the test that you just ran.

  b. Click **Slack** to view all of your activity in the configured channel, including notification messages for the build that just ran.
    
3. On the project's Overview page, click **BUILD & DEPLOY**, and then navigate to the Sauce Labs job to examine the logs and test results for the pipeline that you ran.
![Sauce Labs job][4]


<a name='summary'></a>
## Summary

You created your own version of a sample application in your Bluemix account that is managed by a DevOps Services tool chain. The tool chain was automatically pre-configured with Sauce Labs and Slack integrations. You configured Sauce Labs and Slack to integrate with your DevOps Services project, deployed the app, and then viewed logs and test results.


<a name='next_steps'></a>
## Next steps

DevOps Services supports integrations with many popular tools. To learn more about other supported integrations, see [Integrations](/docs/integrations/).




[1]: /tutorials/integrations_ui/images/app_details_page.png
[2]: /tutorials/integrations_ui/images/deploy_success.png
[3]: /tutorials/integrations_ui/images/more.png
[4]: /tutorials/integrations_ui/images/sauce_labs_job.png