#databases #data-science #data-engineering 

## Primary Key
- A special table column (or combination of columns) that uniquely identify each record
- Every row must have a PK and must be unique
- Often a self-incrementing number
- Cannot be null

![[Pasted image 20240603093121.png]]
## Foreign Key
- A  column (or combo) that provides a link between two tables
- Acts as a cross-reference between two tables as it references the PK of another table
- Must always reference a PK

![[Pasted image 20240603093350.png]]

## Join Clause
A JOIN clause is used to combine rows from wo or mroe tables, based on a relation betweem them.

### INNER JOIN

This will get a list of customers who placed an order:

```
select `name`, order_date, amount
from customers c
inner join orders o
on c.id = o.customer_id
```

|name|order_date|amount|
|---|---|---|
|John Smith|01/01/2020|100|
|Joe Bloggs|01/02/2020|200|

### LEFT JOIN

This left join will append information about orders on the customers table, regardless of whether a customer placed an order or not.

```
select `name`, order_date, amount
from customers c
left join orders o
on c.id = o.customer_id
```

| name       | order_date | amount |
| ---------- | ---------- | ------ |
| John Smith | 01/01/2020 | 100    |
| Jane Smith | NULL       | NULL   |
| Joe Bloggs | 01/02/2020 | 200    |
### RIGHT JOIN

This is a mirror of the left join on the previous slide which will get all orders, appended with customer information.

```
select `name`, order_date, amount
from customers c
right join orders o
on c.id = o.customer_id
```

|name|order_date|amount|
|---|---|---|
|John Smith|01/01/2020|100|
|Joe Bloggs|01/02/2020|200|
|NULL|01/02/2020|400|
|NULL|01/02/2020|500|
### FULL OUTER JOIN

A list of all records from both tables. MySQL has no concept of a full outer join so we have to play a trick here.

```
select `name`, order_date, amount
from
  orders o left join customers c
  on o.customer_id = c.id

union all -- don't remove duplicates

select `name`, order_date, amount
from
  orders o right join customers c
  on o.customer_id = c.id
```

## Functions
![[Pasted image 20240603103930.png]]

### Current_DATE
![[Pasted image 20240603104209.png]]

### COUNT
![[Pasted image 20240603104223.png]]

More can be found here: https://www.w3schools.com/sql/sql_ref_sqlserver.asp
[Web Archive] https://web.archive.org/save/https://www.w3schools.com/sql/sql_ref_sqlserver.asp
