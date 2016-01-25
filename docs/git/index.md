#Git source control 

###### Last updated: 19 November 2015

If you store your code in a Git repository that is hosted by IBM® Bluemix&trade; DevOps Services, you can work with code in a Git terminal or in a web IDE. You can also use GitHub source control with DevOps Services projects. If you work on a local workstation, you can use Git terminal commands to edit the contents of your Git repo. If you use the Web IDE, you don't need the Git terminal: you can run many common Git commands in the Web IDE. 

For information about using a GitHub repo, [see Setting up GitHub for DevOps Services projects][8]. For a complete Git reference, [see the official Git documentation][6].

To access Git commands from the Web IDE, click the **Git Repository** icon <img class="inline" src="./images/gitrepository.png" alt="Git Respository icon">.

**Note:** For a Git repo that is hosted by DevOps Services, the file size limit is 100 MB.

No matter where you code, you can use this quick reference to do common tasks.
<a name="top"></a>
##[Repositories](#repositories)
* [Set up a local Git repo](#set_up_a_local_git_repository)
* [Use an existing Git repo with DevOps Services projects](#existing_git_repository)
* [Replace your origin repo](#replace_your_origin_repository)
* [Integrate local commits in the Web IDE](#integrate_local_commits_in_the_web_IDE)
* [Work with Git submodules](#git_submodules)

##[Branches](#branches)
* [Create a local branch](#create_a_local_branch)
* [Work on a local branch](#start_working_on_a_local_branch)
* [Update a local branch with changes from the remote branch](#update_a_local_branch_with_changes_from_the_remote_branch)
* [Delete a local branch](#delete_a_local_branch)
* [Force push local changes to a remote branch](#force_push)
* [Discard unstaged changes from the active local branch](#discard_changes)

##[Commits](#commits)
* [Commit files and push to the remote branch](#commit_files_to_the_remote_branch)
* [Link a commit to a work item](#link_commit)
* [View the commit history](#view_the_commit_history)
* [Compare changes that a commit introduced](#compare_changes_that_a_commit_introduced)
* [Modify the last commit](#modify_the_last_commit)
* [Tag a commit](#tag_a_commit)
* [Change the committer name and email address](#change_the_committer_name_and_email_address)
* [Revert a commit](#revert)

##[Change integration](#change_integration)
* [Merge changes](#merge_changes)
* [Resolve a merge conflict](#resolve_a_merge_conflict)
* [Rebase branches](#rebase_branches)
* [Resolve a rebase conflict](#resolve_a_rebase_conflict)

##[Git terminal only](#git_terminal)
* [Troubleshoot authentication issues by using the push command](#troubleshoot_authentication_issues_by_using_the_push_command)
* [Delete a branch from origin](#delete_a_branch_from_origin)

<a name="repositories"></a>
##Repositories

<a name="set_up_a_local_git_repository"></a>
### Set up a local Git repo

#### DevOps Services Web IDE
When you use a Git repo with your DevOps Services project, you work with both your local and remote repos through the Web IDE.

1. Click **EDIT CODE** <img class="inline" src="./images/editcode.gif" alt="Edit code button"> and start coding!

#### Git terminal
If you want to code and test locally, set up a local repo.

**Before you begin**: If Git is not installed on your computer, [follow these instructions][1].

1. Determine which directory to store your local repo in. If necessary, you can create a directory.

1. By using your terminal, move to the directory.  

1. [Go to DevOps Services][2]. On the My Projects page, click your project's name.

1. From your project's Overview page, click **Git URL** and copy the URL.  
**Note**: DevOps Services supports the HTTPS protocol for Git URLs. The SSH and Git protocols are not supported.

1. In your terminal, type `git clone `, paste your Git URL, and press Enter.

1. When you are prompted, enter your alias and password.  
**Note**: If you are not prompted for your password, do not continue.  Delete your cloned repo
and repeat the steps by using a modified repo address: `https://your_alias:your_IBM_ID_password@hub.jazz.net/alias/project_name`.

1. After your repo replicates, move into your new local repo.  

<a name="existing_git_repository"></a>
### Use an existing Git repo with DevOps Services projects 
If you already have a Git repo, you can use it with a DevOps Services project.

#### Setting up a new DevOps Services project with an existing Git repo
1. [Go to DevOps Services][2]. On the My Projects page, click **CREATE PROJECT**.
2. Name your project.
3. Click **Create a new repository**.
4. Click **Create a Git repo on Bluemix**.    
**Note:** Do not select the **Initialize the repository with a README and license template** check box. 
5. Select or clear the other project options as needed.
6. Click **CREATE**.
7. Open a command-line window and change to your Git repo directory.
8. Push the contents of the repo by typing these commands:         
       git remote add new_repo https://hub.jazz.net/git/your_alias/project_name     
       git push -u new_repo master     

#### Replacing a DevOps Services Git repo with another Git repo
If you have a DevOps Services project with an initialized Git repo and you want to use another Git repo instead, you must be the owner or an administrator of the project. To overwrite the repo, add a `-f` (force push) to the `git push` command, like this: `git push -f -u new_repo master`.

**Important:** A force push replaces your original DevOps Services Git repo; that repo cannot be recovered.
       
<a name="replace_your_origin_repository"></a>
### Replace your origin repo

#### DevOps Services Web IDE

1. Click the configuration icon <img  class="inline" src="./images/configuration.png" alt="Configuration icon">.

1. In the remote.origin.url pane, click the edit icon <img  class="inline" src="./images/editconfiguration.png" alt="Edit icon"> to edit the configuration entry.

1. In the **value** field, paste your new repo URL. Click **Submit**.

1. Click the **REFERENCE** list and expand **origin**. Click the fetch icon <img class="inline" src="./images/fetchfromremote.png" alt="Fetch icon"> to fetch from the remote repo.

#### Git terminal

1. Type `git remote set-url origin <repository_url>` and press Enter.


<a name="integrate_local_commits_in_the_web_IDE"></a>
###Integrate local commits in the Web IDE

When you work in the Web IDE, both your local and remote repos are hosted on the cloud. To view the changes that you made in a local repo that is stored outside of DevOps Services, you must sync to your remote repo.

1. Click **SYNC**. Sync combines the fetch, rebase, and push commands.


<a name="git_submodules"></a>
###Work with Git submodules

If your DevOps Services project uses a Git repo and you want to add or use another repo in the project, add a Git submodule. A submodule is a Git repo's clone that is within a subdirectory of another repo. You can use submodules to include projects that are developed by third parties or projects that you are developing separately.

#### Add a Git submodule

1. In the Web IDE, click the **Repository** menu.
2. Next to the repo to add a submodule to, click the **Add Git Submodule** icon <img class="inline" src="./images/addsubmodule.png" alt="Add Git Submodule">.
3. Type the repository URL of the new submodule.
4. Click **Submit**.

The submodule is placed in a subdirectory of your initial repo.

#### Initialize nested submodules

If you add a submodule that contains nested submodules, they are shows as unknown repositories in the **Repository** menu and as empty folders in the Web IDE.  You must initialize the nested submodules:

1. From the **Repository** menu, find the parent repo of the submodules..
2. Click the **Sync** icon <img class="inline" src="./images/syncsubmodule.png" alt="Sync Submodule">, and then click the **Update** icon <img class="inline" src="./images/updatesubmodule.png" alt="Update Submodule">.

#### Commit and push submodule changes

When you update a submodule, you must push the changes to the submodule and to all parent repos.

1. From the **Reference** menu, check out the branch to commit to.  The submodule is initially in Detached Head state.
2. Commit and push the changes. These changes are reflected in the parent repo.

#### Remove a submodule

To remove a submodule, click the **Repository** menu.  Next to the submodule to remove, click the **Remove submodule** icon <img class="inline" src="./images/deletesubmodule.png" alt="Delete Submodule">.

[Back to top](#top)

<a name="branches"></a>
##Branches

<a name="create_a_local_branch"></a>
### Create a local branch

#### DevOps Services Web IDE
1. Click the **REFERENCE** list.

1. Click **NEW BRANCH**.

2. Type your branch name, and then click **Submit**.

#### Git terminal
1. Type `git branch <branchname>` and press Enter.

<a name="start_working_on_a_local_branch"></a>
### Work on a local branch

#### DevOps Services Web IDE
1. Click the **REFERENCE** list and expand **local**.

2. Next to the branch to modify, click the checkout icon <img  class="inline" src="./images/checkout.gif" alt="Checkout icon">.

1. Make sure that your selected branch is shown in the **REFERENCE** list.

#### Git terminal
1. To view your local branches, type `git branch -l` and press Enter.

2. Type `git checkout <branchname>` and press Enter.


<a name="update_a_local_branch_with_changes_from_the_remote_branch"></a>
### Update a local branch to include changes from the remote branch

#### DevOps Services Web IDE
1. Click **SYNC**.

1. If you encounter conflicts, [resolve them](#resolve_a_rebase_conflict).

####Git terminal
1. Type `git pull` and press Enter.

1. Enter your IBM id and password.

<a name="delete_a_local_branch"></a>
### Delete a local branch

#### DevOps Services Web IDE
1. Make sure that the branch to delete is not checked out. If that branch is checked out, [check out another branch](#start_working_on_a_local_branch).

1. Click the **REFERENCE** list and expand **local**.

2. Next to the local branch to remove, click **Delete** <img class="inline"  src="./images/delete.gif" alt="Delete icon">.

####Git terminal
1. Type `git branch -d <branchname>` and press Enter.

<a name="force_push"></a>
###Force push local changes to a remote branch

Overwrite the contents of a referenced remote branch with the contents of your active local branch.

**Important:** When you force push a local branch to a remote one, you might lose commits on the remote branch.

####DevOps Services Web IDE

1. In the Working Directory Changes section, in the Outgoing section, click the arrow next to **Push**. 
2. Click **Force Push Branch**.
3. Confirm the warning.

####Git terminal

1. Type `git push <origin> <remote branch> -f` and press Enter. 

<a name="discard_changes"></a>
### Discard unstaged changes from the active local branch

#### DevOps Services Web IDE
1. In the Working Directory Changes section, select the check box for each modified file that has changes you want to discard. 
2. Click the checkout icon <img class="inline"  src="./images/discard.png" alt="Checkout the selected files, discarding all changes">.

#### Git terminal
1. Type `git checkout -- path/to/file/filename` to discard changes to a file.

[Back to top](#top)

<a name="commits"></a>
##Commits

<a name="commit_files_to_the_remote_branch"></a>
### Commit files and push to the remote branch

#### DevOps Services Web IDE
1. In the Working Directory Changes section, select the check box for each file to commit.

3. In the **Enter the commit message** field, type a message that describes your changes.  
**Tip**: In the commit message, describe your changes well.

4. Click **COMMIT**.

5. Click **PUSH**.

#### Git terminal
1. Type `git status` and press Enter.

2. Review the changes to be committed. If all of your files are listed to be committed, proceed. To commit unstaged files, stage them first.

3. Type `git commit -m "<commit_message>"` and press Enter.
**Tip**: In the commit message, describe your changes well.

4. Type `git push` and press Enter.

<a name="link_commit"></a>
### Link a commit to a work item
If you work in a project that uses a Git repo on Bluemix, you can link a commit to a Track & Plan work item. If your repo is hosted on GitHub, you can link your commits to work items when you push, but first, [you must configure it on GitHub][7].

1. When you write your Git commit message, specify a work item in this format: *work item keyword number*.
 * For example, if you type `Implements story 32`, you link the commit to story item 32.
 * Valid work item keywords: `adoption item, bug, defect, epic, impediment, item, retrospective, story, task, track build item,` and `work item`.
2. Push the commit. A linked commit is shown on the work item's **LINKS** tab.

If you push a commit and want to link it to work items later, you can link them on the Git Log page.

1. Open your project's Overview page.
2. Click **GIT LOG**.
3. Open the commit. 
4. Click **Link Work Item**. 
5. Select the work item and click **OK**.

<a name="view_the_commit_history"></a>
### View the commit history

####DevOps Services Web IDE
1. In the Active Branch section, expand **History** to see the commit history for that branch.

The commit history can also be viewed as a connected visual graph.

1. Click the graphical representation toggle icon <img  class="inline" src="./images/graphicalhistoryicon.png" alt="Graphical history icon">.

Once toggled, the commit history and any incoming or outgoing changes for the active branch are drawn as a connected graph.  The visual representation shows all of the commits and the branches they were made on.
 <img class="screen-shot" src="./images/visualhistoryexample.png" alt="Visual commit histroy">

####Git terminal
1. Type `git log` and press Enter. 

2. Navigate through the committer's commits.  
 * To view more entries, press Page Down.  
 * To view previous entries, press Page Up.

3. To stop viewing entries, press  Q.

<a name="compare_changes_that_a_commit_introduced"></a>
### Compare changes that a commit introduced

####DevOps Services Web IDE
1. View your commit history and locate the commit. For more information, [see View the commit history][4].

2. View the details of the commit by clicking it.

3. Next to a file, click the **>** and review the file's changes.  
**Note**: If a commit introduced a change to a line, the original line is shaded pink and the new line is shaded green.  Similarly, lines that were added by a commit are shaded green and lines that were removed by a commit are shaded pink.

####Git terminal
1. Type `git log -p` and press Enter.  
**Note**: To view only a certain number of commits, type `git log -p -<number_of_commits_to_view>`.

2. Navigate through the committer commits.
 * To view more entries, press Page Down.  
 * To view previous entries, press Page Up.

3. Review the changes.  
**Note**: If a commit introduced a change to a line, the original line is in red text and starts with a minus sign (-). The new line is in green text and starts with a plus sign (+).  Similarly, lines that were added by a commit are in green text and start with a +. Lines that were removed by a commit are in red text and start with a -.

1. To stop viewing entries, press  Q.

<a name="modify_the_last_commit"></a>
### Modify the last commit
**Note**: Do not modify your last commit after you push it to a remote repo.

####DevOps Services Web IDE
1. Select the check boxes for the items to add to the commit.

1. Select the **Amend Previous Commit** check box.

2. If necessary, enter a new commit message.

3. Click **COMMIT**.

####Git terminal
1. Check your status. As necessary, stage or unstage files.

2. Type `git commit --amend` and press Enter.

3. In your text editor, accept or modify the commit message.  
**Note**: To save your commit message and close Vim, which might be your default text editor, press Esc, type `:wq`, and press Enter.

<a name="tag_a_commit"></a>
### Tag a commit

####DevOps Services Web IDE
1. View your commit history and locate the commit. For more information, [see View the commit history][4].

2. View the details of the commit by clicking it.

2. In the commit pane, click **Create a tag for the commit** <img class="inline"  src="./images/tag.gif" alt="Create a tag for the commit">.

3. In the name field, type your tag text. Click **Submit**.

####Git terminal
1. View the commit history and obtain the ID of the commit to tag. For more information, [see View the commit history][4].

2. Type `git tag -a <tag_text> <commit_id>` and press Enter. 

<a name="change_the_committer_name_and_email_address"></a>
### Change the committer name and email address

#### DevOps Services Web IDE
1. Click the configuration icon <img class="inline" src="./images/configuration.png" alt="Configuration icon">.

3. Change the user email address and name by updating the user.email and user.name values. Click **Submit** to save each change.

#### Git terminal
To update your name and email address for a single repo:

1. Type `git config user.email "<your@email.com>"` and press Enter.

2. Type `git config user.name "<Your Name>"` and press Enter.

To update your name and email address for all repos:

1. Type `git config --global user.email "<your@email.com>"` and press Enter.

2. Type `git config --global user.name "<Your Name>"` and press Enter.

<a name="revert"></a>
###Revert a commit

Revert the changes that a commit has introduced into your active branch.

####DevOps Services Web IDE

1. Under History, select a commit. 

2. On the right side of the page, above the commit summary, click the revert icon <img class="inline" src="./images/revert.png" alt="Revert icon">. 

####Git terminal

1. Type `git revert <commit ID>` and press Enter.

[Back to top](#top)

<a name="change_integration"></a>
##Change integration

<a name="merge_changes"></a>
### Merge changes

When you need to deliver changes from a source branch to a destination branch, you must first merge. Typically, the source branch is the branch you made changes in, and the destination branch is your master branch.

####DevOps Services Web IDE
1. Decide which branches to merge.

2. Check out the destination branch. For more information, [see Work on a local branch][5].

 <img class="screen-shot" src="./images/destinationbranch.png" alt="Checkout destination branch">

1. Click the **REFERENCE** list, expand **local**, and click the name of the source branch. The changes from the source branch are shown in the Incoming section.

  <img class="screen-shot" src="./images/sourcebranch.png" alt="Changes from the source branch shown in the Incoming section">

1. In the Incoming section, click the **Merge** icon. 

 <img class="screen-shot" src="./images/mergeicon.png" alt="Merge icon in the Incoming section">

1. In the **REFERENCE** list, click the checkout icon next to the branch that you just merged the changes into.

  <img class="screen-shot"  src="./images/checkoutmaster.png" alt="Checkout from master">

1. If you want to deliver the changes, click **PUSH**. Otherwise, at this point, you can create a test deployment to make sure that everything is working as expected.

####Git terminal
1. Decide which branches to merge. 

2. Check out the destination branch. For more information, [see Work on a local branch][5].

3. Type `git merge <source_name>` and press Enter.

<a name="resolve_a_merge_conflict"></a>
### Resolve a merge conflict

####DevOps Services Web IDE
1. In the Changed Files pane, review the list of files that contain conflicts.

2. In the Web IDE, open each file that contains conflicts.

3. Resolve each conflicting change.  
**Note**: Delete all of the text that you do not want to keep. Each conflict is in this format:

		<<<<<<< HEAD  
		Text in checked out branch.  
		=======
		Text in merged branch.  
		>>>>>>> commit_ID_from_merged_branch
4. For each conflicting file, select the check box. Type a merge commit message, and click **COMMIT**.

####Git terminal
1. For the files that contain conflicts, review the Git message for the names.

2. In a text editor, open a file that contains conflicts.

3. Resolve each conflicting change, and then save the file.  
**Note**: Delete all of the text that you do not want to keep. Each conflict is in this format: 
 
		<<<<<<< HEAD  
		Text in checked out branch.  
		=======   
		Text in merged branch.  
		>>>>>>> merged_branch
4. Stage each file that you modified, and then commit the merge.

<a name="rebase_branches"></a>
### Rebase branches

####DevOps Services Web IDE
1. Decide which branches to rebase. You will rebase the contents of the source branch into the destination branch.

2. Check out the destination branch. For more information, [see Work on a local branch][5].

1. Click the **REFERENCE** list.

1. Click the name of the source branch.

1. In the Incoming section, click the rebase icon <img  class="inline" src="./images/rebase.gif" alt="Rebase icon">.

5. If you encounter conflicts, [resolve them](#resolve_a_rebase_conflict).

6. Repeat the previous step as many times as necessary to complete the rebase operation.

1. Click the **REFERENCE** list, expand **origin**, and click the name of the source branch.

1. Click **PUSH**.

#### Git terminal
1. Check out the branch to update by typing `git checkout <destination_branchname>` and pressing Enter.

2. Type `git rebase <source_branchname>` and press Enter.

3. If you encounter conflicts, [resolve them](#resolve_a_rebase_conflict).

5. Repeat the previous step as many times as necessary to complete the rebase operation.  
**Note**: To stop the rebase operation, type `git rebase --abort` and press Enter.

<a name="resolve_a_rebase_conflict"></a>
### Resolve a rebase conflict

####DevOps Services Web IDE
1. In the Working Directory Changes section, review the list of conflicting files.

2. In the Web IDE, open each file that contains conflicts.

3. Resolve each conflicting change.  
**Note**: Delete all of the text that you do not want to retain. Each conflict is in this format: 
  
		<<<<<<< HEAD  
		Text in checked out branch.  
		=======  
		Text in merged branch.  
		>>>>>>> commit_ID_from_merged_branch
4. In the rebase pane, select the check box for each corrected file and click **CONTINUE**.

####Git terminal
1. For the files that contain conflicts, review the Git message for the names.

2. In a text editor, open a file that contains conflicts.

3. Resolve each conflicting change, and then save the file.   
**Note**: Delete all of the text that you do not want to retain. Each conflict is in this format:     

		<<<<<<< HEAD  
		Text in checked out branch.  
		=======  
		Text in merged branch.  
		>>>>>>> merged_branch
4. Stage each file that you modified.

5. Resume the rebase operation by typing `git rebase --continue` and pressing Enter.

[Back to top](#top)

<a name="git_terminal"></a>
##Git terminal only

<a name="troubleshoot_authentication_issues_by_using_the_push_command"></a>
### Troubleshoot authentication issues by using the push command

When you push, if a "406 Not Acceptable" error occurs, complete these steps:

1. Upgrade your version of Git.

1. If you cannot upgrade Git, add your repo again but place your alias in the repo URL.  For example: `https://your_alias@hub.jazz.net/alias/project_name`.

<a name="delete_a_branch_from_origin"></a>
### Delete a branch from origin

Only project owners can delete branches from origin.

1. Type `git push origin :<your_branch_name>` and press Enter.

[1]: ../gitclient/#command_line_git
[2]: https://hub.jazz.net
[3]: https://hub.jazz.net/gitHook/ryehle/GitHubSentiment
[4]: #view_the_commit_history
[5]: #start_working_on_a_local_branch
[6]: http://git-scm.com/docs
[7]: ../githubhooks/#github_hook
[8]: ../githubhooks/
