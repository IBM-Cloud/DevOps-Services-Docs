#Develop with Bluemix Live Sync and Node.js

Last modified: 22 April 2015

Time: 30 minutes

If you are building a Node.js app, you can quickly update it on IBM&reg; Bluemix&trade; and develop as you would on the desktop by using Bluemix Live Sync. You can use Bluemix Live Sync on the command line, through the Desktop Sync feature, and in the Web IDE, through the Live Edit feature. You can also [use Bluemix Live Sync to debug Node.js apps][2]. [Learn more about Bluemix Live Sync][4]. 

In this tutorial, you deploy a Node.js app and then update it by using IBM&reg; Bluemix&trade; DevOps Services and Bluemix Live Sync. You can see the changes to your running Bluemix app immediately, without waiting for redeployment.

* [Learning objectives](#objectives)
* [Before you begin](#prereq)
* [Create a Node.js app from a Bluemix starter](#create)
* [Connect the Node.js app instance to DevOps Services](#connect)
* [Edit the app by using the Web IDE and Bluemix Live Sync](#edit_ide)
* [Edit the app locally by using Bluemix Live Sync](#edit_local)
* [Summary](#summary)
* [Next steps](#nextsteps)


---
<a name='objectives'></a>
##Learning objectives

* Create an app in Bluemix by using the SDK for Node.js starter pack.
* Create a Git repository for the app.
* On the Web IDE run bar, create a launch configuration.
  * Enable the Live Edit feature.
  * View code changes in the running app.
* From the command line, enable the Live Edit feature.
  * View code changes in the running app.

---
<a name='prereq'></a>
##Before you begin 
* [Sign up for DevOps Services](https://hub.jazz.net/register). When you sign up, you'll create an IBM id, create an alias, and register with Bluemix.
* Download and install the Bluemix Live Sync command-line interface for [Windows][1] or for [Mac OS X](http://livesync.mybluemix.net/downloads/BluemixLive.pkg).

**Important:** The Live Sync command-line interface is available only for Windows 7 and 8 and Mac OS X version 10.9 or later. [Learn more about the Live Sync command-line interface][16].

---
<a name='create'></a>
##Create a Node.js app from a Bluemix starter

First, you need an app to edit. Bluemix provides everything you need to get started:

1. Sign in to Bluemix.
2. Click **CREATE AN APP**.
3. Click **WEB**.
4. For the starter, select the **SDK for Node.js**, and then click **CONTINUE**.
5. Name the app, and then click **FINISH**.
6. On the left side of the page, under your app's name, click **Overview**. 

After a few moments, your app is running on Bluemix. To view it, click the URL beside Routes.

![Sample starter app][14]

---
<a name='connect'></a>
##Connect the Node.js app to DevOps Services

Next, create a Git repository that is hosted by DevOps Services and associate the repository with your app instance. The repository will be populated with the code from the SDK for Node.js starter.

1. On your app's Overview page, click **ADD GIT**.
![Clicking ADD GIT][6]
2. On the Create Git Repository Page, confirm that the **Populate the repository with the starter application package and enable Delivery Pipeline (Build & Deploy)** check box is selected. Click **CONTINUE**.
3. When the repository is initialized, close the Create Git Repository window. 

Your app instance is now associated with a DevOps Services project and Git Repository.

---
<a name='edit_ide'></a>
##Edit the app by using the Web IDE and Bluemix Live Sync

<a name='edit_ide_create'></a>
###Create a launch configuration to use with Bluemix Live Sync

Launch configurations define the settings that the Web IDE uses to deploy your app to Bluemix. By default, DevOps Services deploys to the Bluemix app that it was associated with when you created the app. To test your changes before committing to them, create a launch configuration.

1. On your app's Overview page, click **EDIT CODE**. The Web IDE opens. 
2. In the run bar, click the menu and then click the **Create a new launch configuration** icon.
![Clicking Plus icon in the run bar][7]
3. On the Edit Launch Configuration menu, indicate that this is a test version of your app by adding text to the app's name and host. For example, in the following configuration, `–live` is added to the name and host. DevOps Services provides a launch configuration name automatically.
![Edit Launch Configuration menu][8]
4. Click **SAVE**. 

You can use the new launch configuration to edit your project through Bluemix Live Sync.

<a name='edit_ide_live'></a>
###Edit in Live Edit mode

When you’re forced to redeploy to Bluemix each time you make a change, you waste valuable development time. To quickly make changes to your project and preview the changes, turn on Live Edit mode in the DevOps Services Web IDE.

1. On the run bar, click the menu and select your new launch configuration.
  * The new launch configuration has the name of the original launch configuration with "-1" appended to it.
2. Turn on **Live Edit**. The code in your workspace is deployed to Bluemix according to the new launch configuration.
![Clicking the Live Edit button][9]
3. When redeployment finishes, the deployment status icon turns green and the phrase "`(running: live edit)`" is shown beside your launch configuration on the run bar.
4. On the run bar, click **Open the application URL**. The Bluemix Live Sync app opens in a new browser window.
![Clicking the Open the application URL button][10]

Edit the starter app:

1. In the Web IDE editor, expand the **public** folder. Expand **stylesheets** and open the `style.css` file.

2. In the `h1` rule set, increase the `font-size` value to `4em`.
![The code editor][11]

3. Refresh the browser window that shows the running app. The header size doubles.
![4em header shown in running sample app][12]

**Note:** Changes to static file types, such as CSS and HTML, are reflected when you refresh your browser. If you make changes to a Node module, you must first click **Quick Restart** on the run bar to see your changes in Live Edit mode.

Turn off Live Edit mode.

You edited the project in the Web IDE and previewed the result of your changes without redeploying to Bluemix. Excellent!

---
<a name='edit_local'></a>
##Edit the app locally by using Bluemix Live Sync

Live Sync isn't just available for work done in the Web IDE. You can also make changes on your local environment and see them previewed on Bluemix by using the Live Sync command-line tool, "bl," to synchronize the desktop with your project workspace. Before you follow the next steps, be sure to [download and install the Live Sync command-line interface][1].


<a name='edit_local_download'></a>
###Synchronize your local environment with Bluemix

Configure your local environment to work with Bluemix Live Sync:

1. Open a command prompt.
2. Log in to Bluemix by typing your IBM id and password:
```
bl login -u user_name -p password
```
3. View a list of your Bluemix projects: 
```
bl projects
```
4. Synchronize your local environment with your project on Bluemix:
```
bl sync projectName -d localDirectory
```

Where `projectName` is your Bluemix app's name and `localDirectory` is the path to a local workspace.

By synchronizing your local environment with Bluemix, you populate `localDirectory` with the files from your Node project. When you are finished making changes, type `q` to end synchronization.

###Enable the Desktop Sync feature and make an edit

1. In a second command prompt, enable the Desktop Sync feature:
```
cd localDirectory
bl start
```
2. Use the launch configuration that you created in the Web IDE. After you select the launch configuration, Desktop Sync is enabled in your local environment. View the App URL, Debug URL, Manage URL, and Live Sync state in the second command prompt window.

3. Refresh the browser, and verify that you can see the changes that you saved to local, static files in your Debug instance. 

4. In your favorite editor, find the `h1` rule set and add this declaration: `color: #00aed1`. Save the change and view it. If you update the Node module, to see your change, restart the Debug instance by entering `bl start --restart` in the command prompt.

###Disable the Desktop Sync feature:

If you made both of the changes, the header on your app's page is now big and blue. Nice work!
![Big blue header in sample app][13]

Disable the Desktop Sync feature:
1. In the second command prompt, enter `bl stop`.
2. In the first command prompt, press `q`.

If you were working on a real project and you liked the way the app looked, you would commit your changes in Git. Then, the Pipeline in DevOps Services would deploy your updated app to Bluemix.

---

<a name='summary'></a>
##Summary

You used Bluemix Live Sync to edit a Node.js project both in the cloud and locally and to preview your changes along the way.

<a name='nextsteps'></a>
##Next steps

After you have tested your application, [learn more about setting up automated build and deploy processes](/docs/reference/deploy/). 

[1]: https://jazz.net/pub/bluemixlive/blive_setup.msi 
[2]: https://www.ng.bluemix.net/docs/#manageapps/bluemixlive.html#bluemixlivedebugger
[3]: https://console.ng.bluemix.net/
[4]: https://www.ng.bluemix.net/docs/#manageapps/bluemixlive.html
[5]: /tutorials/livesync/images/default_h1.png
[6]: /tutorials/livesync/images/add_git.png
[7]: /tutorials/livesync/images/run_plus.png
[8]: /tutorials/livesync/images/edit_lc.png
[9]: /tutorials/livesync/images/click_live_edit.png
[10]: /tutorials/livesync/images/click_open_url.png
[11]: /tutorials/livesync/images/editor.png
[12]: /tutorials/livesync/images/4em_h1.png
[13]: /tutorials/livesync/images/big_blue_h1.png
[14]: /tutorials/livesync/images/default_h1.png
[15]: /tutorials/livesync/images/click_play.png
[16]: https://www.ng.bluemix.net/docs/#manageapps/bluemixlive.html#live_sync_cli
