#Develop and deploy a Java app

###### Last updated: 1 February 2016

Time: 30 minutes

IBM&reg; Bluemix&trade; is an open-standards, cloud-based platform where you can build, manage, and run all types
of apps: mobile, smart devices, web, and big data. The Bluemix capabilities include Java&trade;, mobile back-end development, app monitoring, and features from ecosystem partners and open source, all through an as-a-service model in the cloud.

In this tutorial, you create an app in Bluemix by using the Liberty for Java&trade; starter pack. You then create a Git repository for the app and add the IBM Continuous Delivery Pipeline for Bluemix (the Delivery Pipeline service). After you make a change or two to your code, you push the changes to the Git repo from the command line. Then, you build and deploy your app by using the Delivery Pipeline service.


<div class="table-of-contents">
 <table>
   <tr>
     <td colspan="6"><h4>Summary of steps</h4></td>
   </tr>
   <tr>
     <td><a href="#prereq>">Before you begin</a></td>
     <td><a href="#create_bluemix_app">Create an app by using Bluemix</a></td>
     <td><a href="#push">Push changes to the Git repository by using the command line</a></td>
     <td><a href="#build_and_deploy">Explore builds and deployments</a></td>
     <td><a href="#summary">Summary</a></td>
     <td><a href="#next_steps">Next steps</a></td>
   </tr>
 </table>
</div>


<a name='prereq'></a>
##Before you begin

To do this tutorial, you need a Bluemix account. Bluemix accounts provide access to everything you need to develop, track, plan, and deploy apps. You can sign up for a free 30-day trial. 

<h5> </h5>
<div class="container-fluid small_bottom_space">
   <div class="row pbl button-links" id="overview-links">
		<a href="https://login.jazz.net/psso/proxy/jazzregister?redirect_uri=https%3A%2F%2Fhub.jazz.net%2F" target="_blank" alt-text="Sign up"> 
			<div class="hollowButton">SIGN UP<div class="extra-title">for Bluemix </div>
			</div>
		</a>
   </div>
</div>
<a name='create_bluemix_app'></a>
##Create an app in Bluemix

[Sign in to Bluemix][1].

![Bluemix Dashboard][6]

The Dashboard shows an overview of the active Bluemix space for your organization. By default, the space is `dev` and the organization is the project creator's user name. For example, if `sara@example.com` signs in to Bluemix for the first time, the active space is `dev` and the organization is `sara@example.com`.

If you create other organizations or spaces in Bluemix, be sure to use the default selections as you follow the tutorial. 

###Create the app
1. Click **CREATE AN APP**.

2. For the type of app, select **WEB**.

3. On the next page, click **Liberty for Java**, and then click **CONTINUE**. 
![Bluemix Java Web Starter][7]

4. Type a unique name for your app, such as `Liberty for Java Starter app tutorial <your initials>`.

5. Click **Finish**. In a few moments, when the app is staged, you'll have a Java web server app running on Bluemix.
![Naming a Bluemix app][54]

5. Click **Overview** to view information about your app:
![The new app's Bluemix Dashboard][55]

6. Click the URL on the app's Dashboard to access the running Starter app:
![A running web application][10]

###Create a Git repository and enable auto-deploy

It's great that the app is running, but you want to make it more interesting.  

You can work with your app code in many ways. For example, with auto-deploy, you can modify the code that runs in your app by pushing the changes to a Git repository. The mechanism that implements auto-deploy is provided by DevOps Services. You'll learn more about that later.

1. On your app’s Overview page, click **ADD GIT**. You might be prompted to enter your password because DevOps Services must verify that it can act on your behalf.
![Add Git][11]

2. Select the **Populate the repository with the starter application package and enable Delivery Pipeline (Build & Deploy)** check box. 
![Create Git repo dialog][13]

3. Click **CONTINUE**, and then click **CLOSE**. A message states that you created a Git repository and loaded it with the app starter code.

###Optional: Add the Delivery Pipeline service to your space

1.	On the app’s Overview page, click **ADD A SERVICE OR API**.
2.	Select the DevOps category, and then click **Delivery Pipeline**. 
3.	Select the space that your app is in. Use the default settings for the selected plan.
4.	Click **CREATE**. The Delivery Pipeline service is added to your Bluemix space. You can view a list of the apps that include the service. 
5. Click **Back to Dashboard** and click the app tile for the app you just created.

###Start using DevOps Services

Click **EDIT CODE**.

![CODE button][15]

Your project opens in the DevOps Services Web IDE (integrated development environment). When you clicked **ADD GIT** in Bluemix, a new Git repository was populated with sample code. When you clicked **EDIT CODE**, the sample code was loaded into this work area associated with the project, which is the project workspace.


<a name='push'></a>
##Push changes to the Git repository by using the command line

You now have a Git repository with sample code. You can use the command-line Git support to push files from your computer to the repository.

If you don't have Git installed, [see Working locally with Bluemix DevOps Services projects][20]. To learn more about Git, [see the Git documentation](http://git-scm.com/doc).

1. Clone from the project repository URL, which you can find on the Bluemix app's Overview page or the project's Overview page in DevOps Services:

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

3. Change some of the text in the body of the HTML.  

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

5. In DevOps Services, click **BUILD &amp; DEPLOY**. You can see that a new build was requested when changes were pushed to the repository. The build is automatically triggered by the changes that you delivered to the project repository. When the build is finished, it is deployed to Bluemix. When the instance is running, you can view your updated app on the web. 

You can continue to modify the example and push your changes to the Git repository as often as needed. As the scope of the work grows and more people are added to the project, everyone can push changes to the repository. Standard repository operations and build and deploy are all that is required to ensure that the right bits are always running.

If you want to configure desktop clients to work with your Git repository, [see Working locally with Bluemix DevOps Services projects][26].



<a name='build_and_deploy'></a>
##Explore builds and deployments

On the Build & Deploy Pipeline page, run your build by clicking the **Run Stage** icon <img  class="inline" src="images/run_stage.gif" alt="Run Stage icon"> on the Build Stage tile. 

The build stage begins running. The deploy stage is configured to auto-deploy your app after the completion of a  successful build stage. 

When the app is running, you can view it by clicking the URL on the Deploy Stage tile. To see the app's Overview page on Bluemix, click the last execution result that shows the app's name.

![Bluemix DevOps Services autoconfigured Pipeline][17]

Your sample project is configured to automatically build and deploy the Liberty for Java sample app. You can explore the preconfigured stages or make changes to the configurations.

### Explore the preconfigured stages

The Delivery Pipeline configuration for your app has two stages: a build stage and a deploy stage. These stages form a pipeline. The build stage runs a build job on the included `build.xml`. Then, the deploy stage runs a deploy job to deploy your code to Bluemix.

####Explore the build stage

1. In the upper-right corner, click **BUILD & DEPLOY**. 

2. On the Build Stage tile, click the **Stage Configuration** icon <img class="inline"  src="images/configure_stage.gif" alt="Stage Configuration icon"> and click **Configure stage**.  
  
  a. Click the **INPUT** tab and review the settings:
  
    * The input for the build is the master branch of the Git repository. 
    * The Build Stage runs automatically every time a change is pushed to the repository. 
  
  b. Click the **JOBS** tab and review the settings:
  
    * The builder type is **Ant**. The ant command will find the default build script file, `build.xml`, which is provided in the sample at the root directory.
    * Because the `build.xml` file is in the root of the project, you do not have to specify a working directory.
    * The build output will be saved in an `output` directory, as specified in the **Build Archive Directory** field. The files that are needed for deployment are copied into the build archive directory.
    * If the build is not completed, the stage stops running and any later jobs do not run.
  ![Configuring the Builder][18]
  
  c. Because you did not make any changes, click **DISCARD CHANGES** to return to the Build & Deploy Pipeline page.
 
3. At the top of the Build Stage tile, click the **Run Stage** icon <img  class="inline" src="images/run_stage.gif" alt="Run Stage icon">. After a moment, you have a successful build.


####Explore the deploy stage

1. On the Deploy Stage tile, click the **Stage Configuration** icon <img  class="inline" src="images/configure_stage.gif" alt=="Stage Configuration"> and click **Configure stage**.

  a. Click the **INPUT** tab and review the settings: 
  
     * The input for the build is the output from the build stage. 
     * The deploy stage runs automatically every time the build stage runs successfully. 
 
  b. Click the **JOBS** tab and review the settings:
  
     * The app is set to deploy to your Bluemix organization and space.
     * Bluemix is based on Cloud Foundry, so the deployment script uses the Cloud Foundry command-line interface command `cf push` to deploy your app. To learn more about configuring deployment scripts when using Cloud Foundry, [see the Cloud Foundry documentation][59].
  ![Configuring the Deployer with the Add Deployer Stage screen][19]

  c. Because you did not make any changes, click **DISCARD CHANGES** to return to the Build & Deploy Pipeline page.
  
  Because you clicked the **Automatically execute jobs when the previous stage completes successfully** option when you set up the deploy stage, builds of your app are deployed automatically.

  **Tip**: In the future, if you do not click that option, you can start a deployment by dragging a build to a stage that has a deploy job. For example, you could drag the build from the LAST EXECUTION RESULT section of the build stage to the deploy stage, as shown here.  

  ![Dropping to deploy][49]

  You can also start a deployment by clicking the **Run Stage** icon <img class="inline"  src="images/run_stage.gif" alt="Run Stage icon"> on the deploy stage. In a few moments, your app is deployed to Bluemix.

2. To view your app on the web, on the Deploy Stage tile, click the URL in the LAST EXECUTION RESULT section. If the app is already open in a browser window, refresh the page. To view your app’s Bluemix Dashboard, click the app's name above the URL. 

 ![Our really cool app][36]


<a name='Summary'></a>
## Summary

In this tutorial, you learned to create and run a Java web app by using Bluemix. 


<a name='next_steps'></a>
## Next steps

[Learn more about Bluemix from the IBM Bluemix Docs][53]. 

To learn how to configure Eclipse or other desktop clients to work with your Git repository, [see Working locally with Bluemix DevOps Services projects][26].

To learn how to integrate unit testing into your DevOps Services projects, [see Setting up local Eclipse clients to work with Jazz source control][40].

To learn more about built-in environment properties and tools in the pipeline, [see Environment properties and resources for the Build & Deploy pipeline](/docs/deploy_var).

   [1]: https://bluemix.net/ (Bluemix)
   [2]: images/bm-join.png
   [3]: https://bluemix.net/docs/QuickStart.jsp (Bluemix getting started)
   [4]: https://bluemix.net/docs/BlueMixIntro.jsp (Bluemix overview)
   [5]: https://bluemix.net/docs/Tutorials.jsp (Bluemix tutorials)
   [6]: images/demo-dash.png 
   [7]: images/bm-java-starter.png 
   [8]: images/create-jws-app.png 
   [9]: images/examplepanel.gif 
   [10]: images/bm-example.png 
   [11]: images/addgitintegration.png
   [12]: images/jh-signin.gif 
   [13]: images/bm-create-git-repo.png
   [14]: images/bm-git-repo-success-msg.png 
   [15]: images/bm-code-button.png 
   [16]: images/webide.gif 
   [17]: images/simpledeploy2.png
   [18]: images/configbuilder.png 
   [19]: images/deployer.png 
   [20]: /tutorials/clients (Setting up Eclipse, Git, and Rational Team Concert Desktop Clients for use with Bluemix DevOps Services)
   [21]: images/cli-git-clone.gif 
   [22]: images/cli-stage-commit.gif 
   [23]: images/cli-push.gif 
   [24]: images/autodeploy.gif 
   [25]: images/app-new-title.png 
   [26]: /tutorials/clients (Setting up Eclipse, Git, and Rational Team Concert Desktop Clients for use with Bluemix DevOps Services)
   [27]: https://hub.jazz.net/learn (Bluemix DevOps Services introduction)
   [28]: http://orion.eclipse.org/ (The Eclipse Orion project)
   [29]: images/orion.png
   [30]: images/completion.png 
   [31]: images/heyworld.png 
   [32]: images/orion-git-status.png 
   [33]: images/unstaged.png 
   [34]: images/commit.png
   [35]: images/push.png 
   [36]: images/endexampleapp.png 
   [37]: images/manualdeploy.png
   [38]: https://www.ibmdw.net/answers?community=jazzhub (forum)
   [39]: mailto:hub%40jazz.net
   [40]: /docs/jazz_scm_client/ (Setting up local Eclipse clients to work with Jazz source control)
   [41]: /tutorials/jazzeditor (Getting Started with Bluemix and Bluemix DevOps Services using Node.js)
   [42]: /tutorials/clients (Setting up Eclipse, Git, and Rational Team Concert Desktop Clients to access Bluemix DevOps Services)
   [43]: /tutorials/jazzweb (Developing Bluemix applications in Node.js with the Bluemix DevOps Services Web IDE)
   [44]: images/panel_gear.gif
   [45]: images/un-pipeline.png
   [46]: images/configured-builder.png
   [47]: images/configured-and-built.png
   [48]: images/configured-pipeline.png
   [49]: images/drop-to-deploy.png
   [50]: images/deployed-with-pipeline.png
   [51]: images/click-to-open.gif
   [52]: images/config-to-delete.png
   [53]: https://www.ng.bluemix.net/docs/#
   [54]: images/bm-name-app.png
   [55]: images/bm-web-starter.png
   [56]: images/runbar_green.png
   [57]: images/playbutton.png
   [58]: /docs/billing/
   [59]: http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html#push
