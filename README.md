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

