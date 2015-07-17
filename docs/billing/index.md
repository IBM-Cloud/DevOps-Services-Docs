#Managing your account

Last modified: 15 July 2015

Without logging into IBM® Bluemix™ DevOps Services, you can explore existing projects or view the documentation. After you register with DevOps Services by using your IBM ID, you can access all of the features to develop, track, plan, and deploy software in one place.

---

* [DevOps Services accounts](#idsaccounts)
* [Setting up a DevOps Services account](#idssetup)
* [Bluemix accounts](#bmaccounts)
* [Table: Free allowance details](#table)
* [Setting up a billing account](#setup)
* [Monitoring your usage](#monitor)

--- 
<a name='idsaccounts'></a>
##DevOps Services accounts

After you register and set up an account with DevOps Services, you can do these tasks:

* Develop and deploy software in the cloud
* Host your source code with built-in source code management
* Code with the web integrated development environment (IDE) in your browser
* Track and plan project activities
* Push your applications to Bluemix, IBM's cloud platform
* Collaborate with other people by using the collaboration tools
* Ask questions and get answers in our forum
* Get started by forking projects or following a tutorial

---
<a name='idssetup'></a>
##Setting up a DevOps Services account

1.	[Register with DevOps services](https://hub.jazz.net/). You need to create an alias or use an existing one. An alias is a publicly visible short name. Your alias is included in the URL of each project that you own. The first time you log in to DevOps Services from a web browser, you link your IBM ID with an alias. If you have a Jazz ID, that is used as your alias.
2.	After your IBM ID and alias are linked, you can log in to DevOps Services from a web browser or your IBM® Rational Team Concert™ client, and you can access a Git repository from your local Git client.

	* To log in from a web browser, use your IBM ID credentials. 
	* To log in from your Rational Team Concert client, use your alias and IBM ID password.
	* To access a Git repository from your local Git client, use your alias and IBM ID password.

**Tip:** For authentication problems or if you are linked to the wrong account, you can request support by email at <idslogin@jazz.net>.

---
<a name='bmaccounts'></a>
##Bluemix accounts

All DevOps Services projects include an allowance of free services. If you exceed your allowances, your work is interrupted. To avoid interruptions, set up a Bluemix billing account and configure your services. By configuring your Bluemix account, you also get advanced features for monitoring your builds, deployments, and status of your projects. 

If you plan to use the Delivery Pipeline (Build & Deploy) and Track & Plan services beyond the free allowance, configure both services. Each service requires a separate billing configuration.

---
<a name='table'></a>
### Table: Free allowance details
<table border="1" summary="" width="100%">
	<tbody>
		<tr>
			<th>Service</th>
			<th>Charging metric</th>
			<th>Free allowance</th>
			<th>Cost</th>
		</tr>
		<tr style="background-color: #FFFFFF">
			<td rowspan="2">Delivery Pipeline</td>
			<td>Build minutes</td>
			<td>60 minutes per app (project), per month</td>
			<td rowspan="2">See the Bluemix [Pricing page](https://ace.ng.bluemix.net/#/pricing/)</td>
		</tr>
		<tr style="background-color: #FFFFFF">
			<td>App instances (deployers)</td>
			<td>First two app instances (deployers) per app (project), per month</td>
		</tr>
		<tr style="background-color: #EBEBFF">
			<td rowspan="2">Track &amp; Plan</td>
			<td rowspan="2">Users per app</td>
			<td>Private project: Three users</td>
			<td rowspan="2">See the Bluemix [Pricing page](https://ace.ng.bluemix.net/#/pricing/)</td>
		</tr>
		<tr style="background-color: #EBEBFF">
			<td>Public project: Unlimited users</td>
		</tr>
	</tbody>
</table> 

---
<a name='setup'></a>
##Setting up a billing account

Before you set up your billing account, determine what the best plan for your project is. [Learn more about billing accounts](https://www.ng.bluemix.net/docs/#acctmgmt/billing.html#bil_plan).

**Important:** The person who is responsible for setting up the billing account might not be the same person who is most affected by build and deployment failures and blocked access to Track & Plan pages. If you are not the person who sets up the account, ask your Bluemix billing manager to enable your billing account early.

To set up your billing account, complete these steps: 
1. Go to your Bluemix dashboard and select the space that is listed in your DevOps Services project settings. 
2. Click **Services** and click **Add a Service or API**.
3. From the DevOps section, select either **Delivery Pipeline** or **Track & Plan**.
4. In the "Add Service" section, make sure that the space that corresponds to your  DevOps Services project is selected.
5. From the **Selected Plan** list, choose a billing plan. 
6. Click **Create.**

---
<a name='monitor'></a>
##Monitoring your usage

You can monitor the usage details for your Bluemix account. For more information, [see the billing and usage documentation](https://www.ng.bluemix.net/docs/#acctmgmt/index-gentopic1.html#genTopProcId2). To determine costs, [see the Bluemix Pricing page](https://bluemix.net/#/pricing).

The Delivery Pipeline and Track & Plan services use metered pricing, where you pay based on consumption. However, they also include a free monthly allowance.

To help monitor monthly usage, [see the Bluemix cost estimator](https://ace.ng.bluemix.net/#/pricing/paneId=pricingSheet).

To see your usage details, click **Profile Settings <img src="./images/bm-profilealien.png"  align="bottom" style="display: inline; margin: 0px; border-style: none; margin-bottom: -10px;"> > Account > Usage Details**.





