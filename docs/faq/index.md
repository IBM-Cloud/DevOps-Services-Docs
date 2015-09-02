# FAQ
##### Last updated: 02 September 2015

Looking for more answers? Check out the [forum](https://developer.ibm.com/answers/smartspace/devops-services/), where you can ask questions and get advice from IBM developers and the IBM&reg; Bluemix&trade; DevOps Services community.
____

-   [I see IBM DevOps Services is now called IBM Bluemix DevOps Services. Can you tell me more?](#q1)
-   [How much does it cost?](#q2)
-   [What help resources are available?](#q17)
-   [Why can't I accept an invitation?](#invite)
-   [How do I change the email address of the DevOps Services account that is associated with my IBM id? ](#changeemail)
-   [Can I log in to DevOps Services from my Rational Team Concert desktop client or Git client?](#rtcgit)
-   [Can I connect my project to a GitHub repository?](#git)
-   [Can I remove DevOps Services access from my GitHub account?](#github_revoke)
-   [How can I troubleshoot errors in my GitHub service hooks?](#github_trouble)
-   [Why can't I use the Add Git link from the Bluemix console?](#git_link)
-   [Which Git data transfer protocols does DevOps Services support?](#protocols)
-   [My team doesn't develop code. Is DevOps Services right for us?](#q5)
-   [How do I report a bug?](#q7)
-   [How can I provide additional feedback?](#q8)
-   [How can I report abuse?](#q18)
-   [How can I see what's new?](#q19)
-   [When I try to deploy an app from the run bar, why does it fail in a yellow, "not synchronized" state?](#yellowrunbar)
-	[Where is the run bar?](#missingrunbar)
-   [Which browser should I be using?](#q20)

____

<a name="q1"></a>

### I see IBM DevOps Services is now called IBM Bluemix DevOps Services. Can you tell me more? 

IBM DevOps Services has a new name: IBM Bluemix DevOps Services. This change corresponds with the effort to align better with IBM Bluemix.

<a name="q2"></a>

### How much does it cost?

[Get pricing information](https://console.ng.bluemix.net/pricing/).

<a name="q17"></a>

### What help resources are available? 

You can find help resources for getting started and improving your skills on the [Docs page](/docs).

<a name="invite"></a>

### Why can't I accept my project invitation?

If you try to accept a project invitation but get a message that states `A problem occurred with the invitation`, one of these issues might have occurred:   
- The email address that is associated with your IBM id is different than the email address that the invitation was sent to.  To fix this issue, check your My IBM profile and your IBM Bluemix DevOps Services profile and make sure that they are both associated with the same email address.  

   * [IBM Profile](https://www.ibm.com/account/profile/us): Check the value in the **Email** field.
   * [Bluemix DevOps Services profile](https://hub.jazz.net/account/profile): On the left, click **PERSONAL INFORMATION**, and then check the value in the **Email** field.

- You are logged in to DevOps Services as a user who has a different email address. To fix this issue, log out and log back in as the user who the invitation was sent to. 

<a name="changeemail"></a>

### How do I change the email address of the DevOps Services account that is associated with my IBM id?

1. Go to your [DevOps Services profile](https://hub.jazz.net/account/profile). 
2. On the left, click **PERSONAL INFORMATION**, and then update your email address.


<a name="rtcgit"></a>

### Can I log in to DevOps Services from my Rational Team Concert desktop client or Git client? 

Yes, but you need an alias. An _alias_ is a publicly visible short name. The first time you log in to DevOps Services from a web browser, you link your IBM id with an alias. If you have a Jazz ID, that is used as your alias. 

After your IBM id and alias are linked, you can log in to DevOps Services from a browser or your IBM&reg; Rational Team Concert&trade; client, and you can access a Git repository from your local Git client.

* To log in from a browser, use your IBM id and IBM password. 
* To log in from your Rational Team Concert client, use your alias and IBM password.
* To access a Git repository from your local Git client, use your alias and IBM password.      
   For example: `https://your_alias:your_IBM_ID_password@hub.jazz.net/alias/project_name`     
   For more information, see [Git source control](/docs/git).

<a name="git"></a>

### Can I connect my project to a GitHub repository? 

Yes. When you create a project, select the option for GitHub and select your GitHub repository from the list.

In DevOps Services, you can track and plan the work you'll store in your GitHub repository. For instructions to configure GitHub to update your work items when you push changes, see [Linking work items in Bluemix DevOps Services to commits in GitHub](/docs/githubhooks).

You can also edit the code that is stored in your GitHub repository by using the Web IDE. When you want to start coding, navigate to your project and click **EDIT CODE** at the top of the page.

![EDIT CODE button][1]

Your GitHub repository is automatically cloned for you, and your files are shown in the directory in the DevOps Services Web IDE. 

When you're ready to deploy your changes, click **BUILD & DEPLOY** and set up your pipeline stages. For instructions, see the [Build & Deploy reference](https://hub.jazz.net/docs/reference/deploy/).

<a name="github_revoke"></a>
### Can I remove DevOps Services access from my GitHub account?

Yes. You can revoke DevOps Services access from your GitHub account or switch to a different GitHub account.   

To remove DevOps Services access to your GitHub account:
1. Log in to your GitHub account.
2. Go to the [GitHub Applications page](https://github.com/settings/applications).
3. In the list of authorized applications, find IBM Bluemix DevOps Services and click **Revoke**.

The next time you create a DevOps Services project that uses a GitHub repository, you are prompted to authorize with GitHub. Before you can authorize your DevOps Services project, you must be logged in to the GitHub account that you want to use.

<a name="github_trouble"></a>
### How can I troubleshoot errors in my GitHub service hooks?

If you configured your GitHub project to create work item links when you push commits and the links aren't working as expected, follow these steps to find the problem:

1. In your GitHub repo, on the right, click **Settings**.
![GitHub settings link.][2]
1. Click **Webhooks & services**.
![GitHub web hooks and services link.][3]
1. To view the message, hover over the IBM Bluemix DevOps Services status icon.
![Error message on service hook.][4]
1. Resolve the error according to the GitHub message.      
1. To verify that the fix worked, commit and push another change or from the service page for IBM Bluemix DevOps Services, click **Test service**.
![GitHub Test service button][5]
1. Verify that there are no errors by checking the status icon again.
![Status icon without errors.][6]

For information, see [Setting up GitHub for Bluemix DevOps Services projects](/docs/githubhooks).

<a name="git_link"></a>

### Why can't I use the ADD GIT link from the Bluemix console?

See [Cannot add Git repository](https://www.ng.bluemix.net/docs/#troubleshoot/index-gentopic4.html#cannot_addgit).


<a name="protocols"></a>

### Which Git data transfer protocols does DevOps Services support?

DevOps Services supports the HTTPS protocol for Git URLs. The SSH and Git protocols are not supported.
 
<a name="q5"></a>

### My team doesn't develop code. Is DevOps Services right for us? 

Absolutely. You can plan, define requirements, track tasks, and collaborate on any type of project.

<a name="q7"></a>

### How do I report a bug? 

[Report a bug here](https://hub.jazz.net/ccm01/web/projects/idsorg | Bluemix DevOps Services#action=com.ibm.team.dashboard.viewDashboard).

<a name="q8"></a>

### How can I provide feedback?

We love feedback. If you have a suggestion, [share your idea in the IBM Bluemix DevOps Services project](https://hub.jazz.net/ccm01/web/projects/idsorg | Bluemix DevOps Services#action=com.ibm.team.dashboard.viewDashboard).
If you need help, [ask a question in the forum](https://developer.ibm.com/answers/smartspace/devops-services/).

<a name="q18"></a>

### How can I report abuse? 

To report an instance of abuse of DevOps Services or a violation of the Terms of Use, send an email to [hub@jazz.net](mailto:hub@jazz.net?Subject=Reporting%20abuse%20of%20JazzHub&Body=Please%20include%20the%20following%20information%3A%0A%0A%20-%20Your%20email%20address%3A%0A%20-%20The%20URL%28s%29%20where%20you%20observed%20abuse%20on%20Jazzhub%3A%0A%20-%20Any%20other%20details%20you%20feel%20could%20help%20in%20our%20investigation%20of%20this%20issue%3A%0A%0AThank%20you%20for%20your%20report%2C%0A%0AThe%20JazzHub%20Team). 
Provide as much information as possible, including the URL where you see the abuse and a description of the nature of the problem. [You can read the Terms of Use here](/terms). 

<a name="q19"></a>

### How can I see what's new?

[Visit the What's New page](/whatsnew).

<a name="yellowrunbar"></a>
### When I try to deploy an app from the run bar, why does it fail in a yellow, "not synchronized" state?

The app that you are deploying has the same route as another app that is running.  To fix this issue, change the route to be unique.

<a name="missingrunbar"></a>
### Where is the run bar?

If you don't see the run bar in the Web IDE, one of these issues occured:

1. DevOps Services isn't identifying your project as a project.
   * Fix: In your project's root directory, create a `project.json` file.
2. DevOps Services failed to determine which folder your app is in.
   * Fix: If your app is in a directory other than the project root, do one of these steps:
      * In your project's root directory, create a `manifest.yml` file.  Then edit the file so that it points to the location of your app.		
For example: `path: path_to_your_app`
      * Move your app so that it is in your project's root directory.
* 3. DevOps Services does not detect that your app is a Node.js app.
   * Fix: In the app folder of your project, create a `package.json` file.

<a name="q20"></a>
### Which browser should I use? 

DevOps Services supports the latest version of these browsers:

* Chrome
* Firefox
* Internet Explorer
* Safari

[1]: /docs/faq/images/toprightnav.gif
[2]: images/githubSettings1_small.png
[3]: images/githubHooks1_small.png
[4]: images/troubleshoothook1_small.png
[5]: images/githubTestService_small.png
[6]: images/githubResolved_small.png


