# ITR2 – Dividend and ESPP Short-Term Capital Gain  

Help sheet for me to fill ITR2.  

⚠️ **Disclaimer**: Use at your own risk. I am not liable for any mistake and penalty. Cross-check multiple times before submitting.  

📌 **Note**: Sometimes dates are shown as numbers in Excel. Format the column or cells to *Date type*.  

---

## 📑 Important Schedules to Look For  

### General
1. **General Information (Prefilled)** – Fill basic fields  

### Income
2. **S: Salary** – Mostly prefilled from AIS  
3. **CG: Capital Gains** – Add Short Term and Long Term Capital Gains  
4. **OS: Other Sources (Dividend + Interest)** – Add Dividend + Interest  
5. **FSI: Foreign Source Income** – Information about CG + Dividend obtained from foreign source  
6. **TR: Tax Relief** – Dividend tax paid outside India on which relief is claimed  

### Other
7. **CYLA: Current Year Losses After Set-off** – Check and submit  
8. **BFLA: Brought Forward Losses After Set-off** – Check and submit  
9. **CFL: Process CYLA and BFLA** – Check and submit  
10. **FA: Foreign Assets Details** – Fill all foreign assets till December 2024  

### Tax
11. **TI: Total Income** – Validate report of all incomes from all sources  
12. **TP: Tax Already Paid** – Validate from Form 16 and other TDS sources  
13. **TTI: Total Tax Liability on Income** – Validate total tax, relief, and amount payable  

---

## 📊 Prepare Datasheets for ITR2  

Prepare **Dividend and Capital Summary Excel Sheet**.  

**Notes:**  
- For **Paying Tax**: Use all entries till **March 2025**  
- For **Reporting Foreign Assets**: Use all entries till **December 2024**  

### Excel Sheets Used
- **RSU** and **ESPP** → For Dividend Calculation  
- **CG** → For Capital Gain (sales of units)  
- **FA** → For values to fill in Schedule FA  

### Downloads Required
1. Download all available **RSU and ESPP reports** from ADP Portal.  
2. Download **E*TRADE Client Statements** between Jan 2024 to Mar 2025 on the dates when dividend payments happened.  
3. Download **E*TRADE Holding Sellable status** (or directly from the website).  
4. Download **E*TRADE Gain and Losses Statement** (to get sale price or purchase price for all sales).  

---

## 💰 Dividend Calculation  

### Mandatory  
0. Update **Cell U9 = 0.03** if income above ₹50L.  
1. Open **E*TRADE Client Statements** for each dividend payment date between April 2024 to March 2025.  
2. Fetch the values:  
   - **Qualified Dividend**  
   - **Tax Withholding**  
3. Fill these values in Excel:  
   - `M8:11` → Dividend earned (USD)  
   - `N8:11` → Dividend Tax deducted in US at 25%  
4. Calculate average tax rate.
   - Calculate Total Income and fill at T2.  Total Income assuming no relief to dividend.
   - Calculate Total Tax and fill at T3. Use Income Tax Calculator, or utilize the ITR by skipping Tax Relief.
   - Average Rate = Total Tax / Total Income.
5. Auto-calculated values:  
   - `S8` → Total Dividend INR  
   - `S10` → 25% Tax INR  
   - `V11` → 31.2% Tax INR  
   - `W11` → Delta tax
   - `T5` → Tax payable on such income under normal provisions in India (d) = Dividend * Average Tax (21.2% for me).

### Optional (For Personal Validation)  
If you want to validate values against all individual stock entries:  
1. Copy RSU Reports (till 31st March 2025) into `RSU` Sheet → Columns `A15:O15` (append below).  
2. For each entry, use **Grant Date** and **Vest Date** → Find Sellable Quantity from **E*TRADE Holdings Sellable Sheet/Website**.  
3. Drag/drop sample entry to auto-populate values in Columns `Q15:Y15`.  
4. Delete the first dummy entry after updating.  
5. Repeat the same for ESPPs:  
   - Copy ESPP reports into `ESPP` Sheet → Columns `A5:K5`  
   - Find sellable quantity and fill **L5** (usually all ESPP shares are sellable).  
   - Drag sample entry to auto-populate `M:U`.  
   - Delete dummy entry.  
6. If RSU/ESPP were **sold in between**:  
   - Update Cells `U` and `V` for those entries.  
   - There are 4 IF conditions in Cells `U14` and `V14` (covering all 4 dividends).  
   - If sold, remove the IF blocks for that entry and make closing value = 0.  
   - *(Next year: Plan to script this for selling dates and partial sales support).*  
7. Check Cells `W11` and `X11`:  
   - `W11` → Tax liability using E*TRADE Statements (**Correct one**)  
   - `X11` → Tax liability using per-stock calculations  
   - Both should be same (minor rounding error possible).  

---

## 📈 Capital Gain Calculation (if RSU/ESPP sold)  

### Mandatory  
If any RSU/ESPP sold:  

1. In **Sheet CG**:  
   - Copy ESPPs sold → Add *Date of Selling* and *Execution Price (USD)*  
   - Enter:  
     - Purchase Date, FMV, Number of Shares, TT Rate (Purchase Date)  
     - Sell Date, Sell Price per Unit, TT Buy Rate (Sell Date)  
   - Remaining fields auto-complete.  
2. Delete sample queries after filling real data.  

### Collect Totals  
- `SUM(L8:L*)` → Full Value of Consideration  
- `SUM(F8:F*)` → Cost of Acquisition  
- `0` → Tax outside India  
- `SUM(N8:N*)` → Gains from outside India  
- `SUM(P8:P*)` → Tax Payable @ 30%  

---

## 🌍 Foreign Assets (Schedule FA)  

### Mandatory  
Same steps as Dividend Calculation, but limit entries **till Dec 31, 2024**.  

Fill obtained data into **A3 Template (Schedule FA)**.  

- Increment Index for each entry  
- `*` → Values remain same for all entries  
- `!` → Values differ (fetched from sheet)  

| Field | Value |
|-------|-------|
| *Country/Region Name | USA |
| *Country Name & Code | 2 |
| *Entity Name | QUALCOMM INC. (QCOM) |
| *Address | 5775 Morehouse Drive, San Diego, CA |
| *ZIP Code | 92121 |
| *Nature of Entity | Company Listed on NASDAQ |
| !Date of Acquiring | YYYY-MM-DD (must remain in correct format) |
| !Initial Value | From Excel Column Q |
| !Peak Value | From Excel Column R |
| !Closing Balance | From Excel Column S |
| !Total Gross Amount Credited | From Excel Column V (All Dividends) |
| !Gross Proceeds from Sale | From CG sheet (Selling Price) |

This `A3.csv` is uploaded to declare FA in ITR2.  


Compute manually for **A2 Template (Schedule FA)**.  

- One entry per account

| Field | Value |
|-------|-------|
| Country Name & Code | 2 |
| Name of financial institution | E*TRADE FROM MORGAN  STANLEY |
| Address of financial institution  | P.O. BOX 484  JERSEY CITY NJ |
| ZIP Code | 07303 |
| Account Number | * |
| Status | I filled Owner |
| Account opening date | Date of Welcome to Etrade mail |
| Peak Balance During the Period | From final statement of the year, I found the peak date after that and multiplied value and TT Rate |
| Closing Balance | Same Final value with stock value and tt rate at 31st Dec 2024 |
| Nature of Amount  | I selected Proceeds from sale or redemption of financial assets for STCG And Dividend |
| Amount  | Dividend |

---

## 📝 Fill Form 67 – Foreign Tax Credit (FTC)  

### Steps  
1. Open **Form 67**  
2. **Part A**:  
   - Country: USA  
   - Source of Income: Dividend  
   - Income from outside India: → Dividend Calculation → Total Dividend  
   - Tax paid outside India: → Dividend Calculation → Tax @ 25%  
   - Rate: 25%  
   - Tax payable in India: → Dividend Calculation → Tax @ AverageTaxRate% 
   - Article No. of DTAA: 10  
   - Rate of Tax as per DTAA: 25%  
   - Amount: Dividend Calculation → Minimum of both taxes.
   - Total foreign tax credit claimed: Dividend Calculation → Minimum of both taxes. 
   - Tax payable under Section 115JB/JC: 0  
   - Credit claimed under Section 91: 0  
3. **Part B**: Fill and update as required  
4. Verify & Attachments:  
   - 1042-S  
   - Credit statements from each quarter for dividend

📌 **Practical Tip (from ChatGPT):**  
Attach **1099-DIV (or 1042-S)** + **Dividend Transaction Report (CSV/PDF)**.  
Ensure both *Gross Dividend* and *Tax Withheld* are clearly visible. Combine multiple files into a single PDF if needed.  

---

## 🧾 Filling ITR2  

### Step 1 – Validate  
Open ITR2 → Select default options → Check all schedules (before adding info) → Note **Tax Paid** and **Payable**.  

### Step 2 – Schedule CG (Capital Gain)  
- **Form A(I)–5(ii)**: Full value of consideration (Selling Price)  
- **Form A(I)–5(b)(i)**: Cost of acquisition (Purchase Price)  
- **Form F–4**: Quarterly CG breakout  

### Step 3 – Schedule OS (Other Sources: Dividend)  
- **Form 1(a): Dividends, Gross (ai + aii + aiii)** → Add RSU + ESPP dividend  
- **Form 10–3(a)**: Quarterly Dividend Breakout (cross-check with sheet, ±1 acceptable)  

### Step 4 – Schedule FSI (Foreign Source Income)  
- Country Code: 2 (USA)  
- TIN: PAN Number  
- Capital Gains → From CG calculation (DTAA Article 13)  
   - Tax payable on such income under normal provisions in India is strictly 30% for Foreign Stocks
- Other Sources → Dividend (DTAA Article 10)  
   - Tax payable on such income under normal provisions in India is Average Tax Rate.

### Step 5 – Schedule TR (Tax Relief)  
- Select **90** under Relief Claimed Section  
- Select **No** for “tax paid outside India”  
- Submit  

### Step 6 – Schedule FA (Foreign Assets)  
- Open **Section A3**  
- Download Template A3  
- Fill with all foreign stocks till 30th Dec 2024 (from FA calculation above)  
- Open **Section A2**
-  Fill the values as described above. 

---

## ✅ Final Check  

- Open all schedules, verify, and finalize.  
- Validate **Total Income (TI)** and **Total Tax on Income (TTI)**.  
- Ensure extra tax matches:  
  `Capital Gain Tax (CG sheet) + Dividend Tax Payable`  
- Some extra difference may appear due to:  
  - 4% Cess  
  - Interest (if advance tax not paid on dividends)  
- Use last sheet for cross-checking.  

---
