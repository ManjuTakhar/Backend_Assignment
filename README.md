# Backend_Assignment

## 🐞 Mini Issue Tracker API — Backend Intern Assignment

### 📌 Goal

Build a mini issue tracker API using Python + FastAPI + PostgreSQL. The service should allow teams to manage projects, issues, and comments.

### ⚙️ Tech Stack

- Python 3.10+
- FastAPI
- PostgreSQL
- SQLAlchemy / SQLModel (your choice)
- Pydantic for request/response schemas
- Uvicorn for running the server

Note: Alembic migrations are optional — you can just use `Base.metadata.create_all`.

### 📂 Data Models

#### Project

- id (PK int/UUID)
- name (string, required, unique)
- key (string, required, unique, e.g. "PRJ")

#### Issue

- id (PK int/UUID)
- project_id (FK → Project, required)
- title (string, required)
- description (text, optional)
- status (enum: OPEN | IN_PROGRESS | DONE, default OPEN)
- priority (enum: LOW | MEDIUM | HIGH, default MEDIUM)
- assignee (string, optional)
- created_at (timestamp, default now)
- updated_at (timestamp, auto-update)

#### Comment

- id (PK int/UUID)
- issue_id (FK → Issue, required)
- body (text, required)
- author (string, optional)
- created_at (timestamp, default now)

### 📑 API Endpoints

```
POST   /projects
GET    /projects

POST   /projects/{project_id}/issues
GET    /projects/{project_id}/issues

GET    /issues/{issue_id}
PATCH  /issues/{issue_id}

POST   /issues/{issue_id}/comments
```

`PATCH /issues/{issue_id}` updates one or more fields (title, description, status, priority, assignee) and refreshes `updated_at`.

---
