# ModCraft Studio — Java Order Decision System & Embedded Web Server

Гибридный проект на **Java**, объединяющий консольную систему расчёта заказов игровых модов (`Main`, `Menu`, `DecisionSystem`, `Validation`, `Report`) и встроенный веб-сервер на стандартном JDK `com.sun.net.httpserver.HttpServer`, обслуживающий адаптивный интерфейс на порту `8088`.

## Архитектура проекта

- **Консольное ядро и бизнес-логика (`src/`):**
  - `Main.java` — точка входа, авторизация пользователя и запуск навигации.
  - `Menu.java` — маршрутизация разделов и интерактивное консольное меню.
  - `DecisionSystem.java` — расчёт стоимости услуг, скидок, статуса и оценки безопасности заказа по многофакторным условиям.
  - `Validation.java` & `Report.java` — валидация пользовательского ввода и генерация структурированного отчёта.
- **Встроенный веб-сервер и UI (`src/WebServer.java`, `web/`):**
  - Работает на чистом JDK (`HttpServer` на `http://localhost:8088`) без внешних зависимостей (Spring/Maven).
  - Отдаёт статический веб-интерфейс магазина (`web/index.html`) и дашборд (`web/fifine-dashboard.html`).
- **Дополнительный модуль (`LibraryManagement/`):**
  - Консольное приложение на C# (`Book`, `Reader`, `Library`) для управления библиотечным фондом.

## Компиляция и запуск (Java 17+)

```bash
javac -d out src/*.java
# Запуск встроенного веб-сервера на http://localhost:8088
java -cp out WebServer
# Либо запуск консольной системы принятия решений
java -cp out Main
```
