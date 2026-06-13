# 🏥 HealthSlot — Doctor Appointment Booking Platform

A full-stack MERN web application that connects patients with doctors for seamless appointment booking, online payments, and clinic management.

---

## 🚀 Features

### 👤 Patient Portal
- Register/Login with JWT authentication and bcrypt password hashing
- Browse doctors by speciality (General Physician, Gynecologist, Dermatologist, Pediatrician, Neurologist, Gastroenterologist)
- Book appointments with real-time slot availability
- Pay online via **Stripe** or **Razorpay**
- View and cancel upcoming appointments
- Update personal profile with photo upload via Cloudinary

### 👨‍⚕️ Doctor Dashboard
- View all scheduled appointments
- Mark appointments as completed or cancelled
- Manage personal profile, fees, and availability
- View earnings dashboard

### 🛠️ Admin Panel
- Add new doctors with photo, speciality, degree, experience, and fees
- View and manage all appointments across the platform
- Dashboard with total doctors, patients, and appointments stats
- Cancel any appointment from admin panel

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 18 + Vite + Tailwind CSS |
| Admin Panel | React 18 + Vite + Tailwind CSS |
| Backend | Node.js + Express.js |
| Database | MongoDB + Mongoose |
| Authentication | JWT + bcrypt |
| Payments | Stripe + Razorpay |
| Image Storage | Cloudinary + Multer |
| Deployment | Vercel (Frontend + Admin) |

---

## 📁 Project Structure

```
healthslot/
├── backend/
│   ├── config/
│   │   ├── mongodb.js          # MongoDB connection
│   │   └── cloudinary.js       # Cloudinary config
│   ├── controllers/
│   │   ├── userController.js   # Patient APIs
│   │   ├── doctorController.js # Doctor APIs
│   │   └── adminController.js  # Admin APIs
│   ├── middleware/
│   │   ├── authUser.js         # Patient auth middleware
│   │   ├── authDoctor.js       # Doctor auth middleware
│   │   └── authAdmin.js        # Admin auth middleware
│   ├── models/
│   │   ├── userModel.js        # Patient schema
│   │   ├── doctorModel.js      # Doctor schema
│   │   └── appointmentModel.js # Appointment schema
│   ├── routes/
│   │   ├── userRoute.js
│   │   ├── doctorRoute.js
│   │   └── adminRoute.js
│   └── server.js
├── frontend/                   # Patient-facing React app
│   └── src/
│       ├── pages/              # Home, Doctors, Appointment, Profile
│       ├── components/         # Navbar, Footer, Banner, etc.
│       └── context/            # Global app state
└── admin/                      # Admin + Doctor React panel
    └── src/
        ├── pages/
        │   ├── Admin/          # Dashboard, AddDoctor, Appointments
        │   └── Doctor/         # Dashboard, Appointments, Profile
        └── context/            # Admin + Doctor context
```

---

## 🔌 API Endpoints

### User (Patient)
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/user/register | Register new patient |
| POST | /api/user/login | Patient login |
| GET | /api/user/get-profile | Get patient profile |
| PUT | /api/user/update-profile | Update profile + photo |
| POST | /api/user/book-appointment | Book appointment |
| GET | /api/user/appointments | List appointments |
| POST | /api/user/cancel-appointment | Cancel appointment |
| POST | /api/user/payment-razorpay | Initiate Razorpay payment |
| POST | /api/user/payment-stripe | Initiate Stripe payment |

### Doctor
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/doctor/login | Doctor login |
| GET | /api/doctor/appointments | View appointments |
| POST | /api/doctor/complete-appointment | Mark completed |
| GET | /api/doctor/dashboard | Earnings + stats |
| GET | /api/doctor/profile | View profile |
| PUT | /api/doctor/update-profile | Update profile |

### Admin
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/admin/login | Admin login |
| POST | /api/admin/add-doctor | Add new doctor |
| GET | /api/admin/all-doctors | List all doctors |
| GET | /api/admin/appointments | All appointments |
| POST | /api/admin/cancel-appointment | Cancel appointment |
| GET | /api/admin/dashboard | Platform stats |

---

## ⚙️ Setup & Installation

### Prerequisites
- Node.js 18+
- MongoDB Atlas account
- Cloudinary account
- Stripe account
- Razorpay account

### 1. Clone & Install

```bash
git clone https://github.com/sarthak88888/healthslot.git
cd healthslot

# Install backend
cd backend && npm install

# Install frontend
cd ../frontend && npm install

# Install admin
cd ../admin && npm install
```

### 2. Configure Environment

Create `backend/.env`:

```env
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
CLOUDINARY_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_cloudinary_key
CLOUDINARY_SECRET_KEY=your_cloudinary_secret
STRIPE_SECRET_KEY=your_stripe_secret
RAZORPAY_KEY_ID=your_razorpay_key_id
RAZORPAY_KEY_SECRET=your_razorpay_secret
ADMIN_EMAIL=admin@healthslot.com
ADMIN_PASSWORD=yourpassword
```

Create `frontend/.env`:
```env
VITE_BACKEND_URL=http://localhost:4000
VITE_RAZORPAY_KEY_ID=your_razorpay_key_id
VITE_STRIPE_KEY=your_stripe_publishable_key
```

### 3. Run the App

```bash
# Terminal 1 - Backend
cd backend && npm run server
# → http://localhost:4000

# Terminal 2 - Frontend
cd frontend && npm run dev
# → http://localhost:5173

# Terminal 3 - Admin Panel
cd admin && npm run dev
# → http://localhost:5174
```

---

## 🚀 Deployment

### Frontend + Admin → Vercel
1. Push repo to GitHub
2. Import project on [vercel.com](https://vercel.com)
3. Set root directory to `frontend` or `admin`
4. Add environment variables
5. Deploy

### Backend → Render
1. Create a new Web Service on [render.com](https://render.com)
2. Connect GitHub repo
3. Root directory: `backend`
4. Build command: `npm install`
5. Start command: `node server.js`
6. Add all environment variables

---

## ✨ Key Highlights

- **Dual payment gateway** — Stripe (international) + Razorpay (India) support
- **Role-based access** — Separate portals for Patients, Doctors, and Admins
- **Secure auth** — JWT tokens + bcrypt password hashing
- **Image management** — Cloudinary integration for doctor and patient photos
- **Real-time slot management** — Prevents double booking automatically

---

## 📄 License

MIT
