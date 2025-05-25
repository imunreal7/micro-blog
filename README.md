# Micro-Blog Application (MERN Microservices Architecture with Docker, Kubernetes, and Skaffold)

This project is a Micro-Blog application structured with a microservices architecture (Node.js for backend services and a React-based frontend). It uses Docker for containerization, Kubernetes for orchestration, and Skaffold for streamlined local development.

---

## 📁 Project Structure

micro-blog/
├── client/ # React frontend
├── comments/ # Comments service (Node.js + Express)
├── event-bus/ # Event bus service for event-driven communication
├── moderation/ # Moderation service to check inappropriate content
├── posts/ # Posts service (Node.js + Express)
├── query/ # Query service to aggregate data for frontend
├── infra/ # Kubernetes manifests and configuration
│ └── k8s/
├── skaffold.yaml # Skaffold configuration
└── .gitignore # Git ignore rules

---

## 🚀 Getting Started

### Prerequisites

-   [Docker](https://www.docker.com/) (latest version recommended)
-   [Minikube](https://minikube.sigs.k8s.io/docs/start/)
-   [kubectl](https://kubernetes.io/docs/tasks/tools/)
-   [Skaffold](https://skaffold.dev/)

---

### 🐳 Build & Deploy with Skaffold

1. **Start Minikube:**

    ```bash
    minikube start
    ```

2. **Point Docker to Minikube’s Docker daemon:**

    ```bash
    eval $(minikube docker-env)
    ```

3. **Run the entire stack with Skaffold:**

    ```bash
    skaffold dev
    ```

    This will:

    - Build all images (client and backend services) locally.
    - Deploy them to your Minikube Kubernetes cluster.
    - Watch for changes and rebuild/redeploy automatically.

---

### 🌐 Accessing the App

1. **Hosts file entry**: To access your app via the configured Ingress (e.g., `posts.com`):

    ```bash
    echo "$(minikube ip) posts.com" | sudo tee -a /etc/hosts
    ```

2. **Visit the frontend**:

    ```
    http://posts.com
    ```

3. **Example backend API endpoints**:

    ```
    http://posts.com/posts
    http://posts.com/posts/create
    ```

---

### ⚙️ Kubernetes Manifests

All manifests are located in:

infra/k8s/

-   **Deployments** for each service
-   **Services** (`ClusterIP`, `NodePort`)
-   **Ingress** for routing traffic to services

---

### 🔧 Development Tips

-   Use Skaffold’s live-reload feature for faster iterations.
-   For direct access to pods:

    ```bash
    kubectl get pods
    kubectl exec -it <pod-name> -- sh
    ```

-   View logs:

    ```bash
    kubectl logs <pod-name>
    ```

---

### 📦 Building Images Manually (optional)

```bash
# Example for client service
cd client
docker build -t client-srv:latest .
```

Load it into Minikube:

```bash
eval $(minikube docker-env)
docker build -t client-srv:latest .
```

---

## 🧱 Services Overview

**Client**: React frontend for users to create posts and add comments.
**Posts**: Node.js service for creating and managing blog posts.
**Comments**: Node.js service for adding comments to posts.
**Event Bus**: Facilitates event-driven communication between services.
**Moderation**: Filters inappropriate words from comments.
**Query**: Aggregates posts and comments for frontend consumption.

---

## 📝 License

This project is open-source and free to use.

---

## 👥 Contributing

PRs and issues are welcome! Let’s collaborate to make it even better.

---

## ✨ Happy Hacking

