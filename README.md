# RetailPulse – E-Commerce Customer Intelligence

An end-to-end e-commerce analytics and customer intelligence project built using **Python, Machine Learning, RFM Analysis, and Power BI**.

RetailPulse transforms transactional retail data into business insights by combining data cleaning, exploratory analysis, customer segmentation, repurchase prediction, revenue-at-risk analysis, and interactive business intelligence dashboards.

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
````

The original dataset contains **541,909 transactions across 8 columns**.

After the cleaning process, the transaction dataset contains **524,878 valid records**.

---

## 🎯 Objectives

RetailPulse was developed to:

* Clean and prepare raw e-commerce transaction data
* Analyze sales and customer purchasing behavior
* Calculate revenue and time-based business metrics
* Identify product and geographic sales patterns
* Segment customers using RFM Analysis
* Build a customer repurchase prediction model
* Estimate customer revenue at risk
* Identify high-value and at-risk customer groups
* Build an interactive Power BI analytics dashboard
* Connect machine learning outputs with business intelligence

---

# 🗂️ Dataset

The project uses the **Online Retail transactional dataset**.

## Original Dataset

| Attribute |   Value |
| --------- | ------: |
| Rows      | 541,909 |
| Columns   |       8 |

### Main Columns

| Column        | Description                      |
| ------------- | -------------------------------- |
| `InvoiceNo`   | Transaction / invoice identifier |
| `StockCode`   | Product identifier               |
| `Description` | Product description              |
| `Quantity`    | Quantity purchased               |
| `InvoiceDate` | Transaction date and time        |
| `UnitPrice`   | Unit price                       |
| `CustomerID`  | Customer identifier              |
| `Country`     | Customer country                 |

The raw dataset is intentionally **not included** in this public repository.

For detailed dataset documentation, preprocessing, feature engineering, RFM data, and analytical dataset information, see:

```text
data/README.md
```

---

# 🔹 Phase 1 — Data Understanding & Cleaning

The first notebook performs the initial data understanding, quality assessment, preprocessing, and feature engineering.

### Notebook

```text
notebooks/01_data_understanding_cleaning.ipynb
```

## Data Cleaning

The workflow includes:

* Duplicate removal
* Missing product-description handling
* Invoice number conversion
* Cancelled invoice removal
* Positive quantity filtering
* Positive unit-price filtering
* Revenue calculation
* Date feature engineering

### Cleaning Workflow

```text
Raw Dataset
     ↓
Data Inspection
     ↓
Duplicate Removal
     ↓
Missing Description Handling
     ↓
Invoice Number Conversion
     ↓
Cancelled Invoice Removal
     ↓
Quantity Filtering
     ↓
Unit Price Filtering
     ↓
Revenue Calculation
     ↓
Date Feature Engineering
```

---

## Revenue Calculation

Revenue is calculated using:

```text
Revenue = Quantity × UnitPrice
```

This transaction-level revenue metric is used throughout the project for sales and customer analysis.

---

## Feature Engineering

Additional time-based features are created from `InvoiceDate`:

* `Year`
* `Month`
* `MonthName`
* `YearMonth`
* `DayOfWeek`
* `Hour`

These features support time-based business analysis and Power BI visualizations.

---

## Cleaning Results

| Metric        |   Value |
| ------------- | ------: |
| Original Rows | 541,909 |
| Cleaned Rows  | 524,878 |
| Rows Removed  |  17,031 |

---

# 🔹 Phase 2 — Exploratory Data Analysis

The second stage focuses on understanding overall sales and customer purchasing behavior.

### Notebook

```text
notebooks/02_eda_rfm_ml.ipynb
```

The project analyzes:

* Monthly revenue
* Order volume
* Product performance
* Country-level sales
* Customer revenue
* Quantity trends
* Customer purchasing behavior
* Transaction patterns
* Product diversity

These analyses form the foundation for customer segmentation and predictive modeling.

---

# 🔹 Phase 3 — RFM Customer Segmentation

Customer-level behavior is analyzed using **RFM Analysis**.

RFM represents:

* **Recency**
* **Frequency**
* **Monetary**

## RFM Metrics

| Metric    | Meaning                             |
| --------- | ----------------------------------- |
| Recency   | How recently the customer purchased |
| Frequency | Number of unique orders             |
| Monetary  | Total customer revenue              |

Additional RFM scores are calculated:

* `R_Score`
* `F_Score`
* `M_Score`
* `RFM_Score`

---

## Customer Segments

Customers are grouped into behavioral segments:

* Champions
* Loyal Customers
* Potential Loyalists
* At Risk
* Lost Customers
* New Customers

The resulting RFM dataset contains **4,338 customers**.

### Customer Segment Distribution

| Segment             | Customers |
| ------------------- | --------: |
| Lost Customers      |     1,065 |
| Potential Loyalists |     1,041 |
| Champions           |       957 |
| Loyal Customers     |       503 |
| At Risk             |       453 |
| New Customers       |       319 |
| **Total**           | **4,338** |

---

## RFM Segment Revenue

The historical revenue contribution of the customer segments is:

| Segment             |        Revenue |
| ------------------- | -------------: |
| Champions           | £5,791,640.740 |
| Loyal Customers     |   £895,651.561 |
| Potential Loyalists |   £796,897.150 |
| At Risk             |   £739,477.551 |
| Lost Customers      |   £518,322.152 |
| New Customers       |   £145,219.740 |

---

# 🔹 Phase 4 — Repurchase Prediction

The project also builds a machine learning workflow to predict customer repurchase behavior.

Historical customer features include:

* `Recency`
* `Frequency`
* `Monetary`
* `AvgOrderValue`
* `ProductDiversity`

A time-based approach is used to create historical customer features and future purchase behavior.

---

## Prediction Model

**Logistic Regression** is used to generate customer repurchase probabilities.

The model produces:

```text
Repurchase_Probability
Predicted_Repurchase
```

The project also uses **Random Forest** for feature importance analysis.

---

## Feature Importance

The analysis identifies the following features and importance values:

| Rank | Feature          | Importance |
| ---: | ---------------- | ---------: |
|    1 | Monetary         |   0.250532 |
|    2 | Recency          |   0.215915 |
|    3 | AvgOrderValue    |   0.210491 |
|    4 | ProductDiversity |   0.200872 |
|    5 | Frequency        |   0.122190 |

---

# 📊 Repurchase Probability Segmentation

Customers are grouped based on predicted repurchase probability.

| Probability   | Segment            |
| ------------- | ------------------ |
| `≥ 0.75`      | High Probability   |
| `0.50 – 0.74` | Medium Probability |
| `< 0.50`      | Low Probability    |

### Customer Distribution

| Segment            | Customers |
| ------------------ | --------: |
| High Probability   |       614 |
| Medium Probability |       914 |
| Low Probability    |     2,088 |
| **Total**          | **3,616** |

---

## Repurchase Probability Analysis

The probability groups show different historical customer behavior:

| Segment            | Average Probability | Average Recency |
| ------------------ | ------------------: | --------------: |
| High Probability   |                0.89 |      24.19 days |
| Medium Probability |                0.61 |      45.63 days |
| Low Probability    |                0.36 |     132.06 days |

### Actual Repurchase Rates

| Segment            | Actual Repurchase Rate |
| ------------------ | ---------------------: |
| High Probability   |                 88.93% |
| Medium Probability |                 62.25% |
| Low Probability    |                 34.63% |

---

# 💰 Revenue-at-Risk Analysis

For customers with low repurchase probability, the project estimates potential revenue at risk.

The calculation is:

```text
Revenue At Risk =
Monetary × (1 − Repurchase Probability)
```

The analysis identified:

| Metric                    |         Value |
| ------------------------- | ------------: |
| Low-Probability Customers |         2,088 |
| Historical Revenue        | £1,061,320.43 |
| Estimated Revenue at Risk |   £713,926.92 |

This connects machine learning predictions with a business-oriented financial metric.

---

# 📊 Power BI Dashboard

The analytical outputs are used to build an interactive **RetailPulse Power BI Dashboard**.

The dashboard contains four analytical pages.

---

## 1. Executive Overview

Provides a high-level view of overall e-commerce performance.

### KPIs

* Total Revenue
* Total Orders
* Total Quantity
* Unique Customers
* Average Order

### Visualizations

* Revenue Trend
* Revenue by Country
* Top 10 Products by Revenue
* Orders vs Quantity
* Revenue Distribution by Country

---

## 2. Customer Intelligence

Focuses on customer behavior and RFM analysis.

### KPIs

* Total Customers
* Champions
* Potential Loyalists
* At Risk
* Lost Customers

### Visualizations

* RFM Segment Distribution
* RFM Segment Revenue Contribution
* Average RFM Scores by Segment
* Recency vs Monetary
* Top 8 Customers by Revenue

---

## 3. Repurchase Intelligence

Focuses on machine-learning-based customer repurchase prediction.

### KPIs

* Predicted Customers
* High Probability
* Medium Probability
* Low Probability
* Estimated Revenue at Risk

### Visualizations

* Repurchase Probability Distribution
* Customers by Probability Segment
* Revenue at Risk by Probability Segment
* Predicted vs Actual Repurchase Rate
* AI-Driven Customer Insights

---

## 4. Product & Geography

Provides deeper product, market, and customer ordering behavior analysis.

### KPIs

* Total Products
* Countries Served
* Total Units Sold
* Average Unit Price
* Units per Order

### Visualizations

* Top 10 Products by Quantity Sold
* Monthly Units Sold by Market
* Orders by Day of Week
* Order Activity by Hour

---

# 🖼️ Dashboard Preview

### Executive Overview

![Executive Overview](powerbi/screenshots/executive-overview.png)

### Customer Intelligence

![Customer Intelligence](powerbi/screenshots/customer-intelligence.png)

### Repurchase Intelligence

![Repurchase Intelligence](powerbi/screenshots/repurchase-intelligence.png)

### Product & Geography

![Product & Geography](powerbi/screenshots/product-geography.png)

---

# 🛠️ Tech Stack

## Programming & Analysis

* Python
* Pandas
* NumPy
* Matplotlib

## Machine Learning

* Scikit-learn
* Logistic Regression
* Random Forest

## Business Intelligence

* Microsoft Power BI

## Development Environment

* Google Colab

---

# 📁 Repository Structure

```text
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
```

---

# 📤 Generated Analytical Datasets

The notebooks generate the following datasets for downstream analysis and Power BI:

### `retail_clean.csv`

Contains the cleaned transaction-level dataset with engineered revenue and time-based features.

### `customer_rfm.csv`

Contains customer-level RFM metrics, RFM scores, and customer segments.

### `customer_predictions.csv`

Contains customer-level repurchase predictions, probability segments, and revenue-at-risk calculations.

These analytical datasets are generated as part of the project workflow and are used for downstream analysis and Power BI development.

---

# 🔍 Key Business Questions

RetailPulse is designed to answer questions such as:

* How is overall revenue changing over time?
* Which products generate the most revenue?
* Which countries contribute the most revenue?
* Who are the highest-value customers?
* Which customers are Champions?
* Which customers are Loyal Customers?
* Which customers are Potential Loyalists?
* Which customers are at risk of becoming inactive?
* Which customers have a low probability of repurchase?
* How many customers fall into each repurchase probability segment?
* How much historical revenue is associated with low-probability customers?
* How much revenue is estimated to be at risk?
* Which customer features contribute to repurchase prediction?
* When are customers most active during the week and day?

---

# 🚀 Project Outcome

RetailPulse combines:

* Descriptive analytics
* Exploratory data analysis
* Customer segmentation
* Predictive modeling
* Revenue-at-risk analysis
* Business intelligence

into a single end-to-end analytics workflow.

The project demonstrates how raw transactional data can be transformed into:

```text
Data
  ↓
Cleaning
  ↓
Analysis
  ↓
Customer Segments
  ↓
Predictions
  ↓
Business Insights
  ↓
Interactive Dashboard
```

---

# 👩‍💻 Author

**Anish Fathima N**

B.Tech — Artificial Intelligence & Data Science

---

## ⭐ Project

If you find this project useful, feel free to explore the notebooks, analytical workflow, and Power BI dashboard.

````

Otherwise GitHub will show broken images.
