# Day 09 – Linux User & Group Management

## Overview
This challenge focused on **Linux user, group, and permission management**, simulating real-world DevOps collaboration scenarios.

---

## Users Created
- tokyo
- berlin
- professor
- nairobi

---

## Groups Created
- developers
- admins
- project-team

---

## Group Assignments
| User       | Groups Assigned                  |
|------------|----------------------------------|
| tokyo      | developers, project-team         |
| berlin     | developers, admins               |
| professor  | admins                           |
| nairobi    | project-team                     |

---

## Directories & Permissions

### `/opt/dev-project`
- Group Owner: developers  
- Permissions: `775`  
- Purpose: Shared development workspace  

**Test Result:**  
- Users in `developers` group were able to create files successfully.

---

### `/opt/team-workspace`
- Group Owner: project-team  
- Permissions: `775`  
- Purpose: Team collaboration directory  

**Test Result:**  
- User `nairobi` successfully created files inside the directory.

---

## Commands Used

```bash
# Create users
sudo useradd -m tokyo
sudo useradd -m berlin
sudo useradd -m professor
sudo useradd -m nairobi

# Create groups
sudo groupadd developers
sudo groupadd admins
sudo groupadd project-team

# Assign users to groups
sudo usermod -aG developers tokyo
sudo usermod -aG developers,admins berlin
sudo usermod -aG admins professor
sudo usermod -aG project-team nairobi
sudo usermod -aG project-team tokyo

# Create directories
sudo mkdir /opt/dev-project
sudo mkdir /opt/team-workspace

# Set group ownership
sudo chgrp developers /opt/dev-project
sudo chgrp project-team /opt/team-workspace

# Set permissions
sudo chmod 775 /opt/dev-project
sudo chmod 775 /opt/team-workspace

# Test access
sudo su - tokyo
touch /opt/dev-project/tokyo.txt

sudo su - nairobi
touch /opt/team-workspace/nairobi.txt
