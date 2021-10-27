# Part 2: Preparing the Satellite Environment  

[Tutorial Menu](https://github.com/pslucas0212/RedHat-Satellite-VM-Provisioning-to-vSphere-Tutorial)  

In Part 2 of the tutorial we will prepare the Satellite environment.  Note: We have Simple Content Access enabled on our customer portal and with any manifests that we create.  For more information regarding Simple Content Access, please refer to the Simple Content Access article link in the reference section below.  

### Create a Manifest for Satellite. 
To enable content on Satellite, you must first create a manifest file containing any Red Hat software subscriptions for that content and import the manifest into Satellite.  

Go to [https://access.redhat.com/](https://access.redhat.com/) and login to your Red Hat customer account.  

Click the person icon in the upper right corner of the Red Hat customer portal page.  

![Red Hat Customer portal page](images/pic01.jpg)  

Next click on the red login button.  

![Red Hat Customer portal login button](images/pic02.jpg)  

In the Login in to Red Hat dialog box, enter your Red Hat login or email and click the red next button.  Enter your password in the Password field and click the red Login button.  

On your Red Hat portal customer page, click the Subscriptions tab in the upper left side of the screen.  

![Red Hat Customer portal Subscriptions tab](images/pic03.jpg)  

Click the Subscription Allocations tab found near the top middle portion of the Red Hat Customer Portal.  

![Click Subscription Allocation tab](images/pic04.png)  

Click the blue Create New subscription allocation button.  

![Click the blue Create New Subscription allocation button](images/pic05.png)  

On the Create a New Subscription Allocation page give the manifest a name and chose the version of Satellite that will use the manifest.  In our example we are creating manifest for the Moline Operations team and adding the manifest to our Satellite 6.9 environment.  Click the blue Create button to continue.

![Click the Create button](images/pic06.png)  

On the Subscription Allocations >> moline_operations page make sure that Simple content access is enabled and click on the Subscriptions tab.  

![Click on the subscriptions tab](images/pic07.png)  

On the Subscriptions tab click the blue Add Subscriptions button.  

![Click on the Add Subscriptions button](images/pic08.png)  

On the Add Subscriptions to moline_operations page you will see the subscriptions available to add to the manifest.  Since we have Simple Content Access enabled we only need to add one subscription per Red Hat product to the manifest.  For this example we are adding one subscription for RHEL Premium with Smart Management. 

![Add subscription ](images/pic09.png)  

If needed scroll down and click the submit button. 

![Click submit button](images/pic10.png)  

Click the Export Manifest button to download the manifest file that you just created.

![Click Export Manifest](images/pic11.png) 

We can now logout of the Red Hat customer portal.  

### Creating an Organization and Importing the Manifest in Satellite

Login to the Satellite console by entering [http://sat01.example.com](http://sat01.example.com) for the Satellite url.  Satellite will redirect the browser to Satellite's secure login page.  If this is the first time you have accessed your Red Hat Satellite console, you will need to accept Satellite's certificate for your browser.  

Enter the user id and password and click the Login button.  

![Click Login button](/images/sat01.png)  

You are now at the Satellite home screen.  

![Satellite Home Srceen](/images/sat02.png)  

Before we import the manifest, we will first create an Organization in Satellite.  Organizations are used to manage content related functions such product management, repositories and content views.  Satellite can support mutliple organization if that makes sense for your envionrment.  For example, you may want to split content between US and European based manufacturing with two organizational views.  You might create Ogranizations based on business units or deparatments.  In this tutorial we will create a single organzation for the operations organization.  

On the side menu click Adminster -> Organziations.  

![Administer -> Organizations](/images/sat03.png)  

On the Organizations page click the blue New Organization button in the upper right of the Satellite console.

![New Organziation](/images/sat04.png) 

Fill in the Name and Label fields and click the blue Submit button.  

![Click Submit button](/images/sat05.png) 

You will now see the Organziations > Edit Operations Department page.  Click the cancel button.

![Click cancel button](/images/sat06.png)

Now we will add a location for our organization. We can use a location to logically map geographically separate areas to an organzation.  On the side menu click Adminster -> Locations.  

![Administer -> Locations](/images/sat07.png)   

On the Locations page click the blue New Location button located towards the top right of the screen.  

![Click New Location button](/images/sat08.png) 

Fill in the Name field and optionally add a description.  Now click the blue Submit button to create the location.  

![Click location Submit button](/images/sat09.png) 

After clicking the blue Submit button you will be returned to the Locations > Edit Moline page.  

We will now import the manifest into Satellite for the Operaions Department organziation.  

On the side menu click Content -> Subscriptions.  

![Content -> Subscriptions](/images/sat10.png)   

Before we import the manifest into Satellite, make sure Satellite is set to the Operations Department organization and the moline location.  You will see the current organization and location settings near the top left of the Satellite Console.  If the Operations Department and moline are not set as the organziation and location, click on each respective drop down to chose the Operations Department and then the moline location.  

Click on the blue Import a Manfiest button.  

![Import Manifest](/images/sat11.png)   

In the Manage Manifest dialog box, we will leave the default settings.  Click the Browse... button and navigate to the location of the manifest file you downloaded and click the Open button.  

![Chose Manifest](/images/sat12.png)  

The manifest will automatically be imported into Satellite and you will next see the Subscriptions page.

![Subscriptions Page](/images/sat14.png)

Finally we will add the Operations Department organization and the moline Location to our Satellite instances.  Technically we are adding it to the Capsule Server running on our Satellite instance.  On the left naviagion bar, click Infrastructure -> Capsules

![Infrastructure -> Capsules](/images/sat51.png)

Click the Edit button in the far right column of the sat01.example.com server line.

![Click the Edit button](/images/sat52.png)

In the Capsules > Edit sat01.example.com page, click on the Location tab.  And the click moline Locations All Items box to move to the Selected items box.

![Click moline](/images/sat53.png)

Next click on the Organizations tab and follow the same steps above to move Operations Department Orgnaizations All Items box to move to the Selected items
box.  

![Click Operations Department](/images/sat54.png)

Click the blue Submit button and we will be returned to the Capsules pages.  There you will observe that moline is now part of the list of Locations and Operations Department is part of the Organizations list.

![Capsules page](/images/sat55.png)  

Satellite will be updating our DNS records when we provision a VM from Satellite.  The reverse DNS zone record update is defined when we create a subnet in ...
The forward DNS zone record update is defined with the domain, and we will set that up now in Satellite.

We've completed preparing the Satellite environment.



## References  
[Installing Satellite Server from a Connected Network](https://access.redhat.com/documentation/en-us/red_hat_satellite/6.9/html/installing_satellite_server_from_a_connected_network/index)   
[Simple Content Access](https://access.redhat.com/articles/simple-content-access)  
[Provisioning VMWare using userdata via Satellite 6.3-6.6](https://access.redhat.com/blogs/1169563/posts/3640721)  
[Understanding Red Hat Content Delivery Network Repositories and their usage with Satellite 6](https://access.redhat.com/articles/1586183)
