<div align="center">

# 🎭 Animation Libraries & Tools 🎭

### _Making the web move, shake, and occasionally breakdance_ 💃

![Animations](https://img.shields.io/badge/Animations-Smooth-purple?style=for-the-badge)
![Performance](https://img.shields.io/badge/60_FPS-Always-green?style=for-the-badge)

</div>

---

<div align="center">

## 🎬 JavaScript Animation Libraries

</div>

### The Heavy Hitters 💪

```

🟢 GSAP (GreenSock) → https://greensock.com/gsap

- Industry standard
- Incredible performance
- Timeline control
- Plugin ecosystem
- npm install gsap

🎭 Framer Motion → https://framer.com/motion

- React animations
- Gesture support
- Layout animations
- Spring physics
- npm install framer-motion

🌊 Anime.js → https://animejs.com

- Lightweight (16kb)
- Simple API
- SVG animations
- Timeline support
- npm install animejs

⚡ Motion One → https://motion.dev

- Web Animations API
- 70% smaller than Framer
- Modern approach
- Great performance
- npm install motion

🎯 Lottie → https://lottiefiles.com

- After Effects to web
- JSON animations
- Complex animations
- Designer friendly
- npm install lottie-web

🎪 Three.js → https://threejs.org

- 3D animations
- WebGL wrapper
- Complex scenes
- VR/AR support
- npm install three

```

---

<div align="center">

## 🎨 CSS Animation Libraries

</div>

### Pure CSS Magic ✨

```

🎯 Animate.css → https://animate.style

- 97 animations
- Just add classes
- 4kb gzipped
- Easy integration
- npm install animate.css

✨ AOS (Animate On Scroll) → https://michalsnik.github.io/aos

- Scroll animations
- Easy setup
- Customizable
- Performance focused
- npm install aos

🌈 Hover.css → https://ianlunn.github.io/Hover

- Hover effects
- 100+ effects
- CSS only
- Copy & paste
- npm install hover.css

💫 Magic Animations → https://www.minimamente.com/project/magic

- Special effects
- Unique animations
- CSS3 based
- Eye-catching

🎪 CSShake → https://elrumordelaluz.github.io/csshake

- Shake animations
- Multiple styles
- Attention grabbers
- npm install csshake

```

---

<div align="center">

## 🎯 Specialized Animation Tools

</div>

### Scroll Animations 📜

```javascript
// 🌊 Parallax.js
import Parallax from "parallax-js";

const scene = document.getElementById("scene");
const parallax = new Parallax(scene, {
  relativeInput: true,
  hoverOnly: true,
});

// 📜 Rellax.js - Buttery smooth parallax
import Rellax from "rellax";

const rellax = new Rellax(".rellax", {
  speed: -2,
  center: true,
  wrapper: null,
  round: true,
  vertical: true,
  horizontal: false,
});

// ✨ ScrollMagic
import ScrollMagic from "scrollmagic";

const controller = new ScrollMagic.Controller();
const scene = new ScrollMagic.Scene({
  triggerElement: "#trigger",
  duration: 300,
})
  .setClassToggle("#animate", "fade-in")
  .addTo(controller);

// 🎭 Intersection Observer (Native!)
const observer = new IntersectionObserver(
  (entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        entry.target.classList.add("animate");
      }
    });
  },
  { threshold: 0.1 }
);

document.querySelectorAll(".animate-on-scroll").forEach((el) => {
  observer.observe(el);
});
```

### Text Animations 📝

```javascript
// 📝 Typed.js - Typing animations
import Typed from "typed.js";

new Typed("#element", {
  strings: ["First sentence.", "Second sentence."],
  typeSpeed: 50,
  backSpeed: 50,
  loop: true,
});

// ✂️ Splitting.js - Split text for animation
import Splitting from "splitting";

Splitting({
  target: "[data-splitting]",
  by: "chars",
});

// 🎨 Textillate.js - Text effects
$(".tlt").textillate({
  in: { effect: "rollIn" },
  out: { effect: "rollOut" },
  loop: true,
});

// 🌈 Lettering.js - Letter manipulation
$(".fancy_title")
  .lettering()
  .children("span")
  .hover(function () {
    $(this).addClass("bounce");
  });
```

---

<div align="center">

## 🎬 React Animation Solutions

</div>

### Component-Based Animations ⚛️

```jsx
// 🎭 Framer Motion
import { motion } from "framer-motion";

function AnimatedBox() {
  return (
    <motion.div
      initial={{ opacity: 0, scale: 0.5 }}
      animate={{ opacity: 1, scale: 1 }}
      transition={{
        duration: 0.8,
        delay: 0.5,
        ease: [0, 0.71, 0.2, 1.01],
      }}
      whileHover={{ scale: 1.1 }}
      whileTap={{ scale: 0.9 }}
    >
      Animated content
    </motion.div>
  );
}

// 🌊 React Spring
import { useSpring, animated } from "react-spring";

function SpringComponent() {
  const props = useSpring({
    from: { opacity: 0 },
    to: { opacity: 1 },
    config: { tension: 300, friction: 20 },
  });

  return <animated.div style={props}>Springy!</animated.div>;
}

// 🎯 Auto-Animate
import autoAnimate from "@formkit/auto-animate";

function ListComponent() {
  const parent = useRef(null);

  useEffect(() => {
    parent.current && autoAnimate(parent.current);
  }, [parent]);

  return (
    <ul ref={parent}>
      {items.map((item) => (
        <li key={item.id}>{item.name}</li>
      ))}
    </ul>
  );
}

// ✨ React Transition Group
import { CSSTransition } from "react-transition-group";

function FadeInComponent({ show }) {
  return (
    <CSSTransition in={show} timeout={200} classNames="fade" unmountOnExit>
      <div>Fading content</div>
    </CSSTransition>
  );
}
```

---

<div align="center">

## 🎨 SVG Animation

</div>

### Bringing Vectors to Life 🎯

```javascript
// 🎨 Vivus.js - SVG drawing animations
import Vivus from "vivus";

new Vivus("my-svg", {
  duration: 200,
  type: "delayed",
  animTimingFunction: "ease-out",
});

// 🌊 Snap.svg - SVG manipulation
import Snap from "snapsvg";

const s = Snap("#svg");
const circle = s.circle(50, 50, 40);
circle.animate({ r: 100 }, 1000);

// ✨ SVG.js - Lightweight SVG library
import { SVG } from "@svgdotjs/svg.js";

const draw = SVG().addTo("#drawing").size(300, 300);
const rect = draw.rect(100, 100).fill("#f06");
rect.animate().move(150, 150);

// 🎯 Rough.js - Hand-drawn style
import rough from "roughjs";

const rc = rough.canvas(document.getElementById("canvas"));
rc.rectangle(10, 10, 200, 100, {
  fill: "red",
  fillStyle: "hachure",
  roughness: 2,
});
```

---

<div align="center">

## ⚡ Performance Optimization

</div>

### Animation Best Practices 🏎️

```javascript
// ✅ GOOD: Transform & Opacity (GPU accelerated)
.element {
  transform: translateX(100px);
  opacity: 0.5;
}

// ❌ BAD: Layout properties (causes reflow)
.element {
  left: 100px;
  width: 200px;
}

// Use will-change for complex animations
.will-animate {
  will-change: transform, opacity;
}

// Remove will-change when done
.animation-done {
  will-change: auto;
}

// Request Animation Frame for smooth 60fps
let start = null
function animate(timestamp) {
  if (!start) start = timestamp
  const progress = timestamp - start

  // Update animation based on progress
  element.style.transform = `translateX(${progress / 10}px)`

  if (progress < 2000) {
    requestAnimationFrame(animate)
  }
}
requestAnimationFrame(animate)

// Debounce scroll animations
let ticking = false
function updateAnimation() {
  if (!ticking) {
    requestAnimationFrame(() => {
      // Animation logic
      ticking = false
    })
    ticking = true
  }
}
window.addEventListener('scroll', updateAnimation)
```

---

<div align="center">

## 🎯 Animation Inspiration

</div>

### Showcase Sites 🌟

```
🎪 CodePen           → https://codepen.io/trending
   - Live examples
   - Animation demos
   - Fork & modify
   - Community driven

✨ Codrops          → https://tympanus.net/codrops
   - Cutting-edge demos
   - Tutorials
   - Experimental
   - Source code

🎨 UI Movement      → https://uimovement.com
   - UI animations
   - Daily inspiration
   - Real products
   - Categories

🌊 LottieFiles      → https://lottiefiles.com
   - Free animations
   - After Effects exports
   - Ready to use
   - Customizable
```

---

<div align="center">

## 🛠️ Animation Tools

</div>

### Visual Animation Builders 🎨

```
🎬 Theatre.js        → https://theatrejs.com
   - Visual editor
   - Complex sequences
   - React/Three.js
   - Professional tool

🎯 Rive             → https://rive.app
   - Interactive animations
   - State machines
   - Runtime engine
   - Cross-platform

✨ Spline           → https://spline.design
   - 3D web animations
   - No code tool
   - Export to web
   - Real-time

🎨 Jitter           → https://jitter.video
   - Motion design tool
   - Export to web
   - Team collaboration
   - Templates
```

---

<div align="center">

## 📐 Easing Functions

</div>

### Make Animations Feel Natural 🌊

```javascript
// Custom cubic-bezier easings
const easings = {
  // Smooth defaults
  easeInOut: 'cubic-bezier(0.4, 0, 0.2, 1)',
  easeOut: 'cubic-bezier(0, 0, 0.2, 1)',
  easeIn: 'cubic-bezier(0.4, 0, 1, 1)',

  // Material Design
  standard: 'cubic-bezier(0.4, 0, 0.2, 1)',
  deceleration: 'cubic-bezier(0, 0, 0.2, 1)',
  acceleration: 'cubic-bezier(0.4, 0, 1, 1)',
  sharp: 'cubic-bezier(0.4, 0, 0.6, 1)',

  // Playful
  bounce: 'cubic-bezier(0.68, -0.55, 0.265, 1.55)',
  elastic: 'cubic-bezier(0.175, 0.885, 0.32, 1.275)',

  // Smooth
  smooth: 'cubic-bezier(0.25, 0.46, 0.45, 0.94)',
  smoother: 'cubic-bezier(0.43, 0.13, 0.23, 0.96)',

  // Snappy
  swift: 'cubic-bezier(0.19, 1, 0.22, 1)',
  snappy: 'cubic-bezier(0.77, 0, 0.175, 1)'
}

// Usage
.element {
  transition: transform 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}
```

### Easing Resources 📊

```
📈 Cubic-bezier.com  → https://cubic-bezier.com
   - Visual editor
   - Compare easings
   - Copy values

🎯 Easings.net       → https://easings.net
   - Easing reference
   - Code examples
   - Visual demos

📊 Ceaser            → https://matthewlein.com/tools/ceaser
   - CSS easing tool
   - Presets
   - Custom curves
```

---

<div align="center">

## 💡 MrDib's Animation Tips

</div>

### Do's ✅

```
✓ Keep it under 300ms for UI
✓ Use transform & opacity
✓ Test on real devices
✓ Provide reduced motion option
✓ Use GPU acceleration
✓ Keep it meaningful
✓ Test performance
```

### Don'ts ❌

```
✗ Animate everything
✗ Use excessive duration
✗ Forget accessibility
✗ Animate width/height
✗ Block user interaction
✗ Overuse bounce effects
✗ Ignore performance
```

---

<div align="center">

## 🎭 Quick Animation Recipes

</div>

### Fade In on Scroll

```css
.fade-in {
  opacity: 0;
  transform: translateY(30px);
  transition: all 0.6s ease-out;
}

.fade-in.visible {
  opacity: 1;
  transform: translateY(0);
}
```

### Hover Effects

```css
.card {
  transition: transform 0.3s ease;
}

.card:hover {
  transform: translateY(-10px) scale(1.02);
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.15);
}
```

### Loading Animation

```css
.loader {
  width: 40px;
  height: 40px;
  border: 3px solid #f3f3f3;
  border-top: 3px solid #3498db;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
```

---

<div align="center">

_Remember: Animation is like salt - a little enhances everything, too much ruins the dish! 🧂_

</div>
