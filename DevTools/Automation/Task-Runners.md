<div align="center">

# ⚙️ Task Runners & Build Tools

<img src="https://img.shields.io/badge/Task-Runners-orange?style=for-the-badge" alt="Task Runners">
<img src="https://img.shields.io/badge/Build-Tools-blue?style=for-the-badge" alt="Build Tools">
<img src="https://img.shields.io/badge/Automation-Efficient-green?style=for-the-badge" alt="Automation">

### _Streamline your development workflow with powerful task automation_ ⚡

**Because manual tasks are for the pre-automation era** 🚀

</div>

---

## 📚 Table of Contents

- [📦 NPM Scripts](#-npm-scripts)
- [🚀 Gulp.js](#-gulpjs)
- [🔨 Grunt.js](#-gruntjs)
- [🏗️ Make](#️-make)
- [⚡ Modern Build Tools](#-modern-build-tools)
- [🎯 Choosing the Right Tool](#-choosing-the-right-tool)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 📦 NPM Scripts

</div>

### The Simple & Powerful Built-in Solution 🎯

```json
// ═══════════════════════════════════════════
// package.json - Complete NPM Scripts Setup
// ═══════════════════════════════════════════

{
  "name": "my-awesome-project",
  "version": "1.0.0",
  "scripts": {
    // ═══════════════════════════════════════════
    // Development
    // ═══════════════════════════════════════════
    "dev": "vite",
    "dev:https": "vite --https",
    "dev:host": "vite --host",
    "dev:debug": "node --inspect node_modules/.bin/vite",
    "dev:open": "vite --open",
    "start": "npm run dev",

    // ═══════════════════════════════════════════
    // Building
    // ═══════════════════════════════════════════
    "build": "vite build",
    "build:dev": "vite build --mode development",
    "build:staging": "vite build --mode staging",
    "build:production": "vite build --mode production",
    "build:analyze": "vite build --mode analyze",
    "build:report": "vite build && vite-bundle-analyzer",
    "preview": "vite preview",

    // ═══════════════════════════════════════════
    // Testing
    // ═══════════════════════════════════════════
    "test": "vitest",
    "test:unit": "vitest run --coverage",
    "test:watch": "vitest watch",
    "test:ui": "vitest --ui",
    "test:e2e": "playwright test",
    "test:e2e:headed": "playwright test --headed",
    "test:e2e:debug": "playwright test --debug",
    "test:coverage": "vitest run --coverage && open coverage/index.html",
    "test:ci": "vitest run --coverage && playwright test",

    // ═══════════════════════════════════════════
    // Code Quality
    // ═══════════════════════════════════════════
    "lint": "eslint . --ext .js,.jsx,.ts,.tsx",
    "lint:fix": "eslint . --ext .js,.jsx,.ts,.tsx --fix",
    "lint:quiet": "eslint . --ext .js,.jsx,.ts,.tsx --quiet",
    "lint:staged": "lint-staged",

    "format": "prettier --write \"src/**/*.{js,jsx,ts,tsx,json,css,scss,md}\"",
    "format:check": "prettier --check \"src/**/*.{js,jsx,ts,tsx,json,css,scss,md}\"",

    "type-check": "tsc --noEmit",
    "type-check:watch": "tsc --noEmit --watch",

    "validate": "npm run lint && npm run type-check && npm run test:unit",

    // ═══════════════════════════════════════════
    // Git Hooks
    // ═══════════════════════════════════════════
    "prepare": "husky install",
    "pre-commit": "lint-staged",
    "pre-push": "npm run type-check && npm run test:unit",
    "commit": "cz",
    "commitlint": "commitlint --edit",

    // ═══════════════════════════════════════════
    // Database
    // ═══════════════════════════════════════════
    "db:generate": "prisma generate",
    "db:migrate": "prisma migrate dev",
    "db:migrate:deploy": "prisma migrate deploy",
    "db:push": "prisma db push",
    "db:seed": "prisma db seed",
    "db:studio": "prisma studio",
    "db:reset": "prisma migrate reset",

    // ═══════════════════════════════════════════
    // Docker
    // ═══════════════════════════════════════════
    "docker:build": "docker build -t myapp:latest .",
    "docker:run": "docker run -p 3000:3000 myapp:latest",
    "docker:up": "docker-compose up -d",
    "docker:down": "docker-compose down",
    "docker:logs": "docker-compose logs -f",
    "docker:clean": "docker system prune -af --volumes",

    // ═══════════════════════════════════════════
    // Deployment
    // ═══════════════════════════════════════════
    "deploy": "npm run build && npm run deploy:vercel",
    "deploy:vercel": "vercel --prod",
    "deploy:netlify": "netlify deploy --prod",
    "deploy:surge": "surge dist",
    "deploy:gh-pages": "gh-pages -d dist",

    // ═══════════════════════════════════════════
    // Utilities
    // ═══════════════════════════════════════════
    "clean": "rimraf node_modules dist build .next coverage",
    "clean:modules": "rimraf node_modules",
    "clean:dist": "rimraf dist build",
    "clean:cache": "rimraf node_modules/.cache .next/cache",

    "fresh": "npm run clean && npm install",
    "fresh:lock": "npm run clean && rm -f package-lock.json && npm install",

    "outdated": "npm outdated",
    "update": "npm update",
    "update:check": "npx npm-check-updates",
    "update:interactive": "npx npm-check-updates -i",
    "update:all": "npx npm-check-updates -u && npm install",

    // ═══════════════════════════════════════════
    // Documentation
    // ═══════════════════════════════════════════
    "docs": "typedoc --out docs src",
    "docs:serve": "npx serve docs",
    "storybook": "storybook dev -p 6006",
    "storybook:build": "storybook build",

    // ═══════════════════════════════════════════
    // Release Management
    // ═══════════════════════════════════════════
    "release": "standard-version",
    "release:minor": "standard-version --release-as minor",
    "release:major": "standard-version --release-as major",
    "release:patch": "standard-version --release-as patch",
    "release:dry": "standard-version --dry-run",

    "changelog": "conventional-changelog -p angular -i CHANGELOG.md -s",

    // ═══════════════════════════════════════════
    // CI/CD
    // ═══════════════════════════════════════════
    "ci": "npm run validate && npm run build",
    "ci:full": "npm ci && npm run validate && npm run build && npm run test:e2e",

    // ═══════════════════════════════════════════
    // Project Management
    // ═══════════════════════════════════════════
    "size": "size-limit",
    "analyze": "source-map-explorer 'dist/**/*.js'",
    "stats": "webpack-bundle-analyzer dist/stats.json",

    "license-check": "license-checker --summary",
    "security": "npm audit",
    "security:fix": "npm audit fix",

    // ═══════════════════════════════════════════
    // Utilities Scripts
    // ═══════════════════════════════════════════
    "create:component": "node scripts/create-component.js",
    "generate:types": "node scripts/generate-types.js",
    "backup": "node scripts/backup.js"
  },

  // ═══════════════════════════════════════════
  // NPM Script Hooks
  // ═══════════════════════════════════════════
  "scripts": {
    "preinstall": "node scripts/check-node-version.js",
    "postinstall": "npm run db:generate",
    "prebuild": "npm run clean:dist",
    "postbuild": "node scripts/post-build.js",
    "pretest": "node scripts/setup-test-env.js",
    "posttest": "node scripts/cleanup-test.js"
  }
}
```

---

### Advanced NPM Scripts Patterns 🎨

```json
// ═══════════════════════════════════════════
// Cross-platform Scripts
// ═══════════════════════════════════════════

{
  "scripts": {
    // Use cross-env for environment variables
    "build": "cross-env NODE_ENV=production webpack",

    // Use rimraf for cross-platform deletion
    "clean": "rimraf dist",

    // Use concurrently to run multiple commands
    "dev:all": "concurrently \"npm run dev\" \"npm run storybook\" \"npm run test:watch\"",

    // Use wait-on to wait for services
    "test:e2e": "wait-on http://localhost:3000 && playwright test",

    // Use npm-run-all for sequential/parallel execution
    "build:all": "npm-run-all clean build:*",
    "build:parallel": "npm-run-all --parallel build:css build:js build:html",

    // Use dotenv for loading environment variables
    "dev": "dotenv -e .env.local -- vite"
  }
}

// ═══════════════════════════════════════════
// Script Composition
// ═══════════════════════════════════════════

{
  "scripts": {
    // Break down complex scripts
    "build": "npm run build:clean && npm run build:compile && npm run build:optimize",
    "build:clean": "rimraf dist",
    "build:compile": "tsc && vite build",
    "build:optimize": "node scripts/optimize.js",

    // Reusable script patterns
    "test:unit:watch": "npm run test:unit -- --watch",
    "test:unit:coverage": "npm run test:unit -- --coverage"
  }
}

// ═══════════════════════════════════════════
// Passing Arguments
// ═══════════════════════════════════════════

{
  "scripts": {
    // Accept arguments with --
    "test": "vitest",
    // Usage: npm run test -- --coverage --watch

    "lint": "eslint .",
    // Usage: npm run lint -- --fix

    // Custom script with arguments
    "generate": "node scripts/generate.js"
    // Access with process.argv in Node.js
  }
}
```

---

### NPM Scripts with Node.js 🟢

```javascript
// ═══════════════════════════════════════════
// scripts/create-component.js
// Create React component boilerplate
// ═══════════════════════════════════════════

const fs = require("fs");
const path = require("path");

// Get component name from command line
const componentName = process.argv[2];

if (!componentName) {
  console.error("❌ Please provide a component name");
  process.exit(1);
}

// Create component directory
const componentDir = path.join(
  __dirname,
  "..",
  "src",
  "components",
  componentName
);

if (fs.existsSync(componentDir)) {
  console.error(`❌ Component ${componentName} already exists`);
  process.exit(1);
}

fs.mkdirSync(componentDir, { recursive: true });

// Component file
const componentContent = `import React from 'react';
import styles from './${componentName}.module.css';

interface ${componentName}Props {
  // Add your props here
}

export const ${componentName}: React.FC<${componentName}Props> = () => {
  return (
    <div className={styles.container}>
      <h1>${componentName}</h1>
    </div>
  );
};
`;

fs.writeFileSync(
  path.join(componentDir, `${componentName}.tsx`),
  componentContent
);

// CSS Module
const cssContent = `.container {
  /* Add your styles here */
}
`;

fs.writeFileSync(
  path.join(componentDir, `${componentName}.module.css`),
  cssContent
);

// Test file
const testContent = `import { render, screen } from '@testing-library/react';
import { ${componentName} } from './${componentName}';

describe('${componentName}', () => {
  it('renders correctly', () => {
    render(<${componentName} />);
    expect(screen.getByText('${componentName}')).toBeInTheDocument();
  });
});
`;

fs.writeFileSync(
  path.join(componentDir, `${componentName}.test.tsx`),
  testContent
);

// Index file
const indexContent = `export { ${componentName} } from './${componentName}';
`;

fs.writeFileSync(path.join(componentDir, "index.ts"), indexContent);

console.log(`✅ Component ${componentName} created successfully!`);
console.log(`📁 Location: ${componentDir}`);

// ═══════════════════════════════════════════
// scripts/check-node-version.js
// Ensure correct Node.js version
// ═══════════════════════════════════════════

const { engines } = require("../package.json");
const semver = require("semver");

const currentVersion = process.version;
const requiredVersion = engines.node;

if (!semver.satisfies(currentVersion, requiredVersion)) {
  console.error(`❌ Node.js version ${currentVersion} is not supported`);
  console.error(`   Required version: ${requiredVersion}`);
  console.error(`   Please use nvm or upgrade your Node.js installation`);
  process.exit(1);
}

console.log(`✅ Node.js version ${currentVersion} is compatible`);

// ═══════════════════════════════════════════
// scripts/post-build.js
// Post-build processing
// ═══════════════════════════════════════════

const fs = require("fs");
const path = require("path");
const { gzipSync } = require("zlib");

const distDir = path.join(__dirname, "..", "dist");

// Calculate bundle sizes
function getFileSize(filePath) {
  const stats = fs.statSync(filePath);
  const fileSizeInBytes = stats.size;
  const fileSizeInKB = (fileSizeInBytes / 1024).toFixed(2);
  return fileSizeInKB;
}

function getGzipSize(filePath) {
  const content = fs.readFileSync(filePath);
  const gzipped = gzipSync(content);
  return (gzipped.length / 1024).toFixed(2);
}

console.log("\n📊 Build Statistics\n");
console.log("File".padEnd(40), "Size".padEnd(12), "Gzipped");
console.log("-".repeat(70));

// Find all JS files
const files = fs
  .readdirSync(distDir, { recursive: true })
  .filter((file) => file.endsWith(".js"));

let totalSize = 0;
let totalGzipSize = 0;

files.forEach((file) => {
  const filePath = path.join(distDir, file);
  const size = getFileSize(filePath);
  const gzipSize = getGzipSize(filePath);

  totalSize += parseFloat(size);
  totalGzipSize += parseFloat(gzipSize);

  console.log(file.padEnd(40), `${size} KB`.padEnd(12), `${gzipSize} KB`);
});

console.log("-".repeat(70));
console.log(
  "Total".padEnd(40),
  `${totalSize.toFixed(2)} KB`.padEnd(12),
  `${totalGzipSize.toFixed(2)} KB`
);
console.log("");

// Check bundle size limits
const MAX_SIZE = 500; // KB
if (totalGzipSize > MAX_SIZE) {
  console.warn(
    `⚠️  Warning: Bundle size (${totalGzipSize} KB) exceeds ${MAX_SIZE} KB`
  );
}
```

---

<div align="center">

## 🚀 Gulp.js

</div>

### Stream-Based Task Runner 💧

```javascript
// ═══════════════════════════════════════════
// gulpfile.js
// Complete Gulp Configuration
// ═══════════════════════════════════════════

const gulp = require("gulp");
const sass = require("gulp-sass")(require("sass"));
const autoprefixer = require("gulp-autoprefixer");
const cleanCSS = require("gulp-clean-css");
const uglify = require("gulp-uglify");
const concat = require("gulp-concat");
const imagemin = require("gulp-imagemin");
const sourcemaps = require("gulp-sourcemaps");
const browserSync = require("browser-sync").create();
const del = require("del");
const gulpIf = require("gulp-if");
const rename = require("gulp-rename");
const babel = require("gulp-babel");
const eslint = require("gulp-eslint");

// Environment
const isProd = process.env.NODE_ENV === "production";

// ═══════════════════════════════════════════
// Paths Configuration
// ═══════════════════════════════════════════

const paths = {
  styles: {
    src: "src/scss/**/*.scss",
    dest: "dist/css",
  },
  scripts: {
    src: "src/js/**/*.js",
    dest: "dist/js",
  },
  images: {
    src: "src/images/**/*.{jpg,jpeg,png,gif,svg}",
    dest: "dist/images",
  },
  html: {
    src: "src/**/*.html",
    dest: "dist",
  },
};

// ═══════════════════════════════════════════
// Clean Task
// ═══════════════════════════════════════════

function clean() {
  return del(["dist"]);
}

// ═══════════════════════════════════════════
// Styles Task
// ═══════════════════════════════════════════

function styles() {
  return gulp
    .src(paths.styles.src)
    .pipe(gulpIf(!isProd, sourcemaps.init()))
    .pipe(sass().on("error", sass.logError))
    .pipe(
      autoprefixer({
        cascade: false,
      })
    )
    .pipe(gulpIf(isProd, cleanCSS()))
    .pipe(gulpIf(isProd, rename({ suffix: ".min" })))
    .pipe(gulpIf(!isProd, sourcemaps.write(".")))
    .pipe(gulp.dest(paths.styles.dest))
    .pipe(browserSync.stream());
}

// ═══════════════════════════════════════════
// Scripts Task
// ═══════════════════════════════════════════

function scripts() {
  return gulp
    .src(paths.scripts.src)
    .pipe(gulpIf(!isProd, sourcemaps.init()))
    .pipe(
      babel({
        presets: ["@babel/preset-env"],
      })
    )
    .pipe(concat("main.js"))
    .pipe(gulpIf(isProd, uglify()))
    .pipe(gulpIf(isProd, rename({ suffix: ".min" })))
    .pipe(gulpIf(!isProd, sourcemaps.write(".")))
    .pipe(gulp.dest(paths.scripts.dest))
    .pipe(browserSync.stream());
}

// ═══════════════════════════════════════════
// Lint Task
// ═══════════════════════════════════════════

function lint() {
  return gulp
    .src(paths.scripts.src)
    .pipe(eslint())
    .pipe(eslint.format())
    .pipe(eslint.failAfterError());
}

// ═══════════════════════════════════════════
// Images Task
// ═══════════════════════════════════════════

function images() {
  return gulp
    .src(paths.images.src)
    .pipe(
      gulpIf(
        isProd,
        imagemin([
          imagemin.gifsicle({ interlaced: true }),
          imagemin.mozjpeg({ quality: 75, progressive: true }),
          imagemin.optipng({ optimizationLevel: 5 }),
          imagemin.svgo({
            plugins: [{ removeViewBox: false }, { cleanupIDs: false }],
          }),
        ])
      )
    )
    .pipe(gulp.dest(paths.images.dest));
}

// ═══════════════════════════════════════════
// HTML Task
// ═══════════════════════════════════════════

function html() {
  return gulp
    .src(paths.html.src)
    .pipe(gulp.dest(paths.html.dest))
    .pipe(browserSync.stream());
}

// ═══════════════════════════════════════════
// Watch Task
// ═══════════════════════════════════════════

function watch() {
  browserSync.init({
    server: {
      baseDir: "./dist",
    },
    notify: false,
  });

  gulp.watch(paths.styles.src, styles);
  gulp.watch(paths.scripts.src, gulp.series(lint, scripts));
  gulp.watch(paths.images.src, images);
  gulp.watch(paths.html.src, html);
}

// ═══════════════════════════════════════════
// Advanced Tasks
// ═══════════════════════════════════════════

// Critical CSS
const critical = require("critical").stream;

function criticalCSS() {
  return gulp
    .src("dist/*.html")
    .pipe(
      critical({
        base: "dist/",
        inline: true,
        css: ["dist/css/main.css"],
        minify: true,
        dimensions: [
          {
            height: 900,
            width: 1300,
          },
        ],
      })
    )
    .pipe(gulp.dest("dist"));
}

// Service Worker
const workbox = require("workbox-build");

function generateSW() {
  return workbox.generateSW({
    globDirectory: "dist",
    globPatterns: ["**/*.{html,js,css,png,jpg,gif,svg}"],
    swDest: "dist/sw.js",
  });
}

// ═══════════════════════════════════════════
// Export Tasks
// ═══════════════════════════════════════════

// Individual tasks
exports.clean = clean;
exports.styles = styles;
exports.scripts = scripts;
exports.lint = lint;
exports.images = images;
exports.html = html;
exports.watch = watch;

// Complex tasks
exports.build = gulp.series(
  clean,
  gulp.parallel(styles, scripts, images, html)
);

exports.buildProd = gulp.series(
  clean,
  gulp.parallel(styles, scripts, images, html),
  criticalCSS,
  generateSW
);

exports.dev = gulp.series(
  clean,
  gulp.parallel(styles, scripts, images, html),
  watch
);

// Default task
exports.default = exports.dev;
```

---

### Gulp Plugins Library 🔌

```javascript
// ═══════════════════════════════════════════
// Popular Gulp Plugins
// ═══════════════════════════════════════════

// CSS
const sass = require('gulp-sass');
const less = require('gulp-less');
const postcss = require('gulp-postcss');
const autoprefixer = require('gulp-autoprefixer');
const cleanCSS = require('gulp-clean-css');
const purgecss = require('gulp-purgecss');

// JavaScript
const babel = require('gulp-babel');
const uglify = require('gulp-uglify');
const terser = require('gulp-terser');
const webpack = require('webpack-stream');

// HTML
const htmlmin = require('gulp-htmlmin');
const pug = require('gulp-pug');
const ejs = require('gulp-ejs');

// Images
const imagemin = require('gulp-imagemin');
const webp = require('gulp-webp');
const svgmin = require('gulp-svgmin');

// Utilities
const concat = require('gulp-concat');
const rename = require('gulp-rename');
const sourcemaps = require('gulp-sourcemaps');
const gulpIf = require('gulp-if');
const plumber = require('gulp-plumber');
const notify = require('gulp-notify');

// Quality
const eslint = require('gulp-eslint');
const stylelint = require('gulp-stylelint');

// Testing
const mocha = require('gulp-mocha');
const jest = require('gulp-jest');

// Package.json example
{
  "devDependencies": {
    "gulp": "^4.0.2",
    "gulp-sass": "^5.1.0",
    "gulp-autoprefixer": "^8.0.0",
    "gulp-clean-css": "^4.3.0",
    "gulp-uglify": "^3.0.2",
    "gulp-concat": "^2.6.1",
    "gulp-imagemin": "^8.0.0",
    "gulp-sourcemaps": "^3.0.0",
    "gulp-rename": "^2.0.0",
    "gulp-babel": "^8.0.0",
    "browser-sync": "^2.29.3",
    "del": "^7.0.0"
  }
}
```

---

<div align="center">

## 🔨 Grunt.js

</div>

### Configuration-Based Task Runner ⚙️

```javascript
// ═══════════════════════════════════════════
// Gruntfile.js
// Grunt Configuration
// ═══════════════════════════════════════════

module.exports = function (grunt) {
  // Project configuration
  grunt.initConfig({
    pkg: grunt.file.readJSON("package.json"),

    // ═══════════════════════════════════════════
    // Clean Task
    // ═══════════════════════════════════════════
    clean: {
      dist: ["dist"],
      temp: [".tmp"],
    },

    // ═══════════════════════════════════════════
    // SASS Compilation
    // ═══════════════════════════════════════════
    sass: {
      options: {
        sourceMap: true,
        outputStyle: "compressed",
      },
      dist: {
        files: {
          "dist/css/main.css": "src/scss/main.scss",
        },
      },
    },

    // ═══════════════════════════════════════════
    // PostCSS (Autoprefixer)
    // ═══════════════════════════════════════════
    postcss: {
      options: {
        map: true,
        processors: [
          require("autoprefixer")({
            overrideBrowserslist: ["last 2 versions"],
          }),
        ],
      },
      dist: {
        src: "dist/css/main.css",
      },
    },

    // ═══════════════════════════════════════════
    // CSS Minification
    // ═══════════════════════════════════════════
    cssmin: {
      target: {
        files: [
          {
            expand: true,
            cwd: "dist/css",
            src: ["*.css", "!*.min.css"],
            dest: "dist/css",
            ext: ".min.css",
          },
        ],
      },
    },

    // ═══════════════════════════════════════════
    // JavaScript Concatenation
    // ═══════════════════════════════════════════
    concat: {
      options: {
        separator: ";",
        sourceMap: true,
      },
      dist: {
        src: ["src/js/**/*.js"],
        dest: "dist/js/main.js",
      },
    },

    // ═══════════════════════════════════════════
    // JavaScript Uglification
    // ═══════════════════════════════════════════
    uglify: {
      options: {
        sourceMap: true,
        banner:
          '/*! <%= pkg.name %> <%= grunt.template.today("yyyy-mm-dd") %> */\n',
      },
      dist: {
        files: {
          "dist/js/main.min.js": ["dist/js/main.js"],
        },
      },
    },

    // ═══════════════════════════════════════════
    // Babel Transpilation
    // ═══════════════════════════════════════════
    babel: {
      options: {
        sourceMap: true,
        presets: ["@babel/preset-env"],
      },
      dist: {
        files: [
          {
            expand: true,
            cwd: "src/js",
            src: ["**/*.js"],
            dest: ".tmp/js",
          },
        ],
      },
    },

    // ═══════════════════════════════════════════
    // ESLint
    // ═══════════════════════════════════════════
    eslint: {
      target: ["src/js/**/*.js"],
    },

    // ═══════════════════════════════════════════
    // Image Optimization
    // ═══════════════════════════════════════════
    imagemin: {
      dynamic: {
        files: [
          {
            expand: true,
            cwd: "src/images",
            src: ["**/*.{png,jpg,gif,svg}"],
            dest: "dist/images",
          },
        ],
      },
    },

    // ═══════════════════════════════════════════
    // HTML Minification
    // ═══════════════════════════════════════════
    htmlmin: {
      dist: {
        options: {
          removeComments: true,
          collapseWhitespace: true,
        },
        files: [
          {
            expand: true,
            cwd: "src",
            src: ["**/*.html"],
            dest: "dist",
          },
        ],
      },
    },

    // ═══════════════════════════════════════════
    // Copy Files
    // ═══════════════════════════════════════════
    copy: {
      main: {
        files: [
          {
            expand: true,
            cwd: "src",
            src: ["**/*.html"],
            dest: "dist/",
          },
          {
            expand: true,
            cwd: "src/fonts",
            src: ["**/*"],
            dest: "dist/fonts",
          },
        ],
      },
    },

    // ═══════════════════════════════════════════
    // Watch Files
    // ═══════════════════════════════════════════
    watch: {
      sass: {
        files: ["src/scss/**/*.scss"],
        tasks: ["sass", "postcss"],
        options: {
          livereload: true,
        },
      },
      js: {
        files: ["src/js/**/*.js"],
        tasks: ["eslint", "babel", "concat", "uglify"],
        options: {
          livereload: true,
        },
      },
      html: {
        files: ["src/**/*.html"],
        tasks: ["copy"],
        options: {
          livereload: true,
        },
      },
    },

    // ═══════════════════════════════════════════
    // BrowserSync
    // ═══════════════════════════════════════════
    browserSync: {
      dev: {
        bsFiles: {
          src: ["dist/css/*.css", "dist/js/*.js", "dist/**/*.html"],
        },
        options: {
          watchTask: true,
          server: "./dist",
        },
      },
    },
  });

  // ═══════════════════════════════════════════
  // Load NPM Tasks
  // ═══════════════════════════════════════════

  grunt.loadNpmTasks("grunt-contrib-clean");
  grunt.loadNpmTasks("grunt-sass");
  grunt.loadNpmTasks("grunt-postcss");
  grunt.loadNpmTasks("grunt-contrib-cssmin");
  grunt.loadNpmTasks("grunt-contrib-concat");
  grunt.loadNpmTasks("grunt-contrib-uglify");
  grunt.loadNpmTasks("grunt-babel");
  grunt.loadNpmTasks("grunt-eslint");
  grunt.loadNpmTasks("grunt-contrib-imagemin");
  grunt.loadNpmTasks("grunt-contrib-htmlmin");
  grunt.loadNpmTasks("grunt-contrib-copy");
  grunt.loadNpmTasks("grunt-contrib-watch");
  grunt.loadNpmTasks("grunt-browser-sync");

  // ═══════════════════════════════════════════
  // Register Tasks
  // ═══════════════════════════════════════════

  // Default task
  grunt.registerTask("default", ["dev"]);

  // Development task
  grunt.registerTask("dev", [
    "clean",
    "sass",
    "postcss",
    "babel",
    "concat",
    "copy",
    "browserSync",
    "watch",
  ]);

  // Build task
  grunt.registerTask("build", [
    "clean",
    "sass",
    "postcss",
    "cssmin",
    "babel",
    "concat",
    "uglify",
    "imagemin",
    "htmlmin",
    "copy",
  ]);

  // Lint task
  grunt.registerTask("lint", ["eslint"]);

  // Custom task
  grunt.registerTask("hello", "A sample task", function () {
    grunt.log.writeln("Hello from Grunt!");
  });
};
```

---

<div align="center">

## 🏗️ Make

</div>

### The Original Build Tool 🔨

```makefile
# ═══════════════════════════════════════════
# Makefile
# Cross-platform task automation
# ═══════════════════════════════════════════

.PHONY: help install dev build test clean deploy all

# Default goal
.DEFAULT_GOAL := help

# Variables
NODE_VERSION := 20
DOCKER_IMAGE := myapp
DOCKER_TAG := latest
DIST_DIR := dist
SRC_DIR := src

# Colors for output
RED := \033[0;31m
GREEN := \033[0;32m
YELLOW := \033[0;33m
BLUE := \033[0;34m
NC := \033[0m # No Color

# ═══════════════════════════════════════════
# Help
# ═══════════════════════════════════════════

help: ## Show this help message
	@echo '$(BLUE)Available targets:$(NC)'
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | \
		awk 'BEGIN {FS = ":.*?## "}; {printf "  $(GREEN)%-20s$(NC) %s\n", $$1, $$2}'

# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

install: ## Install dependencies
	@echo "$(BLUE)Installing dependencies...$(NC)"
	npm ci
	@echo "$(GREEN)✓ Dependencies installed$(NC)"

install-dev: ## Install development dependencies
	@echo "$(BLUE)Installing development dependencies...$(NC)"
	npm install
	@echo "$(GREEN)✓ Development dependencies installed$(NC)"

# ═══════════════════════════════════════════
# Development
# ═══════════════════════════════════════════

dev: install ## Start development server
	@echo "$(BLUE)Starting development server...$(NC)"
	npm run dev

dev-debug: install ## Start development server with debugging
	@echo "$(BLUE)Starting development server with debugging...$(NC)"
	npm run dev:debug

# ═══════════════════════════════════════════
# Building
# ═══════════════════════════════════════════

build: clean install ## Build for production
	@echo "$(BLUE)Building for production...$(NC)"
	npm run build
	@echo "$(GREEN)✓ Build completed$(NC)"
	@$(MAKE) --no-print-directory build-stats

build-dev: clean install ## Build for development
	@echo "$(BLUE)Building for development...$(NC)"
	npm run build:dev
	@echo "$(GREEN)✓ Development build completed$(NC)"

build-staging: clean install ## Build for staging
	@echo "$(BLUE)Building for staging...$(NC)"
	npm run build:staging
	@echo "$(GREEN)✓ Staging build completed$(NC)"

build-stats: ## Show build statistics
	@echo "$(BLUE)Build Statistics:$(NC)"
	@du -sh $(DIST_DIR)
	@find $(DIST_DIR) -type f -name "*.js" -exec du -h {} \; | sort -rh | head -10

# ═══════════════════════════════════════════
# Testing
# ═══════════════════════════════════════════

test: ## Run all tests
	@echo "$(BLUE)Running tests...$(NC)"
	npm test

test-unit: ## Run unit tests
	@echo "$(BLUE)Running unit tests...$(NC)"
	npm run test:unit

test-e2e: ## Run E2E tests
	@echo "$(BLUE)Running E2E tests...$(NC)"
	npm run test:e2e

test-watch: ## Run tests in watch mode
	@echo "$(BLUE)Running tests in watch mode...$(NC)"
	npm run test:watch

test-coverage: ## Run tests with coverage
	@echo "$(BLUE)Running tests with coverage...$(NC)"
	npm run test:coverage
	@echo "$(GREEN)✓ Coverage report generated$(NC)"
	@open coverage/index.html || xdg-open coverage/index.html

# ═══════════════════════════════════════════
# Code Quality
# ═══════════════════════════════════════════

lint: ## Run linter
	@echo "$(BLUE)Running linter...$(NC)"
	npm run lint

lint-fix: ## Run linter with auto-fix
	@echo "$(BLUE)Running linter with auto-fix...$(NC)"
	npm run lint:fix
	@echo "$(GREEN)✓ Linting completed$(NC)"

format: ## Format code
	@echo "$(BLUE)Formatting code...$(NC)"
	npm run format
	@echo "$(GREEN)✓ Code formatted$(NC)"

format-check: ## Check code formatting
	@echo "$(BLUE)Checking code formatting...$(NC)"
	npm run format:check

type-check: ## Run type checking
	@echo "$(BLUE)Running type checking...$(NC)"
	npm run type-check
	@echo "$(GREEN)✓ Type checking passed$(NC)"

quality: lint format-check type-check ## Run all quality checks
	@echo "$(GREEN)✓ All quality checks passed$(NC)"

# ═══════════════════════════════════════════
# Database
# ═══════════════════════════════════════════

db-migrate: ## Run database migrations
	@echo "$(BLUE)Running database migrations...$(NC)"
	npm run db:migrate
	@echo "$(GREEN)✓ Migrations completed$(NC)"

db-seed: ## Seed database
	@echo "$(BLUE)Seeding database...$(NC)"
	npm run db:seed
	@echo "$(GREEN)✓ Database seeded$(NC)"

db-reset: ## Reset database
	@echo "$(YELLOW)⚠️  This will reset the database!$(NC)"
	@read -p "Are you sure? [y/N] " -n 1 -r; \
	echo; \
	if [[ $$REPLY =~ ^[Yy]$$ ]]; then \
		npm run db:reset; \
		echo "$(GREEN)✓ Database reset$(NC)"; \
	else \
		echo "$(YELLOW)Operation cancelled$(NC)"; \
	fi

db-studio: ## Open database studio
	@echo "$(BLUE)Opening database studio...$(NC)"
	npm run db:studio

# ═══════════════════════════════════════════
# Docker
# ═══════════════════════════════════════════

docker-build: ## Build Docker image
	@echo "$(BLUE)Building Docker image...$(NC)"
	docker build -t $(DOCKER_IMAGE):$(DOCKER_TAG) .
	@echo "$(GREEN)✓ Docker image built$(NC)"

docker-run: ## Run Docker container
	@echo "$(BLUE)Running Docker container...$(NC)"
	docker run -p 3000:3000 $(DOCKER_IMAGE):$(DOCKER_TAG)

docker-push: ## Push Docker image
	@echo "$(BLUE)Pushing Docker image...$(NC)"
	docker push $(DOCKER_IMAGE):$(DOCKER_TAG)
	@echo "$(GREEN)✓ Docker image pushed$(NC)"

docker-up: ## Start Docker Compose services
	@echo "$(BLUE)Starting Docker Compose services...$(NC)"
	docker-compose up -d
	@echo "$(GREEN)✓ Services started$(NC)"

docker-down: ## Stop Docker Compose services
	@echo "$(BLUE)Stopping Docker Compose services...$(NC)"
	docker-compose down
	@echo "$(GREEN)✓ Services stopped$(NC)"

docker-logs: ## Show Docker Compose logs
	docker-compose logs -f

docker-clean: ## Clean Docker resources
	@echo "$(YELLOW)⚠️  This will remove all unused Docker resources!$(NC)"
	@read -p "Are you sure? [y/N] " -n 1 -r; \
	echo; \
	if [[ $$REPLY =~ ^[Yy]$$ ]]; then \
		docker system prune -af --volumes; \
		echo "$(GREEN)✓ Docker resources cleaned$(NC)"; \
	else \
		echo "$(YELLOW)Operation cancelled$(NC)"; \
	fi

# ═══════════════════════════════════════════
# Deployment
# ═══════════════════════════════════════════

deploy-staging: build-staging ## Deploy to staging
	@echo "$(BLUE)Deploying to staging...$(NC)"
	npm run deploy:staging
	@echo "$(GREEN)✓ Deployed to staging$(NC)"

deploy-production: build ## Deploy to production
	@echo "$(YELLOW)⚠️  Deploying to PRODUCTION!$(NC)"
	@read -p "Are you sure? [y/N] " -n 1 -r; \
	echo; \
	if [[ $$REPLY =~ ^[Yy]$$ ]]; then \
		npm run deploy:production; \
		echo "$(GREEN)✓ Deployed to production$(NC)"; \
	else \
		echo "$(YELLOW)Deployment cancelled$(NC)"; \
	fi

# ═══════════════════════════════════════════
# Utilities
# ═══════════════════════════════════════════

clean: ## Clean build artifacts
	@echo "$(BLUE)Cleaning build artifacts...$(NC)"
	rm -rf $(DIST_DIR) build .next coverage .cache
	@echo "$(GREEN)✓ Build artifacts cleaned$(NC)"

clean-modules: ## Clean node_modules
	@echo "$(BLUE)Cleaning node_modules...$(NC)"
	rm -rf node_modules
	@echo "$(GREEN)✓ node_modules cleaned$(NC)"

clean-all: clean clean-modules ## Clean everything
	@echo "$(GREEN)✓ Everything cleaned$(NC)"

fresh: clean-all install ## Fresh install
	@echo "$(GREEN)✓ Fresh install completed$(NC)"

update: ## Update dependencies
	@echo "$(BLUE)Updating dependencies...$(NC)"
	npm update
	npm outdated
	@echo "$(GREEN)✓ Dependencies updated$(NC)"

check-updates: ## Check for dependency updates
	@echo "$(BLUE)Checking for updates...$(NC)"
	npx npm-check-updates

# ═══════════════════════════════════════════
# Git
# ═══════════════════════════════════════════

git-cleanup: ## Cleanup merged Git branches
	@echo "$(BLUE)Cleaning up merged branches...$(NC)"
	git fetch --prune
	git branch --merged | grep -v "\*\|main\|master\|develop" | xargs -n 1 git branch -d || true
	@echo "$(GREEN)✓ Branches cleaned$(NC)"

# ═══════════════════════════════════════════
# CI/CD
# ═══════════════════════════════════════════

ci: quality test build ## Run CI pipeline
	@echo "$(GREEN)✓ CI pipeline completed successfully$(NC)"

ci-full: install quality test-coverage build ## Run full CI pipeline
	@echo "$(GREEN)✓ Full CI pipeline completed successfully$(NC)"

# ═══════════════════════════════════════════
# Release
# ═══════════════════════════════════════════

release: ## Create a release
	@echo "$(BLUE)Creating release...$(NC)"
	npm run release
	@echo "$(GREEN)✓ Release created$(NC)"

release-minor: ## Create minor release
	@echo "$(BLUE)Creating minor release...$(NC)"
	npm run release:minor
	@echo "$(GREEN)✓ Minor release created$(NC)"

release-major: ## Create major release
	@echo "$(BLUE)Creating major release...$(NC)"
	npm run release:major
	@echo "$(GREEN)✓ Major release created$(NC)"

# ═══════════════════════════════════════════
# All-in-one commands
# ═══════════════════════════════════════════

all: clean install quality test build ## Run everything
	@echo "$(GREEN)✓ All tasks completed$(NC)"

start: install dev ## Install and start development
	@echo "$(GREEN)✓ Development environment ready$(NC)"

# ═══════════════════════════════════════════
# Advanced Patterns
# ═══════════════════════════════════════════

# Conditional execution
build-if-changed:
	@if git diff --quiet HEAD -- $(SRC_DIR); then \
		echo "$(YELLOW)No changes detected, skipping build$(NC)"; \
	else \
		$(MAKE) build; \
	fi

# Parallel execution
test-all: ## Run all tests in parallel
	@echo "$(BLUE)Running all tests in parallel...$(NC)"
	@$(MAKE) -j4 test-unit test-e2e lint type-check
	@echo "$(GREEN)✓ All tests passed$(NC)"

# Progress indicator
long-task: ## Example of long task with progress
	@echo "$(BLUE)Starting long task...$(NC)"
	@for i in {1..10}; do \
		echo -n "$(GREEN)█$(NC)"; \
		sleep 0.5; \
	done
	@echo "\n$(GREEN)✓ Task completed$(NC)"
```

---

<div align="center">

## ⚡ Modern Build Tools

</div>

### Vite ⚡

```javascript
// ═══════════════════════════════════════════
// vite.config.js
// Modern, Fast Build Tool
// ═══════════════════════════════════════════

import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';
import path from 'path';

export default defineConfig(({ mode }) => {
  const isDev = mode === 'development';

  return {
    // Plugins
    plugins: [
      react({
        // Fast Refresh configuration
        fastRefresh: true,
      }),
    ],

    // Development server
    server: {
      port: 3000,
      open: true,
      cors: true,
      proxy: {
        '/api': {
          target: 'http://localhost:8000',
          changeOrigin: true,
          rewrite: (path) => path.replace(/^\/api/, ''),
        },
      },
    },

    // Build configuration
    build: {
      outDir: 'dist',
      assetsDir: 'assets',
      sourcemap: isDev,
      minify: !isDev ? 'terser' : false,
      terserOptions: {
        compress: {
          drop_console: true,
          drop_debugger: true,
        },
      },
      rollupOptions: {
        output: {
          manualChunks: {
            vendor: ['react', 'react-dom'],
            router: ['react-router-dom'],
          },
        },
      },
      chunkSizeWarningLimit: 1000,
    },

    // Path aliases
    resolve: {
      alias: {
        '@': path.resolve(__dirname, './src'),
        '@components': path.resolve(__dirname, './src/components'),
        '@utils': path.resolve(__dirname, './src/utils'),
        '@hooks': path.resolve(__dirname, './src/hooks'),
        '@styles': path.resolve(__dirname, './src/styles'),
      },
    },

    // CSS configuration
    css: {
      modules: {
        localsConvention: 'camelCase',
      },
      preprocessorOptions: {
        scss: {
          additionalData: `@import "@/styles/variables.scss";`,
        },
      },
    },

    // Environment variables
    define: {
      __APP_VERSION__: JSON.stringify(process.env.npm_package_version),
      __BUILD_DATE__: JSON.stringify(new Date().toISOString()),
    },

    // Optimize dependencies
    optimizeDeps: {
      include: ['react', 'react-dom', 'react-router-dom'],
      exclude: ['@some/large-lib'],
    },

    // Preview server
    preview: {
      port: 8080,
      open: true,
    },
  };
});

// ═══════════════════════════════════════════
// Advanced Vite Plugins
// ═══════════════════════════════════════════

import { visualizer } from 'rollup-plugin-visualizer';
import viteCompression from 'vite-plugin-compression';
import { VitePWA } from 'vite-plugin-pwa';

export default defineConfig({
  plugins: [
    react(),

    // Bundle analyzer
    visualizer({
      open: true,
      gzipSize: true,
      brotliSize: true,
    }),

    // Gzip compression
    viteCompression({
      algorithm: 'gzip',
      ext: '.gz',
    }),

    // Brotli compression
    viteCompression({
      algorithm: 'brotliCompress',
      ext: '.br',
    }),

    // PWA
    VitePWA({
      registerType: 'autoUpdate',
      manifest: {
        name: 'My App',
        short_name: 'App',
        theme_color: '#ffffff',
        icons: [
          {
            src: '/icon-192x192.png',
            sizes: '192x192',
            type: 'image/png',
          },
        ],
      },
    }),
  ],
});
```

---

### Webpack 📦

```javascript
// ═══════════════════════════════════════════
// webpack.config.js
// Powerful Module Bundler
// ═══════════════════════════════════════════

const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");
const MiniCssExtractPlugin = require("mini-css-extract-plugin");
const TerserPlugin = require("terser-webpack-plugin");
const CssMinimizerPlugin = require("css-minimizer-webpack-plugin");
const { BundleAnalyzerPlugin } = require("webpack-bundle-analyzer");

const isDev = process.env.NODE_ENV === "development";

module.exports = {
  mode: isDev ? "development" : "production",

  entry: {
    main: "./src/index.js",
  },

  output: {
    path: path.resolve(__dirname, "dist"),
    filename: isDev ? "[name].js" : "[name].[contenthash].js",
    chunkFilename: isDev ? "[name].chunk.js" : "[name].[contenthash].chunk.js",
    clean: true,
    publicPath: "/",
  },

  devtool: isDev ? "eval-source-map" : "source-map",

  devServer: {
    static: "./dist",
    port: 3000,
    hot: true,
    open: true,
    historyApiFallback: true,
    proxy: {
      "/api": {
        target: "http://localhost:8000",
        changeOrigin: true,
      },
    },
  },

  module: {
    rules: [
      // JavaScript/JSX
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader",
          options: {
            presets: ["@babel/preset-env", "@babel/preset-react"],
            plugins: [isDev && require.resolve("react-refresh/babel")].filter(
              Boolean
            ),
          },
        },
      },

      // TypeScript
      {
        test: /\.(ts|tsx)$/,
        exclude: /node_modules/,
        use: "ts-loader",
      },

      // CSS
      {
        test: /\.css$/,
        use: [
          isDev ? "style-loader" : MiniCssExtractPlugin.loader,
          {
            loader: "css-loader",
            options: {
              importLoaders: 1,
              modules: {
                auto: true,
                localIdentName: isDev
                  ? "[path][name]__[local]"
                  : "[hash:base64]",
              },
            },
          },
          "postcss-loader",
        ],
      },

      // SCSS
      {
        test: /\.scss$/,
        use: [
          isDev ? "style-loader" : MiniCssExtractPlugin.loader,
          "css-loader",
          "postcss-loader",
          "sass-loader",
        ],
      },

      // Images
      {
        test: /\.(png|jpg|jpeg|gif|svg)$/i,
        type: "asset",
        parser: {
          dataUrlCondition: {
            maxSize: 8 * 1024, // 8kb
          },
        },
        generator: {
          filename: "images/[name].[hash][ext]",
        },
      },

      // Fonts
      {
        test: /\.(woff|woff2|eot|ttf|otf)$/i,
        type: "asset/resource",
        generator: {
          filename: "fonts/[name].[hash][ext]",
        },
      },
    ],
  },

  plugins: [
    new HtmlWebpackPlugin({
      template: "./public/index.html",
      minify: !isDev && {
        removeComments: true,
        collapseWhitespace: true,
        removeAttributeQuotes: true,
      },
    }),

    !isDev &&
      new MiniCssExtractPlugin({
        filename: "css/[name].[contenthash].css",
        chunkFilename: "css/[name].[contenthash].chunk.css",
      }),

    !isDev &&
      new BundleAnalyzerPlugin({
        analyzerMode: "static",
        openAnalyzer: false,
      }),
  ].filter(Boolean),

  optimization: {
    minimize: !isDev,
    minimizer: [
      new TerserPlugin({
        terserOptions: {
          compress: {
            drop_console: true,
          },
        },
      }),
      new CssMinimizerPlugin(),
    ],
    splitChunks: {
      chunks: "all",
      cacheGroups: {
        vendor: {
          test: /[\\/]node_modules[\\/]/,
          name: "vendors",
          priority: 10,
        },
        common: {
          minChunks: 2,
          priority: 5,
          reuseExistingChunk: true,
        },
      },
    },
    runtimeChunk: "single",
  },

  resolve: {
    extensions: [".js", ".jsx", ".ts", ".tsx", ".json"],
    alias: {
      "@": path.resolve(__dirname, "src"),
      "@components": path.resolve(__dirname, "src/components"),
      "@utils": path.resolve(__dirname, "src/utils"),
    },
  },
};
```

---

### Parcel 📦

```json
// ═══════════════════════════════════════════
// package.json - Parcel Configuration
// Zero-config bundler
// ═══════════════════════════════════════════

{
  "name": "my-app",
  "source": "src/index.html",
  "scripts": {
    "dev": "parcel",
    "build": "parcel build"
  },
  "devDependencies": {
    "parcel": "^2.10.0"
  }
}

// ═══════════════════════════════════════════
// .parcelrc - Custom Configuration
// ═══════════════════════════════════════════

{
  "extends": "@parcel/config-default",
  "transformers": {
    "*.{js,mjs,jsx,cjs,ts,tsx}": [
      "@parcel/transformer-js",
      "@parcel/transformer-react-refresh-wrap"
    ]
  },
  "optimizers": {
    "*.js": ["@parcel/optimizer-terser"]
  }
}
```

---

### Comparison Table 📊

<div align="center">

| Feature              | NPM Scripts     | Gulp            | Grunt           | Make           | Vite               | Webpack         |
| -------------------- | --------------- | --------------- | --------------- | -------------- | ------------------ | --------------- |
| **Setup Complexity** | ⭐ Simple       | ⭐⭐ Moderate   | ⭐⭐ Moderate   | ⭐⭐ Moderate  | ⭐ Simple          | ⭐⭐⭐ Complex  |
| **Configuration**    | JSON            | JavaScript      | JavaScript      | Makefile       | JavaScript         | JavaScript      |
| **Build Speed**      | ⭐⭐ Slow       | ⭐⭐⭐ Fast     | ⭐⭐ Moderate   | ⭐⭐⭐ Fast    | ⭐⭐⭐⭐⭐ Blazing | ⭐⭐⭐ Fast     |
| **Hot Reload**       | ❌ No           | ⚠️ Plugin       | ⚠️ Plugin       | ❌ No          | ✅ Built-in        | ✅ Built-in     |
| **Code Splitting**   | ❌ No           | ❌ No           | ❌ No           | ❌ No          | ✅ Yes             | ✅ Yes          |
| **Learning Curve**   | ⭐ Easy         | ⭐⭐ Moderate   | ⭐⭐ Moderate   | ⭐⭐ Moderate  | ⭐ Easy            | ⭐⭐⭐ Steep    |
| **Best For**         | Simple tasks    | Frontend builds | Legacy projects | Any project    | Modern apps        | Large apps      |
| **Community**        | ⭐⭐⭐⭐⭐ Huge | ⭐⭐⭐ Good     | ⭐⭐ Declining  | ⭐⭐⭐⭐ Large | ⭐⭐⭐⭐⭐ Growing | ⭐⭐⭐⭐⭐ Huge |

</div>

---

<div align="center">

## 🎯 Choosing the Right Tool

</div>

### Decision Tree 🌳

```
┌─────────────────────────────────────┐
│   What are you building?            │
└──────────────┬──────────────────────┘
               │
        ┌──────┴───────┐
        │              │
   Simple tasks    Complex app
        │              │
        │         ┌────┴─────┐
        │         │          │
   NPM Scripts   Modern    Legacy
        │         │          │
        │    ┌────┴────┐     │
        │    │         │     │
        │   Vite    Webpack  │
        │                    │
        └────────────────────┴──── Make (cross-platform)


When to use each:

📦 NPM Scripts
✅ Simple projects
✅ Running basic commands
✅ No complex build pipeline
❌ Large-scale applications

🚀 Gulp
✅ Frontend asset pipeline
✅ Stream-based operations
✅ File transformations
❌ Module bundling needs

🔨 Grunt
✅ Legacy projects
✅ Configuration over code
❌ New projects (consider alternatives)

🏗️ Make
✅ Cross-language projects
✅ System-level tasks
✅ CI/CD pipelines
✅ Docker workflows

⚡ Vite
✅ Modern web applications
✅ React, Vue, Svelte
✅ Fast development
✅ Small to medium projects

📦 Webpack
✅ Large applications
✅ Complex build requirements
✅ Fine-grained control
✅ Enterprise projects

📦 Parcel
✅ Zero-config needed
✅ Quick prototypes
✅ Simple applications
```

---

<div align="center">

## 💡 Best Practices

</div>

### General Best Practices 📋

```javascript
// ═══════════════════════════════════════════
// 1. Keep Tasks Small & Focused
// ═══════════════════════════════════════════

// ❌ Bad - One monolithic task
"build": "clean && transpile && bundle && minify && optimize && deploy"

// ✅ Good - Composable tasks
"clean": "rimraf dist",
"transpile": "babel src -d dist",
"bundle": "webpack",
"minify": "terser dist/**/*.js",
"optimize": "imagemin src/images",
"build": "npm-run-all clean transpile bundle minify optimize"

// ═══════════════════════════════════════════
// 2. Use Cross-Platform Tools
// ═══════════════════════════════════════════

// ❌ Bad - Platform-specific
"clean": "rm -rf dist"  // Fails on Windows

// ✅ Good - Cross-platform
"clean": "rimraf dist"  // Works everywhere

// ═══════════════════════════════════════════
// 3. Leverage Parallel Execution
// ═══════════════════════════════════════════

// Sequential (slow)
"test": "npm run test:unit && npm run test:e2e && npm run lint"

// Parallel (fast)
"test": "npm-run-all --parallel test:unit test:e2e lint"

// ═══════════════════════════════════════════
// 4. Environment-Specific Configurations
// ═══════════════════════════════════════════

{
  "scripts": {
    "build": "cross-env NODE_ENV=production webpack",
    "build:dev": "cross-env NODE_ENV=development webpack",
    "build:staging": "cross-env NODE_ENV=staging webpack"
  }
}

// ═══════════════════════════════════════════
// 5. Use Caching Effectively
// ═══════════════════════════════════════════

// Webpack caching
module.exports = {
  cache: {
    type: 'filesystem',
    buildDependencies: {
      config: [__filename],
    },
  },
};

// ═══════════════════════════════════════════
// 6. Document Your Tasks
// ═══════════════════════════════════════════

{
  "scripts": {
    "dev": "# Start development server → vite",
    "build": "# Build for production → vite build",
    "test": "# Run all tests → vitest"
  }
}

// Or use a separate docs file
// docs/scripts.md

// ═══════════════════════════════════════════
// 7. Version Lock Your Tools
// ═══════════════════════════════════════════

{
  "devDependencies": {
    "vite": "5.0.0",        // Specific version
    "webpack": "^5.89.0"    // Allow patch updates
  }
}

// ═══════════════════════════════════════════
// 8. Error Handling
// ═══════════════════════════════════════════

// Handle errors gracefully
"build": "npm run lint || exit 0 && npm run build:app"

// Or use try-catch in scripts
// scripts/build.js
try {
  await build();
} catch (error) {
  console.error('Build failed:', error);
  process.exit(1);
}

// ═══════════════════════════════════════════
// 9. Performance Optimization
// ═══════════════════════════════════════════

// Use production mode
"build": "NODE_ENV=production webpack"

// Enable caching
"dev": "webpack serve --cache"

// Watch only necessary files
"watch": "nodemon --watch src --ext js,jsx"

// ═══════════════════════════════════════════
// 10. Maintain Clean Output
// ═══════════════════════════════════════════

// Add --silent flag for cleaner output
"build": "npm run build:app --silent"

// Use progress indicators
"build": "webpack --progress"

// Color-coded output
console.log('\x1b[32m✓ Build successful\x1b[0m');
console.log('\x1b[31m✗ Build failed\x1b[0m');
```

---

<div align="center">

## 🎓 Resources & Learning

</div>

### Essential Resources 📚

```
📘 NPM Scripts
   Documentation: https://docs.npmjs.com/cli/v10/using-npm/scripts
   Awesome NPM Scripts: https://github.com/RyanZim/awesome-npm-scripts

📗 Gulp
   Official Docs: https://gulpjs.com/docs/
   Awesome Gulp: https://github.com/alferov/awesome-gulp

📙 Grunt
   Official Docs: https://gruntjs.com/
   Plugin Directory: https://gruntjs.com/plugins

🏗️ Make
   GNU Make Manual: https://www.gnu.org/software/make/manual/
   Make Tutorial: https://makefiletutorial.com/

⚡ Vite
   Official Docs: https://vitejs.dev/
   Awesome Vite: https://github.com/vitejs/awesome-vite

📦 Webpack
   Official Docs: https://webpack.js.org/
   Webpack Academy: https://webpack.academy/

🎥 Video Tutorials
   - Task Runners Explained (Traversy Media)
   - Modern Build Tools (Fireship)
   - Webpack Deep Dive (Academind)

📚 Books
   - "JavaScript Build Tools" by Andrew Burgess
   - "Modern Web Development" by various authors

🛠️ Tools
   - npm-check-updates: Update dependencies
   - bundlephobia: Check package sizes
   - webpack-bundle-analyzer: Analyze bundles
```

---

<div align="center">

**Built with ⚙️ by developers who automate everything**

_May your builds be fast and your tasks be automated!_ 🚀

**Happy Building!** ✨

</div>
