# Preparing the Satellite Environment

In Part A of the tutorial we will prepare the Satellite environment.  Note: We have Simple Content Access enabled on our customer portal and with any manifests that we create.  See this article to enable Simple Content Access - [add sca reference link here]

### Create a Manifest for Satellite
Go to [https://access.redhat.com/](https://access.redhat.com/) and login to your Red Hat customer account.  

Click the person icon in the upper right corner of the Red Hat customer portal page.  

![Red Hat Customer portal page](images/pic01.jpg)  

Next click on the red login button.  

![Red Hat Customer portal login button](images/pic02.jpg)  

In the Login in to Red Hat dialog box, enter your Red Hat login or email and click the Red next button.  Enter your password and the Password field and click the Red Login button.  

On your Red Hat portal customer page, click the Subscriptions tab in the upper left side of the screen.  

![Red Hat Customer portal Subscriptions tab](images/pic03.jpg)  

Click the Subscription Allocations tab found near the top middle portion of the Red Hat Customer Portal.  

![Click Subscription Allocation tab](images/pic04.png)  

Click the blue Create New subscription allocation button.  

![Click the blue Create New Subscription allocation button](images/pic05.png)  

On the Create a New Subscription Allocation page give the manifest a name and chose the version of Satellite that will use the manifest.  In our example we are creating manifest for the Moline Operations team and adding the manifest to our Satellite 6.9 environment.  Click the blue Create button to continue.

![Click the Create button](images/pic06.png)  

On the Subscription Allocations >> moline_operations page make that Simple content access is enabled and click on the Subscriptions tab.  

![Click on the subscriptions tab](images/pic07.png)  

On the Subscriptions tab click blue Add Subscriptions button.  

![Click on the Add Subscriptions button](images/pic08.png)  

On the Add Subscriptions to moline_operations page you will see subscriptions available to add to the manifest.  Since we have Simple Content Access enabled we only need to add one subscription per Red Hat product to the manifest.  For this example we are adding one subscription for RHEL Premium with Smart Management. 

![Add subscription ](images/pic09.png)  

If needed scroll down and click the submit button. 

![Click submit button](images/pic10.png)  

Click the Export Manifest button to download the manifest that you just created.

![Click Export Manifest](images/pic11.png) 

We can now logout of the Red Hat customer portal.  

### Creating an Organization and Importing the Manifest in Satellite

Let's login to Satellite.  
