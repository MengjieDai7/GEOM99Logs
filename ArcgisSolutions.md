
### ArcGIS Solutions 
Deploy Address Data Management 
Want to test the ability to add new hidden addresses from surveys to existing files

### Gather Data
Road Data: tbd not sure if will need
Test Data: https://open.toronto.ca/dataset/address-points-municipal-toronto-one-address-repository/
Address Points from Open Source Toronto 

### Testing adding in known addresses 
help from this ESRI video https://www.youtube.com/watch?v=hywR1CzyKNo and https://www.youtube.com/watch?v=YhCRC_eKkiY
## REMEMBER TO SAVE ARCPRO WILL CRASH 

1. Download Address Data Management Zip 
2. Upzip open the aprx
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S1.png)
3. Catalog Panel Review the Tasks
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S2.png)
4. Go through the How to Configure Address Data Managment steps
   
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S2.5.png)

5. Read the Review Schema
6. Define Spatial reference
   1. Click on Spatial reference task
   1. Address Data Management.gdb is an empty gdb. Set this at teh geodatabse
   1. Set the Reference. Toronto is 1983 zone 17N
   1. Keep Default Folder location
   1. Provide Output Name (e.g. TorontoTest)
7. Configure map, layers, and rules
   
   1. Update map data sources. When clicking find and replace it will appear on the right side. Drag it out.

   ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S2.6.png)

   When clicking find and replace it will appear on the right side. Drag it out.

   1. Add and mod fields (as needed)

   ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S2.7.png)

   1. Update feature templates (as needed)

   ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S2.8.png) 

   1. Configure Attribtue rules (as needed)

   ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S2.9.png)

   1. Update database sequences

   ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S2.91.png)

8. Go through load Data steps.
   1. Disable attribute rules first. For Address Point and Site address layers
   
   ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S3.png)
   1. Load your data
      
   ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S4.png)
