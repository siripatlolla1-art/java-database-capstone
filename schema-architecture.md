# Smart Clinic App - Architecture Design

## 1. Architecture Summary

The Smart Clinic Management System follows a **three-tier architecture** consisting of a **Presentation Layer**, **Application Layer**, and **Data Layer**. The system separates concerns effectively by using **Spring MVC controllers** and **REST APIs** for handling client requests, applying business logic in service classes, and managing data with both **MySQL** (via JPA) and **MongoDB** (via Spring Data MongoDB). The frontend interacts with the backend through Thymeleaf templates and REST calls, and the backend coordinates between services and the databases.

## 2. Request/Response Flow

1. A user interacts with the frontend via a browser or REST client.
2. The request is sent to the **Spring MVC controller** via a specific route (e.g., `/appointments`).
3. The controller delegates logic to a **Service Layer**, which applies business rules.
4. The service layer determines whether the request is for **relational data** (MySQL via JPA) or **document data** (MongoDB).
5. For relational data, the service interacts with **JPA repositories** to fetch/store data in **MySQL**.
6. For NoSQL documents, it uses **Spring Data MongoDB** to interact with **MongoDB** collections.
7. The data is returned to the service layer, which prepares the response.
8. The controller sends back a **view (Thymeleaf)** or **JSON (REST API)** response.
9. The frontend displays the data or confirms the action to the user.
