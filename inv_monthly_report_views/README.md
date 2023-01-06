# inv_monthly_report_views

This folder holds different components/pages to the Inventory Monthly Report. (All components should already be integrated into the November and December 2022 Inventory Monthly Reports)

### monthly_report_historical_oh_value.twb 
This is the Tableau workbook containing the historical OH value trend line on the first page of the Monthly Report.
It uses the Inventory Cross Check file as a data source. The values in this Excel file need to be manually calculated and inputted at the beginning of each month. (O:\PP-PROLOG\VENDOR_MANAGEMENT\Data_Analytics\Data_Files\Inventory_Mgmt_Data\3_Inventory_On_Hand)

### doh folder
This folder contains my work for the historical days on hand page of the Inventory Monthly Report
#### DOH Historical Data Append.tfl
This is the flow (published to the Tableau server) that generates the summary values for DOH data each month. 
It is scheduled to automatically run on the 1st of every month, and appends a row of values to the data source named "DOH Count Summary Historical" on the server.
#### inv_monthly_report_doh_historical_view.twbx 
This is the Tableau workbook contianing the visualization for the report.

### pastdue folder
This folder contains my work for the historical past due page of the Inventory Monthly Report
#### PastDuePO Historical Data Append.tfl
This is the flow (published to the Tableau server) that generates the summary counts for past due data each month. 
It is scheduled to automatically run on the 1st of every month, and appends a row of values to the data source named "Past Due PO Historical Data" on the server. This is the current data source for the report visualization.
#### PastDuePO Historical Data Append (by Orig Promise Date).tfl
This is a duplicate flow ```PastDuePO Historical Data Append.tfl```, except it calculates based off of the Original Promise Date as the PO Due Date. In comparison, the current flow uses the Revised Due Date as the PO Due Date. 
This flow is to be used when we transition over to using the Original Promise Date as the criteria for what is considered "Past Due."
This flow appends a row to the data source named "Past Due PO Historical Data (using Orig Promise Date)" on the server. 
#### inv_monthly_report_pastdue_historical.twbx
This is the Tableau workbook contianing the visualization for the report.
