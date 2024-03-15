## ArcGIS Server on Google Cloud Platform (CGP)
Creating an image and logging in on Google Cloud Platform

# Must Haves Before Starting 
Gmail Account
Google Cloud Credits. In this case we have free credits thanks to Google's Academic Team 
Access to Shawn's ArcGIS Server. Shawn provided access when you uploaded provided him with your email on a google sheets sign up

## Break down of Main Steps 
Create a CGP Project
Run the virtual Machine to test the ArcGIS Server 

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
5. Leave other defaults
      Cloud is a location and in this case the location is in Iowa
 

   
