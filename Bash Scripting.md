# **1. Introduction to Bash Scripting**
Bash scripting allows you to automate tasks, create utilities, and manage system processes. Scripts are essentially a sequence of Bash commands written in a file.
## **1.1 Creating and Running a Script**
1. **Create a new script file**:
    ```sh
    touch myscript.sh
    ```
2. **Make it executable**:
    ```sh
    chmod +x myscript.sh
    ```
    
3. **Write a basic script**:
    
    ```sh
    #!/bin/bash
    echo "Hello, World!"
    ```
    
4. **Run the script**:
    
    ```sh
    ./myscript.sh
    ```
    
    Or explicitly with Bash:
    
    ```sh
    bash myscript.sh
    ```
    

---
# **2. Variables and Data Types**

## **2.1 Variable Declaration**

```sh
name="Alice"
age=25
echo "Name: $name, Age: $age"
```

## **2.2 Reading User Input**

```sh
read -p "Enter your name: " user_name
echo "Hello, $user_name!"
```

## **2.3 Command Substitution**

```sh
current_date=$(date)
echo "Today's date: $current_date"
```

## **2.4 Arithmetic Operations**

```sh
x=5
y=3
sum=$((x + y))
echo "Sum: $sum"
```

---

# **3. Control Flow**

## **3.1 Conditional Statements**

### **If-Else**

```sh
if [ "$USER" = "root" ]; then
    echo "You are root."
else
    echo "You are not root."
fi
```

### **Nested If**

```sh
if [ -f /etc/passwd ]; then
    echo "File exists."
else
    echo "File does not exist."
fi
```

### **Case Statement**

```sh
echo "Enter a number:"
read num

case $num in
    1) echo "One";;
    2) echo "Two";;
    *) echo "Unknown";;
esac
```

---

# **4. Loops**

## **4.1 For Loop**

```sh
for i in {1..5}; do
    echo "Iteration $i"
done
```

## **4.2 While Loop**

```sh
count=1
while [ $count -le 5 ]; do
    echo "Count: $count"
    ((count++))
done
```

## **4.3 Until Loop**

```sh
count=1
until [ $count -gt 5 ]; do
    echo "Count: $count"
    ((count++))
done
```

---

# **5. Functions**

## **5.1 Basic Function**

```sh
my_function() {
    echo "Hello from function!"
}

my_function
```

## **5.2 Function with Parameters**

```sh
greet() {
    echo "Hello, $1!"
}

greet "Alice"
```

## **5.3 Return Values**

```sh
add() {
    echo $(( $1 + $2 ))
}

result=$(add 3 5)
echo "Sum: $result"
```

---

# **6. File and Directory Operations**

## **6.1 Checking If a File Exists**

```sh
if [ -f "file.txt" ]; then
    echo "File exists."
else
    echo "File does not exist."
fi
```

## **6.2 Creating and Deleting Files**

```sh
touch newfile.txt
rm newfile.txt
```

## **6.3 Reading a File Line by Line**

```sh
while read line; do
    echo "Line: $line"
done < file.txt
```

---

# **7. Process Management**

## **7.1 Running Commands in the Background**

```sh
sleep 10 &
```

## **7.2 Listing Background Jobs**

```sh
jobs
```

## **7.3 Bringing a Job to the Foreground**

```sh
fg %1
```

## **7.4 Killing a Process**

```sh
kill -9 PID
```

---

# **8. Debugging Bash Scripts**

## **8.1 Running with Debug Mode**

```sh
bash -x script.sh
```

## **8.2 Adding Debugging Inside Script**

```sh
set -x  # Enable debugging
echo "Debugging mode is ON"
set +x  # Disable debugging
```

---

# **9. Automation with Cron Jobs**

## **9.1 Creating a Cron Job**

Edit cron jobs using:

```sh
crontab -e
```

Example:

```
0 5 * * * /home/user/myscript.sh
```

This runs the script daily at **5:00 AM**.

## **9.2 Listing Existing Cron Jobs**

```sh
crontab -l
```

---

# **10. Handling Signals**

## **10.1 Trapping Signals**

```sh
trap "echo 'Signal caught!'; exit" SIGINT SIGTERM

while true; do
    sleep 1
done
```

Press `Ctrl+C` to test signal handling.

---

# **11. Input and Output Redirection**

## **11.1 Redirecting Output to a File**

```sh
echo "Hello" > output.txt
```

## **11.2 Appending to a File**

```sh
echo "More text" >> output.txt
```

## **11.3 Redirecting Input**

```sh
sort < file.txt
```

## **11.4 Redirecting Both STDOUT and STDERR**

```sh
command > output.log 2>&1
```

---

# **12. Secure Scripting**

## **12.1 Avoiding Command Injection**

Never use `eval` or unvalidated input:

```sh
# BAD:
eval "rm -rf $user_input"
```

## **12.2 Restricting File Permissions**

```sh
chmod 600 myscript.sh
```

---

# **13. Advanced Bash Techniques**

## **13.1 Using Arrays**

```sh
arr=("one" "two" "three")
echo "${arr[0]}"  # Output: one
```

## **13.2 Associative Arrays (Dictionary)**

```sh
declare -A user
user[name]="Alice"
user[age]=30

echo "Name: ${user[name]}"
```

## **13.3 Parallel Execution**

Run multiple commands in parallel:

```sh
command1 & command2 & wait
```

---

# **14. Bash Best Practices**

✔ **Use Meaningful Variable Names**  
✔ **Quote Variables to Prevent Word Splitting**  
✔ **Check Exit Status (`$?`) for Errors**  
✔ **Use Functions for Code Reusability**  
✔ **Avoid Hardcoded Paths (`/home/user/...`)**

---

# **15. Further Learning**

- `man bash`
- GNU Bash Reference Manual: [https://www.gnu.org/software/bash/manual/bash.html](https://www.gnu.org/software/bash/manual/bash.html)
- Linux Command Line and Shell Scripting Bible (Book)

---

Would you like **practical exercises** or examples for a specific topic?