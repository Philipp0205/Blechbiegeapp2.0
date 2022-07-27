---
tags: programming, java, static, methods
---
[[!Java]]

One rule-of-thumb: ask yourself **"Does it make sense to call this method, even if no object has been constructed yet?" ** If so, it should definitely be static.

So in a class `Car` you might have a method:

```java
double convertMpgToKpl(double mpg)
```

...which would be static, because one might want to know what 35mpg converts to, even if nobody has ever built a `Car`. But this method (which sets the efficiency of one particular `Car`):

```java
void setMileage(double mpg)
```

...can't be static since it's inconceivable to call the method before any `Car` has been constructed.

(By the way, the converse isn't always true: you might sometimes have a method which involves two `Car` objects, and still want it to be static. E.g.:

```java
Car theMoreEfficientOf(Car c1, Car c2)
```

Although this could be converted to a non-static version, some would argue that since there isn't a "privileged" choice of which `Car` is more important, you shouldn't force a caller to choose one `Car` as the object you'll invoke the method on. This situation accounts for a fairly small fraction of all static methods, though.



