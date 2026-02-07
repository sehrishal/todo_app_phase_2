# Todo Application - Phase II

A full-stack, multi-user web application for task management with secure authentication.

## Tech Stack

- **Backend**: Python 3.11+, FastAPI, SQLModel, PostgreSQL (Neon)
- **Frontend**: Next.js 14+, TypeScript, Tailwind CSS
- **Authentication**: JWT-based authentication

## Project Structure

```
todo_app_phase_2/
├── backend/
│   ├── src/
│   │   ├── api/         # API routes (auth, tasks)
│   │   ├── auth/        # JWT authentication middleware
│   │   ├── models/      # SQLModel models and Pydantic schemas
│   │   ├── db.py        # Database configuration
│   │   └── main.py      # FastAPI application entry
│   ├── tests/           # Backend tests
│   └── pyproject.toml   # Python dependencies
├── frontend/
│   ├── src/
│   │   ├── app/         # Next.js App Router pages
│   │   ├── components/  # React components
│   │   ├── contexts/    # React contexts (Auth)
│   │   ├── lib/         # Utility libraries
│   │   ├── services/    # API client services
│   │   └── types/       # TypeScript type definitions
│   └── package.json     # Node.js dependencies
└── .env.example         # Environment variables template
```

## Prerequisites

- Python 3.11+
- Node.js 20+
- PostgreSQL database (Neon recommended)

## Setup

### 1. Clone and Configure Environment

```bash
# Copy environment template
cp .env.example .env

# Edit .env with your values:
# - DATABASE_URL: Your Neon PostgreSQL connection string
# - BETTER_AUTH_SECRET: A secure random string (min 32 characters)
```

### 2. Backend Setup

```bash
cd backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -e .

# Run the backend server
uvicorn src.main:app --reload --port 8000
```

### 3. Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Run the development server
npm run dev
```

## Usage

1. Open http://localhost:3000 in your browser
2. Create an account or log in
3. Start creating and managing your tasks!

## API Endpoints

### Authentication
- `POST /auth/signup` - Register a new user
- `POST /auth/login` - Authenticate and get JWT token

### Tasks (requires authentication)
- `GET /api/tasks` - List all tasks for current user
- `POST /api/tasks` - Create a new task
- `GET /api/tasks/{id}` - Get a specific task
- `PUT /api/tasks/{id}` - Update a task
- `PATCH /api/tasks/{id}/complete` - Toggle task completion
- `DELETE /api/tasks/{id}` - Delete a task

## Features

- User registration and authentication
- Create tasks with title and description
- View personal task list
- Edit task details
- Mark tasks as complete/incomplete
- Delete tasks
- User data isolation (each user sees only their tasks)

## Security

- JWT-based authentication
- Password hashing
- User isolation on all task operations
- CORS configuration for frontend access
