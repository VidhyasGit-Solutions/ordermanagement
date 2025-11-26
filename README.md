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

orders (
id BIGINT PK,
customer_id BIGINT,
items JSON,
total_amount DECIMAL,
status VARCHAR,
created_at TIMESTAMP,
updated_at TIMESTAMP
)


---

## 🔄 Event Publishing

The service publishes events like:

- `order.created`
- `order.confirmed`
- `order.cancelled`
- `order.delivered`

Consumers: Inventory, Payment, Notification services.

---

## ⚙️ Configuration

```properties
server.port=8082
spring.application.name=order-service
eureka.client.service-url.defaultZone=http://localhost:8761/eureka
spring.datasource.url=jdbc:mysql://localhost:3306/ordersdb

Running Locally

Start Discovery Server
Start Kafka/Zookeeper
Run the service:

mvn spring-boot:run

mvn clean install

# Future Enhancements

Add saga pattern for end-to-end order lifecycle

Implement scalable event retry mechanisms

Introduce GraphQL API layer

Containerize using Docker & deploy via Kubernetes
