#Get started with Bluemix and Bluemix DevOps Services using Node.js

Last modified: 21 April 2015

Time: 30 minutes

* [Learning objectives](#objectives)
* [Before you begin](#prereq)
* [Create an app with Bluemix](#create_bluemix_app)
* [Set up Git integration and auto-deploy](#git_integration_and_autodeployment)
* [Push changes to the Git repository by using the Web IDE](#push)
* [Summary](#summary)
* [Next steps](#nextsteps)
 
 
 ---
<a name='objectives'></a>
##Learning objectives

* Create an app in IBM&reg; Bluemix&trade; by using the SDK for Node.js starter pack.
* Create a Git repository for the app.
* Push changes to the Git repository from the IBM&reg; Bluemix&trade; DevOps Services Web IDE.

---

<a name='prereq'></a>
##Before you begin

[Sign up for DevOps Services](https://hub.jazz.net/register). When you sign up, you'll create an IBM id, create an alias, and register with Bluemix. 

---
 
<a name='create_bluemix_app'></a>
##Create an app with IBM Bluemix

Bluemix is an open-standards, cloud-based platform where you can build, manage, and run all types
of apps: mobile, smart devices, web, and big data. The Bluemix capabilities include Java&trade;, mobile back-end development, 
app monitoring, and features from ecosystem partners and open source, 
all through an as-a-service model in the cloud.

You can find helpful information on the Bluemix website:

* [Getting Started with Bluemix](https://www.ng.bluemix.net/docs/#)
* [Bluemix Overview](https://www.ng.bluemix.net/docs/#overview/overview.html#overview)

To get started now, try this tutorial. You'll create an app and deploy it.

1. Sign in to Bluemix. The Dashboard opens:
![Bluemix Dashboard](/tutorials/jazzeditor/images/bm-home_NEW.png)
The Dashboard shows an overview of the active Bluemix space for your organization. 
By default, the space is `dev` and the organization is the user name of the person who created the project. 
For example, if `bob@example.com` logs in to Bluemix for the first time, the active space is `dev` and the organization 
is `bob@example.com`.
If you create more organizations or spaces in Bluemix, use the same ones as you follow the tutorials. Use the default selections.

2. Click **CREATE AN APP**. For the kind of app that you are creating, click **Web**.  

3. For your starter, click **SDK for Node.js**. Review the docs and details, and then click **CONTINUE**.

4. Name your app and then click **FINISH**. The name is a unique URL where you access your app. 
After a moment, the app starts. The app's Overview page opens and shows that the app is running.
![Bluemix Application tile](/tutorials/jazzeditor/images/bm-app-panel_NEW.png)

Now that your app is running, you can see and modify its code by using DevOps Services.

---
<a name='git_integration_and_autodeployment'></a>
##Set up Git integration and auto-deploy in DevOps Services

You can work with your app's code in many ways. For example, with auto-deploy, you can modify the code that runs in your app by pushing your changes to a Git repository. You can auto-deploy your code if you use the Build & Deploy capabilities of DevOps Services.

1. To enable auto-deploy, go to your app's Overview page on the Bluemix Dashboard and click **ADD GIT**. A Git repository is created and is populated with example code and a deployed app. You might be prompted to enter your password to verify that DevOps Services can act on your behalf. 
![Add Git button](/tutorials/jazzeditor/images/bm-add-git-integration_NEW.png)

2. Make sure that the **Populate the repository with the starter application package and enable build and deploy** check box is selected.
![Create Git repo dialog](/tutorials/jazzeditor/images/bm-create-git-repo_NEW.png)
You created a Git repository, populated it with the example code, and deployed the app.
![Git repo success message dialog](/tutorials/jazzeditor/images/bm-git-repo-success-msg_NEW.png)

3. Go to the app's Overview page and click **EDIT CODE**. Your new project opens in the web integrated development environment (Web IDE).  
![CODE button](/tutorials/jazzeditor/images/bm-code-button_NEW.png)

---
<a name='push'></a>
##Push changes to the Git repository by using the Web IDE

The integrated Web IDE is 
based on [the Eclipse Orion open-source project](http://orion.eclipse.org/). 
![Orion at Bluemix DevOps Services](/tutorials/jazzeditor/images/orion_1_NEW.png)

You can edit files with syntax coloring support for multiple languages, including HTML, 
CSS, JavaScript, Ruby, and Python. For some languages, such as JavaScript, the Web IDE also supports 
syntax checking and code completion, both for standard language constructs and for the services that Bluemix provides. To use content assist, press Ctrl+Space. For example, this image shows code completion for the standard Node.js express module:
![Orion showing express completions](/tutorials/jazzeditor/images/completion.png)

4. In the directory, find a file to modify; for example, `views/body.jade`. 

5. Edit the file in the editor.
![Orion editing index](/tutorials/jazzeditor/images/orion-really-cool_NEW.png)

6. Push the change by using the integrated Git support. 

	a. From the leftmost menu, click the **Git Repository** icon.
	
	b. Select the changed file:
![Orion Git staging](/tutorials/jazzeditor/images/orion-git-stage_NEW.png)
	c. Add a commit message and commit the changes:
![Orion Git commit](/tutorials/jazzeditor/images/orion-commit_NEW.png)
	d. Push the changes:
![Orion Git push](/tutorials/jazzeditor/images/orion-push_NEW.png)

7. To verify that your code was deployed, 
click **BUILD & DEPLOY** and wait until you see an indication that the 
app was deployed again. In the Deploy stage, under LAST EXECUTION RESULT, click the URL link that is below the app's name.
![Clicking the web app's URL](/tutorials/jazzeditor/images/click-webapp-url.png)

Your update is shown.
![Our really cool app](/tutorials/jazzeditor/images/really-cool_NEW.png)

---
<a name='summary'></a>
##Summary

You have a good overview of how to get started with Node.js in Bluemix and DevOps Services. 

You saw how to create and run a Node.js web app by using Bluemix. 
With one click, you created a Git repository, populated it with example code, and automatically 
deployed the app. You changed the code and pushed the changes to the Git repository by using the 
Web IDE. Then, you automatically built and deployed your changes, checked the deployment status, 
and verified your changes. 

<a name='nextsteps'></a>
##Next steps

After you have completed this tutorial, [learn more about testing your application as you develop by using Bluemix Live Sync](/tutorials/livesync). 

[1]: /tutorials/jazzeditor/images/runbar_green.png
