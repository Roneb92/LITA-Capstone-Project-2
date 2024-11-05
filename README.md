# LITA-Capstone-Customer-Data-Project-2
---
Documentation of The Incubator Hub LITA Capstone Project 2

### Project Overview
---
This project aims to identify the segment and trends for a subscription service.

### Data Source
The primary source of the data used was gotten from the Incubator Hub(Excel.csv)

### Tools Used
---
- Microsoft Excel for
  1. Data Cleaning
  2. Data Analysis
  3. Data Visualization
  
- SQL- Structured Query Language for Querying 
- Power BI for
  1. Visualization
  2. Interactive Dashboard

- GitHub for Portfolio Building
 
### Data Quality and Preparation
---
The following operations were performed at the initial phase of the Data
 1. Data loading and inspecrion
 2. Handling missing variables
 3. Data cleaning and formatting

### Project Objectives
---
The objectives of this project are
1. To track subscription types
2. To identify key trends in cancellations and renewal
3. To understand customer behaviour

### Data Analysis
---
Some of the basic codes, queries and DAX functions used during analysis are below

### Microsoft Excel Analysis
'''
- This is a preview of the Sales Data after it has been cleaned and transformed and some basic calculations were done to get Subscription Duration and Total Subscription
![Customer Clnd Data wt Clcltn](https://github.com/user-attachments/assets/8fa8e8c7-136d-447b-bc9e-97e05eeab744)


### Pivot Tables
'''
- Pivot Tables and Charts in excel were used for visualization to calculate Subscription type by number of customers, Subscription type by Durattion, Cancelled Subscription by Revenue e.t.c.
 ![Customer Pivot](https://github.com/user-attachments/assets/8f5b46c4-4b72-4aed-b78b-4aa02ed03614)

 ### SQL - Structured Query Language
 '''
 - Below are the queries used to analyse the Customer Data

   -1-----Retrieve the Total Number of Customers From Each Region----
 ```Select Region,
Count(CustomerID) As
Total_No_of_Customers
From [dbo].[CUSTOMER_DATA_PROJECT]
Group By Region
```
-2-----Find the most popular subscription type by the number of customers----

 ```Select
	SubscriptionType,Count(CustomerID)
	As No_Of_Customers From [dbo].[CUSTOMER_DATA_PROJECT]
	Group By SubscriptionType
```

-3-----Find customers who canceled their subscription within 6 months----

 ```Select
	CustomerName,Canceled,SubscriptionStart
	From[dbo].[CUSTOMER_DATA_PROJECT]
	Where Canceled =0 And
	Month(SubscriptionStart)
	Between 1 And 6
```

-4-----Calculate the Average Subscription Duration for all customers----
 ```	Select Count(CustomerID) 
	As All_Customers,Avg(DATEDIFF(DAY,SubscriptionStart,SubscriptionEnd)) 
	As Average_Subscription_Duration From[dbo].[CUSTOMER_DATA_PROJECT]
	Where SubscriptionEnd IS Not Null
```
-5-----Find customers with subscriptions longer than 12 months----

```	Select
	CustomerName,SubscriptionType,SubscriptionStart,SubscriptionEnd
	From [dbo].[CUSTOMER_DATA_PROJECT]
	Where Datediff(Month,SubscriptionStart,SubscriptionEnd)>=12
```
-6-----Calculate Total Revenue by subscription Type----

- ```	Select
	SubscriptionType,Sum(Revenue)
	As Total_Revenue
	From[dbo].[CUSTOMER_DATA_PROJECT]
	Group By SubscriptionType

-7-----Find the Top 3 Regions by subscription Cancellations----
	
 - ```Select Top 3 Region,Canceled
	From[dbo].[CUSTOMER_DATA_PROJECT]

```Select* From[dbo].[CUSTOMER_DATA_PROJECT]

-8   Find the Total Number of Active and Canceled Subscriptions----

	- Select
	Sum(Case When Canceled = 0 Then 1 Else 0 End)
	As ActiveSubscriptions,
	Sum(Case When Canceled = 1 Then 1 Else 0 End)
	As CanceledSubscriptions
	FROM [dbo].[CUSTOMER_DATA_PROJECT]
	Group By CustomerID

### Data Visualization

![Customer BI](https://github.com/user-attachments/assets/c861bce0-cd48-4876-b7eb-48cf12a804df)

   





