# FastAPI CRUD with Kubernetes Deployment

## 📌 Project Overview
This project is a **FastAPI CRUD application** deployed with **Kubernetes** using **Minikube** for local development. It uses **PostgreSQL** as the database and is containerized with **Docker**.

## 🚀 Features
- FastAPI-based **CRUD API**
- **PostgreSQL** database integration
- **Docker** containerization
- **Kubernetes Deployment + Service**
- **GitHub Actions for CI/CD**

## 📂 Project Structure
```
fastapi-k8s-crud/
│── app/
│   ├── main.py          # FastAPI app entry point
│   ├── models.py        # Database models
│   ├── database.py      # DB connection
│   ├── crud.py          # CRUD operations
│   ├── schemas.py       # Pydantic schemas
│── requirements.txt     # Dependencies
│── Dockerfile          # Docker build file
│── k8s/
│   ├── deployment.yaml  # Kubernetes Deployment
│   ├── service.yaml     # Kubernetes Service
│── .github/workflows/
│   ├── deploy.yml       # GitHub Actions workflow
│── README.md            # Documentation
```

---

## 📌 Setup & Installation

### **1️⃣ Clone the repository**
```bash
git clone https://github.com/yourusername/fastapi-k8s-crud.git
cd fastapi-k8s-crud
```

### **2️⃣ Install dependencies**
Create a virtual environment and install dependencies:
```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### **3️⃣ Run FastAPI locally**
```bash
uvicorn app.main:app --host 0.0.0.0 --port 8000
```

API will be available at: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)

---

## 📌 Docker Setup
### **1️⃣ Build the Docker image**
```bash
docker build -t fastapi-k8s-crud .
```

### **2️⃣ Run the container**
```bash
docker run -p 8000:8000 fastapi-k8s-crud
```

---

## 📌 Kubernetes Deployment
### **1️⃣ Start Minikube**
```bash
minikube start --driver=docker
```

### **2️⃣ Apply Kubernetes manifests**
```bash
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

### **3️⃣ Get service URL**
```bash
minikube service fastapi-service --url
```

Your API will be accessible at the given **Minikube URL**.

---

## 📌 CI/CD with GitHub Actions
The project uses **GitHub Actions** to automatically build and push the Docker image on every commit to `main`.

To enable CI/CD:
1. Set **DOCKER_USERNAME** and **DOCKER_PASSWORD** in GitHub Secrets.
2. Push changes to `main` and the workflow will deploy automatically.

---

## 📌 API Endpoints
| Method | Endpoint         | Description          |
|--------|----------------|----------------------|
| POST   | `/items/`       | Create an item      |
| GET    | `/items/{id}`   | Retrieve an item    |

Test with `curl`:
```bash
curl -X POST "http://127.0.0.1:8000/items/" -H "Content-Type: application/json" -d '{"name": "Test Item"}'
```

---

## 📌 Contributing
Pull requests are welcome! If you find any issues or want to improve something, feel free to contribute.

---

## 📌 License
This project is open-source and available under the **MIT License**.