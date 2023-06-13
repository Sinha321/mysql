# mysql
## SELECT CLAUSE
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
## WHERE CLAUSE
* equal to ==
* not equal to != , <>
* greater than > 
* less tahn <
* greater than equal to >=
* less than equal to <=
### To select data from the table customers of the sql_store database where points is greater than 3000
* SELECT *
FROM customers
WHERE points>3000
* The strings or the dates should be enclosed in quotation mark
## AND OPERATOR
* SELECT *
FROM customers
WHERE birth_date >'1990-01-01' AND points >1000
## OR OPERATOR
* SELECT *
FROM customers
WHERE birth_date >'1990-01-01' OR points >1000

* SELECT *
FROM customers
WHERE birth_date >'1990-01-01' OR (points >1000 AND state= 'VA')

## NOT OPERATOR
* SELECT *
FROM customers
WHERE  NOT (birth_date >'1990-01-01' OR points >1000)
 * From the order_items table get the items for order number 6 where the total price is greater than 30
 * SELECT * FROM order_items WHERE order_id = 6 AND quantity * unit_price  > 30
## IN OPERATOR
* SELECT * FROM customers WHERE state NOT IN('VA' , 'FL' , 'GA')
## BETWEEN OPERATOR
* SELECT * FROM customers WHERE points BETWEEN 1000 AND 3000
* Return customers born  between 01-01-2000 and 01-01-2007
* SELECT * FROM customers BETWEEN 2000-01-01 AND 2007-01-01

## LIKE OPERATOR
* Get The customers whose last name starts with B
* SELECT * FROM customers WHERE last_name LIKE 'B%'
* Get The customers whose last name can have B anywhere
* SELECT * FROM customers WHERE last_name LIKE '%B%'
* Get The customers whose last name starts with b and should have y  anywhere
** Get The customers whose last name starts can have B anywhere
* * Get The customers whose last name starts can have B anywhere
* SELECT * FROM customers WHERE last_name LIKE '%B%'
* % Denotes any number of character 
* _ Denotes the single character
* Get the customers whose address contains trail or avenue
* SELECT * FROM cuatomers WHERE address LIKE '%TRAIL%' OR address LIKE '%AVENUE%'
## REGEXP OPERATOR (REGULAR EXPRESSION)
* SELECT * FROM customers WHERE last_name REGEXP 'B'
* Get The customers whose last name must starts with Brush
* SELECT * FROM customers WHERE last_name REGEXP '^Brush'
* Get The customers whose last name must ends with Brush
* SELECT * FROM customers WHERE last_name REGEXP 'Brush$'
* Get The customers whose last name can have Brush or field or rose 
* SELECT * FROM customers WHERE last_name REGEXP 'brush|field|rose
* * Get The customers whose last name must have e with starting of i or g or m
* SELECT * FROM customers WHERE last_name REGEXP '[gim]e'     
* Get The customers whose last name must have e with starting of a-h
* SELECT * FROM customers WHERE last_name REGEXP '[a-h]e' 
* NOTES : 
* ^ beginning
* $ end
* | logical or
* [abcd]e = ae|be|ce|de
* [a-z]e
## IS NULL OPERATOR
* Get The customers whose phone number is missing
* SELECT * FROM customers WHERE phone IS NULL
*  Get The customers whose Phone number is not missing
* SELECT * FROM customers WHERE phone IS NOT NULL
## ORDER BY CLAUSE
* PRIMARY KEY COLUMN by which the table is sorted by default
* SELECT * FROM customers ORDER BY first_name DESC
* Get the customers ordered by their state and then first name
* SELECT * FROM customers ORDER BY state DESC , first_name
* Get the first name ,last name  and points with 10 as data orderd by points and first name from the customer the table
* SELECT first_name,last_name, 10 AS points FROM customers ORDER BY points, first_name
* Get data from table order items where order id iseual to 2 sorted by price in descending order
* SELECT *, unit_price*quantity AS total FROM order_items WHERE order_id=2 ORDER BY unit_price*quantity DESC
* or
* SELECT *, unit_price*quantity AS total FROM order_items WHERE order_id=2 ORDER BY total DESC
## LIMIT CLAUSE : limit the records returned from the query
* SELECT * FROM customers LIMIT 3  :  LIMITS TO 3 ROWS ONLY
* SELECT * FROM customers LIMIT 6,3  :  LIMITS 1st 6 ROWS and then prints NEXT 3 ROWS
* Get the top three loyal customers
* SELECT * FROM customers ORDER BY points DESC  LIMIT 3
##  INNER JOINS : SELECTION OF COLUMNS FROM MULTIPLE TABLES
* combine orders table with the customers table (JOIN: INNER JOIN | OUTER JOIN ) INNER Keyword is optional 
* ON PHRASE : on what basis do we want to join the table ,if we put these two tables next to each other we want to line up the records such that the customers id are equal
* SELECT * FROM orders JOIN customers ON orders.customer_id = customers.customer_id
* SELECT order_id,o.customer_id,first_name,last_name FROM orders o JOIN customers c ON o.customer_id = c.customer_id
* Join the order items table with the products table 
* SELECT * FROM order_items oi JOIN products p ON oi.product_id = p.product_id
*  SELECT order_id,oi.product_id,quantity,oi.unit_price FROM order_items oi JOIN products p ON oi.product_id = p.product_id
*  
