---
output:
  html_document: default
---
# CO Counties Marijuana Dataset<br>
Author: David Martinez<br>
contact: davelovesdata@gmail.com<br>
github: https://github.com/davelovesdata/CO-Marijuana-Dataset<br>

## Project Description<br>
The Colorado Counties Marijuana Dataset was created to use as a tool in determining if machine learning can be used to predict county level sales. As of August 2018, about thirty (46%) of Colorado's sixty-four counties prohibited medical marijuana sales and twenty-seven (42%) prohibited recreational sales. This is an impressive growth market for the marijuana industry and should machine learning predictive analytics prove effective, will identify counties to prioritize business efforts against.<br> 

## Data Collection and Processing Methodology<br>
Multiple public source datasets obtained from the Colorado Department of Revenue (https://www.colorado.gov/pacific/revenue) were manually wrangled into two excel workbooks: CO_County_Sales_2014_2018.xlsx and CO_County_Taxes_2014_2018.xlxs. Each workbook contains monthly level sales/taxes (compilied by year) and aggregate level sales/taxes (compiled over many years).<br>

Data collection was performed against monthly reports found at: <br>
https://www.colorado.gov/pacific/revenue/colorado-marijuana-sales-reports (monthly sales reports for each county by month and year).<br>
https://www.colorado.gov/pacific/revenue/colorado-marijuana-tax-data (monthly taxation reports for each county by month and year). <br>

### 1. Sales file description (CO_County_Sales_2014_2018.xlsx)<br>
The sales files contains not only county level medical and recreational sales by year, but also population information and location information (State, County, Latitude, Longitude, Region). Additionally, medical and recreational sales for each county were applied against county population to determine an average of sales per county citizen for both medical and recreational sales.<br>

**Dataset fields:**<br>
State - Currently only "COLORADO"<br>
County - Colorado County Name (e.g., "Adams" or "Yuma")<br>
Latitude - Latitude of County center<br>
Longitude - Longitude of County Center<br>
Region - An arbitrary assignment I made to quarter the state into geographic quadrants.<br>
Year - Collection Year<br>
Population - Estimated population between census reporting periods<br>
Med_Sales - County level sales of Medical Marijuana (see value explanation below)<br>
Rec_Sales - County level sales of Recreational Marijuana (see value explanation below)<br>
med_sales_per_citizen - a calculated value determined by dividing the "Med_Sales" value by the "Population" value.<br>
rec_sales_pre_citizen - a calculated value determined by dividing the "Rec_Sales" value by the "Population" value.<br>

Med_Sales, Rec_sales, and the two calculated values have three possible values:<br>
**0** = No Sales of legal Marijuana occurred in that county. The original source material did not include counties that had no sales. This information was added to show a full statewide picture as well as county adoption over time.<br> 
**NR** = Not releasable due to confidentiality requirements. The sum of all NR counties ("Not Reported" in the 'County' column) are captured as the last line for each year.<br>
**x** = A positive number representing sales at the dollar level.<br><br>

### 2. Taxes file description (CO_County_Taxes_2014_2018.xlsx)<br>
The taxes file contains taxes collected per county in three columns: Medical Sales Tax (2.9%), Retail Sales Tax (2.9%), Retail Marijuana Special Sales Tax.

**Dataset fields:**<br>
County - Colorado County Name (e.g., "Adams" or "Yuma")<br>
Year - Collection Year<br>
Medical Sales Tax (2.9%) - Sales tax applied to medical marijuana only. This is the only state tax paid.
Retail Sales Tax (2.9%) - Sales tax applied to retail marijuana. Starting in 2018, this tax was no longer collected.
Retail Marijuana Special Sales Tax - an additional tax on retail marijuana sales.

Medical Sales Tax (2.9%), Retail Sales Tax (2.9%), Retail Marijuana Special Sales Tax have three possible values:<br>
**0** = No taxes from legal Marijuana occurred in that county. The original source material did not include counties that had no tax information. This information was added to show a full statewide picture as well as county adoption over time.<br> 
**NR** = Not releasable due to confidentiality requirements. The sum of all NR counties ("Not Reported" in the 'County' column) are captured as the last line for each year.<br>
**x** = A number representing taxes at the dollar level. Negative values indicate previous months overpayment of taxes being returned.<br><br>

