# Day 29 – Introduction to Docker

### Task 1: What is Docker?
  - Docker is a software tool
  - It is used to contarized application
  - objective is to reduce the size of applocation to save time & memory
  - In this we have to create docker images and then run to containerized application
  - We can pull docker images from Docker Hub or Create manually
  - Docker File -> Docker Images -> Docker Container

---

### What is a container 
  - **Container** are light-weight, portable, secure software Packages that bundle an application's code , libraries and dependencies togehter.
    
###  why do we need them?

  1. **Consistency** -> Container solve the problem **it works on my machine**
  2. **Portability** -> Container can move easily between on-premise, cloud and hybrid  environments
  3. **Isolation** -> Each Container run on its own isolatated environment
  4. **Efficiency** -> Container share the host os , so they are faster to start  and required  less resources compared to Virtual Machine

---

### Containers vs Virtual Machines — what's the real difference?

  | Aspect | Containers | Virtual Machines |
|--------|------------|------------------|
| **Architecture** | Share the host OS kernel | Each VM has its own full operating system |
| **Size** | Lightweight (measured in MBs) | Heavy (measured in GBs) |
| **Startup Time** | Starts in seconds | Takes minutes to boot |
| **Performance** | Near-native performance | Slightly slower due to OS overhead |
| **Use Case** | Microservices, DevOps, CI/CD pipelines | Running different OS, legacy systems |
---

### Docker architecture

---

### Docker Client

### What it is
The Docker client is the command-line interface (CLI) used to interact with Docker. It acts as the command center.

### How it works
You type commands in the Docker client, and it sends those requests to the Docker daemon, which performs the actual work.

### Example Commands
- `docker build`
- `docker run`
- `docker pull`
- `docker push`

---

### Docker Daemon

### What it is
The Docker daemon (`dockerd`) is the background service that manages Docker objects such as images, containers, networks, and volumes.

### How it works
The daemon:
- Listens for Docker API requests from the Docker client
- Builds images
- Runs and manages containers
- Handles networking and storage


---

### Docker Hub

### What it is
Docker Hub is a cloud-based public registry for Docker images.

### How it works
It works like an app store for container images. 

You can:
- **Pull** images created by others
- **Push** your own images

### Usage
When you need an image to create a container, you can pull it from Docker Hub.

---

### Docker Registry

### What it is
A Docker registry is a system that stores and distributes Docker images. Docker Hub is the most popular public registry,but you can also create private registries.

### How it works
Registries:
- Store Docker images
- Allow users to pull images
- Allow users to push images

Private registries are commonly used by companies to securely store internal application images.

---


### Task 2: Install Docker
  
1. Install Docker on a cloud instance

   <img width="683" height="29" alt="image" src="https://github.com/user-attachments/assets/dc91ad06-0a6f-4b06-b36e-85115925606c" />

2. Verify the installation
 
     <img width="554" height="46" alt="image" src="https://github.com/user-attachments/assets/23ee790c-3d99-4ade-92b9-a4a99878e741" />

3. Run the `hello-world` container
 
   <img width="693" height="479" alt="image" src="https://github.com/user-attachments/assets/efe3471b-327b-4dca-aaa4-83c77cef1c2a" />
   
4. Read the output carefully — it explains what just happened

   <img width="732" height="168" alt="image" src="https://github.com/user-attachments/assets/3c2e98fb-ee79-4786-83be-5b0536e58a3e" />

---

### Task 3: Run Real Containers
1. Run an **Nginx** container and access it in your browser

   <img width="1346" height="104" alt="image" src="https://github.com/user-attachments/assets/64654993-3bc4-42d7-9df5-096c73787991" />

   <img width="1039" height="294" alt="image" src="https://github.com/user-attachments/assets/1d4ad493-e7b8-43a8-af2a-e8002d175e8e" />


2. Run an **Ubuntu** container in interactive mode — explore it like a mini Linux machine

   <img width="955" height="260" alt="image" src="https://github.com/user-attachments/assets/ddcdd4c9-0c9a-4c33-9ce8-720238742098" />
 
3. List all running containers
    <img width="1281" height="68" alt="image" src="https://github.com/user-attachments/assets/5d9f37ef-ebb0-4353-b741-f2df17b2c723" />

4. List all containers (including stopped ones)

     <img width="1363" height="186" alt="image" src="https://github.com/user-attachments/assets/dccb1ffd-3eff-45d6-bc3b-5d8a4eb8bcc1" />

5. Stop and remove a container

    <img width="666" height="117" alt="image" src="https://github.com/user-attachments/assets/48a75b2b-2edd-43c3-b067-c39a10a3fb22" />

---

### Task 4: Explore
1. Run a container in **detached mode** — what's different?

   <img width="747" height="138" alt="image" src="https://github.com/user-attachments/assets/6e5ea4ca-9cba-4172-bc70-74419a418d4a" />

2. Give a container a custom **name**

    <img width="896" height="294" alt="image" src="https://github.com/user-attachments/assets/33c0fc06-b314-4693-94e6-4e56a20b08ac" />

3. Map a **port** from the container to your host

   <img width="1189" height="116" alt="image" src="https://github.com/user-attachments/assets/bedf2fc9-abdf-4eb4-afa7-af25540e0412" />

4. Check **logs** of a running container
   
   <img width="885" height="346" alt="image" src="https://github.com/user-attachments/assets/2ba9ecee-656d-4b69-84af-fbb46442f43c" />

5. Run a command **inside** a running container

    <img width="1228" height="367" alt="image" src="https://github.com/user-attachments/assets/1d565b84-3f2e-4fbd-b925-6e66d9b51a27" />

---

## Why This Matters for DevOps

- Docker is the foundation of modern deployment. 
- Every CI/CD pipeline, Kubernetes cluster,and microservice - architecture starts with containers. 
- Today you took the first step

