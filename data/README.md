# Dataset Documentation

## Overview

RetailPulse uses the **Online Retail Dataset** for analyzing e-commerce transactions, customer behavior, product performance, and repurchase patterns.

The dataset contains transactional records from an online retail business, including information about invoices, products, quantities, prices, customers, dates, and countries.

The dataset is used as the foundation for the complete RetailPulse analytics workflow:

- Data cleaning and preprocessing
- Exploratory Data Analysis (EDA)
- Sales and revenue analysis
- Customer segmentation using RFM analysis
- Repurchase probability prediction
- Revenue-at-risk analysis
- Product performance analysis
- Geographic analysis
- Power BI dashboard development

---

## Dataset Source

**Dataset:** Online Retail Dataset

**Original File:** `Online Retail.xlsx`

The dataset contains transactional retail data with information related to customer purchases.

The original dataset includes the following columns:

| Column | Description |
|---|---|
| `InvoiceNo` | Unique invoice number associated with a transaction |
| `StockCode` | Unique product or item code |
| `Description` | Product description |
| `Quantity` | Number of units purchased |
| `InvoiceDate` | Date and time of the transaction |
| `UnitPrice` | Price per unit |
| `CustomerID` | Unique customer identifier |
| `Country` | Country where the customer is located |

---

## Original Dataset Statistics

The original dataset contains:

- **Rows:** 541,909
- **Columns:** 8

### Original Columns

```text
InvoiceNo
StockCode
Description
Quantity
InvoiceDate
UnitPrice
CustomerID
Country
````

---

## Data Cleaning

Before performing analysis, the dataset was cleaned and transformed using Python.

The cleaning process was performed to improve data quality and ensure that the dataset was suitable for analytics and machine learning.

### Cleaning Steps

The following preprocessing steps were applied:

1. Removed duplicate records.
2. Removed records with missing product descriptions.
3. Converted `InvoiceNo` into string format.
4. Removed cancelled transactions.
5. Removed transactions where `Quantity <= 0`.
6. Removed transactions where `UnitPrice <= 0`.
7. Created a new `Revenue` column.
8. Extracted date-related features from `InvoiceDate`.

---

## Cancelled Transactions

Transactions with invoice numbers beginning with `C` represent cancelled transactions.

These records were excluded from the cleaned dataset because the project focuses on completed sales transactions.

Example:

```text
InvoiceNo = C536379
```

Such transactions were removed during preprocessing.

---

## Revenue Calculation

A new `Revenue` feature was created to represent the total value of each transaction.

The calculation used was:

```text
Revenue = Quantity × UnitPrice
```

For example:

```text
Quantity = 10
UnitPrice = 5.00

Revenue = 10 × 5.00
Revenue = 50.00
```

This column is used extensively throughout the RetailPulse analysis.

---

## Date Feature Engineering

Additional time-based features were extracted from `InvoiceDate`.

The following features were created:

| Feature     | Description             |
| ----------- | ----------------------- |
| `Year`      | Year of the transaction |
| `Month`     | Numeric month           |
| `MonthName` | Name of the month       |
| `YearMonth` | Combined year and month |
| `DayOfWeek` | Day of the week         |
| `Hour`      | Hour of the transaction |

These features were used for:

* Monthly revenue analysis
* Order trend analysis
* Day-of-week analysis
* Hourly order activity analysis
* Power BI visualizations

---

## Cleaned Dataset

After preprocessing, the dataset contains approximately:

**524,878 transaction records**

The cleaned dataset is used for the main RetailPulse analysis and Power BI dashboard.

---

## Cleaned Dataset Features

The cleaned transactional dataset contains the original fields together with the engineered `Revenue` and date-related features.

The main analytical fields include:

```text
InvoiceNo
StockCode
Description
Quantity
InvoiceDate
UnitPrice
CustomerID
Country
Revenue
Year
Month
MonthName
YearMonth
DayOfWeek
Hour
```

---

## Dataset Summary

The cleaned dataset contains the following overall business metrics:

| Metric              |          Value |
| ------------------- | -------------: |
| Total Revenue       | £10,642,110.80 |
| Total Orders        |         19,960 |
| Total Products      |          3,922 |
| Total Customers     |          4,338 |
| Total Units Sold    |      5,572,420 |
| Average Order Value |        £533.17 |
| Countries           |             38 |

These values form the foundation of the RetailPulse Executive Overview dashboard.

---

# Customer RFM Dataset

RetailPulse also creates a customer-level dataset for **RFM analysis**.

RFM stands for:

* **Recency**
* **Frequency**
* **Monetary**

### Recency

Measures how recently a customer made a purchase.

```text
Recency = Days since the customer's last purchase
```

A lower recency value generally represents a more recently active customer.

### Frequency

Measures how often a customer made purchases.

```text
Frequency = Number of unique orders made by the customer
```

### Monetary

Measures how much revenue a customer generated.

```text
Monetary = Total revenue generated by the customer
```

---

## RFM Customer Segmentation

Customers were assigned to different segments using their RFM scores.

The RetailPulse segmentation includes:

* Champions
* Loyal Customers
* Potential Loyalists
* New Customers
* At Risk
* Lost Customers

### Customer Segment Distribution

| Segment             | Customers |
| ------------------- | --------: |
| Lost Customers      |     1,065 |
| Potential Loyalists |     1,041 |
| Champions           |       957 |
| Loyal Customers     |       503 |
| At Risk             |       453 |
| New Customers       |       319 |

Total:

```text
4,338 customers
```

---

# Customer Prediction Dataset

RetailPulse also generates a customer-level prediction dataset for repurchase analysis.

The prediction dataset contains customer behavioral features and machine learning predictions.

Important fields include:

```text
CustomerID
Recency
Frequency
Monetary
AvgOrderValue
ProductDiversity
Repurchase_Probability
Predicted_Repurchase
Repurchase_Priority
Revenue_At_Risk
```

---

## Machine Learning Features

The prediction model uses customer-level behavioral features including:

| Feature            | Description                            |
| ------------------ | -------------------------------------- |
| `Recency`          | Number of days since last purchase     |
| `Frequency`        | Number of purchases/orders             |
| `Monetary`         | Total customer revenue                 |
| `AvgOrderValue`    | Average order value                    |
| `ProductDiversity` | Number of different products purchased |

These features are used to estimate the probability that a customer will make another purchase.

---

## Repurchase Probability

Customers are grouped into three probability categories.

| Probability   | Segment            |
| ------------- | ------------------ |
| `>= 0.75`     | High Probability   |
| `0.50 – 0.74` | Medium Probability |
| `< 0.50`      | Low Probability    |

Current prediction distribution:

| Segment            | Customers |
| ------------------ | --------: |
| High Probability   |       614 |
| Medium Probability |       914 |
| Low Probability    |     2,088 |

---

## Revenue at Risk

RetailPulse estimates potential revenue exposure using the customer's predicted repurchase probability.

The calculation is:

```text
Revenue_At_Risk =
Monetary × (1 − Repurchase_Probability)
```

This metric helps identify customers whose historical revenue may be exposed if they do not return.

The estimated revenue at risk identified by the model is approximately:

```text
£713,926.92
```

---

# Generated Analytical Files

The project may generate additional datasets during the analysis workflow.

### Customer RFM Data

```text
customer_rfm.csv
```

Contains customer-level RFM metrics and customer segments.

### Customer Prediction Data

```text
customer_predictions.csv
```

Contains customer-level machine learning predictions, probability segments, and revenue-at-risk calculations.

### Cleaned Transaction Data

```text
retail_clean.csv
```

Contains the cleaned transactional dataset used for Power BI and further analysis.

---

# Data Usage in RetailPulse

The dataset supports the following major analytical components:

### 1. Executive Overview

Uses transaction-level data to analyze:

* Revenue
* Orders
* Quantity
* Customers
* Average Order Value
* Monthly revenue trends
* Country-level revenue
* Top products

### 2. Customer Intelligence

Uses RFM analysis to understand:

* Customer value
* Customer activity
* Customer segments
* Recency
* Frequency
* Monetary contribution

### 3. Repurchase Intelligence

Uses machine learning predictions to analyze:

* Repurchase probability
* Customer probability segments
* Actual vs predicted repurchase rates
* Revenue at risk
* Customer retention opportunities

### 4. Product & Geography

Analyzes:

* Product volume
* Product performance
* Units sold
* Countries served
* Units per order
* Order activity by weekday
* Order activity by hour
* Monthly product activity

---

# Repository Data Policy

The original `Online Retail.xlsx` dataset and large generated datasets are **not included directly in this GitHub repository**.

This repository contains the project code, notebooks, documentation, and dashboard-related files required to understand and reproduce the analytical workflow.

The following files are intentionally excluded from the public repository:

```text
Online Retail.xlsx
retail_clean.csv
```

```
