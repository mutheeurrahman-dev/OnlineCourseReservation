# 🎓 Online Course Reservation System

[![Java](https://img.shields.io/badge/Java-17+-ED8B00?style=flat-square&logo=openjdk&logoColor=white)](https://www.oracle.com/java/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-6DB33F?style=flat-square&logo=springboot&logoColor=white)](https://spring.io/projects/spring-boot)
[![Spring Data JPA](https://img.shields.io/badge/Spring%20Data-JPA-6DB33F?style=flat-square&logo=spring&logoColor=white)](https://spring.io/projects/spring-data-jpa)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=flat-square&logo=mysql&logoColor=white)](https://www.mysql.com/)
[![Maven](https://img.shields.io/badge/Maven-Build-C71A36?style=flat-square&logo=apachemaven&logoColor=white)](https://maven.apache.org/)

A backend RESTful Web Service for managing online course catalogs, student enrollments, and course reservations built using **Java**, **Spring Boot**, and **Spring Data JPA** with MySQL relational persistence.

---

## 🏛️ Architecture Overview

```mermaid
flowchart LR
    Client["Client / Frontend / Postman"] -->|HTTP REST Requests| Controller["CourseController<br/>(/courses)"]
    
    subgraph "Spring Boot Application"
        Controller --> Repository["CourseRepository<br/>(Spring Data JPA)"]
        Repository --> Model["Course Entity"]
    end
    
    subgraph "Relational Database"
        Repository -->|Hibernate ORM (JDBC)| MySQL[("MySQL Database<br/>course_reservation")]
    end
```

---

## 🚀 REST API Endpoints

| Method | Endpoint | Description | Request Body |
| :--- | :--- | :--- | :--- |
| `GET` | `/courses` | Retrieve all available courses | *None* |
| `POST` | `/courses` | Register a new course | `{"name": "Data Structures", "description": "Core CS", "instructor": "Prof. Alan"}` |
| `DELETE` | `/courses/{id}` | Remove a course offering by ID | *None* |

---

## 🛠️ Setup & Execution

### Prerequisites
- Java JDK 17 or higher
- MySQL Server (running on port 3306)
- Maven (or use included `mvnw`)

### 1. Database Configuration
Create the database in MySQL:
```sql
CREATE DATABASE course_reservation;
```

Configure your credentials in `src/main/resources/application.properties` (or supply environment variables):
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/course_reservation
spring.datasource.username=root
spring.datasource.password=your_db_password
```

### 2. Build and Run
```bash
# Build with Maven wrapper
./mvnw clean package

# Run the Spring Boot application
./mvnw spring-boot:run
```

The application will launch on **http://localhost:8080**.
