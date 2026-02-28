# Day 33 – Docker Compose: Multi-Container Basics

### Task 1: Install & Verify
1. Check if Docker Compose is available on your machine
2. Verify the version

   <img width="492" height="45" alt="image" src="https://github.com/user-attachments/assets/c34fea7f-3ff4-46ea-b3c8-bae1fa05b8d3" />


### Task 2: Your First Compose File
1. Create a folder `compose-basics`
2. Write a `docker-compose.yml` that runs a single **Nginx** container with port mapping
3. Start it with `docker compose up`

   <img width="1023" height="581" alt="image" src="https://github.com/user-attachments/assets/dbfa0353-84d9-4031-a170-90c0db120883" />

4. Access it in your browser
    <img width="1026" height="410" alt="image" src="https://github.com/user-attachments/assets/7fa5c19c-d726-4870-b197-5e96a3765dad" />

5. Stop it with `docker compose down

    <img width="1205" height="654" alt="image" src="https://github.com/user-attachments/assets/75d9b885-0d6b-48bd-a474-8ccd1001068d" />


### Task 3: Two-Container Setup
Write a `docker-compose.yml` that runs:
- A **WordPress** container
- A **MySQL** container

They should:
- Be on the same network (Compose does this automatically)
- MySQL should have a named volume for data persistence
- WordPress should connect to MySQL using the service name

Start it, access WordPress in your browser, and set it up.

<img width="1201" height="717" alt="image" src="https://github.com/user-attachments/assets/5a7fd442-f32d-46b0-9c5b-221078b213e9" />

<img width="1156" height="687" alt="image" src="https://github.com/user-attachments/assets/73f44a5f-c07b-4783-afa7-47da90289b3c" />

<img width="1071" height="599" alt="image" src="https://github.com/user-attachments/assets/5e9875fb-570b-4c63-9e3f-d2208f1269dc" />

<img width="1315" height="648" alt="image" src="https://github.com/user-attachments/assets/75b6c28f-72e6-46a2-82a1-a47b2bbc0fbf" />


   
**Verify:** Stop and restart with `docker compose down` and `docker compose up` — is your WordPress data still there?
    - **`yes`** -> Wordpress is data is their

  <img width="543" height="185" alt="image" src="https://github.com/user-attachments/assets/1861fb56-f06f-4980-9fab-1dea829ed3f0" />
  <img width="1316" height="617" alt="image" src="https://github.com/user-attachments/assets/f3f32e0d-461a-4e3c-ade8-2df51e3f71fc" />



---

### Task 4: Compose Commands

1. Start services in **detached mode**
   <img width="532" height="74" alt="image" src="https://github.com/user-attachments/assets/9190be7b-0724-4754-843d-23c3fdc9a7d5" />

2. View running services

   <img width="1353" height="121" alt="image" src="https://github.com/user-attachments/assets/c0439dad-4407-4ced-92d3-64a52c0ef9b0" />

3. View **logs** of all services

   <img width="1365" height="410" alt="image" src="https://github.com/user-attachments/assets/47c732e5-8597-4bf8-b699-5a717a575d98" />

4. View logs of a **specific** service

   <img width="1365" height="216" alt="image" src="https://github.com/user-attachments/assets/17a73aca-0611-475e-ae51-15b977338946" />

5. **Stop** services without removing

    <img width="610" height="81" alt="image" src="https://github.com/user-attachments/assets/f11d46dd-c973-4201-8488-c53f7308c99f" />

6. **Remove** everything (containers, networks)

    <img width="540" height="95" alt="image" src="https://github.com/user-attachments/assets/52c91d15-1142-4dc9-83bf-9cd83167d94d" />

7. **Rebuild** images if you make a change

---

### Task 5: Environment Variables
1. Add environment variables directly in your `docker-compose.yml`
3. Create a `.env` file and reference variables from it in your compose file
4. Verify the variables are being picked up

   <img width="455" height="229" alt="image" src="https://github.com/user-attachments/assets/019ec8cf-c5df-40d4-b654-35d9b3b2a26e" />

   <img width="819" height="149" alt="image" src="https://github.com/user-attachments/assets/c436e72f-34f8-441e-b024-e56d6fdb03f8" />

   <img width="896" height="104" alt="image" src="https://github.com/user-attachments/assets/44b555cc-4fb5-4802-ba92-77db30cb1cb7" />



