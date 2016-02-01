#Creating a basic pipeline

###### Last updated: 1 February 2016

Time: 30 minutes

Follow the steps in this tutorial to create a simple Build & Deploy pipeline for a Java&trade; app by using IBM&reg; Bluemix&trade; DevOps Services. 

* [Learning objectives](#objectives)
* [Before you begin](#before_begin)
* [Fork a sample project](#fork_app)
* [Create build and deployment stages](#deploy_app)
* [Summary](#summary)
* [Next steps](#nextsteps)


<a name='objectives'></a>
##Learning objectives

* Create your own version of a DevOps Services project by forking it to your space.
* Create a build and deployment pipeline by using the Build & Deploy feature.




<a name='before_begin'></a>
##Before you begin

1. [Sign up for DevOps Services](https://hub.jazz.net/register). When you sign up, you'll create an IBM id, create an alias, and register with IBM&reg; Bluemix&trade;. 

2. Optional: Add the IBM Continuous Delivery Pipeline for Bluemix (the Delivery Pipeline service) to your Bluemix space so that you can continue to use it beyond the free monthly build time.  

   a. [Open the Bluemix Catalog](https://console.ng.bluemix.net/?ace_base=true/#/store/cloudOEPaneId=store). From the **Category** list, select **DevOps**.

   b. Click **Delivery Pipeline**.

   c. Leave the default settings as they are; then, click **CREATE**.




<a name='fork_app'></a>
##Fork a sample project

To quickly get started developing, fork a sample project named WordCounter. WordCounter is a Java app that uses Jazz&trade; source control management (SCM) and contains a manifest file for deploying to Bluemix. 

1. [Open the WordCounter project in DevOps Services](https://hub.jazz.net/project/ibmdevopsservices/WordCounter/overview). 
2. On the  Overview page, click **FORK PROJECT**. 
![Click Fork Project](/tutorials/jazzrtc/images/click_fork_project.png "Click Fork Project")
3. When you are prompted, enter a unique name for your project. Then, click **CREATE**.
![Create Project Dialog](/tutorials/jazzrtc/images/create_project.png "Create Project Dialog")

A new project is created with a copy of the code from the sample project. You're ready to build and deploy.

<a name='deploy_app'></a>
##Create build and deployment stages

**Important:** When you use the Build & Deploy feature with Bluemix, you can generate charges to your Bluemix account. However, you can complete this tutorial for free because a project is granted 60 minutes of free build time per month. For more information about Bluemix, DevOps Services, and charges, [see Configure Bluemix billing for Bluemix DevOps Services](/docs/reference/billing/).


1. Click **BUILD & DEPLOY**. 

2. Create a stage to build your app:

   a. On the Build & Deploy Pipeline page, click **ADD STAGE**. The Stage Configuration page opens.
![Click Add A Builder](/tutorials/jazzrtc/images/add_builder.png "Click add a builder")
    
    b. Click the default **MyStage** name and change the name of th stage to `Build`. 
    
    c. On the **INPUT** tab, enter the password for your IBM id.  You can use the default settings for the remaining fields, which use these configurations:
      * The input for the build is the master branch of the Git repository. 
      * The Build stage runs automatically every time a change is pushed to the repository. 
	
  d. On the **JOBS** tab, click **ADD JOB**. 
  
  e. Select **Build**, and for the builder type, select **Ant**.   
    
    f. In the **Working Directory** field, type the name of the folder that contains your code, which in this case is `WordCounter`. 
    
    g. In the **Build Archive Directory** field, type the name of the directory where the build output files are archived as part of the build result; for example, `WordCounterArchive`.
    
    h. Select the **Enable unit tests** check box so that you can run the test cases during a build.
    
    i. Click **Save**.
![Add Builder](/tutorials/jazzrtc/images/configure_builder.png "Add Builder")

3.  Create a stage to deploy your app to Bluemix:
     
    a. Click **ADD STAGE**. The Stage Configuration page opens.
![Click Add A New Stage](/tutorials/jazzrtc/images/add_deployer.png "Click add a new stage")
   
    b. Click the default **MyStage** name and change the name of the stage to `Deploy to dev`.
    
    c. On the **INPUT** tab, use the default settings, which use these configurations:
    
     * The input for the deployment is the output from the build stage. 
     * The deployment stage runs automatically every time the build stage runs successfully. 
    
    d. On the **JOBS** tab, click **ADD JOB** and then select **Deploy**. This job uses the settings in the `manifest.yml` file, which is included as part of the sample project. 
    
    You can use all of the values as provided, except for the hostname. The hostname defines your app's URL and must be unique for each app that is deployed on Bluemix.
      
       Override the hostname with the `-n` option in the cf push command, as shown in the next image. **Tip:** Use a combination of your user name and the date or time to ensure that your route is unique.

    e. Click **SAVE**. 
![Add Deployer](/tutorials/jazzrtc/images/configure_deployer.png "Add Deployer")

9. Build and deploy your project for the first time: at the top of the Build stage, click the **Run Stage** icon. The build process takes a couple of minutes. When you see a green circle, the app is live. 
![Successful Build](/tutorials/jazzrtc/images/build1_success.png "Successful Build")

10. Verify that the app is running by clicking the app link.
![Application](/tutorials/jazzrtc/images/app.png "Application")



<a name='summary'></a>
##Summary
You created a basic build and deployment pipeline for a project. You are ready to create builds and deployments for your projects. 

<a name='nextsteps'></a>
##Next steps

* For more information about builds and deployments, [see the Build & Deploy reference](/docs/reference/deploy/).
* To learn more about built-in environment properties and tools in the pipeline, [see Environment properties and resources for the Build & Deploy pipeline](/docs/deploy_var).
