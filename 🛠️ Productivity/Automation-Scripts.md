<div align="center">

# 🤖 Automation Scripts & Workflow Enhancers

### _Making your computer work for you, so you can focus on the fun stuff_ 🎉

![Automation](https://img.shields.io/badge/Automation-Smart-purple?style=for-the-badge)
![Efficiency](https://img.shields.io/badge/Efficiency-High-green?style=for-the-badge)

</div>

---

<div align="center">

## 🎯 Bash/Zsh Automation

</div>

### Shell Scripting Fundamentals 🐚

```bash
# Basic script structure
#!/bin/bash

# Comments start with #
# Variables
NAME="MrDib"
echo "Hello, $NAME!"

# Conditional statements
if [ "$NAME" == "MrDib" ]; then
  echo "You're awesome!"
else
  echo "Who are you?"
fi

# Loops
for i in {1..5}; do
  echo "Iteration $i"
done

# Functions
greet() {
  echo "Greetings, $1!"
}
greet "World"

# Command line arguments
echo "First argument: $1"
echo "All arguments: $@"
echo "Number of arguments: $#"

# Exit codes
exit 0 # Success
exit 1 # Failure
```

### Common Automation Tasks 🚀

```bash
# Clean node_modules and reinstall
alias freshstart='rm -rf node_modules package-lock.json && npm install'

# Kill process on port
alias killport='f() { lsof -ti:$1 | xargs kill -9; }; f' # Usage: killport 3000

# Open current directory in VSCode
alias code.='code .'

# Generate random password
alias genpass='head /dev/urandom | tr -dc A-Za-z0-9_!@#$%^&*()_+=- | head -c 16 ; echo'

# Create a timestamped backup
alias backup='tar -czf "backup_$(date +%Y%m%d_%H%M%S).tar.gz" .'

# Git push --force-with-lease safely
alias pushf='git push --force-with-lease'

# Check internet speed (macOS)
alias speedtest='networkQuality'

# Flush DNS cache (macOS)
alias flushdns='sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder'

# Search file content (grep)
alias findinfiles='f() { grep -r --exclude-dir=node_modules --exclude-dir=.git "$1" .; }; f' # Usage: findinfiles "searchterm"

# Create a temporary directory and cd into it
alias mktmp='f() { DIR=$(mktemp -d); cd "$DIR"; echo "Created and navigated to $DIR"; }; f'
```

---

<div align="center">

## 🐍 Python Automation

</div>

### Python for Everyday Tasks 💡

```python
import os
import shutil
import datetime
import requests
import json

# Clean up temporary files
def clean_temp_files(directory="."):
    for root, _, files in os.walk(directory):
        for file in files:
            if file.endswith((".tmp", ".log", ".DS_Store")):
                file_path = os.path.join(root, file)
                print(f"Deleting {file_path}")
                os.remove(file_path)

# Create a project boilerplate
def create_project(project_name, template_path="templates/react-app"):
    if os.path.exists(project_name):
        print(f"Error: Directory '{project_name}' already exists.")
        return
    shutil.copytree(template_path, project_name)
    print(f"Project '{project_name}' created from template.")

# Fetch weather data
def get_weather(city, api_key="YOUR_OPENWEATHERMAP_API_KEY"):
    base_url = "http://api.openweathermap.org/data/2.5/weather"
    params = {
        "q": city,
        "appid": api_key,
        "units": "metric"
    }
    response = requests.get(base_url, params=params)
    data = response.json()
    if data["cod"] == 200:
        main_data = data["main"]
        print(f"Weather in {city}:")
        print(f"  Temperature: {main_data['temp']}°C")
        print(f"  Humidity: {main_data['humidity']}%")
        print(f"  Conditions: {data['weather'][0]['description']}")
    else:
        print(f"Error fetching weather: {data['message']}")

# Automate GitHub repo creation (requires PyGithub)
def create_github_repo(repo_name, description=""):
    # from github import Github
    # g = Github("YOUR_GITHUB_TOKEN")
    # user = g.get_user()
    # repo = user.create_repo(repo_name, description=description)
    # print(f"Repo '{repo_name}' created: {repo.html_url}")
    print(f"Simulating GitHub repo '{repo_name}' creation.")

if __name__ == "__main__":
    # Example usage:
    # clean_temp_files()
    # create_project("my-new-react-project")
    # get_weather("London")
    # create_github_repo("my-awesome-project", "A new project managed by MrDib's script")
    print("Python automation script ready!")
```

---

<div align="center">

## ⚡ JavaScript/Node.js Automation

</div>

### Node.js for CLI Tools & Scripts 🚀

```javascript
#!/usr/bin/env node

const { execSync } = require("child_process");
const fs = require("fs");
const path = require("path");
const readline = require("readline");

// Command line interface for questions
const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout,
});

const question = (query) =>
  new Promise((resolve) => rl.question(query, resolve));

// Create a new React component boilerplate
async function createReactComponent(componentName) {
  const componentDir = path.join(process.cwd(), componentName);
  if (fs.existsSync(componentDir)) {
    console.error(
      `Error: Component directory '${componentName}' already exists.`
    );
    return;
  }

  fs.mkdirSync(componentDir);
  const indexJsContent = `import React from 'react';\nimport styles from './${componentName}.module.css';\n\nconst ${componentName} = () => {\n  return (\n    <div className={styles.container}>\n      <h1>${componentName} Component</h1>\n    </div>\n  );\n};\n\nexport default ${componentName};\n`;
  const moduleCssContent = `.container {\n  /* Add your styles here */\n}\n`;

  fs.writeFileSync(
    path.join(componentDir, `${componentName}.jsx`),
    indexJsContent
  );
  fs.writeFileSync(
    path.join(componentDir, `${componentName}.module.css`),
    moduleCssContent
  );

  console.log(
    `React component '${componentName}' created successfully in ${componentDir}/`
  );
}

// Update package.json version
async function updatePackageVersion(type = "patch") {
  try {
    const output = execSync(`npm version ${type}`, { encoding: "utf8" });
    console.log(`Version updated:\n${output}`);
  } catch (error) {
    console.error(`Error updating version: ${error.message}`);
  }
}

// Run multiple commands sequentially
async function runSequence(commands) {
  for (const cmd of commands) {
    console.log(`Running: ${cmd}`);
    try {
      execSync(cmd, { stdio: "inherit" });
    } catch (error) {
      console.error(`Command failed: ${cmd}\n${error.message}`);
      process.exit(1);
    }
  }
  console.log("All commands completed successfully!");
}

async function main() {
  const action = process.argv[2];

  switch (action) {
    case "create-component":
      const name = process.argv[3];
      if (!name) {
        console.log("Usage: node script.js create-component <ComponentName>");
        return;
      }
      await createReactComponent(name);
      break;
    case "update-version":
      const versionType = process.argv[3] || "patch";
      await updatePackageVersion(versionType);
      break;
    case "deploy-prod":
      console.log("Initiating production deployment sequence...");
      await runSequence([
        "npm run lint",
        "npm test",
        "npm run build",
        "firebase deploy --only hosting", // Example
        'echo "Deployment complete!"',
      ]);
      break;
    default:
      console.log(`
      Usage: node script.js <command> [args]

      Commands:
        create-component <ComponentName>  - Creates a new React component boilerplate.
        update-version [patch|minor|major] - Updates the package.json version.
        deploy-prod                       - Runs a sequence of commands for production deployment.
      `);
  }
  rl.close();
}

if (require.main === module) {
  main();
}
```

---

<div align="center">

## 🚀 GitHub Actions / GitLab CI

</div>

### CI/CD Pipeline Automation ⚙️

```yaml
# .github/workflows/main.yml
name: CI/CD Pipeline

on:
  push:
    branches:
      - main
      - develop
  pull_request:
    branches:
      - main
      - develop

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Set up Node.js
        uses: actions/setup-node@v4
        with:
          node-version: "20"

      - name: Install dependencies
        run: npm ci

      - name: Run ESLint
        run: npm run lint

      - name: Run tests
        run: npm test -- --coverage

      - name: Build project
        if: github.ref == 'refs/heads/main' || github.ref == 'refs/heads/develop'
        run: npm run build

      - name: Deploy to Vercel (example)
        if: github.ref == 'refs/heads/main' && success()
        run: npx vercel deploy --prebuilt --prod --token ${{ secrets.VERCEL_TOKEN }}
        env:
          VERCEL_ORG_ID: ${{ secrets.VERCEL_ORG_ID }}
          VERCEL_PROJECT_ID: ${{ secrets.VERCEL_PROJECT_ID }}

  deploy-to-staging:
    runs-on: ubuntu-latest
    needs: build
    if: github.ref == 'refs/heads/develop' && success()
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Deploy to Staging (example)
        run: echo "Deploying to staging environment..."
        # Add your staging deployment commands here

  notify-slack:
    runs-on: ubuntu-latest
    needs: build
    if: failure()
    steps:
      - name: Notify Slack on failure
        uses: rtCamp/action-slack-notify@v2
        env:
          SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK }}
          SLACK_CHANNEL: "#dev-alerts"
          SLACK_MESSAGE: "CI/CD Pipeline failed for commit ${{ github.sha }} on ${{ github.ref }}"
          SLACK_COLOR: "danger"
```

---

<div align="center">

## 💡 Workflow Automation Tools

</div>

### Zapier, Make (Integromat), IFTTT 🌐

```
🎯 Zapier            → https://zapier.com
   - Connects 5,000+ apps
   - Event-driven automation
   - No-code/low-code
   - Free tier

⚙️ Make (Integromat) → https://make.com
   - Visual workflow builder
   - More powerful than Zapier
   - Complex logic
   - Free tier

🔗 IFTTT             → https://ifttt.com
   - "If This Then That"
   - Simple applets
   - Consumer focused
   - Free tier
```

---

<div align="center">

## 🎯 Task Runners & Build Tools

</div>

### Local Automation ⚙️

```
📦 npm scripts       → package.json
   - Built-in to Node.js
   - Simple task runner
   - Cross-platform
   - No extra installs

🚀 Gulp.js           → https://gulpjs.com
   - Stream-based build system
   - Flexible
   - Plugin ecosystem
   - npm install -g gulp-cli

🔨 Grunt.js          → https://gruntjs.com
   - Configuration-based
   - Task runner
   - Plugin rich
   - npm install -g grunt-cli

⚡ Vite             → https://vitejs.dev
   - Modern build tool
   - Fast dev server
   - Rollup based
   - HMR built-in
```

---

<div align="center">

## 💡 MrDib's Automation Manifesto

</div>

### Why Automate?

1. **Reduce errors**: Machines don't make typos.
2. **Save time**: Free up cognitive load for actual problem-solving.
3. **Consistency**: Ensure processes are always followed.
4. **Faster feedback**: CI/CD catches issues early.
5. **Less boredom**: Repetitive tasks are soul-crushing.

### What to Automate First

- Project setup & boilerplate generation
- Code formatting & linting
- Testing (unit, integration, E2E)
- Build & deployment processes
- Common terminal commands (aliases!)
- Routine data fetching/parsing
- Daily backups

### My Favorite Toolchains

- **Local Dev**: Zsh + Oh My Zsh + Starship + custom aliases
- **Project Setup**: Node.js scripts (e.g., `create-component`)
- **CI/CD**: GitHub Actions
- **Backend Ops**: Python scripts (e.g., cron jobs)
- **Integrations**: Zapier/Make

---

<div align="center">

_Remember: A developer who automates is a developer who truly understands laziness... I mean, efficiency! 😴_

</div>
