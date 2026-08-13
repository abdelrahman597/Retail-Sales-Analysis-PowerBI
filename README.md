# 📊 Retail Sales Analysis | Power BI

## 📌 Project Overview

This project presents an end-to-end **Retail Sales Analysis** developed using Power BI.

The objective of the project is to analyze sales performance, product profitability, customer behavior, regional performance, and sales trends, then transform the findings into actionable business insights and recommendations.

The report consists of four interactive pages:

- Sales Overview
- Products Analysis
- Customers Analysis
- Business Insights

---

## 🎯 Business Objectives

The analysis aims to answer key business questions such as:

- Which product categories generate the highest sales and profit?
- Which categories have the strongest profit margins?
- Which brands contribute the most to overall business performance?
- Which products contribute the most to profitability?
- Which regions generate the highest sales?
- How has sales performance changed over time?
- What are the main characteristics of the customer base?
- What business actions can be recommended based on the findings?

---

## 🛠️ Tools & Technologies

- **Power BI**
- **Power Query** — Data cleaning and transformation
- **DAX** — Measures and calculated columns
- **Data Modeling** — Relationships between tables
- **Data Visualization**
- **Business Analysis**

---

## 🧹 Data Preparation

The dataset was reviewed, cleaned, and transformed before building the dashboard.

The preparation process included:

- Checking and correcting data types
- Checking duplicate records
- Reviewing missing and inconsistent values
- Preparing date fields for time-based analysis
- Creating customer age groups
- Building relationships between relevant tables
- Creating DAX measures and calculated columns for analysis

### Dataset

`Retail_Sales_Dataset.xlsx`

---

# 📐 DAX Calculations

## Key Measures

### SumSales

```DAX
SumSales =
SUMX(
    Sales,
    Sales[Quantity] * RELATED(Products[Price])
)
```

### Total Profit

```DAX
Total Profit =
SUMX(
    Sales,
    Sales[Quantity] *
    (RELATED(Products[Price]) - RELATED(Products[Cost]))
)
```

### Profit Margin %

```DAX
Profit Margin % =
DIVIDE(
    [Total Profit],
    [SumSales],
    0
)
```

### Number of Customers

```DAX
Number of Customers =
DISTINCTCOUNT(Customers[CustomerID])
```

### Average Age

```DAX
Average Age =
AVERAGE(Customers[Age])
```

---

## Date Analysis Columns

The following calculated columns were created to support time-based analysis.

### Year

```DAX
Year =
YEAR(Sales[OrderDate])
```

### Quarter

```DAX
Quarter =
"Q" & QUARTER(Sales[OrderDate])
```

### Month Name

```DAX
Month Name =
FORMAT(Sales[OrderDate], "MMMM", "en-US")
```

### Month Number

```DAX
Month Number =
MONTH(Sales[OrderDate])
```

`Month Number` was used to sort `Month Name` chronologically instead of alphabetically.

---

## Customer Segmentation

### Age Group

```DAX
Age Group =
SWITCH(
    TRUE(),
    Customers[Age] >= 18 && Customers[Age] <= 25, "18-25",
    Customers[Age] >= 26 && Customers[Age] <= 35, "26-35",
    Customers[Age] >= 36 && Customers[Age] <= 45, "36-45",
    Customers[Age] >= 46 && Customers[Age] <= 55, "46-55",
    Customers[Age] >= 56, "56+",
    "Unknown"
)
```

### Age Group Sort

```DAX
Age Group Sort =
SWITCH(
    Customers[Age Group],
    "18-25", 1,
    "26-35", 2,
    "36-45", 3,
    "46-55", 4,
    "56+", 5
)
```

`Age Group Sort` was used to maintain the correct logical order of customer age segments in dashboard visuals.
---

# 📊 Dashboard Pages

## 1️⃣ Sales Overview

The Sales Overview provides a high-level view of overall business performance.

### Main Analysis

- Total Sales
- Total Profit
- Number of Orders
- Quantity Sold
- Sales performance over time
- Sales by Category
- Sales by Region
- Sales distribution by Gender
- Payment Method analysis

![Sales Overview](sales%20overview.png)

> **Data Note:** Year-over-year sales comparison was based on the January–November period to ensure a fair comparison between 2023 and 2024, as December 2024 data is incomplete.
---

## 2️⃣ Products Analysis

The Products Analysis page focuses on product, category, and brand performance.

### Main Analysis

- Number of Products
- Average Price
- Average Cost
- Total Profit
- Average Price vs. Average Cost by Category
- Product Launch Year analysis
- Brand-level Price and Cost comparison

![Products Analysis](products%20analysis.png)
---

## 3️⃣ Customers Analysis

The Customers Analysis page explores customer demographics and customer acquisition patterns.

### Main Analysis

- Total Number of Customers
- Average Customer Age
- New Customers Over Time
- Customer Distribution by Gender
- Customer Distribution by Age Group

![Customers Analysis](customers%20analysis.png)

> **Data Note:** 2025 customer acquisition data is incomplete, so the lower number of new customers in 2025 should not be interpreted as a decline in customer acquisition.
---

## 4️⃣ Business Insights

The final page combines the most important findings from the previous analysis and translates them into actionable business recommendations.

![Business Insights](business%20insights.png)
---

# 🔎 Key Insights

### 1️⃣ Grocery Leads Profitability

Grocery is the most profitable category, generating approximately **7.35M in profit** with the highest **profit margin of 38%**.

Fashion generated approximately **6.95M in profit with a 31% margin**, despite generating higher total sales.

This indicates that Grocery converts a larger proportion of its sales into profit.

---

### 2️⃣ Grenade Leads Brand Performance

**Grenade** is the top-performing brand, ranking first in both sales and profitability and generating approximately **3.51M in total profit**.

---

### 3️⃣ High Profit Concentration in Protein Bar

**Protein Bar contributes approximately 48% of Grocery's total profit.**

While this product represents a major profitability driver, it also indicates a significant concentration of Grocery's profit in a single product.

---

### 4️⃣ Upper Egypt Leads Regional Sales

**Upper Egypt was the highest-selling region across all product categories.**

This indicates consistently strong regional performance across the product portfolio.

---

### 5️⃣ Sales Remained Stable Year-over-Year

Sales remained stable across comparable periods, generating approximately **32M from January to November in both 2023 and 2024**.

The January–November period was used to ensure a fair year-over-year comparison because December 2024 data is incomplete.

---

# 💡 Key Recommendations

### 1️⃣ Strengthen Grocery While Reducing Concentration Risk

Prioritize investment in Grocery while protecting its strong **38% profit margin**.

At the same time, reduce dependency on Protein Bar by developing and promoting other high-margin Grocery products to diversify profit sources.

---

### 2️⃣ Evaluate Protein Bar Pricing Opportunities

Evaluate controlled price optimization for Protein Bar to determine whether additional margin can be captured without materially reducing customer demand.

---

### 3️⃣ Leverage Grenade's Strong Performance

Maintain strong support for Grenade and analyze the factors behind its performance.

Successful practices identified from Grenade could potentially be applied to other brands to improve their performance.

---

### 4️⃣ Learn From Upper Egypt

Investigate the factors driving Upper Egypt's strong sales performance.

Where appropriate, successful regional strategies could be applied to weaker-performing regions.

---

### 5️⃣ Pursue Additional Sales Growth

Sales remained stable across comparable periods in 2023 and 2024.

The business should explore targeted growth initiatives while maintaining the factors that currently support stable year-over-year performance.

---

# 📂 Project Structure

```text
Retail-Sales-Analysis-PowerBI/
│
├── Retail_Sales_Analysis.pbix
├── Retail_Sales_Dataset.xlsx
│
├── Sales_Overview.png
├── Products_Analysis.png
├── Customers_Analysis.png
├── Business_Insights.png
│
├── README.md
└── LICENSE
```

---

# 🚀 Project Highlights

This project demonstrates practical experience in:

- Data Cleaning & Transformation
- Power Query
- Data Modeling
- DAX Measures
- DAX Calculated Columns
- Time-Based Analysis
- KPI Development
- Interactive Dashboard Design
- Data Visualization
- Profitability Analysis
- Customer Segmentation
- Business Insight Generation
- Data-Driven Recommendations

---

## 👤 Author

**Abdelrahman Sayed**

Junior Data Analyst
