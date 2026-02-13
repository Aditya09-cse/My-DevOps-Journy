# Day 16 – Shell Scripting Basics 🚀

Today I officially started my Shell Scripting journey as part of #90DaysOfDevOps.

Instead of just running Linux commands, I began writing small automation scripts using Bash.

---

## 🔹 Task 1 – hello.sh

### Script
```bash
echo "Hello, DevOps!"
```

### Output
```
Hello, DevOps!
```

### Learning
- A script can be executed using `chmod +x` and `./script.sh`
- Shebang (`#!/bin/bash`) defines the interpreter and is important for portability

---

## 🔹 Task 2 – variables.sh

### Script
```bash
#!/bin/bash

NAME="Aditya Singh Tomar"
Role="DevOps Engineer"

echo "Hello, I am $NAME and I am a $Role"
```

### Output
```
Hello, I am Aditya Singh Tomar and I am a DevOps Engineer
```

### Learning
- No spaces around `=`
- Double quotes allow variable expansion
- Single quotes print literal values
- Variable naming consistency improves readability

---

## 🔹 Task 3 – greet.sh

### Script
```bash
#!/bin/bash

read -p "Enter your name : " name
read -p "Enter your favourite tool : " tool

echo "Hello $name, your favourite tool is $tool"
```

### Sample Output
```
Enter your name : Aditya
Enter your favourite tool : ssh
Hello Aditya, your favourite tool is ssh
```

### Learning
- `read -p` makes scripts interactive
- User input can be stored and reused dynamically

---

## 🔹 Task 4 – check_number.sh

### Script
```bash
#!/bin/bash

read -p "Enter the number : " num

if [ "$num" -gt 0 ]; then
    echo "Number is positive"
elif [ "$num" -eq 0 ]; then
    echo "Number is zero"
else
    echo "Number is negative"
fi
```

### Learning
- Numeric comparisons use `-gt`, `-lt`, `-eq`
- Small syntax mistakes can cause errors like:
  `integer expression expected`
- Debugging helps understand logic deeply

---

## 🔹 Task 5 – file_check.sh

### Script
```bash
#!/bin/bash

read -p "Enter the filename : " filename

if [ -f "$filename" ]; then
    echo "File '$filename' exists."
else
    echo "File '$filename' does not exist."
fi
```

### Learning
- `-f` checks if a file exists
- Always quote variables to avoid errors

---

## 🔹 Task 6 – server_check.sh

### Script
```bash
#!/bin/bash

read -p "Enter the service name : " service
read -p "Do you want to check the status (y/n) : " choice

if [ "$choice" = "y" ]; then
    if systemctl is-active --quiet "$service"; then
        echo "Service '$service' is active."
    else
        echo "Service '$service' is not active."
    fi
else
    echo "Skipped."
fi
```

### Learning
- Nested `if` conditions
- Using `systemctl is-active --quiet`
- Real-world service validation
- Environment differences (like `systemctl: command not found`)

---

# 💡 Key Takeaways

1. Shell scripting requires attention to small syntax details.
2. Debugging builds deeper understanding than just writing code.
3. Even simple scripts can automate real DevOps tasks.

---

#90DaysOfDevOps #DevOpsKaJosh
