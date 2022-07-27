

    
CREATE TABLE order(
	id INT Primary Key,
	order_type VARCHAR(100),
	order_time DATETIME,
	number_persons INT,
	order_filled_by VARCHAR(100),
	customer_id, INT Foreign Key References customer(id)
);