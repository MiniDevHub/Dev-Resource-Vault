<div align="center">

# 🎯 VSCode Setup Guide & Recommendations 🎯

### 🚀 _Transform VSCode into your ultimate coding companion_ 🚀

![VSCode](https://img.shields.io/badge/VSCode-Customization_Guide-blue?style=for-the-badge)
![Extensions](https://img.shields.io/badge/Extensions-Carefully_Curated-green?style=for-the-badge)

### **💡 Looking for a complete VSCode configuration?**

### Check out my [Custom-Code-Styles](https://github.com/MiniDevHub/Custom-Code-Styles.git) repository for my personal setup including settings, keybindings, snippets, and themes!

---

## 🌟 Essential Extensions by Category 🌟

### 🛠️ Core Development 🛠️

| Extension           | Why You Need It             | Pro Tip                  |
| ------------------- | --------------------------- | ------------------------ |
| **Prettier**        | Auto-format code on save    | Set as default formatter |
| **ESLint**          | Catch errors before runtime | Enable auto-fix on save  |
| **GitLens**         | Git superpowers in VSCode   | Use blame annotations    |
| **Error Lens**      | Inline error display        | Customize error colors   |
| **Better Comments** | Highlight TODOs, FIXMEs     | Create custom tags       |

### 💻 Language Support 💻

| Extension               | Best For          | Features               |
| ----------------------- | ----------------- | ---------------------- |
| **ES7+ React snippets** | React developers  | `rafce` for components |
| **Vetur**               | Vue.js developers | Template validation    |
| **Python**              | Python developers | IntelliSense, linting  |
| **Go**                  | Go developers     | Auto imports           |
| **Live Sass Compiler**  | Sass users        | Watch and compile      |

### 🚀 Productivity Boosters 🚀

| Extension                  | What It Does                | Game Changer Feature |
| -------------------------- | --------------------------- | -------------------- |
| **Auto Rename Tag**        | Rename paired HTML/JSX tags | Works with JSX!      |
| **Path Intellisense**      | Autocomplete file paths     | Works in imports     |
| **Bracket Pair Colorizer** | Color-match brackets        | Custom colors        |
| **TODO Highlight**         | Highlight TODO comments     | Custom keywords      |
| **Project Manager**        | Quick project switching     | Workspace groups     |

### 🎯 Advanced Tools 🎯

| Extension          | Use Case             | Why It's Awesome          |
| ------------------ | -------------------- | ------------------------- |
| **Thunder Client** | API testing          | No need for Postman       |
| **Docker**         | Container management | View logs in VSCode       |
| **Remote - SSH**   | Remote development   | Code on servers           |
| **Live Share**     | Collaborative coding | Real-time editing         |
| **GitHub Copilot** | AI pair programming  | Context-aware suggestions |

</div>

---

<div align="center">

## 💎 **Hidden Gems** (Underrated Extensions) 💎

</div>

### Developer Experience

```

📊 Import Cost

- Shows package size inline
- Prevent bloated bundles
- Real-time feedback

🎨 Color Highlight

- Preview colors in code
- Works with all formats
- Hover for picker

📁 File Utils

- Duplicate, move, rename
- Right-click operations
- Keyboard shortcuts

⚡ Turbo Console Log

- Insert console.logs fast
- Ctrl+Alt+L magic
- Auto variable names

🔍 Code Spell Checker

- Catch typos in code
- Multiple languages
- Custom dictionaries

```

### Themes & Visual

```

🌙 Theme Recommendations:

1.  One Dark Pro - Balanced & beautiful
2.  Dracula Official - High contrast
3.  Material Theme - Multiple variants
4.  Winter is Coming - Blue-tinted
5.  Synthwave '84 - Neon glow (fun!)

🎨 Icon Themes:

1.  Material Icon Theme
2.  VSCode Icons
3.  Bearded Icons
4.  Chalice Icon Theme

```

---

<div align="center">

## ⚙️ Recommended Settings ⚙️

</div>

### Performance Settings

```json
{
  // Faster startup
  "extensions.autoCheckUpdates": false,
  "extensions.autoUpdate": false,
  "update.mode": "manual",

  // Better performance
  "files.exclude": {
    "**/node_modules": true,
    "**/.git": true,
    "**/dist": true,
    "**/build": true
  },

  // Disable telemetry
  "telemetry.telemetryLevel": "off",

  // Faster search
  "search.exclude": {
    "**/node_modules": true,
    "**/bower_components": true,
    "**/*.code-search": true
  }
}
```

### Quality of Life Settings

```json
{
  // Auto-save
  "files.autoSave": "afterDelay",
  "files.autoSaveDelay": 1000,

  // Better visuals
  "editor.cursorBlinking": "smooth",
  "editor.cursorSmoothCaretAnimation": true,
  "editor.smoothScrolling": true,

  // Code formatting
  "editor.formatOnSave": true,
  "editor.formatOnPaste": true,

  // Git improvements
  "git.autofetch": true,
  "git.confirmSync": false,

  // Terminal
  "terminal.integrated.cursorBlinking": true,
  "terminal.integrated.fontFamily": "MesloLGS NF"
}
```

---

<div align="center">

## ⌨️ Must-Know Shortcuts ⌨️

### Navigation

| Action          | Mac            | Windows/Linux   |
| --------------- | -------------- | --------------- |
| Quick Open      | `Cmd+P`        | `Ctrl+P`        |
| Command Palette | `Cmd+Shift+P`  | `Ctrl+Shift+P`  |
| Go to Symbol    | `Cmd+Shift+O`  | `Ctrl+Shift+O`  |
| Go to Line      | `Cmd+G`        | `Ctrl+G`        |
| Switch Tabs     | `Cmd+1,2,3...` | `Ctrl+1,2,3...` |

### Editing

| Action        | Mac               | Windows/Linux     |
| ------------- | ----------------- | ----------------- |
| Multi-cursor  | `Cmd+D`           | `Ctrl+D`          |
| Column select | `Alt+Shift+Click` | `Alt+Shift+Click` |
| Move line     | `Alt+↑/↓`         | `Alt+↑/↓`         |
| Copy line     | `Shift+Alt+↑/↓`   | `Shift+Alt+↑/↓`   |
| Delete line   | `Cmd+Shift+K`     | `Ctrl+Shift+K`    |

### Productivity

| Action           | Mac           | Windows/Linux  |
| ---------------- | ------------- | -------------- |
| Toggle Terminal  | `Ctrl+``      | `Ctrl+``       |
| Toggle Sidebar   | `Cmd+B`       | `Ctrl+B`       |
| Find in Files    | `Cmd+Shift+F` | `Ctrl+Shift+F` |
| Replace in Files | `Cmd+Shift+H` | `Ctrl+Shift+H` |
| Format Document  | `Shift+Alt+F` | `Shift+Alt+F`  |

</div>

---

<div align="center">

## 🚀 Setup Workflow 🚀

</div>

### For New Developers

1. **Install VSCode** → [Download here](https://code.visualstudio.com)
2. **Install essential extensions** (start with top 5)
3. **Choose a theme** you love
4. **Configure basic settings** (auto-save, format on save)
5. **Learn keyboard shortcuts** (print cheat sheet)

### For Experienced Developers

1. **Export your settings** → Settings Sync
2. **Create workspace-specific settings**
3. **Set up code snippets** for your stack
4. **Configure debugging** for your languages
5. **Optimize for performance** (exclude folders)

---

<div align="center">

## 💡 Pro Tips & Tricks 💡

</div>

### Multi-Cursor Magic

```
1. Select word: Cmd+D (repeat for next occurrence)
2. Select all occurrences: Cmd+Shift+L
3. Add cursor above/below: Cmd+Alt+↑/↓
4. Box selection: Shift+Alt+drag
```

### File Navigation

```
1. Breadcrumbs: Enable for easy navigation
2. Cmd+P then @ for symbols in file
3. Cmd+P then : for go to line
4. Cmd+P then > for commands
```

### Terminal Tips

```
1. Split terminal: Cmd+\
2. Clear terminal: Cmd+K
3. Kill terminal: trash icon
4. Rename terminal: double-click tab
```

---

<div align="center">

## 🔗 Learning Resources 🔗

</div>

### Official Resources

- [VSCode Docs](https://code.visualstudio.com/docs)
- [VSCode Tips & Tricks](https://code.visualstudio.com/docs/getstarted/tips-and-tricks)
- [Keyboard Shortcuts PDF](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-macos.pdf)

### Community Resources

- [Awesome VSCode](https://github.com/viatsko/awesome-vscode)
- [VSCode Can Do That](https://vscodecandothat.com)
- [VSCode Rocks](https://vscode.rocks)

### YouTube Channels

- [Code With Me](https://www.youtube.com/@CodeWithMe) - VSCode tutorials
- [Fireship](https://www.youtube.com/@Fireship) - Quick VSCode tips
- [The Net Ninja](https://www.youtube.com/@NetNinja) - Setup guides

---

<div align="center">

## 🎨 My Setup 🎨

</div>

**🔗 Full Configuration**: See my [Custom-Code-Styles](https://github.com/yourusername/Custom-Code-Styles) repository for:

- Complete `settings.json`
- Custom keybindings
- Snippets collection
- Custom CSS/JS modifications
- Installation guide

### Quick Preview

- **Theme**: One Dark Pro
- **Font**: Fira Code with ligatures
- **Icons**: Material Icon Theme
- **Key Extensions**: 25+ carefully selected

---

<div align="center">

## 🤔 FAQ 🤔

</div>

**Q: How many extensions is too many?**
A: Keep it under 30-40. Disable workspace-specific ones.

**Q: VSCode is slow, help!**
A: Check View → Process Explorer. Disable unused extensions.

**Q: Best font for coding?**
A: Try Fira Code, JetBrains Mono, or Cascadia Code (all free).

**Q: How to sync settings?**
A: Use Settings Sync (built-in) or my Custom-Code-Styles repo.

---

<div align="center">

### 🚀 Ready to supercharge your VSCode?

Check out my complete setup: [Custom-Code-Styles](https://github.com/yourusername/Custom-Code-Styles)

**Happy Coding!** 💻

</div>
