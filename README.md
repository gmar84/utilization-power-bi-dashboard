### Utilization Dashboard with Power BI

---

### Description

This is a Power BI Dashboard I created for my current role. It loads data from a MySQL server which is hosted on AWS, so the data is always up to date. It uses various visuals to show utilization performance for business services and is primarily used by the company executives.

### Overview

The first page is the welcome page, showing the company logo and the reports available for selection. The Summary page displays utilization metrics: Total amount authorized, amount billed and in-process, and amount not utilized. The average utilization is calculated and shown in the center as a gauge. There is also a date slicer to narrow the data down further, as well as two bookmarks which includes/excludes a specific service from the data, as you may want to filter this data out of the report in some cases. Below is a bar chart showing average utilization by Group, which is a custom feature engineered by assigning certain services a specific group number. There is also a bar chart showing average utilization by QP/Client/Service, which allows the user to drill down to show this data by each of the desired categories.

The second page is the Under-Utilization report. This page shows the amount that was not utilized. Below is a bar chart which shows this data by QP/Client/Service, allowing the user to drill down by each category. There are also two slicers: Client Name and Date Select, which allows viewing data filtered by the chosen selections.

The third page is the Over-Utilization report. This page shows the amount that was over utilized. Below is a bar chart which shows this data by QP/Client/Service, allowing the user to drill down by each category. There are also two slicers: Client Name and Date Select, which allows viewing data filtered by the chosen selections.

## Files

`README.md`- This file

[Dashboard.pdf](Dashboard.pdf) - Preview of the Dashboard

### Filters

Date Select Slicer: Allows ability to filter data table and visuals by Year and Month. 

Client Name Slicer: Allows ability to select a specific client for performance review.

### Visuals

Cards:
- KPIs which include Utilized, Billed + In process, Not Utilized, Under utilized, and over utilized

Gauges:
- Average Utilization

Bar Charts: 
- Average Utilization by GRP
- Average Utilization by QP/Client/Service
- Under-utilization amount by QP/Client/Service
- Over-utilization amount by QP/Client/Service

### DAX Formulas Used

1. Returns the month from the date:

- `month = FORMAT('notes'[date_of_service],"mmmm")`

2. Returns the month number from the date:

- `MonthNumber = FORMAT('notes'[date_of_service],"mm")`

3. Used to encode names for privacy purposes:

- `qp_code = 
var Lname = MID(utilization[qp], FIND(", ", utilization[qp], 1, 0)+1, 4)
var Fname = LEFT(utilization[qp], 2)
Return
    UPPER(CONCATENATE(Lname, Fname))`

