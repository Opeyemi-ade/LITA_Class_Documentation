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

- Power BI:
  1. Data Import And Transformation
  2. Data Modeling
  3. Data Visualization
  4. DAX Functions
  5. Report And Dashboard Creation

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

### Power BI Learning

#### Data Import and Transformation:
Understanding how to connect to various data sources (Excel, SQL databases, etc.), import data, and clean or transform it using Power Query Editor.

#### Data Modeling
Learning to create relationships between different data tables, use DAX (Data Analysis Expressions) for creating calculated columns and measures, and understanding the concept of data hierarchy.

#### Visualization
Developing skills to build interactive dashboards with different chart types such as bar charts, line charts, pie charts, and custom visuals. This includes using slicers, filters, and drill-throughs to enhance the user experience.

---

### Projects

---

### Sales Performance Analysis For A Retail Store

---
### Data Sources
---
The primary source of Data used here is the Sales Data provided by the Sales department of the company. The Data given is table having an array of columns like OrderID, Customer Id, Product, Region, OrderDate, Quantity Sold and UnitPrice


#### Project Overview

The objective of this project is to analyze the sales performance of a retail store using a combination of Excel, SQL, and Power BI. By leveraging these tools, we aim to gain insights into sales trends, top-performing products, regional performance, and customer purchasing behavior. The final output will be an interactive Power BI dashboard that provides a comprehensive view of these findings.

#### Tools Used

- Excel: For initial data exploration and summarization.

- SQL: For extracting detailed insights from the dataset.

- Power BI: For creating interactive visualizations.

- Github for portfolio building.


#### Project Details
---

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

![Sales Performance Report-Excel](https://github.com/user-attachments/assets/6efd1e55-43f0-46af-b569-e7754debed2b)


#### SQL Analysis

The dataset was imported into an SQL Server environment to enable deeper analysis. Key SQL queries were crafted to extract the following insights:


##### TOTAL SALES FOR EACH PRODUCT CATEGORY
	
```SELECT 	
    Product AS ProductCategory,  	
    SUM(SALES_REVENUE) AS TotalSales	
FROM 	
    SALESDATA_LITA_PROJECT	
GROUP BY 	
    Product	
ORDER BY 	
    TotalSales DESC;
```	
	
	
##### NUMBEERS OF SALES TRANSACTIONS IN EACH REGION
	
 ```SELECT 
    REGION, 	
    COUNT(OrderID) AS NumberOfTransactions	
FROM 	
    SALESDATA_LITA_PROJECT	
GROUP BY 	
    Region	
ORDER BY 	
    NumberOfTransactions DESC;	
```	
	
	
##### HIGHEST-SELLING PRODUCT BY TOTAL SALES VALUE
	
 ```SELECT Top 1
	Product, SUM(Quantity * UnitPrice) AS TotalSales
FROM 	
	SALESDATA_LITA_PROJECT
GROUP BY	
	Product
ORDER BY	
	TotalSales DESC;
```
	
	
 ##### TOTAL REVENUE PER PRODUCT
 
  ```SELECT 
    Product, 	
    SUM(Quantity * UnitPrice) AS TotalRevenue	
FROM 	
    SALESDATA_LITA_PROJECT	
GROUP BY 	
    Product	
ORDER BY 	
    TotalRevenue DESC;	
```
	

##### MONTHLY SALES TOTAL FOR THE CURRENT YEAR
	
 ```SELECT 
    MONTH(OrderDate) AS Month, 	
    SUM(Quantity * UnitPrice) AS MonthlySales	
FROM 	
    SALESDATA_LITA_PROJECT	
WHERE 	
    YEAR(OrderDate) = YEAR(GETDATE())	
GROUP BY 	
    MONTH(OrderDate)	
ORDER BY 	
    Month;	
```
	
	
 ##### TOP 5 CUSTOMERS BY TOTAL PURCHASE AMOUNT

```SELECT TOP 5
    CUSTOMER_ID, 	
    SUM(Quantity * UnitPrice) AS TotalPurchaseAmount	
FROM 	
    SALESDATA_LITA_PROJECT 	
GROUP BY 	
    CUSTOMER_ID	
ORDER BY 	
    TotalPurchaseAmount DESC;	
```

	
 ##### PERCENTAGE OF TOTAL SALES CONTRIBUTED BY EACH REGION
	
 ```SELECT 
    Region, 	
    SUM(CAST(Quantity AS DECIMAL(10, 2)) * CAST(UnitPrice AS DECIMAL(10, 2))) AS TotalSales, 	
    (SUM(CAST(Quantity AS DECIMAL(10, 2)) * CAST(UnitPrice AS DECIMAL(10, 2))) / 	
        (SELECT SUM(CAST(Quantity AS DECIMAL(10, 2)) * CAST(UnitPrice AS DECIMAL(10, 2))) 	
         FROM SALESDATA_LITA_PROJECT) * 100) AS SalesPercentage	
FROM 	
    SALESDATA_LITA_PROJECT	
GROUP BY 	
    Region	
ORDER BY 	
    SalesPercentage DESC;	
```
	
	
##### PRODUCTS WITH NO SALES IN THE LAST QUARTER

```SELECT 
    Product	
FROM 	
    SALESDATA_LITA_PROJECT 	
WHERE 	
    NOT EXISTS (	
        SELECT 1	
        FROM SALESDATA_LITA_PROJECT AS SalesLastQuarter	
        WHERE 	
            SalesLastQuarter.Product = SALESDATA_LITA_PROJECT.Product 	
            AND OrderDate >= DATEADD(QUARTER, -1, GETDATE())	
    )	
GROUP BY 	
    Product;
```

![image](https://github.com/user-attachments/assets/54687a03-dae4-425f-a26b-a1f152bec6c2)



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


##### THE TOTAL NUMBER OF CUSTOMERS FROM EACH REGION

```SELECT region, COUNT (CustomerName) as Number_of_Customers
FROM CUSTOMERSDATA_LITA_PROJECT
group by Region
Order by Region
SELECT * FROM CUSTOMERSDATA_LITA_PROJECT
```

##### THE MOST POPULAR SUBSCRIPTION TYPE BY THE NUMBER OF CUSTOMERS

```select top 1(SubscriptionType),
COUNT (CustomerID) as TOTAL_CUSTOMERS
from CUSTOMERSDATA_LITA_PROJECT
group by SubscriptionType
order by TOTAL_CUSTOMERS desc
```

##### CUSTOMERS WHO CANCELLED THEIR SUBSCRIPTION WITHIN 6 MONTHS

```SELECT * FROM CUSTOMERSDATA_LITA_PROJECT
SELECT CustomerID, CustomerName, SubscriptionStart, SubscriptionEnd, Region
from CUSTOMERSDATA_LITA_PROJECT
where canceled = 'TRUE'
and datediff(month, subscriptionEnd, SubscriptionStart) <= 6;
```

##### THE AVERAGE SUBSCRIPTION DURATION FOR ALL CUSTOMERS

```select  AVG(DATEDIFF(day, SubscriptionStart, SubscriptionEnd)) 
as avg_subscription_duration
from CUSTOMERSDATA_LITA_PROJECT
```

##### CUSTOMERS WITH SUBCRIPTIONS LONGER THAN 12 MONTHS

```SELECT CustomerID, CustomerName, SubscriptionStart, SubscriptionEnd
from CUSTOMERSDATA_LITA_PROJECT
where datediff(month, subscriptionEnd, SubscriptionStart) > 12
```

##### CALCULTATE TOTAL REVENUE BY SUBSCRIPTION TYPE

```select SubscriptionType,  sum (revenue) as Total_Revenue
from CUSTOMERSDATA_LITA_PROJECT
group by Subscriptiontype
select * from CUSTOMERSDATA_LITA_PROJECT
```

#### THE TOP THREE REGIONS BY SUBSCRIPTION CANCELLATIONS

```SELECT REGION, COUNT(CustomerID) As total_cancellations
from CUSTOMERSDATA_LITA_PROJECT
where canceled = 'TRUE'
group by region
order by total_cancellations
```

##### THE TOTAL NUMBER OF ACTIVE AND CANCELLED SUBSCRIPTIONS
```SELECT canceled,
count (CustomerID) AS Total_Subscriptions
from CUSTOMERSDATA_LITA_PROJECT
group by canceled
```

#### Power BI Dashboard

Dashboard Features:

Customer Segmentation: A visualization displaying customer distribution by region and subscription type.

Subscription Trends: Line charts showing subscription trends over time, including new sign-ups and cancellations.

Cancellation Analysis: A bar chart highlighting the top regions with the highest cancellation rates.

Average Subscription Duration: Visuals illustrating average subscription periods segmented by subscription type.

Interactive Slicers: Slicers for filtering data by region, subscription type, and status (active/canceled).


Dashboard Insights:

The most popular subscription types and regions with high customer counts.

Key regions with significant numbers of cancellations.

A visual comparison of active vs. canceled subscriptions to highlight retention challenges.

The average subscription duration across different customer segments.


Final Deliverable

The final product is an interactive Power BI dashboard that showcases:

Customer segmentation by region and subscription type.

Trends in subscription cancellations and renewals.

Average subscription durations and total revenue breakdowns.

The ability to interact with data using slicers for deeper analysis.


Conclusion

This project provided valuable insights into customer behavior, popular subscription types, and trends related to subscription cancellations and renewals. The Power BI dashboard offers a user-friendly platform for stakeholders to interact with data and make informed decisions based on real-time analysis.

Repository Structure

Excel Reports: Contains the Excel file with pivot tables and summary analysis.

SQL Queries: Includes a .sql file with all queries used for data extraction and analysis.

Power BI Dashboard: A .pbix file containing the Power BI dashboard for interactive data visualization.

Documentation: This project report and a README.md file outlining the project scope and instructions for replicating the analysis.

Future Enhancements

Implement machine learning models to predict customer churn.

Incorporate additional customer demographics for deeper segmentation analysis.

Automate data extraction using SQL scripts to update the dashboard dynamically.
