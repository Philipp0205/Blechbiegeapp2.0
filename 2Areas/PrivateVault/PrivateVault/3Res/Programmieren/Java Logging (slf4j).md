---
tags: java, logging, programming, log4j, slf4j
---
[[!Java]]

# Add Maven Dependencies:
```xml
<!-- Login utilities -->
        <dependency>
            <groupId>org.apache.logging.log4j</groupId>
            <artifactId>log4j-api</artifactId>
            <version>2.7</version>
        </dependency>
        <dependency>
            <groupId>org.apache.logging.log4j</groupId>
            <artifactId>log4j-core</artifactId>
            <version>2.7</version>
        </dependency>
        <dependency>
            <groupId>org.apache.logging.log4j</groupId>
            <artifactId>log4j-slf4j-impl</artifactId>
            <version>2.7</version>
        </dependency>
        <dependency>
            <groupId>org.slf4j</groupId>
            <artifactId>log4j-over-slf4j</artifactId>
            <version>1.7.30</version>
        </dependency>
```

# Use logger
```java
private static final Logger logger = LoggerFactory.getLogger(Main.class);
...
logger.error("test");
logger.info("test");
logger.debug("test");
logger.warn("test");
...
```


# Resources
[Introductoin to Slf4j](https://www.baeldung.com/slf4j-with-log4j2-logback)
[Intro to Log4](https://www.baeldung.com/log4j2-appenders-layouts-filters)
