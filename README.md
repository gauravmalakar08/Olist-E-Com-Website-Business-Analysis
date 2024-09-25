# Olist E-Com Website Business Analysis

## Introduction

This project focuses on Exploratory Data Analysis (EDA) and visualization of a Brazilian e-commerce platform known as Olist, which connects merchants to customers seeking various products and services. The dataset, publicly available, offers Data Analysts an opportunity to delve into Brazil's e-commerce landscape, identifying avenues for growth and optimization and the business outcomes.

Undertaken as part of an online data analysis challenge, this project allowed me to leverage Power BI for comprehensive analysis. By using DAX functions and data modeling techniques, I aimed to uncover actionable insights that highlight potential growth opportunities and optimizations for the Olist platform, while also honing my skills in Power BI.



## About the Data

The raw data was obtained from [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce). It contains 9 tables which are Olist_customers, Olist_geolocation, Olist_order_items, Olist_order_payments, Olist_order_reviews, Olist_orders, Olist_products, Olist_sellers, Product_category_name. These tables contain a wide range of information about each order, including the order date, product details, payment and shipping information, customer and seller IDs, customer reviews, sellers who list their products on Olist, and data on customer behavior and demographics. You can check out the data dictionary to describe the tables' contents.

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
* order_items_dataset with products_dataset using product_id
* orders_dataset with order_reviews_dataset using order_id
* orders_dataset with customers_dataset using customer_id
