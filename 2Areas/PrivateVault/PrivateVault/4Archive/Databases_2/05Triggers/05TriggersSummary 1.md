# Triggers Summary 

## Syntax

```sql
CREATE TRIGGER triggerName
BEFORE | AFTER <triggerEvent> ON <tableName>
[REFERENCING <oldOrNewValuesAliasList>]
[FOR EACH {ROW | STATEMENT}]
[WHEN (triggerCondition)]
<triggerBody>
```

## Exam 
### SS16
```sql
DELIMITER //
CREATE TRIGGER countStudents
AFTER INSERT ON Takes
FOR EACH ROW
BEGIN
	IF NEW.grade IS NOT NULL THEN
		UPDATE Class
		SET enrolled = enrolled + 1 
		WHERE NEW.classNr = classNr;
	END IF; 
END; 
//
```

Works in MySql: 
```sql
DELIMITER // 

CREATE TRIGGER countStudents2
AFTER INSERT ON Takes 
FOR EACH ROW
BEGIN
	WHEN (NEW.grade IS NOT NULL)
	UPDATE CLASS 
	SET enrolled = enrolled + 1
	WHERE NEW.classNr = classNr;
END;
//

```

Correct Trigger from the slides: 
```sql
CREATE TRIGGER countStudents2
AFTER INSERT ON Takes 
FOR EACH ROW
WHEN (NEW.grade IS NOT NULL)
	UPDATE CLASS 
	SET enrolled = enrolled + 1
	WHERE NEW.classNr = classNr;
```

Konstantinos Answer: 
```sql
CREATE TRIGGER NewData
AFTER INSERT ON Takes 
FOR EACH ROW 
UPDATE CLASS
SET enrolled = (
	SELECT COUNT(classNr) 
	FROM Takes 
	WHERE TAKES.classNr = NEW.classNr )
	WHERE Class.classNr = NEW.classNr;
```


#### Test 
```sql
create table Student ( 
	MatrNr int NOT NULL,
	name varchar(255),
	primary key(MatrNr)
);
```

```sql
create table Takes ( 
	MatrNr int,
	classNr varchar(255),
	grade int
);
```

```sql
create table Class ( 
	classNr int NOT NULL,
	enrolled int
);
```


