# Setting up local Eclipse clients to work with Jazz source control

###### Last updated: 23 June 2016

If you use Jazz Source Control Management (SCM) for your IBM&reg; Bluemix&trade; DevOps Services project, you can either work locally and deliver changes through Eclipse or work by using the integrated Web IDE. If you work locally and deliver changes through Eclipse, you can install the IBM Rational Team Concert&trade; plug-in for version control.

If you use the Track &amp; Plan feature to manage your project plans and work items, you can also access your work items from Eclipse.

* [Installing the Rational Team Concert plug-in](#install_eclipse_and_the_rational_team_concert_plugin)
* [Connecting to your DevOps Services projects from Eclipse](#connect_to_your_devops_services_projects_from_eclipse)
* [Loading DevOps Services projects in Eclipse](#import_code_into_eclipse_from_jazz_source_control)
* [Delivering changes](#delivering)
* [Opening DevOps Services work item queries in Eclipse](#work_items)
* [Limitations to change and configuration management features](#limitations)

<a name='install_eclipse_and_the_rational_team_concert_plugin'></a>
## Installing the Rational Team Concert plug-in


###Before you begin 

The plugin is based on Rational Team Concert 5.0.2. 
* Rational Team Concert 5.0.2 and later requires Eclipse 4.3.2 or later. If you do not have Eclipse installed already, [download and install Eclipse IDE for Java EE Developers](http://www.eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/keplersr2).
* Eclipse 4.3.2 requires Java 1.7 or later. If you do not have Java 1.7 installed, [download and install a Java SE Development Kit](http://www.ibm.com/developerworks/java/jdk/).

###Installing the plug-in

1. In Eclipse, click **Help > Install New Software**.

2. In the Install window, complete these steps:
  1. In the **Work with** field, enter `https://jazz.net/downloads/rational-team-concert/5.0.2/5.0.2/p2`.
  2. Press **Enter** to load the contents of the update site.
  3. Select the **Rational Team Concert Client** feature check box.
  4. Select the **Group items by category** check box.
  5. Click **Next** and click **Next** again.
  6. Review the license terms. If you agree to the terms, accept them.
  7. Click **Finish** to install the plug-in.

3. If you see a security warning message, click **OK**.

4. If you are prompted to restart Eclipse, click **Yes**.

<a name='connect_to_your_devops_services_projects_from_eclipse'></a>
## Connecting to your DevOps Services projects from Eclipse

From Eclipse, you can connect to your projects in two ways:

 * Use the Manage IBM DevOps Services Projects tool
 * Accept a team invitation

After you connect to your project, you can access its work items.

###Before you begin

The project must use a Jazz Source Control Management (SCM) repository.

###Option 1: Connecting by using the Manage IBM DevOps Services Projects tool

1. In Eclipse, click **Window > Preferences > General > Workspaces**. In the Text file encoding field, click **Other** and from the list, select **UTF-8**.

2. Click **Window > Show View > Other > Team Artifacts**.

   **Note:** Depending on which version of Eclipse you are using, the menu options to open the Team Artifacts view might differ.

3. Click the **Manage IBM DevOps Services Projects** icon.
 ![Manage JazzHub Projects button within the Team Artifacts View](./images/jazzhubfeature.png)

4. In the Manage IBM DevOps Services Projects window, sign in to DevOps Services by entering your alias and personal access token or your IBM id password and clicking **Next**.     
  
    **Note**: Your user ID for DevOps Services can be either an IBM id or a federated ID (corporate ID). If you use federated authentication, to log in to your Eclipse client, you must use a personal access token instead of a password. If you don't use federated authentication, your IBM id and password work with all clients. For more information about creating a personal access token, see [What’s federated authentication and how does it affect me?](https://developer.ibm.com/devops-services/2016/06/23/whats-federated-authentication-and-how-does-it-affect-me/)


5. Select the DevOps Services projects to connect to and click **Finish**.

###Option 2: Connecting by accepting a team invitation

1. In [DevOps Services](https://hub.jazz.net/), browse to your project's Overview page.

2. Click **Configure eclipse client**. 
![Configure eclipse button on the project overview](images/configure-eclipse.jpg)

3. Copy the text for the project invitation.

4. In Eclipse, click **Window > Preferences > General > Workspaces**. In the Text file encoding field, click **Other** and from the list, select **UTF-8**.

5. Click **File > Accept JazzHub Client Configuration**. If you don't see that menu option, click **File > Accept Team Invitation**.

6. Paste the invitation text, click **Next**, and then click **Finish**.

7. Sign in to DevOps Services by entering your alias and personal access token or your IBM id password.    

    **Note**: Your user ID for DevOps Services can be either an IBM id or a federated ID (corporate ID). If you use federated authentication, to log in to your Eclipse client, you must use a personal access token instead of a password. If you don't use federated authentication, your IBM id and password work with all clients. For more information about creating a personal access token, see [What’s federated authentication and how does it affect me?](https://developer.ibm.com/devops-services/2016/06/23/whats-federated-authentication-and-how-does-it-affect-me/)

You are now connected to your DevOps Services project in Eclipse. To see the new repository connection and project area, click the **Team Artifacts** tab.

<a name='import_code_into_eclipse_from_jazz_source_control'></a>
## Loading DevOps Services projects in Eclipse

###Before you begin

[Connect to a project from Eclipse](#connect_to_your_devops_services_projects_from_eclipse). The project must have the Track & Plan feature enabled.

###Creating a repository workspace

1. In the Eclipse Workbench,  click **Window > Show View > Other > Team > Team Artifacts**.

2. Expand your project area to show the **Source Control** folder.

3. Right-click the **Source Control** folder, and click **New > Repository Workspace**.

4. Select the stream to flow to and click **Next**. 

4. Specify a new name for your repository workspace and click **Finish**.

5. Complete the wizard.

###Loading projects

6. Click **Find and load Eclipse projects** and click **Next**.

7. Select the Eclipse projects to load and click **Finish**.

8. Click the **Package** tab or the **Project Explorer** tab to create or browse files and edit code.


<a name='delivering'></a>
## Delivering changes

1. Make changes to the files. You can edit them with an Eclipse editor or an external editor of your choice.
2. In the **Package** tab or **Project Explorer** view, refresh the files.
3. In the **Pending changes** view, right-click the unresolved changes and click **Check in** and **New changeset**.
4. Add a comment to the changeset.
5. Right-click the changeset and click **Deliver**.


<a name='work_items'></a>

## Opening DevOps Services work item queries in Eclipse

###Before you begin

[Connect to a project from Eclipse](#connect_to_your_devops_services_projects_from_eclipse). 

###Opening queries

1. In the **Team artifacts** view, expand a project and **Work Items**.

2. Create a query or open an existing query.

<a name='limitations'></a>

##Limitations to change and configuration management features

In DevOps Services projects, certain change and configuration management features that are in Rational Team Concert might not be available.

###Project-area save permissions are not available

+ Team areas cannot be created.
+ Process customization for work items, workflows, approval and review requirements, pre- and post- conditions, and so on, cannot be configured.
+ In Eclipse, timelines cannot be edited directly. To manage timelines, in DevOps Services, click **TRACK & PLAN**, and open the Sprint Planning view.
+ Membership operations are not available. You can invite users to join a project from the DevOps Services project. For more information about user-role privileges, see [Administering a project in Bluemix DevOps Services](../projectadmin/).

**Exception:** You can change work-item categories in the project-area editor.

###Links to Jazz Team Server are not available
+ Personal dashboards cannot be accessed.




[18]: https://developer.ibm.com/answers/questions/?community=devops-services (Bluemix DevOps Services forum)
[19]: mailto:hub%40jazz.net
[20]: /docs
