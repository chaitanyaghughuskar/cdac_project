
# CDAC Management Portal

## 📌 Overview
A full-stack web application for managing **student attendance using QR codes**, created as a CDAC project.

## 🚀 Project Highlights
- Role-based authentication using JWT
- QR-based attendance system
- Secure REST APIs with Spring Security
- MySQL database integration with JPA
- Separate dashboards for Admin, Faculty, and Student

## 🧰 Tech Stack
- **Backend:** Spring Boot, Spring Security (JWT), Spring Data JPA, MySQL  
- **Frontend:** React, Tailwind CSS, Axios, React Router  

## ✅ Prerequisites
- Java 17+  
- Maven  
- MySQL 8.0+  
- Node.js 18+  

## 🗄️ Database Setup
1. Create a MySQL database named `cdac_db`.  
2. Run the SQL script found at `backend/cdac_management_portal.sql` to initialize tables and roles:
```sql
source backend/cdac_management_portal.sql;
```
**Note:** This script creates the roles: ADMIN, FACULTY, STUDENT.

A default admin user is automatically created on first startup (via `DataInitializer.java`).

Default Admin Credentials:
- Email: `admin@cdac.in`
- Password: `admin123`

## Backend Setup (Spring Boot)
1. Navigate to `backend` directory.
2. Update `src/main/resources/application.properties` with your MySQL username and password.
3. Build and run:
   ```bash
   mvn clean install
   mvn spring-boot:run
   ```
4. Server runs on `http://localhost:8080`.

## Running in Eclipse IDE
1. Open Eclipse.
2. File -> Import -> Maven -> Existing Maven Projects.
3. Browse to `d:\cdac_project\backend`.
4. Finish.
5. Right-click on `CdacManagementPortalApplication.java` -> Run As -> Java Application.

## Login Credentials

### Default Admin
- **Email**: `admin@cdac.in`
- **Password**: `admin123`
*(Created automatically on first run)*

### Creating Other Users
1. Log in as Admin.
2. Use the "Register New User" form to create Faculty or Student accounts.


## Frontend Setup (React)
1. Navigate to `frontend` directory.
2. Install dependencies:
   ```bash
   npm install
   ```
3. Run development server:
   ```bash
   npm run dev
   ```
4. Access App at `http://localhost:5173`.

## Features & Usage

### 1. Admin (Role: ADMIN)
- Login with `admin@cdac.in` / `admin123`.
- Dashboard: Register new Users (Faculty, Students).

### 2. Faculty (Role: FACULTY)
- Login with registered faculty credentials.
- Dashboard: Generate QR Code for a subject lecture.
  - Input `Subject ID` (e.g., 1) and `Duration`.
  - Displayed QR Code contains a unique token.

### 3. Student (Role: STUDENT)
- Login with registered student credentials.
- Dashboard:
  - **Mark Attendance:** Scan QR code (or manually enter the token string displayed under the QR).
  - **Apply Leave:** Submit leave application.

## API Endpoints

### Authentication
- `POST /api/auth/signin` - Login

### Admin
- `POST /api/admin/register` - Create new user

### Faculty
- `POST /api/faculty/qr/generate` - Generate QR Session

### Student
- `POST /api/student/attendance/mark` - Mark attendance with token
- `POST /api/student/leave/apply` - Apply for leave

## 🏗️ Architecture
- Backend: REST APIs built using Spring Boot
- Frontend: React SPA consuming APIs via Axios
- Authentication: JWT-based token system
- Database: MySQL with Spring Data JPA
