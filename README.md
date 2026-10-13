# College Placement Management System (DBMS Project)

A centralized, full-stack web application designed for managing campus placement drives, student applications, recruiter interactions, and placement statistics using a normalized relational MySQL database.

---

## 🏛️ Architecture

- **Frontend**: React 18, Vite, Tailwind CSS, Lucide React, Axios, React Router v6
- **Backend**: Node.js, Express.js (REST API, MVC structure)
- **Database**: MySQL (`college_placement_db`) using `mysql2/promise` with parameterized queries
- **Authentication**: JWT (JSON Web Tokens) + `bcrypt` password hashing

---

## 📂 Project Structure

```
CollegePlacement/
│
├── database/
│   ├── schema.sql         # Normalized schema (DDL, primary keys, foreign keys, unique constraints)
│   ├── seed.sql           # Realistic sample data (admin, departments, companies, students, drives)
│   └── queries.sql        # Core DBMS demonstration queries (JOINs, GROUP BY, AVG, MAX, etc.)
│
├── backend/
│   ├── server.js          # Express entry point
│   ├── initDb.js          # Automated database & seed data importer
│   ├── .env               # Environment configuration
│   ├── config/
│   │   └── db.js          # MySQL connection pool
│   ├── controllers/       # Business logic (auth, student, company, drive, application, admin)
│   ├── middleware/        # JWT authMiddleware & roleMiddleware
│   └── routes/            # REST API route handlers
│
└── frontend/
    ├── src/
    │   ├── api.js         # Axios client configured with JWT interceptors
    │   ├── context/       # AuthContext (state, login, register, token)
    │   ├── components/    # Navbar, ProtectedRoute
    │   ├── pages/
    │   │   ├── public/    # Home, About, PublicDrives, PublicCompanies
    │   │   ├── auth/      # Login, Register
    │   │   ├── student/   # StudentDashboard, StudentProfile, StudentDrives, StudentApplications, StudentSelections
    │   │   ├── company/   # CompanyDashboard, CompanyProfile, CompanyDrives, CompanyApplicants, CompanySelections
    │   │   └── admin/     # AdminDashboard, AdminStudents, AdminCompanies, AdminDrives, AdminApplications, AdminSelections, AdminDepartments, AdminReports
    │   ├── App.jsx        # Routing configuration
    │   └── main.jsx
    └── vite.config.js
```

---

## 🚀 Quick Setup & Run Instructions

### 1. Database Setup
1. Ensure your local MySQL server is running.
2. In `backend/.env`, verify your MySQL credentials:
   ```env
   PORT=5000
   DB_HOST=localhost
   DB_USER=root
   DB_PASSWORD=your_mysql_password
   DB_NAME=college_placement_db
   DB_PORT=3306
   JWT_SECRET=super_secret_jwt_key_placement_2024
   ```
3. Initialize the database and sample data:
   ```bash
   cd backend
   npm run init-db
   ```
   *(Or import `database/schema.sql` and `database/seed.sql` directly into MySQL Workbench / phpMyAdmin).*

### 2. Start the Backend Server
```bash
cd backend
npm run dev
# Server will run at http://localhost:5000
```

### 3. Start the Frontend
```bash
cd frontend
npm run dev
# Frontend will run at http://localhost:5173
```

---

## 🔑 Demo Login Credentials

You can use the **1-Click Quick Fill** buttons on the Login page or manually sign in with:

| Role | Email | Password |
|---|---|---|
| **Student** | `alice@student.college.edu` | `password` |
| **Recruiter / Company** | `hr@techcorp.com` | `password` |
| **Admin / Placement Officer** | `admin@college.edu` | `password` |

---

## 🎯 Key Features Demonstrated

- **Eligibility Matching Engine**: Both client and server validate minimum CGPA, active backlogs, department restrictions, and graduation batch. Ineligible students receive specific diagnostic messages.
- **Role-Based Portals**:
  - **Student**: Track applications, view interview calls, review formal placement offers and compensation packages.
  - **Company**: Post drives, review applicant academic metrics, schedule interviews, and issue offers.
  - **Admin**: Approve recruiting companies, inspect system-wide audit logs, manage academic departments, and view real-time SQL aggregated metrics (`COUNT`, `AVG`, `MAX`, `GROUP BY`).
