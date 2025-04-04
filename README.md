# TRASH-TOKRI-PROJECT



## *1. Introduction*
This report provides an in-depth analysis of scrap collection trends, revenue generation, and customer engagement using Power BI. The goal is to help stakeholders optimize operations and maximize revenue.

![TRASH-TOKRI-PROJECT](https://github.com/singhdeepesh20/TRASH-TOKRI-PROJECT/blob/main/TRASH%20TOKRI.png)


## *2. Data Sources*
The report is built using the following datasets:
- *Customers.csv* – Contains customer details.
- *Scrap_Transactions.csv* – Records all scrap collection transactions.
- *Franchise_Partners.csv* – Information about franchise partners.
- *Scrap_Categories.csv* – Categorization of different scrap types.

## *3. Data Cleaning & Transformation*
- Ensured correct data types (Date, Number, Text).
- Removed null values and duplicates.
- Established relationships:
  - Customers[CustomerID] → Scrap_Transactions[CustomerID]
  - Scrap_Transactions[ScrapType] → Scrap_Categories[ScrapType]
  - Scrap_Transactions[Location] → Franchise_Partners[Location]

## *4. Key Metrics (DAX Measures)*
The following DAX measures were created to track performance:

- *Total Revenue:*  
  TotalRevenue = SUM(Scrap_Transactions[TotalAmount])

- *Total Scrap Collected (kg):*  
  TotalScrapCollected = SUM(Scrap_Transactions[Weight(Kg)])

- *Average Price per Kg:*  
  AvgPricePerKg = AVERAGE(Scrap_Transactions[PricePerKg])

- *Top Customers (by Scrap Volume):*  
  TopCustomers = TOPN(10, VALUES(Customers[Name]), SUM(Scrap_Transactions[Weight(Kg)]), DESC)

- *Profit Margin Analysis:*  
  ProfitMargin = (SUM(Scrap_Transactions[TotalAmount]) - SUM(Scrap_Transactions[Cost])) / SUM(Scrap_Transactions[TotalAmount])

- *Revenue Growth Rate:*  
  RevenueGrowth = (SUM(Scrap_Transactions[TotalAmount]) - CALCULATE(SUM(Scrap_Transactions[TotalAmount]), PREVIOUSMONTH(Scrap_Transactions[TransactionDate]))) / CALCULATE(SUM(Scrap_Transactions[TotalAmount]), PREVIOUSMONTH(Scrap_Transactions[TransactionDate]))

## *5. Data Visualizations*
The following visuals were created in Power BI:

### *1️⃣ Total Scrap Collected (Trend Over Time)*
- *Chart Type:* Line Chart  
- *X-Axis:* Scrap_Transactions[TransactionDate]  
- *Y-Axis:* TotalScrapCollected  

### *2️⃣ Revenue Breakdown (Monthly)*
- *Chart Type:* Column Chart  
- *X-Axis:* Scrap_Transactions[TransactionDate] (Month)  
- *Y-Axis:* TotalRevenue  

### *3️⃣ Customer Engagement (Top Customers)*
- *Chart Type:* Table  
- *Columns:* Customers[Name], TotalScrapSold  

### *4️⃣ Franchise Performance (Revenue by Location)*
- *Chart Type:* Map  
- *Location:* Franchise_Partners[Location]  
- *Size:* Franchise_Partners[MonthlyRevenue]  

### *5️⃣ Scrap Category Analysis*
- *Chart Type:* Pie Chart  
- *Legend:* Scrap_Categories[ScrapType]  
- *Values:* TotalScrapCollected  

### *6️⃣ Profit Margin & Growth Trends*
- *Chart Type:* Line Chart  
- *X-Axis:* Scrap_Transactions[TransactionDate]  
- *Y-Axis:* ProfitMargin & RevenueGrowth  

## *6. Filters & Slicers*
To enhance interactivity, the following slicers were added:
- *Transaction Date* (Date filter)
- *Scrap Type* (Category filter)
- *Location* (Geographic filter)

## *7. Insights & Recommendations*
- *Scrap Collection Trends:* The highest volume of scrap collection occurs in certain months; optimizing logistics during peak periods is recommended.
- *Revenue Optimization:* Higher revenue is generated from specific locations, indicating opportunities for expansion.
- *Customer Engagement:* A small percentage of customers contribute the majority of scrap collection, suggesting targeted marketing efforts could improve engagement.
- *Franchise Performance:* Some franchise locations generate significantly higher revenue than others, requiring strategic planning for underperforming locations.
- *Profit Margins:* Some scrap types yield higher profit margins; adjusting procurement and pricing strategies can enhance profitability.
- *Revenue Growth Trends:* Identifying months with significant revenue growth or decline can help in financial forecasting and business planning.

## *8. Conclusion*
This Power BI dashboard provides a real-time, data-driven approach to analyzing scrap collection and revenue. By leveraging these insights, businesses can enhance efficiency, improve customer engagement, and maximize profitability.


