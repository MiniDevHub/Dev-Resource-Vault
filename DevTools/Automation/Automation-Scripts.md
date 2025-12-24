<div align="center">

# 🤖 Automation Scripts & Workflow Enhancers

<img src="https://img.shields.io/badge/Automation-Smart-purple?style=for-the-badge" alt="Automation">
<img src="https://img.shields.io/badge/Efficiency-Maximum-green?style=for-the-badge" alt="Efficiency">
<img src="https://img.shields.io/badge/Productivity-10x-blue?style=for-the-badge" alt="Productivity">

### _Making your computer work for you, so you can focus on the fun stuff_ 🎉

**Because repetitive tasks are for computers, not humans** 💪

</div>

---

## 📚 Table of Contents

- [🐚 Shell Script Automation](#-shell-script-automation)
- [🐍 Python Automation](#-python-automation)
- [⚡ JavaScript/Node.js Automation](#-javascriptnodejs-automation)
- [🚀 CI/CD Automation](#-cicd-automation)
- [🌐 Workflow Automation Tools](#-workflow-automation-tools)
- [⚙️ Task Runners & Build Tools](#️-task-runners--build-tools)
- [💡 Automation Best Practices](#-automation-best-practices)

---

<div align="center">

## 🐚 Shell Script Automation

</div>

### Essential Shell Aliases ⚡

```bash
# ═══════════════════════════════════════════
# Add to ~/.bashrc or ~/.zshrc
# ═══════════════════════════════════════════

# Navigation Shortcuts
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias ~='cd ~'
alias -- -='cd -'

# List files
alias ll='ls -lah'
alias la='ls -A'
alias l='ls -CF'
alias lt='ls -ltrh'         # Sort by date
alias lsize='ls -lSrh'      # Sort by size

# Git shortcuts
alias g='git'
alias gs='git status -sb'
alias ga='git add'
alias gaa='git add .'
alias gc='git commit -m'
alias gca='git commit -am'
alias gp='git push'
alias gpl='git pull'
alias gco='git checkout'
alias gcb='git checkout -b'
alias gb='git branch'
alias gl='git log --oneline --graph --all --decorate'
alias gd='git diff'
alias gdc='git diff --cached'

# Development shortcuts
alias code.='code .'
alias c='clear'
alias h='history'
alias reload='source ~/.zshrc'  # or ~/.bashrc

# Package management shortcuts
alias ni='npm install'
alias nid='npm install -D'
alias nrd='npm run dev'
alias nrb='npm run build'
alias nrs='npm run start'
alias nrt='npm run test'
alias nrl='npm run lint'

alias yi='yarn install'
alias ya='yarn add'
alias yad='yarn add -D'
alias yrd='yarn dev'
alias yrb='yarn build'

# Python shortcuts
alias py='python3'
alias pip='pip3'
alias venv='python3 -m venv venv'
alias activate='source venv/bin/activate'

# Docker shortcuts
alias d='docker'
alias dc='docker-compose'
alias dcu='docker-compose up'
alias dcd='docker-compose down'
alias dcr='docker-compose restart'
alias dps='docker ps'
alias dpsa='docker ps -a'
alias di='docker images'

# ═══════════════════════════════════════════
# Advanced Aliases (Functions)
# ═══════════════════════════════════════════

# Clean node_modules and reinstall
freshstart() {
    echo "Cleaning node_modules and package-lock.json..."
    rm -rf node_modules package-lock.json
    echo "Running npm install..."
    npm install
    echo "✓ Fresh start complete!"
}

# Kill process on port
killport() {
    if [ -z "$1" ]; then
        echo "Usage: killport <port_number>"
        return 1
    fi
    echo "Killing process on port $1..."
    lsof -ti:$1 | xargs kill -9
    echo "✓ Port $1 is now free"
}

# Generate random password
genpass() {
    local length=${1:-16}
    head /dev/urandom | tr -dc A-Za-z0-9_!@#$%^&*()_+=- | head -c $length
    echo ""
}

# Create timestamped backup
backup() {
    local filename=${1:-.}
    local backup_name="${filename}_backup_$(date +%Y%m%d_%H%M%S)"

    if [ -d "$filename" ]; then
        tar -czf "${backup_name}.tar.gz" "$filename"
    else
        cp "$filename" "$backup_name"
    fi

    echo "✓ Backup created: $backup_name"
}

# Search in files (excluding common directories)
findinfiles() {
    if [ -z "$1" ]; then
        echo "Usage: findinfiles <search_term>"
        return 1
    fi
    grep -r --exclude-dir={node_modules,.git,.next,dist,build} \
           --exclude="*.{min.js,map}" \
           --color=auto "$1" .
}

# Git push with lease (safer force push)
pushf() {
    git push --force-with-lease
}

# Create and enter directory
mkcd() {
    mkdir -p "$1" && cd "$1"
}

# Extract any archive
extract() {
    if [ -f "$1" ]; then
        case "$1" in
            *.tar.bz2)   tar xjf "$1"     ;;
            *.tar.gz)    tar xzf "$1"     ;;
            *.bz2)       bunzip2 "$1"     ;;
            *.rar)       unrar x "$1"     ;;
            *.gz)        gunzip "$1"      ;;
            *.tar)       tar xf "$1"      ;;
            *.tbz2)      tar xjf "$1"     ;;
            *.tgz)       tar xzf "$1"     ;;
            *.zip)       unzip "$1"       ;;
            *.Z)         uncompress "$1"  ;;
            *.7z)        7z x "$1"        ;;
            *)           echo "Cannot extract '$1'" ;;
        esac
    else
        echo "'$1' is not a valid file"
    fi
}

# Get weather
weather() {
    local city=${1:-London}
    curl -s "wttr.in/$city?format=3"
}

# Show disk usage of current directory
diskusage() {
    du -sh * | sort -rh | head -20
}

# Find largest files
largest() {
    local count=${1:-10}
    find . -type f -exec ls -lh {} \; | sort -rh -k5 | head -n $count
}

# Quick note taking
note() {
    echo "$(date '+%Y-%m-%d %H:%M:%S') - $*" >> ~/notes.txt
}

# View notes
notes() {
    if [ -f ~/notes.txt ]; then
        cat ~/notes.txt
    else
        echo "No notes yet. Use 'note' command to add one."
    fi
}

# Git commit with AI-suggested message (requires GitHub Copilot CLI)
gac() {
    git add .
    echo "Generating commit message..."
    gh copilot suggest "git commit message for these changes"
}

# Create React component boilerplate
create-component() {
    local name=$1
    if [ -z "$name" ]; then
        echo "Usage: create-component <ComponentName>"
        return 1
    fi

    mkdir -p "$name"

    cat > "$name/$name.jsx" << EOF
import React from 'react';
import styles from './$name.module.css';

const $name = () => {
  return (
    <div className={styles.container}>
      <h1>$name Component</h1>
    </div>
  );
};

export default $name;
EOF

    cat > "$name/$name.module.css" << EOF
.container {
  /* Add your styles here */
}
EOF

    cat > "$name/index.js" << EOF
export { default } from './$name';
EOF

    echo "✓ Component '$name' created successfully!"
}

# Docker cleanup
docker-cleanup() {
    echo "Cleaning up Docker resources..."
    docker system prune -af --volumes
    echo "✓ Docker cleanup complete!"
}

# Start local dev environment
devup() {
    echo "Starting development environment..."

    # Start Docker containers if docker-compose.yml exists
    if [ -f "docker-compose.yml" ]; then
        docker-compose up -d
    fi

    # Install dependencies if needed
    if [ ! -d "node_modules" ]; then
        npm install
    fi

    # Start dev server
    npm run dev
}
```

---

### Productivity Scripts 🚀

```bash
#!/bin/bash
# ═══════════════════════════════════════════
# Daily Development Setup Script
# ═══════════════════════════════════════════
# Save as: ~/bin/dev-setup.sh

echo "🚀 Setting up development environment..."

# Start Docker
echo "Starting Docker..."
open -a Docker

# Wait for Docker to start
while ! docker info > /dev/null 2>&1; do
    echo "Waiting for Docker to start..."
    sleep 1
done
echo "✓ Docker is running"

# Start common services
if [ -d ~/projects/backend ]; then
    echo "Starting backend services..."
    cd ~/projects/backend
    docker-compose up -d
    echo "✓ Backend services started"
fi

# Open common apps
echo "Opening development tools..."
open -a "Visual Studio Code"
open -a "iTerm"
open -a "Google Chrome"

# Update all repositories
echo "Updating repositories..."
for repo in ~/projects/*/; do
    if [ -d "$repo/.git" ]; then
        echo "Updating $(basename $repo)..."
        cd "$repo"
        git fetch origin

        # Check if behind
        LOCAL=$(git rev-parse @)
        REMOTE=$(git rev-parse @{u} 2>/dev/null)

        if [ "$LOCAL" != "$REMOTE" ] && [ ! -z "$REMOTE" ]; then
            echo "  → Pulling changes..."
            git pull
        else
            echo "  ✓ Up to date"
        fi
    fi
done

echo "✓ Development environment ready!"

# ═══════════════════════════════════════════
# Project Cleanup Script
# ═══════════════════════════════════════════
# Save as: ~/bin/cleanup.sh

#!/bin/bash

echo "🧹 Starting cleanup..."

# Clean npm caches
echo "Cleaning npm cache..."
npm cache clean --force

# Clean yarn cache
echo "Cleaning yarn cache..."
yarn cache clean

# Clean pip cache
echo "Cleaning pip cache..."
pip3 cache purge

# Clean Docker
echo "Cleaning Docker..."
docker system prune -af --volumes

# Clean old log files
echo "Cleaning old logs..."
find ~/Library/Logs -name "*.log" -mtime +7 -delete

# Clean Downloads folder (files older than 30 days)
echo "Cleaning old downloads..."
find ~/Downloads -type f -mtime +30 -delete

# Empty Trash
echo "Emptying Trash..."
rm -rf ~/.Trash/*

echo "✓ Cleanup complete!"

# ═══════════════════════════════════════════
# Git Branch Cleanup
# ═══════════════════════════════════════════
# Save as: ~/bin/git-cleanup.sh

#!/bin/bash

echo "🔄 Cleaning up Git branches..."

# Fetch all remotes
git fetch --all --prune

# Delete merged local branches
echo "Deleting merged branches..."
git branch --merged main | grep -v "\* main" | xargs -n 1 git branch -d

# Show remaining branches
echo ""
echo "Remaining branches:"
git branch -a

# ═══════════════════════════════════════════
# Project Statistics
# ═══════════════════════════════════════════
# Save as: ~/bin/project-stats.sh

#!/bin/bash

echo "📊 Project Statistics"
echo "===================="
echo ""

# Total lines of code
echo "Lines of Code:"
find . -name "*.js" -o -name "*.jsx" -o -name "*.ts" -o -name "*.tsx" | xargs wc -l | tail -1

echo ""

# File counts by type
echo "File Counts:"
echo "JavaScript: $(find . -name "*.js" -o -name "*.jsx" | wc -l)"
echo "TypeScript: $(find . -name "*.ts" -o -name "*.tsx" | wc -l)"
echo "CSS/SCSS: $(find . -name "*.css" -o -name "*.scss" | wc -l)"
echo "Tests: $(find . -name "*.test.js" -o -name "*.spec.js" | wc -l)"

echo ""

# Git statistics
echo "Git Statistics:"
echo "Total commits: $(git rev-list --all --count)"
echo "Contributors: $(git shortlog -sn --all | wc -l)"
echo "Branches: $(git branch -a | wc -l)"

# ═══════════════════════════════════════════
# Batch File Renaming
# ═══════════════════════════════════════════
# Save as: ~/bin/batch-rename.sh

#!/bin/bash

if [ $# -lt 3 ]; then
    echo "Usage: $0 <directory> <old_pattern> <new_pattern>"
    echo "Example: $0 . 'Component' 'Widget'"
    exit 1
fi

DIRECTORY=$1
OLD_PATTERN=$2
NEW_PATTERN=$3

echo "Renaming files in $DIRECTORY..."
echo "Pattern: $OLD_PATTERN → $NEW_PATTERN"
echo ""

count=0
for file in "$DIRECTORY"/*; do
    if [[ -f "$file" ]]; then
        filename=$(basename "$file")
        newname=$(echo "$filename" | sed "s/$OLD_PATTERN/$NEW_PATTERN/g")

        if [ "$filename" != "$newname" ]; then
            mv "$file" "$DIRECTORY/$newname"
            echo "✓ $filename → $newname"
            ((count++))
        fi
    fi
done

echo ""
echo "Renamed $count files"
```

---

<div align="center">

## 🐍 Python Automation

</div>

### Python Automation Scripts 💡

```python
#!/usr/bin/env python3
# ═══════════════════════════════════════════
# File Organization Script
# ═══════════════════════════════════════════

import os
import shutil
from pathlib import Path
from datetime import datetime

def organize_downloads():
    """
    Organize Downloads folder by file type
    """
    downloads_path = Path.home() / "Downloads"

    # Define file categories
    categories = {
        'Images': ['.jpg', '.jpeg', '.png', '.gif', '.bmp', '.svg', '.webp'],
        'Documents': ['.pdf', '.doc', '.docx', '.txt', '.rtf', '.odt'],
        'Spreadsheets': ['.xls', '.xlsx', '.csv'],
        'Presentations': ['.ppt', '.pptx', '.key'],
        'Archives': ['.zip', '.rar', '.7z', '.tar', '.gz'],
        'Videos': ['.mp4', '.avi', '.mkv', '.mov', '.wmv'],
        'Audio': ['.mp3', '.wav', '.flac', '.m4a', '.aac'],
        'Code': ['.py', '.js', '.html', '.css', '.json', '.xml']
    }

    # Create category folders
    for category in categories:
        category_path = downloads_path / category
        category_path.mkdir(exist_ok=True)

    # Move files
    moved_count = 0
    for file_path in downloads_path.iterdir():
        if file_path.is_file():
            file_ext = file_path.suffix.lower()

            for category, extensions in categories.items():
                if file_ext in extensions:
                    dest = downloads_path / category / file_path.name

                    # Handle duplicate names
                    counter = 1
                    while dest.exists():
                        name = file_path.stem
                        dest = downloads_path / category / f"{name}_{counter}{file_ext}"
                        counter += 1

                    shutil.move(str(file_path), str(dest))
                    print(f"✓ Moved {file_path.name} → {category}/")
                    moved_count += 1
                    break

    print(f"\n✓ Organized {moved_count} files")

# ═══════════════════════════════════════════
# Clean Temporary Files
# ═══════════════════════════════════════════

def clean_temp_files(directory="."):
    """
    Remove temporary and cache files
    """
    temp_extensions = ['.tmp', '.log', '.cache', '.DS_Store', 'Thumbs.db']
    temp_folders = ['__pycache__', '.pytest_cache', '.mypy_cache', 'node_modules/.cache']

    removed_count = 0

    # Remove temp files
    for root, dirs, files in os.walk(directory):
        for file in files:
            if any(file.endswith(ext) for ext in temp_extensions):
                file_path = os.path.join(root, file)
                try:
                    os.remove(file_path)
                    print(f"✗ Deleted {file_path}")
                    removed_count += 1
                except Exception as e:
                    print(f"✗ Could not delete {file_path}: {e}")

    # Remove temp folders
    for root, dirs, files in os.walk(directory):
        for dir_name in dirs:
            if dir_name in temp_folders:
                dir_path = os.path.join(root, dir_name)
                try:
                    shutil.rmtree(dir_path)
                    print(f"✗ Deleted folder {dir_path}")
                    removed_count += 1
                except Exception as e:
                    print(f"✗ Could not delete {dir_path}: {e}")

    print(f"\n✓ Removed {removed_count} temp files/folders")

# ═══════════════════════════════════════════
# Batch Image Resize
# ═══════════════════════════════════════════

from PIL import Image

def batch_resize_images(directory, max_width=1920, max_height=1080):
    """
    Resize all images in directory to max dimensions
    Requires: pip install Pillow
    """
    image_extensions = ['.jpg', '.jpeg', '.png', '.gif', '.bmp']

    for file in Path(directory).iterdir():
        if file.suffix.lower() in image_extensions:
            try:
                with Image.open(file) as img:
                    # Calculate new size
                    img.thumbnail((max_width, max_height), Image.Resampling.LANCZOS)

                    # Save optimized image
                    output_path = file.parent / f"resized_{file.name}"
                    img.save(output_path, optimize=True, quality=85)
                    print(f"✓ Resized {file.name}")
            except Exception as e:
                print(f"✗ Error processing {file.name}: {e}")

# ═══════════════════════════════════════════
# API Data Fetcher
# ═══════════════════════════════════════════

import requests
import json

def fetch_weather(city, api_key="YOUR_API_KEY"):
    """
    Fetch weather data from OpenWeatherMap
    """
    base_url = "http://api.openweathermap.org/data/2.5/weather"
    params = {
        "q": city,
        "appid": api_key,
        "units": "metric"
    }

    try:
        response = requests.get(base_url, params=params)
        response.raise_for_status()
        data = response.json()

        print(f"Weather in {city}:")
        print(f"  Temperature: {data['main']['temp']}°C")
        print(f"  Feels like: {data['main']['feels_like']}°C")
        print(f"  Humidity: {data['main']['humidity']}%")
        print(f"  Conditions: {data['weather'][0]['description']}")

        return data
    except requests.exceptions.RequestException as e:
        print(f"Error fetching weather: {e}")
        return None

# ═══════════════════════════════════════════
# GitHub Repository Manager
# ═══════════════════════════════════════════

def create_github_repo(repo_name, description="", private=False):
    """
    Create a GitHub repository
    Requires: pip install PyGithub
    """
    from github import Github

    token = os.getenv("GITHUB_TOKEN")
    if not token:
        print("Error: GITHUB_TOKEN environment variable not set")
        return

    try:
        g = Github(token)
        user = g.get_user()
        repo = user.create_repo(
            repo_name,
            description=description,
            private=private
        )
        print(f"✓ Repository created: {repo.html_url}")
        return repo
    except Exception as e:
        print(f"Error creating repository: {e}")

# ═══════════════════════════════════════════
# CSV to JSON Converter
# ═══════════════════════════════════════════

import csv

def csv_to_json(csv_file, json_file):
    """
    Convert CSV file to JSON
    """
    data = []

    with open(csv_file, 'r') as file:
        csv_reader = csv.DictReader(file)
        for row in csv_reader:
            data.append(row)

    with open(json_file, 'w') as file:
        json.dump(data, file, indent=2)

    print(f"✓ Converted {csv_file} to {json_file}")

# ═══════════════════════════════════════════
# Project Scaffolder
# ═══════════════════════════════════════════

def create_project(project_name, project_type="python"):
    """
    Create project boilerplate
    """
    project_path = Path(project_name)
    project_path.mkdir(exist_ok=True)

    if project_type == "python":
        # Create Python project structure
        (project_path / "src").mkdir()
        (project_path / "tests").mkdir()
        (project_path / "docs").mkdir()

        # Create files
        (project_path / "README.md").write_text(f"# {project_name}\n")
        (project_path / "requirements.txt").write_text("")
        (project_path / ".gitignore").write_text("__pycache__/\n*.pyc\nvenv/\n.env\n")
        (project_path / "src" / "__init__.py").write_text("")
        (project_path / "tests" / "__init__.py").write_text("")

    elif project_type == "node":
        # Create Node.js project structure
        (project_path / "src").mkdir()
        (project_path / "tests").mkdir()
        (project_path / "public").mkdir()

        package_json = {
            "name": project_name,
            "version": "1.0.0",
            "description": "",
            "main": "src/index.js",
            "scripts": {
                "start": "node src/index.js",
                "test": "jest"
            }
        }

        (project_path / "package.json").write_text(json.dumps(package_json, indent=2))
        (project_path / "README.md").write_text(f"# {project_name}\n")
        (project_path / ".gitignore").write_text("node_modules/\n.env\ndist/\n")

    print(f"✓ Project '{project_name}' created successfully!")

# ═══════════════════════════════════════════
# Main Menu
# ═══════════════════════════════════════════

def main():
    print("🤖 Python Automation Script")
    print("=" * 40)
    print("1. Organize Downloads")
    print("2. Clean Temp Files")
    print("3. Batch Resize Images")
    print("4. Fetch Weather")
    print("5. Create GitHub Repo")
    print("6. Convert CSV to JSON")
    print("7. Create Project")
    print("0. Exit")
    print("=" * 40)

    choice = input("\nSelect an option: ")

    if choice == "1":
        organize_downloads()
    elif choice == "2":
        directory = input("Enter directory (default: current): ") or "."
        clean_temp_files(directory)
    elif choice == "3":
        directory = input("Enter directory: ")
        batch_resize_images(directory)
    elif choice == "4":
        city = input("Enter city name: ")
        fetch_weather(city)
    elif choice == "5":
        repo_name = input("Repository name: ")
        description = input("Description: ")
        create_github_repo(repo_name, description)
    elif choice == "6":
        csv_file = input("CSV file: ")
        json_file = input("JSON file: ")
        csv_to_json(csv_file, json_file)
    elif choice == "7":
        project_name = input("Project name: ")
        project_type = input("Project type (python/node): ")
        create_project(project_name, project_type)
    elif choice == "0":
        print("Goodbye!")
    else:
        print("Invalid option")

if __name__ == "__main__":
    main()
```

---

<div align="center">

## ⚡ JavaScript/Node.js Automation

</div>

### Node.js CLI Tools 🚀

```javascript
#!/usr/bin/env node
// ═══════════════════════════════════════════
// Modern CLI Tool with Commander.js
// ═══════════════════════════════════════════

const { program } = require("commander");
const { execSync } = require("child_process");
const fs = require("fs").promises;
const path = require("path");
const chalk = require("chalk");
const ora = require("ora");

program
  .name("devtool")
  .description("CLI automation tool for developers")
  .version("1.0.0");

// ═══════════════════════════════════════════
// Create React Component
// ═══════════════════════════════════════════

program
  .command("create-component <name>")
  .description("Create a new React component with boilerplate")
  .option("-t, --typescript", "Use TypeScript")
  .option("-s, --styled", "Include styled-components")
  .action(async (name, options) => {
    const spinner = ora(`Creating component ${name}...`).start();

    try {
      const componentDir = path.join(process.cwd(), name);
      await fs.mkdir(componentDir, { recursive: true });

      const ext = options.typescript ? "tsx" : "jsx";
      const styleExt = options.styled ? "styles.ts" : "module.css";

      // Component file
      const componentContent = `import React from 'react';
${
  options.styled
    ? "import { Container } from './" + name + ".styles';"
    : "import styles from './" + name + ".module.css';"
}

interface ${name}Props {
  // Add props here
}

const ${name}: React.FC<${name}Props> = () => {
  return (
    ${options.styled ? "<Container>" : `<div className={styles.container}>`}
      <h1>${name} Component</h1>
    ${options.styled ? "</Container>" : "</div>"}
  );
};

export default ${name};
`;

      await fs.writeFile(
        path.join(componentDir, `${name}.${ext}`),
        componentContent
      );

      // Style file
      if (options.styled) {
        const styleContent = `import styled from 'styled-components';

export const Container = styled.div\`
  /* Add your styles here */
\`;
`;
        await fs.writeFile(
          path.join(componentDir, `${name}.styles.ts`),
          styleContent
        );
      } else {
        const cssContent = `.container {
  /* Add your styles here */
}
`;
        await fs.writeFile(
          path.join(componentDir, `${name}.module.css`),
          cssContent
        );
      }

      // Index file
      await fs.writeFile(
        path.join(componentDir, "index.ts"),
        `export { default } from './${name}';\n`
      );

      spinner.succeed(chalk.green(`Component ${name} created successfully!`));
    } catch (error) {
      spinner.fail(chalk.red(`Error creating component: ${error.message}`));
    }
  });

// ═══════════════════════════════════════════
// Update Package Version
// ═══════════════════════════════════════════

program
  .command("version <type>")
  .description("Update package.json version (major|minor|patch)")
  .action(async (type) => {
    const spinner = ora("Updating version...").start();

    try {
      execSync(`npm version ${type}`, { stdio: "inherit" });
      spinner.succeed(chalk.green("Version updated successfully!"));
    } catch (error) {
      spinner.fail(chalk.red("Error updating version"));
    }
  });

// ═══════════════════════════════════════════
// Deploy Script
// ═══════════════════════════════════════════

program
  .command("deploy")
  .description("Run deployment sequence")
  .option(
    "-e, --environment <env>",
    "Environment (staging|production)",
    "staging"
  )
  .action(async (options) => {
    const commands = [
      { cmd: "npm run lint", desc: "Linting code..." },
      { cmd: "npm test", desc: "Running tests..." },
      { cmd: "npm run build", desc: "Building project..." },
    ];

    if (options.environment === "production") {
      commands.push({
        cmd: "npm run deploy:prod",
        desc: "Deploying to production...",
      });
    } else {
      commands.push({
        cmd: "npm run deploy:staging",
        desc: "Deploying to staging...",
      });
    }

    for (const { cmd, desc } of commands) {
      const spinner = ora(desc).start();

      try {
        execSync(cmd, { stdio: "inherit" });
        spinner.succeed(chalk.green(desc.replace("...", " complete!")));
      } catch (error) {
        spinner.fail(chalk.red(`${desc} failed`));
        process.exit(1);
      }
    }

    console.log(chalk.green.bold("\n✓ Deployment complete!"));
  });

// ═══════════════════════════════════════════
// Git Workflow
// ═══════════════════════════════════════════

program
  .command("git-flow <type> <name>")
  .description("Create feature/bugfix/hotfix branch and checkout")
  .action((type, name) => {
    const branchName = `${type}/${name}`;
    const spinner = ora(`Creating branch ${branchName}...`).start();

    try {
      execSync(`git checkout -b ${branchName}`, { stdio: "inherit" });
      spinner.succeed(chalk.green(`Branch ${branchName} created!`));
    } catch (error) {
      spinner.fail(chalk.red("Error creating branch"));
    }
  });

// ═══════════════════════════════════════════
// Clean Project
// ═══════════════════════════════════════════

program
  .command("clean")
  .description("Clean project (node_modules, dist, cache)")
  .action(async () => {
    const spinner = ora("Cleaning project...").start();

    const dirsToClean = ["node_modules", "dist", "build", ".next", "coverage"];

    for (const dir of dirsToClean) {
      try {
        await fs.rm(dir, { recursive: true, force: true });
        spinner.text = `Cleaned ${dir}`;
      } catch (error) {
        // Directory might not exist, ignore
      }
    }

    spinner.succeed(chalk.green("Project cleaned successfully!"));

    const install = await confirm("Install dependencies?");
    if (install) {
      const installSpinner = ora("Installing dependencies...").start();
      execSync("npm install", { stdio: "inherit" });
      installSpinner.succeed(chalk.green("Dependencies installed!"));
    }
  });

// ═══════════════════════════════════════════
// Utility Functions
// ═══════════════════════════════════════════

const confirm = (message) => {
  return new Promise((resolve) => {
    const readline = require("readline").createInterface({
      input: process.stdin,
      output: process.stdout,
    });

    readline.question(`${message} (y/n): `, (answer) => {
      readline.close();
      resolve(answer.toLowerCase() === "y");
    });
  });
};

program.parse();
```

<div align="center">

## 🚀 CI/CD Automation

</div>

### GitHub Actions Workflows 🔄

```yaml
# ═══════════════════════════════════════════
# .github/workflows/ci-cd.yml
# Complete CI/CD Pipeline
# ═══════════════════════════════════════════

name: CI/CD Pipeline

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main, develop]
  workflow_dispatch: # Manual trigger

env:
  NODE_VERSION: "20.x"
  REGISTRY: ghcr.io
  IMAGE_NAME: ${{ github.repository }}

jobs:
  # ═══════════════════════════════════════════
  # Code Quality Checks
  # ═══════════════════════════════════════════
  quality:
    name: Code Quality
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4
        with:
          fetch-depth: 0 # Full history for better analysis

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: ${{ env.NODE_VERSION }}
          cache: "npm"

      - name: Install dependencies
        run: npm ci

      - name: Run ESLint
        run: npm run lint

      - name: Run Prettier check
        run: npm run format:check

      - name: Run type checking
        run: npm run type-check

      - name: Check for TODO comments
        run: |
          if grep -r "TODO" src/; then
            echo "⚠️ TODO comments found in source code"
            exit 1
          fi

  # ═══════════════════════════════════════════
  # Security Scanning
  # ═══════════════════════════════════════════
  security:
    name: Security Scan
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Run Trivy vulnerability scanner
        uses: aquasecurity/trivy-action@master
        with:
          scan-type: "fs"
          scan-ref: "."
          format: "sarif"
          output: "trivy-results.sarif"

      - name: Upload Trivy results to GitHub Security
        uses: github/codeql-action/upload-sarif@v2
        with:
          sarif_file: "trivy-results.sarif"

      - name: Dependency audit
        run: npm audit --audit-level=moderate

  # ═══════════════════════════════════════════
  # Testing
  # ═══════════════════════════════════════════
  test:
    name: Tests
    runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [18.x, 20.x]

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Setup Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v4
        with:
          node-version: ${{ matrix.node-version }}
          cache: "npm"

      - name: Install dependencies
        run: npm ci

      - name: Run unit tests
        run: npm run test:unit -- --coverage

      - name: Run integration tests
        run: npm run test:integration

      - name: Upload coverage to Codecov
        uses: codecov/codecov-action@v3
        with:
          files: ./coverage/coverage-final.json
          flags: unittests
          name: codecov-umbrella

      - name: Generate coverage badge
        if: github.ref == 'refs/heads/main'
        run: npm run coverage:badge

  # ═══════════════════════════════════════════
  # Build
  # ═══════════════════════════════════════════
  build:
    name: Build
    runs-on: ubuntu-latest
    needs: [quality, security, test]

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: ${{ env.NODE_VERSION }}
          cache: "npm"

      - name: Install dependencies
        run: npm ci

      - name: Build application
        run: npm run build
        env:
          CI: true

      - name: Archive production artifacts
        uses: actions/upload-artifact@v3
        with:
          name: build-artifacts
          path: |
            dist
            build
            .next
          retention-days: 7

      - name: Check bundle size
        run: npm run analyze

  # ═══════════════════════════════════════════
  # Docker Build
  # ═══════════════════════════════════════════
  docker:
    name: Docker Build & Push
    runs-on: ubuntu-latest
    needs: build
    if: github.event_name == 'push'

    permissions:
      contents: read
      packages: write

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3

      - name: Log in to Container Registry
        uses: docker/login-action@v3
        with:
          registry: ${{ env.REGISTRY }}
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}

      - name: Extract metadata
        id: meta
        uses: docker/metadata-action@v5
        with:
          images: ${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}
          tags: |
            type=ref,event=branch
            type=ref,event=pr
            type=semver,pattern={{version}}
            type=semver,pattern={{major}}.{{minor}}
            type=sha,prefix={{branch}}-

      - name: Build and push Docker image
        uses: docker/build-push-action@v5
        with:
          context: .
          push: true
          tags: ${{ steps.meta.outputs.tags }}
          labels: ${{ steps.meta.outputs.labels }}
          cache-from: type=gha
          cache-to: type=gha,mode=max

  # ═══════════════════════════════════════════
  # Deploy to Staging
  # ═══════════════════════════════════════════
  deploy-staging:
    name: Deploy to Staging
    runs-on: ubuntu-latest
    needs: [build]
    if: github.ref == 'refs/heads/develop'
    environment:
      name: staging
      url: https://staging.example.com

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Download build artifacts
        uses: actions/download-artifact@v3
        with:
          name: build-artifacts

      - name: Deploy to Vercel Staging
        uses: amondnet/vercel-action@v25
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          working-directory: ./

      - name: Run smoke tests
        run: npm run test:smoke
        env:
          BASE_URL: https://staging.example.com

  # ═══════════════════════════════════════════
  # Deploy to Production
  # ═══════════════════════════════════════════
  deploy-production:
    name: Deploy to Production
    runs-on: ubuntu-latest
    needs: [build, docker]
    if: github.ref == 'refs/heads/main'
    environment:
      name: production
      url: https://example.com

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Download build artifacts
        uses: actions/download-artifact@v3
        with:
          name: build-artifacts

      - name: Deploy to Vercel Production
        uses: amondnet/vercel-action@v25
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          vercel-args: "--prod"
          working-directory: ./

      - name: Create release
        uses: actions/create-release@v1
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          tag_name: v${{ github.run_number }}
          release_name: Release v${{ github.run_number }}
          draft: false
          prerelease: false

      - name: Run E2E tests
        run: npm run test:e2e
        env:
          BASE_URL: https://example.com

      - name: Notify Slack
        uses: slackapi/slack-github-action@v1
        with:
          payload: |
            {
              "text": "✅ Production deployment successful!",
              "blocks": [
                {
                  "type": "section",
                  "text": {
                    "type": "mrkdwn",
                    "text": "*Production Deployment*\n✅ Successfully deployed to production\n<${{ github.event.repository.html_url }}/commit/${{ github.sha }}|View commit>"
                  }
                }
              ]
            }
        env:
          SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK_URL }}

  # ═══════════════════════════════════════════
  # Performance Testing
  # ═══════════════════════════════════════════
  performance:
    name: Performance Tests
    runs-on: ubuntu-latest
    needs: [deploy-staging]
    if: github.ref == 'refs/heads/develop'

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Run Lighthouse CI
        uses: treosh/lighthouse-ci-action@v10
        with:
          urls: |
            https://staging.example.com
            https://staging.example.com/about
          uploadArtifacts: true
          temporaryPublicStorage: true

      - name: Run load tests
        run: |
          npm install -g artillery
          artillery run tests/load-test.yml
```

---

### GitLab CI/CD 🦊

```yaml
# ═══════════════════════════════════════════
# .gitlab-ci.yml
# GitLab CI/CD Pipeline
# ═══════════════════════════════════════════

stages:
  - quality
  - test
  - build
  - deploy

variables:
  NODE_VERSION: "20"
  DOCKER_DRIVER: overlay2

# ═══════════════════════════════════════════
# Templates
# ═══════════════════════════════════════════

.node_template: &node_template
  image: node:${NODE_VERSION}
  cache:
    key: ${CI_COMMIT_REF_SLUG}
    paths:
      - node_modules/
      - .npm/
  before_script:
    - npm ci --cache .npm --prefer-offline

# ═══════════════════════════════════════════
# Quality Stage
# ═══════════════════════════════════════════

lint:
  <<: *node_template
  stage: quality
  script:
    - npm run lint
    - npm run format:check
  only:
    - merge_requests
    - main
    - develop

type-check:
  <<: *node_template
  stage: quality
  script:
    - npm run type-check
  only:
    - merge_requests
    - main
    - develop

security:
  <<: *node_template
  stage: quality
  script:
    - npm audit --audit-level=moderate
  allow_failure: true

# ═══════════════════════════════════════════
# Test Stage
# ═══════════════════════════════════════════

test:unit:
  <<: *node_template
  stage: test
  script:
    - npm run test:unit -- --coverage
  coverage: '/All files[^|]*\|[^|]*\s+([\d\.]+)/'
  artifacts:
    reports:
      coverage_report:
        coverage_format: cobertura
        path: coverage/cobertura-coverage.xml
    paths:
      - coverage/

test:integration:
  <<: *node_template
  stage: test
  services:
    - postgres:15
    - redis:7
  variables:
    DATABASE_URL: "postgresql://postgres:postgres@postgres:5432/test"
    REDIS_URL: "redis://redis:6379"
  script:
    - npm run test:integration

# ═══════════════════════════════════════════
# Build Stage
# ═══════════════════════════════════════════

build:
  <<: *node_template
  stage: build
  script:
    - npm run build
  artifacts:
    paths:
      - dist/
      - build/
    expire_in: 1 week
  only:
    - main
    - develop
    - tags

docker:build:
  stage: build
  image: docker:24
  services:
    - docker:24-dind
  before_script:
    - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
  script:
    - docker build -t $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA .
    - docker tag $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA $CI_REGISTRY_IMAGE:latest
    - docker push $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
    - docker push $CI_REGISTRY_IMAGE:latest
  only:
    - main

# ═══════════════════════════════════════════
# Deploy Stage
# ═══════════════════════════════════════════

deploy:staging:
  stage: deploy
  image: alpine:latest
  before_script:
    - apk add --no-cache curl
  script:
    - 'curl -X POST "$STAGING_WEBHOOK_URL" -H "Content-Type: application/json" -d "{\"ref\": \"$CI_COMMIT_SHA\"}"'
  environment:
    name: staging
    url: https://staging.example.com
  only:
    - develop

deploy:production:
  stage: deploy
  image: alpine:latest
  before_script:
    - apk add --no-cache curl
  script:
    - 'curl -X POST "$PRODUCTION_WEBHOOK_URL" -H "Content-Type: application/json" -d "{\"ref\": \"$CI_COMMIT_SHA\"}"'
  environment:
    name: production
    url: https://example.com
  when: manual
  only:
    - main

# ═══════════════════════════════════════════
# Notifications
# ═══════════════════════════════════════════

notify:slack:
  stage: .post
  image: alpine:latest
  before_script:
    - apk add --no-cache curl
  script:
    - |
      curl -X POST $SLACK_WEBHOOK_URL -H 'Content-Type: application/json' -d "{
        \"text\": \"Pipeline ${CI_PIPELINE_STATUS} for ${CI_PROJECT_NAME}\",
        \"attachments\": [{
          \"color\": \"${CI_PIPELINE_STATUS}\",
          \"fields\": [
            {\"title\": \"Project\", \"value\": \"${CI_PROJECT_NAME}\", \"short\": true},
            {\"title\": \"Branch\", \"value\": \"${CI_COMMIT_REF_NAME}\", \"short\": true},
            {\"title\": \"Commit\", \"value\": \"${CI_COMMIT_SHORT_SHA}\", \"short\": true},
            {\"title\": \"Author\", \"value\": \"${GITLAB_USER_NAME}\", \"short\": true}
          ]
        }]
      }"
  when: on_failure
```

---

### Jenkins Pipeline 🔨

```groovy
// ═══════════════════════════════════════════
// Jenkinsfile
// Jenkins Declarative Pipeline
// ═══════════════════════════════════════════

pipeline {
    agent any

    environment {
        NODE_VERSION = '20'
        DOCKER_REGISTRY = 'docker.io'
        IMAGE_NAME = 'myapp'
    }

    options {
        buildDiscarder(logRotator(numToKeepStr: '10'))
        timestamps()
        timeout(time: 1, unit: 'HOURS')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                script {
                    env.GIT_COMMIT_MSG = sh(
                        script: 'git log -1 --pretty=%B',
                        returnStdout: true
                    ).trim()
                }
            }
        }

        stage('Setup') {
            steps {
                nodejs(nodeJSInstallationName: "Node ${NODE_VERSION}") {
                    sh 'npm ci'
                }
            }
        }

        stage('Quality Checks') {
            parallel {
                stage('Lint') {
                    steps {
                        nodejs(nodeJSInstallationName: "Node ${NODE_VERSION}") {
                            sh 'npm run lint'
                        }
                    }
                }

                stage('Type Check') {
                    steps {
                        nodejs(nodeJSInstallationName: "Node ${NODE_VERSION}") {
                            sh 'npm run type-check'
                        }
                    }
                }

                stage('Security Audit') {
                    steps {
                        nodejs(nodeJSInstallationName: "Node ${NODE_VERSION}") {
                            sh 'npm audit --audit-level=moderate'
                        }
                    }
                }
            }
        }

        stage('Test') {
            steps {
                nodejs(nodeJSInstallationName: "Node ${NODE_VERSION}") {
                    sh 'npm run test -- --coverage'
                }
                publishHTML([
                    reportDir: 'coverage',
                    reportFiles: 'index.html',
                    reportName: 'Coverage Report'
                ])
            }
        }

        stage('Build') {
            when {
                anyOf {
                    branch 'main'
                    branch 'develop'
                }
            }
            steps {
                nodejs(nodeJSInstallationName: "Node ${NODE_VERSION}") {
                    sh 'npm run build'
                }
                archiveArtifacts artifacts: 'dist/**/*', fingerprint: true
            }
        }

        stage('Docker Build') {
            when {
                branch 'main'
            }
            steps {
                script {
                    docker.build("${IMAGE_NAME}:${BUILD_NUMBER}")
                    docker.build("${IMAGE_NAME}:latest")
                }
            }
        }

        stage('Deploy to Staging') {
            when {
                branch 'develop'
            }
            steps {
                sh '''
                    ssh user@staging-server "cd /var/www/app && \
                    git pull origin develop && \
                    npm install && \
                    npm run build && \
                    pm2 restart app"
                '''
            }
        }

        stage('Deploy to Production') {
            when {
                branch 'main'
            }
            steps {
                input message: 'Deploy to Production?', ok: 'Deploy'
                sh '''
                    ssh user@prod-server "cd /var/www/app && \
                    git pull origin main && \
                    npm install && \
                    npm run build && \
                    pm2 restart app"
                '''
            }
        }
    }

    post {
        success {
            slackSend(
                color: 'good',
                message: "✅ Build ${env.BUILD_NUMBER} succeeded\nBranch: ${env.BRANCH_NAME}\nCommit: ${env.GIT_COMMIT_MSG}"
            )
        }

        failure {
            slackSend(
                color: 'danger',
                message: "❌ Build ${env.BUILD_NUMBER} failed\nBranch: ${env.BRANCH_NAME}\nCommit: ${env.GIT_COMMIT_MSG}"
            )
        }

        always {
            cleanWs()
        }
    }
}
```

---

<div align="center">

## 🌐 Workflow Automation Tools

</div>

### No-Code/Low-Code Automation 🎯

```
# ═══════════════════════════════════════════
# Zapier
# ═══════════════════════════════════════════

🔗 Website: https://zapier.com
💰 Pricing: Free tier (100 tasks/month), Paid plans from $19.99/month

Popular Zaps:
✅ Gmail → Slack (New email notifications)
✅ Google Forms → Google Sheets (Form responses)
✅ GitHub → Discord (New issues/PRs)
✅ Trello → Slack (Card updates)
✅ Twitter → Discord (New tweets)
✅ Stripe → Slack (New payments)

Example: GitHub Issues to Slack
1. Trigger: New Issue in GitHub
2. Filter: Only issues with label "bug"
3. Action: Send message to Slack channel
4. Action: Create Trello card in "Bugs" list

# ═══════════════════════════════════════════
# Make (Integromat)
# ═══════════════════════════════════════════

🔗 Website: https://make.com
💰 Pricing: Free tier (1,000 operations/month), Paid from $9/month

Features:
✅ Visual workflow builder
✅ More complex logic than Zapier
✅ Error handling & retry logic
✅ Data transformation
✅ Webhooks
✅ 1,000+ integrations

Example: Automated Content Publishing
1. Watch RSS Feed (Trigger)
2. Filter: Only tech articles
3. OpenAI: Generate social media post
4. Twitter: Post tweet
5. LinkedIn: Create post
6. Buffer: Schedule for later

# ═══════════════════════════════════════════
# IFTTT (If This Then That)
# ═══════════════════════════════════════════

🔗 Website: https://ifttt.com
💰 Pricing: Free tier, Pro $3.99/month

Popular Applets:
✅ Post Instagram photo → Twitter
✅ Get notification when ISS passes overhead
✅ Mute phone during calendar events
✅ Save liked tweets to Google Drive
✅ Smart home automation

Example: Daily Weather Notification
If: Weather forecast shows rain tomorrow
Then: Send notification to phone

# ═══════════════════════════════════════════
# n8n (Self-hosted)
# ═══════════════════════════════════════════

🔗 Website: https://n8n.io
💰 Pricing: Free (self-hosted), Cloud from $20/month

Features:
✅ Open-source
✅ Self-hosted option
✅ 300+ integrations
✅ Visual workflow editor
✅ Custom code nodes
✅ No limitations on executions

Example Workflow:
1. Webhook trigger
2. Parse incoming data
3. Run custom JavaScript
4. Store in database
5. Send email notification

# ═══════════════════════════════════════════
# Workflow Comparison
# ═══════════════════════════════════════════

| Feature        | Zapier | Make | IFTTT | n8n |
|----------------|--------|------|-------|-----|
| Free Tier      | ✅     | ✅   | ✅    | ✅  |
| Visual Builder | ✅     | ✅   | ❌    | ✅  |
| Code Support   | ⚠️     | ✅   | ❌    | ✅  |
| Integrations   | 5,000+ | 1,000+ | 700+ | 300+ |
| Complex Logic  | ⚠️     | ✅   | ❌    | ✅  |
| Self-hosted    | ❌     | ❌   | ❌    | ✅  |
```

---

<div align="center">

## ⚙️ Task Runners & Build Tools

</div>

### NPM Scripts 📦

```json
// ═══════════════════════════════════════════
// package.json - NPM Scripts
// ═══════════════════════════════════════════

{
  "name": "my-awesome-project",
  "version": "1.0.0",
  "scripts": {
    // Development
    "dev": "vite",
    "dev:debug": "node --inspect node_modules/.bin/vite",
    "start": "npm run dev",

    // Building
    "build": "vite build",
    "build:analyze": "vite build --mode analyze",
    "build:staging": "vite build --mode staging",
    "build:production": "vite build --mode production",

    // Testing
    "test": "vitest",
    "test:unit": "vitest run --coverage",
    "test:watch": "vitest watch",
    "test:e2e": "playwright test",
    "test:e2e:headed": "playwright test --headed",

    // Linting & Formatting
    "lint": "eslint . --ext .js,.jsx,.ts,.tsx",
    "lint:fix": "eslint . --ext .js,.jsx,.ts,.tsx --fix",
    "format": "prettier --write \"src/**/*.{js,jsx,ts,tsx,json,css,md}\"",
    "format:check": "prettier --check \"src/**/*.{js,jsx,ts,tsx,json,css,md}\"",
    "type-check": "tsc --noEmit",

    // Git Hooks
    "prepare": "husky install",
    "pre-commit": "lint-staged",

    // Deployment
    "deploy": "npm run build && npm run deploy:vercel",
    "deploy:vercel": "vercel --prod",
    "deploy:netlify": "netlify deploy --prod",

    // Database
    "db:migrate": "prisma migrate dev",
    "db:seed": "prisma db seed",
    "db:studio": "prisma studio",
    "db:generate": "prisma generate",

    // Utilities
    "clean": "rm -rf node_modules dist .next build",
    "clean:cache": "rm -rf node_modules/.cache",
    "fresh": "npm run clean && npm install",
    "update": "npm update && npm outdated",
    "check-updates": "npx npm-check-updates",

    // Release
    "release": "standard-version",
    "release:minor": "standard-version --release-as minor",
    "release:major": "standard-version --release-as major",

    // CI/CD
    "ci": "npm run lint && npm run type-check && npm run test:unit && npm run build",
    "ci:e2e": "npm run build && npm run test:e2e"
  }
}
```

---

### Gulp.js 🚀

```javascript
// ═══════════════════════════════════════════
// gulpfile.js
// Gulp Task Runner Configuration
// ═══════════════════════════════════════════

const gulp = require("gulp");
const sass = require("gulp-sass")(require("sass"));
const autoprefixer = require("gulp-autoprefixer");
const cleanCSS = require("gulp-clean-css");
const uglify = require("gulp-uglify");
const concat = require("gulp-concat");
const imagemin = require("gulp-imagemin");
const browserSync = require("browser-sync").create();
const del = require("del");

// Paths
const paths = {
  styles: {
    src: "src/scss/**/*.scss",
    dest: "dist/css",
  },
  scripts: {
    src: "src/js/**/*.js",
    dest: "dist/js",
  },
  images: {
    src: "src/images/**/*",
    dest: "dist/images",
  },
  html: {
    src: "src/**/*.html",
    dest: "dist",
  },
};

// Clean dist folder
function clean() {
  return del(["dist"]);
}

// Compile SCSS
function styles() {
  return gulp
    .src(paths.styles.src)
    .pipe(sass().on("error", sass.logError))
    .pipe(autoprefixer())
    .pipe(cleanCSS())
    .pipe(gulp.dest(paths.styles.dest))
    .pipe(browserSync.stream());
}

// Minify & concatenate JavaScript
function scripts() {
  return gulp
    .src(paths.scripts.src)
    .pipe(concat("main.min.js"))
    .pipe(uglify())
    .pipe(gulp.dest(paths.scripts.dest))
    .pipe(browserSync.stream());
}

// Optimize images
function images() {
  return gulp
    .src(paths.images.src)
    .pipe(imagemin())
    .pipe(gulp.dest(paths.images.dest));
}

// Copy HTML files
function html() {
  return gulp
    .src(paths.html.src)
    .pipe(gulp.dest(paths.html.dest))
    .pipe(browserSync.stream());
}

// Watch files
function watch() {
  browserSync.init({
    server: {
      baseDir: "./dist",
    },
  });

  gulp.watch(paths.styles.src, styles);
  gulp.watch(paths.scripts.src, scripts);
  gulp.watch(paths.images.src, images);
  gulp.watch(paths.html.src, html);
}

// Export tasks
exports.clean = clean;
exports.styles = styles;
exports.scripts = scripts;
exports.images = images;
exports.html = html;
exports.watch = watch;

// Default task
exports.default = gulp.series(
  clean,
  gulp.parallel(styles, scripts, images, html),
  watch
);

// Build task
exports.build = gulp.series(
  clean,
  gulp.parallel(styles, scripts, images, html)
);
```

---

### Makefile 🔨

```makefile
# ═══════════════════════════════════════════
# Makefile
# Cross-platform task automation
# ═══════════════════════════════════════════

.PHONY: help install dev build test clean deploy

# Default target
.DEFAULT_GOAL := help

# Variables
NODE_VERSION := 20
DOCKER_IMAGE := myapp
DOCKER_TAG := latest

# Help command
help: ## Show this help message
	@echo 'Usage: make [target]'
	@echo ''
	@echo 'Available targets:'
	@awk 'BEGIN {FS = ":.*?## "} /^[a-zA-Z_-]+:.*?## / {printf "  %-20s %s\n", $$1, $$2}' $(MAKEFILE_LIST)

# Installation
install: ## Install dependencies
	npm ci

install-dev: ## Install dev dependencies
	npm install

# Development
dev: ## Start development server
	npm run dev

dev-debug: ## Start dev server with debugging
	npm run dev:debug

# Building
build: ## Build for production
	npm run build

build-staging: ## Build for staging
	npm run build:staging

build-analyze: ## Build with bundle analysis
	npm run build:analyze

# Testing
test: ## Run all tests
	npm test

test-unit: ## Run unit tests
	npm run test:unit

test-e2e: ## Run E2E tests
	npm run test:e2e

test-watch: ## Run tests in watch mode
	npm run test:watch

# Code Quality
lint: ## Run linter
	npm run lint

lint-fix: ## Run linter with auto-fix
	npm run lint:fix

format: ## Format code
	npm run format

format-check: ## Check code formatting
	npm run format:check

type-check: ## Run type checking
	npm run type-check

# Quality checks (all)
quality: lint format-check type-check ## Run all quality checks

# Docker
docker-build: ## Build Docker image
	docker build -t $(DOCKER_IMAGE):$(DOCKER_TAG) .

docker-run: ## Run Docker container
	docker run -p 3000:3000 $(DOCKER_IMAGE):$(DOCKER_TAG)

docker-push: ## Push Docker image
	docker push $(DOCKER_IMAGE):$(DOCKER_TAG)

# Deployment
deploy-staging: ## Deploy to staging
	npm run deploy:staging

deploy-production: ## Deploy to production
	npm run deploy:production

# Database
db-migrate: ## Run database migrations
	npm run db:migrate

db-seed: ## Seed database
	npm run db:seed

db-studio: ## Open database studio
	npm run db:studio

# Utilities
clean: ## Clean build artifacts
	rm -rf dist build .next node_modules/.cache

fresh: clean install ## Fresh install (clean + install)

update: ## Update dependencies
	npm update
	npm outdated

# CI/CD
ci: quality test build ## Run CI pipeline
	@echo "✅ CI pipeline complete"

release: ## Create a release
	npm run release

# Git
git-cleanup: ## Cleanup merged branches
	git fetch --prune
	git branch --merged | grep -v "\*" | grep -v "main" | grep -v "develop" | xargs -n 1 git branch -d

# All-in-one commands
all: install lint test build ## Install, lint, test, and build

start: install dev ## Install dependencies and start dev server
```

---

<div align="center">

## 💡 Automation Best Practices

</div>

### MrDib's Automation Manifesto 📜

```
# ═══════════════════════════════════════════
# Why Automate?
# ═══════════════════════════════════════════

1. 🎯 Consistency
   → Machines don't make typos or forget steps
   → Same result every time
   → No human error

2. ⚡ Speed
   → Computers are faster than humans
   → Parallel execution
   → 24/7 availability

3. 💰 Cost Savings
   → Reduce manual labor
   → Fewer errors = less debugging
   → Scale without hiring

4. 🧠 Focus
   → Free up mental bandwidth
   → Work on important problems
   → Less context switching

5. 📈 Scalability
   → Handle more work without more people
   → Consistent quality at scale

6. 📊 Metrics & Insights
   → Track everything automatically
   → Data-driven decisions
   → Identify bottlenecks

# ═══════════════════════════════════════════
# What to Automate First (Priority Order)
# ═══════════════════════════════════════════

1. Code Formatting & Linting
   ✅ Set up Prettier & ESLint
   ✅ Add pre-commit hooks
   ✅ Configure editor integration

2. Testing
   ✅ Unit tests in CI
   ✅ E2E tests before deployment
   ✅ Test coverage reports

3. Build & Deployment
   ✅ CI/CD pipeline
   ✅ Automated builds
   ✅ One-command deployment

4. Code Review
   ✅ Automated checks on PRs
   ✅ Danger.js for PR guidelines
   ✅ Automated security scans

5. Documentation
   ✅ Auto-generate API docs
   ✅ Changelog generation
   ✅ README badges

6. Monitoring & Alerts
   ✅ Error tracking
   ✅ Performance monitoring
   ✅ Uptime monitoring

# ═══════════════════════════════════════════
# Automation Anti-Patterns (What NOT to Do)
# ═══════════════════════════════════════════

❌ Over-automation
   → Don't automate what changes frequently
   → Don't automate before understanding the process
   → Don't automate for the sake of automation

❌ No documentation
   → Always document your automation
   → Explain WHY, not just HOW
   → Include troubleshooting steps

❌ No error handling
   → Always handle failures gracefully
   → Notify on errors
   → Have rollback procedures

❌ No monitoring
   → Automation can fail silently
   → Always monitor your automation
   → Set up alerts

❌ Ignoring maintenance
   → Automation needs updates
   → Dependencies get outdated
   → Requirements change

# ═══════════════════════════════════════════
# Automation Checklist
# ═══════════════════════════════════════════

Before Automating:
☐ Is this task repetitive?
☐ Does it take >5 minutes?
☐ Do you do it >3 times/week?
☐ Is the process well-defined?
☐ Is it error-prone when done manually?

If YES to 3+ questions → AUTOMATE!

When Automating:
☐ Start simple
☐ Document the process
☐ Add error handling
☐ Test thoroughly
☐ Monitor execution
☐ Measure improvement
☐ Iterate and improve

# ═══════════════════════════════════════════
# My Favorite Automation Stack
# ═══════════════════════════════════════════

Local Development:
✅ Zsh + Oh My Zsh
✅ Custom aliases
✅ Shell functions
✅ Git hooks (Husky)

CI/CD:
✅ GitHub Actions
✅ Vercel/Netlify for frontend
✅ Docker for backend

Scripts:
✅ Node.js for complex logic
✅ Shell scripts for simple tasks
✅ Python for data processing

Monitoring:
✅ Sentry for errors
✅ Datadog/New Relic for performance
✅ Slack for notifications

# ═══════════════════════════════════════════
# ROI Calculator for Automation
# ═══════════════════════════════════════════

Time to Automate: X hours
Time Saved per Task: Y minutes
Task Frequency: Z times/week

Payback Time = X / (Y * Z / 60)

Example:
- Automation takes: 4 hours
- Saves: 10 minutes per task
- Do it: 5 times/week

Payback = 4 / (10 * 5 / 60) = 4 / 0.83 = 4.8 weeks

Worth it if you'll do it for >5 weeks!

# ═══════════════════════════════════════════
# Automation Resources
# ═══════════════════════════════════════════

📚 Books:
- "The Phoenix Project" by Gene Kim
- "Release It!" by Michael Nygard
- "Site Reliability Engineering" by Google

🎓 Courses:
- GitHub Actions Certification
- DevOps Engineering (Udemy)
- Automation with Python (Coursera)

🛠️ Tools to Master:
- Shell scripting (Bash/Zsh)
- Git & GitHub
- Docker & Kubernetes
- CI/CD platforms
- Infrastructure as Code (Terraform)

🌐 Communities:
- r/devops
- DevOps Discord servers
- Automation Slack communities
```

---

<div align="center">

## 🎓 Resources & Learning

</div>

### Essential Resources 📚

```
📘 Documentation
   GitHub Actions: https://docs.github.com/actions
   GitLab CI/CD: https://docs.gitlab.com/ee/ci/
   Jenkins: https://www.jenkins.io/doc/
   Docker: https://docs.docker.com/

📗 Tutorials
   DevOps Roadmap: https://roadmap.sh/devops
   CI/CD Tutorial: https://www.atlassian.com/continuous-delivery/tutorials
   Shell Scripting: https://www.shellscript.sh/

📙 Tools
   ShellCheck: https://www.shellcheck.net/
   Act (Local GitHub Actions): https://github.com/nektos/act
   Make automation: https://www.gnu.org/software/make/manual/

🎥 YouTube Channels
   - TechWorld with Nana (DevOps)
   - NetworkChuck (Automation)
   - Fireship (Quick tutorials)
   - DevOps Toolkit

🏋️ Practice
   - Automate boring tasks
   - Build your own CLI tool
   - Create GitHub Actions
   - Set up CI/CD for a project
```

---

<div align="center">

**Built with 🤖 by MrDib, for developers who value their time**

_Remember: Time spent automating is an investment in your future productivity!_ 🚀

**Happy Automating!** ✨

</div>
