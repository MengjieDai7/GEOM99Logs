## ArcGIS Server on Google Cloud Platform (CGP)
Creating an image and logging in on Google Cloud Platform

# Must Haves Before Starting 
Gmail Account
Google Cloud Credits. In this case we have free credits thanks to Google's Academic Team 
Access to Shawn's ArcGIS Server. Shawn provided access when you uploaded provided him with your email on a google sheets sign up

## Setting up a CGP Project
Create a CGP Project
Create Instance 
Set Password 
Set Fire wall rules 

# Create a CGP Project 
Go to console.cloud.google.com and log in 
1. Go to top left corner hamburger
2. In drop down menu select compute engine
3. Click on VM instances
4. Enable compute Engine API

# Create Instance 
1. Click on Create Instance (one of the headers)
2. Provide a memoriable and appropriate name (e.g. arcgisserver)
3. Go to Boot Disk Click on Change
Most images are linux based because it is free but we are using windows since ethat is familiar. It will require a premium charge!
	1. Use custom image
	1. Change the source folder
		This is because we will be using Shawn's project so it is not in your own folder
	1. Select Shawn's ArcGIS Server
	1. Select the image 
		The size of drive will be 50gb
5. Fire Wall Options. Select both Allow HTTP and Allow HTTPS traffic
     So you can use a webserver 
6. Leave other defaults
      Cloud is a location and in this case the location is in Iowa
7. Click Create
      Takes a couple minutes to load

# Set Passward 
1. Under connect column select the down arrow option beside RDP
2. Click Set new windows password
3. Enter in student as username and click set
4. Password will be shown. Make sure to save the password!! Best practice is to save on Notepad++ to ensure formating

If your forget the password you can rerun step 4

# Set up Fire Wall Rules 
1. Click Set up Firewall rules in VM Instances
2. Select Create Firewall rule option (header)
3. Name it flemingrdp444 (This naming convention makes it easier for tech support)
4. Under targets select all instances in the network
5. Under source filter select IPv4 ranges
	1. Select IPv4 Ranges
6. Here are the IP Options 
        1.Working from home: An example is 24.242.25.53 (just google whatsmyip to see yours). Should never start with 192.168.x.x or 10.x.x.x
        1.Any computer no restrictions 0.0.0.0/0
	1.Can come back to change this anytime!
7. Set TCP Port to 444 and click create



## Setting a GCP Firewall Rule to allow ArcGIS Server Management Ports

# Set up Fire Wall Rule to allow for ArcGIS Server
1. In the google cloud hamburger go to networking -> VPC Networl.
2. Click Firewall, then Create Firewall rule   
3. Name the rule (e.g. arcgisserveradmin )
4. Under targets select all instances in the network
5. Under source filter select IPv4 ranges
    1. Select IPv4 Ranges and enter personal IP
6. Set TCP Port to 6443,6080 and create

    
## Setting a Windows Firewall Rule to allow ArcGIS Server Ports

  
#  Log into Remote Desktop
1. Click start menu on computer
2. Select Windows Defender firewall with advanced Security Option
3. Clikc on in bound rules (left side) and click on new rule
4. Select Port then Next
5. Select TCP and enter in ports: 6443,6080
6. Allow Connect and next
7. Ensure domain, private, and public are selected. Then click next
8. Provide a consistent name (e.g. ArcGIS Server Admin Ports)


## Start an existing/shut down VM on GCP
1. Open GCP go to the hamburger select computer engine, then VM instances
2. If the status circle is grey = not running, green = running
3. Click the 3 vertical dotes on the left handside of the column. Select Start/Resume or Stop

   (NOTE! Each time you start VM a new external IP is created. Connections in ArcGIS Pro or Bookmarks saved on web broswer need to be updated
     External IP can be found in the column
     Give ArcGIS Server time)


## Remote Desktop to VM Desktop 
1. Find External IP. If need help Refer to step 3 in Start an existing/shut down VM on GCP
2. On YOUR windows desktop start remote desktop connection tool
    1. Start bbutton and search Remote Desktop Connection Tool
    1. Enter in IP address of virtual machine. Then add :444 to the end for port connection (EXTERNAL IP ADDRESS CHANGES EVERYTIME !!!)
3. Enter in system credentials. Username and password.
    1. Click more choices if you are only getting password prompt. Then select different account
    1. username = student, password what you recorded on notepad++  (If you forget the password go to Set Passward step above)
    1. Click yes on the prompt. Should see remote desktop screen


## How to Turn off Remote Desktop 
Running VM costs $$
Two options to turn off!

1. Turn off using a Windows Desktop Console
   Like turning off your own computer
     1. Go to start menu in VM and lcokc power icon
     1. Shut down
        
Note: Disconnecting does not = shutting of remote desktop. It is like tunring off your monitor machine is still running.
Signing out is does not shut off the machine either.

2. Turn of using GCP Compute Engine Console (BEST WAY)
    1. Open GCP VM instances console
         Hamburger -> compute engine -> VM Instances
    1. Locate the running VM instance. Will be green!
    1. Click on ellipsis on right hand side and select stop
Give it time and refresh page to check that it is shut off. Button is no longer green.


## Open ArcGIS Server REST Service directory 
Running server allows you to connect web browser on your computer to ArcGIS Server REST endpoint
Must use the external IP from your VM (Changes everytime!)

1. Open webroswer
2. Go to https://YOURIPNUMBER/arcgis/rest/services replace with your external IP number
3. Accept the risk prompts
	1. Advanced and click proceed 
 
Directed to ArcGIS REST Services Directory 


## Publish Image from ArcGIS Server on to ArcGIS Online
1. Turn on VM Refer to step "Start an existing/shut down VM on GCP"
2. Go to ArcGIS Server
	1. Go to https://YOURIPNUMBER/arcgis/rest/services replace with your external IP number
	1. Check Server is running
3. Open ArcGIS Pro
4. Under Insert tab click on server and new arcgis server
	1. Server URL:  https://YOURIPNUMBER/arcgis   replace with your external IP number
    	1. Username and Password
5. Check connection
	1. Catalog Panel
	1. Check Server Connections
6. Click on the Service under the catalog
	1. Add SampleWorldCities to Map
7. Share tab then Web Map
	1. Unique name for map!
8. Analyze and resolve errors.
	1. Right click to resolve error
 	1. Can ignore warnings 
9. Finally click Share

## Publish map service onto GCP VM
1. Turn on VM Refer to step "Start an existing/shut down VM on GCP"
2. Go to ArcGIS Server
	1. Go to https://YOURIPNUMBER:6443/arcgis/rest/services replace with your external IP number
	1. Check Server is running
3. Sign into VM to move shapefile of interest into the correction location. Steps to sign into VM are from this step 
Remote Desktop to VM Desktop located above.
	1. In this case move Canada shp folder into c:\gisworkspace\
4. Open ArcGIS Pro
5. Under Insert tab click on server and new arcgis server
	1. Server URL:  https://YOURIPNUMBER:6443/arcgis   replace with your external IP number. Port number is to the GIS server
    	1. Username and Password
6. Catalog Panel. Go to Server select and left click to publish. Select Map Service 
7. Fill out Publish Map Service Tool. Unique name!
	1. Fix the errors
	1. Fix the warning that says 24011: Data source is not registered with the server and data will be copied to the server. 
	1. Register Data to path c:\gisworkspace\canada. Click Create
8. Pubish Map 
9. Check on Manager https://EXTERNALIP:6443/arcgis/manager/
10. Check on Rest Services https://EXTERNALIP:6443/arcgis/rest/services/


