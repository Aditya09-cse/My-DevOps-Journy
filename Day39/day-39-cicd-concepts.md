# Day 39 – CI/CD Concepts

Today I focused on understanding **why CI/CD exists** and what problems it solves before writing any actual pipelines.

---

# Task 1 – The Problem

## Scenario
A team of 5 developers are pushing code to the same repository and manually deploying to production.

---

## 1. What can go wrong?

If deployment is manual, many problems can occur:

- Merge conflicts between developers
- One developer overwriting another’s changes
- Code that works locally but fails in production
- Human mistakes during deployment (wrong file, wrong server, wrong command)
- No automated testing before release
- Production downtime
- No easy rollback if something breaks
- Stress and coordination issues between team members

Manual processes do not scale. As the team grows, risk increases.

This is why automation becomes necessary.

---

## 2. What does “It works on my machine” mean?

“It works on my machine” means the application runs successfully on the developer’s local computer, but fails in another environment like QA, staging, or production.

This happens because:
- Different operating systems
- Different dependency versions
- Missing environment variables
- Different database configurations
- Different installed software

Why this is a real problem:
- It delays releases
- Creates frustration between developers and operations teams
- Makes debugging difficult
- Reduces trust in the deployment process

CI/CD solves this by running builds and tests in clean, consistent environments every time code is pushed.

---

## 3. How many times a day can a team safely deploy manually?

With manual deployment, a team can realistically deploy **1–2 times per day** safely.

Each deployment requires:
- Coordination
- Manual verification
- Careful monitoring

With CI/CD automation:
- Teams can deploy multiple times per day
- Some large companies deploy hundreds or thousands of times per day

Automation increases speed, confidence, and reliability.

---

# Task 2 – CI vs CD

## 1. Continuous Integration (CI)

Continuous Integration is the practice of automatically building and testing code every time developers push changes to a shared repository.

Key points:
- Happens multiple times a day
- Code is merged frequently
- Automated tests run on every push
- Integration problems are caught early

Goal:
Keep the main branch always in a working state.

Example:
A developer pushes code to GitHub → tests run automatically → build fails if tests fail → developer fixes immediately.

---

## 2. Continuous Delivery (CD)

Continuous Delivery ensures that after CI passes, the application is always in a **deployable state**.

Everything is automated up to production, but the final deployment requires **manual approval**.

Key difference from CI:
CI focuses on integration and testing.
Continuous Delivery prepares the software for release.

Example:
Code passes tests → deployed automatically to staging → team reviews → someone clicks "Approve" → deployed to production.

---

## 3. Continuous Deployment

Continuous Deployment goes one step further than Continuous Delivery.

Every change that passes all automated tests is automatically deployed to production **without manual approval**.

Key points:
- Fully automated pipeline
- No human intervention required
- Requires strong test coverage
- Used by mature teams with high confidence in automation

Example:
Developer pushes code → tests pass → Docker image is built → automatically deployed to production.

---

## Difference Summary

- CI = Automatically build and test code
- Continuous Delivery = Automatically prepare for release, manual production approval
- Continuous Deployment = Fully automatic release to production

CI is about integration.
CD is about releasing software safely and frequently.

---

# Task 3 – Pipeline Anatomy

A CI/CD pipeline is made up of several components.

---

## Trigger

A trigger is the event that starts the pipeline.

Examples:
- Push to a branch
- Pull request creation
- Scheduled time
- Manual button click

Without a trigger, the pipeline does not start.

---

## Stage

A stage is a logical phase in the pipeline.

Common stages:
- Build
- Test
- Deploy

Stages help organize the pipeline into clear sections.

---

## Job

A job is a unit of work inside a stage.

A job:
- Runs on a runner
- Contains multiple steps
- Executes a specific task (e.g., build app, run tests)

Each job runs independently unless configured otherwise.

---

## Step

A step is a single command or action inside a job.

Examples:
- Install dependencies
- Run tests
- Build Docker image
- Upload artifact

Steps are the smallest executable unit in a pipeline.

---

## Runner

A runner is the machine (virtual or physical) that executes the job.

It can be:
- Cloud-hosted
- Self-hosted
- A container

The runner performs all the commands defined in the job.

---

## Artifact

An artifact is the output produced by a job.

Examples:
- Compiled binary
- Docker image
- Test report
- Build logs

Artifacts are often passed between stages or stored for later use.

---

# Final Reflection

CI/CD is not just a tool like GitHub Actions or Jenkins.

It is a development practice that:
- Encourages small, frequent changes
- Automates testing and deployment
- Reduces human error
- Increases confidence in releases
- Makes teams move faster without sacrificing stability

Understanding the concept first makes writing pipelines much easier.

---

---

### Task 4: Draw a Pipeline
Draw a CI/CD pipeline for this scenario:
> A developer pushes code to GitHub. The app is tested, built into a Docker image, and deployed to a staging server.

Include at least 3 stages. Hand-drawn and photographed is perfectly fine.

  <img width="976" height="419" alt="image" src="https://github.com/user-attachments/assets/ce80d8d9-cee7-49c3-9e9b-385f5138d322" />

--

### Task 5: Explore in the Wild
1. Open any popular open-source repo on GitHub 
2. Find their `.github/workflows/` folder
3. Open one workflow YAML file

    [workflow](https://github.com/OpenHub-Store/GitHub-Store/blob/main/.github/workflows/build-desktop-platforms.yml)
   
4. Write in your notes:
   - What triggers it?

```
on:
  push:
    branches:
      - generate-installers
```
   - How many jobs does it have?

      This workflow file has **3 jobs**:

   1. **build-windows** - Builds Windows installers (EXE & MSI)
   2. **build-macos** - Builds macOS installers (DMG & PKG) with a matrix strategy for both Intel (x64) and Apple Silicon (arm64)
   3. **build-linux** - Builds Linux installers (DEB, RPM, AppImage) with a matrix strategy for modern Ubuntu and Debian 12 compatibility

 - What does it do? (best guess)

     

##  What does it do

| Aspect | Details |
|--------|---------|
| **Workflow Name** | Build Desktop Platform Installers |
| **Trigger** | Push to `generate-installers` branch |
| **Purpose** | Build and package desktop installers for GitHub-Store app |
| **Windows Build** | Creates EXE & MSI installers on Windows latest |
| **macOS Build** | Creates DMG & PKG installers for Intel (x64) & Apple Silicon (arm64) |
| **Linux Build** | Creates DEB, RPM, & AppImage on Ubuntu latest; DEB & RPM on Ubuntu 22.04 |
| **Build Tool** | Gradle with Java 21 |
| **Retry Logic** | Up to 3 attempts with exponential backoff |
| **Artifact Retention** | 30 days |
| **Execution** | Parallel builds across all platforms |


---
