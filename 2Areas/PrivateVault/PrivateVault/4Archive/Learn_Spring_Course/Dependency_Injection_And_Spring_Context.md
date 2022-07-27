# What is DI and how does it work in Spring? 
## What is DI? 
 There shuold 
- Class A has a dependency to class B when it interacts wit it in a way. 

There are two options how dependencys are created.
1. Class A instantiates Class B itself.
2. Class B comes from the outsode. (That is DI)

```java
public class A {
    private B bDependency;
  
    public A() {
        bDependency = new B();    
    }
}
```

```java
public class A {
    private B bDependency;
    
    public A(B bDependency) { // This is the important part 
        this.bDependency = bDependency;
    }
}
```

Injections is the simple process of injecting dependency B in the object of Type A.

DI is called Bean ind Spring.

## Why DI? 
Seperation of responsibility. 

## Types of Injection
- via raw field
- via constructor
- via setter

---
# The Basics of Java Configuraton and the Sprint Context
## Spring Applicatons Context
When the Spring application starts up, thie Applicaton Context bootstraps and starts instantiating the objects called *beans* in Spring terminology. 

## Contribution Beans to the Contect
We can create our own beans additional to the default beans already created by Spring itself. 

```java
@Configuration
public class PersistenceConfig {

    @Bean // this is the bean 
    public ProjectRepositoryImpl projectRepository() {
        return new ProjectRepositoryImpl();
    }
}
```

The `@Configuraton` Annotation indicates to Spring that this class need to be processed by the container beacuse it will contribute definitions to it. 

The `@Bean` Annotatoin is such an actual bean definiton. 

## Boot Higlight 
Spring loads all classes annotated with @Bean, @Component and @Configuration etc. 

# Defining Beans, Component Scanning and Bean Annotations
## Spring Component Scanning
The context can discover a bean on its own. This is called **Component scaning** and it's a different technique of achieving the same thing: adding beans to the context. 
This can be achieved with `@Component Scan`. Then for classes we want to define we can use *Sterotype Annotations*.

The simplest *Stereoptype* annotation we can use is `@Component`. **Spring wil scan for any classes annotated with `@Component` and will instantiate them as beans**.

**Example:**
```java
@Component
public class ProjectRepositoryImpl implements IProjectRepository {
    // ...
}
```

We are now expecting this to be picked up as bean.

## Other Strereoptype Annotations
There are other *Sterotype Annotation* but they use `@Component` under the hood. 
There are `@Repository` or `@Service`. They can be used to describe the bean better. 

---
# Lifecycle of a Bean
## Bean Lifecycle Phaes
1. Initialization phae
2. use phase
3. destroy phase

## Initalization Phae
Constists of two main stages: 
- loading bean definitons 
- instantiating beans

**Example** 
Create bean *AppConfig* Class:
```java
@Bean
public BeanA beanA() {
    return new BeanA();
}
```

Spring will run methods with `@PostConstruct` only once, just after the nit of the bean properties.

Add a method to the `BeanA` definition:
```java
@PostConstruct
public void post() {
    // 
}
```

```java

public class BeanB {

    public void initialize() {
        log.info("Custom initializer is called.");
    }
}
```

```java
@Bean(initMethod="initialize")
public BeanB beanB() {
    return new BeanB();
}
```

## Destroy Phase
This is the final phase of an applicaton. It's acrtivated whe the application context becomes eligible for garbage collection.

Destroy options are similar to the nit options. 

We have ha `@PreDestroy` annotaton the we cann add on a bean method, to indicate that method sould be executed before the bean get's destroyed. 

Similarly we can use the `destroyMethod` attribute to specifiy the `destroy()` method.

---
# Simple Wiring and Injections
---
# Exploring the Scropes of Spring Beans 
---
# The `BeanPostProcessor` and the `BeanFactoryProcessor` 
---
# The Spring Application Context
---
# Spring Wiring - `@Resource` and `@Inject`
---

