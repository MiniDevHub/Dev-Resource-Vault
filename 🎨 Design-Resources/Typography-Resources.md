<div align="center">

# 🔤 Typography Resources & Font Libraries 🔤

### _Because Comic Sans is never the answer_ 🚫

![Fonts](https://img.shields.io/badge/Fonts-Beautiful-blue?style=for-the-badge)
![Typography](https://img.shields.io/badge/Typography-Matters-purple?style=for-the-badge)

</div>

---

<div align="center">

## 🎨 Free Font Resources

</div>

### Google Fonts Alternative 🌟

```

🔤 Google Fonts → https://fonts.google.com

- 1,400+ open source fonts
- Easy implementation
- Variable fonts support
- No account needed

🎨 Fontsource → https://fontsource.org

- Self-host Google Fonts
- NPM packages
- Better performance
- npm install @fontsource/inter

📦 Bunny Fonts → https://fonts.bunny.net

- Privacy-friendly
- Google Fonts mirror
- GDPR compliant
- Drop-in replacement

🌐 Adobe Fonts → https://fonts.adobe.com

- Free with Creative Cloud
- High-quality fonts
- 20,000+ fonts
- Web fonts included

```

### Open Source Font Collections 🆓

```

🏛️ Font Library → https://fontlibrary.org

- Community-driven
- Open source only
- Quality curated

🎯 Brick → https://brick.im

- Webfonts that work
- Fast CDN
- Open source fonts

💎 Beautiful Web Type → https://beautifulwebtype.com

- Curated Google Fonts
- Usage examples
- Pairing suggestions

🔧 Fontshare → https://fontshare.com

- 100% free fonts
- By Indian Type Foundry
- Professional quality
- Growing collection

```

---

<div align="center">

## 💻 Programming Fonts

</div>

### Monospace Fonts for Coding 👨‍💻

```

🔥 Fira Code → https://github.com/tonsky/FiraCode

- Programming ligatures
- Open source
- Most popular
- Retina ready

✈️ JetBrains Mono → https://jetbrains.com/mono

- By JetBrains
- Designed for IDEs
- Excellent readability
- Free & open source

🏔️ Cascadia Code → https://github.com/microsoft/cascadia-code

- Microsoft's font
- Powerline support
- Programming ligatures
- Variable font

🦆 MonoLisa → https://monolisa.dev

- Premium ($69+)
- Reading comfort
- Unique design
- Worth the price

💰 Dank Mono → https://philpl.gumroad.com/l/dank-mono

- Premium ($40)
- Italic comments
- Unique style
- Developer favorite

⚡ Input → https://input.djr.com

- Customizable
- Free for personal
- Multiple widths
- By David Jonathan Ross

🎯 Iosevka → https://typeof.net/Iosevka

- Highly customizable
- Build your own
- Narrow & wide variants
- Open source

🌟 Victor Mono → https://rubjo.github.io/victor-mono

- Cursive italics
- Programming ligatures
- Free & open source
- Unique personality

```

---

<div align="center">

## 🎨 Display & Creative Fonts

</div>

### Headline Fonts 📰

```

🏆 Bebas Neue → https://fonts.google.com/specimen/Bebas+Neue

- All caps display
- Bold impact
- Free on Google Fonts

🎪 Montserrat → https://fonts.google.com/specimen/Montserrat

- Geometric sans
- 18 styles
- Versatile

💫 Poppins → https://fonts.google.com/specimen/Poppins

- Geometric + friendly
- 18 styles
- Modern favorite

🌊 Raleway → https://fonts.google.com/specimen/Raleway

- Elegant sans
- 18 styles
- Variable font

```

### Script & Decorative 🎭

```

🖋️ Dancing Script → https://fonts.google.com/specimen/Dancing+Script

- Casual script
- Friendly feel
- Popular choice

✍️ Pacifico → https://fonts.google.com/specimen/Pacifico

- Surf style
- Fun personality
- Single weight

🎨 Caveat → https://fonts.google.com/specimen/Caveat

- Handwriting style
- Natural feel
- Variable weight

```

---

<div align="center">

## 🛠️ Typography Tools

</div>

### Font Pairing Tools 🎯

```

🎨 Fontpair → https://fontpair.co

- Google Font pairings
- Curated combinations
- Copy CSS

🔀 Fontjoy → https://fontjoy.com

- AI font pairing
- Generate combinations
- Machine learning

📐 Type Scale → https://type-scale.com

- Typography scale
- Visual calculator
- Export CSS

🎯 Archetype → https://archetypeapp.com

- Font combinations
- Real examples
- Layout testing

```

### Font Testing Tools 🧪

```

📝 Font Flipper → https://fontflipper.com

- Preview on any site
- Chrome extension
- Quick testing

🔍 Wordmark.it → https://wordmark.it

- Compare all fonts
- Your system fonts
- Side by side

⚡ Font Playground → https://play.typedetail.com

- Variable fonts
- Interactive testing
- Real-time preview

```

---

<div align="center">

## 💎 Variable Fonts

</div>

### Understanding Variable Fonts

```css
/* Traditional approach - multiple files */
@font-face {
  font-family: "Roboto";
  src: url("roboto-regular.woff2");
  font-weight: 400;
}
@font-face {
  font-family: "Roboto";
  src: url("roboto-bold.woff2");
  font-weight: 700;
}

/* Variable font - one file! */
@font-face {
  font-family: "Roboto Variable";
  src: url("roboto-variable.woff2") format("woff2-variations");
  font-weight: 100 900; /* Full range! */
}

/* Usage with any weight */
.text {
  font-family: "Roboto Variable";
  font-weight: 650; /* Any value! */
  font-variation-settings: "wght" 650, "slnt" -10;
}
```

### Popular Variable Fonts

```
🎯 Inter             → https://rsms.me/inter
   - UI typeface
   - 9 weights + italics
   - Optimized for screens

🔤 Recursive         → https://recursive.design
   - 5 variation axes
   - Mono to sans
   - Expressive ranges

📐 Public Sans       → https://public-sans.digital.gov
   - By US Web Design
   - Neutral style
   - Government approved

✨ Work Sans         → https://weiweihuanghuang.github.io/Work-Sans
   - 9 weights
   - Optimized for screen
   - Professional
```

---

<div align="center">

## 🎯 Font Loading Strategies

</div>

### Performance Best Practices

```css
/* Optimal @font-face declaration */
@font-face {
  font-family: "MyFont";
  src: url("font.woff2") format("woff2"), url("font.woff") format("woff");
  font-weight: 400;
  font-style: normal;
  font-display: swap; /* Prevent FOIT */
}

/* Preload critical fonts */
<link rel="preload"
      href="/fonts/inter-var.woff2"
      as="font"
      type="font/woff2"
      crossorigin>

/* Subset fonts for performance */
@font-face {
  font-family: "Inter";
  src: url("inter-latin.woff2") format("woff2");
  unicode-range: U+0000-00FF; /* Latin only */
}
```

### Font Loading API

```javascript
// Check if fonts are loaded
document.fonts.ready.then(() => {
  console.log("All fonts loaded!");
  document.body.classList.add("fonts-loaded");
});

// Load specific font
const font = new FontFace("MyFont", "url(myfont.woff2)");
font.load().then((loadedFont) => {
  document.fonts.add(loadedFont);
  document.body.style.fontFamily = "MyFont, sans-serif";
});
```

---

<div align="center">

## 📐 Typography Systems

</div>

### Creating a Type Scale

```css
/* MrDib's Typography System */
:root {
  /* Font families */
  --font-sans: "Inter", system-ui, -apple-system, sans-serif;
  --font-serif: "Georgia", "Times New Roman", serif;
  --font-mono: "Fira Code", "Monaco", monospace;

  /* Type scale - Minor Third (1.2) */
  --text-xs: 0.75rem; /* 12px */
  --text-sm: 0.875rem; /* 14px */
  --text-base: 1rem; /* 16px */
  --text-lg: 1.125rem; /* 18px */
  --text-xl: 1.25rem; /* 20px */
  --text-2xl: 1.5rem; /* 24px */
  --text-3xl: 1.875rem; /* 30px */
  --text-4xl: 2.25rem; /* 36px */
  --text-5xl: 3rem; /* 48px */

  /* Line heights */
  --leading-tight: 1.25;
  --leading-normal: 1.5;
  --leading-relaxed: 1.75;

  /* Letter spacing */
  --tracking-tight: -0.025em;
  --tracking-normal: 0;
  --tracking-wide: 0.025em;

  /* Font weights */
  --font-normal: 400;
  --font-medium: 500;
  --font-semibold: 600;
  --font-bold: 700;
}

/* Usage */
h1 {
  font-family: var(--font-sans);
  font-size: var(--text-5xl);
  font-weight: var(--font-bold);
  line-height: var(--leading-tight);
  letter-spacing: var(--tracking-tight);
}

p {
  font-family: var(--font-sans);
  font-size: var(--text-base);
  font-weight: var(--font-normal);
  line-height: var(--leading-relaxed);
}

code {
  font-family: var(--font-mono);
  font-size: var(--text-sm);
  font-weight: var(--font-medium);
}
```

---

<div align="center">

## 💡 Typography Best Practices

</div>

### Do's ✅

- **Use system font stack for body text**
- **Limit to 2-3 fonts max**
- **Ensure proper contrast ratios**
- **Test on real devices**
- **Use variable fonts when possible**
- **Subset fonts to needed characters**

### Don'ts ❌

- **Don't use too many fonts**
- **Don't use display fonts for body text**
- **Don't forget fallback fonts**
- **Don't load unnecessary weights**
- **Don't ignore performance**
- **Don't use fonts without proper license**

---

<div align="center">

## 🎯 MrDib's Font Stack Recommendations

</div>

```css
/* Sans-serif stack */
font-family: Inter, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
  Ubuntu, sans-serif;

/* Monospace stack */
font-family: "Fira Code", Monaco, Consolas, "Courier New", monospace;

/* Serif stack */
font-family: Georgia, Cambria, "Times New Roman", Times, serif;

/* System UI stack (performance) */
font-family: system-ui, -apple-system, "Segoe UI", Roboto, sans-serif;
```

---

<div align="center">

_Remember: Good typography is invisible. Bad typography is everywhere! 🎨_

</div>
