# SimpleApi (Java, Spring Boot, Maven, Postgres)



**Дисциплина:** "Технологии разработки программного обеспечения"

**Лабораторная работа №1:** создание микросервиса на Spring Boot с базой данных

**Выполнил:** Шабанов Александр (МБД2032)

**Цель работы:** Создание API микросервиса с учетом совеременных архитектурных паттернов. Данный микросервис представляет собой CRUD-приложение, написанное на Java.

---
**Инструкция по сборке и запуску:**

>для работы потребуется установленный Docker. Инструкция написана на примере использования IntelliJ IDEA. Указанные ниже команды запускаются в терминале используемой IDE.

1. Сделайте клон репозитория
2. Запустите БД для теста приложения с помощью команды: `docker run -e POSTGRES_PASSWORD=root -p 5432:5432 postgres`
3. Запустите файлы data.sql и  schema.sql (src > resources) для конфигурации и настройки БД.
4. С помощью сборщика проектов Maven соберите образ для Docker. Для этого перейдте во вкладку Maven > simpleApi (название проекта) > Lifecycle > package (двойной клик). В папке target будет создан jar архив.
5. Произведите сборку образа Docker командой: `docker build . -t myapi:latest `
6. Запустите созданный Docker образ командой: `docker run -p 8080:8080 myapi:latest`

**Приложение запущено, теперь его можно протестировать с помощью curl команд:**
1. Получение hostname: ` curl http://localhost:8080/api/v1/status`
2. Получение списка всех позиций в таблице: ` curl http://localhost:8080/api/v1/products`
3. Получение определенной позиции из таблицы по его id (по-умолчанию счет начинается с 1000): `http://localhost:8080/api/v1/products/{id}`
4. Сохранение позиции в таблицу: `curl -X POST http://localhost:8080/api/v1/products -H "Content-Type:application/json" -d ' { "name": "item name", "brand": "brand", "price": 100, "details": "pieces" }'`
5. Удаление позиции по ее id: `curl -X DELETE http://localhost:8080/api/v1/products/{id}`


---

**Лабораторная работа №3:** CI/CD и деплой приложения в Heroku.

**Цель работы:** знакомство с CI/CD и его реализацией на примере Travis CI и Heroku.

Адрес развернутого приложения: https://prilka.herokuapp.com/api/v1/status

[![Build Status](https://travis-ci.org/A-simo/SimpleApi.svg?branch=main)](https://travis-ci.org/A-simo/SimpleApi)



