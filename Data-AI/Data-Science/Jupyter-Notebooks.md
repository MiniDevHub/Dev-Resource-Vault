<div align="center">

# 📓 Jupyter Notebooks - Complete Guide

![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=for-the-badge&logo=jupyter)
![Python](https://img.shields.io/badge/Python-Interactive-blue?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-All_Levels-green?style=for-the-badge)

### _Where code meets narrative, and ideas become interactive_ 🚀

**The playground where data scientists create magic** ✨

</div>

---

## 📚 Table of Contents

- [🎯 What is Jupyter?](#-what-is-jupyter)
- [🚀 Installation & Setup](#-installation--setup)
- [📱 Interface & Features](#-interface--features)
- [⌨️ Keyboard Shortcuts](#️-keyboard-shortcuts)
- [🎨 Markdown & Formatting](#-markdown--formatting)
- [🪄 Magic Commands](#-magic-commands)
- [🔧 Extensions & Customization](#-extensions--customization)
- [🔬 JupyterLab](#-jupyterlab)
- [💡 Best Practices](#-best-practices)
- [🚀 Advanced Features](#-advanced-features)
- [🛠️ Workflows](#️-workflows)
- [❓ Troubleshooting](#-troubleshooting)

---

<div align="center">

## 🎯 What is Jupyter?

</div>

### Understanding Jupyter Notebooks 📖

```bash
# ═══════════════════════════════════════════
# JUPYTER OVERVIEW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHAT IS JUPYTER?                         ║
╚════════════════════════════════════════════════════════════╝

Jupyter Notebook: Interactive computing environment
─────────────────────────────────────────────────────────────
• Web-based application
• Mix code, text, and visualizations
• Share and reproduce analysis
• Support 40+ programming languages
• Industry-standard for data science

Origin:
─────────────────────────────────────────────────────────────
• Started as IPython Notebooks (2011)
• Renamed to Jupyter (2014)
• Jupyter = Julia + Python + R
• Now supports many languages

Key Features:
─────────────────────────────────────────────────────────────
✅ Interactive code execution
✅ Rich text formatting (Markdown, LaTeX)
✅ Inline visualizations
✅ Notebook sharing (.ipynb files)
✅ Export to multiple formats (PDF, HTML, slides)
✅ Kernel support for multiple languages
✅ Extensions and customization
✅ Version control friendly

Use Cases:
─────────────────────────────────────────────────────────────
📊 Data exploration and analysis
🤖 Machine learning experimentation
📈 Data visualization
📚 Educational materials
📖 Technical documentation
🔬 Research and reproducibility
📊 Reporting and dashboards

╔════════════════════════════════════════════════════════════╗
║                   JUPYTER ECOSYSTEM                        ║
╚════════════════════════════════════════════════════════════╝

Components:
─────────────────────────────────────────────────────────────

┌────────────────────────────────────────────┐
│  Jupyter Notebook                          │
│  Classic interface, single-document        │
└────────────────────────────────────────────┘
          ↓
┌────────────────────────────────────────────┐
│  JupyterLab                                │
│  Next-gen interface, multi-document        │
└────────────────────────────────────────────┘
          ↓
┌────────────────────────────────────────────┐
│  JupyterHub                                │
│  Multi-user server for teams               │
└────────────────────────────────────────────┘
          ↓
┌────────────────────────────────────────────┐
│  Voilà                                     │
│  Convert notebooks to dashboards           │
└────────────────────────────────────────────┘

Related Tools:
─────────────────────────────────────────────────────────────
• Google Colab (cloud-based)
• Kaggle Notebooks (competition platform)
• Deepnote (collaborative)
• Databricks (enterprise)
• VS Code (with Jupyter extension)

╔════════════════════════════════════════════════════════════╗
║                   JUPYTER vs ALTERNATIVES                  ║
╚════════════════════════════════════════════════════════════╝
```

| Feature           | Jupyter | IDE (PyCharm) | Text Editor | Google Colab |
| ----------------- | ------- | ------------- | ----------- | ------------ |
| **Interactive**   | ✅      | ⚠️            | ❌          | ✅           |
| **Visualization** | ✅      | ⚠️            | ❌          | ✅           |
| **Narrative**     | ✅      | ❌            | ⚠️          | ✅           |
| **Debugging**     | ⚠️      | ✅            | ⚠️          | ⚠️           |
| **Production**    | ❌      | ✅            | ✅          | ❌           |
| **Collaboration** | ⚠️      | ⚠️            | ⚠️          | ✅           |
| **Free GPUs**     | ❌      | ❌            | ❌          | ✅           |
| **Local**         | ✅      | ✅            | ✅          | ❌           |

```bash
When to use Jupyter:
─────────────────────────────────────────────────────────────
✅ Exploratory data analysis
✅ Prototyping and experimentation
✅ Teaching and learning
✅ Data visualization
✅ Presenting results
✅ Documentation with code

When NOT to use Jupyter:
─────────────────────────────────────────────────────────────
❌ Production code
❌ Large-scale applications
❌ Complex software development
❌ When you need advanced debugging
❌ Command-line tools
```

---

<div align="center">

## 🚀 Installation & Setup

</div>

### Getting Started with Jupyter 💻

```bash
# ═══════════════════════════════════════════
# INSTALLATION METHODS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   METHOD 1: PIP (RECOMMENDED)              ║
╚════════════════════════════════════════════════════════════╝

# Install Jupyter Notebook
pip install notebook

# Or install JupyterLab (recommended)
pip install jupyterlab

# Install both
pip install jupyter

# Verify installation
jupyter --version
jupyter notebook --version
jupyter lab --version

╔════════════════════════════════════════════════════════════╗
║                   METHOD 2: CONDA                          ║
╚════════════════════════════════════════════════════════════╝

# Create environment with Jupyter
conda create -n jupyter-env python=3.11 jupyter
conda activate jupyter-env

# Or install in existing environment
conda install jupyter
conda install jupyterlab

╔════════════════════════════════════════════════════════════╗
║                   METHOD 3: ANACONDA (EASIEST)             ║
╚════════════════════════════════════════════════════════════╝

# Download Anaconda from: https://www.anaconda.com/download
# Includes Jupyter, scientific libraries, and IDE

# After installation, Jupyter is ready to use
jupyter notebook
jupyter lab

╔════════════════════════════════════════════════════════════╗
║                   STARTING JUPYTER                         ║
╚════════════════════════════════════════════════════════════╝

# Start Jupyter Notebook (classic interface)
jupyter notebook

# Start JupyterLab (modern interface)
jupyter lab

# Start on specific port
jupyter notebook --port 8889

# Start without opening browser
jupyter notebook --no-browser

# Start in specific directory
cd /path/to/project
jupyter notebook

# Or specify path
jupyter notebook /path/to/project

# Show help
jupyter notebook --help

# List running servers
jupyter notebook list

# Stop server
jupyter notebook stop 8888

╔════════════════════════════════════════════════════════════╗
║                   FIRST-TIME SETUP                         ║
╚════════════════════════════════════════════════════════════╝

# Generate config file
jupyter notebook --generate-config

# Config file location:
# Linux/Mac: ~/.jupyter/jupyter_notebook_config.py
# Windows: C:\Users\USERNAME\.jupyter\jupyter_notebook_config.py

# Common configurations:
─────────────────────────────────────────────────────────────

# Set default directory
c.NotebookApp.notebook_dir = '/path/to/notebooks'

# Disable browser auto-open
c.NotebookApp.open_browser = False

# Set custom port
c.NotebookApp.port = 8889

# Enable password protection
jupyter notebook password

# Set token for access
c.NotebookApp.token = 'your-secret-token'

# Allow remote access (be careful!)
c.NotebookApp.ip = '0.0.0.0'

╔════════════════════════════════════════════════════════════╗
║                   ESSENTIAL PACKAGES                       ║
╚════════════════════════════════════════════════════════════╝

# Install commonly used packages
pip install numpy pandas matplotlib seaborn plotly scikit-learn

# Or all at once
pip install jupyter numpy pandas matplotlib seaborn scipy \
            scikit-learn plotly ipywidgets

# For data science (comprehensive)
pip install jupyter \
            numpy pandas matplotlib seaborn plotly \
            scipy scikit-learn statsmodels \
            ipywidgets tqdm

# Verify packages in Jupyter
import sys
print(sys.executable)  # Python interpreter path

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
print("All imports successful!")
```

---

<div align="center">

## 📱 Interface & Features

</div>

### Mastering the Jupyter Interface 🖥️

```bash
# ═══════════════════════════════════════════
# JUPYTER NOTEBOOK INTERFACE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   INTERFACE OVERVIEW                       ║
╚════════════════════════════════════════════════════════════╝

Dashboard (Home Page):
─────────────────────────────────────────────────────────────
┌────────────────────────────────────────────────────────────┐
│  Jupyter                                    [New ▼]  Upload│
├────────────────────────────────────────────────────────────┤
│  Files  Running  Clusters                                  │
├────────────────────────────────────────────────────────────┤
│  □ Select items to perform actions on them                 │
│                                                             │
│  📁 data/                                   [Modify Date]   │
│  📁 notebooks/                              [Modify Date]   │
│  📓 analysis.ipynb                          [Modify Date]   │
│  📄 README.md                               [Modify Date]   │
└────────────────────────────────────────────────────────────┘

Notebook Interface:
─────────────────────────────────────────────────────────────
┌────────────────────────────────────────────────────────────┐
│  Jupyter  File Edit View Insert Cell Kernel Widgets Help  │
├────────────────────────────────────────────────────────────┤
│  💾 ➕ ✂️ 📋 ⬆️ ⬇️ ▶️ ⏹️ 🔄 ⏩                        │
├────────────────────────────────────────────────────────────┤
│  [Code ▼]                                                   │
├────────────────────────────────────────────────────────────┤
│  In [1]:  import numpy as np                               │
│           print("Hello, Jupyter!")                         │
│  Out[1]:  Hello, Jupyter!                                  │
├────────────────────────────────────────────────────────────┤
│  In [ ]:  # Your code here                                 │
│                                                             │
└────────────────────────────────────────────────────────────┘

╔════════════════════════════════════════════════════════════╗
║                   CELL TYPES                               ║
╚════════════════════════════════════════════════════════════╝

1. Code Cells
─────────────────────────────────────────────────────────────
• Execute Python code
• Show output below cell
• Can be re-run multiple times
• Access variables from other cells

In [1]:  x = 5
         y = 10
         print(x + y)
Out[1]:  15

2. Markdown Cells
─────────────────────────────────────────────────────────────
• Format text with Markdown
• Add headings, lists, links
• Include LaTeX equations
• Embed images

# Heading
## Subheading
- Bullet point
- **Bold** and *italic*
- [Link](https://jupyter.org)

Math: $E = mc^2$

3. Raw Cells
─────────────────────────────────────────────────────────────
• Plain text, not executed
• Useful for documentation
• Can be converted to other formats

╔════════════════════════════════════════════════════════════╗
║                   CELL MODES                               ║
╚════════════════════════════════════════════════════════════╝

Command Mode (Blue border - press Esc):
─────────────────────────────────────────────────────────────
• Operate on notebook as a whole
• Navigate between cells
• Add/delete cells
• Change cell types
• No cursor visible

Edit Mode (Green border - press Enter):
─────────────────────────────────────────────────────────────
• Edit cell contents
• Type code or text
• Cursor visible
• Can execute cell

╔════════════════════════════════════════════════════════════╗
║                   MENU BAR OPTIONS                         ║
╚════════════════════════════════════════════════════════════╝

File Menu:
─────────────────────────────────────────────────────────────
• New Notebook
• Open...
• Make a Copy...
• Save and Checkpoint
• Revert to Checkpoint
• Print Preview
• Download as (HTML, PDF, .py, .ipynb)
• Close and Halt

Edit Menu:
─────────────────────────────────────────────────────────────
• Cut/Copy/Paste Cells
• Delete Cells
• Split/Merge Cells
• Move Cells Up/Down
• Find and Replace
• Insert Image

View Menu:
─────────────────────────────────────────────────────────────
• Toggle Header
• Toggle Toolbar
• Toggle Line Numbers
• Cell Toolbar

Insert Menu:
─────────────────────────────────────────────────────────────
• Insert Cell Above
• Insert Cell Below

Cell Menu:
─────────────────────────────────────────────────────────────
• Run Cells
• Run All
• Run All Above/Below
• Cell Type (Code, Markdown, Raw)
• Current Outputs (Clear, Toggle)
• All Output (Clear, Toggle)

Kernel Menu:
─────────────────────────────────────────────────────────────
• Interrupt (Stop execution)
• Restart
• Restart & Clear Output
• Restart & Run All
• Reconnect
• Change kernel

╔════════════════════════════════════════════════════════════╗
║                   TOOLBAR ICONS                            ║
╚════════════════════════════════════════════════════════════╝

Icon    Action
─────────────────────────────────────────────────────────────
💾      Save notebook
➕      Insert cell below
✂️      Cut selected cells
📋      Copy selected cells
📋      Paste cells
⬆️      Move cell up
⬇️      Move cell down
▶️      Run cell
⏹️      Interrupt kernel
🔄      Restart kernel
⏩      Restart & run all
[Code]  Cell type dropdown
```

---

<div align="center">

## ⌨️ Keyboard Shortcuts

</div>

### Speed Up Your Workflow ⚡

```bash
# ═══════════════════════════════════════════
# ESSENTIAL KEYBOARD SHORTCUTS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   NAVIGATION SHORTCUTS                     ║
╚════════════════════════════════════════════════════════════╝

Command Mode (press Esc first):
─────────────────────────────────────────────────────────────
↑ / K           Move to cell above
↓ / J           Move to cell below
Enter           Enter edit mode
Shift + Enter   Run cell and move to next
Ctrl + Enter    Run cell and stay
Alt + Enter     Run cell and insert below

╔════════════════════════════════════════════════════════════╗
║                   CELL MANAGEMENT                          ║
╚════════════════════════════════════════════════════════════╝

Command Mode:
─────────────────────────────────────────────────────────────
A               Insert cell above
B               Insert cell below
X               Cut cell
C               Copy cell
V               Paste cell below
Shift + V       Paste cell above
D, D            Delete cell (press D twice)
Z               Undo cell deletion
Y               Change to code cell
M               Change to markdown cell
R               Change to raw cell
L               Toggle line numbers
Shift + L       Toggle line numbers (all cells)

╔════════════════════════════════════════════════════════════╗
║                   EXECUTION SHORTCUTS                      ║
╚════════════════════════════════════════════════════════════╝

Both Modes:
─────────────────────────────────────────────────────────────
Shift + Enter   Run cell and select below
Ctrl + Enter    Run cell
Alt + Enter     Run cell and insert below

Command Mode:
─────────────────────────────────────────────────────────────
Shift + K       Select cells above
Shift + J       Select cells down
Shift + M       Merge selected cells
Ctrl + S        Save notebook

╔════════════════════════════════════════════════════════════╗
║                   EDIT MODE SHORTCUTS                      ║
╚════════════════════════════════════════════════════════════╝

Edit Mode (inside a cell):
─────────────────────────────────────────────────────────────
Esc             Enter command mode
Ctrl + ]        Indent
Ctrl + [        Dedent
Ctrl + A        Select all
Ctrl + Z        Undo
Ctrl + Shift + Z Redo
Ctrl + Home     Go to cell start
Ctrl + End      Go to cell end
Tab             Code completion or indent
Shift + Tab     Tooltip (press 1-4 times for more info)

╔════════════════════════════════════════════════════════════╗
║                   ADVANCED SHORTCUTS                       ║
╚════════════════════════════════════════════════════════════╝

Command Mode:
─────────────────────────────────────────────────────────────
I, I            Interrupt kernel
0, 0            Restart kernel
Space           Scroll down
Shift + Space   Scroll up
H               Show keyboard shortcuts
P               Open command palette
F               Find and replace

╔════════════════════════════════════════════════════════════╗
║                   CUSTOM SHORTCUTS                         ║
╚════════════════════════════════════════════════════════════╝

To customize shortcuts:
1. Go to Help → Edit Keyboard Shortcuts
2. Or use command palette (Ctrl + Shift + P)

Example custom shortcuts:
─────────────────────────────────────────────────────────────
Ctrl + 1        Toggle heading level 1
Ctrl + 2        Toggle heading level 2
Ctrl + B        Bold selected text
Ctrl + I        Italic selected text

╔════════════════════════════════════════════════════════════╗
║                   PRODUCTIVITY TIPS                        ║
╚════════════════════════════════════════════════════════════╝

Most Used Shortcuts (Master These First):
─────────────────────────────────────────────────────────────
1. Shift + Enter    (Run cell and move)
2. Esc              (Command mode)
3. Enter            (Edit mode)
4. A / B            (Insert cells)
5. D, D             (Delete cell)
6. M                (Markdown)
7. Y                (Code)
8. Ctrl + S         (Save)

Practice Workflow:
─────────────────────────────────────────────────────────────
1. Esc → A          Create cell above
2. Enter            Edit mode
3. Type code
4. Shift + Enter    Run and move
5. Esc → B          Create cell below
6. Repeat

Pro Tip: Use command mode for navigation, edit mode for coding
Pro Tip: Learn one new shortcut per day
Pro Tip: Print shortcut reference (Help → Keyboard Shortcuts)
```

---

<div align="center">

## 🎨 Markdown & Formatting

</div>

### Beautiful Documentation 📝

````markdown
# ═══════════════════════════════════════════

# MARKDOWN IN JUPYTER

# ═══════════════════════════════════════════

## 1. Headings

# Heading 1

## Heading 2

### Heading 3

#### Heading 4

##### Heading 5

###### Heading 6

## 2. Text Formatting

**Bold text** or **Bold text**
_Italic text_ or _Italic text_
**_Bold and italic_** or **_Bold and italic_**
~~Strikethrough~~
`Inline code`

## 3. Lists

Unordered list:

- Item 1
- Item 2
  - Nested item 2.1
  - Nested item 2.2
- Item 3

Ordered list:

1. First item
2. Second item
3. Third item
   1. Nested item
   2. Another nested item

Task list:

- [ ] Task 1
- [x] Task 2 (completed)
- [ ] Task 3

## 4. Links and Images

[Link text](https://jupyter.org)
[Link with title](https://jupyter.org "Jupyter Homepage")

![Alt text](image.png)
![Alt text](https://example.com/image.png "Image title")

## 5. Code Blocks

Inline code: `print("Hello")`

Code block with syntax highlighting:

```python
def greet(name):
    return f"Hello, {name}!"

print(greet("World"))
```
````

```javascript
const greet = (name) => {
  return `Hello, ${name}!`;
};
```

## 6. Tables

| Column 1 | Column 2 | Column 3 |
| -------- | -------- | -------- |
| Data 1   | Data 2   | Data 3   |
| Data 4   | Data 5   | Data 6   |

Aligned tables:
| Left | Center | Right |
|:-----|:------:|------:|
| L1 | C1 | R1 |
| L2 | C2 | R2 |

## 7. Blockquotes

> This is a blockquote
>
> It can span multiple lines

> Nested blockquote
>
> > Nested further
> >
> > > And further

## 8. Horizontal Rules

---

---

---

## 9. LaTeX Math

Inline math: $E = mc^2$

Display math:
$$\int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2}$$

More examples:
$$f(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2}$$

Greek letters: $\alpha, \beta, \gamma, \Delta, \Omega$

Fractions: $\frac{a}{b}$

Superscript/Subscript: $x^2, x_i, x^{2y}, x_{i,j}$

## 10. HTML (Advanced)

<div style="background-color: #e7f3fe; padding: 10px; border-left: 4px solid #2196F3;">
    <strong>Info:</strong> You can use HTML for more complex formatting
</div>

<span style="color: red; font-weight: bold;">Red bold text</span>

<details>
<summary>Click to expand</summary>

Hidden content goes here

</details>

## 11. Colored Text

<font color='red'>This is red text</font>
<font color='blue'>This is blue text</font>
<font color='green'>This is green text</font>

## 12. Escaping Characters

To display special characters literally:
\*This is not italic\*
\# This is not a heading

## 13. Emojis

You can use emojis: 🚀 📊 🐍 💡 ✅ ❌ ⚠️

## 14. Collapsible Sections

<details>
<summary><b>Click to see code</b></summary>

```python
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)
```

</details>

## 15. Alerts/Callouts

> **Note:** This is a note

> **Warning:** This is a warning

> **Tip:** This is a helpful tip

# ═══════════════════════════════════════════

# PRACTICAL EXAMPLES

# ═══════════════════════════════════════════

## Example 1: Project Header

# 📊 Data Analysis Project

**Author:** John Doe
**Date:** 2024-01-15
**Version:** 1.0

## Overview

This notebook analyzes sales data to identify trends and patterns.

---

## Example 2: Section with Code

### Data Loading

First, let's import the necessary libraries:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

Then load the data:

```python
df = pd.read_csv('sales_data.csv')
```

---

## Example 3: Results Table

### Model Performance

| Model               | Accuracy | Precision | Recall | F1-Score |
| ------------------- | -------- | --------- | ------ | -------- |
| Random Forest       | 0.92     | 0.89      | 0.91   | 0.90     |
| Logistic Regression | 0.87     | 0.85      | 0.86   | 0.85     |
| SVM                 | 0.90     | 0.88      | 0.89   | 0.88     |

**Best Model:** Random Forest ✅

---

## Example 4: Mathematical Notation

### Linear Regression Formula

The linear regression model is defined as:

$$y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \ldots + \beta_n x_n + \epsilon$$

Where:

- $y$ is the dependent variable
- $x_i$ are the independent variables
- $\beta_i$ are the coefficients
- $\epsilon$ is the error term

The cost function to minimize:

$$J(\beta) = \frac{1}{2m} \sum_{i=1}^{m} (h_\beta(x^{(i)}) - y^{(i)})^2$$

---

## Example 5: Documentation Template

<div align="center">

# 🔬 Experiment Log

</div>

## Objective

Determine the optimal hyperparameters for the model.

## Methodology

1. Split data into train/test sets (80/20)
2. Perform grid search with 5-fold cross-validation
3. Evaluate on test set

## Results

- **Best Parameters:** `{'n_estimators': 100, 'max_depth': 10}`
- **Test Accuracy:** 92.5%

## Conclusions

The model performs well with these parameters. ✅

---

## Example 6: Checklist

### Data Science Workflow Checklist

- [x] Data collection
- [x] Data cleaning
- [x] Exploratory data analysis
- [x] Feature engineering
- [ ] Model training
- [ ] Model evaluation
- [ ] Model deployment

---

## Tips for Better Markdown

1. **Use headings hierarchy properly** (H1 → H2 → H3)
2. **Add whitespace** for readability
3. **Use code blocks** for code examples
4. **Include tables** for structured data
5. **Add images** to illustrate concepts
6. **Use LaTeX** for mathematical formulas
7. **Create sections** with horizontal rules
8. **Add emojis** for visual appeal (don't overdo it)
9. **Use blockquotes** for important notes
10. **Keep it organized** and consistent

---

<div align="center">

## 🪄 Magic Commands

</div>

### Supercharge Your Notebooks ⚡

```python
# ═══════════════════════════════════════════
# LINE MAGICS (%)
# ═══════════════════════════════════════════

"""
Magic commands are special commands that start with % or %%
- Line magics: % (single line)
- Cell magics: %% (entire cell)
"""

# ─────────────────────────────────────────────
# 1. TIMING & PROFILING
# ─────────────────────────────────────────────

# Time a single statement
%time sum(range(1000000))

# Time multiple runs (average)
%timeit sum(range(1000000))

# Time entire cell
%%time
total = 0
for i in range(1000000):
    total += i
print(total)

# More detailed timing
%%timeit -n 100 -r 5
# -n: number of loops
# -r: number of repeats
sum(range(1000))

# Profile code execution
%prun sum(range(1000000))

# Line-by-line profiling (requires line_profiler)
%load_ext line_profiler
%lprun -f my_function my_function(args)

# Memory profiling (requires memory_profiler)
%load_ext memory_profiler
%memit sum(range(1000000))

%%memit
data = [i**2 for i in range(100000)]

# ─────────────────────────────────────────────
# 2. DEBUGGING
# ─────────────────────────────────────────────

# Enable automatic debugger on exception
%pdb on

# Manual debugging
%debug

# Example with error
def divide(a, b):
    return a / b

divide(10, 0)  # This will raise error
%debug         # Start debugger

# Debug commands:
# n (next line)
# s (step into)
# c (continue)
# q (quit)
# p variable (print variable)

# ─────────────────────────────────────────────
# 3. SYSTEM COMMANDS
# ─────────────────────────────────────────────

# Run shell commands
!ls -la
!pwd
!pip list

# Store output in variable
files = !ls
print(files)

# Use Python variables in shell commands
filename = "data.csv"
!cat {filename}

# Change directory
%cd /path/to/directory

# Print working directory
%pwd

# List environment variables
%env

# Set environment variable
%env MY_VAR=value

# ─────────────────────────────────────────────
# 4. HISTORY & SESSIONS
# ─────────────────────────────────────────────

# Show command history
%history

# Show last N commands
%history -n 1-10

# Save history to file
%save my_script.py 1-10

# Load code from file
%load my_script.py

# Load code from URL
%load https://example.com/script.py

# Run external Python file
%run my_script.py

# Run with debugger
%run -d my_script.py

# ─────────────────────────────────────────────
# 5. VARIABLE MANAGEMENT
# ─────────────────────────────────────────────

# List all variables
%who

# List with type
%whos

# List specific type
%who_ls str

# Delete variables
x = 10
y = 20
%xdel x  # Delete single variable

# Reset namespace (delete all variables)
%reset

# Reset with confirmation
%reset -f

# ─────────────────────────────────────────────
# 6. AUTORELOAD
# ─────────────────────────────────────────────

# Auto-reload modules before execution (great for development)
%load_ext autoreload
%autoreload 2

# Options:
# 0: disable
# 1: reload modules imported with %aimport
# 2: reload all modules (except excluded)

# ─────────────────────────────────────────────
# 7. MATPLOTLIB INTEGRATION
# ─────────────────────────────────────────────

# Display plots inline (default in Jupyter)
%matplotlib inline

# Interactive plots
%matplotlib notebook

# High-resolution plots
%config InlineBackend.figure_format = 'retina'

# SVG plots (scalable)
%config InlineBackend.figure_format = 'svg'

# ─────────────────────────────────────────────
# 8. WRITING CODE
# ─────────────────────────────────────────────

# Write cell contents to file
%%writefile my_module.py
def greet(name):
    return f"Hello, {name}!"

# Append to file
%%writefile -a my_module.py
def goodbye(name):
    return f"Goodbye, {name}!"

# ─────────────────────────────────────────────
# 9. EXECUTE OTHER LANGUAGES
# ─────────────────────────────────────────────

# HTML
%%html
<h1>Hello HTML!</h1>
<p style="color: blue;">This is HTML in Jupyter</p>

# JavaScript
%%javascript
alert('Hello from JavaScript!');
element.text('JavaScript executed!');

# Bash script
%%bash
echo "Hello from Bash"
for i in {1..5}; do
    echo "Count: $i"
done

# Capture bash output
%%bash --out output
echo "This will be captured"
ls -la

# ─────────────────────────────────────────────
# 10. LATEX
# ─────────────────────────────────────────────

%%latex
\begin{align}
\nabla \times \vec{\mathbf{B}} &= \mu_0\vec{\mathbf{j}} + \mu_0\epsilon_0 \frac{\partial\vec{\mathbf{E}}}{\partial t} \\
\nabla \cdot \vec{\mathbf{E}} &= \frac{\rho}{\epsilon_0}
\end{align}

# ═══════════════════════════════════════════
# CELL MAGICS (%%)
# ═══════════════════════════════════════════

# ─────────────────────────────────────────────
# TIME ENTIRE CELL
# ─────────────────────────────────────────────

%%time
import numpy as np
data = np.random.randn(1000000)
result = np.mean(data)

# ─────────────────────────────────────────────
# CAPTURE OUTPUT
# ─────────────────────────────────────────────

%%capture output
print("This output will be captured")
print("Not displayed in notebook")

# Show captured output
output.show()

# ─────────────────────────────────────────────
# SQL QUERIES (requires ipython-sql)
# ─────────────────────────────────────────────

%load_ext sql
%sql sqlite:///my_database.db

%%sql
SELECT * FROM users
WHERE age > 25
ORDER BY name;

# ─────────────────────────────────────────────
# CUSTOM MAGIC COMMANDS
# ─────────────────────────────────────────────

from IPython.core.magic import register_line_magic, register_cell_magic

@register_line_magic
def my_magic(line):
    """My custom magic command"""
    return f"You typed: {line}"

# Usage: %my_magic hello world

@register_cell_magic
def csv_to_df(line, cell):
    """Convert CSV text to DataFrame"""
    import pandas as pd
    from io import StringIO
    return pd.read_csv(StringIO(cell))

# Usage:
# %%csv_to_df
# name,age,city
# Alice,25,NYC
# Bob,30,LA

# ═══════════════════════════════════════════
# USEFUL MAGIC COMBINATIONS
# ═══════════════════════════════════════════

# Time and profile
%%time
%%prun
def complex_function():
    return sum(i**2 for i in range(100000))
complex_function()

# Write and run
%%writefile temp_script.py
def test():
    print("Testing")
test()

%run temp_script.py

# ═══════════════════════════════════════════
# LIST ALL AVAILABLE MAGICS
# ═══════════════════════════════════════════

%lsmagic

# Get help on specific magic
%timeit?
%magic  # Complete documentation

print("Magic commands demonstrated!")
```

---

<div align="center">

## 🔧 Extensions & Customization

</div>

### Enhance Your Jupyter Experience 🎨

```bash
# ═══════════════════════════════════════════
# JUPYTER EXTENSIONS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   INSTALLING EXTENSIONS                    ║
╚════════════════════════════════════════════════════════════╝

# Install nbextensions
pip install jupyter_contrib_nbextensions
jupyter contrib nbextension install --user

# Enable extension configurator
pip install jupyter_nbextensions_configurator
jupyter nbextensions_configurator enable --user

# Access extensions:
# http://localhost:8888/nbextensions

╔════════════════════════════════════════════════════════════╗
║                   POPULAR EXTENSIONS                       ║
╚════════════════════════════════════════════════════════════╝

1. Table of Contents (TOC2)
─────────────────────────────────────────────────────────────
• Auto-generate table of contents from headings
• Navigate large notebooks easily
• Collapsible sections

Enable:
jupyter nbextension enable toc2/main

2. Variable Inspector
─────────────────────────────────────────────────────────────
• Display all variables in workspace
• Show type, size, and value
• Similar to RStudio's environment pane

Enable:
jupyter nbextension enable varInspector/main

3. ExecuteTime
─────────────────────────────────────────────────────────────
• Show execution time for each cell
• Track when cells were run
• Identify slow cells

Enable:
jupyter nbextension enable execute_time/ExecuteTime

4. Code Folding
─────────────────────────────────────────────────────────────
• Fold/unfold code sections
• Collapse functions and classes
• Cleaner notebook view

Enable:
jupyter nbextension enable codefolding/main

5. Collapsible Headings
─────────────────────────────────────────────────────────────
• Collapse sections under headings
• Better organization
• Hide/show content

Enable:
jupyter nbextension enable collapsible_headings/main

6. Autopep8
─────────────────────────────────────────────────────────────
• Auto-format code to PEP 8 style
• Clean code with one click
• Consistent formatting

Install & Enable:
pip install autopep8
jupyter nbextension enable code_prettify/autopep8

7. Hinterland
─────────────────────────────────────────────────────────────
• Auto-complete as you type
• No need to press Tab
• Like modern IDEs

Enable:
jupyter nbextension enable hinterland/hinterland

8. Snippets
─────────────────────────────────────────────────────────────
• Insert code snippets
• Common patterns ready to use
• Customizable

Enable:
jupyter nbextension enable snippets/main

9. Split Cells
─────────────────────────────────────────────────────────────
• Split notebook view
• Compare different sections
• Work on multiple cells

Enable:
jupyter nbextension enable splitcell/splitcell

10. Scratchpad
─────────────────────────────────────────────────────────────
• Temporary cell for testing
• Doesn't save in notebook
• Quick experiments

Enable:
jupyter nbextension enable scratchpad/main

╔════════════════════════════════════════════════════════════╗
║                   THEMES & STYLING                         ║
╚════════════════════════════════════════════════════════════╝

# Install Jupyter themes
pip install jupyterthemes

# List available themes
jt -l

Available themes:
• chesterish
• grade3
• gruvboxd
• gruvboxl
• monokai
• oceans16
• onedork
• solarizedd
• solarizedl

# Apply theme
jt -t monokai

# Customize theme
jt -t monokai -f fira -fs 12 -cellw 90% -T -N

# Options:
# -f: font
# -fs: font size
# -cellw: cell width
# -T: show toolbar
# -N: show notebook name

# Reset to default
jt -r

# Dark theme (popular)
jt -t onedork -fs 12 -altp -tfs 12 -nfs 12 -cellw 90% -T

╔════════════════════════════════════════════════════════════╗
║                   CUSTOM CSS                               ║
╚════════════════════════════════════════════════════════════╝

# Create custom.css in:
# ~/.jupyter/custom/custom.css

Example custom.css:
─────────────────────────────────────────────────────────────

/* Wider notebook */
.container {
    width: 90% !important;
}

/* Larger code font */
.CodeMirror {
    font-size: 14px !important;
}

/* Colored output */
.output_area pre {
    background-color: #f5f5f5;
    border-left: 3px solid #4CAF50;
    padding: 10px;
}

/* Custom markdown styles */
div.text_cell_render h1 {
    color: #2196F3;
    font-size: 36px;
}

╔════════════════════════════════════════════════════════════╗
║                   WIDGETS & INTERACTIVITY                  ║
╚════════════════════════════════════════════════════════════╝

# Install ipywidgets
pip install ipywidgets
jupyter nbextension enable --py widgetsnbextension

# Enable in JupyterLab
jupyter labextension install @jupyter-widgets/jupyterlab-manager

Example interactive widgets:
─────────────────────────────────────────────────────────────

from ipywidgets import interact, widgets
import matplotlib.pyplot as plt
import numpy as np

@interact(freq=(1, 10, 0.5), amplitude=(0.5, 2, 0.1))
def plot_wave(freq=5, amplitude=1):
    x = np.linspace(0, 2*np.pi, 1000)
    y = amplitude * np.sin(freq * x)
    plt.figure(figsize=(10, 4))
    plt.plot(x, y)
    plt.title(f'Sine Wave: freq={freq}, amp={amplitude}')
    plt.show()

# More widgets
slider = widgets.IntSlider(min=0, max=100, value=50)
dropdown = widgets.Dropdown(options=['A', 'B', 'C'])
button = widgets.Button(description='Click me!')

╔════════════════════════════════════════════════════════════╗
║                   PRODUCTIVITY EXTENSIONS                  ║
╚════════════════════════════════════════════════════════════╝

# Keyboard shortcuts editor
jupyter nbextension enable keyboard_shortcut_editor/main

# Limit output length
jupyter nbextension enable limit_output/main

# Hide input cells
jupyter nbextension enable hide_input/main

# Add line numbers by default
jupyter nbextension enable line_numbers/main

# Freeze cells (prevent editing)
jupyter nbextension enable freeze/main

╔════════════════════════════════════════════════════════════╗
║                   RECOMMENDED SETUP                        ║
╚════════════════════════════════════════════════════════════╝

Complete setup for optimal experience:
─────────────────────────────────────────────────────────────

# 1. Install core extensions
pip install jupyter_contrib_nbextensions
jupyter contrib nbextension install --user
pip install jupyter_nbextensions_configurator
jupyter nbextensions_configurator enable --user

# 2. Install widgets
pip install ipywidgets
jupyter nbextension enable --py widgetsnbextension

# 3. Install themes
pip install jupyterthemes

# 4. Apply nice theme
jt -t onedork -fs 12 -cellw 90% -T -N

# 5. Enable favorite extensions
jupyter nbextension enable toc2/main
jupyter nbextension enable varInspector/main
jupyter nbextension enable execute_time/ExecuteTime
jupyter nbextension enable codefolding/main
jupyter nbextension enable collapsible_headings/main

# 6. Install autopep8
pip install autopep8
jupyter nbextension enable code_prettify/autopep8

# 7. Restart Jupyter
jupyter notebook
```

---

<div align="center">

## 🔬 JupyterLab

</div>

### The Next Generation Interface 🚀

```bash
# ═══════════════════════════════════════════
# JUPYTERLAB OVERVIEW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHAT IS JUPYTERLAB?                      ║
╚════════════════════════════════════════════════════════════╝

JupyterLab: Next-generation Jupyter interface
─────────────────────────────────────────────────────────────
• Multi-document interface
• Flexible layouts
• Built-in file browser
• Integrated terminal
• Text editor
• CSV viewer
• Markdown preview
• Extension system
• Modern UI

Jupyter Notebook vs JupyterLab:
─────────────────────────────────────────────────────────────

Feature              Notebook    JupyterLab
─────────────────────────────────────────────────────────────
Multiple documents   ❌          ✅
Drag & drop tabs     ❌          ✅
Terminal             ❌          ✅
Text editor          ❌          ✅
File browser         Basic       Advanced
Customization        Limited     Extensive
Extensions           Legacy      Modern
Learning curve       Easy        Moderate

╔════════════════════════════════════════════════════════════╗
║                   INSTALLATION                             ║
╚════════════════════════════════════════════════════════════╝

# Install JupyterLab
pip install jupyterlab

# Or with conda
conda install -c conda-forge jupyterlab

# Start JupyterLab
jupyter lab

# Start on specific port
jupyter lab --port 8889

# Show version
jupyter lab --version

╔════════════════════════════════════════════════════════════╗
║                   INTERFACE OVERVIEW                       ║
╚════════════════════════════════════════════════════════════╝

JupyterLab Interface:
─────────────────────────────────────────────────────────────

┌──────────────────────────────────────────────────────────┐
│ File Edit View Run Kernel Tabs Settings Help              │
├──────────┬───────────────────────────────────────────────┤
│ 📁 Files │  Launcher                                      │
│ 🏃 Running│  ┌──────┬──────┬──────┐                      │
│ 🧪 Commands│ │ 📓   │ 📄   │ 💻   │                      │
│ 🏷️ Properties│ │Notebook│Console│Terminal│                │
│ 📂 Explorer│ └──────┴──────┴──────┘                      │
│          │                                                │
│ data/    │  [Untitled.ipynb]  [data.csv]  [terminal]    │
│ notebooks/│  ┌──────────────────────────────────┐       │
│ ├─ eda.ipynb│ │ In [1]: import pandas as pd    │       │
│ ├─ model.ipynb│ │        import numpy as np      │       │
│ └─ viz.ipynb│ │                                  │       │
│          │  │ In [2]:                           │       │
│          │  └──────────────────────────────────┘       │
└──────────┴───────────────────────────────────────────────┘

Key Areas:
1. Left Sidebar: File browser, running kernels, commands
2. Main Work Area: Tabs for notebooks, files, terminals
3. Right Sidebar: Property inspector, debugger

╔════════════════════════════════════════════════════════════╗
║                   KEY FEATURES                             ║
╚════════════════════════════════════════════════════════════╝

1. Flexible Layouts
─────────────────────────────────────────────────────────────
• Drag tabs to arrange
• Split view vertically/horizontally
• Multiple notebooks side-by-side
• Compare code and results

2. File Browser
─────────────────────────────────────────────────────────────
• Navigate files easily
• Upload/download files
• Create new files/folders
• Drag and drop
• Right-click context menu

3. Integrated Terminal
─────────────────────────────────────────────────────────────
• Full terminal access
• Multiple terminals
• Run commands while coding
• Monitor processes

4. Text Editor
─────────────────────────────────────────────────────────────
• Edit Python files
• Syntax highlighting
• Auto-completion
• Multiple file support

5. CSV Viewer
─────────────────────────────────────────────────────────────
• View CSV files directly
• Sort and filter
• No need to load in pandas

6. Markdown Preview
─────────────────────────────────────────────────────────────
• Live markdown preview
• Edit and see results
• Side-by-side view

7. Debugger
─────────────────────────────────────────────────────────────
• Visual debugger
• Set breakpoints
• Step through code
• Inspect variables

╔════════════════════════════════════════════════════════════╗
║                   JUPYTERLAB SHORTCUTS                     ║
╚════════════════════════════════════════════════════════════╝

Command Palette:
─────────────────────────────────────────────────────────────
Ctrl + Shift + C    Open command palette

Tabs:
─────────────────────────────────────────────────────────────
Ctrl + Shift + [    Previous tab
Ctrl + Shift + ]    Next tab
Ctrl + Shift + W    Close tab
Ctrl + Shift + T    New terminal

Layout:
─────────────────────────────────────────────────────────────
Ctrl + B            Toggle left sidebar
Ctrl + Shift + D    Toggle right sidebar
Ctrl + Shift + L    Toggle line numbers

File Operations:
─────────────────────────────────────────────────────────────
Ctrl + S            Save
Ctrl + Shift + S    Save as
Ctrl + O            Open

╔════════════════════════════════════════════════════════════╗
║                   EXTENSIONS                               ║
╚════════════════════════════════════════════════════════════╝

# List installed extensions
jupyter labextension list

# Install extension
jupyter labextension install @extension/name

# Popular extensions:
─────────────────────────────────────────────────────────────

# 1. Variable Inspector
jupyter labextension install @lckr/jupyterlab_variableinspector

# 2. Table of Contents
jupyter labextension install @jupyterlab/toc

# 3. Git integration
pip install jupyterlab-git
jupyter labextension install @jupyterlab/git

# 4. GitHub integration
jupyter labextension install @jupyterlab/github

# 5. Code formatter
pip install jupyterlab_code_formatter
jupyter labextension install @ryantam626/jupyterlab_code_formatter

# 6. Spreadsheet viewer
jupyter labextension install jupyterlab-spreadsheet

# 7. Draw.io diagrams
jupyter labextension install jupyterlab-drawio

# 8. LaTeX
jupyter labextension install @jupyterlab/latex

╔════════════════════════════════════════════════════════════╗
║                   CONFIGURATION                            ║
╚════════════════════════════════════════════════════════════╝

# Generate config
jupyter lab --generate-config

# Config location:
# ~/.jupyter/jupyter_lab_config.py

Common settings:
─────────────────────────────────────────────────────────────

# Default directory
c.ServerApp.root_dir = '/path/to/notebooks'

# Disable token
c.ServerApp.token = ''

# Custom port
c.ServerApp.port = 8889

# Allow remote access
c.ServerApp.ip = '0.0.0.0'

# Browser
c.ServerApp.browser = 'chrome'

╔════════════════════════════════════════════════════════════╗
║                   WORKFLOW TIPS                            ║
╚════════════════════════════════════════════════════════════╝

Efficient Workflow:
─────────────────────────────────────────────────────────────

1. Split View
   • Notebook on left, terminal on right
   • Code and visualization side-by-side
   • Compare two notebooks

2. Multiple Notebooks
   • Tabs for different analyses
   • Easy switching between contexts
   • Keep everything organized

3. Integrated Development
   • Edit .py files in editor
   • Test in notebook
   • Run in terminal
   • All in one interface

4. File Management
   • Drag and drop to upload
   • Right-click operations
   • Quick file access
   • Organized workspace

5. Documentation
   • Markdown files for docs
   • Preview side-by-side
   • Edit and view together
```

---

<div align="center">

## 💡 Best Practices

</div>

### Professional Notebook Standards 📋

```bash
# ═══════════════════════════════════════════
# JUPYTER NOTEBOOK BEST PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ORGANIZATION                             ║
╚════════════════════════════════════════════════════════════╝

1. Notebook Structure
─────────────────────────────────────────────────────────────

✅ Good Structure:

# Title and Overview
─────────────────────────────────────────────
# Data Analysis: Sales Trends
**Author:** John Doe
**Date:** 2024-01-15
**Purpose:** Analyze Q4 sales data

## Table of Contents
1. [Setup](#setup)
2. [Data Loading](#data-loading)
3. [Exploratory Analysis](#exploratory-analysis)
4. [Visualization](#visualization)
5. [Conclusions](#conclusions)

## 1. Setup <a id='setup'></a>
### Import Libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

### Configuration
%matplotlib inline
pd.set_option('display.max_columns', None)

## 2. Data Loading <a id='data-loading'></a>
...

❌ Poor Structure:
• No title or description
• Random cell order
• No sections
• Mixed code and exploration
• No clear flow

2. Cell Organization
─────────────────────────────────────────────────────────────

✅ DO:
• One logical operation per cell
• Group related imports
• Separate data loading, processing, visualization
• Add markdown headers between sections
• Keep cells focused and small

❌ DON'T:
• Put everything in one giant cell
• Mix imports throughout notebook
• Repeat code in multiple cells
• Create circular dependencies

3. Naming Conventions
─────────────────────────────────────────────────────────────

Notebook names:
✅ 01_data_exploration.ipynb
✅ 02_feature_engineering.ipynb
✅ 03_model_training.ipynb
✅ 2024-01-15_customer_analysis.ipynb

❌ Untitled1.ipynb
❌ Final.ipynb
❌ analysis_final_v2_FINAL.ipynb

╔════════════════════════════════════════════════════════════╗
║                   CODE QUALITY                             ║
╚════════════════════════════════════════════════════════════╝

1. Imports
─────────────────────────────────────────────────────────────

✅ Good:
# Standard library
import os
import sys
from pathlib import Path

# Third-party
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Local
from my_module import my_function

❌ Bad:
from numpy import *  # Don't do this!
import pandas  # Use standard alias: pd
import matplotlib.pyplot as plt  # Repeated in multiple cells

2. Code Style
─────────────────────────────────────────────────────────────

✅ Good:
# Clear variable names
customer_data = pd.read_csv('customers.csv')
monthly_revenue = customer_data.groupby('month')['revenue'].sum()

# Documented functions
def calculate_metrics(data):
    """
    Calculate key performance metrics.

    Parameters:
    -----------
    data : pd.DataFrame
        Customer data with required columns

    Returns:
    --------
    dict : Dictionary of metrics
    """
    metrics = {
        'total_revenue': data['revenue'].sum(),
        'avg_order_value': data['revenue'].mean(),
        'customer_count': data['customer_id'].nunique()
    }
    return metrics

❌ Bad:
df = pd.read_csv('data.csv')  # What data?
x = df.groupby('a')['b'].sum()  # Unclear variables

3. Comments and Documentation
─────────────────────────────────────────────────────────────

✅ Good:
# Load customer data from Q4 2023
df = pd.read_csv('customers_q4_2023.csv')

# Remove duplicates based on customer ID
df = df.drop_duplicates(subset='customer_id', keep='first')

# Calculate customer lifetime value
# Formula: Average Purchase Value × Purchase Frequency × Customer Lifespan
df['clv'] = df['avg_purchase'] * df['frequency'] * df['lifespan_months']

❌ Bad:
# Load data
df = pd.read_csv('data.csv')
# Do stuff
df = df.drop_duplicates()
# Calculate
df['x'] = df['a'] * df['b'] * df['c']

╔════════════════════════════════════════════════════════════╗
║                   EXECUTION ORDER                          ║
╚════════════════════════════════════════════════════════════╝

Problem: Notebooks can be run out of order
─────────────────────────────────────────────────────────────

✅ Best Practices:

1. Design for Top-to-Bottom Execution
   • Notebook should run from cell 1 to last
   • No circular dependencies
   • No hidden state

2. Test Full Execution
   # Restart kernel and run all
   Kernel → Restart & Run All

   # Or programmatically
   %reset -f
   %run notebook.ipynb

3. Clear Output Before Committing
   # Clear all output
   Cell → All Output → Clear

   # Or command line
   jupyter nbconvert --clear-output --inplace notebook.ipynb

4. Avoid Global State Issues
   # Each cell should be self-contained where possible
   # Minimize dependencies between cells

╔════════════════════════════════════════════════════════════╗
║                   VERSION CONTROL                          ║
╚════════════════════════════════════════════════════════════╝

Git Best Practices for Notebooks:
─────────────────────────────────────────────────────────────

1. .gitignore Setup
─────────────────────────────────────────────────────────────
# .gitignore
.ipynb_checkpoints/
__pycache__/
*.pyc
.DS_Store

2. Clear Output Before Committing
─────────────────────────────────────────────────────────────
# Manual
Cell → All Output → Clear

# Automatic (git hook)
# Install nbstripout
pip install nbstripout
nbstripout --install

# Now output is automatically cleared on commit

3. Use nbdime for Diffs
─────────────────────────────────────────────────────────────
# Install
pip install nbdime

# Configure git
nbdime config-git --enable

# Now see meaningful diffs
git diff notebook.ipynb

4. Commit Often, Small Changes
─────────────────────────────────────────────────────────────
✅ Good commits:
• "Add data loading section"
• "Implement feature engineering"
• "Add visualization for sales trends"

❌ Bad commits:
• "Update"
• "Final version"
• "Changes"

╔════════════════════════════════════════════════════════════╗
║                   REPRODUCIBILITY                          ║
╚════════════════════════════════════════════════════════════╝

1. Document Environment
─────────────────────────────────────────────────────────────
# Create requirements.txt
pip freeze > requirements.txt

# Or use pipreqs (only imports used)
pip install pipreqs
pipreqs /path/to/project

# Add to notebook header
"""
Environment:
- Python 3.9.12
- pandas==1.4.2
- numpy==1.22.3
- matplotlib==3.5.1

Install: pip install -r requirements.txt
"""

2. Set Random Seeds
─────────────────────────────────────────────────────────────
import numpy as np
import random

# Set seeds for reproducibility
SEED = 42
np.random.seed(SEED)
random.seed(SEED)

# For deep learning
# torch.manual_seed(SEED)
# tf.random.set_seed(SEED)

3. Document Data Sources
─────────────────────────────────────────────────────────────
"""
Data Sources:
- customers.csv: Downloaded from internal database on 2024-01-15
- sales_data.xlsx: Provided by finance team, Q4 2023 data
- external_data.json: API call to https://api.example.com/data
"""

4. Include Data Validation
─────────────────────────────────────────────────────────────
# Validate data shape
assert df.shape == (1000, 15), "Data shape unexpected"

# Validate columns
expected_cols = ['customer_id', 'date', 'amount']
assert all(col in df.columns for col in expected_cols)

# Validate data types
assert df['amount'].dtype == np.float64

╔════════════════════════════════════════════════════════════╗
║                   PERFORMANCE                              ║
╚════════════════════════════════════════════════════════════╝

1. Avoid Expensive Operations in Multiple Cells
─────────────────────────────────────────────────────────────

❌ Bad:
# Cell 1
df = pd.read_csv('large_file.csv')  # Slow

# Cell 2
df = pd.read_csv('large_file.csv')  # Slow again!

✅ Good:
# Cell 1: Load once
if 'df' not in locals():
    df = pd.read_csv('large_file.csv')

# Or cache
from functools import lru_cache

@lru_cache(maxsize=1)
def load_data():
    return pd.read_csv('large_file.csv')

df = load_data()

2. Monitor Resource Usage
─────────────────────────────────────────────────────────────
# Check memory usage
%load_ext memory_profiler
%memit df.groupby('category').sum()

# Profile code
%prun expensive_function()

3. Use Efficient Data Types
─────────────────────────────────────────────────────────────
# Optimize dtypes
df['category'] = df['category'].astype('category')
df['amount'] = pd.to_numeric(df['amount'], downcast='float')

╔════════════════════════════════════════════════════════════╗
║                   SECURITY                                 ║
╚════════════════════════════════════════════════════════════╝

1. Never Commit Secrets
─────────────────────────────────────────────────────────────

❌ Bad:
API_KEY = "sk-1234567890abcdef"  # Never do this!
db_password = "mypassword123"

✅ Good:
import os
from dotenv import load_dotenv

load_dotenv()
API_KEY = os.getenv('API_KEY')
DB_PASSWORD = os.getenv('DB_PASSWORD')

# .env file (add to .gitignore!)
API_KEY=sk-1234567890abcdef
DB_PASSWORD=mypassword123

2. Sanitize Output
─────────────────────────────────────────────────────────────
# Before sharing, check for:
• API keys
• Passwords
• Personal data (PII)
• Internal URLs
• Proprietary information

3. Be Careful with File Paths
─────────────────────────────────────────────────────────────

❌ Bad:
df = pd.read_csv('/Users/john/secret/confidential_data.csv')

✅ Good:
from pathlib import Path

DATA_DIR = Path('./data')
df = pd.read_csv(DATA_DIR / 'public_data.csv')

╔════════════════════════════════════════════════════════════╗
║                   SHARING & COLLABORATION                  ║
╚════════════════════════════════════════════════════════════╝

1. Before Sharing
─────────────────────────────────────────────────────────────
☐ Clear all output
☐ Restart kernel and run all
☐ Remove debugging code
☐ Check for secrets
☐ Add documentation
☐ Test with fresh environment

2. Export Options
─────────────────────────────────────────────────────────────
# HTML (for viewing)
jupyter nbconvert --to html notebook.ipynb

# PDF (requires LaTeX)
jupyter nbconvert --to pdf notebook.ipynb

# Python script
jupyter nbconvert --to python notebook.ipynb

# Slides
jupyter nbconvert --to slides notebook.ipynb --post serve

3. Use nbviewer
─────────────────────────────────────────────────────────────
# Share notebooks via GitHub
https://nbviewer.jupyter.org/github/user/repo/blob/master/notebook.ipynb

4. Create Binder Links
─────────────────────────────────────────────────────────────
# Make notebooks interactive
https://mybinder.org/v2/gh/user/repo/master?filepath=notebook.ipynb
```

---

<div align="center">

## 🚀 Advanced Features

</div>

### Power User Techniques ⚡

```python
# ═══════════════════════════════════════════
# ADVANCED JUPYTER FEATURES
# ═══════════════════════════════════════════

# ─────────────────────────────────────────────
# 1. INTERACTIVE WIDGETS
# ─────────────────────────────────────────────

import ipywidgets as widgets
from IPython.display import display
import numpy as np
import matplotlib.pyplot as plt

# Simple slider
slider = widgets.IntSlider(
    value=50,
    min=0,
    max=100,
    step=1,
    description='Value:',
    continuous_update=False
)

# Display widget
display(slider)

# Access value
print(slider.value)

# Interactive plot
def plot_function(frequency=1.0, amplitude=1.0, phase=0.0):
    x = np.linspace(0, 4*np.pi, 1000)
    y = amplitude * np.sin(frequency * x + phase)

    plt.figure(figsize=(10, 4))
    plt.plot(x, y)
    plt.title(f'Sine Wave: freq={frequency}, amp={amplitude}, phase={phase}')
    plt.ylim(-3, 3)
    plt.grid(True, alpha=0.3)
    plt.show()

# Create interactive interface
widgets.interact(
    plot_function,
    frequency=widgets.FloatSlider(min=0.1, max=10, step=0.1, value=1),
    amplitude=widgets.FloatSlider(min=0.1, max=3, step=0.1, value=1),
    phase=widgets.FloatSlider(min=0, max=2*np.pi, step=0.1, value=0)
)

# More widget types
dropdown = widgets.Dropdown(
    options=['Option 1', 'Option 2', 'Option 3'],
    value='Option 1',
    description='Choose:'
)

checkbox = widgets.Checkbox(
    value=False,
    description='Enable feature'
)

button = widgets.Button(
    description='Click Me!',
    button_style='success',  # 'success', 'info', 'warning', 'danger'
    tooltip='Click to execute'
)

def on_button_click(b):
    print("Button clicked!")

button.on_click(on_button_click)

# Layout widgets
box = widgets.HBox([slider, dropdown, checkbox])
display(box)

# Tab widget
tab = widgets.Tab()
tab.children = [widgets.Label('Content 1'), widgets.Label('Content 2')]
tab.set_title(0, 'Tab 1')
tab.set_title(1, 'Tab 2')
display(tab)

# ─────────────────────────────────────────────
# 2. MULTI-KERNEL NOTEBOOKS
# ─────────────────────────────────────────────

# Install additional kernels

# R kernel
# install.packages('IRkernel')
# IRkernel::installspec()

# Julia kernel
# using Pkg
# Pkg.add("IJulia")

# List available kernels
!jupyter kernelspec list

# Switch kernel
# Kernel → Change Kernel → [Select kernel]

# ─────────────────────────────────────────────
# 3. PARALLEL COMPUTING
# ─────────────────────────────────────────────

from ipyparallel import Client

# Start cluster (in terminal):
# ipcluster start -n 4

# Connect to cluster
rc = Client()
print(f"Connected to {len(rc)} engines")

# Direct view (all engines)
dview = rc[:]

# Execute on all engines
dview.execute('import numpy as np')

# Parallel map
def square(x):
    return x ** 2

# Sequential
result_seq = list(map(square, range(100)))

# Parallel
result_par = dview.map_sync(square, range(100))

# Load balanced view
lview = rc.load_balanced_view()
result = lview.map_sync(square, range(100))

# ─────────────────────────────────────────────
# 4. DATABASE INTEGRATION
# ─────────────────────────────────────────────

# SQL magic
%load_ext sql

# Connect to database
%sql sqlite:///my_database.db

# Query database
result = %sql SELECT * FROM users WHERE age > 25

# Multi-line query
%%sql
SELECT
    category,
    COUNT(*) as count,
    AVG(price) as avg_price
FROM products
GROUP BY category
ORDER BY count DESC;

# Store result in DataFrame
result_df = %sql SELECT * FROM users
df = result_df.DataFrame()

# ─────────────────────────────────────────────
# 5. REMOTE JUPYTER
# ─────────────────────────────────────────────

# On remote server:
jupyter notebook --no-browser --port=8889

# On local machine (SSH tunnel):
ssh -N -f -L localhost:8888:localhost:8889 user@remote-server

# Access: http://localhost:8888

# ─────────────────────────────────────────────
# 6. CUSTOM DISPLAY OBJECTS
# ─────────────────────────────────────────────

from IPython.display import HTML, Image, Audio, Video, YouTubeVideo

# HTML
HTML('<h2 style="color: blue;">Custom HTML</h2>')

# Image
Image(url='https://example.com/image.png', width=400)

# Local image
Image(filename='local_image.png')

# Audio
Audio(url='https://example.com/audio.mp3')

# Video
Video(url='https://example.com/video.mp4', width=640, height=480)

# YouTube video
YouTubeVideo('dQw4w9WgXcQ', width=640, height=360)

# ─────────────────────────────────────────────
# 7. PROGRESS BARS
# ─────────────────────────────────────────────

from tqdm.notebook import tqdm
import time

# Simple progress bar
for i in tqdm(range(100)):
    time.sleep(0.01)

# With description
for i in tqdm(range(100), desc='Processing'):
    time.sleep(0.01)

# Nested progress bars
for i in tqdm(range(10), desc='Outer'):
    for j in tqdm(range(100), desc='Inner', leave=False):
        time.sleep(0.001)

# Manual progress bar
pbar = tqdm(total=100)
for i in range(100):
    # Do work
    time.sleep(0.01)
    pbar.update(1)
pbar.close()

# ─────────────────────────────────────────────
# 8. CONDITIONAL CELL EXECUTION
# ─────────────────────────────────────────────

# Skip cell conditionally
SKIP_EXPENSIVE = True

if not SKIP_EXPENSIVE:
    # Expensive computation
    result = expensive_function()
else:
    print("Skipping expensive computation")

# Skip with magic
%skip

# Toggle cell execution
DEBUG = True

if DEBUG:
    %debug

# ─────────────────────────────────────────────
# 9. CELL METADATA & TAGS
# ─────────────────────────────────────────────

# Add tags to cells
# View → Cell Toolbar → Tags

# Useful tags:
# - parameters (for papermill)
# - skip-execution
# - hide-input
# - hide-output

# Access cell metadata (in Python)
from IPython import get_ipython
ipython = get_ipython()

# ─────────────────────────────────────────────
# 10. NOTEBOOK AS MODULE
# ─────────────────────────────────────────────

# Import from another notebook
%run other_notebook.ipynb

# Or use nbimporter
# pip install nbimporter
import nbimporter
from my_notebook import my_function

# ─────────────────────────────────────────────
# 11. PARAMETERIZED NOTEBOOKS (PAPERMILL)
# ─────────────────────────────────────────────

# Install papermill
# pip install papermill

# Tag a cell as "parameters" in notebook
# View → Cell Toolbar → Tags → parameters

# In notebook (parameters cell):
# Parameters
input_file = "data.csv"
output_file = "results.csv"
threshold = 0.5

# Execute notebook with parameters (command line)
# papermill input.ipynb output.ipynb -p input_file data2.csv -p threshold 0.8

# ─────────────────────────────────────────────
# 12. JUPYTEXT - NOTEBOOKS AS SCRIPTS
# ─────────────────────────────────────────────

# Install jupytext
# pip install jupytext

# Convert notebook to script
# jupytext --to py notebook.ipynb

# Convert script to notebook
# jupytext --to ipynb script.py

# Pair notebook with script (auto-sync)
# jupytext --set-formats ipynb,py notebook.ipynb

# ─────────────────────────────────────────────
# 13. CUSTOM CSS IN CELLS
# ─────────────────────────────────────────────

from IPython.display import HTML

HTML("""
<style>
.custom-box {
    background-color: #e7f3fe;
    border-left: 6px solid #2196F3;
    padding: 15px;
    margin: 10px 0;
}
</style>
<div class="custom-box">
    <h3>Important Note</h3>
    <p>This is a custom styled box.</p>
</div>
""")

# ─────────────────────────────────────────────
# 14. VOILA - DASHBOARDS FROM NOTEBOOKS
# ─────────────────────────────────────────────

# Install voila
# pip install voila

# Create dashboard (hides code, shows output)
# voila notebook.ipynb

# Or use as extension
# jupyter serverextension enable voila --sys-prefix

# Access via: http://localhost:8888/voila

print("Advanced features demonstrated!")
```

---

<div align="center">

## 🛠️ Workflows

</div>

### Real-World Jupyter Workflows 💼

```python
# ═══════════════════════════════════════════
# DATA SCIENCE WORKFLOW
# ═══════════════════════════════════════════

"""
Project Structure:
──────────────────────────────────────────────────────────────
project/
├── notebooks/
│   ├── 01_data_collection.ipynb
│   ├── 02_data_cleaning.ipynb
│   ├── 03_exploratory_analysis.ipynb
│   ├── 04_feature_engineering.ipynb
│   ├── 05_model_training.ipynb
│   ├── 06_model_evaluation.ipynb
│   └── 07_reporting.ipynb
├── src/
│   ├── __init__.py
│   ├── data_processing.py
│   ├── features.py
│   └── models.py
├── data/
│   ├── raw/
│   ├── processed/
│   └── external/
├── models/
│   └── trained_models/
├── reports/
│   └── figures/
├── requirements.txt
├── README.md
└── .gitignore
"""

# ═══════════════════════════════════════════
# WORKFLOW 1: EXPLORATORY DATA ANALYSIS
# ═══════════════════════════════════════════

# ──────────────────────────────────────────────────────────
# Notebook: 01_data_exploration.ipynb
# ──────────────────────────────────────────────────────────

# # 📊 Data Exploration - Customer Dataset
#
# **Author:** Data Science Team
# **Date:** 2024-01-15
# **Purpose:** Initial exploration of customer data

# ## 1. Setup

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from pathlib import Path

# Configuration
%matplotlib inline
sns.set_style('whitegrid')
pd.set_option('display.max_columns', None)

# Paths
DATA_DIR = Path('../data')
RAW_DATA = DATA_DIR / 'raw'
PROCESSED_DATA = DATA_DIR / 'processed'
FIGURES_DIR = Path('../reports/figures')

# ## 2. Load Data

df = pd.read_csv(RAW_DATA / 'customers.csv')

print(f"Dataset shape: {df.shape}")
print(f"Memory usage: {df.memory_usage(deep=True).sum() / 1024**2:.2f} MB")

# ## 3. Initial Inspection

# Display first rows
display(df.head())

# Data types
display(df.dtypes)

# Basic statistics
display(df.describe())

# Missing values
missing = df.isnull().sum()
missing_pct = (missing / len(df)) * 100
missing_df = pd.DataFrame({
    'Missing': missing,
    'Percentage': missing_pct
})
display(missing_df[missing_df['Missing'] > 0])

# ## 4. Data Quality Checks

# Duplicates
print(f"Duplicate rows: {df.duplicated().sum()}")

# Value ranges
for col in df.select_dtypes(include=[np.number]).columns:
    print(f"\n{col}:")
    print(f"  Min: {df[col].min()}")
    print(f"  Max: {df[col].max()}")
    print(f"  Mean: {df[col].mean():.2f}")
    print(f"  Std: {df[col].std():.2f}")

# ## 5. Visualizations

# Distribution of numeric variables
fig, axes = plt.subplots(2, 2, figsize=(15, 10))
fig.suptitle('Distribution of Numeric Variables', fontsize=16)

df['age'].hist(ax=axes[0, 0], bins=30, edgecolor='black')
axes[0, 0].set_title('Age Distribution')

df['income'].hist(ax=axes[0, 1], bins=30, edgecolor='black')
axes[0, 1].set_title('Income Distribution')

# Save figure
plt.savefig(FIGURES_DIR / 'distributions.png', dpi=300, bbox_inches='tight')
plt.show()

# ## 6. Key Findings

# - Dataset contains X rows and Y columns
# - Z% missing values in column A
# - Age ranges from X to Y
# - Income is right-skewed

# ## 7. Next Steps

# - [ ] Handle missing values
# - [ ] Remove duplicates
# - [ ] Engineer new features
# - [ ] Prepare for modeling

# ═══════════════════════════════════════════
# WORKFLOW 2: MODEL DEVELOPMENT
# ═══════════════════════════════════════════

# ──────────────────────────────────────────────────────────
# Notebook: 05_model_training.ipynb
# ──────────────────────────────────────────────────────────

# # 🤖 Model Training - Customer Churn Prediction

# ## 1. Setup

import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split, cross_val_score
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import classification_report, confusion_matrix
import joblib

# Set random seed for reproducibility
SEED = 42
np.random.seed(SEED)

# ## 2. Load Processed Data

df = pd.read_csv(PROCESSED_DATA / 'customers_processed.csv')
print(f"Loaded {len(df)} rows")

# ## 3. Prepare Data

# Features and target
feature_cols = ['age', 'income', 'tenure', 'num_products']
target_col = 'churned'

X = df[feature_cols]
y = df[target_col]

# Split data
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=SEED, stratify=y
)

print(f"Training set: {len(X_train)} samples")
print(f"Test set: {len(X_test)} samples")
print(f"Churn rate: {y_train.mean():.2%}")

# ## 4. Train Model

model = RandomForestClassifier(
    n_estimators=100,
    max_depth=10,
    random_state=SEED,
    n_jobs=-1
)

# Train
model.fit(X_train, y_train)

# ## 5. Evaluate Model

# Cross-validation
cv_scores = cross_val_score(model, X_train, y_train, cv=5)
print(f"Cross-validation accuracy: {cv_scores.mean():.4f} (+/- {cv_scores.std():.4f})")

# Test set performance
y_pred = model.predict(X_test)
print("\nTest Set Performance:")
print(classification_report(y_test, y_pred))

# Confusion matrix
cm = confusion_matrix(y_test, y_pred)
print("\nConfusion Matrix:")
print(cm)

# ## 6. Feature Importance

feature_importance = pd.DataFrame({
    'feature': feature_cols,
    'importance': model.feature_importances_
}).sort_values('importance', ascending=False)

print("\nFeature Importance:")
display(feature_importance)

# ## 7. Save Model

model_path = Path('../models/churn_model.pkl')
joblib.dump(model, model_path)
print(f"\nModel saved to {model_path}")

# ## 8. Conclusions

# - Model achieves X% accuracy
# - Most important feature: Y
# - Ready for deployment

# ═══════════════════════════════════════════
# WORKFLOW 3: AUTOMATED REPORTING
# ═══════════════════════════════════════════

# ──────────────────────────────────────────────────────────
# Notebook: 07_weekly_report.ipynb
# ──────────────────────────────────────────────────────────

# # 📈 Weekly Sales Report
#
# **Generated:** {current_date}

from datetime import datetime
import pandas as pd
import matplotlib.pyplot as plt

current_date = datetime.now().strftime("%Y-%m-%d")

# ## Executive Summary

# Load data
df = pd.read_csv(DATA_DIR / 'sales_this_week.csv')

# Calculate metrics
total_sales = df['amount'].sum()
total_orders = len(df)
avg_order_value = total_sales / total_orders

# Display metrics
metrics_html = f"""
<div style="display: flex; justify-content: space-around;">
    <div style="text-align: center; padding: 20px; background: #e3f2fd; border-radius: 5px;">
        <h2>${total_sales:,.2f}</h2>
        <p>Total Sales</p>
    </div>
    <div style="text-align: center; padding: 20px; background: #e8f5e9; border-radius: 5px;">
        <h2>{total_orders:,}</h2>
        <p>Total Orders</p>
    </div>
    <div style="text-align: center; padding: 20px; background: #fff3e0; border-radius: 5px;">
        <h2>${avg_order_value:.2f}</h2>
        <p>Avg Order Value</p>
    </div>
</div>
"""

from IPython.display import HTML
display(HTML(metrics_html))

# ## Sales Trend

# Visualizations...

# ## Recommendations

# - Action item 1
# - Action item 2
# - Action item 3

# Export to HTML
# jupyter nbconvert --to html --no-input 07_weekly_report.ipynb

# ═══════════════════════════════════════════
# WORKFLOW 4: COLLABORATION
# ═══════════════════════════════════════════

"""
Team Collaboration Best Practices:
──────────────────────────────────────────────────────────────

1. Use Shared Repository
   - GitHub/GitLab for version control
   - Clear folder structure
   - README with setup instructions

2. Code Review Process
   - Pull requests for changes
   - Review notebooks before merge
   - Run "Restart & Run All" before PR

3. Documentation Standards
   - Consistent notebook structure
   - Clear markdown documentation
   - Inline comments for complex code

4. Shared Environments
   - requirements.txt or environment.yml
   - Docker containers
   - JupyterHub for team

5. Communication
   - Use GitHub issues
   - Document decisions in notebooks
   - Weekly sync meetings
"""

# ═══════════════════════════════════════════
# WORKFLOW 5: PRESENTATION
# ═══════════════════════════════════════════

# Convert notebook to slides
# jupyter nbconvert notebook.ipynb --to slides --post serve

# Slide types (cell metadata):
# - slide: New slide
# - sub-slide: Sub-slide
# - fragment: Fragment (appears on click)
# - skip: Skip this cell
# - notes: Speaker notes

# Add to cell metadata:
# View → Cell Toolbar → Slideshow

print("Workflows demonstrated!")
```

---

<div align="center">

## ❓ Troubleshooting

</div>

### Common Issues & Solutions 🔧

```bash
# ═══════════════════════════════════════════
# COMMON PROBLEMS & SOLUTIONS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   KERNEL ISSUES                            ║
╚════════════════════════════════════════════════════════════╝

Problem: Kernel won't start
─────────────────────────────────────────────────────────────
Solution 1: Restart Jupyter
jupyter notebook stop
jupyter notebook

Solution 2: Clear kernel cache
jupyter kernelspec list
jupyter kernelspec remove python3
pip install ipykernel
python -m ipykernel install --user

Solution 3: Check Python path
import sys
print(sys.executable)

Problem: Kernel keeps dying
─────────────────────────────────────────────────────────────
Cause: Out of memory
Solution:
- Reduce dataset size
- Use data sampling
- Clear variables: %reset
- Use chunks: pd.read_csv(..., chunksize=10000)

Problem: Wrong kernel/environment
─────────────────────────────────────────────────────────────
Solution: Install kernel in environment
conda activate myenv
pip install ipykernel
python -m ipykernel install --user --name myenv --display-name "Python (myenv)"

╔════════════════════════════════════════════════════════════╗
║                   CONNECTION ISSUES                        ║
╚════════════════════════════════════════════════════════════╝

Problem: Can't connect to Jupyter
─────────────────────────────────────────────────────────────
Solution 1: Check if server is running
jupyter notebook list

Solution 2: Try different port
jupyter notebook --port 8889

Solution 3: Clear browser cache
- Clear cookies for localhost
- Try incognito mode
- Try different browser

Problem: Token/password not working
─────────────────────────────────────────────────────────────
Solution 1: Get token
jupyter notebook list
# Look for token in URL

Solution 2: Reset password
jupyter notebook password

Solution 3: Disable token (local only!)
jupyter notebook --NotebookApp.token=''

╔════════════════════════════════════════════════════════════╗
║                   IMPORT ERRORS                            ║
╚════════════════════════════════════════════════════════════╝

Problem: ModuleNotFoundError
─────────────────────────────────────────────────────────────
Solution 1: Install package
!pip install package_name

Solution 2: Check Python path
import sys
print(sys.path)
sys.path.append('/path/to/module')

Solution 3: Verify correct kernel
# Check which Python
import sys
print(sys.executable)

Problem: Import works in terminal, not in Jupyter
─────────────────────────────────────────────────────────────
Cause: Different Python environments
Solution: Install in correct environment
# Activate environment first
conda activate myenv
# Then start Jupyter from that environment
jupyter notebook

╔════════════════════════════════════════════════════════════╗
║                   DISPLAY ISSUES                           ║
╚════════════════════════════════════════════════════════════╝

Problem: Plots not showing
─────────────────────────────────────────────────────────────
Solution: Enable inline backend
%matplotlib inline
import matplotlib.pyplot as plt
plt.plot([1, 2, 3])
plt.show()

Problem: Widget not displaying
─────────────────────────────────────────────────────────────
Solution: Enable widgets
jupyter nbextension enable --py widgetsnbextension
# Restart Jupyter

Problem: Large output truncated
─────────────────────────────────────────────────────────────
Solution: Adjust settings
from IPython.display import display
pd.set_option('display.max_rows', 100)
pd.set_option('display.max_columns', None)

╔════════════════════════════════════════════════════════════╗
║                   PERFORMANCE ISSUES                       ║
╚════════════════════════════════════════════════════════════╝

Problem: Notebook is slow
─────────────────────────────────────────────────────────────
Solution 1: Clear output
Cell → All Output → Clear

Solution 2: Limit output
from IPython.display import display
for i in range(1000):
    if i < 10:  # Only show first 10
        print(i)

Solution 3: Use %%capture
%%capture
# Code that produces lots of output
for i in range(1000):
    print(i)

Problem: Out of memory
─────────────────────────────────────────────────────────────
Solution 1: Delete variables
del large_dataframe
import gc
gc.collect()

Solution 2: Use efficient dtypes
df['category'] = df['category'].astype('category')

Solution 3: Process in chunks
for chunk in pd.read_csv('large.csv', chunksize=10000):
    process(chunk)

╔════════════════════════════════════════════════════════════╗
║                   FILE ISSUES                              ║
╚════════════════════════════════════════════════════════════╝

Problem: Notebook won't open
─────────────────────────────────────────────────────────────
Solution 1: Check file format
# Try to load as JSON
import json
with open('notebook.ipynb') as f:
    data = json.load(f)

Solution 2: Recover from checkpoint
# Look in .ipynb_checkpoints/
cp .ipynb_checkpoints/notebook-checkpoint.ipynb notebook.ipynb

Problem: Notebook corrupted
─────────────────────────────────────────────────────────────
Solution: Use nbformat to fix
pip install nbformat
python -c "import nbformat; nb = nbformat.read('notebook.ipynb', as_version=4); nbformat.write(nb, 'fixed.ipynb')"

Problem: Can't save notebook
─────────────────────────────────────────────────────────────
Solution 1: Check permissions
ls -la notebook.ipynb
chmod 644 notebook.ipynb

Solution 2: Save as new file
File → Save As → new_name.ipynb

Solution 3: Download and re-upload
File → Download as → Notebook

╔════════════════════════════════════════════════════════════╗
║                   VERSION CONFLICTS                        ║
╚════════════════════════════════════════════════════════════╝

Problem: Incompatible package versions
─────────────────────────────────────────────────────────────
Solution 1: Create new environment
conda create -n fresh python=3.9
conda activate fresh
pip install jupyter numpy pandas matplotlib

Solution 2: Use requirements.txt
pip install -r requirements.txt

Solution 3: Update all packages
pip install --upgrade jupyter numpy pandas matplotlib

Problem: Jupyter version mismatch
─────────────────────────────────────────────────────────────
Solution: Upgrade Jupyter
pip install --upgrade jupyter
pip install --upgrade notebook

╔════════════════════════════════════════════════════════════╗
║                   DEBUGGING TIPS                           ║
╚════════════════════════════════════════════════════════════╝

Enable verbose error messages:
─────────────────────────────────────────────────────────────
%xmode Verbose

Check Jupyter log:
─────────────────────────────────────────────────────────────
# In terminal where Jupyter is running
# Look for error messages

Test in clean environment:
─────────────────────────────────────────────────────────────
# Create minimal test case
import sys
print(f"Python: {sys.version}")
print(f"Executable: {sys.executable}")

import jupyter
print(f"Jupyter: {jupyter.__version__}")

Common fix: Restart everything
─────────────────────────────────────────────────────────────
1. Kernel → Restart
2. Save work
3. Close browser
4. Stop Jupyter server (Ctrl+C in terminal)
5. Start fresh: jupyter notebook

╔════════════════════════════════════════════════════════════╗
║                   GETTING HELP                             ║
╚════════════════════════════════════════════════════════════╝

Resources:
─────────────────────────────────────────────────────────────
• Jupyter Discourse: https://discourse.jupyter.org/
• Stack Overflow: [jupyter-notebook] tag
• GitHub Issues: https://github.com/jupyter/notebook/issues
• Documentation: https://jupyter-notebook.readthedocs.io/

When asking for help, include:
─────────────────────────────────────────────────────────────
• Jupyter version: jupyter --version
• Python version: python --version
• Operating system
• Full error message
• Steps to reproduce
• What you've tried
```

---

<div align="center">

## 📚 Quick Reference

</div>

### Essential Commands & Shortcuts 🚀

```bash
# ═══════════════════════════════════════════
# QUICK REFERENCE GUIDE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   STARTING JUPYTER                         ║
╚════════════════════════════════════════════════════════════╝

jupyter notebook                # Start Jupyter Notebook
jupyter lab                     # Start JupyterLab
jupyter notebook --port 8889    # Custom port
jupyter notebook --no-browser   # Don't open browser
jupyter notebook list           # List running servers
jupyter notebook stop 8888      # Stop server

╔════════════════════════════════════════════════════════════╗
║                   TOP 10 SHORTCUTS                         ║
╚════════════════════════════════════════════════════════════╝

1. Shift + Enter    Run cell and move to next
2. Ctrl + Enter     Run cell and stay
3. Esc              Enter command mode
4. Enter            Enter edit mode
5. A                Insert cell above (command mode)
6. B                Insert cell below (command mode)
7. M                Change to markdown (command mode)
8. Y                Change to code (command mode)
9. D, D             Delete cell (command mode, press D twice)
10. Ctrl + S        Save notebook

╔════════════════════════════════════════════════════════════╗
║                   TOP 10 MAGIC COMMANDS                    ║
╚════════════════════════════════════════════════════════════╝

1. %timeit           Time single line
2. %%time            Time entire cell
3. %matplotlib inline Display plots inline
4. %load_ext         Load extension
5. %run              Run external script
6. %debug            Debug after error
7. %who              List variables
8. %pwd              Print working directory
9. !command          Run shell command
10. %%writefile      Write cell to file

╔════════════════════════════════════════════════════════════╗
║                   COMMON PATTERNS                          ║
╚════════════════════════════════════════════════════════════╝

Standard imports:
─────────────────────────────────────────────────────────────
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

Configuration:
─────────────────────────────────────────────────────────────
%matplotlib inline
pd.set_option('display.max_columns', None)
sns.set_style('whitegrid')

Load data:
─────────────────────────────────────────────────────────────
df = pd.read_csv('data.csv')
df.head()
df.info()
df.describe()

Quick plot:
─────────────────────────────────────────────────────────────
df['column'].hist()
df.plot(x='col1', y='col2')
sns.scatterplot(data=df, x='col1', y='col2', hue='category')
```

---

<div align="center">

## 🎓 Resources & Learning

</div>

### Continue Your Jupyter Journey 📖

```
📘 Official Documentation
   • Jupyter Notebook: https://jupyter-notebook.readthedocs.io/
   • JupyterLab: https://jupyterlab.readthedocs.io/
   • IPython: https://ipython.readthedocs.io/

📗 Tutorials & Courses
   • DataCamp: Jupyter Notebook Tutorial
   • Real Python: Jupyter Notebook Guide
   • Coursera: Jupyter Notebooks for Data Science
   • YouTube: Corey Schafer - Jupyter Tutorials

📙 Books
   • Python for Data Analysis (Wes McKinney)
   • Jupyter Notebook for Beginners (DataCamp)
   • Teaching and Learning with Jupyter

🛠️ Tools & Extensions
   • nbviewer: https://nbviewer.jupyter.org/
   • Binder: https://mybinder.org/
   • Google Colab: https://colab.research.google.com/
   • Kaggle Notebooks: https://www.kaggle.com/code

💬 Community
   • Jupyter Discourse: https://discourse.jupyter.org/
   • Stack Overflow: [jupyter-notebook] tag
   • Reddit: r/Jupyter
   • Twitter: @ProjectJupyter

🎨 Example Notebooks
   • Gallery: https://github.com/jupyter/jupyter/wiki
   • Awesome Jupyter: https://github.com/markusschanta/awesome-jupyter
```

---

<div align="center">

## 🎯 Summary

</div>

### Key Takeaways 💡

```bash
╔════════════════════════════════════════════════════════════╗
║                   REMEMBER                                 ║
╚════════════════════════════════════════════════════════════╝

1. Jupyter = Interactive Computing
   • Mix code, text, and visualizations
   • Iterate quickly
   • Share and reproduce

2. Master the Basics
   • Learn keyboard shortcuts
   • Understand cell types
   • Use markdown for documentation
   • Organize with sections

3. Use Magic Commands
   • %timeit for performance
   • %debug for debugging
   • !command for shell
   • %%writefile for saving

4. Follow Best Practices
   • Clear structure
   • Top-to-bottom execution
   • Version control
   • Clear output before commit

5. Leverage Extensions
   • Table of contents
   • Variable inspector
   • Code formatter
   • Themes

6. JupyterLab for Power Users
   • Multi-document interface
   • Integrated terminal
   • File browser
   • Modern UI

7. Collaborate Effectively
   • Share notebooks
   • Use nbviewer
   • Document well
   • Version control

"Jupyter Notebooks: Where exploration becomes insight,
and insight becomes action." ✨
```

---

<div align="center">

**Built with 📓 by MrDib, for Jupyter enthusiasts**

_Remember: "The best way to learn is to experiment interactively!"_ 🚀

**Happy Jupyter-ing!** 💻
