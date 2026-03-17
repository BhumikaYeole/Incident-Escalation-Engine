#  Incident Escalation Engine (DevOps-Focused Backend Project)

A **DevOps-oriented backend system** that simulates real-world **incident escalation workflows** used by SRE and reliability teams.

This project demonstrates the **complete software delivery lifecycle**:

- Backend system design (Spring Boot)
- Containerization (Docker)
- Automated CI/CD (GitHub Actions)
- Image Registry Integration (Docker Hub)
- Production-style deployment readiness

---

##  Project Overview

In large distributed systems, failures must be detected, tracked, and escalated automatically.

This application allows:

- Creating incidents with severity levels
- Automatic escalation simulation based on time gaps
- Acknowledgement handling
- Metrics dashboard for operational visibility

---

## Tech Stack

### Backend
- Java 21
- Spring Boot
- Spring Data JPA
- Lombok

### Database
- PostgreSQL

### DevOps / Infrastructure
- Docker
- Docker Compose
- GitHub Actions (CI/CD)
- Docker Hub (Container Registry)

---

##  Features
### 1. Incident Management
- Create incident with severity & trigger source
- Status lifecycle:
 ```
 OPEN → NOTIFIED → ESCALATED → ACKNOWLEDGED
```

### 2. Escalation Simulation
Time-based escalation intervals:

| Severity | Escalation Delay |
|---------|-----------------|
| HIGH | 10 sec |
| MEDIUM | 30 sec |
| LOW | 60 sec |

### 3. Metrics Dashboard
Operational metrics include:

- Open incidents count
- Acknowledged incidents count
- Average acknowledgement time

---


##  Docker Setup

### Build and Run Locally
```
docker compose up --build
```

### Services:
- Spring Boot App → Port 8080
- PostgreSQL → Internal container network

## CI/CD Pipeline (GitHub Actions)
Automated pipeline triggers on every push to master branch.

### Pipeline Workflow
```
Push Code
   ↓
Build Maven Project
   ↓
Build Docker Image
   ↓
Login to Docker Hub
   ↓
Push Image to Docker Hub
```
### Pipeline File
```
.github/workflows/ci-cd.yml
```

## Docker Hub Image
Docker image is automatically published via CI/CD:
```
docker.io/0512bhumika/incident-engine:latest
```
This enables portable cloud deployments.
