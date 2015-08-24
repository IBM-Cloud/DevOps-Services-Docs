#Setting up GitHub for Bluemix DevOps Services projects

###### Last updated: 21 August 2015

If you have source code in a GitHub repository, or plan to, you can connect it to a IBM&reg; Bluemix&trade; DevOps Services project. You can automatically track changes between DevOps Services and GitHub by setting up a service hook on GitHub. And after you push, you can add work-item links to commits on the DevOps Services Git Log page. You can configure a Build & Deploy pipeline to automate the deployment of the source in your GitHub repo to your running app on Bluemix.

For a complete GitHub reference, [see the official Git documentation](https://help.github.com/).

 * [Creating a DevOps Services project and a new GitHub repo](#create_project)
 * [Connecting a DevOps Services project to a GitHub repo](#existing_github)
 * [Setting up the GitHub hook](#github_hook)
 * [Testing the hook](#create_work_item)
 * [Adding a link after a change is pushed](#post_push)
 * [Build and deploy your changes](#builddeploy)

<a name='create_project'></a>
##Creating a DevOps Services project and a new GitHub repo

If you already have a GitHub repo, skip to [Connecting a DevOps Services project to a GitHub repo](#existing_github).
1. Sign in to [DevOps Services][1]. The My Projects page opens.
2. If this project is your first project, click **Start coding**. Otherwise, click **CREATE PROJECT**.   
3. Type the project name.
4. Click **Create a new repository**.   
5. Click **Create a Git repo on GitHub**.
6. If you haven't authorized with GitHub or logged in to GitHub, do so when you are prompted and then return to DevOps Services.
7. Optional: Add a README, .gitignore file, or license.
7. Make sure that the **Add features for Scrum development** check box is selected.
8. Click **CREATE**.   

<a name='existing_github'></a>
##Connecting a DevOps Services project to a GitHub repo

1. Sign in to [DevOps Services][1]. The My Projects page opens.
2. If this project is your first project, click **Start coding**. Otherwise, click **CREATE PROJECT**.   
3. Type the project name.
4. Click **Link to an existing repository**.   
5. If you haven't authorized with GitHub or logged in to GitHub, do so when you are prompted and then return to DevOps Services.
6. From the **Select the repository to link** list, select your GitHub repo.  
![The GitHub repository on the Create page.][2]
7. Make sure that the **Add features for Scrum development** check box is selected.
8. Click **CREATE**.  

<a name='github_hook'></a>
## Setting up the GitHub hook

You need to set up your GitHub repo to create a link when the repo receives a push. To do so, you configure a service hook. The hook adds a link to a work item whenever a change is pushed to your repo and you include a work item keyword and number in the commit message. 

### Before you begin

The IBM Bluemix DevOps Services hook replaces the RationalJazzHub hook. If you configured the RationalJazzHub hook, disable it and configure the IBM Bluemix DevOps Services hook instead.

### Configuring the service hook

1. In your GitHub repo, in the right column, click **Settings**.
![GitHub settings link.][4]
2. Click **Webhooks & Services**.
![GitHub web hooks and services link.][5]
3. Click **Add service**, and from the **Available Services** list, select **IBM Bluemix DevOps Services**.
4. Type your IBM id and password.
5. Select the **Active** check box.   
 **Tip:** If you need to disable work item linking later, return to this page and clear the **Active** check box.  
![Configuration settings for the IBM Bluemix DevOps Services hook][6]

6. Click **Add service**.

You can now link work items to your commits. The next time that you commit a change, type a keyword and the work item's number in the commit comment; for example, `task 530`. When you push the change, a link to the change set is generated on the work item's **LINKS** tab. For a list of valid keywords, see ["Testing the hook"](#create_work_item).
![Commit comment with work item keyword and number][7]

<a name='create_work_item'></a>
## Testing the hook

To test your hook, create a work item and commit a change to your code.

1. On the DevOps Services project's Overview page, click **TRACK & PLAN**.
2. In the **Create a work item** field, type a summary and any work item attributes that you need.
3. Click **CREATE**.
4. Note the task number so that you can add it to your comment when you commit your change.
5. Make a change to one of the files in your GitHub repo. This example uses the DevOps Services Web IDE, but you can use any editor.
6. Add a commit comment that includes a work-item keyword and number. 
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
   In this example, the keyword is `task` and number is `530`.
![Commit comment in Web IDE][8]
7. Commit and push the change.
8. Open your work item. On the **LINKS** tab, click the change set.   
![Work item link to the change set.][9]
9. View the commit on the Git Log page.   
![Commit on Git Log page][12]   
10. To view the changed file in GitHub, click **View in GitHub**.   
![View in GitHub link.][13]   
11. View the changes in GitHub.
![Changed file in GitHub.][10]

<a name='post_push'></a>
##Adding a link after a change is pushed

If you already pushed a change and need to link it to a work item, follow these steps:
1. Open your project's Overview page.
1. Click **GIT LOG**.
1. Open the commit.
1. Click **Link Work Item**.
1. Select the work item and click **OK**.

A link to the change set is listed on the work item's **LINKS** tab. You can review the commit details by clicking the change-set link on the work item. From there, you can view the changed files by clicking the GitHub links. ![Link to view changes in GitHub.][11]

<a name='builddeploy'></a>
##Build and deploy

You can configure a Build & Deploy pipeline to automate the deployment of the source in your GitHub repo to your app on Bluemix. After your pipeline is set up, you can request your deployments manually or configure them to run automatically when you push changes to your GitHub repo. For information about setting up a pipeline, [see the Build & Deploy reference](/docs/deploy/).



[1]: https://hub.jazz.net
[2]: images/githubDevOpsProject.png
[4]: images/githubSettings.png
[5]: images/githubHooks.png
[6]: images/githubServiceConfig2.png
[7]: images/githubComment.png
[8]: images/githubCommit.png
[9]: images/githubLink.png
[10]: images/githubChange.png
[11]: images/githublink.png
[12]: images/gitlogcommit.png
[13]: images/viewingithub.png


