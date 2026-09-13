# Kittygram — Full-Stack Application with Docker & CI/CD

A full-stack web application for creating and sharing cat profiles and achievements.

The project demonstrates how a React frontend and Django REST API can be containerized, connected to PostgreSQL, served through Nginx, and automatically tested and deployed using GitHub Actions.

> **Project type:** Educational / portfolio project
> **Focus:** Full-stack development, Docker, deployment, CI/CD

## Key Features

* User authentication
* Create and manage cat profiles
* Upload cat images
* Add achievements to cat profiles
* REST API
* PostgreSQL database
* Containerized frontend and backend
* Nginx reverse proxy
* Automated testing
* CI/CD pipeline with GitHub Actions
* Production deployment

## 🛠 Tech Stack

### Backend

* **Python**
* **Django**
* **Django REST Framework**
* **PostgreSQL**

### Frontend

* **React**
* **JavaScript**

### Infrastructure

* **Docker**
* **Docker Compose**
* **Nginx**
* **Gunicorn**
* **GitHub Actions**

### Testing

* **Pytest**

## Application Architecture

The application consists of several services running in Docker containers:

```text
                    ┌──────────────┐
                    │    Client    │
                    └──────┬───────┘
                           │
                           ▼
                    ┌──────────────┐
                    │    Nginx     │
                    └──────┬───────┘
                           │
              ┌────────────┴────────────┐
              ▼                         ▼
       ┌─────────────┐           ┌─────────────┐
       │   React     │           │ Django API  │
       │  Frontend   │           │   Backend   │
       └─────────────┘           └──────┬──────┘
                                        │
                                        ▼
                                 ┌─────────────┐
                                 │ PostgreSQL  │
                                 └─────────────┘
```

## Docker

The application is split into separate containers for the main services.

Docker Compose is used to manage the production environment and service dependencies.

This makes the application easier to reproduce across different environments.

## CI/CD

GitHub Actions is used to automate the development workflow.

The pipeline can:

1. Run automated tests
2. Validate the application
3. Build/deploy the application
4. Notify about the deployment result

This allows changes pushed to the main branch to go through an automated deployment workflow instead of requiring manual deployment steps.

## Nginx

Nginx is used as a reverse proxy between the client and application services.

It handles routing requests to the appropriate frontend/backend service and serves static files.

## Database

The application uses PostgreSQL as the production database.

Database migrations are handled by Django migrations.

## Testing

The project includes automated tests.

Run the test suite with:

```bash
pytest
```

## Local Setup

### 1. Clone the repository

```bash
git clone https://github.com/dasmindme/kittygram_final.git
cd kittygram_final
```

### 2. Create environment variables

Create a `.env` file based on `.env.example`.

Example:

```env
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=your_password
DB_NAME=kittygram
DB_HOST=db
DB_PORT=5432
DEBUG=False
```

### 3. Start the production environment

```bash
docker compose -f docker-compose.production.yml up --build
```

### 4. Apply migrations

```bash
docker compose -f docker-compose.production.yml exec backend python manage.py migrate
```

### 5. Collect static files

```bash
docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
```

## What This Project Demonstrates

This project demonstrates practical experience with:

* full-stack web applications
* REST APIs
* React
* Django REST Framework
* PostgreSQL
* Docker and Docker Compose
* Nginx
* Gunicorn
* CI/CD
* GitHub Actions
* automated testing
* production deployment

## About

This project is part of my full-stack development portfolio and demonstrates my ability to build, containerize, test, and deploy web applications.
