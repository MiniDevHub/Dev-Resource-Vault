<div align="center">

# 🎨 Icon Libraries & Resources 🎨

### _Because using default folder icons is a crime against design_ 🚫📁

![Icons](https://img.shields.io/badge/Icons-Beautiful-rainbow?style=for-the-badge)
![Free](https://img.shields.io/badge/Price-Mostly_Free-green?style=for-the-badge)

</div>

---

<div align="center">

## 🌟 General Purpose Icons

</div>

### Open Source Icon Sets 🆓

```

🎬 Heroicons → https://heroicons.com

- By Tailwind team
- 292 icons, 3 styles
- SVG & JSX ready
- MIT license

💎 Phosphor Icons → https://phosphoricons.com

- 6,000+ icons
- 6 weights
- Figma plugin available
- npm install phosphor-icons

🌟 Lucide → https://lucide.dev

- Fork of Feather Icons
- 1000+ icons
- Tree-shakeable
- Community-driven

🪶 Feather Icons → https://feathericons.com

- 287 minimalist icons
- 24x24 grid
- Clean & simple
- npm install feather-icons

📦 Tabler Icons → https://tabler-icons.io

- 4,000+ free SVG icons
- Stroke customizable
- Figma plugin
- npm install @tabler/icons

🎯 Remix Icon → https://remixicon.com

- 2,800+ icons
- Neutral style
- Business friendly
- npm install remixicon

🔷 Boxicons → https://boxicons.com

- 1,600+ icons
- Regular & solid styles
- Animations included
- npm install boxicons

🎨 IconPark → https://iconpark.oceanengine.com

- 2,600+ icons
- Multi-color support
- Customizable themes
- By ByteDance

```

### Premium Icon Libraries 💰

```

💸 Streamline Icons → https://streamlinehq.com

- 100,000+ icons
- 50+ icon sets
- $30/month
- Figma plugin

🎯 Icons8 → https://icons8.com

- 1.3M+ icons
- Multiple styles
- Free with link
- $20/month unlimited

🏆 Iconfinder → https://iconfinder.com

- 5M+ icons
- Marketplace model
- Pay per icon set
- Subscription available

✨ Flaticon → https://flaticon.com

- 11M+ icons
- Free with attribution
- Premium from $8/month
- Massive selection

```

---

<div align="center">

## 🎯 Specialized Icon Sets

</div>

### Developer & Tech Icons 💻

```

⚡ Devicon → https://devicon.dev

- 150+ developer logos
- Programming languages
- Frameworks & tools
- Multiple versions

🛠️ Simple Icons → https://simpleicons.org

- 2,400+ brand SVGs
- Tech company logos
- Consistent style
- npm install simple-icons

🔧 Font Awesome → https://fontawesome.com

- 2,000+ free icons
- Pro: 16,000+ icons
- Brand icons included
- Industry standard

👾 Octicons → https://primer.style/octicons

- GitHub's icon set
- Developer focused
- 250+ icons
- npm install @primer/octicons

```

### Emoji & Fun Icons 😄

```

🎉 OpenMoji → https://openmoji.org

- Open source emojis
- 3,900+ emojis
- Consistent style
- SVG format

😊 Twemoji → https://twemoji.twitter.com

- Twitter's emoji set
- Cross-platform
- Open source
- npm install twemoji

🦄 Emoji CSS → https://emoji-css.afeld.me

- Pure CSS emojis
- No images needed
- Lightweight

🎭 Iconoir → https://iconoir.com

- 1,300+ icons
- Unique style
- Free & open source
- Clean aesthetics

```

---

<div align="center">

## 🎨 Icon Design Systems

</div>

### Complete Icon Systems 🏗️

```

🔷 Material Icons → https://fonts.google.com/icons

- Google's system
- 5 themes
- Variable font
- 2,000+ icons

🍎 SF Symbols → https://developer.apple.com/sf-symbols

- Apple's system
- 4,000+ symbols
- macOS/iOS only
- 9 weights

🪟 Fluent Icons → https://github.com/microsoft/fluentui-system-icons

- Microsoft's system
- 2,000+ icons
- Multiple styles
- Open source

🐜 Ant Design Icons → https://ant.design/components/icon

- 600+ icons
- Outlined/filled/two-tone
- React components
- Consistent system

```

---

<div align="center">

## 🛠️ Icon Tools & Utilities

</div>

### Icon Search & Management 🔍

```

🔍 Iconify → https://iconify.design

- 150,000+ icons
- All sets in one place
- Framework agnostic
- API available

🎯 Icon Scout → https://iconscout.com

- 3.5M+ assets
- Icons, illustrations
- Lottie animations
- Design tools

📦 Nucleo → https://nucleoapp.com

- Icon organizer app
- 30,000+ icons
- Desktop app
- $99 one-time

🗂️ IconJar → https://geticonjar.com

- macOS icon manager
- Organize & search
- Quick drag & drop
- $29.99

```

### Icon Generators & Customizers 🎨

```

⚡ Tabler Icons Generator → https://tabler-icons.io/generator

- Custom icon creation
- Based on Tabler style
- Export as SVG

🎨 Icon Kitchen → https://icon.kitchen

- App icon generator
- Multiple platforms
- Adaptive icons

🔧 IcoMoon → https://icomoon.io

- Icon font generator
- SVG to font
- Custom sets
- Free app

✏️ Iconsvg → https://iconsvg.xyz

- Customize open source icons
- Quick editor
- API access

```

---

<div align="center">

## 💻 Implementation Examples

</div>

### React Implementation

```jsx
// Using Heroicons
import { BeakerIcon, BellIcon, CogIcon } from "@heroicons/react/24/solid";

function IconExample() {
  return (
    <div className="flex gap-4">
      <BeakerIcon className="h-6 w-6 text-blue-500" />
      <BellIcon className="h-6 w-6 text-yellow-500" />
      <CogIcon className="h-6 w-6 text-gray-500" />
    </div>
  );
}

// Using Lucide React
import { Calendar, Heart, Settings } from "lucide-react";

function LucideExample() {
  return (
    <>
      <Calendar size={24} color="#3b82f6" strokeWidth={2} />
      <Heart size={24} color="#ef4444" fill="#ef4444" />
      <Settings size={24} color="#6b7280" className="animate-spin" />
    </>
  );
}

// Using Phosphor
import { Coffee, Cookie, Pizza } from "phosphor-react";

function PhosphorExample() {
  return (
    <div>
      <Coffee size={32} weight="duotone" />
      <Cookie size={32} weight="fill" />
      <Pizza size={32} weight="bold" />
    </div>
  );
}
```

### Vue Implementation

```vue
<template>
  <div>
    <!-- Using Heroicons Vue -->
    <BeakerIcon class="h-6 w-6 text-blue-500" />

    <!-- Using Iconify -->
    <Icon icon="mdi:home" width="24" />

    <!-- Using unplugin-icons -->
    <i-mdi-account class="text-2xl" />
  </div>
</template>

<script setup>
import { BeakerIcon } from "@heroicons/vue/24/solid";
import { Icon } from "@iconify/vue";
</script>
```

---

<div align="center">

## 🎯 Icon Selection Guide

</div>

### Questions to Ask:

1. **Style consistency** - Does it match your design?
2. **License** - Free? Attribution needed?
3. **Format** - SVG, font, or components?
4. **Tree-shaking** - Can you import only what you need?
5. **Customization** - Colors, sizes, weights?
6. **Framework support** - React, Vue, Angular?

### MrDib's Recommendations:

**For React Projects:**

- Heroicons (Tailwind projects)
- Lucide (flexible & growing)
- Phosphor (multiple weights)

**For General Web:**

- Tabler Icons (huge selection)
- Feather (minimalist)
- Boxicons (variety)

**For Apps:**

- Material Icons (Android style)
- SF Symbols (iOS style)
- Fluent Icons (Windows style)

---

<div align="center">

## 💡 Pro Tips

</div>

### Performance Tips

```javascript
// ❌ BAD: Importing entire library
import * as Icons from 'lucide-react'

// ✅ GOOD: Import only what you need
import { Home, User, Settings } from 'lucide-react'

// ❌ BAD: Loading icon fonts for 3 icons
<link rel="stylesheet" href="fontawesome.css">

// ✅ GOOD: Inline SVG for few icons
<svg>...</svg>
```

### Accessibility

```html
<!-- Always add labels -->
<button aria-label="Settings">
  <SettingsIcon />
</button>

<!-- Or visible text -->
<button>
  <SettingsIcon />
  <span>Settings</span>
</button>
```

---

<div align="center">

_Choose your icons wisely - they speak louder than words! 🎨_

</div>
