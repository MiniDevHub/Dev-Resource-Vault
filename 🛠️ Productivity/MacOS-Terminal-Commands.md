<div align="center">

# 🖥️ macOS Terminal CheatSheet

<img src="https://img.shields.io/badge/macOS-Terminal-black?style=for-the-badge&logo=apple" alt="macOS Terminal">
<img src="https://img.shields.io/badge/Shell-Zsh-green?style=for-the-badge&logo=gnu-bash" alt="Zsh">
<img src="https://img.shields.io/badge/Level-Beginner_to_Pro-blue?style=for-the-badge" alt="All Levels">

### _Your Swiss Army knife for macOS command-line mastery_ ⚡

**Because clicking through Finder is so 2010** 🎯

</div>

---

## 📚 Table of Contents

- [🍎 macOS Essentials](#-macos-essentials)
- [📂 File System Operations](#-file-system-operations)
- [👥 User Management](#-user-management)
- [👨‍👩‍👧‍👦 Group Management](#-group-management)
- [📦 Package Management](#-package-management)
- [🔌 Port Management](#-port-management)
- [🔀 I/O Redirection](#-io-redirection)
- [💡 Pro Tips & Tricks](#-pro-tips--tricks)

---

<div align="center">

## 🍎 macOS Essentials

_The foundation of your terminal superpowers_

</div>

### 🧹 Terminal Housekeeping

```bash
# Clear your terminal window (goodbye clutter!)
clear

# View your command history
cat /Users/<userName>/.zsh_history

# Check your WiFi MAC address
ifconfig en0 | grep ether

# Check your Ethernet MAC address
ifconfig en1 | grep ether

# List all network interfaces
ifconfig | grep ether

# Test your internet speed (built-in!)
networkQuality
```

> **💡 Pro Tip:** Use `Cmd + K` to clear your terminal screen instantly - it's faster than typing `clear`!

### 🚀 Running Multiple Commands

```bash
# Run commands simultaneously (parallel execution)
command1 & command2 & command3

# Run simultaneously but wait for all to finish
command1 & command2 & command3 & wait

# Run only if previous command succeeds (conditional execution)
command1 && command2 && command3

# Run commands one after another (sequential execution)
command1 ; command2 ; command3 ; command4
```

**Example Use Cases:**

```bash
# Update, upgrade, and cleanup simultaneously
brew update & brew upgrade & brew cleanup & wait

# Build only if tests pass
npm test && npm run build

# Multiple git operations in sequence
git add . ; git commit -m "Update" ; git push
```

---

<div align="center">

### ⚙️ <u>System Management Commands</u> ⚙️

| 🔧 Action               | 🖥️ Command                                                      | 📝 Notes                                   |
| ----------------------- | --------------------------------------------------------------- | ------------------------------------------ |
| **Instant Shutdown**    | `sudo shutdown -h now`                                          | Shuts down immediately                     |
| **Scheduled Shutdown**  | `sudo shutdown -h +30`                                          | Shutdown in 30 minutes                     |
| **Instant Reboot**      | `sudo shutdown -r now`                                          | Restarts immediately                       |
| **Alternative Restart** | `sudo reboot`                                                   | Alternative to shutdown -r                 |
| **Logout Current User** | `osascript -e 'tell application "System Events" to log out'`    | Logs out gracefully                        |
| **Sleep System**        | `pmset sleepnow`                                                | Puts Mac to sleep                          |
| **Sleep Display Only**  | `pmset displaysleepnow`                                         | Display sleeps, system stays on            |
| **Lock Screen**         | `pmset displaysleepnow`                                         | Quick screen lock                          |
| **Cancel Shutdown**     | `sudo killall shutdown`                                         | Stop scheduled shutdown                    |
| **Show Uptime**         | `uptime`                                                        | How long system has been running           |
| **Process List**        | `ps aux`                                                        | All running processes                      |
| **Kill a Process**      | `kill -9 <PID>`                                                 | Force quit by Process ID                   |
| **System Monitor**      | `top`                                                           | Real-time system stats (press `q` to quit) |
| **Better Monitor**      | `htop`                                                          | Enhanced top (install via Homebrew)        |
| **Disk Space**          | `df -h`                                                         | Check available disk space                 |
| **List Files**          | `ls -lah`                                                       | Detailed file listing                      |
| **Find a File**         | `find / -name "filename"`                                       | Search entire system                       |
| **Current Directory**   | `pwd`                                                           | Print working directory                    |
| **Network Status**      | `ifconfig`                                                      | Network configuration                      |
| **Alternative Network** | `networksetup -listallhardwareports`                            | Detailed network info                      |
| **Ping Test**           | `ping google.com`                                               | Test internet connectivity                 |
| **Flush DNS**           | `sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder` | Clear DNS cache                            |
| **System Info**         | `system_profiler SPSoftwareDataType`                            | Detailed system information                |

</div>

> **⚠️ Warning:** Commands with `sudo` require admin password. Use with caution - you have the power to break things! 💥

---

<div align="center">

## 🔀 I/O Redirection

_Channel your data like a pro_ 🌊

</div>

### Understanding Redirection Operators

I/O redirection lets you control where your command's input comes from and where its output goes. Think of it as plumbing for your terminal! 🚰

<div align="center">

| Operator | Meaning                                   | Use Case             | Example                      |
| -------- | ----------------------------------------- | -------------------- | ---------------------------- |
| `>`      | Redirect stdout (overwrite)               | Save output to file  | `echo "hi" > file.txt`       |
| `>>`     | Redirect stdout (append)                  | Add to existing file | `echo "hi" >> file.txt`      |
| `<`      | Redirect file input                       | Read from file       | `cat < file.txt`             |
| `2>`     | Redirect stderr (overwrite)               | Save errors only     | `command 2> error.txt`       |
| `2>>`    | Redirect stderr (append)                  | Append errors        | `command 2>> error.txt`      |
| `&>`     | Redirect both stdout & stderr (overwrite) | Capture everything   | `command &> all_output.txt`  |
| `&>>`    | Redirect both stdout & stderr (append)    | Append everything    | `command &>> all_output.txt` |
| `\|`     | Pipe output to next command               | Chain commands       | `ls \| grep "file"`          |
| `<<`     | Here-document (multi-line input)          | Multi-line strings   | `cat << EOF`                 |
| `<<<`    | Here-string (single string input)         | Quick string input   | `grep "hi" <<< "hi there"`   |
| `>&`     | Redirect one descriptor to another        | Combine streams      | `1>&2` (stdout to stderr)    |
| `<&`     | Read from another descriptor              | Input redirection    | `exec 3<&0`                  |

</div>

### Practical Examples

```bash
# Save command output to file (overwrite)
ls -la > directory_contents.txt

# Append to existing file
date >> log.txt

# Save only errors
npm install 2> errors.log

# Save both output and errors
npm run build &> build_log.txt

# Chain commands with pipes
cat file.txt | grep "error" | wc -l  # Count error lines

# Create multi-line input
cat << EOF > config.txt
This is line 1
This is line 2
This is line 3
EOF

# Quick string search
grep "pattern" <<< "string with pattern in it"

# Redirect both stdout and stderr to different files
command > output.txt 2> error.txt

# Discard output (send to void)
command > /dev/null 2>&1  # Silence everything
```

> **💡 Pro Tip:** The `/dev/null` is like a black hole - anything sent there disappears. Perfect for suppressing unwanted output!

---

<div align="center">

## 📂 File System Operations

_Navigate and manipulate files like a terminal ninja_ 🥷

</div>

### 📍 Navigation Commands

```bash
# List files and folders
ls                  # Basic listing
ls -a              # Show hidden files (including .files)
ls -l              # Detailed listing with permissions
ls -al             # Detailed listing with hidden files
ls -l@             # Show extended attributes

# Change directory
cd <folderName>    # Enter a folder
cd                 # Go to home directory (~)
cd ~               # Alternative home
cd /               # Go to root directory
cd ..              # Go up one level
cd .               # Stay in current directory
cd -               # Go to previous directory

# View current location
pwd                # Print working directory
```

**Quick Navigation Examples:**

```bash
cd ~/Documents           # Go to Documents
cd ~/Desktop            # Go to Desktop
cd /Applications        # Go to Applications folder
cd ../..               # Go up two levels
cd ~/Downloads && ls   # Go to Downloads and list files
```

---

### 📝 File & Folder Management

#### Creating Files & Folders

```bash
# Create a new folder
mkdir <folderName>

# Create multiple nested folders
mkdir -p projects/web/frontend/components

# Create a single file
touch <fileName>

# Create multiple files at once
touch file1.txt file2.txt file3.txt

# Create 100 files (1 to 100)
touch file{1..100}.txt

# Create files with specific pattern
touch test_{a,b,c}.js  # Creates: test_a.js, test_b.js, test_c.js
```

---

#### Reading & Writing Files

```bash
# ═══════════════════════════════════════════
# READ FILE CONTENTS
# ═══════════════════════════════════════════

# Display file contents
cat <fileName>

# ═══════════════════════════════════════════
# WRITE TO FILE (Overwrite)
# ═══════════════════════════════════════════

# Method 1: Echo redirect
echo "Hello, World!" > file.txt

# Method 2: Cat redirect (multi-line)
cat > file.txt
# Type your content
# Press Ctrl + C to exit

# Method 3: Using tee
echo "Content" | tee file.txt

# Method 4: Nano editor
nano file.txt
# Write your content
# Press Ctrl + X to exit, Y to save

# Method 5: Printf (formatted output)
printf "Name: %s\nAge: %d\n" "MrDib" 25 > file.txt

# ═══════════════════════════════════════════
# APPEND TO FILE (Add without overwriting)
# ═══════════════════════════════════════════

# Method 1: Echo append
echo "New line" >> file.txt

# Method 2: Cat append
cat >> file.txt
# Type additional content
# Press Ctrl + C to exit

# Method 3: Tee append
echo "More content" | tee -a file.txt

# Method 4: Nano (open and add)
nano file.txt

# Method 5: Printf append
printf "Additional info" >> file.txt

# ═══════════════════════════════════════════
# DELETE FILE CONTENTS (Keep the file)
# ═══════════════════════════════════════════

# Method 1: Simple redirect
> file.txt

# Method 2: Colon redirect
: > file.txt

# Method 3: Truncate command
truncate -s 0 file.txt

# Method 4: Echo nothing
echo -n > file.txt

# Method 5: Null device
cat /dev/null > file.txt
```

> **💡 Pro Tip:** Use `cat` for simple viewing, `less` for large files (navigate with arrow keys, quit with `q`), and `head` or `tail` to see beginning or end of files!

---

#### Renaming & Deleting

```bash
# Rename a file or folder
mv <oldName> <newName>

# Move and rename simultaneously
mv old_file.txt ~/Documents/new_file.txt

# Delete a single file
rm <fileName>

# Delete all files in current directory
rm *

# Delete files matching pattern
rm fileName*              # All files starting with "fileName"
rm *.txt                 # All .txt files
rm test_?.js             # test_1.js, test_a.js, etc.

# Delete a folder (force, recursive)
rm -rf <folderName>

# Delete empty folder only
rmdir <folderName>

# Safe delete (asks for confirmation)
rm -i <fileName>
```

> **⚠️ DANGER ZONE:** `rm -rf` is powerful and permanent! There's no "Recycle Bin" in terminal. Deleted is DELETED! 💀

---

#### Advanced File Operations

```bash
# Open file/folder in Finder
open <file/folderName>

# Open current directory in Finder
open .

# Open file with specific app
open -a "Visual Studio Code" file.txt

# Edit file in nano
nano <fileName>
# Save: Ctrl + O
# Exit: Ctrl + X

# Copy files
cp source.txt destination.txt
cp -r sourceFolder/ destFolder/  # Copy folder recursively

# Move files
mv source.txt ~/Documents/

# Create symbolic link (shortcut)
ln -s /path/to/original /path/to/link

# Find and delete old app files
find ~/Library -iname "*appname*"

# Get file information
stat <fileName>           # Detailed file info
file <fileName>           # File type information
du -h <fileName>          # File size
```

---

<div align="center">

## 👥 User Management

_Master the art of user control_ 👑

</div>

### Switching Users

```bash
# Switch to root user
sudo su root
# Or simply
sudo su

# Switch to any user
su <userName>

# Switch back to previous user
exit
# Or
su <userName>
```

---

### Creating & Managing Users

```bash
# Add a new user
sudo sysadminctl -addUser <userName> -password <passWord>

# Add user with full name
sudo sysadminctl -addUser <userName> -fullName "John Doe" -password <passWord>

# Add user to a group
sudo dseditgroup -o edit -a <userName> -t user <groupName>

# Change user password
sudo passwd <userName>
```

---

### Viewing User Information

```bash
# List all users with UIDs
dscl . list /Users UniqueID

# List only real users (UID >= 501)
dscl . list /Users UniqueID | awk '$2 >= 501 {print $1}'

# See logged-in users
who
who -H          # With headers
who -a          # All information

# View current user info
id

# View specific user info
id <userName>

# Check user's command history (zsh)
cat /Users/<userName>/.zsh_history

# Check user's command history (bash)
cat /home/<userName>/.bash_history
```

---

### Deleting Users (The Nuclear Option 💥)

**Follow these steps carefully to completely remove a user:**

```bash
# ═══════════════════════════════════════════
# Step 1: Check if user is logged in
# ═══════════════════════════════════════════
who

# ═══════════════════════════════════════════
# Step 2: Kill user's processes
# ═══════════════════════════════════════════

# Method 1: Kill all user processes at once
sudo pkill -u <userName>

# Method 2: Nuclear option (more aggressive)
sudo killall -u <userName>

# Method 3: Manual kill (get process IDs first)
ps -u <userName>                    # List user's processes
sudo kill -9 <PID>                  # Kill specific process

# Method 4: Kill terminal sessions
sudo pkill -t pts/1                 # Kill specific terminal

# ═══════════════════════════════════════════
# Step 3: Delete the user
# ═══════════════════════════════════════════

# Basic delete
sudo sysadminctl -deleteUser <userName>

# Delete user + home directory (secure)
sudo sysadminctl -deleteUser <userName> -secure

# Low-level delete (using dscl)
sudo dscl . -delete /Users/<userName>
# Note: This doesn't remove home directory automatically

# ═══════════════════════════════════════════
# Step 4: Find leftover files
# ═══════════════════════════════════════════
sudo find /var/log -type f -exec grep -l <userName> {} +

# ═══════════════════════════════════════════
# Step 5: Delete leftover files
# ═══════════════════════════════════════════

# Delete log files mentioning user
sudo find /var/log -type f -exec grep -l <userName> {} + | sudo xargs rm -f

# Delete home directory (if not already deleted)
sudo rm -rf /Users/<userName>

# Delete mail spool
sudo rm -f /private/var/mail/<userName>

# ═══════════════════════════════════════════
# Step 6: Remove user's groups (if needed)
# ═══════════════════════════════════════════
sudo dseditgroup -o delete <groupName>
```

> **⚠️ CRITICAL WARNING:** User deletion is PERMANENT! Make sure you backup any important data first. There's no undo button! 🚨

---

### User Security

```bash
# Remove user from admin group (revoke admin rights)
sudo dseditgroup -o edit -d <userName> -t user admin

# Disable root account (security best practice)
dsenableroot -d

# Enable root account (not recommended!)
sudo dsenableroot
```

> **💡 Security Tip:** If root is disabled and user isn't in admin group, they cannot become root via any method. This is good for security! 🔒

---

<div align="center">

## 👨‍👩‍👧‍👦 Group Management

_Organize users like a boss_ 🎯

</div>

### Understanding macOS Groups

> **📝 Important Note:** In macOS, there's no `sudo` group. The equivalent is the `admin` group. Users in the `admin` group can use `sudo` commands.

### Viewing Groups

```bash
# Check current user's groups
groups

# List all system groups
dscl . list /Groups

# View legacy group file (compatibility only)
cat /etc/group
# Note: This file is rarely updated in modern macOS

# View specific group details
dscl . -read /Groups/<groupName>

# View group members
dscl . -read /Groups/<groupName> GroupMembership

# Check all groups for a specific user
id <userName>

# List all users in system
dscl . list /Users
```

---

### Creating & Managing Groups

```bash
# Create a new group
sudo dscl . -create /Groups/<groupName>

# Add user to a group
sudo dscl . -append /Groups/<groupName> GroupMembership <userName>

# Remove user from a group
sudo dscl . -delete /Groups/<groupName> GroupMembership <userName>
```

---

### Deleting Groups

```bash
# Method 1: Safe deletion (recommended)
sudo dseditgroup -o delete <groupName>
# This performs internal checks before deletion

# Method 2: Direct deletion
sudo dscl . -delete /Groups/<groupName>
# More direct but less safe
```

---

### Editing sudoers File

```bash
# Edit sudoers file (advanced users only!)
sudo nano /etc/sudoers

# Better: Use visudo (validates syntax)
sudo visudo
```

> **⚠️ WARNING:** Editing `/etc/sudoers` incorrectly can lock you out of sudo! Always use `visudo` which validates your changes. 🛡️

---

<div align="center">

## 📦 Package Management

_Homebrew: The missing package manager for macOS_ 🍺

</div>

### Installing Homebrew

```bash
# Install Homebrew (paste this in terminal)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Verify installation
brew --version
```

**Official Homebrew website:** [https://brew.sh/](https://brew.sh/)

---

### Essential Homebrew Commands

<div align="center">

| Task                     | Command                    | Description                     |
| ------------------------ | -------------------------- | ------------------------------- |
| **Install Package**      | `brew install <package>`   | Install a new package           |
| **Uninstall Package**    | `brew uninstall <package>` | Remove a package                |
| **Update Package List**  | `brew update`              | Update Homebrew & formulae list |
| **Upgrade Packages**     | `brew upgrade`             | Upgrade all installed packages  |
| **Upgrade Specific**     | `brew upgrade <package>`   | Upgrade specific package        |
| **Search Package**       | `brew search <package>`    | Find available packages         |
| **Show Package Info**    | `brew info <package>`      | Detailed package information    |
| **List Installed**       | `brew list`                | Show all installed packages     |
| **Cleanup Old Versions** | `brew cleanup`             | Remove old package versions     |
| **Check System**         | `brew doctor`              | Diagnose brew issues            |
| **Show Dependencies**    | `brew deps <package>`      | Show package dependencies       |
| **Show Dependents**      | `brew uses <package>`      | Show what depends on package    |

</div>

---

### Practical Homebrew Examples

```bash
# Install popular packages
brew install git              # Version control
brew install node             # Node.js runtime
brew install python           # Python 3
brew install wget             # Download utility
brew install htop             # Better process monitor
brew install tree             # Directory tree viewer
brew install tldr             # Simplified man pages

# Install GUI applications (casks)
brew install --cask visual-studio-code
brew install --cask google-chrome
brew install --cask iterm2
brew install --cask docker
brew install --cask postman

# Search for packages
brew search python
brew search /sql/           # Regex search

# Get package information
brew info node
brew info --cask visual-studio-code

# Update everything
brew update && brew upgrade && brew cleanup

# List outdated packages
brew outdated

# Pin package to prevent upgrades
brew pin node               # Prevent node from upgrading
brew unpin node            # Allow upgrades again

# Uninstall package and dependencies
brew uninstall --ignore-dependencies <package>

# Show which formula provides a command
brew which-formula wget
```

---

### Homebrew Maintenance

```bash
# Check for issues
brew doctor

# Clean up old versions (free up space!)
brew cleanup -s             # Cleanup and see space freed

# Remove unnecessary downloads
brew cleanup --prune=all

# Update Homebrew itself
brew update

# Reinstall package (if corrupted)
brew reinstall <package>

# List services
brew services list

# Start/stop services
brew services start postgresql
brew services stop postgresql
brew services restart nginx
```

> **💡 Pro Tip:** Run `brew update && brew upgrade && brew cleanup` weekly to keep your system fresh and clean! 🧹

---

<div align="center">

## 🔌 Port Management

_Taming the port chaos_ 🎯

</div>

### The Port Already in Use Problem

Ever seen this annoying error?

```
❌ Failed listening on port 3000 (tcp), aborting.
```

Don't panic! Here's how to fix it :

---

### Find What's Using a Port

```bash
# Method 1: Using lsof (List Open Files)
lsof -i :<PORT_NUMBER>

# Example: Check what's on port 3000
lsof -i :3000

# Method 2: Using netstat (alternative)
sudo netstat -tulpn | grep <PORT_NUMBER>

# Example: Check port 8080
sudo netstat -tulpn | grep 8080

# Show all listening ports
lsof -iTCP -sTCP:LISTEN -n -P

# Show specific application's ports
lsof -c node              # All ports used by node
```

**Example Output:**

```
COMMAND   PID     USER   FD   TYPE    DEVICE SIZE/OFF NODE NAME
node    12345   mrdib   23u  IPv6  0x123abc      0t0  TCP *:3000 (LISTEN)
```

The `PID` (Process ID) is what you need to kill the process!

---

### Kill Process Using a Port

```bash
# Kill by Process ID (from lsof output)
kill -9 <PID>

# Example: Kill process 12345
kill -9 12345

# One-liner: Find and kill in one command
lsof -ti :<PORT> | xargs kill -9

# Example: Kill everything on port 3000
lsof -ti :3000 | xargs kill -9

# Kill multiple ports at once
lsof -ti :3000,:8080,:5000 | xargs kill -9

# Safer alternative (SIGTERM before SIGKILL)
kill $(lsof -ti :<PORT>)
```

---

### Complete Port Troubleshooting Workflow

```bash
# ═══════════════════════════════════════════
# Step 1: Identify the problem
# ═══════════════════════════════════════════
lsof -i :3000

# ═══════════════════════════════════════════
# Step 2: Kill the process
# ═══════════════════════════════════════════
lsof -ti :3000 | xargs kill -9

# ═══════════════════════════════════════════
# Step 3: Verify port is free
# ═══════════════════════════════════════════
lsof -i :3000
# Should return nothing if port is free

# ═══════════════════════════════════════════
# Step 4: Start your application
# ═══════════════════════════════════════════
npm run dev  # Or whatever command you use
```

---

### Useful Port Aliases (Add to ~/.zshrc)

```bash
# Add these to your shell configuration

# Kill port (usage: killport 3000)
alias killport='function _kp(){ lsof -ti:$1 | xargs kill -9; }; _kp'

# List all listening ports
alias ports='lsof -iTCP -sTCP:LISTEN -n -P'

# Check specific port (usage: checkport 3000)
alias checkport='function _cp(){ lsof -i :$1; }; _cp'

# Kill all node processes
alias killnode='killall -9 node'

# Kill all Python processes
alias killpython='killall -9 python python3'
```

**Usage:**

```bash
# Kill port 3000
killport 3000

# Check what's on port 8080
checkport 8080

# See all listening ports
ports

# Nuclear option: kill all node processes
killnode
```

---

### Common Port Numbers Reference

<div align="center">

| Port  | Common Use  | Typical Application     |
| ----- | ----------- | ----------------------- |
| 80    | HTTP        | Web servers (unsecured) |
| 443   | HTTPS       | Web servers (secured)   |
| 3000  | Development | React, Node.js apps     |
| 3001  | Development | Additional React app    |
| 4200  | Development | Angular apps            |
| 5000  | Development | Flask, Create React App |
| 5173  | Development | Vite dev server         |
| 8000  | Development | Python SimpleHTTPServer |
| 8080  | Development | Alternative web server  |
| 8888  | Development | Jupyter Notebook        |
| 27017 | Database    | MongoDB                 |
| 5432  | Database    | PostgreSQL              |
| 3306  | Database    | MySQL                   |
| 6379  | Database    | Redis                   |

</div>

> **💡 Pro Tip:** Bookmark this section! Port conflicts are one of the most common developer frustrations. Now you're armed with the solution! 🛡️

---

<div align="center">

## 💡 Pro Tips & Tricks

_Level up your terminal game_ 🚀

</div>

### Keyboard Shortcuts (Speed Demons Only ⚡)

```
# Essential macOS Terminal Shortcuts
Ctrl + A          → Move to beginning of line
Ctrl + E          → Move to end of line
Ctrl + U          → Delete from cursor to beginning
Ctrl + K          → Delete from cursor to end
Ctrl + W          → Delete word before cursor
Ctrl + L          → Clear screen (same as 'clear')
Ctrl + R          → Search command history (reverse search)
Ctrl + C          → Cancel current command
Ctrl + D          → Exit terminal / End of file
Ctrl + Z          → Suspend current process
Cmd + K           → Clear terminal (better than Ctrl+L)
Cmd + T           → New tab
Cmd + N           → New window
Cmd + W           → Close tab
Cmd + Q           → Quit terminal
Option + ←/→      → Move word by word
```

---

### Command History Tricks

```bash
# Search history
history | grep "search_term"

# Re-run last command
!!

# Re-run command #n from history
!123

# Re-run last command starting with "git"
!git

# Re-run last command with sudo
sudo !!

# Get argument from previous command
ls -la ~/Documents
cd !$  # !$ = ~/Documents

# Replace text in previous command
^old^new
# Example:
# git comit -m "test"
# ^comit^commit  → runs: git commit -m "test"

# Clear history
history -c
```

---

### Powerful One-Liners

```bash
# Find large files (over 100MB)
find ~ -type f -size +100M -exec ls -lh {} \; | awk '{ print $9 ": " $5 }'

# Count files in directory
find . -type f | wc -l

# Find and delete empty files
find . -type f -empty -delete

# Find files modified in last 7 days
find . -type f -mtime -7

# Disk usage of current directory
du -sh .

# Disk usage of subdirectories
du -sh */

# Top 10 largest folders
du -sh * | sort -rh | head -10

# Watch command output (refresh every 2 seconds)
watch -n 2 'ls -lah'

# Get public IP address
curl ifconfig.me
# Or
curl ipecho.net/plain

# Get local IP
ipconfig getifaddr en0

# Test website response time
curl -o /dev/null -s -w 'Time: %{time_total}s\n' https://google.com

# Download file with progress bar
curl -# -O https://example.com/file.zip

# Batch rename files
for file in *.txt; do mv "$file" "${file%.txt}.md"; done

# Create backup of file
cp file.txt file.txt.backup.$(date +%Y%m%d)

# Archive and compress folder
tar -czf archive.tar.gz folder/

# Extract archive
tar -xzf archive.tar.gz

# Count lines of code in project
find . -name '*.js' | xargs wc -l

# Remove all .DS_Store files (macOS clutter)
find . -name '.DS_Store' -type f -delete

# Generate random password
openssl rand -base64 32

# Check SSL certificate expiry
echo | openssl s_client -servername example.com -connect example.com:443 2>/dev/null | openssl x509 -noout -dates

# Encode/decode Base64
echo "Hello" | base64          # Encode
echo "SGVsbG8K" | base64 -D    # Decode

# Get weather in terminal
curl wttr.in/London

# Get cheat sheet for any command
curl cheat.sh/tar
```

---

### Terminal Customization

```bash
# Add custom prompt (add to ~/.zshrc)
export PS1="%F{cyan}%n@%m%f %F{yellow}%~%f $ "

# Enable color output
export CLICOLOR=1
export LSCOLORS=GxFxCxDxBxegedabagaced

# Better ls output with colors
alias ls='ls -G'
alias ll='ls -lGh'
alias la='ls -lAGh'

# Colorful grep
alias grep='grep --color=auto'
alias fgrep='fgrep --color=auto'
alias egrep='egrep --color=auto'

# Install Oh My Zsh for amazing terminal experience
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Install Powerlevel10k theme (most beautiful terminal theme!)
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
# Then set ZSH_THEME="powerlevel10k/powerlevel10k" in ~/.zshrc
```

---

### The "Oh Shit!" Commands (We've All Been There 😅)

```bash
# ═══════════════════════════════════════════
# "I accidentally deleted everything!"
# ═══════════════════════════════════════════

# Check if files are in Trash (macOS)
ls ~/.Trash/

# Restore from Trash
mv ~/.Trash/important_file.txt ~/Desktop/

# Time Machine restore (if you have backups)
tmutil listbackups
tmutil restore /path/to/backup /path/to/restore

# ═══════════════════════════════════════════
# "My terminal is frozen!"
# ═══════════════════════════════════════════

# Unfreeze terminal
Ctrl + Q

# If that doesn't work, open new terminal and:
ps aux | grep -i terminal
kill -9 <PID>

# ═══════════════════════════════════════════
# "I forgot what I was doing!"
# ═══════════════════════════════════════════

# Show recent commands
history | tail -20

# Show current running processes
ps aux | grep $(whoami)

# Show current working directory
pwd

# ═══════════════════════════════════════════
# "I can't remember that complex command!"
# ═══════════════════════════════════════════

# Search history interactively
Ctrl + R
# Start typing, press Ctrl+R again to cycle through matches

# ═══════════════════════════════════════════
# "I ran a command as wrong user!"
# ═══════════════════════════════════════════

# Fix file ownership
sudo chown -R $(whoami) /path/to/folder

# Fix permissions
chmod -R 755 /path/to/folder

# ═══════════════════════════════════════════
# "My disk is full!"
# ═══════════════════════════════════════════

# Find what's eating space
du -sh ~/Library/*  | sort -rh | head -10
du -sh ~/Downloads/* | sort -rh | head -10

# Clean Homebrew cache
brew cleanup -s

# Clear system caches (requires password)
sudo periodic daily weekly monthly

# Remove old iOS backups
rm -rf ~/Library/Application\ Support/MobileSync/Backup/*

# Clear Xcode derived data (if you're a dev)
rm -rf ~/Library/Developer/Xcode/DerivedData/*

# ═══════════════════════════════════════════
# "I can't remember the syntax!"
# ═══════════════════════════════════════════

# Use tldr (simplified man pages)
brew install tldr
tldr tar
tldr git
tldr docker

# Or use cheat.sh
curl cheat.sh/rsync
curl cheat.sh/ffmpeg

# ═══════════════════════════════════════════
# "This process won't die!"
# ═══════════════════════════════════════════

# Force kill with extreme prejudice
sudo kill -9 <PID>

# Kill by name
sudo killall -9 "Process Name"

# Nuclear option - kill all instances
ps aux | grep process_name | awk '{print $2}' | xargs kill -9
```

---

<div align="center">

## 🔥 Advanced Terminal Wizardry

_For when you want to flex your terminal muscles_ 💪

</div>

### Network Debugging Like a Pro

```bash
# ═══════════════════════════════════════════
# Network Diagnostics
# ═══════════════════════════════════════════

# Trace route to destination
traceroute google.com

# DNS lookup
nslookup google.com
dig google.com

# Test port connectivity
nc -zv google.com 80
telnet google.com 80

# Scan local network for devices
arp -a

# Monitor network activity
sudo tcpdump -i en0

# Watch real-time network connections
lsof -i -P

# Check who's hogging bandwidth
nettop

# Test download speed
curl -o /dev/null http://speedtest.wdc01.softlayer.com/downloads/test100.zip

# Monitor specific interface
ifconfig en0 | grep "inet "

# Flush ARP cache
sudo arp -a -d

# Renew DHCP lease
sudo ipconfig set en0 DHCP

# Check routing table
netstat -nr

# ═══════════════════════════════════════════
# WiFi Diagnostics
# ═══════════════════════════════════════════

# Scan for WiFi networks
/System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport -s

# Get detailed WiFi info
/System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport -I

# Cycle WiFi (off/on)
networksetup -setairportpower en0 off
sleep 2
networksetup -setairportpower en0 on

# Forget WiFi network
sudo /System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport -z

# Create alias for airport command
alias airport='/System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport'
```

---

### File & Data Processing Magic

```bash
# ═══════════════════════════════════════════
# Text Processing Wizardry
# ═══════════════════════════════════════════

# Find and replace in files
find . -type f -name "*.txt" -exec sed -i '' 's/old/new/g' {} +

# Count unique lines
sort file.txt | uniq -c

# Remove duplicate lines
sort file.txt | uniq > unique.txt

# Merge multiple files
cat file1.txt file2.txt file3.txt > merged.txt

# Split file into chunks (1000 lines each)
split -l 1000 largefile.txt chunk_

# Get specific columns from CSV
cut -d',' -f1,3 data.csv

# Search across multiple files
grep -r "search_term" .

# Search with line numbers
grep -n "search_term" file.txt

# Case-insensitive search
grep -i "search_term" file.txt

# Invert search (show lines NOT matching)
grep -v "exclude_term" file.txt

# Count occurrences
grep -c "search_term" file.txt

# Search for multiple patterns
grep -E "pattern1|pattern2|pattern3" file.txt

# ═══════════════════════════════════════════
# JSON Processing (requires jq)
# ═══════════════════════════════════════════

# Install jq
brew install jq

# Pretty print JSON
cat data.json | jq '.'

# Extract specific field
cat data.json | jq '.users[0].name'

# Filter array
cat data.json | jq '.users[] | select(.age > 25)'

# Get all values of a key
cat data.json | jq '.users[].email'

# Count array elements
cat data.json | jq '.users | length'

# ═══════════════════════════════════════════
# CSV Processing
# ═══════════════════════════════════════════

# View CSV with column alignment
column -t -s',' file.csv | less -S

# Get CSV headers
head -1 file.csv

# Skip first line (header)
tail -n +2 file.csv

# Get specific column (1st column)
awk -F',' '{print $1}' file.csv

# Sum a column (2nd column)
awk -F',' '{sum+=$2} END {print sum}' file.csv

# ═══════════════════════════════════════════
# File Comparison
# ═══════════════════════════════════════════

# Compare two files
diff file1.txt file2.txt

# Side-by-side comparison
diff -y file1.txt file2.txt

# Unified diff (like Git)
diff -u file1.txt file2.txt

# Compare directories
diff -r dir1/ dir2/

# Generate patch file
diff -u original.txt modified.txt > changes.patch

# Apply patch
patch original.txt < changes.patch
```

---

### System Monitoring & Performance

```bash
# ═══════════════════════════════════════════
# Resource Monitoring
# ═══════════════════════════════════════════

# CPU usage per process
ps aux | sort -rk 3 | head -10

# Memory usage per process
ps aux | sort -rk 4 | head -10

# Disk I/O statistics
iostat -w 2

# Battery information
pmset -g batt

# Battery time remaining
pmset -g batt | grep -Eo "\d+:\d+"

# Temperature monitoring (requires installation)
sudo powermetrics --samplers smc | grep -i "CPU die temperature"

# Check system logs
log show --predicate 'eventMessage contains "error"' --info --last 1h

# Monitor file changes in real-time
fswatch /path/to/directory

# ═══════════════════════════════════════════
# Disk Management
# ═══════════════════════════════════════════

# Verify disk
diskutil verifyVolume /

# Repair disk permissions
diskutil resetUserPermissions / $(id -u)

# Eject disk
diskutil eject /Volumes/DiskName

# List all disks
diskutil list

# Get disk info
diskutil info /dev/disk0

# Securely erase free space
diskutil secureErase freespace 0 /Volumes/Macintosh\ HD

# Check S.M.A.R.T. status
diskutil info disk0 | grep SMART

# ═══════════════════════════════════════════
# Memory Management
# ═══════════════════════════════════════════

# Purge memory cache (free up RAM)
sudo purge

# Check memory pressure
memory_pressure

# Virtual memory statistics
vm_stat

# Show memory usage
top -l 1 | grep PhysMem
```

---

### Developer Power Tools

```bash
# ═══════════════════════════════════════════
# Git Power Commands
# ═══════════════════════════════════════════

# Undo last commit but keep changes
git reset --soft HEAD~1

# Completely remove last commit
git reset --hard HEAD~1

# Amend commit without changing message
git commit --amend --no-edit

# Interactive rebase last 5 commits
git rebase -i HEAD~5

# Delete all merged branches
git branch --merged | grep -v "\*" | xargs -n 1 git branch -d

# Show files changed in commit
git show --name-only <commit-hash>

# Show commit history as graph
git log --graph --oneline --all --decorate

# Find who changed a specific line
git blame filename.js

# Search commit messages
git log --grep="bug fix"

# Show changes in staged files
git diff --cached

# Temporarily save changes
git stash
git stash pop  # Restore

# Create branch from stash
git stash branch new-branch-name

# Show all stashes
git stash list

# Cherry-pick specific commit
git cherry-pick <commit-hash>

# ═══════════════════════════════════════════
# Docker Quick Commands
# ═══════════════════════════════════════════

# Remove all stopped containers
docker container prune

# Remove all unused images
docker image prune -a

# Remove all unused volumes
docker volume prune

# Nuclear option - clean everything
docker system prune -a --volumes

# Show container resource usage
docker stats

# Execute command in running container
docker exec -it container_name bash

# Copy files to/from container
docker cp container_name:/path/to/file ./local/path
docker cp ./local/file container_name:/path/to/destination

# Save container as image
docker commit container_name new_image_name

# ═══════════════════════════════════════════
# NPM/Node.js Power Tools
# ═══════════════════════════════════════════

# Check for outdated packages
npm outdated

# Update all packages to latest
npx npm-check-updates -u && npm install

# Check package bundle size before installing
npx bundle-phobia [package-name]

# Find duplicate dependencies
npx find-duplicate-dependencies

# Audit security vulnerabilities
npm audit

# Fix vulnerabilities automatically
npm audit fix

# Force fix (may cause breaking changes)
npm audit fix --force

# Clear npm cache
npm cache clean --force

# Check which version is installed
npm list [package-name]

# Run local package binary
npx [package-name]

# ═══════════════════════════════════════════
# Python Virtual Environments
# ═══════════════════════════════════════════

# Create virtual environment
python3 -m venv venv

# Activate virtual environment
source venv/bin/activate

# Deactivate virtual environment
deactivate

# Install packages from requirements
pip install -r requirements.txt

# Generate requirements file
pip freeze > requirements.txt

# List installed packages
pip list

# Show package details
pip show package-name

# Uninstall package
pip uninstall package-name

# ═══════════════════════════════════════════
# SSL/Certificate Management
# ═══════════════════════════════════════════

# Generate self-signed certificate
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes

# Check certificate details
openssl x509 -in certificate.crt -text -noout

# Convert PEM to DER
openssl x509 -outform der -in certificate.pem -out certificate.der

# Test SSL connection
openssl s_client -connect example.com:443

# Check certificate expiration
echo | openssl s_client -servername example.com -connect example.com:443 2>/dev/null | openssl x509 -noout -dates
```

---

### Fun & Quirky Commands (Because Why Not? 🎉)

```bash
# ═══════════════════════════════════════════
# Easter Eggs & Fun Stuff
# ═══════════════════════════════════════════

# Make your Mac say something
say "Hello, I am your Mac"
say -v Samantha "I prefer this voice"
say -v Zarvox "I am a robot"

# List all available voices
say -v ?

# Create audio file from text
say -o output.aiff "This will be saved as audio"

# Matrix effect in terminal
brew install cmatrix
cmatrix

# ASCII art
brew install figlet
figlet "Hello World"

# More ASCII art
brew install toilet
toilet -f mono12 -F metal "Cool Text"

# Fortune cookies
brew install fortune
fortune

# Cowsay (because why not?)
brew install cowsay
cowsay "Moo!"

# Cowsay with fortune
fortune | cowsay

# Different cow files
cowsay -l  # List all cows
cowsay -f dragon "I am a dragon"
cowsay -f tux "I use Linux... wait, this is macOS"

# Terminal rickroll
curl -s -L https://raw.githubusercontent.com/keroserene/rickrollrc/master/roll.sh | bash

# Screensaver in terminal
brew install asciiquarium
asciiquarium

# Watch Star Wars in terminal
telnet towel.blinkenlights.nl

# Random quote
curl -s https://api.quotable.io/random | jq -r '.content'

# Dad joke API
curl -H "Accept: application/json" https://icanhazdadjoke.com/

# Cat facts
curl -s https://catfact.ninja/fact | jq -r '.fact'

# Yes or No decision
curl -s https://yesno.wtf/api | jq -r '.answer'

# ═══════════════════════════════════════════
# Terminal Pranks (Use Responsibly! 😈)
# ═══════════════════════════════════════════

# Make terminal speak every command
# Add to ~/.zshrc
precmd() { say -v Zarvox "Command completed" }

# Fake hacking screen
brew install hollywood
hollywood

# Matrix screen saver
brew install cmatrix
cmatrix -b

# Random git commit message generator
curl -s http://whatthecommit.com/index.txt

# Useless but satisfying
yes "I am awesome"

# Infinite loop (Ctrl+C to stop)
while true; do echo "Looping..."; sleep 1; done

# ═══════════════════════════════════════════
# Productivity Fun
# ═══════════════════════════════════════════

# Pomodoro timer (25 minutes)
sleep 1500 && say "Take a break"

# Custom countdown
countdown() { date1=$((`date +%s` + $1)); while [ "$date1" -ge `date +%s` ]; do echo -ne "$(date -u --date @$(($date1 - `date +%s`)) +%H:%M:%S)\r"; sleep 0.1; done; say "Time is up!"; }
# Usage: countdown 300  (for 5 minutes)

# Coffee break reminder
alias coffeebreak='sleep 3600 && say "Time for coffee!"'

# End of day reminder
alias endofday='echo "Remember to: git commit, close apps, backup work" | say'
```

---

<div align="center">

## 🎓 Learning Resources & Next Steps

_Keep improving your terminal game!_ 📚

</div>

### Essential Reading

```
📖 The Linux Command Line (William Shotts)
   - Free online: https://linuxcommand.org/tlcl.php
   - Foundation for all Unix-based systems

📖 Advanced Bash-Scripting Guide
   - https://tldp.org/LDP/abs/html/
   - Deep dive into shell scripting

📖 Explain Shell
   - https://explainshell.com
   - Breaks down any command

📖 DevHints
   - https://devhints.io
   - Quick reference cheat sheets

📖 TLDR Pages
   - https://tldr.sh
   - Simplified man pages
```

---

### Video Tutorials

```
🎥 NetworkChuck (YouTube)
   - Fun networking & Linux tutorials
   - https://youtube.com/@NetworkChuck

🎥 The Net Ninja (YouTube)
   - Developer-focused tutorials
   - https://youtube.com/@NetNinja

🎥 Fireship (YouTube)
   - Quick tech overviews
   - https://youtube.com/@Fireship

🎥 Corey Schafer (YouTube)
   - In-depth programming tutorials
   - https://youtube.com/@coreyms
```

---

### Practice Platforms

```
🏋️ OverTheWire: Bandit
   - Learn Linux through challenges
   - https://overthewire.org/wargames/bandit/

🏋️ CMD Challenge
   - Test your command-line skills
   - https://cmdchallenge.com

🏋️ Linux Survival
   - Interactive Linux tutorial
   - https://linuxsurvival.com
```

---

<div align="center">

## 🎯 Final Pro Tips

_The wisdom that took years to learn_ 🧙‍♂️

</div>

### The 10 Commandments of Terminal Usage

1. **Always backup before using `rm -rf`** - There is no undo! 🗑️
2. **Use tab completion** - Let the terminal do the typing 🎹
3. **Read error messages** - They usually tell you what's wrong 📖
4. **Google the error** - Someone has had this problem before 🔍
5. **Use `man` pages** - `man command` is your friend 📚
6. **Test on test data first** - Don't practice surgery on yourself 🧪
7. **Use version control** - Git saves lives (and careers) 💾
8. **Automate repetitive tasks** - Scripts are your servants 🤖
9. **Keep learning** - The terminal is deep 🌊
10. **Have fun!** - It's not work if you enjoy it 🎉

---

### Creating Your Perfect Terminal Setup

```bash
# ═══════════════════════════════════════════
# Ultimate .zshrc Setup
# ═══════════════════════════════════════════

# Open your .zshrc
nano ~/.zshrc

# Add these essential configurations:

# ─────────────────────────────────────────
# 1. Oh My Zsh (if installed)
# ─────────────────────────────────────────
export ZSH="$HOME/.oh-my-zsh"
ZSH_THEME="powerlevel10k/powerlevel10k"
plugins=(
  git
  zsh-autosuggestions
  zsh-syntax-highlighting
  docker
  npm
  node
  vscode
)
source $ZSH/oh-my-zsh.sh

# ─────────────────────────────────────────
# 2. Useful Aliases
# ─────────────────────────────────────────
alias zshconfig="code ~/.zshrc"
alias reload="source ~/.zshrc"

# Navigation
alias ..="cd .."
alias ...="cd ../.."
alias ....="cd ../../.."
alias ~="cd ~"
alias -- -="cd -"

# Better ls
alias ll="ls -lah"
alias la="ls -A"
alias l="ls -CF"

# Git shortcuts
alias g="git"
alias gs="git status"
alias ga="git add"
alias gc="git commit -m"
alias gp="git push"
alias gpl="git pull"
alias gco="git checkout"
alias gcb="git checkout -b"
alias gl="git log --oneline --graph --all"

# NPM shortcuts
alias ni="npm install"
alias nid="npm install -D"
alias nrd="npm run dev"
alias nrb="npm run build"
alias nrs="npm run start"
alias nrt="npm run test"

# Utilities
alias killport='function _kp(){ lsof -ti:$1 | xargs kill -9; }; _kp'
alias myip="curl ifconfig.me"
alias localip="ipconfig getifaddr en0"
alias ports="lsof -iTCP -sTCP:LISTEN -n -P"

# Fun stuff
alias shrug="echo '¯\_(ツ)_/¯' | pbcopy"
alias please="sudo"
alias pls="sudo"

# ─────────────────────────────────────────
# 3. Useful Functions
# ─────────────────────────────────────────

# Make directory and cd into it
mkcd() {
  mkdir -p "$1" && cd "$1"
}

# Extract any archive
extract() {
  if [ -f $1 ]; then
    case $1 in
      *.tar.bz2)   tar xjf $1     ;;
      *.tar.gz)    tar xzf $1     ;;
      *.bz2)       bunzip2 $1     ;;
      *.rar)       unrar e $1     ;;
      *.gz)        gunzip $1      ;;
      *.tar)       tar xf $1      ;;
      *.tbz2)      tar xjf $1     ;;
      *.tgz)       tar xzf $1     ;;
      *.zip)       unzip $1       ;;
      *.Z)         uncompress $1  ;;
      *.7z)        7z x $1        ;;
      *)           echo "'$1' cannot be extracted via extract()" ;;
    esac
  else
    echo "'$1' is not a valid file"
  fi
}

# Find and kill process by name
killprocess() {
  ps aux | grep -i $1 | awk '{print $2}' | xargs kill -9
}

# Weather in terminal
weather() {
  curl wttr.in/${1:-}
}

# ─────────────────────────────────────────
# 4. Environment Variables
# ─────────────────────────────────────────
export EDITOR="code"
export VISUAL="code"
export TERM="xterm-256color"

# ─────────────────────────────────────────
# 5. Path additions
# ─────────────────────────────────────────
export PATH="/usr/local/bin:$PATH"
export PATH="$HOME/.local/bin:$PATH"

# ─────────────────────────────────────────
# 6. Optional: Custom greeting
# ─────────────────────────────────────────
echo "🚀 Welcome back, $(whoami)!"
echo "📅 Today is $(date '+%A, %B %d, %Y')"
echo "💻 System: $(uname -s) $(uname -r)"
echo ""

# Save and reload
# source ~/.zshrc
```

---

<div align="center">

## 🏆 Congratulations!

_You've reached the end of the macOS Terminal CheatSheet!_ 🎉

</div>

**You're now armed with:**

- ✅ Essential macOS commands
- ✅ File system mastery
- ✅ User & group management
- ✅ Network debugging skills
- ✅ Developer power tools
- ✅ Pro tips & tricks
- ✅ Advanced wizardry

### Keep This Handy!

Bookmark this page, share it with friends, and most importantly - **practice, practice, practice!** 💪

The terminal might seem intimidating at first, but with these tools and tricks, you're well on your way to becoming a command-line master. 🧙‍♂️

---

<div align="center">

### Remember

> "With great terminal power comes great responsibility... and the ability to accidentally delete everything with one command. So be careful!" 😅

</div>

---

### Useful Links

🔗 [Homebrew Documentation](https://docs.brew.sh)<br>
🔗 [Zsh Documentation](https://zsh.sourceforge.io/Doc/)<br>
🔗 [Oh My Zsh](https://ohmyz.sh)<br>
🔗 [Powerlevel10k Theme](https://github.com/romkatv/powerlevel10k)<br>
🔗 [Explain Shell](https://explainshell.com)<br>
🔗 [TLDR Pages](https://tldr.sh)

---

<div align="center">

**Built with 💚 by developers, for developers**

_Now go forth and conquer that terminal!_ 🚀

**Happy Command-Line Adventures!** ⚡

**If you found this helpful, give it a ⭐ star and share with fellow developers!**

</div>
