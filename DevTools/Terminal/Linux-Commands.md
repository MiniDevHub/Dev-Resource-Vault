<div align="center">

# 🐧 Linux Terminal CheatSheet

<img src="https://img.shields.io/badge/Linux-Terminal-yellow?style=for-the-badge&logo=linux" alt="Linux Terminal">
<img src="https://img.shields.io/badge/Shell-Bash-green?style=for-the-badge&logo=gnu-bash" alt="Bash">
<img src="https://img.shields.io/badge/Level-Beginner_to_Advanced-blue?style=for-the-badge" alt="All Levels">

### _Your complete guide to mastering the Linux command line_ 🚀

**From zero to hero in the terminal** 💪

</div>

---

## 📚 Table of Contents

- [🐧 Linux Essentials](#-linux-essentials)
- [📂 File System Operations](#-file-system-operations)
- [👥 User & Permission Management](#-user--permission-management)
- [📦 Package Management](#-package-management)
- [🔌 Process & Service Management](#-process--service-management)
- [🌐 Networking](#-networking)
- [🔍 Text Processing](#-text-processing)
- [💡 Pro Tips & Power Commands](#-pro-tips--power-commands)

---

<div align="center">

## 🐧 Linux Essentials

</div>

### Basic Commands 🎯

```bash
# ═══════════════════════════════════════════
# System Information
# ═══════════════════════════════════════════

# Display system information
uname -a                    # All system info
uname -r                    # Kernel version
uname -m                    # Machine hardware name

# Distribution information
cat /etc/os-release         # OS details
lsb_release -a             # Distribution info (if available)

# Hostname
hostname                    # Display hostname
hostnamectl                # Detailed hostname info

# Current date and time
date                       # Current date/time
timedatectl                # Detailed time/date info

# System uptime
uptime                     # How long system has been running
uptime -p                  # Pretty format

# Who is logged in
who                        # Show logged-in users
w                          # Who with more details
whoami                     # Current username
id                         # User ID and groups

# ═══════════════════════════════════════════
# Clear & Reset Terminal
# ═══════════════════════════════════════════

clear                      # Clear screen (Ctrl+L)
reset                      # Reset terminal

# ═══════════════════════════════════════════
# Command History
# ═══════════════════════════════════════════

history                    # Show command history
history 10                 # Last 10 commands
history | grep "search"    # Search in history
!!                         # Run last command
!n                         # Run command number n
!string                    # Run last command starting with string
history -c                 # Clear history

# ═══════════════════════════════════════════
# Getting Help
# ═══════════════════════════════════════════

man command               # Manual page for command
man -k keyword           # Search man pages
info command             # Info documentation
command --help           # Command help
whatis command           # Brief description
apropos keyword          # Search command descriptions
```

---

<div align="center">

## 📂 File System Operations

</div>

### Navigation 🗺️

```bash
# ═══════════════════════════════════════════
# Directory Navigation
# ═══════════════════════════════════════════

pwd                        # Print working directory
cd /path/to/directory     # Change directory
cd ~                       # Go to home directory
cd -                       # Go to previous directory
cd ..                      # Go up one level
cd ../..                   # Go up two levels

# ═══════════════════════════════════════════
# Listing Files & Directories
# ═══════════════════════════════════════════

ls                         # List files
ls -l                      # Long format (detailed)
ls -la                     # Include hidden files
ls -lh                     # Human-readable sizes
ls -ltr                    # Sort by time (newest last)
ls -lS                     # Sort by size
ls -R                      # Recursive listing
ls -d */                   # List only directories

# ═══════════════════════════════════════════
# File Information
# ═══════════════════════════════════════════

file filename             # Determine file type
stat filename             # Detailed file stats
du -h filename            # File size
du -sh directory          # Directory size
du -sh *                  # Size of all items
df -h                     # Disk space usage
tree                      # Directory tree (install tree package)
tree -L 2                 # Limit depth to 2 levels
```

---

### File Operations 📝

```bash
# ═══════════════════════════════════════════
# Creating Files & Directories
# ═══════════════════════════════════════════

touch filename            # Create empty file
touch file1 file2 file3   # Create multiple files
mkdir directory           # Create directory
mkdir -p path/to/dir      # Create nested directories

# ═══════════════════════════════════════════
# Copying Files & Directories
# ═══════════════════════════════════════════

cp source dest            # Copy file
cp -r source dest         # Copy directory recursively
cp -i source dest         # Interactive (prompt before overwrite)
cp -u source dest         # Copy only if source is newer
cp -v source dest         # Verbose output
cp -p source dest         # Preserve permissions/timestamps

# ═══════════════════════════════════════════
# Moving & Renaming
# ═══════════════════════════════════════════

mv source dest            # Move or rename
mv -i source dest         # Interactive mode
mv -n source dest         # Don't overwrite existing
mv -v source dest         # Verbose output

# ═══════════════════════════════════════════
# Deleting Files & Directories
# ═══════════════════════════════════════════

rm filename               # Remove file
rm -r directory           # Remove directory recursively
rm -rf directory          # Force remove (⚠️ DANGEROUS!)
rm -i filename            # Interactive mode (safer)
rmdir directory           # Remove empty directory

# ═══════════════════════════════════════════
# Reading Files
# ═══════════════════════════════════════════

cat filename              # Display entire file
cat file1 file2           # Concatenate files
tac filename              # Display in reverse
head filename             # First 10 lines
head -n 5 filename        # First 5 lines
tail filename             # Last 10 lines
tail -n 20 filename       # Last 20 lines
tail -f filename          # Follow file (real-time updates)
less filename             # Paginated viewing (q to quit)
more filename             # Simple pager

# ═══════════════════════════════════════════
# Creating/Editing Files
# ═══════════════════════════════════════════

echo "text" > file        # Overwrite file
echo "text" >> file       # Append to file
cat > file                # Write to file (Ctrl+D to save)
cat >> file               # Append to file (Ctrl+D to save)

# Editors
nano filename             # Simple editor
vim filename              # Vim editor
vi filename               # Vi editor

# ═══════════════════════════════════════════
# Finding Files
# ═══════════════════════════════════════════

find /path -name "*.txt"              # Find by name
find . -name "file*"                  # Wildcard search
find . -type f                        # Find files only
find . -type d                        # Find directories only
find . -size +10M                     # Files larger than 10MB
find . -mtime -7                      # Modified in last 7 days
find . -user username                 # Find by owner
find . -name "*.log" -delete          # Find and delete

# Locate (faster, uses database)
locate filename                       # Quick search
sudo updatedb                         # Update locate database

# Which (find command location)
which python                          # Find Python executable
whereis python                        # Find binary, source, manual

# ═══════════════════════════════════════════
# Links (Shortcuts)
# ═══════════════════════════════════════════

ln -s target linkname     # Create symbolic link (soft link)
ln target linkname        # Create hard link
readlink linkname         # Show link target
unlink linkname           # Remove link
```

---

<div align="center">

## 👥 User & Permission Management

</div>

### User Management 👤

```bash
# ═══════════════════════════════════════════
# User Information
# ═══════════════════════════════════════════

whoami                    # Current username
id                        # User ID and group IDs
id username               # Info for specific user
groups                    # Show current user's groups
groups username           # Show user's groups

# ═══════════════════════════════════════════
# User Management (requires root/sudo)
# ═══════════════════════════════════════════

# Add user
sudo adduser username                 # Interactive user creation
sudo useradd username                 # Basic user creation
sudo useradd -m -s /bin/bash username # With home dir & shell

# Modify user
sudo usermod -aG groupname username   # Add user to group
sudo usermod -l newname oldname       # Rename user
sudo usermod -d /new/home username    # Change home directory

# Delete user
sudo deluser username                 # Remove user
sudo userdel username                 # Remove user
sudo userdel -r username              # Remove user + home dir

# Password management
passwd                    # Change your password
sudo passwd username      # Change user's password

# Switch user
su username              # Switch to user
su -                     # Switch to root
sudo -i                  # Interactive root shell
sudo -s                  # Root shell
sudo command             # Run command as root

# ═══════════════════════════════════════════
# Group Management
# ═══════════════════════════════════════════

# Create group
sudo groupadd groupname              # Create new group

# Modify group
sudo groupmod -n newname oldname     # Rename group

# Delete group
sudo groupdel groupname              # Delete group

# View groups
cat /etc/group                       # All groups
getent group                         # List all groups
```

---

### File Permissions 🔐

```bash
# ═══════════════════════════════════════════
# Understanding Permissions
# ═══════════════════════════════════════════

# Format: -rwxrwxrwx
# Position: -|owner|group|others
# r = read (4)
# w = write (2)
# x = execute (1)

# Example: -rw-r--r--
# - = file (d = directory, l = link)
# rw- = owner can read/write
# r-- = group can read
# r-- = others can read

# ═══════════════════════════════════════════
# Change Permissions (chmod)
# ═══════════════════════════════════════════

# Symbolic mode
chmod u+x file            # Add execute for user
chmod g+w file            # Add write for group
chmod o-r file            # Remove read for others
chmod a+x file            # Add execute for all
chmod u+rwx file          # Add all permissions for user

# Numeric mode
chmod 755 file            # rwxr-xr-x
chmod 644 file            # rw-r--r--
chmod 777 file            # rwxrwxrwx (⚠️ not recommended!)
chmod 600 file            # rw------- (private file)
chmod 700 directory       # rwx------ (private directory)

# Recursive
chmod -R 755 directory    # Apply to all contents

# Common permission patterns
chmod 755 script.sh       # Executable script
chmod 644 document.txt    # Regular file
chmod 700 ~/.ssh          # SSH directory
chmod 600 ~/.ssh/id_rsa   # SSH private key

# ═══════════════════════════════════════════
# Change Ownership (chown)
# ═══════════════════════════════════════════

sudo chown user file              # Change owner
sudo chown user:group file        # Change owner and group
sudo chown -R user directory      # Recursive
sudo chown :group file            # Change group only

# ═══════════════════════════════════════════
# Change Group (chgrp)
# ═══════════════════════════════════════════

sudo chgrp group file             # Change group
sudo chgrp -R group directory     # Recursive

# ═══════════════════════════════════════════
# Special Permissions
# ═══════════════════════════════════════════

# SUID (Set User ID) - 4000
chmod u+s file            # Run as file owner
chmod 4755 file           # Numeric

# SGID (Set Group ID) - 2000
chmod g+s directory       # Inherit group
chmod 2755 directory      # Numeric

# Sticky Bit - 1000 (only owner can delete)
chmod +t directory        # Sticky bit
chmod 1755 directory      # Numeric

# View special permissions
ls -l file                # Look for 's' or 't'
```

---

<div align="center">

## 📦 Package Management

</div>

### Debian/Ubuntu (APT) 📦

```bash
# ═══════════════════════════════════════════
# APT Commands
# ═══════════════════════════════════════════

# Update package list
sudo apt update                      # Refresh package list

# Upgrade packages
sudo apt upgrade                     # Upgrade all packages
sudo apt full-upgrade                # Upgrade + handle dependencies

# Install packages
sudo apt install package             # Install single package
sudo apt install pkg1 pkg2 pkg3      # Install multiple
sudo apt install -y package          # Auto-yes to prompts

# Remove packages
sudo apt remove package              # Remove package
sudo apt purge package               # Remove package + config
sudo apt autoremove                  # Remove unused dependencies

# Search packages
apt search keyword                   # Search packages
apt show package                     # Show package info

# List packages
apt list --installed                 # All installed packages
apt list --upgradable               # Upgradable packages

# Clean up
sudo apt clean                       # Clear downloaded packages
sudo apt autoclean                   # Clear old packages

# Fix broken dependencies
sudo apt --fix-broken install
sudo dpkg --configure -a

# ═══════════════════════════════════════════
# Essential Packages
# ═══════════════════════════════════════════

sudo apt install curl wget           # Download tools
sudo apt install git                 # Version control
sudo apt install vim nano            # Text editors
sudo apt install htop                # System monitor
sudo apt install tree                # Directory tree
sudo apt install build-essential     # Compiler tools
sudo apt install net-tools           # Network tools
sudo apt install python3-pip         # Python package manager
```

---

### Red Hat/CentOS/Fedora (YUM/DNF) 📦

```bash
# ═══════════════════════════════════════════
# YUM Commands (RHEL 7, CentOS 7)
# ═══════════════════════════════════════════

sudo yum update                      # Update all packages
sudo yum install package             # Install package
sudo yum remove package              # Remove package
sudo yum search keyword              # Search packages
sudo yum info package                # Package information
sudo yum list installed              # List installed
sudo yum clean all                   # Clean cache

# ═══════════════════════════════════════════
# DNF Commands (RHEL 8+, Fedora, CentOS 8+)
# ═══════════════════════════════════════════

sudo dnf update                      # Update all packages
sudo dnf install package             # Install package
sudo dnf remove package              # Remove package
sudo dnf search keyword              # Search packages
sudo dnf info package                # Package information
sudo dnf list installed              # List installed
sudo dnf clean all                   # Clean cache
```

---

### Arch Linux (Pacman) 📦

```bash
# ═══════════════════════════════════════════
# Pacman Commands
# ═══════════════════════════════════════════

sudo pacman -Syu                     # Update system
sudo pacman -S package               # Install package
sudo pacman -R package               # Remove package
sudo pacman -Rns package             # Remove + dependencies
sudo pacman -Ss keyword              # Search packages
sudo pacman -Si package              # Package info
sudo pacman -Q                       # List installed
sudo pacman -Sc                      # Clean cache
```

---

<div align="center">

## 🔌 Process & Service Management

</div>

### Process Management 🔄

```bash
# ═══════════════════════════════════════════
# Viewing Processes
# ═══════════════════════════════════════════

ps                        # Current user processes
ps aux                    # All processes
ps aux | grep process     # Search processes
top                       # Real-time process viewer
htop                      # Better top (install first)
pstree                    # Process tree

# ═══════════════════════════════════════════
# Process Information
# ═══════════════════════════════════════════

pgrep process_name        # Find process ID by name
pidof process_name        # Find PID
ps -p PID                 # Info for specific PID

# ═══════════════════════════════════════════
# Killing Processes
# ═══════════════════════════════════════════

kill PID                  # Terminate process (SIGTERM)
kill -9 PID               # Force kill (SIGKILL)
kill -15 PID              # Graceful termination
killall process_name      # Kill all by name
pkill process_name        # Kill by pattern
pkill -u username         # Kill all user processes

# ═══════════════════════════════════════════
# Background & Foreground Jobs
# ═══════════════════════════════════════════

command &                 # Run in background
jobs                      # List background jobs
fg %1                     # Bring job 1 to foreground
bg %1                     # Continue job 1 in background
Ctrl+Z                    # Suspend current job
Ctrl+C                    # Kill current job

# ═══════════════════════════════════════════
# Nice & Renice (Priority)
# ═══════════════════════════════════════════

nice -n 10 command        # Run with lower priority
renice -n 5 -p PID        # Change priority
# Priority range: -20 (highest) to 19 (lowest)

# ═══════════════════════════════════════════
# nohup (No Hangup)
# ═══════════════════════════════════════════

nohup command &           # Run immune to hangups
nohup command > output.log 2>&1 &
```

---

### Service Management (systemd) ⚙️

```bash
# ═══════════════════════════════════════════
# Service Control
# ═══════════════════════════════════════════

# Start/Stop/Restart
sudo systemctl start service          # Start service
sudo systemctl stop service           # Stop service
sudo systemctl restart service        # Restart service
sudo systemctl reload service         # Reload config

# Status & Info
systemctl status service              # Service status
systemctl is-active service           # Check if active
systemctl is-enabled service          # Check if enabled

# Enable/Disable
sudo systemctl enable service         # Enable at boot
sudo systemctl disable service        # Disable at boot
sudo systemctl enable --now service   # Enable + start

# List services
systemctl list-units --type=service   # All services
systemctl list-units --state=running  # Running services
systemctl list-unit-files            # All unit files

# ═══════════════════════════════════════════
# Common Services
# ═══════════════════════════════════════════

sudo systemctl status ssh             # SSH service
sudo systemctl status apache2         # Apache
sudo systemctl status nginx           # Nginx
sudo systemctl status mysql           # MySQL
sudo systemctl status postgresql      # PostgreSQL
sudo systemctl status docker          # Docker

# ═══════════════════════════════════════════
# System Control
# ═══════════════════════════════════════════

sudo systemctl reboot                 # Reboot system
sudo systemctl poweroff               # Shutdown
sudo systemctl suspend                # Suspend
sudo systemctl hibernate              # Hibernate
```

---

<div align="center">

## 🌐 Networking

</div>

### Network Configuration 🔧

```bash
# ═══════════════════════════════════════════
# Network Interfaces
# ═══════════════════════════════════════════

# View interfaces
ip addr                   # Show all interfaces
ip addr show eth0         # Show specific interface
ifconfig                  # Legacy command (install net-tools)
ip link show              # Show link status

# Interface up/down
sudo ip link set eth0 up       # Bring interface up
sudo ip link set eth0 down     # Bring interface down

# ═══════════════════════════════════════════
# IP Configuration
# ═══════════════════════════════════════════

# Show IP address
hostname -I               # All IP addresses
ip addr show | grep inet  # IPv4 addresses

# Set IP (temporary)
sudo ip addr add 192.168.1.100/24 dev eth0
sudo ip addr del 192.168.1.100/24 dev eth0

# ═══════════════════════════════════════════
# Routing
# ═══════════════════════════════════════════

ip route                  # Show routing table
ip route show             # Same as above
route -n                  # Legacy command

# Add/delete route
sudo ip route add 192.168.2.0/24 via 192.168.1.1
sudo ip route del 192.168.2.0/24

# Default gateway
ip route show default     # Show default gateway
sudo ip route add default via 192.168.1.1

# ═══════════════════════════════════════════
# DNS Configuration
# ═══════════════════════════════════════════

cat /etc/resolv.conf      # DNS servers
resolvectl status         # DNS status (systemd-resolved)
nslookup domain.com       # DNS lookup
dig domain.com            # Detailed DNS query
host domain.com           # Simple DNS lookup
```

---

### Network Testing 🧪

```bash
# ═══════════════════════════════════════════
# Connectivity Testing
# ═══════════════════════════════════════════

# Ping
ping google.com           # Test connectivity
ping -c 4 google.com      # Send 4 packets
ping -i 2 google.com      # Interval 2 seconds

# Traceroute
traceroute google.com     # Trace route to host
tracepath google.com      # Alternative (no root needed)

# MTR (My Traceroute)
mtr google.com            # Combined ping + traceroute

# ═══════════════════════════════════════════
# Port & Service Testing
# ═══════════════════════════════════════════

# Netcat
nc -zv host 80            # Test TCP port
nc -zvu host 53           # Test UDP port
nc -l 8080                # Listen on port 8080

# Telnet
telnet host 80            # Connect to port

# Netstat
netstat -tuln             # All listening ports
netstat -tulnp            # With program names (needs root)
netstat -an               # All connections

# SS (socket statistics)
ss -tuln                  # Listening TCP/UDP
ss -tulnp                 # With process info
ss -s                     # Summary statistics

# Lsof (list open files)
sudo lsof -i              # All network connections
sudo lsof -i :80          # What's using port 80
sudo lsof -i TCP:22       # SSH connections

# ═══════════════════════════════════════════
# Network Performance
# ═══════════════════════════════════════════

# Bandwidth measurement
iperf3 -s                 # Server mode
iperf3 -c server_ip       # Client mode

# Speed test
curl -s https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py | python3 -

# Network statistics
ifstat                    # Interface statistics
nload                     # Bandwidth monitoring
iftop                     # Network usage by connection

# ═══════════════════════════════════════════
# Downloading Files
# ═══════════════════════════════════════════

# wget
wget url                  # Download file
wget -O filename url      # Save as filename
wget -c url               # Resume download
wget -r url               # Recursive download

# curl
curl url                  # Display content
curl -O url               # Download file
curl -o filename url      # Save as filename
curl -L url               # Follow redirects
curl -I url               # Headers only

# ═══════════════════════════════════════════
# Firewall (UFW)
# ═══════════════════════════════════════════

sudo ufw status           # Check status
sudo ufw enable           # Enable firewall
sudo ufw disable          # Disable firewall
sudo ufw allow 80         # Allow port 80
sudo ufw allow ssh        # Allow SSH
sudo ufw deny 80          # Deny port 80
sudo ufw delete allow 80  # Delete rule
sudo ufw reset            # Reset to defaults
```

---

<div align="center">

## 🔍 Text Processing

</div>

### Text Manipulation 📝

```bash
# ═══════════════════════════════════════════
# Searching Text (grep)
# ═══════════════════════════════════════════

grep "pattern" file               # Search in file
grep -i "pattern" file            # Case-insensitive
grep -r "pattern" directory       # Recursive search
grep -v "pattern" file            # Invert match
grep -n "pattern" file            # Show line numbers
grep -c "pattern" file            # Count matches
grep -l "pattern" files*          # Show filenames only
grep -w "word" file               # Match whole word
grep -A 3 "pattern" file          # Show 3 lines after
grep -B 3 "pattern" file          # Show 3 lines before
grep -C 3 "pattern" file          # Show 3 lines around
grep -E "regex" file              # Extended regex
grep -P "regex" file              # Perl regex

# ═══════════════════════════════════════════
# Stream Editor (sed)
# ═══════════════════════════════════════════

sed 's/old/new/' file             # Replace first occurrence
sed 's/old/new/g' file            # Replace all occurrences
sed -i 's/old/new/g' file         # Replace in-place
sed '2d' file                     # Delete line 2
sed '2,5d' file                   # Delete lines 2-5
sed -n '2,5p' file                # Print lines 2-5
sed '2s/old/new/' file            # Replace in line 2

# ═══════════════════════════════════════════
# Text Processing (awk)
# ═══════════════════════════════════════════

awk '{print $1}' file             # Print first column
awk '{print $1,$3}' file          # Print columns 1 and 3
awk -F: '{print $1}' /etc/passwd  # Custom delimiter
awk 'NR==2' file                  # Print line 2
awk 'NR>=2 && NR<=5' file         # Print lines 2-5
awk '{sum+=$1} END {print sum}'   # Sum first column

# ═══════════════════════════════════════════
# Sorting & Uniqueness
# ═══════════════════════════════════════════

sort file                         # Sort lines
sort -r file                      # Reverse sort
sort -n file                      # Numeric sort
sort -k2 file                     # Sort by column 2
sort -u file                      # Sort + remove duplicates
uniq file                         # Remove adjacent duplicates
uniq -c file                      # Count occurrences
uniq -d file                      # Show duplicates only

# ═══════════════════════════════════════════
# Counting
# ═══════════════════════════════════════════

wc file                           # Lines, words, bytes
wc -l file                        # Count lines
wc -w file                        # Count words
wc -c file                        # Count bytes
wc -m file                        # Count characters

# ═══════════════════════════════════════════
# Column Operations
# ═══════════════════════════════════════════

cut -d: -f1 /etc/passwd           # Cut by delimiter
cut -c1-10 file                   # Cut characters 1-10
paste file1 file2                 # Merge lines side-by-side
join file1 file2                  # Join files by common field

# ═══════════════════════════════════════════
# Comparison
# ═══════════════════════════════════════════

diff file1 file2                  # Show differences
diff -u file1 file2               # Unified format
comm file1 file2                  # Compare sorted files
cmp file1 file2                   # Binary comparison

# ═══════════════════════════════════════════
# Translation (tr)
# ═══════════════════════════════════════════

tr 'a-z' 'A-Z' < file             # Lowercase to uppercase
tr -d '0-9' < file                # Delete digits
tr -s ' ' < file                  # Squeeze spaces
```

---

<div align="center">

## 💡 Pro Tips & Power Commands

</div>

### Advanced Techniques 🚀

```bash
# ═══════════════════════════════════════════
# I/O Redirection
# ═══════════════════════════════════════════

command > file                    # Redirect stdout (overwrite)
command >> file                   # Redirect stdout (append)
command 2> file                   # Redirect stderr
command 2>&1                      # Redirect stderr to stdout
command &> file                   # Redirect both stdout & stderr
command < file                    # Input from file
command1 | command2               # Pipe output

# ═══════════════════════════════════════════
# Command Chaining
# ═══════════════════════════════════════════

command1 && command2              # Run command2 if command1 succeeds
command1 || command2              # Run command2 if command1 fails
command1 ; command2               # Run sequentially
command1 & command2 &             # Run in parallel

# ═══════════════════════════════════════════
# Command Substitution
# ═══════════════════════════════════════════

echo "Today is $(date)"           # Modern syntax
echo "Today is `date`"            # Legacy syntax
files=$(ls)                       # Store output in variable

# ═══════════════════════════════════════════
# Keyboard Shortcuts
# ═══════════════════════════════════════════

Ctrl+C                            # Kill current process
Ctrl+Z                            # Suspend process
Ctrl+D                            # Exit / EOF
Ctrl+L                            # Clear screen
Ctrl+A                            # Move to line beginning
Ctrl+E                            # Move to line end
Ctrl+U                            # Cut from cursor to beginning
Ctrl+K                            # Cut from cursor to end
Ctrl+W                            # Cut word before cursor
Ctrl+Y                            # Paste
Ctrl+R                            # Reverse search history
Ctrl+G                            # Cancel search

# ═══════════════════════════════════════════
# Aliases (add to ~/.bashrc)
# ═══════════════════════════════════════════

alias ll='ls -lah'
alias la='ls -A'
alias l='ls -CF'
alias ..='cd ..'
alias ...='cd ../..'
alias gs='git status'
alias gp='git push'
alias ports='netstat -tulanp'
alias update='sudo apt update && sudo apt upgrade'

# ═══════════════════════════════════════════
# One-Liners Power Commands
# ═══════════════════════════════════════════

# Find large files
find / -type f -size +100M 2>/dev/null

# Find and delete empty files
find . -type f -empty -delete

# Count files in directory
find . -type f | wc -l

# Disk usage by directory
du -sh */ | sort -rh | head -10

# Monitor log file
tail -f /var/log/syslog

# Watch command (refresh every 2 seconds)
watch -n 2 'df -h'

# Quick HTTP server (Python)
python3 -m http.server 8000

# Compress directory
tar -czf archive.tar.gz directory/

# Extract archive
tar -xzf archive.tar.gz

# Generate random password
openssl rand -base64 32

# Show directory tree
tree -L 2 -h

# Monitor system resources
watch -n 1 'free -h && df -h'

# Find duplicate files
fdupes -r directory/

# Batch rename files
rename 's/old/new/' *.txt

# Quick backup
rsync -av --progress source/ destination/

# ═══════════════════════════════════════════
# SSH & Remote
# ═══════════════════════════════════════════

# SSH connection
ssh user@host

# SSH with port
ssh -p 2222 user@host

# SSH with key
ssh -i ~/.ssh/key.pem user@host

# Copy file to remote (SCP)
scp file user@host:/path

# Copy directory
scp -r directory user@host:/path

# Copy from remote
scp user@host:/path/file .

# Rsync (better than scp)
rsync -avz source/ user@host:/destination/

# SSH config (~/.ssh/config)
Host myserver
    HostName 192.168.1.100
    User admin
    Port 22
    IdentityFile ~/.ssh/key.pem

# Then simply:
ssh myserver

# ═══════════════════════════════════════════
# System Monitoring
# ═══════════════════════════════════════════

# CPU info
lscpu
cat /proc/cpuinfo

# Memory info
free -h
cat /proc/meminfo

# Disk info
lsblk
fdisk -l

# Hardware info
lshw -short
dmidecode

# PCI devices
lspci

# USB devices
lsusb

# System logs
journalctl -xe                    # Recent logs
journalctl -u service             # Service logs
journalctl -f                     # Follow logs
dmesg                             # Kernel messages
tail -f /var/log/syslog           # System log
```

---

### Emergency & Troubleshooting 🚨

```bash
# ═══════════════════════════════════════════
# System Recovery
# ═══════════════════════════════════════════

# Disk check
sudo fsck /dev/sda1               # Check filesystem
sudo e2fsck -f /dev/sda1          # Force check

# Fix broken packages (Debian/Ubuntu)
sudo apt --fix-broken install
sudo dpkg --configure -a

# Reset password (from recovery mode)
passwd username

# Check system integrity
sudo debsums -c                   # Debian/Ubuntu
rpm -Va                           # RHEL/CentOS

# ═══════════════════════════════════════════
# Performance Issues
# ═══════════════════════════════════════════

# Find high CPU processes
top -o %CPU

# Find high memory processes
top -o %MEM

# I/O statistics
iostat -x 2

# Disk I/O by process
sudo iotop

# ═══════════════════════════════════════════
# Network Issues
# ═══════════════════════════════════════════

# Test DNS
nslookup google.com
dig google.com

# Flush DNS cache
sudo systemd-resolve --flush-caches

# Reset network
sudo systemctl restart NetworkManager

# Check listening ports
sudo netstat -tulnp

# ═══════════════════════════════════════════
# Disk Full Issues
# ═══════════════════════════════════════════

# Find large files
sudo du -h / | sort -rh | head -20

# Find large directories
sudo du -sh /* | sort -rh

# Clean package cache
sudo apt clean                    # Debian/Ubuntu
sudo dnf clean all                # Fedora/RHEL

# Clean logs
sudo journalctl --vacuum-time=3d  # Keep only 3 days

# Find deleted but open files
sudo lsof | grep deleted
```

---

<div align="center">

## 🎓 Resources & Learning

</div>

### Learning Platforms 📚

```
📘 Official Documentation
   man pages - Built-in
   info pages - Built-in

📗 Online Resources
   Linux Journey: https://linuxjourney.com/
   Linux Command: https://linuxcommand.org/
   Explain Shell: https://explainshell.com/
   TLDR Pages: https://tldr.sh/

📙 Books
   "The Linux Command Line" by William Shotts
   "Unix and Linux System Administration Handbook"
   "Linux Pocket Guide" by Daniel J. Barrett

🎥 Video Tutorials
   NetworkChuck (YouTube)
   LearnLinuxTV (YouTube)
   Linux Survival: https://linuxsurvival.com/

🏋️ Practice
   OverTheWire Bandit: https://overthewire.org/wargames/bandit/
   Linux Basics: https://www.hackerrank.com/domains/linux-shell
```

---

<div align="center">

**Built with 🐧 by the Linux community**

_Happy Linux Adventures!_ 🚀

**May your terminals be green and your servers be stable!** ✨

</div>
