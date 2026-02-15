# 🚀 Automated CI/CD Pipeline for a 2-Tier Flask Application on AWS EC2

## 📌 Project Overview

This project demonstrates an end-to-end DevOps implementation of a containerized 2-tier web application (Flask + MySQL) deployed on AWS EC2.

The system uses Jenkins to implement a fully automated CI/CD pipeline.  
Any push to the `main` branch automatically triggers a build and redeployment using Docker and Docker Compose.

This setup simulates a real-world startup deployment workflow with automated builds, containerized services, and cloud infrastructure.

---

## 🏗 Architecture

```
Developer
   │
   │ (git push)
   ▼
GitHub Repository
   │
   │ (Webhook Trigger)
   ▼
Jenkins (CI/CD Server on EC2)
   │
   ├── Clone Repository
   ├── Build Docker Image
   ├── Stop Existing Containers
   └── Deploy via Docker Compose
            │
            ▼
        AWS EC2 Instance
            ├── Flask Container (Port 5000)
            └── MySQL Container (Persistent Volume)
```

---

## ⚙️ Tech Stack

- **Cloud Platform:** AWS EC2 (Ubuntu 22.04 LTS)
- **Backend:** Flask (Python)
- **Database:** MySQL
- **Containerization:** Docker
- **Orchestration:** Docker Compose
- **CI/CD:** Jenkins (Pipeline as Code)
- **Source Control:** GitHub
- **Automation Trigger:** GitHub Webhooks

---

## 🔄 CI/CD Workflow

1. Developer pushes code to GitHub (`main` branch)
2. GitHub webhook sends event to Jenkins
3. Jenkins pipeline triggers automatically
4. Pipeline stages:
   - Clone repository
   - Build Docker image
   - Stop old containers
   - Deploy updated containers
5. Updated application becomes live instantly on EC2

Fully automated deployment with zero manual intervention.

---

## 📂 Project Structure

```
.
├── app.py
├── Dockerfile
├── docker-compose.yml
├── Jenkinsfile
├── requirements.txt
├── message.sql
├── templates/
│   └── index.html
└── README.md
```

---

## 🐳 Container Architecture

### MySQL Container
- Persistent Docker volume for data durability
- Health checks enabled
- Isolated Docker network

### Flask Container
- Built from lightweight `python:3.9-slim`
- Uses environment variables for database configuration
- Connected to MySQL via Docker network
- Health checks configured

---

## 🔐 Security & Best Practices

- Database credentials managed via environment variables
- Docker network isolation between services
- Jenkins authentication enabled
- AWS Security Group configured for required ports only
- Persistent storage using Docker volumes
- Health checks for service reliability

---

## 🚀 Manual Deployment (Without CI/CD)

```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
docker compose up -d --build
```

Access application:

```
http://<ec2-public-ip>:5000
```

---

## 📸 Screenshots

### Jenkins Pipeline - Successful Build

<img width="1920" height="964" alt="Screenshot (174)" src="https://github.com/user-attachments/assets/38b4e07a-7469-4554-83d5-f1d851e6fdab" />



### Pipeline Stage View

<img width="1920" height="962" alt="Screenshot (173)" src="https://github.com/user-attachments/assets/e8f9526a-5509-4462-bba6-c1516045f5a9" />



### Docker Containers Running

<img width="1920" height="948" alt="Screenshot (171)" src="https://github.com/user-attachments/assets/d9acd52a-cb66-4d90-8d3f-35e3e9f71980" />



### Running Application on EC2

<img width="1920" height="969" alt="Screenshot (175)" src="https://github.com/user-attachments/assets/1d671a63-8b3c-44a7-b2fa-d3621adacb8c" />


---


## 📈 Future Improvements

- Move Jenkins to a dedicated EC2 instance
- Push Docker images to Docker Hub or AWS ECR
- Implement image version tagging strategy
- Add Nginx reverse proxy with HTTPS
- Add monitoring (Prometheus + Grafana)
- Use Terraform for Infrastructure as Code
- Deploy using Kubernetes (EKS)

---

## 🎯 DevOps Concepts Demonstrated

- CI/CD Automation
- Pipeline as Code
- Webhook-based triggering
- Containerized architecture
- Automated deployment workflow
- Cloud infrastructure deployment
- Multi-container orchestration
- Persistent storage management

---

## 👩‍💻 Author

Anjali Yadav  
Cloud/DevOps Engineer  

---

⭐ If you found this useful, consider giving this repository a star!
