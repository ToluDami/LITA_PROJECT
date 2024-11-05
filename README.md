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

## Tools Used 
### Microsoft Excel for pivot tables
![image](https://github.com/user-attachments/assets/016b2a49-3602-45ed-95a4-ffc548f46b1a)

![image](https://github.com/user-attachments/assets/6e1b0fda-cee1-47c8-a213-2c6fe58a9f37)

### Microsoft SQL Server Management Studio
This was used to answer various questions as seen below
   
```SELECT * FROM [dbo].[LITA Capstone Sales Dataset]

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
![image](https://github.com/user-attachments/assets/44304dd3-8d11-4b9e-b0ca-01f4b20d46bb)
![image](https://github.com/user-attachments/assets/d63e69ce-3a28-4b17-a994-7096fe29f0d3)
![image](https://github.com/user-attachments/assets/7e8cede9-68ef-48e9-8290-c532bd0d5efa)
![image](https://github.com/user-attachments/assets/9c6bbc00-3221-4d08-94fb-18d03ef7283c)
![image](https://github.com/user-attachments/assets/024f83d6-2861-4e95-8a67-73422eed2793)
![image](https://github.com/user-attachments/assets/54e8c92e-a281-4035-ba20-29853a542322)
![image](https://github.com/user-attachments/assets/0faf9c26-24ec-4753-aeba-b203f113132f)
![image](https://github.com/user-attachments/assets/b160fcf7-c945-4b8e-a00b-f9560676b5ee)

### Microsoft PowerBi
This was also used for visualisation of the data in various ways as seen below
![image](https://github.com/user-attachments/assets/75ff8835-0c91-457e-a9e3-4fa6ab515df7)









