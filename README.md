# K8s-Task

---

# ✅ TASK 5: Build a Kubernetes Cluster Locally with Minikube



-*****Document commond taken from the offical documentation of tools******



## 🎯 **Objective**
To **deploy and manage applications** in Kubernetes by:
- Setting up a **local Kubernetes cluster** using **Minikube**
- Using **kubectl** to interact with the cluster
- Deploying an application using **YAML configuration files**
- Managing the application using Kubernetes services
- Taking screenshots of pods and services

---

## 🛠️ **Tools You'll Need**

1. **Minikube** – Creates a local Kubernetes cluster.
2. **kubectl** – CLI tool to interact with Kubernetes.
3. **Docker** – Used to run containers inside Minikube.

---Exactly right! Here's a brief clarification and how they all fit together in your local Kubernetes workflow:

---

## 🔧 **Tool Roles Overview
## 🛠️ TOOLS DEFINITION

### 1. **Minikube**
**Definition:**  
Minikube is a tool that lets you run a **Kubernetes cluster on your local machine**.

**What it does:**  
- Simulates a real Kubernetes cluster.
- Useful for learning and testing Kubernetes locally.
- Supports features like `kubectl`, services, pods, volumes, etc.

**Example Use:**  
```bash
minikube start
```

---

### 2. **kubectl**
**Definition:**  
kubectl (Kube Control) is the **command-line tool** used to interact with a Kubernetes cluster.

**What it does:**  
- Creates, updates, deletes, and manages Kubernetes resources like pods, deployments, and services.
- Lets you view logs, check pod status, and more.

**Example Use:**  
```bash
kubectl get pods
```

---

### 3. **Docker**
**Definition:**  
Docker is a platform used to build, ship, and run **containerized applications**.

**What it does:**  
- Packages applications into lightweight containers.
- Kubernetes uses Docker containers to run apps inside pods.
- Required by Minikube to start a cluster.

**Example Use:**  
```bash
docker build -t myapp .
```

--

  
``****Document commond taken from the offical documentation of tools****--




## 🧱 PART 1: Install Required Tools

### 1. **Install Docker**

Docker runs containers, which Kubernetes uses to run applications.

Check if installed:
```bash
docker --version
```

If not installed, download from:  
🔗 https://docs.docker.com/get-docker/

---

### 2. **Install kubectl**

kubectl lets you control your Kubernetes cluster.

Check if installed:
```bash
kubectl version --client
```

If not installed, download from:  
🔗 https://kubernetes.io/docs/tasks/tools/

---

### 3. **Install Minikube**

Minikube creates a virtual Kubernetes cluster on your local machine.

Check version:
```bash
minikube version
```

If not installed, download from:  
🔗 https://minikube.sigs.k8s.io/docs/start/

---

## 🚀 PART 2: Start Kubernetes Cluster with Minikube

Start the cluster using:
```bash
minikube start
```

⏱️ This may take a few minutes. It will create a Kubernetes cluster inside a VM (or Docker container) on your machine.

✅ After it's ready, check cluster status:
```bash
minikube status
```

---

## 📄 PART 3: Create Deployment YAML File

This YAML file tells Kubernetes to run a specific application (a containerized web app).

### Create file: `deployment.yaml`
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: hello-world-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: hello-world
  template:
    metadata:
      labels:
        app: hello-world
    spec:
      containers:
      - name: hello-world
        image: paulbouwer/hello-kubernetes:1.7
        ports:
        - containerPort: 8080
```

### Explanation:
| Line | Description |
|------|-------------|
| `apiVersion`, `kind` | Tells Kubernetes this is a Deployment |
| `replicas: 2` | Run 2 copies (pods) of the app |
| `image` | Docker image to run (web app) |
| `containerPort: 8080` | Port the app runs on inside the container |

### Apply it:
```bash
kubectl apply -f deployment.yaml
```

✅ Check if pods are running:
```bash
kubectl get pods
```

---

## 🌐 PART 4: Create a Service YAML File

A Service exposes your app so you can access it in a browser.

### Create file: `service.yaml`
```yaml
apiVersion: v1
kind: Service
metadata:
  name: hello-world-service
spec:
  type: NodePort
  selector:
    app: hello-world
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080
```

### Explanation:
| Line | Description |
|------|-------------|
| `kind: Service` | Defines a Service |
| `type: NodePort` | Makes app accessible from outside |
| `port: 80` | Port exposed to outside |
| `targetPort: 8080` | Port app runs on inside container |

### Apply it:
```bash
kubectl apply -f service.yaml
```

✅ Check services:
```bash
kubectl get services
```

---

## 🌐 PART 5: Access the Application in Browser

Minikube can open the app for you:
```bash
minikube service hello-world-service
```

This command opens the app in your **default browser**. It may look like:
```
http://127.0.0.1:32768
```

You’ll see the **"Hello Kubernetes!"** message from the app.

---

## 📸 PART 6: Take Screenshots for Deliverables

### Screenshot 1: Pods
```bash
kubectl get pods
```
Take a screenshot of the output showing the running pods.

### Screenshot 2: Services
```bash
kubectl get services
```
Take a screenshot of the output showing the running service.

---

## 📁 PART 7: Deliverables Summary

| File | Description |
|------|-------------|
| `deployment.yaml` | Contains app deployment configuration |
| `service.yaml` | Contains service configuration to expose the app |
| `pods_screenshot.png` | Screenshot of `kubectl get pods` output |
| `services_screenshot.png` | Screenshot of `kubectl get services` output |




---
![Screenshot (29)](https://github.com/user-attachments/assets/495f92a9-dd53-45dc-bd82-91025ba9eeed)





[Screenshot (38)](https://github.com/user-attachments/assets/8892c83c-a16e-40d1-a073-979704253e4b)





![Screenshot (30)](https://github.com/user-attachments/assets/e9b168cd-8a21-4e3a-8c79-d38410e74844)


 


![Screenshot (31)](https://github.com/user-attachments/assets/54d0f60e-6b5c-48c0-be8e-9dbf1c5154e0)




![Screenshot (33)](https://github.com/user-attachments/assets/dab2b9be-febe-4798-bcd9-2c08160dc8fe)




![Screenshot (34)](https://github.com/user-attachments/assets/a878f7e1-b0f9-4035-9092-7d6c5bd08e5d)




![Screenshot (35)](https://github.com/user-attachments/assets/f8bb6838-b880-4033-aaf8-be71a2d00961) 




![Screenshot (36)](https://github.com/user-attachments/assets/b4e84e35-dbf7-47b8-82fb-b254545b5eb8)




![Screenshot (37)](https://github.com/user-attachments/assets/2663ba61-8e4e-408d-8a48-f30b40756363)






