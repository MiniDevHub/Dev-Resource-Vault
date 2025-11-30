<div align="center">

# 🚀 Modern CLI Tools for Terminal Ninjas

### _Because life's too short for slow commands and ugly output_ ⚡

![CLI](https://img.shields.io/badge/CLI-Powerful-blue?style=for-the-badge)
![Rust](https://img.shields.io/badge/Rust-Blazing%20Fast-orange?style=for-the-badge)

</div>

---

<div align="center">

## 📚 Table of Contents

</div>

- [📂 Smarter Navigation](#-smarter-navigation)
- [📦 App Management](#-app-management)
- [🔍 Search & Find](#-search--find)
- [🖥️ Terminal Multiplexer](#️-terminal-multiplexer)
- [🗄️ Data Processing](#️-data-processing)
- [☁️ Cloud & DevOps](#️-cloud--devops)
- [🔐 Security & Secrets](#-security--secrets)
- [🔧 System Utilities](#-system-utilities)
- [📊 System Monitoring](#-system-monitoring)
- [🌐 Network Tools](#-network-tools)
- [💾 Disk & Storage](#-disk--storage)
- [🎨 Pretty Output](#-pretty-output)
- [⚡ Shell Enhancement](#-shell-enhancement)
- [💡 MrDib's CLI Philosophy](#-mrdibs-cli-philosophy)

---

<div align="center">

## 📂 Smarter Navigation

</div>

### 📂 Zoxide

**A smarter, faster `cd` command that uses your directory-jumping history to let you instantly jump to frequently or recently used folders with fuzzy matching (e.g., `z project`).**

```
🌐 Website → https://github.com/ajeetdsouza/zoxide
📦 Install  → brew install zoxide
⚡ Speed    → Jump to directories with fragments
```

#### 📥 Installation & Setup

```bash
# Installation
brew install zoxide

# Add Zoxide Path to zshrc:
# Open zshrc file
nano ~/.zshrc

# Add this line to make Zoxide commands available globally
# Zoxide Path
eval "$(zoxide init zsh)"

# Note: You can also add:
# eval "$(zoxide init --cmd cd zsh)"
# in Zshrc to fully replace "cd" with "z"
# In this way "cd" command actually becomes "z"

# Save and reload
source ~/.zshrc
```

#### 📘 Basic Zoxide Commands

```bash
# Get Help
zoxide --help

# Navigate to a Folder
z Projects
z ~/.zshrc
z ..

# Return to Home Directory
z

# Return to Previous Directory
z -

# View Zoxide history
# Way 01
zoxide query -l -s | less

# Way 02
zoxide query -l -s

# Navigate to folder, already navigated in history
# Suppose there is a folder Docx in Apple/Bro/Code/Docx
# With cd we have to give full path :
cd /home/Bro/Code/Docx

# But with z we have to give fragments :
z home Docx

# But for this to work, the path to Docx must be visited at least once with z
# i.e. Must be present in history

# Query Command : Helps to search in Zoxide database
zoxide query Docx

# List Score of result
zoxide query Docx -s

# List all entries
zoxide query -sl

# Delete entries from database of Zoxide
zoxide remove /home/Bro/Code/Docx

# Edit Zoxide database
zoxide edit
```

#### 📜 Zoxide Rules

1.  **The search term is case insensitive:**

    ```bash
    # These two commands are the same:
    z Projects
    z projects
    ```

2.  **All of the terms provided, must be contained within the path in the same order:**

    ```bash
    # Suppose there is a folder Docx in /home/Bro/Code/Docx

    # This command will match:
    z home Docx

    # This command will not match:
    z Docx home
    ```

3.  **The last component of the last keyword must match with the last component of the path:**

    ```bash
    # Suppose there is a folder Docx in home/Bro/Code/Docx

    # This command will match:
    z home Docx

    # This command will not match:
    z home Code
    ```

4.  **All matches are returned in the descending order of their weights:**

    ```bash
    # Suppose in history ( zoxide query -l -s | less ) it shows two Docx
    # 10.0 /home/abcd/Docx
    # 2.0 /home/Apple/Code/Docx

    # Now, if "z Docx" command is used, it will choose:
    /home/abcd/Docx
    ```

    This rule is called **frecency**: https://github.com/ajeetdsouza/zoxide/wiki/Algorithm#matching

---

### 🧲 fzf

**A blazing-fast fuzzy finder for your terminal that lets you interactively search through files, commands, processes, git commits, history, and more with instant fuzzy matching as you type.**

```
🌐 Website → https://github.com/junegunn/fzf
📦 Install  → brew install fzf
✨ Power    → Interactive fuzzy search for anything
```

#### 📥 Installation & Setup

```bash
# Installation
brew install fzf

# Run the install script (adds keybindings and completions)
$(brew --prefix)/opt/fzf/install
```

#### 📘 Basic fzf Commands

```bash
# List Folders (then type to search)
fzf

# Use with Zoxide (Shortcut for history)
zi
# Then use arrows (↓ & ↑) to navigate.
# Then Enter (⏎) to go inside that folder.

# Note: Use "cdi" if z is replaced with cd.

# Open file in editor
vim $(fzf)
code $(fzf)

# Preview files while searching
fzf --preview 'bat --color=always {}'

# Search with multi-select
fzf -m

# Search command history (Ctrl+R is default keybinding after install)
history | fzf

# Search and cd into directory
cd $(find * -type d | fzf)

# Kill process interactively
kill -9 $(ps aux | fzf | awk '{print $2}')
```

#### 🚀 Advanced fzf Usage

```bash
# Use with fd for better file searching
fd --type f | fzf --preview 'bat --color=always {}'

# Git branch checkout with preview
git branch | fzf --preview 'git log --oneline --graph --color=always {}'

# Search and open in vim with preview
vim $(fd --type f | fzf --preview 'bat --color=always --line-range :500 {}')

# Interactive process killer with preview
ps aux | fzf --header-lines=1 --preview 'echo {}' --preview-window down:3:wrap | awk '{print $2}' | xargs kill

# Docker container selection
docker ps | fzf --header-lines=1 | awk '{print $1}' | xargs docker exec -it

# Ripgrep integration (search file content)
rg --line-number . | fzf --delimiter : --preview 'bat --color=always --highlight-line {2} {1}'
```

#### 💡 Environment Variables for fzf

Add to `~/.zshrc`:

```bash
# Use fd instead of find
export FZF_DEFAULT_COMMAND='fd --type f --hidden --follow --exclude .git'
export FZF_CTRL_T_COMMAND="$FZF_DEFAULT_COMMAND"

# Preview with bat
export FZF_CTRL_T_OPTS="--preview 'bat --color=always --line-range :500 {}'"

# Better colors
export FZF_DEFAULT_OPTS='--height 40% --layout=reverse --border --color=fg:#f8f8f2,bg:#282a36,hl:#bd93f9'
```

---

<div align="center">

## 📦 App Management

</div>

### 🛒 mas

**A command-line interface for the Mac App Store that lets you search for, install, update, and manage App Store apps directly from your terminal.**

```
🌐 Website → https://github.com/mas-cli/mas
📦 Install  → brew install mas
🍎 Power    → Manage macOS App Store apps from CLI
```

#### 📥 Installation & Setup

```bash
# Installation
brew install mas
```

#### 📘 Basic mas Commands

```bash
# Get Help
mas --help

# Show AppStore installed apps
mas list

# Show apps need to upgrade
mas outdated

# Upgrade all apps
mas upgrade

# Search for an app
mas search "Xcode"

# Install an app by ID (e.g., Xcode ID is 497799835)
mas install 497799835

# Sign in (may not work with 2FA)
mas signin user@example.com

# Show account info
mas account
```

---

<div align="center">

## 🔍 Search & Find

</div>

### 🦇 bat

**A modern, enhanced replacement for `cat` that adds syntax highlighting, Git integration, line numbers, and a beautiful output format for viewing files in the terminal.**

```
🌐 Website → https://github.com/sharkdp/bat
📦 Install  → brew install bat
✨ Power    → Pretty printing files with syntax highlighting
```

#### 📥 Installation & Setup

```bash
# Installation
brew install bat
```

#### 📘 Basic bat Commands

```bash
# View a file
bat file.txt

# Show line numbers
bat -n file.txt

# Show plain output (no highlighting, no paging)
bat --plain file.txt

# Use bat as a drop-in replacement for cat
bat --paging=never file.txt

# Highlight a specific language (auto-detection is usually good)
bat --language=json config.json

# View a specific range of lines
bat --line-range 10:20 file.txt

# Show non-printable characters
bat -A file.txt

# Show Git changes in the margin
bat --diff file.txt

# Combine multiple files
bat file1.txt file2.txt

# Use with pipes
curl -s https://api.github.com/users/defunkt | bat -l json
```

#### 🎨 Create Aliases

Add to `~/.zshrc`:

```bash
alias cat='bat --paging=never'
alias less='bat'
```

---

### 🦀 ripgrep (rg)

**A blazing-fast grep replacement written in Rust**

```
🌐 Website → https://github.com/BurntSushi/ripgrep
📦 Install  → brew install ripgrep
⚡ Speed    → 5-10x faster than grep
```

**Why ripgrep?**

- Respects `.gitignore` by default
- Automatic encoding detection
- Smart case searching
- Parallel directory traversal
- Beautiful colored output

#### 📥 Installation

```bash
# macOS
brew install ripgrep

# Ubuntu/Debian
sudo apt install ripgrep

# Fedora
sudo dnf install ripgrep

# Arch Linux
sudo pacman -S ripgrep

# From source
cargo install ripgrep
```

#### 📘 Basic Usage

```bash
# Simple search
rg "pattern"

# Search in specific directory
rg "pattern" /path/to/dir

# Case-sensitive search
rg -s "Pattern"

# Case-insensitive search
rg -i "pattern"

# Search specific file types
rg -t py "import"        # Python files only
rg -t js "function"      # JavaScript files only
rg -T md "text"          # Exclude markdown files

# Show line numbers (default)
rg -n "pattern"

# Show context (lines before/after)
rg -A 3 "pattern"        # 3 lines after
rg -B 2 "pattern"        # 2 lines before
rg -C 2 "pattern"        # 2 lines before AND after
```

#### 🔥 Advanced Usage

```bash
# Search hidden files and directories
rg -. "pattern"          # Include hidden
rg --hidden "pattern"    # Same as above

# Include ignored files (.gitignore)
rg -u "pattern"          # -u once = don't respect .gitignore
rg -uu "pattern"         # -u twice = also search hidden files
rg -uuu "pattern"        # -u thrice = search binary files too

# Glob patterns
rg -g '*.js' "pattern"        # Only .js files
rg -g '!*.min.js' "pattern"   # Exclude .min.js files
rg -g '*.{js,ts}' "pattern"   # Multiple extensions

# Fixed string search (no regex)
rg -F "function()"       # Literal search

# Word boundary search
rg -w "word"             # Match whole words only

# Multiline search
rg -U "pattern.*\n.*pattern"

# Count matches
rg -c "pattern"          # Count per file

# List files with matches
rg -l "pattern"          # Just filenames

# List files without matches
rg --files-without-match "pattern"

# Search compressed files
rg -z "pattern" archive.gz
```

#### 🎨 Search & Replace

```bash
# Preview replacements
rg "old" -r "new"

# Replace in files (macOS)
rg "old" --files-with-matches | xargs sed -i '' 's/old/new/g'

# Replace in files (Linux)
rg "old" --files-with-matches | xargs sed -i 's/old/new/g'
```

#### 🚀 Power User Tips

```bash
# Combine with other tools
rg "TODO" -l | xargs wc -l              # Count lines in files with TODO
rg "error" --json | jq '.data.lines'     # JSON output with jq

# Create aliases (add to ~/.zshrc)
alias rgi='rg -i'                        # Case-insensitive by default
alias rgf='rg --files | rg'              # Search filenames
alias rgh='rg --hidden'                  # Include hidden files

# Search only in git tracked files
rg "pattern" $(git ls-files)

# Exclude directories
rg "pattern" -g '!node_modules/*' -g '!.git/*'

# Show file types
rg --type-list

# Add custom file types
rg --type-add 'web:*.{html,css,js}' -tweb "pattern"
```

#### 💡 Common Workflows

```bash
# Find all TODO comments in code
rg "TODO|FIXME|HACK|XXX" -i

# Find function definitions
rg "^(function|def|fn)\s+\w+"

# Find imports/requires
rg "^(import|require|from)\s+"

# Find console.log/print statements
rg "console\.log|print\(" -t js -t py

# Search for IP addresses
rg "\b\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}\b"

# Find email addresses
rg "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b"

# Find environment variables
rg "process\.env\.|os\.getenv"

# Find hardcoded passwords (dangerous!)
rg -i "password\s*=\s*['\"](?!.*\{|\$)"
```

---

### 📂 fd

**A simple, fast, and user-friendly alternative to `find`**

```
🌐 Website → https://github.com/sharkdp/fd
📦 Install  → brew install fd
⚡ Speed    → 9x faster than find
```

**Why fd?**

- Intuitive syntax (no more `-iname '*pattern*'`)
- Respects `.gitignore` by default
- Smart case search
- Colored output
- Parallel execution
- 50% shorter name than `find` 😄

#### 📥 Installation

```bash
# macOS
brew install fd

# Ubuntu/Debian (may be fd-find)
sudo apt install fd-find
# Create alias if needed
alias fd='fdfind'

# Fedora
sudo dnf install fd-find

# Arch Linux
sudo pacman -S fd

# From source
cargo install fd-find
```

#### 📘 Basic Usage

```bash
# Simple search (finds anything with "pattern" in name)
fd pattern

# Search in specific directory
fd pattern /path/to/dir

# Case-sensitive search
fd -s Pattern

# Case-insensitive search
fd -i pattern

# Search by extension
fd -e js                     # All .js files
fd -e md -e txt              # Multiple extensions

# Search specific file types
fd -t f pattern              # Files only
fd -t d pattern              # Directories only
fd -t l pattern              # Symlinks only
fd -t x pattern              # Executable files only
```

#### 🔥 Advanced Usage

```bash
# Include hidden files
fd -H pattern

# Include ignored files (.gitignore)
fd -I pattern

# Include both hidden and ignored
fd -HI pattern

# Follow symbolic links
fd -L pattern

# Exact match (glob pattern)
fd -g '*.js'                 # All .js files
fd -g 'test*.py'             # test*.py files

# Exclude patterns
fd -E node_modules -E .git pattern

# Limit search depth
fd -d 2 pattern              # Max depth of 2 directories

# Search by size
fd -S +10m                   # Files larger than 10MB
fd -S -1k                    # Files smaller than 1KB

# Search by modification time
fd --changed-within 1d       # Changed in last day
fd --changed-within 2w       # Changed in last 2 weeks
fd --changed-before '2024-01-01'  # Before specific date

# Search by owner
fd --owner john pattern
```

#### 🎯 Execute Commands on Results

```bash
# Execute command for each result (-x)
fd -e jpg -x convert {} {.}.png

# Execute command with all results at once (-X)
fd -e log -X tar -czf logs.tar.gz

# Use placeholders:
# {} = full path (e.g., src/app.js)
# {/} = basename (e.g., app.js)
# {//} = parent directory (e.g., src)
# {.} = without extension (e.g., src/app)
# {/.} = basename without extension (e.g., app)

# Examples
fd -e txt -x mv {} {}_backup.txt           # Backup files
fd -e jpg -x exiftool -Title={/.} {}       # Set EXIF title
fd -t d -x chmod 755 {}                    # Change permissions
fd -t f -S +100m -x du -h {}               # Show size of large files
```

#### 🚀 Power User Tips

```bash
# Combine with other tools
fd -e js | xargs wc -l                     # Count lines in JS files
fd -e md | fzf                             # Fuzzy find markdown files
fd -t f | head -20 | xargs bat             # View first 20 files

# Create aliases (add to ~/.zshrc)
alias fdd='fd -t d'                        # Directories only
alias fdf='fd -t f'                        # Files only
alias fde='fd -t x'                        # Executables only
alias fda='fd -HI'                         # All files (hidden + ignored)

# Search and delete
fd -H '^\.DS_Store$' -tf -X rm             # Delete .DS_Store files
fd 'node_modules' -td -X rm -rf            # Delete node_modules dirs

# Integration with fzf for file selection
export FZF_DEFAULT_COMMAND='fd --type f --hidden --follow --exclude .git'
export FZF_CTRL_T_COMMAND="$FZF_DEFAULT_COMMAND"

# Preview files with bat
fd -e js | fzf --preview 'bat --color=always {}'

# Find and move files
fd -e log -x mv {} /backup/
```

#### 💡 Common Workflows

```bash
# Find large files
fd -t f -S +100m

# Find recently modified files
fd -t f --changed-within 1h

# Find empty files or directories
fd -t f -S 0                               # Empty files

# Find broken symlinks
fd -t l -x bash -c 'if [ ! -e {} ]; then echo {}; fi'

# Clean build artifacts
fd -H -I '(\.pyc|\.pyo|__pycache__|\.DS_Store)' -X rm -rf

# Find duplicate filenames
fd -t f | rev | cut -d'/' -f1 | rev | sort | uniq -d

# List all files modified today
fd -t f --changed-within 1d -x ls -lh

# Find files with specific permissions
fd -t f -x bash -c 'if [ "$(stat -f %A {})" = "755" ]; then echo {}; fi'
```

---

<div align="center">

## 🖥️ Terminal Multiplexer

</div>

### 🪟 tmux

**Terminal multiplexer - manage multiple terminal sessions like a boss**

```
🌐 Website → https://github.com/tmux/tmux
📦 Install  → brew install tmux
💪 Power    → Persistent sessions + window management
```

**Why tmux?**

- Persistent sessions (survive SSH disconnects)
- Multiple windows and panes
- Session sharing for pair programming
- Fully scriptable
- Highly customizable

#### 📥 Installation

```bash
# macOS
brew install tmux

# Ubuntu/Debian
sudo apt install tmux

# Fedora
sudo dnf install tmux

# Arch Linux
sudo pacman -S tmux
```

#### 🎯 Core Concepts

```
📊 Hierarchy:
   Session  →  Contains multiple windows (like workspaces)
      ↓
   Window   →  Like browser tabs (one at a time visible)
      ↓
   Pane     →  Split sections within a window (all visible)
```

#### 📘 Basic Session Management

**Default Prefix Key:** `Ctrl+b` (referred to as `<prefix>` below)

```bash
# Start new session
tmux

# Start named session
tmux new -s myproject

# List sessions
tmux ls

# Attach to session
tmux attach -t myproject
tmux a -t myproject          # Short form

# Attach to last session
tmux a

# Kill session
tmux kill-session -t myproject

# Kill all sessions
tmux kill-server
```

#### ⌨️ Essential Keybindings

**Session Management:**

```bash
<prefix> d              # Detach from session
<prefix> s              # List and switch sessions
<prefix> $              # Rename current session
<prefix> (              # Switch to previous session
<prefix> )              # Switch to next session
```

**Window Management:**

```bash
<prefix> c              # Create new window
<prefix> ,              # Rename current window
<prefix> &              # Kill current window
<prefix> n              # Next window
<prefix> p              # Previous window
<prefix> 0-9            # Switch to window by number
<prefix> w              # List windows
<prefix> f              # Find window by name
```

**Pane Management:**

```bash
<prefix> %              # Split pane vertically (left|right)
<prefix> "              # Split pane horizontally (top/bottom)
<prefix> arrow keys     # Navigate between panes
<prefix> o              # Switch to next pane
<prefix> ;              # Toggle between last two panes
<prefix> x              # Kill current pane
<prefix> z              # Toggle pane zoom (fullscreen)
<prefix> space          # Toggle between pane layouts
<prefix> {              # Move pane left
<prefix> }              # Move pane right
<prefix> Ctrl+arrow     # Resize pane (hold Ctrl)
<prefix> Alt+arrow      # Resize pane (5 cells at a time)
```

**Copy Mode (for scrolling/copying):**

```bash
<prefix> [              # Enter copy mode
q                       # Exit copy mode
Space                   # Start selection (in copy mode)
Enter                   # Copy selection
<prefix> ]              # Paste buffer
/                       # Search forward (in copy mode)
?                       # Search backward (in copy mode)
```

**Other Useful Commands:**

```bash
<prefix> ?              # Show all keybindings
<prefix> :              # Enter command mode
<prefix> t              # Show clock
<prefix> =              # List all paste buffers
```

#### 🔧 Configuration

Create `~/.tmux.conf`:

```bash
# ═══════════════════════════════════════════
# General Settings
# ═══════════════════════════════════════════

# Change prefix from Ctrl+b to Ctrl+a (more ergonomic)
unbind C-b
set -g prefix C-a
bind C-a send-prefix

# Enable mouse support
set -g mouse on

# Start window numbering at 1 (not 0)
set -g base-index 1
setw -g pane-base-index 1

# Renumber windows when one is closed
set -g renumber-windows on

# Increase scrollback buffer
set -g history-limit 10000

# Better colors
set -g default-terminal "screen-256color"

# No delay for escape key press
set -sg escape-time 0

# ═══════════════════════════════════════════
# Status Bar Styling
# ═══════════════════════════════════════════

# Status bar position
set -g status-position top

# Status bar colors
set -g status-style 'bg=#1e1e2e,fg=#cdd6f4'

# Left side of status bar
set -g status-left-length 20
set -g status-left '#[fg=#89b4fa,bold]❐ #S #[fg=#45475a]│ '

# Right side of status bar
set -g status-right '#[fg=#a6e3a1]%Y-%m-%d #[fg=#45475a]│ #[fg=#f9e2af]%H:%M'

# Window status
setw -g window-status-format '#[fg=#6c7086] #I:#W '
setw -g window-status-current-format '#[fg=#89b4fa,bold] #I:#W '

# ═══════════════════════════════════════════
# Pane Borders
# ═══════════════════════════════════════════

set -g pane-border-style 'fg=#45475a'
set -g pane-active-border-style 'fg=#89b4fa'

# ═══════════════════════════════════════════
# Custom Keybindings
# ═══════════════════════════════════════════

# Easier pane splitting
bind | split-window -h -c "#{pane_current_path}"
bind - split-window -v -c "#{pane_current_path}"

# Reload config
bind r source-file ~/.tmux.conf \; display "Config reloaded!"

# Vim-style pane navigation
bind h select-pane -L
bind j select-pane -D
bind k select-pane -U
bind l select-pane -R

# Vim-style copy mode
setw -g mode-keys vi
bind -T copy-mode-vi v send-keys -X begin-selection
bind -T copy-mode-vi y send-keys -X copy-selection-and-cancel

# Open new windows/panes in current directory
bind c new-window -c "#{pane_current_path}"

# Kill pane without confirmation
bind x kill-pane

# Synchronize panes (type in all at once)
bind S setw synchronize-panes
```

Apply config:

```bash
# Inside tmux
<prefix> :source-file ~/.tmux.conf
# Or
<prefix> r   # If you added the bind above
```

#### 🚀 Advanced Usage

**Scripted Session Creation:**

Create `~/tmux-dev.sh`:

```bash
#!/bin/bash

SESSION="dev"

# Check if session exists
tmux has-session -t $SESSION 2>/dev/null

if [ $? != 0 ]; then
  # Create new session with first window
  tmux new-session -d -s $SESSION -n editor

  # Window 1: Editor
  tmux send-keys -t $SESSION:editor "cd ~/projects && nvim" C-m

  # Window 2: Server
  tmux new-window -t $SESSION -n server
  tmux send-keys -t $SESSION:server "cd ~/projects && npm run dev" C-m

  # Window 3: Git
  tmux new-window -t $SESSION -n git
  tmux send-keys -t $SESSION:git "cd ~/projects && git status" C-m

  # Window 4: Logs
  tmux new-window -t $SESSION -n logs
  tmux send-keys -t $SESSION:logs "cd ~/projects && tail -f logs/app.log" C-m

  # Split the git window
  tmux split-window -h -t $SESSION:git
  tmux send-keys -t $SESSION:git.right "cd ~/projects && tig" C-m

  # Select first window
  tmux select-window -t $SESSION:editor
fi

# Attach to session
tmux attach -t $SESSION
```

Make executable and run:

```bash
chmod +x ~/tmux-dev.sh
~/tmux-dev.sh
```

#### 🎨 Tmux Plugin Manager (TPM)

```bash
# Install TPM
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm

# Add to ~/.tmux.conf (at the bottom)
# ═══════════════════════════════════════════
# Plugins
# ═══════════════════════════════════════════

set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'tmux-plugins/tmux-resurrect'      # Save/restore sessions
set -g @plugin 'tmux-plugins/tmux-continuum'      # Auto-save sessions
set -g @plugin 'christoomey/vim-tmux-navigator'   # Vim integration
set -g @plugin 'tmux-plugins/tmux-yank'           # Better copy/paste
set -g @plugin 'tmux-plugins/tmux-open'           # Open highlighted text

# Resurrect settings
set -g @resurrect-capture-pane-contents 'on'
set -g @resurrect-strategy-nvim 'session'

# Continuum settings (auto-save every 15 minutes)
set -g @continuum-restore 'on'
set -g @continuum-save-interval '15'

# Initialize TPM (keep at bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'

# Install plugins: <prefix> I (capital i)
# Update plugins: <prefix> U
# Uninstall plugins: <prefix> alt+u
```

#### 💡 Common Workflows

```bash
# Development workflow
tmux new -s project
<prefix> |              # Split vertically
<prefix> -              # Split horizontally
# Left pane: editor, Top right: server, Bottom right: git

# Remote server workflow (survives disconnects!)
ssh user@server
tmux new -s work        # Start tmux on server
# Do your work...
<prefix> d              # Detach
# Connection drops - no problem!
# Later:
ssh user@server
tmux a -t work          # Reattach - everything still running!

# Pair programming (share session)
tmux new -s pairing
# Share session name with colleague
# They run: tmux a -t pairing
# Both see and control the same session!

# Multi-project workflow
tmux new -s frontend
tmux new -s backend
tmux new -s database
# Switch between projects with: <prefix> s

# Monitor multiple logs
tmux new -s logs
<prefix> %              # Split vertically
<prefix> "              # Split horizontally
# Each pane tails different log file
```

#### 🎯 Useful Aliases

Add to `~/.zshrc`:

```bash
# Tmux aliases
alias ta='tmux attach'
alias tad='tmux attach -d -t'
alias ts='tmux new-session -s'
alias tl='tmux list-sessions'
alias tksv='tmux kill-server'
alias tkss='tmux kill-session -t'
alias tmuxconf='nvim ~/.tmux.conf'
```

---

<div align="center">

## 🗄️ Data Processing

</div>

### 🔮 jq

**Command-line JSON processor - like sed for JSON**

```
🌐 Website → https://jqlang.github.io/jq/
📦 Install  → brew install jq
✨ Power    → Parse, filter, transform JSON with ease
```

**Why jq?**

- Powerful JSON manipulation
- Streaming parser (handles large files)
- Turing-complete language
- Pretty printing
- Works with pipes

#### 📥 Installation

```bash
# macOS
brew install jq

# Ubuntu/Debian
sudo apt install jq

# Fedora
sudo dnf install jq

# Arch Linux
sudo pacman -S jq
```

#### 📘 Basic Usage

```bash
# Pretty print JSON
echo '{"name":"John","age":30}' | jq '.'
curl https://api.github.com/users/defunkt | jq '.'

# Get specific field
echo '{"name":"John","age":30}' | jq '.name'
# Output: "John"

# Get nested field
echo '{"user":{"name":"John"}}' | jq '.user.name'
# Output: "John"

# Get array element
echo '["a","b","c"]' | jq '.[0]'
# Output: "a"

# Get array length
echo '["a","b","c"]' | jq 'length'
# Output: 3

# Get last element
echo '["a","b","c"]' | jq '.[-1]'
# Output: "c"
```

#### 🔥 Advanced Filtering

```bash
# Filter array elements
echo '[{"name":"John","age":30},{"name":"Jane","age":25}]' | jq '.[] | select(.age > 26)'

# Get all values of a key
echo '[{"name":"John"},{"name":"Jane"}]' | jq '.[].name'
# Output:
# "John"
# "Jane"

# Map over array
echo '[1,2,3]' | jq 'map(. * 2)'
# Output: [2,4,6]

# Filter and transform
echo '[{"name":"John","age":30},{"name":"Jane","age":25}]' | jq '[.[] | {name, older: .age > 26}]'

# Get keys
echo '{"a":1,"b":2}' | jq 'keys'
# Output: ["a","b"]

# Get values
echo '{"a":1,"b":2}' | jq 'values'
# Output: 1, 2 (separate lines)
```

#### 🎯 Common Use Cases

```bash
# Extract specific fields
curl -s https://api.github.com/users/defunkt | jq '{name: .name, repos: .public_repos}'

# Count items
curl -s https://api.github.com/users/defunkt/repos | jq 'length'

# Get first N items
curl -s https://api.github.com/users/defunkt/repos | jq '.[:5]'

# Sort by field
echo '[{"name":"b","age":30},{"name":"a","age":25}]' | jq 'sort_by(.name)'

# Group by field
echo '[{"cat":"A","val":1},{"cat":"B","val":2},{"cat":"A","val":3}]' | jq 'group_by(.cat)'

# Unique values
echo '[{"cat":"A"},{"cat":"B"},{"cat":"A"}]' | jq '[.[].cat] | unique'

# Merge objects
echo '{"a":1}' | jq '. + {"b":2}'
# Output: {"a":1,"b":2}

# Flatten array
echo '[[1,2],[3,4]]' | jq 'flatten'
# Output: [1,2,3,4]
```

#### 🚀 Power User Tips

```bash
# Raw output (no quotes for strings)
echo '{"name":"John"}' | jq -r '.name'
# Output: John (not "John")

# Compact output (no pretty print)
echo '{"name":"John"}' | jq -c '.'
# Output: {"name":"John"}

# Read from file
jq '.[]' data.json

# Write to file
jq '.' input.json > output.json

# Multiple filters
jq '.[] | select(.age > 25) | .name' data.json

# Conditional logic
echo '{"age":35}' | jq 'if .age > 30 then "old" else "young" end'
# Output: "old"

# String interpolation
echo '[{"name":"John","age":30}]' | jq '.[] | "\(.name) is \(.age) years old"'
# Output: "John is 30 years old"

# Array construction
echo '[{"name":"John","age":30}]' | jq '[.[] | {name, age}]'

# Check if key exists
echo '{"name":"John"}' | jq 'has("name")'
# Output: true

# Delete key
echo '{"name":"John","age":30}' | jq 'del(.age)'
# Output: {"name":"John"}

# Add key
echo '{"name":"John"}' | jq '. + {age: 30}'
# Output: {"name":"John","age":30}

# Recursive descent
echo '{"a":{"b":{"c":1}}}' | jq '.. | numbers'
# Output: 1
```

#### 💡 Real-World Examples

```bash
# Parse GitHub API
curl -s https://api.github.com/users/defunkt/repos | \
  jq '[.[] | {name: .name, stars: .stargazers_count}] | sort_by(.stars) | reverse | .[:5]'

# Process package.json
jq '.dependencies | keys' package.json

# Extract values from logs
cat logs.json | jq -r '.[] | select(.level == "error") | .message'

# Convert to CSV
jq -r '.[] | [.name, .age, .city] | @csv' data.json

# Convert to TSV
jq -r '.[] | [.name, .age, .city] | @tsv' data.json

# Count by category
jq 'group_by(.category) | map({category: .[0].category, count: length})' data.json

# Update JSON in place (requires sponge from moreutils)
jq '.version = "2.0.0"' package.json | sponge package.json

# Or without sponge (create temp file)
jq '.version = "2.0.0"' package.json > tmp.json && mv tmp.json package.json

# Filter by regex
echo '[{"name":"John"},{"name":"Jane"}]' | jq '.[] | select(.name | test("^J"))'

# Calculate average
echo '[{"val":10},{"val":20},{"val":30}]' | jq '[.[].val] | add/length'
# Output: 20

# Combine multiple JSON files
jq -s '.[0] + .[1]' file1.json file2.json

# Pretty print with custom indentation
jq --indent 4 '.' data.json

# URL encode
echo '{"url":"hello world"}' | jq -r '.url | @uri'
# Output: hello%20world

# Base64 encode/decode
echo '{"data":"hello"}' | jq -r '.data | @base64'
# Encode
echo '"aGVsbG8="' | jq -r '@base64d'
# Decode
```

---

<div align="center">

## ☁️ Cloud & DevOps

</div>

### 🐙 gh (GitHub CLI)

**GitHub's official command-line tool**

```
🌐 Website → https://cli.github.com
📦 Install  → brew install gh
🚀 Power    → Manage GitHub from terminal
```

**Why gh?**

- Create PRs from command line
- Manage issues and repos
- GitHub Actions workflow control
- Authenticate easily
- Scriptable workflows

#### 📥 Installation

```bash
# macOS
brew install gh

# Ubuntu/Debian
(type -p wget >/dev/null || (sudo apt update && sudo apt-get install wget -y)) \
&& sudo mkdir -p -m 755 /etc/apt/keyrings \
&& wget -qO- https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null \
&& sudo chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&& sudo apt update \
&& sudo apt install gh -y

# Fedora
sudo dnf install gh

# Arch Linux
sudo pacman -S github-cli
```

#### 🔐 Authentication

```bash
# Login to GitHub
gh auth login

# Check authentication status
gh auth status

# Refresh authentication
gh auth refresh

# Logout
gh auth logout
```

#### 📘 Repository Management

```bash
# Clone a repository
gh repo clone owner/repo

# Create a new repository
gh repo create my-new-repo --public
gh repo create my-new-repo --private

# Create repo and clone it
gh repo create my-new-repo --public --clone

# Fork a repository
gh repo fork owner/repo

# View repository
gh repo view
gh repo view owner/repo

# View repository in browser
gh browse

# List your repositories
gh repo list

# List repositories of an organization
gh repo list organization

# Archive a repository
gh repo archive owner/repo

# Delete a repository
gh repo delete owner/repo
```

#### 🔀 Pull Request Management

```bash
# Create a pull request
gh pr create

# Create PR with title and body
gh pr create --title "Add feature X" --body "Description"

# Create draft PR
gh pr create --draft

# List pull requests
gh pr list

# View a PR
gh pr view 123
gh pr view 123 --web    # Open in browser

# Check out a PR locally
gh pr checkout 123

# Review a PR
gh pr review 123 --approve
gh pr review 123 --request-changes --body "Please fix XYZ"
gh pr review 123 --comment --body "Looks good!"

# Merge a PR
gh pr merge 123
gh pr merge 123 --squash
gh pr merge 123 --rebase

# Close a PR
gh pr close 123

# Reopen a PR
gh pr reopen 123

# List my PRs
gh pr list --author "@me"

# Check PR status
gh pr status

# View PR diff
gh pr diff 123
```

#### 🐛 Issue Management

```bash
# Create an issue
gh issue create

# Create issue with title and body
gh issue create --title "Bug: XYZ" --body "Description"

# List issues
gh issue list

# View an issue
gh issue view 456
gh issue view 456 --web

# Close an issue
gh issue close 456

# Reopen an issue
gh issue reopen 456

# Add labels
gh issue edit 456 --add-label "bug,priority"

# Assign issue
gh issue edit 456 --add-assignee @me

# List my issues
gh issue list --assignee "@me"

# Search issues
gh issue list --search "is:open label:bug"
```

#### ⚙️ GitHub Actions

```bash
# List workflows
gh workflow list

# View workflow details
gh workflow view

# Run a workflow
gh workflow run workflow.yml

# View workflow runs
gh run list

# View specific run
gh run view 123456

# Watch a run in real-time
gh run watch 123456

# Download run artifacts
gh run download 123456

# Rerun a workflow
gh run rerun 123456

# Cancel a run
gh run cancel 123456

# View logs
gh run view 123456 --log
```

#### 🚀 Advanced Usage

```bash
# Create gist
gh gist create file.txt
gh gist create file.txt --public

# List gists
gh gist list

# View gist
gh gist view GIST_ID

# Create release
gh release create v1.0.0 --title "Version 1.0.0" --notes "Release notes"

# Upload assets to release
gh release upload v1.0.0 ./dist/*

# List releases
gh release list

# View release
gh release view v1.0.0

# Create GitHub Pages site
gh repo create my-site --public --enable-pages

# Search repositories
gh search repos "machine learning" --language python

# Search issues
gh search issues "bug" --repo owner/repo

# Search code
gh search code "TODO" --repo owner/repo

# Search users
gh search users "location:london"

# Set secrets (for Actions)
gh secret set MY_SECRET < secret.txt

# List secrets
gh secret list

# Use gh as git credential helper
gh auth setup-git
```

#### 💡 Useful Aliases

Add to `~/.zshrc`:

```bash
# GitHub CLI aliases
alias ghpr='gh pr create'
alias ghprv='gh pr view --web'
alias ghpc='gh pr checkout'
alias ghpl='gh pr list'
alias ghi='gh issue create'
alias ghil='gh issue list'
alias ghrc='gh repo create'
alias ghrv='gh repo view --web'
alias ghb='gh browse'
```

Create custom gh aliases:

```bash
# Add to ~/.config/gh/config.yml

aliases:
  pv: pr view --web
  pc: pr checkout
  rv: repo view --web
  co: pr checkout
```

---

### 🔐 doppler

**Secrets management for developers**

```
🌐 Website → https://doppler.com
📦 Install  → brew install dopplerhq/cli/doppler
🔒 Power    → Sync secrets across environments
```

**Why Doppler?**

- Centralized secrets management
- No more `.env` files in git
- Sync secrets across team
- Integrates with CI/CD
- Automatic rotation

#### 📥 Installation

```bash
# macOS
brew install dopplerhq/cli/doppler

# Ubuntu/Debian
sudo apt-get update && sudo apt-get install -y apt-transport-https ca-certificates curl gnupg
curl -sLf --retry 3 --tlsv1.2 --proto "=https" 'https://packages.doppler.com/public/cli/gpg.DE2A7741A397C129.key' | sudo gpg --dearmor -o /usr/share/keyrings/doppler-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/doppler-archive-keyring.gpg] https://packages.doppler.com/public/cli/deb/debian any-version main" | sudo tee /etc/apt/sources.list.d/doppler-cli.list
sudo apt-get update && sudo apt-get install doppler

# Install script (all platforms)
(curl -Ls --tlsv1.2 --proto "=https" --retry 3 https://cli.doppler.com/install.sh || wget -t 3 -qO- https://cli.doppler.com/install.sh) | sudo sh
```

#### 🔐 Authentication & Setup

```bash
# Login to Doppler
doppler login

# Verify authentication
doppler me

# Logout
doppler logout

# Setup project
doppler setup

# Select specific project and config
doppler setup --project my-project --config dev
```

#### 📘 Basic Usage

```bash
# View secrets
doppler secrets

# Get specific secret
doppler secrets get DATABASE_URL

# Set a secret
doppler secrets set API_KEY="your-key-here"

# Delete a secret
doppler secrets delete API_KEY

# Download secrets to .env file
doppler secrets download --no-file --format env > .env

# Run command with secrets injected
doppler run -- npm start
doppler run -- python app.py
doppler run -- node server.js

# Run script with secrets
doppler run -- ./my-script.sh
```

#### 🚀 Advanced Features

```bash
# Switch environment
doppler configure set config prod

# View current configuration
doppler configure get

# Compare configs
doppler secrets compare dev prod

# Bulk upload secrets from file
doppler secrets upload secrets.json

# Import from .env file
doppler secrets import .env

# View secret history
doppler secrets history

# Rollback to previous version
doppler secrets rollback <version>

# Create service token for CI/CD
doppler configs tokens create ci-token --config prod --max-age 30d

# Revoke token
doppler configs tokens revoke <token-slug>

# Share secrets with team member
doppler share create --project my-project --config dev --email user@example.com
```

#### 🔧 Integration with Applications

```bash
# Node.js
# Use doppler-run wrapper
doppler run -- node app.js

# Docker
# Use doppler as entrypoint
FROM node:18
RUN curl -Ls --tlsv1.2 --proto "=https" --retry 3 https://cli.doppler.com/install.sh | sh
ENTRYPOINT ["doppler", "run", "--"]
CMD ["node", "app.js"]

# GitHub Actions
# Add to .github/workflows/main.yml
- uses: dopplerhq/secrets-fetch-action@v1
  with:
    doppler-token: ${{ secrets.DOPPLER_TOKEN }}

# Docker Compose
# Use doppler to inject secrets
doppler run -- docker-compose up

# Kubernetes
# Use Doppler Operator or External Secrets Operator
doppler secrets download --format env-no-quotes | kubectl create secret generic app-secrets --from-env-file=-
```

#### 💡 Best Practices

```bash
# Never commit .env files
echo ".env" >> .gitignore
echo ".env.*" >> .gitignore

# Use service tokens for CI/CD (not personal tokens)
doppler configs tokens create ci-token --config prod

# Different configs for different environments
doppler setup --config dev      # Local development
doppler setup --config staging  # Staging environment
doppler setup --config prod     # Production

# Name secrets consistently
# Use SCREAMING_SNAKE_CASE
DATABASE_URL
API_KEY
JWT_SECRET

# Document secrets in README
# List what secrets are needed (not values!)

# Rotate secrets regularly
# Use Doppler's secret rotation features

# Audit secret access
doppler activity
```

---

<div align="center">

## 🔐 Security & Secrets

</div>

### 🔑 pass

**The standard Unix password manager**

```
🌐 Website → https://www.passwordstore.org
📦 Install  → brew install pass
🔐 Power    → GPG-encrypted password storage
```

**Why pass?**

- GPG encryption
- Git integration (track changes)
- Simple and Unix-like
- No database (just files)
- Compatible with browser extensions

#### 📥 Installation

```bash
# macOS
brew install pass

# Ubuntu/Debian
sudo apt install pass

# Fedora
sudo dnf install pass

# Arch Linux
sudo pacman -S pass

# Also install GPG if needed
brew install gnupg
```

#### 🔐 Setup

```bash
# Generate GPG key (if you don't have one)
gpg --full-generate-key
# Choose: RSA and RSA, 4096 bits, no expiration

# List GPG keys
gpg --list-keys

# Initialize password store with your GPG key ID
pass init your-gpg-id@email.com

# Initialize with git support
pass git init
pass git remote add origin git@github.com:username/password-store.git
```

#### 📘 Basic Usage

```bash
# Add a password
pass insert Email/gmail
pass insert Social/github

# Generate a strong password
pass generate Email/protonmail 20
pass generate -n Social/twitter 16  # No symbols

# Show password
pass Email/gmail

# Copy password to clipboard (clears after 45s)
pass -c Email/gmail

# Edit password
pass edit Email/gmail

# Remove password
pass rm Email/gmail

# List all passwords
pass
pass ls

# Search for password
pass grep gmail
pass search github
```

#### 🗂️ Organization

```bash
# Organize in folders
pass insert Work/Email/outlook
pass insert Work/SSH/aws-server
pass insert Personal/Banking/chase
pass insert Personal/Social/twitter

# View tree structure
pass

# List specific folder
pass ls Work/Email

# Move password
pass mv old/path new/path

# Copy password entry
pass cp old/path new/path
```

#### 🔄 Git Integration

```bash
# Commit changes
pass git add .
pass git commit -m "Added new passwords"
pass git push

# Pull changes
pass git pull

# View history
pass git log

# View changes
pass git diff

# Undo last commit
pass git revert HEAD
```

#### 🚀 Advanced Features

```bash
# Store multiline secrets (like SSH keys)
pass insert -m Servers/ssh-key
# Then paste your SSH key, press Ctrl+D when done

# Store metadata with password
pass insert Accounts/mybank <<EOF
Username: john_doe
Password: super_secret_123
Security Question: First pet
Answer: Fluffy
URL: https://mybank.com
EOF

# Generate password without symbols
pass generate -n Website/example 20

# Generate password in place (replace existing)
pass generate -i Website/example 20

# Generate QR code (requires qrencode)
pass otp uri -q Social/github-2fa | qrencode -t UTF8

# Import from other password managers
# (Various import scripts available in pass extensions)

# Synchronize across machines using git
pass git push
# On another machine:
git clone git@github.com:username/password-store.git ~/.password-store
pass git pull
```

#### 🌐 Browser Integration

```bash
# Install browserpass extension
# Chrome: https://chrome.google.com/webstore (search "browserpass")
# Firefox: https://addons.mozilla.org/firefox/ (search "browserpass")

# Install browserpass host app
brew install browserpass

# Setup
browserpass install
```

#### 🔧 Extensions

```bash
# pass-otp (for 2FA/TOTP)
brew install pass-otp

# Generate TOTP
pass otp uri github-2fa

# Insert OTP secret
pass otp insert github-2fa

# Generate OTP code
pass otp github-2fa

# Copy OTP to clipboard
pass otp -c github-2fa

# pass-update (check for password breaches)
brew install pass-update

# Check if password is breached
pass update -c Email/gmail

# pass-tomb (additional encryption layer)
brew install pass-tomb
```

#### 💡 Best Practices

```bash
# Good naming conventions
Website/Service/username
Email/provider/email-address
Work/Service/username
Personal/Category/service

# Examples:
pass insert Email/Gmail/john@gmail.com
pass insert Work/AWS/console
pass insert Banking/Chase/checking
pass insert Social/Twitter/myhandle

# Backup GPG key
gpg --export-secret-keys --armor your-email@example.com > private-key.asc
# Store this file securely (encrypted USB, safe location)

# Restore GPG key
gpg --import private-key.asc

# Set up git sync
pass git init
pass git remote add origin git@github.com:username/password-store-private.git
pass git push -u origin main

# Regular backups
tar -czf password-store-backup.tar.gz ~/.password-store/
# Encrypt the backup
gpg -c password-store-backup.tar.gz

# Use different GPG keys for different categories
pass init -p Work/ work-gpg-id@company.com
pass init -p Personal/ personal-gpg-id@email.com
```

#### 🎨 Create Aliases

Add to `~/.zshrc`:

```bash
# Pass aliases
alias p='pass'
alias pc='pass -c'
alias pg='pass generate'
alias pi='pass insert'
alias ps='pass search'
alias pe='pass edit'
alias pl='pass ls'
```

---

<div align="center">

## 🔧 System Utilities

</div>

### 🔗 stow

**GNU Stow - symlink farm manager (perfect for dotfiles!)**

```
🌐 Website → https://www.gnu.org/software/stow/
📦 Install  → brew install stow
💡 Use Case → Organize dotfiles with symlinks
```

**Why GNU Stow?**

- Simple dotfile management
- Uses standard symlinks
- Easy to backup and version control
- No complex tool needed
- Works everywhere

#### 📥 Installation

```bash
# macOS
brew install stow

# Ubuntu/Debian
sudo apt install stow

# Fedora
sudo dnf install stow

# Arch Linux
sudo pacman -S stow
```

#### 📘 Basic Concept

```
~/dotfiles/
  ├── nvim/
  │   └── .config/
  │       └── nvim/
  │           └── init.lua
  ├── zsh/
  │   ├── .zshrc
  │   └── .zsh/
  │       └── aliases.zsh
  └── git/
      └── .gitconfig

# Stow creates symlinks from ~ to ~/dotfiles/*
~/.config/nvim -> ~/dotfiles/nvim/.config/nvim
~/.zshrc -> ~/dotfiles/zsh/.zshrc
~/.gitconfig -> ~/dotfiles/git/.gitconfig
```

#### 🎯 Basic Usage

```bash
# Navigate to dotfiles directory
cd ~/dotfiles

# Stow a package (creates symlinks)
stow nvim

# This creates:
# ~/.config/nvim -> ~/dotfiles/nvim/.config/nvim

# Stow multiple packages
stow nvim zsh git tmux

# Unstow (remove symlinks)
stow -D nvim

# Restow (remove and re-add)
stow -R nvim

# Dry run (see what would happen)
stow -n nvim
stow -nv nvim  # Verbose dry run

# Verbose output
stow -v nvim
```

#### 🗂️ Recommended Dotfiles Structure

```bash
~/dotfiles/
  ├── alacritty/
  │   └── .config/
  │       └── alacritty/
  │           └── alacritty.yml
  ├── bat/
  │   └── .config/
  │       └── bat/
  │           └── config
  ├── git/
  │   ├── .gitconfig
  │   └── .gitignore_global
  ├── nvim/
  │   └── .config/
  │       └── nvim/
  │           ├── init.lua
  │           └── lua/
  │               └── ...
  ├── tmux/
  │   ├── .tmux.conf
  │   └── .config/
  │       └── tmux/
  │           └── plugins/
  ├── zsh/
  │   ├── .zshrc
  │   ├── .zshenv
  │   └── .zsh/
  │       ├── aliases.zsh
  │       ├── functions.zsh
  │       └── exports.zsh
  ├── scripts/
  │   └── .local/
  │       └── bin/
  │           ├── tmux-sessionizer
  │           └── git-backup
  ├── install.sh
  └── README.md
```

#### 🚀 Complete Setup Guide

```bash
# 1. Create dotfiles directory
mkdir ~/dotfiles
cd ~/dotfiles

# 2. Initialize git repo
git init
git remote add origin https://github.com/yourusername/dotfiles.git

# 3. Move existing configs to dotfiles
# For nvim
mkdir -p nvim/.config/nvim
mv ~/.config/nvim/* nvim/.config/nvim/

# For zsh
mkdir -p zsh
mv ~/.zshrc zsh/.zshrc
mv ~/.zshenv zsh/.zshenv
mv ~/.zsh zsh/.zsh

# For git
mkdir -p git
mv ~/.gitconfig git/.gitconfig

# For tmux
mkdir -p tmux
mv ~/.tmux.conf tmux/.tmux.conf

# 4. Stow everything
stow nvim zsh git tmux

# 5. Commit and push
git add .
git commit -m "Initial dotfiles commit"
git push -u origin main
```

#### 💡 Advanced Usage

```bash
# Stow with different target directory
stow -t /usr/local mypackage

# Ignore specific files
stow --ignore='\.DS_Store' nvim
stow --ignore='README.*' nvim

# Use with different dotfiles directory
stow --dir=~/my-dotfiles --target=~ nvim

# Adopt existing files (move them into stow package)
stow --adopt nvim
# This moves existing ~/.config/nvim into ~/dotfiles/nvim/.config/nvim

# Handle conflicts
stow -v --adopt nvim     # Adopt conflicting files
stow --override='.*' nvim  # Override conflicts (dangerous!)

# Stow to custom target
stow -t ~/.config/different-location nvim

# Stow specific subdirectory
cd ~/dotfiles/nvim/.config
stow -t ~ nvim

# Delete stow package directory after unstowing
stow -D old-config && rm -rf old-config
```

#### 🎨 Bootstrap Script

Create `~/dotfiles/install.sh`:

```bash
#!/bin/bash

# Bootstrap script for dotfiles
set -e

DOTFILES=$HOME/dotfiles

echo "🚀 Setting up dotfiles..."

cd $DOTFILES

# List of packages to stow
PACKAGES=(
  "alacritty"
  "bat"
  "git"
  "nvim"
  "tmux"
  "zsh"
  "scripts"
)

# Stow all packages
for package in "${PACKAGES[@]}"; do
  if [ -d "$package" ]; then
    echo "📦 Stowing $package..."
    stow -v "$package"
  else
    echo "⚠️  Package $package not found, skipping..."
  fi
done

echo "✅ Dotfiles installed successfully!"
echo ""
echo "Next steps:"
echo "  1. Reload shell: source ~/.zshrc"
echo "  2. Install plugins: nvim +PackerSync"
echo "  3. Install tmux plugins: <prefix> I"
```

Make executable:

```bash
chmod +x ~/dotfiles/install.sh
./install.sh
```

#### 🔄 Sync Across Machines

```bash
# On Machine 1 (existing dotfiles)
cd ~/dotfiles
git push

# On Machine 2 (new machine)
git clone https://github.com/yourusername/dotfiles.git ~/dotfiles
cd ~/dotfiles
./install.sh

# To update dotfiles
cd ~/dotfiles
git pull
stow -R zsh nvim tmux  # Restow to apply changes
```

#### 📦 Useful Dotfiles Aliases

Add to `~/dotfiles/zsh/.zshrc`:

```bash
# ═══════════════════════════════════════════
# Dotfiles Management
# ═══════════════════════════════════════════

alias dotfiles='cd ~/dotfiles'
alias dots='dotfiles'

# Stow shortcuts
alias stow-all='cd ~/dotfiles && stow */'
alias unstow-all='cd ~/dotfiles && stow -D */'
alias restow-all='cd ~/dotfiles && stow -R */'

# Git shortcuts for dotfiles
alias dotgit='git -C ~/dotfiles'
alias dotpush='git -C ~/dotfiles push'
alias dotpull='git -C ~/dotfiles pull'
alias dotstatus='git -C ~/dotfiles status'
alias dotcommit='git -C ~/dotfiles commit -am'

# Quick edit dotfiles
alias zshrc='$EDITOR ~/dotfiles/zsh/.zshrc'
alias nvimrc='$EDITOR ~/dotfiles/nvim/.config/nvim/init.lua'
alias tmuxrc='$EDITOR ~/dotfiles/tmux/.tmux.conf'
alias gitrc='$EDITOR ~/dotfiles/git/.gitconfig'
```

#### 💡 Pro Tips

```bash
# 1. Keep dotfiles minimal
# Don't stow everything - only config files you actually customize

# 2. Document your setup
# Create a comprehensive README.md in ~/dotfiles/

# 3. Separate private configs
# Use a separate private repo for work/sensitive configs
~/dotfiles/         # Public configs
~/dotfiles-private/ # Private configs (separate repo, not public)

# 4. Use branches for different setups
git checkout -b macos    # macOS-specific configs
git checkout -b linux    # Linux-specific configs
git checkout -b work     # Work-specific configs

# 5. Test before committing
stow -nv package  # Always dry run first!

# 6. Handle machine-specific configs
# Create local override files that aren't tracked
# Example in .zshrc:
if [ -f ~/.zshrc.local ]; then
  source ~/.zshrc.local
fi

# 7. Automate fresh install
# Create a comprehensive install.sh that:
# - Installs Homebrew
# - Installs essential tools
# - Clones dotfiles
# - Stows everything
# - Sets up GPG, SSH keys, etc.
```

---

### 📖 tldr

**Simplified and community-driven man pages**

```
🌐 Website → https://tldr.sh
📦 Install  → brew install tldr
💡 Concept  → Too Long; Didn't Read - practical examples
```

**Why tldr?**

- Quick practical examples
- No overwhelming documentation
- Community-driven
- Fast lookup
- Available offline

#### 📥 Installation

```bash
# macOS
brew install tldr

# Ubuntu/Debian
sudo apt install tldr

# npm (works everywhere)
npm install -g tldr

# pip (Python)
pip install tldr

# cargo (Rust)
cargo install tealdeer

# Note: tealdeer is a Rust implementation (much faster!)
```

#### 📘 Basic Usage

```bash
# Update cache (run after install and periodically)
tldr --update

# Get help for a command
tldr tar
tldr git commit
tldr ffmpeg
tldr ssh
tldr docker
tldr kubectl

# Search for commands
tldr --search "compress"
tldr -s "network"

# List all pages
tldr --list

# Show specific platform
tldr --platform linux tar
tldr --platform osx tar
tldr -p windows powershell

# Random page (discover new commands!)
tldr --random
```

#### 💡 Example Output

```bash
$ tldr tar

  tar

  Archiving utility.
  Often combined with a compression method, such as gzip or bzip2.
  More information: https://www.gnu.org/software/tar.

  - [c]reate an archive and write it to a [f]ile:
    tar cf path/to/target.tar path/to/file1 path/to/file2 ...

  - [c]reate a g[z]ipped archive and write it to a [f]ile:
    tar czf path/to/target.tar.gz path/to/file1 path/to/file2 ...

  - [c]reate a g[z]ipped archive from a directory using relative paths:
    tar czf path/to/target.tar.gz --directory=path/to/directory .

  - E[x]tract a (compressed) archive [f]ile into the current directory [v]erbosely:
    tar xvf path/to/source.tar[.gz|.bz2|.xz]

  - E[x]tract a (compressed) archive [f]ile into the target directory:
    tar xf path/to/source.tar[.gz|.bz2|.xz] --directory=path/to/directory

  - [c]reate a compressed archive and write it to a [f]ile, using [a]rchive suffix to determine the compression program:
    tar caf path/to/target.tar.xz path/to/file1 path/to/file2 ...
```

#### 🚀 Advanced Usage

```bash
# Use with fzf for fuzzy search
tldr --list | fzf --preview 'tldr {1} --color=always' --preview-window=right,70% | xargs tldr

# Create a function for quick lookup (add to ~/.zshrc)
function help() {
  tldr "$@" 2>/dev/null || man "$@"
}

# Language support
tldr -L es git  # Spanish
tldr -L fr tar  # French
tldr -L pt docker  # Portuguese

# Output as markdown
tldr --markdown tar

# Render without colors
tldr --color=never tar

# Use tealdeer (Rust implementation) for extra features
tldr --update
tldr --list
tldr --render /path/to/page.md

# Custom cache location (tealdeer)
export TEALDEER_CACHE_DIR=~/.cache/tldr

# Custom config (tealdeer)
# Create ~/.config/tealdeer/config.toml
[display]
compact = false
use_pager = false

[updates]
auto_update = true
auto_update_interval_hours = 720  # 30 days
```

#### 💡 Useful Aliases

Add to `~/.zshrc`:

```bash
# tldr aliases
alias help='tldr'
alias h='tldr'
alias cheat='tldr'

# Update tldr cache weekly
alias tldr-update='tldr --update'

# Random command discovery
alias learn='tldr --random'
```

#### 🎨 Integration Ideas

```bash
# Create a wrapper that tries tldr first, then man
function ? () {
  if command -v tldr &> /dev/null; then
    tldr "$@" 2>/dev/null || man "$@" 2>/dev/null || echo "No help found for: $@"
  else
    man "$@"
  fi
}

# Example usage:
? tar
? ssh
? docker
```

---

### 🎨 eza

**A modern replacement for `ls` with colors and icons**

```
🌐 Website → https://github.com/eza-community/eza
📦 Install  → brew install eza
✨ Features → Colors, icons, Git integration, tree view
```

**Why eza?**

- Beautiful output with colors and icons
- Git integration (shows file status)
- Extended file attributes
- Tree view built-in
- Fast and intuitive
- Successor to exa (actively maintained)

#### 📥 Installation

```bash
# macOS
brew install eza

# Ubuntu/Debian (via cargo)
cargo install eza

# Arch Linux
sudo pacman -S eza

# Fedora
sudo dnf install eza

# From source
cargo install eza
```

#### 📘 Basic Usage

```bash
# Basic listing
eza

# Long format
eza -l

# Long format with header
eza -lh

# Show hidden files
eza -a

# All details (long + header + hidden)
eza -lha

# Grid view
eza --grid

# One file per line
eza -1

# Sort by time
eza -l --sort=modified
eza -l -s modified

# Sort by size
eza -l --sort=size
eza -l -s size

# Reverse order
eza -l --reverse
eza -lr

# Show file sizes in human readable format
eza -lh --binary
eza -lhb
```

#### 🎯 Advanced Features

```bash
# Tree view
eza --tree
eza -T

# Tree with limited depth
eza --tree --level=2
eza -T -L2

# Git integration
eza -l --git                # Show Git status
eza -lg

# Ignore .gitignore patterns
eza -l --git-ignore
eza -lg --git-ignore

# Icons
eza -l --icons              # Show file icons
eza -l --icons=always
eza -li                     # Short form

# Group directories first
eza -l --group-directories-first
eza -lD

# Show only directories
eza -D
eza --only-dirs

# Show only files
eza -f
eza --only-files

# Extended attributes (macOS)
eza -l@                     # Show extended attributes
eza -l --extended

# Octal permissions
eza -l --octal-permissions
eza -lo

# Inode numbers
eza -li --inode

# File size with blocks
eza -l --blocks

# Time styles
eza -l --time-style=long-iso
eza -l --time-style=iso
eza -l --time-style=relative
eza -l --time-style=default

# Show file headers
eza -lh --header

# Color customization
eza -l --color=always
eza -l --color=never
eza -l --color=automatic

# Show symlink targets
eza -l --no-symlinks         # Don't show symlink targets
```

#### 🎨 Git Status Indicators

```
When using --git flag:

N  New file (not tracked)
M  Modified
T  Type changed
I  Ignored
-  Not in Git
```

Example:

```bash
$ eza -lg
drwxr-xr-x    - user  1 Jan 12:00 M  src
.rw-r--r--  1.2k user  1 Jan 12:00 N  README.md
.rw-r--r--   324 user  1 Jan 12:00 -  package.json
```

#### 🚀 Powerful Aliases

Add to `~/.zshrc`:

```bash
# ═══════════════════════════════════════════
# eza (ls replacement)
# ═══════════════════════════════════════════

# Basic replacements
alias ls='eza --icons'
alias ll='eza -lh --icons --git'
alias la='eza -lha --icons --git'
alias l='eza -lh --icons --git --group-directories-first'

# Tree listings
alias lt='eza --tree --level=2 --icons'
alias lt3='eza --tree --level=3 --icons'
alias lta='eza --tree --level=2 --icons -a'

# Specialized listings
alias lsd='eza -D --icons'                                    # List only directories
alias lsf='eza -f --icons'                                    # List only files
alias lss='eza -lh --icons --git --sort=size'                 # Sort by size
alias lst='eza -lh --icons --git --sort=modified'             # Sort by time
alias lsr='eza -lh --icons --git --sort=modified --reverse'   # Oldest first

# Detailed listings
alias lx='eza -lh --icons --git --extended'                   # Extended attributes
alias lo='eza -lh --icons --git --octal-permissions'          # Octal permissions
alias li='eza -lh --icons --git --inode'                      # Show inodes

# Git-aware listings
alias lg='eza -lh --icons --git --git-ignore'                 # Respect .gitignore

# All files (no hiding)
alias laa='eza -lha --icons --git --group-directories-first -@'  # Everything!
```

#### 💡 Advanced Workflows

```bash
# Find largest files
eza -lh --sort=size --reverse | head -20

# Find newest files
eza -lh --sort=modified --reverse | head -10

# Tree with git status
eza --tree --level=3 --git-ignore --icons

# Only show modified files (requires jq if output is JSON)
eza -l --git | grep -E "^\s*M"

# Directories only, sorted by size
eza -D -lh --sort=size

# Show file sizes in bytes
eza -lh --no-filesize --bytes

# Combine with other tools
eza -f | fzf --preview 'bat --color=always {}'

# Count files by type
eza -1 | grep -E '\.[a-z]+$' | sed 's/.*\.//' | sort | uniq -c | sort -rn

# Find empty directories
eza -D -1 | while read dir; do [ -z "$(ls -A "$dir")" ] && echo "$dir"; done
```

#### 🎨 Color Customization

```bash
# Set custom colors via LS_COLORS
# Add to ~/.zshrc
export LS_COLORS='di=34:ln=35:so=32:pi=33:ex=31:bd=34;46:cd=34;43:su=30;41:sg=30;46:tw=30;42:ow=30;43'

# Or use a generator
# Install vivid for advanced color themes
brew install vivid

# Add to ~/.zshrc
export LS_COLORS="$(vivid generate molokai)"
# Or
export LS_COLORS="$(vivid generate snazzy)"
```

#### 💡 Pro Tips

```bash
# 1. Create custom functions for project navigation
function pls() {
  cd ~/projects
  eza --tree --level=2 --icons --git-ignore
}

# 2. Quick file statistics
function fstats() {
  echo "Total files: $(eza -f | wc -l)"
  echo "Total directories: $(eza -D | wc -l)"
  echo "Total size: $(eza -lh | awk '{s+=$4} END {print s}')"
}

# 3. Find files changed today
alias today='eza -lh --icons --git --sort=modified | grep "$(date +%Y-%m-%d)"'

# 4. Compare directories
function compare-dirs() {
  echo "=== Directory 1: $1 ==="
  eza -1 "$1" | sort > /tmp/dir1.txt
  echo ""
  echo "=== Directory 2: $2 ==="
  eza -1 "$2" | sort > /tmp/dir2.txt
  echo ""
  echo "=== Differences ==="
  diff /tmp/dir1.txt /tmp/dir2.txt
}

# 5. Show file tree with sizes
alias tree-size='eza --tree --level=3 -lh --icons --git-ignore'
```

---

### 🗂️ yazi

**Blazing fast terminal file manager**

```
🌐 Website → https://github.com/sxyazi/yazi
📦 Install  → brew install yazi
⚡ Speed    → Async I/O, image previews, fast navigation
```

**Why yazi?**

- Asynchronous I/O operations
- Built-in image preview
- Vim-like keybindings
- Fast and responsive
- Fully customizable
- Concurrency support

#### 📥 Installation

```bash
# macOS
brew install yazi ffmpegthumb unar jq poppler fd ripgrep fzf zoxide imagemagick

# Arch Linux
sudo pacman -S yazi ffmpegthumbnailer unarchiver jq poppler fd ripgrep fzf zoxide imagemagick

# Ubuntu/Debian
# Add repository first, then:
sudo apt install yazi ffmpegthumbnailer unarchiver jq poppler-utils fd-find ripgrep fzf imagemagick

# From source (latest version)
cargo install --locked yazi-fm yazi-cli
```

#### 📘 Basic Usage

```bash
# Start yazi
yazi

# Start in specific directory
yazi /path/to/dir

# Open specific file
yazi file.txt
```

#### ⌨️ Essential Keybindings

**Navigation:**

```
j / ↓           # Move cursor down
k / ↑           # Move cursor up
h / ←           # Go to parent directory
l / → / Enter   # Enter directory or open file

g               # Go to top
G               # Go to bottom
J               # Page down
K               # Page up

[ / ]           # Previous/Next tab

/               # Search (start typing)
n               # Next search result
N               # Previous search result

~               # Go to home directory
```

**File Operations:**

```
<Space>         # Toggle selection
v               # Enter visual mode (select multiple)
V               # Enter visual mode (unselect all)
Ctrl+a          # Select all

y               # Yank (copy) selected files
x               # Cut selected files
p               # Paste yanked/cut files
P               # Paste (overwrite)

d / Delete      # Delete selected files
D               # Permanently delete (no trash)

r               # Rename file
a               # Create file
A               # Create directory

o               # Open file with system default
O               # Open file interactively (choose app)

.               # Toggle hidden files
z               # Jump to directory (using zoxide)
```

**Tabs:**

```
t               # New tab
T               # New tab in current directory
1-9             # Switch to tab 1-9
Tab             # Next tab
Shift+Tab       # Previous tab
q               # Close tab (or quit if last tab)
```

**Preview & UI:**

```
Ctrl+p          # Toggle preview
Ctrl+w          # Close preview

F1              # Show help
```

**Other:**

```
:               # Command mode
;               # Shell mode (run shell command)
!               # Execute shell command on selected files

?               # Show help
q               # Quit
```

#### 🔧 Configuration

Create `~/.config/yazi/yazi.toml`:

```toml
# ═══════════════════════════════════════════
# Manager (file list)
# ═══════════════════════════════════════════

[manager]
show_hidden = false
show_symlink = true
sort_by = "natural"
sort_dir_first = true
sort_reverse = false
linemode = "size"
scrolloff = 5

# ═══════════════════════════════════════════
# Preview
# ═══════════════════════════════════════════

[preview]
tab_size = 2
max_width = 600
max_height = 900
cache_dir = "~/.cache/yazi"

# ═══════════════════════════════════════════
# Opener (default applications)
# ═══════════════════════════════════════════

[opener]
edit = [
    { run = 'nvim "$@"', block = true, for = "unix" },
    { run = 'code "$@"', block = true, for = "unix" },
]

open = [
    { run = 'open "$@"', desc = "Open", for = "macos" },
    { run = 'xdg-open "$@"', desc = "Open", for = "linux" },
]

play = [
    { run = 'mpv "$@"', orphan = true, for = "unix" },
]

# ═══════════════════════════════════════════
# Tasks
# ═══════════════════════════════════════════

[tasks]
micro_workers = 5
macro_workers = 10
bizarre_retry = 5
```

Create `~/.config/yazi/keymap.toml` for custom keybindings:

```toml
[manager]

keymap = [
    # Custom keybindings
    { on = [ "<C-n>" ], exec = "create --file", desc = "Create file" },
    { on = [ "<C-f>" ], exec = "search fd", desc = "Search with fd" },
    { on = [ "<C-s>" ], exec = "shell $SHELL", desc = "Open shell" },
    { on = [ "g", "h" ], exec = "cd ~", desc = "Go to home" },
    { on = [ "g", "d" ], exec = "cd ~/Downloads", desc = "Go to downloads" },
    { on = [ "g", "D" ], exec = "cd ~/Documents", desc = "Go to documents" },
    { on = [ "g", "p" ], exec = "cd ~/projects", desc = "Go to projects" },
]
```

#### 💡 Shell Wrapper (CD on Exit)

Add to `~/.zshrc`:

```bash
# ═══════════════════════════════════════════
# yazi - CD on exit
# ═══════════════════════════════════════════

function ya() {
    local tmp="$(mktemp -t "yazi-cwd.XXXXX")"
    yazi "$@" --cwd-file="$tmp"
    if cwd="$(cat -- "$tmp")" && [ -n "$cwd" ] && [ "$cwd" != "$PWD" ]; then
        cd -- "$cwd"
    fi
    rm -f -- "$tmp"
}

# Use 'ya' instead of 'yazi' to cd on exit
```

#### 🎨 Plugins & Extensions

```bash
# Plugin directory
~/.config/yazi/plugins/

# Popular plugins:
# 1. full-border.yazi - Better borders
# 2. git.yazi - Git status in file list
# 3. diff.yazi - Preview diffs
# 4. jump-to-char.yazi - Vim-style f/t navigation

# Install plugin example:
cd ~/.config/yazi/plugins
git clone https://github.com/yazi-rs/plugins.git
```

#### 🚀 Advanced Workflows

```bash
# 1. Quick project navigation
# Add to your aliases:
alias p='ya ~/projects'
alias dots='ya ~/dotfiles'

# 2. Open yazi and edit file in nvim
function ye() {
    local file=$(yazi --chooser-file=/dev/stdout | head -1)
    [ -n "$file" ] && nvim "$file"
}

# 3. Batch rename files
# In yazi:
# 1. Select files (Space)
# 2. Press 'r' for bulk rename
# 3. Edit in your $EDITOR
# 4. Save and exit

# 4. Preview integration with bat
# Add to ~/.config/yazi/yazi.toml:
[opener]
preview = [
    { run = 'bat --color=always --style=numbers --line-range :500 "$@"' },
]

# 5. Archive selected files
# Press ';' to enter shell mode, then:
# tar -czf archive.tar.gz $@

# 6. Find and open with fzf
# Press Ctrl+f, then use fzf to search
```

#### 💡 Integration with Other Tools

```bash
# 1. Set yazi as default file manager
export YAZI_FILE_ONE=~/.config/yazi/yazi.toml
export FILE_MANAGER=ya

# 2. Open yazi from nvim
# Add to your nvim config:
vim.keymap.set("n", "<leader>e", ":!yazi<CR>")

# 3. Integration with tmux
# Press prefix + e to open yazi in split
bind e split-window -h "yazi"

# 4. Quick scripts (add to ~/.zshrc)
# Extract archive and cd into it
function extract-cd() {
    if [ -f "$1" ]; then
        case "$1" in
            *.tar.gz|*.tgz) tar -xzf "$1" && cd "${1%.tar.gz}" ;;
            *.tar.bz2) tar -xjf "$1" && cd "${1%.tar.bz2}" ;;
            *.zip) unzip "$1" && cd "${1%.zip}" ;;
        esac
    fi
}

# 5. Bulk operations
# Select files in yazi, then press ';' and run:
# for file in $@; do convert "$file" "${file%.jpg}.png"; done
```

#### 🎯 Pro Tips

```bash
# 1. Image preview (requires überzug or similar)
# On macOS: Install kitty or iTerm2 with image support

# 2. Video thumbnails
# Install ffmpegthumbnailer
brew install ffmpegthumbnailer

# 3. PDF preview
# Install poppler
brew install poppler

# 4. Archive preview
# Install unar or unarchiver
brew install unar

# 5. Code preview with syntax highlighting
# yazi automatically uses bat if available

# 6. Customize colors
# Edit ~/.config/yazi/theme.toml

# 7. Performance tips
# Disable heavy previews for network drives
# Use --no-cwd-file flag when not needed

# 8. Bookmark directories
# Use 'm' to mark directory, then ''<key>' to jump
# In yazi: 'm' then 'a' = mark as 'a'
# Later: ''' then 'a' = jump to 'a'
```

#### 🎨 Useful Aliases

Add to `~/.zshrc`:

```bash
# yazi aliases
alias y='ya'                    # Short form
alias yi='ya .'                 # Current directory
alias yd='ya ~/Downloads'       # Downloads
alias yp='ya ~/projects'        # Projects
alias ydots='ya ~/dotfiles'     # Dotfiles

# File operations
alias yy='ya $(pwd)'            # Open in current directory
```

---

<div align="center">

## 📊 System Monitoring

</div>

### 📈 htop

**Interactive process viewer (better than `top`)**

```
🌐 Website → https://htop.dev
📦 Install  → brew install htop
⚡ Power    → Real-time system monitoring
```

**Why htop?**

- Interactive and user-friendly
- Mouse support
- Tree view for processes
- Colorful output
- Easy to kill processes

#### 📥 Installation

```bash
# macOS
brew install htop

# Ubuntu/Debian
sudo apt install htop

# Fedora
sudo dnf install htop

# Arch Linux
sudo pacman -S htop
```

#### ⌨️ Essential Keys

```
F1 / h      # Help
F2 / S      # Setup
F3 / /      # Search
F4 / \      # Filter
F5 / t      # Tree view
F6 / <      # Sort by column
F7 / ]      # Nice + (lower priority)
F8 / [      # Nice - (higher priority)
F9 / k      # Kill process
F10 / q     # Quit

Space       # Tag process
U           # Untag all
c           # Command line
H           # Hide/show threads
K           # Show/hide kernel threads
```

---

### 🔥 bottom (btm)

**Yet another cross-platform graphical process/system monitor**

```
🌐 Website → https://github.com/ClementTsang/bottom
📦 Install  → brew install bottom
✨ Features → Graphs, widgets, cross-platform
```

#### 📥 Installation

```bash
# macOS
brew install bottom

# Ubuntu/Debian (via cargo)
cargo install bottom

# Arch Linux
sudo pacman -S bottom
```

#### 📘 Basic Usage

```bash
# Start bottom
btm
bottom

# Basic mode
btm --basic

# Show battery
btm --battery

# Update rate (milliseconds)
btm --rate 1000

# Show processes as tree
btm --tree
```

---

### 💻 glances

**Cross-platform system monitoring tool**

```
🌐 Website → https://nicolargo.github.io/glances/
📦 Install  → brew install glances
🌐 Power    → Web UI, exporters, plugins
```

#### 📥 Installation

```bash
# macOS
brew install glances

# Ubuntu/Debian
sudo apt install glances

# pip
pip install glances
```

#### 📘 Basic Usage

```bash
# Start glances
glances

# Web server mode
glances -w
# Then visit http://localhost:61208

# Export to CSV
glances --export csv --export-csv-file /tmp/glances.csv

# Client/server mode
# On server:
glances -s
# On client:
glances -c server-ip
```

---

<div align="center">

## 🌐 Network Tools

</div>

### 🌍 httpie

**User-friendly HTTP client (better than curl)**

```
🌐 Website → https://httpie.io
📦 Install  → brew install httpie
✨ Power    → Human-friendly HTTP requests
```

**Why HTTPie?**

- Simple syntax
- JSON support out of the box
- Syntax highlighting
- Form submissions
- File uploads

#### 📥 Installation

```bash
# macOS
brew install httpie

# Ubuntu/Debian
sudo apt install httpie

# pip
pip install httpie
```

#### 📘 Basic Usage

```bash
# GET request
http https://api.github.com/users/defunkt

# POST JSON
http POST https://api.example.com/users name=John age:=30

# POST form data
http --form POST https://api.example.com/upload file@/path/to/file.jpg

# Custom headers
http GET https://api.example.com/data Authorization:"Bearer token"

# Download file
http --download https://example.com/file.zip

# Follow redirects
http --follow GET https://example.com

# Set timeout
http --timeout 5 GET https://example.com

# Pretty print
http --pretty all GET https://api.github.com/users/defunkt

# Verbose output
http -v GET https://example.com

# Sessions (save cookies)
http --session=./session.json GET https://example.com
```

---

### 🔍 dog

**Command-line DNS client (better than `dig`)**

```
🌐 Website → https://dns.lookup.dog
📦 Install  → brew install dog
⚡ Power    → Modern DNS queries
```

#### 📥 Installation

```bash
# macOS
brew install dog

# Arch Linux
sudo pacman -S dog

# From source
cargo install dog
```

#### 📘 Basic Usage

```bash
# Simple query
dog example.com

# Specific record type
dog example.com A
dog example.com MX
dog example.com TXT

# Use specific DNS server
dog example.com @8.8.8.8

# JSON output
dog --json example.com

# Reverse DNS
dog --reverse 8.8.8.8
```

---

### ⚡ bandwhich

**Terminal bandwidth utilization tool**

```
🌐 Website → https://github.com/imsnif/bandwhich
📦 Install  → brew install bandwhich
📊 Power    → Real-time network bandwidth monitor
```

#### 📥 Installation

```bash
# macOS
brew install bandwhich

# Arch Linux
sudo pacman -S bandwhich

# From source
cargo install bandwhich
```

#### 📘 Basic Usage

```bash
# Start monitoring (requires sudo)
sudo bandwhich

# Show processes only
sudo bandwhich --show-processes

# Show connections
sudo bandwhich --show-connections

# Raw mode (no UI)
sudo bandwhich --raw
```

---

<div align="center">

## 💾 Disk & Storage

</div>

### 📊 dust

**More intuitive version of `du`**

```
🌐 Website → https://github.com/bootandy/dust
📦 Install  → brew install dust
📈 Power    → Visual disk usage
```

**Why dust?**

- More intuitive than `du`
- Visual tree output
- Shows percentages
- Faster

#### 📥 Installation

```bash
# macOS
brew install dust

# Ubuntu/Debian (via cargo)
cargo install du-dust

# Arch Linux
sudo pacman -S dust
```

#### 📘 Basic Usage

```bash
# Analyze current directory
dust

# Analyze specific directory
dust /path/to/dir

# Limit depth
dust -d 2

# Show number of lines
dust -n 20

# Sort by size
dust -r

# Show apparent size (not disk usage)
dust -s

# Show only files (not directories)
dust -t f

# Show only directories
dust -t d

# Minimum size filter (show only >1GB)
dust -M 1G

# Output as JSON
dust -o json
```

---

### 🔍 duf

**Disk Usage/Free Utility (better than `df`)**

```
🌐 Website → https://github.com/muesli/duf
📦 Install  → brew install duf
✨ Power    → Beautiful disk usage overview
```

**Why duf?**

- User-friendly output
- Color-coded
- Shows charts
- JSON export

#### 📥 Installation

```bash
# macOS
brew install duf

# Ubuntu/Debian (via package)
sudo apt install duf

# Arch Linux
sudo pacman -S duf

# From source
go install github.com/muesli/duf@latest
```

#### 📘 Basic Usage

```bash
# Show all devices
duf

# Show only local devices
duf --only local

# Show specific filesystem
duf --only ext4,btrfs

# Hide specific mount points
duf --hide /boot,/tmp

# Sort by usage
duf --sort usage

# JSON output
duf --json

# Show inode information
duf --inodes

# Theme
duf --theme light
duf --theme dark
```

---

### 🧹 ncdu

**NCurses Disk Usage (interactive `du`)**

```
🌐 Website → https://dev.yorhel.nl/ncdu
📦 Install  → brew install ncdu
🎯 Power    → Navigate and delete large files interactively
```

#### 📥 Installation

```bash
# macOS
brew install ncdu

# Ubuntu/Debian
sudo apt install ncdu

# Fedora
sudo dnf install ncdu

# Arch Linux
sudo pacman -S ncdu
```

#### 📘 Basic Usage

```bash
# Analyze current directory
ncdu

# Analyze specific directory
ncdu /path/to/dir

# Export to file
ncdu -o output.json

# Import from file
ncdu -f output.json

# Exclude files
ncdu --exclude /path/to/exclude
```

#### ⌨️ Interactive Keys

```
↑/↓ or k/j  # Navigate
→ or Enter  # Open directory
← or h      # Go to parent directory

d           # Delete selected item
t           # Sort by name/size
g           # Show percentages
c           # Show item counts
q           # Quit
?           # Help
```

---

<div align="center">

## 🎨 Pretty Output

</div>

### 🌈 glow

**Render markdown in the terminal**

```
🌐 Website → https://github.com/charmbracelet/glow
📦 Install  → brew install glow
✨ Power    → Beautiful markdown rendering
```

#### 📥 Installation

```bash
# macOS
brew install glow

# Ubuntu/Debian
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://repo.charm.sh/apt/gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/charm.gpg
echo "deb [signed-by=/etc/apt/keyrings/charm.gpg] https://repo.charm.sh/apt/ * *" | sudo tee /etc/apt/sources.list.d/charm.list
sudo apt update && sudo apt install glow

# Arch Linux
sudo pacman -S glow

# From source
go install github.com/charmbracelet/glow@latest
```

#### 📘 Basic Usage

```bash
# Read markdown file
glow README.md

# Read from stdin
echo "# Hello" | glow -

# Browse markdown files in current dir
glow

# Specific style
glow -s dark README.md
glow -s light README.md

# Export as HTML
glow -s dark README.md > output.html

# Pager mode
glow -p README.md

# Width
glow -w 80 README.md
```

---

### 🌸 delta

**A syntax-highlighting pager for git, diff, and grep output**

```
🌐 Website → https://github.com/dandavison/delta
📦 Install  → brew install git-delta
✨ Power    → Beautiful git diffs
```

#### 📥 Installation

```bash
# macOS
brew install git-delta

# Ubuntu/Debian (via cargo)
cargo install git-delta

# Arch Linux
sudo pacman -S git-delta
```

#### 🔧 Configuration

Add to `~/.gitconfig`:

```ini
[core]
    pager = delta

[interactive]
    diffFilter = delta --color-only

[delta]
    navigate = true
    light = false
    side-by-side = true
    line-numbers = true

[merge]
    conflictstyle = diff3

[diff]
    colorMoved = default
```

#### 📘 Basic Usage

```bash
# Use with git diff
git diff

# Use with git show
git show

# Use as standalone diff tool
delta file1 file2

# Compare directories
delta --side-by-side file1 file2
```

---

### 🎨 lolcat

**Rainbow colorize output**

```
📦 Install  → brew install lolcat
🌈 Power    → Make everything colorful!
```

#### 📥 Installation

```bash
# macOS
brew install lolcat

# Ubuntu/Debian
sudo apt install lolcat

# gem
sudo gem install lolcat
```

#### 📘 Usage

```bash
# Colorize command output
echo "Hello World" | lolcat

# Colorize file
lolcat file.txt

# Use with other commands
fortune | cowsay | lolcat
ls -la | lolcat
cat ~/.zshrc | lolcat

# Animation
echo "Rainbow text" | lolcat -a

# Specific colors
echo "Hello" | lolcat -f

# Force color output
command | lolcat -f
```

---

<div align="center">

## ⚡ Shell Enhancement

</div>

### 🚀 starship

**The minimal, blazing-fast, and infinitely customizable prompt**

```
🌐 Website → https://starship.rs
📦 Install  → brew install starship
✨ Power    → Beautiful customizable prompt
```

#### 📥 Installation

```bash
# macOS
brew install starship

# Ubuntu/Debian (via script)
curl -sS https://starship.rs/install.sh | sh

# Arch Linux
sudo pacman -S starship

# Add to ~/.zshrc
eval "$(starship init zsh)"
```

#### 🔧 Configuration

Create `~/.config/starship.toml`:

```toml
# Minimal config
format = "$all"

[character]
success_symbol = "[➜](bold green)"
error_symbol = "[➜](bold red)"

[directory]
truncation_length = 3
truncate_to_repo = true

[git_branch]
symbol = " "
truncation_length = 20

[git_status]
conflicted = "🏳"
ahead = "⇡"
behind = "⇣"
diverged = "⇕"
untracked = "?"
stashed = "$"
modified = "!"
staged = "+"
renamed = "»"
deleted = "✘"

[nodejs]
symbol = " "

[python]
symbol = " "

[rust]
symbol = " "

[docker_context]
symbol = " "
```

---

### 🐠 thefuck

**Magnificent app that corrects your previous console command**

```
🌐 Website → https://github.com/nvbn/thefuck
📦 Install  → brew install thefuck
😄 Power    → Fix typos automatically
```

#### 📥 Installation

```bash
# macOS
brew install thefuck

# Ubuntu/Debian
sudo apt install python3-dev python3-pip python3-setuptools
pip3 install thefuck

# Add to ~/.zshrc
eval $(thefuck --alias)
eval $(thefuck --alias FUCK)  # Use FUCK instead of fuck
```

#### 📘 Usage

```bash
# Make a typo
$ git psuh
git: 'psuh' is not a git command. See 'git --help'.

# Fix it
$ fuck
git push [enter/↑/↓/ctrl+c]

# Example 2
$ puthon script.py
puthon: command not found

$ fuck
python script.py [enter/↑/↓/ctrl+c]
```

---

### ⚡ atuin

**Magical shell history**

```
🌐 Website → https://atuin.sh
📦 Install  → brew install atuin
✨ Power    → SQLite shell history with sync
```

#### 📥 Installation

```bash
# macOS
brew install atuin

# Ubuntu/Debian (via script)
bash <(curl https://raw.githubusercontent.com/atuinsh/atuin/main/install.sh)

# Setup
atuin import auto
atuin register -u <username> -e <email>
atuin login -u <username>

# Add to ~/.zshrc
eval "$(atuin init zsh)"
```

#### 📘 Usage

```bash
# Search history (replaces Ctrl+R)
# Just press Ctrl+R

# Search by directory
atuin search --cwd /path/to/project

# Stats
atuin stats

# Sync
atuin sync
```

---

<div align="center">

## 💡 MrDib's CLI Philosophy

</div>

### The Ultimate Terminal Setup 🎯

**Core Principles:**

1. **Speed is Sacred** ⚡

   - Use Rust-based tools when possible (ripgrep, fd, eza, bat)
   - Parallel execution (rg, fd)
   - Cache intelligently (zoxide, tldr)

2. **Beauty Matters** 🎨

   - Colors everywhere (eza, bat, delta)
   - Icons for context (eza, yazi)
   - Syntax highlighting (bat, glow)

3. **Smart Defaults** 🧠

   - Respect `.gitignore` (rg, fd)
   - Hide hidden files by default (eza, yazi)
   - Sensible keybindings (tmux, yazi)

4. **Composability** 🔗

   - Pipe everything: `rg | fzf | xargs bat`
   - Combine tools creatively
   - Output formats that work together

5. **Security First** 🔐

   - Use `pass` for passwords
   - Use `doppler` for secrets
   - Never commit secrets to git
   - Use GPG encryption

6. **Configuration as Code** 📝

   - Dotfiles in Git
   - Use GNU Stow for management
   - Document everything
   - Automate setup

7. **Learn Incrementally** 📚
   - Start with `tldr`
   - Master one tool at a time
   - Build muscle memory
   - Share knowledge

### Recommended Learning Path 🗺️

```
Week 1-2: Replace Basics
  ├── cat → bat
  ├── ls → eza
  ├── cd → zoxide
  ├── find → fd
  └── grep → ripgrep

Week 3-4: Terminal Mastery
  ├── Install tmux
  ├── Learn sessions & windows
  ├── Configure keybindings
  └── Create project scripts

Week 5-6: Data Wrangling
  ├── Install jq
  ├── Practice with APIs
  ├── Combine with rg/fd
  └── Process logs

Week 7-8: DevOps Tools
  ├── GitHub CLI (gh)
  ├── Doppler for secrets
  ├── Pass for passwords
  └── HTTP tools (httpie, curl)

Week 9-10: System Management
  ├── File manager (yazi)
  ├── System monitoring (btm, htop)
  ├── Disk usage (dust, duf, ncdu)
  └── Network tools (dog, bandwhich)

Week 11-12: Polish & Automate
  ├── Setup dotfiles repo
  ├── Learn GNU Stow
  ├── Configure starship prompt
  ├── Create shortcuts & aliases
  └── Write automation scripts
```

### Essential Aliases (Complete Set) 🎯

Add to `~/.zshrc`:

```bash
# ═══════════════════════════════════════════
# Modern CLI Tools - Complete Alias Collection
# ═══════════════════════════════════════════

# ─────────────────────────────────────────
# Navigation (zoxide + fzf)
# ─────────────────────────────────────────
alias zi='z -i'                     # Interactive selection
alias zb='z -'                      # Go back
alias zh='z ~'                      # Go home

# ─────────────────────────────────────────
# Search (ripgrep)
# ─────────────────────────────────────────
alias rg='rg --smart-case --hidden'
alias rgi='rg -i'                   # Case insensitive
alias rgf='rg --files | rg'         # Search filenames
alias rgl='rg -l'                   # Files with matches
alias rgc='rg --count'              # Count matches

# ─────────────────────────────────────────
# Find (fd)
# ─────────────────────────────────────────
alias fd='fd --hidden --follow'
alias fda='fd -HI'                  # All files
alias fdd='fd -t d'                 # Directories
alias fdf='fd -t f'                 # Files only
alias fde='fd -t x'                 # Executables

# ─────────────────────────────────────────
# List Files (eza)
# ─────────────────────────────────────────
alias ls='eza --icons'
alias ll='eza -lh --icons --git'
alias la='eza -lha --icons --git'
alias lt='eza --tree --level=2 --icons'
alias l='eza -lh --icons --git --group-directories-first'

# ─────────────────────────────────────────
# View Files (bat)
# ─────────────────────────────────────────
alias cat='bat --paging=never'
alias less='bat'
alias more='bat'

# ─────────────────────────────────────────
# Terminal Multiplexer (tmux)
# ─────────────────────────────────────────
alias ta='tmux attach'
alias tad='tmux attach -d -t'
alias ts='tmux new-session -s'
alias tl='tmux list-sessions'
alias tksv='tmux kill-server'
alias tkss='tmux kill-session -t'

# ─────────────────────────────────────────
# JSON Processing (jq)
# ─────────────────────────────────────────
alias json='jq "."'                 # Pretty print
alias jsonc='jq -c "."'             # Compact

# ─────────────────────────────────────────
# GitHub CLI (gh)
# ─────────────────────────────────────────
alias ghpr='gh pr create'
alias ghprv='gh pr view --web'
alias ghpc='gh pr checkout'
alias ghpl='gh pr list'
alias ghi='gh issue create'
alias ghb='gh browse'

# ─────────────────────────────────────────
# System Monitoring
# ─────────────────────────────────────────
alias top='btm'                     # bottom
alias ports='lsof -iTCP -sTCP:LISTEN -n -P'

# ─────────────────────────────────────────
# Disk Usage
# ─────────────────────────────────────────
alias du='dust'
alias df='duf'

# ─────────────────────────────────────────
# Help & Documentation
# ─────────────────────────────────────────
alias help='tldr'
alias h='tldr'

# ─────────────────────────────────────────
# File Manager (yazi)
# ─────────────────────────────────────────
alias y='ya'
alias yi='ya .'
alias yd='ya ~/Downloads'

# ─────────────────────────────────────────
# Dotfiles Management (stow)
# ─────────────────────────────────────────
alias dots='cd ~/dotfiles'
alias dotfiles='cd ~/dotfiles'
alias dotgit='git -C ~/dotfiles'
alias dotpush='dotgit push'
alias dotpull='dotgit pull'

# ─────────────────────────────────────────
# Network Tools
# ─────────────────────────────────────────
alias curl='http'                   # Use httpie
alias dig='dog'                     # Use dog
```

### Complete Installation Script 🚀

Create `~/setup-complete-cli.sh`:

```bash
#!/bin/bash

set -e

echo "🚀 Installing Complete Modern CLI Toolset..."
echo ""

# Check if Homebrew is installed
if ! command -v brew &> /dev/null; then
    echo "📦 Installing Homebrew..."
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
fi

echo ""
echo "⚡ Installing Essential Tools..."

# Core tools
brew install zoxide fzf bat eza fd ripgrep

# Terminal multiplexer
brew install tmux

# Data processing
brew install jq

# Cloud & DevOps
brew install gh doppler

# Security
brew install pass gnupg

# System utilities
brew install stow tldr

# File manager
brew install yazi ffmpegthumb unar jq poppler imagemagick

# System monitoring
brew install htop bottom glances

# Network tools
brew install httpie dog bandwhich

# Disk usage
brew install dust duf ncdu

# Pretty output
brew install glow git-delta lolcat

# Shell enhancement
brew install starship thefuck atuin

echo ""
echo "📚 Updating tldr cache..."
tldr --update

echo ""
echo "🎨 Installing Oh My Zsh (optional)..."
read -p "Install Oh My Zsh? (y/N) " -n 1 -r
echo
if [[ $REPLY =~ ^[Yy]$ ]]; then
    sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
fi

echo ""
echo "✅ Installation Complete!"
echo ""
echo "📝 Next Steps:"
echo "  1. Copy aliases to ~/.zshrc"
echo "  2. Setup dotfiles: mkdir ~/dotfiles && cd ~/dotfiles && git init"
echo "  3. Configure tmux: touch ~/.tmux.conf"
echo "  4. Configure starship: touch ~/.config/starship.toml"
echo "  5. Setup pass: gpg --generate-key && pass init your-key-id"
echo "  6. Login to gh: gh auth login"
echo "  7. Login to doppler: doppler login"
echo "  8. Reload shell: source ~/.zshrc"
echo ""
echo "🎉 Happy Hacking!"
```

Make executable:

```bash
chmod +x ~/setup-complete-cli.sh
./setup-complete-cli.sh
```

---

<div align="center">

## 🎁 Bonus: CLI Tools Comparison

</div>

### Quick Reference Chart 📊

| Old Tool | New Tool     | Why Switch?                                        |
| -------- | ------------ | -------------------------------------------------- |
| `cat`    | `bat`        | Syntax highlighting, line numbers, Git integration |
| `ls`     | `eza`        | Icons, colors, Git status, tree view               |
| `cd`     | `zoxide`     | Smart jumping, frecency algorithm                  |
| `find`   | `fd`         | Intuitive syntax, faster, respects .gitignore      |
| `grep`   | `ripgrep`    | 5-10x faster, smart defaults, beautiful output     |
| `du`     | `dust`       | Visual tree, percentages, intuitive                |
| `df`     | `duf`        | Colorful, charts, user-friendly                    |
| `top`    | `btm`/`htop` | Modern UI, interactive, better UX                  |
| `curl`   | `httpie`     | Human-friendly syntax, JSON support                |
| `dig`    | `dog`        | Modern DNS client, colorful output                 |
| `man`    | `tldr`       | Quick examples, get started fast                   |

---

<div align="center">

## 🎯 Final Tips & Best Practices

</div>

### Do's ✅

1. **Start Small**: Don't install everything at once
2. **Learn One Tool**: Master one before moving to the next
3. **Create Aliases**: Build muscle memory with shortcuts
4. **Document Everything**: Keep notes on your setup
5. **Use Dotfiles**: Version control your configurations
6. **Automate Setup**: Script your installation process
7. **Share Knowledge**: Help others learn these tools
8. **Stay Updated**: Regularly update your tools
9. **Backup Configs**: Use Git for dotfiles
10. **Experiment**: Try new tools and workflows

### Don'ts ❌

1. **Don't Replace Everything**: Keep what works
2. **Don't Skip Documentation**: Read the README
3. **Don't Forget Backups**: Always backup before changes
4. **Don't Commit Secrets**: Use proper secret management
5. **Don't Ignore Security**: GPG encrypt sensitive data
6. **Don't Skip Testing**: Test aliases/functions before use
7. **Don't Overload ZSH**: Too many plugins slow down shell
8. **Don't Force Tools**: If old tool works, that's fine
9. **Don't Ignore Updates**: Security patches matter
10. **Don't Stop Learning**: CLI tools are always evolving

---

<div align="center">

_Remember: The best CLI tool is the one you actually use. Start simple, grow gradually, automate relentlessly!_ 🚀

**Now go forth and conquer that terminal!** ⚡

**If you found this helpful, give it a ⭐ star and share with fellow developers!**

**Happy Command-Line Adventures!** 🎉

</div>
