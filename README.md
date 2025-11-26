# Order Management Service

The **Order Management Service** is a Spring Boot–based microservice responsible for handling the full lifecycle of customer orders—from creation to completion. It exposes REST APIs, publishes domain events, and integrates with other microservices through an event-driven architecture.

---

## 🚀 Features

- Create, update, and retrieve orders  
- Status management (Pending → Confirmed → In-Progress → Delivered)  
- Communication via REST and Kafka events  
- Integration with Inventory, Payment, and Notification services  
- Uses a centralized Discovery Server for service registry  
- Includes validations, exception handling, and logging

---

## 🏗️ Architecture Overview

- **Tech Stack:**  
  - Spring Boot  
  - Spring Web  
  - Spring Data JPA  
  - Spring Cloud (Eureka Client)  
  - Kafka (Producer)  
  - MySQL/PostgreSQL  
- **Pattern Used:**  
  - Microservices  
  - Event-Driven architecture  
  - Domain-driven design (DDD)  
  - Log aggregation + centralized config

---

## 📌 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/orders` | Create a new order |
| GET | `/orders/{id}` | Get order by ID |
| PUT | `/orders/{id}/status` | Update order status |
| GET | `/orders/customer/{customerId}` | Orders by customer |

---

## 🗄 Database Schema (Sample)

