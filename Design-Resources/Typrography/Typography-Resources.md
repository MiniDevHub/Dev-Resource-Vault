<div align="center">

# 🔤 Typography Resources & Tools

### _Where fonts become art and Comic Sans goes to die_ ✨

![Typography](https://img.shields.io/badge/Typography-Everything-blue?style=for-the-badge)
![Fonts](https://img.shields.io/badge/Fonts-1000+-purple?style=for-the-badge)
![Quality](https://img.shields.io/badge/Quality-Premium-gold?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🆓 Free Font Resources](#-free-font-resources)
- [💎 Premium Font Foundries](#-premium-font-foundries)
- [👨‍💻 Programming Fonts](#-programming-fonts)
- [🎨 Display & Decorative Fonts](#-display--decorative-fonts)
- [🔀 Variable Fonts](#-variable-fonts)
- [🛠️ Typography Tools](#️-typography-tools)
- [🎯 Font Pairing](#-font-pairing)
- [⚡ Performance & Loading](#-performance--loading)
- [📐 Typography Systems](#-typography-systems)
- [💡 Best Practices](#-best-practices)
- [📜 Licensing Guide](#-licensing-guide)

---

<div align="center">

## 🆓 Free Font Resources

_High-quality fonts that won't cost you a penny_ 💰

</div>

### 🏆 Google Fonts

```
🔗 https://fonts.google.com
💰 FREE & Open Source
```

**The King of Free Fonts:**

```
✨ Why It's #1:
├── 1,500+ font families
├── 100% free & open source
├── Easy implementation
├── Variable fonts included
├── Self-hosting allowed
├── No attribution required
├── Regular updates
└── Excellent documentation

📊 Statistics:
• 200+ trillion pageviews/year
• Used by 60%+ of websites
• Trusted by everyone
• CDN hosted globally

🎯 Best Fonts from Google Fonts:
├── Inter (UI/UX king)
├── Roboto (Android standard)
├── Open Sans (most popular)
├── Montserrat (geometric beauty)
├── Poppins (friendly sans)
├── Playfair Display (elegant serif)
├── Source Sans Pro (Adobe's gift)
└── Lato (humanist sans)

⚡ Performance Tips:
• Only load weights you use
• Subset to needed languages
• Use font-display: swap
• Preload critical fonts
• Consider self-hosting
```

**Implementation:**

```html
<!-- ═══════════════════════════════════════════════════════════
     GOOGLE FONTS - BASIC IMPLEMENTATION
     ═══════════════════════════════════════════════════════════ -->

<!-- Method 1: CDN (Easiest) -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
  href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap"
  rel="stylesheet"
/>

<style>
  body {
    font-family: "Inter", sans-serif;
  }
</style>

<!-- Method 2: @import (Not Recommended - Slower) -->
<style>
  @import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap");

  body {
    font-family: "Inter", sans-serif;
  }
</style>

<!-- Method 3: Optimized with Preload -->
<link
  rel="preload"
  as="style"
  href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap"
/>
<link
  rel="stylesheet"
  href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap"
/>
```

**Advanced Usage:**

```css
/* ═══════════════════════════════════════════════════════════
   GOOGLE FONTS - ADVANCED OPTIMIZATION
   ═══════════════════════════════════════════════════════════ */

/* Load only specific characters (subsetting) */
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;700&text=HelloWrd&display=swap");

/* Variable font (better performance) */
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap");

/* With italic support */
@import url("https://fonts.googleapis.com/css2?family=Inter:ital,wght@0,400;0,700;1,400;1,700&display=swap");

/* Multiple fonts optimized */
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&family=Fira+Code:wght@400;500&display=swap");
```

> **💡 Pro Tip:** Always use `display=swap` to prevent invisible text while fonts load (FOIT - Flash of Invisible Text)!

---

### 📦 Fontsource

```
🔗 https://fontsource.org
💰 FREE (Self-hosting solution)
```

**Why Self-Host Google Fonts:**

```
🚀 Benefits of Fontsource:
├── Full control over fonts
├── Better performance (no external requests)
├── GDPR compliant
├── No Google tracking
├── Works offline
├── Version locked (no surprises)
└── NPM/Yarn integration

⚠️ Trade-offs:
├── Bundle size increase
├── Manual updates needed
└── Initial setup required

💡 When to Use:
✅ Privacy concerns (GDPR)
✅ Offline apps
✅ Performance optimization
✅ Full control needed
```

**Installation & Usage:**

```bash
# ═══════════════════════════════════════════════════════════
# FONTSOURCE - NPM INSTALLATION
# ═══════════════════════════════════════════════════════════

# Install specific font
npm install @fontsource/inter

# Install with specific weights
npm install @fontsource/inter@4.5.0

# Install variable font version
npm install @fontsource-variable/inter
```

```javascript
// ═══════════════════════════════════════════════════════════
// FONTSOURCE - IMPLEMENTATION
// ═══════════════════════════════════════════════════════════

// Import in your app entry point (index.js, App.js, etc.)

// Method 1: Import all weights and styles
import '@fontsource/inter';

// Method 2: Import specific weights (better performance)
import '@fontsource/inter/400.css';
import '@fontsource/inter/700.css';

// Method 3: Variable font (best performance)
import '@fontsource-variable/inter';

// Method 4: With italics
import '@fontsource/inter/400.css';
import '@fontsource/inter/400-italic.css';
import '@fontsource/inter/700.css';
import '@fontsource/inter/700-italic.css';

// Then use in CSS
body {
  font-family: 'Inter', sans-serif;
}
```

**React/Next.js Example:**

```javascript
// ═══════════════════════════════════════════════════════════
// app/layout.tsx (Next.js 13+ App Router)
// ═══════════════════════════════════════════════════════════

import '@fontsource-variable/inter';

export default function RootLayout({ children }) {
  return (
    <html lang="en" style={{ fontFamily: "'Inter Variable', sans-serif" }}>
      <body>{children}</body>
    </html>
  );
}

// ═══════════════════════════════════════════════════════════
// Or in global CSS (globals.css)
// ═══════════════════════════════════════════════════════════

@import '@fontsource-variable/inter';

body {
  font-family: 'Inter Variable', sans-serif;
}
```

---

### 🐰 Bunny Fonts

```
🔗 https://fonts.bunny.net
💰 FREE (Privacy-friendly CDN)
```

**Features:**

```
🔒 Privacy-First Google Fonts CDN:
├── Drop-in Google Fonts replacement
├── GDPR compliant
├── No tracking
├── No logs
├── Open source
├── European servers
└── Same API as Google Fonts

🎯 Simply replace:
fonts.googleapis.com → fonts.bunny.net
fonts.gstatic.com → fonts.bunny.net

💡 Use Case:
Perfect for European websites concerned about GDPR
```

**Implementation:**

```html
<!-- Original Google Fonts -->
<link
  href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap"
  rel="stylesheet"
/>

<!-- Bunny Fonts (just change domain!) -->
<link
  href="https://fonts.bunny.net/css2?family=Inter:wght@400;700&display=swap"
  rel="stylesheet"
/>
```

> **🔒 Privacy Tip:** Bunny Fonts is perfect for European websites where GDPR compliance matters!

---

### 💎 Adobe Fonts

```
🔗 https://fonts.adobe.com
💰 FREE with Creative Cloud ($10+/month)
```

**Features:**

```
🎨 Adobe's Font Service:
├── 20,000+ fonts
├── No pageview limits
├── Desktop & web fonts
├── High-quality foundries
├── Automatic sync
├── Adobe integration
└── Commercial use included

🏆 Quality Foundries:
├── Adobe Originals
├── Monotype
├── Linotype
├── ITC
└── Many more

📦 What You Get:
• Desktop fonts (sync to Creative Cloud)
• Web fonts (embed on websites)
• All weights & styles
• New fonts added monthly
• No attribution required
```

**Web Implementation:**

```html
<!-- ═══════════════════════════════════════════════════════════
     ADOBE FONTS WEB IMPLEMENTATION
     ═══════════════════════════════════════════════════════════ -->

<!-- 1. Create Web Project on fonts.adobe.com -->
<!-- 2. Add fonts to project -->
<!-- 3. Get embed code (looks like this): -->

<link rel="stylesheet" href="https://use.typekit.net/abc1234.css" />

<style>
  body {
    font-family: "source-sans-pro", sans-serif;
    font-weight: 400;
    font-style: normal;
  }

  h1 {
    font-family: "freight-display-pro", serif;
    font-weight: 700;
    font-style: normal;
  }
</style>
```

**Is Adobe Fonts Worth It?**

```
💰 Creative Cloud: $10/month (Photography Plan) or $55/month (All Apps)

✅ Worth It If:
• You use Adobe apps already
• Need premium fonts
• Want desktop + web fonts
• Commercial projects
• Quality matters

⚠️ Not Worth It If:
• Google Fonts sufficient
• Budget constraints
• Don't use Adobe apps
• Simple projects only
```

---

### 🎨 More Free Font Sources

<div align="center">

| Source                 |  Fonts  |  Quality   | Best For                |
| :--------------------- | :-----: | :--------: | :---------------------- |
| **Font Library**       | 1,000+  |  ⭐⭐⭐⭐  | Open source community   |
| **Fontshare**          |  100+   | ⭐⭐⭐⭐⭐ | Professional free fonts |
| **DaFont**             | 60,000+ |   ⭐⭐⭐   | Display fonts, quantity |
| **1001 Fonts**         | 40,000+ |   ⭐⭐⭐   | Huge variety            |
| **Font Squirrel**      | 1,500+  |  ⭐⭐⭐⭐  | Commercial use safe     |
| **Uncut Sans**         |    1    | ⭐⭐⭐⭐⭐ | Geometric sans          |
| **Beautiful Web Type** |   40+   | ⭐⭐⭐⭐⭐ | Curated Google Fonts    |

</div>

---

#### 🔥 Fontshare (Must-Check!)

```
🔗 https://www.fontshare.com
💰 100% FREE (by Indian Type Foundry)
```

**Why It's Amazing:**

```
✨ Professional Quality, Zero Cost:
├── Created by Indian Type Foundry (ITF)
├── 100+ high-quality fonts
├── 100% free for personal & commercial
├── Variable fonts included
├── Web fonts ready
├── Growing collection
└── No hidden fees ever

🎯 Standout Fonts:
├── Satoshi (geometric perfection)
├── Cabinet Grotesk (editorial elegance)
├── Clash Display (bold display)
├── General Sans (versatile workhorse)
└── Switzer (Swiss-inspired)

💡 Secret Weapon:
These fonts look premium because they ARE premium -
just made free by generous foundry!
```

**Usage:**

```html
<!-- Download from Fontshare.com, then self-host -->
<link href="/fonts/satoshi.css" rel="stylesheet" />

<style>
  body {
    font-family: "Satoshi", sans-serif;
  }
</style>
```

---

<div align="center">

## 💎 Premium Font Foundries

_When you need that extra polish_ ✨

</div>

### Understanding Font Licensing

```
📜 License Types:

Desktop License:
├── Use in design files
├── Print materials
├── PDFs
└── Not for websites

Web License:
├── Embed on websites
├── Usually by pageviews
├── Monthly/yearly fee
└── Or one-time purchase

App License:
├── Mobile apps
├── Desktop software
├── Per-app basis
└── Usually one-time fee

Server License:
├── Email templates
├── Generated PDFs
├── Server-side rendering
└── Variable pricing

💡 Most Common:
Desktop + Web combo licenses
Check license before purchasing!
```

---

### 🏆 Top Premium Foundries

#### Fonts.com

```
🔗 https://www.fonts.com
💰 Varies ($29-$299+ per font)
```

**Features:**

```
🏢 Monotype's Marketplace:
├── 150,000+ fonts
├── All major foundries
├── Desktop & web licensing
├── Commercial use
└── Professional quality

🎯 Famous Fonts:
├── Helvetica (the classic)
├── Frutiger (readable beauty)
├── Avenir (elegant geometric)
├── Futura (modernist icon)
└── Univers (Swiss perfection)

💰 Pricing:
• Desktop: $29-$99 per weight
• Web: $10-$40/month or $100-$400 one-time
• Packages available
```

---

#### MyFonts

```
🔗 https://www.myfonts.com
💰 Varies ($10-$500+ per font)
```

**Features:**

```
🎨 Huge Font Marketplace:
├── 280,000+ fonts
├── Independent foundries
├── Try before you buy
├── WhatTheFont tool (identify fonts)
└── Regular sales

🔥 Hot New Fonts section
📊 Bestsellers list
💡 What The Font (font identifier)

💰 Pricing Strategy:
• Watch for sales (50%+ off common)
• Newsletter deals
• Bundle offers
• Family packages
```

---

#### Adobe Fonts (Premium)

```
Already covered above - included with Creative Cloud
```

---

#### Hoefler&Co.

```
🔗 https://www.typography.com
💰 Premium ($199-$1,499+ per font)
```

**Features:**

```
👔 The Pinnacle of Typography:
├── Luxury fonts
├── Used by major brands
├── Exceptional quality
├── Limited but perfect collection
└── Worth every penny

🏆 Iconic Fonts:
├── Gotham (Obama campaign, Spotify)
├── Whitney (MoMA, Medium)
├── Sentinel (CBS, Real Simple)
└── Chronicle (Martha Stewart)

💡 When to Splurge:
• Major brand identity
• High-profile projects
• When perfection matters
• Client can afford it
```

---

#### More Premium Foundries

<div align="center">

| Foundry             | Known For       | Price Range | Best For          |
| :------------------ | :-------------- | :---------: | :---------------- |
| **Lineto**          | Swiss design    |     €€€     | Editorial         |
| **Klim Type**       | Contemporary    |     €€€     | Modern brands     |
| **Commercial Type** | Editorial       |     €€      | Publishing        |
| **Grilli Type**     | Swiss modernism |     €€€     | Brand design      |
| **Colophon**        | Experimental    |     €€      | Creative projects |
| **Pangram Pangram** | Geometric       |     €€      | Modern brands     |
| **Dinamo**          | Innovative      |     €€€     | Experimental      |

</div>

> **💡 Budget Tip:** Many foundries offer trial versions. Test before you buy!

---

<div align="center">

## 👨‍💻 Programming Fonts

_Because developers deserve beautiful code too_ ⌨️

</div>

### What Makes a Great Code Font?

```
🎯 Essential Features:

1. Distinct Characters:
   • 0 vs O (zero vs capital O)
   • 1 vs l vs I (one vs lowercase L vs capital i)
   • ` vs ' (backtick vs apostrophe)

2. Programming Ligatures:
   • >= becomes ≥
   • <= becomes ≤
   • === becomes ≡
   • != becomes ≠
   • -> becomes →

3. Readability:
   • Generous letter spacing
   • Clear punctuation
   • Comfortable at small sizes
   • Easy on the eyes

4. Style:
   • Monospaced (fixed-width)
   • Professional appearance
   • Matches your taste
   • Not distracting
```

---

### 🏆 Top Free Coding Fonts

#### 🔥 Fira Code

```
🔗 https://github.com/tonsky/FiraCode
💰 FREE & Open Source
```

**Features:**

```
✨ The Gold Standard:
├── Programming ligatures (100+)
├── Based on Fira Mono
├── Excellent readability
├── Most popular coding font
├── 5 weights
└── Active development

💎 Ligatures Include:
→ >= <= === !== != && || // /* */
→ => -> <-> ++ -- ** =:= #{ }
→ And 100+ more!

🎯 Best For:
• Modern code editors
• Ligature lovers
• JavaScript/TypeScript
• General programming

⚙️ Supported Editors:
• VS Code
• Sublime Text
• Atom
• IntelliJ IDEA
• WebStorm
• And more...
```

**Installation:**

```bash
# macOS
brew tap homebrew/cask-fonts
brew install font-fira-code

# Linux
sudo apt install fonts-firacode

# Windows
# Download from GitHub releases and install manually
```

**VS Code Setup:**

```json
{
  "editor.fontFamily": "'Fira Code', Consolas, 'Courier New', monospace",
  "editor.fontLigatures": true,
  "editor.fontSize": 14,
  "editor.lineHeight": 22
}
```

---

#### ✈️ JetBrains Mono

```
🔗 https://www.jetbrains.com/lp/mono
💰 FREE & Open Source
```

**Features:**

```
🚀 By JetBrains (IntelliJ makers):
├── Designed for code
├── Increased letter height
├── Larger code-specific forms
├── 8 weights
├── Programming ligatures
└── Excellent for long coding sessions

💡 What Makes It Special:
• Increased x-height (taller lowercase)
• Larger punctuation
• Optimized for IDEs
• Scientifically designed
• Reduces eye strain

🎯 Best For:
• Long coding sessions
• JetBrains IDEs
• Developers with eye strain
• Reading comfort priority
```

---

#### 🏔️ Cascadia Code

```
🔗 https://github.com/microsoft/cascadia-code
💰 FREE & Open Source (Microsoft)
```

**Features:**

```
🪟 Microsoft's Contribution:
├── For Windows Terminal
├── Programming ligatures
├── Powerline support
├── Cursive italic variant
└── 7 weights

💎 Variants:
• Cascadia Code (with ligatures)
• Cascadia Mono (no ligatures)
• Cascadia Code PL (Powerline)

🎯 Best For:
• Windows developers
• Terminal work
• Powerline users
• Microsoft ecosystem
```

---

### 💰 Premium Coding Fonts (Worth It!)

#### 🦆 MonoLisa

```
🔗 https://www.monolisa.dev
💰 $79 (Personal) / $199 (Team)
```

**Why Developers Love It:**

```
✨ The Premium Choice:
├── Maximum reading comfort
├── Unique design
├── Excellent ligatures
├── Variable font
├── Script variants
└── Worth the investment

💡 Unique Features:
• Low vs high line positions (reduces jumping)
• Generous spacing
• Italic = cursive (beautiful!)
• Great for dyslexia
• Filter levels (customize ligatures)

💰 Is It Worth $79?
✅ Yes if:
• Code 8+ hours/day
• Value eye comfort
• Appreciate quality
• Can expense it

📊 Popular Among:
• Professional developers
• Design-minded coders
• YouTube tech influencers
• Those who tried it (seriously!)
```

---

#### 💰 Dank Mono

```
🔗 https://philpl.gumroad.com/l/dank-mono
💰 $40 (Personal)
```

**Features:**

```
🎨 The Stylish Coder:
├── Italics are *chef's kiss*
├── Unique personality
├── Programming ligatures
├── Clean & modern
└── Indie developer made

💡 What's Special:
• Italic comments look amazing
• Clean, minimal style
• Personality without distraction
• Great for demos/streaming
• Supports ligatures

🎯 Best For:
• Livestreamers
• Tutorial creators
• Style-conscious devs
• JavaScript/React devs
```

---

### 🆓 More Free Coding Fonts

<div align="center">

| Font                | Ligatures | Best Feature      | Download                                                  |
| :------------------ | :-------: | :---------------- | :-------------------------------------------------------- |
| **Hack**            |    ❌     | Classic monospace | [Link](https://sourcefoundry.org/hack/)                   |
| **Inconsolata**     |    ❌     | Humanist mono     | [Link](https://fonts.google.com/specimen/Inconsolata)     |
| **Source Code Pro** |    ❌     | Adobe quality     | [Link](https://fonts.google.com/specimen/Source+Code+Pro) |
| **Iosevka**         |    ✅     | Customizable      | [Link](https://typeof.net/Iosevka/)                       |
| **Victor Mono**     |    ✅     | Cursive italics   | [Link](https://rubjo.github.io/victor-mono/)              |
| **IBM Plex Mono**   |    ❌     | IBM design        | [Link](https://www.ibm.com/plex/)                         |
| **Commit Mono**     |    ✅     | Neutral design    | [Link](https://commitmono.com/)                           |

</div>

---

### 🔧 Font Setup for Popular Editors

**VS Code:**

```json
{
  // Best setup for Fira Code
  "editor.fontFamily": "'Fira Code', Menlo, Monaco, 'Courier New', monospace",
  "editor.fontLigatures": true,
  "editor.fontSize": 14,
  "editor.lineHeight": 22,
  "editor.letterSpacing": 0.5,
  "editor.fontWeight": "400",
  "editor.tokenColorCustomizations": {
    "textMateRules": [
      {
        "scope": "comment",
        "settings": {
          "fontStyle": "italic"
        }
      }
    ]
  }
}
```

**WebStorm/IntelliJ:**

```
Settings → Editor → Font
Font: Fira Code
Size: 14
Line height: 1.4
Enable ligatures: ✓
```

**Sublime Text:**

```json
{
  "font_face": "Fira Code",
  "font_size": 14,
  "font_options": ["gray_antialias", "subpixel_antialias"]
}
```

---

<div align="center">

## 🎨 Display & Decorative Fonts

_For headlines, heroes, and attention-grabbing moments_ 🌟

</div>

### Understanding Display Fonts

```
📏 Display vs Body Text:

Display Fonts (Headings):
├── Optimized for large sizes
├── More personality
├── Decorative details
├── Use sparingly
└── 18pt+ sizes

Body Text Fonts:
├── Optimized for small sizes
├── High readability
├── Less personality
├── Long-form reading
└── 14-18pt sizes

⚠️ Never use display fonts for body text!
```

---

### 🏆 Top Display Fonts

#### Sans-Serif Display

**Bebas Neue**

```
🔗 https://fonts.google.com/specimen/Bebas+Neue
💰 FREE
```

**Features:**

```
✨ The Heavyweight Champion:
├── All-caps display
├── Bold and impactful
├── Sports, gym, masculine vibes
├── Free on Google Fonts
└── 5 weights available

🎯 Use For:
• Sports brands
• Gym/fitness
• Masculine brands
• Impact headlines
• Call-to-actions

⚠️ Don't Use For:
• Body text (unreadable!)
• Feminine brands
• Long headlines
• Accessibility-focused sites
```

---

**Montserrat**

```
🔗 https://fonts.google.com/specimen/Montserrat
💰 FREE
```

**Features:**

```
🎨 Geometric Versatility:
├── Geometric sans-serif
├── 18 styles (9 weights + italics)
├── Clean and modern
├── Works as display AND body
├── Based on Buenos Aires signage
└── Most popular Google Font

🎯 Perfect For:
• Modern brands
• Tech companies
• Startups
• Clean designs
• Versatile projects

💡 Pro Pairing:
Montserrat (headlines) + Open Sans (body)
```

---

**Poppins**

```
🔗 https://fonts.google.com/specimen/Poppins
💰 FREE
```

**Features:**

```
✨ Friendly Geometric:
├── Geometric + humanist
├── Friendly and approachable
├── 18 styles
├── Excellent readability
├── Modern and clean
└── Supports Devanagari

🎯 Perfect For:
• SaaS products
• Modern apps
• Friendly brands
• Indian market (Devanagari)
• Clean, professional look
```

---

#### Serif Display

**Playfair Display**

```
🔗 https://fonts.google.com/specimen/Playfair+Display
💰 FREE
```

**Features:**

```
👑 Elegant Serif Display:
├── High contrast (thick & thin)
├── Transitional design
├── Elegant and sophisticated
├── 12 styles
└── Pairs well with sans

🎯 Perfect For:
• Fashion brands
• Luxury products
• Editorial design
• Elegant websites
• Feminine brands

💡 Classic Pairing:
Playfair Display (headlines) + Source Sans Pro (body)
```

---

**Merriweather**

```
🔗 https://fonts.google.com/specimen/Merriweather
💰 FREE
```

**Features:**

```
📖 Readable Serif:
├── Designed for screens
├── Slightly condensed
├── Excellent legibility
├── 8 styles
└── Great for body text too

🎯 Perfect For:
• Blogs
• Long-form content
• News sites
• Professional sites
• Readable elegance
```

---

### 🎪 Script & Decorative

<div align="center">

| Font               | Style       | Vibe         | Use For               |
| :----------------- | :---------- | :----------- | :-------------------- |
| **Pacifico**       | Script      | Surf, casual | Beach, casual brands  |
| **Dancing Script** | Script      | Handwritten  | Invitations, feminine |
| **Caveat**         | Handwriting | Natural      | Informal, sketchy     |
| **Satisfy**        | Script      | Elegant      | Weddings, elegance    |
| **Lobster**        | Display     | Bold script  | Retro, 70s            |
| **Righteous**      | Display     | Retro        | 80s, futuristic       |

</div>

> **⚠️ Warning:** Script and decorative fonts should be used VERY sparingly - headlines only, never body text!

---

<div align="center">

## 🔀 Variable Fonts

_The future of web typography_ 🚀

</div>

### Understanding Variable Fonts

```
📊 Traditional Fonts vs Variable Fonts:

Traditional:
├── Separate file per weight
├── 400.woff2 (50 KB)
├── 500.woff2 (50 KB)
├── 600.woff2 (50 KB)
├── 700.woff2 (50 KB)
└── Total: 200 KB

Variable Font:
├── Single file with all weights
├── Inter-Variable.woff2 (100 KB)
├── Includes 100-900 weights
├── Smooth transitions
└── Total: 100 KB (50% smaller!)

💡 Benefits:
• Smaller file size
• Infinite weights (650, 455, etc.)
• Animation possibilities
• Custom axes (width, slant, etc.)
• Future-proof
```

---

### 🏆 Best Variable Fonts

#### Inter

```
🔗 https://rsms.me/inter
💰 FREE & Open Source
```

**Features:**

```
✨ The UI Font King:
├── Designed for computer screens
├── Tall x-height
├── Distinctive characters
├── Variable font version
├── 9 weights (100-900)
├── OpenType features
└── Used by GitHub, Mozilla, etc.

📊 Variable Axes:
• Weight (100-900)
• Slant (0-10°)

🎯 Perfect For:
• UI/UX design
• Dashboards
• Applications
• Web apps
• Modern websites

💡 Fun Fact:
Created by Figma's founder!
```

**Implementation:**

```css
/* ═══════════════════════════════════════════════════════════
   INTER VARIABLE FONT USAGE
   ═══════════════════════════════════════════════════════════ */

@font-face {
  font-family: "Inter Variable";
  src: url("/fonts/Inter-Variable.woff2") format("woff2");
  font-weight: 100 900;
  font-display: swap;
}

body {
  font-family: "Inter Variable", sans-serif;
}

/* Use any weight! */
h1 {
  font-weight: 650;
} /* Custom weight! */
h2 {
  font-weight: 550;
}
p {
  font-weight: 400;
}
strong {
  font-weight: 600;
}

/* Animate weight (cool!) */
@keyframes weightChange {
  from {
    font-weight: 300;
  }
  to {
    font-weight: 900;
  }
}

.animated-text {
  animation: weightChange 2s infinite alternate;
}
```

---

#### Recursive

```
🔗 https://www.recursive.design
💰 FREE & Open Source
```

**Features:**

```
🎨 The Most Flexible Font:
├── 5 variable axes!
├── Mono to Sans continuum
├── Casual to Linear
├── Weight
├── Slant
├── Cursive
└── Infinite possibilities

📊 Variable Axes:
• MONO (monospace to proportional)
• CASL (casual to linear)
• wght (weight)
• slnt (slant)
• CRSV (cursive)

🎯 Use Cases:
• Code + UI in one font
• Creative projects
• Experimental design
• Brand systems
• Flexible typography
```

---

#### Roboto Flex

```
🔗 https://github.com/TypeNetwork/Roboto-Flex
💰 FREE & Open Source
```

**Features:**

```
🤖 Google's Variable Evolution:
├── 12 axes (!)
├── Weight, width, optical size
├── Grade, slant, etc.
├── Extreme flexibility
└── Google Fonts available

📊 Mind-Blowing Axes:
• Weight (100-1000)
• Width (25-151)
• Optical Size (8-144pt)
• Grade (-200 to 150)
• Slant (-10 to 0)
• And 7 more!

💡 Use For:
• Responsive typography
• Advanced control
• Experimental projects
```

---

### 📦 More Variable Fonts

<div align="center">

| Font              | Axes | Best For           | Link                                                  |
| :---------------- | :--: | :----------------- | :---------------------------------------------------- |
| **Public Sans**   |  2   | Government sites   | [Link](https://public-sans.digital.gov/)              |
| **Work Sans**     |  1   | Professional sites | [Link](https://weiweihuanghuang.github.io/Work-Sans/) |
| **Source Sans 3** |  2   | Adobe projects     | [Link](https://adobe-fonts.github.io/source-sans/)    |
| **Amstelvar**     |  14  | Experimental       | [Link](https://github.com/TypeNetwork/Amstelvar)      |
| **Fraunces**      |  3   | Display type       | [Link](https://fraunces.undercase.xyz/)               |

</div>

---

### Browser Support

```
📊 Variable Font Browser Support:

✅ Fully Supported:
• Chrome 66+
• Firefox 62+
• Safari 11+
• Edge 17+

⚠️ Partial:
• IE 11 (no support)
• Opera Mini (no support)

💡 Fallback Strategy:
@supports (font-variation-settings: normal) {
  /* Variable font code */
}

/* Fallback for older browsers */
@font-face {
  font-family: 'Inter Fallback';
  src: url('Inter-Regular.woff2');
  font-weight: 400;
}
```

---

<div align="center">

## 🛠️ Typography Tools

_Tools to make typography easier_ 🎯

</div>

### Font Testing & Preview

#### Wordmark.it

```
🔗 https://wordmark.it
💰 FREE
```

**Features:**

```
🔍 Font Comparison Tool:
├── Type your text once
├── See ALL your system fonts
├── Side-by-side comparison
├── Filter by style
└── Quick font selection

🎯 Perfect For:
• Comparing system fonts
• Quick font decisions
• Client presentations
• Font discovery
```

---

#### Font Flipper

```
🔗 https://fontflipper.com
💰 FREE (Chrome Extension)
```

**Features:**

```
🔄 Test Fonts on Any Website:
├── Chrome extension
├── Try Google Fonts live
├── See fonts in context
├── Quick iteration
└── Client demonstrations

💡 Use Case:
"How would Poppins look on our site?"
Install extension → Browse site → Flip fonts!
```

---

### Font Identification

#### WhatTheFont

```
🔗 https://www.myfonts.com/pages/whatthefont
💰 FREE
```

**Features:**

```
🔍 Identify Fonts from Images:
├── Upload image
├── AI identifies font
├── Suggests similar
├── Mobile app available
└── 90%+ accurate

🎯 When You Need It:
• Client: "Use this font"
• Competitor research
• Inspiration images
• Historical designs
```

---

#### Font Squirrel Matcherator

```
🔗 https://www.fontsquirrel.com/matcherator
💰 FREE
```

**Features:**

```
🎨 Font Identification + Free Alternatives:
├── Upload image
├── Identifies font
├── Suggests FREE alternatives
└── Commercial-use safe

💡 Killer Feature:
Not only identifies fonts but suggests
FREE alternatives you can actually use!
```

---

### Typography Calculators

#### Type Scale

```
🔗 https://type-scale.com
💰 FREE
```

**Features:**

```
📐 Typography Scale Generator:
├── Visual type scale
├── Multiple scale ratios
├── CSS export
├── Font testing
└── Google Fonts integration

🎯 Scale Ratios:
• Minor Second (1.067)
• Major Second (1.125)
• Minor Third (1.2) ← Popular
• Major Third (1.25)
• Perfect Fourth (1.333)
• Augmented Fourth (1.414)
• Perfect Fifth (1.5)
• Golden Ratio (1.618)

💡 Output:
h1: 47.78px
h2: 39.81px
h3: 33.18px
h4: 27.65px
h5: 23.04px
h6: 19.20px
p: 16px
```

---

#### Modular Scale

```
🔗 https://www.modularscale.com
💰 FREE
```

**Features:**

```
📊 Advanced Scale Calculator:
├── Multiple base sizes
├── Custom ratios
├── Complex scales
├── Responsive considerations
└── Sass/SCSS integration
```

---

### Font Pairing Tools

#### Fontpair

```
🔗 https://www.fontpair.co
💰 FREE
```

**Features:**

```
🎨 Google Font Pairing Gallery:
├── Curated combinations
├── Real examples
├── Copy CSS instantly
├── Featured pairings
└── Collection saving

🎯 Popular Pairings:
• Playfair Display + Source Sans Pro
• Montserrat + Merriweather
• Oswald + Lato
• Raleway + Lora
• Poppins + Inter
```

---

#### Fontjoy

```
🔗 https://fontjoy.com
💰 FREE
```

**Features:**

```
🤖 AI Font Pairing Generator:
├── Machine learning powered
├── Generate combinations
├── Lock fonts you like
├── Regenerate others
└── Discover unexpected pairs

🎯 How It Works:
1. Click "Generate"
2. Like the headline font? Lock it
3. Regenerate body font
4. Find perfect combination
5. Copy font names
```

---

<div align="center">

## ⚡ Performance & Loading

_Fast fonts = happy users_ 🚀

</div>

### Font Loading Strategies

```css
/* ═══════════════════════════════════════════════════════════
   FONT-DISPLAY STRATEGIES
   ═══════════════════════════════════════════════════════════ */

/* Block - Wait for font, invisible text meanwhile (FOIT) */
@font-face {
  font-family: 'MyFont';
  src: url('font.woff2');
  font-display: block; /* ❌ Bad UX */
}

/* Swap - Show fallback, swap when ready (FOUT) */
@font-face {
  font-family: 'MyFont';
  src: url('font.woff2');
  font-display: swap; /* ✅ Recommended */
}

/* Fallback - 100ms block, 3s swap period */
@font-face {
  font-family: 'MyFont';
  src: url('font.woff2');
  font-display: fallback; /* ⚠️ Rarely used */
}

/* Optional - 100ms block, no swap */
@font-face {
  font-family: 'MyFont';
  src: url('font.woff2');
  font-display: optional; /* 🎯 Performance first */
}

/* Auto - Browser decides */
@font-face {
  font-family: 'MyFont';
  src: url('font.woff2');
  font-display: auto; /* ❓ Unpredictable */
}

/* ═══════════════════════════════════════════════════════════
   RECOMMENDATION
   ═══════════════════════════════════════════════════════════ */

Most cases: font-display: swap
Performance critical: font-display: optional
```

---

### Preloading Fonts

```html
<!-- ═══════════════════════════════════════════════════════════
     PRELOAD CRITICAL FONTS
     ═══════════════════════════════════════════════════════════ -->

<!-- Preload the most important font (usually body text) -->
<link
  rel="preload"
  href="/fonts/inter-var.woff2"
  as="font"
  type="font/woff2"
  crossorigin
/>

<!-- ⚠️ Only preload 1-2 fonts max! -->
<!-- Preloading too many defeats the purpose -->

<!-- Google Fonts with preconnect -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
  href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap"
  rel="stylesheet"
/>
```

---

### Font Subsetting

```
🎯 What is Subsetting?

Full Font:
├── All characters (Latin, Cyrillic, Greek, etc.)
├── File size: 200 KB
└── Load time: slow

Subset Font (Latin only):
├── Only needed characters
├── File size: 50 KB
└── Load time: 4x faster!

📦 How to Subset:

Online Tools:
• Font Squirrel Webfont Generator
• Transfonter
• Google Fonts (automatic subsetting)

Manual (advanced):
• pyftsubset (Python tool)
• glyphhanger (Node.js)
```

**Example:**

```bash
# Using glyphhanger to subset
npm install -g glyphhanger

# Subset to US-ASCII only
glyphhanger --subset=font.ttf --US_ASCII

# Subset to specific characters
glyphhanger --subset=font.ttf --whitelist="ABCDEFGabcdefg0123456789"

# Subset based on website usage
glyphhanger https://yoursite.com --subset=font.ttf
```

---

### Font Loading API

```javascript
// ═══════════════════════════════════════════════════════════
// FONT LOADING API
// ═══════════════════════════════════════════════════════════

// Check if all fonts are loaded
document.fonts.ready.then(() => {
  console.log("All fonts loaded!");
  document.body.classList.add("fonts-loaded");
});

// Load specific font
const font = new FontFace(
  "MyFont",
  'url(/fonts/myfont.woff2) format("woff2")',
  {
    weight: "400",
    style: "normal",
  }
);

font
  .load()
  .then((loadedFont) => {
    document.fonts.add(loadedFont);
    console.log("Font loaded successfully");
  })
  .catch((error) => {
    console.error("Font load failed:", error);
  });

// Check if font is loaded
if (document.fonts.check("16px Inter")) {
  console.log("Inter is loaded");
}

// Listen for font load events
document.fonts.addEventListener("loading", (event) => {
  console.log("Font loading:", event.fontface.family);
});

document.fonts.addEventListener("loadingdone", (event) => {
  console.log("Font loaded:", event.fontface.family);
});
```

---

### Performance Checklist

```markdown
## Font Performance Checklist

### File Optimization ✅

- [ ] Use WOFF2 format (best compression)
- [ ] Subset fonts to needed characters
- [ ] Use variable fonts when possible
- [ ] Remove unused weights/styles
- [ ] Compress font files

### Loading Strategy ✅

- [ ] Use `font-display: swap`
- [ ] Preload critical fonts only (1-2 max)
- [ ] Preconnect to font CDNs
- [ ] Consider self-hosting
- [ ] Use Font Loading API for critical content

### Browser Caching ✅

- [ ] Set long cache headers (1 year+)
- [ ] Use CDN for fonts
- [ ] Implement service worker caching
- [ ] Version font filenames

### Fallback Strategy ✅

- [ ] Define similar fallback fonts
- [ ] Match fallback metrics
- [ ] Test with slow 3G
- [ ] Ensure readability during load

🎯 Target Metrics:
• First Contentful Paint: < 1.8s
• Largest Contentful Paint: < 2.5s
• Cumulative Layout Shift: < 0.1
```

---

<div align="center">

## 📐 Typography Systems

_Build scalable, maintainable typography_ 🏗️

</div>

### The MrDib Typography System

```css
/* ═══════════════════════════════════════════════════════════
   COMPLETE TYPOGRAPHY SYSTEM
   Copy, customize, conquer!
   ═══════════════════════════════════════════════════════════ */

:root {
  /* ─────────────────────────────────────────────────────────
     FONT FAMILIES
     ─────────────────────────────────────────────────────── */
  --font-sans: "Inter Variable", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    sans-serif;
  --font-serif: "Merriweather", Georgia, "Times New Roman", serif;
  --font-mono: "Fira Code", "SF Mono", Monaco, "Cascadia Code", "Roboto Mono",
    monospace;
  --font-display: "Poppins", var(--font-sans);

  /* ─────────────────────────────────────────────────────────
     TYPE SCALE - Perfect Fourth (1.333)
     ─────────────────────────────────────────────────────── */
  --text-xs: 0.75rem; /* 12px */
  --text-sm: 0.875rem; /* 14px */
  --text-base: 1rem; /* 16px */
  --text-lg: 1.125rem; /* 18px */
  --text-xl: 1.333rem; /* 21.33px */
  --text-2xl: 1.777rem; /* 28.43px */
  --text-3xl: 2.369rem; /* 37.90px */
  --text-4xl: 3.157rem; /* 50.52px */
  --text-5xl: 4.209rem; /* 67.34px */

  /* ─────────────────────────────────────────────────────────
     FONT WEIGHTS
     ─────────────────────────────────────────────────────── */
  --font-light: 300;
  --font-normal: 400;
  --font-medium: 500;
  --font-semibold: 600;
  --font-bold: 700;
  --font-extrabold: 800;
  --font-black: 900;

  /* ─────────────────────────────────────────────────────────
     LINE HEIGHTS
     ─────────────────────────────────────────────────────── */
  --leading-none: 1;
  --leading-tight: 1.25;
  --leading-snug: 1.375;
  --leading-normal: 1.5;
  --leading-relaxed: 1.625;
  --leading-loose: 2;

  /* ─────────────────────────────────────────────────────────
     LETTER SPACING
     ─────────────────────────────────────────────────────── */
  --tracking-tighter: -0.05em;
  --tracking-tight: -0.025em;
  --tracking-normal: 0;
  --tracking-wide: 0.025em;
  --tracking-wider: 0.05em;
  --tracking-widest: 0.1em;

  /* ─────────────────────────────────────────────────────────
     TEXT COLORS
     ─────────────────────────────────────────────────────── */
  --text-primary: #111827; /* Gray 900 */
  --text-secondary: #6b7280; /* Gray 500 */
  --text-tertiary: #9ca3af; /* Gray 400 */
  --text-inverse: #ffffff;
  --text-link: #3b82f6; /* Blue 500 */
  --text-link-hover: #2563eb; /* Blue 600 */
}

/* Dark mode adjustments */
[data-theme="dark"] {
  --text-primary: #f9fafb;
  --text-secondary: #d1d5db;
  --text-tertiary: #9ca3af;
  --text-inverse: #111827;
}

/* ═══════════════════════════════════════════════════════════
   BASE STYLES
   ═══════════════════════════════════════════════════════════ */

html {
  font-size: 16px; /* 1rem base */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  font-family: var(--font-sans);
  font-size: var(--text-base);
  font-weight: var(--font-normal);
  line-height: var(--leading-relaxed);
  color: var(--text-primary);
  letter-spacing: var(--tracking-normal);
}

/* ═══════════════════════════════════════════════════════════
   HEADINGS
   ═══════════════════════════════════════════════════════════ */

h1,
h2,
h3,
h4,
h5,
h6 {
  font-family: var(--font-display);
  font-weight: var(--font-bold);
  line-height: var(--leading-tight);
  letter-spacing: var(--tracking-tight);
  color: var(--text-primary);
  margin-top: 0;
  margin-bottom: 0.5em;
}

h1 {
  font-size: var(--text-5xl);
  font-weight: var(--font-extrabold);
}

h2 {
  font-size: var(--text-4xl);
}

h3 {
  font-size: var(--text-3xl);
}

h4 {
  font-size: var(--text-2xl);
}

h5 {
  font-size: var(--text-xl);
}

h6 {
  font-size: var(--text-lg);
}

/* ═══════════════════════════════════════════════════════════
   BODY TEXT
   ═══════════════════════════════════════════════════════════ */

p {
  margin-top: 0;
  margin-bottom: 1rem;
  max-width: 65ch; /* Optimal reading width */
}

.lead {
  font-size: var(--text-xl);
  line-height: var(--leading-relaxed);
  color: var(--text-secondary);
}

.small {
  font-size: var(--text-sm);
  color: var(--text-secondary);
}

/* ═══════════════════════════════════════════════════════════
   LINKS
   ═══════════════════════════════════════════════════════════ */

a {
  color: var(--text-link);
  text-decoration: none;
  transition: color 0.2s ease;
}

a:hover {
  color: var(--text-link-hover);
  text-decoration: underline;
}

/* ═══════════════════════════════════════════════════════════
   LISTS
   ═══════════════════════════════════════════════════════════ */

ul,
ol {
  margin-top: 0;
  margin-bottom: 1rem;
  padding-left: 1.5rem;
}

li {
  margin-bottom: 0.5rem;
}

/* ═══════════════════════════════════════════════════════════
   CODE & PREFORMATTED TEXT
   ═══════════════════════════════════════════════════════════ */

code {
  font-family: var(--font-mono);
  font-size: 0.875em;
  font-weight: var(--font-medium);
  background: #f3f4f6;
  padding: 0.125rem 0.25rem;
  border-radius: 0.25rem;
  color: #dc2626;
}

pre {
  font-family: var(--font-mono);
  font-size: var(--text-sm);
  line-height: var(--leading-relaxed);
  background: #1f2937;
  color: #f9fafb;
  padding: 1rem;
  border-radius: 0.5rem;
  overflow-x: auto;
  margin-bottom: 1rem;
}

pre code {
  background: none;
  padding: 0;
  color: inherit;
}

/* ═══════════════════════════════════════════════════════════
   UTILITY CLASSES
   ═══════════════════════════════════════════════════════════ */

.text-center {
  text-align: center;
}
.text-left {
  text-align: left;
}
.text-right {
  text-align: right;
}

.font-normal {
  font-weight: var(--font-normal);
}
.font-medium {
  font-weight: var(--font-medium);
}
.font-semibold {
  font-weight: var(--font-semibold);
}
.font-bold {
  font-weight: var(--font-bold);
}

.italic {
  font-style: italic;
}
.uppercase {
  text-transform: uppercase;
}
.lowercase {
  text-transform: lowercase;
}
.capitalize {
  text-transform: capitalize;
}

.truncate {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.line-clamp-2 {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.no-underline {
  text-decoration: none;
}
.underline {
  text-decoration: underline;
}
```

---

### Responsive Typography

```css
/* ═══════════════════════════════════════════════════════════
   RESPONSIVE TYPE SCALES
   ═══════════════════════════════════════════════════════════ */

/* Fluid typography using clamp() */
:root {
  /* Base: 16px at 375px viewport, 18px at 1440px viewport */
  --text-base: clamp(1rem, 0.95rem + 0.19vw, 1.125rem);

  /* Headings scale with viewport */
  --text-5xl: clamp(2.5rem, 1.8rem + 3.5vw, 4.209rem);
  --text-4xl: clamp(2rem, 1.5rem + 2.5vw, 3.157rem);
  --text-3xl: clamp(1.75rem, 1.3rem + 2vw, 2.369rem);
  --text-2xl: clamp(1.5rem, 1.2rem + 1.5vw, 1.777rem);
  --text-xl: clamp(1.25rem, 1.1rem + 0.75vw, 1.333rem);
}

/* Alternative: Breakpoint-based scaling */
:root {
  --text-5xl: 2.5rem; /* Mobile */
}

@media (min-width: 640px) {
  :root {
    --text-5xl: 3rem; /* Tablet */
  }
}

@media (min-width: 1024px) {
  :root {
    --text-5xl: 4.209rem; /* Desktop */
  }
}
```

---

<div align="center">

## 💡 Best Practices

_MrDib's typography wisdom_ 🎓

</div>

### The Typography Commandments

```
🏆 The 10 Typography Rules:

1️⃣  Use 2-3 fonts maximum
    • 1 for headings
    • 1 for body
    • 1 for code (if needed)

2️⃣  Establish clear hierarchy
    • Size, weight, color differentiation
    • Consistent heading structure
    • Visual flow

3️⃣  Optimize line length
    • 45-75 characters per line
    • Use `max-width: 65ch`
    • Better readability

4️⃣  Set proper line height
    • Body: 1.5-1.75
    • Headings: 1.2-1.3
    • Code: 1.5

5️⃣  Mind the contrast
    • 4.5:1 for body text (WCAG AA)
    • 7:1 for better readability (AAA)
    • Test with accessibility tools

6️⃣  Use system fonts for performance
    • Fast loading
    • Native feel
    • Zero network requests

7️⃣  Load fonts efficiently
    • font-display: swap
    • Preload critical fonts
    • Subset when possible

8️⃣  Maintain vertical rhythm
    • Consistent spacing
    • Line height multiples
    • Predictable layout

9️⃣  Test on real devices
    • Mobile readability
    • Different screen sizes
    • Various pixel densities

🔟 Respect readability > beauty
    • Function first
    • Beauty second
    • Users read content
```

---

### Common Typography Mistakes

```css
/* ❌ MISTAKES TO AVOID */

/* 1. Using too many fonts */
body {
  font-family: Arial;
}
h1 {
  font-family: Helvetica;
}
h2 {
  font-family: Verdana;
}
.card {
  font-family: Georgia;
}
/* 4 fonts = chaos! */

/* ✅ BETTER: Stick to 2 */
body {
  font-family: "Inter", sans-serif;
}
h1,
h2,
h3 {
  font-family: "Poppins", sans-serif;
}

/* ❌ 2. Poor line height */
p {
  font-size: 16px;
  line-height: 16px; /* Too cramped! */
}

/* ✅ BETTER: Comfortable spacing */
p {
  font-size: 16px;
  line-height: 1.6; /* 25.6px */
}

/* ❌ 3. Lines too long */
p {
  max-width: 100%; /* Hard to read! */
}

/* ✅ BETTER: Optimal reading width */
p {
  max-width: 65ch; /* 65 characters */
}

/* ❌ 4. Poor contrast */
p {
  color: #999;
  background: #fff; /* Only 2.85:1 - fails WCAG */
}

/* ✅ BETTER: Accessible contrast */
p {
  color: #333;
  background: #fff; /* 12.6:1 - passes AAA */
}

/* ❌ 5. Forgetting fallbacks */
body {
  font-family: "My Custom Font";
  /* What if it fails to load? */
}

/* ✅ BETTER: Always have fallbacks */
body {
  font-family: "My Custom Font", -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
}

/* ❌ 6. Loading too many weights */
@import url("fonts.googleapis.com/css2?family=Inter:wght@100;200;300;400;500;600;700;800;900");
/* 9 weights = slow! */

/* ✅ BETTER: Load only what you need */
@import url("fonts.googleapis.com/css2?family=Inter:wght@400;600;700");
/* 3 weights = fast */
```

---

### Accessibility Guidelines

```markdown
## Typography Accessibility Checklist

### Contrast ✅

- [ ] Body text: 4.5:1 minimum (AA)
- [ ] Large text (18pt+): 3:1 minimum
- [ ] Aim for 7:1 when possible (AAA)
- [ ] Test with WebAIM Contrast Checker

### Size & Spacing ✅

- [ ] Minimum 16px for body text
- [ ] 1.5 line height for body
- [ ] 1.5em paragraph spacing
- [ ] 0.12em letter spacing minimum

### Readability ✅

- [ ] Max 75 characters per line
- [ ] Left-aligned for LTR languages
- [ ] No justified text (causes rivers)
- [ ] Adequate whitespace

### Font Choice ✅

- [ ] Avoid ALL CAPS for long text
- [ ] Prefer sans-serif for screen
- [ ] Ensure distinct characters (1, l, I)
- [ ] Test with actual users

### Responsive ✅

- [ ] Text is resizable (browser zoom works)
- [ ] Minimum 200% zoom supported
- [ ] No horizontal scrolling when zoomed
- [ ] Touch targets: 44x44px minimum

### Special Considerations ✅

- [ ] Dyslexia-friendly options available
- [ ] High contrast mode supported
- [ ] Dark mode available
- [ ] Print stylesheet exists
```

---

<div align="center">

## 📜 Licensing Guide

_Don't get sued over fonts!_ ⚖️

</div>

### License Types Explained

```
📜 Font License Types:

1. Open Source (OFL, Apache, MIT)
   ✅ Free for everything
   ✅ Can modify
   ✅ Can redistribute
   ✅ Commercial use OK
   Example: Google Fonts, Adobe Source

2. Free for Personal Use
   ✅ Personal projects OK
   ❌ Commercial projects NO
   ❌ Client work NO
   ⚠️  Read license carefully!
   Example: Many DaFont fonts

3. Commercial License
   💰 Purchase required
   ✅ Commercial use
   ✅ Client projects
   📊 Often by pageviews/users
   Example: MyFonts, Fonts.com

4. Desktop vs Web License
   Desktop: Design files, PDFs
   Web: Websites (embed code)
   📦 Often sold separately!

5. Subscription (Adobe Fonts)
   💰 Monthly fee
   ✅ All fonts included
   ✅ Desktop + Web
   ⚠️  Stops working if you cancel

⚠️ ALWAYS READ THE LICENSE!
```

---

### Common Licensing Questions

```
🤔 FAQ:

Q: Can I use Google Fonts commercially?
A: ✅ YES! All Google Fonts are 100% free for any use.

Q: Can I use Font Awesome icons?
A: ✅ YES! Free version is under Creative Commons.
   💎 Pro version requires purchase.

Q: Can I use fonts from DaFont?
A: ⚠️  DEPENDS! Each font has its own license.
   Many are "Personal Use Only"
   Always check license before using!

Q: What if I can't find the license?
A: ❌ DON'T USE IT! No license = no permission.

Q: Can I modify open source fonts?
A: ✅ Usually YES if it's OFL/MIT/Apache.
   Must keep original license.

Q: Do I need to credit the font designer?
A: 🤷 DEPENDS on license.
   OFL: No requirement but appreciated
   CC-BY: Yes, required
   Check specific license!

Q: Can I subset/modify web fonts?
A: ✅ Usually YES for open source
   ❌ Usually NO for commercial fonts
   Read license!
```

---

### Safe Font Sources

```
🟢 100% Safe for Commercial:

Google Fonts
├── All fonts free
├── Open Font License
├── No attribution required
└── Desktop + Web use

Font Squirrel
├── Only commercial-safe fonts
├── Generator for webfonts
├── Clearly labeled licenses
└── Desktop + Web use

Fontshare
├── 100% free
├── Commercial OK
├── By Indian Type Foundry
└── No hidden fees

Adobe Fonts (with subscription)
├── Included with Creative Cloud
├── Desktop + Web use
├── No pageview limits
└── While subscribed

Open Source Projects
├── Inter, Recursive, etc.
├── Check GitHub license
├── Usually OFL or Apache
└── Free forever

🟡 Check License Carefully:

DaFont
├── Mixed licenses
├── Many personal use only
├── Read each font's license
└── Commercial often costs

1001 Fonts
├── Mixed licenses
├── Filter by license type
├── Commercial use varies
└── Always verify

🔴 Purchase Required:

MyFonts
Fonts.com
Hoefler&Co.
Typography.com
Most foundry websites
```

---

<div align="center">

## 🎉 You're Now a Typography Master!

**You've learned:**

- ✅ 1000+ font resources
- ✅ Font pairing strategies
- ✅ Performance optimization
- ✅ Variable fonts
- ✅ Typography systems
- ✅ Accessibility best practices
- ✅ Licensing know-how
- ✅ Professional workflows

### Remember

> **"Typography is two-dimensional architecture, based on experience and imagination."** - Hermann Zapf

And don't forget:

> **"Good typography is invisible. Bad typography is everywhere."** - MrDib ✨

</div>

---

### Quick Decision Tree

```
🎯 Which Font Should I Use?

Starting a new project?
├─ Need a UI font?
│  └─ ✅ Inter (free, variable, perfect)
├─ Need a display font?
│  └─ ✅ Poppins (friendly, versatile)
├─ Need a code font?
│  └─ ✅ Fira Code (ligatures, free)
└─ Need a serif?
   └─ ✅ Merriweather (readable, elegant)

Need more personality?
├─ Check Fontshare (free premium fonts)
├─ Browse Google Fonts (1500+ options)
└─ Explore Adobe Fonts (if you have CC)

Client has budget?
├─ MyFonts (wide selection)
├─ Fonts.com (classics)
└─ Hoefler&Co (luxury)

Still unsure?
└─ ✅ Use system fonts!
   - Fast, free, familiar
   - -apple-system, BlinkMacSystemFont, 'Segoe UI'
```

---

<div align="center">

**Built with 🔤 by MrDib, for designers who care about type**

_Now go set some beautiful type!_ ✨

**Remember: The details are not the details. They make the design!** 🎯

</div>

---

### Final Pro Tips

```
💎 MrDib's Typography Wisdom:

1. When in doubt, use Inter
2. Font pairing? One is enough
3. Big project? Invest in premium fonts
4. Performance matters more than variety
5. Test on real devices always
6. Accessibility is not optional
7. Read the license (seriously!)
8. Fewer fonts = faster site
9. System fonts are underrated
10. Ship it - perfect is the enemy of good

📚 Want to Learn More?
• "The Elements of Typographic Style" - Robert Bringhurst
• "Thinking with Type" - Ellen Lupton
• Butterick's Practical Typography - Matthew Butterick
• Typewolf - For daily inspiration

Now close this tab and go create something beautiful! 🚀
```
