# 🛒 Zepto E-commerce SQL Data Analyst Portfolio Project

This is a **real-world Data Analyst Portfolio Project** based on an e-commerce inventory dataset scraped from [Zepto](https://www.zeptonow.com/) — one of India’s fastest-growing quick-commerce startups.  

It simulates real analyst workflows, from **raw data exploration** to **business-focused SQL data analysis**.

---

## 🎯 Who is this Project for?
- 📊 **Data Analyst aspirants** who want to build a Portfolio Project for LinkedIn & interviews  
- 📚 **Students learning SQL hands-on**  
- 💼 **Job seekers** preparing for interviews in retail, e-commerce, or product analytics  

---

## 📌 Project Overview
The goal is to simulate how data analysts in e-commerce/retail industries use SQL for:

✅ Setting up and cleaning a messy, real-world database  
✅ Performing **Exploratory Data Analysis (EDA)** → product categories, availability, pricing inconsistencies  
✅ Implementing **Data Cleaning** → handling nulls, removing invalid rows, converting paise → rupees  
✅ Writing **business-driven SQL queries** → insights on pricing, inventory, stock, and revenue  

---

## 📂 Dataset Overview
The dataset was sourced from [Kaggle](https://www.kaggle.com/datasets/palvinder2006/zepto-inventory-dataset/data?select=zepto_v2.csv) and mimics a **real-world e-commerce system**.

Each row represents a **unique SKU (Stock Keeping Unit)**.  
Duplicate names exist (different package sizes/weights/discounts).  

### 🧾 Columns:
- **sku_id** → Unique identifier (Primary Key)  
- **name** → Product name  
- **category** → Product category (Fruits, Snacks, Beverages, etc.)  
- **mrp** → Maximum Retail Price (originally in paise, converted to ₹)  
- **discountPercent** → Discount applied (%)  
- **discountedSellingPrice** → Final selling price (₹)  
- **availableQuantity** → Units available in stock  
- **weightInGms** → Product weight in grams  
- **outOfStock** → Boolean flag (True/False)  
- **quantity** → Number of units per package  

---

## 🔧 Project Workflow

### 1️⃣ Database & Table Creation
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

---

### 2️⃣ Data Import
Using **pgAdmin import** or `\copy` command:
\copy zepto(category,name,mrp,discountPercent,availableQuantity,
discountedSellingPrice,weightInGms,outOfStock,quantity)
FROM 'data/zepto_v2.csv'
WITH (FORMAT csv, HEADER true, DELIMITER ',', QUOTE '"', ENCODING 'UTF8');

---

### 3️⃣ 🔍 Data Exploration
- Row count, sample preview  
- Check **null values**  
- Distinct **product categories**  
- In-stock vs **out-of-stock analysis**  
- **Duplicate product names**  

---

### 4️⃣ 🧹 Data Cleaning
- Removed rows where **MRP = 0** or **sellingPrice = 0**  
- Converted **paise → rupees**  
- Checked for **unrealistic discounts**  
- Verified **data integrity**  

---

### 5️⃣ 📊 Business Analysis (SQL Insights)
- Top 10 products by **discount %**  
- High-MRP products that are **out of stock**  
- **Revenue by category**  
- Expensive products (**MRP > ₹500, discount < 10%**)  
- Top 5 categories with **highest average discounts**  
- **Price per gram** → best value products  
- Weight classification: *Low, Medium, Bulk*  
- **Total inventory weight** per category  
- **Out-of-stock %** per category  
- **Revenue contribution %** per category  

---

## 📈 Sample Business Insights
- 🏷️ **Top Discounts** → Some categories had >40% discounts → strong customer attraction  
- 📦 **Revenue Drivers** → Essentials & Beverages contributed most revenue  
- 🚫 **Stockouts** → High-MRP products frequently out of stock → revenue loss  
- ⚖️ **Best Value Deals** → Low price per gram + high discount gave **best ROI**  
- 📊 **Category Trends** → High out-of-stock % in some categories → better inventory planning needed  

---

## 💡 Business Recommendations
1. Restock **high-MRP products** that are often out of stock  
2. Promote **best-value products** with **bundle offers**  
3. Improve **inventory planning** in high out-of-stock categories  
4. Validate data for **unrealistic discounts**  
5. Run targeted marketing around **high-discount categories**  

---

## 📜 License
**MIT License** — Free to use in learning projects, portfolios, or personal work.  

---
