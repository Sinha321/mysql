# mysql
### To select all the data from the table customers of the sql_store database
* SELECT * FROM sql_store.customers;
### Every row is called a record
### To select particular database
* USE sql_store
### To retrieve data last_name,first_name,points from a single table customers
* SELECT 
	  last_name,
    first_name,
    points,
    (points+10)*100 AS 'dis count'
FROM customers;
