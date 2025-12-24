<div align="center">

# 🚀 The Ultimate Neovim Guide

<img src="https://img.shields.io/badge/Neovim-57A143?style=for-the-badge&logo=neovim&logoColor=white" alt="Neovim">
<img src="https://img.shields.io/badge/Vim-019733?style=for-the-badge&logo=vim&logoColor=white" alt="Vim">
<img src="https://img.shields.io/badge/Level-Zero_to_Hero-blue?style=for-the-badge" alt="Level">

### _From "How do I exit this thing?" to "I am the keyboard ninja"_ ⚔️

**Because clicking is for people with too much time** 🎯

</div>

---

## 📚 Table of Contents

- [🎯 Understanding Vim/Neovim](#-understanding-vimneovim)
- [🚀 Modes Explained](#-modes-explained)
- [🚪 Exiting (The Most Important Part!)](#-exiting-the-most-important-part)
- [↔️ Movement (WASD for Hackers)](#️-movement-wasd-for-hackers)
- [✏️ Editing Like a Pro](#️-editing-like-a-pro)
- [📋 Copy, Cut & Paste (Yank Gang)](#-copy-cut--paste-yank-gang)
- [🔍 Search & Replace](#-search--replace)
- [📂 File Operations](#-file-operations)
- [🧱 Windows & Splits](#-windows--splits)
- [🗂️ Tabs Management](#️-tabs-management)
- [🎯 Visual Mode](#-visual-mode)
- [🎤 Macros & Automation](#-macros--automation)
- [⚙️ Configuration](#️-configuration)
- [🔌 Plugin Management](#-plugin-management)
- [💡 Pro Tips & Tricks](#-pro-tips--tricks)

---

<div align="center">

## 🎯 Understanding Vim/Neovim

_Before we dive in, let's understand what we're dealing with_

</div>

### What is Neovim?

Neovim is a hyperextensible, modernized fork of Vim - one of the most powerful text editors ever created. It's:

- ✅ **Keyboard-centric** - Your hands never leave the home row
- ✅ **Modal** - Different modes for different tasks (genius!)
- ✅ **Lightning fast** - Edit at the speed of thought
- ✅ **Highly customizable** - Make it yours
- ✅ **Ubiquitous** - Available on every platform
- ✅ **Free & Open Source** - Community-driven

### Why Learn Neovim?

```
📈 Speed       → Edit files 10x faster once mastered
🧠 Efficiency  → Never touch the mouse again
💪 Power       → Unlimited customization possibilities
🌍 Universal   → Works everywhere (servers, containers, etc.)
😎 Flex        → Look cool in front of other developers
🔥 Fun         → Actually enjoyable once you "get it"
```

> **💡 Reality Check:** There's a learning curve, but it's worth it! You'll be slow for a week, normal in a month, and a speed demon in three months. 🏃‍♂️💨

---

<div align="center">

## 🚀 Modes Explained

_The secret sauce of Vim's power_

</div>

Vim/Neovim operates in different **modes**. This is what makes it different (and powerful!). Think of modes like different tools in a toolbox - each one specialized for a specific task.

### The Four Essential Modes

<div align="center">

| Mode           | Purpose                     | How to Enter                 | Key Indicator          |
| -------------- | --------------------------- | ---------------------------- | ---------------------- |
| **NORMAL** 🎯  | Navigate & execute commands | `ESC` or `Ctrl+[`            | Nothing (default mode) |
| **INSERT** ✏️  | Type text normally          | `i`, `a`, `o`, `I`, `A`, `O` | `-- INSERT --`         |
| **VISUAL** 🎨  | Select text                 | `v`, `V`, `Ctrl+v`           | `-- VISUAL --`         |
| **COMMAND** ⌨️ | Execute commands            | `:`                          | `:` at bottom          |

</div>

### Mode Navigation Quick Reference

```
┌───────────────────────────────────────────────────────────────┐
│                                                               │
│  NORMAL MODE (Default - the hub of everything)                │
│      │                                                        │
│      ├─→ i/a/o  ────→  INSERT MODE (typing text)              │
│      │                     │                                  │
│      │                     └─→ ESC ──→ back to NORMAL         │
│      │                                                        │
│      ├─→ v/V/Ctrl+v ──→  VISUAL MODE (selecting)              │
│      │                     │                                  │
│      │                     └─→ ESC ──→ back to NORMAL         │
│      │                                                        │
│      └─→ :  ────────────→  COMMAND MODE (commands)            │
│                              │                                │
│                              └─→ Enter/ESC ──→ back to NORMAL │
│                                                               │
└───────────────────────────────────────────────────────────────┘
```

### Entering INSERT Mode (Multiple Ways!)

```vim
i     → Insert BEFORE cursor
a     → Insert AFTER cursor (append)
I     → Insert at BEGINNING of line
A     → Insert at END of line
o     → Open new line BELOW and insert
O     → Open new line ABOVE and insert
s     → Delete character and insert
S     → Delete line and insert
```

**Example Use Cases:**

```
Cursor is here: "Hello|World"

i → "Hello|World"     (insert before cursor)
a → "HelloW|orld"     (insert after cursor)
I → "|HelloWorld"     (beginning of line)
A → "HelloWorld|"     (end of line)
o → "HelloWorld"      (new line below)
    "|"
```

> **💡 Pro Tip:** When in doubt, press `ESC` multiple times. It's safe and always brings you back to NORMAL mode! 🛡️

---

<div align="center">

## 🚪 Exiting (The Most Important Part!)

_So you can actually leave when you're done_ 😅

</div>

### The Exit Commands Everyone Needs to Know

```vim
:q          → Quit (fails if unsaved changes)
:q!         → Quit WITHOUT saving (force quit)
:w          → Write (save) the file
:wq         → Write and quit (save + exit)
:x          → Write and quit (only if changes made)
ZZ          → Save and quit (same as :wq, but faster!)
ZQ          → Quit without saving (same as :q!)

:wq!        → Force write and quit (if file is read-only)
:qa         → Quit all windows
:qa!        → Quit all windows without saving
:wqa        → Write and quit all windows
```

### The "I'm Stuck!" Rescue Guide

```
┌─────────────────────────────────────────────────────┐
│  😰 STUCK? FOLLOW THIS FLOWCHART:                   │
├─────────────────────────────────────────────────────┤
│                                                     │
│  1. Mash ESC 3-5 times                              │
│     (You're now in NORMAL mode, guaranteed)         │
│                                                     │
│  2. Type: :q!                                       │
│     (Quit without saving)                           │
│                                                     │
│  3. Press: Enter                                    │
│     (Execute the command)                           │
│                                                     │
│  🎉 You're free!                                    │
│                                                     │
└─────────────────────────────────────────────────────┘
```

> **⚠️ Common Mistake:** Typing `:q!` while in INSERT mode just types it into your file! Always press `ESC` first!

---

<div align="center">

## ↔️ Movement (WASD for Hackers)

_Navigate at the speed of thought_ 🏃‍♂️💨

</div>

### Basic Movement (The Home Row)

```vim
     k
     ↑           h → left
h ←     → l      j → down
     ↓           k → up
     j           l → right
```

**Mnemonic:**

- `j` looks like a down arrow ⬇️
- `k` points up ⬆️
- `h` is on the left ⬅️
- `l` is on the right ➡️

---

### Word Movement (The Fast Way)

```vim
w        → jump forward to START of next word
W        → jump forward by WORD (ignores punctuation)
e        → jump forward to END of next word
E        → jump forward to END of WORD (ignores punctuation)
b        → jump backward to START of previous word
B        → jump backward by WORD (ignores punctuation)
ge       → jump backward to END of previous word
```

**Example:**

```
The quick-brown fox jumps over the lazy_dog.
^   ^     ^     ^   ^     ^    ^   ^    ^

w = next word start
e = next word end
b = previous word start
```

---

### Line Movement (Precision Navigation)

```vim
0        → Jump to START of line (column 0)
^        → Jump to FIRST non-blank character of line
$        → Jump to END of line
g_       → Jump to LAST non-blank character of line
```

**Visual Example:**

```
    Hello World
^   ^          ^  ^
0   ^          $  g_
```

---

### Screen Movement (Big Jumps)

```vim
H        → Move to TOP of screen (High)
M        → Move to MIDDLE of screen (Middle)
L        → Move to BOTTOM of screen (Low)

gg       → Go to FIRST line of file
G        → Go to LAST line of file
:42      → Go to line 42 (any number)
42G      → Go to line 42 (alternative)

Ctrl+u   → Scroll UP half page
Ctrl+d   → Scroll DOWN half page
Ctrl+b   → Scroll UP full page (Back)
Ctrl+f   → Scroll DOWN full page (Forward)

zt       → Move current line to TOP of screen
zz       → Move current line to MIDDLE of screen
zb       → Move current line to BOTTOM of screen
```

---

### Character Search (Ninja Mode Unlocked) 🥷

```vim
f<char>  → Find next occurrence of <char> on line
F<char>  → Find previous occurrence of <char> on line
t<char>  → Move cursor TO just before next <char>
T<char>  → Move cursor TO just before previous <char>

;        → Repeat last f/F/t/T motion forward
,        → Repeat last f/F/t/T motion backward
```

**Example:**

```
The quick brown fox jumps

fx    → Move to 'x' in "fox"
;     → Move to next 'x' (none in this line)
,     → Move back to previous 'x'
```

---

### Advanced Movement (Power User Territory)

```vim
%        → Jump to matching bracket/parenthesis/brace
*        → Search for word under cursor (forward)
#        → Search for word under cursor (backward)
gd       → Go to local declaration
gD       → Go to global declaration

{        → Jump to previous paragraph
}        → Jump to next paragraph
(        → Jump to previous sentence
)        → Jump to next sentence

''       → Jump back to previous cursor position
`.       → Jump to last edit location
g;       → Go to older change position
g,       → Go to newer change position
```

---

### Movement with Counts (Multiply Your Power!)

```vim
5j       → Move DOWN 5 lines
10w      → Jump forward 10 words
3fx      → Find 3rd occurrence of 'x' on line
2}       → Jump forward 2 paragraphs
```

> **💡 Pro Tip:** Combine movements with counts! `3w` moves 3 words forward, `5j` moves 5 lines down. You can even do `2fe` to jump to the 2nd 'e' on the line! 🚀

---

<div align="center">

## ✏️ Editing Like a Pro

_The real power of Vim_ ⚡

</div>

### Basic Editing Commands

```vim
x        → Delete character under cursor
X        → Delete character before cursor
r<char>  → Replace character with <char>
R        → Enter REPLACE mode (overwrite)

s        → Substitute character (delete + insert)
S        → Substitute line (delete line + insert)

u        → Undo last change
Ctrl+r   → Redo last undo
U        → Undo all changes on line
.        → Repeat last change (SUPER POWERFUL!)
```

---

### Delete Commands (Cut Operation)

In Vim, **delete = cut** (deleted text goes to clipboard!)

```vim
dd       → Delete (cut) entire line
D        → Delete from cursor to end of line (same as d$)
dw       → Delete word
de       → Delete to end of word
db       → Delete word backward
d$       → Delete to end of line
d0       → Delete to beginning of line
dG       → Delete to end of file
dgg      → Delete to beginning of file
```

**With Counts:**

```vim
2dd      → Delete 2 lines
3dw      → Delete 3 words
5d}      → Delete 5 paragraphs forward
```

---

### Change Commands (Delete + Insert)

The `c` command **deletes** text and puts you in **INSERT** mode!

```vim
cc       → Change entire line
C        → Change from cursor to end of line
cw       → Change word
ce       → Change to end of word
c$       → Change to end of line
c0       → Change to beginning of line
ciw      → Change inner word (doesn't need cursor at start!)
caw      → Change a word (includes surrounding space)
```

**Text Object Changes (MIND BLOWING!):**

```vim
ci"      → Change inside quotes
ci'      → Change inside single quotes
ci(      → Change inside parentheses
ci[      → Change inside square brackets
ci{      → Change inside curly braces
cit      → Change inside HTML/XML tag
```

**Example:**

```
"Hello World"
     ^
    cursor here

ci"  → Deletes "Hello World" and enters INSERT mode
```

---

### Text Objects (The Secret Weapon) 🎯

Text objects let you operate on **logical blocks** of text!

**Inner (`i`) vs Around (`a`):**

- `i` = **inside** (excludes delimiters)
- `a` = **around** (includes delimiters)

```vim
iw       → inner word
aw       → a word (includes space)
is       → inner sentence
as       → a sentence
ip       → inner paragraph
ap       → a paragraph

i"       → inside double quotes
a"       → around double quotes (includes quotes)
i'       → inside single quotes
a'       → around single quotes
i(       → inside parentheses
a(       → around parentheses (includes parens)
i[       → inside brackets
a[       → around brackets
i{       → inside braces
a{       → around braces
it       → inside tag (HTML/XML)
at       → around tag
```

**Practical Examples:**

```vim
diw      → Delete inner word
daw      → Delete a word (including spaces)
ci(      → Change inside parentheses
da"      → Delete around quotes (includes quotes)
yit      → Yank inside HTML tag
vip      → Visual select inner paragraph
```

**Real World Example:**

```javascript
function hello(name) {
    console.log("Hello, " + name);
}

Cursor anywhere in "name" → ciw → changes "name"
Cursor in function braces  → di{ → deletes function body
Cursor in string          → ci" → changes string content
```

---

### Join & Split Lines

```vim
J        → Join current line with next line
gJ       → Join without adding space
:split   → Split line at cursor position (command mode)
```

---

### Indentation

```vim
>>       → Indent line right
<<       → Indent line left
==       → Auto-indent line
=G       → Auto-indent from cursor to end of file
gg=G     → Auto-indent entire file

5>>      → Indent 5 lines right
```

---

### Case Changes

```vim
~        → Toggle case of character
g~~      → Toggle case of entire line
guu      → Make line lowercase
gUU      → Make line uppercase

guiw     → Make inner word lowercase
gUiw     → Make inner word UPPERCASE
```

---

<div align="center">

## 📋 Copy, Cut & Paste (Yank Gang)

_Master the clipboard like a boss_ 👑

</div>

### Understanding Registers (Vim's Clipboard System)

Vim has **multiple clipboards** called **registers**!

```vim
"        → The unnamed register (default)
"0       → The yank register (last yank)
"1-"9    → Delete history (last 9 deletes)
"+       → System clipboard (copy/paste with OS)
"*       → Primary selection (X11 systems)
"_       → Black hole register (delete without saving)
```

---

### Yank (Copy) Commands

```vim
yy       → Yank (copy) entire line
Y        → Yank entire line (same as yy)
yw       → Yank word
ye       → Yank to end of word
y$       → Yank to end of line
y0       → Yank to beginning of line
yiw      → Yank inner word
yaw      → Yank a word
yi"      → Yank inside quotes
ya(      → Yank around parentheses
yG       → Yank to end of file
ygg      → Yank to beginning of file
```

**With Counts:**

```vim
3yy      → Yank 3 lines
5yw      → Yank 5 words
```

---

### Paste Commands

```vim
p        → Paste AFTER cursor/line
P        → Paste BEFORE cursor/line
gp       → Paste after and move cursor after pasted text
gP       → Paste before and move cursor after pasted text
```

**Examples:**

```vim
yy       → Copy current line
p        → Paste below current line
P        → Paste above current line

yw       → Copy word
p        → Paste after cursor
P        → Paste before cursor
```

---

### Using System Clipboard

To copy to/from system clipboard:

```vim
"+yy     → Copy line to system clipboard
"+p      → Paste from system clipboard
"+yiw    → Copy word to system clipboard
```

**Make it easier - Add to your config:**

```vim
" Use system clipboard by default
set clipboard=unnamedplus
```

Now `yy` and `p` work with system clipboard! 🎉

---

### Cut (Delete) Commands

Remember: In Vim, **delete = cut**!

```vim
dd       → Cut entire line
dw       → Cut word
diw      → Cut inner word
di"      → Cut inside quotes
```

Then paste with `p` or `P`!

---

### Register Operations

```vim
:reg     → View all registers and their contents
"ayy     → Yank line to register 'a'
"ap      → Paste from register 'a'
"bdiw    → Delete word to register 'b'
```

**Practical Example:**

```vim
"ayy     → Copy line to register 'a'
"byy     → Copy another line to register 'b'
"ap      → Paste from register 'a'
"bp      → Paste from register 'b'
```

---

### Black Hole Register (Delete Without Storing)

```vim
"_dd     → Delete line without saving to register
"_diw    → Delete word without saving
```

Use this when you don't want to overwrite your clipboard!

---

<div align="center">

## 🔍 Search & Replace

_Find anything, change everything_ 🎯

</div>

### Basic Search

```vim
/pattern     → Search forward for pattern
?pattern     → Search backward for pattern
n            → Go to next search result
N            → Go to previous search result
*            → Search forward for word under cursor
#            → Search backward for word under cursor

/\cpattern   → Case-insensitive search
/\Cpattern   → Case-sensitive search (force)
:noh         → Clear search highlighting
```

**Examples:**

```vim
/hello       → Find "hello"
n            → Next occurrence
N            → Previous occurrence
*            → Search for word under cursor
```

---

### Search Options

```vim
:set ignorecase    → Case-insensitive search
:set smartcase     → Case-sensitive only if capitals used
:set incsearch     → Show matches as you type
:set hlsearch      → Highlight all matches
```

---

### Find & Replace (Substitute Command)

The power of `:substitute` (`:s`):

```vim
:s/old/new/          → Replace first occurrence on line
:s/old/new/g         → Replace all occurrences on line
:s/old/new/gc        → Replace with confirmation
:%s/old/new/g        → Replace in entire file
:%s/old/new/gi       → Replace in entire file (case-insensitive)
:5,12s/old/new/g     → Replace in lines 5-12
:.,$s/old/new/g      → Replace from current line to end
```

**Flags:**

- `g` = global (all occurrences on line)
- `c` = confirm each replacement
- `i` = case-insensitive
- `I` = case-sensitive

**Examples:**

```vim
:%s/foo/bar/g        → Replace all "foo" with "bar"
:%s/foo/bar/gc       → Replace with confirmation
:5,20s/old/new/g     → Replace in lines 5-20
:%s/\s\+$//g         → Remove trailing whitespace (entire file)
```

---

### Advanced Search & Replace

```vim
:%s/\<word\>/new/g   → Replace whole word only
:%s/old/new/gn       → Count matches (don't replace)
:g/pattern/d         → Delete all lines matching pattern
:v/pattern/d         → Delete all lines NOT matching pattern
```

**Delete empty lines:**

```vim
:g/^$/d              → Delete all empty lines
```

**Delete lines containing "TODO":**

```vim
:g/TODO/d
```

---

<div align="center">

## 📂 File Operations

_Manage files like a terminal wizard_ 🧙‍♂️

</div>

### Opening & Saving Files

```vim
:e filename          → Edit (open) file
:e!                  → Reload current file (discard changes)
:w                   → Write (save) file
:w filename          → Save as filename
:w!                  → Force write (override read-only)
:sav filename        → Save as and continue editing new file
:q                   → Quit
:wq                  → Write and quit
:x                   → Write (only if changed) and quit
:qa                  → Quit all windows
:wqa                 → Write and quit all
```

---

### File Browsing

```vim
:e .                 → Open file browser (current directory)
:Ex                  → Open file explorer
:Sex                 → Open file explorer in horizontal split
:Vex                 → Open file explorer in vertical split
:browse e            → Open file browser dialog
```

**In file browser (netrw):**

```vim
<Enter>              → Open file/directory
-                    → Go up one directory
d                    → Create new directory
%                    → Create new file
D                    → Delete file/directory
R                    → Rename file
```

---

### Buffer Management

A **buffer** is an opened file in memory.

```vim
:ls                  → List all buffers
:bnext or :bn        → Go to next buffer
:bprevious or :bp    → Go to previous buffer
:buffer N or :b N    → Go to buffer N
:bfirst              → Go to first buffer
:blast               → Go to last buffer
:bd                  → Delete current buffer (close file)
:bd!                 → Force delete buffer
:bd 3                → Delete buffer 3
:%bd                 → Delete all buffers
:%bd|e#              → Delete all buffers except current
```

**Quick Navigation:**

```vim
Ctrl+^               → Switch to alternate buffer (last file)
:b part<Tab>         → Switch to buffer matching "part"
```

---

### File Information

```vim
Ctrl+g               → Show file information
g Ctrl+g             → Show detailed cursor position
:file                → Show current file name
:file newname        → Rename current buffer
```

---

<div align="center">

## 🧱 Windows & Splits

_Multitask like a boss_ 🪟

</div>

### Creating Splits

```vim
:split or :sp        → Horizontal split (same file)
:vsplit or :vs       → Vertical split (same file)
:split file.txt      → Horizontal split with file.txt
:vsplit file.txt     → Vertical split with file.txt
:new                 → Horizontal split with new file
:vnew                → Vertical split with new file

Ctrl+w s             → Horizontal split (same file)
Ctrl+w v             → Vertical split (same file)
```

---

### Navigating Between Splits

```vim
Ctrl+w h             → Move to left split
Ctrl+w j             → Move to split below
Ctrl+w k             → Move to split above
Ctrl+w l             → Move to right split

Ctrl+w w             → Cycle through splits
Ctrl+w W             → Cycle backwards through splits
Ctrl+w p             → Go to previous split
```

**Mnemonic:** `Ctrl+w` then use the movement keys (`h`, `j`, `k`, `l`)!

---

### Resizing Splits

```vim
Ctrl+w =             → Make all splits equal size
Ctrl+w _             → Maximize current split height
Ctrl+w |             → Maximize current split width
Ctrl+w +             → Increase current split height
Ctrl+w -             → Decrease current split height
Ctrl+w >             → Increase current split width
Ctrl+w <             → Decrease current split width

:resize 20           → Set height to 20 lines
:vertical resize 80  → Set width to 80 columns
```

**With Counts:**

```vim
10 Ctrl+w +          → Increase height by 10
20 Ctrl+w >          → Increase width by 20
```

---

### Moving & Rearranging Splits

```vim
Ctrl+w H             → Move split to far left (vertical)
Ctrl+w J             → Move split to bottom (horizontal)
Ctrl+w K             → Move split to top (horizontal)
Ctrl+w L             → Move split to far right (vertical)

Ctrl+w r             → Rotate splits downward/rightward
Ctrl+w R             → Rotate splits upward/leftward
Ctrl+w x             → Exchange current split with next
```

---

### Closing Splits

```vim
:q                   → Close current split
Ctrl+w q             → Close current split
Ctrl+w c             → Close current split (keeps buffer)
:only or Ctrl+w o    → Close all splits except current
```

---

<div align="center">

## 🗂️ Tabs Management

_Browser-style tabs in Vim!_ 🗂️

</div>

### Creating & Opening Tabs

```vim
:tabnew              → New tab
:tabnew file.txt     → Open file in new tab
:tabe file.txt       → Edit file in new tab
:tabedit file.txt    → Edit file in new tab
:tabfind file.txt    → Find and open file in new tab
```

---

### Navigating Tabs

```vim
gt                   → Go to next tab
gT                   → Go to previous tab
:tabn or :tabnext    → Go to next tab
:tabp or :tabprev    → Go to previous tab
:tabfirst            → Go to first tab
:tablast             → Go to last tab
3gt                  → Go to tab number 3
```

---

### Managing Tabs

```vim
:tabclose or :tabc   → Close current tab
:tabonly or :tabo    → Close all other tabs
:tabs                → List all tabs
:tabm 0              → Move current tab to position 0 (first)
:tabm                → Move current tab to last position
:tabm 3              → Move current tab to position 3
```

---

<div align="center">

## 🎯 Visual Mode

_Select text like a ninja_ 🥷

</div>

### Entering Visual Mode

```vim
v                    → Character-wise visual mode
V                    → Line-wise visual mode
Ctrl+v               → Block-wise visual mode (column selection!)
gv                   → Re-select last visual selection
```

---

### Visual Mode Operations

Once in visual mode, move cursor to select, then:

```vim
d or x               → Delete selection
y                    → Yank (copy) selection
c                    → Change selection (delete + insert)
r                    → Replace all characters with one char
u                    → Make selection lowercase
U                    → Make selection UPPERCASE
~                    → Toggle case
>                    → Indent right
<                    → Indent left
=                    → Auto-indent
```

---

### Visual Block Mode (Column Editing) 🎨

```vim
Ctrl+v               → Enter visual block mode
I                    → Insert before block
A                    → Append after block
c                    → Change block
d                    → Delete block
```

**Practical Example - Add prefix to multiple lines:**

```
line 1
line 2
line 3

1. Ctrl+v          (visual block)
2. jj              (select 3 lines)
3. I               (insert before block)
4. prefix_         (type your prefix)
5. ESC             (apply to all lines)

Result:
prefix_line 1
prefix_line 2
prefix_line 3
```

---

### Visual Mode Text Objects

In visual mode, you can use text objects:

```vim
viw                  → Visual select inner word
vaw                  → Visual select a word
vi"                  → Visual select inside quotes
va(                  → Visual select around parentheses
vip                  → Visual select inner paragraph
```

---

<div align="center">

## 🎤 Macros & Automation

_Automate repetitive tasks like magic_ ✨

</div>

### Recording Macros

```vim
q<letter>            → Start recording macro to register <letter>
q                    → Stop recording
@<letter>            → Play macro from register <letter>
@@                   → Repeat last executed macro
```

**Example Workflow:**

```vim
qa                   → Start recording to register 'a'
<do your edits>      → Perform actions
q                    → Stop recording
@a                   → Play macro
5@a                  → Play macro 5 times
```

---

### Practical Macro Examples

**Example 1: Add semicolons to multiple lines**

```javascript
// Original:
let x = 5
let y = 10
let z = 15

// Steps:
qa               → Start recording to 'a'
A;               → Go to end of line, add semicolon
ESC              → Back to normal mode
j                → Move down one line
q                → Stop recording
2@a              → Apply to next 2 lines

// Result:
let x = 5;
let y = 10;
let z = 15;
```

**Example 2: Surround words with quotes**

```vim
qa               → Start recording
ciw              → Change inner word
"<Ctrl+r>""      → Type quote, paste deleted text, close quote
ESC              → Exit insert mode
q                → Stop recording
```

---

### Running Macros on Multiple Lines

```vim
:5,10norm @a     → Run macro 'a' on lines 5-10
:%norm @a        → Run macro 'a' on all lines
:'<,'>norm @a    → Run macro 'a' on visual selection
```

---

### Viewing & Editing Macros

```vim
:reg a           → View contents of register 'a'
"ap              → Paste macro 'a' to edit it
^[               → Represents ESC (Ctrl+v ESC to type it)
```

---

<div align="center">

## ⚙️ Configuration

_Make Neovim truly yours_ 🎨

</div>

### Configuration File Location

```bash
# Neovim config file
~/.config/nvim/init.vim    # Vimscript version
~/.config/nvim/init.lua    # Lua version (recommended!)

# Traditional Vim config
~/.vimrc
```

---

### Essential Settings (init.vim)

```vim
" ═══════════════════════════════════════════
" Essential Settings - Copy These!
" ═══════════════════════════════════════════

" Line numbers
set number                  " Show line numbers
set relativenumber          " Relative line numbers (amazing for movement!)

" Indentation
set tabstop=4              " Tab width
set shiftwidth=4           " Indent width
set expandtab              " Use spaces instead of tabs
set smartindent            " Smart auto-indenting
set autoindent             " Copy indent from current line

" Search
set ignorecase             " Case-insensitive search
set smartcase              " Case-sensitive if uppercase present
set incsearch              " Show matches as you type
set hlsearch               " Highlight search results

" UI Improvements
set mouse=a                " Enable mouse support
set cursorline             " Highlight current line
set showmatch              " Show matching brackets
set termguicolors          " True color support
set scrolloff=8            " Keep 8 lines visible above/below cursor
set signcolumn=yes         " Always show sign column
set colorcolumn=80         " Show column guide at 80 chars

" Performance
set updatetime=50          " Faster completion
set timeoutlen=500         " Faster key sequence completion

" System
set clipboard=unnamedplus  " Use system clipboard
set noswapfile            " Disable swap files
set nobackup              " Disable backup files
set undofile              " Enable persistent undo
set splitright            " Vertical splits open to right
set splitbelow            " Horizontal splits open below

" ═══════════════════════════════════════════
" Key Remappings
" ═══════════════════════════════════════════

" Set leader key to space
let mapleader = " "

" Better save & quit
nnoremap <leader>w :w<CR>
nnoremap <leader>q :q<CR>
nnoremap <leader>x :x<CR>

" Clear search highlighting
nnoremap <leader>h :noh<CR>

" Better window navigation
nnoremap <C-h> <C-w>h
nnoremap <C-j> <C-w>j
nnoremap <C-k> <C-w>k
nnoremap <C-l> <C-w>l

" Buffer navigation
nnoremap <Tab> :bnext<CR>
nnoremap <S-Tab> :bprevious<CR>

" Move lines up/down
nnoremap <A-j> :m .+1<CR>==
nnoremap <A-k> :m .-2<CR>==
vnoremap <A-j> :m '>+1<CR>gv=gv
vnoremap <A-k> :m '<-2<CR>gv=gv

" Better indenting
vnoremap < <gv
vnoremap > >gv

" ESC alternatives
inoremap jk <ESC>
inoremap kj <ESC>
```

---

### Essential Settings (init.lua)

```lua
-- ═══════════════════════════════════════════
-- Essential Settings (Lua Version)
-- ═══════════════════════════════════════════

local opt = vim.opt

-- Line numbers
opt.number = true
opt.relativenumber = true

-- Indentation
opt.tabstop = 4
opt.shiftwidth = 4
opt.expandtab = true
opt.smartindent = true

-- Search
opt.ignorecase = true
opt.smartcase = true
opt.incsearch = true
opt.hlsearch = true

-- UI
opt.mouse = "a"
opt.cursorline = true
opt.termguicolors = true
opt.scrolloff = 8
opt.signcolumn = "yes"
opt.colorcolumn = "80"

-- Performance
opt.updatetime = 50
opt.timeoutlen = 500

-- System
opt.clipboard = "unnamedplus"
opt.swapfile = false
opt.backup = false
opt.undofile = true
opt.splitright = true
opt.splitbelow = true

-- ═══════════════════════════════════════════
-- Key Mappings (Lua)
-- ═══════════════════════════════════════════

vim.g.mapleader = " "

local keymap = vim.keymap.set

-- Save & quit
keymap("n", "<leader>w", ":w<CR>")
keymap("n", "<leader>q", ":q<CR>")
keymap("n", "<leader>x", ":x<CR>")

-- Clear search
keymap("n", "<leader>h", ":noh<CR>")

-- Window navigation
keymap("n", "<C-h>", "<C-w>h")
keymap("n", "<C-j>", "<C-w>j")
keymap("n", "<C-k>", "<C-w>k")
keymap("n", "<C-l>", "<C-w>l")

-- Buffer navigation
keymap("n", "<Tab>", ":bnext<CR>")
keymap("n", "<S-Tab>", ":bprevious<CR>")

-- Better indenting
keymap("v", "<", "<gv")
keymap("v", ">", ">gv")
```

---

<div align="center">

## 🔌 Plugin Management

_Supercharge your Neovim_ 🚀

</div>

### Installing a Plugin Manager

**Lazy.nvim (Recommended - Modern & Fast)**

```lua
-- ~/.config/nvim/init.lua

-- Bootstrap lazy.nvim
local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
if not vim.loop.fs_stat(lazypath) then
  vim.fn.system({
    "git",
    "clone",
    "--filter=blob:none",
    "https://github.com/folke/lazy.nvim.git",
    "--branch=stable",
    lazypath,
  })
end
vim.opt.rtp:prepend(lazypath)

-- Setup lazy.nvim
require("lazy").setup({
  -- Plugins go here
})
```

---

### Essential Plugins (Starter Pack)

```lua
-- ~/.config/nvim/lua/plugins.lua

return {
  -- Color scheme
  {
    "folke/tokyonight.nvim",
    lazy = false,
    priority = 1000,
    config = function()
      vim.cmd([[colorscheme tokyonight]])
    end,
  },

  -- File explorer
  {
    "nvim-tree/nvim-tree.lua",
    dependencies = { "nvim-tree/nvim-web-devicons" },
    config = function()
      require("nvim-tree").setup()
    end,
  },

  -- Fuzzy finder
  {
    "nvim-telescope/telescope.nvim",
    dependencies = { "nvim-lua/plenary.nvim" },
    config = function()
      require("telescope").setup()
    end,
  },

  -- Syntax highlighting
  {
    "nvim-treesitter/nvim-treesitter",
    build = ":TSUpdate",
    config = function()
      require("nvim-treesitter.configs").setup({
        ensure_installed = { "lua", "vim", "javascript", "python" },
        highlight = { enable = true },
      })
    end,
  },

  -- Auto-completion
  {
    "hrsh7th/nvim-cmp",
    dependencies = {
      "hrsh7th/cmp-nvim-lsp",
      "hrsh7th/cmp-buffer",
      "L3MON4D3/LuaSnip",
    },
  },

  -- LSP (Language Server Protocol)
  {
    "neovim/nvim-lspconfig",
  },

  -- Git integration
  {
    "lewis6991/gitsigns.nvim",
    config = function()
      require("gitsigns").setup()
    end,
  },

  -- Status line
  {
    "nvim-lualine/lualine.nvim",
    dependencies = { "nvim-tree/nvim-web-devicons" },
    config = function()
      require("lualine").setup()
    end,
  },

  -- Auto pairs
  {
    "windwp/nvim-autopairs",
    config = function()
      require("nvim-autopairs").setup()
    end,
  },

  -- Comment plugin
  {
    "numToStr/Comment.nvim",
    config = function()
      require("Comment").setup()
    end,
  },
}
```

---

### Popular Color Schemes

```lua
-- Dark themes
"folke/tokyonight.nvim"        -- Beautiful Tokyo Night theme
"catppuccin/nvim"              -- Soothing pastel theme
"rebelot/kanagawa.nvim"        -- Inspired by Japanese art
"EdenEast/nightfox.nvim"       -- Fox-themed colorscheme
"navarasu/onedark.nvim"        -- One Dark Pro

-- Light themes
"projekt0n/github-nvim-theme"  -- GitHub theme
"folke/tokyonight.nvim"        -- Has light variant
```

---

### Managing Plugins with Lazy.nvim

```vim
:Lazy              " Open plugin manager UI
:Lazy sync         " Install/update/clean plugins
:Lazy update       " Update plugins
:Lazy clean        " Remove unused plugins
:Lazy profile      " Show loading times
```

---

<div align="center">

## 💡 Pro Tips & Tricks

_Level up from good to great_ 🌟

</div>

### Workflow Tips

```vim
" ═══════════════════════════════════════════
" Repeat Commands
" ═══════════════════════════════════════════

.              → Repeat last change (SUPER POWERFUL!)
@:             → Repeat last command-line command
&              → Repeat last :substitute

" Example:
" 1. ciw hello ESC    (change word to "hello")
" 2. Move to another word
" 3. Press .          (changes that word to "hello" too!)

" ═══════════════════════════════════════════
" Marks & Jumps
" ═══════════════════════════════════════════

m<letter>      → Set mark at cursor position
'<letter>      → Jump to mark (line)
`<letter>      → Jump to mark (exact position)
:marks         → Show all marks
''             → Jump back to previous position
`.             → Jump to last change
g;             → Jump to older change
g,             → Jump to newer change

" Special marks (automatic):
''             → Last jump position
'.             → Last change position
'^             → Last insert position
'[             → Start of last change
']             → End of last change

" ═══════════════════════════════════════════
" Folding (Code Folding)
" ═══════════════════════════════════════════

zf             → Create fold (in visual mode)
za             → Toggle fold
zc             → Close fold
zo             → Open fold
zR             → Open all folds
zM             → Close all folds
zj             → Move to next fold
zk             → Move to previous fold

" ═══════════════════════════════════════════
" Multiple Cursors (Poor Man's Version)
" ═══════════════════════════════════════════

" 1. Search for pattern: /word
" 2. Change first: cgn newword ESC
" 3. Press . to change next occurrence
" 4. Press n. to skip and change next
" 5. Repeat step 3 or 4 as needed

" ═══════════════════════════════════════════
" Number Manipulation
" ═══════════════════════════════════════════

Ctrl+a         → Increment number under cursor
Ctrl+x         → Decrement number under cursor
g Ctrl+a       → Increment numbers in sequence (visual mode)

" Example:
" 1. Select lines with Ctrl+v
" 2. Press g Ctrl+a
" Result: 1, 2, 3, 4, 5...

" ═══════════════════════════════════════════
" Spell Checking
" ═══════════════════════════════════════════

:set spell            → Enable spell check
:set spell!           → Toggle spell check
:set spelllang=en_us  → Set language
]s                    → Next misspelled word
[s                    → Previous misspelled word
z=                    → Suggest corrections
zg                    → Add word to dictionary
zug                   → Undo add to dictionary
```

---

### Advanced Editing Tricks

```vim
" ═══════════════════════════════════════════
" Global Commands
" ═══════════════════════════════════════════

:g/pattern/command    → Run command on lines matching pattern
:v/pattern/command    → Run command on lines NOT matching

" Examples:
:g/TODO/d             → Delete all lines with "TODO"
:g/^$/d               → Delete all empty lines
:v/error/d            → Delete lines without "error"
:g/pattern/y A        → Yank matching lines to register A
:g/pattern/t$         → Copy matching lines to end of file

" ═══════════════════════════════════════════
" Sort Lines
" ═══════════════════════════════════════════

:sort             → Sort lines
:sort!            → Reverse sort
:sort u           → Sort and remove duplicates
:sort n           → Numeric sort

" ═══════════════════════════════════════════
" External Commands
" ═══════════════════════════════════════════

:!command         → Run shell command
:r !command       → Read command output into file
:%!command        → Filter file through command

" Examples:
:!ls              → Run ls command
:r !date          → Insert current date
:%!python -m json.tool  → Format JSON
:%!prettier --stdin-filepath %  → Format with prettier

" ═══════════════════════════════════════════
" Recording Into Insert Mode
" ═══════════════════════════════════════════

" Technique: Use Ctrl+r to paste in insert mode
qa                → Start recording
i                 → Enter insert mode
<text>            → Type text
Ctrl+r <letter>   → Paste from register
ESC               → Exit insert mode
q                 → Stop recording

" ═══════════════════════════════════════════
" Quickfix List
" ═══════════════════════════════════════════

:copen            → Open quickfix window
:cclose           → Close quickfix window
:cnext or :cn     → Next item
:cprev or :cp     → Previous item
:cfirst           → First item
:clast            → Last item
```

---

### Time-Saving Aliases

Add to your `init.vim`:

```vim
" ═══════════════════════════════════════════
" Command Aliases (Life Savers!)
" ═══════════════════════════════════════════

" Typo corrections
command! W w
command! Q q
command! Wq wq
command! WQ wq

" Quick commands
command! So source $MYVIMRC        " :So to reload config
command! E Explore                 " :E to explore files

" Format entire file
nnoremap <leader>f gg=G``

" Delete all buffers except current
command! BufOnly %bd|e#|bd#

" Remove trailing whitespace
command! StripTrailingWhitespace %s/\s\+$//e
nnoremap <leader>s :StripTrailingWhitespace<CR>

" Toggle line numbers
nnoremap <leader>n :set number! relativenumber!<CR>

" Open config file quickly
nnoremap <leader>v :e $MYVIMRC<CR>
```

---

### Debugging Your Config

```vim
" Check where option was last set
:verbose set tabstop?

" Check all loaded plugins
:scriptnames

" Check keymapping
:map <key>
:nmap <key>    " Normal mode
:imap <key>    " Insert mode
:vmap <key>    " Visual mode

" Profile startup time
:profile start profile.log
:profile func *
:profile file *
" Restart nvim
:profile pause

" Check health
:checkhealth
```

---

### The "Oh No!" Recovery Commands

```vim
" ═══════════════════════════════════════════
" Disaster Recovery
" ═══════════════════════════════════════════

:earlier 15m      → Go back 15 minutes in undo history
:later 10m        → Go forward 10 minutes in undo history
:earlier 5        → Undo 5 changes
:undo 100         → Go to undo state 100

" Recover from swap file
:recover          → Recover from swap file
:e! <filename>    → Reload file (discard all changes)

" If you mess up visual selection
<ESC><ESC>        → Double ESC to clear

" If terminal is frozen
Ctrl+q            → Unfreeze (if Ctrl+s froze it)

" If you're completely lost
:qa!              → Quit all without saving (nuclear option)
```

---

<div align="center">

## 🎓 Learning Path & Resources

_Your journey to Vim mastery_ 📚

</div>

### Step-by-Step Learning Plan

```
┌──────────────────────────────────────────────────────────┐
│  Week 1: Survival Mode                                   │
├──────────────────────────────────────────────────────────┤
│  ✓ Learn basic navigation (h,j,k,l)                      │
│  ✓ Master modes (Normal, Insert, Visual, Command)        │
│  ✓ Practice entering/exiting                             │
│  ✓ Basic editing (i, a, o, ESC, :wq)                     │
│  Goal: Don't panic, can exit Vim!                        │
└──────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────┐
│  Week 2-3: Getting Comfortable                           │
├──────────────────────────────────────────────────────────┤
│  ✓ Word/line movement (w, b, 0, $)                       │
│  ✓ Delete, change, yank (d, c, y)                        │
│  ✓ Search (/pattern, n, N)                               │
│  ✓ Undo/redo (u, Ctrl+r)                                 │
│  Goal: Edit files without leaving Vim                    │
└──────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────┐
│  Week 4-6: Power User Territory                          │
├──────────────────────────────────────────────────────────┤
│  ✓ Text objects (ciw, di", va()                          │
│  ✓ Visual mode mastery                                   │
│  ✓ Macros (q, @)                                         │
│  ✓ Splits & buffers                                      │
│  ✓ Configure your init.vim                               │
│  Goal: Faster than mouse-based editing                   │
└──────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────┐
│  Month 3+: Vim Wizard Status                             │
├──────────────────────────────────────────────────────────┤
│  ✓ Plugin ecosystem                                      │
│  ✓ LSP & completion                                      │
│  ✓ Custom functions & commands                           │
│  ✓ Advanced text manipulation                            │
│  Goal: Can't imagine using anything else                 │
└──────────────────────────────────────────────────────────┘
```

---

### Essential Resources

```
📚 BUILT-IN TUTORIALS
──────────────────────────────────────────────
:Tutor             → Interactive Vim tutor (30 minutes)
:help              → Built-in documentation
:help user-manual  → Complete user manual

🌐 WEBSITES & GUIDES
──────────────────────────────────────────────
🔗 vim.fandom.com/wiki/Vim_Tips_Wiki
   - Comprehensive tips & tricks

🔗 vimcasts.org
   - Video tutorials on specific topics

🔗 vimgolf.com
   - Practice Vim challenges (fun!)

🔗 openvim.com
   - Interactive tutorial in browser

🔗 vim-adventures.com
   - Learn Vim through gaming

📖 BOOKS
──────────────────────────────────────────────
📕 Practical Vim (Drew Neil)
   - THE book for intermediate users

📕 Modern Vim (Drew Neil)
   - Covers Neovim features

📕 Learning the vi and Vim Editors
   - Comprehensive reference

🎥 YOUTUBE CHANNELS
──────────────────────────────────────────────
🎬 ThePrimeagen
   - Advanced Vim techniques

🎬 TJ DeVries
   - Neovim core maintainer

🎬 Josean Martinez
   - Modern Neovim setup guides

🎬 chris@machine
   - Neovim from scratch series

💬 COMMUNITIES
──────────────────────────────────────────────
💬 r/neovim (Reddit)
💬 r/vim (Reddit)
💬 Neovim Discord
💬 Vi StackExchange
```

---

### Practice Exercises

```vim
" ═══════════════════════════════════════════
" Daily Vim Workout (5-10 minutes)
" ═══════════════════════════════════════════

" Exercise 1: Navigation Drill
" - Open any file
" - Use only h,j,k,l for 5 minutes
" - No arrow keys!

" Exercise 2: Text Object Challenge
" - Find text in quotes: "example"
" - Without moving cursor: ci"new text"
" - Find text in parens: (example)
" - Without moving cursor: ci(new text)

" Exercise 3: Macro Practice
" - Take a list of items
" - Record macro to format them
" - Apply to all items

" Exercise 4: Visual Block Mode
" - Create a column of numbers
" - Use Ctrl+v to select column
" - Try I, A, c operations

" Exercise 5: Search & Replace
" - Find/replace specific pattern
" - Use :s/// with different flags
" - Try global commands :g//
```

---

<div align="center">

## 🏆 Congratulations!

_You've completed the Ultimate Neovim Guide!_ 🎉

</div>

**You now know:**

- ✅ All essential Vim/Neovim modes
- ✅ Navigation like a keyboard ninja
- ✅ Editing techniques that save hours
- ✅ Copy/paste/cut operations
- ✅ Search & replace mastery
- ✅ File & buffer management
- ✅ Window splits & tabs
- ✅ Visual mode superpowers
- ✅ Macro automation
- ✅ Configuration & plugins
- ✅ Pro tips & tricks

---

<div align="center">

### Remember: The Vim Way

> **"Do one thing, do it well, and compose it with other tools"**

</div>

Vim isn't just an editor - it's a **language for editing text**. Every command is a word, and you combine them into sentences that describe what you want to do.

```
Verb       +    Text Object     =     Action
───────        ─────────────          ───────
d (delete)    iw (inner word)     → Delete word
c (change)    i" (inside quotes)  → Change inside quotes
y (yank)      ap (a paragraph)    → Copy paragraph
```

---

### The Journey Continues

```
🎯 Your Vim Journey:

Day 1:    😰 "How do I exit this thing?!"
Week 1:   😐 "This is slower than my old editor..."
Month 1:  🙂 "Oh, I get it now"
Month 3:  😊 "This is pretty cool!"
Month 6:  😎 "I'm never going back"
Year 1:   🧙‍♂️ "I have become one with the keyboard"
```

---

### Keep Learning!

**Daily Practice:**

- Use Vim for all text editing
- Learn one new command per day
- Read `:help` when stuck
- Join the community
- Share your knowledge

**The Vim community's motto:**

> "You never stop learning Vim. You just get progressively less bad at it." 😄

---

<div align="center">

### Quick Reference Card

```vim
╔══════════════════════════════════════════════════════╗
║  VIM CHEAT SHEET - Print This Out!                   ║
╠══════════════════════════════════════════════════════╣
║  BASICS                                              ║
║  ─────────────────────────────────────────────────   ║
║  i, a, o      → Insert mode                          ║
║  ESC          → Normal mode                          ║
║  :wq          → Save & quit                          ║
║  :q!          → Quit without saving                  ║
║                                                      ║
║  MOVEMENT                                            ║
║  ─────────────────────────────────────────────────   ║
║  h,j,k,l      → ←,↓,↑,→                              ║
║  w, b         → Next/prev word                       ║
║  0, $         → Start/end of line                    ║
║  gg, G        → Start/end of file                    ║
║                                                      ║
║  EDITING                                             ║
║  ─────────────────────────────────────────────────   ║
║  dd           → Delete line                          ║
║  yy           → Copy line                            ║
║  p, P         → Paste after/before                   ║
║  u, Ctrl+r    → Undo/Redo                            ║
║  .            → Repeat last change                   ║
║                                                      ║
║  TEXT OBJECTS                                        ║
║  ─────────────────────────────────────────────────   ║
║  ciw          → Change inner word                    ║
║  di"          → Delete inside quotes                 ║
║  ya(          → Yank around parentheses              ║
║                                                      ║
║  SEARCH                                              ║
║  ─────────────────────────────────────────────────   ║
║  /pattern     → Search forward                       ║
║  n, N         → Next/prev result                     ║
║  :%s/old/new/g → Replace all                         ║
╚══════════════════════════════════════════════════════╝
```

</div>

---

<div align="center">

Built with 💚 by [MrDib](https://github.com/ThisIsDibakar), for future Vim wizards 🚀

_Now go forth and edit at the speed of thought!_ ⚡

**Happy Vimming!** 🚀

</div>
