# India's Banking Landscape — Power BI Portfolio

**Banking growth, state-wise distribution and sectoral lending in India (2015–2025)**

A three-page interactive Power BI portfolio report built using tables from the Reserve Bank of India's *Handbook of Statistics on Indian States, 2024–25*. It explores scheduled commercial banks' deposits, credit, bank-office counts, and reported credit to agriculture and industry.

**Tools:** Power BI Desktop · Power Query · DAX  
**Geography:** Indian states and union territories  
**Time:** End-March observations, 2015–2025  
**Repository contents:** Actual Power BI project, final three dashboard screenshots, methods, and documented findings. This repository does not include raw RBI Excel files.

## Dashboard preview

### 1. Banking Overview

![Banking Overview — 2025 selected](assets/screenshots/01_banking_overview.png)

Tracks the national deposits, credit, calculated credit-to-deposit (C-D) ratio and bank-office network. KPI cards show the selected reporting year; historical charts show the 2015–2025 series.

### 2. State-wise Comparison

![State-wise Comparison — 2025](assets/screenshots/02_state_comparison.png)

Top 10 states/UTs by deposits and credit, state-level scatter plot, detailed comparison table and a fixed 2025 findings panel.

### 3. Sectoral Lending Analysis

![Sectoral Lending Analysis — 2025](assets/screenshots/03_sectoral_lending.png)

Agricultural and industrial credit balances, a historical trend chart, a two-sector combined-credit split, and the leading states/UTs for each sector.

## Selected results

| Indicator | End-March 2015 | End-March 2025 | Change |
|---|---:|---:|---:|
| Deposits | ₹89.22 lakh crore | ₹234.52 lakh crore | ≈ +162.9% |
| Bank credit | ₹68.78 lakh crore | ₹187.87 lakh crore | ≈ +173.1% |
| Bank offices | 130,482 | 167,806 | ≈ +28.6% |
| Calculated C-D ratio | 77.1% | 80.1% | ≈ +3.0 percentage points |
| Agricultural credit | ₹9.04 lakh crore | ₹24.20 lakh crore | ≈ +167.7% |
| Industrial credit | ₹28.36 lakh crore | ₹42.86 lakh crore | ≈ +51.1% |

**Highlights:** In 2025, Maharashtra has the largest reported deposits, bank credit and industrial credit in the state/UT comparison, while Tamil Nadu leads agricultural credit. State-level calculated C-D ratios show material variation; for instance Andhra Pradesh is approximately 157.2%.

*Evidence status:* These values and rankings are taken from the final report screenshots and earlier report checks. Growth percentages are calculated using displayed/previously checked figures; rounding affects precision. The 2025 national deposits and credit totals were also cross-checked against an official Government of India statistical appendix, with a possible ₹1 crore rounding difference for credit. A complete cell-by-cell RBI workbook audit was not possible because the original source workbooks were not included in the final uploads. See [findings](docs/FINDINGS.md) and [verification notes](docs/VERIFICATION.md).

## Data and scope

The project uses the following tables from the **2024–25 edition** of the RBI Handbook:

| RBI table | Data used | Measure unit |
|---|---|---|
| 152 | Offices of scheduled commercial banks | Count |
| 155 | Deposits by scheduled commercial banks | ₹ crore |
| 156 | Credit by scheduled commercial banks | ₹ crore |
| 157 | Credit to agriculture | ₹ crore |
| 158 | Credit to industry | ₹ crore |

RBI's official **place-of-sanction** and **place-of-utilisation** C-D ratio tables (153 and 154) were prepared during the wider project but are **not featured in the final three-page report**. The displayed calculated C-D ratio is credit divided by deposits; it is not presented as one of the separately published official ratios.

[Primary source: RBI — Handbook of Statistics on Indian States](https://www.rbi.org.in/Scripts/AnnualPublications.aspx?head=Handbook%20of%20Statistics%20on%20Indian%20States)

## Data preparation and modelling

- Imported 2015–2025 data from each workbook's `(ii)` sheet.
- Removed regional/national summary rows from state-level tables to avoid double counting.
- Promoted headers, unpivoted annual columns, standardised State and Year keys and preserved genuinely unavailable values as nulls.
- Checked repeated State–Year keys and merged five metric queries into `Fact_Banking` on **State + Year**.
- Retained **407 State–Year records** in the final 7-column fact table (37 geographic labels × 11 years, before geographic harmonisation). Some metric observations are null.
- Created measures for totals, credit-to-deposit ratio, and conversions from ₹ crore to ₹ lakh crore (1 lakh crore = 100,000 crore).

Details: [Methodology](docs/METHODOLOGY.md).

## Important analytical limitations

- All financial figures are **end-March balances / outstanding amounts**, not annual lending flows. Adding the same balance across years is not a meaningful national annual total.
- From 2020, RBI's Dadra & Nagar Haveli values include Daman & Diu. Their earlier independent reporting limits direct geographic growth comparisons; the report does not claim to have harmonised that boundary.
- A missing or not-applicable observation is not automatically zero.
- The combined agriculture/industry pie percentages use only **agricultural credit + industrial credit** as the denominator, **not total bank credit**.
- Trends describe observed associations and do not establish why lending, deposits or branch counts changed. Monetary growth is nominal, not inflation-adjusted.
- For a reproducible refresh, original RBI workbook paths may need updating in Power Query; original source workbooks are not shipped here.

See [Verification & limitations](docs/VERIFICATION.md).

## Open the report

1. Download [`dashboard/India_Banking_Portfolio_Final.pbix`](dashboard/India_Banking_Portfolio_Final.pbix).
2. Open it in a compatible Power BI Desktop installation.
3. Explore the three report tabs. Default screenshot captures use **2025**; KPI/ranking values reflect year selection.
4. If refreshing, download the appropriate original RBI Excel files and update the Power Query file-source paths as necessary.

> The uploaded `.pbix` was preserved byte-for-byte from the user's final submission. Its ZIP components, three report pages and essential visual bindings passed static inspection. Opening, rendering and refresh in Power BI Desktop must be checked in Power BI Desktop; they cannot be guaranteed by static inspection alone.

## Documentation

- [Methodology and measures](docs/METHODOLOGY.md)
- [Main findings and calculations](docs/FINDINGS.md)
- [Verification, caveats and limitations](docs/VERIFICATION.md)
- [Interview talking points](docs/INTERVIEW_NOTES.md)

**Project status:** Three analytical report pages completed. No fourth/“Thank You” page is claimed or included.
