# Administering a project

###### Last updated: 02 July 2015

To administer IBM&reg; Bluemix&trade; DevOps Services projects, you must be a project admin or a project owner. A project can have multiple admins, but it can only have one owner. 

* [Project owner privileges](#project_owner_privileges)
* [Project admin privileges](#project_admin_privileges)
* [Project member privileges](#project_member_privileges)
* [Managing projects](#managing_projects)
* [Promoting or demoting project admins](#promoting_demoting)

<a name='project_owner_privileges'></a>
##Project owner privileges
Project owners can do everything that project admins and members can do. In addition, project owners can do these tasks:
* Rename the project
* Transfer ownership of the project
* Delete the project

<a name='project_admin_privileges'></a>
##Project admin privileges

Project admins can do the tasks that project members can do as well as these tasks:
* Invite others to join the project
* Accept or decline when others request to join the project
* Promote members to admins 
* Demote admins to members (including self)
* Edit Track & Plan sprints
* Configure Build and Deploy
* Update these project settings: 

	a. Change the project photo and description
	
	b. Enable or disable project privacy
	
	c. Enable or disable the Track & Plan feature
	
* Manage these functions for Git projects:

	a. Update and delete branches and tags
	
	b. Force pushes

<a name='project_member_privileges'></a>
##Project member privileges
Project members have the fewest privileges and responsibilities. They can do these tasks:  
* Add and edit work items
* Create Git branches for Git projects
* Create tags for Git projects
* Push and pull source code from the repository
* View and edit pipelines
* Add, edit, delete, and run pipeline stages or jobs

<a name='managing_projects'></a>
##Managing projects

A common task for project owners and admins is to manage the project's settings and members. When you sign in to DevOps Services, the My Projects page opens. On the Requests page, you can see any requests to join projects that you administer. As an admin, you can accept or reject those requests. 

In projects that you own or administer, you can invite people to be members. On the Members page, click **INVITE MEMBERS**.

As a project owner or admin, you can also change your project settings. For example, you can add or change the project's image, modify its description, enable or disable features, and make the project public or private. If you are the project owner, you can also reassign its ownership, change its name, or delete the project. To access the project settings, click the **Settings** icon.

![Project settings gear icon][7]

<a name='promoting_demoting'></a>
##Promoting or demoting project admins

Because each project can have multiple admins, you can be promoted or promote others to the project admin role. 

Before you can be promoted to a project admin, you must be a member of the project. Ask the project owner or a project admin to invite you to join the project and promote you to be a project admin. If you are the project creator, you can already promote others.

To promote others to be project admins:

1. If the people that you want to promote aren't project members, invite them. 

2. On the Overview or Members pages, click the **Settings** icon.
 
	**Tip:** If you're on the Members page, you can quickly go to the Project Admins page by clicking **MANAGE ADMINS**. 
![Settings and manage admins buttons on the members page][4]
3. If you clicked the **Settings** icon, the project settings pages open. Click **PROJECT ADMINS**.
![Project Admins page link in navigation pane][5]

4. On the Project Admins page, select the members to promote and click **PROMOTE**.
![Promote button on the project admins page][6]

The newly promoted members are listed as project admins, and they automatically receive an email about their new role.

To demote project admins to be regular project members:
1. On the Project Admins page, select the admins whose privileges you want to remove. 
2. Click **DEMOTE**.
![Project admin selected for demotion][8]

The former project admins are listed as members, and they automatically receive an email about the role change.

[1]: images/invitemembers.png
[2]: images/projadminspage1.png
[3]: images/projectoptionspage1.png
[4]: images/SettingsIcon.png
[5]: images/ProjectAdminsNav.png
[6]: images/promotemember.png
[7]: images/projectsettings.png
[8]: images/demoteadmin.png

