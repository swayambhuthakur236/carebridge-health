# CareBridge — Full-Stack Hospital Management & Coordination Platform

**CareBridge** is an enterprise healthcare management, clinical coordination, and electronic medical record (EMR) platform built with React, TypeScript, Vite, Tailwind CSS, and Supabase (PostgreSQL, Authentication, Private Storage, and Realtime).

CareBridge provides five specialized, role-based dashboards:
1. **Patient Portal**: Schedule visits, manage active prescriptions, track medical history, and view diagnostic pathology reports.
2. **Doctor Suite**: Outpatient appointment management, clinical encounter documentation (vitals, diagnoses, ICD-10), digital e-prescribing, diagnostic test ordering, and follow-up tracking.
3. **Receptionist Desk**: Patient admissions, walk-in registration, token queue stage management, appointment scheduling, and non-clinical intake verification.
4. **Diagnostic Laboratory**: Pathology test accession, urgency prioritization (STAT / Urgent / Routine), quantitative/qualitative result entry, and private verified report publishing.
5. **Hospital Administrator**: Real-time department census telemetry, physician shift scheduling, trusted staff account provisioning, and institutional security audit logging.

---

## 📚 Technical Documentation Index

- 🚀 **Deployment & Cloud Infrastructure**: [`docs/DEPLOYMENT.md`](file:///d:/projects/CareBridge/docs/DEPLOYMENT.md) — Comprehensive Vercel deployment, Supabase cloud configuration, environment variables, SPA rewrites, and troubleshooting.
- 🎯 **Evaluator Demo Guide & Scenarios**: [`docs/DEMO_GUIDE.md`](file:///d:/projects/CareBridge/docs/DEMO_GUIDE.md) — Step-by-step clinical walkthrough across all 5 user roles, instant login guide, and demo reset instructions.
- 📋 **Project Overview & Architecture**: [`docs/PROJECT_OVERVIEW.md`](file:///d:/projects/CareBridge/docs/PROJECT_OVERVIEW.md) — Problem statement, proposed solution, main features, system architecture, technology stack, and future scope.
- 🎤 **Presentation & Academic Defense Flow**: [`docs/PRESENTATION_FLOW.md`](file:///d:/projects/CareBridge/docs/PRESENTATION_FLOW.md) — Recommended 8–10 minute university presentation script, slide breakdown, and anticipated Q&A.
- 🗄️ **Database Architecture & RLS Matrix**: [`docs/DATABASE.md`](file:///d:/projects/CareBridge/docs/DATABASE.md) — 14 PostgreSQL tables, foreign keys, constraints, Row-Level Security policies, and private storage specifications.
- 📖 **User Guide & Operational Manual**: [`docs/USER_GUIDE.md`](file:///d:/projects/CareBridge/docs/USER_GUIDE.md) — End-to-end user manual detailing all five roles, step-by-step clinical workflows, and error handling.
- 🧪 **Automated Testing & QA Guide**: [`docs/TESTING.md`](file:///d:/projects/CareBridge/docs/TESTING.md) — Full test suite specifications (Unit, Integration, Live Supabase assessment) and benchmark reports.
- ⚙️ **Environment Configuration Template**: [`.env.example`](file:///d:/projects/CareBridge/.env.example) — Template for Supabase URL, publishable key, and runtime flags.

---

## 🌟 Key Engineering Highlights

- **Five Distinct Role Dashboards**: Complete isolation and role-specific layouts for Patient, Doctor, Receptionist, Laboratory Staff, and Hospital Administrator.
- **Visual Design Identity**: Healthcare SaaS design system: Primary Blue (`#2563EB`), Teal (`#0D9488`), and clean slate background (`#F8FAFC`).
- **PostgreSQL Database & RLS Security**: 14 tables created via declarative SQL migrations in `supabase/migrations/` with zero unrestricted policies (`USING (true)` strictly prohibited for sensitive data).
- **Private Storage**: Secure private `medical-reports` bucket enforcing a 10MB limit, strict MIME whitelisting (PDF, PNG, JPEG, WebP), and authorized time-limited signed download URLs.
- **Modular Service Layer**: 9 isolated services in `src/services/` (`authService`, `patientService`, `doctorService`, `appointmentService`, `consultationService`, `prescriptionService`, `laboratoryService`, `notificationService`, `adminService`).
- **Code Splitting & Performance**: Route-level dynamic imports (`React.lazy`) and manual chunk splitting in `vite.config.ts`, ensuring all JavaScript chunks are under 500 kB.
- **Resilience & Error Handling**: Global `ErrorBoundary` to prevent white screens, real-time `OfflineNotice` detecting internet loss and recovery, and physician double-booking conflict prevention.
- **Automated Test Suite**: 38 automated checks spanning unit tests, integration workflows, and honest live database verification.

---

## 👥 Evaluator Role Accounts (Demo & Test Mode)

Use the one-click demo role badges on the login screen (`/login`) or the top header role switcher to immediately evaluate any dashboard:

| Role | Demo Identity | Credentials | Key Workflows to Test |
| :--- | :--- | :--- | :--- |
| **Patient** | Marcus Vance | `patient@carebridge.demo` / `CareBridge2026!` | • Book an appointment with validation.<br>• Reschedule or cancel active bookings.<br>• Request prescription refills.<br>• View & download diagnostic lab reports.<br>• Update contact profile. |
| **Doctor** | Dr. Sarah Chen, MD | `doctor@carebridge.demo` / `CareBridge2026!` | • View assigned appointments & patient queue.<br>• Conduct & sign clinical consultation.<br>• Add ICD-10 diagnosis & vital signs.<br>• Issue electronic prescriptions & order lab tests.<br>• Schedule follow-up check-ins. |
| **Receptionist** | Elena Morales | `receptionist@carebridge.demo` / `CareBridge2026!` | • Register walk-in patients and generate queue tickets.<br>• Advance patient queue stages (`Check-in` ➔ `Triage` ➔ `Doctor`).<br>• Confirm, reschedule, or cancel bookings.<br>• Inspect non-clinical patient intake dossiers. |
| **Laboratory** | David Patel, MLS | `laboratory@carebridge.demo` / `CareBridge2026!` | • Accept pending orders and advance to `In Progress`.<br>• Filter by urgency (STAT highlighted).<br>• Upload diagnostic reports with file attachment picker.<br>• Publish verified certificates to private storage. |
| **Administrator** | Dr. Arthur Kingsley | `admin@carebridge.demo` / `CareBridge2026!` | • Monitor department bed occupancy & census telemetry.<br>• Toggle physician availability.<br>• Provision new staff accounts through trusted workflow.<br>• Review real-time audit logs & export audit as CSV. |

---

## 🚀 Getting Started

### 1. Prerequisites
- Node.js (v18.0.0 or higher)
- npm or pnpm

### 2. Installation
```bash
npm install
```

### 3. Environment Configuration
Copy `.env.example` to `.env`:
```bash
cp .env.example .env
```
*(When `VITE_USE_MOCK_FALLBACK=true`, the application operates with local simulated clinical datasets; to connect to your live Supabase cloud instance, provide your `VITE_SUPABASE_URL` and `VITE_SUPABASE_ANON_KEY`.)*

### 4. Development Server
```bash
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) in your browser.

### 5. Automated Tests
```bash
npm test
```

### 6. Production Build
```bash
npm run build
```

---

## 🛠️ Technology Stack

- **Frontend**: React 18, TypeScript, Vite, Tailwind CSS, shadcn/ui primitives, Radix UI.
- **Routing & State**: React Router v6, React Context API (`AuthContext`).
- **Icons & Visuals**: Lucide React, Recharts (Patient flow, registration trends, bed occupancy).
- **Backend & Database**: Supabase (PostgreSQL 15, Supabase Authentication, Private Storage, Supabase Realtime).
