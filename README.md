# LITA_Class_Documentation_and _Projects
This is where I documented my journey while learning Data Analysis with the Incubator Hub. Focusing on tools like Excel, (For Data Cleaning, Data Analysis, Data Visualization), SQL, (Structured Query Language for querying Data), power Bi (for data visualization), and Github, ( for Portfolio Building). I will update this repository with notes, exercises, and projects as I progress.


---

### Table of Contents

[Introduction](#introduction)

[Tools and Skills](#tools-and-skills).

[Excel Learning](#excel-learning).

[Data Cleaning and Manipulation](#data-cleaning-and-manipulation).

[Formulas and Functions](#formulas-and-functions)

[Pivot Tables and Charts](#pivot-tables-and-charts)

[SQL Learning](#sql-learning).

[Projects](#projects).

[Resources](#resources).


---

### Introduction

This repository serves as a log of my learning process in data analysis, including key takeaways, exercises, and project work. The primary tools I am focusing on at this stage are Microsoft Excel, SQL, and Power BI.


---

### Tools and Skills

- Microsoft Excel: [Download Here](https://www.microsoft.com)
  1. Data cleaning
  2. Sorting
  3. Pivot Tables
  4. Data Visualization

- SQL:
  1. Querying Databases
  2. Filtering Data
  3. Joining Tables
  4. Aggregating Data


---

### Excel Learning

#### Basics of Excel

- Data entry, formatting cells, and basic navigation.

- Types of data (numerical, text, dates) and their significance in analysis.


#### Data Cleaning and Manipulation

- Sorting and filtering data.

- Removing duplicates and handling missing data.

- Using Text to Columns and Data Validation.

- Data cleaning and formating.


#### Formulas and Functions

Basic functions like:
```Excel
SUM()
AVERAGE()
COUNT()
```

Logical functions:
```Excel
IF()
AND()
OR()
```

Lookup functions:
```Excel
VLOOKUP()
HLOOKUP()
INDEX()
MATCH()
```

### Data Exercise

![Excel Functions Exercise](https://github.com/user-attachments/assets/a68ad3fe-c149-4019-931d-70bfca1c0ed0)

#### Pivot Tables and Charts

- Creating Pivot Tables for summarizing large datasets.

- Building dynamic charts and graphs to visualize trends.


---

### SQL Learning

#### SQL Basics

Introduction to SQL syntax and statements.

Understanding databases and tables.

Using SELECT statements to extract data.


#### Data Querying

Filtering data using WHERE clauses.

Sorting data with ORDER BY.

Limiting data with LIMIT.


#### Joining Tables

Introduction to different joins: INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL OUTER JOIN.

Combining data from multiple tables to answer questions.


#### Aggregations and Functions

Using aggregate functions: COUNT(), SUM(), AVG(), MIN(), MAX().

Grouping data with GROUP BY.


---
### Projects

### Sales Performance Analysis For A Retail Store

#### Project Overview

The objective of this project is to analyze the sales performance of a retail store using a combination of Excel, SQL, and Power BI. By leveraging these tools, we aim to gain insights into sales trends, top-performing products, regional performance, and customer purchasing behavior. The final output will be an interactive Power BI dashboard that provides a comprehensive view of these findings.

#### Tools Used

- Excel: For initial data exploration and summarization.

- SQL: For extracting detailed insights from the dataset.

- Power BI: For creating interactive visualizations.


#### Project Details


#### Excel Analysis

The initial data exploration and analysis were conducted using Microsoft Excel:

Pivot Tables: Created pivot tables to summarize total sales by product, region, and month, allowing a high-level overview of key metrics.

#### Formulas and Metrics:

Used formulas to calculate the average sales per product using AVERAGE() and the total revenue per region using SUM().

Generated additional insights such as identifying seasonal sales trends.


#### Reports Created:

Sales summary report by month to understand trends.

Product performance report highlighting top and bottom performers.

Revenue distribution report by region for comparative analysis.


#### SQL Analysis

The dataset was imported into an SQL Server environment to enable deeper analysis. Key SQL queries were crafted to extract the following insights:

##### THE TOTAL NUMBER OF CUSTOMERS FROM EACH REGION

```SELECT region, COUNT (CustomerName) as Number_of_Customers
FROM CUSTOMERSDATA_LITA_PROJECT
group by Region
Order by Region
SELECT * FROM CUSTOMERSDATA_LITA_PROJECT
```

##### THE MOST POPULAR SUBSCRIPTION TYPE BY THE NUMBER OF CUSTOMERS

select top 1(SubscriptionType),
COUNT (CustomerID) as TOTAL_CUSTOMERS
from CUSTOMERSDATA_LITA_PROJECT
group by SubscriptionType
order by TOTAL_CUSTOMERS desc

##### CUSTOMERS WHO CANCELLED THEIR SUBSCRIPTION WITHIN 6 MONTHS

SELECT * FROM CUSTOMERSDATA_LITA_PROJECT
SELECT CustomerID, CustomerName, SubscriptionStart, SubscriptionEnd, Region
from CUSTOMERSDATA_LITA_PROJECT
where canceled = 'TRUE'
and datediff(month, subscriptionEnd, SubscriptionStart) <= 6;

##### THE AVERAGE SUBSCRIPTION DURATION FOR ALL CUSTOMERS

select  AVG(DATEDIFF(day, SubscriptionStart, SubscriptionEnd)) 
as avg_subscription_duration
from CUSTOMERSDATA_LITA_PROJECT

##### CUSTOMERS WITH SUBCRIPTIONS LONGER THAN 12 MONTHS

SELECT CustomerID, CustomerName, SubscriptionStart, SubscriptionEnd
from CUSTOMERSDATA_LITA_PROJECT
where datediff(month, subscriptionEnd, SubscriptionStart) > 12

##### CALCULTATE TOTAL REVENUE BY SUBSCRIPTION TYPE

select SubscriptionType,  sum (revenue) as Total_Revenue
from CUSTOMERSDATA_LITA_PROJECT
group by Subscriptiontype
select * from CUSTOMERSDATA_LITA_PROJECT

#### THE TOP THREE REGIONS BY SUBSCRIPTION CANCELLATIONS

SELECT REGION, COUNT(CustomerID) As total_cancellations
from CUSTOMERSDATA_LITA_PROJECT
where canceled = 'TRUE'
group by region
order by total_cancellations

##### THE TOTAL NUMBER OF ACTIVE AND CANCELLED SUBSCRIPTIONS
SELECT canceled,
count (CustomerID) AS Total_Subscriptions
from CUSTOMERSDATA_LITA_PROJECT
group by canceled


![image](https://github.com/user-attachments/assets/311475ac-fdf7-4edc-8200-bede4b0da3cb)



#### Power BI Dashboard

The insights obtained from Excel and SQL were visualized using Power BI. The dashboard includes:

#### Sales Overview:

A line chart displaying monthly sales trends for the current year.

A card showing total revenue and key performance indicators (KPIs) such as average monthly revenue.


#### Top-Performing Products:

A bar chart highlighting the highest-selling products by total sales.

A table displaying products with no recent sales.

#### Regional Performance:

A map visualization showcasing sales distribution by region.

A pie chart depicting the percentage contribution of each region to the overall sales.

#### Customer Analysis:

A table showing the top 5 customers by total purchase amount.


#### Conclusion

This project demonstrated the power of using Excel for preliminary data exploration, SQL for detailed data extraction, and Power BI for comprehensive visualization. The combined analysis provided actionable insights into sales performance, helping to identify growth opportunities and optimize decision-making strategies for the retail store.

#### Repository Contents

Excel Reports: Files containing the pivot tables and sales analysis.

SQL Queries: Scripts used for data extraction.

Power BI Dashboard: Interactive dashboard file and screenshots.

Documentation: This report detailing the project workflow and insights.



#### Customer Segmentation for a Subscription Service

#### Project Overview

This project focuses on analyzing customer data for a subscription service to identify key customer segments and trends. The analysis aims to provide insights into customer behavior, subscription patterns, and trends related to subscription cancellations and renewals. The final output is a Power BI dashboard that visualizes these findings for better business decision-making.

#### Objectives

- Analyze customer data to find subscription patterns and trends.

- Identify popular subscription types and average subscription duration.

- Track subscription cancellations and renewal trends.

- Create a Power BI dashboard to visualize key insights and enable interactive analysis.

#### Tools Used

Microsoft Excel: For initial data exploration and pivot table analysis.

SQL: To extract key insights and perform more advanced data queries.

Power BI: To create an interactive dashboard for data visualization

#### Step-by-Step Process

1. Excel Analysis

Tasks Performed:

Pivot Tables: Used pivot tables to analyze customer data and identify patterns in subscriptions.

Average Subscription Duration: Calculated the average duration of customer subscriptions.

Most Popular Subscription Types: Identified the most subscribed-to types and any trends related to them.

Additional Reports: Created additional reports highlighting customer demographics, subscription changes over time, and common renewal patterns.


- Kaggle Datasets - Free datasets to practice data analysis.


---

## Data Analysis
```SQL
SELECT * FROM TABLE1
WHERE CONDITION = TRUE
```
---
**data visualization**
*SQL*

