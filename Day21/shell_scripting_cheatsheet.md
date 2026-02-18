# 🐚 Shell Scripting Cheat Sheet

**#90DaysOfDevOps -- Day 21**

------------------------------------------------------------------------

# 📌 Quick Reference Table

  Topic      Key Syntax                 Example
  ---------- -------------------------- ------------------------------------
  Variable   `VAR="value"`              `NAME="DevOps"`
  Argument   `$1`, `$2`                 `./script.sh arg1`
  If         `if [ condition ]; then`   `if [ -f file ]; then`
  For loop   `for i in list; do`        `for i in 1 2 3; do`
  Function   `name() { ... }`           `greet() { echo "Hi"; }`
  Grep       `grep pattern file`        `grep -i "error" log.txt`
  Awk        `awk '{print $1}' file`    `awk -F: '{print $1}' /etc/passwd`
  Sed        `sed 's/old/new/g' file`   `sed -i 's/foo/bar/g' config.txt`

------------------------------------------------------------------------

# 1️⃣ Basics

## Shebang

``` bash
#!/bin/bash
```

## Running a Script

``` bash
chmod +x script.sh
./script.sh
bash script.sh
```

## Variables

``` bash
NAME="DevOps"
echo "$NAME"
```

## Read Input

``` bash
read -p "Enter name: " NAME
```

## Arguments

``` bash
echo $0
echo $1
echo $# 
echo $@
echo $?
```

------------------------------------------------------------------------

# 2️⃣ Conditionals

## String

``` bash
[ "$a" = "$b" ]
[ -z "$a" ]
```

## Integer

``` bash
[ $a -eq $b ]
[ $a -gt $b ]
```

## File

``` bash
[ -f file ]
[ -d dir ]
```

## If Statement

``` bash
if [ -f file ]; then
  echo "Exists"
else
  echo "Not Found"
fi
```

------------------------------------------------------------------------

# 3️⃣ Loops

## For

``` bash
for i in 1 2 3; do
  echo $i
done
```

## While

``` bash
while read line; do
  echo $line
done < file.txt
```

------------------------------------------------------------------------

# 4️⃣ Functions

``` bash
greet() {
  echo "Hello $1"
}
greet DevOps
```

------------------------------------------------------------------------

# 5️⃣ Text Processing

## Grep

``` bash
grep -i "error" file
```

## Awk

``` bash
awk -F: '{print $1}' /etc/passwd
```

## Sed

``` bash
sed -i 's/old/new/g' file
```

------------------------------------------------------------------------

# 6️⃣ Useful One-Liners

``` bash
find . -type f -mtime +7 -delete
wc -l *.log
tail -f app.log | grep --line-buffered "ERROR"
df -h | awk '$5 > 80 {print $0}'
```

------------------------------------------------------------------------

# 7️⃣ Error Handling

``` bash
set -euo pipefail
set -x
trap 'echo Cleanup' EXIT
exit 0
```


