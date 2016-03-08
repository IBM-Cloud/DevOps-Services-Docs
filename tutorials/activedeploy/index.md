# Update a running app with zero downtime

###### Last updated: 7 March 2016

Time: 15 minutes

With the IBM&reg; Active Deploy service, you can automate the rollout of changes to your app without interrupting users. 

You can test your application changes in production and roll back if the update doesn't meet your expectations. By integrating Active Deploy into your pipeline, you can easily update running apps with zero downtime every time a change is made.

In this tutorial, you use Active Deploy to update a running app with an extension of the Build &amp; Deploy pipeline. To complete the tutorial, you use a sample app that is preconfigured to clone the project, create an IBM&reg; Bluemix&reg; DevOps Services project that includes a pipeline, and deploy the app to IBM Bluemix.

<div class="table-of-contents">
 <table>
   <tr>
     <td colspan="4"><h4>Summary of steps</h4></td>
   </tr>
   <tr>
     <td><a href="#prereq">Before you begin</a></td>
     <td><a href="#deploy">Deploy to Bluemix</a></td>
     <td><a href="#update">Update your app</a></td>
     <td><a href="#view">View the updates</a></td>
   </tr>
 </table>
</div>

<a name='prereq'></a>
##Before you begin

To do this tutorial, you need a Bluemix account. Bluemix accounts provide access to everything you need to develop, track, plan, and deploy apps. You can sign up for a free 30-day trial. 

<h5> </h5>
<div class="container-fluid small_bottom_space">
   <div class="row pbl button-links" id="overview-links">
		<a href="https://login.jazz.net/psso/proxy/jazzregister?redirect_uri=https%3A%2F%2Fhub.jazz.net%2F" target="_blank" alt-text="Sign up"> 
			<div class="hollowButton">SIGN UP<div class="extra-title">for Bluemix </div>
			</div>
		</a>
   </div>
</div>

<a name='deploy'></a>
### Deploy to Bluemix

1. [Access the sample app on GitHub](https://github.com/IBM-Bluemix/active-deploy/tree/master/sample-apps/pipeline).
2. Click the **Deploy to Bluemix** button and log in.
3. Verify that all of the information, including space and organization, are correct. Click **Deploy**.
4. Click **VIEW YOUR APP** to see your app in production.

<a name='update'></a>
### Update your app

1. In the upper-right corner of the page, click **EDIT CODE**.
2. Click the **hello_world_flask.py** file.
3. Replace `Hello World` with `Hello Universe!`
4. Click the **Git Repository** icon.
5. On the right, type a message about the changes you made and click **Commit**.
6. In the Active Branch section on the left, click **Push** to merge your changes.
7. Return to your pipeline by clicking **BUILD &amp; DEPLOY**.
8. Redeploy your pipeline by clicking the **Run Stage** icon.

The sample app has a preconfigured pipeline, complete with the Active Deploy stage. The first time that the pipeline is run, the Active Deploy service is not invoked. When the pipeline runs, the Deploy Single Instance job exports the `NAME` of the new version of the app. The Active Deploy-Begin job uses the `NAME` to find the `App_Name` and then searches the space for any earlier versions of the app with a route. If an original app is not found, the Active Deploy-Begin job scales the app to `GROUP_SIZE` instances and maps the route to `ROUTE_HOSTNAME.ROUTE_DOMAIN`.

<a name='view'></a>
### View the updates

While the pipeline is running, you can view real-time updates in several ways:

   * To see the code as it is updated, click **View logs and history**.
   * To track progress by using the activity log on your app's Dashboard, click below the **LAST EXECUTION RESULT** heading.
   * To see a history of your updates, including the current deployment, go to the Active Deploy dashboard.

For more information about the Active Deploy service, see the [Bluemix Docs](https://www.ng.bluemix.net/docs/services/ActiveDeploy/index.html).
