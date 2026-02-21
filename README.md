# 🛒 Grocery Market Basket Analysis

Uncovering purchasing patterns from 14 months of real Whole Foods transaction data

## 📌 Project Overview

This project applies market basket analysis and exploratory spend analytics to 14 months of personal Whole Foods grocery transactions (January 2025 – February 2026). Using the Apriori algorithm, the analysis surfaces product association rules, identifies high-affinity item pairs, and reveals seasonal and behavioral spending patterns.

This is a real-world dataset — not a textbook example — which makes the findings both authentic and directly interpretable.


## 🎯 Business Questions Answered

Which product combinations are consistently bought together?
How does monthly spending vary across seasons?
What categories drive the most spend, and where are savings being captured?
How does basket size correlate with order value?
Are there high-lift association rules that could inform cross-promotion or inventory decisions?


## 📊 Key Findings
💵 Spending Patterns
MetricValueData RangeJan 2025 – Feb 2026Average Order Value (AOV)$89.14AOV Range$57.14 (Apr 2025) → $108.18 (Jul 2025)Data CoverageAll 14 months — no gaps in the timeline
## 🧺 Market Basket Insights

Strongest association rules returned a lift of 10.5 with 100% confidence — certain product combinations appeared together in every observed transaction containing one of the items.
Top co-occurring pairs included seasonal produce (e.g., Cantaloupe Chunks, Watermelon Chunks) alongside packaged and protein items, suggesting meal-occasion driven shopping rather than pantry stocking.
365 Organic Roasted Seaweed + Salmon Atlantic Fillet appeared together at high frequency — consistent with weeknight dinner basket behavior.

## 📅 Seasonal Trends

Mid-year spending peak observed in July 2025 and again in February 2026
A notable dip in April–May 2025 reflects lighter basket sizes at the start of the observation window
All 14 months had recorded transactions — complete temporal coverage confirmed


## 🛠️ Tech Stack
ToolPurposepandas / numpyData wrangling, time-series aggregationmatplotlib / seabornTrend lines, heatmaps, distributionsmlxtendApriori algorithm & association rule miningTransactionEncoderOne-hot encoding of product basketsGoogle ColabDevelopment environmentGoogle DriveSecure data source connection

## 🗂️ Project Structure
grocery-market-basket-analysis/
│
├── market_Basket_Analysis_Whole_Foods_Data.ipynb   # Main analysis notebook
├── README.md                                        # Project documentation
└── (data not included — personal transaction data)

Note: Raw transaction data is not included in this repository as it contains personal financial records.


### 🔬 Methodology
Step 1 — Data Preprocessing

Parsed date fields and extracted time features: Year, Month, Quarter, Day of Week, Week of Year
Built a complete date spine to validate data continuity across the full 14-month range
Confirmed zero missing months in the transaction timeline

### Step 2 — Spend Analysis

Aggregated spend at transaction, category, and monthly levels
Computed category-level savings rates from promotion fields
Built a frequency vs. revenue bubble chart to identify high-volume, high-value categories
Analyzed AOV distribution (mean vs. median) to assess skewness

### Step 3 — Market Basket Analysis

Filtered to frequent products (appearing in 3+ transactions) to reduce noise
Applied TransactionEncoder for one-hot encoding of transaction-product pairs
Ran the Apriori algorithm with a dynamic minimum support threshold calibrated to dataset size
Generated association rules using lift as the primary metric (threshold ≥ 1.0)
Filtered for high-confidence rules (confidence > 70%)
Built an independent product co-occurrence matrix to validate item-pair frequency

### Step 4 — Rule Evaluation Metrics
MetricDefinitionSupportHow often the rule appears across all transactionsConfidenceP(buying Y | bought X)LiftStrength of association above random chance — lift > 1 = positive association

### 📈 Visualizations Included

Monthly spend trend with annotated data labels
Category-level spend breakdown — bar chart, pie chart, bubble chart, and savings rate
Average Order Value over time with mean reference line
Items-per-order trend over time
Order value distribution — histogram with mean/median markers
Basket size vs. order value scatter with correlation annotation
Top 5 category spend growth over time (multi-line chart)


### 💡 Real-World Implications
Although this is a personal dataset, the analytical approach maps directly to retail and CPG analytics use cases:

Product placement — High-lift rules guide cross-merchandising strategy
Bundle promotions — Confidence ≥ 70% pairs are strong bundle candidates
Demand forecasting — Seasonal AOV patterns inform inventory planning
Customer segmentation — Basket composition can distinguish shopping occasions (quick run vs. full weekly shop)
