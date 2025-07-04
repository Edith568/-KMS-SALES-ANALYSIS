# -KMS-SALES-ANALYSIS

## Project review 
This project is carried out on KULTRAY MEGA STORE (KMS) INVENTORY which specialize in office supplies and furniture to help analyze their sales data from 2009 to 2012 which is crucial for every business to ensure they have enough stock to meet customer demand without incurring excessive storage cost or experiencing stock out ‘to help provide dynamic understanding of inventory performance of the business for good decision making of the organization.

## Tools Used: SQL

## Data Source 
The dataset for this project was extracted from DSA Learning Management System (LMS) as part of our final project.
Transformation:  The Raw Data was transformed using SQL by changing some inconsistent date format from text to date, Smallint was changed to INT in Order ID  because of large data volume and NULL values were replaced with the MEAN  and converted into real data format.


## checking for null values in "PROFIT and UNIT PRICE COLUMNS"

                          select * from [KMS Sql Case Study]
                          Where Product_Base_Margin Is NULL Or Profit is NULL Or
                          Unit_Price is NULL

  
![REPLACING NULL VALUE WITH MEAN](https://github.com/user-attachments/assets/a8c34e49-d4ac-4aea-83fa-f05ba3620b70)

## Replacing NULL VALUES with Mean

                    update [KMS Sql Case Study]
                    Set Profit = 181.18
                    where Profit is NULL
                    
                    update [KMS Sql Case Study]
                    Set Unit_Price = 89.35
                    where Unit_Price is NULL
                    
                    update [KMS Sql Case Study]
                    Set Product_Base_Margin = 0.51
                    where Product_Base_Margin is NULL

## Key Performance Idicators (KPIs)

                  Select Sum(Sales) As Total_Sales,
                  Count(Order_ID) As Total_Orders,
                  Sum(Profit) As Total_Profit,
                  Sum(Shipping_Cost) As Total_Shipping_Cost,
                  Sum(Discount) As Total_Discount,
                  Sum(Unit_Price) As Total_Unit_Price,
                  Sum(Product_Base_Margin) As Toatl_Product_Base_Margin
                  From [KMS Sql Case Study]


## Which product category had the highest sales?
                Select top 1 Product_Category, Sum(Sales) As TotalSales
                From [KMS Sql Case Study]
                Group By Product_Category
                Order By TotalSales Desc  

![MAIN ANALYSIS STEP 1 (FINDING THE PRODUCT CATEGORY WITH THE HIGHEST SALES](https://github.com/user-attachments/assets/98d54c57-2dd1-487e-906a-f98fdd89720d)


## Top 3 Product -Category with the highest Sales

              Select top 3 Product_Category, Sum(Sales) As TotalSales
              From [KMS Sql Case Study]
              Group By Product_Category
              Order By TotalSales Desc

  ![MAIN ANALYSIS STEP 2 TOP 3 PRODUCT CATEGORY WITH HIGHEST SALES](https://github.com/user-attachments/assets/b8ce4df0-5939-41fc-9c5e-6beec48718f9)

## What are the Top 3 and Bottom 3 regions in terms of sales?

## Top 3 Region by Sales

              Select top 3 Region, Sum(Sales) As TotalSales
              From [KMS Sql Case Study]
              Group By Region
              Order By TotalSales Desc
              
![FINDING THE T![top 3 region](https://github.com/user-attachments/assets/e25122ce-a537-4957-86b0-3282c0c0c614)

## Bottom 3 Region by Sales

            Select top 3 Region, Sum(Sales) As TotalSales
            From [KMS Sql Case Study]
            Group By Region
            Order By TotalSales Asc
OP 3AND BOTTOM 3 BY REGION IN TERMS OF SALES(BUTTOM TOP 3 REGION BY SALES](https://github.com/user-attachments/assets/0214a834-0842-4bd5-a3e8-13d9f65ef74b)

## Determing the Total sales of appliances in Ontario

            Select Sum(Sales) As TotalSales
            From [KMS Sql Case Study]
            where Product_Category = 'Appliances'
            And Region = 'Ontario'

![DETERMING THE TOTAL SALES OF APPLIANCES IN ONTARIO](https://github.com/user-attachments/assets/77eb3c0f-5928-4ca4-ae9b-e8986f8c2dbd)

## Determining the Highest shipping cost in a particular shipping method

          Select Ship_Mode, Shipping_Cost
          From [KMS Sql Case Study]
          Order by Shipping_Cost Desc
          
![SHIPPING COST BY ORDER PRIORITY AND SHIPPING METHOD](https://github.com/user-attachments/assets/7efbc4ef-c312-4316-98f6-4c4d2758654a)
      
![DETERMING THE HIGHEST SHIPPING COST IN A PARTICULAR SHIPPING METHOD](https://github.com/user-attachments/assets/f27b5205-8ee5-4bfe-8fed-ec25609ea399)

## The Most valuable Customers and the product or Services there purchase

          Select Top 10 Customer_Name, Product_Name, Sum(Sales) As Total_Spent
          From [KMS Sql Case Study]
          Group By Customer_Name, Product_Name
          Order By Total_Spent Desc
          
![THE MOST VALUABLE CUSTOMERS AND THE PRODUCT OR SERVICES THERE PURCHASE](https://github.com/user-attachments/assets/175540b7-41f9-482b-a808-7b5d3412c406)

## Small Business Customer with the highest Sales

          SELECT Top 10 Customer_Name, SUM(Sales) AS Total_sales
          FROM [KMS Sql Case Study]
          WHERE Customer_Segment = 'Small Business'
          GROUP BY Customer_Name
          ORDER BY Total_sales DESC

 ![SMALL BUSINESS CUSTOMER WITH THE HIGHEST SALES](https://github.com/user-attachments/assets/83de6cca-e5f7-4d7f-a240-1a28fad690a1)

  ## Top 1 Small Business Customer with the highest Sales

            SELECT Top 1 Customer_Name, SUM(Sales) AS Total_sales
            FROM [KMS Sql Case Study]
            WHERE Customer_Segment = 'Small Business'
            GROUP BY Customer_Name
            ORDER BY Total_sales DESC

 ![TOP 1 SMALL BUSINESS CUSTOMER WITH THE HIGHEST SALES](https://github.com/user-attachments/assets/cbf95e1d-b0ca-4525-96d8-903cbdd892d3)

 ## Corperate customer that placed the most number of orders in 2009 - 2012

          Select Top 1 Customer_Name, Count(Order_ID) As Total_Orders
          From [KMS Sql Case Study]
          WHERE Customer_Segment = 'Corporate'
          And Order_Date Between '2009-01-01' and '2012-12-31'
          Group By Customer_Name
          Order By Total_Orders Desc

![CORPERATECUSTOMER THAT PLACED THE MOST NUMBER OF ORDER IN 2009-2012](https://github.com/user-attachments/assets/21924072-d699-424c-a5b8-3324832abbde)

## Top 5 Corperate customer that placed the most number of orders in 2009 - 2012

          Select Top 5 Customer_Name, Count(Order_ID) As Total_Orders
          From [KMS Sql Case Study]
          WHERE Customer_Segment = 'Corporate'
          And Order_Date Between '2009-01-01' and '2012-12-31'
          Group By Customer_Name
          Order By Total_Orders Desc

![TOP 5 CORPERATE CUSTOMERS THAT PLACED THE MOST NUMBER OF ORDERS IN 2009](https://github.com/user-attachments/assets/abb18223-4a0b-4777-9b3e-693f275835ce)

## Most Profitable Consumer Customer

          SELECT Top 1 Customer_Name, SUM(Profit) AS total_profit
          FROM [KMS Sql Case Study]
          WHERE Customer_Segment = 'Consumer'
          GROUP BY Customer_Name
          ORDER BY total_profit DESC

![MOST PROFITABLE CONSUMER CUSTOMER](https://github.com/user-attachments/assets/e3e29e88-0abc-4e28-ba3a-934020fb1d23)

## Top 5 Most Profitable Consumer Customer

        SELECT Top 5 Customer_Name, SUM(Profit) AS total_profit
        FROM [KMS Sql Case Study]
        WHERE Customer_Segment = 'Consumer'
        GROUP BY Customer_Name
        ORDER BY total_profit DESC

![TOP 5 MOST PROFITABLE CONSUMER CUSTOMER](https://github.com/user-attachments/assets/490ed662-a894-4714-b706-47378a0af2f6)

## Customer that returned items, and the segment they belong to
      
#### Joining the two tables ([KMS Sql Case Study] and Order_Status) together

          SELECT DISTINCT [KMS Sql Case Study].customer_name, [KMS Sql Case Study].customer_segment
          FROM [KMS Sql Case Study]
          JOIN Order_Status 
          ON [KMS Sql Case Study].Order_ID = Order_Status.Order_ID
          WHERE [Status] = 'Returned'

![CUSTOMERS THAT RETURNED ITEMS AND THE SEGMENT THEY BELONG TO (JOINING KMS AND ORDER STATUS TABLE TOGETHER](https://github.com/user-attachments/assets/9d9e5878-5c28-4f5d-bb01-eb735ec68a84)

## Shipping Cost by Order Priority and Shipping Method

          SELECT 
              Order_Priority,
              Ship_Mode,
              SUM(Shipping_Cost) AS Total_Shipping_Cost
          FROM [KMS Sql Case Study]
          GROUP BY Order_Priority, Ship_Mode
          ORDER BY Order_Priority, Ship_Mode

![SHIPPING COST BY ORDER PRIORITY AND SHIPPING METHOD](https://github.com/user-attachments/assets/11f824d1-c440-4b24-acca-24e900a3b752)


