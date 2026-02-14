## Day 17 – Shell Scripting: Loops, Arguments & Error Handling
### Task 1 – For Loop
 #### for_loop.sh
  ```
   #!/bin/bash

# Script to print fruits using for loop

fruits=("apple" "mango" "banana" "orange" "pineapple")

for i in "${fruits[@]}";
do
    echo $i
done
```
### Output
```
apple
mango
banana
orange
pineapple
```
#### count.sh
```
#!/bin/bash

# Script to print numbers 1 to 10

for i in {1..10};
do
    echo $i
done
```
### Output
```
1
2
3
4
5
6
7
8
9
10
```
### Task 2 – While Loop
#### countdown.sh
```
#!/bin/bash

read -p "Enter the number : " num

while [ $num -ge 0 ];
do
    echo $num
    num=$((num - 1))
done

echo "Done!"
```
#### Output
```
Enter the number : 5
5
4
3
2
1
0
Done!
```
### Task 3 – Command Line Arguments
#### greet.sh
```
#!/bin/bash

if [ $# -eq 0 ];
then
    echo "Usage: ./greet.sh <name>"
    exit 1
fi

echo "Hello, $1!"
```
#### args_demo.sh
```
#!/bin/bash

echo "Total number of arguments : $#"
echo "All arguments : $@"
echo "Script name : $0"
```

### Task 4 – Install Packages via Script
#### install_packages.sh
```
#!/bin/bash

# Check if running as root
if [ "$EUID" -ne 0 ]; then
    echo "Please run this script as root"
    exit 1
fi

packages=("nginx" "wget" "curl")

for pkg in "${packages[@]}"
do
    echo "Checking package : $pkg"

    if dpkg -s "$pkg" > /dev/null 2>&1 ; then
        echo "$pkg is already installed"
    else
        echo "Installing $pkg..."
        apt-get update
        apt-get install -y "$pkg"
    fi
done

echo "All packages processed successfully"
```


