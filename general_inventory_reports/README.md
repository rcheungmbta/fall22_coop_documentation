# Inventory Reports

These are the two major Tableau reports that I contributed to for Inventory

## DOH (Days On Hand)
This report is an informative report in which the primary use is to identify which items in the inventory are about to run out, based on historical usage.
DOH refers to the number of days we expect for a certain item to run out, so it is helpful to be informed of whether or not a PO has been created for an item that is about to run out, especially if the PO is expected to take a long duration to fulfill.

## Past Due Report
### PastDuePO
This report contains a table of all POs that are currently past their due date (based on the latest provided due date, in the "Revised Due Date" field). The criteria for the POs that show up on this report are as follows:
* Business Unit is MBTAI (an item belonging to inventory, I believe)
* Receipt Status is Partially Rcvd or PO Not Rcvd (regardless of how much has actually been received, the PO will show up on Past Due if the Receipt Status has not been updated)
* PO Status is Approved or Dispatched
* Line Status is Open

### PastDuePO_RevisedDD
This is the version of PastDuePO, using the Original Promise Date field in FMIS as a basis to determine whether a PO is "past due" or not.