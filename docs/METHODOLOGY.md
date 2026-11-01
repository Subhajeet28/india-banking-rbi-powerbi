# Methodology

## Question and analytic approach

How did scheduled commercial banks' deposits, credit and office counts change in India during 2015–2025? How does banking activity vary across states/UTs? How do reported agriculture and industry credit balances compare?

This is a **descriptive** analysis of RBI statistics; it does not measure financial inclusion, unmet demand, productivity or causal mechanisms.

## Source and tables

Primary publication: [RBI *Handbook of Statistics on Indian States, 2024–25*](https://www.rbi.org.in/Scripts/AnnualPublications.aspx?head=Handbook%20of%20Statistics%20on%20Indian%20States), tables 152 (offices), 155 (deposits), 156 (credit), 157 (agricultural credit), 158 (industrial credit). Data imported from each `(ii)` worksheet, 2015–2025, end-March series. Table numbers refer specifically to the **2024–25** edition and can differ in previous editions.

## Power Query workflow

1. Keep the five RBI Excel files unchanged as source datasets.
2. Remove preamble and footer rows; promote year headings into columns.
3. Exclude six regional aggregates and the ALL INDIA total from the state-level fact table.
4. Unpivot years into State, Year and metric value columns.
5. Standardise geography strings (Trim/Clean, consistent names).
6. Preserve unavailable dash and empty entries as actual `null`, not as zero, and do not drop otherwise valid State–Year rows.
7. Validate State–Year keys for duplicates, then merge five cleaned metric queries by State and Year using left joins.
8. Check that the result remains one observation per State–Year key and the expected 407 rows, 7 columns.

**Final table** `Fact_Banking`: `State` (text), `Year` (whole number), `Deposits_Crore` (decimal), `Credit_Crore` (decimal), `Bank_Offices` (whole number), `Agriculture_Credit_Crore` (decimal), `Industry_Credit_Crore` (decimal). All measures can contain nulls where data is unavailable.

## Calculation definitions

- Total deposits (₹ crore) = sum of `Deposits_Crore` within a single selected end-March year.
- Total credit (₹ crore) = sum of `Credit_Crore` within a single selected end-March year.
- Total bank offices = sum of `Bank_Offices` within a selected year.
- Agriculture/industry credit = sums of their respective measures within the selected year.
- **1 lakh crore = 100,000 crore**; divide RBI ₹ crore measures by 100,000 for the KPI cards and high-level plots.
- Calculated C-D ratio = `(total credit / total deposits) × 100`, displayed as a percentage. Do not sum state-level ratios.
- Growth between endpoints = `(2025 value / 2015 value − 1) × 100`.
- The two-sector pie shows `agriculture / (agriculture + industry)` and `industry / (agriculture + industry)`, not the two sectors' proportions of all credit.

These are the **calculation semantics** used in project explanations. The exact DAX expressions within the Power BI semantic model were not independently extracted or audited; compare the live measure definitions in Power BI Desktop if reproducing this project.

## Filtering and report pages

- **Banking Overview:** four KPI cards, national credit/deposit and office trends, Year slicer. Historic line charts stay on 2015–2025.
- **State-wise Comparison:** top 10 state/UT deposits and credit, scatter plot, detail table, fixed 2025 takeaway text.
- **Sectoral Lending Analysis:** agricultural/industrial KPIs, historic trend chart, paired-sector split pie, top 10 rankings.

All high-level visuals use **₹ lakh crore** for financial balances; detailed state tables use **₹ crore**. Offices use counts and C-D ratios use percentages. Year slicers should be used at a single-year grain for stock balances.

## Geography caveat

The 2020 administrative/reporting change for Dadra & Nagar Haveli and Daman & Diu means raw before/after comparisons involving the affected territories are not geographically homogeneous. Source labels were standardised, but a like-for-like territorial time series was **not** constructed. No claims of growth for this affected territory spanning 2020 are made.
