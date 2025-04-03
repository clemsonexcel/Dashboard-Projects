## **Toman Bike Share Analysis Dashboard** 🚴‍♂️📊  

 ![Bicycle-Gif](bike-bicycle.gif)
#### **Overview**  
This project analyzes bike data for **Toman Bike Share**, providing insights into **revenue trends, rider demographics, and seasonal patterns**. The goal is to assess **whether increasing prices next year is viable** while ensuring business sustainability and customer retention.  

#### **Objectives**  
- **Evaluate revenue trends** (hourly, seasonal, and overall).  
- **Analyze rider demographics** to understand customer segments.  
- **Assess profitability** and **determine factors influencing revenue.**  
- **Provide data-driven recommendations** for potential price adjustments.  

#### **Dataset:** Toman Bike Share [data](data-folder), including trip details, customer information, and revenue. 

#### **Technologies Used**  
🔹 **SQL** – Data storage, querying, and transformation  
🔹 **Power BI** – Data visualization and dashboard creation 

#### **Data Preparation and SQL Query** 
Before building the dashboard in Power BI, the data was processed using SQL. The query below merges the datasets and selects the necessary columns for analysis:

```sql
with full_table as (
with shares_table as (
	SELECT * FROM bike_share_yr_0
	UNION ALL 
	SELECT *
	FROM bike_share_yr_1
)
select dteday,
	season,
    shares_table.yr,
    weekday,
    hr,
    rider_type,
    riders,
    price, 
    COGS,
    round(riders*price, 2) as revenue,
    round(riders*price - COGS*riders, 2) as profit
from shares_table
left join cost_table 
	on shares_table.yr = cost_table.yr
```

This transformed dataset was then loaded into Power BI for visualization.


#### **Key Insights & Findings**  
- Peak riding hour generate the most revenue, particularly during morning and evening commutes on weekdays, while weekends see stable ridership throughout the day.

- Summer and spring generate the highest revenue, while winter contributes the least.

- Frequent riders contribute significantly to total revenue, suggesting the importance of loyalty programs.  

- Seasonal revenue fluctuations highlight the need for data-driven pricing adjustments. Registered users make up over 80% of total riders and contribute more than 70% of total revenue and profit.



*Dashboard Preview*

![Dashboard](dashboard_image.png)

🔗 [View Full Dashboard](link-to-dashbaord)

### **Business Recommendations**  

#### **Pricing Strategy for Toman Bike Share**  

#### **Conservative Increase**  
Given the substantial price increase last year, a more measured approach is recommended to avoid reaching a price ceiling where demand drops. A **10-15% increase** allows for market testing without significant customer loss.  

#### **Price Adjustment Estimates**
Based on a $4.99 Baseline Fare  
- A **10% increase** would set the new price at **$5.49**.  
- A **15% increase** would set the price at approximately **$5.74**. 

Price Adjustment Estimates (Based on a $4.99 Baseline Fare)

#### **Strategic Considerations**  

✔ **Market Analysis**  
Conduct additional market research to understand **customer satisfaction, competitor pricing, and economic factors**. This will help determine whether to adopt the lower or higher end of the proposed increase.  

✔ **Segmented Pricing Strategy**  
Consider different pricing between **casual and registered users**, as their price sensitivity may vary.  

✔ **Monitor & Adjust**  
Roll out the new pricing while closely tracking customer response and sales data. Careful monitoring will enable price adjustments before fully committing to a potentially high price point.


