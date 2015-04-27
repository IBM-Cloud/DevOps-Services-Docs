#Get started with Bluemix and Bluemix DevOps Services using Java

Last modified: 31 March 2015

Time: 30 minutes

* [Learning objectives](#objectives)
* [Before you begin](#prereq)
* [Create an app with Bluemix](#create_bluemix_app)
* [Push changes to the Git repository by using the command line](#push)
* [Explore builds and deployments](#build_and_deploy)
* [Summary](#summary)
* [Next steps](#next_steps)


---
<a name='objectives'></a>
##Learning objectives

* Create an app in IBM&reg; Bluemix&trade; by using the Liberty for Java&trade; starter pack.
* Create a Git repository for the app.
* Add the IBM Continuous Delivery Pipeline for Bluemix (the Delivery Pipeline service).
* Push changes to the Git repository from the command line.
* Build and deploy your changes by using the Delivery Pipeline service.

---

<a name='prereq'></a>
##Before you begin

[Sign up for IBM&reg; Bluemix&trade; DevOps Services](https://hub.jazz.net/register). When you sign up, you'll create an IBM id, create an alias, and register with Bluemix. 

---
<a name='create_bluemix_app'></a>
##Create an app with Bluemix

Bluemix is an open-standard, cloud-based platform for building, managing and running apps of all types, including web, mobile, big data, and smart devices. The Bluemix capabilities include Java™, mobile back-end development, app monitoring, and capabilities from ecosystem partners and open source, all through an as-a-service model in the cloud.

To start working, [sign in to Bluemix][1]!

![Bluemix Dashboard][6]

The Dashboard shows an overview of the active Bluemix space for your organization. By default, the space is `dev` and the organization is the project creator's user name. For example, if `sara@example.com` signs in to Bluemix for the first time, the active space is `dev` and the organization is `sara@example.com`.

If you create other organizations or spaces in Bluemix, be sure to use the default selections as you follow the tutorial. 

###Create the app
1. Click **CREATE AN APP**.

2. Select **WEB** for the type of app you are creating.

3. On the next page, click **Liberty for Java**, and then click **CONTINUE**. 
![Bluemix Java Web Starter][7]

4. Type a unique name for your app, such as `Liberty for Java Starter app tutorial <your initials>`.

5. Click **Finish**. In a few moments, when the app finishes staging, you'll have a Java web server app instance running on Bluemix.
![Naming a Bluemix app][54]

5. Click **Overview** to view information about your app:
![The new app's Bluemix Dashboard][55]

6. Click the URL on the app Dashboard to access the running Starter app:
![A running web application][10]

###Create a Git repository and enable auto-deploy

Although it's great that the app is running, you will want to modify it to make it more interesting.  

You can work with your app code in many ways. For example, with auto-deploy, you can modify the code that runs in your app by pushing the changes to a Git repository. The mechanism that implements auto-deploy is provided by  DevOps Services, but more about that later.

1. On your app’s Overview page, click **ADD GIT**. You might be prompted to enter your password because DevOps Services must verify that it can act on your behalf.
![Add Git][11]

2. Select the **Populate the repository with the starter application package and enable Delivery Pipeline (Build & Deploy)** check box. 
![Create Git repo dialog][13]

3. Click **CONTINUE**, and then **CLOSE**. A message states that you successfully created a Git repository and loaded it with the app starter code.

###Optional: Add the Delivery Pipeline to your space
Add the IBM Continuous Delivery Pipeline for Bluemix service to your Bluemix space so you can continue to use it beyond the free monthly build time.  

1.	On the app’s Overview page, click **ADD A SERVICE OR API**.
2.	Select the DevOps category, and then click **Delivery Pipeline**. 
3.	Select the space that the app you created is in and use the default settings for the selected plan.
4.	Click **CREATE**. The Delivery Pipeline service is added to your Bluemix space. You can view a list of the apps that include the service. 
5. Click **Back to Dashboard** and click the app tile for the app you just created.

Next, start using DevOps Services. Click **EDIT CODE**.

![CODE button][15]

Your project opens in the DevOps Services Web IDE (integrated development environment). When you clicked **ADD GIT** in Bluemix, a new Git repository was populated with sample code. When you clicked **EDIT CODE**, the sample code was loaded into this work area associated with the project, called the project workspace.


---

<a name='push'></a>
##Push changes to the Git repository by using the command line

You now have a Git repository with sample code. You can use the command-line Git support to push files from your computer to the repository.

**Note:** If you don't have Git installed, [see Working locally with Bluemix DevOps Services projects][20]. If you want to learn more about working with Git, [see the Git documentation pages](http://git-scm.com/doc).

1. Clone from the project repository URL, which you can find on the Bluemix app's Overview page or the project's Overview on DevOps Services:

    	$ git clone https://hub.jazz.net/git/jazzhubdemouser/Liberty.for.Java.Starter.app.tutorial
    	Cloning into 'Liberty.for.Java.Starter.app.tutorial'...
    	Username for 'https://hub.jazz.net': <username>
    	Password for 'https://<username>@hub.jazz.net': <password>
    	remote: Counting objects: 49, done
	    remote: Finding sources: 100% (49/49)
    	remote: Total 49 (delta 0), reused 49 (delta 0)
    	Unpacking objects: 100% (49/49), done.
    	Checking connectivity... done. 

2. To make changes to your app source code, change to the `WebContent` folder in the app's root directory, and open the file `index.html`. 

3. Change some text in the body of the HTML.  

4. Change to your project directory and `git stage`, `git commit`, and `git push`:
 
    	$ cd /project_directory
    	$ git stage Webcontent/index.html
    	$ git commit -m "Sample app headline change"
    	[master 2336018] Sample app headline change
    	1 file changed, 1 insertion(+), 1 deletion(-)
    	
    	$ git push
    	Username for 'https://hub.jazz.net': <username>
    	Password for 'https://<username>@hub.jazz.net':
    	Counting objects: 8, done.
    	Delta compression using up to 4 threads.
	    Compressing objects: 100% (4/4), done.
    	Writing objects: 100% (4/4), 382 bytes | 0 bytes/s, done.
    	Total 4 (delta 3), reused 0 (delta 0)
    	remote: Resolving deltas: 100% (3/3)
    	remote: Processing changes: refs: 1, done
    	To https://hub.jazz.net/git/jazzhubdemouser/Liberty.for.Java.Starter.app.tutorial
    	ab4aaad..2336018 master -> master

5. In DevOps Services, click **BUILD &amp; DEPLOY**. You can see that a new build was requested when changes were pushed to the repository. It is automatically triggered by the changes that you delivered to the project repository. When the build is finished, it is deployed to Bluemix. When the instance is running, you can view your updated app on the web. 

You can continue to modify the example and push your changes to the Git repository as often as needed. As the scope of the work grows and more people are added to the project, everyone can push changes to the repository. Standard repository operations and build and deploy are all that is required to ensure that the right bits are always running.

If you want to configure desktop clients to work with your Git repository, [see Working locally with Bluemix DevOps Services projects][26].



---
<a name='build_and_deploy'></a>
##Explore builds and deployments

On the **BUILD & DEPLOY** Pipeline page, run your build by clicking the **Run Stage** icon in the Build Stage tile. 

![Play button][57]

The build stage begins running. The deploy stage is configured to auto-deploy your app after the completion of a  successful build stage. 
When the app is running, it is available at the URL shown on the Deploy stage tile. You can see the app's Overview page on Bluemix by clicking the last execution result, that shows the app's name.

![Bluemix DevOps Services autoconfigured Pipeline][17]

Your sample project is configured to automatically build and deploy the Liberty for Java sample app. You can explore the preconfigured stages or make changes to the configurations.

### Explore the preconfigured stages

The Delivery Pipeline configuration for your app has two stages: a build stage and a deploy stage. These stages form a pipeline. The build stage runs a build job on the included `build.xml` . Then, the deploy stage runs a deploy job to deploy your code to Bluemix.

**Important:** When you use the Build & Deploy feature with Bluemix, you can generate charges to your Bluemix account. However, you can complete this tutorial for free because a project is granted 60 minutes of free build time per month. For more information about Bluemix, DevOps Services, and charges, [see Configure Bluemix billing for Bluemix DevOps Services][58].


####Explore the build stage

1. On the top navigation bar, click **BUILD & DEPLOY**. 

2. On the Build Stage tile, click the gear icon and **Configure stage**.  
  
  a. Click the **INPUT** tab and note the following items:
  
    * The input for the build is the master branch of the Git repository. 
    * The Build Stage runs automatically every time a change is pushed to the repository. 
  
  b. Click the **JOBS** tab and note the following items:
  
    * The builder type is **Ant**. The ant command will find the default build script file, `build.xml`, which is provided in the sample at the root directory.
    * Because the `build.xml` file is located in the root of the project, you do not have to specify a working directory.
    * The build output will be saved in an `output` directory, as specified in the **Build Archive Directory** field. The files that are needed for deployment are copied into the build archive directory.
    * If the build does not complete successfully, the stage stops running and any later jobs do not run.
  
  c. Because you did not make any changes, click **DISCARD CHANGES** to return to the BUILD & DEPLOY Pipeline page.
![Configuring the Builder][18]

3. At the top of the Build stage tile, click the **Play** icon. After a moment, you have a successful build.
![A configured Builder panel with a successful build][47]


####Explore the deploy stage

0. On the Deploy Stage tile, click the gear icon and **Configure stage**.

  a. Click the **INPUT** tab and note the following items: 
  
     * The input for the build is the output from the Build stage. 
     * The Deploy Stage runs automatically every time the Build stage runs successfully. 
 
  b. Click the **JOBS** tab and note the following items:
  
     * The app is set to deploy to your Bluemix organization and space.
     * Bluemix is based on Cloud Foundry, so the deployment script uses the Cloud Foundry command-line interface command `cf push` to deploy your app. To learn more about configuring deployment scripts when using Cloud Foundry, [see the Cloud Foundry documentation][59].

  c. Because you did not make any changes, click **DISCARD CHANGES** to return to the BUILD & DEPLOY Pipeline page.


![Configuring the Deployer with the Add Deployer Stage screen][19]


Because you selected the **Automatically execute jobs when the previous stage completes successfully** option when you set up the deploy stage, successful builds of your app are deployed automatically. If you did not have this option selected, you could start a deployment by dragging a build to a stage with a deploy job. In the LAST EXECUTION RESULT section of the Build tile, drag the build to the Deploy stage, as shown below. You could also click the **Play** button in the Deploy stage to start the deployment. In a few moments, your app is deployed to Bluemix. 

![Dropping to deploy][49]

To view your app on the web, in the Deploy Stage, click the URL under the LAST EXECUTION RESULT heading. If you already had the app open in a browser window, refresh the page. To view your app’s Bluemix Dashboard, click its the tile where the app name is displayed. 

![Our really cool app][36]


---
<a name='Summary'></a>
## Summary

In this tutorial, you learned to create and run a Java web app using Bluemix. 


---
<a name='next_ steps'></a>
## Next steps

[Learn more about Bluemix at IBM Bluemix Docs][53]. 

To learn more about configuring Eclipse or other desktop clients to work with your Git repository, [see Working locally with Bluemix DevOps Services projects][26].

To learn about how to integrate unit testing into your DevOps Services projects, [see Developing Bluemix apps in Java with Eclipse and Bluemix DevOps Services][40].

   [1]: https://bluemix.net/ (Bluemix)
   [2]: /tutorials/jazzeditorjava/images/bm-join.png
   [3]: https://bluemix.net/docs/QuickStart.jsp (Bluemix getting started)
   [4]: https://bluemix.net/docs/BlueMixIntro.jsp (Bluemix overview)
   [5]: https://bluemix.net/docs/Tutorials.jsp (Bluemix tutorials)
   [6]: /tutorials/jazzeditorjava/images/demo-dash.png 
   [7]: /tutorials/jazzeditorjava/images/bm-java-starter.png 
   [8]: /tutorials/jazzeditorjava/images/create-jws-app.png 
   [9]: /tutorials/jazzeditorjava/images/examplepanel.gif 
   [10]: /tutorials/jazzeditorjava/images/bm-example.png 
   [11]: /tutorials/jazzeditorjava/images/addgitintegration.png
   [12]: /tutorials/jazzeditorjava/images/jh-signin.gif 
   [13]: /tutorials/jazzeditorjava/images/bm-create-git-repo.png
   [14]: /tutorials/jazzeditorjava/images/bm-git-repo-success-msg.png 
   [15]: /tutorials/jazzeditorjava/images/bm-code-button.png 
   [16]: /tutorials/jazzeditorjava/images/webide.gif 
   [17]: /tutorials/jazzeditorjava/images/simpledeploy2.png
   [18]: /tutorials/jazzeditorjava/images/configbuilder.png 
   [19]: /tutorials/jazzeditorjava/images/deployer.png 
   [20]: /tutorials/clients (Setting up Eclipse, Git, and Rational Team Concert Desktop Clients for use with Bluemix DevOps Services)
   [21]: /tutorials/jazzeditorjava/images/cli-git-clone.gif 
   [22]: /tutorials/jazzeditorjava/images/cli-stage-commit.gif 
   [23]: /tutorials/jazzeditorjava/images/cli-push.gif 
   [24]: /tutorials/jazzeditorjava/images/autodeploy.gif 
   [25]: /tutorials/jazzeditorjava/images/app-new-title.png 
   [26]: /tutorials/clients (Setting up Eclipse, Git, and Rational Team Concert Desktop Clients for use with Bluemix DevOps Services)
   [27]: https://hub.jazz.net/learn (Bluemix DevOps Services introduction)
   [28]: http://orion.eclipse.org/ (The Eclipse Orion project)
   [29]: /tutorials/jazzeditorjava/images/orion.png
   [30]: /tutorials/jazzeditorjava/images/completion.png 
   [31]: /tutorials/jazzeditorjava/images/heyworld.png 
   [32]: /tutorials/jazzeditorjava/images/orion-git-status.png 
   [33]: /tutorials/jazzeditorjava/images/unstaged.png 
   [34]: /tutorials/jazzeditorjava/images/commit.png
   [35]: /tutorials/jazzeditorjava/images/push.png 
   [36]: /tutorials/jazzeditorjava/images/endexampleapp.png 
   [37]: /tutorials/jazzeditorjava/images/manualdeploy.png
   [38]: https://www.ibmdw.net/answers?community=jazzhub (forum)
   [39]: mailto:hub%40jazz.net
   [40]: /tutorials/jazzrtc (Developing Bluemix apps in Java with Eclipse and Bluemix DevOps Services)
   [41]: /tutorials/jazzeditor (Getting Started with Bluemix and Bluemix DevOps Services using Node.js)
   [42]: /tutorials/clients (Setting up Eclipse, Git, and Rational Team Concert Desktop Clients to access Bluemix DevOps Services)
   [43]: /tutorials/jazzweb (Developing Bluemix applications in Node.js with the Bluemix DevOps Services Web IDE)
   [44]: /tutorials/jazzeditorjava/images/panel_gear.gif
   [45]: /tutorials/jazzeditorjava/images/un-pipeline.png
   [46]: /tutorials/jazzeditorjava/images/configured-builder.png
   [47]: /tutorials/jazzeditorjava/images/configured-and-built.png
   [48]: /tutorials/jazzeditorjava/images/configured-pipeline.png
   [49]: /tutorials/jazzeditorjava/images/drop-to-deploy.png
   [50]: /tutorials/jazzeditorjava/images/deployed-with-pipeline.png
   [51]: /tutorials/jazzeditorjava/images/click-to-open.gif
   [52]: /tutorials/jazzeditorjava/images/config-to-delete.png
   [53]: https://www.ng.bluemix.net/docs/#
   [54]: /tutorials/jazzeditorjava/images/bm-name-app.png
   [55]: /tutorials/jazzeditorjava/images/bm-web-starter.png
   [56]: /tutorials/jazzeditorjava/images/runbar_green.png
   [57]: /tutorials/jazzeditorjava/images/playbutton.png
   [58]: /docs/reference/billing/
   [59]: http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html#push