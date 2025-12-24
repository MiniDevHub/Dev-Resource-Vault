<div align="center">

# ⚡ Build Tools & Dev Servers - Complete Guide

### _Because `python -m http.server` is so 2015_ 🐍

![Build Tools](https://img.shields.io/badge/Build-Lightning%20Fast-yellow?style=for-the-badge)
![Dev Experience](https://img.shields.io/badge/DX-Awesome-green?style=for-the-badge)
![Updated](https://img.shields.io/badge/Updated-2025-blue?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [⚡ Modern Build Tools Overview](#-modern-build-tools-overview)
- [🔥 Vite - The Speed Demon](#-vite---the-speed-demon)
- [🚀 Bun - The New Kid](#-bun---the-new-kid)
- [📦 esbuild - Go Fast](#-esbuild---go-fast)
- [🎯 Turbopack - Rust Power](#-turbopack---rust-power)
- [🔄 Webpack - The OG](#-webpack---the-og)
- [🌊 Parcel - Zero Config](#-parcel---zero-config)
- [🔷 Rollup - Library Builder](#-rollup---library-builder)
- [🔄 Auto-Reload Tools](#-auto-reload-tools)
- [💪 Process Managers](#-process-managers)
- [🧹 Code Quality Tools](#-code-quality-tools)
- [📊 Tool Comparison](#-tool-comparison)
- [💡 Best Practices](#-best-practices)
- [🐛 Troubleshooting](#-troubleshooting)

---

<div align="center">

## ⚡ Modern Build Tools Overview

_The 2025 landscape_ 🗺️

</div>

### Why We Need Build Tools

```
═══════════════════════════════════════════════════════════
THE EVOLUTION OF WEB DEVELOPMENT
═══════════════════════════════════════════════════════════

2010: "Just use jQuery lol"
├── <script src="jquery.js"></script>
├── <script src="app.js"></script>
└── Ship it! ✨

2015: "Webpack is the future!"
├── webpack.config.js (500 lines)
├── babel.config.js
├── .babelrc
├── postcss.config.js
└── Wait 30 seconds to see changes... ⏳

2020: "VITE IS HERE!"
├── npm create vite
├── Changes appear instantly ⚡
└── Builds in seconds, not minutes

2025: "Choose your fighter!"
├── Vite (most popular, proven)
├── Bun (fastest, all-in-one)
├── Turbopack (Next.js optimized)
├── esbuild (raw speed)
└── Webpack (still alive, still slow)

═══════════════════════════════════════════════════════════

WHAT BUILD TOOLS DO:

📦 BUNDLING:
• Combine multiple files into fewer bundles
• Optimize for production
• Tree shake unused code

🔄 TRANSPILING:
• TypeScript → JavaScript
• Modern JS → Older JS (for browser support)
• JSX → JavaScript

⚡ DEV SERVER:
• Hot Module Replacement (HMR)
• Fast refresh
• Live reload

🎨 ASSET PROCESSING:
• CSS preprocessing (Sass, Less)
• Image optimization
• Font loading

🔧 OPTIMIZATION:
• Minification
• Code splitting
• Lazy loading
• Compression
```

---

<div align="center">

## 🔥 Vite - The Speed Demon

**The most popular modern build tool**

</div>

```
🌐 Website → https://vitejs.dev
⭐ GitHub → https://github.com/vitejs/vite
📦 npm → npm create vite@latest
🎯 Best For → Modern SPAs, any framework
⚡ Speed → Instant server start, <50ms HMR
🏆 Status → Industry standard (2025)
```

### 🚀 Quick Start

```bash
# ═══════════════════════════════════════════
# CREATE NEW PROJECT (2025)
# ═══════════════════════════════════════════

# Interactive setup (recommended)
npm create vite@latest my-app

# With specific template
npm create vite@latest my-app -- --template react
npm create vite@latest my-app -- --template react-ts
npm create vite@latest my-app -- --template vue
npm create vite@latest my-app -- --template vue-ts
npm create vite@latest my-app -- --template svelte
npm create vite@latest my-app -- --template vanilla

# Using pnpm (faster!)
pnpm create vite my-app

# Using bun (FASTEST!)
bun create vite my-app

# ═══════════════════════════════════════════
# BASIC COMMANDS
# ═══════════════════════════════════════════

# Install dependencies
npm install

# Start dev server
npm run dev
# Server running at http://localhost:5173
# ⚡ Ready in ~200ms

# Build for production
npm run build

# Preview production build
npm run preview

# ═══════════════════════════════════════════
# WHY VITE IS AWESOME (2025)
# ═══════════════════════════════════════════

⚡ INSTANT SERVER START:
• No bundling in development
• Native ES modules
• Starts in ~200ms

🔥 BLAZING FAST HMR:
• Updates in <50ms
• Precise hot updates
• No full page reload

📦 OPTIMIZED BUILDS:
• Rollup under the hood
• Automatic code splitting
• CSS code splitting
• Asset optimization

🛠️ RICH FEATURES:
• TypeScript (no config!)
• JSX/TSX support
• CSS preprocessing (Sass, Less, Stylus)
• PostCSS
• Asset imports
• JSON imports
• WebAssembly
• Worker support

🔌 PLUGIN ECOSYSTEM:
• React, Vue, Svelte plugins
• Legacy browser support
• PWA support
• Analyze bundle
• Compression
• And 1000+ more!
```

### ⚙️ Vite Configuration (2025 Master Setup)

```javascript
// ═══════════════════════════════════════════
// vite.config.js - MrDib's Ultimate Setup
// ═══════════════════════════════════════════

import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";
import { resolve } from "path";

export default defineConfig({
  // Plugins
  plugins: [
    react({
      // Enable Fast Refresh
      fastRefresh: true,
      // Babel config for React
      babel: {
        plugins: ["babel-plugin-macros"],
      },
    }),
  ],

  // Dev server config
  server: {
    port: 3000,
    host: true, // Listen on all addresses
    open: true, // Auto-open browser
    cors: true,

    // Proxy API requests
    proxy: {
      "/api": {
        target: "http://localhost:8000",
        changeOrigin: true,
        rewrite: (path) => path.replace(/^\/api/, ""),
      },
    },

    // HMR config
    hmr: {
      overlay: true, // Show errors in browser
    },
  },

  // Build config
  build: {
    outDir: "dist",
    sourcemap: true, // Generate sourcemaps

    // Rollup options
    rollupOptions: {
      input: {
        main: resolve(__dirname, "index.html"),
        // Add more entry points if needed
      },
      output: {
        // Manual chunk splitting for better caching
        manualChunks: {
          vendor: ["react", "react-dom"],
          utils: ["lodash", "axios"],
        },
      },
    },

    // Advanced build options
    minify: "terser",
    terserOptions: {
      compress: {
        drop_console: true, // Remove console.log in production
        drop_debugger: true,
      },
    },

    // Chunk size warnings
    chunkSizeWarningLimit: 1000,

    // Asset handling
    assetsInlineLimit: 4096, // 4kb - inline as base64 if smaller
  },

  // Path resolution
  resolve: {
    alias: {
      "@": resolve(__dirname, "src"),
      "@components": resolve(__dirname, "src/components"),
      "@utils": resolve(__dirname, "src/utils"),
      "@styles": resolve(__dirname, "src/styles"),
      "@assets": resolve(__dirname, "src/assets"),
    },
  },

  // CSS config
  css: {
    devSourcemap: true,
    preprocessorOptions: {
      scss: {
        additionalData: `@import "@/styles/variables.scss";`,
      },
    },
    modules: {
      localsConvention: "camelCase",
    },
  },

  // Optimization
  optimizeDeps: {
    include: ["react", "react-dom"],
    exclude: ["@vite/client", "@vite/env"],
  },

  // Environment variables
  envPrefix: "VITE_", // Expose vars starting with VITE_

  // Preview server (for production build)
  preview: {
    port: 4173,
    host: true,
    open: true,
  },
});
```

### 🔌 Essential Vite Plugins (2025)

```bash
# ═══════════════════════════════════════════
# MUST-HAVE PLUGINS
# ═══════════════════════════════════════════

# React with Fast Refresh
npm install -D @vitejs/plugin-react

# Vue 3
npm install -D @vitejs/plugin-vue

# Svelte
npm install -D @sveltejs/vite-plugin-svelte

# Legacy browser support (IE11, etc.)
npm install -D @vitejs/plugin-legacy

# PWA support
npm install -D vite-plugin-pwa

# Bundle analyzer
npm install -D rollup-plugin-visualizer

# Compression (gzip/brotli)
npm install -D vite-plugin-compression

# Environment variables validation
npm install -D vite-plugin-env-compatible

# SVG as React components
npm install -D vite-plugin-svgr

# Image optimization
npm install -D vite-plugin-imagemin
```

```javascript
// ═══════════════════════════════════════════
// vite.config.js - With Plugins
// ═══════════════════════════════════════════

import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";
import legacy from "@vitejs/plugin-legacy";
import { VitePWA } from "vite-plugin-pwa";
import { visualizer } from "rollup-plugin-visualizer";
import compression from "vite-plugin-compression";
import svgr from "vite-plugin-svgr";

export default defineConfig({
  plugins: [
    react(),

    // Legacy browser support
    legacy({
      targets: ["defaults", "not IE 11"],
    }),

    // PWA
    VitePWA({
      registerType: "autoUpdate",
      manifest: {
        name: "My Awesome App",
        short_name: "MyApp",
        theme_color: "#ffffff",
        icons: [
          {
            src: "icon-192.png",
            sizes: "192x192",
            type: "image/png",
          },
        ],
      },
    }),

    // Bundle analyzer (only in analyze mode)
    visualizer({
      open: true,
      gzipSize: true,
      brotliSize: true,
      filename: "./dist/stats.html",
    }),

    // Compression
    compression({
      algorithm: "brotliCompress",
      ext: ".br",
    }),

    // SVG as components
    svgr(),
  ],
});

// Run with: ANALYZE=true npm run build
```

### 💡 Vite Pro Tips (2025)

```javascript
// ═══════════════════════════════════════════
// PERFORMANCE OPTIMIZATION
// ═══════════════════════════════════════════

// 1. Use dynamic imports for code splitting
const HeavyComponent = lazy(() => import('./HeavyComponent'));

// 2. Optimize dependencies
// vite.config.js
export default defineConfig({
  optimizeDeps: {
    // Include deps that are CJS or have issues
    include: ['lodash-es', 'date-fns'],
    // Exclude large deps not needed in dev
    exclude: ['@vite/client']
  }
});

// 3. Use import.meta.glob for dynamic imports
const modules = import.meta.glob('./modules/*.js');
// Or eager load
const modules = import.meta.glob('./modules/*.js', { eager: true });

// 4. Environment variables (2025 best practice)
// .env
VITE_API_URL=https://api.example.com
VITE_APP_TITLE=My App

// Access in code
console.log(import.meta.env.VITE_API_URL);

// 5. Asset handling
import imgUrl from './img.png'; // URL string
import imgRaw from './img.png?raw'; // File content
import imgUrl2x from './img.png?w=200'; // Resized (with plugin)

// 6. Worker support
import MyWorker from './worker?worker';
const worker = new MyWorker();

// ═══════════════════════════════════════════
// DEBUGGING TIPS
// ═══════════════════════════════════════════

// Enable debug logs
DEBUG=vite:* npm run dev

// Check what Vite is bundling
npm run build -- --debug

// Profile build performance
npm run build -- --profile

// ═══════════════════════════════════════════
// MIGRATION FROM WEBPACK/CRA
// ═══════════════════════════════════════════

// 1. Replace webpack imports
// ❌ Old (Webpack)
const context = require.context('./components', true, /\.js$/);

// ✅ New (Vite)
const modules = import.meta.glob('./components/**/*.js');

// 2. Replace environment variables
// ❌ Old
process.env.REACT_APP_API_URL

// ✅ New
import.meta.env.VITE_API_URL

// 3. Update package.json
// ❌ Old
"start": "react-scripts start"

// ✅ New
"dev": "vite"
"build": "vite build"
"preview": "vite preview"
```

---

<div align="center">

## 🚀 Bun - The New Kid

**All-in-one JavaScript runtime & toolkit**

</div>

```
🌐 Website → https://bun.sh
⭐ GitHub → https://github.com/oven-sh/bun
📦 Install → curl -fsSL https://bun.sh/install | bash
🎯 Best For → Everything! Runtime + bundler + package manager
⚡ Speed → 4x faster than Node.js, instant bundling
🆕 Status → Production-ready (2025), gaining traction fast
```

### 🚀 Quick Start

```bash
# ═══════════════════════════════════════════
# INSTALL BUN (2025)
# ═══════════════════════════════════════════

# macOS/Linux
curl -fsSL https://bun.sh/install | bash

# Windows (WSL)
powershell -c "irm bun.sh/install.ps1|iex"

# Verify installation
bun --version

# ═══════════════════════════════════════════
# BUN AS RUNTIME (REPLACES NODE.JS!)
# ═══════════════════════════════════════════

# Run JavaScript/TypeScript
bun index.ts  # Yes, TypeScript directly!
bun run index.js

# REPL
bun

# Watch mode (auto-restart)
bun --watch index.ts

# ═══════════════════════════════════════════
# BUN AS PACKAGE MANAGER (REPLACES NPM!)
# ═══════════════════════════════════════════

# Install dependencies (FAST!)
bun install  # ~10x faster than npm

# Add packages
bun add react
bun add -D typescript

# Remove packages
bun remove react

# Update packages
bun update

# ═══════════════════════════════════════════
# BUN AS BUNDLER (REPLACES VITE/WEBPACK!)
# ═══════════════════════════════════════════

# Bundle for production
bun build ./index.ts --outdir ./dist

# With minification
bun build ./index.ts --outdir ./dist --minify

# Bundle for browser
bun build ./index.tsx --outdir ./dist --target browser

# ═══════════════════════════════════════════
# CREATE NEW PROJECT WITH BUN
# ═══════════════════════════════════════════

# React app
bun create react my-app
cd my-app
bun install
bun dev

# Next.js app
bun create next-app my-app

# Vite app (with Bun!)
bun create vite my-app
```

### ⚙️ Bun Configuration

```typescript
// ═══════════════════════════════════════════
// bunfig.toml - Bun Configuration
// ═══════════════════════════════════════════

# Install behavior
[install]
# Use exact versions
exact = true

# Caching
cache = true

# Registry
registry = "https://registry.npmjs.org"

# Lockfile
frozenLockfile = false

# Auto-install peers
auto = true

# Development dependencies
dev = true

# Production
production = false

[test]
# Test coverage
coverage = true

# Coverage threshold
coverageThreshold = 0.8

# ═══════════════════════════════════════════
# package.json - Bun Scripts
// ═══════════════════════════════════════════

{
  "name": "my-bun-app",
  "scripts": {
    "dev": "bun --watch index.ts",
    "build": "bun build ./index.ts --outdir ./dist --minify",
    "start": "bun index.ts",
    "test": "bun test"
  },
  "dependencies": {
    "react": "^18.2.0"
  },
  "devDependencies": {
    "@types/react": "^18.2.0",
    "bun-types": "latest"
  }
}
```

### 💡 Bun Features (2025)

```typescript
// ═══════════════════════════════════════════
// BUN BUILT-IN APIs
// ═══════════════════════════════════════════

// HTTP Server (built-in, FAST!)
Bun.serve({
  port: 3000,
  fetch(req) {
    return new Response('Hello from Bun!');
  }
});

// File I/O (optimized)
const file = Bun.file('package.json');
const text = await file.text();
const json = await file.json();

// Write file
await Bun.write('output.txt', 'Hello World');

// Environment variables
const apiKey = Bun.env.API_KEY;

// Hashing (built-in!)
const hash = Bun.hash('some-data');

// Password hashing
const hashed = await Bun.password.hash('mypassword');
const isValid = await Bun.password.verify('mypassword', hashed);

// SQLite (built-in!)
import { Database } from 'bun:sqlite';

const db = new Database('mydb.sqlite');
db.run('CREATE TABLE users (id INTEGER PRIMARY KEY, name TEXT)');
db.run('INSERT INTO users (name) VALUES (?)', ['MrDib']);

// Testing (built-in!)
import { test, expect } from 'bun:test';

test('2 + 2', () => {
  expect(2 + 2).toBe(4);
});

// ═══════════════════════════════════════════
// WHY BUN IS AWESOME (2025)
// ═══════════════════════════════════════════

⚡ SPEED:
• 4x faster than Node.js
• 20x faster npm install
• Instant bundling
• Native TypeScript support

🔋 BATTERIES INCLUDED:
• No need for: ts-node, nodemon, jest, dotenv
• Built-in: HTTP server, SQLite, testing, bundler
• Everything you need in one tool

💪 COMPATIBILITY:
• Drop-in replacement for Node.js
• Works with npm packages
• Supports Node APIs
• ES modules and CommonJS

🎯 MODERN:
• TypeScript first-class
• JSX/TSX support
• Top-level await
• Import maps

⚠️ CAVEATS (2025):
• Still maturing (v1.0 in 2024)
• Some npm packages have issues
• Smaller ecosystem than Node.js
• Not all Node APIs implemented yet
```

---

<div align="center">

## 📦 esbuild - Go Fast

**The fastest bundler (written in Go)**

</div>

```
🌐 Website → https://esbuild.github.io
⭐ GitHub → https://github.com/evanw/esbuild
📦 npm → npm install -D esbuild
🎯 Best For → Libraries, fast builds, CI/CD
⚡ Speed → 100x faster than Webpack
```

### 🚀 Quick Start

```bash
# ═══════════════════════════════════════════
# INSTALL & USE
# ═══════════════════════════════════════════

# Install
npm install -D esbuild

# Bundle file
npx esbuild app.js --bundle --outfile=out.js

# Watch mode
npx esbuild app.js --bundle --outfile=out.js --watch

# Minify
npx esbuild app.js --bundle --minify --outfile=out.js

# With sourcemap
npx esbuild app.js --bundle --sourcemap --outfile=out.js

# For browser
npx esbuild app.jsx --bundle --outfile=out.js --loader:.js=jsx
```

### ⚙️ esbuild Configuration

```javascript
// ═══════════════════════════════════════════
// build.js - esbuild Configuration
// ═══════════════════════════════════════════

const esbuild = require("esbuild");

esbuild
  .build({
    entryPoints: ["src/index.tsx"],
    bundle: true,
    minify: true,
    sourcemap: true,
    target: ["es2020"],
    outfile: "dist/bundle.js",

    // External dependencies (don't bundle)
    external: ["react", "react-dom"],

    // Loaders
    loader: {
      ".png": "file",
      ".svg": "dataurl",
    },

    // Define environment variables
    define: {
      "process.env.NODE_ENV": '"production"',
    },

    // Splitting
    splitting: true,
    format: "esm",

    // Watch mode
    watch: process.env.WATCH === "true",

    // Plugins
    plugins: [],
  })
  .catch(() => process.exit(1));

// Run: node build.js
// Watch: WATCH=true node build.js
```

---

<div align="center">

## 🎯 Turbopack - Rust Power

**Next.js's new bundler (Rust-based)**

</div>

```
🌐 Website → https://turbo.build/pack
⭐ GitHub → https://github.com/vercel/turbo
📦 Built into Next.js 13+
🎯 Best For → Next.js applications
⚡ Speed → 700x faster than Webpack (Vercel's claim)
🆕 Status → Beta (2025), improving fast
```

### 🚀 Usage

```bash
# ═══════════════════════════════════════════
# TURBOPACK (NEXT.JS 13+)
# ═══════════════════════════════════════════

# Create Next.js app
npx create-next-app@latest my-app

# Enable Turbopack in development
next dev --turbo

# Or in package.json
{
  "scripts": {
    "dev": "next dev --turbo"
  }
}

# Features (2025):
# ✅ Incremental computation
# ✅ Function-level caching
# ✅ Lazy bundling
# ✅ Faster HMR than Webpack
# ⚠️ Production builds still use Webpack (for now)
```

---

<div align="center">

## 🔄 Webpack - The OG

**Still alive in 2025!**

</div>

```
🌐 Website → https://webpack.js.org
⭐ GitHub → https://github.com/webpack/webpack
📦 npm → npm install -D webpack webpack-cli
🎯 Best For → Complex builds, legacy projects
⚡ Speed → Slower than modern tools, but very powerful
📈 Status → Mature, widely used, not going anywhere
```

### Why Webpack Still Matters (2025)

```bash
# ═══════════════════════════════════════════
# WHEN TO USE WEBPACK IN 2025
# ═══════════════════════════════════════════

✅ USE WEBPACK WHEN:
• Legacy codebase already using it
• Need very specific build customization
• Complex multi-entry point setups
• Module federation (micro-frontends)
• Enterprise projects with strict requirements

❌ DON'T USE WEBPACK FOR:
• New projects (use Vite/Bun)
• Simple SPAs
• Quick prototypes
• When dev speed matters
• When you value your sanity 🧠

⚠️ MIGRATION PATH:
• Webpack → Vite (recommended)
• Webpack → esbuild (for libraries)
• Webpack → Turbopack (for Next.js)
```

---

<div align="center">

## 🔄 Auto-Reload & File Watching

_Never manually restart again_ 🔄

</div>

### Nodemon - Node.js Babysitter 👶

```bash
# ═══════════════════════════════════════════
# NODEMON - CLASSIC CHOICE
# ═══════════════════════════════════════════

# Install
npm install -D nodemon

# Basic usage
npx nodemon server.js

# With TypeScript
npx nodemon --exec ts-node server.ts

# Watch specific files/folders
npx nodemon --watch src --ext js,ts,json server.js

# With environment variables
NODE_ENV=development nodemon server.js

# ═══════════════════════════════════════════
# package.json SCRIPTS
# ═══════════════════════════════════════════

{
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js",
    "dev:ts": "nodemon --exec ts-node src/server.ts",
    "dev:debug": "nodemon --inspect server.js"
  }
}
```

### Advanced Nodemon Config

```json
// ═══════════════════════════════════════════
// nodemon.json - Pro Configuration
// ═══════════════════════════════════════════

{
  "watch": ["src", "config", ".env"],
  "ext": "js,json,ts,tsx",
  "ignore": [
    "src/**/*.test.ts",
    "src/**/*.spec.ts",
    "node_modules/*",
    "dist/*",
    "*.log"
  ],
  "delay": "1000",
  "execMap": {
    "ts": "ts-node",
    "js": "node"
  },
  "env": {
    "NODE_ENV": "development",
    "DEBUG": "app:*"
  },
  "events": {
    "start": "clear && echo '🚀 Server starting...'",
    "restart": "echo '🔄 Server restarting due to file changes...'",
    "crash": "echo '💥 Server crashed! Waiting for changes...'"
  },
  "legacyWatch": false,
  "verbose": false
}
```

### Modern Alternatives to Nodemon (2025)

```bash
# ═══════════════════════════════════════════
# BUN WATCH (BUILT-IN!)
# ═══════════════════════════════════════════

# Just use --watch flag
bun --watch server.ts

# Faster, no config needed! ✨

# ═══════════════════════════════════════════
# NODE.JS NATIVE WATCH (NODE 18+)
# ═══════════════════════════════════════════

# Built into Node.js!
node --watch server.js

# No need for nodemon anymore! 🎉

# ═══════════════════════════════════════════
# TSX (MODERN TS-NODE)
# ═══════════════════════════════════════════

# Install
npm install -D tsx

# Watch mode
npx tsx watch server.ts

# Faster than ts-node, better errors!
```

---

<div align="center">

## 💪 Process Managers

_Keep your apps alive in production_ 🛡️

</div>

### PM2 - Production Process Manager

```bash
# ═══════════════════════════════════════════
# PM2 - THE BODYGUARD
# ═══════════════════════════════════════════

# Install globally
npm install -g pm2

# ═══════════════════════════════════════════
# BASIC COMMANDS
# ═══════════════════════════════════════════

# Start app
pm2 start app.js --name "my-api"

# Start with cluster mode (use all CPU cores!)
pm2 start app.js -i max

# Start TypeScript
pm2 start app.ts --interpreter=./node_modules/.bin/tsx

# List all processes
pm2 list
pm2 status

# Logs
pm2 logs                    # All logs
pm2 logs my-api             # Specific app
pm2 logs --lines 100        # Last 100 lines
pm2 logs --err              # Only errors

# Restart
pm2 restart my-api          # Restart with downtime
pm2 reload my-api           # Zero-downtime reload

# Stop
pm2 stop my-api
pm2 stop all

# Delete
pm2 delete my-api
pm2 delete all

# Monitoring
pm2 monit                   # Real-time monitoring (COOL!)
pm2 describe my-api         # Detailed info

# ═══════════════════════════════════════════
# SAVE & RESURRECT
# ═══════════════════════════════════════════

# Save current process list
pm2 save

# Auto-start on system boot
pm2 startup

# This will output a command to run, like:
# sudo env PATH=$PATH:/usr/bin pm2 startup systemd -u username --hp /home/username

# After reboot, restore saved processes
pm2 resurrect

# ═══════════════════════════════════════════
# ADVANCED FEATURES
# ═══════════════════════════════════════════

# Environment variables
pm2 start app.js --env production

# Max memory restart
pm2 start app.js --max-memory-restart 300M

# Cron restart (restart at specific time)
pm2 start app.js --cron-restart="0 0 * * *"

# Watch mode (auto-restart on file change)
pm2 start app.js --watch

# Interpreter
pm2 start app.py --interpreter python3
pm2 start app.ts --interpreter ./node_modules/.bin/bun
```

### PM2 Ecosystem File (2025 Best Practice)

```javascript
// ═══════════════════════════════════════════
// ecosystem.config.js - PM2 Configuration
// ═══════════════════════════════════════════

module.exports = {
  apps: [
    {
      name: "api",
      script: "./dist/server.js",

      // Cluster mode
      instances: "max",
      exec_mode: "cluster",

      // Auto restart
      watch: false,
      max_memory_restart: "500M",

      // Environment variables
      env: {
        NODE_ENV: "development",
        PORT: 3000,
      },
      env_production: {
        NODE_ENV: "production",
        PORT: 8080,
      },

      // Logs
      error_file: "./logs/err.log",
      out_file: "./logs/out.log",
      log_date_format: "YYYY-MM-DD HH:mm:ss Z",

      // Advanced
      merge_logs: true,
      autorestart: true,
      max_restarts: 10,
      min_uptime: "10s",
    },

    // Worker process
    {
      name: "worker",
      script: "./dist/worker.js",
      instances: 2,
      exec_mode: "cluster",
      cron_restart: "0 0 * * *", // Restart daily at midnight
      env_production: {
        NODE_ENV: "production",
      },
    },
  ],
};

// Deploy: pm2 start ecosystem.config.js --env production
// Stop all: pm2 stop ecosystem.config.js
```

### PM2 Plus (Monitoring Dashboard)

```bash
# ═══════════════════════════════════════════
# PM2 PLUS - CLOUD MONITORING (2025)
# ═══════════════════════════════════════════

# Sign up at https://pm2.io

# Link your server
pm2 link <secret-key> <public-key>

# Now you get:
# ✅ Web dashboard
# ✅ Real-time monitoring
# ✅ Email/Slack alerts
# ✅ Custom metrics
# ✅ Transaction tracing
# ✅ Log streaming

# Free tier: 4 servers
# Paid: $19/month for more
```

---

<div align="center">

## 🧹 Code Quality Tools

_Keep your code clean_ ✨

</div>

### Biome - All-in-One (2025 Hot!)

```bash
# ═══════════════════════════════════════════
# BIOME - ESLINT + PRETTIER REPLACEMENT
# ═══════════════════════════════════════════

# Install
npm install -D @biomejs/biome

# Initialize
npx @biomejs/biome init

# Format
npx @biomejs/biome format --write .

# Lint
npx @biomejs/biome lint --apply .

# Check (format + lint)
npx @biomejs/biome check --apply .

# ═══════════════════════════════════════════
# WHY BIOME? (2025)
# ═══════════════════════════════════════════

✅ UNIFIED TOOL:
• Replaces ESLint + Prettier
• Single config file
• Faster than both combined

⚡ BLAZING FAST:
• Written in Rust
• 35x faster than ESLint
• 25x faster than Prettier

🔧 FEATURES:
• Formatting (like Prettier)
• Linting (like ESLint)
• Import sorting
• TypeScript support
• JSON/JSONC support

📦 SIMPLE:
• One dependency instead of dozens
• No plugin hell
• Works out of the box
```

### Biome Configuration

```json
// ═══════════════════════════════════════════
// biome.json - Biome Configuration
// ═══════════════════════════════════════════

{
  "$schema": "https://biomejs.dev/schemas/1.4.1/schema.json",
  "organizeImports": {
    "enabled": true
  },
  "linter": {
    "enabled": true,
    "rules": {
      "recommended": true,
      "suspicious": {
        "noExplicitAny": "error"
      },
      "complexity": {
        "noForEach": "warn"
      }
    }
  },
  "formatter": {
    "enabled": true,
    "formatWithErrors": false,
    "indentStyle": "space",
    "indentWidth": 2,
    "lineWidth": 100,
    "ignore": ["node_modules", "dist", "build"]
  },
  "javascript": {
    "formatter": {
      "quoteStyle": "single",
      "trailingComma": "es5",
      "semicolons": "always",
      "arrowParentheses": "always"
    }
  },
  "json": {
    "parser": {
      "allowComments": true
    },
    "formatter": {
      "indentWidth": 2
    }
  }
}
```

---

<div align="center">

## 📊 Tool Comparison

_Choose your fighter_ ⚔️

</div>

### Build Tool Comparison (2025)

```
═══════════════════════════════════════════════════════════
BUILD TOOL COMPARISON (2025 EDITION)
═══════════════════════════════════════════════════════════

┌──────────┬────────┬──────────┬──────────┬────────┬────────┐
│ Tool     │ Speed  │ DX       │ Maturity │ Use    │ Rating │
├──────────┼────────┼──────────┼──────────┼────────┼────────┤
│ Vite     │ ⚡⚡⚡⚡  │ ⭐⭐⭐⭐⭐   │ Mature   │ SPAs   │ 10/10  │
│ Bun      │ ⚡⚡⚡⚡⚡ │ ⭐⭐⭐⭐    │ New      │ All    │ 9/10   │
│ esbuild  │ ⚡⚡⚡⚡⚡ │ ⭐⭐⭐     │ Mature   │ Libs   │ 8/10   │
│ Turbopack│ ⚡⚡⚡⚡⚡ │ ⭐⭐⭐⭐    │ Beta     │ Next   │ 8/10   │
│ Webpack  │ ⚡      │ ⭐⭐      │ Very old │ Legacy │ 6/10   │
│ Parcel   │ ⚡⚡⚡   │ ⭐⭐⭐⭐    │ Mature   │ Simple │ 7/10   │
│ Rollup   │ ⚡⚡⚡   │ ⭐⭐⭐     │ Mature   │ Libs   │ 8/10   │
└──────────┴────────┴──────────┴──────────┴────────┴────────┘

DETAILED BREAKDOWN:

┌──────────┬───────────┬─────────────┬──────────────────┐
│ Tool     │ Dev Start │ HMR         │ Prod Build       │
├──────────┼───────────┼─────────────┼──────────────────┤
│ Vite     │ ~200ms    │ <50ms       │ 10-30s           │
│ Bun      │ ~100ms    │ <30ms       │ 5-15s            │
│ esbuild  │ N/A       │ N/A         │ 2-5s             │
│ Turbopack│ ~300ms    │ <100ms      │ N/A (uses webpack│
│ Webpack  │ 30-60s    │ 500ms-2s    │ 60-180s          │
└──────────┴───────────┴─────────────┴──────────────────┘

FEATURES COMPARISON:

┌──────────┬────┬────┬───┬─────┬────────┬────────┐
│ Feature  │Vite│Bun │esb│Turbo│Webpack │Parcel  │
├──────────┼────┼────┼───┼─────┼────────┼────────┤
│ HMR      │ ✅ │ ✅ │ ❌│ ✅  │ ✅     │ ✅     │
│ TypeScript│✅ │ ✅ │ ✅│ ✅  │ ✅     │ ✅     │
│ JSX/TSX  │ ✅ │ ✅ │ ✅│ ✅  │ ✅     │ ✅     │
│ CSS Proc │ ✅ │ ✅ │ ⚠️ │ ✅  │ ✅     │ ✅     │
│ Code Split│✅ │ ✅ │ ✅│ ✅  │ ✅     │ ✅     │
│ Tree Shake│✅ │ ✅ │ ✅│ ✅  │ ✅     │ ✅     │
│ Plugins  │ ✅ │ ⚠️ │ ⚠️ │ ⚠️  │ ✅     │ ✅     │
│ Zero Config│✅│ ✅ │ ❌│ ✅  │ ❌     │ ✅     │
└──────────┴────┴────┴───┴─────┴────────┴────────┘

RECOMMENDATIONS BY PROJECT TYPE:

🎯 NEW SPA (React/Vue/Svelte):
   → Vite (proven, mature, best DX)

🚀 NEXT.JS APP:
   → Turbopack (built-in, optimized)

📚 LIBRARY/PACKAGE:
   → Rollup or esbuild (best tree shaking)

⚡ NEED ABSOLUTE SPEED:
   → Bun (fastest everything)

🧪 QUICK PROTOTYPE:
   → Vite or Parcel (zero config)

🏢 LEGACY/ENTERPRISE:
   → Webpack (if already using it)
   → Otherwise: Migrate to Vite!

💻 FULL-STACK JS:
   → Bun (runtime + bundler + package manager)
```

---

<div align="center">

## 💡 Best Practices

_Build better, faster_ ⚡

</div>

### 2025 Best Practices

```bash
# ═══════════════════════════════════════════
# PROJECT SETUP
# ═══════════════════════════════════════════

✅ USE MODERN TOOLS:
• Vite or Bun (not Webpack!)
• TypeScript (not JavaScript)
• pnpm or bun (not npm)
• Biome (not ESLint + Prettier)

✅ PACKAGE.JSON SCRIPTS:
{
  "scripts": {
    "dev": "vite",              # Development
    "build": "vite build",      # Production build
    "preview": "vite preview",  # Preview production build
    "lint": "biome check .",    # Lint & format
    "test": "vitest",           # Testing
    "type-check": "tsc --noEmit" # TypeScript check
  }
}

# ═══════════════════════════════════════════
# PERFORMANCE OPTIMIZATION
# ═══════════════════════════════════════════

✅ CODE SPLITTING:
• Use dynamic imports
• Lazy load routes
• Lazy load heavy components

✅ BUNDLE OPTIMIZATION:
• Enable minification
• Enable tree shaking
• Remove console.logs in production
• Use compression (gzip/brotli)

✅ CACHING:
• Use content hashing in filenames
• Set proper cache headers
• Leverage browser caching

# ═══════════════════════════════════════════
# DEVELOPMENT WORKFLOW
# ═══════════════════════════════════════════

✅ GIT HOOKS:
# Install husky
npm install -D husky

# Setup
npx husky init

# Pre-commit hook (.husky/pre-commit)
#!/bin/sh
npm run lint
npm run type-check

# Pre-push hook (.husky/pre-push)
#!/bin/sh
npm test

✅ CI/CD:
# GitHub Actions example
name: CI
on: [push]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: oven-sh/setup-bun@v1
      - run: bun install
      - run: bun test
      - run: bun run build

# ═══════════════════════════════════════════
# ENVIRONMENT MANAGEMENT
# ═══════════════════════════════════════════

✅ ENVIRONMENT FILES:
.env                 # Local development (gitignored)
.env.example         # Template (committed)
.env.production      # Production (never commit!)
.env.test            # Testing

✅ VARIABLE NAMING:
# Vite
VITE_API_URL=https://api.example.com

# Next.js (public)
NEXT_PUBLIC_API_URL=https://api.example.com

# Next.js (private)
DATABASE_URL=postgres://...

# ═══════════════════════════════════════════
# MONITORING & DEBUGGING
# ═══════════════════════════════════════════

✅ PRODUCTION MONITORING:
• PM2 for process management
• PM2 Plus for monitoring
• Sentry for error tracking
• DataDog/NewRelic for APM

✅ BUILD ANALYSIS:
# Analyze bundle size
npm run build -- --analyze

# Check what's in your bundle
npx vite-bundle-visualizer

# Check dependencies
npx depcheck

# ═══════════════════════════════════════════
# SECURITY
# ═══════════════════════════════════════════

✅ DEPENDENCIES:
# Audit regularly
npm audit
bun audit

# Update dependencies
npx npm-check-updates -u
npm install

# Remove unused
npx depcheck

✅ SECRETS:
# Never commit secrets!
# Use environment variables
# Use secret management (Vault, AWS Secrets Manager)
# Rotate keys regularly
```

---

<div align="center">

## 🐛 Troubleshooting

_Common issues & solutions_ 🔧

</div>

### Common Problems (2025)

```bash
# ═══════════════════════════════════════════
# BUILD FAILURES
# ═══════════════════════════════════════════

# ❌ "Cannot find module"
✅ Solutions:
1. Check import paths (case-sensitive!)
2. Check file extensions
3. Clear node_modules: rm -rf node_modules && npm install
4. Check tsconfig.json paths
5. Restart dev server

# ❌ "Out of memory"
✅ Solutions:
# Increase Node memory
export NODE_OPTIONS="--max-old-space-size=4096"

# Or in package.json
"build": "NODE_OPTIONS='--max-old-space-size=4096' vite build"

# ❌ "Module externalized for browser compatibility"
✅ Solution (Vite):
// vite.config.js
export default {
  resolve: {
    alias: {
      // Add polyfills or mocks
      util: 'util/'
    }
  },
  optimizeDeps: {
    include: ['problem-package']
  }
}

# ═══════════════════════════════════════════
# DEV SERVER ISSUES
# ═══════════════════════════════════════════

# ❌ "Port already in use"
✅ Solutions:
# Kill process on port
# macOS/Linux:
lsof -ti:3000 | xargs kill -9

# Windows:
netstat -ano | findstr :3000
taskkill /PID <PID> /F

# Or change port
vite --port 3001

# ❌ "Changes not reflecting"
✅ Solutions:
1. Check if file is being watched
2. Clear browser cache (Cmd+Shift+R)
3. Clear build cache: rm -rf node_modules/.vite
4. Restart dev server

# ═══════════════════════════════════════════
# PERFORMANCE ISSUES
# ═══════════════════════════════════════════

# ❌ "Slow builds"
✅ Solutions:
1. Upgrade to latest tool version
2. Enable caching
3. Exclude unnecessary files from build
4. Use faster alternatives (Vite vs Webpack)
5. Check antivirus isn't scanning node_modules

# ❌ "Large bundle size"
✅ Solutions:
1. Analyze bundle: npm run build -- --analyze
2. Remove unused dependencies
3. Use dynamic imports
4. Enable tree shaking
5. Check for duplicate dependencies: npm dedupe

# ═══════════════════════════════════════════
# PM2 ISSUES
# ═══════════════════════════════════════════

# ❌ "App keeps restarting"
✅ Solutions:
1. Check logs: pm2 logs
2. Check app isn't crashing on startup
3. Increase max_restarts in ecosystem file
4. Check memory usage: pm2 monit

# ❌ "Can't connect after pm2 save"
✅ Solution:
pm2 resurrect
# Or start from ecosystem file:
pm2 start ecosystem.config.js

# ═══════════════════════════════════════════
# DEBUGGING TIPS
# ═══════════════════════════════════════════

# Enable verbose logging
DEBUG=* npm run dev          # All debug logs
DEBUG=vite:* npm run dev     # Vite logs only

# Check what's being bundled
npm run build -- --debug

# Profile build performance
npm run build -- --profile

# Test production build locally
npm run build
npm run preview
```

---

<div align="center">

## 🎓 Additional Resources

_Learn more_ 📚

</div>

**Official Docs:**

- Vite: https://vitejs.dev
- Bun: https://bun.sh
- esbuild: https://esbuild.github.io
- Turbopack: https://turbo.build/pack
- PM2: https://pm2.keymetrics.io
- Biome: https://biomejs.dev

**Comparisons:**

- Bundlers Tooling: https://bundlers.tooling.report/
- Build Tool Benchmarks: https://github.com/privatenumber/minification-benchmarks

**Video Tutorials:**

- Fireship - Vite in 100 Seconds
- Traversy Media - Vite Crash Course
- Web Dev Simplified - Modern Build Tools

---

<div align="center">

## 🏆 MrDib's 2025 Recommendations

</div>

```yaml
# ═══════════════════════════════════════════
# THE ULTIMATE 2025 STACK
# ═══════════════════════════════════════════

🥇 FOR NEW PROJECTS:
Build Tool: Vite
Runtime: Bun (or Node.js 20+)
Package Manager: pnpm or bun
Linter/Formatter: Biome
Process Manager: PM2 (production)
Auto-reload: bun --watch or node --watch

Why: Proven, fast, great DX, mature ecosystem

🥈 FOR MAXIMUM SPEED:
Everything: Bun
Build: Bun
Runtime: Bun
Package Manager: Bun
Test: Bun

Why: One tool, insanely fast, modern

🥉 FOR NEXT.JS:
Build: Turbopack (--turbo flag)
Runtime: Node.js or Bun
Package Manager: pnpm
Process Manager: PM2

Why: Optimized for Next.js

📚 FOR LIBRARIES:
Build: Rollup or esbuild
Why: Best tree shaking, ES modules

🏢 FOR LEGACY:
Migrate from: Webpack
Migrate to: Vite
How: Gradually, test thoroughly

# ═══════════════════════════════════════════
# DECISION FLOWCHART
# ═══════════════════════════════════════════

┌──────────────────────────────────┐
│  What are you building?          │
└──────────────────────────────────┘
            │
            ├─→ New SPA? → Vite
            │
            ├─→ Next.js? → Turbopack
            │
            ├─→ Library? → Rollup/esbuild
            │
            ├─→ Want speed? → Bun (everything)
            │
            ├─→ Need maximum control? → Rollup
            │
            └─→ Legacy project? → Migrate to Vite!
```

---

<div align="center">

**Built with ⚡ by MrDib**

_"Life's too short for slow builds"_ 🚀

**Choose fast tools. Ship faster. Win.** 💪

**If this helped you, ⭐ star the repo!**

</div>

---

<div align="center">

### Remember

> _"The best build tool is the one that gets out of your way."_

> _"Fast feedback loops = happy developers."_

> _"Don't use Webpack in 2025 unless you absolutely have to."_

> _"Bun is the future, but Vite is the present."_

</div>
