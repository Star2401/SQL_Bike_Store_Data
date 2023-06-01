# SQL BikeStore Data
A Bike store's management wants to know the condition of sales activities within the company and gain insights into the various trends happening in the sales volume over the 2016 - 2018 period. They also want to know the revenue per region, store, product category, and brand. A list of the top customers and sales reps would also be insightful.<br/>
<br/>
-- Write an SQL script that generates a dataset consisting of order id, customer's first name, customer's last name, customer's city, and state, order date, sales volume, revenue, product name, product category, brand name, store name and sales rep<br/>
<br/>
SELECT<br/>
	 ord.order_id,<br/>
	 CONCAT(cus.first_name,' ', cus.last_name) as 'customer name',<br/>
	 cus.city,<br/>
	 cus.state,<br/>
	 ord.order_date,<br/>
	 sum(ite.quantity) as 'total units',<br/>
	 sum(ite.quantity * ite.list_price) as 'revenue',<br/>
	 pro.product_name,<br/>
	 cat.category_name,<br/>
	 bra.brand_name,<br/>
	 sto.store_name,<br/>
	 CONCAT(sta.first_name,' ',sta.last_name) as 'sales rep'<br/>
FROM [sales].[orders] ord<br/>
join [sales].[customers] cus<br/>
ON ord.customer_id = cus.customer_id<br/>
join [sales].[order_items] ite<br/>
ON ord.order_id = ite.order_id<br/>
join [production].[products] pro<br/>
on ite.product_id = pro.product_id<br/>
join [production].[categories] cat<br/>
on pro.category_id = cat.category_id<br/>
join [sales].[stores] sto<br/>
on ord.store_id = sto.store_id<br/>
join [sales].[staffs] sta<br/>
on ord.staff_id = sta.staff_id<br/>
join [production].[brands] bra<br/>
on pro.brand_id = bra.brand_id<br/>
GROUP BY<br/>
	 ord.order_id,<br/>
	 CONCAT(cus.first_name,' ', cus.last_name),<br/>
	 cus.city,<br/>
	 cus.state,<br/>
	 ord.order_date,<br/>
	 pro.product_name,<br/>
	 cat.category_name,<br/>
	 bra.brand_name,<br/>
	 sto.store_name,<br/>
	 CONCAT(sta.first_name,' ',sta.last_name)<br/>
   <br/>
   
 **Below is the resulting dataset and analysis in Microsoft Excel**<br/>
 [Bike Stores.xlsx](https://github.com/Star2401/SQL_Bike_Store_Data/files/11629995/Bike.Stores.xlsx)
