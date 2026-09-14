# Job Portal — Full-Stack MERN Application

A full-stack job portal with role-based authentication (recruiters vs. job seekers), job posting, applications with resume uploads, an applicant tracking system, real-time error monitoring, and cloud deployment support.

**Stack:** MongoDB · Express · React (Vite) · Node.js · Clerk (auth) · Cloudinary (file storage) · Sentry (monitoring) · Tailwind CSS · deployed on Vercel

---

## ✨ Features

- **Secure role-based auth** via Clerk — users sign up once and choose "Job Seeker" or "Recruiter"; routes and API endpoints are gated by role.
- **Recruiter dashboard** — post jobs, edit/hide/delete postings, view applicant counts.
- **Job-seeker dashboard** — browse/search/filter jobs, apply with resume + cover letter, track application status.
- **Resume & profile management** — upload resumes (PDF) and company logos to Cloudinary; edit bio/skills/company info.
- **Applicant Tracking System (ATS)** — recruiters view applicants per job and move them through Pending → Reviewed → Shortlisted → Hired/Rejected.
- **RESTful API** — clean CRUD endpoints for jobs, applications, and users, all protected with Clerk-verified JWTs.
- **Sentry integration** — real-time error monitoring & performance tracing on both backend (Express) and frontend (React).
- **Deployable to Vercel** — both `frontend/` and `backend/` include `vercel.json` for one-click cloud hosting.

---

## 📁 Project Structure

```
job-portal/
├── backend/
│   ├── config/          # MongoDB + Cloudinary config
│   ├── controllers/     # Business logic (jobs, applications, users)
│   ├── middleware/      # Clerk auth guard, role guard, multer upload
│   ├── models/          # Mongoose schemas: User, Job, Application
│   ├── routes/          # Express routers
│   ├── instrument.js    # Sentry init (must load first)
│   └── server.js        # App entry point
└── frontend/
    ├── src/
    │   ├── components/  # Navbar, JobCard, ProtectedRoute
    │   ├── context/     # UserContext (syncs Clerk user -> backend profile)
    │   ├── lib/api.js   # Axios instance w/ Clerk token interceptor
    │   ├── pages/        # Home, Jobs, JobDetail, Dashboards, Profile...
    │   └── App.jsx / main.jsx
    └── index.html
```

---

## 🚀 Getting Started Locally

### 1. Prerequisites
- Node.js 18+
- A [MongoDB Atlas](https://www.mongodb.com/atlas) cluster (or local MongoDB)
- A [Clerk](https://clerk.com) application (free tier is fine)
- A [Cloudinary](https://cloudinary.com) account (free tier)
- A [Sentry](https://sentry.io) project for both backend (Node) and frontend (React)

### 2. Backend setup
```bash
cd backend
cp .env.example .env      # fill in your real keys
npm install
npm run dev                # starts on http://localhost:5000
```

### 3. Frontend setup
```bash
cd frontend
cp .env.example .env      # fill in your real keys
npm install
npm run dev                # starts on http://localhost:5173
```

tures both handled and unhandled errors on both ends without leaking `.env` secrets into client bundles (only `VITE_`-prefixed vars are exposed to the frontend).
