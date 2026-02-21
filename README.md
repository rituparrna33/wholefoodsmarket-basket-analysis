# 🛒 Grocery Market Basket Analysis

Uncovering purchasing patterns from 11 months of real Whole Foods transaction data

## 📌 Project Overview

This project applies market basket analysis and exploratory spend analytics to 11 months of personal Whole Foods grocery transactions (April 2025 – February 2026). Using the Apriori algorithm, the analysis surfaces product association rules, identifies high-affinity item pairs, and reveals seasonal and behavioral spending patterns.
This is a real-world dataset — not a textbook example — which makes the findings both authentic and directly interpretable.

## 🗃️ Data Collection
How the Dataset Was Built

There is no public API or data export for Whole Foods transaction history. So this dataset was built from scratch using a custom data pipeline powered by Claude (Anthropic) and Amazon order history.
### Step 1 — Export Amazon Order History
Whole Foods purchases made through Amazon Prime are logged in your Amazon account order history. Orders were exported by navigating to:
Amazon → Returns & Orders → [Whole Foods orders] → Download order history
This produced a raw order history file containing transaction dates, item descriptions, quantities, and prices — but in an unstructured, non-analytical format.
### Step 2 — Parse and Structure with Claude
The raw export was processed using Claude as an AI-assisted data transformation layer:
Extracted individual line items, product names, quantities, and prices from unstructured order text
Inferred and assigned product categories (e.g., Produce, Meat, Dairy, Snacks) based on product names
Standardized inconsistent product naming conventions across 14 months of orders
Flagged and structured promotion/discount fields where applicable
Output a clean, analysis-ready CSV: whole_foods_transactions.csv

### Step 3 — Load into Python for Analysis
The structured CSV was saved to Google Drive and loaded directly into a Google Colab notebook for all downstream analysis.
Why this matters: Manual grocery receipt tracking is tedious and error-prone. This pipeline demonstrates how LLMs can accelerate personal data projects by handling the messy, unstructured extraction layer — turning a raw export into a queryable dataset in minutes rather than hours.

## 🎯 Business Questions Answered

What is the total spend and savings, and what are the average monthly spending trends?

What is the overall average order value, and how does it fluctuate monthly?

Which product categories contribute most to total spending? 

Which products are purchased most often?

What are the strongest product pairings and association rules?

What is the average number of items and categories per basket?


## 📊 Key Findings
## 💵 Overall Spending Patterns

What is the total spend and savings, and what are the average monthly spending trends?

Metric Value 

Total Spend $1,871.96 

Total Savings $94.00

Overall Savings Rate 4.8%

Average Monthly Spend $208.00

Spending Trend 📈 Generally increasing

## 💳 Average Order Value (AOV)

What is the overall average order value, and how does it fluctuate monthly?

Overall AOV: $89.14

Monthly AOV showed notable fluctuations — lower in April, May, and December 2025 and peaking in July 2025 and February 2026


## 📦 Top Categories by Spend

Which product categories contribute most to total spending?

Rank Category Total Spend 

1 Meat $356.69 

2 Seafood $317.85

3 Produce $282.82 

4 Frozen Foods $167.89 

5 Bakery $162.62 

## 🔁 Frequent Products

Which products are purchased most often?

31 products were bought in 3 or more transactions, representing 44.4% of all purchases

Top repeat item: Hot Guacamole Dip — appearing in 14 transactions


## 🤝 Product Associations

What are the strongest product pairings and association rules?

Strongest product pairing: 365 Large White Eggs + Hot Guacamole Dip — bought together in 7 transactions

Strongest association rule had 10.50x lift and 100% confidence:

IF (Pork Chorizo Sausage, Watermelon Chunks, Hot Guacamole Dip)
THEN (Cedar's Chickpea Salad, Mitica Walnut Date Cake Cubes, Cantaloupe Chunks)

## 🧺 Basket Composition

What is the average number of items and categories per basket?

MetricValue Avg Items per Basket 6.6 items

Avg Categories per Basket 4.5 categories

Customers consistently shop across 4–5 categories per trip, indicating diverse, multi-department shopping lists.

## 🗓️ Seasonal Spending Habits
Peaks in July 2025 and February 2026, with dips in April, May, and December 2025, suggest seasonal purchasing behaviors — creating opportunities for targeted campaigns timed around these patterns.

🏪 Cross-Merchandising Potential
Strong pairings like Hot Guacamole Dip + 365 Large White Eggs and complex multi-item rules highlight clear opportunities for bundle offers, meal kit promotions, and in-store product placement strategy.

🥩 High-Value Categories
Meat, Seafood, and Produce account for over 50% of total spend combined. These categories are the highest-leverage areas for promotions and quality-driven loyalty.

🏷️ Discount Effectiveness
The Health/Supplements category had the highest savings rate at 22.0%, compared to an overall rate of 4.8% — suggesting promotions in this category are especially influential on purchase decisions.

🛒 Basket Behavior
With an average of 6–7 items across 4–5 categories per trip, shoppers are running multi-department errands rather than single-category runs — making cross-category recommendations highly actionable.


## 🛠️ Tech Stack
Tool Purpose

pandas / numpyData wrangling, time-series aggregation

matplotlib / seabornTrend lines, heatmaps, distribution

smlxtend Apriori algorithm & association rule mining

TransactionEncoderOne-hot encoding of product baskets

Google Colab Development environment

Google DriveSecure data source connection


### 🔬 Methodology
Step 1 — Data Preprocessing

Parsed date fields and extracted time features: Year, Month, Quarter, Day of Week, Week of Year

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
Metric Definition Support How often the rule appears across all transactions

ConfidenceP(buying Y | bought X)

LiftStrength of association above random chance — lift > 1 = positive association

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



If you have questions or feedback send me a message through [LinkedIn](https://www.linkedin.com/in/rituparna-das13/) . Enjoy! 
