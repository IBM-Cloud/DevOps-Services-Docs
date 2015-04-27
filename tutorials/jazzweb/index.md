#Develop a Bluemix app in Node.js using the Web IDE

Last modified: 31 March 2015

Time: 30 minutes

In this tutorial, you use IBM® Bluemix™ DevOps Services to develop an app in the cloud and deploy it to [IBM® Bluemix™][1].

* [Learning objectives](#objectives)
* [Before you begin](#prereq)
* [Explore and clone the sample project](#fork)
* [Understand builds and deployments](#deploy)
* [Edit the sample app](#edit)
* [Deploy your workspace contents by using the Web IDE](#deploy_from_web_ide)
* [Push changes to the repository](#push)
* [Verify changes](#automatic_deployment)
* [Summary](#summary)


---
<a name='objectives'></a>
##Learning objectives

* Create your own version of a DevOps Services project by cloning it in your space.
* Create build and deployment stages by using the Build & Deploy feature.
* Make a code update and push it to the project repository by using the Web IDE.
* Deploy the app by using the run bar in the Web IDE.

---

<a name='prereq'></a>
##Before you begin

To complete this tutorial, you must [register with DevOps Services by creating an IBM ID, creating an alias, and registering with Bluemix](https://hub.jazz.net/register).

---
<a name='fork'></a>
##Explore and clone the sample project

Start by [exploring the live version of the sample project you will work with][27]. The app analyzes Twitter users' collective sentiment about a search phrase. 

Next, explore the contents of the  [Sentiment Analysis project][2]. This Node.js app uses a Git repository, and includes a Grunt build file.

After you are familiar with the project, click the button below to create your own copy of it by cloning and deploying it:

<a target="_blank" href="https://bluemix.net/deploy?repository=https://hub.jazz.net/git/ibmdevopsservices/Sentiment.Analysis.App"><img src="images/bigButton.png" alt="Deploy to Bluemix"></a>

After the project is cloned and the deployment is complete, click **EDIT CODE** to continue.

---

<a name='deploy'></a>
## Understand builds and deployments

When you clone a project by clicking the **Deploy to Bluemix** button, the Build & Deploy configuration is created for your project automatically. In this section, you will explore how the preconfigured stages work.

The Delivery Pipeline configuration for your Sentiment Analysis app has two stages: a build stage and a deploy stage. These stages form a pipeline. The build stage runs a build job on the included `Gruntfile.js` to validate your code. Then, the deploy stage runs a deploy job to deploy your code to Bluemix.

**Important:** When you use the Build & Deploy feature with Bluemix, you can generate charges to your Bluemix account. However, you can complete this tutorial for free because a project is granted 60 minutes of free build time per month. For more information about Bluemix, DevOps Services, and charges, [see Configure Bluemix billing for Bluemix DevOps Services](/docs/reference/billing/).


1. On the top navigation bar, click **BUILD & DEPLOY**. 

2. On the Build Stage tile, click the gear icon and **Configure stage**.  
  
  a. Click the **INPUT** tab and note the following items:
  
    * The input for the build is the master branch of the SCM repository. 
    * The Build Stage runs automatically every time a change is pushed to the repository. 
  
  b. Click the **JOBS** tab and note the following items:
  
    * The builder type is **Grunt**. The sample project uses JSHint validation to check its code for errors. For the validation to work, the repository must contain a Grunt build file and the build job must use Grunt. Every time a change is pushed to its repository, the project uses JSHint to make sure that the code is error-free.
    * Since the `app.js` file is located in the root of the project, you do not have to specify a Working Directory or a Build Archive Directory.
    
    * If the build does not complete successfully, the stage stops running and any later jobs do not run.
  
  c. Since you did not make any changes, click **DISCARD CHANGES** to return to the BUILD & DEPLOY page.

	![Configuring the Builder][8]

The next stage contains a deploy job. Deploy jobs deploy your project to Bluemix. You can have many deploy jobs in a project, but in this tutorial, you need only one:

0. On the Deploy Stage tile, click the gear icon and **Configure stage**.

  a. Click the **INPUT** tab and note the following items: 
  
     * The input for the build is the output from the Build stage. 
     * The Deploy Stage runs automatically every time a the Build stage runs successfully. 
 
  b. Click the **JOBS** tab and note the following items:
  
     * The app is set to deploy to your Bluemix organization and space.
     * Bluemix is based on Cloud Foundry, so the deployment script uses the Cloud Foundry command-line interface command cf push to deploy your app. To learn more about configuring deployment scripts when using Cloud Foundry [see the Cloud Foundry documentation][29].

  c. Since you did not make any changes, click **DISCARD CHANGES** to return to the BUILD & DEPLOY page.

![Configuring the Deployer][9]

7. To test the configuration, on the Pipeline page, click the **Play** icon at the top of the Build Stage.

	![Clicking Request Build on configured Pipeline][23]

	Your project is queued to build. When the build is completed, your app is queued for deployment to Bluemix automatically. You can observe its status from this page and open the app when it is deployed.

8. To open the app, click its URL on the Deploy Stage tile. If you want to see your app's Bluemix Dashboard, click its name:

![Ready to click to Bluemix from Pipeline][10]

You can manage the live app instance on the [Bluemix Dashboard][11]. From the Dashboard, you can start, stop, edit, or delete the app. On the Services page, you can add various services such as MongoDB, SSO, MapReduce, and more.
 

![Starting a Bluemix app][12]

---
<a name='edit'></a>
##Edit the sample app

You can now personalize the sample app in the DevOps Services web-based code editor, push your changes to the project's remote repository, and initiate a redeployment of your project. These activities won’t take more than a few minutes.

1. Click **Edit Code**, and then open the `app.js` file by clicking it in the side panel. The editor recognizes and highlights the code as JavaScript.

2. Change how the app greets its users: click **Edit**, and then click **Find**. Search for the phrase "Welcome to the Twitter Sentiment Analysis app."

	![Configure Builder][13]

3. Replace occurrences of that message with whatever you like.

4. If you want a fully functional version of the app, you must supply your own Twitter API keys. To sign up for API keys, [go to Twitter Application Management][27]. When you have the API keys, you can replace the keys that are in the tweeter variable, which starts at line 22. 

5. When you're finished, save your work by pressing Ctrl+S (or Command+S on a Mac).

---

<a name='deploy_from_web_ide'></a>
##Deploy your workspace contents by using the Web IDE

While you're working in the directory that contains your `manifest.yml file`, you can manually deploy whatever is in the Web IDE workspace to Bluemix by clicking Play on the run bar. **Remember:** When you deploy by using the run bar, you deploy the current state of your code in the Web IDE. When you deploy by using the Build &amp; Deploy feature, you deploy the code that is checked into the repository.

![The IDE Run bar][28]

You can configure Web IDE deployment and the Delivery Pipeline service to use different app names. Then, you can use the Web IDE deployment for a personal test environment and the Delivery Pipeline deployment for a team integration environment. The Web IDE saves launch configurations; you can access them from the menu on the run bar. 

Whether you are using command-line tools or the Web IDE, both methods are effective for rapid, solo development. You might prefer the added security of using auto-deploy so that you can control what is being pushed. Auto-deploy is available through the Delivery Pipeline service. By using auto-deploy, you know that the code that is running in the app matches a known state in the repository. In contrast, the Web IDE deploys whatever is in your working directory when you push.


---
<a name='push'></a>
##Push changes to the repository

After you edit the `app.js` file, share the changed file with other members of your project by pushing the file to the repository. 

1. In the sidebar, click the Git Repository icon. 
2. Stage the change to `app.js` by selecting the check box next to it.

	![Stage Changes][14]

3. Commit your change to the Git repository for your project by entering a commit message, and then clicking **COMMIT**.

	![Committing changes][15]

4. Push the change to the remote project repository by clicking **PUSH**.

![Pushing Changes][16]

Any changes that are delivered to your project trigger a build. When a build is completed successfully, it is auto-deployed. If you click **BUILD &amp; DEPLOY** again, you'll see that your change started a new build that will be deployed when the build is finished.


---
<a name='automatic_deployment'></a>
##Verify changes


When the app is deployed, try it by clicking its web URL:

![Our updated app on Bluemix][19]

---
<a name='summary'></a>
##Summary

You developed and deployed a Bluemix app by using the Web IDE. 

[1]: https://bluemix.net/ (Bluemix)
[2]: https://hub.jazz.net/project/ibmdevopsservices/Sentiment%20Analysis%20App/overview
[3]: /tutorials/jazzweb/images/forkbutton.png
[4]: /tutorials/jazzweb/images/forknew.png
[5]: /tutorials/jazzweb/images/simpledeployment.png
[6]: /tutorials/jazzweb/images/closedeploy.png
[7]: /tutorials/jazzweb/images/stockapp.png
[8]: /tutorials/jazzweb/images/builder1.png
[9]: /tutorials/jazzweb/images/deployscriptex.png
[10]: /tutorials/jazzweb/images/click2blue.png
[11]: https://bluemix.net
[12]: /tutorials/jazzweb/images/startappbluemix.png
[13]: /tutorials/jazzweb/images/autocompletesearch.png
[14]: /tutorials/jazzweb/images/staging.png
[15]: /tutorials/jazzweb/images/commit.png
[16]: /tutorials/jazzweb/images/pushing.png
[17]: /tutorials/jazzweb/images/manifest.png
[18]: /tutorials/jazzweb/images/manualdeploy.png
[19]: /tutorials/jazzweb/images/updatedapp.png
[20]: https://www.ibmdw.net/answers?community=jazzhub (forum)
[21]: mailto:hub%40jazz.net
[22]: /tutorials/jazzweb/images/deployto.png
[23]: /tutorials/jazzweb/images/request-build.png  
[24]: http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html
[25]: /tutorials/jazzweb/images/config-to-delete.png
[26]: https://www.ng.bluemix.net/docs/#services/DeliveryPipeline/index.html#getstartwithCD
[27]: https://dev.twitter.com/apps
[28]: /tutorials/jazzweb/images/runbar_green.png
[29]: http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html#push