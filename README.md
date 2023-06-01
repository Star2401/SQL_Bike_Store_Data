# SQL BikeStore Data
A Bike store's management wants to know the condition of sales activities within the company and gain insights into the various trends happening in the sales volume over the 2016 - 2018 period. They also want to know the revenue per region, store, product category, and brand. A list of the top customers and sales reps would also be insightful.

-- Write an SQL script that generates a dataset consisting of order id, customer's first name, customer's last name, customer's city, and state, order date, sales volume, revenue, product name, product category, brand name, store name and sales rep

SELECT
	 ord.order_id,
	 CONCAT(cus.first_name,' ', cus.last_name) as 'customer name',
	 cus.city,
	 cus.state,
	 ord.order_date,
	 sum(ite.quantity) as 'total units',
	 sum(ite.quantity * ite.list_price) as 'revenue',
	 pro.product_name,
	 cat.category_name,
	 bra.brand_name,
	 sto.store_name,
	 CONCAT(sta.first_name,' ',sta.last_name) as 'sales rep'
FROM [sales].[orders] ord
join [sales].[customers] cus
ON ord.customer_id = cus.customer_id
join [sales].[order_items] ite
ON ord.order_id = ite.order_id
join [production].[products] pro
on ite.product_id = pro.product_id
join [production].[categories] cat
on pro.category_id = cat.category_id
join [sales].[stores] sto
on ord.store_id = sto.store_id
join [sales].[staffs] sta
on ord.staff_id = sta.staff_id
join [production].[brands] bra
on pro.brand_id = bra.brand_id
GROUP BY
	 ord.order_id,
	 CONCAT(cus.first_name,' ', cus.last_name),
	 cus.city,
	 cus.state,
	 ord.order_date,
	 pro.product_name,
	 cat.category_name,
	 bra.brand_name,
	 sto.store_name,
	 CONCAT(sta.first_name,' ',sta.last_name)
   
   
 #Below is the resulting dataset and analysis in Microsoft Excel
 [Bike Stores.xlsx](https://github.com/Star2401/SQL_Bike_Store_Data/files/11629995/Bike.Stores.xlsx)
