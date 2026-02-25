# Day 30 – Docker Images & Container Lifecycle

### Task 1: Docker Images
1. Pull the `nginx`, `ubuntu`, and `alpine` images from Docker Hub

    <img width="769" height="523" alt="image" src="https://github.com/user-attachments/assets/6ad7820f-6279-4bac-9c5a-db187b2ab518" />
  
2. List all images on your machine — note the sizes
   
   <img width="605" height="101" alt="image" src="https://github.com/user-attachments/assets/fb2ae19e-7991-492c-9263-f0c4b7bb7621" />
   

    | Image         | Size | 
    | ------------- | ---------- | 
    | alpine:latest | 8.44MB     | 
    | nginx:latest  | 161MB      | 
    | ubuntu:latest | 78.1MB      |

3. Compare `ubuntu` vs `alpine` — why is one much smaller?
  -  `Ubuntu` is full feature Linux Distribution -> so it's size was large than `alpine`
  -  `alpine` is minimal distibution optimized for containers -> so its lize was small than `ubuntu`


     | Aspect | Ubuntu         | alpine | 
      | ------------- | ---------- | ------- |
      | size | 78.1 MB     | 8.44 Mb |

4. Inspect an image — `NGINX`

   <img width="1111" height="630" alt="image" src="https://github.com/user-attachments/assets/1e23c179-4387-4ab6-b943-68b6cb1459d2" />

4.1 what information can you see?

  | Image (nginx) | Repo tags     | Entrypoint                | Exposed Port | Architecture | OS    |
|---------------|---------------|---------------------------|--------------|--------------|-------|
| nginx         | nginx:latest  | "/docker-entrypoint.sh"   | 80           | amd64        | linux |

 
5. Remove an image you no longer need
   
   <img width="808" height="282" alt="image" src="https://github.com/user-attachments/assets/f90985ea-8ff7-48a1-b6ae-8a8eb06b4004" />

 ---

### Task 2: Image Layers
1. Run `docker image history nginx`

    <img width="1018" height="387" alt="image" src="https://github.com/user-attachments/assets/3240df51-4f6d-4b40-8b25-e2c77711b7b2" />

1.1 what do you see?
  - A list of instuction/layers executed to create nginx image [like CMD,ENTRYPOINT,EXPOSE PORT, COPY, ENV, RUN, LABEL]

2. Each line is a **layer**. Note how some layers show sizes and some show 0B
   - Layers with a size (MB or kB) were created by instructions that modify the filesystem,such as RUN, COPY, or ADD.
   - Layers showing 0B were created by instructions that only change metadata, such as ENV, CMD, EXPOSE, LABEL, or ENTRYPOINT.These do not change the filesystem.

3. Write in your notes: What are layers and why does Docker use them?
   - Docker layers are read-only filesystem snapshots created by each instruction in a Dockerfile.
   - Docker uses layers because:
    - They allow build caching (faster builds)
    - They allow images to share common layers (saves storage).
    - They make image downloads faster (only new layers are pulled)

---


### Task 3: Container Lifecycle
Practice the full lifecycle on one container:
1. **Create** a container (without starting it)
2. **Start** the container
3. **Pause** it and check status
4. **Unpause** it
5. **Stop** it
6. **Restart** it
7. **Kill** it
8. **Remove** it

Check `docker ps -a` after each step — observe the state changes.

  <img width="918" height="581" alt="image" src="https://github.com/user-attachments/assets/690b741f-463c-48a7-bbec-38fc92b42873" />


---

### Task 4: Working with Running Containers
1. Run an Nginx container in detached mode
2. View its **logs**
3. View **real-time logs** (follow mode)

  <img width="901" height="560" alt="image" src="https://github.com/user-attachments/assets/c9ed4b88-7f13-4878-a775-2d50653e2ab0" />

    
4. **Exec** into the container and look around the filesystem

   <img width="1298" height="548" alt="image" src="https://github.com/user-attachments/assets/f479e94b-e308-459b-b5b5-e244350af1bd" />

5. Run a single command inside the container without entering it

   <img width="1297" height="330" alt="image" src="https://github.com/user-attachments/assets/9e3e7606-0d60-406f-9c80-a575bf1c8291" />

6. **Inspect** the container — find its IP address, port mappings, and mounts
   
    <img width="852" height="189" alt="image" src="https://github.com/user-attachments/assets/7009fb71-ae19-4c83-bad3-150268df32e5" />

  - **ip**

     <img width="369" height="77" alt="image" src="https://github.com/user-attachments/assets/c5962e83-5364-4e7c-926d-71cc5858066d" />

  
  - **port-mapping**
    
      <img width="428" height="223" alt="image" src="https://github.com/user-attachments/assets/23c29f5f-72ab-465b-9d94-f566497c815d" />

  - **mount**
    
      <img width="317" height="219" alt="image" src="https://github.com/user-attachments/assets/5bab163f-41b8-4327-8445-1fc379de5857" />


---

---

### Task 5: Cleanup
1. Stop all running containers in one command
2. Remove all stopped containers in one command
3. Remove unused images
4. Check how much disk space Docker is using -> 0B

    <img width="899" height="601" alt="image" src="https://github.com/user-attachments/assets/237ee869-577f-4f0d-b332-67d74a5c3446" />


    


   
