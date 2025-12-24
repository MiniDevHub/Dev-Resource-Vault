<div align="center">

# 🐚 Shell Scripting Mastery

<img src="https://img.shields.io/badge/Shell-Bash-green?style=for-the-badge&logo=gnu-bash" alt="Bash">
<img src="https://img.shields.io/badge/Automation-Scripts-blue?style=for-the-badge" alt="Automation">
<img src="https://img.shields.io/badge/Level-Beginner_to_Advanced-orange?style=for-the-badge" alt="All Levels">

### _Automate everything with the power of shell scripts_ ⚡

**Because clicking is for amateurs** 🚀

</div>

---

## 📚 Table of Contents

- [🎯 Shell Scripting Basics](#-shell-scripting-basics)
- [📝 Variables & Data Types](#-variables--data-types)
- [🔄 Control Structures](#-control-structures)
- [⚙️ Functions](#️-functions)
- [📂 File Operations](#-file-operations)
- [🌐 Network Operations](#-network-operations)
- [🛠️ Practical Automation Scripts](#️-practical-automation-scripts)
- [💡 Best Practices & Pro Tips](#-best-practices--pro-tips)

---

<div align="center">

## 🎯 Shell Scripting Basics

</div>

### Your First Script 🚀

```bash
#!/bin/bash
# ═══════════════════════════════════════════
# Basic Script Structure
# ═══════════════════════════════════════════

# Shebang - tells system which interpreter to use
#!/bin/bash          # Bash (most common)
#!/bin/sh            # POSIX sh (portable)
#!/usr/bin/env bash  # Find bash in PATH (portable)

# ═══════════════════════════════════════════
# Hello World Script
# ═══════════════════════════════════════════

#!/bin/bash
echo "Hello, World!"
echo "Today is $(date)"

# Save as: hello.sh
# Make executable: chmod +x hello.sh
# Run: ./hello.sh

# ═══════════════════════════════════════════
# Comments
# ═══════════════════════════════════════════

# Single line comment

: '
Multi-line comment
This is line 2
This is line 3
'

# ═══════════════════════════════════════════
# Exit Codes
# ═══════════════════════════════════════════

#!/bin/bash

# Exit with success
exit 0

# Exit with error
exit 1

# Check last command's exit code
command
if [ $? -eq 0 ]; then
    echo "Success"
else
    echo "Failed"
fi
```

---

### Script Execution 🏃

```bash
# ═══════════════════════════════════════════
# Making Scripts Executable
# ═══════════════════════════════════════════

# View current permissions
ls -l script.sh

# Add execute permission
chmod +x script.sh

# Specific permissions
chmod 755 script.sh    # rwxr-xr-x
chmod 700 script.sh    # rwx------

# ═══════════════════════════════════════════
# Running Scripts
# ═══════════════════════════════════════════

# Method 1: Direct execution (requires execute permission)
./script.sh

# Method 2: Specify interpreter
bash script.sh
sh script.sh

# Method 3: Source (run in current shell)
source script.sh
. script.sh

# ═══════════════════════════════════════════
# Script Location Best Practices
# ═══════════════════════════════════════════

# Personal scripts
~/bin/script.sh
~/.local/bin/script.sh

# System-wide scripts
/usr/local/bin/script.sh

# Add to PATH
export PATH="$HOME/bin:$PATH"

# Make available everywhere
sudo ln -s /path/to/script.sh /usr/local/bin/scriptname
```

---

<div align="center">

## 📝 Variables & Data Types

</div>

### Variables 📊

```bash
#!/bin/bash
# ═══════════════════════════════════════════
# Variable Declaration
# ═══════════════════════════════════════════

# Simple assignment (no spaces around =)
name="MrDib"
age=25
is_active=true

# Using variables
echo "Name: $name"
echo "Age: ${age}"          # Safer with braces
echo "Name: ${name}123"     # Braces necessary here

# ═══════════════════════════════════════════
# Read-Only Variables
# ═══════════════════════════════════════════

readonly VERSION="1.0.0"
VERSION="2.0.0"  # Error: VERSION is read-only

# ═══════════════════════════════════════════
# Command Substitution
# ═══════════════════════════════════════════

# Modern way
current_date=$(date)
files=$(ls -l)

# Legacy way (still works)
current_date=`date`

# ═══════════════════════════════════════════
# Environment Variables
# ═══════════════════════════════════════════

# Export for child processes
export MY_VAR="value"

# Common environment variables
echo $HOME          # Home directory
echo $USER          # Current user
echo $PATH          # Command search path
echo $PWD           # Current directory
echo $SHELL         # Current shell
echo $HOSTNAME      # Machine name

# ═══════════════════════════════════════════
# Default Values
# ═══════════════════════════════════════════

# Use default if unset
name=${name:-"Guest"}

# Assign default if unset
name=${name:="Guest"}

# Use alternate if set
message=${name:+"Hello, $name"}

# Error if unset
name=${name:?"Error: name is not set"}

# ═══════════════════════════════════════════
# String Operations
# ═══════════════════════════════════════════

text="Hello, World!"

# Length
echo ${#text}                    # 13

# Substring
echo ${text:0:5}                 # Hello
echo ${text:7}                   # World!

# Replace
echo ${text/World/Universe}      # Hello, Universe!
echo ${text//l/L}                # HeLLo, WorLd! (all occurrences)

# Remove pattern
filename="file.txt.bak"
echo ${filename%.bak}            # file.txt
echo ${filename#file.}           # txt.bak

# Uppercase/Lowercase
echo ${text^^}                   # HELLO, WORLD!
echo ${text,,}                   # hello, world!

# ═══════════════════════════════════════════
# Arrays
# ═══════════════════════════════════════════

# Declare array
fruits=("apple" "banana" "cherry")

# Another way
declare -a colors
colors[0]="red"
colors[1]="green"
colors[2]="blue"

# Access elements
echo ${fruits[0]}                # apple
echo ${fruits[@]}                # All elements
echo ${fruits[*]}                # All elements (different in quotes)

# Array length
echo ${#fruits[@]}               # 3

# Add element
fruits+=("orange")

# Loop through array
for fruit in "${fruits[@]}"; do
    echo "$fruit"
done

# ═══════════════════════════════════════════
# Associative Arrays (Hash Maps)
# ═══════════════════════════════════════════

# Bash 4.0+
declare -A user
user[name]="MrDib"
user[age]=25
user[city]="New York"

# Access
echo ${user[name]}

# All keys
echo ${!user[@]}

# All values
echo ${user[@]}

# Loop
for key in "${!user[@]}"; do
    echo "$key: ${user[$key]}"
done
```

---

### User Input 📥

```bash
#!/bin/bash
# ═══════════════════════════════════════════
# Reading Input
# ═══════════════════════════════════════════

# Basic input
echo "Enter your name:"
read name
echo "Hello, $name!"

# Prompt in same line
read -p "Enter your name: " name

# Silent input (passwords)
read -sp "Enter password: " password
echo ""  # New line after password

# Multiple inputs
read -p "Enter first and last name: " first last

# Read with timeout
read -t 5 -p "Quick! Enter something (5 sec): " quick_input

# Read single character
read -n 1 -p "Press any key to continue..."

# Read from file
while read line; do
    echo "$line"
done < input.txt

# ═══════════════════════════════════════════
# Command Line Arguments
# ═══════════════════════════════════════════

#!/bin/bash

# Special variables
echo "Script name: $0"
echo "First argument: $1"
echo "Second argument: $2"
echo "All arguments: $@"
echo "Number of arguments: $#"

# Example usage: ./script.sh arg1 arg2 arg3

# Check argument count
if [ $# -lt 2 ]; then
    echo "Usage: $0 <arg1> <arg2>"
    exit 1
fi

# Loop through arguments
for arg in "$@"; do
    echo "Argument: $arg"
done

# ═══════════════════════════════════════════
# Parsing Options
# ═══════════════════════════════════════════

#!/bin/bash

# Simple option parsing
while getopts "f:u:p:h" opt; do
    case $opt in
        f) filename=$OPTARG ;;
        u) username=$OPTARG ;;
        p) password=$OPTARG ;;
        h)
            echo "Usage: $0 -f file -u user -p pass"
            exit 0
            ;;
        \?)
            echo "Invalid option: -$OPTARG"
            exit 1
            ;;
    esac
done

echo "File: $filename"
echo "User: $username"

# Usage: ./script.sh -f myfile.txt -u admin -p secret
```

---

<div align="center">

## 🔄 Control Structures

</div>

### Conditionals 🎯

```bash
#!/bin/bash
# ═══════════════════════════════════════════
# If Statements
# ═══════════════════════════════════════════

# Basic if
if [ $age -ge 18 ]; then
    echo "Adult"
fi

# If-else
if [ $age -ge 18 ]; then
    echo "Adult"
else
    echo "Minor"
fi

# If-elif-else
if [ $age -ge 65 ]; then
    echo "Senior"
elif [ $age -ge 18 ]; then
    echo "Adult"
else
    echo "Minor"
fi

# ═══════════════════════════════════════════
# Comparison Operators
# ═══════════════════════════════════════════

# Numeric comparisons
if [ $a -eq $b ]; then echo "Equal"; fi
if [ $a -ne $b ]; then echo "Not equal"; fi
if [ $a -gt $b ]; then echo "Greater than"; fi
if [ $a -lt $b ]; then echo "Less than"; fi
if [ $a -ge $b ]; then echo "Greater or equal"; fi
if [ $a -le $b ]; then echo "Less or equal"; fi

# String comparisons
if [ "$str1" = "$str2" ]; then echo "Equal"; fi
if [ "$str1" != "$str2" ]; then echo "Not equal"; fi
if [ -z "$str" ]; then echo "Empty string"; fi
if [ -n "$str" ]; then echo "Not empty"; fi

# ═══════════════════════════════════════════
# File Tests
# ═══════════════════════════════════════════

if [ -e file.txt ]; then echo "Exists"; fi
if [ -f file.txt ]; then echo "Regular file"; fi
if [ -d directory ]; then echo "Directory"; fi
if [ -r file.txt ]; then echo "Readable"; fi
if [ -w file.txt ]; then echo "Writable"; fi
if [ -x script.sh ]; then echo "Executable"; fi
if [ -s file.txt ]; then echo "Not empty"; fi
if [ -L link ]; then echo "Symbolic link"; fi

# ═══════════════════════════════════════════
# Logical Operators
# ═══════════════════════════════════════════

# AND
if [ $a -gt 0 ] && [ $a -lt 10 ]; then
    echo "Between 0 and 10"
fi

# OR
if [ $a -eq 0 ] || [ $a -eq 10 ]; then
    echo "Is 0 or 10"
fi

# NOT
if [ ! -f file.txt ]; then
    echo "File doesn't exist"
fi

# ═══════════════════════════════════════════
# Modern Test Syntax [[ ]]
# ═══════════════════════════════════════════

# Recommended for bash scripts
if [[ $name == "MrDib" ]]; then
    echo "Hello, MrDib!"
fi

# Pattern matching
if [[ $filename == *.txt ]]; then
    echo "Text file"
fi

# Regex matching
if [[ $email =~ ^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$ ]]; then
    echo "Valid email"
fi

# Multiple conditions
if [[ $age -ge 18 && $country == "USA" ]]; then
    echo "Can vote in USA"
fi

# ═══════════════════════════════════════════
# Case Statements
# ═══════════════════════════════════════════

case $fruit in
    apple)
        echo "It's an apple"
        ;;
    banana|orange)
        echo "It's a banana or orange"
        ;;
    *)
        echo "Unknown fruit"
        ;;
esac

# Real-world example
read -p "Enter command (start/stop/restart): " cmd

case $cmd in
    start)
        echo "Starting service..."
        # start commands
        ;;
    stop)
        echo "Stopping service..."
        # stop commands
        ;;
    restart)
        echo "Restarting service..."
        # restart commands
        ;;
    *)
        echo "Invalid command"
        exit 1
        ;;
esac
```

---

### Loops 🔄

```bash
#!/bin/bash
# ═══════════════════════════════════════════
# For Loops
# ═══════════════════════════════════════════

# Loop over items
for item in apple banana cherry; do
    echo "Fruit: $item"
done

# Loop over range
for i in {1..5}; do
    echo "Number: $i"
done

# Loop with step
for i in {0..10..2}; do
    echo "Even: $i"
done

# C-style for loop
for ((i=0; i<5; i++)); do
    echo "Count: $i"
done

# Loop over files
for file in *.txt; do
    echo "Processing: $file"
done

# Loop over command output
for user in $(cat users.txt); do
    echo "User: $user"
done

# ═══════════════════════════════════════════
# While Loops
# ═══════════════════════════════════════════

# Basic while
count=0
while [ $count -lt 5 ]; do
    echo "Count: $count"
    ((count++))
done

# Read file line by line
while IFS= read -r line; do
    echo "Line: $line"
done < file.txt

# Infinite loop
while true; do
    echo "Running..."
    sleep 1
    # Break condition
    if [ condition ]; then
        break
    fi
done

# ═══════════════════════════════════════════
# Until Loops
# ═══════════════════════════════════════════

# Runs until condition is true
count=0
until [ $count -ge 5 ]; do
    echo "Count: $count"
    ((count++))
done

# ═══════════════════════════════════════════
# Loop Control
# ═══════════════════════════════════════════

# Break - exit loop
for i in {1..10}; do
    if [ $i -eq 5 ]; then
        break
    fi
    echo $i
done

# Continue - skip iteration
for i in {1..10}; do
    if [ $((i % 2)) -eq 0 ]; then
        continue
    fi
    echo "Odd: $i"
done
```

---

<div align="center">

## ⚙️ Functions

</div>

### Function Basics 🎯

```bash
#!/bin/bash
# ═══════════════════════════════════════════
# Defining Functions
# ═══════════════════════════════════════════

# Method 1
function greet() {
    echo "Hello, World!"
}

# Method 2 (preferred)
greet() {
    echo "Hello, World!"
}

# Call function
greet

# ═══════════════════════════════════════════
# Functions with Parameters
# ═══════════════════════════════════════════

greet_user() {
    local name=$1
    local age=$2
    echo "Hello, $name! You are $age years old."
}

# Call with arguments
greet_user "MrDib" 25

# ═══════════════════════════════════════════
# Return Values
# ═══════════════════════════════════════════

# Return exit status (0-255)
is_even() {
    local num=$1
    if [ $((num % 2)) -eq 0 ]; then
        return 0  # Success (true)
    else
        return 1  # Failure (false)
    fi
}

# Check return value
if is_even 4; then
    echo "4 is even"
fi

# Return string (via echo)
get_greeting() {
    local name=$1
    echo "Hello, $name!"
}

# Capture output
greeting=$(get_greeting "MrDib")
echo $greeting

# ═══════════════════════════════════════════
# Local Variables
# ═══════════════════════════════════════════

my_function() {
    local local_var="I'm local"
    global_var="I'm global"
    echo $local_var
}

my_function
echo $global_var     # Accessible
# echo $local_var    # Not accessible

# ═══════════════════════════════════════════
# Function with Multiple Return Values
# ═══════════════════════════════════════════

get_system_info() {
    local os=$(uname -s)
    local hostname=$(hostname)
    local user=$(whoami)

    echo "$os|$hostname|$user"
}

# Parse output
IFS='|' read -r os hostname user <<< "$(get_system_info)"
echo "OS: $os"
echo "Hostname: $hostname"
echo "User: $user"

# ═══════════════════════════════════════════
# Recursive Functions
# ═══════════════════════════════════════════

factorial() {
    local n=$1
    if [ $n -le 1 ]; then
        echo 1
    else
        local prev=$(factorial $((n - 1)))
        echo $((n * prev))
    fi
}

result=$(factorial 5)
echo "5! = $result"  # 120

# ═══════════════════════════════════════════
# Practical Examples
# ═══════════════════════════════════════════

# Check if command exists
command_exists() {
    command -v "$1" >/dev/null 2>&1
}

if command_exists git; then
    echo "Git is installed"
fi

# Print colored output
print_success() {
    echo -e "\033[0;32m✓ $1\033[0m"
}

print_error() {
    echo -e "\033[0;31m✗ $1\033[0m"
}

print_warning() {
    echo -e "\033[0;33m⚠ $1\033[0m"
}

print_success "Operation completed"
print_error "Operation failed"
print_warning "Be careful"

# Confirm action
confirm() {
    local message=${1:-"Are you sure?"}
    read -p "$message (y/n): " -n 1 -r
    echo
    [[ $REPLY =~ ^[Yy]$ ]]
}

if confirm "Delete file?"; then
    echo "Deleting..."
fi

# Progress bar
show_progress() {
    local duration=$1
    local steps=50
    local step_duration=$(awk "BEGIN {print $duration/$steps}")

    for ((i=0; i<=$steps; i++)); do
        local percent=$((i * 100 / steps))
        local filled=$((i * 50 / steps))
        local empty=$((50 - filled))

        printf "\r["
        printf "%${filled}s" | tr ' ' '='
        printf "%${empty}s" | tr ' ' ' '
        printf "] %3d%%" $percent

        sleep $step_duration
    done
    echo ""
}

echo "Processing..."
show_progress 3
echo "Done!"
```

---

<div align="center">

## 📂 File Operations

</div>

### Working with Files 📄

```bash
#!/bin/bash
# ═══════════════════════════════════════════
# File Creation & Deletion
# ═══════════════════════════════════════════

# Create file
touch newfile.txt
echo "content" > newfile.txt

# Create multiple files
touch file{1..5}.txt

# Create directory
mkdir -p path/to/nested/directory

# Delete file
rm file.txt

# Delete directory
rm -rf directory/

# Safe delete (ask confirmation)
rm -i file.txt

# ═══════════════════════════════════════════
# Reading Files
# ═══════════════════════════════════════════

# Read entire file
content=$(cat file.txt)

# Read line by line
while IFS= read -r line; do
    echo "Line: $line"
done < file.txt

# Read first N lines
head -n 10 file.txt

# Read last N lines
tail -n 10 file.txt

# Follow file (like tail -f)
tail -f logfile.txt

# ═══════════════════════════════════════════
# Writing Files
# ═══════════════════════════════════════════

# Overwrite file
echo "New content" > file.txt

# Append to file
echo "More content" >> file.txt

# Write multiple lines
cat > file.txt << EOF
Line 1
Line 2
Line 3
EOF

# Write with variables
cat > config.txt << EOF
Username: $USER
Date: $(date)
Path: $PWD
EOF

# ═══════════════════════════════════════════
# File Information
# ═══════════════════════════════════════════

# Check if file exists
if [ -f file.txt ]; then
    echo "File exists"
fi

# Check if directory exists
if [ -d directory ]; then
    echo "Directory exists"
fi

# File size
size=$(stat -f%z file.txt)  # macOS
size=$(stat -c%s file.txt)  # Linux

# File modification time
mtime=$(stat -f%m file.txt)  # macOS
mtime=$(stat -c%Y file.txt)  # Linux

# Line count
lines=$(wc -l < file.txt)

# ═══════════════════════════════════════════
# File Searching
# ═══════════════════════════════════════════

# Find files by name
find . -name "*.txt"

# Find files modified in last 7 days
find . -type f -mtime -7

# Find large files (>100MB)
find . -type f -size +100M

# Find and execute command
find . -name "*.log" -exec rm {} \;

# ═══════════════════════════════════════════
# Text Processing
# ═══════════════════════════════════════════

# Search in file
grep "pattern" file.txt

# Case-insensitive search
grep -i "pattern" file.txt

# Count matches
grep -c "pattern" file.txt

# Show line numbers
grep -n "pattern" file.txt

# Search multiple files
grep -r "pattern" directory/

# Replace text
sed 's/old/new/g' file.txt > newfile.txt

# In-place replace
sed -i.bak 's/old/new/g' file.txt

# Extract columns
awk '{print $1, $3}' file.txt

# Sum column
awk '{sum+=$1} END {print sum}' file.txt

# ═══════════════════════════════════════════
# File Comparison
# ═══════════════════════════════════════════

# Show differences
diff file1.txt file2.txt

# Side-by-side comparison
diff -y file1.txt file2.txt

# Unified format (like git diff)
diff -u file1.txt file2.txt

# ═══════════════════════════════════════════
# Archive & Compression
# ═══════════════════════════════════════════

# Create tar archive
tar -czf archive.tar.gz directory/

# Extract tar archive
tar -xzf archive.tar.gz

# Create zip
zip -r archive.zip directory/

# Extract zip
unzip archive.zip

# ═══════════════════════════════════════════
# File Permissions
# ═══════════════════════════════════════════

# Make executable
chmod +x script.sh

# Set specific permissions
chmod 755 script.sh

# Recursive permissions
chmod -R 755 directory/

# Change owner
chown user:group file.txt

# Recursive owner change
chown -R user:group directory/
```

---

<div align="center">

## 🌐 Network Operations

</div>

### Network Scripts 🌍

```bash
#!/bin/bash
# ═══════════════════════════════════════════
# Download Files
# ═══════════════════════════════════════════

# Using curl
curl -O https://example.com/file.zip
curl -o custom_name.zip https://example.com/file.zip

# With progress bar
curl -# -O https://example.com/file.zip

# Using wget
wget https://example.com/file.zip
wget -O custom_name.zip https://example.com/file.zip

# ═══════════════════════════════════════════
# API Requests
# ═══════════════════════════════════════════

# GET request
response=$(curl -s https://api.github.com/users/mrdib)
echo $response | jq '.name'

# POST request
curl -X POST https://api.example.com/users \
    -H "Content-Type: application/json" \
    -d '{"name":"MrDib","email":"mrdib@example.com"}'

# With authentication
curl -H "Authorization: Bearer $TOKEN" \
    https://api.example.com/protected

# ═══════════════════════════════════════════
# Network Testing
# ═══════════════════════════════════════════

# Check if host is reachable
ping -c 4 google.com

# Check if port is open
nc -zv google.com 80

# Get public IP
curl -s ifconfig.me
curl -s ipecho.net/plain

# DNS lookup
dig google.com
nslookup google.com

# ═══════════════════════════════════════════
# Speed Test
# ═══════════════════════════════════════════

speed_test() {
    echo "Testing download speed..."

    local start=$(date +%s)
    curl -o /dev/null https://speed.cloudflare.com/__down?bytes=10000000
    local end=$(date +%s)

    local duration=$((end - start))
    local speed=$((10 / duration))

    echo "Speed: ${speed}MB/s"
}

# ═══════════════════════════════════════════
# Monitor Website
# ═══════════════════════════════════════════

check_website() {
    local url=$1
    local status=$(curl -o /dev/null -s -w "%{http_code}" $url)

    if [ $status -eq 200 ]; then
        echo "✓ $url is UP (Status: $status)"
        return 0
    else
        echo "✗ $url is DOWN (Status: $status)"
        return 1
    fi
}

check_website "https://google.com"

# ═══════════════════════════════════════════
# Send Email via API
# ═══════════════════════════════════════════

send_email() {
    local to=$1
    local subject=$2
    local body=$3

    curl -X POST https://api.mailgun.net/v3/YOUR_DOMAIN/messages \
        -u "api:YOUR_API_KEY" \
        -F from="no-reply@example.com" \
        -F to="$to" \
        -F subject="$subject" \
        -F text="$body"
}
```

---

<div align="center">

## 🛠️ Practical Automation Scripts

</div>

### Real-World Examples 🚀

```bash
# ═══════════════════════════════════════════
# 1. Backup Script
# ═══════════════════════════════════════════

#!/bin/bash
# backup.sh - Automated backup script

BACKUP_DIR="$HOME/backups"
SOURCE_DIR="$HOME/documents"
DATE=$(date +%Y%m%d_%H%M%S)
BACKUP_FILE="backup_$DATE.tar.gz"

# Create backup directory
mkdir -p "$BACKUP_DIR"

# Create backup
echo "Creating backup..."
tar -czf "$BACKUP_DIR/$BACKUP_FILE" "$SOURCE_DIR"

# Check if successful
if [ $? -eq 0 ]; then
    echo "✓ Backup created: $BACKUP_FILE"

    # Delete backups older than 7 days
    find "$BACKUP_DIR" -name "backup_*.tar.gz" -mtime +7 -delete
    echo "✓ Old backups cleaned"
else
    echo "✗ Backup failed"
    exit 1
fi

# ═══════════════════════════════════════════
# 2. System Health Check
# ═══════════════════════════════════════════

#!/bin/bash
# health_check.sh - System health monitoring

echo "=== System Health Check ==="
echo "Date: $(date)"
echo ""

# CPU Usage
echo "CPU Usage:"
top -l 1 | grep "CPU usage" || mpstat 1 1

# Memory Usage
echo ""
echo "Memory Usage:"
free -h || vm_stat

# Disk Usage
echo ""
echo "Disk Usage:"
df -h | grep -E '^/dev/'

# Check services
echo ""
echo "Service Status:"
services=("nginx" "mysql" "redis")
for service in "${services[@]}"; do
    if systemctl is-active --quiet $service; then
        echo "✓ $service is running"
    else
        echo "✗ $service is NOT running"
    fi
done

# ═══════════════════════════════════════════
# 3. Git Repository Manager
# ═══════════════════════════════════════════

#!/bin/bash
# git_updater.sh - Update multiple git repositories

REPOS_DIR="$HOME/projects"

echo "Updating all repositories in $REPOS_DIR"

for repo in "$REPOS_DIR"/*/; do
    if [ -d "$repo/.git" ]; then
        echo ""
        echo "Updating: $(basename $repo)"
        cd "$repo"

        git fetch origin

        # Check if behind
        LOCAL=$(git rev-parse @)
        REMOTE=$(git rev-parse @{u})

        if [ $LOCAL = $REMOTE ]; then
            echo "✓ Up to date"
        else
            git pull origin main
            echo "✓ Updated"
        fi
    fi
done

# ═══════════════════════════════════════════
# 4. Development Environment Setup
# ═══════════════════════════════════════════

#!/bin/bash
# dev_setup.sh - Setup development environment

set -e  # Exit on error

echo "Setting up development environment..."

# Install Homebrew (macOS)
if ! command -v brew &> /dev/null; then
    echo "Installing Homebrew..."
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
fi

# Install packages
packages=(
    "git"
    "node"
    "python"
    "docker"
    "vim"
)

for package in "${packages[@]}"; do
    if ! command -v $package &> /dev/null; then
        echo "Installing $package..."
        brew install $package
    else
        echo "✓ $package already installed"
    fi
done

# Create project directories
mkdir -p ~/projects/{personal,work,opensource}

# Configure git
git config --global user.name "MrDib"
git config --global user.email "mrdib@example.com"

echo "✓ Development environment setup complete!"

# ═══════════════════════════════════════════
# 5. Log Monitor & Alert
# ═══════════════════════════════════════════

#!/bin/bash
# log_monitor.sh - Monitor logs for errors

LOG_FILE="/var/log/app.log"
ERROR_PATTERN="ERROR|FATAL|CRITICAL"
ALERT_EMAIL="admin@example.com"

# Tail log and check for errors
tail -f "$LOG_FILE" | while read line; do
    if echo "$line" | grep -qE "$ERROR_PATTERN"; then
        echo "Error detected: $line"

        # Send alert
        echo "$line" | mail -s "ERROR ALERT" "$ALERT_EMAIL"

        # Log to separate error file
        echo "$(date): $line" >> /var/log/errors.log
    fi
done

# ═══════════════════════════════════════════
# 6. Bulk File Rename
# ═══════════════════════════════════════════

#!/bin/bash
# rename.sh - Bulk rename files

OLD_EXT="txt"
NEW_EXT="md"
DIRECTORY="."

count=0
for file in "$DIRECTORY"/*.$OLD_EXT; do
    if [ -f "$file" ]; then
        new_name="${file%.$OLD_EXT}.$NEW_EXT"
        mv "$file" "$new_name"
        echo "Renamed: $(basename $file) -> $(basename $new_name)"
        ((count++))
    fi
done

echo "✓ Renamed $count files"

# ═══════════════════════════════════════════
# 7. Database Backup
# ═══════════════════════════════════════════

#!/bin/bash
# db_backup.sh - Automated database backup

DB_NAME="myapp"
DB_USER="root"
DB_PASS="password"
BACKUP_DIR="$HOME/db_backups"
DATE=$(date +%Y%m%d_%H%M%S)
BACKUP_FILE="$BACKUP_DIR/${DB_NAME}_$DATE.sql"

# Create backup directory
mkdir -p "$BACKUP_DIR"

# Create backup
echo "Backing up database: $DB_NAME"
mysqldump -u$DB_USER -p$DB_PASS $DB_NAME > "$BACKUP_FILE"

# Compress
gzip "$BACKUP_FILE"

# Delete old backups (keep last 30 days)
find "$BACKUP_DIR" -name "${DB_NAME}_*.sql.gz" -mtime +30 -delete

echo "✓ Backup completed: ${BACKUP_FILE}.gz"

# ═══════════════════════════════════════════
# 8. Server Deployment Script
# ═══════════════════════════════════════════

#!/bin/bash
# deploy.sh - Application deployment

set -e

APP_DIR="/var/www/myapp"
REPO_URL="git@github.com:user/myapp.git"
BRANCH="main"

echo "Starting deployment..."

# Navigate to app directory
cd "$APP_DIR"

# Pull latest changes
echo "Pulling latest code..."
git pull origin $BRANCH

# Install dependencies
echo "Installing dependencies..."
npm install

# Build application
echo "Building application..."
npm run build

# Restart service
echo "Restarting service..."
sudo systemctl restart myapp

echo "✓ Deployment completed successfully!"

# ═══════════════════════════════════════════
# 9. Docker Container Manager
# ═══════════════════════════════════════════

#!/bin/bash
# docker_manager.sh - Manage Docker containers

ACTION=$1

case $ACTION in
    start)
        echo "Starting containers..."
        docker-compose up -d
        ;;
    stop)
        echo "Stopping containers..."
        docker-compose down
        ;;
    restart)
        echo "Restarting containers..."
        docker-compose restart
        ;;
    logs)
        docker-compose logs -f
        ;;
    clean)
        echo "Cleaning up..."
        docker system prune -af
        docker volume prune -f
        ;;
    *)
        echo "Usage: $0 {start|stop|restart|logs|clean}"
        exit 1
        ;;
esac

# ═══════════════════════════════════════════
# 10. SSL Certificate Checker
# ═══════════════════════════════════════════

#!/bin/bash
# ssl_check.sh - Check SSL certificate expiry

DOMAIN=$1
DAYS_WARNING=30

if [ -z "$DOMAIN" ]; then
    echo "Usage: $0 domain.com"
    exit 1
fi

# Get certificate expiry date
expiry_date=$(echo | openssl s_client -servername $DOMAIN -connect $DOMAIN:443 2>/dev/null | openssl x509 -noout -enddate | cut -d= -f2)

# Convert to seconds
expiry_epoch=$(date -d "$expiry_date" +%s)
current_epoch=$(date +%s)

# Calculate days remaining
days_remaining=$(( (expiry_epoch - current_epoch) / 86400 ))

echo "Domain: $DOMAIN"
echo "Expires: $expiry_date"
echo "Days remaining: $days_remaining"

if [ $days_remaining -lt $DAYS_WARNING ]; then
    echo "⚠️  WARNING: Certificate expires soon!"
else
    echo "✓ Certificate is valid"
fi
```

---

<div align="center">

## 💡 Best Practices & Pro Tips

</div>

### Shell Script Best Practices 📋

```bash
#!/bin/bash
# ═══════════════════════════════════════════
# 1. Script Header Template
# ═══════════════════════════════════════════

#!/bin/bash
#
# Script Name: backup.sh
# Description: Automated backup system
# Author: MrDib
# Created: 2024-01-01
# Last Modified: 2024-01-15
#
# Usage: ./backup.sh [options]
# Options:
#   -d    Destination directory
#   -s    Source directory
#   -h    Show help
#

set -euo pipefail  # Exit on error, undefined vars, pipe failures
IFS=$'\n\t'        # Better word splitting

# ═══════════════════════════════════════════
# 2. Error Handling
# ═══════════════════════════════════════════

# Trap errors
trap 'error_handler $? $LINENO' ERR

error_handler() {
    local exit_code=$1
    local line_number=$2
    echo "Error on line $line_number: Exit code $exit_code"
    # Cleanup code here
    exit $exit_code
}

# Trap exit
trap cleanup EXIT

cleanup() {
    echo "Cleaning up..."
    # Remove temporary files, etc.
}

# ═══════════════════════════════════════════
# 3. Logging
# ═══════════════════════════════════════════

LOG_FILE="/var/log/script.log"

log() {
    local level=$1
    shift
    local message="$@"
    echo "[$(date +'%Y-%m-%d %H:%M:%S')] [$level] $message" | tee -a "$LOG_FILE"
}

log_info() {
    log "INFO" "$@"
}

log_error() {
    log "ERROR" "$@"
}

log_warning() {
    log "WARNING" "$@"
}

# Usage
log_info "Script started"
log_error "Something went wrong"

# ═══════════════════════════════════════════
# 4. Configuration File
# ═══════════════════════════════════════════

# config.conf
"""
BACKUP_DIR=/home/user/backups
RETENTION_DAYS=7
EMAIL=admin@example.com
"""

# Load configuration
CONFIG_FILE="./config.conf"

if [ -f "$CONFIG_FILE" ]; then
    source "$CONFIG_FILE"
else
    echo "Config file not found: $CONFIG_FILE"
    exit 1
fi

# ═══════════════════════════════════════════
# 5. Input Validation
# ═══════════════════════════════════════════

validate_email() {
    local email=$1
    if [[ $email =~ ^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$ ]]; then
        return 0
    else
        return 1
    fi
}

validate_ip() {
    local ip=$1
    if [[ $ip =~ ^[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}$ ]]; then
        return 0
    else
        return 1
    fi
}

# ═══════════════════════════════════════════
# 6. Check Prerequisites
# ═══════════════════════════════════════════

check_prerequisites() {
    local missing_tools=()

    for tool in git docker node; do
        if ! command -v $tool &> /dev/null; then
            missing_tools+=($tool)
        fi
    done

    if [ ${#missing_tools[@]} -gt 0 ]; then
        echo "Missing required tools: ${missing_tools[*]}"
        echo "Please install them and try again."
        exit 1
    fi
}

# ═══════════════════════════════════════════
# 7. Progress Indicators
# ═══════════════════════════════════════════

spinner() {
    local pid=$1
    local delay=0.1
    local spinstr='|/-\'

    while kill -0 $pid 2>/dev/null; do
        local temp=${spinstr#?}
        printf " [%c]  " "$spinstr"
        spinstr=$temp${spinstr%"$temp"}
        sleep $delay
        printf "\b\b\b\b\b\b"
    done
    printf "    \b\b\b\b"
}

# Usage
long_running_command &
spinner $!

# ═══════════════════════════════════════════
# 8. Colored Output
# ═══════════════════════════════════════════

# Colors
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[0;33m'
BLUE='\033[0;34m'
NC='\033[0m' # No Color

echo -e "${GREEN}✓ Success${NC}"
echo -e "${RED}✗ Error${NC}"
echo -e "${YELLOW}⚠ Warning${NC}"
echo -e "${BLUE}ℹ Info${NC}"

# ═══════════════════════════════════════════
# 9. Dry Run Mode
# ═══════════════════════════════════════════

DRY_RUN=false

execute() {
    local command="$@"

    if [ "$DRY_RUN" = true ]; then
        echo "[DRY RUN] Would execute: $command"
    else
        eval "$command"
    fi
}

# Usage: ./script.sh --dry-run

# ═══════════════════════════════════════════
# 10. Help Function
# ═══════════════════════════════════════════

show_help() {
    cat << EOF
Usage: $0 [OPTIONS]

Description:
    This script does amazing things!

OPTIONS:
    -h, --help          Show this help message
    -v, --version       Show version information
    -d, --directory     Specify directory
    -f, --file          Specify file
    -n, --dry-run       Simulate execution

EXAMPLES:
    $0 -d /path/to/dir
    $0 --file myfile.txt --dry-run

AUTHOR:
    MrDib <mrdib@example.com>
EOF
}

# Check for help flag
if [[ "${1:-}" =~ ^-h|--help$ ]]; then
    show_help
    exit 0
fi
```

---

### Debugging Tips 🐛

```bash
# ═══════════════════════════════════════════
# Debug Mode
# ═══════════════════════════════════════════

# Enable debug output
set -x          # Print commands before execution
bash -x script.sh

# Enable verbose mode
set -v          # Print shell input lines

# Combine options
set -xv

# Disable
set +x
set +v

# ═══════════════════════════════════════════
# ShellCheck - Static Analysis
# ═══════════════════════════════════════════

# Install
brew install shellcheck

# Check script
shellcheck script.sh

# Ignore specific warnings
# shellcheck disable=SC2086
command $var

# ═══════════════════════════════════════════
# Testing
# ═══════════════════════════════════════════

# Use BATS (Bash Automated Testing System)
brew install bats-core

# test.bats
#!/usr/bin/env bats

@test "addition works" {
    result="$(echo 2+2 | bc)"
    [ "$result" -eq 4 ]
}

# Run tests
bats test.bats
```

---

<div align="center">

## 🎓 Resources & Learning

</div>

### Learning Materials 📚

```
📘 Official Documentation
   Bash Manual: https://www.gnu.org/software/bash/manual/
   Advanced Bash-Scripting Guide: https://tldp.org/LDP/abs/html/

📗 Online Resources
   ShellCheck: https://www.shellcheck.net/
   Explain Shell: https://explainshell.com/
   Bash Guide: https://mywiki.wooledge.org/BashGuide

📙 Books
   "The Linux Command Line" by William Shotts
   "Wicked Cool Shell Scripts" by Dave Taylor
   "Learning the bash Shell" by Cameron Newham

🎥 Video Tutorials
   Shell Scripting Tutorial (YouTube)
   Linux Academy
   Udemy Bash Courses

🛠️ Tools
   ShellCheck - Linter
   BATS - Testing framework
   shfmt - Formatter
```

---

<div align="center">

**Built with 🐚 by automation enthusiasts**

_May your scripts be bug-free and your automation be endless!_ 🚀

**Happy Scripting!** ✨

</div>
