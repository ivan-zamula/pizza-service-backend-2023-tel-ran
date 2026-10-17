# Pizza Service: бэкенд (Tel-Ran, 2023)

[English](README.md) | [Русский](README.ru.md)

Pizza Service — мой дипломный проект в Tel-Ran. В этом репозитории находится Java-бэкенд: REST API для данных кафе, меню, поиска, сортировки и постраничной выдачи. [Frontend на React](https://github.com/ivan-zamula/pizza-service-frontend-2023-tel-ran) я также разработал самостоятельно.

## Интерфейс

![Список кафе Pizza Service с поиском и действиями управления](docs/images/pizza-service-cafe-list.jpeg)

Список кафе в React-интерфейсе, который я самостоятельно разработал для дипломного проекта в Tel-Ran.

## Стек и структура

Java 17, Spring Boot 3.0.2, Spring Web, Spring Data JPA, H2, Spring Security, Thymeleaf и springdoc OpenAPI.

| Путь | Содержимое |
| --- | --- |
| [controller](src/main/java/com/example/pizzaserviceproject/controller) | REST-эндпоинты кафе и пиццы |
| [entity](src/main/java/com/example/pizzaserviceproject/entity) | Модели кафе и пиццы |
| [repository](src/main/java/com/example/pizzaserviceproject/repository) | Запросы к базе данных |
| [src/test/java](src/test/java) | Тесты контроллеров, репозиториев и приложения |
| [doc](doc) | Описание проекта, схемы и документы API |

## Локальный запуск

Установите JDK 17 и Maven; команды `java` и `mvn` должны быть доступны в терминале.

```bash
git clone https://github.com/ivan-zamula/pizza-service-backend-2023-tel-ran.git
cd pizza-service-backend-2023-tel-ran
```

```bash
mvn spring-boot:run
```

Стандартный адрес бэкенда — `http://localhost:8080`. Эндпоинты можно просмотреть в [Swagger UI](http://localhost:8080/swagger-ui/index.html). Приложение использует H2 в памяти с настройками из [application.properties](src/main/resources/application.properties).

## Примеры API

| Метод | Путь | Назначение |
| --- | --- | --- |
| GET | `/cafe` | Список кафе |
| GET | `/cafe/full/{id}` | Кафе с его пиццами |
| POST | `/cafe/add` | Добавление кафе |
| PUT / DELETE | `/cafe/{id}` | Изменение или удаление кафе |
| GET | `/cafe/search?name={value}&address=` | Поиск кафе по названию |
| GET | `/pizza?cafe_id={id}` | Пиццы выбранного кафе |
| POST | `/pizza?cafeId={id}` | Добавление пиццы в кафе |
| GET / PUT / DELETE | `/pizza/{id}` | Просмотр, изменение или удаление пиццы |
| GET | `/pizza/search?name={value}` | Поиск пиццы по названию |
| GET | `/pizza/sort?column=name&direction=ASC` | Сортировка пиццы |
| GET | `/pizza/page?page=0&size=5` | Постраничный список пиццы |

Запросы на чтение можно выполнить напрямую:

```bash
curl http://localhost:8080/cafe
curl 'http://localhost:8080/pizza/page?page=0&size=5'
```

Для операций записи действуют правила доступа из [SecurityConfig.java](src/main/java/com/example/pizzaserviceproject/config/SecurityConfig.java). Формат тела запросов описан в OpenAPI. Схемы проекта находятся в [doc](doc).
