Help sheet for me to fill ITR2.

Use at your own risk. I am not liable for any mistake and penalty. Crosscheck multiple times before submitting.
* Sometime Dates as shown as numbers in Excel. Format the column or cells to date type.

----------------------------------------------------------------------------
Important Schedule to look for.
---------General--------------
1. General Information (Prefilled)							: Fill basic fields						
---------Income---------------
2. S 	: Salary 									: Mostly Prefilled from AIS
3. CG 	: Capital Gains									: Add Short Term and Long Term Capital Gain
4. OS 	: Other Source 		: Interest Dividend					: Add Dividend + Interest
5. FSI 	: Foreign Source Income								: Describing Information : CG + Dividend obtained from foreign source.
6. TR 	: Tax Relief									: Dividend Tax Paid outside India on which relief is claimed. 
--------Other------------------
7. CYLA 	: Current Years Losses After set-off of current years			: Check and Submit
8. BFLA 	: Brought Forward Losses after set off of previous years		: Check and Submit
9. CFL  	: Process CYLA and BFLA							: Check and Submit
10. FA 	 	: Foreign Assists Details.						: Fill all foreign assets till December 2024
---------Tax-------------------
11. TI 	: Total Income									: Validate the report of all incomes from all income sources.		
12. TP	: Tax Already Paid 								: Validate from Form 16 and other TDS sources.
13. TTI	: Total Tax Liability on Income							: Validate the total tax, obtained relief and amount payable.
----------------------------------------------------------------------------


--------------------------------------------------------------------------------------------------------------------------------------------------------
Prepare Datasheets for ITR2.
--------------------------------------------------------------------------------------------------------------------------------------------------------
Prepare Dividend and Capital Summary Excel Sheet.
NOTE: 
 	- For Paying Tax : Use all entries till March 2025.
	- For Reporting Foreign Assets : Use all entries till December 2024.

EXCEL:
	- Sheet RSU and ESPP are for Dividend Calculation. 
	- Sheet CG is to prepare Capital Gain from sales of units.
	- Sheet FA is to prepare values to fill in Schedule FA

1. Download all available RSU and ESPP reports from ADP Portal.
2. Download E*TRADE Client Statements between Jan 2024 to Mar 2025 on the dates when Dividend payment has happened.
3. Download E*TRADE Holding Sellable status or use values directly from the website.
4. Download E*TRADE Gain and Losses Statement for getting sale price or purchase price for all sales made.

----->>>> Dividend Calculation
MANDATORY:
** Update U9 with 0.03 if income above 50L. 
1. Open E*TRADE Client Statements for each Dividend Payment Date between April 2024 To March 2025.
2. Fetch the values "Qualified Dividend" and "Tax Withholding".
3. Fill these values in appropriate rows in Columns "Dividend earned USD" M8:11 and "Dividend Tax deducted in US at 25%" N8:11
4. Fetch these values from the sheet.
	S8 	: Total Dividend INR	
	S10 	: 25% Tax INR
	V11 	: 31.2% Tax INR
	W11	: Tax Payable

OPTIONAL : 
If you want to validate this value with all the individual stocks obtained. : FOR PERSONAL SATISFACTION
1. Copy all the multiple RSU Reports Entries obtained till 31st March 2025 to RSU Sheet Column A15 : O15. Keeps appending data below.
2. For each entry, using Grant Date and Vest Date. Find the Sellable Quantity from E*TRADE Holdings Sellable Sheet or Website.
3. Drag and drop the sample entry to auto use or auto populate the values in all the remaining columns. Q15 : Y15.
4. Delete First Entry after filling correct information.

5. Same for ESPPs, if any. 
6. Copy all the multiple ESPP Reports Entries obtained till 31st March 2025 to ESPP Sheet Column A5 : K5.
7. Find the Sellable Quantity and Fill in L5. In most cases, the sellable Quantity is the ESPP Shares completely. 
8. Drag and drop the sample entry to auto use or auto populate the values in all the remaining columns. M : U.
9. Delete the dummy entry.

10. If any RSU or ESPP sold in between. Update the Cell U and V for those entries.
	- There are 4 IF condition in Cell U14 and V14, considering all 4 dividend received.
	- If any RSU or ESPP is sold in between, Remove the IF Blocks not to consider for calculation. 
	- And make the closing value 0.
	- * Next year, will make this scripted with selling date. And add partial sales support.
	
11. Check the Cell W11 and X11.  W11 is tax liability using E*TRADE Statements and is correct one. 
	X11 is tax liability with dividends earned per stock and calculated individually for each stock.
	Both as expected to be same. Or else minor error due to Rounding Error.

----->>>> Capital Gain Calculation,  Assuming only Gain happened
MANDATORY: 
If sold any RSU and ESPPs.
1. Sheet CG, Copy the ESPPs sold and Manually add Date of selling and Execution price USD. 
2. Use the information to fill below table for Gain Calculation
	- Fill Purchase Date FMV Purchase and Num Shares, TT Rate  from above Data collected.
	- Fill Sell Date, Sell Price Per Unit, TT Buy Rate on that Selling Date.
	- Rest of the field will be autocompleted.
3. Delete Sample Queries.

Collect for all entries.
	SUM(L8:L*)	: Full Value of Consideration
	SUM(F8:F*)	: Cost of Acquisition
	0		: Tax outside India
	SUM(N8:N*) 	: Gains from outside India.
	SUM(P8:P*)	: Tax Payable @ 31.24 % 	

----->>>> Foreign Assets Calculation
MANDATORY:
Same steps as Dividend Calculation only here the RSU and ESPP entries will be limited till December 31 2024.

Fill the data obtained in the sheet to A3 Template downloaded from Schedule FA. Sample Attached.
Increment Index for each entry
* Represent entries to be same for all
! Represent entries to be different and fetched from this sheet.

Country/Region name,								- Index
*Country Name and Code,								- 2
*Name of entity,								- QUALCOMM INC.(QCOM)
*Address of entity,								- 5775 Morehouse Drive San Diego CA
*ZIP Code,									- 92121
*Nature of entity,								- Company Listed on NASDAQ

!Date of acquiring the interest,						- YYYY-MM-DD *<Format should not change while uploading>
!Initial value of the investment,						- Take value from column Q
!Peak value of investment during the Period,					- Take value from column R
!Closing balance,								- Take value from column S
!Total gross amount paid/credited with respect to the holding during the period,- Take value from column V  * All Dividend	
!Total gross proceeds from sale or redemption of investment during the period	- Fill value from CG sheet  * Selling Price.

This sheet A3.csv will be used to declare FA in ITR2.


--------------------------------------------------------------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------------------------------------------------------------

--------------------------------------------------------------------------------------------------------------------------------------------------------
Fill Form 67. To Claim Foreign Tax Credit for Tax Paid on Dividend in US.
--------------------------------------------------------------------------------------------------------------------------------------------------------
a. Find an fill Form 67.
b. Fill Part A. 
	- Name of Country, Source of Income Dividend
	- Income from outside India 			: ----->>>> Dividend Calculation -> Total Dividend
	- Tax paid outside India 			: ----->>>> Dividend Calculation -> Tax @ 25
	- Rate(%)					: 25%
	- Tax payable on such income under normal provisions in India : : ----->>>> Dividend Calculation -> Tax @ 31.24
	- Article No. of Double Taxation Avoidance Agreements		: 10
	- Rate of tax as per Double Taxation Avoidance Agreements(%	: 25%
	- Amount					: ----->>>> Dividend Calculation -> Tax @ 25
	- Total foreign tax credit claimed		: ----->>>> Dividend Calculation -> Tax @ 25
	- Tax payable on such income under section 115JB/JC : 0
	- Credit claimed under section 91		: 0

c. Fill Part B. Read and Update
d. Verify
e. Attachments. : To claim FTC.
	- 1042S 
	- Credit Statements from each Quarter for dividend.
	- Small Txt, with Dividend Received in all 4 quarters
📌 Practical Tip from Chat Gpt:
Attach 1099-DIV (or 1042-S) + Dividend Transaction Report (CSV/PDF).
Make sure both Income (Gross dividend) and Tax Withheld are clearly visible.
You can combine multiple pages into a single PDF and upload.
	

--------------------------------------------------------------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------------------------------------------------------------
Fill ITR2.
--------------------------------------------------------------------------------------------------------------------------------------------------------
1. Select the default options available, check all schedules without adding any information, and note the Tax Paid and Payable at the end
	without adding anything.

 
------>>>> 2. Fill Schedule Capital Gain : CG
a. Open Schedule CG and Fill in Form A(I) -> 5. 
	ii. 	Full value of consideration in respect of assets other than unquoted shares :: Selling Price 
	b(i) 	Cost of acquisition without indexation					    :: Purchase Price.
b. Check the Schedule BFLA for the new entry added.
c. Open Schedule CG and Fill in Form/Table F -> 4
	Quarterly breakout of the CG depending upon the date received

------>>>> 3. Fill Schedule Other Sources: OS for dividend
a. Open Schedule OS and Fill in Form 1 -> a 
	a. Dividends, Gross (ai + aii + aiii)						    :: Add RSU + ESPP dividend to existing value
   In the same schedule, fill in Form/Table 10 -> 3a.
	b. Quarterly Breakout of the Dividend Received						    :: Present in the sheet. +-1 to match.

------>>>> 4. Schedule Foreign Source Income: FSI : To denote what part of capital gain and dividend are from outside India.
a. Open Schedule FSI and add/edit
	a. Country Code : 2-USA
	b. TIN -> PAN Number***
	c. Fill Capital Gain with values from  ----->>>> Capital Gain Calculation Above
		Relevant article of DTAA if relief claimed u/s 90 or 90A (f) : 13
	d. Fill Other Sources with Dividend with values ----->>>> Dividend Calculation Above
		Relevant article of DTAA if relief claimed u/s 90 or 90A (f) : 10

	
------>>>> 5. Schedule Tax Rebate: TR : To apply for tax relief for tax paid outside India on Dividend
a. Open Schedule TR, Select 90 in Relief Claimed under section option and No for tax paid outside India and Submit.

------>>>> 6. Schedule Foreign Assets: FA : Only For Reporting FA till 31st December 2024
a. Open Schedule FA, In Section A3. 
b. Download Template A3, 
c. Fill template with all foreign stocks till 30th December 2024, as already mentioned in ----->>>> Foreign Assets Calculation


** All Done. All that is left is to open remaining Schedules and verify and keep finalizing them.
Validate the values of Total Income TI and Total Tax on Income TTI and check if the extra tax that has occurred is 
matching the sum of capital Gain Tax in Sheet CG + Dividend Tax Payable Calculated above. 
** Some extra value may be there for 4% cess and Interest if not pay advanced tax for these dividends
Use last sheet for cross checking.

--------------------------------------------------------------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------------------------------------------------------------



	
 

