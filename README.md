-- Daily Trend of Total Orders
SELECT DATENAME(DW, order_date) AS Order_Day, 
       COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY DATENAME(DW, order_date);

-- Hourly Trend of Total Orders
SELECT DATEPART(HOUR, order_time) AS Order_Hour, 
       COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY DATEPART(HOUR, order_time)
ORDER BY Order_Hour;

-- Percentage of Sales by Pizza Category
SELECT pizza_category, 
       CAST(SUM(total_price) AS DECIMAL(10,2)) AS Total_Revenue,
       CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) FROM pizza_sales) AS DECIMAL(10,2)) AS Sales_Percentage
FROM pizza_sales
GROUP BY pizza_category
ORDER BY Sales_Percentage DESC;

-- Top 5 Best Sellers by Total Pizzas Sold
SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizzas_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizzas_Sold DESC;

-- Bottom 5 Worst Sellers by Total Pizzas Sold
SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizzas_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizzas_Sold ASC;