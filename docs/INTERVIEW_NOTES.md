# Interview explanation (approximately 90 seconds)

> I analysed RBI state-wise scheduled commercial bank data from end-March 2015 to 2025 in Power BI. The report has three pages covering national banking growth, state-wise comparisons and agricultural versus industrial credit. I used Power Query to clean the RBI Excel tables: I removed summary rows that would double-count state values, unpivoted annual columns, preserved missing values as nulls, standardised state names and merged five measures using State and Year. I checked that the final table kept the expected State–Year grain. In DAX I created aggregations, lakh-crore display measures and a calculated credit-to-deposit ratio. A key result was that bank credit grew slightly faster than deposits over the decade, while bank-office counts grew much more slowly. Maharashtra leads the 2025 deposit, total-credit and industrial-credit rankings, whereas Tamil Nadu leads agricultural credit. I also documented a territorial reporting change and kept the official RBI credit-deposit ratios separate from my calculated one. The dashboard is descriptive—it does not claim to prove causes or outcomes.

## Questions to practise

**Why choose this dataset?** Official RBI data, relevant to banking and suitable for regional and time-series comparisons.

**Why unpivot the years?** It converts eleven year columns into a Year field so visuals can filter and aggregate by State–Year.

**Why use `null` instead of zero?** Some original values are unavailable or not applicable; replacing them with zero would imply an observation that the source may not support.

**Why check State–Year keys before merging?** Duplicate keys can multiply financial amounts in joins.

**Why use a calculated C-D ratio?** A straightforward credit/deposit balance comparison; it must not be mislabelled as an RBI place-of-sanction or place-of-utilisation ratio.

**Why avoid adding balances across years?** These are stock values measured at end-March, so multi-year sums aren't a meaningful year-specific total.

**What would you improve in a second iteration?** More systematic boundary harmonisation, a documented refreshable source pipeline, and clearly defined weighted/sourced comparisons with the two official C-D ratio tables.
