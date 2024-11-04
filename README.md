# INTRODUCTION
This is where I documented the project I submitted while learning at Incubator Hub. This project is aimed at analysing the sales perfomance of a retail store. I explored the sales data so as to uncover key insights such as top-selling products, regional performance, and monthly sales trends. The goal is to produce an interactive Power BI dashboard that highlights these findings.

## Data Description
The dataset includes the following fields:
- Order ID
- Customer ID
- Product
- Region
- Order Date
- Quantity
- Unit Price
- Revenue

## Basic Statistics about the dataset:
Total Sales: 2,101,090 
Total Quantity Sold: 68,461 items
Number of Product Category: 6

## Data Manipulation
### Data Cleaning:
I checked for duplicates and blank cells. These were removed to avoid duplicate entries and address missing values

### Excel Analysis
![image](https://github.com/user-attachments/assets/016b2a49-3602-45ed-95a4-ffc548f46b1a)

![image](https://github.com/user-attachments/assets/6e1b0fda-cee1-47c8-a213-2c6fe58a9f37)


## Tools Used
1. Microsoft Excel
2. SQL
3. Power BI

   
```SELECT * FROM [dbo].[LITA Capstone Sales Dataset]

DELETE FROM [dbo].[LITA Capstone Sales Dataset] 
WHERE REGION IS NULL

select sum(revenue) as TotalSales from [dbo].[LITA Capstone Sales Dataset]

------to get Total Sales for each product category	

select Product, 
sum(revenue) as TotalSales
from [dbo].[LITA Capstone Sales Dataset] 
group by Product 
order by 2 desc

----to find the number of sales transactions in each region-----

select Region, count(Quantity) as SalesTransactions from [dbo].[LITA Capstone Sales Dataset]
group by Region

----find the highest-selling product by total sales value-----

select Top 1 Product, 
sum(revenue) as TotalSales from [dbo].[LITA Capstone Sales Dataset] 
group by Product 
order by TotalSales Desc

----calculate total revenue per product----

select Product, sum(revenue) as TotalRevenue from [dbo].[LITA Capstone Sales Dataset]
group by Product 

-----calculate monthly sales totals for the current year-----

 Select DATENAME(Month, OrderDate) as SalesMonth, 
SUM(Quantity) AS TotalSales from [dbo].[LITA Capstone Sales Dataset]
WHERE YEAR(OrderDate) = YEAR(GETDATE())
Group By DATENAME(Month, OrderDate), Month(OrderDate)
Order By Month(OrderDate)

-----find the top 5 customers by total purchase amount-----

Select Top 5 [Customer_Id] ,
SUM(Revenue) as TotalPurchaseAmount from [dbo].[LITA Capstone Sales Dataset]
Group By [Customer_Id]
Order By TotalPurchaseAmount Desc

-----calculate the percentage of total sales contributed by each region-----

SELECT Region, 
       SUM ([Quantity]) AS TotalSales,
	   ROUND ((SUM([Quantity]) * 100 / (SELECT SUM([Quantity])
	   FROM [dbo].[LITA Capstone Sales Dataset])), 2) AS SalesPercentage
FROM [dbo].[LITA Capstone Sales Dataset]
GROUP BY Region;

-----identify products with no sales in the last quarter------

Select Product from [dbo].[LITA Capstone Sales Dataset] 
where Product Not In (Select DISTINCT Product from [dbo].[LITA Capstone Sales Dataset] 
where OrderDate >= DATEADD(Quarter, -1, GETDATE())
)
Group By Product
```



