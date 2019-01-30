# How to Import Data from Acumatica Generic Inquires (GIs) into Tableau Desktop
Connecting Tableau to Acumatica - Do it Yourself.  
How one can import data from Acumatica Generic Inquires (GIs) into Tableau Desktop.  

~~As an example, the procedure will import Acumatica "AR-Invoices and Memos" data into Tableau. ~~

### System requirements: 
Acumatica v2018 R2 and Tableau Desktop 2018.3 running on Windows or Mac.   
Procedures for other Acumatica and Tableau versions are identical or very similar.

##### NOTES:
- To use ready-to-go Tableau connectors with sample reports and dashboards, visit https://github.com/dataself/Tableau-Acumatica-Connectors/tree/master/ready-to-go-templates.

-----

## Step by Step: Import Data from Acumatica Generic Inquires (GIs) into Tableau Desktop

### 1. Configure Acumatica to render data to external applications like Tableau: 
1. Log in to your Acumatica portal.
2. Select `Generic Inquiry`.  
There are two main paths to Generic Inquiry:   
a) `More Items > Configuration > Customization > Generic Inquiry`. b) `System > Customization > Generic Inquiry`. 
2. Click the search icon in the `Inquiry Title` box and double-click  `AR-Invoices and Memos`.
2. Mark the `Expose via OData` checkbox.  
   The checkbox is found below `Screen ID:` in the top section of the Generic Inquiry edit screen.
2. Click the `Save` icon in the top left corner. 
2. Repeat the steps above for other GIs that contain data you would like to import into Tableau.

##### NOTES:
- **Important:** Find out from your system administrator the OData Feed URL for your Acumatica site.  
For instance, for an Acumatica portal https://abcorp.acumatica.com, the OData Feed URL might be something like https://abcorp.acumatica.com/odata/abcorp.

### 2. Configure Tableau Desktop to import data from Acumatica:
1. Install Tableau Desktop as needed:   
   1.1.  Browse to https://www.tableau.com/support/releases.  
   1.2.  Select a Tableau Desktop version to download (we recommend downloading the latest version).  
   1.3.    Download and run the Tableau installer.  
   1.4.   MORE STUFF missing HERE
1. At the `OData` prompt  
  - enter the `Server` name (Acumatica OData Feed URL - see the last step in section 1 above)
  - enter the name of the first GI using the following format: https://abcorp.acumatica.com/odata/abcorp/AR-Invoices%20and%20Memos/.  
  - Notes:  
    + A forward slash was added before and after the the GI name.  
    + Spaces have been replaced by "%20".
3. Select `Authentication = Username and Password`
1. Enter your credentials 
1. Click `Sign In`.
   - Validation may take several seconds.  
   - Once validatated You should  see a list of field names from your GI listed in Tableau.
1.  Click the `Sheet 1` tab at the bottom of the page.   
    +  Clicking the tab will trigger the data import process from Acumatica.  The process might take a while depending on the size of GI's dataset.
    + At the end of the import process you will see a snapshot of your GI's data, extracted into Tableau. 
~~- You'll now see a blank Sheet 1 with your GI information on the left Data panel.~~
7. Click `File > Save`.

##### NOTES:
- `File > Save` saves a Tableau workbook for future use.
- To take a new snapshot of your data, make Tableau Desktop the active window and  press `F5`.  
- Search for Tableau documentation (see section 4) to learn how you can slice and dice your data and create reports and dashboards.

-----

### 3. Further Considerations, Possibilities and Limitations:
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

==================

> # Cortlandt's Notes
> - The word "Select", "Click" or perhaps "Navigate to" should be preferred over "find".
> - All sequential instructions must be numbered.
> - Prefer simple, active voice e.g.  "Setup" over "Setting up".
> - References to text strings that appear on the screen should be consistently displayed with a different font.  Here I've used the deliminited the literal text strings using the "backtick" character.

> - GitHub markup has some screwy formatting rules and syntax. 
> -- Some lines must be terminated with two blanks after the final visible character. 
> For instance, to produce
- Notes:  
    + A forward slash was added before and after the the GI name.  
    + Spaces have been replaced by "%20".
    
Requires the following markup language.    
```
- Notes:  <cr> 
    + A forward slash was added before and after the the GI name.  <cr>  
    + Spaces have been replaced by "%20".
```    
