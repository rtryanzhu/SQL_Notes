# SQL_Notes
# Subquery: Use another query as the condition in its superior query.
## Example
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
  
# With clause(CTE): It serves as a function/template.
## Example
with cte as( /*name the CTE chunk*/
    select distinct a.id
    from highschooler as a/*set alias for table highschooler*/
    join friend as b/*find mutual friends*/
    on a.id = b.id1
    join highschooler c
    on b.id2 = c.id
    where
    a.grade = c.grade/*and their grades are the same*/
)

select distinct a.name, a.grade
from highschooler as a
join friend as b
on a.id = b.id1
where
a.id not in(
  select id
  from cte
)

# Select value within a range
[a,b]: between a and b / where xxx >= a and xxx <= b
(a,b): where xxx > a and xxx < b
Add not at the front to exclud the range
