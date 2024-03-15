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
     3a. Use custom image
     3b. Change the source folder
             This is because we will be using Shawn's project so it is not in your own folder
     3c. Select Shawn's ArcGIS Server
     3d. Select the image (in this case it is geom99-2024-v1)
             The size of drive will be 50gb
     Once you click select the cost estimate will change to ~$60.
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

# Set up Fire Wall Rules 
1. Click Set up Firewall rules in VM Instances
2. Select Create Firewall rule option (header)
3. Name it flemingrdp444
     This naming convention makes it easier for tech support
4. Under targets select all instances in the network
5. Under source filter select IPv4 ranges
    5a. Select IPv4 Ranges
        Fleming College computer: 142.237.0.0/16
        Working from home: An example is 24.242.25.53 (just google whatsmyip to see yours).
              Should never start with 192.168.x.x or 10.x.x.x
        Any computer no restrictions 0.0.0.0/0
   Can come back to change this anytime!
6. Set TCP Port to 444 and click create

## Setting a GCP Firewall Rule to allow ArcGIS Server Management Ports
   
