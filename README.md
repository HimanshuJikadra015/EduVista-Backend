# EduVista - Backend

## Overview

EduVista is a Learning Management System (LMS) that provides a secure and robust platform for managing courses, students, and instructors. This backend API ensures that users can register, log in, and access their resources based on their roles (Admin, User).

### Tech Stack:
- **Backend**: Node.js with Express.js
- **Database**: MongoDB (NoSQL)
- **Authentication**: JWT (JSON Web Tokens) for secure session management
- **Social Authentication**: Google and GitHub OAuth
- **RBAC**: Role-Based Access Control (Admin, User)
- **Email Service**: Nodemailer (Gmail SMTP) for user registration and activation
- **Redis**: Session caching
- **Cloud Storage**: Cloudinary for file uploads
- **Environment Configuration**: `.env` file for managing sensitive information

---

## Installation

### Prerequisites:
1. Node.js >= 14.x
2. MongoDB running (or a cloud database like MongoDB Atlas)
3. Redis server running (or use Redis cloud services like Upstash)

### Steps to Run the Project:

1. Clone the repository:
   ```bash
   git clone https://github.com/HimanshuJikadra015/EduVista-Backend.git
   cd EduVista-Backend

2. Install dependencies:
   ```bash
   npm install

3. Create a .env file in the root of the project and add the following environment variables:
   ```bash
   PORT=8000
   ORIGIN=http://localhost:3000/
   NODE_ENV=development
   DB_URL=mongodb://localhost:27017/eduvista
   CLOUD_NAME=your-cloud-name
   CLOUD_API_KEY=your-cloud-api-key
   CLOUD_SECRET_KEY=your-cloud-secret-key
   REDIS_URL=your-redis-url
   ACTIVATION_SECRET=your-activation-secret
   ACCESS_TOKEN=your-access-token-key
   REFRESH_TOKEN=your-refresh-token-key
   SMTP_HOST=smtp.gmail.com
   SMTP_PORT=465
   SMTP_SERVICE=gmail
   SMTP_MAIL=your-email@gmail.com
   SMTP_PASSWORD=your-email-password

4. Start the server:
   ```bash
   npm start


## Authentication & Authorization

### JWT Authentication:
- **Login**: After successful authentication, a JWT token is provided to the user. This token should be included in the headers of all subsequent requests to protected routes.
- **Usage**: To access protected routes, include the token in the `Authorization` header:
  ```bash
  Authorization: Bearer <token>

### Social Authentication:
- **Google Auth**: Users can authenticate using Google.
- **Github Auth**: Users can authenticate using GitHub.

### Role-Based Access Control (RBAC):
- Users are assigned roles (admin or user) during registration. Based on these roles, access to certain routes is allowed or restricted.

### Protected Routes:
- Routes are secured using the isAuthenticated middleware to ensure the user is logged in, and the authorizeRoles middleware to ensure the user has the appropriate role. Admin-only routes require the admin role.

## API Endpoints

### User Authentication

#### POST /api/auth/register
- Registers a new user.
- **Request body**:
  ```json
  { "email": "user@example.com", "password": "password" }
- **Response**: 200 OK with
  ```json
  { "message": "Registration successful" }

#### POST /api/auth/login
- Logs in the user and returns a JWT token.
- **Request body**:
  ```json
  { "email": "user@example.com", "password": "password" }
- **Response**: 200 OK with
  ```json
  { "token": "<JWT_TOKEN>" }

#### POST /api/auth/google
- Google OAuth login.
- **Response**: 200 OK with
  ```json
  { "token": "<JWT_TOKEN>" }

#### POST /api/auth/github
- GitHub OAuth login.
- **Response**: 200 OK with
  ```json
  { "token": "<JWT_TOKEN>" }

### User Management (Admin-Only Routes)

#### POST /api/admin/update-role/:id
- Update the role of a user (admin or user).
- Requires: isAuthenticated, authorizeRoles("admin")
- **Request body**:
  ```json
  { "role": "admin" }
- **Response**: 200 OK with
  ```json
  { "message": "User role updated successfully" }

### Profile & Settings

#### GET /api/profile
- Fetch the authenticated user's profile.
- Requires: isAuthenticated
- **Response**: 200 OK with
  ```json
  { "user": { "email": "user@example.com", "role": "user" } }
  
#### PUT /api/profile/update
- Update user details (email, password, etc.).
- Requires: isAuthenticated
- **Request body**:
  ```json
  { "email": "new-email@example.com", "password": "new-password" }
- **Response**: 200 OK with
  ```json
  { "message": "Profile updated successfully" }

### Admin-Only Routes

#### GET /api/admin/users
- List all users (admin only).
- Requires: isAuthenticated, authorizeRoles("admin")
- **Response**: 200 OK with
  ```json
  { "users": [...] }
  
#### DELETE /api/admin/delete-user/:id
- Delete a user by ID (admin only).
- Requires: isAuthenticated, authorizeRoles("admin")
- **Response**: 200 OK with
  ```json
  { "message": "User deleted successfully" }

### Email & Activation

#### POST /api/auth/activate
- Send an activation email to the user.
- Requires: isAuthenticated
- **Request body**:
  ```json
  { "email": "user@example.com" }
- **Response**: 200 OK with
  ```json
  { "message": "Activation email sent" }

## Security Best Practices
- **Password Hashing:** Passwords are securely hashed before storing them in the database using bcrypt.
- **JWT:** JSON Web Tokens are used for secure authentication and authorization.
- **Role-Based Access Control:** Ensures that only users with appropriate roles (admin/user) can access specific routes.
- **Email Activation:** Users must activate their accounts via a code sent to their email before logging in.

