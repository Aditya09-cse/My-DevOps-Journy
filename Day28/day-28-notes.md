# Day 28 – Revision Day: Everything from Day 1 to Day 27



## Challenge Tasks

### Task 1: Self-Assessment Checklist
Go through the checklist below. For each item, mark yourself honestly:
- **Can do confidently**
- **Need to revisit**
- **Haven't done yet**

#### Linux
- [**Can do confidently**] Navigate the file system, create/move/delete files and directories
- [**Can do confidently**] Manage processes — list, kill, background/foreground
- [**Can do confidently**] Work with systemd — start, stop, enable, check status of services
- [**Can do confidently**] Read and edit text files using vi/vim or nano
- [**Can do confidently**] Troubleshoot CPU, memory, and disk issues using top, free, df, du
- [**Need to revisit**] Explain the Linux file system hierarchy (/, /etc, /var, /home, /tmp, etc.)
- [**Can do confidently**] Create users and groups, manage passwords
- [**Can do confidently**] Set file permissions using chmod (numeric and symbolic)
- [**Can do confidently**] Change file ownership with chown and chgrp
- [**Need to revisit**] Create and manage LVM volumes
- [**Can do confidently**] Check network connectivity — ping, curl, netstat, ss, dig, nslookup
- [**Can do confidently**] Explain DNS resolution, IP addressing, subnets, and common ports

#### Shell Scripting
- [**Can do confidently**] Write a script with variables, arguments, and user input
- [**Need to revisit**] Use if/elif/else and case statements
- [**Need to revisit**] Write for, while, and until loops
- [**Need to revisit**] Define and call functions with arguments and return values
- [**Need to revisit**] Use grep, awk, sed, sort, uniq for text processing
- [**Need to revisit**] Handle errors with set -e, set -u, set -o pipefail, trap
- [**Need to revisit**] Schedule scripts with crontab

#### Git & GitHub
- [**Can do confidently**] Initialize a repo, stage, commit, and view history
- [**Can do confidently**] Create and switch branches
- [**Can do confidently**] Push to and pull from GitHub
- [**Can do confidently**] Explain clone vs fork
- [**Can do confidently**] Merge branches — understand fast-forward vs merge commit
- [**Can do confidently**] Rebase a branch and explain when to use it vs merge
- [**Can do confidently**] Use git stash and git stash pop
- [**Can do confidently**] Cherry-pick a commit from another branch
- [**Can do confidently**] Explain squash merge vs regular merge
- [**Can do confidently**] Use git reset (soft, mixed, hard) and git revert
- [**Need to revisit**] Explain GitFlow, GitHub Flow, and Trunk-Based Development
- [**Can do confidently**] Use GitHub CLI to create repos, PRs, and issues

---

### Task 2: Revisit Your Weak Spots
1. Pick **3 topics** from the checklist where you marked "Need to revisit"
2. Go back to that day's challenge and redo the hands-on tasks
3. Document what you re-learned in `day-28-notes.md`

---

### Task 3: Quick-Fire Questions

1. What does `chmod 755 script.sh` do?
   
   - It will give `read/write/execute permission to owner and read/excute to group & other`
2. What is the difference between a process and a service?
   - `process` is instance of program  while `service` is also a long running process in backrgound.

3. How do you find which process is using port 8080?
  - ` ss -tulpn | grep 8080 `
    
4. What does `set -euo pipefail` do in a shell script?
   ```
   -e  → Exit immediately if a command fails
   -u  → Exit if using an undefined variable
   -o pipefail → If any command in a pipeline fails, the whole pipeline fails
   ```
   
5. What is the difference between `git reset --hard` and `git revert`?
  - `git reset --hard` -> Remove the commit completely from history
  - `git revert` -> keep the orginal commit in history and generate new commit
    
6. What branching strategy would you recommend for a team of 5 developers shipping weekly?
   - 
7. What does `git stash` do and when would you use it?
   - `git stash` -> hide the current ongoing work
     
8. How do you schedule a script to run every day at 3 AM?
   - 0 3 * * * /path/script.sh
   - 
9. What is the difference between `git fetch` and `git pull`?
    - ` git fetch ` -> Download changes without merging
    - `git pull` -> Download Changes and merge them
      
14. What is LVM and why would you use it instead of regular partitions?
  - `LVM ` stands for Linux Volume Managemnet , Where you can manage storage accoding to need
  - Regular Partision are fixed Sized and hard to Change
  - While LVM allows you to easily resize and combine disk space when need
---

### Task 4: Organize Your Work
1. [✅] Make sure all your daily submissions (day-1 through day-27) are committed and pushed
2. [✅] Check that your `git-commands.md` is up to date
3. [*] Check that your shell scripting cheat sheet is complete
4. [✅] Verify your GitHub profile and repos are clean (from Day 27)

---

### Task 5: Teach It Back

1. Explain file permissions to a new Linux user
   - file permission are used to autharize the user, means what you do with that particular file
   - Three types permission - `read` , `write` , `execute`
   - Range of file permission is `0-7`
   - example - if you give hello.sh , permission `777` , then everyone can read, write and execute this shell script
   - Recomended Permission for better Security `744` means only user can `execute` and group  & other can read only

Teaching is the best test of understanding.

---

## Submission
1. Add your `day-28-notes.md` to `2026/day-28/`
2. Push to your fork
3. Make sure all previous days are pushed and up to date

---

## Learn in Public

Share your self-assessment results or your "teach it back" explanation on LinkedIn. Be honest about what you found easy and what you need to work on.

`#90DaysOfDevOps` `#DevOpsKaJosh` `#TrainWithShubham`

Happy Learning!
**TrainWithShubham**
