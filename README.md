# 🚀 Flask CI/CD on Kubernetes

This project demonstrates a complete **CI/CD pipeline** for a simple Flask application, using **GitHub Actions, Docker, GitHub Container Registry (GHCR), and Kubernetes (k3s)**. Based on [ubc/flask-sample-app](https://github.com/ubc/flask-sample-app) application.

---

## 🔧 Tech Stack
- **Application:** Python (Flask)  
- **CI/CD:** GitHub Actions (self-hosted runner)  
- **Containerization:** Docker, GitHub Container Registry (GHCR)  
- **Orchestration:** Kubernetes (k3s)  
- **Networking:** Traefik 
- **Testing:** pytest, coverage.py  

---

## 📌 Features
- ✅ Unit testing with `pytest`  
- ✅ Code coverage reports 
- ✅ Docker image build & push to **GHCR**  
- ✅ Automated deployment to **Kubernetes (k3s)**  
- ✅ Namespaced resources and LoadBalancer service via Traefik  

---

## ⚙️ CI/CD Workflow
1. **CI/CD (Continuous Integration/Continuous Deployment)**  
   - Runs tests and code coverage  
   - Generates coverage report as an artifact  
   - Builds Docker image  
   - Pushes to **GHCR**  

  Triggered on push or pull requests to the `main` branch.  
  - Performs:
  - Dependency installation (runtime + dev) with pip caching.  
  - Unit tests using `pytest`.  
  - Generates code coverage report (`coverage.xml`) and shows summary in logs.  
  - Uploads coverage report as a GitHub Actions artifact.  

2. **CD (Continuous Deployment)**  
   - Deploys to local Kubernetes cluster via self-hosted runner  


   Triggered automatically after a successful CI run (`workflow_run`).  
   - Performs:
   - Builds Docker image and pushes it to **GitHub Container Registry (GHCR)**.
   - Deploys to **k3s** cluster using a self-hosted runner. 
   - Applies Kubernetes manifests (`deployment`, `service`).
   - Waits for successful deployment rollout and shows the status of services.
---

## 📂 Project Structure
flask-test-cicd/
├── README.md
├── app/ # Flask application code
│ ├── init.py
│ └── routes.py
├── tests/ # Unit tests
│ └── test_routes.py
├── kubernetes/ # Kubernetes manifests
│ ├── namespace.yaml
│ ├── deployment.yaml
│ ├── service.yaml
│ └── ingress.yaml
├── .github/
│ └── workflows/ # GitHub Actions pipelines
│ ├── ci.yml
│ └── cd.yml
├── requirements.txt # Python runtime dependencies
├── requirements-dev.txt # Development & test dependencies
├── Dockerfile # Docker build instructions
└── run.py # Entrypoint to run the Flask app

---
## 📝 Author
👤 Konrad Ptasznik  
- GitHub: [@kptasznik](https://github.com/kptasznik)
