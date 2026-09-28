# RetailPulse – E-Commerce Customer Intelligence

An end-to-end e-commerce analytics and customer intelligence project built using **Python, Machine Learning, RFM Analysis, and Power BI**.

RetailPulse transforms transactional retail data into business insights by combining data cleaning, exploratory analysis, customer segmentation, repurchase prediction, and interactive business intelligence dashboards.

---

## 📌 Project Overview

RetailPulse analyzes the **Online Retail** dataset and follows an end-to-end analytics workflow:

```text
Raw Retail Data
      ↓
Data Understanding & Cleaning
      ↓
Exploratory Data Analysis
      ↓
RFM Customer Segmentation
      ↓
Repurchase Prediction
      ↓
Customer Risk & Revenue-at-Risk Analysis
      ↓
Power BI Dashboard

The original dataset contains 541,909 transactions across 8 columns.

After the cleaning process, the transaction dataset contains 524,878 valid records.


---

🎯 Objectives

Clean and prepare raw e-commerce transaction data

Analyze sales and customer purchasing behavior

Calculate revenue and time-based business metrics

Segment customers using RFM Analysis

Build a customer repurchase prediction model

Estimate customer revenue at risk

Identify high-value and at-risk customers

Build an interactive Power BI analytics dashboard



---

🗂️ Dataset

The project uses the Online Retail transactional dataset.

Original Dataset

Rows: 541,909

Columns: 8


Main Columns

Column	Description

InvoiceNo	Transaction / invoice identifier
StockCode	Product identifier
Description	Product description
Quantity	Quantity purchased
InvoiceDate	Transaction date and time
UnitPrice	Unit price
CustomerID	Customer identifier
Country	Customer country


The raw dataset is intentionally not included in this public repository.


---

🔹 Phase 1 — Data Understanding & Cleaning

The first notebook performs the initial data understanding and preparation.

Data Cleaning

The workflow includes:

Duplicate removal

Missing product-description handling

Invoice number conversion

Cancelled invoice removal

Positive quantity filtering

Positive unit-price filtering


Revenue Calculation

Revenue is calculated as:

Revenue = Quantity × UnitPrice

Feature Engineering

Additional time-based features are created:

Year

Month

MonthName

YearMonth

DayOfWeek

Hour


After cleaning:

Original rows: 541,909
Clean rows:    524,878
Rows removed:  17,031


---

🔹 Phase 2 — Exploratory Data Analysis

The project analyzes:

Monthly revenue

Order volume

Product performance

Country-level sales

Customer revenue

Quantity trends

Customer purchasing behavior


These analyses form the foundation for the customer intelligence stage.


---

🔹 Phase 3 — RFM Customer Segmentation

Customer-level behavior is analyzed using RFM Analysis.

RFM Metrics

Metric	Meaning

Recency	How recently the customer purchased
Frequency	Number of unique orders
Monetary	Total customer revenue


Additional RFM scores are calculated:

R_Score

F_Score

M_Score

RFM_Score


Customers are grouped into behavioral segments such as:

Champions

Loyal Customers

Potential Loyalists

At Risk

Lost Customers

New Customers


The resulting RFM dataset contains 4,338 customers.


---

🔹 Phase 4 — Repurchase Prediction

The project also builds a machine learning workflow to predict customer repurchase behavior.

Historical customer features include:

Recency
Frequency
Monetary
AvgOrderValue
ProductDiversity

A time-based split is used to create historical customer features and future purchase behavior.

Prediction Model

Logistic Regression is used to generate customer repurchase probabilities.

The model produces:

Repurchase_Probability

Predicted_Repurchase


The project also uses Random Forest for feature importance analysis.

Feature Importance

The analysis identifies the following features as important for prediction:

1. Monetary


2. Recency


3. AvgOrderValue


4. ProductDiversity


5. Frequency




---

📊 Repurchase Probability Segmentation

Customers are grouped based on predicted repurchase probability:

Probability	Segment

≥ 0.75	High Probability
0.50 – 0.74	Medium Probability
< 0.50	Low Probability


The resulting analysis contains:

Segment	Customers

High Probability	614
Medium Probability	914
Low Probability	2,088



---

💰 Revenue-at-Risk Analysis

For customers with low repurchase probability, the project estimates potential revenue at risk.

The analysis identified:

Low-probability customers: 2,088

Historical revenue:
£1,061,320.43

Estimated revenue at risk:
£713,926.92

This helps connect machine learning predictions with a business-oriented financial metric.


---

📊 Power BI Dashboard

The analytical outputs are used to build an interactive RetailPulse Power BI Dashboard.

Dashboard Pages

1. Executive Overview

Provides a high-level view of:

Total Revenue

Total Orders

Total Quantity

Unique Customers

Average Order

Revenue Trend

Revenue by Country

Top Products

Orders vs Quantity

Revenue Distribution by Country


2. Customer Intelligence

Focuses on customer behavior and RFM analysis:

Total Customers

Champions

Potential Loyalists

At Risk

Lost Customers

RFM Segment Distribution

RFM Segment Revenue Contribution

Average RFM Scores by Segment

Recency vs Monetary

Top Customers by Revenue


3. Repurchase Intelligence

Focuses on machine-learning-based customer repurchase prediction:

Predicted Customers

Repurchase Probability

Probability Segments

Customers at Risk

Revenue at Risk


4. Product & Geography

Provides deeper product and geographic analysis.


---

🛠️ Tech Stack

Programming & Analysis

Python

Pandas

NumPy

Matplotlib


Machine Learning

Scikit-learn

Logistic Regression

Random Forest


Business Intelligence

Microsoft Power BI


Development Environment

Google Colab



---

📁 Repository Structure

RetailPulse-Ecommerce-Customer-Intelligence/
│
├── notebooks/
│   ├── 01_data_understanding_cleaning.ipynb
│   └── 02_eda_rfm_ml.ipynb
│
├── data/
│   └── README.md
│
├── powerbi/
│   ├── RetailPulse.pbix
│   └── screenshots/
│       ├── executive-overview.png
│       ├── customer-intelligence.png
│       ├── repurchase-intelligence.png
│       └── product-geography.png
│
├── docs/
│   └── project-workflow.png
│
├── README.md
└── .gitignore


---

📤 Generated Analytical Datasets

The notebooks generate the following datasets for downstream analysis and Power BI:

retail_clean.csv
customer_rfm.csv
customer_predictions.csv

These contain the cleaned transaction data, customer RFM metrics, and repurchase prediction results respectively.


---

🔍 Key Business Questions

RetailPulse is designed to answer questions such as:

How is overall revenue changing over time?

Which products generate the most revenue?

Which countries contribute the most revenue?

Who are the highest-value customers?

Which customers are Champions?

Which customers are at risk of becoming inactive?

Which customers have a low probability of repurchase?

How much historical revenue is associated with low-probability customers?

Which customer features contribute to repurchase prediction?



---

🚀 Project Outcome

RetailPulse combines descriptive analytics, customer segmentation, predictive modeling, and business intelligence into a single end-to-end workflow.

The project demonstrates how raw transactional data can be transformed into:

Data → Insights → Customer Segments → Predictions → Business Decisions


---

👩‍💻 Author

Anish Fathima N

B.Tech — Artificial Intelligence & Data Science


---

⭐ If you find this project useful, feel free to explore the notebooks and Power BI dashboard.

### One important correction

I deliberately **didn't claim that the model is “highly accurate”** or make up an accuracy figure. Your notebook actually evaluates the models, so we can add the exact evaluation metrics later if you want the README to include a proper **Model Performance** section. 0

Also, your notebooks actually export the three Power BI datasets at the end of the workflow, so that section is directly supported by your work. 1

**For now:** create/edit the repository's `README.md` and paste this content. Don't create the `.gitignore` yet—we'll do that next so we can make sure the large/raw data files don't accidentally get committed.
