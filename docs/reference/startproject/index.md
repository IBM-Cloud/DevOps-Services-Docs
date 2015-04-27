# Start a project in Bluemix DevOps Services 

Last modified: 19 February 2015

You can start an IBM&reg; Bluemix&trade; DevOps Services project in three ways. If you want to start by using new code or an existing Git repository, [create a project](#starting_a_devops_services_project). If you want to start from a copy of the code in a Bluemix DevOps Services project, [fork the code](#forking_a_devops_services_project).  You can also [create a Bluemix DevOps Services project from an IBM&reg; Bluemix&trade; app](#creating_a_devops_services_project_for_your_bluemix_app).

**Before you begin**
* [Register for Bluemix DevOps Services](https://hub.jazz.net). 
* If you plan to deploy your project to IBM Bluemix, which is a cloud-based software hosting and deployment service, [register for Bluemix](http://bluemix.net/). 

---
## Contents

 * [Creating a project](#starting_a_devops_services_project)
 * [Forking a project](#forking_a_devops_services_project)
 * [Creating a project for a Bluemix app](#creating_a_devops_services_project_for_your_bluemix_app)

---
<a name='starting_a_devops_services_project'></a>
##Creating a project

1. Sign in to [IBM Bluemix DevOps Services](https://hub.jazz.net). The MY PROJECTS page opens.

2. If this project is your first project, click on **Start coding**. Otherwise, click **CREATE PROJECT**.

3. Type the project name.

4. Select a repository type.  
 * If you are familiar with IBM&reg;  Rational Team Concert&trade; and want to use Jazz&trade; source control management (SCM), click the **Use Jazz SCM** icon.
 * If you are familiar with Git and want to create a hosted repository, click the **Create a Git repository** icon.  
**Tip**: You can host a local Git repository on Bluemix DevOps Services. First, create the new Bluemix DevOps Services project; then, force push the local repository to the new hosted repository.
 * If you stored code in a GitHub repository, you can continue to use that repository. Click the **Connect to an external GitHub repository** icon and paste the repository URL into the field.

5. If you want to control who can view your project and its code, select the **Private** check box. Bluemix DevOps Services users who you invite can access your private projects. 

6. If you want to use all of the Track & Plan features, including the ability to create sprints from the project backlog of work items, select the **Add features for Scrum development** check box.  
If you want to use only the traditional planning feature, which uses simplte tasks and iterations without a backlog, clear the check box.

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
##Creating a project for your Bluemix app

1. [Log in to Bluemix][3].

2. On your Bluemix dashboard, click the app to create a Bluemix DevOps Services project for.

3. On the app's dashboard, click **ADD GIT**.

4. Review the message and click **CONTINUE**.

5. After the repository is created, review the new message and click **CLOSE**.

6. Access the new Bluemix DevOps Services project by clicking **EDIT CODE**.  

7. If you wrote code for your app, push your code to your project's repository.

[1]: images/restyle_projectname.png
[2]: images/restyle_newprojectwindow.png
[3]: http://bluemix.net/
