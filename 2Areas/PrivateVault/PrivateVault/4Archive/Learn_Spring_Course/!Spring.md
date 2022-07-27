---
tags: index, java, spring
---

[[Dependency_Injection_And_Spring_Context]]
[[Project_Configuration]]

## Application Context
Before we can understand the value of _@Component_, we must first understand a little bit about the [Spring _ApplicationContext_](https://www.baeldung.com/spring-application-context). This is where Spring holds instances of objects that it has identified to be managed and distributed automatically. These are called beans. Bean management and the opportunity for dependency injection are some of Spring's main features.

Using the [Inversion of Control principle](https://www.baeldung.com/inversion-control-and-dependency-injection-in-spring), **Spring collects bean instances from our application and uses them at the appropriate time.** We can show bean dependencies to Spring without needing to handle the setup and instantiation of those objects.

The ability to use annotations like [_@Autowired_](https://www.baeldung.com/spring-autowire) to inject Spring-managed beans into our application is a driving force for creating powerful and scalable code in Spring.

So, how do we tell Spring about the beans we would like for it to manage for us? **We should take advantage of Spring's automatic bean detection by using stereotype annotations on our classes.**

Source: https://www.baeldung.com/spring-component-annotation

### Warum wir in Harcon nicht @Component benutzen sondern eine "manuelle" Konfiguration
Die `@Component` annoation reicht nicht aus da wir nicht nur die Bean detecten wollen sondern auch gleich die `loadController` Methode ausführen wollen.
Deshalb haben wir eine separate `ControllerConfiguration`. 

## @Component
_@Component_ is an annotation that allows Spring to automatically detect our custom beans.

In other words, without having to write any explicit code, Spring will:

-   Scan our application for classes annotated with _@Component_
-   Instantiate them and inject any specified dependencies into them
-   Inject them wherever needed

However, most developers prefer to use the more specialized stereotype annotations to serve this function.

## @Autowired
_@Autowired_  **allows Spring to resolve and inject collaborating beans into our bean.**

Source: https://www.baeldung.com/spring-autowire

tem
TAB_016_999_A

