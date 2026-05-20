# Facebook-Ad-Campaign-Performance-Analysis

## 📌 Project Overview
This project focuses on the comprehensive analysis of Facebook advertising campaigns using Python. The primary goal is to evaluate the performance of 11 different advertising strategies, identify key factors driving revenue (Total Value), analyze seasonality, and discover optimization opportunities for marketing budgets.

* **Dataset:** Contains 1,494 records of daily ad performance data across 10 key marketing metrics (`ad_date`, `campaign_name`, `total_spend`, `total_impressions`, `total_clicks`, `total_value`, `cpc`, `cpm`, `ctr`, `romi`).

---

## 🛠️ Tech Stack & Libraries
* **Environment:** Google Colab / Jupyter Notebook
* **Data Manipulation:** `pandas`, `numpy`
* **Data Visualization & Statistics:** `matplotlib`, `seaborn`

---

## 📊 Core Analytical Steps

### 1. Exploratory Data Analysis (EDA) & Data Profiles
* Checked data types and shapes using `df.info()`.
* Performed initial statistical summary via `df.describe(include='all')` to understand metric distributions.

### 2. Time-Series Analysis & Trend Smoothing
* Aggregated data by date (`df.groupby('ad_date')`) and recalculated overall daily **ROMI**.
* Filtered data to isolate **2021 performance trends**.
* Applied a **10-day Moving Average (`.rolling(10).mean()`)** to smooth out daily budget fluctuations. This revealed a massive peak in marketing spend between May and August 2021, while daily ROMI remained consistently profitable (mostly between 1.0 and 1.75).

### 3. Campaign-Level Performance Analysis
* Grouped metrics by `campaign_name` to isolate total spend, revenue, and efficiency.
* Visualized budget distribution using Seaborn barplots, identifying **Expansion** ($67.2k) and **Lookalike** ($63.6k) as the dominant campaigns by investment.

### 4. Advanced Statistical Distribution (Boxplots & Histograms)
* Built a `sns.boxplot` distribution of daily ROMI per campaign to evaluate performance stability.
* Analyzed overall ROMI density via `sns.displot`, showing a classic right-skewed distribution where most days hover around 1.0–1.5, with exceptional high-performing days reaching up to 2.5.

### 5. Correlation & Linear Regression Modeling
* Generated a correlation matrix heatmap (`sns.heatmap`) to identify underlying metric relationships.
* Visualized the strongest business driver using a linear regression plot (`sns.lmplot`).

---

## 💡 Key Insights & Business Recommendations

1. **The Spend-to-Revenue Driver:** There is an exceptionally strong positive correlation (**98%**) between `total_spend` and `total_value`. The regression model proves that increasing the budget directly scales total revenue.
2. **Volume vs. Efficiency:** While **Expansion** and **Lookalike** campaigns absorb over 60% of the total budget and generate the highest nominal revenue, they maintain a standard ROMI of **1.24–1.26**. 
3. **Hidden Gems (High ROI):** The **Trendy** campaign achieved the highest overall efficiency with an outstanding ROMI of **1.91**, followed by **Promos** at **1.76**. Notably, the boxplot proves that **Trendy** delivers stable performance, keeping 75% of its active days well above a 1.5 ROMI.
4. **The ROAS Paradox:** There is almost zero correlation (**-1%**) between `total_value` and `romi`. **Crucial analytical takeaway:** Scaling ad spend guarantees more revenue volume, but does *not* automatically guarantee higher investment efficiency.
5. **Cost vs. Engagement:** A negative correlation of **-21%** exists between Cost Per Click (`cpc`) and Click-Through Rate (`ctr`), proving that rising ad costs negatively impact audience engagement.

🎯 **Strategic Action Plan:** Scale the budget for **Trendy** and **Promos** campaigns, as they demonstrate elite ROI and strong day-to-day stability. Maintain **Expansion** and **Lookalike** as volume drivers, but optimize their ad creatives to combat rising CPC costs.

---

## 🚀 How to Run
1. Open the repository and view the static file `Facebook_Ad_Campaigns_Performance_Analysis.ipynb`.
