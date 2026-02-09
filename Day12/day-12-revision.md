# Day 12 – Revision & Consolidation (Days 01–11)

## Goal
Pause and revise core Linux fundamentals before moving ahead.

---

## 1. Mindset & Plan
- Focused on revising instead of learning new topics
- Rewrote notes to reinforce understanding
- Commands make more sense after hands-on practice

---

## 2. Processes & Services Review

Checked service status using `systemctl status`:

### SSH
- Status: running
- Loaded: disabled
- Purpose: Secure remote access

### Cron
- Status: running
- Loaded: enabled
- Purpose: Background job scheduling

### Nginx
- Status: running
- Loaded: enabled
- Purpose: Web server / reverse proxy

### Docker
- Status: running
- Loaded: enabled
- Purpose: Container engine

---

## 3. File Skills Practice (Days 06–11)

Commands practiced:
- `echo >> file`
- `chmod 400`, `chmod 664`
- `chown user file`
- `ls -l`
- `cp file1 file2`

Key learnings:
- Write permission is required to append data
- Ownership directly affects access
- `cp` overwrites destination content

---

## 4. User & Group Sanity Check

- Created a user using `sudo useradd -m dummy`
- Verified users under `/home`
- Understood directory permission restrictions
- Changed ownership using:
  ```bash
  sudo chown nairobi:tokyo dummy

## Mini Self-Check
 ### 1) Top 3 commands I use most
  - ls -l – permissions & ownership
  - grep – filter specific information
  - systemctl status – service health
    
 ### 2) Service health check commands
   - systemctl status <service>
   - systemctl is-enabled <service>
   - journalctl -u <service>

 ### 3) Safe permission/ownership change
  ```
  	chmod 664 file.txt
    chown user:group file.txt
  ```
 ### 4) Next 3-day focus
   - Stronger grip on services & logs
   - More real-world permission scenarios
   - shell fundamentals and advance

 
