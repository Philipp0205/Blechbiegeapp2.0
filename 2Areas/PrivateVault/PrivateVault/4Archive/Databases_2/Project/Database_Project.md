- Develop a database with a small GUI written in Java or some other programming language. Use an appropriate interface (JDBC, ODBC,...) to inter-face between your application and your database. Chose a relational DBMS (Page 1)
- Data (a short explanation of the contents, size, purpose, and sources of your data set. Display a few (10-20) data records as an exa-mple on paper. Include the complete data in the electronic ver-sion. If this presents a problem, talk to me). (Page 4)
- Operations(what did you do with the data, what type of analysis did you per-form, list a few (at least 5) queries/use cases, include some screen shots) (Page 4)
- Include diagrams or pictures as necessary and useful, but the text should not consist only or mainly of those. (Page 5)

## Idea
- **Front end** 
	- One screen for ordering food 
		- food can be added to a shopping card
	- Checkout screen 
	- Maybe Delivery status screen 

- **Database**
	- Customer 
	- Order 
	- Bills
	- MenuItems
	- (DeliveryTrack)

## SQL Queries
- **Trigger**
	- When customer has more than five pending orders flag customer (fraud)
- **More complex sql queries**
	- Find customer of the month with the most orders 


```sql
CREATE TRIGGER findSusCustomer AFTER INSERT ON customer_order
	 
```

### Total number of orders
Create table
```sql
CREATE TABLE order_management (
	 TotalOrders INT
);
```

```sql
delimiter //
CREATE TRIGGER totalOrdersOfCustomer
AFTER INSERT ON customer_order FOR EACH ROW 
BEGIN
DECLARE updatecount INT; 
	set updatecount = (SELECT COUNT(*) FROM customer_order WHERE CustomerId = NEW.CustomerId);
    IF EXISTS (SELECT * FROM order_management WHERE CustomerId = NEW.CustomerId) THEN
		DELETE FROM order_management WHERE CustomerId = NEW.CustomerId;
	END IF;
	INSERT INTO order_management (CustomerId, Orders)
    VALUES (NEW.CustomerId, updatecount);
END //
```



## Source
[[projectfinal2021.pdf]]