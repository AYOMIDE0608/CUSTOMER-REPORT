# CUSTOMER REPORT
An analysis was done on a data containing customer data for a subscription service to identify  segments and trends. I was able to report about subscription types,  and identify key trends in cancellations and renewals. A Power BI  dashboard that presents my analysis can also be found here. 


### PROJECT TITLE: CUSTOMER SEGMENTATION REPORT


### PROJECT OVERVIEW
This Data Analysis project aims to analyze customer data for a subscription service  for three years, by eploring this data set,I was able to identify 
segments and trends, understand customer behavior, track subscription types, and identify key trends in cancellations and renewals,
to enable me tell compelling stories about the data and help the business make informed decisions.
An interactive Power BI dashboard that presents my analysis is also found here.


### DATA SOURCES
The primary source of Data used here is an Excel file,which i had to convert to a csv file for me to be able to import into SQL. The file
was provided by INCUBATOR HUB.


### TOOLS USED
- Microsoft Excel [Download Here](https://www.microsoft.com)
  1. For Data cleaning 
  2. For Analysis
  3. For Visualiation
- SQL - Structured Query Language [Download Here](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
  1. For Querying of Data
- Power BI [Download Here](https://www.microsoft.com/en-us/download/details.aspx?id=58494)
  1. For Data Visualiation
 

 ### DATA CLEANING AND PREPARATION  
 In the initial phase of the Data Cleaning and preparations,I performed the following action;
 1. Data loading and inspection
 2. Conversion of dataset to tables
 3. Removal of duplicates 
 4. Data cleaning and formatting

 ### EXPLORATORY DATA ANALYSIS
 EDA involved the exploring of the Data to answer some questions about the Data such as;
  - What are the customer behavior
  - What are the track subscription types
  - What arethe key trends in cancellations and renewals.
  - What are the varous segments and trends

### DATA ANALYSIS
This is where I include some basic functions used in Excel, basic lines of code and queries used in SQL and some 
of the DAX epressions used in POWER BI during my analysis.
1. Excel
   1. Total subscription duration
   ```Excel
      =F2-E2 
   ```
   2. Average subscription duration
      ```Excel
      =AVERAGE([@[Total Subscription Duration]])
      ```
   3. Basic Subscription Type
      ```Excel
        =COUNTIF(D:D,"basic")
      ```
   4. Standard subscription type
      ```Excel
      =COUNTIF(D:D,"standard")
      ```
   5. Premium subscription type
     ```Excel
     =COUNTIF(D:D,"premium")
     ```
    
2. SQL;
    1. Customers who cancelled within 6 months
     ```SQL
     SELECT CUSTOMERNAME
     FROM[dbo].[LITA Capstone Dataset 2]
     WHERE CANCELED =1
     AND DATEDIFF(MONTH,SUBSCRIPTIONSTART,SUBSCRIPTIONEND)<=6
     ```
    2. total number of customers from each region
    ```SQL
    SELECT REGION,COUNT(CustomerID) AS NUMBEROFCUSTOMERS
    FROM[dbo].[LITA Capstone Dataset 2]
     GROUP BY REGION
    ```
   3. Most popular subscripption type by the number of customers
    ```SQL
   SELECT TOP(1) SUBSCRIPTIONTYPE,COUNT(CUSTOMERID)AS MOSTPOPULAR
   FROM [dbo].[LITA Capstone Dataset 2]
   GROUP BY SUBSCRIPTIONTYPE
   ORDER BY MOSTPOPULAR DESC
   ```
   4. Average subscription duration for all customers
     ```SQL
    SELECT AVG(DATEDIFF(DAY,SUBSCRIPTIONSTART,SUBSCRIPTIONEND))
    AS AVERAGESUBSCRIPTIONDURATION
    FROM [dbo].[LITA Capstone Dataset 2]
   ```
   5. customers with subscription longer than 12 months
     ```SQL
     SELECT CUSTOMERNAME
     FROM[dbo].[LITA Capstone Dataset 2]
     WHERE DATEDIFF(MONTH,SUBSCRIPTIONSTART,SUBSCRIPTIONEND)>12
     ```
   6. total revenue by subscription type
    ```SQL
    SELECT SUBSCRIPTIONTYPE,SUM(REVENUE)
    AS TOTALREVENUE FROM[dbo].[LITA Capstone Dataset 2]
    GROUP BY SubscriptionType
    ```
    7. top 3 regions by subscriptions cancallations
      ```SQL
     SELECT TOP 3 Region,
     count (CUSTOMERID) AS TOTALCANCELED
     FROM [dbo].[LITA Capstone Dataset 2]
     WHERE CANCELED=1
     GROUP BY REGION
     ORDER BY TOTALCANCELED DESC
     ```
    8. total number of active and cancelled subscriptions
    ```SQL
    SELECT 
    SUM(CASE WHEN CANCELED=0
    THEN 1 ELSE 0 END)
    AS ACTIVESUBSCRIPTIONS,
    SUM(CASE WHEN CANCELED=1
    THEN 1 ELSE 0 END)
    AS CANCELEDSUBSCRIPTIONS
    FROM[dbo].[LITA Capstone Dataset 2]
  ```



      


     



   
