# Day 34 – Docker Compose: Real-World Multi-Container Apps

---
### Task 1: Build Your Own App Stack
Create a `docker-compose.yml` for a 3-service stack:
- A **web app** (use Python Flask, Node.js, or any language you know)
- A **database** (Postgres or MySQL)
- A **cache** (Redis)

Write a simple Dockerfile for the web app. The app doesn't need to be complex — even a "Hello World" that connects to the database is enough.


  <img width="793" height="146" alt="image" src="https://github.com/user-attachments/assets/caa7cbd5-cfc9-4f54-bd4f-76ccaae4be02" />

---

### Task 2: depends_on & Healthchecks
1. Add `depends_on` to your compose file so the app starts **after** the database
2. Add a **healthcheck** on the database service
3. Use `depends_on` with `condition: service_healthy` so the app waits for the database to be truly ready, not just started

     
**Test:** Bring everything down and up — does the app wait for the DB?
 - **yes** the app container waiting for database container to be healthy
   
  <img width="1356" height="187" alt="image" src="https://github.com/user-attachments/assets/b98f4902-d15b-4d3e-b2b1-f9f41ea450b6" />


  <img width="1365" height="164" alt="image" src="https://github.com/user-attachments/assets/d376a4f0-07f5-40eb-9ba2-fcd869886831" />


---

### Task 3: Restart Policies
1. Add `restart: always` to your database service
2. Manually kill the database container — does it come back?

  - **yes it back**

      <img width="1365" height="576" alt="image" src="https://github.com/user-attachments/assets/589d1f9a-defa-44f7-8fc3-d305162b3315" />
3. Try `restart: on-failure` — how is it different?

    <img width="1365" height="390" alt="image" src="https://github.com/user-attachments/assets/d2e97b80-d1ee-442f-9bd5-87ad875fd6fc" />

4. Write in your notes: When would you use each restart policy?\
     - `restart:always` `Use When:`
            Databases,
            Backend APIs,
            Production services,
            Anything that must always run

    - `restart:on-failure` `Use When`:
            Data processing jobs
            One-time migration scripts

---

### Task 4: Custom Dockerfiles in Compose
1. Instead of using a pre-built image for your app, use `build:` in your compose file to build from a Dockerfile

   <img width="1281" height="680" alt="image" src="https://github.com/user-attachments/assets/8e004bd2-5ddd-4918-a039-abaf4d6d70fc" />

2. Make a code change in your app
3. Rebuild and restart with one command

     <img width="1244" height="709" alt="image" src="https://github.com/user-attachments/assets/6cea0d25-2728-4c89-ad1e-e185a59b85b1" />
---

### Task 5: Named Networks & Volumes
1. Define **explicit networks** in your compose file instead of relying on the default
2. Define **named volumes** for database data
3. Add **labels** to your services for better organization

---

### Task 6: Scaling (Bonus)
1. Try scaling your web app to 3 replicas using `docker compose up --scale`
2. What happens? What breaks?
3. Write in your notes: Why doesn't simple scaling work with port mapping?

  <img width="1359" height="240" alt="image" src="https://github.com/user-attachments/assets/2411b2f8-38f0-4d6a-9477-cb196f4baac1" />


  <img width="1365" height="194" alt="image" src="https://github.com/user-attachments/assets/237f8c24-be85-4d8f-9f44-1f632f1b1bff" />

  - First container started

  - It binds host port 8080 = container port 8080.

  - Second and third containers failed

  - Status Created means Docker couldn’t start them,port 8080 is already in use on the host.

  - Docker can’t bind multiple containers to the same host port.

---



