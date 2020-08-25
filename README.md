 # Projeto - Web Services com Spring Boot e JPA / Hibernate

**Professor**: Dr. Nelio Alves

## Objetivos

- Criar projeto Spring Boot Java
- Implementar modelo de domínio
- Estruturar camadas lógicas: resource, service, repository
- Configurar banco de dados de teste (H2)
- Povoar o banco de dados
- CRUD - Create, Retrieve, Update, Delete
- Tratamento de exceções

## Tecnologias

![image](https://user-images.githubusercontent.com/56324728/91174184-4d62a180-e6b5-11ea-9c22-581dc0ed7da6.png)

## Domain Model

![image](https://user-images.githubusercontent.com/56324728/91174275-73884180-e6b5-11ea-93f6-76e43a953c34.png)

## Domain Instance

![image](https://user-images.githubusercontent.com/56324728/91174350-8864d500-e6b5-11ea-874b-5013bb69bad9.png)

## Logical Layers

![image](https://user-images.githubusercontent.com/56324728/91174418-9f0b2c00-e6b5-11ea-8eec-bdc01cce6ebe.png)

## Project created

**Checklist:**
- File -> New -> Spring Starter Project
  - Maven
  - Java 11
  - Packing JAR
  - Dependencies: Spring Web

## User entity and resource

**Basic entity checklist:**
- Basic attributes
- Associations (instantiate collections)
- Constructors
- Getters & Setters (collections: only get)
- hashCode & equals
- Serializable

## H2 database, test profile, JPA

**Checklist:**
- JPA & H2 dependencies
- application.properties
- application-test.properties
- Entity: JPA mapping

**Dependencies:**

```properties
<dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>

<dependency>
   <groupId>com.h2database</groupId>
   <artifactId>h2</artifactId>
   <scope>runtime</scope>
</dependency>
```

**application.properties:**

```properties
spring.profiles.active=test

spring.jpa.open-in-view=true
```

**application-test.properties:**

```properties
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.username=sa
spring.datasource.password=

spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
```

## JPA repository, dependency injection, database seeding

**Checklist:**
- UserRepository extends JPARepository<User, Long>
- Configuration class for "test" profile
- @Autowired UserRepository
- Instantiate objects in memory
- Persist objects

**Objects:**

```java
User u1 = new User(null, "Maria Brown", "maria@gmail.com", "988888888", "123456");
User u2 = new User(null, "Alex Green", "alex@gmail.com", "977777777", "123456");
```

## Service layer, component registration
