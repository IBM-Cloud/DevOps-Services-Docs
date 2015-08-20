#Develop a Node.js app from Bluemix

###### Last updated: 20 August 2015

Time: 15 minutes

IBM&reg; Bluemix&trade; is an open-standards, cloud-based platform where you can build, manage, and run all types
of apps: mobile, smart devices, web, and big data. The Bluemix capabilities include Java&trade;, mobile back-end development, app monitoring, and features from ecosystem partners and open source, all through an as-a-service model in the cloud.

In this tutorial, you create an app in Bluemix by using the SDK for Node.js starter pack. You then create a Git repository for the app and push changes to that repo from the IBM&reg; Bluemix&trade; DevOps Services Web IDE.

If you want more information about Bluemix, see [Getting Started with Bluemix](https://www.ng.bluemix.net/docs/#) and [Bluemix Overview](https://www.ng.bluemix.net/docs/#overview/overview.html#overview).

If you're ready to try Bluemix, start this tutorial!

<div class="table-of-contents">
 <table>
   <tr>
     <td colspan="6"><h4>Summary of steps</h4></td>
   </tr>
   <tr>
     <td><a href="#prereq">Before you begin</a></td>
     <td><a href="#create_bluemix_app">Create an app with Bluemix</a></td>
     <td><a href="#git_integration_and_autodeployment">Set up Git integration and auto-deploy</a></td>
     <td><a href="#push">Push changes to the Git repository by using the Web IDE</a></td>
     <td><a href="#summary">Summary</a></td>
     <td><a href="#nextsteps">Next steps</a></td>
   </tr>
 </table>
</div>

 

<a name='prereq'></a>
##Before you begin

[Sign up for DevOps Services](https://hub.jazz.net/register). When you sign up, you'll create an IBM id, create an alias, and register with Bluemix. 

 <a name='create_bluemix_app'></a>
##Create an app in Bluemix

1. Sign in to Bluemix. The Dashboard opens:
![Bluemix Dashboard](/tutorials/jazzeditor/images/bm-home_NEW.png)
The Dashboard shows an overview of the active Bluemix space for your organization. 
By default, the space is `dev` and the organization is the user name of the person who created the project. 
For example, if `bob@example.com` logs in to Bluemix for the first time, the active space is `dev` and the organization 
is `bob@example.com`.
If you create more organizations or spaces in Bluemix, use the same ones as you follow the tutorials. Use the default selections.

2. Click **CREATE AN APP**. For the kind of app that you are creating, click **WEB**.  

3. For your starter, click **SDK for Node.js**. Review the docs and details, and then click **CONTINUE**.

4. Name your app and then click **FINISH**. The name is a unique URL where you access your app. 
After a moment, the app starts. The app's Overview page opens and shows that the app is running.
![Bluemix Application tile](/tutorials/jazzeditor/images/bm-app-panel_NEW.png)

Now that your app is running, you can see and modify its code by using DevOps Services.

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

<a name='push'></a>
##Push changes to the Git repository by using the Web IDE

The integrated Web IDE is 
based on [the Eclipse Orion open-source project](http://orion.eclipse.org/). 
![Orion at Bluemix DevOps Services](/tutorials/jazzeditor/images/orion_1_NEW.png)

You can edit files with syntax coloring support for multiple languages, including HTML, 
CSS, JavaScript, Ruby, and Python. For some languages, such as JavaScript, the Web IDE also supports 
syntax checking and code completion, both for standard language constructs and for the services that Bluemix provides. To use content assist, press Ctrl+Space. For example, this image shows code completion for the standard Node.js express module.
![Orion showing express completions](/tutorials/jazzeditor/images/completion.png)

To make a change to a file and then push the change, follow these steps:

1. In the directory, find a file to modify; for example, `public/index.html`. 

5. Edit the file in the editor.
![Orion editing index](/tutorials/jazzeditor/images/orion-really-cool_NEW.png)

6. Push the change by using the integrated Git support. 

	a. From the leftmost menu, click the **Git Repository** icon <img  class="inline" src="/tutorials/jazzeditor/images/git.gif" alt="Git Repository icon">.
	
	b. Select check box for the changed file.
![Orion Git staging](/tutorials/jazzeditor/images/orion-git-stage_NEW.png)
	c. Type a commit message, and then click **Commit**.
![Orion Git commit](/tutorials/jazzeditor/images/orion-commit_NEW.png)
	d. In the Outgoing section on the left, click **Push**.
![Orion Git push](/tutorials/jazzeditor/images/orion-push_NEW.png)

7. To verify that your code was deployed, 
click **BUILD & DEPLOY** and wait until you see an indication that the 
app was deployed again. On the Deploy stage, in the LAST EXECUTION RESULT section, click the URL link under the app's name.
![Clicking the web app's URL](/tutorials/jazzeditor/images/click-webapp-url.png)

Your update is shown.
![Our really cool app](/tutorials/jazzeditor/images/really-cool_NEW.png)

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

[Learn more about testing your app as you develop by using Bluemix Live Sync](/tutorials/livesync). 

[1]: /tutorials/jazzeditor/images/runbar_green.png
