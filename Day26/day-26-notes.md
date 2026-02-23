# Day 26 – GitHub CLI: Manage GitHub from Your Terminal

## Challenge Tasks

### Task 1: Install and Authenticate
1. Install the GitHub CLI on your machine
2. Authenticate with your GitHub account
3. Verify you're logged in and check which account is active
<img width="774" height="166" alt="image" src="https://github.com/user-attachments/assets/b728f3f3-099e-483e-87c0-aa329984a769" />

4. Answer in your notes: What authentication methods does `gh` support?
   - OAuth flow for browser login
   - Personal Acccess Token(PAT)
   - SSH-key Based
### Task 2: Working with Repositories
1. Create a **new GitHub repo** directly from the terminal — make it public with a README
<img width="792" height="249" alt="image" src="https://github.com/user-attachments/assets/621db449-100c-4a97-82d0-170e1c83204d" />

2. Clone a repo using `gh` instead of `git clone`
   <img width="1057" height="137" alt="image" src="https://github.com/user-attachments/assets/7d91457e-c9f9-4c2c-a449-9fe4b65799ee" />
   
3. View details of one of your repos from the terminal
   <img width="784" height="230" alt="image" src="https://github.com/user-attachments/assets/387c7849-bad2-48a3-9582-15b98de38202" />
   
4. List all your repositories
   <img width="1088" height="341" alt="image" src="https://github.com/user-attachments/assets/8bf1b5bd-4b92-4254-ab98-632b4a4bd8a9" />

5. Open a repo in your browser directly from the terminal
  <img width="1059" height="46" alt="image" src="https://github.com/user-attachments/assets/6f6377c7-906e-4c00-bfea-075de34bb174" />
  
  <img width="1329" height="533" alt="image" src="https://github.com/user-attachments/assets/da51c57a-a7f2-41be-b628-8992f86b4f56" />

6. Delete the test repo you created (be careful!)
   <img width="859" height="58" alt="image" src="https://github.com/user-attachments/assets/de85bd4b-13aa-4614-8f02-448836fa06eb" />

### Task 3: Issues
1. Create an issue on one of your repos from the terminal — give it a title, body, and a label
   <img width="936" height="194" alt="image" src="https://github.com/user-attachments/assets/00fedd38-7312-424c-be29-9dbb1d014eab" />

   <img width="1324" height="485" alt="image" src="https://github.com/user-attachments/assets/bed1e0df-0d19-4a70-8155-b89532cc40b1" />


2. List all open issues on that repo
  <img width="1017" height="140" alt="image" src="https://github.com/user-attachments/assets/40e9c996-430e-4f92-af51-5797defcc58d" />


3. View a specific issue by its number
    sorry , unable to do this at this time
 
4. Close an issue from the terminal
   <img width="1018" height="46" alt="image" src="https://github.com/user-attachments/assets/f4192bea-b3fb-4c10-98c4-e3a22a56ed2d" />


   <img width="1287" height="516" alt="image" src="https://github.com/user-attachments/assets/9f1f55df-ce3b-4b99-8007-4f2ab40b28a6" />


5. Answer in your notes: How could you use `gh issue` in a script or automation?
     - By combining gh issue commands in a script,you can automatically:
        - Check open issues
        - Add comments
        - Close issues

    - Example:
        ```bash
        gh issue list --repo Aditya09-cse/gh-cli-task-day-26
        gh issue comment 1 --repo Aditya09-cse/gh-cli-task-day-26 --body "Checked automatically."
        gh issue close 1 --repo Aditya09-cse/gh-cli-task-day-26
        ```
### Task 4: Pull Requests
1. Create a branch, make a change, push it, and create a **pull request** entirely from the terminal
   <img width="1086" height="210" alt="image" src="https://github.com/user-attachments/assets/0361cdbd-a258-4a80-905b-13951e62737a" />

   <img width="896" height="325" alt="image" src="https://github.com/user-attachments/assets/8753a226-5445-45b9-92e0-34dce69219c4" />

   <img width="761" height="154" alt="image" src="https://github.com/user-attachments/assets/2b8d8ecb-4868-44f8-8594-3ea5600fbcca" />

   <img width="619" height="182" alt="image" src="https://github.com/user-attachments/assets/e659ae26-d5ef-4429-8b39-19907c2f3789" />

   <img width="1308" height="422" alt="image" src="https://github.com/user-attachments/assets/3f24151b-f2c5-4bc2-8f94-4a741225ad4b" />
 
2. List all open PRs on a repo
   <img width="722" height="114" alt="image" src="https://github.com/user-attachments/assets/5442966c-7f57-4f67-923e-a0038e001ff0" />


3. View the details of your PR — check its status, reviewers, and checks
   <img width="1141" height="121" alt="image" src="https://github.com/user-attachments/assets/f0b653d5-bc71-4394-a874-c5c829a208dc" />

4. Merge your PR from the terminal
   <img width="752" height="110" alt="image" src="https://github.com/user-attachments/assets/ea9ad880-2de6-4a9f-9078-6aac133f91f5" />

   <img width="1289" height="506" alt="image" src="https://github.com/user-attachments/assets/bac37ebd-0039-42b1-9d98-80bfa1d7dbc3" />


5. Answer in your notes:
   - What merge methods does `gh pr merge` support?
       - merge commit
       - merge & rebase
       - merge & squash
         
   - How would you review someone else's PR using `gh`?
      - ` gh pr review <PR-Number>`

  ---

## I will do this in future ( PENDING WORK ) 
  ### Task 5: GitHub Actions & Workflows (Preview) 
1. List the workflow runs on any public repo that uses GitHub Actions
2. View the status of a specific workflow run
3. Answer in your notes: How could `gh run` and `gh workflow` be useful in a CI/CD pipeline?

### Task 6: Useful `gh` Tricks
Explore and try these — add the ones you find useful to your `git-commands.md`:
1. `gh api` — make raw GitHub API calls from the terminal
2. `gh gist` — create and manage GitHub Gists
3. `gh release` — create and manage releases
4. `gh alias` — create shortcuts for commands you use often
5. `gh search repos` — search GitHub repos from the terminal


  
     





