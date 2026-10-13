# Hostel Management System

A MERN-stack web app for managing hostel students, room-wise attendance and user accounts. Wardens (admins) add students and record attendance, and everyone can view records and simple analytics.

**Stack:** MongoDB, Express, React, Node.js, Redux, JWT

## Features

- Register and log in with JWT authentication
- Two roles: admin and normal user
- Add students and view them by room number
- Record attendance for a room and view attendance history
- Attendance analysis screen with search and CSV export
- Admin controls: user list, edit users, delete old attendance records
- Seed script with sample students for quick testing
- Heroku-style deployment config (`Procfile`)

## API overview

| Area | Endpoints |
|---|---|
| Users | `POST /users` (register), `POST /users/login`, `GET /users` (admin) |
| Students | `GET /student/all`, `POST /student/addStudent` (admin), `GET /student/room/:roomId` |
| Attendance | `POST /attendance` (admin), `GET /attendance/:roomId`, `POST /attendance/getAnalysis`, `DELETE /attendance/:days` (admin) |

In development the React app proxies these routes to the API on port 5000.

## Project structure

```text
Hostel-Management-master/
├── server/      # Express API: controllers, models, routes, auth middleware, seeder
├── frontend/    # React app: screens, components, Redux actions and reducers
└── assets/      # Images
```

## Run locally

You need Node.js and a MongoDB database.

1. Create `Hostel-Management-master/.env`:

```text
NODE_ENV=development
PORT=5000
MONGO_URI=<your MongoDB connection string>
JWT_SECRET=<a long random string>
```

2. Install and start both servers:

```bash
cd Hostel-Management-master
npm install
npm install --prefix frontend
npm run dev
```

3. Optional: load sample students with `node server/seeder.js`.

The React app runs on http://localhost:3000 and the API on http://localhost:5000.

## Possible improvements

- Add real screenshots of the app
- Add automated tests for the API
- Upgrade old dependencies (Mongoose 5, Node 15)
