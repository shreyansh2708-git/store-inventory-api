# 🛒 Store Inventory REST API

[![Java](https://img.shields.io/badge/Java-17-ED8B00?style=flat-square&logo=openjdk&logoColor=white)](https://openjdk.org/projects/jdk/17/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.5-6DB33F?style=flat-square&logo=springboot&logoColor=white)](https://spring.io/projects/spring-boot)
[![Maven](https://img.shields.io/badge/Maven-Build-C71A36?style=flat-square&logo=apachemaven&logoColor=white)](https://maven.apache.org/)
[![H2](https://img.shields.io/badge/H2-In--Memory_DB-003545?style=flat-square)](https://h2database.com/)
[![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)](LICENSE)

A production-style RESTful backend built with **Java 17 and Spring Boot 3.5** to manage a store's product catalog — full CRUD, layered architecture, and live database inspection via H2 Console.

> Built to demonstrate core backend engineering skills: REST API design, JPA-based persistence, layered architecture, and clean separation of concerns.

---

## 🚀 Tech Stack

| Layer        | Technology                        |
|--------------|-----------------------------------|
| Language     | Java 17                           |
| Framework    | Spring Boot 3.5                   |
| ORM          | Spring Data JPA (Hibernate)       |
| Database     | H2 In-Memory                      |
| Build Tool   | Maven                             |
| API Testing  | Postman                           |

---

## 📐 Architecture
┌─────────────────────────────────────────────────┐

│                   Client (Postman / Frontend)    │

└──────────────────────┬──────────────────────────┘

│ HTTP Request

▼

┌─────────────────────────────────────────────────┐

│             Controller Layer                     │

│         ItemController.java                      │

│   (Route handling, request/response mapping)     │

└──────────────────────┬──────────────────────────┘

│

▼

┌─────────────────────────────────────────────────┐

│             Repository Layer                     │

│         ItemRepository.java                      │

│   (Spring Data JPA — auto-generated SQL queries) │

└──────────────────────┬──────────────────────────┘

│

▼

┌─────────────────────────────────────────────────┐

│             Database Layer                       │

│         H2 In-Memory (inventorydb)               │

│   (Persists Item entities during runtime)        │

└─────────────────────────────────────────────────┘---

## 📦 Features

- ✅ Add new products to the inventory
- ✅ Retrieve full catalog or fetch a single product by ID
- ✅ Full product update (name, price, stock)
- ✅ Partial stock update — simulates a real sale transaction
- ✅ Delete a product from the catalog
- ✅ Live database inspection via H2 Console

---

## 🗂️ Project Structure
src/main/java/com/walmart/inventory/

│

├── model/

│   └── Item.java                  # JPA Entity — maps to DB table

│

├── repository/

│   └── ItemRepository.java        # Spring Data JPA — zero boilerplate SQL

│

├── controller/

│   └── ItemController.java        # REST endpoints — routes all HTTP traffic

│

└── InventoryApplication.java      # Spring Boot entry point
---

## ⚙️ Running Locally

**Prerequisites:** Java 17+, Maven (bundled with IntelliJ)

```bash
# Clone the repository
git clone https://github.com/shreyansh2708-git/store-inventory-api.git

# Navigate into the project
cd store-inventory-api

# Run the application
./mvnw spring-boot:run
```

Server starts at: **`http://localhost:8080`**

---

## 🔌 API Reference

**Base URL:** `http://localhost:8080/api/items`

| Method   | Endpoint                          | Description                    |
|----------|-----------------------------------|--------------------------------|
| `POST`   | `/api/items`                      | Add a new product              |
| `GET`    | `/api/items`                      | Retrieve all products          |
| `GET`    | `/api/items/{id}`                 | Retrieve product by ID         |
| `PUT`    | `/api/items/{id}`                 | Full product update            |
| `PATCH`  | `/api/items/{id}/stock?quantity=X`| Update stock level only        |
| `DELETE` | `/api/items/{id}`                 | Remove a product               |

---

## 🧪 Sample Requests

**Create a product**
```http
POST /api/items
Content-Type: application/json

{
  "name": "Great Value Paper Towels",
  "price": 5.99,
  "quantityInStock": 100
}
```

**Response**
```json
{
  "id": 1,
  "name": "Great Value Paper Towels",
  "price": 5.99,
  "quantityInStock": 100
}
```

**Simulate a sale — update stock only**
```http
PATCH /api/items/1/stock?quantity=95
```

---

## 🗄️ H2 Console

Live database viewer available at: **`http://localhost:8080/h2-console`**

| Field    | Value                    |
|----------|--------------------------|
| JDBC URL | `jdbc:h2:mem:inventorydb`|
| Username | `sa`                     |
| Password | *(leave blank)*          |

---

## 🧠 Design Decisions

**Why Spring Data JPA over plain JDBC?**
JPA eliminates repetitive SQL boilerplate. `ItemRepository` extends `JpaRepository` and auto-generates all standard queries — the focus stays on business logic, not SQL mechanics.

**Why PATCH for stock updates instead of PUT?**
PUT replaces the full resource. Stock updates during sales transactions only need to touch one field — using PATCH accurately models this partial update semantics and avoids overwrite bugs.

**Why H2 for the database?**
Zero-config in-memory setup makes local development and testing fast. Migrating to PostgreSQL for production requires only a `pom.xml` dependency change and updated `application.properties` — the JPA layer handles the rest.

---

## 📸 Screenshots

| Add Product | Get All Products | Update Stock |
|-------------|-----------------|--------------|
| ![POST](<img width="1053" height="881" alt="Screenshot 2026-05-18 183843" src="https://github.com/user-attachments/assets/9c1c2060-d248-4d0d-be07-d4289638c11d" />
) | ![GET](<img width="1065" height="879" alt="Screenshot 2026-05-18 183918" src="https://github.com/user-attachments/assets/bd6c4d34-4415-45f0-aad4-380746bd106f" />
) | ![PATCH](<img width="1050" height="490" alt="Screenshot 2026-05-18 184026" src="https://github.com/user-attachments/assets/7cf5d869-25fa-4661-bca9-8a2f24e665b9" />
) |

---

## 👤 Author

**Shreyansh Mishra** — B.Tech CSE @ JUET Guna (2027)

Backend Engineering · Gen AI Systems · Spring Boot · FastAPI · LangChain

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/shreyansh-mishra-314a98284/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/shreyansh2708-git)
