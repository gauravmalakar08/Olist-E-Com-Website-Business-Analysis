# Olist E-Com Website Business Analysis

## Introduction

This project focuses on Exploratory Data Analysis (EDA) and visualization of a Brazilian e-commerce platform known as Olist, which connects merchants to customers seeking various products and services. The dataset, publicly available, offers Data Analysts an opportunity to delve into Brazil's e-commerce landscape, identifying avenues for growth and optimization and the business outcomes.

Undertaken as part of an online data analysis challenge, this project allowed me to leverage Power BI for comprehensive analysis. By using DAX functions and data modeling techniques, I aimed to uncover actionable insights that highlight potential growth opportunities and optimizations for the Olist platform, while also honing my skills in Power BI.

![Image A](https://github.com/user-attachments/assets/f8cbd047-1f4c-4a9c-a574-daebc7b5fc30)

## About the Data

The raw data was obtained from [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce). It contains 9 tables which are Olist_customers, Olist_geolocation, Olist_order_items, Olist_order_payments, Olist_order_reviews, Olist_orders, Olist_products, Olist_sellers, Product_category_name. These tables contain a wide range of information about each order, including the order date, product details, payment and shipping information, customer and seller IDs, customer reviews, sellers who list their products on Olist, and data on customer behavior and demographics. You can check out the data dictionary to describe the tables' contents.

## Data Schema
![Image B](https://github.com/user-attachments/assets/7cfe0d83-be66-4715-a3ee-89f6f9e8f1f3)

## Tools Used
* PowerBI
* Power Query Editor
* Microsoft SQL Server
* Excel

## Database

The database is stored in SQL format and can be accessed using SQL Server ( In this case it was Microsoft SQL Server) or any compatible database management system. The CSV files provided for each table were imported into the database, ensuring that the data was structured and ready for analysis. I

## Queries
Several SQL queries were performed on the database to extract meaningful insights and perform data analysis. The queries covered various aspects, such as calculating the average shipping cost and price per product category, checking for duplicate values, and retrieving data for visualization purposes.

## Table Relationships
To enable comprehensive analysis, the following relationships were established between the tables:

* orders_dataset with order_items_dataset using order_id
* order_reviews_dataset with orders_dataset using order_id
* order_items_dataset with products_dataset using product_id
* orders_dataset with order_reviews_dataset using order_id
* orders_dataset with customers_dataset using customer_id
* sellers_dataset with order_item_dataset using seller_id
* sellers_dataset with geolocation_dataset using zip_code_prefix
* order_customer_dataset with geolocation_dataset using zip_code_prefix 

## Metrics and KPIs
* Total Revenue
* Total Orders
* Total Sellers
* Total Products
* Avg Review Score
* Total Customers
* Avg Revenue Per Customer
* Response Rate
* Avg Freight Value
* Avg Order Value
* Total Categories
* Avg Product Price

## Calculations (DAX)
* Total Revenue = SUM('order_items_dataset'[total_value])
* Number of Sales = COUNT('orders_dataset'[order_id])
* Average Ticket = DIVIDE([Total Revenue], [Number of Sales])
* Number of Unique Customers = DISTINCTCOUNT('orders_dataset'[customer_id])
* On_time_delivery = IF( AND(orders_dataset[order_status] = "delivered", orders_dataset[order_delivered_customer_date]<= orders_dataset[order_estimated_delivery_date]), "On Time", 
  IF(AND(orders_dataset[order_status] = "delivered", orders_dataset[order_delivered_customer_date]> orders_dataset[order_estimated_delivery_date]), "Late", "Not Delivered"))
* Percentage_on_time = DIVIDE( CALCULATE(COUNTROWS(orders_dataset),orders_dataset[On_time_delivery] = "On time"),COUNTROWS(orders_dataset))
* Top Selling Products = TOPN(10, SUMMARIZE('order_items_dataset', 'products_dataset'[product_category_name]), [Total Revenue])
* Sales by State = SUMMARIZE('customers_dataset', 'customers_dataset'[customer_state], [Total Revenue])
* Sales Over Time = SUMMARIZE('orders_dataset', 'orders_dataset'[order_purchase_timestamp], [Total Revenue])

## Visualizations

