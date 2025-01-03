# Business-Performance-Evaluation-Data-Analytics
A business performance analytics project.  

## Table of Contents
1. [About the project](#BUSINESS-PERFORMANCE-SQL-EXCEL-TABLEAU-PROJECT)
1. [Business objective and problem definition.](#BUSINESS-OBJECTIVE-AND-PROBLEM-STATEMENT)
2. [Business metrics.](#BUSINESS-METRICS)
3. [Tools.](#TOOLS)
4. [Steps.](#STEPS)
5. [Insights.](#INSIGHTS)

## ABOUT THE PROJECT

### BUSINESS PERFORMANCE SQL EXCEL & TABLEAU PROJECT

In this project, we explain how a typical Data Analytics or Business Analytics project will be implemented. The steps are explained below;

**1.	Understanding the business problems:** In my view, Data Analytics should follow simple and adaptable approach. That is, it can be fine-tuned to fit any kind of project. Although this is a preliminary step in Data Analytics, it helps you as a Data Analyst understand the business needs and as well discuss about your approach to solving the problem.

Typically, I would begin by consulting with clients and stakeholders to fulfil the step (understanding the business problems) as pointed out. 

**2.	Understanding the business goals:** In this step, we discuss the business goals and preferred performance metrics to evaluate. This leads to information or data gathering. We then have to model the data to ensure it contains the necessary information we need. Finally, we jointly carry out project scoping and planning. With this step we would have created an efficient business workflow that meets the aim, timeframe and budget.

**3.	Taking steps to find a solution:** Here, we implement the project plan whilst keeping stakeholders and clients updated on the progress. This step would often involve creating reports and dashboards of the agreed metrics leveraging various data visualization tools such as Tableau, Power BI, Google Looker Studio, MS Excel depending on which tool the business feels most acquainted with. 

The final report would often include a measure of the initial goal against the outcomes. In other words, we interpret the results of our analysis to demonstrate the essence of the project.

## BUSINESS OBJECTIVE AND PROBLEM DEFINITION.
For this particular problem, a start-up business wants to evaluate its business performance across regions, brands, product category and channels of sale. They are particularly interested in the following metrics;

## BUSINESS METRICS

1.	Total & average revenue generated between 2016 – 2018.
2.	Total & average monthly revenue generated between 2016 – 2018.
3.	Total & average revenue generated by region.
4.	Total units sold.
5.	Total orders processed.
6.	Number of customers.
7.	Most profitable customers.
8.	Sales representative performance by revenue.
9.	Revenue by brand.

### TOOLS
- SQL: 
This query in this project is written for MSSQL
First, we create a database if we have don’t already have one using te following command. This step of creating a database can be skipped if we already have a database.

```
Create database Bikestore;

Initialize the database using
Use bikestore;

SELECT orders.order_id AS [ORDER_ID], CONCAT(customers.first_name, ' ', customers.last_name) AS [CUSTOMERS], stores.city AS [CITY], stores.state AS [STATE], 
order_date AS [ORDER_DATE], 
quantity AS [QUANTITY], (order_items.quantity * order_items.list_price) AS [REVENUE], PRODUCT_NAME,

categories.category_name AS [CATEGORY_NAME], CONCAT(staffs.first_name, ' ', staffs.last_name) AS [SALES_REP], brands.brand_name [BRAND_NAME]
FROM sales.orders
JOIN sales.customers
ON orders.customer_id = customers.customer_id
JOIN sales.order_items
ON orders.order_id = order_items.order_id
JOIN production.products
ON order_items.product_id = products.product_id
JOIN production.categories
ON products.category_id = categories.category_id
JOIN sales.stores
ON orders.store_id = stores.store_id
JOIN sales.staffs
ON orders.staff_id = staffs.staff_id
JOIN production.brands
ON products.brand_id = brands.brand_id

GROUP BY
orders.order_id, CONCAT(customers.first_name,' ', customers.last_name), stores.city, stores.state, customers.city, customers.state,
CONCAT(staffs.FIRST_NAME, ' ', staffs.LAST_NAME), brands.brand_name,
orders.order_date, products.product_name,
categories.category_name, stores.store_name, order_items.list_price,
order_items.quantity

```
- MS Excel.
- Tableau.

## STEPS
**1. Data collection:**  We used SQL to perform data extraction, transformation and Load (ETL). I wrote SQL queries to extract the required data for my analysis.

**2. Data cleaning with MS Excel:** Connected excel to the database and loaded the extracted data to excel where I cleaned the data this entails removing points in the data such as missing data, duplicates etc. which could impede our analysis.

**3. Data analysis and Visualization:** utilized excel pivot tables to create dashboard showing these Key performance Indicators (KPIs).

**4. Data interpretation:** In this final step, we described how the various KPIs impacted on the business performance or the objectives of the project.

## INSIGHTS
-	We notice a 42% rise in revenue in the year 2017 and a 47% decrease in the year 2018.
-	In the year 2018, we see a sharp rise in sales between Feb – April followed by a decline in May through to December.
-	Baldwin appears to be the most profitable region for the business accounting for about 68% of total revenue.





