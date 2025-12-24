<div align="center">

# 🎭 Animation Libraries & Tools

### _Bringing life to the web with smooth, delightful animations_ ✨

![Animations](https://img.shields.io/badge/Animations-Smooth-purple?style=for-the-badge)
![Performance](https://img.shields.io/badge/60_FPS-Always-green?style=for-the-badge)
![Motion](https://img.shields.io/badge/Motion-Delightful-orange?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎬 JavaScript Animation Libraries](#-javascript-animation-libraries)
- [⚛️ React Animation Solutions](#️-react-animation-solutions)
- [🎨 CSS Animation Libraries](#-css-animation-libraries)
- [📜 Scroll Animations](#-scroll-animations)
- [📝 Text Animations](#-text-animations)
- [🎨 SVG Animation](#-svg-animation)
- [✨ 3D & WebGL](#-3d--webgl)
- [⚡ Performance & Best Practices](#-performance--best-practices)
- [🎯 Animation Patterns](#-animation-patterns)
- [💡 Tips & Resources](#-tips--resources)

---

<div align="center">

## 🎬 JavaScript Animation Libraries

</div>

### GSAP (GreenSock) - The Industry Standard 💪

```javascript
// ═══════════════════════════════════════════
// Installation
// ═══════════════════════════════════════════

// npm install gsap

import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

// ═══════════════════════════════════════════
// Basic Animations
// ═══════════════════════════════════════════

// Simple tween
gsap.to(".box", {
  x: 200,
  duration: 1,
  ease: "power2.out",
});

// From animation
gsap.from(".element", {
  opacity: 0,
  y: 50,
  duration: 1,
});

// FromTo animation
gsap.fromTo(
  ".card",
  { scale: 0, opacity: 0 },
  { scale: 1, opacity: 1, duration: 0.5 }
);

// Set (instant, no animation)
gsap.set(".menu", { x: -100 });

// ═══════════════════════════════════════════
// Timelines (Sequence Animations)
// ═══════════════════════════════════════════

const tl = gsap.timeline({
  defaults: { duration: 0.5, ease: "power2.out" },
});

tl.from(".hero-title", { y: -50, opacity: 0 })
  .from(".hero-subtitle", { y: 50, opacity: 0 }, "-=0.3") // Overlap
  .from(".hero-cta", { scale: 0, opacity: 0 })
  .from(".hero-image", { x: 100, opacity: 0 }, "<"); // Start with previous

// ═══════════════════════════════════════════
// Scroll-Triggered Animations
// ═══════════════════════════════════════════

gsap.from(".feature", {
  scrollTrigger: {
    trigger: ".feature",
    start: "top 80%",
    end: "top 50%",
    scrub: true, // Smooth scrubbing
    markers: true, // Debug markers
    toggleActions: "play none none reverse",
  },
  opacity: 0,
  y: 100,
});

// Parallax effect
gsap.to(".parallax", {
  scrollTrigger: {
    trigger: ".parallax",
    scrub: 1,
  },
  y: -200,
  ease: "none",
});

// ═══════════════════════════════════════════
// Advanced Features
// ═══════════════════════════════════════════

// Stagger (animate multiple elements)
gsap.from(".card", {
  y: 50,
  opacity: 0,
  duration: 0.5,
  stagger: 0.1, // 0.1s between each
});

// Repeat
gsap.to(".pulse", {
  scale: 1.2,
  duration: 0.5,
  repeat: -1, // Infinite
  yoyo: true, // Reverse
});

// Complex easing
gsap.to(".bounce", {
  y: -100,
  duration: 1,
  ease: "elastic.out(1, 0.3)",
});

// Control animation
const anim = gsap.to(".element", { x: 200, paused: true });
anim.play();
anim.pause();
anim.reverse();
anim.restart();

// ═══════════════════════════════════════════
// Utility Functions
// ═══════════════════════════════════════════

// Utility for dragging
import { Draggable } from "gsap/Draggable";
gsap.registerPlugin(Draggable);

Draggable.create(".draggable", {
  type: "x,y",
  bounds: ".container",
  inertia: true,
});

// Utility for morphing SVG
import { MorphSVGPlugin } from "gsap/MorphSVGPlugin";
gsap.registerPlugin(MorphSVGPlugin);

gsap.to("#shape1", {
  morphSVG: "#shape2",
  duration: 1,
});
```

**📦 GSAP Links:**

- Docs: https://greensock.com/docs/
- CDN: https://cdn.jsdelivr.net/npm/gsap@3/dist/gsap.min.js
- Pricing: Free (commercial license for some plugins)

> **💡 Pro Tip:** GSAP is the most powerful animation library with rock-solid performance. It's used by companies like Google, Nike, and Apple. The learning curve is gentle but the capabilities are endless!

---

### Anime.js - Lightweight & Powerful 🎯

```javascript
// ═══════════════════════════════════════════
// Installation
// ═══════════════════════════════════════════

// npm install animejs

import anime from "animejs";

// ═══════════════════════════════════════════
// Basic Animations
// ═══════════════════════════════════════════

// Simple animation
anime({
  targets: ".box",
  translateX: 250,
  rotate: "1turn",
  duration: 2000,
  easing: "easeInOutQuad",
});

// Multiple properties
anime({
  targets: ".element",
  translateY: [-100, 0],
  opacity: [0, 1],
  scale: [0.5, 1],
  delay: anime.stagger(100), // Delay each element
});

// ═══════════════════════════════════════════
// Advanced Features
// ═══════════════════════════════════════════

// Keyframes
anime({
  targets: ".ball",
  keyframes: [
    { translateY: -40 },
    { translateX: 250 },
    { translateY: 40 },
    { translateX: 0 },
    { translateY: 0 },
  ],
  duration: 4000,
  easing: "easeOutElastic(1, .8)",
  loop: true,
});

// Timeline
const tl = anime.timeline({
  easing: "easeOutExpo",
  duration: 750,
});

tl.add({
  targets: ".hero-title",
  translateY: [-50, 0],
  opacity: [0, 1],
}).add(
  {
    targets: ".hero-subtitle",
    translateY: [50, 0],
    opacity: [0, 1],
  },
  "-=500"
); // Start 500ms before previous ends

// ═══════════════════════════════════════════
// SVG Animations
// ═══════════════════════════════════════════

// Animate SVG path
anime({
  targets: "path",
  strokeDashoffset: [anime.setDashoffset, 0],
  easing: "easeInOutSine",
  duration: 1500,
  delay: anime.stagger(200),
});

// Morph SVG
anime({
  targets: "#polygon",
  points: [
    { value: "70 24 119 60 75 103 25 103 -19 60" },
    { value: "70 41 118 60 94 106 46 106 22 60" },
  ],
  easing: "easeOutQuad",
  duration: 2000,
  loop: true,
});

// ═══════════════════════════════════════════
// Controls
// ═══════════════════════════════════════════

const animation = anime({
  targets: ".box",
  translateX: 250,
  autoplay: false,
});

animation.play();
animation.pause();
animation.restart();
animation.reverse();
animation.seek(1000); // Jump to 1000ms
```

**📦 Anime.js Links:**

- Docs: https://animejs.com/documentation/
- Size: 16kb (minified + gzipped)
- License: MIT (Free)

> **💡 Pro Tip:** Anime.js is perfect for smaller projects or when you need a lightweight solution. It has a simple API but powerful features, especially for SVG animations!

---

### Motion One - Modern & Minimal ⚡

```javascript
// ═══════════════════════════════════════════
// Installation
// ═══════════════════════════════════════════

// npm install motion

import { animate, stagger, spring, inView } from "motion";

// ═══════════════════════════════════════════
// Basic Animations
// ═══════════════════════════════════════════

// Simple animation
animate(".box", { x: 100, opacity: 1 });

// With options
animate(
  ".element",
  { scale: 1.2, rotate: 45 },
  { duration: 0.5, easing: "ease-out" }
);

// Spring physics (no duration needed!)
animate(
  ".spring",
  { y: 100 },
  { easing: spring({ stiffness: 300, damping: 20 }) }
);

// ═══════════════════════════════════════════
// Advanced Features
// ═══════════════════════════════════════════

// Stagger animations
animate(".card", { opacity: 1, y: 0 }, { delay: stagger(0.1) });

// Sequence (timeline)
animate(".element", { x: 100 })
  .then(() => animate(".element", { y: 100 }))
  .then(() => animate(".element", { scale: 1.5 }));

// Scroll animations
inView(".section", (info) => {
  animate(info.target, { opacity: 1, y: 0 });
});

// With scroll progress
inView(".parallax", ({ target }) => {
  animate(
    target,
    { y: [0, -100] },
    {
      easing: "linear",
      scrollOptions: {
        target,
        offset: ["start end", "end start"],
      },
    }
  );
});

// ═══════════════════════════════════════════
// Controls
// ═══════════════════════════════════════════

const controls = animate(".box", { x: 100 });

controls.pause();
controls.play();
controls.cancel();
controls.finish();
```

**📦 Motion One Links:**

- Docs: https://motion.dev/
- Size: 5kb (70% smaller than Framer Motion)
- License: MIT (Free)

> **💡 Pro Tip:** Motion One is the future - built on Web Animations API, it's incredibly small and fast. Great for modern projects where bundle size matters!

---

<div align="center">

## ⚛️ React Animation Solutions

</div>

### Framer Motion - React's Animation Powerhouse 🎭

```jsx
// ═══════════════════════════════════════════
// Installation
// ═══════════════════════════════════════════

// npm install framer-motion

import {
  motion,
  useAnimation,
  useInView,
  AnimatePresence,
} from "framer-motion";

// ═══════════════════════════════════════════
// Basic Animations
// ═══════════════════════════════════════════

function FadeIn() {
  return (
    <motion.div
      initial={{ opacity: 0, y: 20 }}
      animate={{ opacity: 1, y: 0 }}
      transition={{ duration: 0.5 }}
    >
      Content
    </motion.div>
  );
}

// ═══════════════════════════════════════════
// Gesture Animations
// ═══════════════════════════════════════════

function InteractiveCard() {
  return (
    <motion.div
      whileHover={{ scale: 1.05 }}
      whileTap={{ scale: 0.95 }}
      drag
      dragConstraints={{ left: -100, right: 100, top: -50, bottom: 50 }}
      dragElastic={0.2}
    >
      Drag me!
    </motion.div>
  );
}

// ═══════════════════════════════════════════
// Variants (Reusable Animations)
// ═══════════════════════════════════════════

const containerVariants = {
  hidden: { opacity: 0 },
  visible: {
    opacity: 1,
    transition: {
      staggerChildren: 0.1,
      delayChildren: 0.3,
    },
  },
};

const itemVariants = {
  hidden: { y: 20, opacity: 0 },
  visible: { y: 0, opacity: 1 },
};

function StaggerList() {
  return (
    <motion.ul variants={containerVariants} initial="hidden" animate="visible">
      {items.map((item) => (
        <motion.li key={item.id} variants={itemVariants}>
          {item.text}
        </motion.li>
      ))}
    </motion.ul>
  );
}

// ═══════════════════════════════════════════
// Layout Animations (Magic!)
// ═══════════════════════════════════════════

function LayoutAnimation() {
  const [isOpen, setIsOpen] = useState(false);

  return (
    <motion.div
      layout
      onClick={() => setIsOpen(!isOpen)}
      style={{
        width: isOpen ? 300 : 150,
        height: isOpen ? 200 : 100,
      }}
    >
      <motion.h2 layout>Title</motion.h2>
      {isOpen && <motion.p layout>Content</motion.p>}
    </motion.div>
  );
}

// ═══════════════════════════════════════════
// Exit Animations with AnimatePresence
// ═══════════════════════════════════════════

function Modal({ isOpen, onClose }) {
  return (
    <AnimatePresence>
      {isOpen && (
        <>
          <motion.div
            initial={{ opacity: 0 }}
            animate={{ opacity: 1 }}
            exit={{ opacity: 0 }}
            onClick={onClose}
            className="backdrop"
          />
          <motion.div
            initial={{ scale: 0.8, opacity: 0 }}
            animate={{ scale: 1, opacity: 1 }}
            exit={{ scale: 0.8, opacity: 0 }}
            className="modal"
          >
            <h2>Modal Content</h2>
            <button onClick={onClose}>Close</button>
          </motion.div>
        </>
      )}
    </AnimatePresence>
  );
}

// ═══════════════════════════════════════════
// Scroll Animations
// ═══════════════════════════════════════════

import { useScroll, useTransform } from "framer-motion";

function ParallaxSection() {
  const { scrollYProgress } = useScroll();
  const y = useTransform(scrollYProgress, [0, 1], [0, -100]);
  const opacity = useTransform(scrollYProgress, [0, 0.5, 1], [1, 0.5, 0]);

  return <motion.div style={{ y, opacity }}>Parallax content</motion.div>;
}

// Scroll-triggered animation
function FadeInOnScroll() {
  const ref = useRef(null);
  const isInView = useInView(ref, { once: true });

  return (
    <motion.div
      ref={ref}
      initial={{ opacity: 0, y: 50 }}
      animate={isInView ? { opacity: 1, y: 0 } : {}}
      transition={{ duration: 0.6 }}
    >
      Scroll to reveal
    </motion.div>
  );
}

// ═══════════════════════════════════════════
// SVG Path Animation
// ═══════════════════════════════════════════

function DrawSVG() {
  const pathLength = useMotionValue(0);

  return (
    <motion.svg>
      <motion.path
        d="M0 100 Q 50 10 100 100"
        stroke="#000"
        fill="transparent"
        initial={{ pathLength: 0 }}
        animate={{ pathLength: 1 }}
        transition={{ duration: 2 }}
      />
    </motion.svg>
  );
}

// ═══════════════════════════════════════════
// Spring Animations
// ═══════════════════════════════════════════

function SpringBox() {
  return (
    <motion.div
      animate={{ x: 100 }}
      transition={{
        type: "spring",
        stiffness: 300,
        damping: 20,
      }}
    >
      Springy!
    </motion.div>
  );
}
```

**📦 Framer Motion Links:**

- Docs: https://www.framer.com/motion/
- Playground: https://www.framer.com/motion/examples/
- License: MIT (Free)

> **💡 Pro Tip:** Framer Motion's layout animations are magical - they automatically animate size and position changes. Perfect for complex UI transitions!

---

### React Spring - Physics-Based Animations 🌊

```jsx
// ═══════════════════════════════════════════
// Installation
// ═══════════════════════════════════════════

// npm install react-spring

import { useSpring, animated, useTrail, useChain } from "react-spring";

// ═══════════════════════════════════════════
// Basic Spring
// ═══════════════════════════════════════════

function FadeIn() {
  const props = useSpring({
    from: { opacity: 0, transform: "translate3d(0,40px,0)" },
    to: { opacity: 1, transform: "translate3d(0,0px,0)" },
    config: { tension: 280, friction: 60 },
  });

  return <animated.div style={props}>Content</animated.div>;
}

// ═══════════════════════════════════════════
// Interactive Spring
// ═══════════════════════════════════════════

function InteractiveBox() {
  const [flipped, setFlipped] = useState(false);

  const { transform, opacity } = useSpring({
    opacity: flipped ? 1 : 0,
    transform: `perspective(600px) rotateX(${flipped ? 180 : 0}deg)`,
    config: { mass: 5, tension: 500, friction: 80 },
  });

  return (
    <animated.div
      onClick={() => setFlipped(!flipped)}
      style={{
        opacity: opacity.to((o) => 1 - o),
        transform,
      }}
    >
      Click me!
    </animated.div>
  );
}

// ═══════════════════════════════════════════
// Trail (Stagger)
// ═══════════════════════════════════════════

function TrailAnimation({ items }) {
  const trail = useTrail(items.length, {
    from: { opacity: 0, x: -20 },
    to: { opacity: 1, x: 0 },
  });

  return (
    <div>
      {trail.map((props, index) => (
        <animated.div key={index} style={props}>
          {items[index]}
        </animated.div>
      ))}
    </div>
  );
}

// ═══════════════════════════════════════════
// Chain Animations
// ═══════════════════════════════════════════

function ChainedAnimation() {
  const springRef = useRef();
  const { size } = useSpring({
    ref: springRef,
    from: { size: "20%" },
    to: { size: "100%" },
  });

  const trailRef = useRef();
  const trail = useTrail(5, {
    ref: trailRef,
    from: { opacity: 0 },
    to: { opacity: 1 },
  });

  // Chain them together
  useChain([springRef, trailRef], [0, 0.5]);

  return <animated.div style={{ width: size }}>Content</animated.div>;
}
```

**📦 React Spring Links:**

- Docs: https://www.react-spring.dev/
- Examples: https://www.react-spring.dev/examples
- License: MIT (Free)

> **💡 Pro Tip:** React Spring uses physics-based animations - no durations needed! The animations feel more natural and responsive. Great for interactive UIs!

---

### Auto Animate - Zero Configuration ✨

```jsx
// ═══════════════════════════════════════════
// Installation
// ═══════════════════════════════════════════

// npm install @formkit/auto-animate

import { useAutoAnimate } from "@formkit/auto-animate/react";

// ═══════════════════════════════════════════
// Automatic List Animations
// ═══════════════════════════════════════════

function TodoList() {
  const [parent] = useAutoAnimate();
  const [todos, setTodos] = useState([]);

  return (
    <ul ref={parent}>
      {todos.map((todo) => (
        <li key={todo.id}>{todo.text}</li>
      ))}
    </ul>
  );
}

// ═══════════════════════════════════════════
// With Custom Options
// ═══════════════════════════════════════════

function AnimatedGrid() {
  const [parent] = useAutoAnimate({
    duration: 250,
    easing: "ease-in-out",
  });

  return (
    <div ref={parent} className="grid">
      {items.map((item) => (
        <div key={item.id}>{item.name}</div>
      ))}
    </div>
  );
}

// ═══════════════════════════════════════════
// Conditional Rendering
// ═══════════════════════════════════════════

function Accordion() {
  const [parent] = useAutoAnimate();
  const [isOpen, setIsOpen] = useState(false);

  return (
    <div ref={parent}>
      <button onClick={() => setIsOpen(!isOpen)}>Toggle</button>
      {isOpen && (
        <div className="content">Animated content appears smoothly!</div>
      )}
    </div>
  );
}
```

**📦 Auto Animate Links:**

- Docs: https://auto-animate.formkit.com/
- Size: 2.7kb
- License: MIT (Free)

> **💡 Pro Tip:** Auto Animate is magic - just add one ref and all DOM changes animate automatically. Perfect for lists, conditional rendering, and dynamic content!

---

<div align="center">

## 🎨 CSS Animation Libraries

</div>

### Animate.css - Plug & Play Animations 🎯

```html
<!-- ═══════════════════════════════════════════ -->
<!-- Installation -->
<!-- ═══════════════════════════════════════════ -->

<!-- CDN -->
<link
  rel="stylesheet"
  href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css"
/>

<!-- npm -->
<!-- npm install animate.css -->

<!-- ═══════════════════════════════════════════ -->
<!-- Basic Usage -->
<!-- ═══════════════════════════════════════════ -->

<h1 class="animate__animated animate__bounce">Bouncing Title!</h1>

<div class="animate__animated animate__fadeIn">Fading in...</div>

<button class="animate__animated animate__pulse animate__infinite">
  Pulsing button!
</button>

<!-- ═══════════════════════════════════════════ -->
<!-- With Delays & Durations -->
<!-- ═══════════════════════════════════════════ -->

<div class="animate__animated animate__fadeIn animate__delay-1s">
  Delayed 1 second
</div>

<div class="animate__animated animate__bounce animate__slow">
  Slower bounce (2s)
</div>

<div class="animate__animated animate__shake animate__fast">
  Faster shake (800ms)
</div>

<!-- ═══════════════════════════════════════════ -->
<!-- Custom Properties -->
<!-- ═══════════════════════════════════════════ -->

<style>
  .custom-animation {
    --animate-duration: 2s;
    --animate-delay: 0.5s;
    --animate-repeat: 3;
  }
</style>

<div class="animate__animated animate__fadeIn custom-animation">
  Custom timing!
</div>
```

**🎯 Popular Animations:**

```
Attention Seekers:
  - bounce, flash, pulse, rubberBand, shakeX, shakeY, headShake, swing, tada, wobble, jello, heartBeat

Entrances:
  - fadeIn, fadeInDown, fadeInLeft, fadeInRight, fadeInUp
  - slideInDown, slideInLeft, slideInRight, slideInUp
  - zoomIn, zoomInDown, zoomInLeft, zoomInRight, zoomInUp

Exits:
  - fadeOut, fadeOutDown, fadeOutLeft, fadeOutRight, fadeOutUp
  - slideOutDown, slideOutLeft, slideOutRight, slideOutUp
  - zoomOut, zoomOutDown, zoomOutLeft, zoomOutRight, zoomOutUp

Specials:
  - flip, flipInX, flipInY, flipOutX, flipOutY
  - rotateIn, rotateInDownLeft, rotateInUpLeft
  - rollIn, rollOut
```

**📦 Animate.css Links:**

- Docs: https://animate.style/
- Size: 4kb (gzipped)
- License: MIT (Free)

> **💡 Pro Tip:** Perfect for quick prototypes and simple animations. Just add classes and you're done. Great for attention-seekers and page transitions!

---

### AOS (Animate On Scroll) - Scroll Reveal Made Easy 📜

```html
<!-- ═══════════════════════════════════════════ -->
<!-- Installation -->
<!-- ═══════════════════════════════════════════ -->

<!-- CDN -->
<link rel="stylesheet" href="https://unpkg.com/aos@next/dist/aos.css" />
<script src="https://unpkg.com/aos@next/dist/aos.js"></script>

<!-- npm install aos -->

<!-- ═══════════════════════════════════════════ -->
<!-- Basic Usage -->
<!-- ═══════════════════════════════════════════ -->

<div data-aos="fade-up">Fade up on scroll</div>

<div data-aos="zoom-in" data-aos-duration="1000">Zoom in with 1s duration</div>

<div data-aos="slide-right" data-aos-delay="300">
  Slide right with 300ms delay
</div>

<!-- ═══════════════════════════════════════════ -->
<!-- Advanced Options -->
<!-- ═══════════════════════════════════════════ -->

<div
  data-aos="fade-up"
  data-aos-offset="200"
  data-aos-delay="50"
  data-aos-duration="1000"
  data-aos-easing="ease-in-out"
  data-aos-mirror="true"
  data-aos-once="false"
  data-aos-anchor-placement="top-center"
>
  Advanced animation
</div>

<script>
  // ═══════════════════════════════════════════
  // Initialize AOS
  // ═══════════════════════════════════════════

  AOS.init({
    // Global settings
    duration: 800,
    easing: "ease-in-out",
    once: true,
    mirror: false,
    offset: 120,

    // Mobile settings
    disable: "mobile", // Disable on mobile
    // Or: disable: window.innerWidth < 768

    // Advanced
    startEvent: "DOMContentLoaded",
    animatedClassName: "aos-animate",
    initClassName: "aos-init",
  });

  // Refresh AOS (after dynamic content)
  AOS.refresh();
</script>
```

**🎯 Animation Types:**

```
Fade:
  - fade, fade-up, fade-down, fade-left, fade-right
  - fade-up-right, fade-up-left, fade-down-right, fade-down-left

Flip:
  - flip-up, flip-down, flip-left, flip-right

Slide:
  - slide-up, slide-down, slide-left, slide-right

Zoom:
  - zoom-in, zoom-in-up, zoom-in-down, zoom-in-left, zoom-in-right
  - zoom-out, zoom-out-up, zoom-out-down, zoom-out-left, zoom-out-right
```

**📦 AOS Links:**

- Docs: https://michalsnik.github.io/aos/
- GitHub: https://github.com/michalsnik/aos
- License: MIT (Free)

> **💡 Pro Tip:** AOS is the easiest way to add scroll animations. Set it up once and add data attributes. Perfect for marketing pages and portfolios!

---

<div align="center">

## 📜 Scroll Animations

</div>

### Intersection Observer (Native API) 👁️

```javascript
// ═══════════════════════════════════════════
// Basic Intersection Observer
// ═══════════════════════════════════════════

const observer = new IntersectionObserver(
  (entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        entry.target.classList.add("animate");
      }
    });
  },
  {
    threshold: 0.1, // Trigger when 10% visible
    rootMargin: "0px 0px -100px 0px", // Offset
  }
);

// Observe elements
document.querySelectorAll(".fade-in").forEach((el) => {
  observer.observe(el);
});

// ═══════════════════════════════════════════
// Advanced: Scroll Progress
// ═══════════════════════════════════════════

const progressObserver = new IntersectionObserver(
  (entries) => {
    entries.forEach((entry) => {
      const progress = entry.intersectionRatio;
      entry.target.style.opacity = progress;
      entry.target.style.transform = `translateY(${(1 - progress) * 50}px)`;
    });
  },
  {
    threshold: Array.from({ length: 100 }, (_, i) => i / 100),
  }
);

// ═══════════════════════════════════════════
// Reusable Hook (React)
// ═══════════════════════════════════════════

function useIntersectionObserver(options = {}) {
  const [isIntersecting, setIsIntersecting] = useState(false);
  const ref = useRef(null);

  useEffect(() => {
    const observer = new IntersectionObserver(
      ([entry]) => setIsIntersecting(entry.isIntersecting),
      options
    );

    if (ref.current) {
      observer.observe(ref.current);
    }

    return () => observer.disconnect();
  }, []);

  return [ref, isIntersecting];
}

// Usage
function FadeInOnScroll() {
  const [ref, isVisible] = useIntersectionObserver({ threshold: 0.5 });

  return (
    <div
      ref={ref}
      style={{
        opacity: isVisible ? 1 : 0,
        transition: "opacity 0.6s",
      }}
    >
      Content
    </div>
  );
}
```

---

### Lenis - Smooth Scroll Library 🌊

```javascript
// ═══════════════════════════════════════════
// Installation
// ═══════════════════════════════════════════

// npm install @studio-freight/lenis

import Lenis from "@studio-freight/lenis";

// ═══════════════════════════════════════════
// Basic Setup
// ═══════════════════════════════════════════

const lenis = new Lenis({
  duration: 1.2,
  easing: (t) => Math.min(1, 1.001 - Math.pow(2, -10 * t)),
  direction: "vertical",
  gestureDirection: "vertical",
  smooth: true,
  mouseMultiplier: 1,
  smoothTouch: false,
  touchMultiplier: 2,
  infinite: false,
});

// Animation frame loop
function raf(time) {
  lenis.raf(time);
  requestAnimationFrame(raf);
}

requestAnimationFrame(raf);

// ═══════════════════════════════════════════
// Scroll To Element
// ═══════════════════════════════════════════

document.querySelectorAll('a[href^="#"]').forEach((anchor) => {
  anchor.addEventListener("click", function (e) {
    e.preventDefault();
    lenis.scrollTo(this.getAttribute("href"));
  });
});

// Scroll to specific position
lenis.scrollTo(1000); // Scroll to 1000px

// Scroll to element
lenis.scrollTo("#section-2", {
  offset: 0,
  duration: 2,
  easing: (t) => t,
  immediate: false,
});

// ═══════════════════════════════════════════
// Events
// ═══════════════════════════════════════════

lenis.on("scroll", ({ scroll, velocity, direction, progress }) => {
  console.log({ scroll, velocity, direction, progress });
});

// ═══════════════════════════════════════════
// Control Methods
// ═══════════════════════════════════════════

lenis.start();
lenis.stop();
lenis.destroy();
```

**📦 Lenis Links:**

- GitHub: https://github.com/studio-freight/lenis
- Demo: https://lenis.studiofreight.com/
- License: MIT (Free)

> **💡 Pro Tip:** Lenis provides buttery smooth scrolling. It's lightweight and performant - perfect for creating that premium feel in your websites!

---

<div align="center">

## 📝 Text Animations

</div>

### Splitting.js - Character-Level Control ✂️

```javascript
// ═══════════════════════════════════════════
// Installation
// ═══════════════════════════════════════════

// npm install splitting

import Splitting from 'splitting';
import 'splitting/dist/splitting.css';

// ═══════════════════════════════════════════
// Basic Splitting
// ═══════════════════════════════════════════

// Split by characters
Splitting({ target: '.text', by: 'chars' });

// Split by words
Splitting({ target: '.text', by: 'words' });

// Split by lines
Splitting({ target: '.text', by: 'lines' });

// ═══════════════════════════════════════════
// Animate with CSS
// ═══════════════════════════════════════════

<style>
.text .char {
    display: inline-block;
    animation: fadeIn 0.5s ease forwards;
    opacity: 0;
    animation-delay: calc(0.05s * var(--char-index));
}

@keyframes fadeIn {
    to {
        opacity: 1;
        transform: translateY(0);
    }
}
</style>

// ═══════════════════════════════════════════
// Animate with GSAP
// ═══════════════════════════════════════════

Splitting({ target: '.title', by: 'chars' });

gsap.from('.title .char', {
    opacity: 0,
    y: 50,
    stagger: 0.05,
    duration: 0.5,
    ease: 'back.out(1.7)'
});

// ═══════════════════════════════════════════
// Advanced: Custom Splitting
// ═══════════════════════════════════════════

Splitting({
    target: '.fancy-text',
    by: 'chars',
    key: null
});

// Reveal animation
gsap.timeline()
    .from('.fancy-text .char', {
        opacity: 0,
        scale: 0,
        stagger: 0.02,
        ease: 'back.out(1.7)'
    })
    .to('.fancy-text .char', {
        color: '#ff0000',
        stagger: 0.02
    });
```

**📦 Splitting.js Links:**

- Docs: https://splitting.js.org/
- Size: 3kb
- License: MIT (Free)

---

### Typed.js - Typing Effect 📝

```javascript
// ═══════════════════════════════════════════
// Installation
// ═══════════════════════════════════════════

// npm install typed.js

import Typed from "typed.js";

// ═══════════════════════════════════════════
// Basic Typing
// ═══════════════════════════════════════════

const typed = new Typed("#element", {
  strings: [
    "I am a developer.",
    "I build amazing things.",
    "I love TypeScript!",
  ],
  typeSpeed: 50,
  backSpeed: 50,
  backDelay: 1000,
  startDelay: 500,
  loop: true,
  showCursor: true,
  cursorChar: "|",
  autoInsertCss: true,
});

// ═══════════════════════════════════════════
// Advanced Options
// ═══════════════════════════════════════════

const advancedTyped = new Typed("#advanced", {
  strings: [
    "First sentence.",
    "Second sentence with ^1000 pause.",
    "Third ^500 sentence with ^1000 multiple pauses.",
  ],
  typeSpeed: 40,
  backSpeed: 40,
  smartBackspace: true, // Only backspace what differs
  shuffle: false,
  backDelay: 700,
  fadeOut: false,
  fadeOutClass: "typed-fade-out",
  fadeOutDelay: 500,
  loop: true,
  loopCount: Infinity,
  showCursor: true,
  cursorChar: "_",
  autoInsertCss: true,
  attr: null,
  bindInputFocusEvents: false,
  contentType: "html",

  // Callbacks
  onBegin: (self) => {},
  onComplete: (self) => {},
  preStringTyped: (arrayPos, self) => {},
  onStringTyped: (arrayPos, self) => {},
  onLastStringBackspaced: (self) => {},
  onTypingPaused: (arrayPos, self) => {},
  onTypingResumed: (arrayPos, self) => {},
  onReset: (self) => {},
  onStop: (arrayPos, self) => {},
  onStart: (arrayPos, self) => {},
  onDestroy: (self) => {},
});

// ═══════════════════════════════════════════
// Control Methods
// ═══════════════════════════════════════════

typed.toggle(); // Start/stop typing
typed.stop(); // Stop typing
typed.start(); // Start typing
typed.destroy(); // Destroy instance
typed.reset(); // Reset and restart
```

**📦 Typed.js Links:**

- Docs: https://github.com/mattboldt/typed.js
- Demo: https://mattboldt.github.io/typed.js/
- License: MIT (Free)

> **💡 Pro Tip:** Typed.js is perfect for hero sections and landing pages. Combine it with other animations for maximum impact!

---

<div align="center">

## 🎨 SVG Animation

</div>

### SVG Path Animation 🎯

```javascript
// ═══════════════════════════════════════════
// Vivus.js - SVG Drawing Animation
// ═══════════════════════════════════════════

// npm install vivus

import Vivus from 'vivus';

new Vivus('my-svg', {
    type: 'delayed',        // 'delayed' | 'sync' | 'oneByOne'
    duration: 200,
    start: 'autostart',     // 'autostart' | 'manual' | 'inViewport'
    forceRender: false,
    animTimingFunction: Vivus.EASE
});

// ═══════════════════════════════════════════
// Anime.js SVG Path Drawing
// ═══════════════════════════════════════════

anime({
    targets: 'path',
    strokeDashoffset: [anime.setDashoffset, 0],
    easing: 'easeInOutSine',
    duration: 1500,
    delay: (el, i) => i * 250
});

// ═══════════════════════════════════════════
// GSAP SVG Animation
// ═══════════════════════════════════════════

gsap.from('path', {
    drawSVG: '0%',
    duration: 2,
    stagger: 0.2,
    ease: 'power2.inOut'
});

// Morph SVG shapes
gsap.to('#shape1', {
    morphSVG: '#shape2',
    duration: 1,
    ease: 'power1.inOut'
});

// ═══════════════════════════════════════════
// CSS-Only SVG Animation
// ═══════════════════════════════════════════

<style>
/* Get path length first */
path {
    stroke-dasharray: 1000;
    stroke-dashoffset: 1000;
    animation: draw 2s ease-out forwards;
}

@keyframes draw {
    to {
        stroke-dashoffset: 0;
    }
}
</style>
```

---

<div align="center">

## ✨ 3D & WebGL

</div>

### Three.js - 3D Graphics 🎮

```javascript
// ═══════════════════════════════════════════
// Installation
// ═══════════════════════════════════════════

// npm install three

import * as THREE from "three";
import { OrbitControls } from "three/examples/jsm/controls/OrbitControls";

// ═══════════════════════════════════════════
// Basic Setup
// ═══════════════════════════════════════════

// Scene
const scene = new THREE.Scene();

// Camera
const camera = new THREE.PerspectiveCamera(
  75,
  window.innerWidth / window.innerHeight,
  0.1,
  1000
);
camera.position.z = 5;

// Renderer
const renderer = new THREE.WebGLRenderer({ antialias: true });
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

// ═══════════════════════════════════════════
// Create Animated Object
// ═══════════════════════════════════════════

// Geometry
const geometry = new THREE.BoxGeometry(1, 1, 1);
const material = new THREE.MeshPhongMaterial({ color: 0x00ff00 });
const cube = new THREE.Mesh(geometry, material);
scene.add(cube);

// Lighting
const light = new THREE.DirectionalLight(0xffffff, 1);
light.position.set(5, 5, 5);
scene.add(light);

// ═══════════════════════════════════════════
// Animation Loop
// ═══════════════════════════════════════════

function animate() {
  requestAnimationFrame(animate);

  // Animate cube
  cube.rotation.x += 0.01;
  cube.rotation.y += 0.01;

  renderer.render(scene, camera);
}

animate();

// ═══════════════════════════════════════════
// React Three Fiber (React Integration)
// ═══════════════════════════════════════════

// npm install @react-three/fiber @react-three/drei

import { Canvas } from "@react-three/fiber";
import { OrbitControls } from "@react-three/drei";

function Box() {
  const meshRef = useRef();

  useFrame(() => {
    meshRef.current.rotation.x += 0.01;
    meshRef.current.rotation.y += 0.01;
  });

  return (
    <mesh ref={meshRef}>
      <boxGeometry args={[1, 1, 1]} />
      <meshStandardMaterial color="hotpink" />
    </mesh>
  );
}

function Scene() {
  return (
    <Canvas>
      <ambientLight intensity={0.5} />
      <directionalLight position={[10, 10, 5]} />
      <Box />
      <OrbitControls />
    </Canvas>
  );
}
```

**📦 Three.js Links:**

- Docs: https://threejs.org/docs/
- Examples: https://threejs.org/examples/
- License: MIT (Free)

> **💡 Pro Tip:** Three.js is powerful but complex. Use React Three Fiber if you're building with React - it makes 3D development much more enjoyable!

---

<div align="center">

## ⚡ Performance & Best Practices

</div>

### Animation Performance Tips 🏎️

```javascript
// ═══════════════════════════════════════════
// Optimize Animations
// ═══════════════════════════════════════════

// ✅ GOOD: Transform & Opacity (GPU-accelerated)
.element {
    transform: translateX(100px);
    opacity: 0.5;
}

// ❌ BAD: Layout properties (causes reflow)
.element {
    left: 100px;
    width: 200px;
    margin-left: 50px;
}

// ✅ Use will-change for complex animations
.will-animate {
    will-change: transform, opacity;
}

// ❌ Don't overuse will-change
.everything {
    will-change: transform, opacity, color, width, height;  // Too much!
}

// ✅ Remove will-change after animation
element.addEventListener('animationend', () => {
    element.style.willChange = 'auto';
});

// ═══════════════════════════════════════════
// Use requestAnimationFrame
// ═══════════════════════════════════════════

// ✅ GOOD: Synced with browser refresh
function animate() {
    element.style.transform = `translateX(${position}px)`;
    requestAnimationFrame(animate);
}

// ❌ BAD: setInterval can cause jank
setInterval(() => {
    element.style.transform = `translateX(${position}px)`;
}, 16);

// ═══════════════════════════════════════════
// Debounce Scroll Events
// ═══════════════════════════════════════════

let ticking = false;

function onScroll() {
    if (!ticking) {
        requestAnimationFrame(() => {
            updateAnimations();
            ticking = false;
        });
        ticking = true;
    }
}

window.addEventListener('scroll', onScroll);

// ═══════════════════════════════════════════
// Reduce Motion (Accessibility)
// ═══════════════════════════════════════════

// Check user preference
const prefersReducedMotion = window.matchMedia(
    '(prefers-reduced-motion: reduce)'
).matches;

if (!prefersReducedMotion) {
    // Enable animations
    enableAnimations();
}

// CSS Media Query
@media (prefers-reduced-motion: reduce) {
    * {
        animation-duration: 0.01ms !important;
        animation-iteration-count: 1 !important;
        transition-duration: 0.01ms !important;
    }
}

// ═══════════════════════════════════════════
// Intersection Observer for Performance
// ═══════════════════════════════════════════

// Only animate when in viewport
const observer = new IntersectionObserver(
    (entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.classList.add('animate');
                // Optional: Stop observing after animation
                observer.unobserve(entry.target);
            }
        });
    },
    {
        threshold: 0.1,
        rootMargin: '50px'  // Start animation slightly before visible
    }
);

// ═══════════════════════════════════════════
// Layer Promotion
// ═══════════════════════════════════════════

// Force layer creation for smooth animation
.animated-element {
    transform: translateZ(0);
    /* or */
    will-change: transform;
    /* or */
    backface-visibility: hidden;
}

// ═══════════════════════════════════════════
// Avoid Layout Thrashing
// ═══════════════════════════════════════════

// ❌ BAD: Interleaved reads and writes
elements.forEach(el => {
    const height = el.offsetHeight;  // Read
    el.style.height = height * 2 + 'px';  // Write
});

// ✅ GOOD: Batch reads, then batch writes
const heights = elements.map(el => el.offsetHeight);  // Read all
elements.forEach((el, i) => {
    el.style.height = heights[i] * 2 + 'px';  // Write all
});
```

> **💡 Pro Tip:** Always test animations on lower-end devices! What runs smoothly on your MacBook might stutter on a budget smartphone. Use Chrome DevTools to throttle CPU and test performance!

---

<div align="center">

## 🎯 Animation Patterns

</div>

### Common Animation Recipes 🍳

```css
/* ═══════════════════════════════════════════ */
/* Fade In on Scroll */
/* ═══════════════════════════════════════════ */

.fade-in {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.6s ease-out, transform 0.6s ease-out;
}

.fade-in.visible {
  opacity: 1;
  transform: translateY(0);
}

/* ═══════════════════════════════════════════ */
/* Card Hover Effect */
/* ═══════════════════════════════════════════ */

.card {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-10px) scale(1.02);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
}

/* ═══════════════════════════════════════════ */
/* Button Press Animation */
/* ═══════════════════════════════════════════ */

.button {
  transition: transform 0.1s ease;
}

.button:active {
  transform: scale(0.95);
}

/* ═══════════════════════════════════════════ */
/* Loading Spinner */
/* ═══════════════════════════════════════════ */

.spinner {
  width: 40px;
  height: 40px;
  border: 4px solid rgba(0, 0, 0, 0.1);
  border-top-color: #3498db;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

/* ═══════════════════════════════════════════ */
/* Skeleton Loading */
/* ═══════════════════════════════════════════ */

.skeleton {
  background: linear-gradient(90deg, #f0f0f0 25%, #e0e0e0 50%, #f0f0f0 75%);
  background-size: 200% 100%;
  animation: loading 1.5s infinite;
}

@keyframes loading {
  0% {
    background-position: 200% 0;
  }
  100% {
    background-position: -200% 0;
  }
}

/* ═══════════════════════════════════════════ */
/* Pulse Effect */
/* ═══════════════════════════════════════════ */

.pulse {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}

@keyframes pulse {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

/* ═══════════════════════════════════════════ */
/* Bounce Animation */
/* ═══════════════════════════════════════════ */

.bounce {
  animation: bounce 1s ease infinite;
}

@keyframes bounce {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-20px);
  }
}

/* ═══════════════════════════════════════════ */
/* Shake Animation */
/* ═══════════════════════════════════════════ */

.shake {
  animation: shake 0.5s ease;
}

@keyframes shake {
  0%,
  100% {
    transform: translateX(0);
  }
  10%,
  30%,
  50%,
  70%,
  90% {
    transform: translateX(-10px);
  }
  20%,
  40%,
  60%,
  80% {
    transform: translateX(10px);
  }
}

/* ═══════════════════════════════════════════ */
/* Gradient Animation */
/* ═══════════════════════════════════════════ */

.gradient-text {
  background: linear-gradient(
    45deg,
    #ff0000,
    #ff7300,
    #fffb00,
    #48ff00,
    #00ffd5,
    #002bff,
    #7a00ff,
    #ff00c8,
    #ff0000
  );
  background-size: 400%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: gradient 10s ease infinite;
}

@keyframes gradient {
  0%,
  100% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
}

/* ═══════════════════════════════════════════ */
/* Typewriter Effect */
/* ═══════════════════════════════════════════ */

.typewriter {
  overflow: hidden;
  border-right: 2px solid;
  white-space: nowrap;
  animation: typing 3.5s steps(40, end), blink-caret 0.75s step-end infinite;
}

@keyframes typing {
  from {
    width: 0;
  }
  to {
    width: 100%;
  }
}

@keyframes blink-caret {
  from,
  to {
    border-color: transparent;
  }
  50% {
    border-color: currentColor;
  }
}

/* ═══════════════════════════════════════════ */
/* Slide In Animations */
/* ═══════════════════════════════════════════ */

.slide-in-left {
  animation: slideInLeft 0.5s ease-out;
}

@keyframes slideInLeft {
  from {
    transform: translateX(-100%);
    opacity: 0;
  }
  to {
    transform: translateX(0);
    opacity: 1;
  }
}

.slide-in-right {
  animation: slideInRight 0.5s ease-out;
}

@keyframes slideInRight {
  from {
    transform: translateX(100%);
    opacity: 0;
  }
  to {
    transform: translateX(0);
    opacity: 1;
  }
}

/* ═══════════════════════════════════════════ */
/* Scale In Animation */
/* ═══════════════════════════════════════════ */

.scale-in {
  animation: scaleIn 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

@keyframes scaleIn {
  from {
    transform: scale(0);
    opacity: 0;
  }
  to {
    transform: scale(1);
    opacity: 1;
  }
}

/* ═══════════════════════════════════════════ */
/* Flip Animation */
/* ═══════════════════════════════════════════ */

.flip {
  animation: flip 0.6s ease;
}

@keyframes flip {
  0% {
    transform: perspective(400px) rotateY(0);
  }
  100% {
    transform: perspective(400px) rotateY(360deg);
  }
}

/* ═══════════════════════════════════════════ */
/* Glowing Effect */
/* ═══════════════════════════════════════════ */

.glow {
  animation: glow 2s ease-in-out infinite;
}

@keyframes glow {
  0%,
  100% {
    box-shadow: 0 0 5px rgba(59, 130, 246, 0.5);
  }
  50% {
    box-shadow: 0 0 20px rgba(59, 130, 246, 1), 0 0 30px rgba(59, 130, 246, 0.8);
  }
}
```

---

### JavaScript Animation Patterns 🔧

```javascript
// ═══════════════════════════════════════════
// Stagger Animation Helper
// ═══════════════════════════════════════════

function staggerAnimation(elements, animationFn, delay = 100) {
  elements.forEach((element, index) => {
    setTimeout(() => {
      animationFn(element);
    }, index * delay);
  });
}

// Usage
staggerAnimation(
  document.querySelectorAll(".card"),
  (el) => el.classList.add("fade-in"),
  100
);

// ═══════════════════════════════════════════
// Scroll Progress Indicator
// ═══════════════════════════════════════════

function updateScrollProgress() {
  const windowHeight = window.innerHeight;
  const documentHeight = document.documentElement.scrollHeight - windowHeight;
  const scrolled = window.scrollY;
  const progress = (scrolled / documentHeight) * 100;

  document.getElementById("progress-bar").style.width = progress + "%";
}

window.addEventListener("scroll", updateScrollProgress);

// ═══════════════════════════════════════════
// Parallax Effect
// ═══════════════════════════════════════════

function parallaxEffect() {
  const parallaxElements = document.querySelectorAll(".parallax");
  const scrolled = window.pageYOffset;

  parallaxElements.forEach((element) => {
    const speed = element.dataset.speed || 0.5;
    const yPos = -(scrolled * speed);
    element.style.transform = `translateY(${yPos}px)`;
  });
}

window.addEventListener("scroll", parallaxEffect);

// ═══════════════════════════════════════════
// Number Counter Animation
// ═══════════════════════════════════════════

function animateCounter(element, target, duration = 2000) {
  const start = 0;
  const increment = target / (duration / 16); // 60fps
  let current = start;

  const timer = setInterval(() => {
    current += increment;
    if (current >= target) {
      current = target;
      clearInterval(timer);
    }
    element.textContent = Math.floor(current);
  }, 16);
}

// Usage
animateCounter(document.getElementById("counter"), 1000);

// ═══════════════════════════════════════════
// Smooth Scroll to Element
// ═══════════════════════════════════════════

function smoothScrollTo(target, duration = 800) {
  const targetElement = document.querySelector(target);
  const targetPosition = targetElement.offsetTop;
  const startPosition = window.pageYOffset;
  const distance = targetPosition - startPosition;
  let startTime = null;

  function animation(currentTime) {
    if (startTime === null) startTime = currentTime;
    const timeElapsed = currentTime - startTime;
    const run = ease(timeElapsed, startPosition, distance, duration);
    window.scrollTo(0, run);
    if (timeElapsed < duration) requestAnimationFrame(animation);
  }

  function ease(t, b, c, d) {
    t /= d / 2;
    if (t < 1) return (c / 2) * t * t + b;
    t--;
    return (-c / 2) * (t * (t - 2) - 1) + b;
  }

  requestAnimationFrame(animation);
}

// ═══════════════════════════════════════════
// Mouse Follow Effect
// ═══════════════════════════════════════════

function createMouseFollower() {
  const follower = document.querySelector(".mouse-follower");
  let mouseX = 0,
    mouseY = 0;
  let followerX = 0,
    followerY = 0;

  document.addEventListener("mousemove", (e) => {
    mouseX = e.clientX;
    mouseY = e.clientY;
  });

  function animate() {
    // Smooth follow with easing
    followerX += (mouseX - followerX) * 0.1;
    followerY += (mouseY - followerY) * 0.1;

    follower.style.left = followerX + "px";
    follower.style.top = followerY + "px";

    requestAnimationFrame(animate);
  }

  animate();
}
```

> **💡 Pro Tip:** Keep a library of reusable animation patterns. Don't reinvent the wheel - build on proven patterns and customize them for your needs!

---

<div align="center">

## 💡 Tips & Resources

</div>

### Easing Functions 📊

```javascript
// ═══════════════════════════════════════════
// Common Easing Functions
// ═══════════════════════════════════════════

const easings = {
  // Linear
  linear: "linear",

  // Ease
  ease: "ease",
  easeIn: "ease-in",
  easeOut: "ease-out",
  easeInOut: "ease-in-out",

  // Cubic Bezier (Custom)
  smooth: "cubic-bezier(0.25, 0.46, 0.45, 0.94)",
  swift: "cubic-bezier(0.55, 0, 0.1, 1)",
  bounce: "cubic-bezier(0.68, -0.55, 0.265, 1.55)",
  elastic: "cubic-bezier(0.175, 0.885, 0.32, 1.275)",

  // Material Design
  standard: "cubic-bezier(0.4, 0, 0.2, 1)",
  deceleration: "cubic-bezier(0, 0, 0.2, 1)",
  acceleration: "cubic-bezier(0.4, 0, 1, 1)",
  sharp: "cubic-bezier(0.4, 0, 0.6, 1)",

  // iOS
  iosStandard: "cubic-bezier(0.4, 0.01, 0.165, 0.99)",
  iosAcceleration: "cubic-bezier(0.755, 0.05, 0.855, 0.06)",
  iosDeceleration: "cubic-bezier(0.23, 1, 0.32, 1)",
};
```

**📊 Easing Resources:**

- Cubic Bezier Generator: https://cubic-bezier.com
- Easings.net: https://easings.net
- Ceaser CSS Easing: https://matthewlein.com/tools/ceaser

---

### Animation Timing Guidelines ⏱️

```
🎯 UI Feedback
   - Button press: 50-100ms
   - Checkbox/Toggle: 100-150ms
   - Tooltip: 150-200ms

🎯 Small Transitions
   - Fade in/out: 150-300ms
   - Scale/Rotate: 200-300ms
   - Slide: 250-350ms

🎯 Medium Transitions
   - Modal open/close: 300-500ms
   - Drawer slide: 350-450ms
   - Page transition: 400-600ms

🎯 Large Transitions
   - Loading states: 500ms+
   - Complex sequences: 1000ms+

⚡ General Rules:
   - Mobile: 20-30% faster
   - Desktop: Standard timing
   - Accessibility: Respect prefers-reduced-motion
```

---

### Best Practices Checklist ✅

```
Performance:
  ✓ Use transform and opacity (GPU-accelerated)
  ✓ Avoid animating width, height, left, right, top, bottom
  ✓ Use will-change sparingly
  ✓ Remove will-change after animation
  ✓ Use requestAnimationFrame for JS animations
  ✓ Debounce scroll events
  ✓ Use Intersection Observer for scroll animations

Accessibility:
  ✓ Respect prefers-reduced-motion
  ✓ Provide alternative non-animated experience
  ✓ Don't rely solely on animation for important info
  ✓ Avoid flashing animations (seizure risk)
  ✓ Keep animations under 5 seconds
  ✓ Provide pause/stop controls for auto-playing animations

UX:
  ✓ Keep it subtle (less is more)
  ✓ Animation should enhance, not distract
  ✓ Match animation to brand personality
  ✓ Be consistent across the site
  ✓ Test on real devices
  ✓ Provide immediate feedback for interactions
  ✓ Don't block user interaction during animations

Code:
  ✓ Use CSS animations for simple effects
  ✓ Use JavaScript for complex sequences
  ✓ Keep animation logic separate from business logic
  ✓ Make animations reusable
  ✓ Document complex animations
  ✓ Version control animation values
```

---

### Inspiration & Learning 🌟

```
🎪 Showcase Sites
   - CodePen: https://codepen.io/trending
   - Codrops: https://tympanus.net/codrops
   - Awwwards: https://awwwards.com
   - UI Movement: https://uimovement.com
   - LottieFiles: https://lottiefiles.com
   - Dribbble: https://dribbble.com/tags/animation

📚 Learning Resources
   - CSS Animations Guide: MDN Web Docs
   - Animation Handbook: Joshwcomeau.com
   - GSAP Learning: GreenSock.com/learning
   - JavaScript.info Animations
   - Web.dev Animation Guide

🎥 YouTube Channels
   - Traversy Media
   - DesignCourse
   - Online Tutorials
   - Kevin Powell (CSS animations)
   - Fireship (quick tutorials)

📱 Tools
   - Lottie Creator
   - Rive
   - Spline (3D)
   - Theatre.js
   - Jitter Video
```

---

<div align="center">

## 🎬 Quick Start Guide

</div>

### Getting Started Checklist 🚀

```
1. Choose Your Stack:
   □ Pure CSS (Simple effects)
   □ GSAP (Complex animations)
   □ Framer Motion (React projects)
   □ Anime.js (Lightweight projects)
   □ Three.js (3D requirements)

2. Set Up Performance:
   □ Enable hardware acceleration
   □ Use transform & opacity
   □ Add will-change strategically
   □ Implement prefers-reduced-motion

3. Plan Your Animations:
   □ Define animation purpose
   □ Choose appropriate timing
   □ Select easing functions
   □ Plan stagger patterns

4. Implement:
   □ Start with CSS where possible
   □ Add JS for complex needs
   □ Test on multiple devices
   □ Optimize for performance

5. Polish:
   □ Fine-tune timing
   □ Adjust easings
   □ Add accessibility features
   □ Test with real users
```

---

<div align="center">

## 🏆 Summary

### _Animation Library Comparison_ 📊

</div>

| Library           | Size  | Best For           | Learning Curve | Performance |
| ----------------- | ----- | ------------------ | -------------- | ----------- |
| **GSAP**          | 58kb  | Complex animations | Medium         | ⭐⭐⭐⭐⭐  |
| **Framer Motion** | 38kb  | React apps         | Low            | ⭐⭐⭐⭐    |
| **Anime.js**      | 16kb  | SVG animations     | Low            | ⭐⭐⭐⭐    |
| **Motion One**    | 5kb   | Modern projects    | Low            | ⭐⭐⭐⭐⭐  |
| **React Spring**  | 26kb  | Physics-based      | Medium         | ⭐⭐⭐⭐    |
| **Auto Animate**  | 2.7kb | Simple transitions | Very Low       | ⭐⭐⭐⭐⭐  |
| **Animate.css**   | 4kb   | Quick prototypes   | Very Low       | ⭐⭐⭐⭐    |
| **Three.js**      | 588kb | 3D graphics        | High           | ⭐⭐⭐      |

---

<div align="center">

**Built with 🎭 by MrDib, for Animation Enthusiasts**

_"Animation is not just about making things move - it's about bringing interfaces to life and creating memorable experiences."_

**Happy Animating!** ✨

**If you found this helpful, give it a ⭐ star and share with fellow developers!**

</div>

---

### Contributing 🤝

Found a great animation library? Want to add examples? Contributions are welcome!

1. Fork the repository
2. Add your animation examples
3. Test on multiple devices
4. Submit a pull request

---

### License 📄

This guide is open source and available under the MIT License.

---

<div align="center">

**Stay smooth. Keep animating. Make the web delightful!** 🚀

🎭 **#Animations** 🎭 **#DevResourceVault** 🎭 **#MrDib** 🎭

### Remember

> _"Animation is like salt - a little enhances everything, too much ruins the dish."_

> _"The best animation is the one you don't notice."_

> _"Performance > Fancy effects"_

> _"Always respect prefers-reduced-motion"_

</div>

---

<div align="center">

**Now go forth and make the web move beautifully!** 🎨✨

</div>
