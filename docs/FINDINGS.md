# Findings supported by the final dashboard

All figures below refer to **end-March** observations. Financial amounts are nominal stocks, not flows. Values are rounded in the report. The final screenshots are stored under `assets/screenshots/`.

| Metric | 2015 | 2025 | Approx. growth |
|---|---:|---:|---:|
| Deposits | ₹89.22 L Cr | ₹234.52 L Cr | 162.9% |
| Bank credit | ₹68.78 L Cr | ₹187.87 L Cr | 173.1% |
| Bank offices | 130,482 | 167,806 | 28.6% |
| Agricultural credit | ₹9.04 L Cr | ₹24.20 L Cr | 167.7% |
| Industrial credit | ₹28.36 L Cr | ₹42.86 L Cr | 51.1% |

Here `L Cr` means **lakh crore**. Endpoint growth is calculated as `(2025 / 2015 − 1) × 100`; using rounded values may change the last decimal. Detailed earlier screenshots gave 2015 deposits ₹8,922,111 crore and credit ₹6,878,473 crore; 2025 table totals are ₹23,451,838 crore and ₹18,786,866 crore.

## Finding 1 — Credit grew a little faster than deposits

Bank credit rose approximately 173.1% versus deposit growth of approximately 162.9%. This is nominal balance growth, not lending disbursements or inflation-adjusted growth.

## Finding 2 — Bank office growth was slower

Reported bank offices grew about 28.6%, from 130,482 to 167,806. The number of offices increased much less rapidly than reported credit or deposit balances. This **does not by itself prove** digital adoption, improved efficiency, or better banking access.

## Finding 3 — Calculated national C-D ratio edged upward

The calculated credit-to-deposit ratio increased from approximately 77.1% in 2015 to 80.1% in 2025, about **3.0 percentage points**. This ratio uses the two selected banking amount measures; it should not be described as the RBI's separately published place-of-sanction or place-of-utilisation ratio.

## Finding 4 — Concentrated large markets

Maharashtra ranks highest in the 2025 state/UT comparison for bank deposits and overall bank credit. The dashboard provides top-ten rankings, but concentration should only be stated quantitatively if a Top 5 or Top 10 share has been explicitly calculated.

## Finding 5 — C-D ratios vary across states/UTs

Andhra Pradesh's calculated 2025 C-D ratio appears as approximately 157.2% in the state detail table, compared with the calculated national 80.1%. A ratio above 100% is not automatically an error and does not prove any causal explanation of local deposit or credit movement.

## Finding 6 — Different sectoral growth patterns

Agricultural credit rose from about ₹9.04 to ₹24.20 lakh crore (about 167.7%), while industrial credit rose from about ₹28.36 to ₹42.86 lakh crore (about 51.1%). Industrial credit remains larger in reported amount at end-March 2025.

## Finding 7 — Different sectoral state leaders

In 2025, Maharashtra ranks first in industrial credit (approximately ₹10.85 lakh crore); Tamil Nadu ranks first in agricultural credit (approximately ₹3.82 lakh crore).

## Two-sector share chart: correct interpretation

For 2025, among the **sum of agricultural and industrial credit only**, agriculture represents about 36.09% and industry 63.91%: 24.20 / (24.20 + 42.86) and 42.86 / (24.20 + 42.86). These are **not** shares of total bank credit.

## Validation status

These interpretations are supported by the values visible on the supplied final dashboards and the statically inspected `.pbix` report configuration. The raw RBI workbooks were **not** provided in the final upload, so all state-year entries and DAX expressions could not be independently recomputed from primary Excel data. See [Verification](VERIFICATION.md).
