# SmartExam — Smart Exam Hall Allocation System

A MERN starter project for the FYP: admin dashboard, hall management, student management, allocation preview, and printable seating reports.

## Stack
- React + Vite + custom responsive CSS
- Express + MongoDB/Mongoose
- JWT admin authentication
- CSV/XLSX import with SheetJS
- PDF export with jsPDF
- Constraint-aware greedy / graph-colouring-inspired allocator (same-subject adjacency avoidance)

> This is a working foundation, not a validated ML model. The allocation engine is a deterministic heuristic. For your final-year research claims, evaluate it against baselines and only describe it as ML if you train and validate a genuine model.

## Requirements
Node.js 20+, MongoDB (local or Atlas).

## Setup
1. Copy `server/.env.example` to `server/.env` and configure MongoDB + JWT secret.
2. From `server/`: `npm install`, then `npm run dev`.
3. From `client/`: `npm install`, then `npm run dev`.
4. Open the Vite URL (normally http://localhost:5173).

Demo mode: the frontend opens with sample data when the API is not configured. To use persistent data, create an admin via `POST /api/auth/register` (first admin only) or use the login endpoint after registration.

## Student import format
CSV/XLSX columns: `registerNumber`, `name`, `department`, `subjectCode` (subjectCode is used for adjacency constraints). Example: `students-sample.csv`.

## Main API
- `POST /api/auth/register`, `POST /api/auth/login`, `GET /api/auth/me`
- `GET/POST/PUT/DELETE /api/halls`
- `GET/POST/DELETE /api/students`, `POST /api/students/import`
- `POST /api/allocations/generate`, `GET /api/allocations/latest`

## Before submission
- Add authorization and validation tests, role-based access, audit logging, real-world data consent, and backups.
- Add invigilator constraints / department mixing / exam-session support if required.
- Measure runtime, utilization, same-subject adjacency conflicts and compare against random/round-robin baselines.
