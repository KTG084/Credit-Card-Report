# 💳 Credit Card Transaction Analysis

> An end-to-end Business Intelligence project analyzing credit card transactions, customer spending behavior, revenue trends, and card performance using **Power BI**, **SQL**, **DAX**, and **Power Query**.

![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?style=for-the-badge&logo=powerbi)
![SQL](https://img.shields.io/badge/SQL-Analytics-orange?style=for-the-badge)
![DAX](https://img.shields.io/badge/DAX-Measures-blue?style=for-the-badge)
![Power Query](https://img.shields.io/badge/Power%20Query-ETL-green?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

---

## 📖 Table of Contents

- [Dashboard Preview](#-dashboard-preview)
- [Project Overview](#-project-overview)
- [Tech Stack](#-tech-stack)
- [Repository Structure](#-repository-structure)
- [Dataset](#-dataset)
- [Data Preparation](#-data-preparation)
- [Data Model](#-data-model)
- [Dashboard Features](#-dashboard-features)
- [Key Performance Indicators](#-key-performance-indicators)
- [DAX Measures](#-dax-measures)
- [Business Insights](#-business-insights)
- [Getting Started](#-getting-started)
- [Future Improvements](#-future-improvements)
- [Author](#-author)
- [License](#-license)

---



<!-- Replace the placeholders below with actual screenshots, e.g. assets/screenshots/executive-dashboard.png -->

## 📷 Dashboard Preview

| Executive Dashboard | Customer Dashboard |
|---------------------|--------------------|
| ![](assets/Screenshots/Screenshot%202026-07-01%20185918.png) | ![](assets/Screenshots/Screenshot%202026-07-01%20185932.png) |

> 📄 A pre-rendered version of the full report is also available in [`ReportIN_PDF.pdf`](ReportIN_PDF.pdf) if you don't have Power BI installed.

---

## 📌 Project Overview

This project analyzes **10,000+ credit card customers** and their associated weekly transaction records to uncover spending patterns, revenue performance, customer demographics, and card-level trends.

Raw data is loaded into SQL for structured storage, shaped with Power Query, modeled with DAX, and visualized in an interactive Power BI dashboard — enabling business users to monitor KPIs, evaluate card performance, and identify high-value customer segments.

---

## 🚀 Tech Stack

| Category | Tools |
|---|---|
| Database | SQL (Server / PostgreSQL / MySQL — adjust to your engine) |
| ETL / Transformation | Power Query |
| Modeling & Metrics | DAX |
| Visualization | Power BI |
| Raw Data | CSV |

---

## 📂 Repository Structure

```
Credit-Card-Report
│
├── SQL_createTable_Query.sql   # DDL for cc_detail & cust_detail tables
├── customer.csv                 # Customer master data
├── credit_card.csv              # Weekly transaction/card data
├── cust_add.csv                 # Additional customer records
├── cc_add.csv                   # Additional transaction records
├── wada.pbix                    # Power BI dashboard file
├── ReportIN_PDF.pdf              # Exported static report
└── README.md
```

---

## 📊 Dataset

The project uses two related datasets, joined on `Client_Num`.

### Customer Dataset (`customer.csv`, `cust_add.csv`)

| Field | Description |
|---|---|
| Client_Num | Unique customer identifier |
| Customer_Age | Age of the customer |
| Gender | Customer gender |
| Dependent_Count | Number of dependents |
| Education_Level | Highest level of education |
| Marital_Status | Marital status |
| state_cd | State code |
| Zipcode | Postal code |
| Car_Owner | Owns a car (Y/N) |
| House_Owner | Owns a house (Y/N) |
| Personal_loan | Has a personal loan (Y/N) |
| contact | Preferred contact method |
| Customer_Job | Occupation |
| Income | Annual income |
| Cust_Satisfaction_Score | Customer satisfaction rating |

### Transaction / Card Dataset (`credit_card.csv`, `cc_add.csv`)

| Field | Description |
|---|---|
| Client_Num | Unique customer identifier (FK) |
| Card_Category | Blue, Silver, Gold, or Platinum |
| Annual_Fees | Annual card fee |
| Activation_30_Days | Activated within 30 days (0/1) |
| Customer_Acq_Cost | Cost to acquire the customer |
| Week_Start_Date | Start date of the reporting week |
| Week_Num | Week number |
| Qtr | Quarter |
| current_year | Reporting year |
| Credit_Limit | Assigned credit limit |
| Total_Revolving_Bal | Revolving balance carried |
| Total_Trans_Amt | Total transaction amount |
| Total_Trans_Vol / Total_Trans_Ct | Total transaction count |
| Avg_Utilization_Ratio | Average credit utilization |
| Use Chip | Chip vs. swipe usage |
| Exp Type | Spend category (Grocery, Fuel, Travel, Entertainment, Bills, Food) |
| Interest_Earned | Interest revenue earned |
| Delinquent_Acc | Delinquent account flag |

**Scale:** ~10,100 customers and ~10,100 weekly transaction records across 4 card tiers and 6 spend categories.

---

## ⚙ Data Preparation

The data preparation workflow includes:

- Creating the `cc_detail` and `cust_detail` tables via `SQL_createTable_Query.sql`
- Importing the CSV files into SQL
- Cleaning missing/null values and standardizing data types
- Power Query transformations (renaming, splitting, type casting)
- Building the relationship between `cust_detail` and `cc_detail` on `Client_Num`
- Feature engineering (e.g., age groups, income bands, quarter/week fields)

---

## 📐 Data Model

The dashboard uses a simple two-table relational model, joined on `Client_Num`:

```
+----------------+        1        *        +----------------+
|  cust_detail   |------------------------->|   cc_detail    |
|  (Customers)   |       Client_Num          | (Transactions/ |
|                |                            |  Card Info)   |
+----------------+                            +----------------+
```

Each customer (`cust_detail`) can have multiple weekly card/transaction records (`cc_detail`).

---

## 📈 Dashboard Features

The interactive Power BI dashboard provides insights into:

### Executive Overview
- Total Revenue
- Total Transactions
- Total Customers
- Average Transaction Value
- Revenue Growth

### Customer Analytics
- Spending by Gender
- Spending by Age Group
- Income Group Analysis
- Occupation-wise Revenue
- State-wise Customers

### Transaction Analytics
- Monthly Transaction Trends
- Quarterly Revenue
- Transaction Count
- Merchant/Spend Category Analysis (Grocery, Fuel, Travel, Entertainment, Bills, Food)
- Payment Mode Distribution (Chip vs. Swipe)

### Card Performance
- Revenue by Card Type (Blue, Silver, Gold, Platinum)
- Transaction Volume by Card
- Credit Utilization
- Interest Revenue
- Card-wise KPIs

---

## 📊 Key Performance Indicators

- Total Revenue
- Total Transaction Amount
- Total Interest Earned
- Total Customers
- Transaction Count
- Average Revenue per Customer
- Average Transaction Value
- Revenue Growth %
- Customer Growth %

---

## 🧠 DAX Measures

Some of the key DAX calculations include:

- Total Revenue
- Total Transactions
- Revenue Growth
- Running Total
- Average Transaction Value
- Total Interest
- Customer Count
- Dynamic KPI Cards
- Time Intelligence Measures

---

## 📈 Business Insights

The dashboard helps answer questions such as:

- Which card type generates the highest revenue?
- Which customer segments contribute the most to sales?
- How do spending patterns vary across age groups?
- Which states have the highest transaction volume?
- What are the monthly and quarterly revenue trends?
- Which spend categories generate the most transactions?
- How much interest revenue is earned from each card type?
- What is the relationship between credit utilization and delinquency?

---

## ▶ Getting Started

### Prerequisites

- Power BI Desktop
- A SQL database engine (SQL Server, PostgreSQL, or MySQL)

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/Credit-Card-Transaction-Analysis.git
cd Credit-Card-Transaction-Analysis
```

### 2. Create the SQL tables

Run the schema script to create `cc_detail` and `cust_detail`:

```bash
SQL_createTable_Query.sql
```

### 3. Import the data

Load the following CSV files into their corresponding tables:

| File | Target Table |
|---|---|
| `customer.csv`, `cust_add.csv` | `cust_detail` |
| `credit_card.csv`, `cc_add.csv` | `cc_detail` |

### 4. Open the dashboard

Open `wada.pbix` in Power BI Desktop, refresh the data source to point at your database, and explore the report.

> Don't have Power BI installed? View the static export in [`ReportIN_PDF.pdf`](ReportIN_PDF.pdf).

---

## 📌 Future Improvements

- [ ] Customer Lifetime Value (CLV)
- [ ] RFM Segmentation
- [ ] Fraud Detection Dashboard
- [ ] Predictive Spending Forecast
- [ ] Customer Churn Analysis
- [ ] Real-time SQL Database Integration

---

## 👨‍💻 Author

**Karanjyoti Medhi**

- Power BI
- SQL
- DAX
- Power Query
- Data Analytics
- Dashboard Development

---

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## ⭐ Support

If you found this project useful, consider giving it a star — it helps others discover it too!
