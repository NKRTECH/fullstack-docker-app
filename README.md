# Fullstack Docker App

A full-stack application featuring a React frontend, Express backend, and PostgreSQL database, designed for containerization with Docker.

## Technologies

- **Frontend**: React
- **Backend**: Node.js with Express
- **Database**: PostgreSQL

## Project Structure

```
fullstack-docker-app/
├── backend/
│   ├── app.js
│   └── package.json
├── frontend/
│   ├── package.json
│   └── src/
│       └── App.js
├── db-data/          # Database volume
├── docker-compose.yml
├── .env
└── README.md
```

## Backend

The backend provides an API endpoint at `/api` that queries the PostgreSQL database for the current server time.

## Frontend

The React app fetches and displays the message from the backend API.