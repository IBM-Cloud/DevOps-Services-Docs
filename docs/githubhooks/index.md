#Linking work items in Bluemix DevOps Services to code changes in GitHub

###### Last updated: 16 June 2015

If you have source code in a GitHub repository, you can use your IBM&reg; Bluemix&trade; DevOps Services project to track changes by setting up a service hook on GitHub. When you push a change to your GitHub repository, the hook adds a change set link to your DevOps Services work item. You can view the changes in your GitHub repository by clicking the change set link in the work item.

 * [Creating a DevOps Services project](#create_project)
 * [Setting up the GitHub hook](#github_hook)
 * [Creating a work item to test the hooks](#create_work_item)

<a name='create_project'></a>
##Creating a DevOps Services project

 **Note:** If you already have a DevOps Services project that is connected to a GitHub repository, skip to [Set up the GitHub hook](#github_hook).
1. Sign in to [DevOps Services][1]. The My Projects page opens.
2. If this project is your first project, click **Start coding**. Otherwise, click **CREATE PROJECT**.   
3. Type the project name.
4. Click **Link to an existing repository**.   
5. If you haven't authorized with GitHub or logged in to GitHub, do so when you are prompted and then return to DevOps Services.
6. From the **Select the repository to link** list, select your GitHub repository.  
![The GitHub repository on the Create page.][2]
7. Make sure that the **Add features for Scrum development** check box is selected.
8. Click **CREATE**.

<a name='github_hook'></a>
## Setting up the GitHub hook

You need to set up your GitHub repository to create a link when the repository receives a push. To do so, you configure a service hook. The hook adds a link to a work item whenever a change is pushed to your repository and you include a work item keyword and number in the commit message. 

### Before you begin:

The IBM Bluemix DevOps Services hook replaces the RationalJazzHub hook. If you configured the RationalJazzHub hook, disable it and configure the IBM Bluemix DevOps Services hook instead.

### Configuring the service hook:

1. In your GitHub repository, in the right column, click **Settings**.
![GitHub settings link.][4]
2. Click **Webhooks & Services**.
![GitHub web hooks and services link.][5]
3. Click **Add service**, and from the **Available Services** list, select **IBM Bluemix DevOps Services**.
4. Type your IBM id and password.
5. Select the **Active** check box.   
 **Tip:** If you need to disable work item linking later, return to this page and clear the **Active** check box.  
![Configuration settings for the IBM Bluemix DevOps Services hook][6]

6. Click **Add service**.

Now you can add a work item keyword and number to your commit comments. Then, when you push changes, a link to the change set will be generated on the **LINKS** tab of the work item.
![Commit comment with work item keyword and number][7]
You can use these keywords for hooks:
   - `adoption item`
   - `bug`
   - `defect`
   - `epic`
   - `impediment`
   - `item`
   - `retrospective`
   - `story`
   - `task`
   - `track build item`
   - `work item`

<a name='create_work_item'></a>
## Creating a work item for testing

To test your hook, create a work item and commit a change to your code.

1. On the DevOps Services project's Overview page, click **TRACK & PLAN**.
2. In the **Create a work item** field, type a summary and any work item attributes that you need.
3. Click **CREATE**.
4. Note the task number so that you can add it to your comment when you commit your change.
5. Make a change to one of the files in your GitHub repository. This example uses the DevOps Services Web IDE, but you can use any editor.
6. Add a commit comment that includes one of the work item keywords and your work item number. In this example, the work item keyword and number are `task 530`.
![Commit comment in Web IDE][8]
7. Commit and push the change.
8. Open your work item. On the **LINKS** tab, click the change set.   
![Work item link to the change set.][9]
9. View the change in GitHub.
![Changed file in GitHub.][10]


[1]: https://hub.jazz.net
[2]: images/githubDevOpsProject.png
[4]: images/githubSettings.png
[5]: images/githubHooks.png
[6]: images/githubServiceConfig2.png
[7]: images/githubComment.png
[8]: images/githubCommit.png
[9]: /docs/reference/githubhooks/images/githubLink.png
[10]: /docs/reference/githubhooks/images/githubChange.png


