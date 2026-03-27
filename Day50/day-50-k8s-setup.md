# Day 50 – Kubernetes Architecture and Cluster Setup

### Task 1: Recall the Kubernetes Story
Before touching a terminal, write down from memory:

1. Why was Kubernetes created? What problem does it solve that Docker alone cannot?
   - kubernetes was created to manage the problem of container crashing and auto-heal problem
   - google internal system faced problem of auto-scale & auto-heal when traffic increase or container crashes, docker is not able to solve this issue
   - to solve this issue google created borg, which can auto-heal & auto-scale when needed
     
3. Who created Kubernetes and what was it inspired by?
   - kubernetes is created by google in 2014,
   - This project was inspired by borg,an interal system used by google to manage containers at massiv scale
   - Borg automatically autoheal when get crashed & auto-scale when traffic spike sudden
   - later on, google made this project open source, now it was managed by CNCF(Cloud Native Computing Foundation) which is part of Linux foundation
    
3. What does the name "Kubernetes" mean?
   - The name Kubernetes comes from a Greek word meaning “helmsman” or “ship pilot.” It refers to someone who steers a ship.
   - This name reflects the role of Kubernetes, which guides and manages containers, similar to how a helmsman controls a ship.
   - Kubernetes is often shortened to K8s, where the number 8 represents the eight letters between K and S.


---

### Task 2: Draw the Kubernetes Architecture
From memory, draw or describe the Kubernetes architecture. Your diagram should include:

**Control Plane (Master Node):**
- API Server — the front door to the cluster, every command goes through it
- etcd — the database that stores all cluster state
- Scheduler — decides which node a new pod should run on
- Controller Manager — watches the cluster and makes sure the desired state matches reality

**Worker Node:**
- kubelet — the agent on each node that talks to the API server and manages pods
- kube-proxy — handles networking rules so pods can communicate
- Container Runtime — the engine that actually runs containers (containerd, CRI-O)



  <img width="925" height="431" alt="image" src="https://github.com/user-attachments/assets/142b0dd0-53b8-4cec-87fe-6f55be9173df" />

  <img width="1055" height="583" alt="image" src="https://github.com/user-attachments/assets/ff5290ae-6d82-44c2-9eb0-fc534666af6f" />



After drawing, verify your understanding:
- What happens when you run `kubectl apply -f pod.yaml`? Trace the request through each component.
  - kubectl read the pod.yml
  - Request is send to kubernets API server
  - API server, perform authentication & autherization
  - if valid, the pod object is stored in etcd(database in k8s)
  - kubernetes Schedular, detects unscheduled pods and assign them node
  - he kubelet on that node sees the Pod and instructs the container runtime (e.g., containerd) to start the container.
  - The container starts and the Pod status is updated to Running in the API Server.
    
- What happens if the API server goes down?
  - you can not run kubectl commands and make changes to cluster
  - All running pods or services are kept running
  - No new deployment & Scheduling works
    
- What happens if a worker node goes down?
  - Pods on that node stop running. Kubernetes marks the node as NotReady and after a timeout, it evicts the pods and reschedules them on healthy nodes.

---

### Task 3: Install kubectl
`kubectl` is the CLI tool you will use to talk to your Kubernetes cluster.

Install it:
```bash
# macOS
brew install kubectl

# Linux (amd64)
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/

# Windows (with chocolatey)
choco install kubernetes-cli
```

Verify:
```bash
kubectl version --client
```

   <img width="658" height="63" alt="image" src="https://github.com/user-attachments/assets/53e94c84-5bfb-479a-a907-3320806418ee" />

---


### Task 4: Set Up Your Local Cluster
Choose **one** of the following. Both give you a fully functional Kubernetes cluster on your machine.

**Option A: kind (Kubernetes in Docker)**
```bash
# Install kind
# macOS
brew install kind

# Linux
curl -Lo ./kind https://kind.sigs.k8s.io/dl/latest/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind

# Create a cluster
kind create cluster --name aditya-cluster

# Verify
kubectl cluster-info
kubectl get nodes
```

   <img width="982" height="175" alt="image" src="https://github.com/user-attachments/assets/62336edb-6be5-4986-a850-7f633ef308ff" />

Write down: Which one did you choose and why?
 - I choose kind(kubernets in Docker) because it is lightweight and easy to local testing
 - It runs a Kubernetes cluster inside Docker containers,so I can quickly create and delete clusters without needing VMs or a cloud environment.
 - This makes it ideal for development, CI testing, and experimenting with Kubernetes features.

---

### Task 5: Explore Your Cluster
Now that your cluster is running, explore it:

```bash
# See cluster info
kubectl cluster-info

# List all nodes
kubectl get nodes

# Get detailed info about your node
kubectl describe node <node-name>

# List all namespaces
kubectl get namespaces

# See ALL pods running in the cluster (across all namespaces)
kubectl get pods -A
```

Look at the pods running in the `kube-system` namespace:
```bash
kubectl get pods -n kube-system
```

You should see pods like `etcd`, `kube-apiserver`, `kube-scheduler`, `kube-controller-manager`, `coredns`, and `kube-proxy`. These are the architecture components you drew in Task 2 — running as pods inside the cluster.

**Verify:** Can you match each running pod in `kube-system` to a component in your architecture diagram?

---

