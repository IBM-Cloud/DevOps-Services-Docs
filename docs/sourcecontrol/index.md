# Source control in Bluemix DevOps Services

###### Last updated: 4 March 2016

For your project's repository, you can choose one of three source control systems: a GitHub repo, a Git repo that is hosted on IBM&reg; Bluemix&trade;, or a Jazz source control management (SCM) repo that is hosted on Bluemix. You select a source control system when you create your project. 
* [GitHub](#github)
* [Git](#hostedgit)
* [Jazz SCM](#jazzscm)
* [Link a source control repository to an existing Bluemix app](#bluemix)

<a name='github'></a>
## GitHub
You can store your source code on this popular Git hosting service and use IBM&reg; Bluemix&trade; DevOps Services to develop and deploy your app to Bluemix. To learn more, [see the GitHub website](https://github.com/features).

If you want to store your code in a GitHub repo, you must have a GitHub account and give Bluemix access to your GitHub account. When you create a project, you can either create a GitHub repo or link to a repo that you already use. For more details, see these topics:

* [Setting up GitHub for Bluemix DevOps Services projects](/docs/githubhooks)
* [Git source control](/docs/git)

<a name='hostedgit'></a>
## Git

You can create a public or private Git repo that is hosted on Bluemix. You control access to the repo by adding members to your DevOps Services project.

If you want to store your source code in a hosted Git repo and you already have a local Git repo, create your DevOps Services project and then force push your local repo to the new hosted repo. 

For more information about using Git with DevOps Services projects, see these topics:

* [Setting up local clients to work with Git source control](/docs/gitclient)
* [Git source control](/docs/git)

<a name='jazzscm'></a>
## Jazz SCM
Jazz SCM works well with Eclipse and IBM Rational Team Concert&trade;. For information about using a Jazz SCM repo that is hosted on Bluemix, [see Setting up local Eclipse clients to work with Jazz SCM](/docs/jazz_scm_client).

## Create a Git repository for an existing Bluemix app

You can create a new Git repository and link it to an existing Bluemix app. On the app's Overview page, click **Add Git Repo and Pipeline**, or in the Bluemix Classic Experience, click **ADD GIT**. This does not populate the new repository with the running app's code. After the repository is created, you can check your source code into it from the Web IDE, or locally using your Git client of choice.
