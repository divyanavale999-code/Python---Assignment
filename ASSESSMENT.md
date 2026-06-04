#### Section A: Concept Application



1\. Compare the technical differences between Import and DirectQuery modes and identify which is suitable for a static CSV file.



\->  Power BI handles data retrieval, storage, and performance differently depending on the connection mode.



* **Data Storage:** Import mode copies and compresses data into the Power BI file. DirectQuery does not store data inside Power BI; it leaves the data at the source.
* **Query Performance:** Import mode is exceptionally fast because it runs queries directly from local RAM. DirectQuery performance depends entirely on the speed of the source database.
* **Data Refresh:** Import mode requires a scheduled refresh to see new data. DirectQuery fetches live data instantly by sending queries to the source in real time.
* **Modeling Restrictions:** Import mode supports full DAX and Power Query functionality. DirectQuery limits certain DAX functions and Power Query transformations to ensure the source database can handle the translated SQL.
* **File Size:** Import mode files grow based on data volume (up to 1 GB for Pro). DirectQuery files remain very small because they only store metadata.





2\. Explain the consequence of a "Text" data type on a Card visual displaying sales and identify where in the workflow to correct this.



\->  A "Text" data type forces a Card visual to only display the first alphabetical value instead of aggregating the numerical sum. This produces nonsensical or blank results for Sales.



3\. Identify the specific menu or pane used to change a bar chart's sort order from alphabetical to descending by value.



\-> In Power BI, we can change a bar chart's sort order using the Visual Header menu on the chart itself.



**Steps**

* Select the bar chart visual.
* Click the More options (⋯) icon in the upper-right corner of the visual.
* Choose Sort by.
* Select the measure you want to sort on (for example, Sales or Revenue).
* Choose Sort descending.



This changes the chart from an alphabetical sort (based on the category field) to a descending sort based on the selected value.



Menu/Pane Used: Visual Header → More Options (⋯) → Sort By → Sort Descending





4\. Contrast filtering in Power Query versus using a visual-level "Top N" filter regarding their impact on other report visuals.



* Power Query Filter: Filter the data to keep only products with sales above ₹10,000. The remaining products are removed from the model. Every visual in the report will only see those filtered products.
* Visual-Level Top N Filter: Apply a Top 10 Products by Sales filter to a bar chart. That chart shows only the top 10 products, but other visuals (tables, maps, KPIs, etc.) can still use all 1,000 products.



5\. Describe how to modify a bar chart or use a DAX measure to show a region's percentage of total sales instead of absolute values.



\->  You can show a region's percentage of total sales either by using Power BI's built-in visual calculation settings or by writing a dynamic DAX measure.



\->  Method 1: Modify the Visual (No DAX Required) 

&#x09;

If you just want to transform absolute values into percentages without creating new formulas, use the built-in "Show Value As" feature.



* Select your bar chart on the report canvas.
* In the Visualizations pane, locate the X-axis (or Y-axis, depending on your chart orientation) where your Sales field is placed.
* Click the down arrow next to your Sales measure.
* Hover over Show value as and select Percent of grand total.
* The visual will automatically resize to 100% and calculate the percentages for each region.



6\. Explain why hardcoded file paths cause shared PBIX files to break and how to make a report portable for other users.



\->  Hardcoded file paths break shared PBIX files because they point to rigid local directories (e.g., C:\\Users\\John\\Documents) that don't exist for other users. To make a report portable, you can use Power Query Parameters for paths, leverage SharePoint/OneDrive syncing, or use Relative Paths to keep links dynamic.



###### **Why Hardcoded Paths Break Reports**



* Absolute Dependencies: When you import an Excel or CSV file locally, Power BI records the full, exact path to that file in the Power Query (M) code's Source step.
* User Profiles: A path pointing to your personal Windows username (e.g., C:\\Users\\Name\\) instantly returns a "File Not Found" error when opened by a colleague on their machine.
* Network Drives: Network or mapped drive letters can also vary depending on how a team member connects to the company's server.



###### **How to Make a Report Portable**



\->  Follow these three techniques to ensure your PBIX files work seamlessly across multiple developers or business users.



1\. Use Power Query Parameters (Best Practice)Instead of typing the path directly in your Source step, define a Power Query Parameter that each user can adjust locally without altering the underlying report logic.



* Define the Parameter: Go to Transform Data > Manage Parameters > New Parameter. Name it something like File\_Path and set the type to Text. Paste your current folder or file path as the default value.



* Apply to Queries: In your main table queries, click the Source step and change the hardcoded string to reference your new parameter.



* How to Port: When a different user opens the PBIX file, they simply go to Home > Edit Parameters, update the File\_Path to their local directory, and click Refresh.



2\. Centralize on SharePoint or OneDriveUsing cloud storage removes local directory issues entirely by using web-based Uniform Resource Locators (URLs) rather than local C-drives.



* Connect to the Cloud: Instead of importing from a local folder, use the SharePoint Folder or Web connector.



* Copy the URL: Use the HTTPS path directly from your SharePoint/OneDrive site.



* How to Port: As long as all users have viewing/editing permissions to that specific SharePoint document library, the file paths will resolve automatically for everyone.



3\. Use Relative Paths for Folders



\->  If your team works out of a shared root folder (e.g., a shared Dropbox folder or a specific project folder), you can dynamically concatenate the folder path so it auto-adjusts.



* By creating an Excel parameter table that dynamically extracts its own file path using the Excel =CELL("filename") function, you can load this dynamic path into Power Query to use as a master folder variable.

