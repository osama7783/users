# 🔐 User Auth App – Java Spring Boot with REST APIs, ReactJS, PostgreSQL

[

## 📌 Project Overview

**User Auth App** is a full-stack authentication system built using **Java Spring Boot** (backend), **ReactJS** (frontend), and **PostgreSQL** (database). This practice project focuses on implementing a secure **JWT-based Authentication system**, including **access tokens**, **refresh tokens**, **role-based access control**, and **user profile management**.

It provides a foundational structure for any application requiring user login, registration, token refresh, profile management, and admin-based user operations.

---

## 🚀 Features

- 🔐 **JWT Authentication**: Implements secure access and refresh token strategy.
- 📝 **User Registration & Login**: Register new users and authenticate existing ones.
- ♻️ **Token Refresh**: Renew access token using refresh token seamlessly.
- 👤 **User Profile Management**: Get, update profile info (only for logged-in users).
- 🧑‍💼 **Admin Operations**: Admins can manage all users (CRUD).
- 🌐 **Role-based Routing**: Conditional rendering and routing based on roles.
- ❌ **404 Page**: User-friendly error page for invalid routes.
- ⛔ **403 Page**: Unauthorized page shown when access is forbidden.

---

## 🛠️ Tech Stack

### Backend

- 🔙 [Java Spring Boot](https://start.spring.io/)
- Spring Security + JWT
- Spring Data JPA
- PostgreSQL
- Swagger UI for API testing
- Maven for dependency management

### Frontend

- 🌐 [ReactJS](https://reactjs.org/)
- Axios for HTTP requests
- React Router DOM
- Context API (Auth state)
- TailwindCSS for styling
- React Toastify for alerts

### Database

- 🛢️ [PostgreSQL](https://www.postgresql.org/)

---

## 📸 Screenshots

### 🔄 Swagger API Flow

1. **All APIs Overview**

2. **Login with user `mahmud` (get Access & Refresh Tokens)**

3. **Authorize Swagger with Token**


4. **Access Protected `/profile` Endpoint**

5. **Admin Endpoint: All Users with Pagination (Page 1, 2 Users)**


### 💻 React Frontend

1. **Admin Dashboard**

2. **User Profile Page**

3. **Edit Profile Modal**

4. **Login Page**

5. **403 Forbidden Page**

6. **404 Not Found Page**

---

## 🏗️ Project Structure

### 🔙 Backend (Spring Boot)

```
users/
├── src/
│   ├── main/
│   │   ├── java/com/mahmudalam/userauth/
│   │   │   ├── controller/
│   │   │   ├── service/
│   │   │   ├── repository/
│   │   │   ├── model/
│   │   │   ├── dto/
│   │   │   ├── security/
│   │   │   └── UserAuthApplication.java
│   │   └── resources/
│   │       ├── application.properties
│   └── test/
├── pom.xml
```

### 🌐 Frontend (React)

```
user-auth-frontend/
├── public/
├── src/
│   ├── api/
│   ├── pages/
│   ├── components/
│   ├── routes/
│   ├── contexts/
│   ├── App.jsx
│   └── main.jsx
├── package.json
```

---

## 🔧 Installation & Setup

### 📌 Prerequisites

- **Java 21 LTS**
- **Node.js & npm**
- **PostgreSQL installed locally**

### 🔽 Backend Setup

```bash
cd spring-boot-userauth
```

#### 🧪 Configure Database

Edit `application.properties`:

```properties
spring.application.name=userauth
server.port=8082

# PostgreSQL DB settings
spring.datasource.driver-class-name=org.postgresql.Driver
spring.datasource.url=jdbc:postgresql://localhost:5432/bmudb
spring.datasource.username=postgres
spring.datasource.password=1234

# Hibernate / JPA settings
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect

# Spring Security
spring.security.user.name=mahmud
spring.security.user.password=mahmud

# Access/Refresh Token Secret
# Base64 encoded
# base64AccessSecretKeyMahmudAlamMahmudAlamMahmudAlam
# base64RefreshSecretKeyMahmudAlamMahmudAlamMahmudAlam
jwt.access.secret=YmFzZTY0QWNjZXNzU2VjcmV0S2V5TWFobXVkQWxhbU1haG11ZEFsYW1NYWhtdWRBbGFt
jwt.refresh.secret=YmFzZTY0UmVmcmVzaFNlY3JldEtleU1haG11ZEFsYW1NYWhtdWRBbGFtTWFobXVkQWxhbQ==
jwt.access.expiry=600000
jwt.refresh.expiry=1209600000
```

#### ▶️ Run the App

```bash
# Using Maven
mvn spring-boot:run
```

- App runs on: **[http://localhost:8082](http://localhost:8082)**
- Swagger UI: **[http://localhost:8082/swagger-ui.html](http://localhost:8082/swagger-ui.html)**

---

### 🌐 Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

App runs on: **[http://localhost:5173](http://localhost:5173)**

Create `.env` file:

```env
VITE_API_BASE = "http://localhost:8082"
```

---

## 📘 API Endpoints

### 🔐 Authentication ( `/api/auth` )

| Method | Endpoint         | Description                |
| ------ | ---------------- | -------------------------- |
| POST   | `/register`      | Register new user          |
| POST   | `/login`         | Login user, returns tokens |
| POST   | `/refresh-token` | Refresh access token       |

---

### 👤 User ( `/api/users` )

| Method | Endpoint         | Access Role  | Description                |
| ------ | ---------------- | ------------ | -------------------------- |
| GET    | `/users`         | ADMIN        | Get all users              |
| GET    | `/users/{id}`    | ADMIN        | Get user by ID             |
| POST   | `/users`         | ADMIN        | Create new user            |
| PUT    | `/users/{id}`    | ADMIN        | Full update                |
| PATCH  | `/users/{id}`    | ADMIN        | Partial update             |
| GET    | `/users/profile` | USER / ADMIN | Get current user's profile |
| PUT    | `/users/profile` | USER / ADMIN | Full profile update        |
| PATCH  | `/users/profile` | USER / ADMIN | Partial profile update     |

---

## 🔒 Security

- 🔐 Passwords are hashed securely using Spring Security.
- 🧾 Role-based access control (ADMIN / USER).
- ✅ JWT refresh & access token handling via HTTP-only headers/localStorage.
- ⛔ 401 & 403 responses handled gracefully on frontend.

---

## 🧪 Testing

```bash
mvn test
```

---

## 🔮 Future Improvements

- Add account verification via email
- Add password reset functionality
- Rate limiting for login attempts
- OAuth2 or social login support
- Deploy to Render / Vercel / Railway

---

## 🤝 Contributing

1. Fork the project
2. Create a new branch: `git checkout -b feature/AmazingFeature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature/AmazingFeature`
5. Open a Pull Request

---

## 🏆 Author

---

## 🙏 Acknowledgments

- Thanks to the **Spring Security** and **JWT** communities
- Inspired by modern authentication best practices

#### Happy coding! 🔐🚀
