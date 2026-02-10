# IHIS - Complete Setup Guide (Running on a New Laptop)

This guide will walk you through step-by-step instructions on how to set up and run the project on a new laptop.

---

## 🛠️ Technologies Used

### Backend
- **Framework**: NestJS (Node.js framework)
- **Language**: TypeScript
- **Database**: PostgreSQL
- **ORM**: Prisma
- **Authentication**: JWT (JSON Web Tokens)
- **API Documentation**: Swagger
- **File Upload**: Multer

### Frontend
- **Framework**: React 18
- **Language**: TypeScript
- **Build Tool**: Vite
- **Styling**: TailwindCSS
- **State Management**: React Query (TanStack Query)
- **Routing**: React Router DOM
- **UI Icons**: Lucide React
- **Forms**: React Hook Form
- **Charts**: Recharts
- **Calendar**: React Big Calendar
- **Notifications**: React Hot Toast
- **HTTP Client**: Axios

### Development Tools
- **Package Manager**: npm
- **Database Client**: Prisma Studio
- **Code Quality**: ESLint, Prettier

---

## 📋 Prerequisites

You need to have the following installed on your system:

1. **Node.js** (v18 or higher)
   - Download: https://nodejs.org/
   - Check version: `node --version`

2. **PostgreSQL** (v14 or higher)
   - Download: https://www.postgresql.org/download/
   - Check version: `psql --version`

3. **npm** (comes with Node.js)
   - Check version: `npm --version`

---

## 🚀 Step-by-Step Setup (On a New Laptop)

### Step 1: Copy Project to Laptop

If you already have the project folder, skip this step. Otherwise:

```bash
# If cloning from Git:
git clone <repository-url>
cd IHIS

# Or copy the project folder via USB/flash drive
```

---

### Step 2: PostgreSQL Database Setup

1. **Install PostgreSQL** (if not already installed)

2. **Create the database:**
   ```bash
   # Open PostgreSQL terminal
   psql -U postgres
   
   # Create database
   CREATE DATABASE ihis;
   
   # Exit
   \q
   ```

3. **Note down database connection details:**
   - Username: (usually `postgres`)
   - Password: (your password)
   - Database Name: `ihis`
   - Port: `5432` (default)

---

### Step 3: Backend Setup

1. **Navigate to backend folder:**
   ```bash
   cd backend
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```
   
   ⏱️ *This may take 2-3 minutes*

3. **Create environment file:**
   
   Create a file named `.env` in the `backend` folder and add this content:
   
   ```env
   DATABASE_URL="postgresql://postgres:YOUR_PASSWORD@localhost:5432/ihis?schema=public"
   JWT_SECRET="your-super-secret-jwt-key-change-this-in-production"
   JWT_EXPIRES_IN="7d"
   PORT=3000
   UPLOAD_PATH="./uploads"
   ```
   
   ⚠️ **Important**: Replace `YOUR_PASSWORD` with your PostgreSQL password!

4. **Generate Prisma Client:**
   ```bash
   npm run prisma:generate
   ```

5. **Run database migrations:**
   ```bash
   npm run prisma:migrate
   ```
   
   💡 *This will create database tables*

6. **(Optional) Add seed data:**
   ```bash
   npm run seed
   ```

7. **Start the backend server:**
   ```bash
   npm run start:dev
   ```
   
   ✅ **Success!** Backend will run at `http://localhost:3000`
   
   📖 API Documentation: `http://localhost:3000/api/docs`

---

### Step 4: Frontend Setup

**Open a new terminal window** (keep backend running)

1. **Navigate to frontend folder:**
   ```bash
   cd frontend
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```
   
   ⏱️ *This may take 3-5 minutes*

3. **Create environment file (Optional):**
   
   Create a file named `.env` in the `frontend` folder:
   
   ```env
   VITE_API_URL=http://localhost:3000
   ```
   
   💡 *This is the default, change if backend is on a different port*

4. **Start the frontend server:**
   ```bash
   npm run dev
   ```
   
   ✅ **Success!** Frontend will run at `http://localhost:3001`
   
   🌐 Browser will open automatically

---

## ✅ Verification (Check if Everything is Working)

### Backend Check:
1. Open in browser: `http://localhost:3000/api/docs`
2. Swagger API documentation page should open

### Frontend Check:
1. Open in browser: `http://localhost:3001`
2. Landing page or login page should appear

### Database Check:
```bash
cd backend
npm run prisma:studio
```
- Prisma Studio will open in browser
- Database tables should be visible

---

## 🔑 Default Login Credentials (If Seed Data is Added)

If you ran `npm run seed`, you can use these credentials:

**Admin:**
- Email: `admin@ihis.com`
- Password: `admin123`

**Doctor:**
- Email: `doctor@ihis.com`
- Password: `doctor123`

**Nurse:**
- Email: `nurse@ihis.com`
- Password: `nurse123`

**Patient:**
- Email: `patient@ihis.com`
- Password: `patient123`

⚠️ **Make sure to change these credentials in production!**

---

## 🛑 Stopping Development Servers

### Backend Stop:
- Press `Ctrl + C` in terminal

### Frontend Stop:
- Press `Ctrl + C` in terminal

Or for backend:
```bash
cd backend
npm run stop
```

---

## 🔄 Daily Use (When Working Daily)

1. **Ensure database is running:**
   - Start PostgreSQL service

2. **Start backend:**
   ```bash
   cd backend
   npm run start:dev
   ```

3. **Start frontend (in new terminal):**
   ```bash
   cd frontend
   npm run dev
   ```

4. **Open in browser:** `http://localhost:3001`

---

## 🐛 Common Issues & Solutions

### Issue 1: Port Already in Use
**Error**: `Port 3000 is already in use`

**Solution**:
```bash
cd backend
npm run stop
# Or:
lsof -ti:3000 | xargs kill -9
```

### Issue 2: Database Connection Error
**Error**: `Can't reach database server`

**Solutions**:
- Start PostgreSQL service
- Check `DATABASE_URL` in `.env` file
- Verify password is correct

### Issue 3: Module Not Found
**Error**: `Cannot find module`

**Solution**:
```bash
# In Frontend or Backend folder:
rm -rf node_modules package-lock.json
npm install
```

### Issue 4: Prisma Client Error
**Error**: `PrismaClient is not generated`

**Solution**:
```bash
cd backend
npm run prisma:generate
```

### Issue 5: Migration Error
**Error**: `Migration failed`

**Solution**:
```bash
cd backend
npm run prisma:migrate reset  # ⚠️ This will delete data
npm run prisma:migrate
```

---

## 📁 Important Files & Folders

```
IHIS/
├── backend/
│   ├── .env                 # ⚠️ Database and JWT settings (must create)
│   ├── prisma/
│   │   ├── schema.prisma    # Database schema
│   │   └── migrations/      # Database migrations
│   └── src/                 # Backend source code
│
├── frontend/
│   ├── .env                 # ⚠️ API URL (optional, can create)
│   └── src/                 # Frontend source code
│
└── SETUP_GUIDE.md          # This file
```

---

## 📞 Need Help?

If you encounter any problems:

1. Read the error message carefully
2. Check the Common Issues section
3. Check console logs (in both browser and terminal)
4. Verify database connection

---

## 🎯 Quick Start Summary

```bash
# 1. Database setup
psql -U postgres
CREATE DATABASE ihis;
\q

# 2. Backend setup
cd backend
npm install
# Create .env file (see Step 3.3)
npm run prisma:generate
npm run prisma:migrate
npm run start:dev

# 3. Frontend setup (in new terminal)
cd frontend
npm install
npm run dev

# 4. Open in browser
# http://localhost:3001
```

---

**Happy Coding! 🚀**
