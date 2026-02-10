# IHIS - Hospital & Clinical Management System

A complete Hospital & Clinical Management System with role-based access for Admin, Doctors, Nurses, and Patients.

## Features

### Core Features
- **User Management**: Login, registration, and role-based access (Admin, Doctor, Nurse, Patient)
- **Patient Management**: Create, update, search, and filter patient records
- **Appointments**: Book, reschedule, cancel appointments with doctor availability management
- **EHR (Electronic Health Records)**: Visit notes, diagnoses, treatment plans, and attachments
- **Lab Records**: Upload, view, and update lab results
- **Prescriptions**: Doctors can write prescriptions, patients can view/download them
- **Billing & Invoices**: Generate invoices and view invoice history
- **Dashboards**: Role-specific dashboards for each user type

### Operational Features (Day-to-Day Operations)
- **Audit Trail System**: Automatic logging of all user activities (CREATE, UPDATE, DELETE, LOGIN, etc.)
- **KPI Dashboard**: Real-time metrics for management (users, appointments, revenue, activity)
- **Activity Monitoring**: Track all system activities with filters (user, entity, action, date)
- **Admin Governance**: Complete system oversight, user management, role control
- **Automated Activity Logging**: All actions automatically logged with IP, timestamp, user info
- **System Analytics**: Appointment trends, revenue analytics, user activity statistics

## 🚀 Quick Setup (Naye Laptop Par Run Karne Ke Liye)

**Detailed step-by-step guide ke liye**: [`SETUP_GUIDE.md`](./SETUP_GUIDE.md) file dekh lein

**Quick Start:**
```bash
# 1. Backend Setup
cd backend
npm install
# .env file create karein (DATABASE_URL, JWT_SECRET required)
npm run prisma:generate
npm run prisma:migrate
npm run start:dev

# 2. Frontend Setup (nayi terminal mein)
cd frontend
npm install
npm run dev

# 3. Browser mein: http://localhost:3001
```

## Technology Stack

### Backend
- **Framework**: NestJS (Node.js framework)
- **Language**: TypeScript
- **Database**: PostgreSQL
- **ORM**: Prisma
- **Authentication**: JWT (JSON Web Tokens)
- **API Documentation**: Swagger
- **File Upload**: Multer

### Frontend
- **Framework**: React 18 + TypeScript
- **Build Tool**: Vite
- **Styling**: TailwindCSS
- **State Management**: React Query (TanStack Query)
- **Routing**: React Router DOM
- **UI Icons**: Lucide React
- **Forms**: React Hook Form
- **Charts**: Recharts
- **Calendar**: React Big Calendar
- **HTTP Client**: Axios
- **Notifications**: React Hot Toast

## Project Structure

```
IHIS/
├── backend/
│   ├── src/
│   │   ├── auth/          # Authentication module
│   │   ├── users/         # User management
│   │   ├── patients/      # Patient management
│   │   ├── appointments/  # Appointment management
│   │   ├── visit-notes/   # EHR/Visit notes
│   │   ├── lab-records/   # Lab records
│   │   ├── prescriptions/ # Prescriptions
│   │   ├── invoices/      # Billing & invoices
│   │   └── doctors/       # Doctor management
│   └── prisma/
│       └── schema.prisma  # Database schema
├── frontend/
│   └── src/
│       ├── pages/         # Page components
│       ├── components/    # Reusable components
│       ├── contexts/      # React contexts
│       └── services/      # API services
└── README.md
```

## Setup Instructions

📖 **Complete detailed guide**: See [`SETUP_GUIDE.md`](./SETUP_GUIDE.md) for step-by-step instructions, troubleshooting, and all requirements.

### Prerequisites
- Node.js (v18 or higher)
- PostgreSQL (v14 or higher)
- npm (comes with Node.js)

### Quick Setup

**Backend:**
```bash
cd backend
npm install
# Create .env file (see SETUP_GUIDE.md for details)
npm run prisma:generate
npm run prisma:migrate
npm run start:dev
```

**Frontend:**
```bash
cd frontend
npm install
npm run dev
```

**Access:**
- Frontend: `http://localhost:3001`
- Backend API: `http://localhost:3000`
- API Docs: `http://localhost:3000/api/docs`

## Database Schema

The system uses the following main entities:
- **User**: Base user entity with role-based access
- **Patient**: Patient-specific information
- **Doctor**: Doctor profile and specialization
- **Nurse**: Nurse profile
- **Appointment**: Appointment scheduling
- **VisitNote**: Electronic health records
- **LabRecord**: Laboratory test results
- **Prescription**: Medication prescriptions
- **Invoice**: Billing and invoices
- **DoctorAvailability**: Doctor schedule management

## API Endpoints

### Authentication
- `POST /auth/login` - User login
- `POST /auth/register` - User registration
- `GET /auth/profile` - Get current user profile

### Patients
- `GET /patients` - Get all patients (with search)
- `GET /patients/:id` - Get patient by ID
- `POST /patients` - Create patient
- `PATCH /patients/:id` - Update patient

### Appointments
- `GET /appointments` - Get all appointments (with filters)
- `GET /appointments/:id` - Get appointment by ID
- `POST /appointments` - Create appointment
- `PATCH /appointments/:id` - Update appointment
- `PATCH /appointments/:id/cancel` - Cancel appointment
- `PATCH /appointments/:id/reschedule` - Reschedule appointment

### Visit Notes (EHR)
- `GET /visit-notes` - Get all visit notes
- `GET /visit-notes/:id` - Get visit note by ID
- `POST /visit-notes` - Create visit note
- `PATCH /visit-notes/:id` - Update visit note

### Lab Records
- `GET /lab-records` - Get all lab records
- `GET /lab-records/:id` - Get lab record by ID
- `POST /lab-records` - Create lab record
- `PATCH /lab-records/:id` - Update lab record

### Prescriptions
- `GET /prescriptions` - Get all prescriptions
- `GET /prescriptions/:id` - Get prescription by ID
- `POST /prescriptions` - Create prescription
- `PATCH /prescriptions/:id` - Update prescription

### Invoices
- `GET /invoices` - Get all invoices
- `GET /invoices/:id` - Get invoice by ID
- `POST /invoices` - Create invoice
- `PATCH /invoices/:id/mark-paid` - Mark invoice as paid

### Doctors
- `GET /doctors` - Get all doctors
- `GET /doctors/:id` - Get doctor by ID
- `POST /doctors/availability` - Update doctor availability
- `GET /doctors/availability/:doctorId` - Get doctor availability

### Audit & Activity (Admin Only)
- `GET /audit/logs` - Get activity logs with filters
- `GET /audit/kpis` - Get KPIs and system metrics

## Role-Based Access

### Admin
- Full system access
- User management
- View all patients, appointments, invoices
- System administration

### Doctor
- View and manage patients
- Create visit notes and prescriptions
- Manage appointments
- Set availability schedule

### Nurse
- View patients
- Manage appointments
- Upload and update lab records

### Patient
- View own medical records
- Book appointments
- View prescriptions
- View invoices

## Development

### Running Tests
```bash
# Backend
cd backend
npm run test

# Frontend
cd frontend
npm run test
```

### Building for Production

**Backend:**
```bash
cd backend
npm run build
npm run start:prod
```

**Frontend:**
```bash
cd frontend
npm run build
```

## Security Notes

- Change the `JWT_SECRET` in production
- Use strong database passwords
- Enable HTTPS in production
- Implement rate limiting
- Add input validation and sanitization
- Regular security audits

## Day-to-Day Operations

### For Staff
1. **Log in** → Work in dashboard → Update records → System automatically syncs across all modules

### For Management
1. **Admin portal** → Track KPIs → Manage roles → Audit activity → Optimize workflows

### For Patients
1. **Use portal** → Access services → Receive updates → Engage with healthcare digitally

### System Features
- **Central Nervous System**: All data routes back into secure, centralized repository
- **Automatic Sync**: Changes sync across all modules instantly
- **Audit Trails**: Complete activity logging for compliance
- **Role-Based Control**: Admin governance with automated backups and system audit trails

See `OPERATIONS_GUIDE.md` for detailed operational procedures.

## License

MIT

## Support

For issues and questions, please open an issue in the repository.



# integrated-health-information-system-fyp
