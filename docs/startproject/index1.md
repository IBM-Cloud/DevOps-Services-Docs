# Starting a project in Bluemix DevOps Services 


Last modified: 05 June 2015


You can start an IBM&reg; Bluemix&trade; DevOps Services project four ways. If you want to start by using new code or an existing Git repository, [create a project](#starting_a_devops_services_project). If you want to start from a copy of the code in a Bluemix DevOps Services project, [fork the code](#forking_a_devops_services_project).  You can also [create a Bluemix DevOps Services project from an IBM&reg; Bluemix&trade; app](#creating_a_devops_services_project_for_your_bluemix_app).  Finally, you can clone a fully functioning app by using the [Deploy to Bluemix](#deploy_to_bluemix_button) button.

<table border="0px"><tr style="border: none; vertical-align: text_top; align: center;"><td style="vertical-align: text_top; align: center;"><img style="border: 0px; padding: 5px; margin: 0px;" src="images/access-password-key_64.png"></td><td><h2> Projects</h2><p>Projects are ...  </td></tr></table>

**Before you begin**
* [Register for Bluemix DevOps Services](https://hub.jazz.net). 
* If you plan to deploy your project to Bluemix, which is a cloud-based software hosting and deployment service, [register for Bluemix](http://bluemix.net/). 

---
## Contents

 <table border="1px"><tr style="border: 1px solid #ccc; vertical-align: text_top; align: center; padding: 0px; margin: 0px;"><td style="border:1px solid #ccc; vertical-align: text_top; align: center;"  width="20%"><a href="#starting_a_devops_services_project"><img src="images/create-new_64.svg" style="border: 0px; padding: 0px;" ><center>Create a project</center></a></td>
 <td style="border: 1px solid #ccc; vertical-align: text_top; align: center;" width="20%"><a href="#forking_a_devops_services_project"><img src="images/repository-archive_64.png" style="border: 0px;" ><center>Fork a project</center></a></td>
  <td style="border: 1px solid #ccc;" width="20%"><a href="#creating_a_devops_services_project_for_your_bluemix_app"><img src="images/add-new_64.svg" style="border: 0px" ><center>Create a Bluemix App</center></a></td>
    <td style="border: 1px solid #ccc;" width="20%"><a href="#deploy_to_bluemix_button"><img src="images/deploy_64.svg" style="border: 0px;" ><center>Clone and Deploy to Bluemix</center></a></td>
	 <td style="border: 1px solid #ccc;" width="20%"><a href="#create_with_existing_code"><img src="images/run-running_64.svg" style="border: 0px;" ><center>Create a project with existing code</center></a></td>
</tr></table>

---

<a href="https://developer.ibm.com/devops-services/tag/projects/"><img src="images/link-externallink_32.png" style="border: 0px; display: inline;">More on projects</a> &nbsp;&nbsp; 
<a href="https://developer.ibm.com/devops-services/tag/fork/"><img src="images/link-externallink_32.png" style="border: 0px; display: inline;">More on forking</a>

---
<a name='starting_a_devops_services_project'></a>
##Creating a project

1. Sign in to [IBM Bluemix DevOps Services](https://hub.jazz.net). The My projects page opens.

2. If this project is your first project, click **Start coding**. Otherwise, click **CREATE PROJECT**.

3. Type the project name.

4. Select a repository type. 
  * If you are familiar with GitHub, you can create or link to a GitHub repository.  To use a new GitHub repository, click the **Create a new repository** icon, and then click the **Create a Git repo on GitHub** icon. If you already have your code in a GitHub repository, you can continue to use that repository with this project. Click the **Link to an existing repository** icon, and then select the repository from the list.    
 * If you are familiar with Git and want to create a hosted repository, click the **Create a new repository** icon, and then click the **Create a Git repo on Bluemix** icon.  
**Tip**: You can host a local Git repository on Bluemix DevOps Services. First, create the DevOps Services project; then, force push the local repository to the new hosted repository.
 * If you are familiar with IBM&reg;  Rational Team Concert&trade; and want to use Jazz&trade; source control management (SCM), click the **Create a new repository** icon, and then click the **Create Jazz SCM on Bluemix** icon.
 
5. If you want to control who can view your project and its code, select the **Private** check box. Bluemix DevOps Services users who you invite can access your private projects.    
**Note**: To create a private repository on GitHub, you must have a paid GitHub account. If necessary, click **Change your GitHub plan** or use a private Bluemix repository instead.

6. If you want to use all of the Track & Plan features, including the ability to create sprints from the project backlog of work items, select the **Add features for Scrum development** check box.  
If you want to use only the traditional planning feature, which uses tasks and iterations without a backlog, clear the check box.

7. To deploy the project code to Bluemix, select the **Make this a Bluemix Project** check box.  
**Important**: Building and deploying apps can result in charges to your Bluemix billing account. For more information about pricing, [see the Bluemix Pricing page](https://console.ng.bluemix.net/?ace_base=true/#/pricing).

8. Click **CREATE**.  

---
<a name='forking_a_devops_services_project'></a>
## Forking a project

1. [Sign in to IBM Bluemix DevOps Services](https://hub.jazz.net).

2. Click **EXPLORE**, find the project to start from, and click its name.
![Bluemix DevOps Services new user landing page][1]

3. Click **FORK PROJECT**. 

4. In the Fork Project window that opens, type your project name, review the contents of the window, and specify options as needed. For more information about the options, [see Starting a Bluemix DevOps Services project](#starting_a_devops_services_project).
![Options while forking project][2]

5. Click **CREATE**.

---
<a name='creating_a_devops_services_project_for_your_bluemix_app'></a>
## Creating a project for your Bluemix app

1. [Log in to Bluemix][3].

2. On your Bluemix Dashboard, click the app to create a Bluemix DevOps Services project for.

3. On the app's Dashboard, click **ADD GIT**.

4. Review the message and click **CONTINUE**.

5. After the repository is created, review the new message and click **CLOSE**.

6. Access the new Bluemix DevOps Services project by clicking **EDIT CODE**.  

7. If you wrote code for your app, push your code to your project's repository.


---
<a name='deploy_to_bluemix_button'></a>
## Cloning an app by using the Deploy to Bluemix button

App developers can embed the **Deploy to Bluemix** button in many kinds of content, including readme files, blogs, articles, and web pages.  The button is useful when you want to set up a cloned version of an app that is publicly available from a Git repository, such as Bluemix DevOps Services or GitHub.

When you click the button, Bluemix opens, the app is cloned, any necessary build tools are set up, and the Cloud Foundry script to deploy the app to your Bluemix account is provided.  With the **Deploy to Bluemix** button, you can confidentely clone and deploy apps to Bluemix.

1. Click <img src="./images/deploy-button.png"  alt="Deploy to Bluemix" align="center" style="display: inline; margin: 0px; border-style: none;"> for an app to open the Deploy to Bluemix page.

2. Log in to or sign up for Bluemix.

3. Name your new app and and specify any options as needed.

4. Click **DEPLOY**.

When the deployment is completed, a private Bluemix&trade; DevOps Services project is set up.  The project contains a running instance of the app, back-end services, and a dedicated Git repository that you can use to make  updates to the app.

[1]: images/restyle_projectname.png
[2]: images/restyle_newprojectwindow.png
[3]: http://bluemix.net/
