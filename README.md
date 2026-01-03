# 🚕 Drivz — Ride Booking Backend System

> **Drivz** is a **backend-only, microservices-based ride booking system** built with **Java & Spring Boot**, designed to closely mirror **real-world ride-hailing platforms**.
> It emphasizes **clean architecture, real-time communication, strict service ownership**, and **production-grade design practices**.

---

## ✨ Highlights

* 🧩 Microservices-based backend architecture
* 🔁 Event-driven & real-time workflows
* 📡 WebSocket-based live communication (SockJS)
* 🔐 JWT-based authentication & role-based authorization
* 🧠 Strict service ownership (no cross-service state mutation)
* ⚡ Redis GEO-powered driver matching
* 🧱 Production-ready MVP design

---

## 🧠 System Overview

* Backend-only ride booking platform
* Clear domain boundaries per service
* Centralized API Gateway & Service Registry
* Real-time ride & driver updates
* Crash-safe, idempotent operations
* Designed for scalability & extensibility

---

## 🛠 Tech Stack

| Category          | Technology             |
| ----------------- | ---------------------- |
| Language          | Java                   |
| Framework         | Spring Boot            |
| Architecture      | Microservices          |
| Security          | Spring Security, JWT   |
| API Style         | REST APIs + WebSockets |
| Real-Time         | SockJS                 |
| Database          | MySQL                  |
| Geo Queries       | Redis (GEO)            |
| Service Discovery | Service Registry       |
| API Gateway       | Centralized Gateway    |
| DB Migration      | Flyway                 |

---

## 🧱 Core Services (separate git repositories)

### 🚪 [API Gateway](https://github.com/mdseraj786/Drivz-Api-Gateway)

* Single entry point for all client requests
* Centralized authentication & validation
* Routes requests to internal services
* Hides internal service topology

---

### 🧭 [Service Registry](https://github.com/mdseraj786/Drivz-ServiceRegistry)

* Dynamic service discovery
* Eliminates hardcoded service URLs
* Enables horizontal scaling
* Improves fault tolerance

---

### 🔐 [Auth Service](https://github.com/mdseraj786/Drivz-Auth-Service)

* JWT-based stateless authentication
* Role-based authorization
* Supported roles:

  * `PASSENGER`
  * `DRIVER`
* Secures inter-service communication

---

### 📘 [Booking Service](https://github.com/mdseraj786/Drivz-Booking-Service) (System of Record)

* **Single source of truth** for rides
* Owns the complete ride lifecycle
* Enforces valid booking state transitions

**Responsibilities:**

* Ride creation
* Driver assignment
* OTP-based ride start
* Ride completion
* Fare calculation

---

### 🔌 [Socket Server](https://github.com/mdseraj786/Drivz-Socket-Server)

* Central real-time communication layer
* Built using **SockJS over WebSockets**
* Stateless & horizontally scalable

**Used for:**

* Driver assignment notifications
* Ride status updates
* Live ride visibility

---

### 📍 [Location Service](https://github.com/mdseraj786/Drivz-Location-Service)

* Real-time driver location tracking
* Uses **Redis GEO** for spatial queries
* Efficient nearest-driver discovery
* Handles frequent GPS updates
* Designed for replay tolerance & crash safety

---

### ⭐ [Review Service](https://github.com/mdseraj786/Drivz-Review-Service)

* Handles post-ride feedback
* One review per completed booking
* Rating (1–5) with optional comments
* Accessible only after ride completion

---

### 📦 [Common Library](https://github.com/mdseraj786/Drivz-Common-Library-Service)

* Shared utilities & models across services
* Contains:

  * Common DTOs
  * Enums (roles, booking states, payment states)
  * Exception handling utilities
* Prevents contract drift
* Reduces duplication

---

## 🔄 Communication Patterns

* **Client → System:** REST APIs via API Gateway
* **Inter-service:** REST APIs secured with JWT
* **Real-time updates:** WebSockets (SockJS)
* **Async workflows:** Event-driven messaging

---

## 🗺 Driver Matching & Location Logic

* Continuous driver location updates
* Redis GEO operations used to:

  * Store driver coordinates
  * Query nearest available drivers
* Optimized for low-latency ride assignment
* Fully decoupled from booking state logic

---

## 🔐 Security & Reliability

* JWT-based authentication
* Role-based authorization
* Idempotent APIs for critical operations
* Strict service ownership
* Crash-safe persistence
* No cross-service data mutation

---

## 🗃 Database Migration

* **Flyway** for schema migrations
* Versioned & controlled DB changes
* Ensures:

  * Schema consistency
  * Safe rollouts
  * Predictable upgrades

---

## ✅ Project Status

* ✔ Ride booking lifecycle — **Complete**
* ✔ Real-time driver tracking — **Complete**
* ✔ Review system — **Complete**
* ✔ Secure authentication — **Complete**

> The system is **MVP-complete** and structured for future production extensions.

---

## 🚀 Future Enhancements

* 💳 Payment gateway integration
* 👛 Wallet & refunds
* 📈 Surge pricing
* 🔔 Push notification service
* 🚦 Advanced driver availability rules
* 📊 Analytics & reporting

---

## 🧠 Key Takeaway

**Drivz** focuses on **correctness, scalability, and maintainability**, closely reflecting how **production-grade ride booking backends** are built.

This project is ideal for:

* Backend architecture learning
* Microservices & real-time systems practice
* Resume projects
* System design & backend interviews

---

🚕 *Designed to learn, scale, and evolve like a real-world ride-hailing platform.*
