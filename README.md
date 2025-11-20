# Workshop 5 & 6: Full Stack Student Manager (Spring Boot + Angular + Security)

## 📌 Overview
This project is a robust **Full Stack Student Management System**. It demonstrates the migration from a mock backend to a professional architecture using **Spring Boot** for the REST API and **PostgreSQL** for persistent data storage. 

In **Workshop 6**, the application was further enhanced with a complete security layer using **JWT (JSON Web Tokens)**, securing both the API endpoints and the Angular frontend routes.

## 🚀 Features

### Backend (Spring Boot)
- **RESTful API:** Full CRUD operations for managing students.
- **Persistent Storage:** Connected to a **PostgreSQL** database.
- **Security:** - Stateless authentication with **Spring Security**.
  - **JWT** generation and validation.
  - Password encryption using `BCrypt`.
  - Role-based architecture (User/Admin ready).
- **Validation:** Data integrity checks (e.g., Age > 20 years).

### Frontend (Angular Standalone)
- **Reactive Forms:** Robust forms for adding/editing students and logging in.
- **Authentication:** - Login & Registration pages.
  - **Auth Interceptor:** Automatically attaches the JWT token to every HTTP request.
  - **Auth Guard:** Protects routes (redirects unauthenticated users to login).
- **Modern Architecture:** Uses Angular Standalone components (no `AppModule`).

## 🛠️ Tech Stack
- **Backend:** Java 17, Spring Boot 3.3, Spring Data JPA, Hibernate, Spring Security.
- **Database:** PostgreSQL 16.
- **Frontend:** Angular 17+, TypeScript, Bootstrap 5.
- **Tools:** Maven, Postman, IntelliJ IDEA, VS Code.

---

## ⚙️ Setup & Installation

### 1. Prerequisites
* Java 17+ installed.
* PostgreSQL installed and running on port `5432`.
* Node.js & Angular CLI installed.

### 2. Database Configuration
Open a terminal (or pgAdmin) and create the database:
```sql
CREATE DATABASE studentsdb;

3. Backend Setup
Navigate to the student-api folder.

Open src/main/resources/application.properties and configure your PostgreSQL credentials:

Properties

spring.datasource.url=jdbc:postgresql://localhost:5432/studentsdb
spring.datasource.username=postgres
spring.datasource.password=YOUR_PASSWORD
spring.jpa.hibernate.ddl-auto=update
Run the server:

Bash

mvn spring-boot:run
Server starts at: http://localhost:8080

4. Frontend Setup
Navigate to the student-crud folder.

Install dependencies:

Bash

npm install
Start the application:

Bash

ng serve -o
Application opens at: http://localhost:4200

🔐 How to Use (Security)
1. Register a User
Since the database is empty initially, you must create a user to access the system.

Method: POST

URL: http://localhost:8080/api/auth/register

Body:

JSON

{
  "username": "admin",
  "password": "password123"
}
2. Login
You can now log in via the Angular interface at http://localhost:4200/login using these credentials.
🔗 API Endpoints
Public Endpoints
Method,Endpoint,Description
POST,/api/auth/register,Register a new user
POST,/api/auth/login,Login and receive a JWT Token
Protected Endpoints (Requires Bearer Token)
Method,Endpoint,Description
GET,/api/students,Retrieve all students
GET,/api/students/{id},Retrieve a student by ID
POST,/api/students,Create a new student (Validates Age > 20)
PUT,/api/students/{id},Update an existing student
DELETE,/api/students/{id},Delete a student

