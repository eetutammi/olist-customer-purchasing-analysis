# Olist Customer Purchasing Behavior Analysis

## Overview

This project analyzes customer purchasing behavior using the Olist Brazilian E-Commerce Public Dataset.

The analysis focuses on customer retention, customer value, and the relationship between delivery performance and customer satisfaction. The goal is to identify patterns that can help explain why some customers return, which customers generate the most value, and how the delivery experience relates to customer behavior.

The analysis is conducted in R using Quarto and includes data preparation, exploratory analysis, statistical testing, visualization, and logistic regression.

## Research Questions

### 1. Repeat Purchasing

**How common are repeat purchases, and what characteristics of the first purchase are associated with customers returning?**

The analysis examines:

- the frequency of repeat purchases
- the time between the first and second order
- differences between repeat and non-repeat customers
- the relationship between first-order product categories and repeat purchasing
- whether repeat purchases can be predicted using information available from the first order

### 2. Customer Value

**Which customers are most valuable, and can high-value customers be identified using information from their first purchase?**

The analysis examines:

- the distribution of customer spending
- the concentration of revenue among high-value customers
- differences in customer value across first-order categories
- whether high-value customers can be identified using characteristics of their first purchase

Customers in the top 10% of total customer spending are classified as high-value customers.

### 3. Delivery Experience

**How is delivery performance associated with customer satisfaction and repeat purchasing?**

The analysis examines:

- delivery time
- late delivery rates
- the relationship between delivery performance and review scores
- differences in repeat-purchase rates between on-time and late deliveries
- statistical evidence for the observed relationships

## Data

The project uses the **Olist Brazilian E-Commerce Public Dataset**, which contains information about orders, customers, products, order items, reviews, payments, sellers, and delivery dates.

The analysis uses `customer_unique_id` as the main customer identifier. Orders are linked to customer records using `customer_id`, after which customers are grouped using `customer_unique_id` to identify individual customers across orders.

## Data Preparation

Orders are sorted by purchase timestamp for each customer so that the first and second orders can be identified.

A repeat purchase is defined as a second order occurring at least one day after the first order. Customers without a qualifying second order are classified as non-repeat customers.

First-order characteristics include:

- order value
- number of items
- freight value
- delivery time
- delivery status
- product category
- review score

These variables are used to investigate customer retention and customer satisfaction.

For the customer-value analysis, orders are aggregated at the customer level. Total spending, number of orders, number of items, average order value, and other customer-level measures are calculated.

## Methods

The project uses several analytical methods:

- descriptive statistics
- customer-level aggregation
- grouped comparisons
- data visualization with `ggplot2`
- chi-squared tests
- Wilcoxon rank-sum tests
- logistic regression
- ROC analysis and AUC

For predictive modelling, the data is divided into training and test sets. Logistic regression is used to evaluate whether customer behavior can be predicted using information available from the first purchase.

## Key Findings

### Repeat Purchasing

Repeat purchasing is relatively uncommon in the dataset. The analysis distinguishes customers with an observed second purchase from customers without an observed qualifying repeat purchase.

The analysis also examines whether characteristics of the first purchase, such as order value, number of items, freight value, and product category, are associated with repeat purchasing.

### Customer Value

Customer spending is highly concentrated.

The top 10% of customers by total spending account for approximately **41.4% of total customer spending**, despite representing only **10% of customers**.

High-value customers have substantially higher total spending than other customers. Differences in high-value customer rates are also observed across first-order product categories.

The logistic regression model shows that first-order information, particularly order value, can be used to distinguish high-value customers with high predictive performance.

### Delivery Experience

Delivery performance is strongly associated with customer satisfaction.

The average review score was approximately:

- **4.29** for on-time deliveries
- **2.56** for late deliveries

The difference in review scores was statistically significant according to a Wilcoxon rank-sum test.

Late deliveries were also associated with a lower repeat-purchase rate:

- **2.19%** for on-time deliveries
- **1.55%** for late deliveries

The chi-squared test indicated a statistically significant association between delivery status and repeat purchasing.

These results should be interpreted as associations rather than causal effects.
