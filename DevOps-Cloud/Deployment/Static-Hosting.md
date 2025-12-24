<div align="center">

# 🌐 Static Site & Frontend Hosting - Complete Guide

### _Deploy your frontend to the world in minutes_ 🚀

![Static Hosting](https://img.shields.io/badge/Hosting-Lightning%20Fast-yellow?style=for-the-badge)
![CDN](https://img.shields.io/badge/CDN-Global-blue?style=for-the-badge)
![Deploy](https://img.shields.io/badge/Deploy-Seconds-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Guide-2025%20Updated-gold?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 Understanding Static Hosting](#-understanding-static-hosting)
- [⚡ Platform Comparison 2025](#-platform-comparison-2025)
- [▲ Vercel](#-vercel)
- [🌐 Netlify](#-netlify)
- [🐙 GitHub Pages](#-github-pages)
- [☁️ Cloudflare Pages](#️-cloudflare-pages)
- [🎨 Render Static Sites](#-render-static-sites)
- [🌊 Surge](#-surge)
- [🔧 Build Optimization](#-build-optimization)
- [🎨 Performance Optimization](#-performance-optimization)
- [🔍 SEO Best Practices](#-seo-best-practices)
- [🔐 Security Headers](#-security-headers)
- [🌍 Custom Domains](#-custom-domains)
- [🚀 CI/CD Integration](#-cicd-integration)
- [🐛 Troubleshooting](#-troubleshooting)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Understanding Static Hosting

_What makes static sites special?_ ⚡

</div>

### Static vs Dynamic Explained

```
╔═══════════════════════════════════════════════════════════╗
║              STATIC VS DYNAMIC HOSTING                     ║
╚═══════════════════════════════════════════════════════════╝

TRADITIONAL DYNAMIC SITE:
┌────────────────────────────────────────────────────────┐
│  Browser                                               │
│    ↓ Request: example.com/page                        │
│                                                        │
│  Server (Node.js, PHP, Python)                        │
│    ↓ Process request                                  │
│    ↓ Query database                                   │
│    ↓ Run business logic                               │
│    ↓ Generate HTML                                    │
│    ↓ Send response                                    │
│                                                        │
│  Browser                                               │
│    ↓ Render page                                      │
│                                                        │
│  ⏱️  Response Time: 200-500ms                          │
│  💰 Cost: $5-50/month                                  │
│  🔧 Complexity: High                                   │
└────────────────────────────────────────────────────────┘

STATIC SITE (JAMstack):
┌────────────────────────────────────────────────────────┐
│  Browser                                               │
│    ↓ Request: example.com/page.html                   │
│                                                        │
│  CDN (Global Edge Network)                            │
│    ↓ Return pre-built HTML (cached)                  │
│                                                        │
│  Browser                                               │
│    ↓ Render page                                      │
│                                                        │
│  ⏱️  Response Time: 10-50ms                            │
│  💰 Cost: $0-10/month                                  │
│  🔧 Complexity: Low                                    │
└────────────────────────────────────────────────────────┘

═══════════════════════════════════════════════════════════

STATIC SITE GENERATION (SSG):

Build Time:
┌────────────────────────────────────────────┐
│  Source Code (React, Vue, etc.)            │
│           ↓                                │
│  Build Process (npm run build)            │
│  • Compile components                      │
│  • Fetch data from APIs                    │
│  • Generate HTML files                     │
│  • Optimize assets                         │
│           ↓                                │
│  Static Files                              │
│  ├── index.html                            │
│  ├── about.html                            │
│  ├── blog/                                 │
│  │   ├── post-1.html                       │
│  │   └── post-2.html                       │
│  └── assets/                               │
│      ├── styles.css                        │
│      └── app.js                            │
└────────────────────────────────────────────┘

Runtime:
┌────────────────────────────────────────────┐
│  User Request                              │
│    ↓                                       │
│  CDN (Cached Files)                        │
│    ↓ Instant Delivery                     │
│  Browser                                   │
│    ↓ Hydrate with JavaScript              │
│  Interactive App                           │
└────────────────────────────────────────────┘

═══════════════════════════════════════════════════════════

WHEN TO USE STATIC HOSTING:

✅ PERFECT FOR:
• Marketing websites
• Portfolios
• Documentation sites
• Blogs
• Landing pages
• E-commerce (with headless CMS)
• Single Page Applications (SPAs)
• Progressive Web Apps (PWAs)

❌ NOT IDEAL FOR:
• Real-time collaboration tools
• Apps with user-specific server state
• Heavy server-side processing
• Complex authentication flows
• Frequently changing data (better with SSR)

💡 SOLUTION: Hybrid Approach
Static pages + Serverless functions + External APIs
Example: Next.js with Static Generation + API Routes

═══════════════════════════════════════════════════════════

BENEFITS OF STATIC HOSTING:

⚡ SPEED
• Files served from CDN edge locations
• No server processing time
• Pre-rendered at build time
• 50-100ms response times globally

💰 COST
• No servers to maintain
• Free or very cheap ($0-10/month)
• No scaling costs
• Pay only for bandwidth

🔒 SECURITY
• No server to hack
• No database vulnerabilities
• Reduced attack surface
• Automatic DDoS protection

📈 SCALABILITY
• CDN handles millions of requests
• No server capacity limits
• Global distribution
• Automatic scaling

🛠️ SIMPLICITY
• No server management
• No DevOps complexity
• Git-based deployment
• Version control built-in

🔄 RELIABILITY
• No server downtime
• Redundant CDN nodes
• 99.99% uptime
• Instant rollbacks
```

---

<div align="center">

## ⚡ Platform Comparison 2025

_Choose the right platform for your needs_ 🎯

</div>

### Comprehensive Comparison

```
═══════════════════════════════════════════════════════════
STATIC HOSTING PLATFORM COMPARISON 2025
═══════════════════════════════════════════════════════════

┌──────────────┬─────────────┬────────────┬──────────────┬─────────┐
│ Platform     │ Free Tier   │ Best For   │ Deploy Speed │ Rating  │
├──────────────┼─────────────┼────────────┼──────────────┼─────────┤
│ Vercel       │ 100GB BW    │ Next.js    │ ⚡⚡⚡ Fast   │ ⭐⭐⭐⭐⭐ │
│              │ 1M requests │ React      │ 30-60s       │         │
│              │ Unlimited   │ Modern SPAs│              │         │
├──────────────┼─────────────┼────────────┼──────────────┼─────────┤
│ Netlify      │ 100GB BW    │ JAMstack   │ ⚡⚡⚡ Fast   │ ⭐⭐⭐⭐⭐ │
│              │ 300min build│ Static+API │ 40-90s       │         │
│              │ /month      │ Headless   │              │         │
├──────────────┼─────────────┼────────────┼──────────────┼─────────┤
│ Cloudflare   │ Unlimited   │ Global CDN │ ⚡⚡ Medium  │ ⭐⭐⭐⭐⭐ │
│ Pages        │ requests    │ Edge       │ 60-120s      │         │
│              │ 500 builds  │ functions  │              │         │
├──────────────┼─────────────┼────────────┼──────────────┼─────────┤
│ GitHub Pages │ 100GB BW    │ Docs       │ ⚡ Slow      │ ⭐⭐⭐⭐  │
│              │ 100GB       │ Portfolios │ 1-5 min      │         │
│              │ storage     │ Simple     │              │         │
├──────────────┼─────────────┼────────────┼──────────────┼─────────┤
│ Render       │ Free for    │ Full-stack │ ⚡⚡ Medium  │ ⭐⭐⭐⭐  │
│              │ static      │ Combined   │ 60-180s      │         │
│              │ sites       │ apps       │              │         │
├──────────────┼─────────────┼────────────┼──────────────┼─────────┤
│ Surge        │ Unlimited   │ Quick test │ ⚡⚡⚡⚡ Very │ ⭐⭐⭐   │
│              │ Free        │ prototypes │ <10s         │ Fast    │
│              │             │ CLI deploy │              │         │
└──────────────┴─────────────┴────────────┴──────────────┴─────────┘

DETAILED FEATURE COMPARISON (2025 UPDATE):

┌──────────────┬────────┬────────┬────────┬────────┬────────┐
│ Feature      │ Vercel │ Netlify│ CF Pg  │ GH Pg  │ Render │
├──────────────┼────────┼────────┼────────┼────────┼────────┤
│ Custom Domain│   ✅   │   ✅   │   ✅   │   ✅   │   ✅   │
├──────────────┼────────┼────────┼────────┼────────┼────────┤
│ Auto SSL     │   ✅   │   ✅   │   ✅   │   ✅   │   ✅   │
├──────────────┼────────┼────────┼────────┼────────┼────────┤
│ Git Deploy   │   ✅   │   ✅   │   ✅   │   ✅   │   ✅   │
├──────────────┼────────┼────────┼────────┼────────┼────────┤
│ Preview URLs │   ✅   │   ✅   │   ✅   │   ❌   │   ✅   │
├──────────────┼────────┼────────┼────────┼────────┼────────┤
│ Serverless   │   ✅   │   ✅   │   ✅   │   ❌   │   ✅   │
│ Functions    │        │        │        │        │        │
├──────────────┼────────┼────────┼────────┼────────┼────────┤
│ Forms        │   ❌   │   ✅   │   ❌   │   ❌   │   ❌   │
├──────────────┼────────┼────────┼────────┼────────┼────────┤
│ Analytics    │   ✅   │   ✅   │   ✅   │   ❌   │   ❌   │
├──────────────┼────────┼────────┼────────┼────────┼────────┤
│ Edge Functions│  ✅   │   ✅   │   ✅   │   ❌   │   ❌   │
├──────────────┼────────┼────────┼────────┼────────┼────────┤
│ Build Plugins│   ❌   │   ✅   │   ❌   │   ❌   │   ❌   │
├──────────────┼────────┼────────┼────────┼────────┼────────┤
│ CLI Quality  │  ⭐⭐⭐⭐⭐│ ⭐⭐⭐⭐⭐│  ⭐⭐⭐⭐ │  ⭐⭐⭐  │  ⭐⭐⭐⭐ │
├──────────────┼────────┼────────┼────────┼────────┼────────┤
│ UI/UX        │  ⭐⭐⭐⭐⭐│ ⭐⭐⭐⭐⭐│  ⭐⭐⭐⭐ │  ⭐⭐⭐⭐ │  ⭐⭐⭐⭐ │
└──────────────┴────────┴────────┴────────┴────────┴────────┘

2025 PRICING COMPARISON (HOBBY/FREE TIER):

┌──────────────┬────────────┬─────────────┬──────────────┐
│ Platform     │ Bandwidth  │ Build Min   │ Edge Requests│
├──────────────┼────────────┼─────────────┼──────────────┤
│ Vercel       │ 100GB      │ Unlimited   │ 1M/month     │
├──────────────┼────────────┼─────────────┼──────────────┤
│ Netlify      │ 100GB      │ 300min/mo   │ 1M edge      │
├──────────────┼────────────┼─────────────┼──────────────┤
│ Cloudflare   │ Unlimited  │ 500/month   │ Unlimited    │
├──────────────┼────────────┼─────────────┼──────────────┤
│ GitHub Pages │ 100GB      │ 2,000min/mo │ N/A          │
├──────────────┼────────────┼─────────────┼──────────────┤
│ Render       │ 100GB      │ Free        │ N/A          │
└──────────────┴────────────┴─────────────┴──────────────┘

2025 PRO TIER PRICING:

┌──────────────┬────────────┬─────────────┬──────────────┐
│ Platform     │ Base Price │ Bandwidth   │ Extra Costs  │
├──────────────┼────────────┼─────────────┼──────────────┤
│ Vercel       │ $20/user   │ 1TB         │ $0.15/GB     │
│              │            │             │ $2/M requests│
├──────────────┼────────────┼─────────────┼──────────────┤
│ Netlify      │ $19/member │ 1TB         │ $20/100GB    │
├──────────────┼────────────┼─────────────┼──────────────┤
│ Cloudflare   │ $20/month  │ Unlimited   │ Variable     │
├──────────────┼────────────┼─────────────┼──────────────┤
│ Render       │ $7/service │ 100GB free  │ $15/100GB    │
└──────────────┴────────────┴─────────────┴──────────────┘

RECOMMENDATIONS BY USE CASE:

🎯 Next.js / React / Modern SPA:
   → Vercel (best Next.js support + edge)
   → Netlify (great for all frameworks)

📝 Documentation / Static Blog:
   → GitHub Pages (free, simple)
   → Cloudflare Pages (fast global CDN)

🚀 JAMstack with Headless CMS:
   → Netlify (build plugins, forms)
   → Vercel (edge functions)

🌍 Global Performance Critical:
   → Cloudflare Pages (best CDN, unlimited BW)
   → Vercel (great global performance)

💰 Budget-Conscious:
   → GitHub Pages (100% free forever)
   → Cloudflare Pages (unlimited bandwidth)
   → Surge (simplest free option)

🧪 Quick Testing / Prototypes:
   → Surge (deploy in seconds)
   → Vercel (no config needed)

👨‍💼 Enterprise / Team:
   → Vercel Enterprise ($20k+/year, SLA, SSO)
   → Netlify Enterprise (custom pricing)
   → Cloudflare for Teams

🔧 Full-Stack (Static + Backend):
   → Render (unified platform, $7/service)
   → Vercel (with serverless functions)
```

---

<div align="center">

## ▲ Vercel

**The platform for frontend developers**

</div>

```
🌐 Website → https://vercel.com
🎯 Best For → Next.js, React, Vue, Modern SPAs
💰 Pricing  → Hobby (Free): 100GB BW, 1M edge requests
             Pro: $20/month per user + usage
             Enterprise: Custom ($20k-25k+/year)
⚡ Features → Zero-config, Preview URLs, Edge Functions, Analytics
🔧 Frameworks→ Next.js (best), React, Vue, Svelte, Nuxt, Angular
🆕 2025     → New fluid compute pricing, edge request pricing
```

### 📥 Vercel Setup & Deployment

```bash
# ═══════════════════════════════════════════
# INSTALLATION
# ═══════════════════════════════════════════

# Install Vercel CLI
npm install -g vercel

# Or via pnpm/yarn
pnpm install -g vercel
yarn global add vercel

# Login
vercel login

# ═══════════════════════════════════════════
# DEPLOYMENT
# ═══════════════════════════════════════════

# Deploy (automatic detection)
vercel

# Deploy to production
vercel --prod

# Deploy with custom name
vercel --name my-awesome-site

# Deploy specific folder
vercel ./dist --prod

# ═══════════════════════════════════════════
# PROJECT MANAGEMENT
# ═══════════════════════════════════════════

# List deployments
vercel ls

# List projects
vercel projects ls

# View deployment logs
vercel logs deployment-url

# Remove deployment
vercel rm deployment-url

# Link to existing project
vercel link

# ═══════════════════════════════════════════
# ENVIRONMENT VARIABLES
# ═══════════════════════════════════════════

# Add environment variable
vercel env add API_KEY

# List environment variables
vercel env ls

# Pull environment variables
vercel env pull

# Remove environment variable
vercel env rm API_KEY
```

### 📝 Vercel Configuration (2025 Update)

```json
// ═══════════════════════════════════════════
// vercel.json - Project Configuration
// ═══════════════════════════════════════════

{
  "version": 2,

  // Build configuration
  "buildCommand": "npm run build",
  "outputDirectory": "dist",
  "devCommand": "npm run dev",
  "installCommand": "npm install",

  // Environment variables
  "env": {
    "NEXT_PUBLIC_API_URL": "https://api.example.com"
  },

  // Framework preset (auto-detected)
  "framework": "nextjs",

  // Custom regions (Enterprise only)
  "regions": ["iad1", "sfo1"],

  // Redirects
  "redirects": [
    {
      "source": "/old-page",
      "destination": "/new-page",
      "permanent": true
    },
    {
      "source": "/blog/:slug",
      "destination": "/news/:slug",
      "permanent": false
    }
  ],

  // Rewrites (internal redirects)
  "rewrites": [
    {
      "source": "/api/:path*",
      "destination": "https://api.example.com/:path*"
    }
  ],

  // Headers
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        {
          "key": "X-Content-Type-Options",
          "value": "nosniff"
        },
        {
          "key": "X-Frame-Options",
          "value": "DENY"
        },
        {
          "key": "X-XSS-Protection",
          "value": "1; mode=block"
        }
      ]
    },
    {
      "source": "/api/(.*)",
      "headers": [
        {
          "key": "Access-Control-Allow-Origin",
          "value": "*"
        },
        {
          "key": "Access-Control-Allow-Methods",
          "value": "GET, POST, PUT, DELETE, OPTIONS"
        }
      ]
    }
  ],

  // Custom build configuration
  "build": {
    "env": {
      "NODE_VERSION": "18"
    }
  },

  // Functions configuration (2025 - Fluid Compute)
  "functions": {
    "api/**/*.js": {
      "memory": 1024,
      "maxDuration": 10
    }
  },

  // Clean URLs (remove .html extension)
  "cleanUrls": true,

  // Trailing slash handling
  "trailingSlash": false,

  // Custom error pages
  "routes": [
    { "handle": "filesystem" },
    { "src": "/(.*)", "status": 404, "dest": "/404.html" }
  ]
}
```

### 🆕 2025 Vercel Pricing Changes

```
═══════════════════════════════════════════════════════════
VERCEL 2025 PRICING MODEL (IMPROVED INFRASTRUCTURE)
═══════════════════════════════════════════════════════════

HOBBY (FREE):
┌─────────────────────────────────────────┐
│ Edge Requests: 1M/month                 │
│ Fast Data Transfer: 100GB/month         │
│ Active CPU: 4 hours/month               │
│ Bandwidth: 100GB/month                  │
│ Commercial Use: ❌ NOT ALLOWED          │
│ Team Size: 1 person only                │
└─────────────────────────────────────────┘

PRO ($20/user/month):
┌─────────────────────────────────────────┐
│ Edge Requests: 10M/month included       │
│ Fast Data Transfer: 1TB/month           │
│ Active CPU: 40 hours/month              │
│ Function Invocations: 1M/month          │
│ Commercial Use: ✅ ALLOWED              │
│ Team Seats: $20 per additional user     │
└─────────────────────────────────────────┘

OVERAGE PRICING (PRO):
• Edge Requests: $2 per 1M requests
• Fast Data Transfer: $0.15/GB
• Fast Origin Transfer: $0.06/GB
• ISR Cache Reads: $0.40 per 1M
• ISR Cache Writes: $4.00 per 1M
• Image Optimization: $0.05 per 1K transformations
• Function Duration: $0.128 per CPU hour

ENTERPRISE (Custom Pricing):
• Starts at ~$20,000-25,000/year
• Custom bandwidth limits
• SSO/SAML ($300/month add-on)
• HIPAA BAA ($350/month add-on)
• 99.99% SLA guarantee
• Dedicated support manager
• Advanced security features

IMPORTANT 2025 CHANGES:
⚠️  Edge Requests now counted separately
⚠️  ISR split into Cache Reads/Writes
⚠️  New "Fluid Compute" active CPU pricing
⚠️  Bandwidth split: Edge vs Origin Transfer
⚠️  Free tier: No commercial use allowed!

COST OPTIMIZATION TIPS (2025):
✅ Use external CDN (Bunny, Cloudflare) for static assets
✅ Reduce Edge Requests (~25 → 10 per page possible)
✅ Monitor ISR cache usage carefully
✅ Use proper caching strategies
✅ Consider hybrid deployment for high traffic
```

### 💡 Vercel Pro Tips (2025 Update)

```bash
# ═══════════════════════════════════════════
# COST OPTIMIZATION (CRITICAL FOR 2025!)
# ═══════════════════════════════════════════

# Problem: Edge Requests add up FAST
# A typical homepage: 25+ edge requests
# - JS chunks (5-10 requests)
# - CSS files (2-3 requests)
# - Images (5-10 requests)
# - Fonts (2-4 requests)
# - Prefetch requests (3-5 requests)

# Solution: Use external CDN for static assets
# Result: 25 → 10 edge requests per page

# Setup with Bunny CDN (recommended):
# 1. Sign up: https://bunny.net
# 2. Create Pull Zone: origin = vercel.app
# 3. Update next.config.js:

// next.config.js
module.exports = {
  assetPrefix: process.env.NODE_ENV === 'production'
    ? 'https://static.example.com'
    : '',

  // Update CSP if you use it
  async headers() {
    return [
      {
        source: '/:path*',
        headers: [
          {
            key: 'Content-Security-Policy',
            value: `script-src 'self' 'unsafe-eval' 'unsafe-inline' https://static.example.com;`
          }
        ]
      }
    ]
  }
}

# Cost Comparison (1M page views):
# Without CDN: 25M edge requests = $30/month extra
# With CDN: 10M edge requests = $0 (within free tier)
# CDN cost (Bunny): ~$1-2/month
# SAVINGS: ~$28/month or $336/year!

# ═══════════════════════════════════════════
# PREVIEW DEPLOYMENTS
# ═══════════════════════════════════════════

# Every Git branch gets a preview URL automatically
# Example: feature-branch-abc123.vercel.app

# Comment on PR with deployment link
# Automatic visual regression testing (with integrations)

# Environment variables for preview:
# VERCEL_ENV = "preview"
# VERCEL_URL = "preview-url.vercel.app"

# ═══════════════════════════════════════════
# PERFORMANCE MONITORING
# ═══════════════════════════════════════════

# Vercel Analytics (built-in)
import { Analytics } from '@vercel/analytics/react';

export default function App({ Component, pageProps }) {
  return (
    <>
      <Component {...pageProps} />
      <Analytics />
    </>
  );
}

# Speed Insights
import { SpeedInsights } from "@vercel/speed-insights/next";

export default function RootLayout({ children }) {
  return (
    <html lang="en">
      <body>
        {children}
        <SpeedInsights />
      </body>
    </html>
  );
}

# ═══════════════════════════════════════════
# EDGE FUNCTIONS (2025 UPDATE)
# ═══════════════════════════════════════════

// app/api/edge/route.ts
export const runtime = 'edge';

export async function GET(request: Request) {
  return new Response('Hello from the edge!', {
    headers: {
      'content-type': 'text/plain',
    },
  });
}

// Middleware (runs on all requests)
// middleware.ts
import { NextResponse } from 'next/server';
import type { NextRequest } from 'next/server';

export function middleware(request: NextRequest) {
  // Add custom header
  const response = NextResponse.next();
  response.headers.set('x-custom-header', 'my-value');

  // Geo-based redirect
  const country = request.geo?.country;
  if (country === 'US') {
    return NextResponse.redirect(new URL('/us', request.url));
  }

  return response;
}

export const config = {
  matcher: '/:path*',
};

# ═══════════════════════════════════════════
# MONITORING USAGE TO AVOID SURPRISES
# ═══════════════════════════════════════════

# Dashboard → Analytics → Usage
# Watch these metrics:
# 1. Edge Requests (biggest cost driver)
# 2. Fast Data Transfer
# 3. Function Duration
# 4. ISR Cache Operations

# Set up usage alerts:
# Settings → Usage Alerts
# Example: Alert at 80% of monthly quota

# ═══════════════════════════════════════════
# OPTIMIZATION TIPS
# ═══════════════════════════════════════════

# 1. Use Image Optimization
import Image from 'next/image';

<Image
  src="/photo.jpg"
  alt="Photo"
  width={500}
  height={300}
  priority
/>

# 2. Enable ISR (Incremental Static Regeneration)
export async function generateStaticParams() {
  return [{ slug: 'post-1' }, { slug: 'post-2' }];
}

export const revalidate = 60; // Revalidate every 60 seconds

# 3. Use dynamic imports for code splitting
import dynamic from 'next/dynamic';

const DynamicComponent = dynamic(() => import('../components/Heavy'), {
  loading: () => <p>Loading...</p>,
  ssr: false,
});

# 4. Optimize fonts
import { Inter } from 'next/font/google';

const inter = Inter({ subsets: ['latin'] });

# 5. Monitor with Vercel Analytics (free!)
# Real Experience Score (RES) tracking included
```

### ⚠️ Vercel Limitations & When to Consider Alternatives

```
═══════════════════════════════════════════════════════════
WHEN VERCEL MIGHT NOT BE THE BEST CHOICE
═══════════════════════════════════════════════════════════

❌ HIGH TRAFFIC APPS:
Problem: Edge requests add up fast
Example: 500K monthly visitors = $2,000+/month
Alternative: Self-host on AWS/DigitalOcean (~$50/month)
             Or use Cloudflare Pages (unlimited bandwidth)

❌ COMPLEX BACKEND NEEDS:
Problem: Serverless functions have limits
- Max duration: 10s (Hobby), 15min (Pro)
- No persistent connections (WebSockets)
- No background jobs
Alternative: Render, Railway, Fly.io for full backend

❌ BUDGET CONSTRAINTS:
Problem: Costs scale with usage unpredictably
Example: Viral marketing campaign = surprise $500 bill
Alternative: GitHub Pages (free), Netlify (predictable)

❌ NEED FULL INFRASTRUCTURE CONTROL:
Problem: Can't customize network, install system libs
Alternative: VPS (DigitalOcean), AWS EC2

✅ VERCEL IS PERFECT FOR:
• Next.js applications (best-in-class support)
• Modern React/Vue SPAs
• Static sites with occasional dynamic content
• Teams that value DX over infrastructure control
• Projects with moderate, predictable traffic
• Rapid prototyping and MVP launches

MIGRATION STORIES (REAL EXAMPLES FROM 2024-2025):
• Showzone: $800/month → $40/month (moved to Render)
• Various startups moving to self-hosted after Series A
• Enterprise clients paying $20k+/year for SSO/compliance

💡 HYBRID APPROACH (BEST OF BOTH WORLDS):
• Frontend on Vercel (fast, global CDN)
• Backend on Render/Railway ($7-20/month)
• Static assets on Bunny CDN ($1-2/month)
• Total cost: $30-50/month for high-traffic apps
```

---

<div align="center">

## 🌐 Netlify

**All-in-one platform for modern web projects**

</div>

🌐 Website → https://netlify.com
🎯 Best For → JAMstack, headless CMS, forms, serverless
💰 Pricing → Free: 100GB bandwidth, 300 build minutes/month
Pro: $19/month per member
Enterprise: Custom pricing
⚡ Features → Build plugins, Forms, Split testing, Edge functions
🔧 Frameworks→ All static site generators, React, Vue, Angular
🆕 2025 → Enhanced edge functions, improved build times

### 📥 Netlify Setup & Deployment

```bash
# ═══════════════════════════════════════════
# INSTALLATION
# ═══════════════════════════════════════════

# Install Netlify CLI
npm install -g netlify-cli

# Login
netlify login

# ═══════════════════════════════════════════
# DEPLOYMENT
# ═══════════════════════════════════════════

# Initialize new site
netlify init

# Deploy (preview)
netlify deploy

# Deploy to production
netlify deploy --prod

# Deploy specific directory
netlify deploy --dir=dist --prod

# ═══════════════════════════════════════════
# SITE MANAGEMENT
# ═══════════════════════════════════════════

# List sites
netlify sites:list

# Open site in browser
netlify open

# View site info
netlify status

# Link to existing site
netlify link

# Unlink site
netlify unlink

# ═══════════════════════════════════════════
# FUNCTIONS & DEV
# ═══════════════════════════════════════════

# Create new function
netlify functions:create

# Run dev server (with functions)
netlify dev

# Test functions locally
netlify functions:invoke function-name

# ═══════════════════════════════════════════
# ENVIRONMENT VARIABLES
# ═══════════════════════════════════════════

# Set environment variable
netlify env:set API_KEY your-key-here

# List environment variables
netlify env:list

# Get variable value
netlify env:get API_KEY

# Import from .env file
netlify env:import .env
```

### 📝 Netlify Configuration (2025 Update)

```toml
# ═══════════════════════════════════════════
# netlify.toml - Site Configuration
# ═══════════════════════════════════════════

[build]
  # Build command
  command = "npm run build"

  # Publish directory
  publish = "dist"

  # Functions directory
  functions = "netlify/functions"

  # Base directory (for monorepos)
  base = "packages/frontend"

  # Environment variables
  environment = { NODE_VERSION = "18", NODE_ENV = "production" }

# Build processing
[build.processing]
  skip_processing = false

[build.processing.css]
  bundle = true
  minify = true

[build.processing.js]
  bundle = true
  minify = true

[build.processing.html]
  pretty_urls = true

[build.processing.images]
  compress = true

# ═══════════════════════════════════════════
# REDIRECTS
# ═══════════════════════════════════════════

[[redirects]]
  from = "/old-path"
  to = "/new-path"
  status = 301
  force = true

[[redirects]]
  from = "/blog/*"
  to = "/news/:splat"
  status = 301

# Proxy (rewrite without changing URL)
[[redirects]]
  from = "/api/*"
  to = "https://api.example.com/:splat"
  status = 200
  force = true

# SPA fallback (important for React Router, etc.)
[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200

# Redirect by country (2025 feature)
[[redirects]]
  from = "/"
  to = "/us"
  status = 302
  conditions = {Country = ["US"]}

# Redirect by language
[[redirects]]
  from = "/"
  to = "/es"
  status = 302
  conditions = {Language = ["es"]}

# ═══════════════════════════════════════════
# HEADERS
# ═══════════════════════════════════════════

[[headers]]
  for = "/*"
  [headers.values]
    X-Frame-Options = "DENY"
    X-XSS-Protection = "1; mode=block"
    X-Content-Type-Options = "nosniff"
    Referrer-Policy = "strict-origin-when-cross-origin"

[[headers]]
  for = "/assets/*"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

[[headers]]
  for = "/*.js"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

[[headers]]
  for = "/*.css"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

[[headers]]
  for = "/*.woff2"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

# ═══════════════════════════════════════════
# FORMS (Built-in Feature!)
# ═══════════════════════════════════════════

# No configuration needed! Just add netlify attribute
# <form name="contact" method="POST" data-netlify="true">

# ═══════════════════════════════════════════
# PLUGINS (2025 UPDATE)
# ═══════════════════════════════════════════

[[plugins]]
  package = "@netlify/plugin-sitemap"

[[plugins]]
  package = "netlify-plugin-lighthouse"

  [plugins.inputs]
    thresholds.performance = 0.9
    thresholds.accessibility = 0.9

[[plugins]]
  package = "@netlify/plugin-nextjs"

[[plugins]]
  package = "netlify-plugin-checklinks"

# ═══════════════════════════════════════════
# CONTEXT-SPECIFIC CONFIG
# ═══════════════════════════════════════════

# Production-specific
[context.production]
  command = "npm run build:prod"

[context.production.environment]
  NODE_ENV = "production"
  REACT_APP_API_URL = "https://api.example.com"

# Deploy preview-specific
[context.deploy-preview]
  command = "npm run build:preview"

[context.deploy-preview.environment]
  REACT_APP_API_URL = "https://api-staging.example.com"

# Branch-specific
[context.staging]
  command = "npm run build:staging"
  base = "staging-branch"

# ═══════════════════════════════════════════
# EDGE FUNCTIONS (2025 - Enhanced)
# ═══════════════════════════════════════════

[[edge_functions]]
  function = "hello"
  path = "/api/hello"

[[edge_functions]]
  function = "auth"
  path = "/admin/*"
```

### 🎯 Netlify Features (2025 Update)

```javascript
// ═══════════════════════════════════════════
// NETLIFY FORMS
// ═══════════════════════════════════════════

// Simple form (HTML)
<form name="contact" method="POST" data-netlify="true">
  <input type="hidden" name="form-name" value="contact" />
  <p>
    <label>Name: <input type="text" name="name" required /></label>
  </p>
  <p>
    <label>Email: <input type="email" name="email" required /></label>
  </p>
  <p>
    <label>Message: <textarea name="message" required></textarea></label>
  </p>
  <p>
    <button type="submit">Send</button>
  </p>
</form>

// React form with reCAPTCHA
import React, { useState } from 'react';

function ContactForm() {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    message: ''
  });

  const handleSubmit = async (e) => {
    e.preventDefault();

    const form = e.target;
    const data = new FormData(form);

    try {
      await fetch('/', {
        method: 'POST',
        headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
        body: new URLSearchParams(data).toString()
      });
      alert('Form submitted!');
    } catch (error) {
      alert('Error submitting form');
    }
  };

  return (
    <form
      name="contact"
      method="POST"
      data-netlify="true"
      data-netlify-recaptcha="true"
      onSubmit={handleSubmit}
    >
      <input type="hidden" name="form-name" value="contact" />

      <input
        type="text"
        name="name"
        value={formData.name}
        onChange={(e) => setFormData({...formData, name: e.target.value})}
        required
      />

      <input
        type="email"
        name="email"
        value={formData.email}
        onChange={(e) => setFormData({...formData, email: e.target.value})}
        required
      />

      <textarea
        name="message"
        value={formData.message}
        onChange={(e) => setFormData({...formData, message: e.target.value})}
        required
      />

      <div data-netlify-recaptcha="true"></div>

      <button type="submit">Send</button>
    </form>
  );
}

// ═══════════════════════════════════════════
// NETLIFY FUNCTIONS (Serverless)
// ═══════════════════════════════════════════

// netlify/functions/hello.js
exports.handler = async (event, context) => {
  return {
    statusCode: 200,
    body: JSON.stringify({ message: 'Hello from Netlify!' })
  };
};

// With query parameters
exports.handler = async (event, context) => {
  const { name = 'World' } = event.queryStringParameters || {};

  return {
    statusCode: 200,
    headers: {
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({ message: `Hello, ${name}!` })
  };
};

// POST request handler
exports.handler = async (event, context) => {
  if (event.httpMethod !== 'POST') {
    return { statusCode: 405, body: 'Method Not Allowed' };
  }

  const data = JSON.parse(event.body);

  // Process data

  return {
    statusCode: 200,
    body: JSON.stringify({ success: true, data })
  };
};

// Background function (TypeScript) - 2025 feature
// netlify/functions/background.ts
import type { Handler } from '@netlify/functions';

export const handler: Handler = async (event, context) => {
  // Long-running task (up to 15 minutes)
  await processLargeDataset();

  return {
    statusCode: 200,
    body: JSON.stringify({ status: 'Processing started' })
  };
};

// ═══════════════════════════════════════════
// NETLIFY EDGE FUNCTIONS (2025 - Enhanced)
// ═══════════════════════════════════════════

// netlify/edge-functions/hello.ts
export default async (request: Request) => {
  return new Response('Hello from the edge!', {
    headers: {
      'content-type': 'text/plain',
    },
  });
};

// With Netlify context
import type { Context } from "https://edge.netlify.com";

export default async (request: Request, context: Context) => {
  // Access geolocation
  const { city, country } = context.geo;

  return new Response(`Hello from ${city}, ${country}!`);
};

// ═══════════════════════════════════════════
// NETLIFY IDENTITY (Authentication)
// ═══════════════════════════════════════════

// Enable in Netlify UI: Site settings → Identity

// Install netlify-identity-widget
import netlifyIdentity from 'netlify-identity-widget';

// Initialize
netlifyIdentity.init();

// Login
netlifyIdentity.open('login');

// Signup
netlifyIdentity.open('signup');

// Get current user
const user = netlifyIdentity.currentUser();

// Listen to auth events
netlifyIdentity.on('login', (user) => {
  console.log('User logged in:', user);
});

netlifyIdentity.on('logout', () => {
  console.log('User logged out');
});

// Protected function
// netlify/functions/protected.js
exports.handler = async (event, context) => {
  const { user } = context.clientContext;

  if (!user) {
    return {
      statusCode: 401,
      body: JSON.stringify({ error: 'Not authenticated' })
    };
  }

  return {
    statusCode: 200,
    body: JSON.stringify({ message: `Hello, ${user.email}!` })
  };
};
```

### 💡 Netlify Pro Tips (2025 Update)

```bash
# ═══════════════════════════════════════════
# BUILD PLUGINS (2025 - More Powerful!)
# ═══════════════════════════════════════════

# Install plugins in netlify.toml
[[plugins]]
  package = "@netlify/plugin-lighthouse"

  [plugins.inputs]
    thresholds.performance = 0.9
    thresholds.accessibility = 0.9

[[plugins]]
  package = "netlify-plugin-checklinks"

[[plugins]]
  package = "@netlify/plugin-sitemap"

# Create custom plugin
# netlify/plugins/my-plugin/index.js
module.exports = {
  onPreBuild: async ({ utils }) => {
    console.log('Running before build');
  },

  onBuild: async ({ utils }) => {
    console.log('Running during build');
  },

  onPostBuild: async ({ utils }) => {
    console.log('Running after build');
  },

  onSuccess: async ({ utils }) => {
    console.log('Build succeeded!');
  },

  onError: async ({ utils }) => {
    console.log('Build failed!');
  }
};

# ═══════════════════════════════════════════
# SPLIT TESTING (A/B TESTING)
# ═══════════════════════════════════════════

# Deploy multiple branches
# Site settings → Build & deploy → Branch deploys

# Configure split test
# Site settings → Split testing
# Split traffic between branches: 50% main, 50% feature

# ═══════════════════════════════════════════
# LARGE MEDIA (Git LFS)
# ═══════════════════════════════════════════

# Install Git LFS
brew install git-lfs
git lfs install

# Track large files
git lfs track "*.psd"
git lfs track "*.mp4"

# Install Netlify Large Media
netlify lm:install

# Enable transforms
netlify lm:setup

# Use in HTML
<img src="/image.jpg?nf_resize=fit&w=400" />

# ═══════════════════════════════════════════
# SNIPPET INJECTION
# ═══════════════════════════════════════════

# Inject scripts before </head> or </body>
# Site settings → Build & deploy → Post processing → Snippet injection

# Example: Add analytics
<script>
  // Your analytics code
</script>

# ═══════════════════════════════════════════
# DEPLOY NOTIFICATIONS (2025 - Enhanced)
# ═══════════════════════════════════════════

# Site settings → Build & deploy → Deploy notifications
# - Slack
# - Email
# - Webhook
# - GitHub commit status
# - Discord (new in 2025)

# Webhook example
curl -X POST https://your-webhook.com/deploy \
  -H "Content-Type: application/json" \
  -d '{"status": "success", "url": "https://site.netlify.app"}'

# ═══════════════════════════════════════════
# NETLIFY VS VERCEL - KEY DIFFERENCES (2025)
# ═══════════════════════════════════════════

NETLIFY ADVANTAGES:
✅ Built-in forms (no external service needed)
✅ More predictable pricing ($19/user vs $20/user)
✅ Bandwidth overage: $20/100GB vs Vercel's $40/100GB
✅ Better for non-Next.js frameworks
✅ Build plugins ecosystem
✅ Split testing built-in
✅ Identity/Auth built-in

VERCEL ADVANTAGES:
✅ Best Next.js integration
✅ Better edge function performance
✅ Faster deployment times
✅ Better analytics (built-in Web Vitals)
✅ More modern developer experience
✅ Better for serverless-heavy apps

WHEN TO CHOOSE NETLIFY:
• JAMstack sites with forms
• Multiple framework projects
• Need A/B testing
• Budget-conscious (more predictable costs)
• Need built-in authentication

WHEN TO CHOOSE VERCEL:
• Next.js applications
• Edge-first architecture
• Need best-in-class DX
• Performance-critical apps
```

---

<div align="center">

## 🐙 GitHub Pages

**Free hosting directly from your GitHub repository**

</div>

```
🌐 Website → https://pages.github.com
🎯 Best For → Documentation, portfolios, project sites, open source
💰 Pricing  → 100% Free (public repos), GitHub Pro for private repos
⚡ Features → Jekyll integration, Custom domains, HTTPS, 100GB/month BW
🔧 Frameworks→ Static HTML, Jekyll, any static site generator
🆕 2025     → GitHub Actions integration, faster builds
```

### 📥 GitHub Pages Setup (2025 Update)

```bash
# ═══════════════════════════════════════════
# METHOD 1: GITHUB ACTIONS (MODERN - RECOMMENDED)
# ═══════════════════════════════════════════

# 1. Enable GitHub Pages in repo settings
# Settings → Pages → Source → GitHub Actions

# 2. Create workflow file
# .github/workflows/deploy.yml

name: Deploy to GitHub Pages

on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'

      - name: Install dependencies
        run: npm ci

      - name: Build
        run: npm run build
        env:
          NODE_ENV: production

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./dist

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4

# ═══════════════════════════════════════════
# METHOD 2: GH-PAGES NPM PACKAGE
# ═══════════════════════════════════════════

# Install
npm install --save-dev gh-pages

# Add to package.json
{
  "homepage": "https://username.github.io/repo-name",
  "scripts": {
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build"
  }
}

# Deploy
npm run deploy

# ═══════════════════════════════════════════
# METHOD 3: JEKYLL (CLASSIC)
# ═══════════════════════════════════════════

# 1. Create _config.yml
title: My Site
description: My awesome site
baseurl: "" # Empty for user/org pages, /repo-name for project pages
url: "https://username.github.io"
theme: minima

# 2. Push to GitHub
git add .
git commit -m "Initial commit"
git push origin main

# 3. Enable Pages in settings
# Settings → Pages → Source → Deploy from branch → main → / (root)

# ═══════════════════════════════════════════
# CUSTOM DOMAIN (2025 - Improved Process)
# ═══════════════════════════════════════════

# 1. Add CNAME file to repository root
echo "www.example.com" > CNAME

# 2. Configure DNS (at your domain provider)
# For apex domain (example.com):
# A records pointing to (2025 IPs):
# 185.199.108.153
# 185.199.109.153
# 185.199.110.153
# 185.199.111.153

# For www subdomain:
# CNAME record: www → username.github.io

# 3. Enable in GitHub
# Settings → Pages → Custom domain → Save

# 4. Enable HTTPS (automatic after DNS propagates)
# ✅ Enforce HTTPS checkbox
```

### 📝 GitHub Pages Configuration (2025)

```yaml
# ═══════════════════════════════════════════
# _config.yml - Jekyll Configuration
# ═══════════════════════════════════════════

# Site settings
title: My Awesome Site
description: >-
  Write an awesome description for your site here.
baseurl: "" # Subpath, e.g., /blog
url: "https://username.github.io"

# Build settings
markdown: kramdown
theme: minima

# Plugins (supported by GitHub Pages)
plugins:
  - jekyll-feed
  - jekyll-seo-tag
  - jekyll-sitemap
  - jekyll-github-metadata
  - jekyll-avatar
  - jemoji

# Exclude files
exclude:
  - Gemfile
  - Gemfile.lock
  - node_modules
  - vendor
  - README.md
  - package.json
  - package-lock.json

# Include files
include:
  - _pages

# Permalink structure
permalink: /:categories/:year/:month/:day/:title/

# Collections
collections:
  projects:
    output: true
    permalink: /projects/:name

# Defaults
defaults:
  - scope:
      path: ""
      type: "posts"
    values:
      layout: "post"
      author: "Your Name"
  - scope:
      path: ""
      type: "pages"
    values:
      layout: "default"
```

```html
<!-- ═══════════════════════════════════════════ -->
<!-- Jekyll Template Example -->
<!-- ═══════════════════════════════════════════ -->

<!-- _layouts/default.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>{{ page.title }} - {{ site.title }}</title>
    <link
      rel="stylesheet"
      href="{{ '/assets/css/style.css' | relative_url }}"
    />
    {% seo %}
  </head>
  <body>
    {% include header.html %}

    <main>{{ content }}</main>

    {% include footer.html %}
  </body>
</html>

<!-- _posts/2025-01-01-my-post.md -->
--- layout: post title: "My First Post" date: 2025-01-01 12:00:00 +0000
categories: blog tags: [web, development] --- # Welcome This is my first post on
GitHub Pages! {{ site.title }} {{ page.title }}
```

### 💡 GitHub Pages Pro Tips (2025)

```bash
# ═══════════════════════════════════════════
# OPTIMIZATION (2025 BEST PRACTICES)
# ═══════════════════════════════════════════

# 1. Use GitHub Actions for any framework
# - React, Vue, Angular, Svelte
# - Eleventy, Astro, Hugo
# - Custom build process

# Example: Deploy Vite app
# .github/workflows/deploy.yml
name: Deploy Vite App

on:
  push:
    branches: [main]

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
      - run: npm ci
      - run: npm run build
      - uses: actions/upload-pages-artifact@v3
        with:
          path: dist
      - uses: actions/deploy-pages@v4

# 2. Leverage GitHub's CDN
# Files are automatically distributed globally

# 3. Use relative URLs
# Works for both custom domains and github.io URLs
<a href="{{ '/about/' | relative_url }}">About</a>

# 4. Optimize images
# Use responsive images
<img
  src="image.jpg"
  srcset="image-400w.jpg 400w, image-800w.jpg 800w"
  sizes="(max-width: 600px) 400px, 800px"
  alt="Description"
/>

# 5. Add 404 page
# Create 404.html or 404.md in root

# 6. Use Jekyll plugins (GitHub Pages supported)
# In _config.yml:
plugins:
  - jekyll-seo-tag        # SEO optimization
  - jekyll-sitemap        # Auto-generate sitemap
  - jekyll-feed          # RSS feed
  - jekyll-github-metadata # Access repo data
  - jemoji               # Emoji support 🎉

# ═══════════════════════════════════════════
# LIMITATIONS & WORKAROUNDS (2025 UPDATE)
# ═══════════════════════════════════════════

# Limitations:
# - No server-side processing
# - No environment variables (use build-time)
# - 1GB repository size limit
# - 100GB bandwidth/month (soft limit)
# - 10 builds/hour (increased from previous)
# - Deploy time: 1-5 minutes (slower than Vercel/Netlify)

# Workarounds:
# - Use GitHub Actions for builds
# - Use external APIs for dynamic content
# - Use client-side JavaScript for interactivity
# - Use GitHub Secrets for build-time secrets
# - For high traffic: Use Cloudflare in front

# ═══════════════════════════════════════════
# LOCAL TESTING (2025)
# ═══════════════════════════════════════════

# Install Jekyll
gem install bundler jekyll

# Create Gemfile
source 'https://rubygems.org'
gem 'github-pages', group: :jekyll_plugins

# Install dependencies
bundle install

# Run locally
bundle exec jekyll serve

# Open http://localhost:4000

# Live reload (2025 feature)
bundle exec jekyll serve --livereload

# ═══════════════════════════════════════════
# ADVANCED: MULTIPLE SITES FROM ONE REPO
# ═══════════════════════════════════════════

# Use different branches for different sites
# main branch → username.github.io
# docs branch → username.github.io/docs

# Or use GitHub Actions to deploy to different repos

# ═══════════════════════════════════════════
# GITHUB PAGES VS ALTERNATIVES (2025)
# ═══════════════════════════════════════════

✅ GITHUB PAGES WINS:
• 100% free forever
• No build minute limits
• Integrated with GitHub workflow
• Perfect for documentation
• Great for open source projects

❌ GITHUB PAGES LOSES:
• Slower deploy times (1-5 min vs 30s)
• No preview deployments
• No serverless functions
• Limited to static content
• No advanced edge features

BEST USE CASES:
• Open source project documentation
• Personal portfolios
• GitHub organization sites
• Educational projects
• Static blogs
```

---

<div align="center">

## ☁️ Cloudflare Pages

**Deploy to the Cloudflare edge network**

</div>

```
🌐 Website → https://pages.cloudflare.com
🎯 Best For → Global CDN, edge functions, unlimited bandwidth
💰 Pricing  → Free: Unlimited requests, 500 builds/month
             Paid: $20/month for 5,000 builds, advanced features
⚡ Features → Edge functions, Web Analytics, unlimited bandwidth
🔧 Frameworks→ All static frameworks, SSR with Workers
🆕 2025     → Enhanced Workers integration, better build times
```

### 📥 Cloudflare Pages Setup

```bash
# ═══════════════════════════════════════════
# DEPLOYMENT VIA UI (RECOMMENDED)
# ═══════════════════════════════════════════

# 1. Go to pages.cloudflare.com
# 2. Connect Git provider (GitHub/GitLab)
# 3. Select repository
# 4. Configure build settings:
#    - Build command: npm run build
#    - Build output directory: dist
#    - Root directory: (leave blank or specify)
# 5. Deploy!

# ═══════════════════════════════════════════
# WRANGLER CLI (ADVANCED - 2025 UPDATE)
# ═══════════════════════════════════════════

# Install Wrangler
npm install -g wrangler

# Login
wrangler login

# Initialize Pages project
wrangler pages project create my-project

# Deploy
wrangler pages publish dist

# Deploy with custom project
wrangler pages publish dist --project-name=my-site

# Deploy with environment
wrangler pages publish dist --branch=production

# ═══════════════════════════════════════════
# DIRECT UPLOAD (NO GIT)
# ═══════════════════════════════════════════

# Build your site
npm run build

# Upload via drag & drop in Cloudflare dashboard
# Or use Wrangler CLI
wrangler pages publish ./dist

# Useful for:
# - CI/CD from non-GitHub sources
# - Local development deployment
# - Manual deployments
```

### 📝 Cloudflare Pages Configuration (2025)

```toml
# ═══════════════════════════════════════════
# wrangler.toml (optional - for advanced config)
# ═══════════════════════════════════════════

name = "my-site"
compatibility_date = "2025-01-01"

[site]
bucket = "./dist"

# Environment variables
[env.production]
name = "my-site"
vars = { ENVIRONMENT = "production", API_URL = "https://api.example.com" }

[env.preview]
name = "my-site-preview"
vars = { ENVIRONMENT = "preview", API_URL = "https://api-staging.example.com" }

# Build configuration
[build]
command = "npm run build"
cwd = "."
watch_dirs = ["src"]

# KV Namespaces (2025 feature)
[[kv_namespaces]]
binding = "MY_KV"
id = "your-kv-namespace-id"

# D1 Database (2025 feature)
[[d1_databases]]
binding = "DB"
database_name = "my-database"
database_id = "your-database-id"

# R2 Storage (2025 feature)
[[r2_buckets]]
binding = "MY_BUCKET"
bucket_name = "my-bucket"
```

```javascript
// ═══════════════════════════════════════════
// _headers - Custom Headers
// ═══════════════════════════════════════════

// Place in project root or output directory

/*
  X-Frame-Options: DENY
  X-Content-Type-Options: nosniff
  X-XSS-Protection: 1; mode=block
  Referrer-Policy: strict-origin-when-cross-origin

/assets/*
  Cache-Control: public, max-age=31536000, immutable

/*.js
  Cache-Control: public, max-age=31536000, immutable

/*.css
  Cache-Control: public, max-age=31536000, immutable

// ═══════════════════════════════════════════
// _redirects - URL Redirects
// ═══════════════════════════════════════════

# Redirect with status code
/old-page /new-page 301

# Redirect with splat
/blog/* /news/:splat 301

# Proxy (don't change URL)
/api/* https://api.example.com/:splat 200

# SPA fallback
/* /index.html 200

# Country-based redirect (2025 feature)
/ /us 302 Country=US
/ /uk 302 Country=GB

// ═══════════════════════════════════════════
// CLOUDFLARE PAGES FUNCTIONS (2025 - Enhanced)
// ═══════════════════════════════════════════

// functions/api/hello.js
export async function onRequest(context) {
  return new Response('Hello from Cloudflare!');
}

// With different HTTP methods
// functions/api/users.js
export async function onRequestGet(context) {
  return Response.json({ users: [] });
}

export async function onRequestPost(context) {
  const data = await context.request.json();
  return Response.json({ success: true, data });
}

// Middleware
// functions/_middleware.js
export async function onRequest(context) {
  // Add custom header
  const response = await context.next();
  response.headers.set('X-Custom-Header', 'value');
  return response;
}

// Advanced example with KV (2025)
// functions/api/data.js
export async function onRequest(context) {
  const { env } = context;

  // Access KV namespace
  const value = await env.MY_KV.get('key');

  return Response.json({ value });
}

// With D1 Database (2025 feature)
// functions/api/posts.js
export async function onRequest(context) {
  const { env } = context;

  // Query D1 database
  const { results } = await env.DB.prepare(
    'SELECT * FROM posts ORDER BY created_at DESC LIMIT 10'
  ).all();

  return Response.json({ posts: results });
}

// ═══════════════════════════════════════════
// CLOUDFLARE WORKERS (Advanced - 2025)
// ═══════════════════════════════════════════

// _worker.js in project root
export default {
  async fetch(request, env) {
    const url = new URL(request.url);

    // Custom routing
    if (url.pathname.startsWith('/api')) {
      return handleApi(request, env);
    }

    // A/B testing with edge logic
    if (url.pathname === '/') {
      const variant = Math.random() < 0.5 ? 'a' : 'b';
      return env.ASSETS.fetch(new Request(`/${variant}.html`));
    }

    // Serve static assets
    return env.ASSETS.fetch(request);
  }
};

async function handleApi(request, env) {
  // Your API logic here
  return new Response('API response');
}
```

### 💡 Cloudflare Pages Pro Tips (2025)

```bash
# ═══════════════════════════════════════════
# PERFORMANCE FEATURES (2025 UPDATE)
# ═══════════════════════════════════════════

# 1. Automatic image optimization
# Images served via Cloudflare CDN are automatically optimized
# - WebP/AVIF conversion
# - Responsive sizing
# - Lazy loading

# 2. Brotli compression
# Automatically enabled for all assets

# 3. HTTP/2 and HTTP/3
# Enabled by default for better performance

# 4. Edge caching
# Static assets cached globally at 300+ locations (2025)

# 5. Zero cold starts
# Unlike Vercel/Netlify functions, Workers are instant

# ═══════════════════════════════════════════
# ANALYTICS (2025 - FREE!)
# ═══════════════════════════════════════════

# Free Web Analytics (privacy-friendly, no cookies)
# Enable in Cloudflare dashboard

# Add to your HTML (optional - automatic tracking)
<script defer src='https://static.cloudflareinsights.com/beacon.min.js'
        data-cf-beacon='{"token": "your-token"}'></script>

# Features:
# - Page views
# - Unique visitors
# - Popular pages
# - Referrers
# - Countries
# - Devices/Browsers

# ═══════════════════════════════════════════
# PREVIEW DEPLOYMENTS (2025)
# ═══════════════════════════════════════════

# Every Git branch gets a preview URL
# https://branch-name.your-project.pages.dev

# Pull requests get unique URLs
# https://pr-123.your-project.pages.dev

# Preview URL naming format (2025):
# https://<hash>.<project-name>.pages.dev

# ═══════════════════════════════════════════
# CUSTOM DOMAINS (2025 - SIMPLIFIED)
# ═══════════════════════════════════════════

# Add custom domain in dashboard
# Pages → Your Project → Custom domains

# DNS setup (if domain on Cloudflare):
# Automatic CNAME record created ✨

# DNS setup (external provider):
# CNAME: www → your-project.pages.dev
# Or use Cloudflare nameservers (recommended)

# Benefits of Cloudflare DNS:
# - Faster propagation
# - Automatic SSL
# - DDoS protection
# - Argo Smart Routing

# ═══════════════════════════════════════════
# CLOUDFLARE PAGES VS COMPETITORS (2025)
# ═══════════════════════════════════════════

✅ CLOUDFLARE PAGES WINS:
• Unlimited bandwidth (biggest advantage!)
• 300+ global locations
• Free Web Analytics
• Zero cold starts for functions
• Best DDoS protection
• Fastest DNS
• Most generous free tier

❌ CLOUDFLARE PAGES LOSES:
• Slower build times (60-120s vs Vercel's 30s)
• Less mature than Vercel/Netlify
• Fewer integrations
• UI not as polished
• Documentation less comprehensive

PERFECT FOR:
• High-traffic sites (unlimited bandwidth!)
• Global applications
• Need best CDN performance
• Already using Cloudflare
• Budget-conscious projects
• Edge-first architecture

# ═══════════════════════════════════════════
# ADVANCED: WORKERS + PAGES (2025)
# ═══════════════════════════════════════════

# Combine Pages (frontend) with Workers (backend)
# Pages: Static assets + edge functions
# Workers: Complex backend logic + APIs

# Example: E-commerce site
# - Pages: Product catalog (static)
# - Workers: Cart, checkout, payment processing
# - D1: Product database
# - R2: Product images
# - KV: Session storage

# Benefits:
# - Single platform
# - Unified billing
# - Edge performance
# - Infinite scalability

# Cost: Still mostly free! 💰
# Workers: 100k requests/day free
# Pages: Unlimited bandwidth free
# D1: 5M reads/day free
# R2: 10GB storage free
# KV: 100k reads/day free
```

### 🆕 Cloudflare 2025 New Features

```javascript
// ═══════════════════════════════════════════
// D1 DATABASE INTEGRATION (2025)
// ═══════════════════════════════════════════

// functions/api/posts/[id].js
export async function onRequest(context) {
  const { params, env } = context;

  // Query D1 (Cloudflare's edge SQL database)
  const post = await env.DB.prepare("SELECT * FROM posts WHERE id = ?")
    .bind(params.id)
    .first();

  if (!post) {
    return new Response("Not found", { status: 404 });
  }

  return Response.json(post);
}

// ═══════════════════════════════════════════
// R2 STORAGE INTEGRATION (2025)
// ═══════════════════════════════════════════

// functions/api/upload.js
export async function onRequestPost(context) {
  const { request, env } = context;

  const formData = await request.formData();
  const file = formData.get("file");

  // Upload to R2 (S3-compatible storage)
  await env.MY_BUCKET.put(file.name, file);

  return Response.json({
    success: true,
    url: `https://r2.example.com/${file.name}`,
  });
}

// ═══════════════════════════════════════════
// QUEUES INTEGRATION (2025 - NEW!)
// ═══════════════════════════════════════════

// Background job processing
// functions/api/process.js
export async function onRequestPost(context) {
  const { request, env } = context;
  const data = await request.json();

  // Send to queue for background processing
  await env.MY_QUEUE.send(data);

  return Response.json({
    status: "queued",
    message: "Processing started",
  });
}

// Consumer: Process queue messages
// worker.js
export default {
  async queue(batch, env) {
    for (const message of batch.messages) {
      await processJob(message.body);
      message.ack();
    }
  },
};

// ═══════════════════════════════════════════
// AI INTEGRATION (2025 - WORKERS AI)
// ═══════════════════════════════════════════

// functions/api/ai-chat.js
export async function onRequestPost(context) {
  const { request, env } = context;
  const { prompt } = await request.json();

  // Use Cloudflare's AI models at the edge!
  const response = await env.AI.run("@cf/meta/llama-2-7b-chat-int8", {
    prompt: prompt,
  });

  return Response.json({ response });
}
```

---

<div align="center">

## 🎨 Render Static Sites

**Simple, unified platform for static sites**

</div>

```
🌐 Website → https://render.com
🎯 Best For → Combined static + backend hosting, unified platform
💰 Pricing  → Free for static sites, no credit card required
             Paid: Backend services start at $7/month
⚡ Features → Auto-deploy, Custom domains, HTTPS, Docker support
🔧 Frameworks→ All static frameworks, plus backend services
🆕 2025     → Improved build times, better free tier
```

### 📥 Render Setup

```bash
# ═══════════════════════════════════════════
# SETUP VIA UI (EASIEST)
# ═══════════════════════════════════════════

# 1. Go to render.com
# 2. New → Static Site
# 3. Connect Git repository
# 4. Configure:
#    - Build Command: npm run build
#    - Publish Directory: dist
#    - Branch: main
# 5. Create Static Site

# Auto-deploys on every push! 🚀

# ═══════════════════════════════════════════
# RENDER.YAML (INFRASTRUCTURE AS CODE)
# ═══════════════════════════════════════════

# render.yaml in repository root
services:
  - type: web
    name: my-static-site
    env: static
    buildCommand: npm run build
    staticPublishPath: ./dist

    # Branch to deploy from
    branch: main

    # Custom domains
    domains:
      - www.example.com
      - example.com

    # Environment variables
    envVars:
      - key: NODE_VERSION
        value: 20
      - key: NODE_ENV
        value: production

    # Headers (2025 feature)
    headers:
      - path: /*
        name: X-Frame-Options
        value: DENY
      - path: /*
        name: X-Content-Type-Options
        value: nosniff
      - path: /assets/*
        name: Cache-Control
        value: public, max-age=31536000, immutable

    # Redirects
    routes:
      - type: redirect
        source: /old-path
        destination: /new-path
        status: 301

      # SPA fallback
      - type: rewrite
        source: /*
        destination: /index.html

# Deploy automatically on git push ✨
```

### 💡 Render Pro Tips

```bash
# ═══════════════════════════════════════════
# RENDER ADVANTAGES
# ═══════════════════════════════════════════

✅ FREE TIER:
• Static sites: Completely free
• Custom domains: Free
• HTTPS: Free
• No credit card required
• No time limit

✅ UNIFIED PLATFORM:
• Static frontend + Backend + Database
• All in one place
• Single billing
• Easy inter-service communication

✅ ZERO CONFIG:
• Auto-detects framework
• Auto-installs dependencies
• Auto-generates build command
• Just works™

# ═══════════════════════════════════════════
# WHEN TO CHOOSE RENDER
# ═══════════════════════════════════════════

✅ PERFECT FOR:
• Full-stack applications
• Need backend + frontend
• Want predictable pricing
• Need databases (Postgres, Redis)
• Docker-based deployments
• Background workers/cron jobs

❌ MIGHT NOT BE IDEAL FOR:
• Cutting-edge edge computing
• Need fastest deploy times
• Next.js-specific features
• Global CDN performance critical

# ═══════════════════════════════════════════
# RENDER VS VERCEL COST COMPARISON (2025)
# ═══════════════════════════════════════════

# Example: Medium traffic site (500k visitors/month)

VERCEL:
• Pro Plan: $20/user/month
• Edge Requests: ~12.5M = $5
• Bandwidth: ~50GB = $7.50
• TOTAL: ~$32.50/month

RENDER:
• Static Site: $0/month
• Backend (if needed): $7/month
• TOTAL: $7/month or FREE (static only)

💰 SAVINGS: $25.50/month = $306/year!

# Real example: Showzone
# Vercel: $800/month
# Moved to Render: $40/month
# Savings: $760/month = $9,120/year! 🎉

# ═══════════════════════════════════════════
# ADVANCED: FULL-STACK SETUP
# ═══════════════════════════════════════════

# render.yaml - Full stack example
services:
  # Frontend (Static)
  - type: web
    name: frontend
    env: static
    buildCommand: npm run build
    staticPublishPath: ./dist

  # Backend (API)
  - type: web
    name: backend
    env: node
    buildCommand: npm install
    startCommand: npm start
    envVars:
      - key: DATABASE_URL
        fromDatabase:
          name: mydb
          property: connectionString

  # Database
databases:
  - name: mydb
    plan: free
    databaseName: myapp
    user: myapp

# Cost: Still mostly free! 💰
```

---

<div align="center">

## 🌊 Surge

**Simple, single-command deployments**

</div>

```
🌐 Website → https://surge.sh
🎯 Best For → Quick prototypes, testing, simple static sites
💰 Pricing  → Free with surge.sh subdomain
             Plus: $30/month (custom domains, no ads)
⚡ Features → CLI-first, ultra-fast deployment (<10s)
🔧 Tech     → Any static HTML/CSS/JS
🆕 2025     → Still simple, still fast, still reliable
```

### 📥 Surge Setup

```bash
# ═══════════════════════════════════════════
# INSTALLATION & DEPLOYMENT
# ═══════════════════════════════════════════

# Install
npm install -g surge

# Deploy current directory
surge

# Deploy specific directory
surge ./dist

# Deploy to custom subdomain
surge ./dist my-awesome-site.surge.sh

# Deploy with custom domain (Plus plan required)
surge ./dist example.com

# ═══════════════════════════════════════════
# CUSTOM DOMAIN
# ═══════════════════════════════════════════

# 1. Deploy to custom domain
surge ./dist example.com

# 2. Add CNAME file in your project
echo "example.com" > CNAME

# 3. Configure DNS (at domain provider)
# CNAME: www → na-west1.surge.sh
# A: @ → 138.197.235.123

# ═══════════════════════════════════════════
# COMMON COMMANDS
# ═══════════════════════════════════════════

# List projects
surge list

# Remove project
surge teardown my-site.surge.sh

# View project
surge open my-site.surge.sh

# Get help
surge --help

# ═══════════════════════════════════════════
# CORS & ROUTING
# ═══════════════════════════════════════════

# Enable CORS
# Create CORS file in root
echo '*' > CORS

# SPA routing (200.html)
# Copy index.html to 200.html
cp index.html 200.html

# This makes all routes serve index.html
# Perfect for React Router, Vue Router, etc.

# ═══════════════════════════════════════════
# SURGE ADVANTAGES
# ═══════════════════════════════════════════

✅ INSANELY FAST:
• Deploy in <10 seconds
• Fastest deployment of all platforms
• No build process (just upload)

✅ SUPER SIMPLE:
• One command: surge
• No configuration files
• No account required (for .surge.sh domains)

✅ FREE FOREVER:
• Unlimited sites
• Unlimited deploys
• No bandwidth limits on free tier

✅ PERFECT FOR:
• Quick demos
• Client previews
• Testing
• Learning
• Hackathons

❌ LIMITATIONS:
• No build process (you build locally)
• No preview URLs
• No team features
• Basic features only
• Plus plan expensive for what you get ($30/month)

# ═══════════════════════════════════════════
# SURGE vs ALTERNATIVES (2025)
# ═══════════════════════════════════════════

USE SURGE WHEN:
• Need instant deployment (<10s)
• Testing something quickly
• Don't need CI/CD
• Want simplest possible solution
• Sharing quick demo

USE VERCEL/NETLIFY WHEN:
• Need build process
• Need preview URLs
• Need team collaboration
• Production application
• Need serverless functions

# Pro tip: Use Surge for quick tests,
# then move to Vercel/Netlify for production
```

---

<div align="center">

## 🔧 Build Optimization

_Fast builds, faster sites_ ⚡

</div>

### Build Performance (2025 Update)

```bash
# ═══════════════════════════════════════════
# CACHING STRATEGIES
# ═══════════════════════════════════════════

# Most platforms cache node_modules automatically

# Vercel: Automatic caching of node_modules
# Netlify: Automatic caching with build plugins
# Cloudflare Pages: Cache configuration in wrangler.toml
# GitHub Actions: Manual caching required

# GitHub Actions caching example (2025):
- name: Cache dependencies
  uses: actions/cache@v4
  with:
    path: |
      ~/.npm
      .next/cache
    key: ${{ runner.os }}-node-${{ hashFiles('**/package-lock.json') }}
    restore-keys: |
      ${{ runner.os }}-node-

# ═══════════════════════════════════════════
# OPTIMIZE BUILD COMMAND
# ═══════════════════════════════════════════

# Use production builds
npm run build
# NOT: npm run dev

# Set NODE_ENV
NODE_ENV=production npm run build

# Use faster package managers (2025 recommendation)
pnpm install  # Fastest
npm ci        # Faster than npm install
yarn install  # Also fast

# Disable source maps in production (faster builds)
# vite.config.js
export default {
  build: {
    sourcemap: false,
    minify: 'terser',
    cssCodeSplit: true
  }
}

# next.config.js
module.exports = {
  productionBrowserSourceMaps: false,
  swcMinify: true,  // Use SWC instead of Terser (faster)
}

# ═══════════════════════════════════════════
# PARALLEL BUILDS (2025 - MULTI-CORE)
# ═══════════════════════════════════════════

# Use all CPU cores
# package.json
{
  "scripts": {
    "build": "vite build --parallel"
  }
}

# Webpack parallel builds
// webpack.config.js
const TerserPlugin = require('terser-webpack-plugin');

module.exports = {
  optimization: {
    minimize: true,
    minimizer: [
      new TerserPlugin({
        parallel: true,
        terserOptions: {
          compress: {
            drop_console: true
          }
        }
      })
    ]
  }
};

# Next.js parallel builds (automatic with SWC)
# Just upgrade to Next.js 14+ for automatic optimization

# ═══════════════════════════════════════════
# INCREMENTAL BUILDS (2025)
# ═══════════════════════════════════════════

# Next.js ISR (Incremental Static Regeneration)
export const revalidate = 60; // Revalidate every 60 seconds

# Gatsby incremental builds
gatsby build --log-pages

# Vite dependency pre-bundling
# vite.config.js
export default {
  optimizeDeps: {
    include: ['react', 'react-dom'],
    exclude: ['@vueuse/core']
  }
}

# ═══════════════════════════════════════════
# BUILD OUTPUT ANALYSIS (2025 TOOLS)
# ═══════════════════════════════════════════

# Next.js bundle analyzer
npm install @next/bundle-analyzer

# next.config.js
const withBundleAnalyzer = require('@next/bundle-analyzer')({
  enabled: process.env.ANALYZE === 'true'
});

module.exports = withBundleAnalyzer({
  // Your Next.js config
});

# Analyze
ANALYZE=true npm run build

# Vite bundle analyzer
npm install rollup-plugin-visualizer

# vite.config.js
import { visualizer } from 'rollup-plugin-visualizer';

export default {
  plugins: [
    visualizer({
      open: true,
      gzipSize: true,
      brotliSize: true,
      filename: './dist/stats.html'
    })
  ]
};

# Webpack Bundle Analyzer
npm install webpack-bundle-analyzer

# webpack.config.js
const BundleAnalyzerPlugin = require('webpack-bundle-analyzer').BundleAnalyzerPlugin;

module.exports = {
  plugins: [
    new BundleAnalyzerPlugin({
      analyzerMode: 'static',
      openAnalyzer: false,
      reportFilename: 'bundle-report.html'
    })
  ]
};

# ═══════════════════════════════════════════
# REDUCE BUILD TIME (2025 TIPS)
# ═══════════════════════════════════════════

✅ USE FASTER TOOLS:
• Vite instead of Create React App
• SWC instead of Babel
• esbuild instead of Webpack
• pnpm instead of npm

✅ OPTIMIZE DEPENDENCIES:
• Remove unused dependencies
• Use lighter alternatives
• Import only what you need

Example:
// ❌ Bad - imports entire library
import _ from 'lodash';

// ✅ Good - imports only what you need
import debounce from 'lodash/debounce';

✅ ENABLE CACHING:
• .next/cache (Next.js)
• node_modules/.vite (Vite)
• .cache (Gatsby)

✅ USE TYPESCRIPT PROJECT REFERENCES:
// tsconfig.json
{
  "compilerOptions": {
    "incremental": true,
    "composite": true
  }
}

✅ SPLIT YOUR BUILD:
• Build frontend and backend separately
• Use monorepo tools (Turborepo, Nx)
• Only rebuild what changed

# ═══════════════════════════════════════════
# BUILD TIME COMPARISON (2025)
# ═══════════════════════════════════════════

Tool              | Small Project | Large Project
------------------|---------------|---------------
Vite              | 5-15s        | 30-60s
Next.js (SWC)     | 10-20s       | 45-90s
Create React App  | 20-40s       | 90-180s
Webpack (optimized)| 15-30s      | 60-120s
```

---

<div align="center">

## 🎨 Performance Optimization

_Make your site blazing fast_ 🚀

</div>

### Performance Checklist (2025)

```javascript
// ═══════════════════════════════════════════
// IMAGE OPTIMIZATION (2025 BEST PRACTICES)
// ═══════════════════════════════════════════

// 1. Use Next.js Image component (automatic optimization)
import Image from 'next/image';

<Image
  src="/photo.jpg"
  alt="Photo"
  width={800}
  height={600}
  loading="lazy"
  placeholder="blur"
  quality={85}
  sizes="(max-width: 768px) 100vw, 50vw"
/>

// 2. Use modern formats (WebP, AVIF)
<picture>
  <source srcset="image.avif" type="image/avif" />
  <source srcset="image.webp" type="image/webp" />
  <img src="image.jpg" alt="Image" loading="lazy" />
</picture>

// 3. Responsive images
<img
  srcset="
    image-400w.jpg 400w,
    image-800w.jpg 800w,
    image-1200w.jpg 1200w
  "
  sizes="(max-width: 600px) 400px, (max-width: 1200px) 800px, 1200px"
  src="image-800w.jpg"
  alt="Image"
  loading="lazy"
/>

// 4. Native lazy loading
<img src="image.jpg" loading="lazy" alt="Image" />

// 5. Image optimization services (2025)
// - Cloudinary (AI-powered)
// - imgix
// - Vercel Image Optimization (automatic)
// - Netlify Image CDN
// - Cloudflare Images

// 6. Use Image CDN with transformations
// Cloudinary example:
const imageUrl = 'https://res.cloudinary.com/demo/image/upload/w_400,f_auto,q_auto/sample.jpg';

// Parameters:
// w_400 - width 400px
// f_auto - automatic format (WebP, AVIF)
// q_auto - automatic quality

// ═══════════════════════════════════════════
// CODE SPLITTING (2025)
// ═══════════════════════════════════════════

// Dynamic imports
import dynamic from 'next/dynamic';

const HeavyComponent = dynamic(() => import('./HeavyComponent'), {
  loading: () => <p>Loading...</p>,
  ssr: false
});

// React lazy
import { lazy, Suspense } from 'react';

const LazyComponent = lazy(() => import('./LazyComponent'));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </Suspense>
  );
}

// Route-based splitting (automatic with Next.js App Router)
// app/dashboard/page.tsx - automatically code split

// Component-level splitting with webpack magic comments
const Admin = lazy(() => import(
  /* webpackChunkName: "admin" */
  /* webpackPrefetch: true */
  './Admin'
));

// ═══════════════════════════════════════════
// MINIFICATION (2025 - AUTOMATIC)
// ═══════════════════════════════════════════

// Most build tools handle this automatically
// Vite, Next.js, Create React App, etc.

// Manual configuration if needed
// vite.config.js
export default {
  build: {
    minify: 'terser',
    terserOptions: {
      compress: {
        drop_console: true,
        drop_debugger: true,
        pure_funcs: ['console.log']
      }
    }
  }
};

// next.config.js (SWC minification - faster)
module.exports = {
  swcMinify: true,
  compiler: {
    removeConsole: process.env.NODE_ENV === 'production'
  }
};

// ═══════════════════════════════════════════
// CACHING STRATEGIES (2025)
// ═══════════════════════════════════════════

// Static assets with cache busting
// Automatic with most build tools

// Example: Vite output
// main-abc123.js (hash changes when file changes)

// Service Worker for offline support
// Using Workbox
import { precacheAndRoute } from 'workbox-precaching';

precacheAndRoute(self.__WB_MANIFEST);

// Next.js PWA
// next-pwa configuration
const withPWA = require('next-pwa')({
  dest: 'public',
  register: true,
  skipWaiting: true,
  disable: process.env.NODE_ENV === 'development'
});

module.exports = withPWA({
  // Your Next.js config
});

// ═══════════════════════════════════════════
// PREFETCHING & PRELOADING (2025)
// ═══════════════════════════════════════════

// Preload critical resources
<link rel="preload" href="/font.woff2" as="font" type="font/woff2" crossorigin />
<link rel="preload" href="/critical.css" as="style" />
<link rel="preload" href="/hero.jpg" as="image" />

// Prefetch next page
<link rel="prefetch" href="/about" />

// Preconnect to external domains
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="dns-prefetch" href="https://analytics.example.com" />

// Next.js automatic prefetching
import Link from 'next/link';

<Link href="/about" prefetch>About</Link>

// React lazy with prefetch
const LazyComponent = lazy(() => {
  const promise = import('./Component');
  // Prefetch in the background
  promise.then(module => module);
  return promise;
});

// ═══════════════════════════════════════════
// CRITICAL CSS (2025)
// ═══════════════════════════════════════════

// Inline critical CSS
<style>
  /* Critical CSS here */
  body { margin: 0; font-family: system-ui; }
  .hero { background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); }
</style>

// Load rest async
<link rel="stylesheet" href="/styles.css" media="print" onload="this.media='all'" />
<noscript><link rel="stylesheet" href="/styles.css" /></noscript>

// Tools for extracting critical CSS:
// - Critical (npm package)
// - Critters (automatic in Next.js)
// - PurgeCSS
// - UnCSS

// Next.js automatic critical CSS extraction
// No configuration needed! ✨

// ═══════════════════════════════════════════
// THIRD-PARTY SCRIPTS (2025)
// ═══════════════════════════════════════════

// Load async/defer
<script src="analytics.js" async></script>
<script src="widget.js" defer></script>

// Next.js Script component (recommended)
import Script from 'next/script';

<Script
  src="https://analytics.example.com/script.js"
  strategy="afterInteractive"
/>

// Strategies:
// - beforeInteractive: Load before page is interactive
// - afterInteractive: Load after page is interactive (default)
// - lazyOnload: Load during idle time
// - worker: Load in a web worker (experimental)

// Load on interaction
import { useEffect, useState } from 'react';

function Component() {
  const [loaded, setLoaded] = useState(false);

  const loadScript = () => {
    if (!loaded) {
      const script = document.createElement('script');
      script.src = 'heavy-widget.js';
      document.body.appendChild(script);
      setLoaded(true);
    }
  };

  return <button onClick={loadScript}>Load Widget</button>;
}

// Facade pattern for heavy embeds
// Example: YouTube video facade
function YouTubeFacade({ videoId }) {
  const [clicked, setClicked] = useState(false);

  if (!clicked) {
    return (
      <div
        style={{
          backgroundImage: `url(https://img.youtube.com/vi/${videoId}/maxresdefault.jpg)`,
          cursor: 'pointer'
        }}
        onClick={() => setClicked(true)}
      >
        ▶️ Play
      </div>
    );
  }

  return (
    <iframe
      src={`https://www.youtube.com/embed/${videoId}?autoplay=1`}
      allow="accelerometer; autoplay; encrypted-media; gyroscope"
    />
  );
}

// ═══════════════════════════════════════════
// PERFORMANCE MONITORING (2025)
// ═══════════════════════════════════════════

// Web Vitals
import { onCLS, onFID, onFCP, onLCP, onTTFB, onINP } from 'web-vitals';

onCLS(console.log);  // Cumulative Layout Shift
onFID(console.log);  // First Input Delay
onFCP(console.log);  // First Contentful Paint
onLCP(console.log);  // Largest Contentful Paint
onTTFB(console.log); // Time to First Byte
onINP(console.log);  // Interaction to Next Paint (new in 2025!)

// Send to analytics
import { sendToAnalytics } from './analytics';

function reportWebVitals(metric) {
  sendToAnalytics(metric);
}

onCLS(reportWebVitals);
onFID(reportWebVitals);
onLCP(reportWebVitals);
onINP(reportWebVitals);

// Next.js built-in Web Vitals reporting
// pages/_app.js
export function reportWebVitals(metric) {
  console.log(metric);
}

// Vercel Analytics (automatic)
import { Analytics } from '@vercel/analytics/react';

<Analytics />

// Lighthouse CI
// .github/workflows/lighthouse.yml
- name: Run Lighthouse CI
  run: |
    npm install -g @lhci/cli
    lhci autorun

// ═══════════════════════════════════════════
// FONT OPTIMIZATION (2025)
// ═══════════════════════════════════════════

// Use next/font (automatic optimization)
import { Inter, Roboto_Mono } from 'next/font/google';

const inter = Inter({
  subsets: ['latin'],
  display: 'swap',
  variable: '--font-inter'
});

const robotoMono = Roboto_Mono({
  subsets: ['latin'],
  display: 'swap',
  variable: '--font-roboto-mono'
});

// Font display strategies
// - swap: Show fallback immediately, swap when loaded
// - optional: Use fallback if font takes too long
// - fallback: Brief invisible period, then fallback
// - block: Hide text until font loads

// Self-hosted fonts
<link
  rel="preload"
  href="/fonts/inter.woff2"
  as="font"
  type="font/woff2"
  crossorigin
/>

@font-face {
  font-family: 'Inter';
  src: url('/fonts/inter.woff2') format('woff2');
  font-display: swap;
  font-weight: 400;
}

// ═══════════════════════════════════════════
// RESOURCE HINTS (2025)
// ═══════════════════════════════════════════

// DNS prefetch
<link rel="dns-prefetch" href="https://api.example.com" />

// Preconnect (DNS + TCP + TLS)
<link rel="preconnect" href="https://fonts.googleapis.com" />

// Prefetch (low priority)
<link rel="prefetch" href="/next-page.js" />

// Preload (high priority)
<link rel="preload" href="/critical.css" as="style" />

// Prerender (experimental)
<link rel="prerender" href="/next-page" />

// Module preload (ES modules)
<link rel="modulepreload" href="/app.js" />
```

### Performance Budget (2025)

```javascript
// ═══════════════════════════════════════════
// SET PERFORMANCE BUDGETS
// ═══════════════════════════════════════════

// lighthouse-budget.json
[
  {
    "path": "/*",
    "timings": [
      {
        "metric": "interactive",
        "budget": 3000
      },
      {
        "metric": "first-contentful-paint",
        "budget": 1000
      },
      {
        "metric": "largest-contentful-paint",
        "budget": 2500
      },
      {
        "metric": "total-blocking-time",
        "budget": 300
      },
      {
        "metric": "cumulative-layout-shift",
        "budget": 0.1
      }
    ],
    "resourceSizes": [
      {
        "resourceType": "script",
        "budget": 300
      },
      {
        "resourceType": "image",
        "budget": 500
      },
      {
        "resourceType": "stylesheet",
        "budget": 50
      },
      {
        "resourceType": "total",
        "budget": 1000
      }
    ],
    "resourceCounts": [
      {
        "resourceType": "third-party",
        "budget": 10
      },
      {
        "resourceType": "script",
        "budget": 15
      }
    ]
  }
]

// Run Lighthouse with budget
lighthouse https://example.com --budget-path=./lighthouse-budget.json

// Fail CI if budget exceeded
// .github/workflows/performance.yml
- name: Check Performance Budget
  run: |
    npm install -g lighthouse
    lighthouse https://example.com \
      --budget-path=./budget.json \
      --output=json \
      --output-path=./report.json
    node check-budget.js

// check-budget.js
const report = require('./report.json');
const budgets = require('./lighthouse-budget.json');

let failed = false;

report.audits['performance-budget'].details.items.forEach(item => {
  if (item.sizeOverBudget > 0) {
    console.error(`❌ ${item.label} exceeded budget by ${item.sizeOverBudget}KB`);
    failed = true;
  }
});

if (failed) {
  process.exit(1);
}

// ═══════════════════════════════════════════
// 2025 PERFORMANCE TARGETS
// ═══════════════════════════════════════════

EXCELLENT:
• LCP: < 2.5s
• FID/INP: < 100ms
• CLS: < 0.1
• FCP: < 1.8s
• TTFB: < 600ms

GOOD:
• LCP: < 4s
• FID/INP: < 300ms
• CLS: < 0.25
• FCP: < 3s
• TTFB: < 1.8s

NEEDS IMPROVEMENT:
• LCP: > 4s
• FID/INP: > 300ms
• CLS: > 0.25
• FCP: > 3s
• TTFB: > 1.8s
```

---

<div align="center">

## 🔍 SEO Best Practices

_Get found on search engines_ 📈

</div>

### SEO Essentials (2025 Update)

```html
<!-- ═══════════════════════════════════════════ -->
<!-- ESSENTIAL META TAGS (2025) -->
<!-- ═══════════════════════════════════════════ -->

<!DOCTYPE html>
<html lang="en">
  <head>
    <!-- Character encoding -->
    <meta charset="UTF-8" />

    <!-- Viewport for responsive design -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />

    <!-- Primary Meta Tags -->
    <title>Page Title (50-60 chars) - Your Brand Name</title>
    <meta name="title" content="Page Title - Your Brand Name" />
    <meta
      name="description"
      content="Compelling description under 160 characters that includes relevant keywords and entices users to click"
    />
    <meta name="keywords" content="keyword1, keyword2, keyword3" />
    <meta name="robots" content="index, follow" />
    <meta name="language" content="English" />
    <meta name="author" content="Your Name" />

    <!-- Canonical URL (prevent duplicate content) -->
    <link rel="canonical" href="https://www.example.com/page" />

    <!-- Open Graph / Facebook -->
    <meta property="og:type" content="website" />
    <meta property="og:url" content="https://www.example.com/" />
    <meta property="og:title" content="Page Title - Your Brand" />
    <meta
      property="og:description"
      content="Your description here (up to 200 chars)"
    />
    <meta property="og:image" content="https://www.example.com/og-image.jpg" />
    <meta property="og:image:width" content="1200" />
    <meta property="og:image:height" content="630" />
    <meta property="og:site_name" content="Your Site Name" />
    <meta property="og:locale" content="en_US" />

    <!-- Twitter -->
    <meta property="twitter:card" content="summary_large_image" />
    <meta property="twitter:url" content="https://www.example.com/" />
    <meta property="twitter:title" content="Page Title - Your Brand" />
    <meta property="twitter:description" content="Your description here" />
    <meta
      property="twitter:image"
      content="https://www.example.com/twitter-image.jpg"
    />
    <meta name="twitter:creator" content="@yourusername" />
    <meta name="twitter:site" content="@yourusername" />

    <!-- Favicon (2025 - all formats) -->
    <link rel="icon" type="image/x-icon" href="/favicon.ico" />
    <link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png" />
    <link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png" />
    <link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png" />
    <link rel="manifest" href="/site.webmanifest" />

    <!-- Theme Color -->
    <meta name="theme-color" content="#ffffff" />
    <meta name="msapplication-TileColor" content="#da532c" />

    <!-- Preconnect to external domains -->
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://cdn.example.com" />

    <!-- Structured Data (JSON-LD) -->
    <script type="application/ld+json">
      {
        "@context": "https://schema.org",
        "@type": "WebSite",
        "name": "Your Site Name",
        "url": "https://www.example.com",
        "description": "Your site description",
        "potentialAction": {
          "@type": "SearchAction",
          "target": "https://www.example.com/search?q={search_term_string}",
          "query-input": "required name=search_term_string"
        }
      }
    </script>
  </head>
  <body>
    <!-- Content here -->
  </body>
</html>

<!-- ═══════════════════════════════════════════ -->
<!-- STRUCTURED DATA EXAMPLES (2025) -->
<!-- ═══════════════════════════════════════════ -->

<!-- Article -->
<script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "Article",
    "headline": "Article Headline (max 110 chars)",
    "image": [
      "https://example.com/image-1x1.jpg",
      "https://example.com/image-4x3.jpg",
      "https://example.com/image-16x9.jpg"
    ],
    "datePublished": "2025-01-01T08:00:00+00:00",
    "dateModified": "2025-01-02T09:20:00+00:00",
    "author": {
      "@type": "Person",
      "name": "Author Name",
      "url": "https://example.com/author"
    },
    "publisher": {
      "@type": "Organization",
      "name": "Publisher Name",
      "logo": {
        "@type": "ImageObject",
        "url": "https://example.com/logo.png"
      }
    },
    "description": "Article description"
  }
</script>

<!-- Organization -->
<script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "Organization",
    "name": "Your Company",
    "url": "https://www.example.com",
    "logo": "https://www.example.com/logo.png",
    "description": "Company description",
    "contactPoint": {
      "@type": "ContactPoint",
      "telephone": "+1-555-555-5555",
      "contactType": "Customer Service",
      "email": "support@example.com"
    },
    "sameAs": [
      "https://www.facebook.com/yourpage",
      "https://twitter.com/yourhandle",
      "https://www.linkedin.com/company/yourcompany",
      "https://www.instagram.com/yourhandle",
      "https://github.com/yourorg"
    ]
  }
</script>

<!-- Product (E-commerce) -->
<script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "Product",
    "name": "Product Name",
    "image": "https://example.com/product.jpg",
    "description": "Product description",
    "brand": {
      "@type": "Brand",
      "name": "Brand Name"
    },
    "sku": "12345",
    "offers": {
      "@type": "Offer",
      "url": "https://example.com/product",
      "priceCurrency": "USD",
      "price": "99.99",
      "availability": "https://schema.org/InStock",
      "seller": {
        "@type": "Organization",
        "name": "Your Store"
      }
    },
    "aggregateRating": {
      "@type": "AggregateRating",
      "ratingValue": "4.5",
      "reviewCount": "123"
    }
  }
</script>

<!-- Breadcrumb -->
<script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "BreadcrumbList",
    "itemListElement": [
      {
        "@type": "ListItem",
        "position": 1,
        "name": "Home",
        "item": "https://example.com"
      },
      {
        "@type": "ListItem",
        "position": 2,
        "name": "Category",
        "item": "https://example.com/category"
      },
      {
        "@type": "ListItem",
        "position": 3,
        "name": "Product",
        "item": "https://example.com/category/product"
      }
    ]
  }
</script>

<!-- FAQ -->
<script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "FAQPage",
    "mainEntity": [
      {
        "@type": "Question",
        "name": "What is your return policy?",
        "acceptedAnswer": {
          "@type": "Answer",
          "text": "We offer a 30-day money-back guarantee..."
        }
      },
      {
        "@type": "Question",
        "name": "How long does shipping take?",
        "acceptedAnswer": {
          "@type": "Answer",
          "text": "Standard shipping takes 3-5 business days..."
        }
      }
    ]
  }
</script>
```

### SEO Tools & Files (2025)

```xml
<!-- ═══════════════════════════════════════════ -->
<!-- sitemap.xml (2025 format) -->
<!-- ═══════════════════════════════════════════ -->

<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"
        xmlns:news="http://www.google.com/schemas/sitemap-news/0.9"
        xmlns:xhtml="http://www.w3.org/1999/xhtml"
        xmlns:mobile="http://www.google.com/schemas/sitemap-mobile/1.0"
        xmlns:image="http://www.google.com/schemas/sitemap-image/1.1"
        xmlns:video="http://www.google.com/schemas/sitemap-video/1.1">

  <url>
    <loc>https://www.example.com/</loc>
    <lastmod>2025-01-01</lastmod>
    <changefreq>daily</changefreq>
    <priority>1.0</priority>
  </url>

  <url>
    <loc>https://www.example.com/about</loc>
    <lastmod>2025-01-01</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
    <!-- Alternate language versions -->
    <xhtml:link
      rel="alternate"
      hreflang="es"
      href="https://www.example.com/es/about"/>
  </url>

  <!-- With images -->
  <url>
    <loc>https://www.example.com/blog/post</loc>
    <lastmod>2025-01-15</lastmod>
    <changefreq>weekly</changefreq>
    <priority>0.9</priority>
    <image:image>
      <image:loc>https://www.example.com/images/photo.jpg</image:loc>
      <image:caption>Photo caption</image:caption>
    </image:image>
  </url>

</urlset>

<!-- Generate sitemap automatically -->
<!-- Next.js example (2025) -->
<!-- app/sitemap.ts -->
import { MetadataRoute } from 'next';

export default async function sitemap(): Promise<MetadataRoute.Sitemap> {
  const posts = await getPosts();

  return [
    {
      url: 'https://www.example.com',
      lastModified: new Date(),
      changeFrequency: 'daily',
      priority: 1,
    },
    {
      url: 'https://www.example.com/about',
      lastModified: new Date(),
      changeFrequency: 'monthly',
      priority: 0.8,
    },
    ...posts.map((post) => ({
      url: `https://www.example.com/blog/${post.slug}`,
      lastModified: new Date(post.updatedAt),
      changeFrequency: 'weekly' as const,
      priority: 0.9,
    })),
  ];
}
```

```txt
# ═══════════════════════════════════════════
# robots.txt (2025)
# ═══════════════════════════════════════════

User-agent: *
Allow: /

# Disallow admin pages
Disallow: /admin/
Disallow: /private/
Disallow: /api/
Disallow: /*.json$
Disallow: /*?*print=*

# Allow Google Image Bot
User-agent: Googlebot-Image
Allow: /

# Sitemap location
Sitemap: https://www.example.com/sitemap.xml
Sitemap: https://www.example.com/sitemap-images.xml

# Block specific bots (if needed)
User-agent: BadBot
Disallow: /

User-agent: AhrefsBot
Crawl-delay: 10

# Crawl delay for all bots
User-agent: *
Crawl-delay: 1

# ═══════════════════════════════════════════
# Next.js robots.ts (2025)
# ═══════════════════════════════════════════

// app/robots.ts
import { MetadataRoute } from 'next';

export default function robots(): MetadataRoute.Robots {
  return {
    rules: {
      userAgent: '*',
      allow: '/',
      disallow: ['/private/', '/admin/', '/api/'],
    },
    sitemap: 'https://www.example.com/sitemap.xml',
  };
}
```

### 2025 SEO Checklist

```
═══════════════════════════════════════════════════════════
SEO CHECKLIST FOR STATIC SITES (2025)
═══════════════════════════════════════════════════════════

TECHNICAL SEO:
☑ HTTPS enabled (all platforms do this automatically)
☑ Sitemap.xml generated and submitted to Search Console
☑ Robots.txt configured
☑ Canonical URLs set
☑ 404 pages exist and are helpful
☑ 301 redirects for old URLs
☑ Mobile-friendly (responsive design)
☑ Fast loading (LCP < 2.5s)
☑ No broken links
☑ Clean URL structure (/blog/post-name not /blog.php?id=123)

ON-PAGE SEO:
☑ Unique title tags (50-60 chars)
☑ Compelling meta descriptions (150-160 chars)
☑ H1 tag on every page (only one)
☑ Logical heading structure (H1 → H2 → H3)
☑ Alt text on all images
☑ Internal linking strategy
☑ Keyword in URL, title, H1, first paragraph
☑ Content is valuable and original
☑ Schema markup (JSON-LD)

CONTENT:
☑ High-quality, original content
☑ Target keywords naturally integrated
☑ Content is up-to-date
☑ Proper use of headings
☑ Lists and formatting for readability
☑ Multimedia (images, videos)
☑ Internal links to related content
☑ External links to authority sources

PERFORMANCE:
☑ Core Web Vitals passing
☑ Images optimized (WebP/AVIF)
☑ Lazy loading images
☑ Minified CSS/JS
☑ No render-blocking resources
☑ CDN in use

SOCIAL:
☑ Open Graph tags
☑ Twitter Card tags
☑ Social sharing buttons
☑ Attractive og:image (1200x630px)

LOCAL SEO (IF APPLICABLE):
☑ Google Business Profile
☑ NAP (Name, Address, Phone) consistent
☑ Local schema markup
☑ Reviews and ratings

MONITORING:
☑ Google Search Console setup
☑ Google Analytics setup
☑ Performance monitoring
☑ Regular content updates
☑ Backlink monitoring
```

---

<div align="center">

## 🔐 Security Headers

_Protect your users and your site_ 🛡️

</div>

### Essential Security Headers (2025)

```javascript
// ═══════════════════════════════════════════
// SECURITY HEADERS EXPLAINED (2025)
// ═══════════════════════════════════════════

const securityHeaders = {
  // Prevent clickjacking attacks
  "X-Frame-Options": "DENY",
  // Alternative to X-Frame-Options (more flexible)
  "Content-Security-Policy": "frame-ancestors 'none'",

  // Prevent MIME type sniffing
  "X-Content-Type-Options": "nosniff",

  // Enable XSS protection (legacy browsers)
  "X-XSS-Protection": "1; mode=block",

  // Force HTTPS
  "Strict-Transport-Security": "max-age=31536000; includeSubDomains; preload",

  // Control referrer information
  "Referrer-Policy": "strict-origin-when-cross-origin",

  // Permissions Policy (formerly Feature Policy)
  "Permissions-Policy": "geolocation=(), microphone=(), camera=(), payment=()",

  // Content Security Policy (comprehensive - 2025)
  "Content-Security-Policy": [
    "default-src 'self'",
    "script-src 'self' 'unsafe-inline' 'unsafe-eval' https://cdn.example.com",
    "style-src 'self' 'unsafe-inline' https://fonts.googleapis.com",
    "img-src 'self' data: https: blob:",
    "font-src 'self' https://fonts.gstatic.com",
    "connect-src 'self' https://api.example.com",
    "frame-ancestors 'none'",
    "base-uri 'self'",
    "form-action 'self'",
    "upgrade-insecure-requests",
  ].join("; "),

  // Cross-Origin policies (2025)
  "Cross-Origin-Embedder-Policy": "require-corp",
  "Cross-Origin-Opener-Policy": "same-origin",
  "Cross-Origin-Resource-Policy": "same-origin",
};
```

### Platform-Specific Configuration (2025)

```javascript
// ═══════════════════════════════════════════
// VERCEL - vercel.json
// ═══════════════════════════════════════════

{
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        {
          "key": "X-Content-Type-Options",
          "value": "nosniff"
        },
        {
          "key": "X-Frame-Options",
          "value": "DENY"
        },
        {
          "key": "X-XSS-Protection",
          "value": "1; mode=block"
        },
        {
          "key": "Strict-Transport-Security",
          "value": "max-age=31536000; includeSubDomains; preload"
        },
        {
          "key": "Referrer-Policy",
          "value": "strict-origin-when-cross-origin"
        },
        {
          "key": "Permissions-Policy",
          "value": "geolocation=(), microphone=(), camera=()"
        },
        {
          "key": "Content-Security-Policy",
          "value": "default-src 'self'; script-src 'self' 'unsafe-inline' 'unsafe-eval'; style-src 'self' 'unsafe-inline'; img-src 'self' data: https:; font-src 'self' data:; connect-src 'self' https://api.example.com"
        },
        {
          "key": "Cross-Origin-Embedder-Policy",
          "value": "require-corp"
        },
        {
          "key": "Cross-Origin-Opener-Policy",
          "value": "same-origin"
        }
      ]
    },
    {
      "source": "/assets/(.*)",
      "headers": [
        {
          "key": "Cache-Control",
          "value": "public, max-age=31536000, immutable"
        }
      ]
    }
  ]
}

// ═══════════════════════════════════════════
// NETLIFY - netlify.toml
// ═══════════════════════════════════════════

[[headers]]
  for = "/*"
  [headers.values]
    X-Frame-Options = "DENY"
    X-Content-Type-Options = "nosniff"
    X-XSS-Protection = "1; mode=block"
    Referrer-Policy = "strict-origin-when-cross-origin"
    Permissions-Policy = "geolocation=(), microphone=(), camera=()"
    Strict-Transport-Security = "max-age=31536000; includeSubDomains; preload"
    Content-Security-Policy = "default-src 'self'; script-src 'self' 'unsafe-inline'; style-src 'self' 'unsafe-inline'; img-src 'self' data: https:; font-src 'self' data:"
    Cross-Origin-Embedder-Policy = "require-corp"
    Cross-Origin-Opener-Policy = "same-origin"

[[headers]]
  for = "/assets/*"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

[[headers]]
  for = "/*.js"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

[[headers]]
  for = "/*.css"
  [headers.values]
    Cache-Control = "public, max-age=31536000, immutable"

// ═══════════════════════════════════════════
// CLOUDFLARE PAGES - _headers file
// ═══════════════════════════════════════════

/*
  X-Frame-Options: DENY
  X-Content-Type-Options: nosniff
  X-XSS-Protection: 1; mode=block
  Referrer-Policy: strict-origin-when-cross-origin
  Permissions-Policy: geolocation=(), microphone=(), camera=()
  Strict-Transport-Security: max-age=31536000; includeSubDomains; preload
  Content-Security-Policy: default-src 'self'; script-src 'self' 'unsafe-inline'; style-src 'self' 'unsafe-inline'; img-src 'self' data: https:
  Cross-Origin-Embedder-Policy: require-corp
  Cross-Origin-Opener-Policy: same-origin

/assets/*
  Cache-Control: public, max-age=31536000, immutable

/*.js
  Cache-Control: public, max-age=31536000, immutable

/*.css
  Cache-Control: public, max-age=31536000, immutable

// ═══════════════════════════════════════════
// NEXT.JS - next.config.js (2025)
// ═══════════════════════════════════════════

/** @type {import('next').NextConfig} */
const nextConfig = {
  async headers() {
    return [
      {
        source: '/:path*',
        headers: [
          {
            key: 'X-DNS-Prefetch-Control',
            value: 'on'
          },
          {
            key: 'Strict-Transport-Security',
            value: 'max-age=63072000; includeSubDomains; preload'
          },
          {
            key: 'X-Frame-Options',
            value: 'SAMEORIGIN'
          },
          {
            key: 'X-Content-Type-Options',
            value: 'nosniff'
          },
          {
            key: 'X-XSS-Protection',
            value: '1; mode=block'
          },
          {
            key: 'Referrer-Policy',
            value: 'strict-origin-when-cross-origin'
          },
          {
            key: 'Permissions-Policy',
            value: 'camera=(), microphone=(), geolocation=()'
          },
          {
            key: 'Content-Security-Policy',
            value: `
              default-src 'self';
              script-src 'self' 'unsafe-eval' 'unsafe-inline';
              style-src 'self' 'unsafe-inline';
              img-src 'self' data: blob: https:;
              font-src 'self';
              connect-src 'self' https://api.example.com;
              frame-ancestors 'none';
            `.replace(/\s{2,}/g, ' ').trim()
          }
        ]
      }
    ];
  }
};

module.exports = nextConfig;
```

### Testing Security Headers (2025)

```bash
# ═══════════════════════════════════════════
# TEST YOUR SECURITY HEADERS
# ═══════════════════════════════════════════

# Using curl
curl -I https://your-site.com

# Check specific header
curl -I https://your-site.com | grep -i "x-frame-options"

# Online tools (2025):
# • https://securityheaders.com (most popular)
# • https://observatory.mozilla.org (comprehensive)
# • https://csp-evaluator.withgoogle.com (CSP specific)
# • https://hstspreload.org (HSTS submission)

# Automated testing with Playwright (2025)
// security-test.spec.js
import { test, expect } from '@playwright/test';

test('should have security headers', async ({ page }) => {
  const response = await page.goto('https://your-site.com');

  const headers = response.headers();

  expect(headers['x-frame-options']).toBe('DENY');
  expect(headers['x-content-type-options']).toBe('nosniff');
  expect(headers['strict-transport-security']).toContain('max-age=31536000');
  expect(headers['referrer-policy']).toBeTruthy();
  expect(headers['content-security-policy']).toBeTruthy();
});

# Run test
npx playwright test security-test.spec.js

# ═══════════════════════════════════════════
# SECURITY HEADER GRADES (2025)
# ═══════════════════════════════════════════

A+ RATING REQUIREMENTS:
✅ Strict-Transport-Security
✅ Content-Security-Policy
✅ X-Content-Type-Options
✅ X-Frame-Options or CSP frame-ancestors
✅ Referrer-Policy
✅ Permissions-Policy

BONUS POINTS:
✅ Cross-Origin-Embedder-Policy
✅ Cross-Origin-Opener-Policy
✅ Cross-Origin-Resource-Policy

⚠️ COMMON MISTAKES:
❌ Missing CSP
❌ CSP with 'unsafe-inline' and 'unsafe-eval'
❌ No HSTS
❌ Using X-XSS-Protection (deprecated in modern browsers)
❌ Loose CORS policies
```

---

<div align="center">

## 🌍 Custom Domains

_Use your own domain name_ 🎯

</div>

### DNS Configuration (2025 Guide)

```bash
# ═══════════════════════════════════════════
# DNS SETUP FOR DIFFERENT PLATFORMS (2025)
# ═══════════════════════════════════════════

# ─────────────────────────────────────────────
# VERCEL (2025 UPDATE)
# ─────────────────────────────────────────────

# 1. Add domain in Vercel dashboard
# Project → Settings → Domains → Add

# 2. Configure DNS (at your domain provider)

# METHOD A: Vercel Nameservers (RECOMMENDED)
# Use Vercel's nameservers for automatic configuration
NS records:
  ns1.vercel-dns.com
  ns2.vercel-dns.com

# METHOD B: A/CNAME Records
# For apex domain (example.com):
A     @     76.76.21.21

# For www subdomain:
CNAME www   cname.vercel-dns.com

# 3. Enable in GitHub
# Vercel handles SSL automatically ✨
# DNS propagation: Usually 5-60 minutes

# ─────────────────────────────────────────────
# NETLIFY (2025 UPDATE)
# ─────────────────────────────────────────────

# 1. Add domain in Netlify
# Site settings → Domain management → Add custom domain

# 2. Configure DNS

# METHOD A: Netlify DNS (RECOMMENDED)
# Use Netlify's nameservers
NS records:
  dns1.p05.nsone.net
  dns2.p05.nsone.net
  dns3.p05.nsone.net
  dns4.p05.nsone.net

# METHOD B: External DNS
# For apex domain:
A     @     75.2.60.5

# For www:
CNAME www   your-site.netlify.app

# For both apex and www (2025 best practice):
ALIAS @     your-site.netlify.app  # If your DNS supports ALIAS
CNAME www   your-site.netlify.app

# 3. SSL/TLS
# Automatic Let's Encrypt certificate
# Force HTTPS: Site settings → Domain management → HTTPS

# ─────────────────────────────────────────────
# CLOUDFLARE PAGES (2025 - EASIEST!)
# ─────────────────────────────────────────────

# If domain already on Cloudflare:
# 1. Go to Pages → Your Project → Custom domains
# 2. Click "Set up a custom domain"
# 3. Select your domain
# 4. Done! ✨ (Automatic DNS configuration)

# If domain NOT on Cloudflare:
# 1. Add domain in Pages
# 2. Add DNS record at current provider:

CNAME www   your-project.pages.dev

# Or transfer domain to Cloudflare (recommended)
# - Free DNS
# - Free SSL
# - Free DDoS protection
# - Better performance

# ─────────────────────────────────────────────
# GITHUB PAGES (2025 UPDATE)
# ─────────────────────────────────────────────

# 1. Add CNAME file to repository
echo "www.example.com" > CNAME

# 2. Configure DNS

# For apex domain (example.com):
A     @     185.199.108.153
A     @     185.199.109.153
A     @     185.199.110.153
A     @     185.199.111.153

# For www subdomain:
CNAME www   username.github.io

# 3. Enable in GitHub
# Settings → Pages → Custom domain → www.example.com
# ✅ Enforce HTTPS (wait for DNS to propagate first)

# 4. Wait for DNS propagation (can take up to 24 hours)

# ─────────────────────────────────────────────
# RENDER (2025)
# ─────────────────────────────────────────────

# 1. Add custom domain in Render
# Dashboard → Your Service → Settings → Custom Domains

# 2. Configure DNS
CNAME www   your-site.onrender.com

# For apex domain (if DNS supports ALIAS):
ALIAS @     your-site.onrender.com

# 3. SSL automatic via Let's Encrypt

# ═══════════════════════════════════════════
# SUBDOMAIN SETUP (ALL PLATFORMS)
# ═══════════════════════════════════════════

# For blog.example.com:
CNAME blog  your-site.platform.com

# For api.example.com:
CNAME api   your-api.platform.com

# For docs.example.com:
CNAME docs  your-docs.platform.com

# ═══════════════════════════════════════════
# VERIFY DNS PROPAGATION
# ═══════════════════════════════════════════

# Check DNS records (2025 tools)
dig example.com
dig www.example.com

# Check from specific DNS server
dig @8.8.8.8 example.com        # Google DNS
dig @1.1.1.1 example.com        # Cloudflare DNS
dig @208.67.222.222 example.com # OpenDNS

# Online tools (2025):
# • https://dnschecker.org (check worldwide)
# • https://www.whatsmydns.net (visual map)
# • https://mxtoolbox.com/SuperTool.aspx (comprehensive)

# Wait for propagation
# Typical times:
# - A records: 5-60 minutes
# - CNAME records: 5-60 minutes
# - NS records: 24-48 hours

# Force DNS flush (your computer)
# macOS:
sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder

# Windows:
ipconfig /flushdns

# Linux:
sudo systemd-resolve --flush-caches

# ═══════════════════════════════════════════
# APEX DOMAIN vs WWW (2025 BEST PRACTICES)
# ═══════════════════════════════════════════

RECOMMENDATION: Use WWW subdomain

WHY:
✅ More flexible (can use CNAME)
✅ Easier to change hosting
✅ Better for CDN
✅ Standard practice for large sites

REDIRECT APEX TO WWW:
# Most platforms handle this automatically
# Or configure in DNS:

# Cloudflare: Page Rules
# example.com/* → https://www.example.com/$1 (301)

# Netlify: netlify.toml
[[redirects]]
  from = "https://example.com/*"
  to = "https://www.example.com/:splat"
  status = 301
  force = true

# Vercel: vercel.json
{
  "redirects": [
    {
      "source": "/:path*",
      "has": [
        {
          "type": "host",
          "value": "example.com"
        }
      ],
      "destination": "https://www.example.com/:path*",
      "permanent": true
    }
  ]
}
```

### SSL/TLS Certificates (2025)

```bash
# ═══════════════════════════════════════════
# SSL CERTIFICATES (AUTOMATIC IN 2025!)
# ═══════════════════════════════════════════

# All major platforms provide automatic SSL via Let's Encrypt
# - Vercel: Automatic ✅
# - Netlify: Automatic ✅
# - Cloudflare Pages: Automatic ✅
# - GitHub Pages: Automatic ✅ (after DNS verification)
# - Render: Automatic ✅

# No configuration needed! 🎉

# Features (2025):
# ✅ Free SSL certificates
# ✅ Auto-renewal (no expiration!)
# ✅ Wildcard SSL (*.example.com)
# ✅ Force HTTPS redirect
# ✅ HSTS preload support
# ✅ TLS 1.3 support

# ═══════════════════════════════════════════
# FORCE HTTPS (2025)
# ═══════════════════════════════════════════

# Usually enabled by default, or toggle in platform settings

# Vercel: Automatic
# Netlify: Site settings → Domain management → HTTPS → Force HTTPS
# Cloudflare: SSL/TLS → Edge Certificates → Always Use HTTPS
# GitHub Pages: Settings → Pages → Enforce HTTPS

# ═══════════════════════════════════════════
# CUSTOM SSL CERTIFICATE (ADVANCED)
# ═══════════════════════════════════════════

# Only needed for:
# - Enterprise requirements
# - Extended Validation (EV) certificates
# - Specific compliance needs

# Vercel Pro/Enterprise:
# Project → Settings → Domains → Custom SSL

# Netlify:
# Site settings → Domain management → HTTPS → Provide certificate

# Files needed:
# - Certificate (.crt or .pem)
# - Private key (.key)
# - Certificate chain (intermediate certificates)

# ═══════════════════════════════════════════
# SSL TESTING (2025)
# ═══════════════════════════════════════════

# Online tools:
# • https://www.ssllabs.com/ssltest/ (most comprehensive)
# • https://www.wormly.com/test_ssl
# • https://observatory.mozilla.org

# Check SSL certificate
openssl s_client -connect example.com:443 -servername example.com

# Check SSL expiration
echo | openssl s_client -servername example.com -connect example.com:443 2>/dev/null | openssl x509 -noout -dates

# Target: A+ rating on SSL Labs
```

---

<div align="center">

## 🚀 CI/CD Integration

_Automate your deployments_ ⚙️

</div>

### GitHub Actions Examples (2025)

```yaml
# ═══════════════════════════════════════════
# .github/workflows/deploy-vercel.yml (2025)
# ═══════════════════════════════════════════

name: Deploy to Vercel

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

env:
  VERCEL_ORG_ID: ${{ secrets.VERCEL_ORG_ID }}
  VERCEL_PROJECT_ID: ${{ secrets.VERCEL_PROJECT_ID }}

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'

      - name: Install dependencies
        run: npm ci

      - name: Run tests
        run: npm test

      - name: Run linter
        run: npm run lint

  deploy-preview:
    needs: test
    if: github.event_name == 'pull_request'
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Install Vercel CLI
        run: npm install --global vercel@latest

      - name: Pull Vercel Environment Information
        run: vercel pull --yes --environment=preview --token=${{ secrets.VERCEL_TOKEN }}

      - name: Build Project Artifacts
        run: vercel build --token=${{ secrets.VERCEL_TOKEN }}

      - name: Deploy Preview to Vercel
        run: vercel deploy --prebuilt --token=${{ secrets.VERCEL_TOKEN }}

  deploy-production:
    needs: test
    if: github.event_name == 'push' && github.ref == 'refs/heads/main'
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Install Vercel CLI
        run: npm install --global vercel@latest

      - name: Pull Vercel Environment Information
        run: vercel pull --yes --environment=production --token=${{ secrets.VERCEL_TOKEN }}

      - name: Build Project Artifacts
        run: vercel build --prod --token=${{ secrets.VERCEL_TOKEN }}

      - name: Deploy Production to Vercel
        run: vercel deploy --prebuilt --prod --token=${{ secrets.VERCEL_TOKEN }}

# ═══════════════════════════════════════════
# .github/workflows/deploy-netlify.yml (2025)
# ═══════════════════════════════════════════

name: Deploy to Netlify

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'

      - name: Install dependencies
        run: npm ci

      - name: Run tests
        run: npm test

      - name: Build
        run: npm run build
        env:
          NODE_ENV: production
          REACT_APP_API_URL: ${{ secrets.API_URL }}

      - name: Deploy to Netlify
        uses: netlify/actions/cli@master
        env:
          NETLIFY_AUTH_TOKEN: ${{ secrets.NETLIFY_AUTH_TOKEN }}
          NETLIFY_SITE_ID: ${{ secrets.NETLIFY_SITE_ID }}
        with:
          args: deploy --prod --dir=dist --message="Deploy from GitHub Actions"

      - name: Comment PR with deploy URL
        if: github.event_name == 'pull_request'
        uses: actions/github-script@v7
        with:
          script: |
            github.rest.issues.createComment({
              issue_number: context.issue.number,
              owner: context.repo.owner,
              repo: context.repo.repo,
              body: '🚀 Preview deployed to Netlify!'
            })

# ═══════════════════════════════════════════
# .github/workflows/deploy-pages.yml (2025)
# ═══════════════════════════════════════════

name: Deploy to GitHub Pages

on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'

      - name: Install dependencies
        run: npm ci

      - name: Run tests
        run: npm test

      - name: Build
        run: npm run build
        env:
          NODE_ENV: production

      - name: Setup Pages
        uses: actions/configure-pages@v4

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./dist

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4

# ═══════════════════════════════════════════
# .github/workflows/lighthouse.yml (2025)
# ═══════════════════════════════════════════

name: Lighthouse CI

on:
  pull_request:
    branches: [main]

jobs:
  lighthouse:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'

      - name: Install dependencies
        run: npm ci

      - name: Build
        run: npm run build

      - name: Run Lighthouse CI
        uses: treosh/lighthouse-ci-action@v10
        with:
          urls: |
            http://localhost:3000
            http://localhost:3000/about
          budgetPath: ./budget.json
          uploadArtifacts: true
          temporaryPublicStorage: true

# ═══════════════════════════════════════════
# .github/workflows/security-scan.yml (2025)
# ═══════════════════════════════════════════

name: Security Scan

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]
  schedule:
    - cron: '0 0 * * 0'  # Weekly

jobs:
  security:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Run npm audit
        run: npm audit --production

      - name: Run Snyk security scan
        uses: snyk/actions/node@master
        env:
          SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}

      - name: Check dependencies
        run: npx depcheck

      - name: Scan for secrets
        uses: trufflesecurity/trufflehog@main
        with:
          path: ./

# ═══════════════════════════════════════════
# .github/workflows/preview-cleanup.yml (2025)
# ═══════════════════════════════════════════

name: Cleanup Preview Deployments

on:
  pull_request:
    types: [closed]

jobs:
  cleanup:
    runs-on: ubuntu-latest
    steps:
      - name: Delete preview deployment
        run: |
          # Add cleanup logic for your platform
          echo "Cleaning up preview deployment"
```

### GitLab CI/CD Example (2025)

```yaml
# ═══════════════════════════════════════════
# .gitlab-ci.yml (2025)
# ═══════════════════════════════════════════

stages:
  - test
  - build
  - deploy

variables:
  NODE_VERSION: "20"

cache:
  paths:
    - node_modules/
    - .next/cache/

test:
  stage: test
  image: node:20
  script:
    - npm ci
    - npm run lint
    - npm test
  only:
    - merge_requests
    - main

build:
  stage: build
  image: node:20
  script:
    - npm ci
    - npm run build
  artifacts:
    paths:
      - dist/
    expire_in: 1 hour
  only:
    - main

deploy_netlify:
  stage: deploy
  image: node:20
  script:
    - npm install -g netlify-cli
    - netlify deploy --prod --dir=dist --site=$NETLIFY_SITE_ID --auth=$NETLIFY_AUTH_TOKEN
  only:
    - main
  when: manual

deploy_vercel:
  stage: deploy
  image: node:20
  script:
    - npm install -g vercel
    - vercel --token=$VERCEL_TOKEN --prod
  only:
    - main
  when: manual
```

---

<div align="center">

## 🐛 Troubleshooting

_Common issues and solutions_ 🔧

</div>

### Common Issues (2025)

```bash
# ═══════════════════════════════════════════
# BUILD FAILURES
# ═══════════════════════════════════════════

# ❌ Issue: "Command failed with exit code 1"
# ✅ Solution:
# 1. Check build logs for specific error
# 2. Test build locally: npm run build
# 3. Check Node version matches
# 4. Clear cache and rebuild

# Vercel:
vercel --force

# Netlify:
# Site settings → Build & deploy → Clear cache and deploy site

# GitHub Actions:
# Re-run workflow with cache disabled

# ❌ Issue: "Out of memory"
# ✅ Solution:
# Increase Node memory limit

# package.json
{
  "scripts": {
    "build": "NODE_OPTIONS='--max-old-space-size=4096' next build"
  }
}

# Or use environment variable
export NODE_OPTIONS=--max-old-space-size=4096
npm run build

# ❌ Issue: "Module not found"
# ✅ Solution:
# 1. Check case sensitivity (Linux is case-sensitive!)
# 2. Verify import paths
# 3. Check node_modules is not in .gitignore
# 4. Delete node_modules and reinstall:
rm -rf node_modules package-lock.json
npm install

# ═══════════════════════════════════════════
# DEPLOYMENT ISSUES
# ═══════════════════════════════════════════

# ❌ Issue: "404 on refresh" (SPA)
# ✅ Solution: Add SPA fallback

# Vercel (vercel.json):
{
  "rewrites": [{ "source": "/(.*)", "destination": "/index.html" }]
}

# Netlify (_redirects or netlify.toml):
/*    /index.html   200

# Cloudflare Pages (_redirects):
/*    /index.html   200

# ❌ Issue: "Environment variables not working"
# ✅ Solution:
# 1. Check variable names (must start with NEXT_PUBLIC_, REACT_APP_, VITE_, etc.)
# 2. Rebuild after adding variables
# 3. Check if variables are set in correct environment (preview vs production)

# ❌ Issue: "Custom domain not working"
# ✅ Solution:
# 1. Check DNS propagation: dig yourdomain.com
# 2. Wait 24-48 hours for full propagation
# 3. Clear DNS cache locally
# 4. Verify DNS records are correct
# 5. Check domain is not in "pending" state

# ❌ Issue: "SSL certificate error"
# ✅ Solution:
# 1. Wait for automatic provisioning (can take up to 24 hours)
# 2. Remove and re-add domain
# 3. Check DNS is pointing correctly
# 4. Force SSL renewal in platform settings

# ═══════════════════════════════════════════
# PERFORMANCE ISSUES
# ═══════════════════════════════════════════

# ❌ Issue: "Slow page loads"
# ✅ Solution:
# 1. Run Lighthouse audit
# 2. Optimize images (use WebP/AVIF)
# 3. Enable compression (automatic on most platforms)
# 4. Check for large bundle sizes
# 5. Use code splitting

# Analyze bundle size:
# Next.js:
ANALYZE=true npm run build

# Vite:
npm run build -- --mode analyze

# ❌ Issue: "High bandwidth usage"
# ✅ Solution:
# 1. Enable CDN caching (automatic)
# 2. Compress images
# 3. Use external CDN for large assets
# 4. Check for unnecessary API calls
# 5. Enable Brotli compression

# ═══════════════════════════════════════════
# VERCEL SPECIFIC ISSUES (2025)
# ═══════════════════════════════════════════

# ❌ Issue: "Edge requests too high"
# ✅ Solution:
# 1. Use external CDN for static assets
# 2. Implement proper caching
# 3. Reduce number of requests per page
# 4. Use Image Optimization sparingly

# ❌ Issue: "Function timeout"
# ✅ Solution:
# Upgrade to Pro plan (10s → 15 min timeout)
# Or optimize function code
# Or move heavy processing to background job

# ❌ Issue: "ISR not working"
# ✅ Solution:
# Check revalidate time is set correctly:
export const revalidate = 60;

# ═══════════════════════════════════════════
# DEBUGGING TIPS (2025)
# ═══════════════════════════════════════════

# 1. Check deployment logs
# All platforms provide detailed build logs

# 2. Test locally first
npm run build
npm run start

# 3. Check browser console
# Look for JavaScript errors

# 4. Use preview deployments
# Test changes before production

# 5. Check platform status pages
# - status.vercel.com
# - netlifystatus.com
# - cloudflarestatus.com
# - githubstatus.com

# 6. Enable verbose logging
# Most build tools support --verbose flag
npm run build --verbose

# 7. Check network tab
# Look for failed requests, slow resources

# 8. Use platform-specific debugging
# Vercel: vercel logs deployment-url
# Netlify: netlify logs
```

---

<div align="center">

## 💡 Best Practices

_Build better static sites_ ⭐

</div>

### 2025 Best Practices

```bash
# ═══════════════════════════════════════════
# PROJECT STRUCTURE
# ═══════════════════════════════════════════

my-static-site/
├── .github/
│   └── workflows/           # CI/CD
│       ├── deploy.yml
│       └── lighthouse.yml
├── public/                  # Static assets
│   ├── images/
│   ├── fonts/
│   └── favicon.ico
├── src/
│   ├── components/         # Reusable components
│   ├── pages/             # Page components
│   ├── styles/            # CSS/SCSS
│   └── utils/             # Helper functions
├── .env.example           # Environment variables template
├── .gitignore
├── package.json
├── README.md
├── vercel.json           # or netlify.toml
└── lighthouse-budget.json

# ═══════════════════════════════════════════
# PERFORMANCE BEST PRACTICES (2025)
# ═══════════════════════════════════════════

✅ IMAGE OPTIMIZATION:
• Use next/image or similar
• Serve WebP/AVIF formats
• Implement lazy loading
• Use responsive images
• Optimize file sizes (<100KB per image)
• Use CDN for images

✅ CODE OPTIMIZATION:
• Code split by route
• Dynamic imports for heavy components
• Tree shake unused code
• Minify CSS/JS (automatic)
• Remove console.logs in production

✅ CACHING STRATEGY:
• Cache static assets aggressively (1 year)
• Use cache busting (hashes in filenames)
• Implement service worker
• Use stale-while-revalidate

✅ LOADING STRATEGY:
• Preload critical resources
• Defer non-critical scripts
• Use font-display: swap
• Lazy load below-the-fold content

✅ MONITORING:
• Track Core Web Vitals
• Set up performance budgets
• Monitor bundle sizes
• Use Real User Monitoring (RUM)

# ═══════════════════════════════════════════
# SEO BEST PRACTICES (2025)
# ═══════════════════════════════════════════

✅ MUST HAVE:
• Unique title tags (50-60 chars)
• Meta descriptions (150-160 chars)
• Semantic HTML (h1, h2, nav, main, etc.)
• Alt text on all images
• Sitemap.xml
• robots.txt
• Canonical URLs
• Open Graph tags
• Schema.org markup
• Mobile-friendly design
• Fast loading (LCP < 2.5s)

✅ CONTENT:
• High-quality, original content
• Proper heading hierarchy (H1 → H2 → H3)
• Internal linking
• Regular updates
• Readable URLs (/blog/post-name)

# ═══════════════════════════════════════════
# SECURITY BEST PRACTICES (2025)
# ═══════════════════════════════════════════

✅ HEADERS:
• Strict-Transport-Security
• Content-Security-Policy
• X-Content-Type-Options: nosniff
• X-Frame-Options: DENY
• Referrer-Policy
• Permissions-Policy

✅ DEPENDENCIES:
• Run npm audit regularly
• Keep dependencies updated
• Use Dependabot/Renovate
• Remove unused packages
• Check for known vulnerabilities

✅ SECRETS:
• Never commit secrets to Git
• Use environment variables
• Use .env.example for documentation
• Rotate secrets regularly

# ═══════════════════════════════════════════
# DEPLOYMENT BEST PRACTICES (2025)
# ═══════════════════════════════════════════

✅ CI/CD:
• Automated testing
• Automated linting
• Automated deployment
• Preview deployments for PRs
• Rollback capability

✅ ENVIRONMENTS:
• Development
• Staging
• Production
• Use different environment variables

✅ MONITORING:
• Uptime monitoring
• Error tracking (Sentry)
• Analytics (Google Analytics, Plausible)
• Performance monitoring
• Cost monitoring

# ═══════════════════════════════════════════
# COST OPTIMIZATION (2025)
# ═══════════════════════════════════════════

✅ REDUCE EDGE REQUESTS:
• Use external CDN for static assets
• Implement proper caching
• Reduce assets per page
• Combine small files

✅ REDUCE BANDWIDTH:
• Compress images
• Enable Brotli compression
• Use efficient formats (WebP, AVIF)
• Lazy load images
• Trim unused CSS/JS

✅ OPTIMIZE BUILDS:
• Cache node_modules
• Use incremental builds
• Parallel builds when possible
• Disable source maps in production

✅ CHOOSE RIGHT PLATFORM:
• GitHub Pages: Free forever
• Cloudflare Pages: Unlimited bandwidth
• Netlify/Vercel: Great DX, but watch usage
• Render: Predictable pricing

# ═══════════════════════════════════════════
# DEVELOPER EXPERIENCE (2025)
# ═══════════════════════════════════════════

✅ TOOLING:
• Use TypeScript
• ESLint + Prettier
• Git hooks (husky)
• VS Code extensions
• Hot reload in development

✅ DOCUMENTATION:
• README with setup instructions
• API documentation
• Deployment guide
• Contributing guidelines
• Code comments where needed

✅ VERSION CONTROL:
• Meaningful commit messages
• Feature branches
• Pull request reviews
• Semantic versioning
• CHANGELOG.md

# ═══════════════════════════════════════════
# ACCESSIBILITY (2025)
# ═══════════════════════════════════════════

✅ MUST HAVE:
• Semantic HTML
• ARIA labels where needed
• Keyboard navigation
• Sufficient color contrast (WCAG AA)
• Alt text on images
• Focus indicators
• Skip to main content link

✅ TESTING:
• Lighthouse accessibility audit
• axe DevTools
• Screen reader testing
• Keyboard-only navigation test

# ═══════════════════════════════════════════
# INTERNATIONALIZATION (i18n) (2025)
# ═══════════════════════════════════════════

✅ IMPLEMENTATION:
• Use i18n library (next-i18next, react-i18next)
• Language detection
• URL structure (/en/, /es/)
• hreflang tags
• Localized content
• Date/number formatting

# ═══════════════════════════════════════════
# MAINTENANCE (2025)
# ═══════════════════════════════════════════

✅ REGULAR TASKS:
• Update dependencies monthly
• Review and fix security alerts
• Monitor performance metrics
• Check and fix broken links
• Review and update content
• Backup strategy
• Test backups regularly
```

---

<div align="center">

## 🏆 Final Recommendations

### _The Ultimate Static Hosting Stack (2025)_ 🚀

</div>

```yaml
# ═══════════════════════════════════════════
# MRDIB'S RECOMMENDED STACKS (2025)
# ═══════════════════════════════════════════

# ─────────────────────────────────────────────
# 🥇 BEST FOR NEXT.JS APPLICATIONS
# ─────────────────────────────────────────────
Platform: Vercel
Cost: Free tier or $20/mo Pro
Why:
  ✅ Built by Next.js creators
  ✅ Best Next.js integration
  ✅ Edge functions
  ✅ Preview deployments
  ✅ Excellent DX
Tip: Use external CDN (Bunny) for static assets to reduce edge requests

# ─────────────────────────────────────────────
# 💰 BEST FOR BUDGET (HIGH TRAFFIC)
# ─────────────────────────────────────────────
Platform: Cloudflare Pages
Cost: Free (unlimited bandwidth!)
Why:
  ✅ Unlimited bandwidth
  ✅ 300+ edge locations
  ✅ Free Web Analytics
  ✅ D1 Database (free tier)
  ✅ R2 Storage (free tier)
  ✅ Best CDN performance
Perfect for: High-traffic blogs, documentation, marketing sites

# ─────────────────────────────────────────────
# 🎯 BEST FOR JAMSTACK + FORMS
# ─────────────────────────────────────────────
Platform: Netlify
Cost: Free tier or $19/mo Pro
Why:
  ✅ Built-in forms
  ✅ Built-in authentication
  ✅ Build plugins ecosystem
  ✅ Split testing
  ✅ Predictable pricing
Perfect for: Landing pages, marketing sites, client projects

# ─────────────────────────────────────────────
# 📚 BEST FOR DOCUMENTATION/OPEN SOURCE
# ─────────────────────────────────────────────
Platform: GitHub Pages
Cost: Free forever
Why:
  ✅ 100% free
  ✅ Integrated with GitHub
  ✅ Jekyll built-in
  ✅ Custom domains free
  ✅ Perfect for docs
Perfect for: Project documentation, personal sites, open source

# ─────────────────────────────────────────────
# 🔧 BEST FOR FULL-STACK APPS
# ─────────────────────────────────────────────
Platform: Render
Cost: $0 (static) + $7/mo (backend)
Why:
  ✅ Static + backend in one place
  ✅ Free static hosting
  ✅ Postgres, Redis included
  ✅ Predictable pricing
  ✅ Docker support
Perfect for: Full-stack startups, SaaS apps

# ─────────────────────────────────────────────
# ⚡ BEST FOR QUICK PROTOTYPES
# ─────────────────────────────────────────────
Platform: Surge
Cost: Free
Why:
  ✅ Deploy in <10 seconds
  ✅ One command: surge
  ✅ No configuration
  ✅ Perfect for demos
Perfect for: Quick demos, client previews, testing

# ═══════════════════════════════════════════
# HYBRID APPROACH (RECOMMENDED FOR PRODUCTION)
# ═══════════════════════════════════════════

Frontend: Vercel (Next.js)
Backend: Render ($7-20/mo)
Static Assets: Bunny CDN ($1-2/mo)
Database: Render Postgres or Supabase
Total Cost: ~$30-50/month for high-traffic apps

Benefits:
✅ Best-in-class frontend performance
✅ Reliable backend
✅ Cost-effective at scale
✅ Easy to manage

# ═══════════════════════════════════════════
# DECISION FLOWCHART
# ═══════════════════════════════════════════

┌─────────────────────────────────────┐
│   What are you building?            │
└─────────────────────────────────────┘
           │
           ├─→ Next.js app? → Vercel
           │
           ├─→ High traffic blog/docs? → Cloudflare Pages
           │
           ├─→ Need forms/auth? → Netlify
           │
           ├─→ Open source docs? → GitHub Pages
           │
           ├─→ Full-stack app? → Render
           │
           └─→ Quick prototype? → Surge

# ═══════════════════════════════════════════
# BUDGET-BASED RECOMMENDATIONS
# ═══════════════════════════════════════════

$0/month:
• GitHub Pages (static only)
• Cloudflare Pages (unlimited bandwidth!)
• Surge (basic features)

$0-20/month:
• Vercel Pro ($20/user)
• Netlify Pro ($19/member)
• Cloudflare Pages Pro ($20/month)

$20-50/month:
• Vercel Pro + Bunny CDN + Backend
• Render (static + backend + database)
• Netlify Pro + Functions

$50+/month:
• Vercel Pro with high usage
• Netlify Pro with high usage
• Enterprise plans ($20k+/year)
```

---

<div align="center">

## 🎓 Additional Resources

### _Learn more_ 📚

</div>

**📖 Official Documentation:**

- Vercel: https://vercel.com/docs
- Netlify: https://docs.netlify.com
- Cloudflare Pages: https://developers.cloudflare.com/pages
- GitHub Pages: https://docs.github.com/pages
- Render: https://render.com/docs

**🎥 Video Tutorials:**

- Fireship (YouTube) - Platform comparisons
- Traversy Media - Deployment tutorials
- Web Dev Simplified - Best practices

**📊 Comparison Tools:**

- https://getdeploying.com - Platform comparison
- https://jamstack.org - JAMstack resources

**🛠️ Tools:**

- Lighthouse CI - Performance testing
- securityheaders.com - Security audit
- web.dev - Performance best practices
- bundlephobia.com - Bundle size checker

---

<div align="center">

## 🤝 Contributing

Found something missing? Want to add a platform or update information?

**Contributions are welcome!**

1. Fork the repository
2. Add your improvements
3. Submit a pull request

---

## 📄 License

This guide is open source and available under the MIT License.

---

**Built with 🌐 by MrDib, for developers who ship fast**

_"The best deployment is one you don't have to think about."_ ✨

**Happy Deploying!** 🚀

**If you found this helpful, ⭐ star the repo and share with fellow developers!**

</div>

---

<div align="center">

### Remember

> _"Choose the platform that fits your needs, not your hype."_

> _"Free tiers are generous, but always monitor your usage."_

> _"Performance matters - your users will thank you."_

> _"Automate everything - from testing to deployment."_

**Now go forth and deploy with confidence!** 🌟💪

**#StaticHosting #DevResourceVault #MrDib #2025**

</div>
