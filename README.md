### State-Data-Analysis-Using-SQL



### Table of Contents

- [Introduction](introduction)
Data Analysis Queries and Results
2.1 State with the Highest Number of Orders
2.2 Total Revenue Generated per State
2.3 Average Order Value per State
2.4 Trends Between Product Categories and States
2.5 State with the Highest Number of Unique Customers
Insights
Professional Recommendations



## Introduction

This portfolio showcases a series of SQL queries designed to analyze sales and customer data across different U.S. states. Each query provides specific insights into sales trends, customer concentration, and regional preferences, essential for making informed business decisions. The purpose of this portfolio is to illustrate my technical expertise in SQL and data analysis, making a compelling case for roles that require strong analytical skills and business insights.

## Data Analysis Queries and Results

- State with the Highest Number of Orders
 
Objective: Identify the state generating the highest number of orders.

SQL Query:

SELECT s.StateName, COUNT(o.OrderID) AS total_orders
FROM states s
JOIN customers c ON s.StateAbbr = c.State
JOIN orders o ON c.CustomerID = o.CustomerID
GROUP BY s.StateName
ORDER BY total_orders DESC
LIMIT 1;



![State with highest no of order](https://github.com/user-attachments/assets/2d54954d-6dcc-4a10-ad80-8da23105cdac)



Result:
State: Newyork
Total Orders: 232


-  Total Revenue Generated per State

Objective: Calculate total revenue generated per state.

SQL Query:

SELECT s.StateName, SUM(o.Quantity * p.SuggestedRetail) AS total_revenue
FROM states s
JOIN customers c ON s.StateAbbr = c.State
JOIN orders o ON c.CustomerID = o.CustomerID
JOIN products p ON o.ProductID = p.ProductID
GROUP BY s.StateName
ORDER BY total_revenue DESC;

Result (Top 5 States):

![Total Revenue generated per state](https://github.com/user-attachments/assets/f75a6b05-4804-427f-bc3b-f3d4839d00c8)


State	                  Total Revenue

Newyork	                $2,188,539.88

Texas 	                $2,125,229.56

California	            $1,587,539.40

District of Columbia	  $1,133,373.42

Florida 	              $926,804.52


- Average Order Value per State
  
Objective: Determine the average order value in each state.

SQL Query:

SELECT s.StateName, AVG(o.Quantity * p.SuggestedRetail) AS avg_order_value
FROM states s
JOIN customers c ON s.StateAbbr = c.State
JOIN orders o ON c.CustomerID = o.CustomerID
JOIN products p ON o.ProductID = p.ProductID
GROUP BY s.StateName
ORDER BY avg_order_value DESC;

Result (Top 5 States):


![Average order value per state](https://github.com/user-attachments/assets/87e4c371-1522-4c1d-ace1-4423e3ebd7e1)



State	                  Average Order Value

Alaska       	          24671.17

Montana	                19514.97

District of columbia	  19209.71

North Carolina	        17317.74

Vermont	                16321.98


- Trends Between Product Categories and States
  
Objective: Analyze order trends by product category within each state.

SQL Query:

SELECT s.StateName, p.Category, COUNT(o.OrderID) AS orders_in_category
FROM states s
JOIN customers c ON s.StateAbbr = c.State
JOIN orders o ON c.CustomerID = o.CustomerID
JOIN products p ON o.ProductID = p.ProductID
GROUP BY s.StateName, p.Category
ORDER BY s.StateName, orders_in_category DESC;


![Trend btw product category   state](https://github.com/user-attachments/assets/1b2054e0-abfe-428d-a634-91b89e979579)


Result (Example Data):

StateName     Category    	Orders in Category

Alabama	     Lightbulbs	        12

Alabama	     Solar panels	      12

Alabama	     wind harvester     12

Alabama	     batteries          8

Alabama      Grid tie Inverters 7


- State with the Highest Number of Unique Customers
 
Objective: Identify the state with the highest number of unique customers.

SQL Query:

SELECT s.StateName, COUNT(DISTINCT c.CustomerID) AS unique_customers
FROM states s
JOIN customers c ON s.StateAbbr = c.State
GROUP BY s.StateName
ORDER BY unique_customers DESC
LIMIT 1;

Result:


![State with the highest no of unique customers](https://github.com/user-attachments/assets/6d717c52-192c-457b-8108-38e2c729b6c3)



State: Newyork

Unique Customers: 98


## Insights

- High Demand States: The analysis identifies states with high demand for orders, guiding inventory allocation and highlighting areas for logistical focus.

- Revenue Distribution: Revenue metrics reveal states that generate the most income, aiding in investment decisions, targeted marketing, and resource prioritization.

- Spending Patterns: The average order value per state provides insights into the purchasing power and spending behavior of customers in each region.

- Product Popularity: By exploring product categories and state-level trends, this analysis identifies popular product lines in specific areas, helping target promotions more effectively.

- Customer Density: States with the highest concentration of unique customers are potential markets for loyalty programs and customer engagement efforts.


## Professional Recommendations

- Resource Allocation and Logistics: Based on the states with the highest order volumes, consider allocating additional resources, such as warehouse facilities or distribution centers, to optimize delivery times and reduce shipping costs.

- Revenue Optimization Strategies: Focus marketing campaigns and sales efforts on states with high revenue but lower customer density to maximize profitability in these areas.

- Targeted Marketing for High-Value Orders: In states where average order values are high, use premium product promotions and upsell campaigns to capitalize on existing spending patterns.

- Localized Product Strategy: Adjust product offerings according to state-specific category preferences to better align with customer demand, thereby reducing excess inventory and boosting sales.

- Customer Loyalty Programs: Implement loyalty programs in states with high unique customer counts to foster customer retention and increase the lifetime value of customers in these regions.

This portfolio demonstrates the practical applications of SQL in analyzing state-level sales data, customer trends, and product popularity, equipping stakeholders with the insights needed to make data-informed business decisions.


