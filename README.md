# 🍕 Pizza Sales Analysis Dashboard | Power BI

An interactive **Pizza Sales Analysis Dashboard** built with Microsoft Power BI to evaluate sales performance, monitor key business metrics, identify sales trends, and understand product-level performance across a pizza business.

The report provides two complementary views:
- **Home Page:** Overall business performance, order trends, sales contribution by category and size, and busiest days.
- **Best & Worst Sellers:** Product-level ranking to identify the highest- and lowest-performing pizzas by revenue, quantity sold, and number of orders.

---

## 📌 Project Overview

The objective of this project is to transform raw pizza sales data into meaningful business insights through SQL-based analysis and interactive Power BI visualizations.

The dashboard helps answer questions such as:

- How much revenue does the business generate?
- How many orders and pizzas are sold?
- What is the average order value?
- Which days and months generate the highest number of orders?
- Which pizza categories and sizes contribute most to revenue?
- Which pizzas are the best and worst performers?
- How does product performance differ when measured by revenue, quantity, and order count?

The report includes date and pizza-category filters, allowing users to explore the business performance across different periods and categories.

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| **Microsoft Power BI** | Interactive dashboard development and data visualization |
| **Microsoft SQL Server (T-SQL)** | KPI calculations, aggregations, ranking, and sales analysis queries |
| **Microsoft Excel** | Source dataset |
| **Power BI Visuals** | KPI cards, bar charts, column charts, line charts, and donut charts |

## 📂 Repository Structure

```text
Pizza-Sales-Analysis/
│
├── README.md
│
├── Dashboard/
│   └── PizzaSalesReport.pbix
│
├── SQL/
│   └── Pizza_Sales_Queries.sql
│
├── Dataset/
│   └── pizza_sales_excel_file.xlsx
│
└── Screenshots/
    ├── Home_Page.png
    └── Best_and_Worst_Sellers.png
```

> The folder structure above is a suggested GitHub organization. Place your files in the corresponding folders and use the same screenshot filenames, or update the image paths below to match your repository.

---

## 📊 Dataset Description

The project uses a pizza sales dataset containing **48,620 records** covering the period **January 1, 2015 to December 31, 2015**.

The dataset contains order-level and product-level information, including:

| Column | Description |
|---|---|
| `pizza_id` | Unique identifier for each pizza record |
| `order_id` | Identifier used to group pizzas belonging to an order |
| `pizza_name_id` | Unique identifier for the pizza type |
| `quantity` | Number of pizzas sold |
| `order_date` | Date on which the order was placed |
| `order_time` | Time at which the order was placed |
| `unit_price` | Price of one pizza |
| `total_price` | Total price for the pizza record |
| `pizza_size` | Size of the pizza |
| `pizza_category` | Category of the pizza |
| `pizza_ingredients` | Ingredients used in the pizza |
| `pizza_name` | Name of the pizza |

**Dataset coverage:** 48,620 records, 21,350 distinct orders, and 49,574 pizzas sold.

---

## 📈 Dashboard Walkthrough

### 1. Home Page – Overall Sales Performance

The Home Page provides a consolidated overview of business performance through KPI cards and interactive charts.

![Pizza Sales Dashboard - Home Page](Screenshots/Home_Page.png)

#### Key Performance Indicators (KPIs)

| KPI | Value | Business Meaning |
|---|---:|---|
| Total Revenue | **$817.86K** | Total revenue generated from pizza sales |
| Average Order Value | **$38.31** | Average revenue generated per order |
| Total Orders | **21,350** | Total number of distinct orders |
| Total Pizzas Sold | **49,574** | Total quantity of pizzas sold |
| Average Pizzas Per Order | **2.32** | Average number of pizzas purchased per order |

#### Visualizations and Analysis

**A. Daily Trend of Total Orders**

- Compares the number of orders across the days of the week.
- Helps identify the busiest days and understand weekly demand patterns.
- Friday records the highest order volume, at approximately 3.5K orders.

**B. Monthly Trend of Total Orders**

- Tracks order volume across all 12 months.
- Helps identify seasonal patterns and changes in customer demand.
- July records the highest monthly order volume, at approximately 1,935 orders.

**C. Percentage of Sales by Pizza Category**

- Uses a donut chart to show each category's contribution to total revenue.
- Makes it easier to compare Classic, Supreme, Chicken, and Veggie pizzas.

| Pizza Category | Revenue Contribution |
|---|---:|
| Classic | 26.91% |
| Supreme | 25.46% |
| Chicken | 23.96% |
| Veggie | 23.68% |

**D. Percentage of Sales by Pizza Size**

- Shows the revenue contribution of different pizza sizes.
- Helps understand customer preferences and the revenue mix by size.

| Pizza Size | Revenue Contribution |
|---|---:|
| Large | 45.89% |
| Medium | 30.49% |
| Regular / Small | 21.77% |
| X-Large | 1.72% |
| XX-Large | 0.12% |

**E. Total Pizzas Sold by Pizza Category**

- Compares the total quantity sold across pizza categories.
- Helps identify categories with the highest sales volume.
- Classic pizzas lead the category comparison with 14,888 pizzas sold.

---

### 2. Best & Worst Sellers – Product-Level Performance

This page focuses on individual pizza performance and ranks products using three different business metrics.

![Pizza Sales Dashboard - Best and Worst Sellers](Screenshots/Best_and_Worst_Sellers.png)

#### Best Sellers

The dashboard identifies the top five pizzas based on:

1. **Revenue:** Pizzas generating the highest total sales revenue.
2. **Quantity:** Pizzas with the highest number of units sold.
3. **Total Orders:** Pizzas appearing in the highest number of distinct orders.

#### Worst Sellers

The dashboard also identifies the bottom five pizzas based on the same three metrics:

1. **Revenue:** Pizzas generating the lowest total revenue.
2. **Quantity:** Pizzas with the lowest number of units sold.
3. **Total Orders:** Pizzas appearing in the lowest number of distinct orders.

Using these three metrics provides a more complete view of product performance. A pizza may generate high revenue without having the highest quantity sold, so evaluating products from multiple perspectives helps avoid relying on a single metric.

#### Dynamic Business Insights

The page includes insight summaries that highlight the best- and worst-performing pizzas across revenue, quantity, and order count. These summaries make the dashboard easier to interpret without manually comparing every chart.

---

## 🔍 SQL Analysis

The project includes a dedicated SQL script containing analytical queries written in **Microsoft SQL Server (T-SQL)**.

The queries cover the following areas:

| Analysis | SQL Concepts Used |
|---|---|
| Total Revenue | `SUM()` |
| Average Order Value | `SUM()`, `COUNT(DISTINCT)` |
| Total Pizzas Sold | `SUM()` |
| Total Orders | `COUNT(DISTINCT)` |
| Average Pizzas Per Order | `CAST()`, `DECIMAL` |
| Daily Order Trends | `DATENAME()`, `GROUP BY` |
| Monthly Order Trends | `DATENAME()`, `GROUP BY` |
| Sales by Pizza Category | `SUM()`, subqueries, `GROUP BY` |
| Sales by Pizza Size | `SUM()`, subqueries, `GROUP BY` |
| Top 5 Pizza Analysis | `TOP`, `ORDER BY DESC` |
| Bottom 5 Pizza Analysis | `TOP`, `ORDER BY ASC` |

### Example: Total Revenue

```sql
SELECT
    SUM(total_price) AS Total_Revenue
FROM pizza_sales;
```

### Example: Average Order Value

```sql
SELECT
    SUM(total_price) / COUNT(DISTINCT order_id) AS Avg_Order_Value
FROM pizza_sales;
```

### Example: Top 5 Pizzas by Revenue

```sql
SELECT TOP 5
    pizza_name,
    SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue DESC;
```

### Example: Daily Order Trend

```sql
SELECT
    DATENAME(WEEKDAY, order_date) AS Order_Day,
    COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY DATENAME(WEEKDAY, order_date);
```

The complete set of queries is available in [`SQL/Pizza_Sales_Queries.sql`](SQL/Pizza_Sales_Queries.sql).

---

## 💡 Key Business Insights

Based on the dashboard's displayed results:

1. **Strong overall sales performance:** The business generated approximately **$817.86K in revenue** from 21,350 orders.
2. **Friday is the busiest day:** Friday records the highest order volume, suggesting stronger demand toward the end of the working week.
3. **July leads monthly orders:** July records approximately 1,935 orders, the highest among the months shown.
4. **Classic pizzas lead category sales:** The Classic category contributes 26.91% of total revenue and has the highest quantity sold, with 14,888 pizzas.
5. **Large pizzas dominate revenue:** Large pizzas contribute 45.89% of total revenue, making them the leading size segment.
6. **Product performance varies by metric:** Ranking pizzas by revenue, quantity, and order count reveals different aspects of product performance and helps identify products that may need further attention.

---

## 🎯 Skills Demonstrated

- SQL querying and analytical calculations using Microsoft SQL Server.
- Business KPI definition and performance monitoring.
- Data analysis and exploratory sales analysis.
- Power BI dashboard development and data visualization.
- Product performance analysis and ranking.
- Time-based analysis using daily and monthly trends.
- Business storytelling through interactive reports.
- Translating raw sales data into actionable business insights.

---

## 🚀 How to Explore the Project

1. Clone or download this repository.
2. Open `Dashboard/PizzaSalesReport.pbix` using Microsoft Power BI Desktop.
3. If prompted, update the source file path to the dataset in the `Dataset` folder.
4. Refresh the data if required.
5. Use the date range and pizza category slicers to filter the report.
6. Navigate between the **Home** and **Best/Worst Sellers** pages to explore the analysis.
7. Open the SQL script in SQL Server Management Studio (SSMS) to review and execute the analytical queries against a table named `pizza_sales` containing the dataset fields.

---

## 📁 Project Files

- **Power BI Report:** `Dashboard/PizzaSalesReport.pbix`
- **SQL Queries:** `SQL/Pizza_Sales_Queries.sql`
- **Source Dataset:** `Dataset/pizza_sales_excel_file.xlsx`
- **Dashboard Screenshots:** `Screenshots/`

---

## 👤 Author

**Hrithik Sangle**

Interested in Data Analytics, Business Intelligence, and Data Engineering.

- **LinkedIn:** [Add your LinkedIn profile URL](https://www.linkedin.com/)
- **GitHub:** [Add your GitHub profile URL](https://github.com/)

---

⭐ If you find this project useful, feel free to star the repository!
