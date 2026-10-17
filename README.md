# Pizza Service backend (Tel-Ran, 2023)

[English](README.md) | [Русский](README.ru.md)

Pizza Service is my diploma project at Tel-Ran. This repository contains the Java backend: a REST API for cafe details, menus, search, sorting and pagination. I also built the [React frontend](https://github.com/ivan-zamula/pizza-service-frontend-2023-tel-ran) myself.

## Preview

![Pizza Service cafe list with search and cafe management actions](docs/images/pizza-service-cafe-list.jpeg)

The cafe list in the React frontend I built for my Tel-Ran diploma project.

## Stack and structure

Java 17, Spring Boot 3.0.2, Spring Web, Spring Data JPA, H2, Spring Security, Thymeleaf and springdoc OpenAPI.

| Path | Content |
| --- | --- |
| [controller](src/main/java/com/example/pizzaserviceproject/controller) | Cafe and pizza REST endpoints |
| [entity](src/main/java/com/example/pizzaserviceproject/entity) | Cafe and pizza models |
| [repository](src/main/java/com/example/pizzaserviceproject/repository) | Database queries |
| [src/test/java](src/test/java) | Controller, repository and application tests |
| [doc](doc) | Project description, diagrams and API documents |

## Run locally

Install JDK 17 and Maven, with `java` and `mvn` available in your terminal.

```bash
git clone https://github.com/ivan-zamula/pizza-service-backend-2023-tel-ran.git
cd pizza-service-backend-2023-tel-ran
```

```bash
mvn spring-boot:run
```

The default backend address is `http://localhost:8080`. Browse endpoints in [Swagger UI](http://localhost:8080/swagger-ui/index.html). The application uses an in-memory H2 database configured in [application.properties](src/main/resources/application.properties).

## API examples

| Method | Path | Purpose |
| --- | --- | --- |
| GET | `/cafe` | List cafes |
| GET | `/cafe/full/{id}` | Read a cafe with its pizzas |
| POST | `/cafe/add` | Add a cafe |
| PUT / DELETE | `/cafe/{id}` | Update or delete a cafe |
| GET | `/cafe/search?name={value}&address=` | Search cafes by name |
| GET | `/pizza?cafe_id={id}` | List pizzas for a cafe |
| POST | `/pizza?cafeId={id}` | Add a pizza to a cafe |
| GET / PUT / DELETE | `/pizza/{id}` | Read, update or delete a pizza |
| GET | `/pizza/search?name={value}` | Search pizzas by name |
| GET | `/pizza/sort?column=name&direction=ASC` | Sort pizzas |
| GET | `/pizza/page?page=0&size=5` | Read a page of pizzas |

Read-only requests can be explored directly:

```bash
curl http://localhost:8080/cafe
curl 'http://localhost:8080/pizza/page?page=0&size=5'
```

Write operations use the access rules in [SecurityConfig.java](src/main/java/com/example/pizzaserviceproject/config/SecurityConfig.java). OpenAPI describes the request bodies. Project diagrams are in [doc](doc).
