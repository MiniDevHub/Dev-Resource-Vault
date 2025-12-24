<div align="center">

# 🧠 JetBrains IDEs - Intelligent Development

### _The smartest IDEs for professional developers_ 💡

![JetBrains](https://img.shields.io/badge/JetBrains-IDEs-black?style=for-the-badge&logo=jetbrains)
![IntelliJ IDEA](https://img.shields.io/badge/IntelliJ-IDEA-blue?style=for-the-badge&logo=intellijidea)
![Productivity](https://img.shields.io/badge/Productivity-Maximum-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Guide-Complete-gold?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 JetBrains IDE Family](#-jetbrains-ide-family)
  - [Complete Lineup](#the-complete-lineup-)
  - [Choosing Your IDE](#choosing-the-right-ide)
  - [Edition Comparison](#-edition-comparison)
- [⚡ Essential Shortcuts](#-essential-shortcuts)
  - [Navigation Shortcuts](#navigation-shortcuts-️)
  - [Editing Shortcuts](#editing-shortcuts-️)
  - [Refactoring Shortcuts](#refactoring-shortcuts-)
  - [Running & Debugging](#running--debugging-)
  - [Code Generation](#code-generation-)
  - [Version Control](#version-control-)
- [🔧 Configuration & Settings](#-configuration--settings)
  - [Essential Settings](#essential-settings-️)
  - [Performance Settings](#recommended-settings-for-performance-)
  - [Keymap Customization](#keymap-customization)
- [🎨 Themes & Appearance](#-themes--appearance)
  - [Popular Themes](#popular-themes-)
  - [Icon Packs](#icon-packs-)
  - [Custom Fonts](#custom-fonts-)
- [🔌 Must-Have Plugins](#-must-have-plugins)
  - [Productivity Boosters](#1️⃣-productivity-boosters)
  - [Git & Version Control](#2️⃣-git--version-control)
  - [Code Quality](#3️⃣-code-quality)
  - [Framework Support](#4️⃣-framework-support)
  - [UI/UX Enhancements](#5️⃣-uiux-enhancements)
  - [AI Assistants](#6️⃣-ai-assistants)
- [💡 Pro Tips & Tricks](#-pro-tips--tricks)
  - [Power User Features](#power-user-features-)
  - [Productivity Hacks](#productivity-hacks-)
  - [Debugging Tips](#debugging-tips-)
- [🎓 Learning Resources](#-learning-resources)
- [🐛 Troubleshooting](#-troubleshooting)
- [🎯 Final Pro Tips](#-final-pro-tips)

---

<div align="center">

## 🎯 JetBrains IDE Family

_One platform, multiple specialized IDEs_ 🌟

</div>

### The Complete Lineup 🚀

```
═══════════════════════════════════════════════════════════
JETBRAINS IDE ECOSYSTEM
═══════════════════════════════════════════════════════════

                    ┌──────────────────┐
                    │  IntelliJ IDEA   │
                    │   (Platform)     │
                    └────────┬─────────┘
                             │
        ┌────────────────────┼────────────────────┐
        │                    │                    │
        ▼                    ▼                    ▼
   Java/Kotlin          Web Dev            Other Languages
        │                    │                    │
        ├─ IntelliJ IDEA     ├─ WebStorm          ├─ PyCharm (Python)
        ├─ Android Studio    ├─ PhpStorm          ├─ RubyMine (Ruby)
        └─ Rider (.NET)      └─ DataGrip (SQL)    ├─ GoLand (Go)
                                                   ├─ CLion (C/C++)
                                                   ├─ RustRover (Rust)
                                                   └─ Fleet (Next-gen)

ALL SHARE:
✓ Same keyboard shortcuts
✓ Same UI paradigm
✓ Same plugin ecosystem
✓ Same refactoring engine
✓ Same Git integration
```

<div align="center">

| IDE               | Language/Framework     | Best For                    | Download                                          | Price     |
| ----------------- | ---------------------- | --------------------------- | ------------------------------------------------- | --------- |
| **IntelliJ IDEA** | Java, Kotlin, Scala    | Enterprise Java development | [Download](https://www.jetbrains.com/idea/)       | Free/Paid |
| **PyCharm**       | Python                 | Data science & web apps     | [Download](https://www.jetbrains.com/pycharm/)    | Free/Paid |
| **WebStorm**      | JavaScript, TypeScript | Modern web development      | [Download](https://www.jetbrains.com/webstorm/)   | Paid      |
| **PhpStorm**      | PHP                    | PHP & WordPress dev         | [Download](https://www.jetbrains.com/phpstorm/)   | Paid      |
| **Rider**         | C#, .NET               | Cross-platform .NET         | [Download](https://www.jetbrains.com/rider/)      | Paid      |
| **CLion**         | C, C++                 | System programming          | [Download](https://www.jetbrains.com/clion/)      | Paid      |
| **RubyMine**      | Ruby                   | Ruby & Rails development    | [Download](https://www.jetbrains.com/ruby/)       | Paid      |
| **GoLand**        | Go                     | Go microservices            | [Download](https://www.jetbrains.com/go/)         | Paid      |
| **DataGrip**      | SQL                    | Database management         | [Download](https://www.jetbrains.com/datagrip/)   | Paid      |
| **RustRover**     | Rust                   | Rust development            | [Download](https://www.jetbrains.com/rust/)       | Paid      |
| **Fleet**         | Polyglot               | Lightweight, collaborative  | [Download](https://www.jetbrains.com/fleet/)      | Free Beta |
| **Aqua**          | Test Automation        | Test framework development  | [Download](https://www.jetbrains.com/aqua/)       | Paid      |
| **Writerside**    | Documentation          | Technical documentation     | [Download](https://www.jetbrains.com/writerside/) | Free Beta |

</div>

> **💡 Pro Tip:** All JetBrains IDEs share the same underlying platform (IntelliJ Platform), so shortcuts, settings, and plugins work consistently across all tools! 🎯

---

### Choosing the Right IDE

```bash
# ═══════════════════════════════════════════
# DECISION TREE
# ═══════════════════════════════════════════

START: What's your primary language/stack?

├─❓ Java, Kotlin, Scala, Android?
│  └─✅ IntelliJ IDEA Ultimate
│     • Best Java IDE in the world
│     • Spring Framework support
│     • Database tools included
│     • Web development features
│
├─❓ Python (Data Science, Web, ML)?
│  └─✅ PyCharm Professional
│     • Jupyter Notebook integration
│     • Scientific packages support
│     • Django/Flask support
│     • Remote interpreter support
│
├─❓ JavaScript, TypeScript, React, Vue, Angular?
│  └─✅ WebStorm
│     • Best JS/TS support
│     • Framework templates
│     • Node.js debugging
│     • npm/yarn integration
│
├─❓ PHP, WordPress, Laravel?
│  └─✅ PhpStorm
│     • PHP-specific refactoring
│     • Composer support
│     • Database & SQL
│     • HTTP client
│
├─❓ C#, .NET, Unity, ASP.NET?
│  └─✅ Rider
│     • ReSharper built-in
│     • .NET & .NET Core
│     • Unity support
│     • Cross-platform
│
├─❓ C, C++, CMake, Embedded?
│  └─✅ CLion
│     • CMake integration
│     • Remote development
│     • Embedded systems
│     • Memory debugger
│
├─❓ Go, Microservices, Cloud Native?
│  └─✅ GoLand
│     • Go modules support
│     • Debugging & profiling
│     • Docker & Kubernetes
│     • Database tools
│
├─❓ Ruby, Rails?
│  └─✅ RubyMine
│     • Rails support
│     • RVM/rbenv integration
│     • Test frameworks
│     • Database tools
│
├─❓ Rust?
│  └─✅ RustRover
│     • Cargo integration
│     • Error highlighting
│     • Refactoring support
│     • Debugging
│
├─❓ Multiple languages / Polyglot?
│  ├─ Option 1: IntelliJ IDEA Ultimate
│  │  (Supports most languages via plugins)
│  └─ Option 2: Fleet (Modern, lightweight)
│
└─❓ Database work only?
   └─✅ DataGrip
      • Universal database tool
      • SQL editor & console
      • ER diagrams
      • Query execution plans

═══════════════════════════════════════════════════════════

ALL-IN-ONE OPTIONS:

🎯 All JetBrains Toolbox ($249/year)
   • Access to ALL IDEs
   • Best for polyglot developers
   • Professional use
   • Regular updates

🆓 IntelliJ IDEA Community Edition (Free)
   • Java, Kotlin, Groovy, Scala
   • Android development
   • Maven, Gradle, SBT
   • Git, SVN, Mercurial
   • No Spring, no web dev, no database tools

🆓 PyCharm Community Edition (Free)
   • Python only
   • No web frameworks
   • No database tools
   • No remote development
   • Good for learning/hobby

💡 Fleet (Free Beta)
   • New lightweight IDE
   • Collaborative features
   • Distributed development
   • Multiple languages
   • Still in active development
```

---

<div align="center">

## ⚡ Essential Shortcuts

_Master these shortcuts to 10x your productivity_ ⌨️

</div>

### Navigation Shortcuts 🗺️

```bash
═══════════════════════════════════════════════════════════
NAVIGATION - THE FOUNDATION OF SPEED
═══════════════════════════════════════════════════════════

🎯 THE MOST IMPORTANT SHORTCUT:

⇧⇧ (Double Shift) | Shift Shift - SEARCH EVERYWHERE
─────────────────────────────────────────────────────────
The ULTIMATE navigation tool. Searches:
• Files
• Classes
• Symbols
• Actions
• Settings
• Tool windows
• Recently opened files

Advanced Search Everything:
⇧⇧ then type:
  /filename    → Search files only
  #action      → Search actions only
  :123         → Go to line 123
  @method      → Search symbols
  .recent      → Recent files

Example: ⇧⇧ → /User.java → Enter (opens file)
Example: ⇧⇧ → #Format → Enter (formats code)
Example: ⇧⇧ → :42 → Enter (jumps to line 42)

═══════════════════════════════════════════════════════════
```

<div align="center">

| Action                     | macOS               | Windows/Linux            | Description               |
| -------------------------- | ------------------- | ------------------------ | ------------------------- |
| **Search Everywhere**      | `⇧⇧` (Double Shift) | `Shift Shift`            | Universal search          |
| **Find File**              | `⌘⇧O`               | `Ctrl+Shift+N`           | Navigate to file          |
| **Find Class**             | `⌘O`                | `Ctrl+N`                 | Navigate to class         |
| **Find Symbol**            | `⌘⌥O`               | `Ctrl+Alt+Shift+N`       | Navigate to symbol/method |
| **Recent Files**           | `⌘E`                | `Ctrl+E`                 | Recently opened files     |
| **Recent Locations**       | `⌘⇧E`               | `Ctrl+Shift+E`           | Recently edited locations |
| **Go to Line**             | `⌘L`                | `Ctrl+G`                 | Jump to line number       |
| **Navigate Back**          | `⌘[` or `⌘⌥←`       | `Ctrl+Alt+←`             | Previous location         |
| **Navigate Forward**       | `⌘]` or `⌘⌥→`       | `Ctrl+Alt+→`             | Next location             |
| **Go to Declaration**      | `⌘B` or `⌘Click`    | `Ctrl+B` or `Ctrl+Click` | Jump to definition        |
| **Go to Implementation**   | `⌘⌥B`               | `Ctrl+Alt+B`             | Jump to implementation    |
| **Go to Type Declaration** | `⌘⇧B`               | `Ctrl+Shift+B`           | Go to type definition     |
| **Find Usages**            | `⌥F7`               | `Alt+F7`                 | Find where used           |
| **Show Usages**            | `⌘⌥F7`              | `Ctrl+Alt+F7`            | Show usages popup         |
| **File Structure**         | `⌘F12`              | `Ctrl+F12`               | View file structure popup |
| **Type Hierarchy**         | `⌃H`                | `Ctrl+H`                 | Show class hierarchy      |
| **Call Hierarchy**         | `⌃⌥H`               | `Ctrl+Alt+H`             | Show method call tree     |
| **Select In**              | `⌥F1`               | `Alt+F1`                 | Locate in Project/Files   |
| **Recent Changes**         | `⌥⇧C`               | `Alt+Shift+C`            | View recent changes       |
| **Bookmarks**              | `F3`                | `F11`                    | Toggle bookmark           |
| **Show Bookmarks**         | `⌘F3`               | `Ctrl+F11`               | View all bookmarks        |
| **Next Error**             | `F2`                | `F2`                     | Jump to next error        |
| **Previous Error**         | `⇧F2`               | `Shift+F2`               | Jump to previous error    |
| **Navigate to Test**       | `⌘⇧T`               | `Ctrl+Shift+T`           | Jump between test/source  |

</div>

```bash
# ═══════════════════════════════════════════
# PRO NAVIGATION PATTERNS
# ═══════════════════════════════════════════

# 1. NAVIGATE WITHOUT MOUSE
⇧⇧ → Search file → Enter → Start coding
⌘E → Select recent file → Enter
⌘⇧E → Select recent location → Enter

# 2. JUMP TO SPECIFIC CODE
⌘O → Type class name → Enter
⌘⌥O → Type method name → Enter
⌘L → Type line number → Enter

# 3. EXPLORE CODEBASE
⌘B on symbol → Go to definition
⌘⌥B on interface → See implementations
⌥F7 on method → See all usages
⌃H on class → See class hierarchy

# 4. UNDERSTAND CALL FLOW
⌃⌥H on method → See who calls this method
F2 → Jump through errors/warnings

# 5. REMEMBER IMPORTANT LOCATIONS
F3 on line → Bookmark it
⌘F3 → View all bookmarks → Jump to any

# ═══════════════════════════════════════════
# NAVIGATION WORKFLOW EXAMPLE
# ═══════════════════════════════════════════

Scenario: Find where User.getName() is called

1. ⇧⇧ → Type "User" → Enter (opens User class)
2. ⌘F → Type "getName" → Enter (finds method)
3. ⌥F7 → See all usages (popup shows everywhere it's called)
4. Click usage → Jump to that location
5. ⌘[ → Go back to User class
6. ⌘] → Go forward to usage again

Time: ~5 seconds! ⚡
```

---

### Editing Shortcuts ✏️

<div align="center">

| Action                     | macOS                                  | Windows/Linux                             | Description                 |
| -------------------------- | -------------------------------------- | ----------------------------------------- | --------------------------- |
| **Duplicate Line**         | `⌘D`                                   | `Ctrl+D`                                  | Duplicate current line      |
| **Delete Line**            | `⌘⌫`                                   | `Ctrl+Y`                                  | Delete current line         |
| **Move Line Up**           | `⌥⇧↑`                                  | `Alt+Shift+↑`                             | Move line up                |
| **Move Line Down**         | `⌥⇧↓`                                  | `Alt+Shift+↓`                             | Move line down              |
| **Move Statement Up**      | `⌘⇧↑`                                  | `Ctrl+Shift+↑`                            | Move statement up (smart)   |
| **Move Statement Down**    | `⌘⇧↓`                                  | `Ctrl+Shift+↓`                            | Move statement down         |
| **Comment Line**           | `⌘/`                                   | `Ctrl+/`                                  | Toggle line comment         |
| **Block Comment**          | `⌘⌥/`                                  | `Ctrl+Shift+/`                            | Toggle block comment        |
| **Reformat Code**          | `⌘⌥L`                                  | `Ctrl+Alt+L`                              | Auto-format code            |
| **Optimize Imports**       | `⌃⌥O`                                  | `Ctrl+Alt+O`                              | Remove unused imports       |
| **Auto-Indent Lines**      | `⌃⌥I`                                  | `Ctrl+Alt+I`                              | Fix indentation             |
| **Surround With**          | `⌘⌥T`                                  | `Ctrl+Alt+T`                              | Wrap code (if, try, etc)    |
| **Complete Statement**     | `⌘⇧↩`                                  | `Ctrl+Shift+Enter`                        | Complete line intelligently |
| **Start New Line**         | `⇧↩`                                   | `Shift+Enter`                             | New line below              |
| **Start New Line Above**   | `⌘⌥↩`                                  | `Ctrl+Alt+Enter`                          | New line above              |
| **Join Lines**             | `⌃⇧J`                                  | `Ctrl+Shift+J`                            | Join lines intelligently    |
| **Expand Selection**       | `⌥↑`                                   | `Ctrl+W`                                  | Expand selection smartly    |
| **Shrink Selection**       | `⌥↓`                                   | `Ctrl+Shift+W`                            | Shrink selection            |
| **Multiple Cursors**       | `⌥⌥ + ↑/↓`                             | `Ctrl+Ctrl + ↑/↓`                         | Add cursor above/below      |
| **Select Next Occurrence** | `⌃G`                                   | `Alt+J`                                   | Multi-select same text      |
| **Unselect Occurrence**    | `⌃⇧G`                                  | `Alt+Shift+J`                             | Deselect last occurrence    |
| **Select All Occurrences** | `⌃⌘G`                                  | `Ctrl+Alt+Shift+J`                        | Select all occurrences      |
| **Column Selection Mode**  | `⌘⇧8`                                  | `Alt+Shift+Insert`                        | Toggle column select        |
| **Clone Caret Below**      | press `⌥` twice + hold, then press `↓` | press `Ctrl` twice + hold, then press `↓` | Add caret below             |
| **Clone Caret Above**      | press `⌥` twice + hold, then press `↑` | press `Ctrl` twice + hold, then press `↑` | Add caret above             |

</div>

```bash
# ═══════════════════════════════════════════
# ADVANCED EDITING TECHNIQUES
# ═══════════════════════════════════════════

# 1. SMART SELECTION
Position cursor inside string: "Hello World"
⌥↑ → Selects "Hello"
⌥↑ → Selects "Hello World" (with quotes)
⌥↑ → Selects entire statement
⌥↑ → Selects entire method
⌥↑ → Selects entire class

# 2. MULTIPLE CURSORS
Scenario: Change variable name in multiple places

Method A: Select Next Occurrence
1. Select variable name
2. ⌃G → Selects next occurrence
3. ⌃G → Selects next occurrence (repeat)
4. Type new name → Changes all at once

Method B: Column Selection
1. ⌘⇧8 → Enable column selection
2. ⌥ + Drag → Select column
3. Type → Changes all lines

Method C: Find & Replace
1. ⌘R → Open replace dialog
2. Type old → Type new
3. ⌘⌥↩ → Replace all

# 3. SMART CODE COMPLETION
⌘⇧↩ (Complete Statement) is MAGIC:

// Before (cursor at |):
if (user.isActive()|

// After pressing ⌘⇧↩:
if (user.isActive()) {
    |
}

// Before:
System.out.println("Hello"|

// After ⌘⇧↩:
System.out.println("Hello");
|

# 4. SURROUND WITH
Select code → ⌘⌥T → Choose:
• if
• if/else
• while
• for
• try/catch
• try/catch/finally
• Runnable
• synchronized
• Custom templates

Example:
1. Select: user.save();
2. ⌘⌥T → Choose "try/catch"
3. Result:
try {
    user.save();
} catch (Exception e) {
    e.printStackTrace();
}

# 5. MOVE STATEMENT (SMART!)
⌘⇧↑/↓ moves code intelligently:

// Before:
public void method() {
    int x = 5;
    String name = "test";  // Cursor here
    System.out.println(x);
}

// After ⌘⇧↑:
public void method() {
    String name = "test";  // Moved up
    int x = 5;
    System.out.println(x);
}

# Respects scope and syntax!

# ═══════════════════════════════════════════
# EDITING WORKFLOW EXAMPLES
# ═══════════════════════════════════════════

Example 1: Duplicate & Modify Line
1. Write: const user = getUser();
2. ⌘D → Duplicates line
3. Edit: const admin = getAdmin();

Example 2: Rename Multiple Occurrences
1. Select variable name
2. ⌃G → Add next occurrence
3. ⌃G → Keep adding
4. Type new name → All changed

Example 3: Comment Block of Code
1. Select lines
2. ⌘/ → Comments all
3. ⌘/ again → Uncomments

Example 4: Reformat Messy Code
1. Select code (or ⌘A for all)
2. ⌘⌥L → Perfectly formatted
3. ⌃⌥O → Removes unused imports

Example 5: Surround with Try-Catch
1. Select risky code
2. ⌘⌥T → Choose "try/catch"
3. Edit exception handling
```

---

### Refactoring Shortcuts 🔄

<div align="center">

| Action                | macOS | Windows/Linux      | Description              |
| --------------------- | ----- | ------------------ | ------------------------ |
| **Refactor This**     | `⌃T`  | `Ctrl+Alt+Shift+T` | Show refactor menu       |
| **Rename**            | `⇧F6` | `Shift+F6`         | Rename symbol everywhere |
| **Change Signature**  | `⌘F6` | `Ctrl+F6`          | Change method signature  |
| **Move**              | `F6`  | `F6`               | Move class/method        |
| **Copy**              | `F5`  | `F5`               | Copy class/file          |
| **Safe Delete**       | `⌘⌫`  | `Alt+Delete`       | Delete with usage check  |
| **Extract Variable**  | `⌘⌥V` | `Ctrl+Alt+V`       | Extract to variable      |
| **Extract Constant**  | `⌘⌥C` | `Ctrl+Alt+C`       | Extract to constant      |
| **Extract Field**     | `⌘⌥F` | `Ctrl+Alt+F`       | Extract to field         |
| **Extract Method**    | `⌘⌥M` | `Ctrl+Alt+M`       | Extract to method        |
| **Extract Parameter** | `⌘⌥P` | `Ctrl+Alt+P`       | Extract to parameter     |
| **Inline**            | `⌘⌥N` | `Ctrl+Alt+N`       | Inline variable/method   |
| **Pull Members Up**   | -     | -                  | Move to parent class     |
| **Push Members Down** | -     | -                  | Move to subclass         |

</div>

```bash
# ═══════════════════════════════════════════
# REFACTORING MASTERY
# ═══════════════════════════════════════════

🎯 GOLDEN RULE: Always use ⇧F6 to rename!
Never find-and-replace. IntelliJ knows context.

# ═══════════════════════════════════════════
# REFACTORING SCENARIOS
# ═══════════════════════════════════════════

Scenario 1: EXTRACT METHOD
─────────────────────────────────────────────
// Before (messy code):
public void processOrder(Order order) {
    // Validation
    if (order.getItems().isEmpty()) {
        throw new IllegalArgumentException("Empty order");
    }
    if (order.getTotal() < 0) {
        throw new IllegalArgumentException("Negative total");
    }

    // Processing
    orderRepository.save(order);
    emailService.sendConfirmation(order);
}

// Refactor:
1. Select validation code
2. ⌘⌥M → Extract Method
3. Name it: validateOrder
4. Result:

public void processOrder(Order order) {
    validateOrder(order);
    orderRepository.save(order);
    emailService.sendConfirmation(order);
}

private void validateOrder(Order order) {
    if (order.getItems().isEmpty()) {
        throw new IllegalArgumentException("Empty order");
    }
    if (order.getTotal() < 0) {
        throw new IllegalArgumentException("Negative total");
    }
}

Scenario 2: EXTRACT VARIABLE
─────────────────────────────────────────────
// Before:
if (user.getAge() >= 18 && user.getAge() < 65) {
    // ...
}

// Refactor:
1. Select: user.getAge()
2. ⌘⌥V → Extract Variable
3. Name it: age
4. IntelliJ replaces ALL occurrences

// After:
int age = user.getAge();
if (age >= 18 && age < 65) {
    // ...
}

Scenario 3: RENAME (SAFEST WAY)
─────────────────────────────────────────────
// Before:
class User {
    private String n;  // Bad name!

    public String getN() { return n; }
    public void setN(String n) { this.n = n; }
}

User u = new User();
u.setN("MrDib");
System.out.println(u.getN());

// Refactor:
1. Put cursor on 'n' field
2. ⇧F6 → Rename
3. Type: name
4. Enter

// After (ALL references updated):
class User {
    private String name;

    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
}

User u = new User();
u.setName("MrDib");
System.out.println(u.getName());

Scenario 4: CHANGE METHOD SIGNATURE
─────────────────────────────────────────────
// Before:
public void sendEmail(String to, String subject, String body) {
    // Implementation
}

// Called in 50 places:
sendEmail("user@example.com", "Hello", "Content");

// Refactor to add CC parameter:
1. Put cursor on method
2. ⌘F6 → Change Signature
3. Add parameter: String cc
4. Set default value: ""
5. Enter

// After (ALL 50 calls updated automatically!):
public void sendEmail(String to, String subject, String body, String cc) {
    // Implementation
}

sendEmail("user@example.com", "Hello", "Content", "");

Scenario 5: EXTRACT CONSTANT
─────────────────────────────────────────────
// Before:
if (user.getAge() >= 18) {
    // ...
}
if (employee.getAge() >= 18) {
    // ...
}

// Refactor:
1. Select: 18
2. ⌘⌥C → Extract Constant
3. Name it: LEGAL_AGE
4. Result:

private static final int LEGAL_AGE = 18;

if (user.getAge() >= LEGAL_AGE) {
    // ...
}
if (employee.getAge() >= LEGAL_AGE) {
    // ...
}

Scenario 6: INLINE VARIABLE
─────────────────────────────────────────────
// Before (unnecessary variable):
String name = user.getName();
System.out.println(name);

// Refactor:
1. Cursor on 'name'
2. ⌘⌥N → Inline

// After:
System.out.println(user.getName());

# ═══════════════════════════════════════════
# SAFE REFACTORING WORKFLOW
# ═══════════════════════════════════════════

1. Make sure tests pass ✅
2. Refactor using IDE shortcuts
3. Review changes (⌘⌥Z to undo if needed)
4. Run tests again ✅
5. Commit

# ═══════════════════════════════════════════
# REFACTORING MENU (⌃T)
# ═══════════════════════════════════════════

Press ⌃T to see ALL available refactorings:

• Rename                    ⇧F6
• Extract Method            ⌘⌥M
• Extract Variable          ⌘⌥V
• Extract Constant          ⌘⌥C
• Extract Field             ⌘⌥F
• Extract Parameter         ⌘⌥P
• Inline                    ⌘⌥N
• Move                      F6
• Copy                      F5
• Safe Delete               ⌘⌫
• Change Signature          ⌘F6
• Pull Members Up
• Push Members Down
• Extract Interface
• Extract Superclass
• Use Interface Where Possible
• Replace Constructor with Factory
• Encapsulate Fields
• Replace Inheritance with Delegation
• Remove Middleman
• Introduce Parameter Object
• ... and many more!

IntelliJ has 60+ refactorings! 🤯
```

---

### Running & Debugging 🐛

<div align="center">

| Action                     | macOS              | Windows/Linux    | Description              |
| -------------------------- | ------------------ | ---------------- | ------------------------ |
| **Run**                    | `⌃R`               | `Shift+F10`      | Run current file         |
| **Debug**                  | `⌃D`               | `Shift+F9`       | Debug current file       |
| **Run Anything**           | `⌃⌃` (Double Ctrl) | `Ctrl Ctrl`      | Run command/config       |
| **Run Context**            | `⌃⇧R`              | `Ctrl+Shift+F10` | Run from context         |
| **Debug Context**          | `⌃⇧D`              | `Ctrl+Shift+F9`  | Debug from context       |
| **Stop**                   | `⌘F2`              | `Ctrl+F2`        | Stop program             |
| **Toggle Breakpoint**      | `⌘F8`              | `Ctrl+F8`        | Add/remove breakpoint    |
| **View Breakpoints**       | `⌘⇧F8`             | `Ctrl+Shift+F8`  | Manage all breakpoints   |
| **Step Over**              | `F8`               | `F8`             | Execute next line        |
| **Step Into**              | `F7`               | `F7`             | Step into method         |
| **Smart Step Into**        | `⇧F7`              | `Shift+F7`       | Choose method to step in |
| **Step Out**               | `⇧F8`              | `Shift+F8`       | Step out of method       |
| **Resume Program**         | `⌘⌥R`              | `F9`             | Continue execution       |
| **Run to Cursor**          | `⌥F9`              | `Alt+F9`         | Run until cursor         |
| **Evaluate Expression**    | `⌥F8`              | `Alt+F8`         | Evaluate while debugging |
| **Quick Evaluate**         | `⌘⌥F8`             | `Ctrl+Alt+F8`    | Quick expression eval    |
| **Show Execution Point**   | `⌘F10`             | `Alt+F10`        | Show current line        |
| **Toggle Line Breakpoint** | `⌘F8`              | `Ctrl+F8`        | Add/remove breakpoint    |

</div>

```bash
# ═══════════════════════════════════════════
# DEBUGGING LIKE A PRO
# ═══════════════════════════════════════════

🎯 DEBUGGING WORKFLOW:

1. SET BREAKPOINT
   Click gutter (left side of code) or ⌘F8
   Red dot appears ●

2. START DEBUGGING
   ⌃D (Debug) or click Bug icon 🐛

3. WHEN BREAKPOINT HITS:
   ┌─────────────────────────────────────┐
   │  Debug Tool Window Opens            │
   ├─────────────────────────────────────┤
   │  Frames  │  Variables  │  Watches   │
   │  ────────┼─────────────┼──────────  │
   │  main()  │  x = 5      │            │
   │  ↓       │  name = "Hi"│            │
   │  myFn()  │  user = {...│            │
   └─────────────────────────────────────┘

4. NAVIGATE THROUGH CODE:
   F8      → Step Over (next line)
   F7      → Step Into (enter method)
   ⇧F8     → Step Out (exit method)
   ⌥F9     → Run to Cursor
   ⌘⌥R/F9  → Resume (continue)

5. INSPECT VALUES:
   • Hover over variables
   • View in Variables panel
   • ⌥F8 → Evaluate any expression

6. STOP DEBUGGING:
   ⌘F2 → Stop

# ═══════════════════════════════════════════
# ADVANCED DEBUGGING TECHNIQUES
# ═══════════════════════════════════════════

1. CONDITIONAL BREAKPOINTS
─────────────────────────────────────────────
Right-click breakpoint ● → Add condition

Example:
for (int i = 0; i < 1000; i++) {
    processItem(i);  // ● Breakpoint here
}

Condition: i == 500
Now only breaks when i equals 500!

Other conditions:
• i > 100 && i < 200
• user.getName().equals("MrDib")
• items.size() > 10

2. EXCEPTION BREAKPOINTS
─────────────────────────────────────────────
Run → View Breakpoints → + → Java Exception Breakpoints
Add: NullPointerException

Now breaks whenever NPE occurs (even without breakpoint)!

Catches exceptions you didn't expect! 🎯

3. METHOD BREAKPOINTS
─────────────────────────────────────────────
Click on method name line (not inside method)

Breaks when method is:
• Entered
• Exited
• Both

Great for interface/abstract methods!

4. FIELD WATCHPOINTS
─────────────────────────────────────────────
Click on field declaration line

Breaks when field is:
• Read (accessed)
• Written (modified)
• Both

Example:
private String status;  // ● Watchpoint here

Breaks every time status changes!

5. EVALUATE EXPRESSION (⌥F8)
─────────────────────────────────────────────
While debugging, press ⌥F8

Can execute ANY code:
• Call methods: user.getName()
• Create objects: new ArrayList<>()
• Complex expressions: users.stream().filter(...)
• Even modify state! (use carefully)

Example debugging session:
1. Break at: processUser(user);
2. ⌥F8 → Type: user.getAge() > 18
3. See result: true
4. ⌥F8 → Type: user.setAge(25)  // Modify!
5. Continue debugging with new value

6. DROP FRAME (GO BACK IN TIME!)
─────────────────────────────────────────────
While debugging, right-click on frame → Drop Frame

Goes back to beginning of method!
Can re-execute method with different values

Limitations:
• Can't undo external changes (database, files)
• Can't go before method entry

7. SMART STEP INTO (⇧F7)
─────────────────────────────────────────────
Code: result = service.process(dao.getUser());
Regular F7 → Steps into first method
Smart ⇧F7 → Choose which method:
1. service.process()
2. dao.getUser()

Select the one you care about! 🎯

8. RUN TO CURSOR (⌥F9)
─────────────────────────────────────────────
Place cursor on line you want to reach
⌥F9 → Runs until that line

Temporary breakpoint! Very useful.

# ═══════════════════════════════════════════
# DEBUGGING SCENARIO: FIXING A BUG
# ═══════════════════════════════════════════

Bug: NullPointerException in getUserEmail()

Step 1: SET EXCEPTION BREAKPOINT
Run → View Breakpoints → + → Java Exception
Add: NullPointerException

Step 2: RUN IN DEBUG MODE
⌃D → App crashes, breaks at exception

Step 3: INSPECT STATE
Variables panel shows:
user = null  // AHA! 🎯

Step 4: TRACE BACKWARDS
Look at call stack:
getUserEmail() ← Called from here
getUser()      ← Problem is here!

Step 5: FIX
Add null check:
if (user == null) {
    throw new IllegalArgumentException("User not found");
}

Step 6: TEST
Remove exception breakpoint
Run tests ✅

# ═══════════════════════════════════════════
# PERFORMANCE DEBUGGING
# ═══════════════════════════════════════════

1. CPU PROFILER
Run → Profile 'Application'

Shows:
• Which methods are slow
• Call counts
• CPU time per method

2. MEMORY PROFILER
Helps find memory leaks:
• See object counts
• Heap dumps
• GC activity

Access: Run → Profile with...
```

---

### Code Generation 🤖

<div align="center">

| Action                         | macOS | Windows/Linux      | Description           |
| ------------------------------ | ----- | ------------------ | --------------------- |
| **Generate Code**              | `⌘N`  | `Alt+Insert`       | Generate menu         |
| **Override Methods**           | `⌃O`  | `Ctrl+O`           | Override methods      |
| **Implement Methods**          | `⌃I`  | `Ctrl+I`           | Implement interface   |
| **Show Intention Actions**     | `⌥↩`  | `Alt+Enter`        | Quick fixes / actions |
| **Complete Current Statement** | `⌘⇧↩` | `Ctrl+Shift+Enter` | Complete line         |
| **Parameter Info**             | `⌘P`  | `Ctrl+P`           | Show parameters       |
| **Quick Documentation**        | `⌃J`  | `Ctrl+Q`           | Show docs popup       |
| **External Documentation**     | `⇧F1` | `Shift+F1`         | Open in browser       |

</div>

```bash
# ═══════════════════════════════════════════
# CODE GENERATION MAGIC
# ═══════════════════════════════════════════

🎯 GENERATE MENU (⌘N / Alt+Insert)

Inside class, press ⌘N:

╔════════════════════════════════════╗
║     Generate Menu                  ║
╠════════════════════════════════════╣
║  Constructor                       ║
║  Getter                            ║
║  Setter                            ║
║  Getter and Setter                 ║
║  equals() and hashCode()           ║
║  toString()                        ║
║  Override Methods...               ║
║  Implement Methods...              ║
║  Delegate Methods...               ║
║  Test...                           ║
║  Copyright                         ║
╚════════════════════════════════════╝

# ═══════════════════════════════════════════
# GENERATION EXAMPLES
# ═══════════════════════════════════════════

Example 1: GENERATE GETTERS/SETTERS
─────────────────────────────────────────────
// Start with:
public class User {
    private String name;
    private int age;
    private String email;
}

// Generate:
1. ⌘N → Getter and Setter
2. Select all fields
3. Result:

public class User {
    private String name;
    private int age;
    private String email;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }
}

Example 2: GENERATE EQUALS & HASHCODE
─────────────────────────────────────────────
⌘N → equals() and hashCode()
→ Select fields to include
→ Choose template (Java 7+, IntelliJ IDEA, etc.)

Generated:
@Override
public boolean equals(Object o) {
    if (this == o) return true;
    if (o == null || getClass() != o.getClass()) return false;
    User user = (User) o;
    return age == user.age &&
           Objects.equals(name, user.name) &&
           Objects.equals(email, user.email);
}

@Override
public int hashCode() {
    return Objects.hash(name, age, email);
}

Example 3: GENERATE CONSTRUCTOR
─────────────────────────────────────────────
⌘N → Constructor
→ Select fields to include

Generated:
public User(String name, int age, String email) {
    this.name = name;
    this.age = age;
    this.email = email;
}

Example 4: IMPLEMENT INTERFACE
─────────────────────────────────────────────
// Code:
public class UserService implements Service {
    // Empty
}

// Generate:
1. ⌃I (Implement Methods)
2. Select methods from Service interface
3. IntelliJ generates stubs:

public class UserService implements Service {
    @Override
    public void start() {
        // TODO: Implement
    }

    @Override
    public void stop() {
        // TODO: Implement
    }
}

# ═══════════════════════════════════════════
# INTENTION ACTIONS (⌥↩) - THE SWISS ARMY KNIFE
# ═══════════════════════════════════════════

Press ⌥↩ (Alt+Enter) for context-aware actions:

Scenario 1: IMPORT CLASS
// Code:
List users;  // 'List' is red (not imported)

// Action:
1. Cursor on 'List'
2. ⌥↩ → Import class
3. Selects correct import automatically

Scenario 2: CREATE CLASS/METHOD
// Code:
User user = new User();  // 'User' doesn't exist

// Action:
1. ⌥↩ on 'User'
2. Choose: Create class 'User'
3. IntelliJ creates the class!

// Code:
user.sendEmail();  // Method doesn't exist

// Action:
1. ⌥↩ on 'sendEmail'
2. Choose: Create method 'sendEmail'
3. IntelliJ adds the method!

Scenario 3: QUICK FIXES
// Code:
String result = processData();  // Returns Integer, not String

// Action:
1. ⌥↩ on error
2. Options:
   • Change return type to 'Integer'
   • Cast expression to 'String'
   • Change variable type to 'Integer'

Scenario 4: REFACTORING SUGGESTIONS
// Code:
if (user.getName() != null) {
    System.out.println(user.getName());
}

// Action:
1. ⌥↩ inside if
2. Choose: Replace 'if' with 'if-not-null' pattern
3. Generates better code

Scenario 5: CONVERT/TRANSFORM
// Code:
String result = "";
for (String item : list) {
    result += item;
}

// Action:
1. ⌥↩ on loop
2. Choose: Replace with Stream API
3. Result:
String result = list.stream()
    .collect(Collectors.joining());

# ═══════════════════════════════════════════
# LIVE TEMPLATES (TYPE & EXPAND)
# ═══════════════════════════════════════════

IntelliJ has built-in templates that expand:

Java:
─────
psvm + Tab → public static void main(String[] args)
sout + Tab → System.out.println();
fori + Tab → for (int i = 0; i < ; i++) { }
iter + Tab → for (Type item : collection) { }
ifn + Tab  → if (variable == null) { }
inn + Tab  → if (variable != null) { }

JavaScript/TypeScript:
─────
cl + Tab   → console.log();
fun + Tab  → function name() { }
foreach + Tab → array.forEach(item => { });

Python:
─────
main + Tab → if __name__ == '__main__':
def + Tab  → def function_name(param):

# ═══════════════════════════════════════════
# POSTFIX COMPLETION (TYPE BACKWARDS)
# ═══════════════════════════════════════════

Type expression, then add postfix:

// Type: user.null + Tab
// Becomes: if (user == null) { }

// Type: user.notnull + Tab
// Becomes: if (user != null) { }

// Type: list.for + Tab
// Becomes: for (Type item : list) { }

// Type: result.var + Tab
// Becomes: Type result = expression;

// Type: value.return + Tab
// Becomes: return value;

// Type: value.sout + Tab
// Becomes: System.out.println(value);

// Type: condition.if + Tab
// Becomes: if (condition) { }

// Type: value.cast + Tab
// Becomes: ((Type) value)

Examples:
─────────
user.getName().notnull
→ if (user.getName() != null) { }

numbers.for
→ for (Integer number : numbers) { }

result.return
→ return result;

# ═══════════════════════════════════════════
# CUSTOM LIVE TEMPLATES
# ═══════════════════════════════════════════

Create your own templates!

Settings → Editor → Live Templates → + (Add)

Example: Create "test" template

Abbreviation: test
Description: Create test method
Template text:
@Test
public void test$NAME$() {
    $END$
}

Variables:
$NAME$ → capitalize(camelCase(fileNameWithoutExtension()))

Usage:
Type: test + Tab
Result:
@Test
public void testUserService() {
    |  ← Cursor here
}

# ═══════════════════════════════════════════
# GENERATE TEST CLASS
# ═══════════════════════════════════════════

In production class:
⌘⇧T → Create Test
→ Select test framework (JUnit 5, etc.)
→ Select methods to test
→ IntelliJ creates test class with stubs!

// From: UserService.java
public class UserService {
    public User getUser(int id) { }
    public void saveUser(User user) { }
}

// Generates: UserServiceTest.java
class UserServiceTest {
    @Test
    void getUser() {
        // TODO
    }

    @Test
    void saveUser() {
        // TODO
    }
}
```

---

### Version Control 🔀

<div align="center">

| Action                  | macOS   | Windows/Linux    | Description       |
| ----------------------- | ------- | ---------------- | ----------------- |
| **Commit**              | `⌘K`    | `Ctrl+K`         | Commit changes    |
| **Push**                | `⌘⇧K`   | `Ctrl+Shift+K`   | Push commits      |
| **Update Project**      | `⌘T`    | `Ctrl+T`         | Pull/update       |
| **VCS Operations**      | `⌃V`    | `` Alt+`  ``     | Show VCS menu     |
| **Show Diff**           | `⌘D`    | `Ctrl+D`         | Show changes      |
| **Show History**        | `⌃V, H` | `` Alt+`  ``, H` | View file history |
| **Annotate**            | `⌃V, A` | `` Alt+`  ``, A` | Git blame         |
| **Compare with Branch** | -       | -                | Compare branches  |
| **Rollback**            | `⌘⌥Z`   | `Ctrl+Alt+Z`     | Rollback changes  |

</div>

```bash
# ═══════════════════════════════════════════
# GIT INTEGRATION
# ═══════════════════════════════════════════

🎯 IntelliJ has THE BEST Git integration!

# ═══════════════════════════════════════════
# COMMIT WORKFLOW
# ═══════════════════════════════════════════

1. Make changes to code
2. ⌘K (Commit) → Opens commit dialog

Commit Dialog:
┌─────────────────────────────────────────┐
│ Commit to main                          │
├─────────────────────────────────────────┤
│ ☑ UserService.java     (Modified)      │
│ ☑ UserController.java  (New)           │
│ ☐ Test.java            (Modified)      │
├─────────────────────────────────────────┤
│ Commit Message:                         │
│ ┌─────────────────────────────────────┐ │
│ │ feat: add user service              │ │
│ │                                     │ │
│ │ - Add getUserById method            │ │
│ │ - Add saveUser method               │ │
│ └─────────────────────────────────────┘ │
├─────────────────────────────────────────┤
│ [Commit] [Commit and Push]              │
└─────────────────────────────────────────┘

3. Select files to commit
4. Write commit message
5. Commit or Commit and Push

# ═══════════════════════════════════════════
# VIEW CHANGES
# ═══════════════════════════════════════════

Method 1: GUTTER INDICATORS
─────────────────────────────────────────────
Look at left side of editor (gutter):

│ Blue line    → Line modified
│ Green line   → Line added
│ Red triangle → Line deleted

Click gutter marker:
• See diff
• Rollback change
• Show history

Method 2: SHOW DIFF (⌘D)
─────────────────────────────────────────────
Select file in commit dialog → ⌘D

Shows side-by-side diff:
┌──────────────┬──────────────┐
│   Before     │    After     │
├──────────────┼──────────────┤
│ old line     │              │ ← Deleted
│              │ new line     │ ← Added
│ same line    │ same line    │
│ modified old │ modified new │ ← Changed
└──────────────┴──────────────┘

In diff:
• Accept left/right changes
• Navigate with F7/⇧F7
• Edit inline

Method 3: LOCAL HISTORY
─────────────────────────────────────────────
Right-click file → Local History → Show History

Shows ALL changes (even uncommitted!):
• Every save
• Every refactoring
• Can restore from any point

Safety net! 🛡️

# ═══════════════════════════════════════════
# GIT OPERATIONS
# ═══════════════════════════════════════════

PULL/UPDATE (⌘T)
─────────────────────────────────────────────
⌘T → Update Project

Options:
• Merge (default)
• Rebase
• Stash changes

PUSH (⌘⇧K)
─────────────────────────────────────────────
⌘⇧K → Push Commits

Shows:
• Commits to push
• Target branch
• Force push option (use carefully!)

BRANCHES
─────────────────────────────────────────────
Bottom-right corner → Branch name → Click

Options:
• New Branch
• Checkout existing
• Compare branches
• Merge
• Rebase
• Delete

Create branch workflow:
1. Click branch name
2. New Branch
3. Name it: feature/new-feature
4. Checkout
5. Make changes
6. Commit
7. Push
8. Create Pull Request (via GitHub/GitLab)

MERGE CONFLICTS
─────────────────────────────────────────────
When conflict occurs, IntelliJ shows:

┌────────────────────────────────────────┐
│ Merge Conflicts                        │
├────────────────────────────────────────┤
│ ⚠ UserService.java                     │
│ ⚠ UserController.java                  │
└────────────────────────────────────────┘

Click file → Opens 3-way merge:
┌─────────┬─────────┬─────────┐
│  Yours  │ Result  │ Theirs  │
├─────────┼─────────┼─────────┤
│ code A  │    ?    │ code B  │
└─────────┴─────────┴─────────┘

Actions:
• Accept yours
• Accept theirs
• Merge manually

STASH CHANGES
─────────────────────────────────────────────
VCS → Git → Stash Changes

Use when:
• Need to pull but have uncommitted work
• Want to switch branches
• Need to save work-in-progress

Unstash:
VCS → Git → Unstash Changes

# ═══════════════════════════════════════════
# GITHUB/GITLAB INTEGRATION
# ═══════════════════════════════════════════

Settings → Version Control → GitHub
→ Add account

Features:
• Clone repositories
• Create Pull Requests
• Review PRs inline
• See PR comments
• Manage issues

Create PR:
VCS → Git → Create Pull Request
→ Fill details
→ Create

Review PR:
View → Tool Windows → Pull Requests
→ Select PR
→ Review changes
→ Comment
→ Approve/Request changes

# ═══════════════════════════════════════════
# GIT HISTORY & BLAME
# ═══════════════════════════════════════════

VIEW FILE HISTORY
─────────────────────────────────────────────
Right-click file → Git → Show History

Shows:
• All commits affecting file
• Who changed what
• When
• Commit messages

Click commit → See full diff

GIT BLAME (ANNOTATE)
─────────────────────────────────────────────
Right-click gutter → Annotate with Git Blame

Shows for each line:
• Who wrote it
• When
• Commit message

Hover → Full commit details

Great for:
• "Who wrote this code?"
• "When was this added?"
• "Why was this changed?"

# ═══════════════════════════════════════════
# ADVANCED GIT FEATURES
# ═══════════════════════════════════════════

CHERRY-PICK
─────────────────────────────────────────────
Git Log → Right-click commit → Cherry-Pick

Applies specific commit to current branch

REVERT COMMIT
─────────────────────────────────────────────
Git Log → Right-click commit → Revert Commit

Creates new commit that undoes changes

RESET HEAD
─────────────────────────────────────────────
Git → Reset HEAD

Options:
• Soft (keeps changes)
• Mixed (unstages)
• Hard (discards everything) ⚠️

INTERACTIVE REBASE
─────────────────────────────────────────────
Git Log → Right-click → Rebase from Here

Can:
• Reorder commits
• Squash commits
• Edit commit messages
• Drop commits

PARTIAL COMMITS
─────────────────────────────────────────────
In commit dialog:
• Select specific lines to commit
• Commit only part of file changes

Great for:
• Separating concerns
• Atomic commits
```

---

<div align="center">

## 🔧 Configuration & Settings

_Customize your IDE for maximum productivity_ ⚙️

</div>

### Essential Settings ⚙️

```bash
# ═══════════════════════════════════════════
# ACCESSING SETTINGS
# ═══════════════════════════════════════════

macOS: ⌘, (Command + Comma)
Windows/Linux: Ctrl+Alt+S

Quick search in settings: Start typing!

# ═══════════════════════════════════════════
# 1️⃣ APPEARANCE & BEHAVIOR
# ═══════════════════════════════════════════

Settings → Appearance & Behavior → Appearance

✅ Theme
   • Darcula (Dark) - Most popular 🌙
   • IntelliJ Light
   • High Contrast
   • Custom themes via plugins

✅ Use custom font
   • JetBrains Mono (recommended)
   • Size: 13-14

✅ Antialiasing
   • Subpixel (best on LCD)
   • Grayscale (best on retina)

✅ Tool window font
   • Smaller than editor (11-12)

✅ Enable animations
   • Makes UI smoother

✅ Show tool window bars
   • Always show

✅ Smooth scrolling
   • Enable for better experience

# ═══════════════════════════════════════════
# 2️⃣ EDITOR SETTINGS
# ═══════════════════════════════════════════

Settings → Editor → General

ESSENTIAL TWEAKS:

☑ Change font size with Ctrl+Mouse Wheel
   • Zoom in/out easily

☑ Show quick documentation on mouse move
   • Delay: 500ms

☑ Show parameter hints
   • For methods with multiple parameters

☑ Show hints for
   • Method separators ✅
   • Chain calls ✅
   • Parameter names ✅

Settings → Editor → Font

╔════════════════════════════════════════╗
║ RECOMMENDED EDITOR FONT SETTINGS       ║
╠════════════════════════════════════════╣
║ Font: JetBrains Mono                   ║
║ Size: 14                               ║
║ Line spacing: 1.2                      ║
║ ☑ Enable ligatures                     ║
║ Secondary font: Fira Code              ║
╚════════════════════════════════════════╝

Settings → Editor → Code Style

✅ Hard wrap at: 120 columns
✅ Visual guides: 80, 120
✅ Detect and use existing file indents
✅ Use tab character: ☐ (use spaces)
✅ Tab size: 4 (Java) or 2 (JS/TS)
✅ Indent: Same as tab size

Settings → Editor → General → Auto Import

✅ Add unambiguous imports on the fly
✅ Optimize imports on the fly (Java)
✅ Show import popup (when multiple options)

Settings → Editor → General → Appearance

✅ Show line numbers
✅ Show method separators
✅ Show whitespaces
   • Leading ✅
   • Inner ☐
   • Trailing ✅

✅ Show indent guides
✅ Show breadcrumbs
✅ Caret blinking (period: 500ms)

Settings → Editor → General → Code Completion

✅ Match case: First letter only
✅ Auto-display in (ms): 1000
✅ Insert selected variant by typing: . ( = [
✅ Show suggestions as you type
✅ Sort suggestions by statistics

✅ Parameter hints:
   • Show parameter hints ✅
   • Show hints on mouse hover ✅

Settings → Editor → General → Code Folding

Fold by default:
☐ Imports (don't fold, you need to see them)
☐ One-line methods
☑ File header
☑ Method bodies (in interfaces)
☑ Generic constructor/method parameters
☑ JavaDoc comments (can fold if verbose)

Settings → Editor → Inspections

✅ Profile: Default (IDE)

Adjust severity:
• Typo: Warning (not Error)
• Unused declaration: Warning
• Missing documentation: Weak Warning

# ═══════════════════════════════════════════
# 3️⃣ KEYMAP
# ═══════════════════════════════════════════

Settings → Keymap

Schemes:
• macOS (default on Mac)
• Windows (default on Windows)
• Emacs, Vim (if you prefer)
• VS Code (familiar for VS Code users)
• Sublime Text

Customize shortcuts:
1. Search for action
2. Right-click → Add Keyboard Shortcut
3. Press keys
4. OK

Conflicts are highlighted! ⚠️

# ═══════════════════════════════════════════
# 4️⃣ PLUGINS
# ═══════════════════════════════════════════

Settings → Plugins

Marketplace:
• Browse and install plugins
• Update plugins
• Manage installed

Installed:
• Disable unused plugins (improves performance!)

# ═══════════════════════════════════════════
# 5️⃣ BUILD, EXECUTION, DEPLOYMENT
# ═══════════════════════════════════════════

Settings → Build, Execution, Deployment → Compiler

✅ Build project automatically
✅ Compile independent modules in parallel
✅ Heap size: 2048 MB (for large projects)

Settings → Build, Execution, Deployment → Build Tools

Maven:
• JDK for importer: Project JDK
• Maven home directory: Bundled (recommended)
• User settings file: ~/.m2/settings.xml
• Thread count: 4-8 (for parallel builds)

Gradle:
• Use Gradle from: 'gradle-wrapper.properties'
• Build and run using: Gradle (faster)
• Run tests using: Gradle

# ═══════════════════════════════════════════
# 6️⃣ VERSION CONTROL
# ═══════════════════════════════════════════

Settings → Version Control → Git

✅ Path to Git executable: /usr/bin/git
✅ SSH executable: Native
✅ Commit message:
   • Right margin (columns): 72
   • Wrap when typing reaches right margin ✅

✅ Annotate:
   • Show author/date on gutter click

Settings → Version Control → Commit

☑ Use non-modal commit interface
☑ Show unversioned files
☑ Highlight modified files in Project view
☑ Analyze code (before commit)
☑ Check TODO (before commit)
☑ Reformat code (before commit)
☑ Optimize imports (before commit)
☐ Perform code cleanup (optional)

# ═══════════════════════════════════════════
# 7️⃣ TOOLS
# ═══════════════════════════════════════════

Settings → Tools → Terminal

✅ Shell path: /bin/zsh (or /bin/bash)
✅ Tab name: Local
✅ Close session when it ends
✅ Mouse reporting: Enable

Settings → Tools → Web Browsers

✅ Default browser: Chrome/Firefox
✅ Show browser popup in the editor

Settings → Tools → File Watchers

Add watchers for:
• Prettier (auto-format)
• ESLint (auto-fix)
• TypeScript compiler

# ═══════════════════════════════════════════
# 8️⃣ LANGUAGE-SPECIFIC SETTINGS
# ═══════════════════════════════════════════

JAVA:
Settings → Editor → Code Style → Java

• Imports:
  - Class count to use import with '*': 999
  - Names count to use static import with '*': 999
  (Prevents wildcard imports)

• Tabs and Indents:
  - Tab size: 4
  - Indent: 4
  - Continuation indent: 8

JAVASCRIPT/TYPESCRIPT:
Settings → Languages & Frameworks → JavaScript

• JavaScript language version: ECMAScript 6+
• Code Quality Tools:
  - ESLint: ✅
  - Prettier: ✅

PYTHON:
Settings → Project → Python Interpreter

• Select interpreter
• Install packages:
  - pylint
  - black
  - mypy

# ═══════════════════════════════════════════
# 9️⃣ PRODUCTIVITY SETTINGS
# ═══════════════════════════════════════════

Settings → Advanced Settings

✅ IDE Features:
   • Maximum number of recent files: 50
   • Maximum number of open editors: 20

✅ User Interface:
   • Show main menu in a separate toolbar (macOS) ✅
   • Show navigation bar ☐ (use ⇧⇧ instead)

✅ Version Control:
   • Annotate inline (shows author next to code)

# ═══════════════════════════════════════════
# 🔟 LIVE TEMPLATES
# ═══════════════════════════════════════════

Settings → Editor → Live Templates

Create custom templates!

Example: "test" template (Java)
───────────────────────────────────────────
Abbreviation: test

Template text:
@Test
public void test$NAME$() {
    $END$
}

Variables:
• $NAME$ → capitalize(camelCase(fileNameWithoutExtension()))
• $END$ → cursor position

Context: Java → Declaration

Usage:
Type: test<Tab>
Result: Test method with cursor at body

Example: "cl" template (JavaScript)
───────────────────────────────────────────
Abbreviation: cl

Template text:
console.log($EXPR$);$END$

Variables:
• $EXPR$ → clipboard()

Usage:
Type: cl<Tab>
Result: console.log(); with cursor inside

# ═══════════════════════════════════════════
# SYNC SETTINGS ACROSS MACHINES
# ═══════════════════════════════════════════

File → Manage IDE Settings → Settings Sync

Options:
1. Sync with JetBrains Account (recommended)
   • Settings stored on JetBrains servers
   • Access from any machine

2. Sync with Settings Repository
   • Store in Git repository
   • Full version control

Syncs:
• Keymap
• Code style
• Live templates
• Plugins list
• UI settings
• Inspection profiles

# ═══════════════════════════════════════════
# EXPORT/IMPORT SETTINGS
# ═══════════════════════════════════════════

File → Manage IDE Settings → Export Settings

Exports .zip with all settings

File → Manage IDE Settings → Import Settings

Imports from .zip

Great for:
• Team consistency
• Backup
• New machine setup
```

---

### Recommended Settings for Performance 🚀

```bash
# ═══════════════════════════════════════════
# OPTIMIZE FOR SPEED
# ═══════════════════════════════════════════

1. INCREASE MEMORY
───────────────────────────────────────────
Help → Edit Custom VM Options

Add or modify:
-Xms1024m              # Initial heap
-Xmx4096m              # Maximum heap (4GB)
-XX:ReservedCodeCacheSize=512m
-XX:+UseG1GC           # Better garbage collector
-XX:SoftRefLRUPolicyMSPerMB=50
-XX:+HeapDumpOnOutOfMemoryError
-Dsun.io.useCanonCaches=false
-Djava.net.preferIPv4Stack=true
-Djdk.http.auth.tunneling.disabledSchemes=""

Recommended by project size:
• Small projects: -Xmx2048m (2GB)
• Medium projects: -Xmx4096m (4GB)
• Large projects: -Xmx8192m (8GB)

Restart IDE after changing!

2. DISABLE UNUSED PLUGINS
───────────────────────────────────────────
Settings → Plugins → Installed

Disable plugins you don't use:
• Android (if not doing Android dev)
• Kubernetes (if not using K8s)
• Markdown (if not editing MD files)
• CVS, Mercurial (if only using Git)
• Jupyter (if not using notebooks)
• Docker (if not using Docker)

Each disabled plugin = faster startup! 🚀

3. EXCLUDE DIRECTORIES
───────────────────────────────────────────
Right-click folder → Mark Directory as → Excluded

Exclude:
• node_modules (huge!)
• .git (don't index)
• build/ dist/ target/ (build outputs)
• venv/ .venv/ (Python virtual envs)
• .idea/ (project files)
• Caches, logs

Speeds up indexing significantly!

4. POWER SAVE MODE
───────────────────────────────────────────
File → Power Save Mode

When enabled:
• No code inspection
• No auto-completion
• No auto-import
• Minimal features

Use when:
• Low battery
• Viewing code only (not editing)
• Maximum battery life needed

Toggle: ⌃⌘P

5. DISABLE CODE INSPECTIONS (SELECTIVELY)
───────────────────────────────────────────
Settings → Editor → Inspections

Disable heavy inspections:
☐ JavaScript and TypeScript → General → JSDoc comments
☐ Spelling (if too noisy)

Keep important ones:
✅ Probable bugs
✅ Code quality
✅ Security

6. OPTIMIZE INDEXING
───────────────────────────────────────────
Settings → Advanced Settings → IDE Features

✅ Maximum heap size to trigger indexing GC: 2048
✅ Pause indexing when IDE is not in focus

Help → Diagnostic Tools → Optimize indexing

Let indexing complete once! Don't interrupt.

7. USE LOCAL HISTORY WISELY
───────────────────────────────────────────
Settings → System Settings → Local History

Days to keep: 5 (default: infinite)

Reduces disk usage.

8. APPEARANCE OPTIMIZATION
───────────────────────────────────────────
Settings → Appearance & Behavior → Appearance

☐ Smooth scrolling (disable for speed)
☐ Animate windows (disable for speed)
✅ Antialiasing: Greyscale (faster than subpixel)

9. COMPILER OPTIMIZATION
───────────────────────────────────────────
Settings → Build, Execution, Deployment → Compiler

✅ Build project automatically (in small projects)
☐ Build project automatically (in large projects)
✅ Compile independent modules in parallel
✅ User-local build process heap size: 2048

10. DISABLE UNNECESSARY FEATURES
───────────────────────────────────────────
Settings → Editor → General → Code Completion

☐ Show suggestions as you type (if too slow)

Settings → Editor → General → Breadcrumbs

☐ Show breadcrumbs (saves resources)

Settings → Editor → Inlay Hints

Disable hints you don't need:
☐ Parameter names
☐ Type hints (in some languages)

# ═══════════════════════════════════════════
# MONITORING PERFORMANCE
# ═══════════════════════════════════════════

Help → Diagnostic Tools → Activity Monitor

Shows:
• CPU usage
• Memory usage
• Active threads
• Slow operations

Identify bottlenecks!

Help → Diagnostic Tools → Analyze Plugin Startup Performance

Shows which plugins slow down startup.

Help → Edit Custom VM Options → Add:
-Didea.log.slow.operations=true

Logs slow operations to idea.log

Check logs:
Help → Show Log in Finder/Explorer

# ═══════════════════════════════════════════
# TROUBLESHOOTING SLOW IDE
# ═══════════════════════════════════════════

1. File → Invalidate Caches → Invalidate and Restart
   Fixes corrupted caches

2. Delete .idea folder and reimport project
   Fresh start

3. Upgrade to latest version
   Performance improvements in updates

4. Check antivirus exclusions
   Exclude IntelliJ directories

5. Use SSD (not HDD)
   Major performance difference!

6. Close unnecessary projects
   Only keep current project open

7. Reduce number of open files
   Close tabs you're not using

# ═══════════════════════════════════════════
# BENCHMARK RESULTS
# ═══════════════════════════════════════════

Example improvements:

BEFORE:
• Startup time: 25 seconds
• Indexing time: 5 minutes
• Code completion: 500ms
• Find usages: 10 seconds

AFTER (with optimizations):
• Startup time: 8 seconds ⚡ (68% faster!)
• Indexing time: 2 minutes ⚡ (60% faster!)
• Code completion: 50ms ⚡ (90% faster!)
• Find usages: 2 seconds ⚡ (80% faster!)
```

---

### Keymap Customization

```bash
# ═══════════════════════════════════════════
# CREATING PERFECT KEYMAP
# ═══════════════════════════════════════════

Settings → Keymap → Right-click scheme → Duplicate
Name it: "My Custom Keymap"

# ═══════════════════════════════════════════
# RECOMMENDED CUSTOM SHORTCUTS
# ═══════════════════════════════════════════

1. QUICK ACTIONS
───────────────────────────────────────────
Action: "Recent Locations"
Default: ⌘⇧E
Add: ⌘P (like VS Code Command Palette)

Action: "Search Everywhere"
Default: ⇧⇧
Add: ⌘P (if you prefer)

Action: "Run Anything"
Default: ⌃⌃
Add: ⌘⇧P

2. TERMINAL
───────────────────────────────────────────
Action: "Terminal"
Default: ⌥F12
Add: `⌃` ` (like VS Code)

3. NAVIGATION
───────────────────────────────────────────
Action: "Back"
Default: ⌘[
Add: ⌘← (intuitive)

Action: "Forward"
Default: ⌘]
Add: ⌘→ (intuitive)

4. DEBUGGING
───────────────────────────────────────────
Action: "Debug"
Default: ⌃D
Add: F5 (like VS Code)

Action: "Toggle Breakpoint"
Default: ⌘F8
Add: F9

5. CODE ACTIONS
───────────────────────────────────────────
Action: "Show Context Actions"
Default: ⌥↩
Add: ⌘. (like VS Code)

Action: "Reformat Code"
Default: ⌘⌥L
Add: ⌘⇧F (like VS Code)

# ═══════════════════════════════════════════
# IMPORTING KEYMAPS FROM OTHER EDITORS
# ═══════════════════════════════════════════

VS CODE USERS:
───────────────────────────────────────────
Settings → Keymap → Add Keymap → VS Code (macOS/Windows)

Almost all VS Code shortcuts work! 🎉

VIM USERS:
───────────────────────────────────────────
Install plugin: IdeaVim
Settings → Plugins → Marketplace → "IdeaVim"

Creates ~/.ideavimrc file:
set number
set relativenumber
set incsearch
set hlsearch
set smartcase
set ignorecase

nnoremap <leader>f :action GotoFile<CR>
nnoremap <leader>r :action RecentFiles<CR>
nnoremap <leader>b :action ToggleLineBreakpoint<CR>

EMACS USERS:
───────────────────────────────────────────
Settings → Keymap → Emacs

Familiar Emacs shortcuts!

SUBLIME TEXT USERS:
───────────────────────────────────────────
Settings → Keymap → Sublime Text

# ═══════════════════════════════════════════
# EXPORT YOUR KEYMAP
# ═══════════════════════════════════════════

Settings → Keymap → ⚙️ → Export

Share with team for consistency!
```

---

<div align="center">

## 🎨 Themes & Appearance

_Make your IDE beautiful and comfortable_ 🌈

</div>

### Popular Themes 🌈

```bash
# ═══════════════════════════════════════════
# BUILT-IN THEMES
# ═══════════════════════════════════════════

Settings → Appearance & Behavior → Appearance → Theme

1. Darcula ⚫ (Default Dark)
   • Easy on eyes
   • Great syntax highlighting
   • Most popular
   • Professional look

2. IntelliJ Light ⚪ (Default Light)
   • Classic look
   • High contrast
   • Good for bright environments

3. High Contrast 🔲
   • Maximum contrast
   • Accessibility
   • Visual impairment friendly

4. New UI (Light/Dark) 🆕
   • Modern redesign
   • Cleaner icons
   • Better spacing
   • Available in 2023.3+

# ═══════════════════════════════════════════
# PLUGIN THEMES (INSTALL VIA PLUGINS)
# ═══════════════════════════════════════════

Settings → Plugins → Marketplace → Search "theme"

═══════════════════════════════════════════════════════════

1. MATERIAL THEME UI ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Most popular theme plugin! 50M+ downloads

Includes:
• Material Oceanic
• Material Darker
• Material Lighter
• Material Palenight
• Material DeepOcean
• Monokai Pro
• Arc Dark
• Atom One Dark
• Dracula
• GitHub
• Light Owl
• Solarized Dark/Light

Features:
✓ Customizable colors
✓ Multiple accent colors
✓ Icon themes included
✓ Tab height customization
✓ Compact sidebar
✓ Custom fonts
✓ Project frame colors

Installation:
Settings → Plugins → Material Theme UI → Install

Activation:
Settings → Appearance → Material Theme

Configuration:
Tools → Material Theme → Material Theme Settings

Popular presets:
• Material Oceanic (blue/teal) 🌊
• Material Palenight (purple) 💜
• Monokai Pro (orange/pink) 🧡
• Dracula (purple/pink) 🧛
• GitHub (clean white) ☁️

2. ONE DARK THEME ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Atom's iconic One Dark theme

Colors:
• Background: Dark gray
• Accent: Blue
• Keywords: Purple
• Strings: Green
• Functions: Blue

Great for:
• Long coding sessions
• Dark environment
• VS Code users (familiar)

Installation:
Settings → Plugins → "One Dark theme" → Install

3. DRACULA THEME 🧛 ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Popular across all editors

Colors:
• Background: Dark purple-gray
• Accent: Pink/Purple
• Keywords: Pink
• Strings: Yellow
• Comments: Gray

Great for:
• Night coding
• Reduced eye strain
• Popular aesthetic

Installation:
Settings → Plugins → "Dracula Theme" → Install

4. NORD THEME ❄️ ⭐⭐⭐⭐
───────────────────────────────────────────
Arctic-inspired color palette

Colors:
• Background: Dark blue-gray
• Accent: Frost blue/teal
• Keywords: Blue
• Strings: Green
• Calm and focused

Great for:
• Minimalist aesthetic
• Focus and concentration
• Cool color lovers

Installation:
Settings → Plugins → "Nord" → Install

5. SOLARIZED THEME ☀️ ⭐⭐⭐⭐
───────────────────────────────────────────
Scientifically designed for readability

Variants:
• Solarized Dark (most popular)
• Solarized Light

Colors:
• Carefully chosen for contrast
• Easy on eyes
• Reduces eye strain

Installation:
Settings → Plugins → "Solarized" → Install

6. GRUVBOX THEME ⭐⭐⭐⭐
───────────────────────────────────────────
Retro groove colors

Colors:
• Warm, earthy tones
• Brown/orange/yellow base
• High contrast
• Vintage feel

Installation:
Settings → Plugins → "Gruvbox Theme" → Install

7. TOKYO NIGHT ⭐⭐⭐⭐
───────────────────────────────────────────
Modern, vibrant dark theme

Colors:
• Dark blue background
• Purple/pink accents
• Cyan highlights
• Trendy aesthetic

Installation:
Settings → Plugins → "Tokyo Night" → Install

8. MONOKAI PRO ⭐⭐⭐⭐
───────────────────────────────────────────
Modern take on classic Monokai

Variants:
• Classic
• Machine
• Octagon
• Ristretto
• Spectrum

Installation:
Settings → Plugins → "Monokai Pro" → Install

9. MATERIAL THEME DARK ⭐⭐⭐⭐
───────────────────────────────────────────
Google Material Design inspired

Colors:
• Modern and clean
• Blue/teal accents
• Professional look
• Popular for Android dev

10. COBALT 2 ⭐⭐⭐⭐
───────────────────────────────────────────
By Wes Bos

Colors:
• Dark blue background
• Bright accents
• High readability
• Popular with instructors

# ═══════════════════════════════════════════
# THEME CUSTOMIZATION
# ═══════════════════════════════════════════

Settings → Editor → Color Scheme

Customize any theme:
• Language syntax colors
• Background colors
• Error/warning colors
• Console colors
• Diff colors

Export custom theme:
Settings → Editor → Color Scheme → ⚙️ → Export

Share with team! 🎨

# ═══════════════════════════════════════════
# RECOMMENDED THEME COMBINATIONS
# ═══════════════════════════════════════════

FOR DARK ENVIRONMENT 🌙:
• Material Oceanic
• Dracula
• One Dark
• Nord

FOR BRIGHT ENVIRONMENT ☀️:
• IntelliJ Light
• Solarized Light
• Material Lighter
• GitHub

FOR LONG CODING SESSIONS 💻:
• Dracula (less eye strain)
• Nord (calming)
• Gruvbox (warm tones)

FOR MAXIMUM FOCUS 🎯:
• Monochrome themes
• Minimal accent colors
• Nord (distraction-free)

FOR PRESENTATIONS 🎤:
• High Contrast
• IntelliJ Light
• Clear, readable colors

# ═══════════════════════════════════════════
# FONT & THEME PAIRING
# ═══════════════════════════════════════════

Best combinations:

JetBrains Mono + Material Oceanic ⭐⭐⭐⭐⭐
→ Modern and professional

Fira Code + One Dark ⭐⭐⭐⭐⭐
→ Clean and readable

Cascadia Code + Dracula ⭐⭐⭐⭐⭐
→ Modern and vibrant

Source Code Pro + Solarized Dark ⭐⭐⭐⭐⭐
→ Classic and reliable

Hack + Gruvbox ⭐⭐⭐⭐
→ Retro and warm

# ═══════════════════════════════════════════
# THEME SWITCHING WORKFLOW
# ═══════════════════════════════════════════

Quick Actions (⌘⇧A):
Type: "Theme"
→ Select theme from list
→ Applied instantly!

No need to go through settings!

Create keybinding for quick switching:
Settings → Keymap → "Quick Switch Scheme"
Assign: ⌃⌘T

Now: ⌃⌘T → Choose Theme

# ═══════════════════════════════════════════
# SYNC THEME ACROSS JETBRAINS IDES
# ═══════════════════════════════════════════

All JetBrains IDEs share theme settings!

Install theme plugin in one IDE:
→ Available in ALL your JetBrains IDEs

Configure once, use everywhere! 🎉
```

---

### Icon Packs 🎨

```bash
# ═══════════════════════════════════════════
# ICON PACKS (MAKE FILES PRETTY)
# ═══════════════════════════════════════════

Settings → Plugins → Marketplace

1. MATERIAL THEME UI ICONS ⭐⭐⭐⭐⭐ (BEST!)
───────────────────────────────────────────
Included with Material Theme UI plugin

Features:
• 1000+ file type icons
• Folder icons
• Custom colors
• Arrow styles
• Tab height

Settings:
Tools → Material Theme → Material Icons Settings

Options:
• Monochrome icons
• Saturation level
• Icon size

2. ATOM MATERIAL ICONS ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Similar to VS Code icons

Features:
• Clean and modern
• All file types covered
• Folder themes
• Arrow styles

Installation:
Settings → Plugins → "Atom Material Icons" → Install

3. EXTRA ICONS ⭐⭐⭐⭐
───────────────────────────────────────────
Additional icons for files without default icons

Supports:
• .env files
• Docker files
• Config files
• Framework files

Installation:
Settings → Plugins → "Extra Icons" → Install

4. VSICONS ⭐⭐⭐⭐
───────────────────────────────────────────
VS Code icon theme port

Familiar for VS Code users!

Installation:
Settings → Plugins → "VSCode Icons" → Install

5. CATPPUCCIN ICONS ⭐⭐⭐⭐
───────────────────────────────────────────
Part of Catppuccin theme

Pastel-colored icons
Cute and modern

Installation:
Settings → Plugins → "Catppuccin Icons" → Install

# ═══════════════════════════════════════════
# CUSTOMIZING ICONS
# ═══════════════════════════════════════════

With Material Theme UI:

Tools → Material Theme → Material Icons Settings

╔════════════════════════════════════════╗
║   Material Icons Settings              ║
╠════════════════════════════════════════╣
║ ☑ Enable Material Icons               ║
║ ☑ Enable Folder Decorators            ║
║ ☑ Enable PSI Icons                    ║
║ ☑ Enable UI Icons                     ║
║ ☐ Monochrome Icons                    ║
║ Arrow Style: Material                  ║
║ Icon Opacity: 100%                     ║
║ Icon Saturation: 100%                  ║
╚════════════════════════════════════════╝

Folder Themes:
• Default
• Classic (IntelliJ style)
• None (no folder icons)

# ═══════════════════════════════════════════
# ICON PREVIEW
# ═══════════════════════════════════════════

Common file icons:

JavaScript: 📄 (yellow)
TypeScript: 📘 (blue)
Python: 🐍 (blue/yellow)
Java: ☕ (red)
HTML: 📝 (orange)
CSS: 🎨 (blue)
JSON: 📋 (green)
Markdown: 📑 (blue)
Docker: 🐳 (blue)
Git: 🔀 (orange)
React: ⚛️ (blue)
Vue: 💚 (green)
Angular: 🅰️ (red)
Node.js: 🟢 (green)

Much easier to find files! 🎯

# ═══════════════════════════════════════════
# PERFORMANCE IMPACT
# ═══════════════════════════════════════════

Icon plugins have minimal performance impact

Benefits outweigh costs:
• Faster file recognition ⚡
• Better visual organization 📁
• Professional appearance ✨

Recommendation: Use Material Theme UI Icons (best overall)
```

---

### Custom Fonts 🔤

```bash
# ═══════════════════════════════════════════
# RECOMMENDED CODING FONTS
# ═══════════════════════════════════════════

Settings → Editor → Font

╔════════════════════════════════════════╗
║     TOP 10 CODING FONTS                ║
╚════════════════════════════════════════╝

1. JETBRAINS MONO ⭐⭐⭐⭐⭐ (BEST!)
───────────────────────────────────────────
Designed BY JetBrains FOR programming

✓ Free and open source
✓ 140+ ligatures
✓ Perfect for code
✓ Excellent readability
✓ Optimized for long sessions
✓ Special programming characters
✓ Built-in IntelliJ!

Download: https://www.jetbrains.com/lp/mono/

Settings:
Font: JetBrains Mono
Size: 14
Line spacing: 1.2
☑ Enable ligatures

2. FIRA CODE ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Most popular ligature font

✓ Free and open source
✓ Amazing ligatures
✓ Clear and readable
✓ Great for arrows (→ ⇒ ≠ ≥)

Download: https://github.com/tonsky/FiraCode

Ligatures Examples:
!= → ≠
== → ≡
=> → ⇒
-> → →
<= → ≤
>= → ≥
=== → ≣

3. CASCADIA CODE ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Microsoft's modern font

✓ Free and open source
✓ Excellent ligatures
✓ Powerline symbols
✓ Cursor-friendly
✓ Modern design

Download: https://github.com/microsoft/cascadia-code

Variants:
• Cascadia Code (default)
• Cascadia Mono (no ligatures)
• Cascadia Code PL (Powerline)

4. SOURCE CODE PRO ⭐⭐⭐⭐
───────────────────────────────────────────
Adobe's monospaced font

✓ Free and open source
✓ Clean and professional
✓ No ligatures (if you prefer)
✓ Great readability
✓ Many weights

Download: https://github.com/adobe-fonts/source-code-pro

Best for:
• No-ligature preference
• Professional look
• Long documents

5. HACK ⭐⭐⭐⭐
───────────────────────────────────────────
Designed specifically for source code

✓ Free and open source
✓ Open Type features
✓ Easy on eyes
✓ Great for small sizes
✓ High legibility

Download: https://github.com/source-foundry/Hack

Best for:
• Small screen sizes
• Dense code
• Extended reading

6. VICTOR MONO ⭐⭐⭐⭐
───────────────────────────────────────────
Elegant programming font

✓ Free and open source
✓ Italic cursive style (unique!)
✓ Ligatures
✓ Stylish appearance

Download: https://rubjo.github.io/victor-mono/

Best for:
• Aesthetic preference
• Unique style
• Comments in cursive

7. INCONSOLATA ⭐⭐⭐⭐
───────────────────────────────────────────
Humanist monospace font

✓ Free and open source
✓ Clean design
✓ Google Fonts available
✓ Compact

Best for:
• Classic style
• Terminal use
• Small screens

8. IOSEVKA ⭐⭐⭐⭐
───────────────────────────────────────────
Highly customizable

✓ Free and open source
✓ Extremely narrow
✓ High information density
✓ Many variants

Download: https://github.com/be5invis/Iosevka

Best for:
• More code on screen
• Narrow displays
• Compact preference

9. MONOID ⭐⭐⭐⭐
───────────────────────────────────────────
Customizable and legible

✓ Free and open source
✓ Good for small sizes
✓ Clear characters
✓ Tight spacing option

Best for:
• Small font sizes
• High DPI displays

10. COMIC CODE ⭐⭐⭐⭐ (PAID)
───────────────────────────────────────────
Comic Sans for coding (seriously!)

✓ Surprisingly readable
✓ Ligatures
✓ Fun appearance
✓ Easy on eyes

Download: https://tosche.net/fonts/comic-code

Price: $19 (one-time)

Best for:
• Fun atmosphere
• Casual coding
• Reducing intimidation

# ═══════════════════════════════════════════
# FONT INSTALLATION
# ═══════════════════════════════════════════

macOS:
1. Download .ttf or .otf file
2. Double-click
3. Click "Install Font"
4. Restart IntelliJ
5. Settings → Editor → Font → Select font

Windows:
1. Download font file
2. Right-click → Install
3. Restart IntelliJ
4. Settings → Editor → Font → Select font

Linux:
1. Copy to ~/.fonts/
2. Run: fc-cache -f -v
3. Restart IntelliJ
4. Settings → Editor → Font → Select font

# ═══════════════════════════════════════════
# FONT CONFIGURATION
# ═══════════════════════════════════════════

Settings → Editor → Font

╔════════════════════════════════════════╗
║   RECOMMENDED SETTINGS                 ║
╠════════════════════════════════════════╣
║ Font: JetBrains Mono                   ║
║ Fallback font: JetBrains Mono          ║
║ Size: 14                               ║
║ Line spacing: 1.2                      ║
║ ☑ Enable ligatures                     ║
╚════════════════════════════════════════╝

Size recommendations:
• 13px: Small screens, more code visible
• 14px: Standard, most comfortable ⭐
• 15-16px: Larger screens, presentations
• 18px+: Accessibility, visual impairment

Line spacing:
• 1.0: Compact, dense code
• 1.2: Standard, recommended ⭐
• 1.4: Spacious, easier reading
• 1.6: Very spacious, presentations

# ═══════════════════════════════════════════
# LIGATURES SHOWCASE
# ═══════════════════════════════════════════

With ligatures (JetBrains Mono, Fira Code):

// Normal:
if (x != y && x >= 0) {
    const result = x => x * 2;
}

// With ligatures (displayed):
if (x ≠ y && x ≥ 0) {
    const result = x ⇒ x × 2;
}

Common ligatures:
!= → ≠
== → ≡
=== → ≣
!== → ≢
<= → ≤
>= → ≥
-> → →
=> → ⇒
:: → ∷
<> → ◇
|> → ▷
<| → ◁

# ═══════════════════════════════════════════
# FONT FOR SPECIFIC USES
# ═══════════════════════════════════════════

FOR GENERAL CODING:
• JetBrains Mono ⭐⭐⭐⭐⭐
• Fira Code ⭐⭐⭐⭐⭐
• Cascadia Code ⭐⭐⭐⭐⭐

FOR PRESENTATIONS/TEACHING:
• Larger size: 18-20px
• High contrast theme
• JetBrains Mono or Source Code Pro

FOR LONG CODING SESSIONS:
• JetBrains Mono ⭐
• Hack
• Victor Mono

FOR TERMINAL/CONSOLE:
• JetBrains Mono
• Cascadia Code PL (Powerline)
• Hack

FOR SMALL SCREENS:
• Hack
• Monoid
• Iosevka

# ═══════════════════════════════════════════
# MULTIPLE FONT CONFIGURATION
# ═══════════════════════════════════════════

Primary font: JetBrains Mono
Fallback font: Fira Code
Console font: JetBrains Mono

Settings → Editor → Font
→ Font: JetBrains Mono

Settings → Editor → Console Font
→ Use console font instead of default
→ Font: JetBrains Mono

Settings → Appearance & Behavior → Appearance
→ Use custom font: JetBrains Mono
→ Size: 13 (for UI elements)

# ═══════════════════════════════════════════
# ENABLE LIGATURES
# ═══════════════════════════════════════════

Settings → Editor → Font
☑ Enable ligatures

Font ligatures string (advanced):
'calt', 'liga', 'dlig', 'ss01', 'ss02', 'ss03'

Disable specific ligatures:
Settings → Editor → Font → Font ligatures
Remove unwanted ligature codes

Example: Disable -> ligature
Remove 'ss03' from ligatures string
```

---

<div align="center">

## 🔌 Must-Have Plugins

_Supercharge your IDE_ 🚀

</div>

### 1️⃣ Productivity Boosters

```bash
# ═══════════════════════════════════════════
# PRODUCTIVITY PLUGINS
# ═══════════════════════════════════════════

Settings → Plugins → Marketplace

═══════════════════════════════════════════════════════════

1. KEY PROMOTER X ⭐⭐⭐⭐⭐ (MUST HAVE!)
───────────────────────────────────────────
Learn shortcuts faster!

What it does:
• Shows popup when you use mouse for action
• Displays keyboard shortcut you should use
• Statistics on most-used actions
• Suggests creating shortcuts for unbound actions

Example:
You click: Run button with mouse
Popup shows: "Use ⌃R instead!"

Installation:
Settings → Plugins → "Key Promoter X" → Install

View statistics:
Help → Key Promoter X → Show Statistics

Shows:
• Actions you perform most
• How many times via mouse
• Available shortcuts

Over time, you'll use mouse less! 🎯

═══════════════════════════════════════════════════════════

2. RAINBOW BRACKETS ⭐⭐⭐⭐⭐ (MUST HAVE!)
───────────────────────────────────────────
Colorful bracket matching!

What it does:
• Colors matching brackets
• Easy to see code structure
• Navigate nested code
• Identify mismatched brackets

Visual:
if (condition) {
    for (item in list) {  ← Blue
        if (check) {      ← Green
            doSomething() ← Yellow
        }
    }
}

Installation:
Settings → Plugins → "Rainbow Brackets" → Install

Configuration:
Settings → Editor → Color Scheme → Rainbow Brackets

Customize:
• Colors
• Enable/disable for specific languages
• Opacity
• Bold/italic

Works with:
• Parentheses ()
• Brackets []
• Braces {}
• Angle brackets <>

═══════════════════════════════════════════════════════════

3. STRING MANIPULATION ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Swiss army knife for text!

What it does:
• Case conversion (camelCase, snake_case, etc.)
• Sort lines
• Filter lines
• Encode/decode (Base64, URL, etc.)
• Increment/decrement numbers
• Align text
• Escape/unescape strings

Usage:
1. Select text
2. Right-click → String Manipulation
3. Choose action

Actions available:

CASE CONVERSION:
─────────────────
• Switch case
• To SCREAMING_SNAKE_CASE
• To camelCase
• To PascalCase
• To snake_case
• To kebab-case
• To dot.case
• To UPPER CASE
• To lower case

Example:
my_variable_name
→ myVariableName (camelCase)
→ MyVariableName (PascalCase)
→ MY_VARIABLE_NAME (SCREAMING_SNAKE_CASE)
→ my-variable-name (kebab-case)

SORTING:
─────────────────
• Sort lines (A-Z)
• Sort lines (Z-A)
• Sort lines by length
• Shuffle lines
• Reverse lines

FILTERING:
─────────────────
• Remove empty lines
• Remove duplicate lines
• Keep only unique lines
• Grep (regex filter)

ENCODING:
─────────────────
• Encode Base64
• Decode Base64
• Encode URL
• Decode URL
• Encode HTML
• Decode HTML

INCREMENTING:
─────────────────
// Before:
item_1
item_1
item_1

// After (Increment duplicate numbers):
item_1
item_2
item_3

ALIGNMENT:
─────────────────
// Before:
const x = 1;
const longName = 2;
const y = 3;

// After (Align by =):
const x        = 1;
const longName = 2;
const y        = 3;

Installation:
Settings → Plugins → "String Manipulation" → Install

Keyboard shortcuts (default):
⌥M (Alt+M) → String Manipulation menu

═══════════════════════════════════════════════════════════

4. CODEGLANCE PRO ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Minimap like Sublime Text!

What it does:
• Shows code overview in scrollbar
• Quick navigation
• See file structure at glance
• Click to jump to location

Visual:
┌────────────────────────────┬──┐
│ public class User {        │▓▓│
│   private String name;     │▓▓│← Minimap
│   private int age;         │▓▓│
│                            │  │
│   public void setName() {  │▓▓│
│     this.name = name;      │▓▓│
│   }                        │▓▓│
│ }                          │▓▓│
└────────────────────────────┴──┘

Installation:
Settings → Plugins → "CodeGlance Pro" → Install

Configuration:
Settings → Editor → CodeGlance Pro

Options:
• Width: 100px (adjustable)
• Opacity: 50% (adjustable)
• Show on: Right side (default)
• Minimap on click (instead of scroll)

Disable for specific file types:
Settings → CodeGlance Pro → Disabled file types

═══════════════════════════════════════════════════════════

5. SAVE ACTIONS ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Auto-format on save!

What it does:
• Format code on save
• Optimize imports on save
• Remove trailing spaces
• Run inspections
• Organize code

Configuration:
Settings → Other Settings → Save Actions

Enable:
☑ Activate save actions on save
☑ Activate save actions on shortcut
☑ No action if compile errors

Actions:
☑ Optimize imports
☑ Reformat file
☑ Rearrange code
☑ Remove unused suppress warning annotation
☑ Remove unnecessary semicolons
☑ Remove unnecessary blank lines
☑ Remove explicit generic type for diamond
☑ Qualify field access with this
☑ Qualify method access with this

File inclusions:
.*\.java  (only Java files)
.*\.js    (JavaScript files)
.*\.ts    (TypeScript files)

Installation:
Settings → Plugins → "Save Actions" → Install

Similar to:
• Prettier (auto-format on save)
• ESLint (auto-fix)
• Black (Python auto-format)

═══════════════════════════════════════════════════════════

6. IDEOLOG ⭐⭐⭐⭐
───────────────────────────────────────────
Better log file viewer!

What it does:
• Syntax highlighting for logs
• Filter logs
• Jump to errors
• Fold log entries
• Custom patterns

Supports:
• Log4j
• Logback
• java.util.logging
• Custom formats

Features:
• Highlight ERROR, WARN, INFO, DEBUG
• Filter by level
• Hide/show log entries
• Jump to source (if file paths in logs)

Installation:
Settings → Plugins → "Ideolog" → Install

Usage:
Open .log file → Automatic highlighting!

Configuration:
Settings → Editor → Log Highlighting

Add custom patterns:
Pattern: ^\d{4}-\d{2}-\d{2} \d{2}:\d{2}:\d{2}
Format: {DATE} {TIME} {LEVEL} {MESSAGE}

═══════════════════════════════════════════════════════════

7. TABS TO SPACES ⭐⭐⭐⭐
───────────────────────────────────────────
Convert tabs to spaces (or vice versa)

What it does:
• Convert tabs to spaces on save
• Convert spaces to tabs
• Consistent indentation

Installation:
Settings → Plugins → "Tabs to Spaces" → Install

Usage:
Edit → Convert Indents → To Spaces
Edit → Convert Indents → To Tabs

Auto-convert:
Settings → Tabs to Spaces
☑ Run on save

═══════════════════════════════════════════════════════════

8. INDENT RAINBOW ⭐⭐⭐⭐
───────────────────────────────────────────
Colorful indentation guides!

What it does:
• Colors indentation levels
• Visual hierarchy
• Easy to see code structure

Visual:
│ def function():
│ │   if condition:
│ │ │   for item in list:
│ │ │ │   process(item)
Red Blue Green Yellow

Installation:
Settings → Plugins → "Indent Rainbow" → Install

Configuration:
Settings → Indent Rainbow

Customize:
• Colors
• Opacity
• Error highlighting

═══════════════════════════════════════════════════════════

9. PRESENTATION ASSISTANT ⭐⭐⭐⭐
───────────────────────────────────────────
Show shortcuts during presentations!

What it does:
• Displays shortcuts on screen
• Great for teaching
• Live coding demos
• Pair programming

Visual:
When you press ⌘⇧A:
┌──────────────────────────┐
│   ⌘⇧A                   │
│   Find Action            │
└──────────────────────────┘

Installation:
Settings → Plugins → "Presentation Assistant" → Install

Configuration:
Settings → Appearance → Presentation Assistant

Options:
• Font size: 24 (larger for presentations)
• Display duration: 2 seconds
• Position: Bottom center
• Show key combinations

Enable:
Tools → Presentation Assistant → Toggle

═══════════════════════════════════════════════════════════

10. CAMELCASE ⭐⭐⭐⭐
───────────────────────────────────────────
Switch between naming conventions!

What it does:
• Cycle through case styles
• Quick case conversion
• Keyboard shortcut

Usage:
1. Select text or put cursor on word
2. Press ⌥⇧U (or custom shortcut)
3. Cycles through cases

Example:
my_variable
→ myVariable (camelCase)
→ MyVariable (PascalCase)
→ MY_VARIABLE (SCREAMING_SNAKE_CASE)
→ my-variable (kebab-case)
→ my_variable (back to start)

Installation:
Settings → Plugins → "CamelCase" → Install

Default shortcut: ⌥⇧U

═══════════════════════════════════════════════════════════

11. GREP CONSOLE ⭐⭐⭐⭐
───────────────────────────────────────────
Filter and highlight console output!

What it does:
• Filter console by regex
• Highlight patterns
• Fold console sections
• Tail mode (auto-scroll)

Features:
• Highlight ERROR in red
• Highlight WARN in yellow
• Hide DEBUG logs
• Filter by package name

Installation:
Settings → Plugins → "Grep Console" → Install

Usage:
Run app → Console toolbar → Grep options

Configuration:
Settings → Editor → Grep Console

Add patterns:
• Pattern: ERROR
• Color: Red
• Action: Highlight

═══════════════════════════════════════════════════════════

12. MULTIRUN ⭐⭐⭐⭐
───────────────────────────────────────────
Run multiple configurations at once!

What it does:
• Run multiple services
• Start frontend + backend together
• Microservices development
• Parallel execution

Setup:
1. Create Multirun configuration
2. Add existing run configurations
3. Run all at once

Example:
Multirun: "Full Stack"
├─ Backend API (Spring Boot)
├─ Frontend Dev Server (npm start)
└─ Database (Docker)

One click → Everything starts! 🚀

Installation:
Settings → Plugins → "Multirun" → Install

Usage:
Run → Edit Configurations → + → Multirun
Add configurations → Run

═══════════════════════════════════════════════════════════

13. QUICK FILE PREVIEW ⭐⭐⭐⭐
───────────────────────────────────────────
Preview files without opening!

What it does:
• Quick peek at files
• Don't clutter tabs
• Fast navigation

Usage:
Select file in Project view
→ Press Space
→ Preview opens
→ Press Space again to close

Installation:
Settings → Plugins → "Quick File Preview" → Install

═══════════════════════════════════════════════════════════

14. SHIFTER ⭐⭐⭐⭐
───────────────────────────────────────────
Shift values up/down!

What it does:
• Increment/decrement numbers
• Toggle booleans
• Cycle through options
• Smart value shifting

Examples:
true → false → true
0 → 1 → 2 → 3
Monday → Tuesday → Wednesday
red → green → blue

Usage:
1. Cursor on value
2. ⌃⌥↑ to shift up
3. ⌃⌥↓ to shift down

Installation:
Settings → Plugins → "Shifter" → Install

Custom dictionaries:
Settings → Shifter

Add your own cycles:
dev → staging → production
small → medium → large
```

---

### 2️⃣ Git & Version Control

```bash
# ═══════════════════════════════════════════
# GIT PLUGINS
# ═══════════════════════════════════════════

═══════════════════════════════════════════════════════════

1. GITTOOLBOX ⭐⭐⭐⭐⭐ (MUST HAVE!)
───────────────────────────────────────────
Enhanced Git integration!

What it does:
• Inline Git blame annotations
• Status display in Project view
• Auto-fetch
• Behind/ahead tracker
• Commit message completion

Features:

INLINE BLAME:
─────────────────────────────────────────────
Shows author and date inline:

public class User {  // John Doe, 2 days ago
    private String name;  // Jane Smith, 1 month ago

    public void save() {  // John Doe, 2 days ago
        repository.save(this);
    }
}

PROJECT VIEW STATUS:
─────────────────────────────────────────────
Shows Git status next to files:

📁 src/
  📁 main/
    📁 java/
      📄 User.java ← Modified
      📄 UserService.java ← Ahead 2 commits

AUTO-FETCH:
─────────────────────────────────────────────
Fetches from remote automatically:
• Every 15 minutes (configurable)
• Shows if you're behind
• No need to manually fetch

AHEAD/BEHIND TRACKER:
─────────────────────────────────────────────
Status bar shows:
↓ 3 ↑ 2
• 3 commits behind remote
• 2 commits ahead of remote

Installation:
Settings → Plugins → "GitToolBox" → Install

Configuration:
Settings → Other Settings → GitToolBox Global

Enable:
☑ Inline blame
☑ Status display
☑ Auto fetch
☑ Behind tracker
☑ Show project view decoration

Customization:
• Blame format: ${author}, ${date}
• Fetch interval: 15 minutes
• Status colors

═══════════════════════════════════════════════════════════

2. GIT FLOW INTEGRATION ⭐⭐⭐⭐
───────────────────────────────────────────
Git Flow workflow support!

What it does:
• Initialize Git Flow
• Create feature branches
• Create release branches
• Create hotfix branches
• Finish branches (merge + delete)

Git Flow branches:
• main (production)
• develop (development)
• feature/* (new features)
• release/* (release prep)
• hotfix/* (urgent fixes)

Usage:

INITIALIZE GIT FLOW:
─────────────────────────────────────────────
VCS → Git → Git Flow → Init Repo

Sets up:
• Production branch: main
• Development branch: develop

START FEATURE:
─────────────────────────────────────────────
VCS → Git → Git Flow → Start Feature
→ Name: user-authentication
→ Creates: feature/user-authentication
→ Checks out branch

Develop feature...

FINISH FEATURE:
─────────────────────────────────────────────
VCS → Git → Git Flow → Finish Feature
→ Merges to develop
→ Deletes feature branch
→ Checks out develop

START RELEASE:
─────────────────────────────────────────────
VCS → Git → Git Flow → Start Release
→ Version: 1.0.0
→ Creates: release/1.0.0

Prepare release (fix bugs, update version)...

FINISH RELEASE:
─────────────────────────────────────────────
VCS → Git → Git Flow → Finish Release
→ Merges to main
→ Creates tag: v1.0.0
→ Merges back to develop
→ Deletes release branch

START HOTFIX:
─────────────────────────────────────────────
VCS → Git → Git Flow → Start Hotfix
→ Version: 1.0.1
→ Creates: hotfix/1.0.1 (from main)

Fix critical bug...

FINISH HOTFIX:
─────────────────────────────────────────────
VCS → Git → Git Flow → Finish Hotfix
→ Merges to main
→ Creates tag: v1.0.1
→ Merges back to develop
→ Deletes hotfix branch

Installation:
Settings → Plugins → "Git Flow Integration" → Install

═══════════════════════════════════════════════════════════

3. CONVENTIONAL COMMIT ⭐⭐⭐⭐
───────────────────────────────────────────
Structured commit messages!

What it does:
• Template for commit messages
• Follows Conventional Commits spec
• Auto-generate changelogs
• Semantic versioning

Format:
<type>(<scope>): <subject>

<body>

<footer>

Types:
• feat: New feature
• fix: Bug fix
• docs: Documentation
• style: Formatting
• refactor: Code refactoring
• test: Tests
• chore: Maintenance

Examples:
feat(auth): add JWT authentication

Implement JWT token generation and validation
for user authentication.

BREAKING CHANGE: Changes authentication API

fix(api): resolve null pointer exception in getUserById

Add null check before accessing user object

docs(readme): update installation instructions

Usage:
⌘K (Commit) → Commit Message Template
→ Fill in type, scope, subject
→ Commit

Installation:
Settings → Plugins → "Conventional Commit" → Install

Configuration:
Settings → Other Settings → Conventional Commit

Templates:
• feat
• fix
• docs
• style
• refactor
• perf
• test
• build
• ci
• chore
• revert

═══════════════════════════════════════════════════════════

4. GIT COMMIT TEMPLATE ⭐⭐⭐⭐
───────────────────────────────────────────
Custom commit message templates!

What it does:
• Load commit templates
• Consistent commit messages
• Team standards

Setup:
1. Create template file: .gitmessage

# .gitmessage
# Type: (feat|fix|docs|style|refactor|test|chore)
# Scope: (optional)
# Subject: (max 50 chars)
#
# Body: (optional, wrap at 72 chars)
#
# Footer: (optional)
# Breaking changes, issue references

2. Configure Git:
git config commit.template .gitmessage

3. IntelliJ loads template on commit!

Installation:
Settings → Plugins → "Git Commit Template" → Install

═══════════════════════════════════════════════════════════

5. GITHUB ACTIONS MANAGER ⭐⭐⭐⭐
───────────────────────────────────────────
Manage GitHub Actions from IDE!

What it does:
• View workflow runs
• See action logs
• Trigger workflows
• View status checks

Features:
• Tool window for Actions
• Real-time status updates
• Logs viewer
• Re-run failed workflows

Installation:
Settings → Plugins → "GitHub Actions Manager" → Install

Usage:
View → Tool Windows → GitHub Actions
→ See all workflows
→ Click to view logs

═══════════════════════════════════════════════════════════

6. .IGNORE ⭐⭐⭐⭐⭐
───────────────────────────────────────────
.gitignore file support!

What it does:
• Syntax highlighting for .gitignore
• Templates for various tools
• Auto-completion
• Validation

Features:

TEMPLATES:
─────────────────────────────────────────────
Right-click project → New → .ignore File → .gitignore

Choose template:
• Java
• Node.js
• Python
• Go
• Rust
• Android
• iOS
• etc.

Generated .gitignore has common patterns!

SYNTAX HIGHLIGHTING:
─────────────────────────────────────────────
# Comments in green
*.class   # Patterns in blue
!important.class  # Negations in red

AUTO-COMPLETION:
─────────────────────────────────────────────
Type: node
→ Suggests: node_modules/

Type: *.
→ Suggests: *.class, *.log, etc.

PREVIEW:
─────────────────────────────────────────────
See which files will be ignored

Installation:
Settings → Plugins → ".ignore" → Install

Supports:
• .gitignore
• .dockerignore
• .npmignore
• .eslintignore
• .prettierignore
```

---

### 3️⃣ Code Quality

```bash
# ═══════════════════════════════════════════
# CODE QUALITY PLUGINS
# ═══════════════════════════════════════════

═══════════════════════════════════════════════════════════

1. SONARLINT ⭐⭐⭐⭐⭐ (MUST HAVE!)
───────────────────────────────────────────
On-the-fly code analysis!

What it does:
• Detects bugs
• Security vulnerabilities
• Code smells
• Best practice violations
• Works like spell checker for code

Supports:
• Java
• JavaScript/TypeScript
• Python
• PHP
• HTML
• C/C++
• And more!

Features:

REAL-TIME ANALYSIS:
─────────────────────────────────────────────
Underlines issues as you type:

String password = request.getParameter("pwd");
                  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
                  ⚠️ Security: Don't log passwords

DETAILED EXPLANATIONS:
─────────────────────────────────────────────
Hover over issue:
┌────────────────────────────────────────┐
│ Security Hotspot                       │
│                                        │
│ Avoid using hardcoded credentials.    │
│                                        │
│ This can lead to security issues.     │
│                                        │
│ See: OWASP Top 10                      │
│ [More Info] [Ignore]                   │
└────────────────────────────────────────┘

QUICK FIXES:
─────────────────────────────────────────────
⌥↩ (Alt+Enter) → Apply fix

CATEGORIES:
─────────────────────────────────────────────
🐛 Bug: Potential runtime error
🔒 Security Hotspot: Security risk
💩 Code Smell: Maintainability issue
🎯 Best Practice: Recommended approach

Examples:

BUG:
─────────────────────────────────────────────
if (user = null) {  // Should be ==
    return;
}
// ⚠️ Bug: Assignment instead of comparison

SECURITY:
─────────────────────────────────────────────
String query = "SELECT * FROM users WHERE id = " + userId;
// ⚠️ Security: SQL injection risk

CODE SMELL:
─────────────────────────────────────────────
public void process() {
    // 200 lines of code...
}
// ⚠️ Code Smell: Method too long (max 50 lines)

Installation:
Settings → Plugins → "SonarLint" → Install

Configuration:
Settings → Tools → SonarLint

Options:
☑ Automatically trigger analysis
☑ Show issue locations
☑ Highlight issue in editor

Connect to SonarQube/SonarCloud:
Settings → SonarLint → Add connection
→ Enter server URL
→ Authentication
→ Bind project

Tool Window:
View → Tool Windows → SonarLint
→ See all issues
→ Filter by type
→ Navigate to issue

═══════════════════════════════════════════════════════════

2. CHECKSTYLE-IDEA ⭐⭐⭐⭐
───────────────────────────────────────────
Java code style checker!

What it does:
• Enforce coding standards
• Check style violations
• Team consistency
• Custom rules

Features:
• Real-time checking
• Custom checkstyle.xml
• Predefined rule sets (Google, Sun)
• Quick fixes

Configuration:

1. Create checkstyle.xml:
<?xml version="1.0"?>
<!DOCTYPE module PUBLIC
    "-//Checkstyle//DTD Checkstyle Configuration 1.3//EN"
    "https://checkstyle.org/dtds/configuration_1_3.dtd">

<module name="Checker">
    <module name="TreeWalker">
        <!-- Naming -->
        <module name="TypeName"/>
        <module name="MethodName"/>
        <module name="PackageName"/>

        <!-- Imports -->
        <module name="AvoidStarImport"/>
        <module name="UnusedImports"/>

        <!-- Size -->
        <module name="LineLength">
            <property name="max" value="120"/>
        </module>
        <module name="MethodLength">
            <property name="max" value="50"/>
        </module>

        <!-- Whitespace -->
        <module name="WhitespaceAfter"/>
        <module name="WhitespaceAround"/>
    </module>
</module>

2. Configure plugin:
Settings → Tools → Checkstyle
→ Add checkstyle.xml
→ Set as active

3. Run:
Right-click project → Analyze → Inspect Code

Installation:
Settings → Plugins → "CheckStyle-IDEA" → Install

Tool Window:
View → Tool Windows → CheckStyle
→ Run scan
→ See violations
→ Navigate to code

═══════════════════════════════════════════════════════════

3. PMD ⭐⭐⭐⭐
───────────────────────────────────────────
Source code analyzer!

What it does:
• Find common flaws
• Unused variables
• Empty catch blocks
• Unnecessary object creation
• Complex code

Rules categories:
• Best Practices
• Code Style
• Design
• Documentation
• Error Prone
• Multithreading
• Performance
• Security

Examples:

UNUSED CODE:
─────────────────────────────────────────────
public void process() {
    int x = 5;  // Never used!
    // ...
}
// ⚠️ PMD: Unused local variable

EMPTY CATCH:
─────────────────────────────────────────────
try {
    doSomething();
} catch (Exception e) {
    // Empty!
}
// ⚠️ PMD: Empty catch block

PERFORMANCE:
─────────────────────────────────────────────
for (int i = 0; i < list.size(); i++) {
    // Calls size() each iteration!
}
// ⚠️ PMD: Cache list.size() outside loop

Installation:
Settings → Plugins → "PMDPlugin" → Install

Usage:
Right-click file → Run PMD → Choose rules

═══════════════════════════════════════════════════════════

4. SPOTBUGS ⭐⭐⭐⭐
───────────────────────────────────────────
Find bugs in Java code!

What it does:
• Static analysis
• Find potential bugs
• Detect bad practices
• Security issues

Bug categories:
• Bad practice
• Correctness
• Dodgy code
• Malicious code
• Multithreaded correctness
• Performance
• Security

Examples:

NULL POINTER:
─────────────────────────────────────────────
String value = map.get(key);
int length = value.length();  // Potential NPE!
// ⚠️ SpotBugs: Possible null pointer dereference

RESOURCE LEAK:
─────────────────────────────────────────────
FileInputStream fis = new FileInputStream(file);
// No close() called!
// ⚠️ SpotBugs: Resource leak

EQUALS CONTRACT:
─────────────────────────────────────────────
@Override
public boolean equals(Object obj) {
    return this.name.equals(((User)obj).name);
}
// No hashCode() override!
// ⚠️ SpotBugs: equals() without hashCode()

Installation:
Settings → Plugins → "SpotBugs" → Install

Usage:
Right-click project → Analyze → Run SpotBugs Analysis

Tool Window:
View → Tool Windows → SpotBugs
→ See all bugs
→ Navigate to code
→ Filter by priority

═══════════════════════════════════════════════════════════

5. ESLINT ⭐⭐⭐⭐⭐ (JAVASCRIPT/TYPESCRIPT)
───────────────────────────────────────────
JavaScript linter!

What it does:
• Find JavaScript errors
• Enforce code style
• Auto-fix issues
• Custom rules

Setup:

1. Install ESLint:
npm install eslint --save-dev

2. Initialize:
npx eslint --init

3. Configure IntelliJ:
Settings → Languages & Frameworks → JavaScript → ESLint
☑ Automatic ESLint configuration
☑ Run eslint --fix on save

4. Create .eslintrc.js:
module.exports = {
  env: {
    browser: true,
    es2021: true,
    node: true
  },
  extends: [
    'eslint:recommended',
    'plugin:@typescript-eslint/recommended'
  ],
  rules: {
    'no-console': 'warn',
    'no-unused-vars': 'error',
    'quotes': ['error', 'single'],
    'semi': ['error', 'always']
  }
};

Features:
• Real-time linting
• Auto-fix on save
• Error highlighting
• Quick fixes (⌥↩)

Examples:

UNUSED VARIABLE:
─────────────────────────────────────────────
const x = 5;  // Never used
// ⚠️ ESLint: 'x' is assigned but never used

CONSOLE LOG:
─────────────────────────────────────────────
console.log('Debug');
// ⚠️ ESLint: Unexpected console statement

MISSING SEMICOLON:
─────────────────────────────────────────────
const x = 5  // Missing semicolon
// ⚠️ ESLint: Missing semicolon

AUTO-FIX:
─────────────────────────────────────────────
Save file → ESLint auto-fixes all fixable issues!

Tool Window:
View → Tool Windows → ESLint
→ See all warnings/errors

Built-in (no plugin needed in WebStorm/Ultimate)

═══════════════════════════════════════════════════════════

6. PRETTIER ⭐⭐⭐⭐⭐ (CODE FORMATTER)
───────────────────────────────────────────
Opinionated code formatter!

What it does:
• Auto-format code
• Consistent style
• Supports many languages
• Zero config

Supports:
• JavaScript
• TypeScript
• CSS/SCSS
• HTML
• JSON
• Markdown
• YAML
• GraphQL

Setup:

1. Install Prettier:
npm install prettier --save-dev

2. Create .prettierrc:
{
  "semi": true,
  "singleQuote": true,
  "tabWidth": 2,
  "trailingComma": "es5",
  "printWidth": 80
}

3. Configure IntelliJ:
Settings → Languages & Frameworks → Prettier
☑ Automatic Prettier configuration
☑ Run on save for files: **/*.{js,ts,jsx,tsx,css,json}

Features:
• Format on save
• Format selection
• Consistent formatting
• No configuration debates!

Example:

BEFORE:
─────────────────────────────────────────────
const x={a:1,b:2,c:3};function test(arg1,arg2){return arg1+arg2}

AFTER (Prettier):
─────────────────────────────────────────────
const x = { a: 1, b: 2, c: 3 };

function test(arg1, arg2) {
  return arg1 + arg2;
}

Tool Window:
View → Tool Windows → Prettier

Built-in (no plugin needed in WebStorm/Ultimate)

═══════════════════════════════════════════════════════════

7. ERROR-PRONE COMPILER ⭐⭐⭐⭐
───────────────────────────────────────────
Catch common Java mistakes!

What it does:
• Compile-time checks
• Find bugs early
• Google's bug detector

Setup:

1. Add to build.gradle:
plugins {
    id 'net.ltgt.errorprone' version '3.0.1'
}

dependencies {
    errorprone 'com.google.errorprone:error_prone_core:2.18.0'
}

2. IntelliJ integration:
Settings → Build, Execution, Deployment → Compiler → Java Compiler
→ Use compiler: Error Prone

Examples:

DEPRECATED API:
─────────────────────────────────────────────
Date date = new Date(2023, 1, 1);  // Deprecated!
// ⚠️ Error Prone: Use LocalDate instead

NULL CHECK:
─────────────────────────────────────────────
if (x == null || x.equals("test")) {
    // NPE if x is null!
}
// ⚠️ Error Prone: Possible null pointer

Installation:
Settings → Plugins → "Error Prone" → Install
```

---

### 4️⃣ Framework Support

```bash
# ═══════════════════════════════════════════
# FRAMEWORK-SPECIFIC PLUGINS
# ═══════════════════════════════════════════

═══════════════════════════════════════════════════════════

1. SPRING BOOT ASSISTANT ⭐⭐⭐⭐⭐ (JAVA)
───────────────────────────────────────────
Enhanced Spring Boot development!

What it does:
• application.properties/yaml auto-completion
• Spring Bean navigation
• Endpoint mapping
• Configuration hints
• Request mapping shortcuts

Features:

AUTO-COMPLETION:
─────────────────────────────────────────────
Type in application.properties:
server.   → Shows all server.* properties
spring.   → Shows all spring.* properties

Includes:
• Property name
• Description
• Default value
• Deprecated status

ENDPOINT NAVIGATION:
─────────────────────────────────────────────
Tool Window: Spring Boot
→ Mappings tab
→ See all @RequestMapping endpoints
→ Click to navigate

Example:
GET /api/users → UserController.getAllUsers()
POST /api/users/{id} → UserController.getUser()

BEAN NAVIGATION:
─────────────────────────────────────────────
⌘B on @Autowired field
→ Jumps to bean definition

@Autowired
private UserService userService;  // ⌘B → Jumps to @Service

HTTP CLIENT:
─────────────────────────────────────────────
Next to @RequestMapping:
[▶] Test Endpoint

Click → Opens HTTP client
GET http://localhost:8080/api/users

Send request directly from IDE!

Installation:
Settings → Plugins → "Spring Boot Assistant" → Install

Requirements:
• IntelliJ Ultimate (Spring support built-in)
• Or plugin for Community Edition

═══════════════════════════════════════════════════════════

2. LOMBOK ⭐⭐⭐⭐⭐ (JAVA)
───────────────────────────────────────────
Reduce Java boilerplate!

What it does:
• Generate getters/setters
• Generate equals/hashCode
• Generate toString
• Generate constructors
• Logging annotations

Without Lombok:
─────────────────────────────────────────────
public class User {
    private String name;
    private int age;

    public User() {}

    public User(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public boolean equals(Object o) {
        // ... 20 lines
    }

    @Override
    public int hashCode() {
        // ... 10 lines
    }

    @Override
    public String toString() {
        // ... 5 lines
    }
}

With Lombok:
─────────────────────────────────────────────
@Data
@AllArgsConstructor
@NoArgsConstructor
public class User {
    private String name;
    private int age;
}

That's it! All methods generated! 🎉

Annotations:

@Getter / @Setter
→ Generate getters/setters

@ToString
→ Generate toString()

@EqualsAndHashCode
→ Generate equals() and hashCode()

@NoArgsConstructor
→ Generate empty constructor

@AllArgsConstructor
→ Generate constructor with all fields

@RequiredArgsConstructor
→ Constructor for final fields

@Data
→ @Getter + @Setter + @ToString + @EqualsAndHashCode + @RequiredArgsConstructor

@Builder
→ Builder pattern

@Slf4j
→ Logging (log field automatically available)

Examples:

BUILDER:
─────────────────────────────────────────────
@Builder
public class User {
    private String name;
    private int age;
    private String email;
}

// Usage:
User user = User.builder()
    .name("MrDib")
    .age(25)
    .email("email@example.com")
    .build();

LOGGING:
─────────────────────────────────────────────
@Slf4j
public class UserService {
    public void process() {
        log.info("Processing...");
        log.error("Error occurred", exception);
    }
}

Installation:
Settings → Plugins → "Lombok" → Install

Setup:
1. Add dependency (Maven):
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.18.30</version>
    <scope>provided</scope>
</dependency>

2. Enable annotation processing:
Settings → Build, Execution, Deployment → Compiler → Annotation Processors
☑ Enable annotation processing

═══════════════════════════════════════════════════════════

3. REACT SNIPPETS ⭐⭐⭐⭐⭐ (JAVASCRIPT)
───────────────────────────────────────────
React code snippets!

What it does:
• Quick React component creation
• Hooks snippets
• PropTypes snippets
• Redux snippets

Snippets:

COMPONENT:
─────────────────────────────────────────────
rfc → React Functional Component
import React from 'react';

const ComponentName = () => {
  return (
    <div>

    </div>
  );
};

export default ComponentName;

rfce → React Functional Component with Export
rcc → React Class Component

HOOKS:
─────────────────────────────────────────────
useState → const [state, setState] = useState(initialValue);
useEffect → useEffect(() => { }, []);
useContext → const context = useContext(ContextName);
useReducer → const [state, dispatch] = useReducer(reducer, initialState);
useCallback → useCallback(() => { }, []);
useMemo → useMemo(() => { }, []);
useRef → const ref = useRef(initialValue);

PROPS:
─────────────────────────────────────────────
impt → Import PropTypes
rpt → PropTypes definition

REDUX:
─────────────────────────────────────────────
rxaction → Redux action
rxreducer → Redux reducer
rxselect → Redux selector

Installation:
Settings → Plugins → "React Snippets" → Install

Or use built-in React support in WebStorm/Ultimate!

═══════════════════════════════════════════════════════════

4. VUE.JS ⭐⭐⭐⭐⭐ (JAVASCRIPT)
───────────────────────────────────────────
Vue.js support!

What it does:
• Vue component syntax
• Template highlighting
• Auto-completion
• Navigation
• Refactoring

Features:

COMPONENT CREATION:
─────────────────────────────────────────────
Right-click → New → Vue Component

Generates:
<template>
  <div>
    {{ message }}
  </div>
</template>

<script>
export default {
  name: 'ComponentName',
  data() {
    return {
      message: 'Hello!'
    }
  }
}
</script>

<style scoped>
/* Component styles */
</style>

AUTO-COMPLETION:
─────────────────────────────────────────────
In template:
<div v-   → Shows all Vue directives
v-if
v-for
v-model
v-bind
v-on

NAVIGATION:
─────────────────────────────────────────────
⌘B on component tag → Jump to component definition

<UserProfile />  // ⌘B → UserProfile.vue

REFACTORING:
─────────────────────────────────────────────
Extract component
Extract method
Rename

Built-in in WebStorm/Ultimate!

═══════════════════════════════════════════════════════════

5. ANGULAR / ANGULARJS ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Angular framework support!

Features:
• Component creation
• Service generation
• Template syntax
• Auto-completion
• Navigation
• Refactoring

Component Creation:
─────────────────────────────────────────────
Right-click → New → Angular Schematic
→ Choose: Component, Service, Module, etc.

Generates full Angular component structure!

Template Support:
─────────────────────────────────────────────
Auto-completion for:
• Directives: *ngIf, *ngFor, [ngClass]
• Pipes: {{ value | date }}
• Events: (click)="handler()"
• Properties: [disabled]="isDisabled"

Navigation:
─────────────────────────────────────────────
⌘B on selector → Jump to component

Built-in in WebStorm/Ultimate!

═══════════════════════════════════════════════════════════

6. DATABASE NAVIGATOR ⭐⭐⭐⭐
───────────────────────────────────────────
Database IDE within IntelliJ!

What it does:
• Database connections
• SQL editor
• Query execution
• Data viewer
• Schema browser

Features:

CONNECTION MANAGEMENT:
─────────────────────────────────────────────
View → Tool Windows → Database Navigator
→ New Connection
→ Select: PostgreSQL, MySQL, Oracle, etc.
→ Enter credentials
→ Test connection
→ Connect

SCHEMA BROWSER:
─────────────────────────────────────────────
📁 Database
  📁 Schemas
    📁 public
      📁 Tables
        📄 users (columns, indexes, constraints)
        📄 posts
      📁 Views
      📁 Procedures

SQL EDITOR:
─────────────────────────────────────────────
Right-click table → New SQL Console

Features:
• Auto-completion (table names, columns)
• Syntax highlighting
• Query execution
• Result grid
• Export results

DATA VIEWER:
─────────────────────────────────────────────
Double-click table → Opens data grid

Features:
• View data
• Edit inline
• Filter rows
• Sort columns
• Add/delete rows

ER DIAGRAM:
─────────────────────────────────────────────
Right-click schema → Diagrams → Show Diagram

Visual representation of:
• Tables
• Relationships
• Foreign keys

Installation:
Settings → Plugins → "Database Navigator" → Install

Or use built-in Database Tools (Ultimate Edition)!

Note: IntelliJ Ultimate has superior built-in database tools!
```

---

### 5️⃣ UI/UX Enhancements

```bash
# ═══════════════════════════════════════════
# UI/UX PLUGINS
# ═══════════════════════════════════════════

═══════════════════════════════════════════════════════════

1. NYAN PROGRESS BAR 🐱 ⭐⭐⭐⭐⭐ (FUN!)
───────────────────────────────────────────
Nyan Cat progress bar!

What it does:
• Replaces boring progress bar
• Nyan Cat animation
• Rainbow trail
• Makes waiting fun!

Visual:
[🐱════════════════════] 67%

Because why not? 😄

Installation:
Settings → Plugins → "Nyan Progress Bar" → Install

Restart IDE → Enjoy! 🎉

═══════════════════════════════════════════════════════════

2. POWER MODE II ⭐⭐⭐⭐ (FUN!)
───────────────────────────────────────────
Particles and effects when typing!

What it does:
• Particles fly off cursor
• Screen shake
• Combo counter
• Sound effects

Visual:
Type code → ✨💥⭐ Particles everywhere!

Installation:
Settings → Plugins → "Power Mode II" → Install

Configuration:
Settings → Other Settings → Power Mode II

Options:
☑ Enable particles
☑ Enable shake
☐ Enable sound (can be annoying)
• Particle count: 50
• Shake intensity: 2

Warning: Very distracting! Use for fun, not production 😅

═══════════════════════════════════════════════════════════

3. BACKGROUND IMAGE PLUS+ ⭐⭐⭐⭐
───────────────────────────────────────────
Custom background images!

What it does:
• Set custom background
• Different images per window
• Opacity control
• Image positioning

Setup:
View → Appearance → Set Background Image
→ Choose image
→ Adjust opacity: 10-20% (keep readable!)
→ OK

Or:
Settings → Appearance & Behavior → Background Image

Recommended:
• Subtle images
• Low opacity (10-15%)
• High contrast with text

Installation:
Settings → Plugins → "Background Image Plus+" → Install

═══════════════════════════════════════════════════════════

4. GRAZIE PRO ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Advanced grammar and spell checking!

What it does:
• Grammar checking
• Spell checking
• Style suggestions
• Supports multiple languages

Features:
• Better than built-in spell check
• Context-aware
• Technical writing
• Code comments
• Documentation

Installation:
Settings → Plugins → "Grazie Pro" → Install

Configuration:
Settings → Editor → Natural Languages → Grazie

Languages:
☑ English
☐ Spanish
☐ German
☐ French
☐ etc.

Check:
☑ Comments
☑ String literals
☑ Documentation
☑ Text files
☐ Commit messages

═══════════════════════════════════════════════════════════

5. ATOM MATERIAL ICONS ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Beautiful file icons!

(Already covered in Icon Packs section)

═══════════════════════════════════════════════════════════

6. EXTRA ICONS ⭐⭐⭐⭐
───────────────────────────────────────────
More file type icons!

(Already covered in Icon Packs section)

═══════════════════════════════════════════════════════════

7. INDENT RAINBOW ⭐⭐⭐⭐
───────────────────────────────────────────
Colorful indentation!

(Already covered in Productivity Boosters section)
```

---

### 6️⃣ AI Assistants

```bash
# ═══════════════════════════════════════════
# AI-POWERED PLUGINS
# ═══════════════════════════════════════════

═══════════════════════════════════════════════════════════

1. GITHUB COPILOT ⭐⭐⭐⭐⭐ (BEST!)
───────────────────────────────────────────
AI pair programmer!

What it does:
• Code suggestions
• Complete functions
• Write tests
• Documentation
• Explain code
• Fix bugs

Requirements:
• GitHub Copilot subscription ($10/month or $100/year)
• Free for students, teachers, open source maintainers

Features:

CODE COMPLETION:
─────────────────────────────────────────────
Start typing function:

// Type: function calculate
function calculateTotalPrice(items) {
    // Copilot suggests:
    return items.reduce((total, item) => total + item.price, 0);
}

Gray text = Copilot suggestion
Tab = Accept
Esc = Reject

MULTIPLE SUGGESTIONS:
─────────────────────────────────────────────
⌥] (Alt+]) → Next suggestion
⌥[ (Alt+[) → Previous suggestion

COMMENT TO CODE:
─────────────────────────────────────────────
// Sort array of users by age in descending order
// Copilot generates:
const sortedUsers = users.sort((a, b) => b.age - a.age);

TESTS:
─────────────────────────────────────────────
// test getUserById
// Copilot generates:
test('getUserById returns user when found', () => {
    const user = getUserById(1);
    expect(user).toBeDefined();
    expect(user.id).toBe(1);
});

DOCUMENTATION:
─────────────────────────────────────────────
/**
 * Copilot generates JSDoc:
 * Calculates the total price of items
 * @param {Array} items - Array of items with price property
 * @returns {number} Total price
 */

COPILOT CHAT:
─────────────────────────────────────────────
View → Tool Windows → GitHub Copilot Chat

Ask questions:
• "How do I sort this array?"
• "Explain this function"
• "Find bugs in this code"
• "Write tests for this"
• "Optimize this function"

Example:
You: "Explain this code"
Copilot: "This function calculates the factorial..."

You: "How can I optimize it?"
Copilot: "You can use memoization..."

COPILOT LABS:
─────────────────────────────────────────────
Additional features:
• Explain code
• Translate to another language
• Fix bug
• Write tests
• Make code readable

Installation:
Settings → Plugins → "GitHub Copilot" → Install
→ Sign in with GitHub
→ Start coding!

Configuration:
Settings → Tools → GitHub Copilot

Options:
☑ Enable GitHub Copilot
☑ Show inline suggestions
☑ Accept suggestions with Tab
Languages: All (or select specific)

Tips:
• Write descriptive comments for better suggestions
• Use meaningful variable names
• Break down complex functions
• Review suggestions before accepting!

═══════════════════════════════════════════════════════════

2. TABNINE ⭐⭐⭐⭐⭐
───────────────────────────────────────────
AI code completion!

What it does:
• Context-aware completions
• Learns from your code
• Works offline (Pro)
• Supports all languages

Tiers:
• Free: Basic completions
• Pro ($12/month): Advanced AI, team learning

Features:

SMART COMPLETION:
─────────────────────────────────────────────
Learns your coding patterns:

// After writing similar code:
function getUserBy
// Tabnine suggests:
function getUserById(id) {
    return users.find(user => user.id === id);
}

WHOLE-LINE COMPLETION:
─────────────────────────────────────────────
Start typing:
const result =
// Suggests: array.filter(item => item.active).map(item => item.name);

TEAM LEARNING (PRO):
─────────────────────────────────────────────
Learns from your team's codebase:
• Common patterns
• Team conventions
• Best practices

Installation:
Settings → Plugins → "Tabnine" → Install
→ Sign in (optional, for Pro features)

Configuration:
Settings → Tools → Tabnine

Options:
☑ Enable Tabnine
☑ Deep completions (Pro)
☑ Inline suggestions
☑ Learn from my code

═══════════════════════════════════════════════════════════

3. JETBRAINS AI ASSISTANT ⭐⭐⭐⭐⭐ (NEW!)
───────────────────────────────────────────
Native JetBrains AI!

What it does:
• Code completion
• Chat interface
• Refactoring suggestions
• Test generation
• Documentation
• Commit message generation

Requirements:
• JetBrains AI subscription
• Or JetBrains All Products Pack

Features:

AI CHAT:
─────────────────────────────────────────────
View → Tool Windows → AI Assistant

Ask anything:
• "How do I implement authentication?"
• "Explain this Spring annotation"
• "Write a test for this method"
• "Refactor this code"

CONTEXT-AWARE:
─────────────────────────────────────────────
AI understands:
• Your project structure
• Dependencies
• Framework (Spring, React, etc.)
• Your coding style

REFACTORING:
─────────────────────────────────────────────
Select code → Right-click → AI Actions
• Suggest refactoring
• Simplify
• Add error handling
• Extract method

TEST GENERATION:
─────────────────────────────────────────────
Right-click method → AI Actions → Generate Tests

Creates comprehensive test cases!

COMMIT MESSAGES:
─────────────────────────────────────────────
⌘K (Commit) → AI button → Generate commit message

AI analyzes your changes and writes descriptive message!

Installation:
Built-in! (Enable in Settings)

Settings → Tools → AI Assistant
☑ Enable AI Assistant

═══════════════════════════════════════════════════════════

4. CODEIUM ⭐⭐⭐⭐
───────────────────────────────────────────
Free AI code acceleration!

What it does:
• Code completion (FREE!)
• Chat interface
• Similar to Copilot
• No subscription required

Installation:
Settings → Plugins → "Codeium" → Install
→ Sign up (free)

Features:
• Multi-line completions
• Context-aware
• 70+ languages
• Fast suggestions

Best for:
• Budget-conscious developers
• Students
• Open source projects

═══════════════════════════════════════════════════════════

COMPARISON: AI ASSISTANTS
───────────────────────────────────────────

┌─────────────┬──────────┬─────────┬──────────┬─────────┐
│ Feature     │ Copilot  │ Tabnine │ JetBrains│ Codeium │
│             │          │         │ AI       │         │
├─────────────┼──────────┼─────────┼──────────┼─────────┤
│ Completion  │ ⭐⭐⭐⭐⭐ │ ⭐⭐⭐⭐⭐│ ⭐⭐⭐⭐⭐ │ ⭐⭐⭐⭐  │
├─────────────┼──────────┼─────────┼──────────┼─────────┤
│ Chat        │ ⭐⭐⭐⭐⭐ │ ⭐⭐⭐    │ ⭐⭐⭐⭐⭐ │ ⭐⭐⭐⭐  │
├─────────────┼──────────┼─────────┼──────────┼─────────┤
│ Context     │ ⭐⭐⭐⭐⭐ │ ⭐⭐⭐⭐  │ ⭐⭐⭐⭐⭐ │ ⭐⭐⭐⭐  │
├─────────────┼──────────┼─────────┼──────────┼─────────┤
│ Price       │ $10/mo   │ $12/mo  │ Bundle   │ FREE!   │
├─────────────┼──────────┼─────────┼──────────┼─────────┤
│ Offline     │ No       │ Pro only│ No       │ No      │
├─────────────┼──────────┼─────────┼──────────┼─────────┤
│ Integration │ ⭐⭐⭐⭐  │ ⭐⭐⭐⭐⭐│ ⭐⭐⭐⭐⭐ │ ⭐⭐⭐⭐  │
└─────────────┴──────────┴─────────┴──────────┴─────────┘

RECOMMENDATION:
• Best overall: GitHub Copilot ⭐
• Best for JetBrains users: JetBrains AI ⭐
• Best free option: Codeium ⭐
• Best for teams: Tabnine Pro

You can use multiple! Try them all! 🚀
```

---

<div align="center">

## 💡 Pro Tips & Tricks

_Become a power user_ 🚀

</div>

### Power User Features 🚀

```bash
# ═══════════════════════════════════════════
# ADVANCED FEATURES
# ═══════════════════════════════════════════

1. MULTIPLE CURSORS ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Edit multiple locations simultaneously!

METHOD 1: Alt/Option + Click
─────────────────────────────────────────────
macOS: ⌥ + Click
Windows/Linux: Alt + Click

Click multiple locations → Multiple cursors!

// Example:
const name = "John";
const age = 25;
const city = "Tokyo";

// ⌥+Click before each "const" → Change all to "let"

METHOD 2: Select Next Occurrence
─────────────────────────────────────────────
1. Select word
2. ⌃G (Ctrl+G) → Adds next occurrence
3. Repeat → Adds more

// Example:
const user = getUser();
const user = loadUser();
const user = fetchUser();

// Select "user" → ⌃G → ⌃G → Change all at once!

METHOD 3: Select All Occurrences
─────────────────────────────────────────────
1. Select word
2. ⌃⌘G (Ctrl+Alt+Shift+J) → Selects ALL occurrences
3. Type → Changes all!

METHOD 4: Column Selection
─────────────────────────────────────────────
1. ⌘⇧8 (Ctrl+Shift+8) → Enable column mode
2. ⌥+Drag (Alt+Drag) → Select column
3. Type → Changes all lines

// Example:
const x = 1;
const y = 2;
const z = 3;

// Select "const" column → Change to "let"

METHOD 5: Clone Caret Above/Below
─────────────────────────────────────────────
macOS: Press ⌥ twice (hold), then ↑/↓
Windows/Linux: Press Ctrl twice (hold), then ↑/↓

Creates caret on line above/below!

═══════════════════════════════════════════════════════════

2. COLUMN SELECTION MODE ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Edit rectangular blocks of text!

Toggle: ⌘⇧8 (Ctrl+Shift+8)

Use cases:

ALIGN CODE:
─────────────────────────────────────────────
// Before:
const x = 1;
const longName = 2;
const y = 3;

// Column select before "="
// Add spaces to align:
const x        = 1;
const longName = 2;
const y        = 3;

ADD SAME TEXT TO MULTIPLE LINES:
─────────────────────────────────────────────
// Before:
user.name
user.email
user.age

// Column select beginning
// Type "console.log(" :
console.log(user.name
console.log(user.email
console.log(user.age

REMOVE COLUMNS:
─────────────────────────────────────────────
// Select and delete columns!

═══════════════════════════════════════════════════════════

3. SEARCH EVERYWHERE FILTERS ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Advanced search tricks!

Press ⇧⇧ (Double Shift) then use prefixes:

PREFIXES:
─────────────────────────────────────────────
/  → Search files
   Example: /User
   Finds: User.java, UserService.java, etc.

#  → Search actions
   Example: #Format
   Finds: Reformat Code, Format File, etc.

:  → Go to line
   Example: :42
   Goes to line 42 in current file

@  → Search symbols (methods, fields)
   Example: @getUserById
   Finds: getUserById method

.  → Search recent files
   Example: .User
   Filters recent files

COMBINATIONS:
─────────────────────────────────────────────
⇧⇧ → /User.java → Enter
→ Opens User.java

⇧⇧ → #Reformat → Enter
→ Runs Reformat Code

⇧⇧ → :100 → Enter
→ Jumps to line 100

⇧⇧ → @main → Enter
→ Jumps to main method

⇧⇧ → .pom → Enter
→ Opens recent pom.xml

FUZZY SEARCH:
─────────────────────────────────────────────
Don't need exact names!

⇧⇧ → UsServ
Finds: UserService, UserServlet, etc.

⇧⇧ → UFP
Finds: UserFileProcessor (uppercase letters)

SEARCH IN SPECIFIC TAB:
─────────────────────────────────────────────
⇧⇧ → Tab (Classes, Files, Actions, etc.)
→ Type query
→ Results filtered to that tab

═══════════════════════════════════════════════════════════

4. QUICK DOCUMENTATION ⭐⭐⭐⭐⭐
───────────────────────────────────────────
View documentation without leaving code!

Shortcut:
macOS: ⌃J
Windows/Linux: Ctrl+Q

Usage:
Cursor on symbol → ⌃J

Shows:
┌────────────────────────────────────────┐
│ String                                 │
│                                        │
│ java.lang.String                       │
│                                        │
│ The String class represents character  │
│ sequences. Strings are constant...     │
│                                        │
│ Methods:                               │
│ • length() - Returns length            │
│ • charAt(int) - Returns character      │
│ • substring(int, int) - Returns sub... │
│                                        │
│ See also: StringBuilder, CharSequence  │
└────────────────────────────────────────┘

Features:
• Clickable links
• Scroll through docs
• Copy code examples
• Press ⌃J again → Opens external docs

AUTO-SHOW:
─────────────────────────────────────────────
Settings → Editor → General → Code Completion
☑ Show quick documentation on mouse move
Delay: 500ms

Hover over symbol → Docs appear automatically!

═══════════════════════════════════════════════════════════

5. POSTFIX COMPLETION ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Type expressions backwards!

Idea: Write value first, then add postfix

JAVA POSTFIXES:
─────────────────────────────────────────────
.var → Wrap in variable
user.var → User user = expression;

.null → Null check
user.null → if (user == null) { }

.notnull → Not null check
user.notnull → if (user != null) { }

.nn → Not null check (short)
user.nn → if (user != null) { }

.for → For loop
list.for → for (Type item : list) { }

.fori → For loop with index
list.fori → for (int i = 0; i < list.size(); i++) { }

.forr → Reverse for loop
list.forr → for (int i = list.size()-1; i >= 0; i--) { }

.return → Return statement
result.return → return result;

.sout → System.out.println
value.sout → System.out.println(value);

.try → Try-catch
riskyCode().try → try { riskyCode(); } catch (Exception e) { }

.if → If statement
condition.if → if (condition) { }

.else → If-else statement
condition.else → if (!condition) { }

.while → While loop
condition.while → while (condition) { }

.cast → Type cast
value.cast → ((Type) value)

.arg → Method argument
value.arg → method(value)

.lambda → Lambda expression
value.lambda → () -> value

.not → Negate
condition.not → !condition

.par → Parentheses
expr.par → (expr)

JAVASCRIPT/TYPESCRIPT POSTFIXES:
─────────────────────────────────────────────
.log → console.log
value.log → console.log(value);

.error → console.error
error.error → console.error(error);

.warn → console.warn
warning.warn → console.warn(warning);

.var / .let / .const → Variable
value.const → const name = value;

.return → Return
value.return → return value;

.await → Await
promise.await → await promise

.then → Promise then
promise.then → promise.then(result => { })

.typeof → Type check
value.typeof → typeof value

.not → Negate
condition.not → !condition

PYTHON POSTFIXES:
─────────────────────────────────────────────
.print → Print
value.print → print(value)

.len → Length
list.len → len(list)

.for → For loop
iterable.for → for item in iterable:

.if → If statement
condition.if → if condition:

Examples:
─────────────────────────────────────────────
// JAVA:
getUserById(123).var
→ User user = getUserById(123);

users.for
→ for (User user : users) { }

result.return
→ return result;

// JAVASCRIPT:
fetchData().await
→ await fetchData()

items.log
→ console.log(items);

response.return
→ return response;

// PYTHON:
get_users().for
→ for user in get_users():

len(items).print
→ print(len(items))

═══════════════════════════════════════════════════════════

6. SCRATCHES & CONSOLES ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Temporary files for experiments!

Create Scratch:
─────────────────────────────────────────────
⌘⇧N (Ctrl+Shift+Alt+Insert)
→ New Scratch File
→ Choose language
→ Start coding!

Or:
File → New → Scratch File

Features:
• Not part of project
• Saved automatically
• Syntax highlighting
• Code completion
• Run code

Use cases:
• Quick experiments
• Test code snippets
• SQL queries
• HTTP requests
• JSON formatting
• RegEx testing

SCRATCH TYPES:
─────────────────────────────────────────────
Java Scratch:
→ Run → Execute
→ See output in console

JavaScript Scratch:
→ Run → Execute
→ Runs in Node.js

HTTP Request Scratch:
→ Write HTTP requests
→ Send from IDE

GET https://api.github.com/users/mrdib
Accept: application/json

###

POST https://api.example.com/users
Content-Type: application/json

{
  "name": "MrDib",
  "email": "email@example.com"
}

SQL Scratch:
→ Connect to database
→ Write queries
→ Execute
→ See results

LOCATION:
─────────────────────────────────────────────
View → Tool Windows → Project
→ Scratches and Consoles
→ All scratches listed

═══════════════════════════════════════════════════════════

7. LOCAL HISTORY ⭐⭐⭐⭐⭐ (LIFESAVER!)
───────────────────────────────────────────
IntelliJ tracks ALL changes!

What it saves:
• Every save
• Every refactoring
• Before/after test runs
• Even deleted files!

View Local History:
─────────────────────────────────────────────
Right-click file → Local History → Show History

Shows:
┌────────────────────────────────────────┐
│ Timestamp        │ Label               │
├──────────────────┼─────────────────────┤
│ 2 minutes ago    │ Saved               │
│ 10 minutes ago   │ Refactoring: Rename │
│ 1 hour ago       │ Saved               │
│ 2 hours ago      │ Before test run     │
└────────────────────────────────────────┘

Click timestamp → See diff
→ Revert if needed!

Restore Deleted File:
─────────────────────────────────────────────
Right-click folder → Local History → Show History
→ Find file
→ Revert

SAVED MY LIFE MANY TIMES! 🛡️

Use cases:
• "What did I change?"
• "How did this work before?"
• "Undo refactoring"
• "Recover deleted code"

Settings:
─────────────────────────────────────────────
Settings → System Settings → Local History

Days to keep: 5 (default)
• Keep longer for important projects

═══════════════════════════════════════════════════════════

8. COMPARE FILES/FOLDERS ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Visual diff tool!

Compare Files:
─────────────────────────────────────────────
1. Select two files
2. Right-click → Compare Files
3. See side-by-side diff

Features:
• Syntax highlighting
• Navigate differences (F7/⇧F7)
• Apply changes (◀ / ▶)
• Edit inline
• Merge changes

Compare Folders:
─────────────────────────────────────────────
1. Select two folders
2. Right-click → Compare Directories

Shows:
┌────────────────────────────────────────┐
│ File         │ Left  │ Right          │
├──────────────┼───────┼────────────────┤
│ User.java    │ ✅    │ ✅ (modified)  │
│ Test.java    │ ✅    │ ❌ (missing)   │
│ Config.xml   │ ❌    │ ✅ (new)       │
└────────────────────────────────────────┘

Compare with Clipboard:
─────────────────────────────────────────────
Select text → Right-click → Compare with Clipboard

Great for:
• Comparing configs
• Reviewing API responses
• Checking outputs

Compare with Branch:
─────────────────────────────────────────────
Right-click file → Git → Compare with Branch
→ Select branch
→ See differences

═══════════════════════════════════════════════════════════

9. HTTP CLIENT ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Test APIs directly from IDE!

Create HTTP Request:
─────────────────────────────────────────────
Tools → HTTP Client → Create Request in HTTP Client

Or create .http file:
Right-click → New → HTTP Request

Syntax:
─────────────────────────────────────────────
# Simple GET request
GET https://api.github.com/users/mrdib
Accept: application/json

###

# POST request
POST https://api.example.com/users
Content-Type: application/json

{
  "name": "MrDib",
  "email": "email@example.com"
}

###

# With headers
GET https://api.example.com/protected
Authorization: Bearer {{token}}
Accept: application/json

###

# With variables
GET https://{{host}}/api/users/{{userId}}

# Define variables in http-client.env.json:
{
  "dev": {
    "host": "localhost:8080",
    "userId": "123",
    "token": "abc123"
  },
  "prod": {
    "host": "api.production.com",
    "userId": "456",
    "token": "xyz789"
  }
}

Execute Request:
─────────────────────────────────────────────
Click ▶ icon next to request

Results:
┌────────────────────────────────────────┐
│ Response                               │
├────────────────────────────────────────┤
│ Status: 200 OK                         │
│ Time: 245ms                            │
│                                        │
│ Headers:                               │
│ Content-Type: application/json         │
│                                        │
│ Body:                                  │
│ {                                      │
│   "id": 123,                           │
│   "name": "MrDib",                     │
│   "email": "email@example.com"         │
│ }                                      │
└────────────────────────────────────────┘

Advanced Features:
─────────────────────────────────────────────
# Multiple requests
GET {{host}}/users
###
POST {{host}}/users
Content-Type: application/json

{"name": "User"}
###

# Save response to file
GET {{host}}/users
> response.json

# Use response in next request
POST {{host}}/login
###
GET {{host}}/profile
Authorization: Bearer {{login.response.body.token}}

# GraphQL
POST {{host}}/graphql
Content-Type: application/json

{
  "query": "query { users { id name } }"
}

Benefits:
─────────────────────────────────────────────
✅ No Postman needed!
✅ Requests in version control
✅ Share with team
✅ Environment variables
✅ Test automation
✅ Response validation

═══════════════════════════════════════════════════════════

10. DATABASE TOOLS (ULTIMATE) ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Built-in database IDE!

(IntelliJ Ultimate Edition only)

Open Database Tool:
─────────────────────────────────────────────
View → Tool Windows → Database

Features:

CONNECTION MANAGEMENT:
─────────────────────────────────────────────
+ → New → Data Source
→ Select: PostgreSQL, MySQL, Oracle, MongoDB, etc.
→ Download driver (automatic)
→ Enter credentials
→ Test connection
→ OK

SCHEMA BROWSER:
─────────────────────────────────────────────
📁 Database
  📁 Schemas
    📁 public
      📁 Tables
        📄 users
          📁 Columns
            id (integer, PK)
            name (varchar)
            email (varchar)
          📁 Indexes
          📁 Foreign Keys
          📁 Triggers

SQL EDITOR:
─────────────────────────────────────────────
Right-click database → New → Query Console

Features:
• Intelligent completion (table/column names)
• Syntax highlighting
• Execute query (⌘↩)
• Explain plan
• Format SQL (⌘⌥L)

SELECT * FROM users WHERE |
                         ↑ Completion shows all columns!

DATA VIEWER:
─────────────────────────────────────────────
Double-click table → Data editor opens

Features:
• View data in grid
• Edit inline
• Add/delete rows
• Filter rows
• Sort columns
• Export data (CSV, JSON, SQL, etc.)
• Pagination

ER DIAGRAMS:
─────────────────────────────────────────────
Right-click schema → Diagrams → Show Diagram

Visual diagram shows:
• Tables
• Columns
• Relationships (foreign keys)
• Primary keys

MIGRATIONS:
─────────────────────────────────────────────
Right-click table → SQL Scripts → DDL

Generates CREATE TABLE statement!

DATA IMPORT/EXPORT:
─────────────────────────────────────────────
Right-click table → Import/Export Data

Formats:
• CSV
• JSON
• XML
• SQL INSERT statements

QUERY HISTORY:
─────────────────────────────────────────────
View all executed queries
→ Re-run previous queries
→ See execution time

DATABASE DIFF:
─────────────────────────────────────────────
Compare two databases:
• Structure differences
• Data differences
• Generate migration script

This is THE BEST database tool! 🎯
```

---

### Productivity Hacks ⚡

```bash
# ═══════════════════════════════════════════
# ADVANCED PRODUCTIVITY TIPS
# ═══════════════════════════════════════════

1. CUSTOM LIVE TEMPLATES ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Create your own code snippets!

Settings → Editor → Live Templates

Create Template:
─────────────────────────────────────────────
1. Click + → Template Group → "My Templates"
2. Click + → Live Template

Example: Logger template

Abbreviation: logger
Description: Create logger field
Template text:
private static final Logger log = LoggerFactory.getLogger($CLASS$.class);
$END$

Define variables:
$CLASS$ → className()
$END$ → cursor position

Context: Java → Declaration

Usage:
Type: logger<Tab>
Result:
private static final Logger log = LoggerFactory.getLogger(CurrentClass.class);
|  ← cursor here

More Examples:
─────────────────────────────────────────────
Abbreviation: todo
Template:
// TODO($USER$): $TEXT$
$END$

Variables:
$USER$ → user()
$TEXT$ → no default (ask user)

Abbreviation: test
Template:
@Test
void test$NAME$() {
    // given
    $GIVEN$

    // when
    $WHEN$

    // then
    $THEN$
}

Abbreviation: main
Template:
public static void main(String[] args) {
    $END$
}

Custom templates save hours! ⚡

═══════════════════════════════════════════════════════════

2. MACROS ⭐⭐⭐⭐
───────────────────────────────────────────
Record sequences of actions!

Record Macro:
─────────────────────────────────────────────
Edit → Macros → Start Macro Recording

Perform actions:
1. ⌘D (duplicate line)
2. ⌘/ (comment)
3. Move down

Edit → Macros → Stop Macro Recording
→ Name it: "Duplicate and Comment"

Assign Shortcut:
─────────────────────────────────────────────
Settings → Keymap
→ Search: "Duplicate and Comment"
→ Add Keyboard Shortcut: ⌘⌥D

Now: ⌘⌥D duplicates line and comments original!

Use cases:
• Repetitive refactorings
• Complex formatting
• Multi-step operations

═══════════════════════════════════════════════════════════

3. EXTERNAL TOOLS ⭐⭐⭐⭐
───────────────────────────────────────────
Integrate command-line tools!

Settings → Tools → External Tools → +

Example: Prettier Integration

Name: Prettier
Program: /usr/local/bin/prettier
Arguments: --write $FilePath$
Working directory: $ProjectFileDir$

☑ Synchronize files after execution
☑ Open console for tool output

Usage:
Right-click file → External Tools → Prettier

Or assign shortcut:
Settings → Keymap → External Tools → Prettier
→ Add: ⌘⌥⇧P

More Examples:
─────────────────────────────────────────────
ESLint Fix:
Program: npx
Arguments: eslint --fix $FilePath$

Black (Python formatter):
Program: black
Arguments: $FilePath$

Custom Scripts:
Program: /path/to/your/script.sh
Arguments: $FilePath$

Macros available:
$FilePath$ → Full file path
$FileName$ → File name
$FileDir$ → File directory
$ProjectFileDir$ → Project root
$ContentRoot$ → Content root
$MODULE_DIR$ → Module directory
$Prompt$ → Ask user for input

═══════════════════════════════════════════════════════════

4. STRUCTURAL SEARCH & REPLACE ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Advanced find & replace with code structure!

Edit → Find → Replace Structurally

Example: Find all System.out.println

Search template:
System.out.println($text$);

Replace template:
log.info($text$);

Click Replace → All System.out.println become log.info!

More Examples:
─────────────────────────────────────────────
Find all try-catch with empty catch:
try {
    $statements$
} catch ($Exception$ $e$) {
}

Replace with logged exception:
try {
    $statements$
} catch ($Exception$ $e$) {
    log.error("Error: ", $e$);
}

Find deprecated API:
@Deprecated
$Method$

Find potential null pointer:
$var$ == null

This is POWERFUL! 🎯

═══════════════════════════════════════════════════════════

5. RUN CONFIGURATIONS TEMPLATES ⭐⭐⭐⭐
───────────────────────────────────────────
Create run configuration templates!

Run → Edit Configurations → Templates

Create template for Spring Boot apps:
─────────────────────────────────────────────
1. Select: Spring Boot
2. Set default VM options:
   -Xmx2048m -Dspring.profiles.active=dev
3. Set default environment variables:
   DB_HOST=localhost
   DB_PORT=5432
4. Save template

Now all new Spring Boot configs inherit these! 🎉

═══════════════════════════════════════════════════════════

6. BOOKMARKS ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Mark important locations!

Toggle Bookmark:
─────────────────────────────────────────────
F3 (macOS) / F11 (Windows/Linux)

Mnemonic Bookmark:
─────────────────────────────────────────────
⌥F3 (macOS) / Ctrl+F11 (Windows/Linux)
→ Assign letter: A-Z, 0-9

Jump to Mnemonic:
⌃ + Letter (macOS)
Ctrl + Letter (Windows/Linux)

View All Bookmarks:
─────────────────────────────────────────────
⌘F3 (macOS) / Shift+F11 (Windows/Linux)

Shows:
┌────────────────────────────────────────┐
│ Bookmarks                              │
├────────────────────────────────────────┤
│ A: UserService.java:42                 │
│ B: UserController.java:128             │
│ 1: application.properties:10           │
└────────────────────────────────────────┘

Use cases:
• Mark TODO locations
• Important methods
• Bug locations
• Reference code

═══════════════════════════════════════════════════════════

7. TASKS & CONTEXTS ⭐⭐⭐⭐
───────────────────────────────────────────
Switch between tasks seamlessly!

Open Tasks:
─────────────────────────────────────────────
Tools → Tasks & Contexts → Open Task

Or: ⌥⇧N (Alt+Shift+N)

Features:
• Saves open files
• Saves navigation history
• Saves breakpoints
• Restores everything when switching back!

Example Workflow:
─────────────────────────────────────────────
Working on Feature A:
• 10 files open
• 5 breakpoints set
• Specific tool windows open

Bug reported! Need to fix now:
1. ⌥⇧N → "Fix Bug #123"
2. Open relevant files
3. Fix bug
4. Commit

Back to Feature A:
1. ⌥⇧N → "Feature A"
2. All 10 files restored!
3. Breakpoints restored!
4. Continue where you left off!

No more: "What was I doing?" 🎯

Integration with Issue Trackers:
─────────────────────────────────────────────
Tools → Tasks & Contexts → Configure Servers
→ Add: GitHub, JIRA, YouTrack, etc.
→ Tasks synced automatically!

Click issue → Opens task with context!

═══════════════════════════════════════════════════════════

8. SPEED SEARCH ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Filter any list by typing!

Works in:
• Project view
• File structure
• Settings
• Tool windows
• Action dialogs

Usage:
─────────────────────────────────────────────
1. Focus on list/tree
2. Start typing
3. List filters automatically!

Example:
Project view showing 100 files
Type: "user"
→ Shows only: User.java, UserService.java, UserTest.java

Settings with 1000 options
Type: "font"
→ Shows only font-related settings!

No clicking through menus! ⚡

═══════════════════════════════════════════════════════════

9. EMMET / ZEN CODING ⭐⭐⭐⭐⭐ (HTML/CSS)
───────────────────────────────────────────
Write HTML/CSS super fast!

Examples:
─────────────────────────────────────────────
Type: div.container>ul>li*5>a
Tab →
<div class="container">
    <ul>
        <li><a href=""></a></li>
        <li><a href=""></a></li>
        <li><a href=""></a></li>
        <li><a href=""></a></li>
        <li><a href=""></a></li>
    </ul>
</div>

Type: ul.nav>li.nav-item*3>a.nav-link
Tab →
<ul class="nav">
    <li class="nav-item"><a href="" class="nav-link"></a></li>
    <li class="nav-item"><a href="" class="nav-link"></a></li>
    <li class="nav-item"><a href="" class="nav-link"></a></li>
</ul>

Type: form:post>input:email+input:password+button:submit
Tab → Full form!

CSS:
─────────────────────────────────────────────
Type: m10
Tab → margin: 10px;

Type: p20-30
Tab → padding: 20px 30px;

Type: w100p
Tab → width: 100%;

Type: df
Tab → display: flex;

Built-in in WebStorm/Ultimate!

═══════════════════════════════════════════════════════════

10. FILE TEMPLATES ⭐⭐⭐⭐
───────────────────────────────────────────
Custom file templates!

Settings → Editor → File and Code Templates

Customize:
─────────────────────────────────────────────
Files tab → Select template (e.g., Class)

Add header:
/**
 * @author ${USER}
 * @date ${DATE}
 * @project ${PROJECT_NAME}
 */
#parse("File Header.java")

public class ${NAME} {
    $END$
}

Now every new class has this header!

Create Custom Template:
─────────────────────────────────────────────
+ → New template
Name: React Component
Extension: jsx

Template:
import React from 'react';

/**
 * ${NAME} component
 * @author ${USER}
 */
const ${NAME} = () => {
  return (
    <div className="${NAME}">
      $END$
    </div>
  );
};

export default ${NAME};

Usage:
Right-click → New → React Component
→ Name it
→ Template applied!

Variables:
${NAME} → File name
${USER} → Current user
${DATE} → Current date
${TIME} → Current time
${PROJECT_NAME} → Project name
${PACKAGE_NAME} → Package name
```

---

### Debugging Tips 🐛

```bash
# ═══════════════════════════════════════════
# ADVANCED DEBUGGING
# ═══════════════════════════════════════════

1. CONDITIONAL BREAKPOINTS ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Break only when condition is true!

Setup:
─────────────────────────────────────────────
1. Set breakpoint (⌘F8)
2. Right-click breakpoint
3. Enter condition

Examples:

Break when i equals 100:
for (int i = 0; i < 1000; i++) {
    process(i);  // ● Condition: i == 100
}

Break when user is admin:
processUser(user);  // ● Condition: user.isAdmin()

Break when list size exceeds 10:
addItem(item);  // ● Condition: items.size() > 10

Break on specific value:
process(value);  // ● Condition: value.equals("debug")

Saves time! No stepping through 99 iterations! ⚡

═══════════════════════════════════════════════════════════

2. EXCEPTION BREAKPOINTS ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Break when exception is thrown!

Setup:
─────────────────────────────────────────────
Run → View Breakpoints (⌘⇧F8)
→ + → Java Exception Breakpoints
→ Type exception: NullPointerException
→ OK

Now debugger breaks WHENEVER NPE occurs!

Even if no breakpoint set! 🎯

Use cases:
• Debug unexpected exceptions
• Find exception source
• Catch all NullPointerExceptions
• Debug third-party code

Filters:
─────────────────────────────────────────────
Right-click exception breakpoint → More
→ Class filters: Only in my code
→ Instance filters: Specific object
→ Condition: Custom logic

═══════════════════════════════════════════════════════════

3. METHOD BREAKPOINTS ⭐⭐⭐⭐
───────────────────────────────────────────
Break on method entry/exit!

Setup:
─────────────────────────────────────────────
Click on method name line (not inside method body)

Options:
☑ Method entry
☑ Method exit

Shows:
• Parameters on entry
• Return value on exit

Great for:
• Interface methods (unknown implementation)
• Abstract methods
• Overridden methods
• Library methods

═══════════════════════════════════════════════════════════

4. FIELD WATCHPOINTS ⭐⭐⭐⭐
───────────────────────────────────────────
Break when field value changes!

Setup:
─────────────────────────────────────────────
Click on field declaration line

private String status;  // ● Watchpoint

Options:
☑ Field access
☑ Field modification

Breaks whenever:
• Field is read (access)
• Field is modified (write)

Shows:
• Old value
• New value
• Stack trace (who changed it)

Perfect for:
• Tracking state changes
• Finding unexpected modifications
• Debugging race conditions

═══════════════════════════════════════════════════════════

5. EVALUATE EXPRESSION (⌥F8) ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Execute code while debugging!

While paused at breakpoint:
─────────────────────────────────────────────
Press ⌥F8 (Alt+F8)

Can execute ANYTHING:
• Call methods: user.getName()
• Create objects: new ArrayList<>()
• Complex expressions: users.stream().filter(...)
• Modify state: user.setAge(25)

Examples:

Check value:
user.isActive()
→ See result: true

Try different logic:
items.stream()
    .filter(i -> i.getPrice() > 100)
    .collect(Collectors.toList())
→ See filtered list

Modify for testing:
user.setStatus("ADMIN")
→ Continue with modified state

Call private methods:
// Works! Can call private methods while debugging!

Even execute SQL queries! 🤯

═══════════════════════════════════════════════════════════

6. DROP FRAME (TIME TRAVEL!) ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Go back in time while debugging!

While debugging:
─────────────────────────────────────────────
Frames panel → Right-click frame → Drop Frame

Rewinds to beginning of method!

Example:
public void process(int value) {
    value = value * 2;      // Step 1
    value = value + 10;     // Step 2 ← Currently here
    System.out.println(value); // Step 3
}

Drop Frame → Back to beginning!
Can re-execute method with different values!

⚡ Use Cases:
• Test different values
• Re-run method
• Fix logic and retry
• Skip unwanted execution

⚠️ Limitations:
• Can't undo external changes (DB, files, network)
• Can't go before method entry

But still AMAZING! 🎯

═══════════════════════════════════════════════════════════

7. SMART STEP INTO (⇧F7) ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Choose which method to step into!

Problem:
result = service.process(dao.getUser(repo.find(id)));

Regular F7 → Steps into first method (repo.find)

Smart Step Into (⇧F7):
─────────────────────────────────────────────
Shows menu:
1. repo.find(id)
2. dao.getUser(...)
3. service.process(...)

Choose the one you care about! 🎯

Saves time! No stepping through 10 methods!

═══════════════════════════════════════════════════════════

8. RUN TO CURSOR (⌥F9) ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Temporary breakpoint!

Usage:
─────────────────────────────────────────────
1. Place cursor on line you want to reach
2. ⌥F9 (Alt+F9)
3. Execution runs until that line

Faster than:
• Setting breakpoint
• Running
• Removing breakpoint

One shortcut! ⚡

═══════════════════════════════════════════════════════════

9. FORCE RETURN (⌥⌘R) ⭐⭐⭐⭐
───────────────────────────────────────────
Force method to return value!

While debugging in method:
─────────────────────────────────────────────
⌥⌘R (Ctrl+Shift+F8) → Force Return

Specify return value:
→ Enter value
→ Method returns immediately!

Example:
public boolean isValid() {
    // Complex validation logic...
    return result;
}

Debugging → Force Return → true
Method returns true without executing rest!

Use cases:
• Test different return values
• Skip slow code
• Bypass validation for testing

═══════════════════════════════════════════════════════════

10. BREAKPOINT GROUPS ⭐⭐⭐⭐
───────────────────────────────────────────
Organize breakpoints!

View Breakpoints (⌘⇧F8):
─────────────────────────────────────────────
Right-click breakpoint → Move to group

Create groups:
• "Feature A"
• "Bug #123"
• "Performance"

Enable/disable entire groups!

═══════════════════════════════════════════════════════════

11. OBJECT MARKING ⭐⭐⭐⭐
───────────────────────────────────────────
Mark object instances!

While debugging:
─────────────────────────────────────────────
Variables panel → Right-click object → Mark Object

Give it label: "User 1"

Now in Variables panel:
user: User@123 "User 1"  // Your label!

Track specific instances through execution!

═══════════════════════════════════════════════════════════

12. STREAM DEBUGGER ⭐⭐⭐⭐⭐ (JAVA)
───────────────────────────────────────────
Debug Java Streams visually!

Code:
list.stream()
    .filter(x -> x > 10)
    .map(x -> x * 2)
    .collect(Collectors.toList());

Set breakpoint → Debug

"Trace Current Stream Chain" button appears!

Click → Visual representation:
┌─────────────────────────────────────┐
│ Stream Operations                   │
├─────────────────────────────────────┤
│ source: [1, 5, 15, 20, 25]         │
│    ↓                                │
│ filter: [15, 20, 25]               │
│    ↓                                │
│ map: [30, 40, 50]                  │
│    ↓                                │
│ collect: [30, 40, 50]              │
└─────────────────────────────────────┘

See data flow through stream! 🎯

═══════════════════════════════════════════════════════════

13. MEMORY VIEW ⭐⭐⭐⭐
───────────────────────────────────────────
See object instances!

While debugging:
─────────────────────────────────────────────
Debugger → Memory View tab

Shows:
┌────────────────────────────────────────┐
│ Class           │ Count  │ Size        │
├─────────────────┼────────┼─────────────┤
│ String          │ 1,247  │ 125.6 KB    │
│ ArrayList       │ 423    │ 45.2 KB     │
│ User            │ 156    │ 12.3 KB     │
└────────────────────────────────────────┘

Right-click → Show Instances
→ See all instances of class!

Find memory leaks! 🔍

═══════════════════════════════════════════════════════════

14. REMOTE DEBUGGING ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Debug application running elsewhere!

Setup Remote JVM:
─────────────────────────────────────────────
java -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=*:5005 -jar myapp.jar

IntelliJ Configuration:
─────────────────────────────────────────────
Run → Edit Configurations → + → Remote JVM Debug

Host: localhost (or remote host)
Port: 5005

Debugger Command Line:
-agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=*:5005

Start debugging → Connects to remote JVM!

Use cases:
• Debug server applications
• Debug in Docker containers
• Debug on staging/production (carefully!)
• Debug embedded systems

═══════════════════════════════════════════════════════════

15. ASYNC STACK TRACES ⭐⭐⭐⭐
───────────────────────────────────────────
See full async call chain!

For async code (CompletableFuture, reactive):
─────────────────────────────────────────────
Settings → Build, Execution, Deployment → Debugger → Async Stack Traces
☑ Instrument CompletableFuture

Now debugger shows:
• Where CompletableFuture was created
• Full chain of .then() calls
• Original caller

No more "lost in async land"! 🎯
```

---

<div align="center">

## 🐛 Troubleshooting

_Common issues and solutions_ 🔧

</div>

### Common Problems & Solutions

```bash
# ═══════════════════════════════════════════
# PERFORMANCE ISSUES
# ═══════════════════════════════════════════

PROBLEM 1: IDE IS SLOW/LAGGY
───────────────────────────────────────────
Symptoms:
• Typing lag
• Slow code completion
• High CPU usage
• Freezing

Solutions:

1. INCREASE MEMORY
─────────────────────────────────────────────
Help → Edit Custom VM Options

Add/modify:
-Xms1024m
-Xmx4096m
-XX:ReservedCodeCacheSize=512m

Restart IDE

2. DISABLE UNUSED PLUGINS
─────────────────────────────────────────────
Settings → Plugins → Installed

Disable plugins you don't use:
☐ Android (if not Android dev)
☐ Kubernetes (if not using)
☐ Docker (if not using)
☐ SVN, Mercurial (if only Git)

Each disabled plugin = faster! ⚡

3. EXCLUDE DIRECTORIES
─────────────────────────────────────────────
Right-click folder → Mark Directory as → Excluded

Exclude:
• node_modules (HUGE!)
• .git
• build/
• dist/
• target/
• venv/
• __pycache__/

Major performance boost! 🚀

4. INVALIDATE CACHES
─────────────────────────────────────────────
File → Invalidate Caches → Invalidate and Restart

Fixes corrupted caches causing slowness

5. CHECK ANTIVIRUS
─────────────────────────────────────────────
Add IntelliJ directories to exclusions:
• Installation directory
• System directory (~/.IntelliJIdea*)
• Project directory

6. POWER SAVE MODE
─────────────────────────────────────────────
File → Power Save Mode

Disables:
• Code inspection
• Auto-completion
• Background indexing

Use when battery low or just viewing code

7. REDUCE CODE INSPECTIONS
─────────────────────────────────────────────
Settings → Editor → Inspections

Disable heavy inspections:
☐ Spelling (if too slow)
☐ JSDoc validation
☐ Unused symbols in large projects

8. OPTIMIZE INDEXING
─────────────────────────────────────────────
Help → Diagnostic Tools → Optimize Shared Indexes

Let indexing complete ONCE!
Don't interrupt it!

9. CHECK ACTIVITY MONITOR
─────────────────────────────────────────────
Help → Diagnostic Tools → Activity Monitor

Shows:
• CPU usage
• Memory usage
• Slow operations
• Plugin overhead

Identify bottlenecks!

10. UPGRADE HARDWARE
─────────────────────────────────────────────
Minimum for good experience:
• 8GB RAM (16GB recommended)
• SSD (not HDD!)
• Multi-core CPU

IntelliJ is resource-intensive!

═══════════════════════════════════════════════════════════

PROBLEM 2: INDEXING TAKES FOREVER
───────────────────────────────────────────
Symptoms:
• "Indexing..." for 30+ minutes
• Can't use IDE features

Solutions:

1. EXCLUDE BUILD DIRECTORIES
─────────────────────────────────────────────
node_modules/
build/
dist/
.git/
venv/

2. INCREASE INDEXING MEMORY
─────────────────────────────────────────────
Help → Edit Custom VM Options
-XX:SoftRefLRUPolicyMSPerMB=50

3. WAIT FOR COMPLETION
─────────────────────────────────────────────
Let it finish ONCE!
Subsequent indexing will be incremental (fast)

4. SHARED INDEXES (2023.2+)
─────────────────────────────────────────────
Settings → Tools → Shared Indexes
☑ Download automatically

Pre-built indexes for libraries!

═══════════════════════════════════════════════════════════

PROBLEM 3: OUT OF MEMORY ERRORS
───────────────────────────────────────────
Symptoms:
• "OutOfMemoryError" popup
• IDE crashes
• "GC overhead limit exceeded"

Solutions:

1. INCREASE HEAP SIZE
─────────────────────────────────────────────
Help → Edit Custom VM Options
-Xmx8192m  (8GB for large projects)

2. INCREASE METASPACE
─────────────────────────────────────────────
-XX:MetaspaceSize=512m
-XX:MaxMetaspaceSize=1024m

3. USE G1GC
─────────────────────────────────────────────
-XX:+UseG1GC
-XX:MaxGCPauseMillis=200

Better garbage collection!

4. ANALYZE MEMORY SNAPSHOT
─────────────────────────────────────────────
Help → Diagnostic Tools → Analyze Memory Snapshot

Shows what's using memory

5. CLOSE UNUSED PROJECTS
─────────────────────────────────────────────
File → Close Project

Only keep current project open

═══════════════════════════════════════════════════════════

PROBLEM 4: GRADLE/MAVEN SYNC FAILS
───────────────────────────────────────────
Symptoms:
• "Sync failed" error
• Dependencies not resolved
• Red imports

Solutions:

1. REFRESH GRADLE/MAVEN
─────────────────────────────────────────────
View → Tool Windows → Gradle
Click 🔄 (Refresh)

Or:
View → Tool Windows → Maven
Click 🔄 (Reimport)

2. CLEAR CACHE
─────────────────────────────────────────────
# Gradle:
./gradlew clean build --refresh-dependencies

# Maven:
mvn clean install -U

3. DELETE .IDEA FOLDER
─────────────────────────────────────────────
1. Close project
2. Delete .idea/ folder
3. Delete *.iml files
4. Reopen project
5. Reimport

Fresh start! ✨

4. CHECK BUILD TOOL VERSION
─────────────────────────────────────────────
Settings → Build Tools → Gradle/Maven
→ Use Gradle/Maven from: gradle-wrapper.properties

5. OFFLINE MODE
─────────────────────────────────────────────
If network issues:
Gradle tool window → Toggle Offline Mode

6. CHECK PROXY SETTINGS
─────────────────────────────────────────────
Settings → Appearance & Behavior → System Settings → HTTP Proxy

Configure if behind corporate proxy

═══════════════════════════════════════════════════════════

PROBLEM 5: GIT OPERATIONS FAIL
───────────────────────────────────────────
Symptoms:
• "Cannot pull"
• "Authentication failed"
• "Cannot push"

Solutions:

1. CHECK GIT CONFIGURATION
─────────────────────────────────────────────
Settings → Version Control → Git

Test Git executable:
Click "Test" button

Should show: Git version X.Y.Z

2. SSH KEY ISSUES
─────────────────────────────────────────────
# Generate SSH key:
ssh-keygen -t ed25519 -C "your_email@example.com"

# Add to ssh-agent:
ssh-add ~/.ssh/id_ed25519

# Add public key to GitHub/GitLab:
cat ~/.ssh/id_ed25519.pub
# Copy and add to GitHub → Settings → SSH Keys

3. CREDENTIAL HELPER
─────────────────────────────────────────────
# macOS:
git config --global credential.helper osxkeychain

# Windows:
git config --global credential.helper wincred

# Linux:
git config --global credential.helper cache

4. RESET GIT CONFIGURATION
─────────────────────────────────────────────
VCS → Git → Reset Git Configuration

5. CHECK REMOTE URL
─────────────────────────────────────────────
# In terminal:
git remote -v

# If HTTPS but want SSH:
git remote set-url origin git@github.com:user/repo.git

6. AUTHENTICATION FAILURE
─────────────────────────────────────────────
Settings → Appearance & Behavior → System Settings → Passwords

Clear saved passwords
Re-authenticate

═══════════════════════════════════════════════════════════

PROBLEM 6: CODE COMPLETION NOT WORKING
───────────────────────────────────────────
Symptoms:
• No suggestions
• Empty completion popup
• Missing imports

Solutions:

1. WAIT FOR INDEXING
─────────────────────────────────────────────
Check bottom right corner
Wait for indexing to complete

2. INVALIDATE CACHES
─────────────────────────────────────────────
File → Invalidate Caches → Invalidate and Restart

3. POWER SAVE MODE OFF
─────────────────────────────────────────────
File → Power Save Mode (make sure NOT checked)

4. CHECK COMPLETION SETTINGS
─────────────────────────────────────────────
Settings → Editor → General → Code Completion
☑ Show suggestions as you type
☑ Insert selected variant by typing

5. REBUILD PROJECT
─────────────────────────────────────────────
Build → Rebuild Project

6. CHECK FILE ENCODING
─────────────────────────────────────────────
Bottom right → File encoding
Should be UTF-8

═══════════════════════════════════════════════════════════

PROBLEM 7: DEBUGGER NOT STOPPING AT BREAKPOINTS
───────────────────────────────────────────
Symptoms:
• Breakpoints ignored
• Debug mode runs through code

Solutions:

1. CHECK BREAKPOINT IS ENABLED
─────────────────────────────────────────────
Red dot = enabled ●
Gray dot = disabled ○

Click to toggle

2. CHECK DEBUG MODE
─────────────────────────────────────────────
Running with Run (▶) won't stop at breakpoints
Must use Debug (🐛)

3. MUTED BREAKPOINTS
─────────────────────────────────────────────
Click 🔇 icon in debugger
→ Unmute Breakpoints

4. CHECK CONDITIONS
─────────────────────────────────────────────
Right-click breakpoint → Remove condition
Maybe condition never true

5. CHECK SUSPEND POLICY
─────────────────────────────────────────────
Right-click breakpoint
☑ Suspend: Thread (not None)

6. SOURCE CODE MISMATCH
─────────────────────────────────────────────
Running old compiled code!

Build → Rebuild Project
Run again

7. OPTIMIZATION
─────────────────────────────────────────────
In production builds, code may be optimized away

Run in debug configuration!

═══════════════════════════════════════════════════════════

PROBLEM 8: CANNOT FIND MAIN CLASS
───────────────────────────────────────────
Error: "Error: Could not find or load main class"

Solutions:

1. REBUILD PROJECT
─────────────────────────────────────────────
Build → Rebuild Project

2. MARK DIRECTORY AS SOURCES ROOT
─────────────────────────────────────────────
Right-click src/ → Mark Directory as → Sources Root

3. CHECK MODULE CONFIGURATION
─────────────────────────────────────────────
File → Project Structure → Modules
→ Check Sources folders
→ Check output path

4. INVALIDATE CACHES
─────────────────────────────────────────────
File → Invalidate Caches → Invalidate and Restart

5. DELETE OUT/BUILD FOLDER
─────────────────────────────────────────────
Delete:
• out/
• build/
• target/

Rebuild!

6. CHECK RUN CONFIGURATION
─────────────────────────────────────────────
Run → Edit Configurations
→ Main class: Verify correct
→ Working directory: Check path

═══════════════════════════════════════════════════════════

PROBLEM 9: PLUGINS NOT WORKING
───────────────────────────────────────────
Symptoms:
• Plugin installed but features missing
• Plugin errors

Solutions:

1. RESTART IDE
─────────────────────────────────────────────
Most plugins require restart!

2. CHECK PLUGIN COMPATIBILITY
─────────────────────────────────────────────
Settings → Plugins → Installed
→ Check plugin version
→ Must match IDE version

3. UPDATE PLUGIN
─────────────────────────────────────────────
Settings → Plugins → Updates tab
→ Update All

4. REINSTALL PLUGIN
─────────────────────────────────────────────
1. Uninstall plugin
2. Restart IDE
3. Reinstall plugin
4. Restart IDE

5. CHECK PLUGIN CONFLICTS
─────────────────────────────────────────────
Two plugins might conflict
Try disabling one

6. CHECK LOGS
─────────────────────────────────────────────
Help → Show Log in Finder/Explorer
→ Check idea.log for errors

═══════════════════════════════════════════════════════════

PROBLEM 10: HIGH CPU USAGE
───────────────────────────────────────────
Symptoms:
• Fan running loud
• Laptop hot
• Battery draining fast

Solutions:

1. CHECK ACTIVITY MONITOR
─────────────────────────────────────────────
Help → Diagnostic Tools → Activity Monitor

Identify what's using CPU

2. WAIT FOR INDEXING
─────────────────────────────────────────────
Indexing uses lots of CPU
Wait for completion

3. DISABLE CODE ANALYSIS
─────────────────────────────────────────────
Settings → Editor → Inspections
→ Disable heavy inspections

4. POWER SAVE MODE
─────────────────────────────────────────────
File → Power Save Mode

5. CLOSE UNUSED TOOL WINDOWS
─────────────────────────────────────────────
Close windows you're not using:
• Terminal
• Database
• Docker
• etc.

6. CHECK FOR INFINITE LOOPS
─────────────────────────────────────────────
In debugger/running code
Bug might be causing CPU spike

7. RESTART IDE
─────────────────────────────────────────────
Fresh start often helps

═══════════════════════════════════════════════════════════

PROBLEM 11: CANNOT OPEN PROJECT
───────────────────────────────────────────
Error: "Cannot load project" or crashes on open

Solutions:

1. DELETE .IDEA FOLDER
─────────────────────────────────────────────
1. Navigate to project folder
2. Delete .idea/ directory
3. Delete *.iml files
4. Open in IntelliJ
5. Reconfigure

2. OPEN AS NEW PROJECT
─────────────────────────────────────────────
File → Open → Select build.gradle or pom.xml
→ "Open as Project"

3. CHECK IDE VERSION
─────────────────────────────────────────────
Project might be created with newer IDE version
Update IntelliJ!

4. CHECK DISK SPACE
─────────────────────────────────────────────
Need at least 1GB free space

5. CHECK PERMISSIONS
─────────────────────────────────────────────
# Unix/macOS:
chmod -R 755 project-directory

6. IMPORT PROJECT
─────────────────────────────────────────────
File → New → Project from Existing Sources
→ Select project folder
→ Import

═══════════════════════════════════════════════════════════

PROBLEM 12: TERMINAL NOT WORKING
───────────────────────────────────────────
Symptoms:
• Terminal won't open
• Terminal crashes
• Wrong shell

Solutions:

1. CHECK SHELL PATH
─────────────────────────────────────────────
Settings → Tools → Terminal
Shell path: /bin/zsh (or /bin/bash)

Verify path exists:
which zsh
which bash

2. RESET TERMINAL
─────────────────────────────────────────────
Right-click Terminal tab → Close
Reopen: View → Tool Windows → Terminal

3. CHECK ENVIRONMENT VARIABLES
─────────────────────────────────────────────
Settings → Tools → Terminal
→ Environment variables

Remove problematic variables

4. USE SYSTEM TERMINAL
─────────────────────────────────────────────
Instead of built-in terminal:
Tools → Terminal → Open in Terminal
Opens external terminal app

═══════════════════════════════════════════════════════════

PROBLEM 13: JAVA_HOME NOT SET
───────────────────────────────────────────
Error: "JAVA_HOME is not set"

Solutions:

1. SET IN INTELLIJ
─────────────────────────────────────────────
File → Project Structure → Project
→ Project SDK: Select JDK

Settings → Build, Execution, Deployment → Build Tools → Gradle
→ Gradle JVM: Select JDK

2. SET SYSTEM VARIABLE
─────────────────────────────────────────────
# macOS/Linux:
export JAVA_HOME=$(/usr/libexec/java_home)

# Add to ~/.zshrc or ~/.bashrc:
echo 'export JAVA_HOME=$(/usr/libexec/java_home)' >> ~/.zshrc

# Windows:
# System Properties → Environment Variables
# Add: JAVA_HOME = C:\Program Files\Java\jdk-17

3. DOWNLOAD JDK
─────────────────────────────────────────────
File → Project Structure → Platform Settings → SDKs
→ + → Download JDK
→ Choose version (17 or 21 recommended)

═══════════════════════════════════════════════════════════

PROBLEM 14: CANNOT INSTALL PLUGIN
───────────────────────────────────────────
Error: "Plugin installation failed"

Solutions:

1. CHECK INTERNET CONNECTION
─────────────────────────────────────────────
Test: Settings → Plugins → Marketplace

2. CHECK PROXY SETTINGS
─────────────────────────────────────────────
Settings → Appearance & Behavior → System Settings → HTTP Proxy

3. DOWNLOAD MANUALLY
─────────────────────────────────────────────
1. Visit https://plugins.jetbrains.com/
2. Download plugin .zip
3. Settings → Plugins → ⚙️ → Install Plugin from Disk
4. Select .zip file
5. Restart

4. CLEAR PLUGIN CACHE
─────────────────────────────────────────────
File → Invalidate Caches → Clear downloaded plugins cache

5. CHECK IDE VERSION
─────────────────────────────────────────────
Plugin might not support your IDE version
Update IDE!

═══════════════════════════════════════════════════════════

EMERGENCY FIXES
───────────────────────────────────────────

When ALL ELSE FAILS:

NUCLEAR OPTION 1: Delete Configuration
─────────────────────────────────────────────
# macOS:
rm -rf ~/Library/Application\ Support/JetBrains/IntelliJIdea*
rm -rf ~/Library/Caches/JetBrains/IntelliJIdea*
rm -rf ~/Library/Logs/JetBrains/IntelliJIdea*

# Linux:
rm -rf ~/.config/JetBrains/IntelliJIdea*
rm -rf ~/.cache/JetBrains/IntelliJIdea*
rm -rf ~/.local/share/JetBrains/IntelliJIdea*

# Windows:
# Delete:
# %APPDATA%\JetBrains\IntelliJIdea*
# %LOCALAPPDATA%\JetBrains\IntelliJIdea*

⚠️ CAUTION: Loses ALL settings!
Export settings first!

NUCLEAR OPTION 2: Fresh Install
─────────────────────────────────────────────
1. Uninstall IntelliJ completely
2. Delete all config folders (above)
3. Reinstall fresh
4. Import settings if backed up

NUCLEAR OPTION 3: Rollback Version
─────────────────────────────────────────────
Download previous IDE version:
https://www.jetbrains.com/idea/download/other.html

Install older stable version
```

---

<div align="center">

## 🎓 Learning Resources

_Master IntelliJ IDEA_ 📚

</div>

### Official Documentation

```bash
# ═══════════════════════════════════════════
# OFFICIAL RESOURCES
# ═══════════════════════════════════════════

📘 DOCUMENTATION
───────────────────────────────────────────
🔗 IntelliJ IDEA Help
   https://www.jetbrains.com/help/idea/

   Comprehensive official documentation
   • Getting started
   • Features
   • Shortcuts
   • Troubleshooting

🔗 What's New
   https://www.jetbrains.com/idea/whatsnew/

   Latest features in each release

🔗 IntelliJ IDEA Guide
   https://www.jetbrains.com/idea/guide/

   ⭐⭐⭐⭐⭐ EXCELLENT RESOURCE!

   Interactive tutorials:
   • Tips & Tricks
   • Tutorials
   • Playlists
   • Technologies

   Example sections:
   • Getting Started
   • Writing Code
   • Inspecting Code
   • Running & Debugging
   • Testing
   • Version Control
   • Web Development
   • Database

📘 BLOG
───────────────────────────────────────────
🔗 IntelliJ IDEA Blog
   https://blog.jetbrains.com/idea/

   • Feature announcements
   • Tips & tricks
   • Best practices
   • Interviews
   • Releases

   Subscribe to RSS feed!

📺 YOUTUBE
───────────────────────────────────────────
🔗 JetBrains TV
   https://www.youtube.com/@intellijidea

   Official channel with:
   • Feature demos
   • Webinars
   • Conference talks
   • Tips & tricks
   • What's new videos

   Playlists:
   ├─ IntelliJ IDEA Tips & Tricks
   ├─ IntelliJ IDEA Tutorials
   ├─ IntelliJ IDEA Webinars
   ├─ Live Streams
   └─ Conferences

🔗 Recommended Playlists:
   • "IntelliJ IDEA. Tips & Tricks" (Essential!)
   • "IntelliJ IDEA Tutorials for Beginners"
   • "IntelliJ IDEA Full Tutorial Course"

📱 SOCIAL MEDIA
───────────────────────────────────────────
🐦 Twitter: @intellijidea
   Daily tips and updates

💬 Reddit: r/IntelliJIDEA
   Community discussions

💬 Stack Overflow: [intellij-idea]
   Q&A for problems

📧 NEWSLETTER
───────────────────────────────────────────
Subscribe: https://www.jetbrains.com/
→ Weekly/Monthly tips
→ Feature highlights
→ Webinar announcements

🎮 INTERACTIVE LEARNING
───────────────────────────────────────────
🔗 IDE Features Trainer (Built-in!)
   Help → Learn IDE Features

   Interactive lessons:
   • Basic IDE features
   • Code editing
   • Navigation
   • Refactoring
   • Debugging
   • Version control

   Learn by doing! ⭐⭐⭐⭐⭐

🔗 JetBrains Academy
   https://www.jetbrains.com/academy/

   Free courses:
   • Introduction to Python
   • Java for Beginners
   • Kotlin Basics

   Uses IntelliJ IDE!

📚 KEYBOARD SHORTCUTS REFERENCE
───────────────────────────────────────────
🔗 Printable PDF
   Help → Keyboard Shortcuts PDF

   Or download:
   macOS: https://resources.jetbrains.com/storage/products/intellij-idea/docs/IntelliJIDEA_ReferenceCard.pdf
   Windows/Linux: Available in Help menu

🔗 Interactive Keymap
   https://www.jetbrains.com/help/idea/mastering-keyboard-shortcuts.html

🔗 Custom Keymap Export
   Settings → Keymap → ⚙️ → Export to PDF

   Print and hang on wall! 📋
```

---

### Video Courses

```bash
# ═══════════════════════════════════════════
# RECOMMENDED VIDEO COURSES
# ═══════════════════════════════════════════

FREE COURSES
───────────────────────────────────────────
🎥 "IntelliJ IDEA Full Course" - Amigoscode
   YouTube (Free)
   Duration: 2+ hours
   Rating: ⭐⭐⭐⭐⭐

   Covers:
   • Installation
   • Project setup
   • Shortcuts
   • Refactoring
   • Debugging
   • Git integration

   Perfect for beginners!

🎥 "IntelliJ IDEA Tips & Tricks" - JetBrains
   YouTube (Free)
   Collection of short tips
   Rating: ⭐⭐⭐⭐⭐

   5-10 minute videos
   Learn one tip at a time!

🎥 "Mastering IntelliJ IDEA" - JetBrains Webinars
   YouTube (Free)
   Multiple webinar recordings
   Rating: ⭐⭐⭐⭐⭐

   Deep dives into features

PAID COURSES
───────────────────────────────────────────
💰 "IntelliJ IDEA Tricks to Boost Productivity" - Udemy
   Price: $10-50 (on sale)
   Duration: 3-4 hours
   Rating: ⭐⭐⭐⭐

   Worth it on sale!

💰 "Become More Productive With IntelliJ IDEA" - LinkedIn Learning
   Price: LinkedIn Premium ($30/month)
   Duration: 2 hours
   Rating: ⭐⭐⭐⭐

   Professional production quality

💰 Pluralsight Courses
   Multiple IntelliJ courses
   Subscription: $29/month

   • "Getting Started with IntelliJ IDEA"
   • "IntelliJ IDEA Fundamentals"
   • "Advanced IntelliJ IDEA"
```

---

### Books

```bash
# ═══════════════════════════════════════════
# RECOMMENDED BOOKS
# ═══════════════════════════════════════════

📚 "IntelliJ IDEA Essentials" - Jarosław Krochmalski
   Publisher: Packt
   Pages: ~200
   Rating: ⭐⭐⭐⭐

   Good overview of features
   Slightly dated but fundamentals same

📚 "IntelliJ IDEA in Action" (Unofficial User Guide)
   Community-written guide
   Free online

   Comprehensive tips and tricks

📚 "Mastering IntelliJ IDEA" - Multiple Authors
   Various books on Amazon
   Check reviews before buying!

📚 BETTER: Read Framework-Specific Books
───────────────────────────────────────────
Instead of IDE books, learn frameworks:
• "Spring in Action" (uses IntelliJ)
• "Effective Java" (IDE-agnostic but useful)
• "Clean Code" (principles apply to all IDEs)

IDE features learned through practice!
```

---

### Community Resources

```bash
# ═══════════════════════════════════════════
# COMMUNITY & FORUMS
# ═══════════════════════════════════════════

💬 FORUMS
───────────────────────────────────────────
🔗 JetBrains Community Forum
   https://intellij-support.jetbrains.com/

   Official forum
   • Ask questions
   • Report bugs
   • Feature requests
   • Active community

🔗 Stack Overflow [intellij-idea]
   https://stackoverflow.com/questions/tagged/intellij-idea

   100,000+ questions
   Quick answers for problems

🔗 Reddit
   r/IntelliJIDEA - Dedicated subreddit
   r/java - General Java (uses IntelliJ)
   r/Kotlin - Kotlin development

   Active communities

💬 DISCORD/SLACK
───────────────────────────────────────────
🔗 JetBrains Community Discord
   Unofficial but active
   Real-time chat

🔗 Framework-specific channels
   • Spring community
   • Kotlin Slack
   • etc.

📝 BLOGS
───────────────────────────────────────────
🔗 "IntelliJ IDEA Tips" - Trisha Gee
   https://trishagee.com/

   JetBrains Developer Advocate
   Excellent tips!

🔗 Baeldung
   https://www.baeldung.com/

   Java tutorials using IntelliJ

🔗 Vojtěch Ruzicka's Blog
   https://www.vojtechruzicka.com/

   Great IntelliJ tips

🎙️ PODCASTS
───────────────────────────────────────────
🔗 "Talking Kotlin"
   Official JetBrains podcast
   Kotlin-focused but IDE tips included

🔗 "The IntelliJ IDEA Podcast" (Unofficial)
   Various episodes on YouTube

🔗 Framework-specific podcasts
   Often discuss IDE usage

🎮 CHALLENGES & PRACTICE
───────────────────────────────────────────
🔗 JetBrains Academy
   https://www.jetbrains.com/academy/

   Learn by building projects!

🔗 Coding challenges
   • LeetCode (use IntelliJ!)
   • HackerRank
   • Exercism

   Practice shortcuts while solving!

📊 CHEAT SHEETS
───────────────────────────────────────────
🔗 Official Keyboard Shortcuts
   Help → Keyboard Shortcuts PDF

🔗 Community Cheat Sheets
   Search: "IntelliJ IDEA cheat sheet"
   Many visual guides available!

🔗 Create Your Own
   Document shortcuts you use most
   Customize to your workflow

💡 PRODUCTIVITY TIPS ACCOUNTS
───────────────────────────────────────────
Follow for daily tips:

🐦 @mesirii (Trisha Gee) - IntelliJ expert
🐦 @intellijidea - Official account
🐦 @kotlin - Kotlin tips (often IntelliJ)

📺 YouTube Channels Beyond JetBrains:
• Amigoscode
• Java Brains
• Telusko
• Programming with Mosh

Often show IntelliJ in action!
```

---

### Best Learning Path

```bash
# ═══════════════════════════════════════════
# RECOMMENDED LEARNING PATH
# ═══════════════════════════════════════════

WEEK 1: BASICS
───────────────────────────────────────────
Days 1-2: Installation & Setup
• Install IntelliJ IDEA
• Create first project
• Understand project structure
• Configure basic settings

Days 3-4: Navigation
• Master Search Everywhere (⇧⇧)
• Learn Find File (⌘⇧O)
• Practice Go to Class (⌘O)
• Use Recent Files (⌘E)

Days 5-7: Editing
• Duplicate lines (⌘D)
• Comment code (⌘/)
• Multiple cursors (⌥+Click)
• Code completion

🎯 Goal: Navigate and edit without mouse!

WEEK 2: INTERMEDIATE
───────────────────────────────────────────
Days 1-2: Code Generation
• Use ⌘N (Generate)
• Live templates
• Postfix completion

Days 3-4: Refactoring
• Rename (⇧F6)
• Extract method (⌘⌥M)
• Extract variable (⌘⌥V)
• Inline (⌘⌥N)

Days 5-7: Running & Debugging
• Run configurations
• Breakpoints
• Step through code
• Evaluate expressions

🎯 Goal: Refactor confidently, debug efficiently!

WEEK 3: ADVANCED
───────────────────────────────────────────
Days 1-2: Version Control
• Git integration
• Commit (⌘K)
• Push (⌘⇧K)
• Resolve conflicts

Days 3-4: Database Tools
• Connect database
• Write SQL
• View data
• Query execution

Days 5-7: Custom Setup
• Install plugins
• Configure themes
• Create live templates
• Set up external tools

🎯 Goal: Customize IDE to your workflow!

WEEK 4: MASTERY
───────────────────────────────────────────
Days 1-2: Power Features
• Structural search & replace
• Macros
• Tasks & contexts
• Scratches

Days 3-4: Productivity Hacks
• Keyboard-only workflow
• Custom shortcuts
• Optimize settings
• Speed search

Days 5-7: Real Project
• Apply everything learned
• Build complete project
• Only use keyboard
• Time yourself!

🎯 Goal: Professional-level efficiency!

ONGOING: CONTINUOUS IMPROVEMENT
───────────────────────────────────────────
• Learn 1 new shortcut per day
• Watch IntelliJ tips videos
• Read blog posts
• Share tips with team
• Teach others (best way to learn!)

═══════════════════════════════════════════════════════════

PRACTICE EXERCISES
───────────────────────────────────────────

Exercise 1: 10-Minute Challenge
─────────────────────────────────────────────
Create new class WITHOUT using mouse:
1. Create project (keyboard only)
2. Create package
3. Create class
4. Generate main method
5. Write println
6. Run program

Goal: < 1 minute ⚡

Exercise 2: Refactoring Challenge
─────────────────────────────────────────────
Given messy code, refactor using shortcuts:
• Rename variables
• Extract methods
• Optimize imports
• Format code

Goal: Clean code in 5 minutes!

Exercise 3: Navigation Challenge
─────────────────────────────────────────────
Large codebase (e.g., Spring Pet Clinic):
1. Find specific method
2. Find usages
3. Navigate to implementation
4. View hierarchy

Goal: < 30 seconds per task!

Exercise 4: Debugging Challenge
─────────────────────────────────────────────
Given buggy code:
1. Set breakpoints
2. Debug
3. Evaluate expressions
4. Fix bug
5. Verify

Goal: Keyboard only!

═══════════════════════════════════════════════════════════

CERTIFICATION (Unofficial)
───────────────────────────────────────────

No official IntelliJ certification, but:

✓ Complete JetBrains Academy courses
✓ Contribute to open source (shows proficiency)
✓ Write blog posts about IntelliJ tips
✓ Create video tutorials
✓ Help others in forums

Build portfolio demonstrating expertise!

═══════════════════════════════════════════════════════════

MEASURING PROGRESS
───────────────────────────────────────────

Track your improvement:

📊 Metrics:
• Mouse usage (try to reduce!)
• Time to complete tasks
• Number of shortcuts memorized
• Code written per hour

📈 Tools:
• Key Promoter X (shows mouse usage)
• Time tracking apps
• Productivity journal

🎯 Milestones:
• ☐ 1 day without mouse
• ☐ Create project in < 1 minute
• ☐ Navigate large codebase efficiently
• ☐ Debug complex issue quickly
• ☐ Teach IntelliJ to colleague

Keep learning! 🚀
```

---

<div align="center">

## 🎯 Final Pro Tips

_The 10 Commandments of IntelliJ IDEA_ 📜

</div>

### Master These First

```bash
# ═══════════════════════════════════════════
# THE 10 COMMANDMENTS
# ═══════════════════════════════════════════

1. THOU SHALT LEARN SEARCH EVERYWHERE (⇧⇧) ⭐⭐⭐⭐⭐
───────────────────────────────────────────
This is THE most important shortcut!

⇧⇧ → Type anything → Enter

Searches:
• Files
• Classes
• Actions
• Settings
• Symbols

Master this = 50% faster! 🚀

═══════════════════════════════════════════════════════════

2. THOU SHALT USE RECENT FILES (⌘E) ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Faster than project tree navigation!

⌘E → Select file → Enter

⌘⇧E → Recent locations (even better!)

Stop clicking through folders!

═══════════════════════════════════════════════════════════

3. THOU SHALT REFACTOR WITH SHORTCUTS ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Never manual find-and-replace!

⇧F6 → Rename (safest rename ever!)
⌘⌥M → Extract Method
⌘⌥V → Extract Variable

Let IDE handle renames across entire project!

═══════════════════════════════════════════════════════════

4. THOU SHALT ENABLE AUTOSAVE ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Settings → System Settings
☑ Autosave files if application is idle

Never lose work again! 💾

No more Ctrl+S paranoia!

═══════════════════════════════════════════════════════════

5. THOU SHALT USE SCRATCHES ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Quick experiments without cluttering project!

⌘⇧N → New Scratch

Perfect for:
• Testing code snippets
• SQL queries
• HTTP requests
• JSON parsing

═══════════════════════════════════════════════════════════

6. THOU SHALT MASTER DEBUGGING ⭐⭐⭐⭐⭐
───────────────────────────────────────────
More powerful than println!

⌘F8 → Breakpoint
⌃D → Debug
⌥F8 → Evaluate expression
F7/F8 → Step into/over

Debug, don't guess! 🐛

═══════════════════════════════════════════════════════════

7. THOU SHALT CUSTOMIZE KEYMAP ⭐⭐⭐⭐
───────────────────────────────────────────
Make shortcuts intuitive for YOU!

Settings → Keymap → Duplicate
→ Customize

Common customizations:
• Terminal: ⌃` (like VS Code)
• Format: ⌘⇧F (like VS Code)
• Search: ⌘P (if prefer)

Your IDE, your shortcuts!

═══════════════════════════════════════════════════════════

8. THOU SHALT INSTALL FEWER PLUGINS ⭐⭐⭐⭐
───────────────────────────────────────────
Quality over quantity!

Essential plugins only:
• Key Promoter X ✅
• Rainbow Brackets ✅
• GitHub Copilot (if needed) ✅

Each plugin = slower IDE
Disable unused plugins!

═══════════════════════════════════════════════════════════

9. THOU SHALT USE LOCAL HISTORY ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Your safety net! 🛡️

Right-click file → Local History → Show History

Tracks:
• Every save
• Every refactoring
• Even deleted files!

Has saved me countless times!

═══════════════════════════════════════════════════════════

10. THOU SHALT PRACTICE KEYBOARD SHORTCUTS ⭐⭐⭐⭐⭐
───────────────────────────────────────────
Speed = Productivity ⚡

Challenge: Code 1 day without mouse!

Install Key Promoter X
→ Learn shortcuts as you work

Goal: < 10% mouse usage!

═══════════════════════════════════════════════════════════

BONUS COMMANDMENTS
───────────────────────────────────────────

11. THOU SHALT VERSION CONTROL EVERYTHING
    • Commit often (⌘K)
    • Write good messages
    • Push regularly (⌘⇧K)

12. THOU SHALT READ ERROR MESSAGES
    • Don't panic!
    • Read carefully
    • Click links in errors
    • Use ⌥↩ for quick fixes

13. THOU SHALT INCREASE MEMORY
    • 4GB minimum for IDE
    • 8GB for large projects
    • Help → Edit Custom VM Options

14. THOU SHALT EXCLUDE BUILD FOLDERS
    • node_modules/ ❌
    • build/ ❌
    • .git/ ❌
    • Faster indexing!

15. THOU SHALT SHARE KNOWLEDGE
    • Teach teammates
    • Write tips
    • Pair program
    • Teaching solidifies learning!

═══════════════════════════════════════════════════════════

THE ULTIMATE GOAL
───────────────────────────────────────────

IDE should feel like extension of your thoughts! 🧠✨

When you think "rename", fingers type ⇧F6
When you think "find", fingers type ⇧⇧
When you think "debug", fingers type ⌃D

Muscle memory = Flow state = Productivity! 🚀

═══════════════════════════════════════════════════════════

PRODUCTIVITY STATISTICS
───────────────────────────────────────────

Help → Productivity Guide

Shows:
• Features you use most
• Shortcuts usage
• Time saved
• Potential improvements

Check monthly!
Track improvement! 📈

═══════════════════════════════════════════════════════════

ONE LAST THING... 🎁
───────────────────────────────────────────

Set aside 10 minutes DAILY:
• Learn 1 new shortcut
• Try 1 new feature
• Read 1 tip

10 minutes × 365 days = Master level! 🎓

═══════════════════════════════════════════════════════════

REMEMBER:
"The best IDE is the one you know well!"

IntelliJ is powerful, but only if you use it properly!

Now go forth and code efficiently! 💻⚡

═══════════════════════════════════════════════════════════
```

---

## 🆚 Edition Comparison

<div align="center">

### Community vs Ultimate 💎

| Feature                         | Community (Free) | Ultimate (Paid) |
| ------------------------------- | ---------------- | --------------- |
| **Java, Kotlin, Groovy, Scala** | ✅               | ✅              |
| **Android Development**         | ✅               | ✅              |
| **Maven, Gradle, SBT**          | ✅               | ✅              |
| **Git, SVN, Mercurial**         | ✅               | ✅              |
| **JUnit, TestNG**               | ✅               | ✅              |
| **Debugger**                    | ✅               | ✅              |
| **Code Completion**             | ✅               | ✅              |
| **Refactoring**                 | ✅               | ✅              |
| **Web Development (JS/TS)**     | ❌               | ✅              |
| **Spring Framework**            | ❌               | ✅              |
| **Database Tools**              | ❌               | ✅              |
| **HTTP Client**                 | ❌               | ✅              |
| **Docker, Kubernetes**          | ❌               | ✅              |
| **Remote Development**          | ❌               | ✅              |
| **Profiler**                    | ❌               | ✅              |
| **Duplicates Detection**        | ❌               | ✅              |
| **Deployment**                  | ❌               | ✅              |
| **Micronaut, Quarkus**          | ❌               | ✅              |
| **Jakarta EE**                  | ❌               | ✅              |
| **Endpoints**                   | ❌               | ✅              |

</div>

```bash
# ═══════════════════════════════════════════
# PRICING
# ═══════════════════════════════════════════

ULTIMATE EDITION:
─────────────────────────────────────────────
Individual:
• Year 1: $149/year
• Year 2: $119/year
• Year 3+: $89/year

Pricing decreases with continuity! 🎉

Organizations:
• Year 1: $499/year
• Year 2: $399/year
• Year 3+: $299/year

ALL PRODUCTS PACK:
─────────────────────────────────────────────
• All JetBrains IDEs
• Individual: $249/year (first year)
• Best value if use multiple IDEs!

FREE LICENSES:
─────────────────────────────────────────────
✅ Students (with .edu email)
✅ Teachers
✅ Open source contributors
✅ Bootcamps & Training programs

Apply: https://www.jetbrains.com/community/education/

COMMUNITY EDITION:
─────────────────────────────────────────────
FREE forever! ✅

Perfect for:
• Java/Kotlin pure development
• Android development
• Learning
• Open source projects

═══════════════════════════════════════════════════════════

WHICH TO CHOOSE?
───────────────────────────────────────────

CHOOSE COMMUNITY IF:
• Only Java/Kotlin/Android
• No web development
• Don't need database tools
• Don't need Spring support
• Budget-conscious

CHOOSE ULTIMATE IF:
• Professional development
• Full-stack (backend + frontend)
• Spring/Jakarta EE
• Database work
• Docker/Kubernetes
• Worth the investment! 🎯

RECOMMENDATION:
Try Ultimate free for 30 days!
Then decide if features worth cost.

For most professionals: WORTH IT! ⭐⭐⭐⭐⭐
```

---

<div align="center">

## 🎉 Conclusion

**Congratulations!** You now have a comprehensive guide to mastering JetBrains IDEs! 🚀

</div>

### Your Journey Starts Now 🌟

```bash
# ═══════════════════════════════════════════
# NEXT STEPS
# ═══════════════════════════════════════════

1. INSTALL & SETUP
   □ Download IntelliJ IDEA
   □ Configure basic settings
   □ Install essential plugins
   □ Set up themes & fonts

2. LEARN SHORTCUTS (PRIORITY!)
   □ Master ⇧⇧ (Search Everywhere)
   □ Learn ⌘E (Recent Files)
   □ Practice navigation (⌘B, ⌥F7)
   □ Master refactoring (⇧F6, ⌘⌥M)

3. DAILY PRACTICE
   □ Code 10 minutes keyboard-only
   □ Learn 1 new shortcut daily
   □ Watch 1 tip video per week
   □ Read official blog

4. SHARE KNOWLEDGE
   □ Teach teammates
   □ Write tips
   □ Create cheat sheet
   □ Help in forums

═══════════════════════════════════════════════════════════

REMEMBER:
"An IDE is just a tool. The real magic is in your code!" ✨

But a GREAT tool makes you faster, happier, and more productive! 🚀

═══════════════════════════════════════════════════════════

KEEP LEARNING!
• IntelliJ releases new features every 3 months
• Follow @intellijidea on Twitter
• Subscribe to JetBrains Blog
• Join community forums

═══════════════════════════════════════════════════════════

THE JOURNEY FROM BEGINNER TO MASTER:

Beginner:
"How do I find a file?"

Intermediate:
"I know most shortcuts!"

Advanced:
"I can code without mouse!"

Master:
"IDE is extension of my thoughts!"

═══════════════════════════════════════════════════════════

MAY YOUR:
• Builds be green ✅
• Refactorings be safe 🔄
• Merges be conflict-free 🔀
• Code be bug-free 🐛
• Productivity be maximum ⚡

HAPPY CODING WITH INTELLIJ IDEA! 🎉

═══════════════════════════════════════════════════════════
```

---

<div align="center">

**Built with 🧠 by MrDib, for Developers**

_May your IDE always be responsive and your shortcuts muscle memory!_ ⚡

**Now go build amazing things!** 🚀

---

### Quick Reference Card 📋

```
MUST-KNOW SHORTCUTS:

⇧⇧     Search Everywhere (MOST IMPORTANT!)
⌘E     Recent Files
⌘⇧A    Find Action
⌘B     Go to Declaration
⌥F7    Find Usages
⇧F6    Rename
⌘⌥M    Extract Method
⌘K     Commit
⌃D     Debug
⌥↩     Show Intention Actions
⌘/     Comment Line
⌘D     Duplicate Line

Master these = 80% productivity gain! 🎯
```

**Found this guide helpful?**

- ⭐ Star the repo
- 📤 Share with your team
- 💬 Contribute improvements
- 🐛 Report issues

_Happy IntelliJ-ing!_ 💻✨

</div>

---

## 📑 Appendix

### Additional Resources

```bash
# ═══════════════════════════════════════════
# USEFUL LINKS
# ═══════════════════════════════════════════

🔗 Official Website
   https://www.jetbrains.com/idea/

🔗 Download
   https://www.jetbrains.com/idea/download/

🔗 Documentation
   https://www.jetbrains.com/help/idea/

🔗 Issue Tracker
   https://youtrack.jetbrains.com/issues/IDEA

🔗 Plugin Repository
   https://plugins.jetbrains.com/

🔗 Feature Requests
   https://youtrack.jetbrains.com/issues/IDEA?q=Type:%20Feature

🔗 Early Access Program (EAP)
   https://www.jetbrains.com/idea/nextversion/

🔗 Twitter
   https://twitter.com/intellijidea

🔗 YouTube
   https://www.youtube.com/@intellijidea

🔗 Blog
   https://blog.jetbrains.com/idea/

═══════════════════════════════════════════════════════════

VERSIONS:
─────────────────────────────────────────────
• Community Edition: FREE ✅
• Ultimate Edition: PAID 💎
• Educational: FREE (for students) 🎓

SYSTEM REQUIREMENTS:
─────────────────────────────────────────────
Minimum:
• 2 GB RAM
• 2.5 GB disk space
• 1024x768 resolution

Recommended:
• 8 GB RAM
• SSD
• 1920x1080 resolution
• Multi-core processor

═══════════════════════════════════════════════════════════

This guide will be continuously updated! 🔄

Last updated: 2024
Version: 1.0 (Comprehensive Edition)

Feedback? Contributions?
Open an issue or PR on GitHub!
```

---

**THE END** 🎬

**May your code compile, your tests pass, and your IDE never crash!** ✨

---

</div>
