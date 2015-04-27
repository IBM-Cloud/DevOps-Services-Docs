#Developing Bluemix apps in Java with Eclipse and Bluemix DevOps Services


Last modified: 31 March 2015

Time: 30 minutes

Follow the steps in this tutorial to develop a Java&trade; application by using IBM&reg; Bluemix&trade;, IBM&reg; Bluemix&trade; DevOps Services, and the Rational Team Concert&trade; client for Eclipse. 

* [Learning objectives](#objectives)
* [Before you begin](#before_begin)
* [Fork a sample project](#fork_app)
* [Deploy your app](#deploy_app)
* [Add the Delivery Pipeline service](#add_pipeline)
* [Access your app from the Rational Team Concert client for Eclipse](#use_rtc)
* [Deliver your first change](#first_change)
* [Add a test failure](#test_failure)
* [Fix the bug](#fix_bug)
* [Summary](#summary)


---

<a name='objectives'></a>
##Learning objectives

* Create your own version of a DevOps Services project by forking it to your space.
* Create build and deployment stages by using the Build & Deploy feature.
* Open the project in Rational Team Concert.
* Make a code update and push it to the project repository by using Rational Team Concert.
* Verify automatic builds.
* Make a code update that causes a build failure to see how the build results look.


---


<a name='before_begin'></a>
##Before you begin

To complete this tutorial, you must [register with DevOps Services by creating an IBM ID, creating an alias, and registering with Bluemix](https://hub.jazz.net/register).

---

<a name='fork_app'></a>
##Fork a sample project

To quickly get started developing in Java, you fork a sample project named WordCounter. WordCounter uses Jazz&trade; source control management (SCM) and contains a manifest for deploying to Bluemix. You can load the project directly in the Rational Team Concert client for Eclipse. To explore the project before you fork it,  [see the WordCounter project page](https://hub.jazz.net/project/ibmdevopsservices/WordCounter/overview).


On the WordCounter project Overview page, click **FORK PROJECT**. 
![Click Fork Project](/tutorials/jazzrtc/images/click_fork_project.png "Click Fork Project")

When you are prompted, enter a unique name for your project. Then, click **CREATE**.
![Create Project Dialog](/tutorials/jazzrtc/images/create_project.png "Create Project Dialog")

A new project is created with a copy of the code from the sample project.

**Tip:** If you see an error message, [make sure you have a Bluemix account](//bluemix.net).

You're ready to build and deploy.

---
<a name='deploy_app'></a>
##Deploy your app

**Note**: When you build and deploy, your Bluemix account might be charged. For more information, [see the Bluemix Pricing page](https://bluemix.net/#/pricing).

1. Click **BUILD & DEPLOY**. 

3. On the Pipeline page, click **ADD STAGE**. The Stage Configuration page opens.
![Click Add A Builder](/tutorials/jazzrtc/images/add_builder.png "Click add a builder")

4. Create a stage to build your app:
    1. Click the default **MyStage** name and change the name of this stage to `Build`. 
    2. On the **INPUT** tab, use the default settings. Be sure to enter the password for your IBM id where indicated.  
	3. On the **JOBS** tab, click **ADD JOB**. Select **Build** and the select the **Ant** builder type.   
    4. In the **Working Directory** field, type the name of the folder that contains your code; which in this case is `WordCounter`. When the project is loaded in the Rational Team Concert client, this folder maps to an Eclipse project automatically.
    5. In the **Build Archive Directory** field, type the name of the directory where the build output files are archived as part of the build result; for example, `WordCounterArchive`.
    6. Select the **Enable unit tests** check box so that you can run the test cases during a build.
    7. Click **Save**.
![Add Builder](/tutorials/jazzrtc/images/configure_builder.png "Add Builder")

6. Click **ADD STAGE**. The Stage Configuration page opens.
![Click Add A New Stage](/tutorials/jazzrtc/images/add_deployer.png "Click add a new stage")

7.  Create a stage to deploy your app to Bluemix:
  1. Click the default **MyStage** name and change the name of this stage to `Deploy to dev`. 
  2. On the **INPUT** tab, use the default settings.
  3. On the **JOBS** tab, click **ADD JOB** and then select **Deploy**. This job uses the settings in the `manifest.yml` file, which is included as part of the sample project. You can use all of the values as provided, except for the hostname. The hostname is used to define your app's URL and must be unique for each app that is deployed on Bluemix.
      4. Override the hostname with the `-n` option in the cf push command, as shown in the following image.
     **Tip:** Use a combination of your user name and the date or time to ensure that your route is unique.
  5. Click **SAVE**.
![Add Deployer](/tutorials/jazzrtc/images/configure_deployer.png "Add Deployer")

9. At the top of the Build stage, click the **Play** icon to build and deploy your project for the first time. The build process takes a couple of minutes. When you see a green circle, the app is live. 
![Successful Build](/tutorials/jazzrtc/images/build1_success.png "Successful Build")

10. Verify that the app is running by clicking the app link.
![Application](/tutorials/jazzrtc/images/app.png "Application")

---
<a name='add_pipeline'></a>
##Add the Delivery Pipeline service

To track charges, after you deploy your first build, add the Delivery Pipeline service to your Bluemix space.  

1. Click the running instance of you app to view it in Bluemix. If prompted, enter your IBM id and password.
![Bluemix Instance](/tutorials/jazzrtc/images/running_instance.png "Bluemix Instance")

2. On the new app's Overview page, click **ADD A SERVICE OR API**.

3. Select the DevOps category, then click **Delivery Pipeline**.

4. Leave the settings for Space and App as they are. Click **CREATE**.

The Delivery Pipeline service is added to your Bluemix space. 

---
<a name='use_rtc'></a>
##Access your app from the Rational Team Concert client for Eclipse

From the Rational Team Concert client for Eclipse, connect to your running app. 

1. In the DevOps Services Web IDE, click the project link to go to the project Overview page. 
![Project Link](/tutorials/jazzrtc/images/project_link.png "Project Link")

2. From this page, get the Jazz repository information. 
![Team Invitation](/tutorials/jazzrtc/images/team_invite.png "Team Invitation")

3. In the Rational Team Concert client for Eclipse, connect to your project and load the code. For detailed instructions, [see Setting up local Eclipse clients to work with Jazz source control](/docs/reference/jazz_scm_client).				

---
<a name='first_change'></a>
##Deliver your first change

When you're in the Rational Team Concert client for Eclipse, change your code then verify that the change is shown in the running app.

1. On line 10 of `index.html`, change the app name.
![Edit Code](/tutorials/jazzrtc/images/edit_code.png "Edit Code")

2. Deliver the change to the Jazz SCM repository:

	a. In the Pending Changes view, check in the change in a new change set.
	![Check In Change](/tutorials/jazzrtc/images/checkin.png "Check In Change")

	b. If necessary, you can edit the comment for the change set.
	![Edit Change Set Comment](/tutorials/jazzrtc/images/edit_comment.png "Edit Change Set Comment")
	
	c. Deliver the change. 
	![Deliver Change Set](/tutorials/jazzrtc/images/deliver.png "Deliver Change Set")

3. In a browser, go to the deployment page. A build is triggered soon and the page is updated automatically. Wait until the app status is green.
![Successful Build](/tutorials/jazzrtc/images/build2_success.png "Successful Build")

4. Click the app link and verify that the app name is updated.
![Application](/tutorials/jazzrtc/images/app2.png "Application") 

---
<a name='test_failure'></a>
##Add a test failure

To see what happens when the build fails, add a failure to the JUnit tests. 

1. In the `WordCounterFinderTest.java` file, on line 26, set `this.wcFinder` to null.
![Edit Test Case](/tutorials/jazzrtc/images/edit_testcase.png "Edit Test Case")

2. In the `index.html` file, on line 10, change the app name. 
![Edit App Name Again](/tutorials/jazzrtc/images/edit_code_2.png "Edit App Name Again")

3. Deliver the changes. DevOps Services shows a failed build, as you expected. The Build stage could not complete. Only successful builds are deployed automatically. When you click the app link, the app name is not updated.
![Failed Build](/tutorials/jazzrtc/images/build3_failure.png "Failed Build")

4. Access the build logs and test results by clicking the build.
![Click Build](/tutorials/jazzrtc/images/build_log.png "Click Build")

---
<a name='fix_bug'></a>
##Fix the bug

1. Revert the code in `WordCounterFinderTest.java` to its previous state and deliver the change.
![Fix Test Case](/tutorials/jazzrtc/images/fix_testcase.png "Fix Test Case")

2. Verify that the build is now green.
![Successful Build](/tutorials/jazzrtc/images/build4_success.png "Successful Build")

3. Verify that the app is running, too.
![Application](/tutorials/jazzrtc/images/app3.png "Application")
	

---
<a name='summary'></a>
##Summary
You finished this tutorial. You are ready to develop Java applications on your own. 
