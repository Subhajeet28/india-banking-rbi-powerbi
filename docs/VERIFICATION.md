# Verification and limitations

## What was actually checked

- The submitted Power BI file is a readable ZIP-based `.pbix` package and passed the ZIP CRC/integrity test.
- Its report-definition metadata contains **exactly three** pages named `Banking Overview`, `State-wise Comparison` and `Sectoral Lending Analysis`.
- The report has visuals bound to the expected deposit, credit, bank-office, agricultural-credit and industrial-credit measures.
- Both Page 2 and Page 3 ranking bar charts have Top-N definitions with **Top 10**; the ranking measures reference the correct deposits/credit/sector metrics rather than the previously incorrect `First State` field.
- The three supplied PNG screenshots load successfully, show the expected pages and have Year **2025** selected.
- The end-March 2025 deposit and credit national amounts shown in the state table (₹23,451,838 crore and ₹18,786,866 crore) convert to approximately ₹234.52 and ₹187.87 lakh crore. The calculated C-D ratio is approximately 80.1%.
- Independent context check: the Government of India's *Economic Survey 2025–26* statistical appendix reports the same March 2025 deposit figure and a credit figure differing by just ₹1 crore, consistent with rounding.

## What could not be verified automatically

- Opening/refreshing the `.pbix` in **Power BI Desktop**; static inspection is not a functional Desktop opening test.
- Every row and numeric value against the original RBI Excel tables: the five original workbooks were not attached with the final package.
- Exact DAX expressions and Power Query M steps within the compressed model.
- All missing value and boundary-change handling beyond the checks described during development.
- Whether a recipient's computer has the original local workbook paths needed to refresh.

## Limitations worth disclosing

1. **Stock vs flow:** Credit, deposits and sectoral credit are end-March outstanding balances, not year-long loan disbursements. Multi-year sums are not meaningful annual headline amounts.
2. **Dadra & Nagar Haveli / Daman & Diu:** From 2020 the first label incorporates both; growth spanning the geography break is not like-for-like without adjustment. Asterisk stripping standardises labels only, not the underlying border.
3. **Missing observations:** Original RBI dashes can mean nil/not applicable/negligible. Retaining them as null avoids inventing zero amounts; nulls should not silently drop state-year keys.
4. **Ratios:** The calculated C-D ratio is `credit / deposits`. RBI's official ratios distinguished by sanction and utilisation geography are separate data series and should not be mislabelled.
5. **Pie chart:** Agriculture/industry share is a share of their **combined two-sector amount**, not all bank credit.
6. **Unadjusted figures:** Growth is nominal and cannot, by itself, establish real growth or cause.
7. **Aggregations:** The RBI all-India and region totals were excluded from state-level sums to avoid double counting. Published totals may differ from state sums because of rounding or source coverage.

## Recommended final reviewer check in Desktop

Open the `.pbix`, confirm all three pages render, each Year slicer defaults to 2025, line charts retain 2015–2025, Top 10 ranking filters are correct, state table totals agree with source for 2025, and no query errors appear upon refresh (after updating source paths if necessary).
