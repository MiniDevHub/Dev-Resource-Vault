<div align="center">

# ⚙️ VSCode Setup - Your Complete Development Environment

### _Transform VSCode into a powerhouse IDE_ ✨

![VSCode](https://img.shields.io/badge/VSCode-1.85+-blue?style=for-the-badge&logo=visualstudiocode)
![Extensions](https://img.shields.io/badge/Extensions-50+-green?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🌟 My Personal VSCode Setup](#-my-personal-vscode-setup)
- [📥 Installation](#-installation)
- [🎨 UI Customization](#-ui-customization)
- [⚡ Essential Extensions](#-essential-extensions)
- [💻 Language-Specific Extensions](#-language-specific-extensions)
- [🚀 Productivity Boosters](#-productivity-boosters)
- [🎯 Git & Version Control](#-git--version-control)
- [🐛 Debugging](#-debugging)
- [⌨️ Keyboard Shortcuts](#️-keyboard-shortcuts)
- [🔧 Settings & Configuration](#-settings--configuration)
- [🎭 Themes & Icons](#-themes--icons)
- [💡 Pro Tips](#-pro-tips)

---

<div align="center">

## 🌟 My Personal VSCode Setup

</div>

```bash
# ═══════════════════════════════════════════
# COMPLETE PRODUCTION-READY CONFIGURATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║          💎 CUSTOM-CODE-STYLES REPOSITORY 💎               ║
╚════════════════════════════════════════════════════════════╝

Looking for a battle-tested, production-ready VSCode setup?

🔗 GitHub Repository:
   https://github.com/MiniDevHub/Custom-Code-Styles

⭐ Star the repo to show support!
🔀 Fork it to customize for your needs!
📝 Open issues for questions or suggestions!

╔════════════════════════════════════════════════════════════╗
║                   REPOSITORY STRUCTURE                     ║
╚════════════════════════════════════════════════════════════╝

Custom-Code-Styles/
├── Assets/
│   ├── Images/                    # Screenshots & visuals
│   └── README.md
├── Configs/                       # ⭐ Main configuration files
│   ├── Extensions.json            # Recommended extensions
│   ├── KeyBindings.json           # Custom keyboard shortcuts
│   ├── Settings.json              # Complete VSCode settings
│   ├── VsCode-Keybindings.md      # Shortcut documentation
│   └── README.md
├── Docs/                          # 📚 Documentation
│   ├── Customization.md           # How to customize
│   ├── Installation.md            # Installation guide
│   ├── Keyboard-Shortcuts.md      # Shortcut reference
│   ├── TroubleShooting.md         # Common issues
│   └── README.md
├── Snippets/                      # 📝 Code snippets
│   ├── HTML.json
│   ├── Java.json
│   └── README.md
├── Styles/                        # 🎨 Custom styling
│   ├── CustomCSS.css
│   ├── CustomJavascript.js
│   └── README.md
├── .gitignore
├── CONTRIBUTING.md
├── LICENSE
└── README.md

╔════════════════════════════════════════════════════════════╗
║                     WHAT'S INCLUDED?                       ║
╚════════════════════════════════════════════════════════════╝

✅ CONFIGS/ - Ready-to-use configuration files:
   ├─ Settings.json          500+ carefully tuned settings
   ├─ KeyBindings.json       Custom productivity shortcuts
   ├─ Extensions.json        Curated extension recommendations
   └─ Documentation          Detailed explanations

✅ DOCS/ - Comprehensive guides:
   ├─ Installation.md        Step-by-step setup
   ├─ Customization.md       Make it your own
   ├─ Keyboard-Shortcuts.md  Complete shortcut reference
   └─ TroubleShooting.md     Common issues & solutions

✅ SNIPPETS/ - Code snippets for productivity:
   ├─ HTML.json              HTML boilerplate & shortcuts
   ├─ Java.json              Java development snippets
   └─ More languages         (Check repo for updates)

✅ STYLES/ - Advanced customization:
   ├─ CustomCSS.css          UI tweaks & enhancements
   ├─ CustomJavascript.js    Custom functionality
   └─ Instructions           How to apply custom styles

╔════════════════════════════════════════════════════════════╗
║                      PERFECT FOR:                          ║
╚════════════════════════════════════════════════════════════╝

🎯 New Machine Setup
   → Clone repo, copy files, done! ⚡

🎯 Team Standardization
   → Share consistent config across developers

🎯 Learning Best Practices
   → Well-documented, production-tested settings

🎯 Productivity Boost
   → Optimized shortcuts and workflows

🎯 Quick Reference
   → Documentation for all shortcuts & features

╔════════════════════════════════════════════════════════════╗
║                    QUICK INSTALLATION                      ║
╚════════════════════════════════════════════════════════════╝

# Clone repository
git clone https://github.com/MiniDevHub/Custom-Code-Styles.git
cd Custom-Code-Styles

# macOS/Linux
cp Configs/Settings.json ~/Library/Application\ Support/Code/User/settings.json
cp Configs/KeyBindings.json ~/Library/Application\ Support/Code/User/keybindings.json
cp Snippets/*.json ~/Library/Application\ Support/Code/User/snippets/

# Linux (alternative)
cp Configs/Settings.json ~/.config/Code/User/settings.json
cp Configs/KeyBindings.json ~/.config/Code/User/keybindings.json
cp Snippets/*.json ~/.config/Code/User/snippets/

# Windows (PowerShell)
Copy-Item Configs\Settings.json $env:APPDATA\Code\User\settings.json
Copy-Item Configs\KeyBindings.json $env:APPDATA\Code\User\keybindings.json
Copy-Item Snippets\*.json $env:APPDATA\Code\User\snippets\

╔════════════════════════════════════════════════════════════╗
║                     BACKUP YOUR CONFIG                     ║
╚════════════════════════════════════════════════════════════╝

# Create backup before applying
BACKUP_DIR="$HOME/vscode-backup-$(date +%Y%m%d_%H%M%S)"
mkdir -p "$BACKUP_DIR"

# macOS
cp ~/Library/Application\ Support/Code/User/settings.json "$BACKUP_DIR/"
cp ~/Library/Application\ Support/Code/User/keybindings.json "$BACKUP_DIR/"
code --list-extensions > "$BACKUP_DIR/extensions.txt"

echo "✅ Backup saved to: $BACKUP_DIR"

═══════════════════════════════════════════════════════════

💡 TIP: This is MY personal, production-ready setup!
   → Use this guide to UNDERSTAND the setup
   → Use the REPO to GET the configurations
   → Combine both for maximum productivity! 🚀

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 📥 Installation

</div>

### Download & Install 🔽

```bash
# ═══════════════════════════════════════════
# VSCODE INSTALLATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                    OFFICIAL DOWNLOAD                       ║
╚════════════════════════════════════════════════════════════╝

🔗 https://code.visualstudio.com/

VERSIONS:
─────────────────────────────────────────────────────────────
├─ VSCode           Stable, recommended for most users
├─ VSCode Insiders  Beta features, updated daily
└─ VSCodium         Open-source build, no telemetry

╔════════════════════════════════════════════════════════════╗
║                  INSTALLATION METHODS                      ║
╚════════════════════════════════════════════════════════════╝

macOS:
─────────────────────────────────────────────────────────────
# Homebrew (recommended)
brew install --cask visual-studio-code

# Direct download
# Download .dmg from official site
# Drag to Applications folder

# Add to PATH
cat << EOF >> ~/.zshrc
# VSCode
export PATH="\$PATH:/Applications/Visual Studio Code.app/Contents/Resources/app/bin"
EOF

source ~/.zshrc

Linux (Ubuntu/Debian):
─────────────────────────────────────────────────────────────
# Download .deb package
wget -O code.deb 'https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64'

# Install
sudo apt install ./code.deb

# Or use snap
sudo snap install --classic code

# Arch Linux
sudo pacman -S code

Linux (Fedora/RHEL):
─────────────────────────────────────────────────────────────
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'

sudo dnf install code

Windows:
─────────────────────────────────────────────────────────────
# Chocolatey
choco install vscode

# Scoop
scoop bucket add extras
scoop install vscode

# Winget
winget install Microsoft.VisualStudioCode

# Direct download
# Download installer from official site
# Run installer

# Add to PATH (usually automatic)
# Check: Windows Settings → System → About → Advanced system settings
# → Environment Variables → PATH

╔════════════════════════════════════════════════════════════╗
║                  VERIFY INSTALLATION                       ║
╚════════════════════════════════════════════════════════════╝

# Check version
code --version

# Expected output:
# 1.85.1
# 0ee08df0cf4527e40edc9aa28f4b5bd38bbff2b2
# x64

# Launch VSCode
code

# Open folder
code ~/projects/myproject

# Open file
code file.txt

# Install extension from CLI
code --install-extension ms-python.python

# List installed extensions
code --list-extensions

╔════════════════════════════════════════════════════════════╗
║                    FIRST-TIME SETUP                        ║
╚════════════════════════════════════════════════════════════╝

STEP 1: Launch VSCode
─────────────────────────────────────────────────────────────
code

STEP 2: Sign in (Optional but recommended)
─────────────────────────────────────────────────────────────
• Click account icon (bottom left)
• Sign in with GitHub/Microsoft
• Enables Settings Sync across devices

STEP 3: Choose Theme
─────────────────────────────────────────────────────────────
Cmd+K Cmd+T → Select theme
Recommended: Dark+ (default), One Dark Pro, Dracula

STEP 4: Configure Settings Sync
─────────────────────────────────────────────────────────────
• Settings icon → Turn on Settings Sync
• Choose what to sync:
  ✓ Settings
  ✓ Keyboard Shortcuts
  ✓ Extensions
  ✓ UI State
  ✓ Snippets

STEP 5: Install Essential Extensions
─────────────────────────────────────────────────────────────
See "Essential Extensions" section below

STEP 6: Configure Basic Settings
─────────────────────────────────────────────────────────────
Cmd+, (Settings)
• Font Size: 14
• Tab Size: 2 or 4
• Format On Save: Enable
• Auto Save: afterDelay

═══════════════════════════════════════════════════════════

💡 TIP: Open Command Palette: Cmd+Shift+P (Mac) / Ctrl+Shift+P (Win/Linux)
   → This is your gateway to ALL VSCode commands!

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🎨 UI Customization

</div>

### Interface Tweaks 🖼️

```bash
# ═══════════════════════════════════════════
# UI CUSTOMIZATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                      LAYOUT CONTROLS                       ║
╚════════════════════════════════════════════════════════════╝

TOGGLE PANELS:
─────────────────────────────────────────────────────────────
Cmd+B              Toggle Sidebar
Cmd+J              Toggle Panel (Terminal/Problems/Output)
Cmd+Shift+E        Explorer
Cmd+Shift+F        Search
Cmd+Shift+G        Source Control
Cmd+Shift+D        Debug
Cmd+Shift+X        Extensions

Cmd+K Z            Zen Mode (distraction-free)
Esc Esc            Exit Zen Mode

Cmd+\              Split Editor
Cmd+1/2/3          Focus Editor Group

╔════════════════════════════════════════════════════════════╗
║                    EDITOR CUSTOMIZATION                    ║
╚════════════════════════════════════════════════════════════╝

View → Appearance:
─────────────────────────────────────────────────────────────
✓ Menu Bar           Show/Hide menu bar
✓ Activity Bar       Left sidebar icons
✓ Side Bar           File explorer, search, etc.
✓ Status Bar         Bottom bar with info
✓ Panel              Terminal, problems, output
✓ Minimap            Code overview on right
✓ Breadcrumbs        File path navigation

╔════════════════════════════════════════════════════════════╗
║                  RECOMMENDED SETTINGS                      ║
╚════════════════════════════════════════════════════════════╝

{
  // EDITOR
  "editor.fontSize": 14,
  "editor.fontFamily": "'Fira Code', 'JetBrains Mono', Menlo, Monaco, 'Courier New'",
  "editor.fontLigatures": true,
  "editor.lineHeight": 22,
  "editor.letterSpacing": 0.5,
  "editor.cursorBlinking": "smooth",
  "editor.cursorSmoothCaretAnimation": "on",
  "editor.smoothScrolling": true,

  // MINIMAP
  "editor.minimap.enabled": true,
  "editor.minimap.scale": 1,
  "editor.minimap.showSlider": "always",
  "editor.minimap.renderCharacters": false,

  // BREADCRUMBS
  "breadcrumbs.enabled": true,
  "breadcrumbs.filePath": "on",
  "breadcrumbs.symbolPath": "on",

  // WORKBENCH
  "workbench.colorTheme": "One Dark Pro",
  "workbench.iconTheme": "material-icon-theme",
  "workbench.startupEditor": "newUntitledFile",
  "workbench.sideBar.location": "left",
  "workbench.statusBar.visible": true,
  "workbench.activityBar.visible": true,

  // WINDOW
  "window.zoomLevel": 0,
  "window.title": "${dirty}${activeEditorShort}${separator}${rootName}",
  "window.nativeTabs": false,  // macOS only

  // TERMINAL
  "terminal.integrated.fontSize": 13,
  "terminal.integrated.fontFamily": "'MesloLGS NF', 'Fira Code', monospace",
  "terminal.integrated.cursorBlinking": true,
  "terminal.integrated.cursorStyle": "line"
}

╔════════════════════════════════════════════════════════════╗
║                   CUSTOM CSS & JS                          ║
╚════════════════════════════════════════════════════════════╝

CUSTOM CSS AND JS LOADER EXTENSION:
─────────────────────────────────────────────────────────────
code --install-extension be5invis.vscode-custom-css

Setup:
1. Create custom CSS file
2. Add to settings.json:

{
  "vscode_custom_css.imports": [
    "file:///path/to/custom.css",
    "file:///path/to/custom.js"
  ],
  "vscode_custom_css.policy": true
}

3. Cmd+Shift+P → "Enable Custom CSS and JS"
4. Restart VSCode

Example custom.css:
─────────────────────────────────────────────────────────────
/* Glow cursor */
.monaco-editor .cursors-layer .cursor {
  background: linear-gradient(to bottom, #7f00ff, #e100ff) !important;
  width: 3px !important;
  box-shadow: 0 0 10px 2px #bf40bf;
}

/* Custom scrollbar */
.monaco-scrollable-element > .scrollbar > .slider {
  background: rgba(121, 121, 121, 0.4) !important;
  border-radius: 10px !important;
}

/* Smoother animations */
* {
  transition: all 0.2s ease !important;
}

⚠️ WARNING: Custom CSS modifies VSCode binary
   May need to reapply after updates
   Use at your own risk

╔════════════════════════════════════════════════════════════╗
║                     FONT RECOMMENDATIONS                   ║
╚════════════════════════════════════════════════════════════╝

CODING FONTS WITH LIGATURES:
─────────────────────────────────────────────────────────────
1. Fira Code          ⭐⭐⭐⭐⭐ Most popular
   https://github.com/tonsky/FiraCode

2. JetBrains Mono     ⭐⭐⭐⭐⭐ Great readability
   https://www.jetbrains.com/lp/mono/

3. Cascadia Code      ⭐⭐⭐⭐ Microsoft's font
   https://github.com/microsoft/cascadia-code

4. Victor Mono        ⭐⭐⭐⭐ Cursive italics
   https://rubjo.github.io/victor-mono/

5. MonoLisa          ⭐⭐⭐⭐ Premium ($)
   https://www.monolisa.dev/

Installation (macOS):
─────────────────────────────────────────────────────────────
# Fira Code
brew tap homebrew/cask-fonts
brew install font-fira-code

# JetBrains Mono
brew install font-jetbrains-mono

# Cascadia Code
brew install font-cascadia-code

# Apply in VSCode
{
  "editor.fontFamily": "'Fira Code', Menlo, Monaco",
  "editor.fontLigatures": true
}

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## ⚡ Essential Extensions

</div>

### Must-Have Extensions 🔌

```bash
# ═══════════════════════════════════════════
# ESSENTIAL EXTENSIONS FOR EVERYONE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                    CODE INTELLIGENCE                       ║
╚════════════════════════════════════════════════════════════╝

1. INTELLICODE ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: VisualStudioExptTeam.vscodeintellicode
Downloads: 30M+

What it does:
• AI-assisted IntelliSense
• Smart code completion
• Learns from your patterns
• Supports 10+ languages

Install:
code --install-extension VisualStudioExptTeam.vscodeintellicode

Why essential:
✓ Suggests most relevant completions first
✓ Context-aware recommendations
✓ Works with TypeScript, Python, Java, etc.
✓ Free and from Microsoft

═══════════════════════════════════════════════════════════

2. PATH INTELLISENSE ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: christian-kohler.path-intellisense

What it does:
• Autocomplete file paths
• Works in all languages
• Relative and absolute paths

Install:
code --install-extension christian-kohler.path-intellisense

Example:
import './components/|'  ← Shows all files in folder

Configuration:
{
  "path-intellisense.autoSlashAfterDirectory": true,
  "path-intellisense.extensionOnImport": true
}

═══════════════════════════════════════════════════════════

3. AUTO RENAME TAG ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: formulahendry.auto-rename-tag

What it does:
• Rename paired HTML/XML tags
• Works in JSX, Vue, Angular

Install:
code --install-extension formulahendry.auto-rename-tag

Magic:
<div>|</div>
Change to <section> → Both tags update!
<section>|</section>

╔════════════════════════════════════════════════════════════╗
║                     CODE FORMATTING                        ║
╚════════════════════════════════════════════════════════════╝

1. PRETTIER ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: esbenp.prettier-vscode
Downloads: 35M+

What it does:
• Opinionated code formatter
• Supports 10+ languages
• Consistent style
• Format on save

Install:
code --install-extension esbenp.prettier-vscode

Configuration:
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}

Create .prettierrc:
─────────────────────────────────────────────────────────────
{
  "semi": true,
  "trailingComma": "es5",
  "singleQuote": true,
  "printWidth": 80,
  "tabWidth": 2,
  "useTabs": false
}

═══════════════════════════════════════════════════════════

2. ESLINT ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: dbaeumer.vscode-eslint
Downloads: 28M+

What it does:
• JavaScript/TypeScript linting
• Find and fix problems
• Enforce code standards

Install:
code --install-extension dbaeumer.vscode-eslint

# Install ESLint
npm install -D eslint

# Initialize config
npx eslint --init

Configuration:
{
  "eslint.validate": [
    "javascript",
    "javascriptreact",
    "typescript",
    "typescriptreact"
  ],
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}

╔════════════════════════════════════════════════════════════╗
║                    SNIPPET EXTENSIONS                      ║
╚════════════════════════════════════════════════════════════╝

1. SNIPPET CREATOR ⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: nikitaKunevich.snippet-creator

What it does:
• Create snippets from selected code
• Visual snippet editor
• Easy management

Install:
code --install-extension nikitaKunevich.snippet-creator

Usage:
1. Select code
2. Right-click → "Create Snippet"
3. Name it
4. Done!

╔════════════════════════════════════════════════════════════╗
║                     ERROR DETECTION                        ║
╚════════════════════════════════════════════════════════════╝

1. ERROR LENS ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: usernamehw.errorlens

What it does:
• Inline error messages
• Highlight entire line
• Severity colors
• Real-time feedback

Install:
code --install-extension usernamehw.errorlens

Visual:
const x = 10
const y = x + z  ← ❌ Cannot find name 'z'. ts(2304)

Configuration:
{
  "errorLens.enabled": true,
  "errorLens.fontSize": "12",
  "errorLens.delay": 500,
  "errorLens.enabledDiagnosticLevels": [
    "error",
    "warning"
  ]
}

═══════════════════════════════════════════════════════════

2. INDENT-RAINBOW ⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: oderwat.indent-rainbow

What it does:
• Colorize indentation
• Easy to spot nesting
• Customizable colors

Install:
code --install-extension oderwat.indent-rainbow

Visual indentation colors:
Level 1: Red
Level 2: Yellow
Level 3: Green
Level 4: Blue

╔════════════════════════════════════════════════════════════╗
║                   BRACKET MANAGEMENT                       ║
╚════════════════════════════════════════════════════════════╝

1. BRACKET PAIR COLORIZER (Built-in now!)
─────────────────────────────────────────────────────────────
VSCode has this built-in now!

Enable:
{
  "editor.bracketPairColorization.enabled": true,
  "editor.guides.bracketPairs": "active"
}

Colors matching brackets:
( )  ← Red
{ }  ← Yellow
[ ]  ← Purple

╔════════════════════════════════════════════════════════════╗
║                    BATCH INSTALLATION                      ║
╚════════════════════════════════════════════════════════════╝

#!/bin/bash

# Code Intelligence
code --install-extension VisualStudioExptTeam.vscodeintellicode
code --install-extension christian-kohler.path-intellisense
code --install-extension formulahendry.auto-rename-tag

# Formatting
code --install-extension esbenp.prettier-vscode
code --install-extension dbaeumer.vscode-eslint

# Snippets
code --install-extension nikitaKunevich.snippet-creator

# Error Detection
code --install-extension usernamehw.errorlens
code --install-extension oderwat.indent-rainbow

echo "✅ Essential extensions installed!"

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 💻 Language-Specific Extensions

</div>

### Your Language Extensions (From Your Config) 🔤

```bash
# ═══════════════════════════════════════════
# REFER TO YOUR PERSONAL SETUP ABOVE ☝️
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║   SEE "MY PERSONAL VSCODE SETUP" SECTION FOR:             ║
║                                                            ║
║   • JavaScript/TypeScript Extensions                      ║
║   • Python Extensions                                     ║
║   • Java Extensions                                       ║
║   • Go Extensions                                         ║
║   • Rust Extensions                                       ║
║   • Web Development Extensions                            ║
║   • Markdown Extensions                                   ║
║                                                            ║
║   This section is already comprehensive in your repo!     ║
╚════════════════════════════════════════════════════════════╝
```

---

<div align="center">

## 🚀 Productivity Boosters

</div>

### Productivity Extensions (From Your Config) ⚡

```bash
# ═══════════════════════════════════════════
# REFER TO YOUR PERSONAL SETUP ABOVE ☝️
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║   SEE "MY PERSONAL VSCODE SETUP" SECTION FOR:             ║
║                                                            ║
║   • Project Manager                                       ║
║   • Bookmarks                                             ║
║   • TODO Tree                                             ║
║   • TODO Highlight                                        ║
║   • Jumpy                                                 ║
║   • File Utils                                            ║
║   • Advanced New File                                     ║
║   • Turbo Console Log                                     ║
║   • Live Share                                            ║
║                                                            ║
║   This section is already comprehensive in your repo!     ║
╚════════════════════════════════════════════════════════════╝
```

---

<div align="center">

## 🎯 Git & Version Control

</div>

### Git Extensions & Features 📦

```bash
# ═══════════════════════════════════════════
# GIT INTEGRATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   BUILT-IN GIT FEATURES                    ║
╚════════════════════════════════════════════════════════════╝

SOURCE CONTROL PANEL:
─────────────────────────────────────────────────────────────
Cmd+Shift+G                    Open Source Control

• View changed files
• Stage/unstage files
• Commit changes
• Push/pull
• View diff inline
• Merge conflict resolution

KEYBOARD SHORTCUTS:
─────────────────────────────────────────────────────────────
Cmd+Shift+G G                  Focus source control input
Cmd+Enter                      Commit staged changes
Cmd+K Cmd+P                    Show file history

DIFF VIEW:
─────────────────────────────────────────────────────────────
• Click file → See side-by-side diff
• Inline diff view
• Navigate changes: F7 / Shift+F7
• Stage specific lines

╔════════════════════════════════════════════════════════════╗
║                     GIT EXTENSIONS                         ║
╚════════════════════════════════════════════════════════════╝

1. GITLENS ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: eamodio.gitlens
Downloads: 25M+

What it does:
• Git blame annotations
• Line history
• File history
• Compare branches
• Rich commit search
• Interactive rebase editor

Install:
code --install-extension eamodio.gitlens

Features:

GIT BLAME:
• See who changed each line
• Hover for commit details
• Click to see full commit

FILE HISTORY:
• View all commits for file
• Compare versions
• Jump to commit

COMPARE:
• Compare branches
• Compare commits
• Compare working tree

SIDEBAR VIEWS:
• Commits view
• File History
• Branches
• Remotes
• Stashes
• Tags

Configuration:
{
  "gitlens.currentLine.enabled": true,
  "gitlens.currentLine.pullRequests.enabled": true,
  "gitlens.hovers.currentLine.over": "line",
  "gitlens.codeLens.enabled": true,
  "gitlens.codeLens.authors.enabled": true,
  "gitlens.codeLens.recentChange.enabled": true
}

═══════════════════════════════════════════════════════════

2. GIT GRAPH ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: mhutchie.git-graph

What it does:
• Visual git history
• Branch visualization
• Interactive graph
• Commit details

Install:
code --install-extension mhutchie.git-graph

Usage:
• Status bar → "Git Graph" icon
• Or: Cmd+Shift+P → "Git Graph: View Git Graph"

Features:
• Visual branch tree
• Click commit → See details
• Right-click → Git operations
• Search commits
• Filter by author/branch

═══════════════════════════════════════════════════════════

3. GIT HISTORY ⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: donjayamanne.githistory

What it does:
• View git log
• File history
• Line history
• Compare versions

Install:
code --install-extension donjayamanne.githistory

Commands:
• Git: View History
• Git: View File History
• Git: View Line History

═══════════════════════════════════════════════════════════

4. GITIGNORE ⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: codezombiech.gitignore

What it does:
• Generate .gitignore files
• Templates for all languages
• Add to existing .gitignore

Install:
code --install-extension codezombiech.gitignore

Usage:
1. Cmd+Shift+P → "Add gitignore"
2. Select language (e.g., Node, Python)
3. .gitignore created with templates!

╔════════════════════════════════════════════════════════════╗
║                     GITHUB INTEGRATION                     ║
╚════════════════════════════════════════════════════════════╝

1. GITHUB PULL REQUESTS ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: GitHub.vscode-pull-request-github

What it does:
• Review PRs in VSCode
• Create PRs
• Comment on code
• Approve/merge
• Issue tracking

Install:
code --install-extension GitHub.vscode-pull-request-github

Features:
• PR list in sidebar
• Diff view
• Comment threads
• Request changes
• Merge from VSCode

Setup:
1. Sign in to GitHub (account icon)
2. Open repo
3. GitHub icon in sidebar
4. See all PRs!

═══════════════════════════════════════════════════════════

2. GITHUB CODESPACES ⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: GitHub.codespaces

What it does:
• Cloud dev environments
• VSCode in browser
• Full Linux environment
• Pre-configured

Install:
code --install-extension GitHub.codespaces

Access:
• Browser: github.com → Press . (period)
• VSCode: Connect to Codespace

╔════════════════════════════════════════════════════════════╗
║                    GIT CONFIGURATION                       ║
╚════════════════════════════════════════════════════════════╝

VSCODE GIT SETTINGS:
─────────────────────────────────────────────────────────────
{
  // Auto-fetch
  "git.autofetch": true,
  "git.autofetchPeriod": 180,

  // Confirm actions
  "git.confirmSync": false,
  "git.confirmEmptyCommits": false,

  // Branch checkout
  "git.checkoutType": "all",

  // Diff editor
  "diffEditor.ignoreTrimWhitespace": false,
  "diffEditor.renderSideBySide": true,

  // Merge editor
  "merge-conflict.autoNavigateNextConflict.enabled": true,

  // Timeline
  "timeline.excludeSources": [],

  // GitLens specific
  "gitlens.currentLine.enabled": true,
  "gitlens.hovers.currentLine.over": "line",
  "gitlens.blame.format": "${author|10} ${date}",
  "gitlens.blame.highlight.locations": [
    "gutter",
    "line",
    "overview"
  ]
}

GLOBAL GIT CONFIG:
─────────────────────────────────────────────────────────────
# Set editor
git config --global core.editor "code --wait"

# Set diff tool
git config --global diff.tool vscode
git config --global difftool.vscode.cmd 'code --wait --diff $LOCAL $REMOTE'

# Set merge tool
git config --global merge.tool vscode
git config --global mergetool.vscode.cmd 'code --wait $MERGED'

# Use VSCode for git commands
git config --global core.editor "code --wait"
git config --global sequence.editor "code --wait"

╔════════════════════════════════════════════════════════════╗
║                    BATCH INSTALLATION                      ║
╚════════════════════════════════════════════════════════════╝

#!/bin/bash

code --install-extension eamodio.gitlens
code --install-extension mhutchie.git-graph
code --install-extension donjayamanne.githistory
code --install-extension codezombiech.gitignore
code --install-extension GitHub.vscode-pull-request-github
code --install-extension GitHub.codespaces

echo "✅ Git extensions installed!"

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🐛 Debugging

</div>

### Debugging Like a Pro 🔍

```bash
# ═══════════════════════════════════════════
# DEBUGGING IN VSCODE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                    BUILT-IN DEBUGGER                       ║
╚════════════════════════════════════════════════════════════╝

LAUNCH DEBUGGER:
─────────────────────────────────────────────────────────────
F5                         Start debugging
Shift+F5                   Stop debugging
Cmd+Shift+F5               Restart debugging
F9                         Toggle breakpoint
F10                        Step over
F11                        Step into
Shift+F11                  Step out
F5                         Continue

╔════════════════════════════════════════════════════════════╗
║                   DEBUG CONFIGURATIONS                     ║
╚════════════════════════════════════════════════════════════╝

Create .vscode/launch.json:
─────────────────────────────────────────────────────────────

JAVASCRIPT/NODE.JS:
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Launch Program",
      "skipFiles": ["<node_internals>/**"],
      "program": "${workspaceFolder}/index.js"
    },
    {
      "type": "node",
      "request": "attach",
      "name": "Attach to Process",
      "port": 9229
    }
  ]
}

PYTHON:
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Python: Current File",
      "type": "python",
      "request": "launch",
      "program": "${file}",
      "console": "integratedTerminal"
    },
    {
      "name": "Python: Django",
      "type": "python",
      "request": "launch",
      "program": "${workspaceFolder}/manage.py",
      "args": ["runserver"],
      "django": true
    },
    {
      "name": "Python: Flask",
      "type": "python",
      "request": "launch",
      "module": "flask",
      "env": {
        "FLASK_APP": "app.py",
        "FLASK_DEBUG": "1"
      },
      "args": ["run"]
    }
  ]
}

CHROME DEBUGGING:
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "chrome",
      "request": "launch",
      "name": "Launch Chrome",
      "url": "http://localhost:3000",
      "webRoot": "${workspaceFolder}"
    },
    {
      "type": "chrome",
      "request": "attach",
      "name": "Attach to Chrome",
      "port": 9222,
      "webRoot": "${workspaceFolder}"
    }
  ]
}

╔════════════════════════════════════════════════════════════╗
║                    BREAKPOINTS                             ║
╚════════════════════════════════════════════════════════════╝

TYPES OF BREAKPOINTS:
─────────────────────────────────────────────────────────────
1. Line Breakpoint
   Click gutter or press F9

2. Conditional Breakpoint
   Right-click breakpoint → Edit Breakpoint
   Example: i === 10

3. Log Point
   Right-click line → Add Logpoint
   Example: "Value of x: {x}"

4. Function Breakpoint
   Debug panel → + → Function name

BREAKPOINT FEATURES:
─────────────────────────────────────────────────────────────
• Enable/disable specific breakpoints
• Hit count
• Conditional expressions
• Log messages without stopping

╔════════════════════════════════════════════════════════════╗
║                    DEBUG CONSOLE                           ║
╚════════════════════════════════════════════════════════════╝

WHILE DEBUGGING:
─────────────────────────────────────────────────────────────
• View variables
• Evaluate expressions
• Call functions
• Modify variables

Debug Console commands:
> variableName              // View value
> variableName = newValue   // Change value
> myFunction()              // Call function
> console.log(data)         // Log data

╔════════════════════════════════════════════════════════════╗
║                    WATCH EXPRESSIONS                       ║
╚════════════════════════════════════════════════════════════╝

Debug panel → Watch section:
─────────────────────────────────────────────────────────────
• Add expression to watch
• Updates on every step
• Complex expressions supported

Examples:
user.name
items.length
calculateTotal(items)

╔════════════════════════════════════════════════════════════╗
║                   DEBUG EXTENSIONS                         ║
╚════════════════════════════════════════════════════════════╝

1. DEBUGGER FOR CHROME ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: msjsdiag.debugger-for-chrome

What it does:
• Debug JavaScript in Chrome
• Breakpoints in VSCode
• Step through code
• Console integration

Install:
code --install-extension msjsdiag.debugger-for-chrome

═══════════════════════════════════════════════════════════

2. REST CLIENT ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: humao.rest-client

What it does:
• Send HTTP requests
• Test APIs
• Debug responses
• Save requests

Install:
code --install-extension humao.rest-client

Usage:
Create .http or .rest file:

# Get request
GET https://api.github.com/users/MiniDevHub

###

# Post request
POST https://api.example.com/users
Content-Type: application/json

{
  "name": "MrDib",
  "email": "test@example.com"
}

###

# With variables
@baseUrl = https://api.example.com
@token = your_token_here

GET {{baseUrl}}/users
Authorization: Bearer {{token}}

Click "Send Request" above each request!

═══════════════════════════════════════════════════════════

3. THUNDER CLIENT ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: rangav.vscode-thunder-client

What it does:
• Postman alternative
• Built into VSCode
• Collections
• Environment variables
• Test APIs

Install:
code --install-extension rangav.vscode-thunder-client

Features:
• GUI for requests
• Collections management
• Environment variables
• Import/export
• GraphQL support

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## ⌨️ Keyboard Shortcuts

</div>

### Essential Shortcuts 🔥

```bash
# ═══════════════════════════════════════════
# VSCODE KEYBOARD SHORTCUTS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                    GENERAL SHORTCUTS                       ║
╚════════════════════════════════════════════════════════════╝

COMMAND PALETTE & QUICK OPEN:
─────────────────────────────────────────────────────────────
Cmd+Shift+P / F1           Command Palette
Cmd+P                      Quick Open (files)
Cmd+Shift+N                New window
Cmd+W                      Close editor
Cmd+Shift+W                Close window
Cmd+,                      Settings
Cmd+K Cmd+S                Keyboard shortcuts

╔════════════════════════════════════════════════════════════╗
║                    FILE MANAGEMENT                         ║
╚════════════════════════════════════════════════════════════╝

Cmd+N                      New file
Cmd+O                      Open file
Cmd+S                      Save
Cmd+Shift+S                Save As
Cmd+Option+S               Save All
Cmd+K S                    Save without formatting
Cmd+K Cmd+W                Close all editors
Cmd+K R                    Reveal file in Finder
Cmd+K O                    Show file in new window

╔════════════════════════════════════════════════════════════╗
║                    EDITOR CONTROL                          ║
╚════════════════════════════════════════════════════════════╝

Cmd+\                      Split editor
Cmd+1 / 2 / 3              Focus editor group
Cmd+K Cmd+Left/Right       Focus previous/next group
Cmd+W                      Close editor
Cmd+K W                    Close all editors in group
Cmd+Option+T               Close other editors

╔════════════════════════════════════════════════════════════╗
║                    CODE EDITING                            ║
╚════════════════════════════════════════════════════════════╝

BASIC EDITING:
─────────────────────────────────────────────────────────────
Cmd+X                      Cut line
Cmd+C                      Copy line
Cmd+V                      Paste
Cmd+Shift+K                Delete line
Cmd+Enter                  Insert line below
Cmd+Shift+Enter            Insert line above
Option+Up/Down             Move line up/down
Shift+Option+Up/Down       Copy line up/down

MULTI-CURSOR:
─────────────────────────────────────────────────────────────
Cmd+D                      Select next occurrence
Cmd+K Cmd+D                Skip occurrence
Cmd+Shift+L                Select all occurrences
Option+Click               Add cursor
Cmd+Option+Up/Down         Add cursor above/below
Cmd+U                      Undo last cursor operation

SELECTION:
─────────────────────────────────────────────────────────────
Cmd+L                      Select line
Cmd+Shift+L                Select all occurrences of word
Cmd+A                      Select all
Shift+Left/Right           Expand selection
Shift+Option+Left/Right    Expand selection by word
Cmd+Shift+Right            Select to end of line
Option+Shift+Drag          Column (box) selection

SEARCH & REPLACE:
─────────────────────────────────────────────────────────────
Cmd+F                      Find
Cmd+Option+F               Replace
Cmd+G / Shift+Cmd+G        Find next/previous
Cmd+Shift+F                Find in files
Cmd+Shift+H                Replace in files
Enter / Shift+Enter        Find next/previous in find box

NAVIGATION:
─────────────────────────────────────────────────────────────
Cmd+T                      Go to Symbol in Workspace
Cmd+Shift+O                Go to Symbol in File
Ctrl+G                     Go to Line
Cmd+P                      Go to File
Cmd+Shift+M                Show Problems
F8 / Shift+F8              Go to next/previous error
Cmd+Shift+Tab              Navigate editor history
Ctrl+- / Ctrl+Shift+-      Go back/forward

CODE:
─────────────────────────────────────────────────────────────
Cmd+/                      Toggle line comment
Shift+Option+A             Toggle block comment
Cmd+]                      Indent line
Cmd+[                      Outdent line
Cmd+K Cmd+F                Format selection
Shift+Option+F             Format document
Cmd+K Cmd+X                Trim trailing whitespace
Cmd+K Cmd+C                Add line comment
Cmd+K Cmd+U                Remove line comment

FOLDING:
─────────────────────────────────────────────────────────────
Cmd+Option+[               Fold
Cmd+Option+]               Unfold
Cmd+K Cmd+0                Fold all
Cmd+K Cmd+J                Unfold all
Cmd+K Cmd+1-5              Fold level 1-5

INTELLISENSE:
─────────────────────────────────────────────────────────────
Ctrl+Space                 Trigger suggestions
Cmd+Shift+Space            Trigger parameter hints
Shift+Option+F             Format document
F12                        Go to Definition
Option+F12                 Peek Definition
Shift+F12                  Show References
F2                         Rename Symbol
Cmd+K Cmd+I                Show Hover
Cmd+.                      Quick Fix

╔════════════════════════════════════════════════════════════╗
║                    TERMINAL                                ║
╚════════════════════════════════════════════════════════════╝

Ctrl+`                     Toggle terminal
Cmd+Shift+`                Create new terminal
Cmd+K Cmd+`                Clear terminal
Cmd+\ (in terminal)        Split terminal

╔════════════════════════════════════════════════════════════╗
║                    SIDEBAR & PANELS                        ║
╚════════════════════════════════════════════════════════════╝

Cmd+B                      Toggle sidebar
Cmd+J                      Toggle panel
Cmd+Shift+E                Explorer
Cmd+Shift+F                Search
Cmd+Shift+G                Source Control
Cmd+Shift+D                Debug
Cmd+Shift+X                Extensions
Cmd+K Z                    Zen Mode

╔════════════════════════════════════════════════════════════╗
║                    DEBUGGING                               ║
╚════════════════════════════════════════════════════════════╝

F5                         Start/Continue
Shift+F5                   Stop
Cmd+Shift+F5               Restart
F9                         Toggle breakpoint
F10                        Step Over
F11                        Step Into
Shift+F11                  Step Out
Cmd+K Cmd+I                Show Hover (during debug)

╔════════════════════════════════════════════════════════════╗
║                    CUSTOM KEYBINDINGS                      ║
╚════════════════════════════════════════════════════════════╝

Open keybindings.json:
─────────────────────────────────────────────────────────────
Cmd+K Cmd+S → Click icon in top-right

Example custom keybindings:
[
  // Duplicate line
  {
    "key": "cmd+shift+d",
    "command": "editor.action.copyLinesDownAction",
    "when": "editorTextFocus"
  },

  // Delete line without cutting
  {
    "key": "cmd+shift+k",
    "command": "editor.action.deleteLines",
    "when": "editorTextFocus"
  },

  // Quick open recent
  {
    "key": "cmd+shift+r",
    "command": "workbench.action.openRecent"
  },

  // Toggle word wrap
  {
    "key": "cmd+shift+w",
    "command": "editor.action.toggleWordWrap"
  },

  // Open in browser
  {
    "key": "cmd+shift+o",
    "command": "extension.openInBrowser"
  }
]

╔════════════════════════════════════════════════════════════╗
║                    CHEAT SHEET                             ║
╚════════════════════════════════════════════════════════════╝

Download official PDF:
🔗 https://code.visualstudio.com/shortcuts/keyboard-shortcuts-macos.pdf
🔗 https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf
🔗 https://code.visualstudio.com/shortcuts/keyboard-shortcuts-linux.pdf

View in VSCode:
Cmd+K Cmd+R → Open keyboard shortcuts PDF

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔧 Settings & Configuration

</div>

### Power User Settings ⚙️

```json
// ═══════════════════════════════════════════
// COMPREHENSIVE VSCODE SETTINGS
// ═══════════════════════════════════════════

{
  // ═══════════════════════════════════════════
  // EDITOR SETTINGS
  // ═══════════════════════════════════════════

  "editor.fontSize": 14,
  "editor.fontFamily": "'Fira Code', 'JetBrains Mono', Menlo, Monaco",
  "editor.fontLigatures": true,
  "editor.lineHeight": 22,
  "editor.letterSpacing": 0.5,

  // Cursor
  "editor.cursorStyle": "line",
  "editor.cursorBlinking": "smooth",
  "editor.cursorSmoothCaretAnimation": "on",
  "editor.cursorWidth": 2,

  // Formatting
  "editor.formatOnSave": true,
  "editor.formatOnPaste": true,
  "editor.formatOnType": false,
  "editor.defaultFormatter": "esbenp.prettier-vscode",

  // Auto Save
  "files.autoSave": "afterDelay",
  "files.autoSaveDelay": 1000,

  // Suggestions
  "editor.suggestSelection": "first",
  "editor.acceptSuggestionOnCommitCharacter": true,
  "editor.acceptSuggestionOnEnter": "on",
  "editor.quickSuggestions": {
    "other": true,
    "comments": false,
    "strings": true
  },
  "editor.snippetSuggestions": "top",
  "editor.tabCompletion": "on",
  "editor.wordBasedSuggestions": true,

  // Minimap
  "editor.minimap.enabled": true,
  "editor.minimap.maxColumn": 120,
  "editor.minimap.renderCharacters": false,
  "editor.minimap.showSlider": "always",
  "editor.minimap.scale": 1,

  // Scrolling
  "editor.smoothScrolling": true,
  "editor.scrollBeyondLastLine": false,
  "editor.mouseWheelScrollSensitivity": 1,

  // Line numbers & rulers
  "editor.lineNumbers": "on",
  "editor.renderLineHighlight": "all",
  "editor.rulers": [80, 120],

  // Whitespace & indentation
  "editor.renderWhitespace": "selection",
  "editor.insertSpaces": true,
  "editor.tabSize": 2,
  "editor.detectIndentation": true,
  "editor.trimAutoWhitespace": true,
  "files.trimTrailingWhitespace": true,
  "files.insertFinalNewline": true,

  // Bracket pairs
  "editor.bracketPairColorization.enabled": true,
  "editor.guides.bracketPairs": "active",
  "editor.matchBrackets": "always",

  // Code actions
  "editor.codeActionsOnSave": {
    "source.fixAll": true,
    "source.organizeImports": true,
    "source.fixAll.eslint": true
  },

  // Word wrap
  "editor.wordWrap": "off",
  "editor.wordWrapColumn": 80,

  // ═══════════════════════════════════════════
  // WORKBENCH
  // ═══════════════════════════════════════════

  "workbench.startupEditor": "newUntitledFile",
  "workbench.colorTheme": "One Dark Pro",
  "workbench.iconTheme": "material-icon-theme",
  "workbench.sideBar.location": "left",
  "workbench.statusBar.visible": true,
  "workbench.activityBar.visible": true,
  "workbench.editor.enablePreview": false,
  "workbench.editor.tabCloseButton": "right",
  "workbench.editor.tabSizing": "shrink",
  "workbench.editor.limit.enabled": false,
  "workbench.list.smoothScrolling": true,

  // ═══════════════════════════════════════════
  // FILES
  // ═══════════════════════════════════════════

  "files.eol": "\n",
  "files.encoding": "utf8",
  "files.exclude": {
    "**/.git": true,
    "**/.DS_Store": true,
    "**/node_modules": true,
    "**/__pycache__": true,
    "**/.pytest_cache": true,
    "**/*.pyc": true
  },
  "files.watcherExclude": {
    "**/.git/objects/**": true,
    "**/node_modules/**": true,
    "**/.venv/**": true
  },
  "files.associations": {
    "*.json": "jsonc",
    ".prettierrc": "json",
    ".eslintrc": "json"
  },

  // ═══════════════════════════════════════════
  // TERMINAL
  // ═══════════════════════════════════════════

  "terminal.integrated.fontSize": 13,
  "terminal.integrated.fontFamily": "'MesloLGS NF', 'Fira Code', monospace",
  "terminal.integrated.cursorBlinking": true,
  "terminal.integrated.cursorStyle": "line",
  "terminal.integrated.scrollback": 10000,
  "terminal.integrated.copyOnSelection": true,
  "terminal.integrated.confirmOnExit": "hasChildProcesses",
  "terminal.integrated.enableBell": false,
  "terminal.integrated.env.osx": {
    "FIG_NEW_SESSION": "1"
  },

  // ═══════════════════════════════════════════
  // EXPLORER
  // ═══════════════════════════════════════════

  "explorer.confirmDelete": false,
  "explorer.confirmDragAndDrop": false,
  "explorer.compactFolders": false,
  "explorer.sortOrder": "type",

  // ═══════════════════════════════════════════
  // SEARCH
  // ═══════════════════════════════════════════

  "search.exclude": {
    "**/node_modules": true,
    "**/bower_components": true,
    "**/.venv": true,
    "**/__pycache__": true,
    "**/dist": true,
    "**/build": true,
    "**/.next": true
  },
  "search.useIgnoreFiles": true,
  "search.smartCase": true,

  // ═══════════════════════════════════════════
  // GIT
  // ═══════════════════════════════════════════

  "git.autofetch": true,
  "git.autofetchPeriod": 180,
  "git.confirmSync": false,
  "git.enableSmartCommit": true,
  "git.ignoreMissingGitWarning": false,
  "git.suggestSmartCommit": true,
  "git.openRepositoryInParentFolders": "always",

  // ═══════════════════════════════════════════
  // EXTENSIONS
  // ═══════════════════════════════════════════

  "extensions.autoUpdate": true,
  "extensions.ignoreRecommendations": false,

  // ═══════════════════════════════════════════
  // LANGUAGE-SPECIFIC
  // ═══════════════════════════════════════════

  // JavaScript/TypeScript
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "[javascriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },

  // Python
  "[python]": {
    "editor.defaultFormatter": "ms-python.black-formatter",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "source.organizeImports": true
    }
  },
  "python.linting.enabled": true,
  "python.linting.pylintEnabled": true,
  "python.formatting.provider": "black",
  "python.analysis.typeCheckingMode": "basic",

  // HTML/CSS
  "[html]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[css]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[scss]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },

  // JSON
  "[json]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[jsonc]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },

  // Markdown
  "[markdown]": {
    "editor.wordWrap": "on",
    "editor.quickSuggestions": {
      "comments": "on",
      "strings": "on",
      "other": "on"
    }
  },

  // ═══════════════════════════════════════════
  // EMMET
  // ═══════════════════════════════════════════

  "emmet.includeLanguages": {
    "javascript": "javascriptreact",
    "typescript": "typescriptreact",
    "vue-html": "html"
  },
  "emmet.triggerExpansionOnTab": true,
  "emmet.showSuggestionsAsSnippets": true,

  // ═══════════════════════════════════════════
  // PERFORMANCE
  // ═══════════════════════════════════════════

  "files.watcherExclude": {
    "**/.git/objects/**": true,
    "**/.git/subtree-cache/**": true,
    "**/node_modules/*/**": true,
    "**/.hg/store/**": true
  }
}
```

---

<div align="center">

## 🎭 Themes & Icons

</div>

### Beautiful VSCode 🎨

```bash
# ═══════════════════════════════════════════
# COLOR THEMES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                    TOP COLOR THEMES                        ║
╚════════════════════════════════════════════════════════════╝

1. ONE DARK PRO ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: zhuangtongfa.material-theme
Downloads: 8M+

Install:
code --install-extension zhuangtongfa.material-theme

Variants:
• One Dark Pro
• One Dark Pro Darker
• One Dark Pro Flat

═══════════════════════════════════════════════════════════

2. DRACULA OFFICIAL ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: dracula-theme.theme-dracula

Install:
code --install-extension dracula-theme.theme-dracula

═══════════════════════════════════════════════════════════

3. NIGHT OWL ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: sdras.night-owl

Install:
code --install-extension sdras.night-owl

Variants:
• Night Owl
• Night Owl (No Italics)
• Night Owl Light

═══════════════════════════════════════════════════════════

4. GITHUB THEME ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: GitHub.github-vscode-theme

Install:
code --install-extension GitHub.github-vscode-theme

Variants:
• GitHub Dark
• GitHub Light
• GitHub Dark Dimmed

═══════════════════════════════════════════════════════════

5. TOKYO NIGHT ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: enkia.tokyo-night

Install:
code --install-extension enkia.tokyo-night

═══════════════════════════════════════════════════════════

6. MONOKAI PRO ⭐⭐⭐⭐ (Premium $)
─────────────────────────────────────────────────────────────
Publisher: monokai.theme-monokai-pro-vscode

Install:
code --install-extension monokai.theme-monokai-pro-vscode

Free trial: 7 days
Price: €10

╔════════════════════════════════════════════════════════════╗
║                    ICON THEMES                             ║
╚════════════════════════════════════════════════════════════╝

1. MATERIAL ICON THEME ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: PKief.material-icon-theme
Downloads: 15M+

Install:
code --install-extension PKief.material-icon-theme

Features:
• 1000+ file icons
• Folder icons
• Customizable
• Active development

═══════════════════════════════════════════════════════════

2. MATERIAL PRODUCT ICONS ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: PKief.material-product-icons

Install:
code --install-extension PKief.material-product-icons

Changes VSCode UI icons

═══════════════════════════════════════════════════════════

3. VSCODE ICONS ⭐⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: vscode-icons-team.vscode-icons

Install:
code --install-extension vscode-icons-team.vscode-icons

═══════════════════════════════════════════════════════════

4. HELIUM ICON THEME ⭐⭐⭐⭐
─────────────────────────────────────────────────────────────
Publisher: helgardrichard.helium-icon-theme

Install:
code --install-extension helgardrichard.helium-icon-theme

╔════════════════════════════════════════════════════════════╗
║                    APPLY THEMES                            ║
╚════════════════════════════════════════════════════════════╝

# Open theme selector
Cmd+K Cmd+T

# Settings.json
{
  "workbench.colorTheme": "One Dark Pro",
  "workbench.iconTheme": "material-icon-theme",
  "workbench.productIconTheme": "material-product-icons"
}

╔════════════════════════════════════════════════════════════╗
║                    CUSTOMIZE THEMES                        ║
╚════════════════════════════════════════════════════════════╝

# Add to settings.json
{
  "workbench.colorCustomizations": {
    "[One Dark Pro]": {
      "editor.background": "#1e1e1e",
      "sideBar.background": "#252526",
      "activityBar.background": "#333333"
    }
  },

  "editor.tokenColorCustomizations": {
    "[One Dark Pro]": {
      "comments": "#6A9955",
      "strings": "#CE9178"
    }
  }
}

╔════════════════════════════════════════════════════════════╗
║                    BATCH INSTALLATION                      ║
╚════════════════════════════════════════════════════════════╝

#!/bin/bash

# Color themes
code --install-extension zhuangtongfa.material-theme
code --install-extension dracula-theme.theme-dracula
code --install-extension sdras.night-owl
code --install-extension GitHub.github-vscode-theme
code --install-extension enkia.tokyo-night

# Icon themes
code --install-extension PKief.material-icon-theme
code --install-extension PKief.material-product-icons
code --install-extension vscode-icons-team.vscode-icons

echo "✅ Themes installed!"

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 💡 Pro Tips

</div>

### VSCode Mastery 🚀

```bash
# ═══════════════════════════════════════════
# PRO TIPS & TRICKS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                    HIDDEN FEATURES                         ║
╚════════════════════════════════════════════════════════════╝

1. QUICK OPEN TRICKS
─────────────────────────────────────────────────────────────
Cmd+P                      Quick Open
  → Type filename
  → Add : for line number (file.js:42)
  → Add @ for symbols (@functionName)
  → Add # for workspace symbols

Examples:
  app.ts:20               Go to line 20 in app.ts
  @useState               Find useState in current file
  #MyComponent            Find MyComponent in workspace

═══════════════════════════════════════════════════════════

2. MULTI-CURSOR MASTERY
─────────────────────────────────────────────────────────────
Cmd+D                      Select next occurrence
Cmd+K Cmd+D                Skip occurrence
Cmd+Shift+L                Select all occurrences
Option+Click               Add cursor at position
Cmd+Option+Up/Down         Add cursor above/below

Pro tip: Select text → Cmd+D repeatedly to select all same text!

═══════════════════════════════════════════════════════════

3. COLUMN SELECTION
─────────────────────────────────────────────────────────────
Shift+Option+Drag          Column selection
Cmd+Shift+Option+Arrows    Column selection with keyboard

Use case: Edit multiple lines at once!

const a = 1;
const b = 2;
const c = 3;

→ Select "const" on all lines → Type "let" → Done!

═══════════════════════════════════════════════════════════

4. RENAME SYMBOL
─────────────────────────────────────────────────────────────
F2                         Rename symbol everywhere

Works with:
• Variables
• Functions
• Classes
• Imports

Renames across ALL files in project!

═══════════════════════════════════════════════════════════

5. BREADCRUMBS NAVIGATION
─────────────────────────────────────────────────────────────
Cmd+Shift+.                Focus breadcrumbs
Cmd+Shift+;                Navigate breadcrumbs

Quick navigation through file structure!

═══════════════════════════════════════════════════════════

6. TIMELINE VIEW
─────────────────────────────────────────────────────────────
Explorer → Timeline (bottom)

Shows:
• Git history for file
• Local file history
• Unsaved changes

═══════════════════════════════════════════════════════════

7. WORKSPACE TRUST
─────────────────────────────────────────────────────────────
Security feature for untrusted code

Cmd+Shift+P → "Manage Workspace Trust"

Restricted Mode:
• No extensions run
• Tasks disabled
• Debugging disabled

╔════════════════════════════════════════════════════════════╗
║                    PRODUCTIVITY HACKS                      ║
╚════════════════════════════════════════════════════════════╝

1. EMMET SHORTCUTS
─────────────────────────────────────────────────────────────
Type: ul>li*5>a
Press: Tab

Result:
<ul>
  <li><a href=""></a></li>
  <li><a href=""></a></li>
  <li><a href=""></a></li>
  <li><a href=""></a></li>
  <li><a href=""></a></li>
</ul>

More examples:
.container>h1+p              Class with children
#header>nav>ul>li*3>a        ID with nested structure
div.box{Item $}*5            Text content with numbering

═══════════════════════════════════════════════════════════

2. SNIPPETS
─────────────────────────────────────────────────────────────
Create custom snippets:
Cmd+Shift+P → "Configure User Snippets"

Example React component snippet:
{
  "React Component": {
    "prefix": "rfc",
    "body": [
      "import React from 'react';",
      "",
      "const ${1:ComponentName} = () => {",
      "  return (",
      "    <div>",
      "      $0",
      "    </div>",
      "  );",
      "};",
      "",
      "export default ${1:ComponentName};"
    ]
  }
}

═══════════════════════════════════════════════════════════

3. TASKS
─────────────────────────────────────────────────────────────
Create .vscode/tasks.json:

{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Build",
      "type": "shell",
      "command": "npm run build",
      "group": {
        "kind": "build",
        "isDefault": true
      }
    },
    {
      "label": "Test",
      "type": "shell",
      "command": "npm test",
      "group": "test"
    }
  ]
}

Run: Cmd+Shift+B (build) or Cmd+Shift+P → "Run Task"

═══════════════════════════════════════════════════════════

4. SETTINGS SYNC
─────────────────────────────────────────────────────────────
Settings icon → Turn on Settings Sync

Syncs:
✓ Settings
✓ Keybindings
✓ Extensions
✓ UI State
✓ Snippets

Works across:
• Multiple machines
• Different OS
• VSCode & VSCode Insiders

═══════════════════════════════════════════════════════════

5. PORTABLE MODE
─────────────────────────────────────────────────────────────
Create "data" folder next to VSCode executable

VSCode will:
• Store all data in folder
• No system-wide changes
• Perfect for USB drive

Useful for:
• Testing configurations
• Multiple VSCode installations
• Portable development environment

╔════════════════════════════════════════════════════════════╗
║                    PERFORMANCE TIPS                        ║
╚════════════════════════════════════════════════════════════╝

1. EXCLUDE FILES FROM WATCHER
─────────────────────────────────────────────────────────────
{
  "files.watcherExclude": {
    "**/.git/objects/**": true,
    "**/node_modules/**": true,
    "**/dist/**": true,
    "**/build/**": true
  }
}

2. DISABLE UNUSED EXTENSIONS
─────────────────────────────────────────────────────────────
Extensions → Disable per workspace

Right-click extension → "Disable (Workspace)"

3. INCREASE MEMORY LIMIT
─────────────────────────────────────────────────────────────
# macOS/Linux
code --max-memory=8192

# Add to launch command or alias

4. PROCESS EXPLORER
─────────────────────────────────────────────────────────────
Cmd+Shift+P → "Developer: Open Process Explorer"

See what's using CPU/memory

╔════════════════════════════════════════════════════════════╗
║                    USEFUL COMMANDS                         ║
╚════════════════════════════════════════════════════════════╝

# Compare files
code --diff file1.txt file2.txt

# Open with specific language
code --file-uri vscode-remote://ssh-remote+server/path

# List extensions
code --list-extensions

# Install extension
code --install-extension publisher.extension

# Uninstall extension
code --uninstall-extension publisher.extension

# Open logs
Cmd+Shift+P → "Developer: Open Logs Folder"

# Clear cache
# macOS: ~/Library/Application Support/Code/Cache
# Linux: ~/.config/Code/Cache
# Windows: %APPDATA%\Code\Cache

═══════════════════════════════════════════════════════════

💡 ULTIMATE TIP: Cmd+Shift+P is your best friend!
   → Access EVERY command
   → Discover new features
   → No need to remember all shortcuts!

═══════════════════════════════════════════════════════════
```

---

<div align="center">

**Built with ⚙️ by MrDib**

_"Code is like humor. When you have to explain it, it's bad."_ – Cory House

**Master your editor, master your craft!** 🚀

</div>
