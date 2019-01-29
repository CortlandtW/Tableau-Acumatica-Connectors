# How to Import Data from Acumatica Generic Inquires (GIs) into Tableau Desktop
Connecting Tableau to Acumatica - Do it Yourself
How one can import data from Acumatica Generic Inquires (GIs) into Tableau Desktop.  

~~As an example, the procedure will import Acumatica "AR-Invoices and Memos" data into Tableau. ~~

To use ready-to-go Tableau connectors with sample reports and dashboards, visit https://github.com/dataself/Tableau-Acumatica-Connectors/tree/master/ready-to-go-templates.

### System requirements: 
Acumatica v2018 R2 and Tableau Desktop 2018.3 running on Windows or Mac.   
Procedures for other Acumatica and Tableau versions are identical or very similar.

### 1. Setting up Acumatica to render data to external applications like Tableau: 
- Log in to your Acumatica portal and find Generic Inquiry. There are two main paths: 1) More Items > Configuration > Customization > Generic Inquiry. 2) System > Customization > Generic Inquiry. 
- Click the search icon in the Inquiry Title box, find and double-click on "AR-Invoices and Memos".
- Be sure the "Expose via OData" checkbox is checked. You will find this below Screen ID: in the top section of the Generic Inquiry edit screen. If it is not checked, check it and click the Save icon in the top left corner. 
- Repeat the steps above for other GIs that contain data you would like to import into Tableau.
- Important: Find out from your system administrator the OData Feed URL for your Acumatica site. For instance, for an Acumatica portal https://abcorp.acumatica.com, the OData Feed URL might be something like https://abcorp.acumatica.com/odata/abcorp.<br/><br/>
### 2. Setting up Tableau Desktop to import data from Acumatica:
- Installing Tableau Desktop: Go to https://www.tableau.com/support/releases and select a Tableau Desktop version to download (we recommend downloading the latest version). Download and run the Tableau installer, then follow the prompts to complete the installation. You'll need admin rights to the computer where you're installing Tableau. 
- Run Tableau Desktop.  On the left panel in the "To a Server" section, click More... and then OData.
- On the OData prompt, fill out the Server (Acumatica OData Feed URL - see the last step in section 1 above) and add the name of the first GI using the following format: https://abcorp.acumatica.com/odata/abcorp/AR-Invoices%20and%20Memos/  Please note that a forward slash was added before and after the the GI name.  Also note that spaces have been replaced by "%20"
- Select Authentication = Username and Password, enter your credentials, and click Sign In. It might take several seconds for Tableau to validate your credentials. 
- You should now see a list of field names from your GI listed in Tableau.
- Click the Sheet 1 tab at the bottom of the page. This will trigger the data import process from Acumatica which might take a while depending on the size of GI's dataset. At the end of this process, you'll have a snapshot of your GI's data, extracted into Tableau. 
- You'll now see a blank Sheet 1 with your GI information on the left Data panel.
- Your Tableau connection to Acumatica is all set. You can now click File > Save to save a Tableau workbook for future use.
- To take a new snapshot of your data, just hit F5 inside of Tableau Desktop. 
- Search for Tableau documentation (see section 4) to learn how you can slice and dice your data and create reports and dashboards.
<br/><br/>
### 3. Possibilities and limitations:
- The approach described here establishes a direct connection between Tableau and Acumatica. This connection retrieves data and stores it in a Tableau extract.  Every time you need to get new data from your Acumatica instance, you will need to refresh the extract.
- Retrieving data via OData protocol can be very slow (average of a few thousand records every 10 seconds).
- No matter what BI tool you use, retrieving large amounts of data from Acumatica might cause performance issues in your Acumatica site.  So, if this is a concern, you should consider refreshing the extracts outside of normal business hours and also avoid refresh extracts in parallel.
- You might also want to explore publishing your Tableau workbooks to Tableau Server such as Tableau Online (https://www.tableau.com/products/online/request-trial). This will allow you to:
  - Expose your Tableau reports to other users via web browsers and mobile device apps
  - Insert your Tableau reports and dashboards directly inside Acumatica dashboards
- To publish to an existing Tableau Server, click on "Server" in the top bar and select Publish Workbook.  When prompted for your Tableau Server information, provide it, then select which project you would like it saved in, enter a name and click Publish. 
- There are vendors like DataSelf Corp that have optimized the Tableau and Acumatica integration to overcome many of the OData protocol and Tableau limitations. See below for details. <br/><br/>
### 4. Further support and assistance:
- Tableau support: https://www.tableau.com/support
- Acumatica support: https://www.acumatica.com/acumatica-service-offerings/
- DataSelf Corp: https://dataself.com/acumatica-bi-analytics/. DataSelf Corp is a Tableau and Acumatica certified partner which can assist you in maximizing and expediting your return-on-investment in Tableau and Acumatica. Out-of-the-box, DataSelf provides dozens of connectors and 5,000+ reports and dashboards for areas such as sales, inventory, services, and financials.  This allows your team to focus on data analysis on day one, instead of building everything from scratch. 
