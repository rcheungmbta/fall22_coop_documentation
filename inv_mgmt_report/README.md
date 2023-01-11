# IOH (Inventory On Hand) Value Historical View
# inv_monthly_report

The initial goal of this work was for the automation of the monthly inventory report. However, this approach was decided to be unfeasible (see Issues section).

The code is based on the transaction data formula, using transaction codes. 
This is the formula: 
> Qty Offset on total transaction = End  Qty - Start Qty = 041 + 022 + 024 - 031 + 050 - (051 + 054) + 010 + 020 - 030 - 012


---
### Issues
In v1 and v2, I first tried to do it with all the historical transaction data available, starting from 2004. However, this may have been too ambitious because there are many factors that were not considered. To get the sums, I grouped by item ID, date, and the base the items were stored in.
* Items may not have transactions since 2004, so their values would not be reflected in the derived total
* It is a lot of historical data, so there is a lot more room for error

To mitigate these issues, I decided to apply the formula using a "base file" as a starting point in v3.

Starting with the PL_INV_BY_BASE pull from April 2019, I applied the formula with transactions data (in the `txns` folder) using 4/19/2019 as a starting point.

However, I was still seeing a lot of discrepancies when I tried to match my results with the actual Total On Hand Value sums derived from PL_INV_BY_BASE pulls. 

This lead to v4, in which the objective changed from replicating PL_INV_BY_BASE into creating a Tableau tool that could be useful for analyzing min/max. 

Here, we stop applying the formula to try to derive the On Hand Value sum, but focus on getting the Qty On Hand fluctuations to analyze the usage of items over time, and whether we are buying too much or storing too much of a certain part, since warehouse space is expensive. 

---
### V4: The final version
This final v4 notebook takes in all the historical transaction data, starting from April 2004 to present day and outputs a CSV file with the following columns: TXN Date, TXN Item, TXN Output Qty, TXN Input Qty, and Overall Qty. 

This table details how many units of an item goes in/out of the system each day. It is currently exported to the Tableau Server as "Historical IOH Qty" data source in the "Logistics Data Sources" folder. However this data only goes up to October 2022, and is not being updated live.

I use this data source in the ```Historical IOH Qty.twb``` Tableau workbook, where you can explore and isolate items to analyze their usage over time, comparing it to the CS004 Min/Max Qty. Here are some interesting item IDs that we had looked at: #04596067, #05295197, #02593057.


### History of this work
This work was also previously conducted by co-ops Anni Yuan (O:\PP-PROLOG\VENDOR_MANAGEMENT\Vendor Management Team\Co-Ops\Anni Yuan) and [Peter Benson](https://github.com/mbtapbenson/MBTA-coop-documentation). The formula above has been verified, so it makes sense in theory and in practice.
