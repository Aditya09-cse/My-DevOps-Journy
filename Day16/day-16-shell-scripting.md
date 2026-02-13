# Day 16 – Shell Scripting Basics

## Overview
Today I started my Shell Scripting journey and learned the fundamentals every script needs.

---

## Task 1 – hello.sh

### Script
```bash
#!/bin/bash
echo "Hello, DevOps!"
```
Output
  - Hello, DevOps
  
Learning
  - Shebang (#!/bin/bash) defines interpreter.
  - Without shebang, script may not execute correctly with ./script.sh.

## Task 2 – variables.sh

### Script
```
#!/bin/bash

NAME="Aditya Singh Tomar"
ROLE="DevOps Engineer"

echo "Hello, I am $NAME and I am a $ROLE"
```
Output
  - Hello, I am Aditya Singh Tomar and I am a DevOps Engineer

Learning
  - No spaces around =
  - Double quotes allow variable expansion
  - Single quotes print literal value

## Task 3 – greet.sh

### Script

```
#!/bin/bash

read -p "Enter your
name: " NAME
read -p "Enter your favourite tool: " TOOL

echo "Hello $NAME, your favourite tool is $TOOL"
```
Output Example
 - Enter your name: Aditya
 - Enter your favourite tool: ssh
 - Hello Aditya, your favourite tool is ssh

## Task 4 – check_number.sh

### Script

```
#!/bin/bash

read -p "Enter the number: " NUM

if [ $NUM -gt 0 ]; then
    echo "Number is positive"
elif [ $NUM -lt 0 ]; then
    echo "Number is negative"
else
    echo "Number is zero"
fi
```
