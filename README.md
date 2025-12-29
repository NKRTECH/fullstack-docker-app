# Fullstack Docker App

This is a mini project to set up a full-stack application with React frontend, Express backend, and PostgreSQL database, prepared for containerization with Docker.

## Technologies

- **Frontend**: React
- **Backend**: Node.js with Express
- **Database**: PostgreSQL
- **Containerization**: Docker (planned)

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

The backend is a Node.js application using Express, connecting to PostgreSQL.

- `app.js`: Main server file with API endpoint.
- `package.json`: Dependencies and scripts.

## Frontend

The frontend is a React application.

- `src/App.js`: Main component fetching data from backend.
- `package.json`: Dependencies and scripts.

## Next Steps

Future parts will involve Docker containerization, database setup, and deployment.