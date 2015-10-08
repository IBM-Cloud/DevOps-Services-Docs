#Integrate Sauce Labs and Slack with a Bluemix DevOps Services project <em><span style="color: #35b2d5">BETA</span></em>

######Last modified: 08 October 2015

Time: 15 minutes 

In this tutorial, you learn how to deploy a copy of a sample app that is managed by an IBM&reg; Bluemix&trade; DevOps Services toolchain. The toolchain is preconfigured with Sauce Labs and Slack integrations and with DevOps Services features, such as the Track &amp; Plan feature, the web integrated development environment (Web IDE), the Build &amp; Deploy pipeline, and Git for source control.

This DevOps Services toolchain integrates automated functional tests that are run on Sauce Labs into the DevOps Services pipeline. These tests can provide valuable flow control for your project as they act as gates to prevent the deployment of bad code.

The toolchain also integrates Slack messaging into the DevOps Services pipeline. For example, your team can get notifications about build and deploy activities through a Slack channel. 

**Important:** This integration capability is beta quality. After you [deploy your app](#deploy_app), you cannot modify or remove the configured integrations from the project.

<div class="table-of-contents">
 <table>
   <tr>
     <td colspan="6"><h4>Summary of steps</h4></td>
   </tr>
   <tr>
     <td><a href="#prereq">Before you begin</a></td>
     <td><a href="#app_details">Fork and set up the app</a></td>
     <td><a href="#configure_slack">Configure the Slack integration</a></td>
     <td><a href="#configure_sauce_labs">Configure the Sauce Labs integration</a></td>
     <td><a href="#deploy_app">Deploy your app</a></td>
     <td><a href="#view_results">View the logs and test results</a></td>
   </tr>
 </table>
</div>

<a name='prereq'></a>
## Before you begin

* To do this tutorial, you need a DevOps Services account and a Bluemix account. The accounts are free and provide access to everything you need to develop, track, plan, and deploy apps. Signing up is simple: when you sign up for DevOps Services, you can also sign up for a trial of Bluemix.
<h5> </h5>
<div class="container-fluid small_bottom_space">
   <div class="row pbl button-links" id="overview-links">
		<a href="https://login.jazz.net/psso/proxy/jazzregister?redirect_uri=https%3A%2F%2Fhub.jazz.net%2F" target="_blank" alt-text="Sign up"> 
			<div class="hollowButton">SIGN UP<div class="extra-title">for DevOps Services </div>
			</div>
		</a>
   </div>
</div>

* If you don't already have a Sauce Labs account, [register for one](https://saucelabs.com/). Sauce Labs offers 14-day trials for new accounts.

* If you don't already have a Slack account, [register for one](https://slack.com/).

* Review [DevOps Tutorial Application](https://github.com/oneibmcloud/devops-tutorial-1) for guidance and a toolchain for Bluemix. The toolchain includes a Build &amp; Deploy pipeline, Sauce Labs, Git, Web IDE, and Track and Plan.

<a name='app_details'></a>
## Fork and set up the app

1. In the [DevOps Tutorial Application](https://github.com/oneibmcloud/devops-tutorial-2), click <img class="inline" src="./images/deploy-button.png"  alt="Deploy to Bluemix"> to fork the sample into DevOps Services. 
2. [Log in to Bluemix](http://bluemix.net/) to start the Deploy to Bluemix flow.
3. Click **App Details**. 
![App Details page][1]
4. Review the default information for the APP NAME and destination (REGION, ORGANIZATION, and SPACE). Change these settings as needed.
5. The Integrations section shows information that is specific to the Slack and Sauce Labs integrations. For information about configuring those integrations, see [Configure the Slack integration](#configure_slack) and [Configure the Sauce Labs integration](#configure_sauce_labs).


<a name='configure_slack'></a>
## Configure the Slack integration

1. On the App Details page, go to the Integrations section. 
2. Expand the **SLACK** section.
3. Type the API authentication token for your Slack account. For instructions about how to find the token, see [Slack authentication](https://api.slack.com/web#authentication). 
4. Type the name of the Slack channel that you want pipeline notifications to be sent to. You can use an existing, archived, or new channel. If the specified Slack channel doesn't exist, it is created. If the specified Slack channel is currently archived, it is reactivated.
	

<a name='configure_sauce_labs'></a>
## Configure the Sauce Labs integration

1. On the App Details page, go to the Integrations section. 
2. Expand the **SAUCE LABS** section.
3. Type the user name that is associated with your Sauce Labs account. You can [find your user name in the welcome message at the top of your Sauce Labs account page](https://saucelabs.com/account).
4. Type the access token for your Sauce Labs account. You can [find this token in the lower-left corner of your Sauce Labs account page](https://saucelabs.com/account).


<a name='deploy_app'></a>
## Deploy your app

1. On the App Details page, click **DEPLOY**. The following steps run to set up the automated toolchain:

   a. Create the project.
   
   b. Clone the repository.
   
   c. Configure the pipeline to run.
   
   d. Configure the Sauce Labs integration to add a job to the pipeline and run tests.
   
   e. Configure the Slack integration to send notifications to the channel that you configured in Slack. These notifications indicate the progress of the deployment; for example, "Connected with Project XYZ", "Pipeline Configured", and "Stage 'build" started".
   
   f. Deploy the app to Bluemix.
   ![Deploy success dialog][2] 
   
2. To view your running app in Bluemix, click **VIEW YOUR APP**. 

3. To view or modify the code for the sample that you just deployed, click **EDIT CODE**. Your new project opens in the DevOps Services Web IDE.
 


<a name='view_results'></a>
## View the logs and test results

1. On the project's Overview page in DevOps Services, click **MORE**. 
![MORE button][3]

2. From the list of available integrations, select any of these options:  

  * Click **Sauce Labs** to view all of your activity, including the test that you just ran.

  * Click **Slack** to view all of your activity in the configured channel, including notification messages for the build that just ran.
    
3. On the project's Overview page, click **BUILD & DEPLOY**. Go to the Sauce Labs job to examine the logs and test results for the pipeline that you ran.
![Sauce Labs job][4]


<a name='summary'></a>
## Summary

You created your own version of a sample app in your Bluemix account that is managed by a DevOps Services toolchain. The toolchain was preconfigured with Sauce Labs and Slack integrations. You configured Sauce Labs and Slack to integrate with your DevOps Services project, deployed the app, and viewed logs and test results.


<a name='next_steps'></a>
## Next steps

DevOps Services supports integrations with many popular tools. To learn more about other supported integrations, see [Integrations](/docs/integrations/).



[1]: /tutorials/integrations_ui/images/app_details_page.png
[2]: /tutorials/integrations_ui/images/deploy_success.png
[3]: /tutorials/integrations_ui/images/more.png
[4]: /tutorials/integrations_ui/images/sauce_labs_job.png
