# Module 10 – Enhanced Calculator with FastAPI, PostgreSQL, and Docker

## Project Overview

This project enhances the calculator application using **FastAPI, PostgreSQL, SQLAlchemy, and Docker**. It includes automated testing, database integration, security scanning, and a CI/CD pipeline using GitHub Actions.

The application provides calculator operations and incorporates database and user authentication functionality as part of the Module 10 assignment.

## Technologies Used

- Python 3.12
- FastAPI
- PostgreSQL 17
- SQLAlchemy
- Pydantic
- Pytest and Pytest-Cov
- Playwright
- Docker and Docker Compose
- GitHub Actions
- Trivy security scanner

## Repository and Docker Hub

**GitHub Repository:**  
https://github.com/DeepLearnDS/module10_is601

**Docker Hub Repository:**  
https://hub.docker.com/r/codeec/601_module10

**Docker Image:**  
`codeec/601_module10:latest`

## Prerequisites

Install the following before running the application locally:

- Python 3.12
- Docker Desktop
- Docker Compose
- Git

## Running the Application Locally

### 1. Clone the repository

```bash
git clone https://github.com/DeepLearnDS/module10_is601.git
cd module10_is601
```

### 2. Create and activate a virtual environment

```bash
python3 -m venv venv
source venv/bin/activate
```

On Windows PowerShell:

```powershell
venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Start PostgreSQL and the application

Use Docker Compose to start the services:

```bash
docker compose up --build
```

The application is available at:

- **FastAPI application:** http://localhost:8000
- **Swagger API documentation:** http://localhost:8000/docs
- **pgAdmin:** http://localhost:5050

To stop the services:

```bash
docker compose down
```

## Running with Docker Hub

You can download and run the published Docker image without building it locally.

### 1. Pull the image

```bash
docker pull codeec/601_module10:latest
```

### 2. Run the container

```bash
docker run -d --name module10-calculator -p 8000:8000 codeec/601_module10:latest
```

### 3. Access the application

Open:

http://localhost:8000

API documentation:

http://localhost:8000/docs

**Note:** The standalone Docker command starts the application container. For database-dependent functionality, use Docker Compose so that PostgreSQL is also available and configured.

### 4. Stop and remove the container

```bash
docker stop module10-calculator
docker rm module10-calculator
```

## Running Tests

Activate your virtual environment and run:

```bash
pytest -v
```

To run tests with coverage:

```bash
pytest --cov=app --cov-report=term-missing
```

To generate an HTML coverage report:

```bash
pytest --cov=app --cov-report=html
```

The HTML report is generated in the `htmlcov` directory.

## CI/CD Pipeline – GitHub Actions

GitHub Actions automates testing, security scanning, and Docker image deployment.

The workflow includes three jobs:

1. **Test**
   - Installs Python dependencies.
   - Starts a PostgreSQL service.
   - Runs automated tests.
   - Generates test and coverage reports.

2. **Security**
   - Builds the Docker image.
   - Scans the image using Trivy.
   - Checks for HIGH and CRITICAL vulnerabilities.

3. **Deploy**
   - Runs after successful testing and security scanning.
   - Authenticates with Docker Hub using GitHub repository secrets.
   - Builds and pushes the Docker image to Docker Hub.

The Docker Hub deployment uses these GitHub repository secrets:

- `DOCKERHUB_USERNAME`
- `DOCKERHUB_TOKEN`

The published image is tagged as:

```text
codeec/601_module10:latest
codeec/601_module10:<commit-sha>
```

## Project Structure

```text
module10_is601/
│
├── app/
│   ├── database.py
│   ├── models/
│   ├── schemas/
│   └── operations.py
│
├── tests/
│
├── templates/
│
├── .github/
│   └── workflows/
│       └── test.yml
│
├── Dockerfile
├── docker-compose.yml
├── .dockerignore
├── requirements.txt
├── main.py
└── README.md
```

## Learning Outcomes

Through this assignment, I gained experience with:

- Integrating FastAPI with PostgreSQL.
- Working with SQLAlchemy and Pydantic.
- Managing Python dependencies.
- Running automated tests and measuring code coverage.
- Containerizing an application with Docker.
- Using Docker Compose to manage application services.
- Automating testing and deployment through GitHub Actions.
- Scanning Docker images for security vulnerabilities using Trivy.
- Publishing Docker images to Docker Hub.

