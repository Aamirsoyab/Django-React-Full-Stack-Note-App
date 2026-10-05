# Django + React Full-Stack Notes App

A full-stack note-taking application built with **Django REST Framework** (backend) and **React + Vite** (frontend), featuring JWT authentication and MS SQL Server as the database.

![Django](https://img.shields.io/badge/Django-6.1-092E20?style=for-the-badge&logo=django&logoColor=white)
![React](https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-8-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![SQL Server](https://img.shields.io/badge/MS%20SQL%20Server-CC2927?style=for-the-badge&logo=microsoftsqlserver&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-black?style=for-the-badge&logo=JSON%20web%20tokens)

---

## Features

- JWT Authentication - Secure login & registration with access + refresh tokens
- Full CRUD for Notes - Create, read, and delete personal notes
- User-Specific Notes - Each user sees only their own notes
- Protected Routes - React routes guarded by authentication state
- Auto Token Refresh - Seamlessly refreshes expired access tokens
- MS SQL Server - Production-grade relational database
- CORS Configured - Frontend & backend communicate securely
- Vite - Lightning-fast frontend dev server

---

## Tech Stack

### Backend
- Django 6.1
- Django REST Framework - REST API
- Simple JWT - Token-based authentication
- django-cors-headers - Cross-origin resource sharing
- mssql-django - MS SQL Server backend
- python-dotenv - Environment variable management

### Frontend
- React 19
- Vite 8
- React Router - Client-side routing
- Axios - HTTP client
- jwt-decode - Token decoding

### Database
- Microsoft SQL Server 2022

---

Project Structure

## 📁 Project Structure

```text
Django-React-Full-Stack-Note-App/
│
├── backend/                          # Django backend
│   ├── api/                          # API application
│   │   ├── migrations/
│   │   ├── models.py                 # Note model
│   │   ├── serializers.py            # User & Note serializers
│   │   ├── urls.py                   # API routes
│   │   └── views.py                  # API views
│   │
│   ├── backend/                      # Django project configuration
│   │   ├── settings.py
│   │   └── urls.py
│   │
│   ├── .env                          # Environment variables (gitignored)
│   ├── manage.py
│   └── requirements.txt
│
├── frontend/                         # React frontend
│   ├── src/
│   │   ├── assets/
│   │   │
│   │   ├── components/               # Reusable components
│   │   │   ├── Form.jsx
│   │   │   ├── LoadingIndicator.jsx
│   │   │   ├── Note.jsx
│   │   │   └── ProtectedRoute.jsx
│   │   │
│   │   ├── pages/                    # Application pages
│   │   │   ├── Home.jsx
│   │   │   ├── Login.jsx
│   │   │   ├── Register.jsx
│   │   │   └── NotFound.jsx
│   │   │
│   │   ├── styles/
│   │   ├── api.js                    # Axios API configuration
│   │   ├── constants.js              # Token key constants
│   │   ├── App.jsx
│   │   └── main.jsx
│   │
│   ├── .env                          # Frontend environment variables (gitignored)
│   ├── package.json
│   └── vite.config.js
│
└── .gitignore
```

---

## Getting Started

### Prerequisites

Make sure you have installed:

- Python 3.10+
- Node.js 18+ & npm
- Microsoft SQL Server 2019+
- ODBC Driver 18 for SQL Server

---

### Backend Setup

1. Clone the repository
   ```bash
   git clone https://github.com/Aamirsoyab/Django-React-Full-Stack-Note-App.git
   cd Django-React-Full-Stack-Note-App

2. Create and activate virtual environment
# Windows
python -m venv env
env\Scripts\activate

# macOS / Linux
python3 -m venv env
source env/bin/activate

3. Install backend dependencies
cd backend
pip install -r requirements.txt

4. Create a database in SQL Server
CREATE DATABASE MyDjangoDB;

5. Create backend/.env file
DB_HOST=localhost
DB_PORT=1433
DB_USER=your_sql_username
DB_NAME=MyDjangoDB
DB_PWD=your_sql_password

6. Run migrations & start server
python manage.py migrate
python manage.py runserver
Backend will run at http://127.0.0.1:8000

### Frontend Setup
1. Open a new terminal, navigate to frontend
cd frontend

2. Install dependencies
npm install

3. Create frontend/.env file
ini
VITE_API_URL=http://127.0.0.1:8000

4. Start the dev server
bash
npm run dev
Frontend will run at http://localhost:5173

API Endpoints
Method	Endpoint	Description	Auth Required
POST	/api/user/register/	Register a new user	No
POST	/api/token/	Obtain access & refresh	No
POST	/api/token/refresh/	Refresh access token	No
GET	/api/notes/	List user's notes	Yes
POST	/api/notes/	Create a new note	Yes
DELETE	/api/notes/delete/<id>/	Delete a note by ID	Yes
Authentication Flow
User registers at /register and sends request to /api/user/register/

User logs in at /login and sends request to /api/token/

Backend returns access + refresh tokens which are stored in localStorage

Axios interceptor attaches Bearer <access> to every request

If access token expires, ProtectedRoute auto-refreshes via /api/token/refresh/

Logout clears localStorage and redirects to /login

Screenshots
Screenshots coming soon...

Future Improvements
□ Edit / update notes
□ Note categories / tags
□ Search & filter notes
□ Markdown support for notes
□ Dark mode
□ User profile page
□ Deployment on Railway / Render
Contributing
Contributions, issues, and feature requests are welcome.
Feel free to fork and submit a pull request.

License
This project is open-source and available under the MIT License.

Author
Aamir Soyab

GitHub: @Aamirsoyab
