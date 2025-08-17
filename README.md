## Sales Insights Data Analysis Project
This project is a Power BI dashboard designed to analyze sales performance trends, identify revenue drivers, and provide actionable insights for decision-making.
### **Objective

1. Understand overall sales performance over time

2. Identify top-performing products, regions, and customers

3. Track KPIs such as revenue, growth rate, and profit margins

4. Provide data-driven insights to guide strategic decisions**

## Dashboard Features

1. Interactive sales trend charts by time period

2. Top products and regional performance analysis

3. Revenue and profit KPIs

4. Slicers and filters for deeper exploration

## Tools Used

Power BI for visualization and analysis

Excel / SQL (if applicable) for preprocessing

DAX for calculated measures

## How to Use

Download the .pbix file from this repository

Open it using Power BI Desktop (free from Microsoft Store)

Use slicers and filters to explore different views

## Key Insights

Delhi NCR contributed over 50% of total revenue

Top 5 customers account for a significant share of sales

Sales trend shows fluctuations between 2018–2020 with peaks in early 2018

Product portfolio is highly concentrated, with top products driving most revenue

### Data Analysis Using SQL

1. Show all customer records

    `SELECT * FROM customers;`

1. Show total number of customers

    `SELECT count(*) FROM customers;`

1. Show transactions for Chennai market (market code for chennai is Mark001

    `SELECT * FROM transactions where market_code='Mark001';`

1. Show distrinct product codes that were sold in chennai

    `SELECT distinct product_code FROM transactions where market_code='Mark001';`

1. Show transactions where currency is US dollars

    `SELECT * from transactions where currency="USD"`

1. Show transactions in 2020 join by date table

    `SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`

1. Show total revenue in year 2020,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`
	
1. Show total revenue in year 2020, January Month,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`

1. Show total revenue in year 2020 in Chennai

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark001";`


Data Analysis Using Power BI
============================

1. Formula used to create norm_sales_amount column

`= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD\r" then [sales_amount]*75 else [sales_amount], type any)`



