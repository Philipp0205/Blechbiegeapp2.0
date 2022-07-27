[[1_Spring-Boot-Introduction-v.1.1.2.pdf]]

# Spring and Spring Boot 
## Spring
- Spring should be a lightweight alternative to Java EE and Java EE Beans 
- Focused on providing various ways to help manage business objects. 
- Can be considered as collection of sub frameworks -> *Layers* 
	- Spring AOP, Spring ORM, Spring Web MVC.
	
### Key features 
- Dependency injection
- Aspect oriented programming 
- Light in code but heavy in config
	- But any time spent in writing config is time spent not writing applications logic 
	

## **Spring Boot** 
### Idea 
- Many configs re-occur in different deployments 
	- Only the application logic itself is different 
- -> Re-Use Spring config possibilites and "boilerplate" them

### Essentials
- Provides all features of Spring and is easier to use
- Microservice-based framework

**Automatic Config**
- Everything is auto-configured, manual config only used for utilizing a particular functionality. 

**Start Dependencies**
- Built on top of the conventional spring framework. 

**Actuator**
- Insight of what is going inside Spring Boot app

### Pros 
- Automatic config 
- Production ready features like metrics, health checks, external config 
- No code generation 
- Embeds Tomcat etc. 

# Why frameworks? 
- They provide things for the developer that he/she does not need to define then.
- Provides therefore higher level of abstraction
- Less boilerplate code and more actual logic. 
- Makes things easier.

# Initializr
- Project Type 
	- Maven, Gradle 
- Langage 
	- Java, Kotlin, Groovy
- Spring Boot Version
- Project Metadata
	- Group, artifactid, name, description 
	- package name 
	- Packacking 
		- Jar, War
	- Java Version
		- 17,11,8
- Additional Dependencies 
	- e.g Actuator, Spring Web, 

# Actuator 
- Sub-project / layer 
- Provides various useful metrics
	- Health of app, configs, error page, version details 
- Metrics can be accessed through different endpoints
	- error, metric 

## REST Endpoints in Spring 
1. Annotate class with *@RestController* 
2. Annotate endpoints with *@GetMapping*, *@PostMapping*, *@DeleteMapping* etc.  

```java
@GetMapping(produces = "application/json", path = "/shoppingItem/")
    public List<ShoppingItem> getShoppingItems() {
}

@PostMapping(consumes = "application/json", produces = "application/json", path = "/shoppingItem")
    public ShoppingItem addShoppingItem(@RequestBody ShoppingItem item){
}

@DeleteMapping("/shoppingItem/{id}")
    public String deleteShoppingItem(@PathVariable long id){
}
```

# Learning 
## Objectives 
The student is able to 
- build anc configure an own Spring Boot app from scratch 
- REST end pint and CRUD operations 
- Optional: Logging , testing, actuator. 

## Exercises 
- Build a simple Spring Boot Microservice with the following starter dependencies: Web, Actuator
- Run the microservice and test the endpoint /actuator/health and /actuator/info
- Annotate the Microservice with @RestController and implement a "Hello, World!" method, which responds to an HTTP GET request.
- Add some basic "functionality" to make the service react to HTTP GET, POST calls (e.g. modify an internal list). Optional: PUT and DELETE
- Change the configuration to make the server run on port 8081 instead of 8080

## Review Questions 
- "WHY" Spring Boot? "WHY" Frameworks?
- What is the difference (and common aspects) between Spring and Spring Boot?
- What is the web page to start building your spring boot apps?
- What kind of things can you configure on that Initializr?
- What is the role of the Actuator?
