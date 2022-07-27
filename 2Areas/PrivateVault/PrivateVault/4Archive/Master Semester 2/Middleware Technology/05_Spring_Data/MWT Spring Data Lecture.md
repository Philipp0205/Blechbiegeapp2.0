[[4_Spring-Data-v.1.1.0.pdf]]

# Persistence 
Objects outlive the applications process that created them. 

## Why Persistence?
- 12 Factors: App process should have no state 
	- -> When app crashes state is gone. 
- If you want to scale the app -> CAP theorem -> you have to sync the state

## Software
**Java Persistence API** Defines a set of concepts that can be implemented

**Hibernate** Implementation of JPA

**Object-relational mapping (ORM)** Managing the conversion of software objects to interact with the tables and columns in a rel. database. 

# Spring Data 
- Spring-based programming model for data access. 
- Relational, non-relational databases, cloud based

## Advantages
- Powerful repository and custom object mapping abstractions 
- Dynamic query derivation from repository method names.

## Exercise
1. Spring Initializr with deps **PostgreSQL Driver** and **Spring Data JPA**. 
2. mvn package 
3. Create **Dockerfile** and **Docker compose file**
4. Running Spring Boot app and PostgeSQL with *docker compose up*
5. Create *@Entity*, *@Table* and *@Column*s
6. Run. 

*@Entity* tells hibernate that this class represents an object we can persist. 

*@Table* and *@Column* map the corresponding values to tables and cols in the database

### Example
```java
@Entity
@Table(name = "Items")
public class ShoppingItem {

	@Id
	@GeneratedValue
	@JsonProperty
	long id;
}
```

```java
public interface ShoppingItemRepository extends JpaRepository<ShoppingItem, Long> {
}
```



### Docker Compose 
- Tool for defining and running multi-container Docker app. 
- YAML file used for config

```yaml
version: '2'

services:
  app:
    image: 'docker-spring-boot-postgres:latest'
    build:
      context: .
    container_name: app
    depends_on:
      - db
    environment:
      - SPRING_DATASOURCE_URL=jdbc:postgresql://db:5432/compose-postgres
      - SPRING_DATASOURCE_USERNAME=compose-postgres
      - SPRING_DATASOURCE_PASSWORD=compose-postgres
      - SPRING_JPA_HIBERNATE_DDL_AUTO=update
          
  db:
    image: 'postgres:13.1-alpine'
    container_name: db
    environment:
      - POSTGRES_USER=compose-postgres
      - POSTGRES_PASSWORD=compose-postgres
```


**Spring Application**
```java
@SpringBootApplication
public class DemoApplication {
    @Autowired 
    private CustomerRepository repository; 
  
    @EventListener(ApplicationReadyEvent.class)
    public void runAfterStartup() {
        List allCustomers = this.repository.findAll(); 
        logger.info("Number of customers: " + allCustomers.size());
 
        Customer newCustomer = new Customer(); 
        newCustomer.setFirstName("John"); 
        newCustomer.setLastName("Doe"); 
        logger.info("Saving new customer..."); 
        this.repository.save(newCustomer); 
 
        allCustomers = this.repository.findAll(); 
        logger.info("Number of customers: " + allCustomers.size());
    }
}
```

### Objectives and exercises
- The student is able to build a Spring Boot application (or extend an existing one) with Spring Data configuration. 
- The exercise is to create an application, which performs CRUD operations on a database backend. 
- The database can either be in-memory (H2) or a (containerized) PostgreSQL. 
	- The Optional: Provide a docker-compose file to stand up a multi-container environment with application and database.
# Review Questions 
- "WHY" persistence? "WHY" persistence frameworks like JPA?
- Describe the necessary components to build an application with Spring Data? Potentially sketch
- What does the annotation @Entity do?
- How could docker compose help if you have a persistence-based application?
