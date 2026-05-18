# 🛒 Store Inventory REST API

A production-style RESTful backend API built with **Java** and **Spring Boot** to manage a store's product catalog — supporting full CRUD operations on inventory items including product name, pricing, and real-time stock level tracking.

---

## 🚀 Tech Stack

| Layer | Technology |
|-------|-----------|
| Language | Java 17 |
| Framework | Spring Boot 3.5 |
| ORM | Spring Data JPA (Hibernate) |
| Database | H2 In-Memory Database |
| API Testing | Postman |
| Build Tool | Maven |

---

## 📦 Features

- ✅ Add new products to the inventory
- ✅ View all products or fetch a single product by ID
- ✅ Update full product details (name, price, stock)
- ✅ Update only the stock level (simulates a sale transaction)
- ✅ Delete a product from the catalog
- ✅ Live database viewer via H2 Console

---

## 🗂️ Project Structure

```
src/main/java/com/walmart/inventory/
│
├── model/
│   └── Item.java              # Entity class (maps to DB table)
│
├── repository/
│   └── ItemRepository.java    # JPA Repository (auto-generated SQL)
│
├── controller/
│   └── ItemController.java    # REST API endpoints
│
└── InventoryApplication.java  # Main entry point
```

---

## ⚙️ How to Run Locally

**Prerequisites:**
- Java 17+
- Maven (comes bundled with IntelliJ)

**Steps:**

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/store-inventory-api.git

# Navigate into the project
cd store-inventory-api

# Run the application
./mvnw spring-boot:run
```

The server starts at: `http://localhost:8080`

---

## 🔌 API Endpoints

Base URL: `http://localhost:8080/api/items`

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/items` | Add a new product |
| GET | `/api/items` | Get all products |
| GET | `/api/items/{id}` | Get product by ID |
| PUT | `/api/items/{id}` | Update full product details |
| PATCH | `/api/items/{id}/stock?quantity=X` | Update stock level only |
| DELETE | `/api/items/{id}` | Delete a product |

---

## 🧪 Sample API Usage

**Add a product:**
```json
POST /api/items
Content-Type: application/json

{
  "name": "Great Value Paper Towels",
  "price": 5.99,
  "quantityInStock": 100
}
```

**Response:**
```json
{
  "id": 1,
  "name": "Great Value Paper Towels",
  "price": 5.99,
  "quantityInStock": 100
}
```

**Update stock after a sale:**
```
PATCH /api/items/1/stock?quantity=95
```

---

## 🗄️ H2 Database Console

While the app is running, view the live database at:

```
http://localhost:8080/h2-console
```

| Field | Value |
|-------|-------|
| JDBC URL | `jdbc:h2:mem:inventorydb` |
| Username | `sa` |
| Password | *(leave blank)* |

---

## 📸 Screenshots

*(Add Postman screenshots here)*
<img width="600" height="600" alt="Screenshot 2026-05-18 183918" src="https://github.com/user-attachments/assets/cf460c5e-522d-4f65-8c62-9987ba10078d" />
<img width="600" height="600" alt="Screenshot 2026-05-18 183843" src="https://github.com/user-attachments/assets/eb9062be-0c5f-486e-8a93-7f49acff5a97" />
<img width="600" height="490" alt="Screenshot 2026-05-18 184026" src="https://github.com/user-attachments/assets/49345ac8-d40c-4042-bd15-9059f6038763" />

---

## 👤 Author

**Shreyansh Mishra**  
B.Tech CSE, Jaypee University of Engineering and Technology (2027)  
[LinkedIn](https://www.linkedin.com/in/shreyansh-mishra-314a98284/) | [GitHub](https://github.com/shreyansh2708-git)
