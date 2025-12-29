Mini Project Setup - I



This project is divided into three parts to help you progressively build, containerize, and manage a full-stack application with persistence and debugging.
What you are building
You will set up the file structure and plan a full-stack app that includes:

A React frontend
An Express backend
A PostgreSQL database
This stage focuses on organizing the project and thinking through the services.

Tasks
Create the main project folder fullstack-docker-app
Inside, create frontend, backend, and db-data folders
Create empty files:
docker-compose.yml (empty or with top-level version info)
backend/Dockerfile (empty)
frontend/Dockerfile (empty)
.env (empty,for future use)
Initialize a Git repository
Create this README file as documentation
Folder structure


fullstack-docker-app/
├── backend/
│ ├── app.js
│ └── package.json
├── frontend/
│ ├── package.json
│ └── src/
│ └── App.js
├── db-data/ --------------- --------------------- # For database volume
├── docker-compose.yml ----------------- # Empty,
├── .env -------------------------------------------- # Empty for future use.
└── README.md ------------------------------

You are provided the code for both the backend (Node.js + Express + PostgreSQL) and the frontend (React).

Copy-paste the provided code into the appropriate files in your project folder structure.



Set up backend
Inside backend/, create app.js:



const express = require('express');
const { Client } = require('pg');
const app = express();
const port = 5000;

const dbClient = new Client({
  host: process.env.DB_HOST || 'localhost',
  user: process.env.DB_USER || 'postgres',
  password: process.env.DB_PASSWORD || 'postgres',
  database: process.env.DB_NAME || 'testdb',
  port: process.env.DB_PORT || 5432,
});

dbClient.connect()
  .then(() => console.log('Connected to Postgres'))
  .catch((err) => console.error('Failed to connect to Postgres', err));

app.get('/api', async (req, res) => {
  try {
    const result = await dbClient.query('SELECT NOW() AS time');
    res.send(`Hello from Express + Postgres! Server time: ${result.rows[0].time}`);
  } catch (err) {
    console.error('DB query error:', err);
    res.status(500).send('Database error');
  }
});

app.listen(port, () => {
  console.log(`Backend listening at http://localhost:${port}`);
});
Add a package.json with:

json

{
  "name": "backend",
  "version": "1.0.0",
  "main": "app.js",
  "scripts": {
    "start": "node app.js"
  },
  "dependencies": {
    "express": "^4.18.2",
    "pg": "^8.7.3"
  }
}
Set up frontend
Inside frontend/src/
create App.js:

import React, { useEffect, useState } from 'react';

function App() {
  const [message, setMessage] = useState('');

  useEffect(() => {
    fetch('/api')
      .then((res) => res.text())
      .then((data) => setMessage(data))
      .catch((err) => console.error('Error fetching from backend:', err));
  }, []);

  return (
    <div>
      <h1>React + Express + Postgres App</h1>
      <p>{message ? message : 'Loading...'}</p>
    </div>
  );
}

export default App;
Add a package.json:

json

{
  "name": "frontend",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-scripts": "5.0.1"
  },
  "scripts": {
    "start": "react-scripts start"
  },
  "proxy": "http://localhost:5000"
}
What to do for submission
Create a GitHub repository (suggested name: fullstack-docker-app).
Initialize Git in your local project folder.
Add all files to the repository and make your first commit.
Link your local repository to GitHub and push all files to the main branch.
Verify that your repository structure on GitHub shows:
backend/ with app code
frontend/ with app code
db-data/ (empty folder for database volume)
.env file (empty for now)
docker-compose.yml
README.md
For Submission:

Take a screenshot of your GitHub repository page showing the full project structure in your browser.

Make sure the screenshot clearly displays the repository name and all folders/files listed above.

Important Notes:

Make sure your GitHub repository is public or shared in a way that we can view it.
Double-check that your code is committed and pushed to GitHub before sharing the link.

Submission Requirements
What you need to submit:

Submit a screenshot of your GitHub repository page showing the project structure clearly.

The screenshot should display all required files and folders in the repository:

backend/ with app code
frontend/ with app code
db-data/ (empty folder for DB volume)
.env file (can be empty for now)
docker-compose.yml
README.md
Important Notes:

Ensure your repository is public or accessible for review.
The screenshot must clearly show the repository name and file structure in the browser.