# Microservices Kubernetes Deployment

## 📌 Objective
Deploy a microservices-based application on Kubernetes using Minikube, implementing proper service communication and ingress configuration.

---

## 🏗️ Project Structure
```
submission/
├── deployments/
│   ├── user-service.yaml
│   ├── product-service.yaml
│   ├── order-service.yaml
│   └── gateway-service.yaml
├── services/
│   ├── user-service.yaml
│   ├── product-service.yaml
│   ├── order-service.yaml
│   └── gateway-service.yaml
├── ingress/
│   └── ingress.yaml
├── screenshots/
│   ├── pods-running.png
│   ├── ingress-working.png
│   ├── service-communication.png
└── README.md
```

---

## 🚀 Step 1: Minikube Setup
1. Install Minikube:
   ```bash
   minikube start --driver=docker
   ```
2. Enable the Ingress Controller:
   ```bash
   minikube addons enable ingress
   ```
3. Verify that Minikube is running:
   ```bash
   kubectl get nodes
   ```

---

## 📦 Step 2: Deploy Microservices
1. Apply Kubernetes Deployment manifests:
   ```bash
   kubectl apply -f deployments/
   ```
2. Verify the pod status:
   ```bash
   kubectl get pods
   ```

---

## 🌐 Step 3: Configure Services
1. Apply Kubernetes Service manifests:
   ```bash
   kubectl apply -f services/
   ```
2. Verify the service status:
   ```bash
   kubectl get services
   ```

---

## 🚦 Step 4: Configure Ingress
1. Apply the Ingress manifest:
   ```bash
   kubectl apply -f ingress/ingress.yaml
   ```
2. Verify the Ingress configuration:
   ```bash
   kubectl get ingress
   ```
3. Add Minikube’s IP to `/etc/hosts`:
   ```bash
   echo "$(minikube ip) microservices.local" | sudo tee -a /etc/hosts
   ```

---

## 🔍 Step 5: Testing
1. Test individual services using `curl`:
   ```bash
   curl http://microservices.local/api/users
   curl http://microservices.local/api/products
   curl http://microservices.local/api/orders
   curl http://microservices.local/
   ```
2. Verify inter-service communication:
   ```bash
   kubectl exec -it $(kubectl get pods -l app=user-service -o jsonpath="{.items[0].metadata.name}") -- sh
   curl http://product-service.default.svc.cluster.local
   exit
   ```

---

## 📌 Conclusion
This project demonstrates a complete microservices deployment on Kubernetes using Minikube, implementing service communication and ingress routing. 🎉

