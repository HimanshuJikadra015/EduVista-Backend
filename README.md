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
   git clone https://github.com/your-repo/eduvista-backend.git
   cd eduvista-backend
