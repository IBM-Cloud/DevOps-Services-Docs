# Creating a project in Bluemix DevOps Services 

####### Last modified: 2 July 2015

In an IBM&reg; Bluemix&trade; DevOps Services project, one or more people can build, share, organize, and manage versions of resources to achieve a goal. Usually, that goal is to create an app. After you create an app in a DevOps Services project, you can deploy the app to IBM&reg; Bluemix&trade;. 


* [Projects](#projects)
* [Creating a project](#starting_a_devops_services_project)
* [Forking a project](#forking_a_devops_services_project)
* [Creating a project for a Bluemix app](#creating_a_devops_services_project_for_your_bluemix_app)
* [Cloning an existing app using the Deploy to Bluemix button](#deploy_to_bluemix_button)


<a name='projects'></a>
## Projects
When you configure a DevOps Services project to deploy to Bluemix, the project is associated with an organization (org) and space in Bluemix for billing purposes. You can configure the project's pipeline and Web IDE workspace to deploy to any org and space in Bluemix that you have access to. 

When you deploy your project to Bluemix, the project becomes a Bluemix app that you can enable services for, such as the Track & Plan service or the Delivery Pipeline service. Because the use of services can generate charges, you must set up a Bluemix account for your project.

You can start a project four ways. If you want to start by using new code or an existing Git repository, [create a project](#starting_a_devops_services_project). If you want to start from a copy of the code in a DevOps Services project, [fork the code](#forking_a_devops_services_project).  You can also [create a DevOps Services project from an IBM&reg; Bluemix&trade; app](#creating_a_devops_services_project_for_your_bluemix_app).  Finally, you can clone a fully functioning app by using the [Deploy to Bluemix](#deploy_to_bluemix_button) button.


** Before you begin**
* [Register for DevOps Services](https://hub.jazz.net). 
* If you plan to deploy your project to Bluemix, which is a cloud-based software hosting and deployment service, [register for Bluemix](http://bluemix.net/). 

<a name='starting_a_devops_services_project'></a>
##Creating a project

1. [Log in to DevOps Services](https://hub.jazz.net). The My Projects page opens.

2. If this project is your first project, click **Start coding**. Otherwise, click **CREATE PROJECT**.

3. Type the project name.

4. Select a repository type. 
  * If you are familiar with GitHub, you can create or link to a GitHub repository.  To use a new GitHub repository, click the **Create a new repository** icon, and then click the **Create a Git repo on GitHub** icon. If you already have your code in a GitHub repository, you can continue to use that repository with this project. Click the **Link to an existing repository** icon, and then select the repository from the list.    
 * If you are familiar with Git and want to create a hosted repository, click the **Create a new repository** icon, and then click the **Create a Git repo on Bluemix** icon.  
**Tip**: You can host a local Git repository on DevOps Services. First, create the DevOps Services project; then, force push the local repository to the new hosted repository.
 * If you are familiar with IBM&reg;  Rational Team Concert&trade; and want to use Jazz&trade; source control management (SCM), click the **Create a new repository** icon, and then click the **Create Jazz SCM on Bluemix** icon.
 
5. If you want to control who can view your project and its code, select the **Private Project** check box. DevOps Services users who you invite can access your private projects.    
**Note**: To create a private repository on GitHub, you must have a paid GitHub account. If necessary, click **Change your GitHub plan** or use a private Bluemix repository instead.

6. If you want to use all of the Track & Plan features, including the ability to create sprints from the project backlog of work items, select the **Add features for Scrum development** check box.  
If you want to use only the traditional planning feature, which uses tasks and iterations without a backlog, clear the check box.

7. To deploy the project code to Bluemix, select the **Make this a Bluemix Project** check box.  
**Important**: Building and deploying apps can result in charges to your Bluemix billing account. For more information about pricing, [see the Bluemix Pricing page](https://console.ng.bluemix.net/?ace_base=true/#/pricing).

8. Click **CREATE**.  

<a name='forking_a_devops_services_project'></a>
## Forking a project

When you fork a project, the original project's source is copied into a new DevOps Services project that you own.  You might fork a project for these purposes:
 * To implement a feature by following a different process or plan
 * To propose changes to a project
 * To use another project as the starting point for a new idea

Although the complete source of the original project is copied, you'll notice that aspects of the original project are not in the new project.  For example, Build & Deploy pipelines, Track & Plan work items, and any other Bluemix services that were bound to the original project are not in the new project.  You can add those services to the new project.

1. [Log in to DevOps Services](https://hub.jazz.net).

2. Click **EXPLORE**, find the project to start from, and click its name.
![Bluemix DevOps Services new user landing page][1]

3. Click **FORK PROJECT**.
	
4. In the Fork Project window that opens, type your project name, review the contents of the window, and specify options as needed. For more information about the options, [see Starting a Bluemix DevOps Services project](#starting_a_devops_services_project).
![Options while forking project][2]

5. Click **CREATE**.


### Changing the org or space for a project

After you fork your project, you might need to change the specified org or space. For example, if the org that is selected for the forked project cannot be found, specify a different org to deploy the project.

To change the org or space:

1. On the project's Overview page, click the **Settings** icon.
![Project settings icon][4]
2. Click **OPTIONS**.
3. In the Make this a Bluemix Project section, change the selected org or space.
4. Click **SAVE**.


<a name='creating_a_devops_services_project_for_your_bluemix_app'></a>
## Creating a project for your Bluemix app

1. [Log in to Bluemix][3].

2. On your Bluemix Dashboard, click the app to create a DevOps Services project for.

3. On the app's Dashboard, in the upper-right corner, click **ADD GIT**.
![The ADD GIT link][5]

4. Review the message and click **CONTINUE**.

5. After the repository is created, review the new message and click **CLOSE**.

6. Access the new DevOps Services project by clicking **EDIT CODE**.
![The EDIT CODE button][6]  

7. If you wrote code for your app, push your code to your project's repository.


<a name='deploy_to_bluemix_button'></a>
## Cloning an app by using the Deploy to Bluemix button

App developers can embed the **Deploy to Bluemix** button in many kinds of content, including readme files, blogs, articles, and web pages.  The button is useful when you want to set up a cloned version of an app that is publicly available from a Git repository, such as DevOps Services or GitHub.

When you click the button, Bluemix opens, the app is cloned, any necessary build tools are set up, and the Cloud Foundry script to deploy the app to your Bluemix account is provided. With the **Deploy to Bluemix** button, you can confidently clone and deploy apps to Bluemix.

1. Click <img src="./images/deploy-button.png"  alt="Deploy to Bluemix" align="center" style="display: inline; margin: 0px; border-style: none;"> for an app to open the Deploy to Bluemix page.

2. Log in to or sign up for Bluemix.

3. Name your new app and specify any options as needed.

4. Click **DEPLOY**.

When the deployment is completed, a private DevOps Services project is set up.  The project contains a running instance of the app, back-end services, and a dedicated Git repository that you can use to make  updates to the app.

[1]: images/restyle_projectname.png
[2]: images/restyle_newprojectwindow.png
[3]: http://bluemix.net/
[4]: images/project_settings_icon.png
[5]: images/addgit.png
[6]: images/editcode.png
