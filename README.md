# 🍕 Pizza Sales Analysis Dashboard  

![Dashboard Cover](Dashboard.png)
![Pizza Performance](Insights.png)
![SQL Database Structure](SQL_Database.png)

---

## 📘 Project Overview  
This project analyzes pizza sales data to uncover insights on top-performing products, revenue drivers, and customer behavior using **SQL Server** and **Power BI**.  
The workflow includes **data cleaning**, **SQL querying**, **data modeling (Snowflake)**, **DAX-based KPI calculation**, and **dashboard visualization**.

---

## 🧩 1. SQL Data Preparation  

The data was processed using **Microsoft SQL Server**, with structured tables and views built inside the database **Pizza**.

### ⚙️ Steps Performed:
- Created database schema and tables for pizza sales.
- Applied **data cleaning**:
  - Removed duplicates and nulls.
  - Fixed data types and standardized field names.
- Built **SQL Views** for clean data integration into Power BI.

### 🧠 Sample SQL Queries

```sql
-- 1️⃣ Retrieve Top 5 Pizzas by Orders
SELECT TOP 5 
    pizza_name, 
    COUNT(DISTINCT order_id) AS Total_Orders
FROM dbo.pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders DESC;
```

```sql
-- 2️⃣ Revenue by Pizza Category
SELECT 
    pizza_category,
    SUM(total_price) AS Total_Revenue
FROM dbo.pizza_sales
GROUP BY pizza_category;
```

```sql
-- 3️⃣ Average Order Value
SELECT 
    SUM(total_price) / COUNT(DISTINCT order_id) AS Avg_Order_Value
FROM dbo.pizza_sales;
```

---

## 🧮 2. Data Modeling  

The Power BI data model follows the **Snowflake Schema**, chosen for its flexibility and scalability.  

### 💡 Components:
- **Fact Table:** Sales transactions.  
- **Dimension Tables:** Pizza details, category, size, and time.  
- **Direct Relationships:** Between fact and dimensions.  
- **Indirect Relationships:** Handled using DAX (e.g. `USERELATIONSHIP()`).

---

## 📊 3. DAX & KPI Calculations  

### 🔹 Main DAX Measures:
```DAX
Total Revenue = SUM(pizza_sales[total_price])

Total Orders = DISTINCTCOUNT(pizza_sales[order_id])

Average Order Value = [Total Revenue] / [Total Orders]

Total Pizzas Sold = SUM(pizza_sales[quantity])

Pizzas per Order = [Total Pizzas Sold] / [Total Orders]
```

These KPIs were visualized in cards and charts for dynamic analysis.

---

## 💡 4. Insights & Recommendations  

### 🥇 **Top Performers — Focus & Promote**  
🟤 *The Thai Chicken* and *Barbecue Chicken* pizzas lead in revenue (~43K each).  
🟠 **Action:** Highlight as “Best Sellers” and bundle them in combo or family offers to maximize total sales.

---

### 📉 **Low Performers — Review & Improve**  
🟤 *Brie Carre* and *Mediterranean* pizzas show weak performance (<15K).  
🟠 **Action:** Reassess pricing, recipe, and visibility in menus to increase engagement.

---

### 🌿 **Healthy Options — Growth Potential**  
🟤 *Spinach Pesto* and *Green Garden* pizzas show steady performance (~15K).  
🟠 **Action:** Promote them as “Healthy Choices” to attract health-conscious customers.

---

### 📈 **Menu Strategy — Optimize Mix**  
🟤 Concentrate marketing and production on high-demand pizzas.  
🟠 **Action:** Adjust inventory and marketing spend toward top-performing categories for better ROI.

---

## 🎯 5. Dashboard Highlights  

### 🔸 KPIs Displayed:
- **Total Orders:** 21K  
- **Average Order Value:** 38.31  
- **Total Revenue:** 817.86K  
- **Pizzas Sold per Order:** 2.32  

### 🔸 Visual Insights:
- Orders trend by **Month & Day**  
- Revenue by **Pizza Category & Size**  
- Top 5 Pizzas by **Revenue, Orders, and Quantity**  
- Interactive filters for date, size, and category  
- Recommendations panel integrated with visuals

---

## 🧰 6. Tools & Technologies  

| Tool | Purpose |
|------|----------|
| 🧮 SQL Server | Data cleaning, transformation & queries |
| 📊 Power BI | Data visualization & DAX modeling |
| 🧾 Excel | Data verification & structure |
| 💻 GitHub | Project hosting & sharing |

---

## 📎 7. Author & Contact  

👤 **Abdallah Elshokey**  
🔗 [LinkedIn Profile](https://www.linkedin.com/in/abdallah-elshokey-230b95225)  
📂 [GitHub Repository](https://github.com/Abdallah101290/HR-Analysis)

---

## 🧠 8. Conclusion  
This project showcases a full **Data Analysis Lifecycle** — from raw data in SQL to meaningful business insights in Power BI.  
Using a **Snowflake Model** ensures efficient DAX calculations and optimized relationships, while visual storytelling drives strategic decisions.

---

⭐ *If you found this project useful, don’t forget to star the repository and connect on LinkedIn!*