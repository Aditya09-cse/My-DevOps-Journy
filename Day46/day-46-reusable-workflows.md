# Day 46 – Reusable Workflows & Composite Actions


### Task 1: Understand `workflow_call`
Before writing any code, research and answer in your notes:
1. What is a **reusable workflow**?
   - Reusable workflows are predefined workflows stored in a single location and invoked by other workflows across repositories.
   - This approach centralizes logic, reduces duplication, and ensures consistent implementation of processes like testing, deployment, and linting.
2. What is the `workflow_call` trigger?
   - workflow_call is a special trigger in GitHub Actions that makes a workflow reusable.
   - This workflow will not run by itself (like on push/pull).
   - It will run only when another workflow calls it using uses:.
     ```
     on:
       workflow_call:
     ```

     ```
     jobs:
      call-workflow:
        uses: username/repo/.github/workflows/reusable.yml@main
     ```
3. How is calling a reusable workflow different from using a regular action (`uses:`)?
   - regular action - A single action (like a plugin/tool), Runs inside a job as one step
     ```
     - name: Checkout code
      uses: actions/checkout@v4
     ```
    - Calling a Reusable Workflow - A full workflow, Contains multiple jobs + steps, Called at the job level, not step level
    ```
    jobs:
      deploy:
        uses: username/repo/.github/workflows/deploy.yml@main
    ```
   
4. Where must a reusable workflow file live?
   - A resuable workflow file must be inside ` .github/workflows ` folder
   ```
   .github/workflows/reusable.yml
   ```
---

### Task 2: Create Your First Reusable Workflow
Create `.github/workflows/reusable-build.yml`:
1. Set the trigger to `workflow_call`
2. Add an `inputs:` section with:
   - `app_name` (string, required)
   - `environment` (string, required, default: `staging`)
3. Add a `secrets:` section with:
   - `docker_token` (required)
4. Create a job that:
   - Checks out the code
   - Prints `Building <app_name> for <environment>`
   - Prints `Docker token is set: true` (never print the actual secret)

**Verify:** This file alone won't run — it needs a caller. That's next.

   <img width="1344" height="581" alt="image" src="https://github.com/user-attachments/assets/4144f467-b7b8-4b43-8bf9-02c7d2e257a0" />


---

### Task 3: Create a Caller Workflow
Create `.github/workflows/call-build.yml`:
1. Trigger on push to `main`
2. Add a job that uses your reusable workflow:
   ```yaml
   jobs:
     build:
       uses: ./.github/workflows/reusable-build.yml
       with:
         app_name: "my-web-app"
         environment: "production"
       secrets:
         docker_token: ${{ secrets.DOCKER_TOKEN }}
   ```
3. Push to `main` and watch it run

**Verify:** In the Actions tab, do you see the caller triggering the reusable workflow? Click into the job — can you see the inputs printed?


<img width="1052" height="387" alt="image" src="https://github.com/user-attachments/assets/a415364d-ba04-4f82-a8c4-cb55f8f8d9d5" />


<img width="1338" height="575" alt="image" src="https://github.com/user-attachments/assets/ce6b721b-d7f6-4cd3-a3f4-09ecb4d87b0d" />


---

### Task 4: Add Outputs to the Reusable Workflow
Extend `reusable-build.yml`:
1. Add an `outputs:` section that exposes a `build_version` value
2. Inside the job, generate a version string (e.g., `v1.0-<short-sha>`) and set it as output
3. In your caller workflow, add a second job that:
   - Depends on the build job (`needs:`)
   - Reads and prints the `build_version` output

**Verify:** Does the second job print the version from the reusable workflow?
*yes* - it print the version

<img width="1322" height="467" alt="image" src="https://github.com/user-attachments/assets/6eba81d1-a3a0-424a-933e-bd519fd88c5e" />


<img width="1312" height="483" alt="image" src="https://github.com/user-attachments/assets/51001727-da55-4530-8be4-d12c2da7e661" />


---

### Task 5: Create a Composite Action
Create a **custom composite action** in your repo at `.github/actions/setup-and-greet/action.yml`:
1. Define inputs: `name` and `language` (default: `en`)
2. Add steps that:
   - Print a greeting in the specified language
   - Print the current date and runner OS
   - Set an output called `greeted` with value `true`
3. Use the composite action in a new workflow with `uses: ./.github/actions/setup-and-greet`

**Verify:** Does your custom action run and print the greeting?

---
