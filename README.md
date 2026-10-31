# Cineverse

Cineverse is a full-stack movie booking platform that lets users discover movies, view show timings, book seats, make payments, and manage reservations. The project includes a Node.js/Express backend, a MongoDB data layer, and a React + Vite frontend for the user experience.

## Features

- User registration and login
- JWT-based authentication and protected routes
- Movie catalog and management
- Theatre and screen management
- Show scheduling and seat availability checks
- Booking creation and booking history
- Payment flow integration with Razorpay
- Admin dashboard and administrative management tools
- Email notifications for booking confirmation and cancellation
- Automated expiration for pending bookings

## Tech Stack

### Backend
- Node.js
- Express.js
- MongoDB with Mongoose
- JWT for authentication
- Razorpay API
- Nodemailer for email sending
- Helmet, CORS, rate limiting, and Morgan for API security and monitoring

### Frontend
- React
- Vite
- React Router
- Tailwind CSS
- Framer Motion
- React Toastify

## Project Structure

```text
Cineverse/
├── frontend/                     # React frontend
│   ├── src/
│   ├── package.json
│   └── README.md
├── Movie_Backend_API_Node/       # Express backend
│   ├── controllers/
│   ├── routes/
│   ├── model/
│   ├── middlewares/
│   ├── services/
│   ├── templates/
│   ├── index.js
│   ├── seed-admin.js
│   └── README.md
├── .env                          # Environment variables
├── package.json
├── package-lock.json
├── .gitignore
└── README.md                     # Project overview
```

## Prerequisites

Before running the project, make sure you have the following installed:

- Node.js (v18 or higher recommended)
- npm
- MongoDB connection URL
- Razorpay account (for payment integration)
- SMTP credentials for email functionality

## Environment Variables

Create a `.env` file in the project root with the following configuration:

```env
PORT=1917
DB_URL=mongodb+srv://<username>:<password>@<cluster-url>/<database>
SECRET=your_jwt_secret
RAZORPAY_KEY_ID=your_razorpay_key_id
RAZORPAY_KEY_SECRET=your_razorpay_key_secret
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your_email@gmail.com
EMAIL_PASS=your_app_password
EMAIL_FROM="Cineverse <your_email@gmail.com>"
```

Note: Use a real MongoDB URI and valid email credentials for local or production use.

## Installation

From the project root:

```bash
npm install
```

## Running the Application

Start the backend API:

```bash
npm run start
```

Start the frontend app:

```bash
npm run start:frontend
```

The backend server runs on:

```text
http://localhost:1917
```

The frontend usually runs on:

```text
http://localhost:5173
```

## API Overview

The backend exposes routes under the `/mba/api/v1` prefix.

### Authentication
- `POST /mba/api/v1/auth/signup`
- `POST /mba/api/v1/auth/signin`
- `GET /mba/api/v1/auth/me`
- `PATCH /mba/api/v1/auth/me`
- `POST /mba/api/v1/auth/change-password`

### Movies
- `GET /mba/api/v1/movies`
- `GET /mba/api/v1/movies/:id`
- `POST /mba/api/v1/movies`
- `PUT /mba/api/v1/movies/:id`
- `DELETE /mba/api/v1/movies/:movieId`

### Bookings
- `POST /mba/api/v1/bookings`
- `GET /mba/api/v1/bookings`
- `GET /mba/api/v1/bookings/my-bookings`
- `GET /mba/api/v1/bookings/:id`
- `POST /mba/api/v1/bookings/:bookingId/cancel`

### Admin
- `GET /mba/api/v1/admin/dashboard`
- `GET /mba/api/v1/admin/locations`
- `POST /mba/api/v1/admin/locations`
- `GET /mba/api/v1/admin/screens`
- `POST /mba/api/v1/admin/screens`
- `GET /mba/api/v1/admin/audit-logs`

## Admin Seed

An admin account can be created using:

```bash
npm run seed:admin
```

## Notes

- The project includes automatic cleanup for expired pending bookings every minute.
- Booking confirmation and cancellation emails are sent through the backend email service.
- The frontend serves static assets from the backend in production mode when built.

## License

This project is for educational and portfolio use and is not currently licensed for commercial redistribution unless explicitly stated by the author.
