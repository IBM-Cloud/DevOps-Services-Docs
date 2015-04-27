#Developing with Git in the Bluemix DevOps Services Web IDE

Last modified: 31 March 2015

Time estimate: 30 minutes

If you want to learn more about managing your Git repository, an open source code management system, with the IBM® Bluemix&trade; DevOps Services Web IDE, complete this tutorial. The tutorial doesn't cover all of the possible Git commands in the DevOps Services Web IDE, but you can practice creating a change on a separate branch, testing the change, and adding the change to the master branch. If you need help with specific commands, [see the Git reference](/docs/reference/git).  If you want to try to work locally by using the command line, [see Setting up local clients to work with Git source control](/docs/reference/gitclient).


 * [Learning objectives](#objectives)
 * [Before you begin](#before_you_begin)
 * [Explore and clone the sample project](#fork_a_project)
 * [Create a branch](#create_a_branch)
 * [Deploy a new Bluemix app](#deploy_a_new_bluemix_app)
 * [Change and test the code](#change_and_test_the_code)
 * [Deliver a change to the repository](#deliver_a_change_to_the_repository)
 * [Rebase to add changes to the master branch](#add_changes_to_the_master_branch)
 * [Summary](#summary)


---
<a name='objectives'></a>
##Learning objectives

* Create a version of an app in your space by clicking the Deploy to Bluemix button.
* Create a branch in the Web IDE to deliver code to.
* Deploy the contents of your workspace to an app by using the run bar.
* Edit code in the Web IDE.
* Deliver a changed file to the branch in the Web IDE.
* Deliver a changed file to the master branch in the Web IDE.


---
<a name='before_you_begin'></a>
##Before you begin

To complete this tutorial, you must [register with DevOps Services by creating an IBM ID, creating an alias, and registering with Bluemix](https://hub.jazz.net/register).

---
<a name='fork_a_project'></a>
##Explore and clone the sample project


Start by [exploring the live version of the sample project you will work with](http://yummyration.mybluemix.net/). The app is a website for a catering service. 

Next, explore the contents of the  [Yummy Ration project](https://hub.jazz.net/project/ibmdevopsservices/YummyRation/overview). This Node.js app uses a Git repository, and includes a Grunt build file.

After you are familiar with the project, click the button below to create your own copy of it by cloning and deploying it:


<a target="_blank" href="https://bluemix.net/deploy?repository=https://hub.jazz.net/git/ibmdevopsservices/YummyRation"><img src="images/bigButton.png" alt="Deploy to Bluemix"></a>


After the project is forked and the deployment is complete, click **EDIT CODE** to continue.

---
<a name='create_a_branch'></a>
## Create a branch
When you work with many people or want to test different ideas, a common practice is to work in different branches.

1. Click the **Git Repository** icon <img src="images/gitrepository.png"  align="bottom" style="display: inline; margin: 0px; border-style: none; margin-bottom: -10px;">.

1. Click the **REFERENCE field**.

1. Click **NEW BRANCH**. For the name, enter `testbranch`. Click **Submit**.
![New branch dialog][10]

1. Under **local**, next to the `testbranch` branch, click the **Checkout** icon.

1. Confirm that the value in the **REFERENCE** field is "testbranch => origin/testbranch [New Branch]".
![testbranch reference][11]

1. Beneath the **REFERENCE** field, click the **PUSH** button to populate `origin/testbranch` with the current contents of your local workspace.

---
<a name='deploy_a_new_bluemix_app'></a>
##Deploy a new Bluemix app

To see the changes that you make to your code, create a Bluemix app and deploy the changes to the app. To create an app from within the DevOps Services Web IDE, you edit the manifest.yml file to direct deployments to a different Bluemix app.

1. To view your code, click the **Show Current Folder** icon <img src="images/showcurrentfolder.png"  align="bottom" style="display: inline; margin: 0px; border-style: none; margin-bottom: -10px;">.

1. In the project side panel, click the `manifest.yml` file.

1. In both the **host** and **name** fields, enter the same unique host name.  
**Note**: The host name must be unique through all of Bluemix.
![Change the host and name entries in the manifest.yml file][1]

1. Click **File**, and then click **Save**.

1. Click the status area on the run bar. Click **+**, and then review the contents of the Edit Launch Configuration window.
![The dropdown menu in the Run Bar][33]
 * Make sure that the information about the organization and space are as you expected.
 * Make sure that the displayed host and app name match the contents of the `manifest.yml` file

6. Click **SAVE**.

7. On the run bar, click the Play icon. After the deployment succeeds, click the **Open the application URL** button to see the YummyRation project page.
![Play button in the Run Bar][34]
![Open URL button in the Run Bar][31]

Leave this page open; you'll need it in a moment.

---
<a name='change_and_test_the_code'></a>
## Change and test the code

1. Return to your YummyRation project page in DevOps Services.

1. Near the run bar, click the **Live Edit** button. Let the app deployment finish.
  * Bluemix Live Sync allows you to quickly preview changes to Node.js apps in Live Edit mode. When you update your static files with Live Edit turned on, you can refresh your web app's browser window to see those changes reflected seconds after you make them. For more information on Bluemix Live Sync, [see the Bluemix Live Sync documentation][14].

2. In the file explorer, next to `views`, click the **>** to expand the contents of the folder. Then, click **home.jade**.

3. Locate the phrase "We deliver delicious fresh cooked food for your next dinner, cocktail, or party." Change it to `We deliver delicious, freshly cooked food for your next dinner or gathering.`
![Changed Fisherman's Platter code block][5]

4. Switch to the browser window where you have the YummyRation page open. Refresh it to see your change.
![Runbar at status green with Upen URL button highlighted][31]

![New subheader][7]

That looks better! Click the **Live Edit** button again to stop using Bluemix Live Sync.

---
<a name='deliver_a_change_to_the_repository'></a>
##Deliver a change to the repository

You save your changes to your DevOps Services project.  Because this project uses a Git repository, you first make a commit to record all of your changes to your local branch. Then, you push the commit to the remote branch.

1. Return to your YummyRation project page in DevOps Services.

1. Click **Git Repository**.

1. In the Working Directory Changes panel, select the check boxes next to `manifest.yml` and `views/home.jade`.

1. In the **Enter the commit message** field, enter a descriptive commit message, like `Add deployment information to manifest and updated home page`.
![Sample commit message][6]

1. Click **COMMIT** to commit your changes to your local repository.

1. View your commit in the Active Branch (testbranch) panel under OUTGOING.
![Outgoing commit][9]

1. Click **PUSH** to copy your commit to the remote repository.

---
<a name='add_changes_to_the_master_branch'></a>
##Rebase to add changes to the master branch

After you confirm a change in a test branch, you can introduce its code to the master branch.  To do so, you copy the contents of the testbranch branch to the master branch by using a rebase command. When you use the rebase command, you place the commits from the testbranch branch after the commits on the master branch.  For more information about the rebase command, [review the official Git documentation](http://git-scm.com/book/ch3-6.html).

To rebase, you must compare the contents of one branch to another by modifying the references.

1. Click the **REFERENCE** field.
![The Git Repository reference field][15]

1. Next to local, click **>** to expand the list of local branches.
![Click local branch][16]

1. Next to the local master branch, click the **Checkout** icon.
![Checkout master branch][13]

1. Click the **REFERENCE field** again.

1. Next to local, click **>** to expand the list of local branches again.

1. Compare the contents of the local master and testbranch branches by clicking the **testbranch** row.
![Comparing testbranch to master][12]

1. Click the **Rebase** icon <img src="images/rebase.png"  align="bottom" style="display: inline; margin: 0px; border-style: none; margin-bottom: -10px;">.

1. Click the **REFERENCE field** again.

1. Next to origin, click **>** to expand the list of remote branches.

1. Click the **master** row to compare the contents of the local copy of the master branch and the remote copy of the master branch. 

1. Confirm that the commit that you originally made on the testbranch branch is visible under OUTGOING.

1. Click **PUSH**. Your commit moves to the HISTORY panel.

---
<a name='summary'></a>
##Summary

You forked a project and manually deployed to a Bluemix app. You made a branch, completed changes to your code in the Web IDE, and committed your changes. You also combined contents of branches.


[1]: images/manifest.png
[2]: images/forkproject.png
[3]: images/manualdeployment.png
[4]: images/manualdeploymentpanel.png
[5]: images/fishermansfeast.png
[6]: images/commitmessage.png
[7]: images/newffprice.png
[8]: images/oldffprice.png
[9]: images/outgoingcommit.png
[10]: images/newbranch.png
[11]: images/testbranchreference.png
[12]: images/mastertotestbranch.png
[13]: images/arrowbylocal.png
[14]: https://www.ng.bluemix.net/docs/#manageapps/bluemixlive.html
[15]: images/reference.png
[16]: images/local.png
[18]: https://developer.ibm.com/answers/questions/?community=devops-services (Bluemix DevOps Services forum)
[19]: mailto:hub%40jazz.net
[20]: /docs
[28]: https://developer.ibm.com/answers/smartspace/devops-services/
[30]: /docs
[31]: images/runbar_url.png
[32]: images/runbar_play.png
[33]: images/launch-configs-callout.png
[34]: images/runbar_click_play.png
