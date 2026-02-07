# Day 10 – File Permissions & File Operations

## Files Created
- devops.txt (created using touch)
- notes.txt (content added using cat >>)
- scrip.sh (shell script created using vim)
- project/ (directory)

## Reading Files
- Viewed notes.txt using cat
- Opened scrip.sh in read-only mode using vim -R
- Displayed first 5 lines of /etc/passwd using head
- Displayed last 5 lines of /etc/passwd using tail

## Permission Understanding
Linux permissions follow the format:
rwxrwxrwx (owner | group | others)

Numeric values:
- r = 4
- w = 2
- x = 1

## Permission Changes

### scrip.sh
- Initially not executable
- Permission changed using chmod
- Executed using ./scrip.sh
- Later execution failed after permission removal (Permission denied)

### devops.txt
- Set to read-only using chmod 400
- Writing to file failed with Permission denied

### notes.txt
- Permission set to 640 (owner: rw, group: r, others: ---)

### project/
- Directory created
- Permission set to 755 (rwxr-xr-x)

## Commands Used
```bash
touch devops.txt
cat >> notes.txt
vim scrip.sh
cat notes.txt
vim -R scrip.sh
head -5 /etc/passwd
tail -5 /etc/passwd
chmod 764 scrip.sh
chmod 400 devops.txt
chmod 640 notes.txt
mkdir project
chmod 755 project
ls -l
```

### Testing Permissions
  - Writing to devops.txt resulted in Permission denied
  - Executing scrip.sh without execute permission resulted in Permission denied
### What I Learned
  - File permissions control access and security in Linux
  - Execute permission is required to run scripts
  - Testing permission errors helps understand real system behavior
