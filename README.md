# Superstore-Retail-Business-Analysis-SQL-PowerBI-Dashboard


# Case Study
 
A superstore retail business is a large, multi-department store that sells various products, including groceries, electronics, home goods, clothing, and more. These stores are often designed to be a one-stop shop for customers, offering a wide range of products and services under one roof. Superstores are typically larger than traditional retail stores and may have a larger product selection. Superstores are often part of a larger chain and have multiple locations in a region or country.

# SUPERSTORE RETAIL BUSINESS DISTRIBUTION AND SALES
•	Imported the data to power bi and loaded data into Query Editor.
## Query Editor:-
1.	Deleted the empty columns.
2.	Promoted the Headers (use first row as headers).
3.	Changed the fields to appropriate data types.
4.	Spitted the address column to City, State, Country and Pin code.
5.	Standardized the values in the column Ship mode, replaced FC with First Class.
6.	Checked for errors in the table and removed blank rows and errors.
7.	Replaced null values with Fill down value instead of deleting the row.
8.	Created new group in Query section as Dim-Tables, in order to store the Dim tables.
9.	Created dim and fact tables by using reference of main table (orders table).
10.	Removed duplicates from the dim tables.
11.	After cleaning the data loaded the data into Data Model.

## Data Model:-
1.	Once the data is loaded into data model, relationships were created between fact and dim tables by using common columns between them.
2.	Created Sales and Order value columns and visualized
   
``` Sales = 'Fact-Orders'[Quantity]*'Fact-Orders'[Buy Price]```
```Order Value = 'Fact-Orders'[Quantity]*'Fact-Orders'[Price Per Each]*(1-'Fact-Orders'[Discount]) ```

3.	Calculated the Sales from discounted products.
   
```Sales After Discount = 'Fact-Orders'[Sales]-'Fact-Orders'[Discount]```

4.	Created cart value category as low, high , medium and created pie chart.
   
```Cart Value = SWITCH(TRUE(),'Fact-Orders'[Sales]<1000, "Low",'Fact-Orders'[Sales]<3500,"Medium",'Fact-Orders'[Sales]<10000, "High",'Fact-Orders'[Sales]>10000, "Very High")```

5.	Calculated and visualized the sales which are from low cart.
   
```Low cart Value = CALCULATE(SUM('Fact-Orders'[Sales]), 'Fact-Orders'[Cart Value] = "Low")```

6.	Created a new measure track the total sales coming from the low cart category and discount more than or equal to 50% to find out the contribution and cause
   
```Low cart and Discount is 50 = CALCULATE(SUM('Fact-Orders'[Sales]), 'Fact-Orders'[Cart Value] = "Low", 'Fact-Orders'[Discount] >= 0.5)```

7.	Calculated number of days it takes to deliver for each shipment type, so that delivery issues can be looked at on priority
   
8.	Created a column chart that shows the average number of days it takes to deliver for each shipment type
    
```No of days to deliver = DATEDIFF('Fact-Orders'[Order Date], 'Fact-Orders'[Ship Date],DAY)```

9.	Calculated sales and sales year to date and created a matrix visualization.
    
```YTDSumOfSales = TOTALYTD([Sum of Sales],'Calendar'[Date])```

10.	Calculated and Visualized the cumulative sales for each month for all the years to calculate Year on Year Sales Growth
     
```Cumulative Sales = CALCULATE(SUM('Fact-Orders'[Sales]), FILTER(ALL('Fact-Orders'), 'Fact-Orders'[Order Date] <= MAX('Fact-Orders'[Order Date])))```
```YOY Sales Growth = CALCULATE(SUM('Fact-Orders'[Sales]), DATEADD('Calendar'[Date],-1,YEAR))```

# Report View:-
![image](https://github.com/Abhinav3393/Superstore-Retail-Business-Analysis-SQL-PowerBI-Dashboard/assets/109345010/03c71596-b7ed-46c1-ae5f-eb4b4db3864f)

	We can observe there are totally 2.3 million sales as per data provided.

	After discount is provided we can observe there are 696.06 k sales.

	From the above report we can observe that there are more sales for Low cart that is about 1.31 million (56.9%).

	Office supplies category have high sales when compared to Technology and Furniture.

	We can observe 57.44k sales were done from low cart and when discount is greater than 50%.

![image](https://github.com/Abhinav3393/Superstore-Retail-Business-Analysis-SQL-PowerBI-Dashboard/assets/109345010/bc03bf40-b0d2-48ce-9d26-4ef97cfd7367)

	In order deliver product Standard class takes more number of days when compared to First and Second class.

	We can observe total sum of sales year wise and month wise.

![image](https://github.com/Abhinav3393/Superstore-Retail-Business-Analysis-SQL-PowerBI-Dashboard/assets/109345010/1348484c-f6b8-4399-a309-0cf60249a51f)

	We can observe west region has more sales when compared to other regions.

	In sub category phones have more number of sales followed by chairs and storage category.

	In segment consumer has more sales with 1.16 million.

	Technology category has highest number of sales then office supplies and furniture

	There are more sales in New York city when compared to other cities.



