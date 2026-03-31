# 💳 India Credit Card Intelligence Dashboard
### Power BI Portfolio Project | 2026

---

## 📌 Business Problem
India's credit card market has 15+ major cards across 5 categories —
Cashback, Travel, Fuel, Lifestyle, and Secured. Customers struggle to
compare cards, banks struggle to understand rejection patterns, and
analysts struggle to identify which customer segments generate the
most reward value. This dashboard solves all three problems in one
interactive report.

---

## 📂 Dataset
4 CSV files — real credit card data + synthetic customer & transaction data and application

| File | Rows | Description |
|---|---|---|
| credit_cards_raw.csv | 16 | 15 real Indian credit cards — HDFC, Axis, SBI, ICICI, Amex |
| customers_raw.csv | 21 | 20 synthetic customers across Indian cities |
| applications_raw.csv | 24 | 23 applications including 3 rejections |
| transactions_raw.csv | 56 | 55 transactions across all spend categories |

---

## 🔧 Data Quality Issues Fixed (Power Query)
30+ data quality issues identified and resolved across 4 tables:

| Issue | Table | Fix Applied |
|---|---|---|
| Fees stored as "Rs.999" strings | credit_cards | Stripped prefix, converted to number |
| Rewards stored as "5%" strings | credit_cards | Stripped %, converted to decimal |
| Inconsistent category case | All tables | Text.Proper / Capitalize Each Word |
| Income stored as "1,25,000" | customers | Removed commas, converted to number |
| Mixed date formats (3 formats) | All tables | Power Query date type conversion |
| Gender inconsistency (6 variants) | customers | Custom column M-code standardisation |
| Credit limit as "Rs.2,00,000" | applications | Stripped prefix and commas |
| NULL amount as string "NULL" | transactions | Replace values → null |
| Negative amount (-500) | transactions | Flagged as "Data Error" |
| Blank rejection reasons | applications | Replaced with "Not Specified" |
| Duplicate rows | credit_cards, applications | Remove Duplicates step |
| Blank rows | customers | Remove Blank Rows step |
| Invalid email (missing @) | customers | Flagged with Custom Column |
| Merchant trailing spaces | transactions | Trim transformation |

---

## 🛠️ Tools & Features Used

### Power Query
- Replace Values, Remove Duplicates, Remove Blank Rows
- Conditional Columns, Custom Columns with M-code
- Date type standardisation across 3 mixed formats
- Text.Proper, Text.Upper, Text.Contains, Text.Replace
- Duration.Days for live days-to-expiry calculation
- Advanced Editor — full M-code pipeline visible

### Data Model
- Star schema — 4 tables, 3 relationships
- One-to-Many cardinality, Single cross-filter direction
- applications as fact table, credit_cards + customers + transactions as dimensions

### DAX
- CALCULATE, DIVIDE, SUMX, RANKX, SWITCH(TRUE())
- VAR / RETURN for optimised measures
- Calculated columns vs measures — used both correctly

### Report Features
- 3 report pages
- Custom dark theme with gold accents
- Conditional formatting — colour scale, data bars, icon sets
- Page navigation buttons
---

## 📊 Key Findings

- **IDFC FIRST Ashva** offers unlimited domestic lounge access at
  Rs.2,999/year — the best lounge-per-rupee ratio of any travel card
- **Axis ACE** delivers higher reward yield % than HDFC Infinia
  despite Infinia holders spending 10x more in absolute terms
- **1 application rejections** were for Travel category cards —
  the highest CIBIL barrier category in the dataset
- **International transactions** account for only 12% of total
  transactions but 38% of total spend — high-value customers skew
  heavily toward international usage

---

## 📁 Files in This Repository
```
cc-powerbi-project/
├── data_raw/                  ← Original messy CSV files
│   ├── credit_cards_raw.csv
│   ├── customers_raw.csv
│   ├── applications_raw.csv
│   └── transactions_raw.csv
├── screenshots/
│   ├── before_cleaning/       ← Power Query before screenshots
│   ├── after_cleaning/        ← Power Query after screenshots
│   ├── data_model.png         ← Star schema screenshot
│   └── dashboard_pages/       ← All 3 report page screenshots
├── cc_dashboard.pbix          ← Power BI file
└── README.md
```

---

## 🚀 How to Open
1. Download Power BI Desktop (free) from microsoft.com/en-us/power-bi
2. Clone or download this repository
3. Open `cc_dashboard.pbix` in Power BI Desktop
4. If data refresh needed — update file paths in
   Power Query → Data Source Settings

---

**Author:** Akash | Kolkata, India
**LinkedIn:** your-linkedin-url
**Tools:** Power BI Desktop · DAX · Power Query · M-code
