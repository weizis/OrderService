# 🛍️ Order Service API
```
[![.NET](https://img.shields.io/badge/.NET-9.0-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)](https://dotnet.microsoft.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-316192?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Swagger](https://img.shields.io/badge/Swagger-UI-85EA2D?style=for-the-badge&logo=swagger&logoColor=black)](https://swagger.io/)
[![License](https://img.shields.io/badge/license-MIT-blue?style=for-the-badge)](LICENSE)
```
Backend-сервис для управления заказами. Проект демонстрирует чистую архитектуру и современные практики backend-разработки на .NET 9 с использованием PostgreSQL.

---

## ✨ Возможности

- ✅ **Полный CRUD** для заказов (Create, Read, Update, Delete)
- ✅ **RESTful API** с правильными HTTP-методами и кодами ответов
- ✅ **PostgreSQL** + Entity Framework Core (Code First подход)
- ✅ **Swagger UI** для тестирования и документации API
- ✅ **Миграции базы данных** (автоматическое создание/обновление схемы)
- ✅ **Валидация данных** на уровне модели

---

## 🛠️ Технологический стек

| Технология | Назначение |
|------------|------------|
| **.NET 9** | Основная платформа |
| **ASP.NET Core Web API** | REST API |
| **Entity Framework Core 9** | ORM для работы с БД |
| **PostgreSQL 15** | База данных |
| **Swagger / OpenAPI** | Документация API |
| **Git** | Контроль версий |

---

## 📊 Модель данных

```csharp
public class Order
{
    public int Id { get; set; }                    // Уникальный идентификатор
    public string CustomerName { get; set; }        // Имя клиента
    public string ProductName { get; set; }         // Название товара
    public int Quantity { get; set; }                // Количество
    public decimal Price { get; set; }               // Цена
    public DateTime OrderDate { get; set; }          // Дата заказа (UTC)
    public string Status { get; set; } = "New";      // Статус (New/Processing/Completed/Cancelled)
}
```

---

## 📋 API Endpoints

| Метод | URL | Описание |
|-------|-----|----------|
| **GET** | `/api/Orders` | Получить все заказы |
| **GET** | `/api/Orders/{id}` | Получить заказ по ID |
| **POST** | `/api/Orders` | Создать новый заказ |
| **PUT** | `/api/Orders/{id}` | Обновить существующий заказ |
| **DELETE** | `/api/Orders/{id}` | Удалить заказ |

---

## 🔄 Примеры запросов

### Создание заказа (POST)

**Request:**
```json
{
  "customerName": "Иван Петров",
  "productName": "Ноутбук ASUS",
  "quantity": 1,
  "price": 75000.00,
  "status": "New"
}
```

**Response (201 Created):**
```json
{
  "id": 1,
  "customerName": "Иван Петров",
  "productName": "Ноутбук ASUS",
  "quantity": 1,
  "price": 75000.00,
  "orderDate": "2026-02-19T17:46:01.328028Z",
  "status": "New"
}
```

### Получение всех заказов (GET)

**Response (200 OK):**
```json
[
  {
    "id": 1,
    "customerName": "Иван Петров",
    "productName": "Ноутбук ASUS",
    "quantity": 1,
    "price": 75000.00,
    "orderDate": "2026-02-19T17:46:01.328028Z",
    "status": "New"
  }
]
```

---

## 🗂️ Структура проекта

```
OrderService/
├── 📁 Controllers/
│   └── OrdersController.cs           # API контроллеры
├── 📁 Data/
│   └── AppDbContext.cs                # Работа с БД
├── 📁 Models/
│   └── Order.cs                       # Сущности
├── 📁 Migrations/                      # Миграции EF Core
├── 📄 Program.cs                       # Точка входа
├── 📄 appsettings.json                 # Конфигурация
└── 📄 OrderService.csproj              # Файл проекта
```

---

## 🚀 Запуск проекта локально

### Предварительные требования

- [.NET 9 SDK](https://dotnet.microsoft.com/download/dotnet/9.0)
- [PostgreSQL 15](https://www.postgresql.org/download/)
- [Visual Studio 2022](https://visualstudio.microsoft.com/) или [VS Code](https://code.visualstudio.com/)
- [Git](https://git-scm.com/)

### Пошаговая инструкция

**1. Клонировать репозиторий**

```bash
git clone https://github.com/weizis/OrderService.git
cd OrderService
```

**2. Настроить подключение к БД**

Открой `appsettings.json` и укажи свой пароль от PostgreSQL:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Host=localhost;Port=5432;Database=ordersdb;Username=postgres;Password=your_password_here"
  }
}
```

**3. Создать базу данных и применить миграции**

```bash
dotnet ef database update
```

*Если нет dotnet ef:*
```bash
dotnet tool install --global dotnet-ef
```

**4. Запустить приложение**

```bash
dotnet run
```

**5. Открыть Swagger UI**

Перейди по адресу: `https://localhost:7037/swagger`

---

## 🔜 Планы по развитию

- [ ] **🐳 Docker-контейнеризация** — запуск API и PostgreSQL в контейнерах
- [ ] **🐙 Docker Compose** — оркестрация нескольких контейнеров одной командой
- [ ] **🧪 Юнит-тесты** — покрытие CRUD операций xUnit тестами
- [ ] **📝 Логирование** — добавление Serilog для логирования запросов
- [ ] **✅ Валидация** — FluentValidation для моделей
- [ ] **🚨 Обработка ошибок** — глобальный middleware для обработки исключений
- [ ] **📄 Пагинация** — для GET /api/orders
- [ ] **🔍 Фильтрация и сортировка** — по дате, статусу, цене

---

## 📄 Лицензия

Этот проект распространяется под лицензией MIT. Смотри файл [LICENSE](LICENSE) для деталей.
