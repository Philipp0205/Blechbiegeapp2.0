# Data Clumps
Refs: [[Refractoring Kurs]]
Tags: #refactoring #course-notes

---
![[Pasted image 20201123143424.png]]
Sometimes different part of the code contain identical groups of variables (such as parameter for conneting to a database). These clumps should be turned into their own classes.


## Recipe 1: Extract Class
If repeating data comprises the fields of a class, use Extract Class to move the fields to their own class.

![[3_Resources/attachments/ExtractClass.png]]


## Recipe 2: Introduce Parameter Object
If the same data clumps are passed in the parameters of methods, use Introduce Parameter Object to set them off as a class.

![[ParameterObject.png]]

## Recipe 3: Presever Whole Object
If some of the data is passed to other methods, think about passing the entire data object to the method instead of just individual fields. Preserve Whole Object will help with this.

**Problem**
```java
int low = daysTempRange.getLow();
int high = daysTempRange.getHigh();
boolean withinPlan = plan.withinRange(low, high);
```
**Solution**
```java
boolean withinPlan = plan.withinRange(daysTempRange);
```