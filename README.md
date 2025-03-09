# 🏆 NYU Application Security - Homework 3: Deployment Gone Wrong  
**Grade: 100/100** ✅  

## 🚀 Introduction  
Right when you thought things couldn't get worse, your company decided to re-hire **Shoddycorp's Cut-Rate Contracting** again. While they containerized the application and set up Kubernetes, they left **major security issues, leaked secrets, and poor deployment practices** in place.  

Your job? **Fix their mistakes** and secure the deployment properly.

---

## 📁 Project Overview  

This assignment involved working with:  
- **Docker** 🐳 - Containerizing the web app, database, and reverse proxy  
- **Kubernetes (Minikube)** ☸️ - Deploying a scalable and secure system  
- **Prometheus** 📊 - Setting up monitoring for application health  
- **GitHub Actions** 🤖 - Automating Docker image deployment  

---

## 📌 Assignment Breakdown  

### **Part 1: Getting the Broken Deployment Running**  
✅ Installed and configured **Docker, Minikube, and kubectl**  
✅ Built Docker images and deployed them to a **local Kubernetes cluster**  
✅ Fixed issues in **Kubernetes YAML configurations**  

### **Part 2: Securing Secrets**  
✅ Identified and **removed hardcoded secrets** in Django settings  
✅ Implemented **Kubernetes Sealed Secrets** for secure secret management  
✅ Updated the application to **load secrets securely from environment variables**  

### **Part 3: Monitoring with Prometheus**  
✅ Removed **insecure logging of sensitive data**  
✅ Implemented **custom Prometheus metrics** for monitoring errors  
✅ Deployed **Prometheus to Kubernetes** for real-time metric collection  

---

## 📂 Key Files in This Repository  

### 🖥️ **Web Application (Django)**
- `GiftcardSite/GiftcardSite/settings.py` – Fixed hardcoded secrets  
- `GiftcardSite/LegacySite/views.py` – Removed insecure Prometheus monitoring  

### ☸️ **Kubernetes Deployment**
- `GiftcardSite/k8/django-deploy.yaml` – Updated app deployment  
- `db/k8/db-deployment.yaml` – Secured database secrets  
- `part1.yaml` – **Kubernetes Sealed Secrets file**  

### 📊 **Monitoring & Observability**
- `prometheus.yaml` – Config for **Prometheus monitoring in Kubernetes**  
- `prometheus.txt` – Writeup on setting up Prometheus  

### 🔑 **Security & Secrets**
- `secrets.txt` – Document detailing **secure secrets implementation**  

### ⚙️ **Automation & CI/CD**
- `.github/workflows/deploy.yml` – GitHub Actions workflow for **Docker image deployment**  

---

## 💡 Key Takeaways  
- **Never hardcode secrets** 🔑 in source code  
- **Use Kubernetes Sealed Secrets** for secure credential management  
- **Always log responsibly** – avoid exposing sensitive data  
- **Infrastructure as Code (IaC) + CI/CD** makes deployments scalable and secure  

---

## 🚀 Running the Project Locally  

1. **Start Minikube**  
   ```bash
   minikube start
##2. 🛠️ Build Docker Images
```bash
docker build -t nyuappsec/assign3:v0 .
docker build -t nyuappsec/assign3-proxy:v0 proxy/
docker build -t nyuappsec/assign3-db:v0 db/
## 3.🛠️ Deploy to Kubernetes
kubectl apply -f db/k8
kubectl apply -f GiftcardSite/k8
kubectl apply -f proxy/k8
## 4.🛠️ Check Running Pods
kubectl get pods
## 5. Access the Web application
minikube service proxy-service

