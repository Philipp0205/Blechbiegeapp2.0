# Recusive SQL Summary
## Exam 2011 

**Question:**

ProdStruct (partNr, partName, weight, containedIn)
 
List the names of all parts which are lighter than 1g and which are used somewhere
within parts named "Intel Pentium". 

---

**Answer:**
- Start with Parts of *Intel Pentium*. 
- Recursively add parts of parts. 
- Terminate when not more parts can bed added.
- Uses *UNION* not *UNION ALL* to avoid duplicates.
- Select all parts with wanted weight.  


```sql
WITH RECURSIVE Parts (partName, weight, containedIn) AS
	((SELECT partName, weight
	  FROM ProdStruct
	 containedIn = "Intel Plentium")
	 
	 UNION
	 SELECT in.containedIn, out.containedIn
	 WHERE in.containedIn = out.containedIn);
	 
SELECT partName, weight
FROM Parts
WHERE weight < 7;
```

--- 
Another approach

```sql
WITH RECURSIVE Parts (partName, weight, containedIn) AS
(SELECT partName, weight, containedIn)
FROM ProdStruct
WHERE containedIn IN
	(SELECT partNr 
	FROM ProStruct
	WHERE partName = "Intel Plentium")
UNION ALL 
(SELECT ProdStruct.partName, ProdStruct.weight
FROM ProdStruct, Parts
WHERE Ancestors.containedIn = Parts.partNr))

SELECT partName, weight
FROM Parts
WHERE weight < 7;
```
