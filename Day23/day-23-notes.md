## Task 1:
1. What is a branch in Git?**

    - A git branch is like a separate line of work where you can make   changes without affecting the main project.
    - it was like a parallel track to experiment, if everything pushes to main branch - this increase clarity in code and in main branch is not too messy.

2. Why do we use branches instead of committing everything to `main`?

   - we use branches because it will not affect our main code, until you push work to main branch, helps to work multiple users in one project and test, if everything looks than push to main branch

3. What is `HEAD` in Git?

   - HEAD points the current changes are done in which directory/ branch

4. What happens to your files when you switch branches?

   - if we switch branches then file in current branch will not be shown to another branch
   - means git works isolated for each branch until you push/commit changes from one branch to other branch
   - so, our files are not visible in another branch

##TASK 2:

 1. List all branches in your repo

    - git branch - use to list all branches in your repo

 2. Create a new branch called `feature-1`

    - git branch feature-1

 3. Switch to `feature-1`

    - git checkout feature-1
    - git switch feature-1

  4. Create a new branch and switch to it in a single command — call it `feature-2`

    - git checkout -b feature-2
    - git switch -c feature-2

 5. Try using `git switch` to move between branches — how is it different from `git checkout`?

    - git checkout is older way to create and switch to branch while git switch is newer way
    - it makes branches operations easier to understand
    - in checkout flag `-b` is used
    - in switch flag `-c` is used

 6. Make a commit on `feature-1` that does **not** exist on `main`

    - git switch `-c` feature-1
    - make commit
    - this commit will not exist on main branch, because both are different branches
    - changes will not reflect until you push changes to main branch

 7. Switch back to `main` — verify that the commit from `feature-1` is not there

    - git checkout main
    - you will see there is no commit shown made in feature branch

 8. Delete a branch you no longer need

    - git branch `-d` branch_name → delete locally (safe way)
    - git branch `-D` branch_name → force delete locally
    - git push origin —delete branch_name → Delete from remote (GitHub)
    - `-d` → safe delete (check merge status)
    - `-D` → force delete (ignores merge status)
    - push origin —delete → removes it from the remote

## Taks 3:
 1. What is the difference between `origin` and `upstream`?

    - origin → your fork/clone (the repo you own or cloned)
    -  upstream → the source/original repo (the one you forked from)
    - you push changes to origin
    - pull updates from upstream to stay aligned/update with your project

##Taks 4: 

 What is the difference between git fetch and git pull?
   - fetch → download only (safe, review before applying
   - pull → download + apply (faster, but can surprise you with conflicts)
   - git fetch for control and visibility
   - git pull when you are confident, you want the changes of remote

   
