# Olist Customer Purchasing Analysis

## Overview

This project analyzes customer purchasing behavior using the Olist Brazilian E-Commerce Public Dataset.

The analysis focuses on customer retention, customer value, and the relationship between delivery performance and customer satisfaction.

The project uses R and Quarto and combines exploratory data analysis, statistical testing, data visualization, and predictive modelling.

## Research Questions

### 1. Repeat Purchasing

**How common are repeat purchases, and what characteristics of the first purchase are associated with customers returning?**

The analysis examines:

- how common repeat purchases are
- the time between the first and second order
- differences between repeat and non-repeat customers
- first-order product categories and repeat purchasing
- whether repeat purchases can be predicted from information available at the first purchase

### 2. Customer Value

**Which customers are most valuable, and can high-value customers be identified using information from their first purchase?**

Customers in the top 10% of total spending are classified as high-value customers.

The analysis examines:

- the distribution of customer spending
- revenue concentration among high-value customers
- differences in customer value across first-order categories
- whether high-value customers can be identified using first-purchase characteristics

### 3. Delivery Experience and Customer Satisfaction

**How is delivery performance associated with customer satisfaction and repeat purchasing?**

The analysis examines:

- delivery time
- late delivery rates
- the relationship between delivery performance and review scores
- differences in repeat-purchase rates between on-time and late deliveries
- statistical evidence for the observed relationships

## Key Findings

### Repeat Purchasing

Repeat purchasing is relatively uncommon in the dataset.

Customers with an observed repeat purchase generally have higher first-order values and different purchasing characteristics compared with customers without an observed repeat purchase.

The analysis also examines differences in repeat-purchase rates across first-order product categories.

A logistic regression model is used to evaluate whether repeat purchasing can be predicted using information available from the first order.

### Customer Value

Customer spending is highly concentrated among a relatively small group of customers.

The top 10% of customers by total spending account for approximately **41.4% of total customer spending**, while representing approximately **10% of customers**.

High-value customers have substantially higher total spending than other customers.

The rate of high-value customers also varies across first-order product categories. Categories with fewer than 100 customers are excluded from the category comparison to reduce the influence of very small groups.

A logistic regression model is used to evaluate whether high-value customers can be identified using information available from their first purchase.

### Delivery Experience

Delivery performance is strongly associated with customer satisfaction.

The average review score was approximately:

- **4.29** for on-time deliveries
- **2.56** for late deliveries

The difference in review scores was statistically significant according to a Wilcoxon rank-sum test.

Late deliveries were also associated with a lower repeat-purchase rate:

- **2.19%** for on-time deliveries
- **1.55%** for late deliveries

A chi-squared test indicated a statistically significant association between delivery status and repeat purchasing.

These results describe associations and should not be interpreted as evidence of causal effects.

## Data

The project uses the **Olist Brazilian E-Commerce Public Dataset**.

The dataset contains information about customers, orders, order items, products, reviews, sellers, payments, and delivery dates.

The analysis uses `customer_unique_id` as the main customer identifier. Orders are linked to customer records using `customer_id`, after which customers are grouped using `customer_unique_id` to identify individual customers across orders.

The raw dataset is not included in this repository.

Information about the dataset and instructions for obtaining the raw data are provided in the `data/README.md` file.

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

For the customer-value analysis, orders are aggregated at the customer level. Total spending, number of orders, number of items, average order value, and other customer-level measures are calculated.

Customers in the top 10% of total spending are classified as high-value customers.

## Methods

The project uses:

- descriptive statistics
- customer-level aggregation
- grouped comparisons
- data visualization with `ggplot2`
- chi-squared tests
- Wilcoxon rank-sum tests
- logistic regression
- ROC analysis
- AUC

The predictive models use information available from the first purchase to investigate whether later customer outcomes can be identified from initial purchasing characteristics.

## Tools

- R
- Quarto
- tidyverse
- dplyr
- ggplot2
- pROC

## Project Files

### `olist_analysis.qmd`

The original Quarto source file containing the analysis code and written interpretation.

### `olist_analysis.md`

The rendered Markdown version of the complete analysis, including results, tables, visualizations, and interpretations.

### `olist_analysis_files/`

Supporting files generated by Quarto for the rendered analysis.

### `data/`

Contains information and instructions related to the dataset. The raw dataset is not included in the repository.

## Full Analysis

The complete rendered analysis is available here:

[View the full analysis](olist_analysis.md)

The original Quarto source code is available here:

[View the Quarto source](olist_analysis.qmd)

## Conclusion

The analysis provides three perspectives on customer behavior: retention, customer value, and delivery experience.

Repeat purchasing is relatively uncommon, while customer spending is strongly concentrated among high-value customers. The top 10% of customers account for approximately 41.4% of total customer spending.

Delivery performance shows a particularly strong relationship with customer satisfaction. Late deliveries are associated with substantially lower review scores and a lower repeat-purchase rate.

Overall, the project demonstrates how customer-level e-commerce data can be used to combine exploratory analysis, statistical testing, visualization, and predictive modelling to investigate customer purchasing behavior.
