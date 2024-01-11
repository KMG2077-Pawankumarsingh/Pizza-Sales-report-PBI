# Pizza-Sales-report-PBI

Total revenue
1.	select SUM(total_price) as Total_Revenue from Tbl_pizza_sales;

 

Average Order Value 
2.	select sum(total_price) /count(DISTINCT order_id ) AS Avg_Order_value from tbl_pizza_sales;





Total Pizza Sold .
select sum(quantity) as Total_Pizza_sold from Tbl_pizza_sales;
 

Total Order Placed 
select count(DISTINCT order_id) as Tatal_order from Tbl_pizza_sales;

 




5. Average Pizza per order.
select cast(sum(quantity) as decimal(10,2)) / cast(count(distinct order_id) as decimal(10,2))  as AVG_pizza_order from Tbl_pizza_sales;
 

6.    Order day + total order 
select datename(DW, ORDER_DATE) AS Order_day, count(distinct order_id) as Total_order from            Tbl_pizza_sales
   group by datename(DW, ORDER_DATE);
 

7.  Order per month 
select datename(month, ORDER_DATE) AS Order_Month, count(distinct order_id) as Total_order from Tbl_pizza_sales
group by datename(month, ORDER_DATE) order by total_order DESC;

 


8. Percentage of total sales by pizza category wise.  

select pizza_category, sum(total_price) AS total_sales, sum(total_price) * 100 / (select sum(total_price) 
from Tbl_pizza_sales where month(order_date)= 1) as PCT
from Tbl_pizza_sales where month(order_date)= 1   Group by pizza_category ORDER BY pizza_category;

 

9. pizza salese paercetage by pizza size wise. 

 select pizza_size, sum(total_price) AS total_sales, sum(total_price) * 100 / (select sum(total_price) 
from Tbl_pizza_sales where month(order_date)= 1) as PCT
from Tbl_pizza_sales where month(order_date)= 1   Group by pizza_size order by pct ;

OR

select pizza_size, sum(total_price) as Total_sales, cast(sum(total_price) * 100 / (select sum(total_price) 
from Tbl_pizza_sales) as decimal(10,2)) as PCT FROM Tbl_pizza_sales GROUP BY pizza_size order by PCT DESC;

 

10.   Top 5 pizza sales by Pizza name & Revenue.
select top 5 pizza_name,sum(total_price) as Total_Revenue from Tbl_pizza_sales group by pizza_name order by Total_Revenue desc;

 

