# 🚀 APEX - Premium Task Management SaaS Application

A production-ready, full-stack task management application built with modern technologies and best practices.

## 📋 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Environment Configuration](#environment-configuration)
- [Running the Application](#running-the-application)
- [API Documentation](#api-documentation)
- [Architecture Overview](#architecture-overview)
- [Development Guide](#development-guide)

---

## ✨ Features

### User Accounts
- 🔐 Secure authentication with JWT tokens
- 🔑 Password hashing with bcryptjs
- 👤 User profiles with avatars and customization
- 🎯 "Remember Me" functionality
- 🔄 Refresh token management

### Task Intelligence
- 📂 Task Categories (Work, Personal, Shopping, Health, Other)
- 🎯 Priority Levels (Low, Medium, High)
- 📅 Due dates with countdown timer
- ✅ Task status tracking (Todo, In-Progress, Completed, Archived)
- 📝 Sub-tasks with nested checklists
- 🏷️ Tags for organization

### Advanced Features
- 🔍 Real-time search & filter system
- 📊 Task statistics and analytics
- 🌙 Dark/Light mode toggle with system awareness
- 📱 Fully responsive (mobile-first design)
- 🎨 Neuomorphic-Glass hybrid design aesthetic
- ✨ Micro-interactions with Web Animations
- 🎆 Confetti celebration for high-priority completions

### Backend
- 🔒 Input validation to prevent SQL/NoSQL injection
- ⚡ Optimistic UI updates with background sync
- 🛡️ Helmet security middleware
- 🌍 CORS enabled for multi-origin requests

---

## 🛠️ Tech Stack

### Frontend
- **HTML5** - Semantic markup
- **CSS3** - Modern styling with Tailwind CSS
- **Vanilla JavaScript (ES6+)** - Modular architecture

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - ODM for MongoDB
- **JWT** - Authentication tokens
- **bcryptjs** - Password hashing
- **cors** - Cross-origin support
- **helmet** - Security headers

---

## 📁 Project Structure

```
apex-todo-app/
├── server/
│   ├── models/
│   │   ├── User.js                 # User schema & methods
│   │   └── Task.js                 # Task schema with sub-tasks
│   ├── routes/
│   │   ├── auth.js                 # Authentication endpoints
│   │   └── tasks.js                # Task management endpoints
│   ├── middleware/
│   │   ├── auth.js                 # JWT verification
│   │   ├── errorHandler.js         # Error handling
│   │   └── validation.js           # Request validation
│   ├── controllers/
│   │   ├── authController.js       # Auth logic
│   │   └── taskController.js       # Task logic
│   ├── config/
│   │   └── database.js             # MongoDB connection
│   ├── server.js                   # Express server setup
│   └── .env.example                # Environment template
├── public/
│   ├── index.html                  # Main HTML file
│   ├── css/
│   │   └── styles.css              # Custom styles & themes
│   └── js/
│       ├── app.js                  # Main application
│       └── modules/
│           ├── api.js              # API client
│           ├── auth.js             # Authentication manager
│           ├── tasks.js            # Task manager
│           ├── ui.js               # UI renderer
│           └── darkMode.js         # Theme manager
├── package.json                    # Dependencies
├── README.md                       # Documentation
└── .gitignore                      # Git configuration
```

---

## ✅ Prerequisites

Before you begin, ensure you have installed:

- **Node.js** (v14.0.0 or higher) - [Download](https://nodejs.org/)
- **npm** or **yarn** - Comes with Node.js
- **MongoDB** (v4.4 or higher) - [Download](https://www.mongodb.com/try/download/community)
  - Or use MongoDB Atlas (cloud): https://www.mongodb.com/cloud/atlas

### Verify Installation

```bash
node --version    # Should be v14.0.0 or higher
npm --version     # Should be v6.0.0 or higher
```

---

## 📦 Installation

### Step 1: Clone or Extract the Project

```bash
# Navigate to the project directory
cd apex-todo-app
```

### Step 2: Install Backend Dependencies

```bash
# Install npm packages
npm install
```

This will install all required packages specified in `package.json`:
- express
- mongoose
- bcryptjs
- jsonwebtoken
- dotenv
- cors
- helmet
- express-validator
- multer

### Step 3: Verify Installation

```bash
# Check if all packages are installed
npm list
```

---

## ⚙️ Environment Configuration

### Step 1: Create .env File

Copy the `.env.example` file to create your own `.env` file:

```bash
# Windows (PowerShell)
Copy-Item .env.example .env

# macOS / Linux
cp .env.example .env
```

### Step 2: Configure Environment Variables

Edit the `.env` file with your specific configuration:

```env
# Database Configuration
MONGODB_URI=mongodb://localhost:27017/apex-todo-app
NODE_ENV=development

# JWT Configuration
JWT_SECRET=your_super_secret_jwt_key_change_this_in_production_12345
JWT_EXPIRE=7d

# Server Configuration
PORT=5000
CLIENT_URL=http://localhost:3000

# Email Configuration (Optional)
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your_email@gmail.com
SMTP_PASS=your_app_password

# Session Configuration
SESSION_SECRET=your_session_secret_key_change_this

# CORS Configuration
ALLOWED_ORIGINS=http://localhost:3000,http://localhost:5000
```

### Important Security Notes

⚠️ **Before Deploying to Production:**

1. **Change JWT_SECRET** to a long, random, secure string:
   ```bash
   node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"
   ```

2. **Use Environment-specific values** for each deployment stage

3. **Never commit `.env` file** to version control (already listed in .gitignore)

4. **Use MongoDB Atlas** for production databases for better security and backups

---

## 🚀 Running the Application

### Option 1: Development Mode (with auto-reload)

Requires `nodemon` to be installed (included in devDependencies):

```bash
npm run dev
```

The server will start and automatically reload on file changes.

### Option 2: Production Mode

```bash
npm start
```

### Verify Server is Running

Open your browser and navigate to:

```
http://localhost:5000
```

You should see the Apex login page.

### Console Output

When the server starts successfully, you'll see:

```
🚀 ============================================
   ⭐ APEX TASK MANAGEMENT SaaS APPLICATION
🚀 ============================================
🌐 Server running on http://localhost:5000
🔌 Environment: development
📊 API Base: http://localhost:5000/api
🚀 ============================================
```

---

## 📡 API Documentation

### Authentication Endpoints

#### Sign Up
```http
POST /api/auth/signup
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "SecurePass123"
}

Response: { success: true, token: "jwt_token", user: {...} }
```

#### Login
```http
POST /api/auth/login
Content-Type: application/json

{
  "email": "john@example.com",
  "password": "SecurePass123",
  "rememberMe": true
}

Response: { success: true, token: "jwt_token", user: {...} }
```

#### Get Profile
```http
GET /api/auth/profile
Authorization: Bearer {token}

Response: { success: true, user: {...} }
```

#### Logout
```http
POST /api/auth/logout
Authorization: Bearer {token}

Response: { success: true, message: "Logged out successfully" }
```

### Task Endpoints

#### Create Task
```http
POST /api/tasks
Authorization: Bearer {token}
Content-Type: application/json

{
  "title": "Complete project",
  "description": "Finish the task management app",
  "category": "work",
  "priority": "high",
  "dueDate": "2024-12-31"
}

Response: { success: true, task: {...} }
```

#### Get All Tasks
```http
GET /api/tasks?status=active&category=work&priority=high&search=query&sort=dueDate
Authorization: Bearer {token}

Response: { success: true, tasks: [...], pagination: {...} }
```

#### Update Task
```http
PUT /api/tasks/{taskId}
Authorization: Bearer {token}
Content-Type: application/json

{
  "title": "Updated title",
  "isCompleted": true,
  "status": "completed"
}

Response: { success: true, task: {...} }
```

#### Delete Task
```http
DELETE /api/tasks/{taskId}
Authorization: Bearer {token}

Response: { success: true, message: "Task deleted successfully" }
```

#### Add Sub-task
```http
POST /api/tasks/{taskId}/subtasks
Authorization: Bearer {token}
Content-Type: application/json

{
  "title": "Sub-task 1"
}

Response: { success: true, task: {...} }
```

#### Get Statistics
```http
GET /api/tasks/stats/overview
Authorization: Bearer {token}

Response: { success: true, stats: { total, completed, pending, byCategory, byPriority } }
```

---

## 🏗️ Architecture Overview

### Client-Side Architecture

The frontend follows a **modular, separation-of-concerns** pattern:

```
App (Main Controller)
├── API Module (HTTP Communication)
├── Auth Manager (User Authentication)
├── Task Manager (State Management)
├── UI Manager (DOM Rendering)
└── Dark Mode Manager (Theme Management)
```

### Server-Side Architecture

```
Express Server
├── Routes (Endpoint definitions)
├── Controllers (Business logic)
├── Middleware (Auth, validation, error handling)
├── Models (MongoDB schemas)
├── Config (Database connection)
└── Database (MongoDB)
```

### Data Flow

1. **User Action** → UI Event Handler
2. **Validation** → Input validation
3. **API Call** → Backend request with JWT
4. **Backend Processing** → Controller logic
5. **Database Operation** → CRUD with Mongoose
6. **Response** → JSON response
7. **UI Update** → Optimistic update + render

---

## 👨‍💻 Development Guide

### Adding a New Task Field

1. **Update MongoDB Model** (`server/models/Task.js`):
   ```javascript
   newField: {
       type: String,
       required: false,
       default: null
   }
   ```

2. **Update Controller** (`server/controllers/taskController.js`):
   ```javascript
   allowedFields.push('newField');
   ```

3. **Update Validation** (`server/middleware/validation.js`):
   ```javascript
   body('newField').optional().isString()
   ```

4. **Update Frontend** (`public/js/modules/tasks.js`):
   ```javascript
   // Handle in UI rendering and form submission
   ```

### Adding New API Endpoint

1. Create route in `server/routes/tasks.js`:
   ```javascript
   router.post('/endpoint', authMiddleware, controller.method);
   ```

2. Add controller method in `server/controllers/taskController.js`

3. Add API client method in `public/js/modules/api.js`

4. Update UI manager in `public/js/modules/ui.js`

### Error Handling

All errors are caught by the global error handler middleware:

```javascript
// In controllers, throw AppError
throw new AppError('Error message', statusCode);

// Errors are automatically caught and formatted
```

---

## 🔒 Security Best Practices

### Implemented Security Features

✅ **JWT Authentication** - Secure token-based authentication  
✅ **Password Hashing** - bcryptjs with salt rounds  
✅ **Input Validation** - express-validator prevents injection attacks  
✅ **CORS Protection** - Limited to allowed origins  
✅ **Helmet Middleware** - Sets secure HTTP headers  
✅ **Input Escaping** - XSS prevention on frontend  

### Production Deployment Checklist

- [ ] Change all secrets in `.env`
- [ ] Set `NODE_ENV=production`
- [ ] Enable HTTPS
- [ ] Use environment variables for sensitive data
- [ ] Implement rate limiting
- [ ] Set up database backups
- [ ] Enable MongoDB encryption
- [ ] Use strong JWT secrets
- [ ] Implement request logging

---

## 🐛 Troubleshooting

### MongoDB Connection Failed

```bash
# Check if MongoDB is running
# Windows: Services > MongoDB Server
# macOS: brew services list
# Linux: systemctl status MongoDB

# Or use MongoDB Atlas connection
MONGODB_URI=mongodb+srv://user:password@cluster.mongodb.net/dbname
```

### Port Already in Use

```bash
# Change PORT in .env file
PORT=5001
```

### Node Modules Issues

```bash
# Clear node_modules and reinstall
rm -rf node_modules
npm install
```

### Dependencies Issue

```bash
# Update npm
npm install -g npm@latest

# Clear npm cache
npm cache clean --force

# Reinstall dependencies
npm install
```

---

## 📚 Additional Resources

- [Express.js Documentation](https://expressjs.com/)
- [MongoDB Mongoose Guide](https://mongoosejs.com/)
- [JWT Introduction](https://jwt.io/introduction)
- [REST API Best Practices](https://restfulapi.net/)
- [Web Security Academy](https://portswigger.net/web-security)

---

## 📄 License

This project is licensed under the MIT License.

---

## 👥 Support

For issues or questions, please refer to the project documentation or create an issue in the repository.

---

## 🎯 Roadmap

Future enhancements:
- [ ] Real-time collaboration with WebSockets
- [ ] Mobile apps (React Native)
- [ ] Analytics dashboard
- [ ] Team management
- [ ] File attachments
- [ ] Calendar integration
- [ ] Notifications
- [ ] Advanced reporting

---

**Made with ❤️ by the Apex Development Team**

*v1.0.0 - Production Ready*
