Timesheet: https://docs.google.com/spreadsheets/d/1VNTvaNi8FSfdM6DfVeu9pz9DLAKOSjkncDM1nab1UnM/edit#gid=0

# ArcGIS Solutions 
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
   1. Look at your data layesr.In this case the Toronto Address Points shapefile the field with the data full name is ADDRESS37. And on the Site Address shapefile the field with the full name is called Full Address. 
      
   ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S4.png)
   1. Load Data.  Use the Field mapping tools if schema is different.
  
   ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S5.png)

   Ran into problems here. There was an error but the geometry type of both shapefiles are the same. 
     
   ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S6.png)

   Went onto an ESRI form https://community.esri.com/t5/arcgis-pro-questions/merge-error-of-different-data-type-but-data-types/td-p/1012686
   Some of the solutions suggested recreating the file datasets to fix the problem. I played around with the different field types to examine different 
   combinations. 
   ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S7.png)

9. Conclusion
While there is a lot of utilty in ArcGIS Solutions and it creates a great product for people to explore and deploy. After playing around with the tasks and the existing structure of this solution, I believe it is too out of scope for our project. Our project is to find a way to document hidden address from people on the ground who might come across one. There is no need to use the Address Data Management because the municapities would already have their own system in place for address data management we are not replacing their system. Instead we are simply provided updated information.


# Survey 123
Looking at the Pull Function to intergrate an an existing item from AGOL in our case this would be the open source Toronto Address points
Sources that were used to learn from https://www.youtube.com/watch?v=sSjr8KV1HLc

1. Upload the Toronto Address Points into AGOL. Create a map.
   1.  Compress the data into a ZIP and add layer from file. 
 ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S8.png)
 ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S9.png)
   1. Click Create and add to map. Since the Toronto Address points has a lot of data make sure to give it time to load.
   1. Save the map as Hidden Address Test or another memorial name.

2. Go to REST ENDPOINT of feature layer
   1. Click on the layer
 ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S10.png)
   1. Scroll down on the left hand side copy the URL 
 ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S11.png)
   1. Paste the URL into Notepad++ for the time being and save it in a spot that you can easily access
Note: Make sure you have the right REST ENDPOINT it should be the URl from the layer page

3. Take a look at the Data set up
   1. Click on Data in the headings
   1. Click on Check out the Table and Fields
   ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S12.png)
   1. Note down the fields of relevance into the same Notepad++ file. In this case ADDRESS37 has the full address name so this is the field we want. Alongside the WARD35 and WARD_NA36 field which gave you the ward names.
   ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S13.png)

4. Open up Survey123
If the App is not downloaded Download the Survey123 App
   1. Open up Survey123 Connect
  ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S14.png)
   1. Create new Standard Template so people can open up in the app & web format
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S15.png)
   1. Create relevant question. Geopoint. Collector name. Date/time
 ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S16.png)

5. Address Names Collection Format. The address name pulldata only works if it matches exactly. Look at how the field value is written in AGOL.
   1. Break up the address so it is easier for individual to record. (Less errors this way).
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S22.png)
   1. Easy to mis type/write street suffix so include a list for this option. https://www.toronto.ca/wp-content/uploads/2017/11/9783-city-wide_index.pdf
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S23.png)
   1. Create a full address read only first address field https://doc.arcgis.com/en/survey123/desktop/create-surveys/xlsformformulas.htm
   Previous questions must always be referred to in formulas with the format ${field_name}.
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S24.png)

7. Property Codes from https://www.mpac.ca/en/PropertyTypes/FindYourPropertyType/Propertycodes
It is useful to also have user record property code so that people know what to look for when searching for a property
   1. Create property code options
   
  ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S19.png)
  
  ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S20.png)


7. Constrain using pulldata https://community.esri.com/t5/arcgis-survey123-questions/reject-entry-of-specific-text-value/td-p/1049444
If an address already exists then it individual should not be able to input a response

*** Trouble shooting if you are unable to ope xlxs form Survey123 connect go directly to the file path instead. 
  ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S21.png)

Explore the pulldata layer options https://doc.arcgis.com/en/survey123/desktop/create-surveys/xlsformformulas.htm#ESRI_SECTION1_BB97985CAFB740EE8AEF99EFD6E238E3
   1. Pull the data you want from the AGOL layer. Refer back to the Notepad++. Compare the user entered data to the existing dataset. If address already exists there should be a constraint message that appears. 
  ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S25.png)

8. Check your survey! Save your xlxs form and Publish look at results. 
  ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S26.png)
   1. Ran into Error 
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S27.png)
   1. Looked at the Error in Row 6 and consulted online blogs https://community.esri.com/t5/arcgis-survey123-questions/error-converting-xlsform/td-p/1125573
Changed the list_name
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S28.png)
   1. Error for pulldata expression  https://community.esri.com/t5/arcgis-survey123-questions/survey123-data-validation-error/td-p/839703
  ![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S29.png)
Error was because of brackets use {field_name} instead of (field_name)

9. Errors for Survey Fixed! Now test out Survey.
   1. Use this as test data 4 Merrill Ave W (this address exists in the database)
   1. Result of inputing address
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S30.png)
   1. Change equation to add in a space before the suffix
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S31.png)
Add   "" between the fields in the calcultion. This ensures that there is a space.

10. Getting the survey to acknowledge when a deuplicate data is etnered 
   1. Test out different variations of the code. I did trail & error. Each Time I changed the code I would recheck the survery form to see if it would indicate when an address already existed. 

![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S32.png)
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S33.png)
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S34.png)
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S35.png)

11. Survey was able to display Not Valid when an address already existed in the previoulsy specified shapefile

![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S36.png)
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S37.png)

12. Inputing a constraint so that survey rejects duplicate addresses
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S38.png)
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S39.png)

13. Incorporate feedback. Instead of having a lot list of options for suffix. Split it so that the e,w,s,n options are another select field. 
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S40.png)
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S41.png)

15. Add additiona fields to help find the door of addresses
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S42.png)

15. Add the additiona direction field when creating the full address
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S43.png)


# Survey 123
PART 2! Use the same survey but make minor change so that the survey only takes in existing addresses. 

1. Save the previous surveys xlxs file.
2. Upload the xlxs file into a new survey. 
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S45.png)

3. In the formulations to make it so that instead of looking for a full address field that is blank. You want a not blank one which signals that an existing address is there.
Simply add ! to the equation.

![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S47.png)

4. Check that the formula works!
![alt](https://github.com/MengjieDai7/GEOM99Logs/blob/main/Pictures/S46.png)

