# 🔐 User Auth System - Setup Guide

## 📁 Project Structure
```
auth-project/
├── backend/
│   ├── server.js
│   ├── package.json
│   ├── models/
│   │   └── User.js
│   └── routes/
│       └── auth.js
└── frontend/
    └── index.html
```

---

## ⚠️ Things YOU Must Change Before Running

### 1. MongoDB Connection (backend/server.js, line 11)
- **Local MongoDB**: Keep as `mongodb://localhost:27017/authdb`
  - Make sure MongoDB is installed and running
- **MongoDB Atlas (cloud)**: Replace with your Atlas URI:
  `mongodb+srv://YourUsername:YourPassword@cluster0.xxxxx.mongodb.net/authdb`

### 2. JWT Secret (backend/routes/auth.js, line 8)
- Change `'mysecretkey123'` to any random long string
- Example: `'xK9#mP2@qL5vN8'`

---

## 🚀 Steps to Run (VS Code)

### Step 1 — Install MongoDB (if using local)
- Download from: https://www.mongodb.com/try/download/community
- Install and start MongoDB service

### Step 2 — Open Project in VS Code
- Open VS Code
- File → Open Folder → select the `auth-project` folder

### Step 3 — Open Terminal in VS Code
- Press `` Ctrl + ` `` (backtick) to open terminal

### Step 4 — Install Backend Dependencies
```bash
cd backend
npm install
```
(This installs express, mongoose, bcryptjs, jsonwebtoken, cors)

### Step 5 — Start the Backend Server
```bash
node server.js
```
✅ You should see:
```
✅ MongoDB Connected
✅ Server running on http://localhost:5000
```

### Step 6 — Open the Frontend
- Go to the `frontend` folder
- Right-click `index.html` → Open with Live Server
  (Install "Live Server" extension in VS Code if not installed)
- OR just double-click `index.html` to open in browser

---

## 🧪 Testing with Postman

### Register
- Method: `POST`
- URL: `http://localhost:5000/api/register`
- Body → raw → JSON:
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "password123"
}
```

### Login
- Method: `POST`
- URL: `http://localhost:5000/api/login`
- Body → raw → JSON:
```json
{
  "email": "john@example.com",
  "password": "password123"
}
```
✅ Copy the `token` from the response

### Profile (Protected Route)
- Method: `GET`
- URL: `http://localhost:5000/api/profile`
- Headers:
  - Key: `Authorization`
  - Value: `Bearer <paste your token here>`

---

## ✅ Features Covered
- [x] Registration form (Name, Email, Password, Confirm, Gender, DOB, Address)
- [x] Frontend validation (email format, password length, required fields)
- [x] POST /register API
- [x] POST /login API
- [x] Password hashing (bcrypt)
- [x] Input validation + error handling
- [x] MongoDB User schema (name, email, password, role)
- [x] Insert user / Find user during login
- [x] JWT-based authentication
- [x] Protected /profile route
- [x] Token validation middleware
