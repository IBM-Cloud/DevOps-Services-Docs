#Integrate Sauce Labs and Slack with Bluemix DevOps Services

######Last modified: 21 September 2015

Time: 15 minutes 

In this tutorial, you create your own version of a sample IBM&reg; Bluemix&trade; DevOps Services project by cloning it in your space. You configure Sauce Labs and Slack to integrate with your DevOps Services project. When you deploy the project to IBM&reg; Bluemix&trade;, a pre-configured DevOps tool chain is set up.

This DevOps Services tool chain integrates automated functional tests run on Sauce Labs into the DevOps Services pipeline. These tests can provide valuable flow control for your projects, acting as gates to prevent the deployment of bad code.

The tool chain also integrates Slack communications into the DevOps Services pipeline. You can send notifications about build results from your delivery pipeline to your Slack channels. 


<div class="table-of-contents">
 <table>
   <tr>
     <td colspan="8"><h4>Summary of steps</h4></td>
   </tr>
   <tr>
     <td><a href="#prereq">Before you begin</a></td>
     <td><a href="#clone">Clone the sample app</a></td>
     <td><a href="#configure_slack">Configure the Slack integration</a></td>
     <td><a href="#configure_sauce_labs">Configure the Sauce Labs integration</a></td>
     <td><a href="#deploy_app">Deploy your app</a></td>
     <td><a href="#view_results">View logs and test results</a></td>
   </tr>
 </table>
</div>

<a name='prereq'></a>
## Before you begin

*To do this tutorial, you need a DevOps Services account and a Bluemix account. The accounts are free and provide access to everything you need to develop, track, plan, and deploy apps. Signing up is simple: when you sign up for DevOps Services, you can also sign up for a trial of Bluemix.

<h5> </h5>
<div class="container-fluid small_bottom_space">
   <div class="row pbl button-links" id="overview-links">
		<a href="https://login.jazz.net/psso/proxy/jazzregister?redirect_uri=https%3A%2F%2Fhub.jazz.net%2F" target="_blank" alt-text="Sign up"> 
			<div class="hollowButton">SIGN UP<div class="extra-title">for DevOps Services </div>
			</div>
		</a>
   </div>
</div>
*If you don't already have a Sauce Labs account, [register for one].(https://saucelabs.com/) Sauce Labs offers 14-day trials for new accounts.
*If you don't already have a Slack account, [register for one].(https://slack.com/)
*Read [DevOps Tutorial Application](https://github.com/oneibmcloud/devops-tutorial-1) for guidance and a tool chain recommendation for IBM Bluemix. The tool chain recommendation includes a Build and Deploy Delivery Pipeline, Sauce Labs or SpeedCurve, GitHub, the DevOps Services web integrated development environment (Web IDE), and Track and Plan.
<a name='clone'></a>
## Clone the sample app

1. In the [DevOps Tutorial Application](https://github.com/oneibmcloud/devops-tutorial-1), click <img class="inline" src="./images/deploy-button.png"  alt="Deploy to Bluemix"> to fork the sample into DevOps Services. 
2. [Log in to or sign up for Bluemix](http://bluemix.net/).
![Prompt to log in or sign up for Bluemix][1]
A clone of the sample application is deployed on Bluemix, with a pre-configured DevOps tool chain.
3. In the App details page, review the default information for the APP NAME and destination (REGION, ORGANIZATION, and SPACE). Change these settings, as required.
![App details page][2]


<a name='configure_slack'></a>
## Configure the Slack integration

1. Navigate to the .bluemix folder in the sample code. 
2. Open the slack.yml file.
3. In the parameters section, update the following parameter values to use your own Slack account.

	 a. **auth-token** - The authentication token for your Slack account.
	
	 b. **channelName** - The name of the Slack channel to send notifications to about build results from your delivery pipeline.

4. In the App details page in Bluemix, review the information in the MESSAGING (SLACK) section. The values in the **AUTH-TOKEN and **CHANNELNAME** fields should match the parameter values that you set in the Slack.yml file.
![SLACK section of the App details page][3]


<a name='configure_sauce_labs'></a>
## Configure the Sauce Labs integration

1. Navigate to the .bluemix folder in the sample code. 
2. Open the saucelabs.yml file.
3. In the parameters section, update the following parameter values to use your own Sauce Labs account.

	 a. **user name** - The user name associated with your Sauce Labs account. You can [locate your user name in the welcome message at the top of your Sauce Labs account page](https://saucelabs.com/account).
	
	 b. **key** - The access (API) key for your Sauce Labs account. You can [locate this key in the bottom-left corner of your Sauce Labs account page](https://saucelabs.com/account).

4. In the App details page in Bluemix, review the information in the TEST (SAUCE LABS) section. The values in the **KEY and **USER NAME** fields should match the parameter values that you set in the saucelabs.yml file.
![SAUCE LABS section of the App details page][4]


<a name='deploy_app'></a>
## Deploy your app

1. In the App details page in Bluemix, click **DEPLOY**. The following steps run to set up the automated tool chain:

   a. Create the project.
   
   b. Clone the repository.
   
   c. Configure the pipeline to run.
   
   d. Configure the Sauce Labs integration to add a job to the pipeline and run tests.
   
   e. Configure the Slack integration to send notifications to the channel that you configured in Slack. These notifications indicate the progress of the deployment, such as "Connected with Project XYZ", "Pipeline Configured", and "Stage 'build" started".
   
   f. Deploy the app to Bluemix.
   ![Deploy success dialog][5] 
   
2. To view your running application in Bluemix, click **VIEW YOUR APP**.

3. TO view the overview page for the project, click **VIEW TOOLCHAIN**.

4. To view or modify the code for the sample that you just deployed, click **EDIT CODE**. Your new project opens in the DevOps Services Web IDE.
 


<a name='view_results'></a>
## View logs and test results

1. On the project's Overview page in DevOps Services, click **MORE**. 
![MORE button][6]

2. From the list of available integrations, select any of the following options:  

  a. Click **Sauce Labs** to view all of your activity, including the test that you just ran.

  b. Click Slack to view all of your activity in the configured channel, including notification messages for the build that just ran.
    
3. On the project's Overview page, click **BUILD & DEPLOY**, and then navigate to the Sauce Labs job to examine the logs and test results for the pipeline that you ran.
![Sauce Labs job][7]


<a name='summary'></a>
## Summary




<a name='next_steps'></a>
## Next steps


[1]: /tutorials/integrations_ui/images/bm_login.png
[2]: /tutorials/integrations_ui/images/app_details_page.png
[3]: /tutorials/integrations_ui/images/app_details_page2.png
[4]: /tutorials/integrations_ui/images/app_details_page3.png
[5]: /tutorials/integrations_ui/images/deploy_success.png
[6]: /tutorials/integrations_ui/images/more.png
[7]: /tutorials/integrations_ui/images/sauce_labs_job.png