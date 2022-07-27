# Long Parameter List
Refs: [[Refractoring Kurs]]
Tags: #refractoring 

---
![[Pasted image 20201123143448.png]]
More than four parameter for a method. 

### Recipe 1: Replace Parameter with Method Call
If some parameter are just results of method calls of another object, use  Replace Parameter with Method Call. 

**Problem**
```java
int basePrice = quantity * itemPrice;
double seasonDiscount = this.getSeasonalDiscount();
double fees = this.getFees();
double finalPrice = discountedPrice(basePrice, seasonDiscount, fees);
```

**Solution**
```java
int basePrice = quantity * itemPrice;
double finalPrice = discountedPrice(basePrice);
```

### Recipe 2: Presever Whole Object
Instead of passing a group of data received from another object as parameters, pass the object itself to the method, by using Preserve Whole Object.

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

### Recipe 3: Introduce Parameter Object
If there are several unrelated data elements, sometimes you can merge them into a single parameter object via Introduce Parameter Object.

![[IntroduceParameterObject.png]]
