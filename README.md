

# **Zepto E-commerce SQL Data Analyst Portfolio Project**

![SQL Badge](https://img.shields.io/badge/SQL-PostgreSQL-blue) ![CSV Badge](https://img.shields.io/badge/Data-CSV-green) ![Portfolio Badge](https://img.shields.io/badge/Portfolio-Project-orange)

---

## **Problem Statement**

In the fast-growing e-commerce sector, companies like Zepto face challenges managing large inventories with multiple SKUs for the same product. Raw product data is often messy, inconsistent, and difficult to analyze.

**Goal:** Simulate real-world data analyst workflows to clean, explore, and extract business insights from Zepto’s e-commerce product inventory dataset using SQL.

**Business Questions Solved:**

* Which products are best-value for customers?
* What are the inventory trends across categories?
* How to identify high-MRP or out-of-stock products impacting revenue?
* How to categorize products for inventory management?

---

## **Solution Overview**

This project demonstrates an **end-to-end SQL workflow** applied to a real-world e-commerce dataset:

* **Data Setup:** Creation of SQL tables with proper data types.
* **Data Cleaning:** Handling nulls, invalid entries, and unit conversions.
* **Exploratory Data Analysis (EDA):** Explore categories, stock availability, and pricing inconsistencies.
* **Business Insights:** SQL queries to derive actionable insights for revenue and inventory optimization.

This workflow mirrors what a **real data analyst** would perform in an e-commerce company.

---

## **Dataset Overview**

Each row represents a unique SKU (Stock Keeping Unit).

| Column                 | Description                                                      |
| ---------------------- | ---------------------------------------------------------------- |
| sku_id                 | Unique identifier for each product entry (Primary Key)           |
| name                   | Product name as it appears on the app                            |
| category               | Product category (Fruits, Snacks, Beverages, etc.)               |
| mrp                    | Maximum Retail Price (originally in paise, converted to ₹)       |
| discountPercent        | Discount applied on MRP                                          |
| discountedSellingPrice | Final price after discount (converted to ₹)                      |
| availableQuantity      | Units available in inventory                                     |
| weightInGms            | Product weight in grams                                          |
| outOfStock             | Boolean flag indicating stock availability                       |
| quantity               | Number of units per package (mixed with grams for loose produce) |

---

## **Database Schema**

```text
+------------------------+
|        zepto           |
+------------------------+
| sku_id (PK)            |
| category VARCHAR(120)   |
| name VARCHAR(150)       |
| mrp NUMERIC(8,2)       |
| discountPercent NUMERIC(5,2) |
| availableQuantity INT   |
| discountedSellingPrice NUMERIC(8,2) |
| weightInGms INT         |
| outOfStock BOOLEAN      |
| quantity INT            |
+------------------------+
```

> You can replace this ASCII diagram with a **visual diagram** (PNG or SVG) using tools like [dbdiagram.io](https://dbdiagram.io) or draw.io.

---

## **Project Workflow**

**Visual Workflow Diagram (Example Placeholder)**

```text
Raw CSV Data
     │
     ▼
Data Exploration (EDA)
     │
     ▼
Data Cleaning & Transformation
     │
     ▼
Business Insights & SQL Analysis
     │
     ▼
Reports / Portfolio Results
```

> You can replace this with a professional **workflow image** for GitHub README.

---

### **1. Database & Table Creation**

```sql
CREATE TABLE zepto (
    sku_id SERIAL PRIMARY KEY,
    category VARCHAR(120),
    name VARCHAR(150) NOT NULL,
    mrp NUMERIC(8,2),
    discountPercent NUMERIC(5,2),
    availableQuantity INTEGER,
    discountedSellingPrice NUMERIC(8,2),
    weightInGms INTEGER,
    outOfStock BOOLEAN,
    quantity INTEGER
);
```

---

### **2. Data Import**

```sql
\copy zepto(category, name, mrp, discountPercent, availableQuantity,
            discountedSellingPrice, weightInGms, outOfStock, quantity)
FROM 'data/zepto_v2.csv' 
WITH (FORMAT csv, HEADER true, DELIMITER ',', QUOTE '"', ENCODING 'UTF8');
```

> ⚠️ Fix encoding issues by saving the CSV in **UTF-8 format**.

---

### **3. 🔍 Data Exploration**

* Count total records
* Sample dataset view
* Check null values
* Identify distinct categories
* Compare in-stock vs out-of-stock
* Detect duplicate SKUs

---

### **4. 🧹 Data Cleaning**

* Remove rows with `mrp` or `discountedSellingPrice` = 0
* Convert prices from **paise to rupees**

---

### **5. 📊 Business Insights**

* Top 10 best-value products
* High-MRP products out-of-stock
* Potential revenue per category
* Filter expensive products (MRP > ₹500) with minimal discount
* Rank top 5 categories by average discount
* Calculate price per gram
* Group products by weight: Low, Medium, Bulk
* Total inventory weight per category

---

## **How to Use This Project**

1. Clone the repository.
2. Open `zepto_SQL_data_analysis.sql` (contains table creation, EDA, cleaning, and business queries).
3. Load dataset into **pgAdmin** or PostgreSQL client.
4. Create a database and run the SQL file.

---




