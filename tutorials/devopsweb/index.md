#Clone, edit, and deploy an app from Bluemix

######Last modified: 24 August 2015

Time: 60 minutes 

In this tutorial, you create your own version of an IBM&reg; Bluemix&trade; DevOps Services project by cloning it in your space. Your project's code is stored in a Git repository that is part of DevOps Services. The project is private, so people can't see it unless you invite them to join.

In your project, you plan your work in the Track & Plan feature. If you've used IBM Rational Team Concert&trade;, the Track & Plan feature will seem familiar. As you work on your project, you update code in the editor and push the updates to the project repository, all by using the Web IDE.

When you're ready to deploy your updated code to IBM&reg; Bluemix&trade;, you create jobs to build and deploy your app by using the Build & Deploy feature (the pipeline). 

<div class="table-of-contents">
 <table>
   <tr>
     <td colspan="8"><h4>Summary of steps</h4></td>
   </tr>
   <tr>
     <td><a href="#prereq">Before you begin</a></td>
     <td><a href="#fork">Explore and clone the sample project</a></td>
     <td><a href="#plan_change">Plan a change to your project</a></td>
     <td><a href="#modify_code">Modify your project&#39;s code</a></td>
     <td><a href="#push_changes">Push your change to the project repository</a></td>
     <td><a href="#build_deploy">Explore builds and deployments</a></td>
     <td><a href="#deploy_app">Deploy the app and verify your changes</a></td>
     <td><a href="#work_item">Complete the work item</a></td>
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
		</a>&nbsp;
   </div>
</div>

<a name='fork'></a>
## Explore and clone the sample project

1. If you want to get an idea of what the app that you are about to create is like, [see the sample app running][27]. The app analyzes Twitter users' collective sentiment about a search phrase. 
2. If you want to get an idea of what the project is like, [see the contents of the Sentiment Analysis project][2]. This Node.js app uses a Git repository, and includes a Grunt build file.
3. Create your own copy of the Sentiment Analysis project by clicking the following button, **Deploy to Bluemix**. When you click the button, the project is cloned to a new, private project that you own, and then the new project is deployed to Bluemix:
<a target="_blank" href="https://bluemix.net/deploy?repository=https://hub.jazz.net/git/ibmdevopsservices/Sentiment.Analysis.App"><img class="button" src="images/bigButton.png" alt="Deploy to Bluemix"></a>
4. If you are prompted to log in to Bluemix, log in.
5. Click **DEPLOY**.
6. After the project is cloned and the deployment is complete, click **EDIT CODE** to continue.
![EDIT CODE button][41]


<a name='plan_change'></a>
## Plan a change to your project

With the Track & Plan feature in DevOps Services, you can manage projects by using an agile approach. You can create sprints and rank and assign stories, tasks, and defects to members of your development team. 

###Enable the Track & Plan feature

1. On the project's Overview page, click the **Project settings** icon.
![The Project Settings icon][44]
2. Click **OPTIONS**.
3. Select **Enable Track & Plan**.
4. Click **SAVE**.


###Explore the Track & Plan views

1. Near the top of the page, click **TRACK & PLAN**.
2. If you don't see lanes labeled OPEN and IN PROGRESS, enter the Lanes view by clicking **Display as lanes**.
![Click Display as lanes button][38]
3. In the OPEN lane, click the **Create a work item** field. Work items are grouped into the OPEN, IN PROGRESS, and RESOLVED lanes based on their status.

###Create a task
You can create different types of work items depending on what you're planning. For example, to describe a minor feature update, you might create a task item. To track the work to fix a problem, you might create a defect item. 

Describe a task to personalize the Sentiment Analysis App. You can assign attributes to the new work item by clicking the attribute icons under the **Create a work item** field, and you can use shorthand in the field:

1. In the **Create a work item** field, enter `Update default search topic, then deploy app` as your work item's summary. In this field, you can also assign other information to the work item, such as its owner and priority, by typing special characters. For more information, see the [Track & Plan reference](https://hub.jazz.net/docs/reference/trackplan/).

   a. Assign the "task" type to the work item: after the summary, type a space and then type `*task`.
   
   b. Assign the work item to yourself by typing `@:<Your Username>`.
   
   c. Assign a high priority to the work item by typing `$high`. 
   
2. Click **CREATE**. Your new work item is shown in the OPEN lane in the Recently Created section.

![Creating a new task item][4]
    
Your project now has one work item: a task to update the app's default search topic. The task has a high priority, so you need to do it soon.

![A recently created work item][5]

###Change the status of the task

1. On the task, click the **Status** icon.
2. Click **Start Working**. The task moves from the OPEN lane to IN PROGRESS lane.
![Click Start Working on a task in the lanes view.][12]
3. Write down the task's work item number, which in this example is 437. You need the number later when you link the task to a commit on the Git Repository page.


<a name='modify_code'></a>
## Modify your project's code

You now have a sample project and a task to personalize it. You can make and deliver that change in your browser by using the DevOps Services Web IDE.

1. Click **EDIT CODE**. The Web IDE opens and your project’s root directory is shown.
2. Open the `app.js` file.
3. On line 6 of the file, find the `DEFAULT_TOPIC` variable. That variable is the subject of the sentiment analysis that runs when your app is first deployed. Change the value of the variable to whatever you like. 
4. By default, when you stop typing for a moment, your change is saved automatically. 

![Updating a variable in the Web IDE][6]

Your change is saved and ready to be committed to the project's remote repository.


<a name='push_changes'></a>
## Push your change to the project repository

For revision control and source code management, DevOps Services supports Git, Jazz SCM, and GitHub. Because the original Sentiment Analysis App project uses a Git repository that is hosted by IBM, your copy of the project uses a Git repository, too. 

The code that you changed is currently in your workspace on the cloud. Push the changed code to your project's master branch and then deploy your app to Bluemix.

1. On the far left, click the **Git Repository** icon. 
![The Git Repository icon][14]
On the Git page that opens, check the Working Directory Changes section to verify that it shows an uncommitted change to the `app.js` file. You might also see other changes that are related to cloning the project into your workspace. You can check in those changes. 
2. Select the check box next to `app.js`. If you want to compare your version of the 'app.js' file with the version that is in the Git repository, click the arrow next to 'app.js'.
3. Type a commit message. Somewhere in the message, be sure to include this phrase: `task <number of your work item>`. That phrase links this commit to the task work item. If you don’t remember the number, return to the Track &amp; Plan area to find it.
![Ready to commit a change to app.js][13]
4. Click **COMMIT**. Your change is shown in the Active Branch section.
5. Click **PUSH**. Your local master branch is pushed to the remote master branch. 

![Ready to push a file update][7]

You're almost done. Now that your updated code is in your remote repository, you can configure DevOps Services to build the code and then deploy it automatically to Bluemix. Your updated app is about to go live! 


<a name='build_deploy'></a>
## Explore builds and deployments

When you clone a project by clicking the **Deploy to Bluemix** button, a pipeline is created for your project automatically. Before you deploy your app, explore how the pipeline works.

A pipeline is formed by its stages. The pipeline for your Sentiment Analysis app has two stages: a build stage and a deployment stage. The purpose of the build stage is to run a build job on the included `Gruntfile.js` to validate your code. The purpose of the deployment stage is to run a deploy job that deploys your code to Bluemix.

**Important:** You can complete this tutorial for free because a project is granted 60 minutes of free build time per month. However, the pipeline is a feature of the IBM Continuous Delivery Pipeline for Bluemix (the Delivery Pipeline service). When you use the Delivery Pipeline service with Bluemix, you can generate charges to your Bluemix account. For more information about Bluemix, DevOps Services, and charges, [see Configuring Bluemix billing for Bluemix DevOps Services][39].

###Explore the build stage
1. On the top navigation bar, click **BUILD & DEPLOY**. 

2. On the Build stage tile, click the **Stage Configuration** icon <img class="inline" src="images/configure_stage.png" alt="The Stage Configuration icon"> and then click **Configure Stage**.  

  a. On the **INPUT** tab, note this information:

    * The input for the build is the master branch of the Git repository. 
    * The Build stage runs automatically every time a change is pushed to the repository. 
      ![The INPUT tab][42]

  b. Click the **JOBS** tab and note this information:
    * The builder type is **Grunt**. The sample project uses JSHint validation to check its code for errors. For the validation to work, the repository must contain a Grunt build file and the build job must use Grunt. Every time a change is pushed to its repository, the project uses JSHint to make sure that the code is error-free.
    * Because the `app.js` file is located in the root of the project, you do not have to specify a working directory or a build archive directory.
    * If the build does not complete successfully, the stage stops running and any later jobs do not run.

  c. Because you did not make any changes, click **CANCEL** to return to the Build & Deploy Pipeline page.

![A configured builder stage][8]


The next stage is the Deploy stage; it contains a deploy job. Deploy jobs deploy your project to Bluemix. You can have many deploy jobs in a project, but in this tutorial, you need only one.

###Explore the deployment stage

0. On the Deploy stage tile, click the **Stage Configuration** icon <img class="inline" src="images/configure_stage.png" alt="The Stage Configuration icon"> and then click **Configure Stage**.

  a. On the **INPUT** tab, note this information: 
  * The input for the deployment is the output from the Build stage. 
  * The Deploy stage runs automatically every time the Build stage runs successfully. 
     ![The INPUT tab][46]

  b. Click the **JOBS** tab and note this information:
  * The app is set to deploy to your Bluemix organization and space.
  * Bluemix is based on Cloud Foundry, so the deployment script uses the Cloud Foundry command-line interface command `cf push` to deploy your app. To learn more about configuring deployment scripts when using Cloud Foundry, [see the Cloud Foundry documentation][29]. 

c. Because you did not make any changes, click **CANCEL** to return to the Build & Deploy Pipeline page.

![A configured deployer stage][9]

With these connected stages, you have a fully functional pipeline. By default, the changes that you push to the master branch will trigger new builds. Successful builds are deployed according to your deployment stage configuration. In this case, the builds are deployed when you manually run the deployment stage.


<a name='deploy_app'></a>
## Deploy the app and verify your change

It's time to see the stages in action. You can start a build without waiting for changes to be pushed.

1. On the Build stage tile, click the **Run Stage** icon <img  class="inline" src="/tutorials/devopsweb/images/run_stage.png" alt="The Run Stage icon">. The build is added to the queue, is run, and then is deployed to Bluemix.
2. After the deployment tile indicates that your app is running, in the LAST EXECUTION RESULT section, click the URL that is under the app name. Make sure that your topic is in the INPUT section.
3. If you want to see more information about your app, open its Bluemix Overview page by clicking the app's name, which is above the URL. For more information about the Overview page, [see Managing applications on Bluemix][28].

![The project's configured Pipeline][10]

Now that you’re familiar with the deployment process, return to the code editor, make another change, and push it to your project's repository. This practice is a good way to observe the automatic build and deployment capabilities in DevOps Services and become familiar with the interface. All you need to do is push a change. DevOps Services does the rest. To see the pipeline at work, click **BUILD & DEPLOY**.

<a name='work_item'></a>
## Complete the work item
When you're satisfied with your changes, close the task. 

1.	On the navigation bar at the top of the page, click **TRACK & PLAN**. 
2.	In the IN PROGRESS lane, find the task that you created earlier.
3.	Open the task in the work item editor by clicking the task's summary.
4.	Click the **LINKS** tab. Because you mentioned this task in your Git commit, DevOps Services linked your change to this work item automatically by using the commit ID.
5.	Return to the view that you started in by clicking **Back to My Work**. 
6.	Click the **Status** icon on the task. Select **Complete**. The task disappears.
7.	Scroll to the rightmost lane and verify that your newly resolved task is in the RESOLVED section.  

Well done! The Track & Plan service keeps administrative overheard to a minimum so that you can concentrate on development.

![A resolved work item][11]

<a name='summary'></a>
## Summary

You cloned a Node.js app project, planned and tracked an update to the app, made the update, and deployed the updated app to Bluemix--all without leaving your browser. 


<a name='next_steps'></a>
## Next steps
Now that you know the basics, you might want to explore this information:

- [Working locally with Bluemix DevOps Services projects][37]
- [Test and debug a Node.js app with Bluemix Live Sync][40]
- [Track and plan a Bluemix DevOps Services project][35] 
- [Build & Deploy (pipeline)][36]

[1]: https://bluemix.net/ (Bluemix)
[2]: https://hub.jazz.net/project/ibmdevopsservices/Sentiment%20Analysis%20App
[3]: /tutorials/devopsweb/images/forking.png
[4]: /tutorials/devopsweb/images/create_task.png
[5]: /tutorials/devopsweb/images/recent_task.png
[6]: /tutorials/devopsweb/images/edit_var.png
[7]: /tutorials/devopsweb/images/to_push.png
[8]: /tutorials/devopsweb/images/builder.png
[9]: /tutorials/devopsweb/images/deployer.png
[10]: /tutorials/devopsweb/images/configured_pipeline.png
[11]: /tutorials/devopsweb/images/resolved.png
[12]: /tutorials/devopsweb/images/start_working.png
[13]: /tutorials/devopsweb/images/about_to_commit.png
[14]: /tutorials/devopsweb/images/click_git.png
[20]: https://developer.ibm.com/answers/smartspace/devops-services/
[21]: mailto:hub%40jazz.net
[24]: http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html
[26]: https://www.ng.bluemix.net/docs/#services/DeliveryPipeline/index.html#getstartwithCD
[27]: http://sentiment-ua.mybluemix.net/
[28]: https://www.ng.bluemix.net/docs/manageapps/manageapps.html
[29]: http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html#push
[30]: https://hub.jazz.net/register
[31]: https://jazz.net/action/register
[32]: https://apps.admin.ibmcloud.com/manage/trial/bluemix.html
[33]: https://www.ng.bluemix.net/docs/#services/DeliveryPipeline/index.html#getstartwithCD
[34]: /docs
[35]: /tutorials/trackplan/
[36]: /docs/reference/deploy/
[37]: /tutorials/clients
[38]: /tutorials/devopsweb/images/displayAsLanes.png
[39]: /docs/reference/billing/
[40]: /tutorials/livesync
[41]: /tutorials/devopsweb/images/editcode.png
[42]: /tutorials/devopsweb/images/input_tab.png
[43]: /tutorials/devopsweb/images/run_stage.png
[44]: /tutorials/devopsweb/images/project_settings_icon.png
[45]: /tutorials/devopsweb/images/configure_stage.png
[46]: /tutorials/devopsweb/images/input_tab_deploy.png
