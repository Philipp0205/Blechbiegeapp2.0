#lecture-note |  #sql #databases #triggers

---

- **Definition**
	- Is a piece of code executed automatically in response to a specific event occurred on a table in a DB.
	- Invoked either before or after the following event:
		- INSERT, UPDATE, DELETE
- **Syntax**

```sql
CREATE TRIGGER trigger_name [BEFORE|AFTER] event
ON table_name trigger_type
BEGIN
  -- trigger_logic
END;
```
- To create triggers with several statements a DELIMITER  needs to be used
	- `DELIMITER //`
	- 