---
tags: java, programming, intellij
---
Refs: [[!Java]]

When resources return null eg. 
```java
this.getClass().getRescours("...") // null
```

Add to maven
```xml
<build\>  
 <resources\>  
 <resource\>  
 <directory\>src/main/resources</directory\>  
 <filtering\>true</filtering\>  
 </resource\>  
 </resources\>
```



