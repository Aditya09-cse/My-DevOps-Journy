# Day 32 – Docker Volumes & Networking



### Task 1: The Problem
1. Run a Postgres or MySQL container
  <img width="1053" height="231" alt="image" src="https://github.com/user-attachments/assets/78d555a9-4efc-41ff-8015-dd69a81baac2" />
    
2. Create some data inside it (a table, a few rows — anything)
     <img width="572" height="639" alt="image" src="https://github.com/user-attachments/assets/d9ad6dbb-c137-4357-9a43-2606d4027380" />
     
3. Stop and remove the container
   <img width="1088" height="259" alt="image" src="https://github.com/user-attachments/assets/ffc1fc27-dfe7-4145-958f-ff3ccbebc89b" />
   
4. Run a new one — is your data still there?
   <img width="952" height="355" alt="image" src="https://github.com/user-attachments/assets/39baaaa8-cf37-4cbf-b5b0-e464273d991a" />

   <img width="353" height="210" alt="image" src="https://github.com/user-attachments/assets/a149922c-7738-444d-8339-8cd24d473edf" />

   - Previous data was deleted because we stop & delete the container and don't attch any volume with database
   - Container are empheral dont persist any data by default
  
   ---
   
### Task 2: Named Volumes
1. Create a named volume
   <img width="1061" height="140" alt="image" src="https://github.com/user-attachments/assets/6e68ec6b-bb4d-40bb-b750-518e80075b20" />

2. Run the same database container, but this time **attach the volume** to it
   <img width="1147" height="48" alt="image" src="https://github.com/user-attachments/assets/544f0711-89e2-4842-880b-0f479bd65a2a" />

3. Add some data, stop and remove the container

   <img width="554" height="104" alt="image" src="https://github.com/user-attachments/assets/ecda75b3-8bad-480f-b055-ee83b6f7dc4b" />

   <img width="579" height="578" alt="image" src="https://github.com/user-attachments/assets/c116f0e7-f75b-40f2-a58e-263b8b69f039" />


4. Run a brand new container with the **same volume**

   <img width="1113" height="407" alt="image" src="https://github.com/user-attachments/assets/0561d740-4325-44e4-9c05-ef1d315816b0" />

   <img width="635" height="550" alt="image" src="https://github.com/user-attachments/assets/d894a910-3353-4627-a9cd-a48e52186011" />


5. Is the data still there?
   - **yes** , Data is their  because we attach the volume with container

 **Verify:** `docker volume ls`, `docker volume inspect`
     <img width="697" height="333" alt="image" src="https://github.com/user-attachments/assets/73da45d7-460b-4d56-8d2a-8f47dd3e973a" />

---

### Task 3: Bind Mounts
1. Create a folder on your host machine with an `index.html` file

   <img width="577" height="83" alt="image" src="https://github.com/user-attachments/assets/8f56c230-9a82-422d-87ef-0ef5f9250f88" />

2. Run an Nginx container and **bind mount** your folder to the Nginx web directory

   <img width="1365" height="406" alt="image" src="https://github.com/user-attachments/assets/d6ef7c50-a80c-485f-bff4-5e6da66c0830" />

   
3. Access the page in your browser

   <img width="693" height="344" alt="image" src="https://github.com/user-attachments/assets/c8790224-f156-4f5a-ad3a-fa40e2fa9561" />


4. Edit the `index.html` on your host — refresh the browser

    <img width="580" height="76" alt="image" src="https://github.com/user-attachments/assets/03b93bd0-8804-443f-b34f-df0a5fd4374f" />

   <img width="695" height="287" alt="image" src="https://github.com/user-attachments/assets/3ef7c9d8-6208-48c9-904e-b978b6edac1d" />


Write in your notes: What is the difference between a named volume and a bind mount?

**Volumes vs Bind Mounts**
    
**Volumes:**
- Managed by Docker.
- Stored in a part of the host filesystem which is managed by Docker.
- Preferred method for data persistence.

**Bind Mounts:**
- Maps a file or directory on the host to a file or directory in the container.
- More complex but provides flexibility to interact with the host system.

---

### Task 4: Docker Networking Basics
1. List all Docker networks on your machine

   <img width="605" height="112" alt="image" src="https://github.com/user-attachments/assets/941ecd15-c1bb-4a0b-837f-7a10bf099078" />
2. Inspect the default `bridge` network'

    <img width="889" height="672" alt="image" src="https://github.com/user-attachments/assets/fda4430a-42dc-4524-b92e-f127fd52edf0" />

   - `docker network inspect` is the command used to retrieve detailed configuration and status information about a specific Docker network.
   - The `bridge network` is indeed the default network in Docker.
     
3. Run two containers on the default bridge — can they ping each other by **name**?
   
  - **No** -> they not ping each other name

    <img width="898" height="180" alt="image" src="https://github.com/user-attachments/assets/e53d2f91-b4af-431a-a049-fe7deb463734" />

   
4. Run two containers on the default bridge — can they ping each other by **IP**?

  - **yes** -> they ping each other by ip

     <img width="866" height="316" alt="image" src="https://github.com/user-attachments/assets/700e9cca-7d1b-4959-9e4c-f0b31d495da1" />

     <img width="904" height="304" alt="image" src="https://github.com/user-attachments/assets/ca39328c-319c-4ed7-9647-6ede53d3127e" />


---

### Task 5: Custom Networks
1. Create a custom bridge network called `my-app-net`

   <img width="735" height="154" alt="image" src="https://github.com/user-attachments/assets/534f259f-bca8-4d77-9838-547262b70110" />

2. Run two containers on `my-app-net`

   <img width="1012" height="78" alt="image" src="https://github.com/user-attachments/assets/67fce6ee-0180-4e23-b5fe-e1e2687cd78b" />

3. Can they ping each other by **name** now?

   - **yes** -> they can ping each other by name

     <img width="1090" height="529" alt="image" src="https://github.com/user-attachments/assets/41e5e559-dd45-436b-83a4-2d1c0976229f" />

4. Write in your notes: Why does custom networking allow name-based communication but the default bridge doesn't?

   - Default Docker `bridge network` `does not have built-in DNS`,so containers cannot resolve each other by name.they need IPs.
   - `User-defined networks` have `embedded DNS`, so containers can communicate using their names.
     
---

### Task 6: Put It Together
1. Create a custom network -> `name -> two-tier`
   <img width="718" height="229" alt="image" src="https://github.com/user-attachments/assets/aa514b1d-d2b4-49a8-b675-e72636b45d46" />

3. Run a **database container** (MySQL/Postgres) on that network with a volume for data

   <img width="1344" height="123" alt="image" src="https://github.com/user-attachments/assets/dea58076-b201-4bba-9c7b-b36c3f8edb90" />

5. Run an **app container** (use any image) on the same network
6. Verify the app container can reach the database by container name

  <img width="850" height="229" alt="image" src="https://github.com/user-attachments/assets/7a18106c-e9db-457b-9ed8-3b864d769f3a" />

---

---











