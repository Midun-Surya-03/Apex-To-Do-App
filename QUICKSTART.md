# 🚀 APEX - Quick Start Guide

## Installation (5 minutes)

### 1. Install Dependencies
```bash
npm install
```

### 2. Setup Environment
```bash
# Copy example env file
cp .env.example .env

# Edit .env with your settings:
# - MONGODB_URI (local or Atlas)
# - JWT_SECRET (change to random string)
# - PORT (default 5000)
```

### 3. Start MongoDB
```bash
# Option A: Local MongoDB
mongod

# Option B: Use MongoDB Atlas (cloud)
# Update MONGODB_URI in .env
```

### 4. Run Server
```bash
# Development (with auto-reload)
npm run dev

# Production
npm start
```

### 5. Open Browser
```
http://localhost:5000
```

---

## 📋 Create Test Account

1. Click "Create Account" on login page
2. Enter:
   - Name: Test User
   - Email: test@example.com
   - Password: Test123456 (must have uppercase + number)
3. Click "Create Account"
4. Start adding tasks!

---

## 🎯 Key Features to Try

- ✅ Create tasks with categories and priorities
- 📅 Add due dates and see countdowns
- 🔍 Search and filter tasks
- 🌙 Toggle dark/light mode
- ✨ Mark high-priority tasks complete (confetti!)
- 📝 Add sub-tasks to main tasks
- 🎨 Customize avatar colors

---

## 🔧 Common Commands

```bash
# Development with reload
npm run dev

# Production server
npm start

# Run tests
npm test

# Clear node_modules
rm -rf node_modules && npm install
```

---

## 📚 Full Documentation

See `README.md` for:
- Complete feature list
- API documentation
- Architecture overview
- Deployment guide
- Development guide
- Troubleshooting

---

## ⚠️ Important

- MongoDB must be running before starting the server
- Change `JWT_SECRET` in `.env` for production
- Never commit `.env` file to GitHub
- Use `npm run dev` for development

---

**Happy Task Managing! 🎉**
