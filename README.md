# Pizza Restaurant Sales
Data Analyst Project which covers analyzing , cleaning , modeling and visualizing data

## Tools
1. Sql Server

2. Power Bi


## About Data

This pizza sales dataset From kaggle make up 12 relevant features:

**order_id**: Unique identifier for each order placed by a table

**order_details_id**: Unique identifier for each pizza placed within each order (pizzas of the same type and size are kept in the same row, and the quantity increases)

**pizza_id**: Unique key identifier that ties the pizza ordered to its details, like size and price

**quantity**: Quantity ordered for each pizza of the same type and size

**order_date**: Date the order was placed (entered into the system prior to cooking & serving)

**order_time**: Time the order was placed (entered into the system prior to cooking & serving)

**unit_price**: Price of the pizza in USD

**total_price**: unit_price * quantity

**pizza_size**: Size of the pizza (Small, Medium, Large, X Large, or XX Large)

**pizza_type**: Unique key identifier that ties the pizza ordered to its details, like size and price

**pizza_ingredients**: ingredients used in the pizza as shown in the menu (they all include Mozzarella Cheese, even if not specified; and they all include Tomato Sauce, unless another sauce is specified)

**pizza_name**: Name of the pizza as shown in the menu

## Project Steps
1.Get Data to Sql Server

2.Develop the Sql Query

3.Cleaning Data

4.Analyzing Data

5.Connect Power Bi to The Database

6.Cleaning and Transform Data

7.Create some measures by DAX

7.built interactive dashboard

## SQL Queries for Pizza Sales Analysis

1. **Total Revenue**:
```sql
SELECT CAST(SUM(total_price) AS decimal(10, 2)) AS 'Total Revenue' FROM pizza_sales;
```
![image](https://github.com/Mustafamegahed20/Pizza-Dashboard/assets/61358936/3d13da54-ef5c-4186-be76-32b08baaf067)

2. **Average Order Value**:
```sql
SELECT CAST((SUM(total_price) / COUNT(DISTINCT order_id)) AS decimal(10, 2)) AS 'Average Order Value' FROM pizza_sales;
```
![image](https://github.com/Mustafamegahed20/Pizza-Dashboard/assets/61358936/873a91b9-158a-4150-8f7d-c3c2ead8c438)

3. **Total Pizzas Sold**:
```sql
SELECT SUM(quantity) AS 'Total Pizzas Sold' FROM pizza_sales;
```
![image](https://github.com/Mustafamegahed20/Pizza-Dashboard/assets/61358936/88acbdc3-770a-4691-8133-6ac90a88264e)

4. **Total Orders:**:
```sql
SELECT COUNT(DISTINCT order_id) AS 'Total Orders' FROM pizza_sales;
```
![image](https://github.com/Mustafamegahed20/Pizza-Dashboard/assets/61358936/0308c198-dac3-4e15-ab6c-88cdf68a58d5)

5. **Total Sales by Day**:
```sql
SELECT DATENAME(DW, order_date) AS "Order Day", SUM(total_price) AS total_Sales
FROM pizza_sales
GROUP BY DATENAME(DW, order_date)
```
![image](https://github.com/Mustafamegahed20/Pizza-Dashboard/assets/61358936/0d5a14b4-662d-44ef-b0f9-1eb047dc9895)

6.**Total Sales by Hour**:
```sql
SELECT DATEPART(HOUR, order_time) as order_hours, SUM(total_price) AS total_Sales
from pizza_sales
group by DATEPART(HOUR, order_time)
order by DATEPART(HOUR, order_time)
```
![image](https://github.com/Mustafamegahed20/Pizza-Dashboard/assets/61358936/22a182ef-3520-42b1-8c23-cfbac8d44ec8)

7.**Total Sales by Category**:
```sql
SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_category
```
![image](https://github.com/Mustafamegahed20/Pizza-Dashboard/assets/61358936/36c9e8f0-31ac-484f-8219-18b44d2e8b04)

8.**Total Sales by Pizza Size**:
```sql
SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_size
ORDER BY pizza_size
```
![image](https://github.com/Mustafamegahed20/Pizza-Dashboard/assets/61358936/fc62793b-95be-4ed4-b719-00f9982c4557)

9.**Top 5 Sales by Pizza Name**:
```sql
SELECT Top 5 pizza_name, SUM(total_price) AS Total_Sales
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Sales DESC
```
![image](https://github.com/Mustafamegahed20/Pizza-Dashboard/assets/61358936/fb864899-04fb-4043-bad5-ace15dc038b3)

10.**Less 5 Sales by Pizza Name**:
```sql
SELECT Top 5 pizza_name, SUM(total_price) AS Total_Sales
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Sales
```
![image](https://github.com/Mustafamegahed20/Pizza-Dashboard/assets/61358936/93dd4294-8af1-435c-b3af-6100d5b94bcf)

# DashBoard
## Page 1
![image](https://github.com/Mustafamegahed20/Pizza-Dashboard/assets/61358936/242fed4e-4553-4db2-b336-e9cb20da1d78)
## page 2
![image](https://github.com/Mustafamegahed20/Pizza-Dashboard/assets/61358936/92b38c37-c201-4bd6-ad6a-e3760341119c)



