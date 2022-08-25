# SQL_Notes
Subquery: Use another query as the condition in its superior query.
select 
	order_id, order_date, customer_id
from 
	sales.orders
where
	customer_id in (
		select 
			customer_id
		from
			sales.customers
		where
			state = 'CA'
)
order by
	order_date desc
  
With claush(CTE): It serves as a function/versatile template to 
