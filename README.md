# LITA CAPSTONE PROJECT

## Project Title: Sales Performance Analysis for a Retail Store
  
## Project Overview:
###  For Sales Performance Analysis for a Retail Store:
This project aims to collect and analyze data from various regions, stores, and markets to provide actionable insights that will inform business strategies, enhance operational efficiency, and improve customer satisfaction, gaining insights into revenue, units sold, and transaction categories across various regions and stores is critical for driving business strategies and improving overall performance. This project systematically collects and analyzes relevant data to provide actionable insights into sales trends, product performance, and market dynamics over different periods.

## Tools:
- Microsoft Excel
   - For data cleaning
   - For data exploration
   -  For data analysis
- Structured Query Language(SQL) for quering the data
- Power BI for data visualization
  
  # Exploratory Data Analysis
  ## For Sales Performance Analysis for a Retail Store:
  - Data Cleaning and Prepation: The data given has about 50,000 records but the records were duplicated. To gain insights and avoid overstating the outcome, I embarked on removing duplicate and prepare the data for exploration.
  ## Data Exploration: Excel and SQL
  In Excel: I carried out expolration of the data by using pivot table to summarize
   
    - Total Sales By Product
    - Total Sales By Region
    - Total Sales By Month
    -  Other Interesting report such as: Quantity sold by region, Average sales per product, Total quantity sold. 
  ![Screenshot (33)](https://github.com/user-attachments/assets/160f11de-af36-4992-8bf7-95fcae5e5e58)      

  I used excel formula to calculate 
  
   - Average Sales Per Product
   - Total Revenue By Region
   
    ![Screenshot (32)](https://github.com/user-attachments/assets/58961657-7b9b-4591-a44a-47e28e8270fe)

    
In SQL: I wrote the queries to extract insight from the  following question

- Total number of sales for each category

  ```SQL
  select ProductName, sum(Total_Sales) as ToTalSalesforProduct from [dbo].[LITA CAPSTONE SALES2]
  group by ProductName
   order by sum(Total_Sales) desc
  ```
- The number of sale transaction in each region
```SQL
select  Region, count(OrderID) as SalesByRegion  from [dbo].[LITA CAPSTONE SALES2]
 Group by Region
 order by count(OrderID) desc
```
- The highest selling product by total sales

  ```SQL
  select ProductName, max(Total_sales) as HighestSellingProduct  from [dbo].[LITA CAPSTONE SALES2]
    group by ProductName
     order by max(Total_Sales) desc
```
- The total revenue by product

```SQL
   select sum(Total_Sales) as ToTalRevenueperProduct, ProductName
     from [dbo].[LITA CAPSTONE SALES2]
       group by ProductName
```
- The monthly sales totals for current year

 ```SQL
   select OrderDate,
     sum(Total_Sales) as MonthlySales from  [dbo].[LITA CAPSTONE SALES2]
      where OrderDate between '2024-01-01' and '2024-12-31'
        group by OrderDate 
        order by OrderDate
```
- The top 5 customer by total purchase amount

 ```SQL
  select top 5 Customer_Id, sum(Total_Sales) as TOP5CUSTOMER
    from [dbo].[LITA CAPSTONE SALES2]
    group by Customer_Id
     order by Customer_Id desc
```
- Percentage of total sales contributed by region

  ```SQL
  With Region as (
    select Region,
    sum(Total_Sales) as PercentageSales from [dbo].[LITA CAPSTONE SALES2]
      group by Region)
      select Region, (PercentageSales * 100.0/(Select sum(Total_Sales) from [dbo].[LITA CAPSTONE SALES2])) as PercentageSales 
       from Region
  ```
### Visualization and Reporting with PowerBI

I developed an interactive dashboard using Power BI to visualize the sales performance of the retail store. The dashboard provides key insights into 
- Total revenue made by the retail store
- Top-performing product by revenue
- Sales made by each region
- Top selling product by quantity

 It allows users to filter data by product and region.
 
![Screenshot (35)](https://github.com/user-attachments/assets/8e6e26e0-a6e6-4d3a-b11b-08bc5540063f)


 ### Inference and Conclusion
 In this analysis of the sales performance of the retail store from 1st of January  2023 to 31st of December 2024, I aimed to uncover trends such as top-selling products, regional performance, and monthly sales trends. The analysis reveled key findings 

 - Total Revenue: The total revenue made by the retail store is #2101090 for the cumulative year of 2023 and 2024
 - Top perfoeming product by revenue: The product 'Shoe' accounted for 613,000 0f the total revenue
 
 

 








