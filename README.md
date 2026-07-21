# 🌱 PlantApp Backend

PlantApp is a plant observation and identification app that allows users to upload photos of plants, get automatic identification suggestions via the **perenual API**, and share their observations with a community.  
This repo contains the **backend API** built with **Node.js** and **Express.js**, connected to **MongoDB** and **Firebase Storage**, and secured with **JWT authentication**.

---

## 🚀 Deployed API

- **Base URL**: [https://plantapp-2mp9.onrender.com]
- **API Docs (Swagger UI)**: [https://plantapp-2mp9.onrender.com/api-docs/]

---

## ✨ Features

- 🔑 **User Authentication** – JWT-based login & signup
- 🌍 **Public Observation Feed** – browse recent plant posts
- 📸 **Observation Posting** – upload plant photos (stored on Firebase) with name, location, and notes
- 🌿 **Plant Identification** – powered by perenual API integration
- 📜 **Activity Feed** – see your own plant observation history
- 🔎 **Search & Filter** – by plant name, location, or date
- 🧪 **Testing** – functional tests with Mocha, Chai, Chai HTTP, and Faker
- 📖 **API Documentation** – via Swagger

---

## 🛠️ Tech Stack

- **Backend Framework**: Node.js + Express.js
- **Database**: MongoDB (Atlas)
- **Storage**: Firebase (for images)
- **Authentication**: JWT
- **Middleware**: CORS, Helmet
- **API Docs**: Swagger
- **Testing**: Mocha, Chai, Chai HTTP, Faker
- **API Client**: Postman (for manual testing)

---

## 📂 Project Structure

```bash
plantapp-backend/
│── src/
│   ├── controllers/    # API controllers
│   ├── db/             # Database connection
│   ├── errors/         # Custom error handlers
│   ├── middleware/     # Auth & security middleware
│   ├── models/         # Mongoose models
│   ├── routes/         # Express routes
│   ├── util/           # Utility functions (Firebase, helpers, etc.)
│   ├── app.js          # Express app setup
│   ├── firebase.js     # Firebase storage config
│   ├── server.js       # Entry point
│   └── firebase-key.json # Firebase service account key
│── tests/              # Functional tests              # Environment variables (not committed)
│── .env.example        # Example env vars
│── .gitignore
│── .node-version
│── package.json
│── package-lock.json
│── swagger.yaml        # API docs (Swagger)
│── README.md

```

---

## ⚙️ Installation & Setup

Clone the repo

```bash
git clone https://github.com/Code-the-Dream-School/jj-practicum-team-1-back.git

```

---

## Install dependencies

```bash
npm install
```

---

## Set up environment variables

Create a .env file based on .env.example and add your keys:

**MONGO_URI**=your_mongodb_connection

**JWT_SECRET**=your_jwt_secret

**JWT_LIFETIME**=value

**FIREBASE_KEY**=your_firebase_key

**PLANTNET_KEY**=your_plantnet_api_key

**PERENUAL_KEY**=value

## Run the server (dev mode)

```bash
npm run dev
```

## Run tests

```bash
npm run test
```

---

## Setting up the VS Code Debugger

1. On your local machine create a new folder
2. Bring in both the `plantasy-back` and the `plantasy-front` directories into that newly created parent folder
3. In the parent folder create another child folder called `.vscode` which will be a sibling to the other two directories
4. In the `.vscode` folder create two files called:
   - `launch.json`
   - `tasks.json`
5. Paste the following in the `launch.json` file:

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Backend (Node)",
      "program": "${workspaceFolder}/plantasy-back/src/server.js",
      "cwd": "${workspaceFolder}/plantasy-back",
      "envFile": "${workspaceFolder}/plantasy-back/.env",
      "console": "integratedTerminal"
    },
    {
      "type": "chrome",
      "request": "launch",
      "name": "Frontend (React)",
      "url": "http://localhost:5173",
      "webRoot": "${workspaceFolder}/plantasy-front",
      "preLaunchTask": "Start Frontend Dev Server"
    }
  ],
  "compounds": [
    {
      "name": "Full Stack App",
      "configurations": ["Backend (Node)", "Frontend (React)"]
    }
  ]
}
```

6. Paste the following in the `tasks.json` file:

```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Start Frontend Dev Server",
      "type": "shell",
      "command": "npm run dev",
      "options": {
        "cwd": "${workspaceFolder}/plantasy-front"
      },
      "isBackground": true,
      "problemMatcher": {
        "pattern": {
          "regexp": "^$"
        },
        "background": {
          "activeOnStart": true,
          "beginsPattern": "VITE",
          "endsPattern": "ready in"
        }
      },
      "presentation": {
        "reveal": "always",
        "panel": "dedicated"
      }
    }
  ]
}
```

7. Open VS Code from the parent directory and now you should be able to run the debugger
   - Just make sure the servers are not already in use

---

## 📬 API Usage

You can explore endpoints via Swagger UI.
Or test with Postman using the base URL:

```bash
https://plantapp-2mp9.onrender.com/api/v1
```

---

## ✅ Core Endpoints

Auth
POST /api/v1/auth/register – Register new user

POST /api/v1/auth/login – Login & get JWT

Plants
GET /api/v1/plants – Public feed of observations

POST /api/v1/plants – Create new observation (auth required)

GET /api/v1/plants/:id – View single observation

PUT /api/v1/plants/:id – Update observation (auth required)

DELETE /api/v1/plants/:id – Delete observation (auth required)

---

## 🧪 Testing

We use Mocha + Chai + Chai HTTP + Faker for functional and integration tests.

Run all tests:

```bash
npm run test
```

---

## 📸 Storage

Plant observation images are stored in Firebase Storage.

Plants metadata (name, notes, location, etc.) is stored in MongoDB.

---

## 🧩 Schema

### User Schema

- name
  - String
  - required
- email
  - String
  - required
- password
  - String
  - required

### Plant Schema

- name
  - String
  - required
- imageURL
  - String
- notes
  - String
- location
  - String
- createdBy
  - ObjectId
  - required

---

## 🔐 Authentication

JWT tokens are issued on login/register.

Protected routes require Authorization: Bearer <token> in the header.

---

## 🌍 Third-Party API

We integrate with the Perenual API for automatic plant identification.

---

## 👥 Contributors

Jaguar Team 1(Code the Dream)

---

## 📜 License

MIT License – feel free to use and contribute.
