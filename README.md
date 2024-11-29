# EduVista Backend - Role-Based Access Control (RBAC) Implementation

## Description

This is the backend part of the **EduVista** platform, which includes user authentication, authorization, and role-based access control (RBAC). The project demonstrates the ability to secure a web application by implementing secure user management and access control based on roles such as **Admin** and **User**. 

This project was built to demonstrate the implementation of role-based access control in a backend API, along with secure user registration, login, and role-based permissions.

### Key Features:
- **User Authentication** (JWT)
- **Role-Based Access Control (RBAC)** (Admin and User roles)
- **Admin Role for User Management**
- **Protected Routes** for Admin users
- **Password Hashing** (using bcrypt)
- **MongoDB for data storage**

## Table of Contents
- [Technologies Used](#technologies-used)
- [Core Endpoints](#core-endpoints)
- [Getting Started](#getting-started)
- [Installation](#installation)
- [Usage](#usage)
- [Environment Variables](#environment-variables)
- [Security Features](#security-features)
- [License](#license)

## Technologies Used
- **Node.js** - Backend JavaScript runtime
- **Express.js** - Web framework for Node.js
- **MongoDB** - Database for storing user data
- **JWT** - For secure authentication and token management
- **bcrypt** - For hashing passwords
- **dotenv** - For managing environment variables

## Core Endpoints

### User Authentication and Management:
- **POST** `/api/users/register`: Registers a new user.
  - Request body: `{ "username": "user1", "email": "user1@example.com", "password": "password123" }`
  - Response: `201 Created`

- **POST** `/api/users/login`: Logs in a user and returns a JWT token.
  - Request body: `{ "email": "user1@example.com", "password": "password123" }`
  - Response: `200 OK` with token `{ "token": "jwt_token" }`
  
- **PUT** `/api/users/:id/role`: Updates a user's role (Admin only).
  - Request body: `{ "role": "admin" }`
  - Response: `201 Created`

### Protected Routes (with RBAC):
- **GET** `/api/protected`: Accessible only by authenticated users.
  - Requires JWT Token in the Authorization header.

- **GET** `/api/admin-only`: Accessible only by users with the 'admin' role.
  - This route is protected by RBAC and is accessible only by the Admin role.
  - Response: `200 OK` with `{ "message": "Welcome, Admin!" }`

## Getting Started

### Prerequisites
To run this project, you need the following:
- **Node.js** (v16 or higher)
- **MongoDB** (either local or MongoDB Atlas)
- **Redis** (for session storage or caching)
- **Gmail SMTP configuration** (for email functionality if using email-related features)

### Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/yourusername/eduvista-backend.git
    cd eduvista-backend
    ```

2. Install the dependencies:

    ```bash
    npm install
    ```

3. Set up environment variables. Create a `.env` file in the root directory and add your variables:

    ```bash
    PORT=8000
    DB_URL='mongodb+srv://<username>:<password>@<cluster>.mongodb.net/EduVista'
    JWT_SECRET='your_jwt_secret_key'
    ACCESS_TOKEN_EXPIRE=3600
    REFRESH_TOKEN_EXPIRE=86400
    SMTP_HOST='smtp.gmail.com'
    SMTP_PORT=465
    SMTP_MAIL='your_email@gmail.com'
    SMTP_PASSWORD='your_email_password'
    ```

4. Start the server:

    ```bash
    npm start
    ```

The server will run on `http://localhost:8000`.

## Usage

### Registering a New User
To register a new user, send a `POST` request to `/api/users/register` with the following JSON payload:

```json
{
  "username": "user1",
  "email": "user1@example.com",
  "password": "password123"
}
