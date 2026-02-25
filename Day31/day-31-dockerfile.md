# Day 31 – Dockerfile: Build Your Own Images

### Task 1: Your First Dockerfile
1. Create a folder called `my-first-image`
2. Inside it, create a `Dockerfile` that:
   - Uses `ubuntu` as the base image
   - Installs `curl`
   - Sets a default command to print `"Hello from my custom image!"`
3. Build the image and tag it `my-ubuntu:v1`
4. Run a container from your image

     
**Verify:** The message prints on `docker run`

---
### Task 2: Dockerfile Instructions
Create a new Dockerfile that uses **all** of these instructions:
- `FROM` — base image
- `RUN` — execute commands during build
- `COPY` — copy files from host to image
- `WORKDIR` — set working directory
- `EXPOSE` — document the port
- `CMD` — default command

<img width="1331" height="705" alt="image" src="https://github.com/user-attachments/assets/9cab8713-d24b-4651-99db-9f718c0d03c4" />











### Task 3: CMD vs ENTRYPOINT
1. Create an image with `CMD ["echo", "hello"]` — run it, then run it with a custom command. What happens?
2. Create an image with `ENTRYPOINT ["echo"]` — run it, then run it with additional arguments. What happens?
3. Write in your notes: When would you use CMD vs ENTRYPOINT?

   <img width="1018" height="83" alt="image" src="https://github.com/user-attachments/assets/712c3514-60a2-4806-826f-faad6caf0500" />

   <img width="1084" height="485" alt="image" src="https://github.com/user-attachments/assets/bb1d0a96-41ad-438c-9dc2-7a761d84a8be" />
  
---


### Task 4: Build a Simple Web App Image
1. Create a small static HTML file (`index.html`) with any content
2. Write a Dockerfile that:
   - Uses `nginx:alpine` as base
   - Copies your `index.html` to the Nginx web directory
3. Build and tag it `my-website:v1`
4. Run it with port mapping and access it in your browser

   <img width="1365" height="706" alt="image" src="https://github.com/user-attachments/assets/3426c223-ee0e-443d-a2c0-7efa3e5dc648" />
 
---

### Task 5: .dockerignore
1. Create a `.dockerignore` file in one of your project folders
2. Add entries for: `node_modules`, `.git`, `*.md`, `.env`
3. Build the image — verify that ignored files are not included

  <img width="982" height="504" alt="image" src="https://github.com/user-attachments/assets/3b3e63d0-1df4-4fc2-81d1-4e13bb95d33a" />

---

