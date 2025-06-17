# fastapi-postgres-k8s

A minimal full-stack microservice application using **FastAPI** with a **PostgreSQL** database, containerized using **Docker**, and deployed locally with **Kubernetes** using ClusterIP services.

---

## 📦 Tech Stack

- [FastAPI](https://fastapi.tiangolo.com/) (Python)
- PostgreSQL (via official Docker image)
- Docker + Docker Compose (for initial local testing)
- Kubernetes (Minikube)
- ClusterIP services for internal service discovery

---

## 🗂️ Project Structure

```
fastapi-postgres-k8s/
├── app/
│   ├── main.py
│   ├── requirements.txt
│   └── Dockerfile
├── docker-compose.yml
└── k8s/
    ├── fastapi-deployment.yaml
    ├── fastapi-service.yaml
    ├── postgres-deployment.yaml
    ├── postgres-service.yaml
```

---

## 🚀 How to Run

### 1. ✅ Docker Compose (for quick local test)

```bash
docker-compose up --build
```

- Visit: [http://localhost:8000](http://localhost:8000)
- `/` → FastAPI is working  
- `/db` → DB connection check

---

### 2. 🧠 Kubernetes (via Minikube)

#### 🔧 Start Minikube

```bash
minikube start
```

#### 📦 Apply K8s Manifests

```bash
kubectl apply -f k8s/
```

#### 🔁 Port Forward to Access FastAPI

```bash
kubectl port-forward svc/fastapi-service 8000:8000
```

Then visit:
- [http://localhost:8000](http://localhost:8000)
- [http://localhost:8000/db](http://localhost:8000/db)

---

## 📁 Environment Variables

| Variable     | Description              | Set In           |
|--------------|--------------------------|------------------|
| `DB_HOST`    | Hostname of Postgres DB  | Deployment YAML  |
| `DB_USER`    | DB username              | Deployment YAML  |
| `DB_PASS`    | DB password              | Deployment YAML  |
| `DB_NAME`    | DB name                  | Deployment YAML  |

---

## 🔒 Next Steps

- ✅ Use `Secrets` instead of plain env vars
- ✅ Add `PersistentVolume` to make DB stateful
- ✅ Expose FastAPI using `NodePort` or `Ingress`
- ✅ Deploy to a cloud cluster (AWS EKS, GKE, etc.)

---

## 🧑‍💻 Author

**Mukul Bhardwaj**  
[GitHub: @MukulB0412](https://github.com/MukulB0412)

---

## 📜 License

This project is open source and available under the [MIT License](LICENSE).
