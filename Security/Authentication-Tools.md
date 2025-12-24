<div align="center">

# 🔐 Authentication Tools - Complete Implementation Guide

![Authentication](https://img.shields.io/badge/Authentication-Tools-blue?style=for-the-badge&logo=auth0)
![Security](https://img.shields.io/badge/Security-First-red?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-All_Levels-green?style=for-the-badge)

### _Because authentication is the gateway to your application_ 🚪

**One weak authentication = Complete compromise** 🔓

</div>

---

## 📚 Table of Contents

- [🎯 Authentication Fundamentals](#-authentication-fundamentals)
- [🔑 Authentication Methods](#-authentication-methods)
- [🛠️ Popular Auth Tools](#️-popular-auth-tools)
- [🎫 Session-Based Authentication](#-session-based-authentication)
- [🎟️ Token-Based Authentication (JWT)](#️-token-based-authentication-jwt)
- [🌐 OAuth 2.0 & Social Login](#-oauth-20--social-login)
- [📱 Multi-Factor Authentication](#-multi-factor-authentication)
- [🔐 Passwordless Authentication](#-passwordless-authentication)
- [🏢 Enterprise Solutions](#-enterprise-solutions)
- [⚙️ Implementation Guides](#️-implementation-guides)
- [✅ Security Best Practices](#-security-best-practices)

---

<div align="center">

## 🎯 Authentication Fundamentals

</div>

### Authentication vs Authorization 🤔

```bash
# ═══════════════════════════════════════════
# THE DIFFERENCE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   AUTHENTICATION vs AUTHORIZATION          ║
╚════════════════════════════════════════════════════════════╝

🔐 AUTHENTICATION
   "Who are you?"
   ─────────────────────────────────────────────────────────
   • Verifies identity
   • Proves you are who you claim to be
   • Methods: Password, biometric, token, certificate
   • Examples:
     - Login with username/password
     - Fingerprint scan
     - Face ID
     - Security key (YubiKey)

   Result: You get access to the system

🎫 AUTHORIZATION
   "What can you do?"
   ─────────────────────────────────────────────────────────
   • Verifies permissions
   • Determines what you can access
   • Methods: RBAC, ABAC, ACL
   • Examples:
     - User can view posts
     - Admin can delete users
     - Manager can approve requests

   Result: You can perform specific actions

The Flow:
─────────────────────────────────────────────────────────────
1. User provides credentials (Authentication)
   ↓
2. System verifies credentials
   ↓
3. User authenticated ✅
   ↓
4. User requests resource
   ↓
5. System checks permissions (Authorization)
   ↓
6. Access granted or denied

# ═══════════════════════════════════════════
# AUTHENTICATION FACTORS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   THREE FACTORS OF AUTH                    ║
╚════════════════════════════════════════════════════════════╝

🧠 Knowledge (Something you know)
   • Password
   • PIN
   • Security questions
   • Passphrase

   Pros: Easy to implement
   Cons: Can be forgotten, stolen, shared

📱 Possession (Something you have)
   • Phone (SMS, authenticator app)
   • Hardware token (YubiKey)
   • Smart card
   • Email access

   Pros: Hard to steal remotely
   Cons: Can be lost or stolen physically

👤 Inherence (Something you are)
   • Fingerprint
   • Face recognition
   • Iris scan
   • Voice recognition

   Pros: Can't be lost or forgotten
   Cons: Privacy concerns, can't change if compromised

Multi-Factor Authentication (MFA):
─────────────────────────────────────────────────────────────
Combine 2+ factors for stronger security

Examples:
• Password (knowledge) + SMS code (possession)
• Password (knowledge) + Fingerprint (inherence)
• PIN (knowledge) + Hardware key (possession)

Security Level:
Single factor   → ⭐ Weak
Two factors     → ⭐⭐⭐⭐ Strong
Three factors   → ⭐⭐⭐⭐⭐ Maximum

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔑 Authentication Methods

</div>

### Authentication Strategies Comparison 📊

```bash
# ═══════════════════════════════════════════
# AUTHENTICATION METHOD COMPARISON
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   METHOD SELECTION GUIDE                   ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Method            | Complexity | Security   | Scalability | Use Case           | User Experience |
| ----------------- | ---------- | ---------- | ----------- | ------------------ | --------------- |
| **Basic Auth**    | ⭐         | ⭐         | ⭐⭐⭐      | Internal APIs      | ⭐⭐            |
| **Session-based** | ⭐⭐       | ⭐⭐⭐     | ⭐⭐        | Traditional web    | ⭐⭐⭐⭐        |
| **JWT/Token**     | ⭐⭐⭐     | ⭐⭐⭐⭐   | ⭐⭐⭐⭐⭐  | SPAs, Mobile, APIs | ⭐⭐⭐⭐        |
| **OAuth 2.0**     | ⭐⭐⭐⭐   | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐  | Third-party access | ⭐⭐⭐⭐⭐      |
| **SAML**          | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐    | Enterprise SSO     | ⭐⭐⭐          |
| **API Keys**      | ⭐         | ⭐⭐       | ⭐⭐⭐⭐⭐  | Service-to-service | ⭐⭐⭐          |
| **Passwordless**  | ⭐⭐⭐     | ⭐⭐⭐⭐   | ⭐⭐⭐⭐    | Modern apps        | ⭐⭐⭐⭐⭐      |
| **Certificate**   | ⭐⭐⭐⭐   | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐    | High security      | ⭐⭐            |

</div>

```bash
# ═══════════════════════════════════════════
# METHOD DEEP DIVE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   BASIC AUTHENTICATION                     ║
╚════════════════════════════════════════════════════════════╝

How it works:
─────────────────────────────────────────────────────────────
1. Client sends username:password in Authorization header
2. Encoded in Base64 (NOT encrypted!)
3. Server validates on every request

Header Format:
Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=
                      ↑
                Base64("username:password")

❌ Problems:
• Credentials sent with EVERY request
• Base64 is encoding, not encryption
• No way to revoke without changing password
• Vulnerable to replay attacks
• No built-in timeout

✅ When to use:
• Internal APIs (behind firewall)
• Development/testing
• Simple service-to-service auth
• Always with HTTPS!

Example (Node.js):
─────────────────────────────────────────────────────────────
const express = require('express');
const basicAuth = require('express-basic-auth');

app.use(basicAuth({
  users: {
    'admin': 'supersecret',
    'user': 'password123'
  },
  challenge: true,  // Send WWW-Authenticate header
  realm: 'My API'
}));

// Or validate from database
app.use(basicAuth({
  authorizer: async (username, password) => {
    const user = await User.findOne({ username });
    if (!user) return false;
    return await bcrypt.compare(password, user.passwordHash);
  },
  authorizeAsync: true
}));

╔════════════════════════════════════════════════════════════╗
║                   DIGEST AUTHENTICATION                    ║
╚════════════════════════════════════════════════════════════╝

Improvement over Basic Auth:
─────────────────────────────────────────────────────────────
• Password never sent in plaintext
• Uses MD5 hashing
• Nonce prevents replay attacks
• Server challenge/response

How it works:
─────────────────────────────────────────────────────────────
1. Client requests resource
2. Server sends challenge (nonce)
3. Client hashes password + nonce + other data
4. Server verifies hash

Still not recommended:
─────────────────────────────────────────────────────────────
❌ MD5 is weak
❌ Complex implementation
❌ Better alternatives exist (JWT, OAuth)
✅ Use JWT or OAuth 2.0 instead

╔════════════════════════════════════════════════════════════╗
║                   API KEY AUTHENTICATION                   ║
╚════════════════════════════════════════════════════════════╗

Simple & effective for service-to-service:
─────────────────────────────────────────────────────────────

Format:
X-API-Key: sk_live_1234567890abcdefghijklmnopqrstuvwxyz

Characteristics:
• Long-lived (don't expire automatically)
• Can be scoped to specific permissions
• Easy to rotate
• Can track usage per key

✅ Best Practices:
• Prefix keys (sk_live_, sk_test_)
• Hash before storing (bcrypt)
• Allow multiple keys per user
• Track last used date
• Support key rotation
• Rate limit per key

❌ Limitations:
• No built-in expiration
• Manual revocation required
• Can't identify specific user (if shared)
• If leaked, need to rotate

Implementation:
─────────────────────────────────────────────────────────────
// Generate API key
function generateApiKey() {
  const prefix = 'sk_live';
  const random = crypto.randomBytes(32).toString('hex');
  return `${prefix}_${random}`;
}

// Middleware
const apiKeyAuth = async (req, res, next) => {
  const apiKey = req.headers['x-api-key'];

  if (!apiKey) {
    return res.status(401).json({ error: 'API key required' });
  }

  // Find and validate key
  const key = await ApiKey.findOne({
    keyHash: await bcrypt.hash(apiKey, 10),
    revoked: false
  });

  if (!key) {
    return res.status(401).json({ error: 'Invalid API key' });
  }

  // Update last used
  await key.updateOne({ lastUsed: new Date() });

  req.apiKey = key;
  req.user = await User.findById(key.userId);
  next();
};

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🛠️ Popular Auth Tools

</div>

### Authentication Services & Libraries 🔧

```bash
# ═══════════════════════════════════════════
# AUTHENTICATION TOOLS LANDSCAPE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   AUTH AS A SERVICE                        ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Service           | Type             | Pricing            | Best For     | Features                |
| ----------------- | ---------------- | ------------------ | ------------ | ----------------------- |
| **Auth0**         | SaaS             | Free-$240/mo       | Enterprise   | Full-featured, SSO, MFA |
| **Firebase Auth** | SaaS             | Free-Pay as you go | Mobile/Web   | Google ecosystem        |
| **Supabase Auth** | SaaS/Self-hosted | Free-$25/mo        | Modern apps  | Postgres-based          |
| **Clerk**         | SaaS             | Free-$25/mo        | Modern web   | Beautiful UI            |
| **AWS Cognito**   | SaaS             | Pay per user       | AWS users    | AWS integration         |
| **Azure AD B2C**  | SaaS             | Pay per auth       | Enterprise   | Microsoft ecosystem     |
| **Keycloak**      | Self-hosted      | Free (OSS)         | Enterprise   | Full control            |
| **Ory**           | SaaS/Self-hosted | Free-Custom        | Cloud-native | Modern, scalable        |

</div>

```bash
# ═══════════════════════════════════════════
# AUTH0 (Most Popular)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   AUTH0 - COMPLETE SOLUTION                ║
╚════════════════════════════════════════════════════════════╝

Website: https://auth0.com
Pricing: Free (7,500 MAU) → $240/mo (Enterprise)

Why Auth0:
─────────────────────────────────────────────────────────────
✅ Fully managed
✅ 30+ social providers
✅ Enterprise SSO (SAML, LDAP)
✅ Passwordless (SMS, email, biometric)
✅ Multi-factor authentication
✅ Attack protection (bot detection)
✅ Beautiful login UI (customizable)
✅ Comprehensive SDKs
✅ Rules/Actions (custom logic)
✅ Extensive documentation

Features:
─────────────────────────────────────────────────────────────
🔐 Authentication:
   • Universal Login (hosted)
   • Social Login (Google, GitHub, etc.)
   • Username/Password
   • Passwordless (Magic Links, SMS)
   • Multi-factor Authentication
   • Biometric (WebAuthn)

🎫 Authorization:
   • Role-Based Access Control
   • Permissions
   • API Authorization

🛡️ Security:
   • Breached Password Detection
   • Bot Detection
   • Anomaly Detection
   • Rate Limiting

🔧 Customization:
   • Rules (deprecated) / Actions (new)
   • Custom Database
   • Hooks
   • Extensibility

Implementation (Node.js):
─────────────────────────────────────────────────────────────
// Install
npm install express express-openid-connect

// Setup
const { auth } = require('express-openid-connect');

const config = {
  authRequired: false,
  auth0Logout: true,
  secret: process.env.AUTH0_SECRET,
  baseURL: process.env.BASE_URL,
  clientID: process.env.AUTH0_CLIENT_ID,
  issuerBaseURL: process.env.AUTH0_ISSUER_BASE_URL
};

app.use(auth(config));

// Protected route
app.get('/profile', requiresAuth(), (req, res) => {
  res.json(req.oidc.user);
});

// Login
app.get('/login', (req, res) => {
  res.oidc.login({ returnTo: '/dashboard' });
});

// Logout
app.get('/logout', (req, res) => {
  res.oidc.logout();
});

React Integration:
─────────────────────────────────────────────────────────────
// Install
npm install @auth0/auth0-react

// Setup
import { Auth0Provider } from '@auth0/auth0-react';

<Auth0Provider
  domain={process.env.REACT_APP_AUTH0_DOMAIN}
  clientId={process.env.REACT_APP_AUTH0_CLIENT_ID}
  redirectUri={window.location.origin}
>
  <App />
</Auth0Provider>

// Login button
import { useAuth0 } from '@auth0/auth0-react';

function LoginButton() {
  const { loginWithRedirect, isAuthenticated, logout, user } = useAuth0();

  if (isAuthenticated) {
    return (
      <div>
        <span>Hello, {user.name}</span>
        <button onClick={() => logout()}>Log Out</button>
      </div>
    );
  }

  return <button onClick={() => loginWithRedirect()}>Log In</button>;
}

// Protected component
import { withAuthenticationRequired } from '@auth0/auth0-react';

const ProtectedComponent = () => <div>Protected content</div>;

export default withAuthenticationRequired(ProtectedComponent, {
  onRedirecting: () => <div>Loading...</div>,
});

# ═══════════════════════════════════════════
# FIREBASE AUTHENTICATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   FIREBASE AUTH - GOOGLE'S SOLUTION        ║
╚════════════════════════════════════════════════════════════╝

Website: https://firebase.google.com/products/auth
Pricing: Free (unlimited users)

Why Firebase Auth:
─────────────────────────────────────────────────────────────
✅ Completely free
✅ Easy integration (Google ecosystem)
✅ Multiple auth methods
✅ Real-time database integration
✅ Great for mobile apps
✅ Anonymous authentication
✅ Phone number authentication

Supported Providers:
─────────────────────────────────────────────────────────────
• Email/Password
• Google, Facebook, Twitter, GitHub
• Phone Number (SMS)
• Anonymous
• Custom (your backend)
• SAML, OpenID Connect

Setup (Web):
─────────────────────────────────────────────────────────────
// Install
npm install firebase

// Initialize
import { initializeApp } from 'firebase/app';
import {
  getAuth,
  createUserWithEmailAndPassword,
  signInWithEmailAndPassword,
  signInWithPopup,
  GoogleAuthProvider,
  onAuthStateChanged
} from 'firebase/auth';

const firebaseConfig = {
  apiKey: process.env.REACT_APP_FIREBASE_API_KEY,
  authDomain: process.env.REACT_APP_FIREBASE_AUTH_DOMAIN,
  projectId: process.env.REACT_APP_FIREBASE_PROJECT_ID,
};

const app = initializeApp(firebaseConfig);
const auth = getAuth(app);

// Sign up
async function signUp(email, password) {
  try {
    const userCredential = await createUserWithEmailAndPassword(
      auth,
      email,
      password
    );
    console.log('User created:', userCredential.user);
  } catch (error) {
    console.error('Sign up error:', error.message);
  }
}

// Sign in
async function signIn(email, password) {
  try {
    const userCredential = await signInWithEmailAndPassword(
      auth,
      email,
      password
    );
    console.log('Signed in:', userCredential.user);
  } catch (error) {
    console.error('Sign in error:', error.message);
  }
}

// Google sign-in
async function signInWithGoogle() {
  const provider = new GoogleAuthProvider();
  try {
    const result = await signInWithPopup(auth, provider);
    console.log('Google user:', result.user);
  } catch (error) {
    console.error('Google sign in error:', error.message);
  }
}

// Auth state observer
onAuthStateChanged(auth, (user) => {
  if (user) {
    console.log('User signed in:', user.uid);
  } else {
    console.log('User signed out');
  }
});

React Hook:
─────────────────────────────────────────────────────────────
import { useState, useEffect } from 'react';
import { getAuth, onAuthStateChanged } from 'firebase/auth';

function useAuth() {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    const auth = getAuth();
    const unsubscribe = onAuthStateChanged(auth, (user) => {
      setUser(user);
      setLoading(false);
    });

    return unsubscribe;
  }, []);

  return { user, loading };
}

// Usage
function App() {
  const { user, loading } = useAuth();

  if (loading) return <div>Loading...</div>;

  if (user) {
    return <Dashboard user={user} />;
  }

  return <Login />;
}

# ═══════════════════════════════════════════
# SUPABASE AUTH
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SUPABASE - OPEN SOURCE FIREBASE          ║
╚════════════════════════════════════════════════════════════╝

Website: https://supabase.com
Pricing: Free (50,000 MAU) → $25/mo (Pro)

Why Supabase:
─────────────────────────────────────────────────────────────
✅ Open source (self-hostable)
✅ PostgreSQL-based
✅ Row Level Security (RLS)
✅ Real-time subscriptions
✅ Built-in storage
✅ Auto-generated APIs
✅ Great developer experience

Setup:
─────────────────────────────────────────────────────────────
// Install
npm install @supabase/supabase-js

// Initialize
import { createClient } from '@supabase/supabase-js';

const supabase = createClient(
  process.env.REACT_APP_SUPABASE_URL,
  process.env.REACT_APP_SUPABASE_ANON_KEY
);

// Sign up
async function signUp(email, password) {
  const { data, error } = await supabase.auth.signUp({
    email,
    password,
  });

  if (error) console.error('Error:', error.message);
  else console.log('User:', data.user);
}

// Sign in
async function signIn(email, password) {
  const { data, error } = await supabase.auth.signInWithPassword({
    email,
    password,
  });

  if (error) console.error('Error:', error.message);
  else console.log('Session:', data.session);
}

// OAuth (GitHub)
async function signInWithGitHub() {
  const { data, error } = await supabase.auth.signInWithOAuth({
    provider: 'github',
  });
}

// Magic Link
async function signInWithMagicLink(email) {
  const { data, error } = await supabase.auth.signInWithOtp({
    email,
  });
}

// Get session
const { data: { session } } = await supabase.auth.getSession();

// Listen to auth changes
supabase.auth.onAuthStateChange((event, session) => {
  console.log(event, session);
});

// Sign out
await supabase.auth.signOut();

React Hook:
─────────────────────────────────────────────────────────────
import { useEffect, useState } from 'react';
import { supabase } from './supabaseClient';

export function useAuth() {
  const [session, setSession] = useState(null);

  useEffect(() => {
    // Get initial session
    supabase.auth.getSession().then(({ data: { session } }) => {
      setSession(session);
    });

    // Listen for changes
    const {
      data: { subscription },
    } = supabase.auth.onAuthStateChange((_event, session) => {
      setSession(session);
    });

    return () => subscription.unsubscribe();
  }, []);

  return session;
}

Row Level Security (RLS):
─────────────────────────────────────────────────────────────
-- Enable RLS
ALTER TABLE posts ENABLE ROW LEVEL SECURITY;

-- Policy: Users can only see their own posts
CREATE POLICY "Users can view own posts"
ON posts
FOR SELECT
USING (auth.uid() = user_id);

-- Policy: Users can only insert their own posts
CREATE POLICY "Users can insert own posts"
ON posts
FOR INSERT
WITH CHECK (auth.uid() = user_id);

# ═══════════════════════════════════════════
# CLERK
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CLERK - MODERN AUTH UX                   ║
╚════════════════════════════════════════════════════════════╝

Website: https://clerk.dev
Pricing: Free (5,000 MAU) → $25/mo (Pro)

Why Clerk:
─────────────────────────────────────────────────────────────
✅ Beautiful pre-built UI components
✅ Drop-in React components
✅ User management dashboard
✅ Organizations/Teams support
✅ Webhook events
✅ Session management
✅ Amazing developer experience

Setup (Next.js):
─────────────────────────────────────────────────────────────
// Install
npm install @clerk/nextjs

// app/layout.tsx
import { ClerkProvider } from '@clerk/nextjs';

export default function RootLayout({ children }) {
  return (
    <ClerkProvider>
      <html lang="en">
        <body>{children}</body>
      </html>
    </ClerkProvider>
  );
}

// app/sign-in/[[...sign-in]]/page.tsx
import { SignIn } from '@clerk/nextjs';

export default function SignInPage() {
  return <SignIn />;
}

// app/sign-up/[[...sign-up]]/page.tsx
import { SignUp } from '@clerk/nextjs';

export default function SignUpPage() {
  return <SignUp />;
}

// Protected page
import { currentUser } from '@clerk/nextjs';

export default async function DashboardPage() {
  const user = await currentUser();

  if (!user) {
    redirect('/sign-in');
  }

  return <div>Hello {user.firstName}</div>;
}

Components:
─────────────────────────────────────────────────────────────
import {
  SignedIn,
  SignedOut,
  SignInButton,
  UserButton,
  useUser,
  useAuth,
} from '@clerk/nextjs';

function Header() {
  return (
    <header>
      <SignedOut>
        <SignInButton />
      </SignedOut>

      <SignedIn>
        <UserButton />
      </SignedIn>
    </header>
  );
}

function Profile() {
  const { user } = useUser();

  return <div>Email: {user.emailAddresses[0].emailAddress}</div>;
}

function ProtectedAction() {
  const { getToken } = useAuth();

  async function callAPI() {
    const token = await getToken();

    const response = await fetch('/api/protected', {
      headers: {
        Authorization: `Bearer ${token}`,
      },
    });
  }

  return <button onClick={callAPI}>Call API</button>;
}

# ═══════════════════════════════════════════
# PASSPORT.JS (Library)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PASSPORT.JS - FLEXIBLE MIDDLEWARE        ║
╚════════════════════════════════════════════════════════════╝

Website: https://passportjs.org
Type: Node.js library (free)

Why Passport:
─────────────────────────────────────────────────────────────
✅ 500+ authentication strategies
✅ Flexible & unopinionated
✅ Works with Express
✅ Large community
✅ Free & open source

Popular Strategies:
─────────────────────────────────────────────────────────────
• passport-local (username/password)
• passport-jwt (JWT tokens)
• passport-google-oauth20 (Google)
• passport-github2 (GitHub)
• passport-facebook (Facebook)
• passport-twitter (Twitter)
• passport-saml (SAML SSO)

Setup:
─────────────────────────────────────────────────────────────
// Install
npm install passport passport-local express-session

// Configure
const passport = require('passport');
const LocalStrategy = require('passport-local').Strategy;

// Local strategy
passport.use(new LocalStrategy(
  async (username, password, done) => {
    try {
      const user = await User.findOne({ username });

      if (!user) {
        return done(null, false, { message: 'User not found' });
      }

      const isValid = await bcrypt.compare(password, user.passwordHash);

      if (!isValid) {
        return done(null, false, { message: 'Invalid password' });
      }

      return done(null, user);
    } catch (error) {
      return done(error);
    }
  }
));

// Serialize user
passport.serializeUser((user, done) => {
  done(null, user.id);
});

// Deserialize user
passport.deserializeUser(async (id, done) => {
  try {
    const user = await User.findById(id);
    done(null, user);
  } catch (error) {
    done(error);
  }
});

// Express setup
app.use(session({
  secret: process.env.SESSION_SECRET,
  resave: false,
  saveUninitialized: false
}));

app.use(passport.initialize());
app.use(passport.session());

// Routes
app.post('/login',
  passport.authenticate('local', {
    successRedirect: '/dashboard',
    failureRedirect: '/login',
    failureMessage: true
  })
);

app.post('/logout', (req, res) => {
  req.logout((err) => {
    if (err) return next(err);
    res.redirect('/');
  });
});

// Protected route
function ensureAuthenticated(req, res, next) {
  if (req.isAuthenticated()) {
    return next();
  }
  res.redirect('/login');
}

app.get('/dashboard', ensureAuthenticated, (req, res) => {
  res.render('dashboard', { user: req.user });
});

Google OAuth Strategy:
─────────────────────────────────────────────────────────────
const GoogleStrategy = require('passport-google-oauth20').Strategy;

passport.use(new GoogleStrategy({
    clientID: process.env.GOOGLE_CLIENT_ID,
    clientSecret: process.env.GOOGLE_CLIENT_SECRET,
    callbackURL: '/auth/google/callback'
  },
  async (accessToken, refreshToken, profile, done) => {
    try {
      let user = await User.findOne({ googleId: profile.id });

      if (!user) {
        user = await User.create({
          googleId: profile.id,
          email: profile.emails[0].value,
          name: profile.displayName,
          avatar: profile.photos[0].value
        });
      }

      return done(null, user);
    } catch (error) {
      return done(error);
    }
  }
));

// Routes
app.get('/auth/google',
  passport.authenticate('google', { scope: ['profile', 'email'] })
);

app.get('/auth/google/callback',
  passport.authenticate('google', { failureRedirect: '/login' }),
  (req, res) => {
    res.redirect('/dashboard');
  }
);

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🎫 Session-Based Authentication

</div>

### Traditional Session Management 🍪

```bash
# ═══════════════════════════════════════════
# SESSION-BASED AUTHENTICATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   HOW SESSIONS WORK                        ║
╚════════════════════════════════════════════════════════════╝

Flow:
─────────────────────────────────────────────────────────────
1. User submits credentials
   ↓
2. Server validates credentials
   ↓
3. Server creates session in database/memory
   ↓
4. Server sends session ID in cookie
   ↓
5. Browser stores cookie
   ↓
6. Browser sends cookie with every request
   ↓
7. Server looks up session by ID
   ↓
8. Server validates session
   ↓
9. Request processed

Session Storage:
─────────────────────────────────────────────────────────────
┌─────────────────────────────────────────┐
│ Client (Browser)                        │
│  Cookie: sessionId=abc123xyz            │
└─────────────────────────────────────────┘
             ↓ HTTP Request
┌─────────────────────────────────────────┐
│ Server                                  │
│  Express-session middleware             │
└─────────────────────────────────────────┘
             ↓ Session ID
┌─────────────────────────────────────────┐
│ Session Store (Redis/MongoDB)          │
│  abc123xyz → { userId: 42, ... }       │
└─────────────────────────────────────────┘

Pros:
─────────────────────────────────────────────────────────────
✅ Server controls sessions (can revoke instantly)
✅ Mature & well-understood
✅ Works with server-side rendering
✅ Can store large amounts of data
✅ Built-in CSRF protection

Cons:
─────────────────────────────────────────────────────────────
❌ Requires server-side storage
❌ Harder to scale horizontally
❌ Not ideal for mobile apps
❌ Not suitable for microservices
❌ Stateful (server must remember sessions)

# ═══════════════════════════════════════════
# IMPLEMENTATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   EXPRESS SESSION                          ║
╚════════════════════════════════════════════════════════════╝

Basic Setup:
─────────────────────────────────────────────────────────────
const express = require('express');
const session = require('express-session');
const MongoStore = require('connect-mongo');

app.use(session({
  // Session secret (use strong random string)
  secret: process.env.SESSION_SECRET,

  // Don't save unmodified sessions
  resave: false,

  // Don't create session until something stored
  saveUninitialized: false,

  // Cookie settings
  cookie: {
    secure: process.env.NODE_ENV === 'production', // HTTPS only in production
    httpOnly: true,        // Prevent JavaScript access
    maxAge: 1000 * 60 * 60 * 24, // 24 hours
    sameSite: 'strict'     // CSRF protection
  },

  // Store sessions in MongoDB
  store: MongoStore.create({
    mongoUrl: process.env.MONGODB_URI,
    touchAfter: 24 * 3600  // Lazy update (once per 24h)
  })
}));

// Login route
app.post('/login', async (req, res) => {
  const { username, password } = req.body;

  try {
    // Validate credentials
    const user = await User.findOne({ username });
    if (!user || !await bcrypt.compare(password, user.passwordHash)) {
      return res.status(401).json({ error: 'Invalid credentials' });
    }

    // Create session
    req.session.userId = user.id;
    req.session.username = user.username;
    req.session.role = user.role;

    // Regenerate session ID (prevent session fixation)
    req.session.regenerate((err) => {
      if (err) {
        return res.status(500).json({ error: 'Session error' });
      }

      req.session.userId = user.id;
      res.json({ success: true, user: { id: user.id, username: user.username } });
    });
  } catch (error) {
    res.status(500).json({ error: 'Login failed' });
  }
});

// Logout route
app.post('/logout', (req, res) => {
  req.session.destroy((err) => {
    if (err) {
      return res.status(500).json({ error: 'Logout failed' });
    }

    res.clearCookie('connect.sid'); // Default cookie name
    res.json({ success: true });
  });
});

// Protected route
function requireAuth(req, res, next) {
  if (!req.session.userId) {
    return res.status(401).json({ error: 'Authentication required' });
  }
  next();
}

app.get('/api/profile', requireAuth, async (req, res) => {
  const user = await User.findById(req.session.userId);
  res.json(user);
});

// Check session
app.get('/api/session', (req, res) => {
  if (req.session.userId) {
    res.json({
      authenticated: true,
      userId: req.session.userId,
      username: req.session.username
    });
  } else {
    res.json({ authenticated: false });
  }
});

╔════════════════════════════════════════════════════════════╗
║                   REDIS SESSION STORE                      ║
╚════════════════════════════════════════════════════════════╝

For better performance (recommended):
─────────────────────────────────────────────────────────────
const Redis = require('ioredis');
const RedisStore = require('connect-redis').default;

const redisClient = new Redis({
  host: process.env.REDIS_HOST,
  port: process.env.REDIS_PORT,
  password: process.env.REDIS_PASSWORD
});

app.use(session({
  store: new RedisStore({
    client: redisClient,
    prefix: 'sess:',
  }),
  secret: process.env.SESSION_SECRET,
  resave: false,
  saveUninitialized: false,
  cookie: {
    secure: true,
    httpOnly: true,
    maxAge: 1000 * 60 * 60 * 24 // 24 hours
  }
}));

Why Redis:
─────────────────────────────────────────────────────────────
✅ Fast (in-memory)
✅ Built-in expiration
✅ Scales horizontally
✅ Atomic operations
✅ Pub/Sub for multi-server

╔════════════════════════════════════════════════════════════╗
║                   SESSION SECURITY                         ║
╚════════════════════════════════════════════════════════════╝

Security Best Practices:
─────────────────────────────────────────────────────────────

1. Regenerate Session ID After Login
─────────────────────────────────────────────────────────────
app.post('/login', async (req, res) => {
  // Authenticate user...

  // ✅ Regenerate to prevent session fixation
  req.session.regenerate((err) => {
    if (err) next(err);
    req.session.userId = user.id;
    res.json({ success: true });
  });
});

2. Set Secure Cookie Flags
─────────────────────────────────────────────────────────────
cookie: {
  secure: true,       // ✅ HTTPS only
  httpOnly: true,     // ✅ No JavaScript access
  sameSite: 'strict', // ✅ CSRF protection
  maxAge: 3600000     // ✅ 1 hour expiration
}

3. Implement Session Timeout
─────────────────────────────────────────────────────────────
// Middleware to check session age
app.use((req, res, next) => {
  if (req.session.userId) {
    const now = Date.now();
    const lastActivity = req.session.lastActivity || now;
    const maxInactive = 30 * 60 * 1000; // 30 minutes

    if (now - lastActivity > maxInactive) {
      // Session expired
      req.session.destroy();
      return res.status(401).json({ error: 'Session expired' });
    }

    // Update last activity
    req.session.lastActivity = now;
  }
  next();
});

4. Store Minimal Data in Session
─────────────────────────────────────────────────────────────
// ❌ Don't store large objects
req.session.user = await User.findById(userId); // Entire user object

// ✅ Store only ID, fetch on demand
req.session.userId = userId;

// When needed:
const user = await User.findById(req.session.userId);

5. Concurrent Session Control
─────────────────────────────────────────────────────────────
// Track active sessions per user
const activeSessions = new Map();

app.post('/login', async (req, res) => {
  // Authenticate...

  // Limit to 3 concurrent sessions
  const userSessions = activeSessions.get(user.id) || [];

  if (userSessions.length >= 3) {
    // Destroy oldest session
    const oldestSessionId = userSessions.shift();
    await sessionStore.destroy(oldestSessionId);
  }

  // Add new session
  userSessions.push(req.sessionID);
  activeSessions.set(user.id, userSessions);
});

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🎟️ Token-Based Authentication (JWT)

</div>

### JSON Web Tokens Implementation 🎫

```bash
# ═══════════════════════════════════════════
# JWT AUTHENTICATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   JWT STRUCTURE                            ║
╚════════════════════════════════════════════════════════════╝

JSON Web Token Format:
─────────────────────────────────────────────────────────────
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
                 ↓                                  ↓                                                         ↓
              HEADER                              PAYLOAD                                                SIGNATURE

Header (Base64):
{
  "alg": "HS256",    // Algorithm
  "typ": "JWT"       // Type
}

Payload (Base64):
{
  "sub": "1234567890",           // Subject (user ID)
  "name": "John Doe",            // Custom claims
  "iat": 1516239022,             // Issued at
  "exp": 1516242622              // Expiration
}

Signature:
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret
)

How It Works:
─────────────────────────────────────────────────────────────
1. User logs in with credentials
   ↓
2. Server validates credentials
   ↓
3. Server generates JWT (signs with secret)
   ↓
4. Server sends JWT to client
   ↓
5. Client stores JWT (localStorage/cookie)
   ↓
6. Client includes JWT in requests (Authorization header)
   ↓
7. Server verifies JWT signature
   ↓
8. Server extracts user info from payload
   ↓
9. Request processed

Pros:
─────────────────────────────────────────────────────────────
✅ Stateless (no server storage needed)
✅ Scalable (any server can verify)
✅ Works across domains (CORS friendly)
✅ Perfect for APIs & SPAs
✅ Mobile-friendly
✅ Microservices-friendly
✅ Self-contained (all data in token)

Cons:
─────────────────────────────────────────────────────────────
❌ Can't revoke until expiration
❌ Larger than session IDs
❌ If leaked, valid until expiration
❌ Secret must be shared across servers
❌ Token size grows with claims

# ═══════════════════════════════════════════
# IMPLEMENTATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   COMPLETE JWT SETUP                       ║
╚════════════════════════════════════════════════════════════╝

Install:
─────────────────────────────────────────────────────────────
npm install jsonwebtoken bcrypt

Complete Implementation:
─────────────────────────────────────────────────────────────
const jwt = require('jsonwebtoken');
const bcrypt = require('bcrypt');

// JWT Configuration
const JWT_SECRET = process.env.JWT_SECRET; // Strong secret!
const JWT_EXPIRES_IN = '15m';              // Short-lived access token
const REFRESH_TOKEN_SECRET = process.env.REFRESH_TOKEN_SECRET;
const REFRESH_TOKEN_EXPIRES_IN = '7d';     // Long-lived refresh token

// Generate tokens
function generateTokens(user) {
  // Access token (short-lived)
  const accessToken = jwt.sign(
    {
      sub: user.id,          // Subject (user ID)
      username: user.username,
      role: user.role,
      type: 'access'
    },
    JWT_SECRET,
    {
      expiresIn: JWT_EXPIRES_IN,
      issuer: 'myapp.com',
      audience: 'myapp-users'
    }
  );

  // Refresh token (long-lived)
  const refreshToken = jwt.sign(
    {
      sub: user.id,
      type: 'refresh'
    },
    REFRESH_TOKEN_SECRET,
    {
      expiresIn: REFRESH_TOKEN_EXPIRES_IN
    }
  );

  return { accessToken, refreshToken };
}

// Login endpoint
app.post('/auth/login', async (req, res) => {
  const { username, password } = req.body;

  try {
    // Find user
    const user = await User.findOne({ username });
    if (!user) {
      return res.status(401).json({ error: 'Invalid credentials' });
    }

    // Verify password
    const isValid = await bcrypt.compare(password, user.passwordHash);
    if (!isValid) {
      return res.status(401).json({ error: 'Invalid credentials' });
    }

    // Generate tokens
    const { accessToken, refreshToken } = generateTokens(user);

    // Store refresh token in database (for revocation)
    await RefreshToken.create({
      token: refreshToken,
      userId: user.id,
      expiresAt: new Date(Date.now() + 7 * 24 * 60 * 60 * 1000)
    });

    // Send tokens
    res.json({
      accessToken,
      refreshToken,
      user: {
        id: user.id,
        username: user.username,
        role: user.role
      }
    });
  } catch (error) {
    console.error('Login error:', error);
    res.status(500).json({ error: 'Login failed' });
  }
});

// Refresh token endpoint
app.post('/auth/refresh', async (req, res) => {
  const { refreshToken } = req.body;

  if (!refreshToken) {
    return res.status(401).json({ error: 'Refresh token required' });
  }

  try {
    // Verify refresh token
    const decoded = jwt.verify(refreshToken, REFRESH_TOKEN_SECRET);

    // Check if refresh token exists in database
    const storedToken = await RefreshToken.findOne({
      token: refreshToken,
      userId: decoded.sub,
      expiresAt: { $gt: new Date() }
    });

    if (!storedToken) {
      return res.status(401).json({ error: 'Invalid refresh token' });
    }

    // Get user
    const user = await User.findById(decoded.sub);
    if (!user) {
      return res.status(401).json({ error: 'User not found' });
    }

    // Generate new access token
    const accessToken = jwt.sign(
      {
        sub: user.id,
        username: user.username,
        role: user.role,
        type: 'access'
      },
      JWT_SECRET,
      { expiresIn: JWT_EXPIRES_IN }
    );

    res.json({ accessToken });
  } catch (error) {
    if (error.name === 'TokenExpiredError') {
      return res.status(401).json({ error: 'Refresh token expired' });
    }
    res.status(401).json({ error: 'Invalid refresh token' });
  }
});

// Logout endpoint (revoke refresh token)
app.post('/auth/logout', async (req, res) => {
  const { refreshToken } = req.body;

  try {
    // Delete refresh token from database
    await RefreshToken.deleteOne({ token: refreshToken });
    res.json({ message: 'Logged out successfully' });
  } catch (error) {
    res.status(500).json({ error: 'Logout failed' });
  }
});

// Auth middleware
const authenticateJWT = (req, res, next) => {
  const authHeader = req.headers.authorization;

  if (!authHeader || !authHeader.startsWith('Bearer ')) {
    return res.status(401).json({ error: 'No token provided' });
  }

  const token = authHeader.split(' ')[1];

  try {
    const decoded = jwt.verify(token, JWT_SECRET, {
      issuer: 'myapp.com',
      audience: 'myapp-users'
    });

    // Check token type
    if (decoded.type !== 'access') {
      return res.status(401).json({ error: 'Invalid token type' });
    }

    // Attach user to request
    req.user = {
      id: decoded.sub,
      username: decoded.username,
      role: decoded.role
    };

    next();
  } catch (error) {
    if (error.name === 'TokenExpiredError') {
      return res.status(401).json({
        error: 'Token expired',
        code: 'TOKEN_EXPIRED'
      });
    }

    if (error.name === 'JsonWebTokenError') {
      return res.status(401).json({ error: 'Invalid token' });
    }

    res.status(500).json({ error: 'Authentication failed' });
  }
};

// Protected route
app.get('/api/profile', authenticateJWT, async (req, res) => {
  const user = await User.findById(req.user.id);
  res.json(user);
});

// Role-based middleware
const requireRole = (role) => {
  return (req, res, next) => {
    if (req.user.role !== role) {
      return res.status(403).json({ error: 'Forbidden' });
    }
    next();
  };
};

app.get('/api/admin', authenticateJWT, requireRole('admin'), (req, res) => {
  res.json({ message: 'Admin only' });
});

╔════════════════════════════════════════════════════════════╗
║                   CLIENT-SIDE IMPLEMENTATION               ║
╚════════════════════════════════════════════════════════════╝

React Example:
─────────────────────────────────────────────────────────────
// authContext.js
import React, { createContext, useState, useEffect } from 'react';
import axios from 'axios';

export const AuthContext = createContext();

export function AuthProvider({ children }) {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);

  // Load user on mount
  useEffect(() => {
    const accessToken = localStorage.getItem('accessToken');
    if (accessToken) {
      // Verify token by fetching user profile
      fetchProfile(accessToken);
    } else {
      setLoading(false);
    }
  }, []);

  async function fetchProfile(token) {
    try {
      const response = await axios.get('/api/profile', {
        headers: { Authorization: `Bearer ${token}` }
      });
      setUser(response.data);
    } catch (error) {
      if (error.response?.data?.code === 'TOKEN_EXPIRED') {
        // Try refreshing token
        await refreshToken();
      } else {
        // Invalid token, clear storage
        localStorage.removeItem('accessToken');
        localStorage.removeItem('refreshToken');
      }
    } finally {
      setLoading(false);
    }
  }

  async function login(username, password) {
    try {
      const response = await axios.post('/auth/login', {
        username,
        password
      });

      const { accessToken, refreshToken, user } = response.data;

      // Store tokens
      localStorage.setItem('accessToken', accessToken);
      localStorage.setItem('refreshToken', refreshToken);

      setUser(user);
      return { success: true };
    } catch (error) {
      return {
        success: false,
        error: error.response?.data?.error || 'Login failed'
      };
    }
  }

  async function refreshToken() {
    try {
      const refreshToken = localStorage.getItem('refreshToken');
      if (!refreshToken) throw new Error('No refresh token');

      const response = await axios.post('/auth/refresh', {
        refreshToken
      });

      const { accessToken } = response.data;
      localStorage.setItem('accessToken', accessToken);

      // Retry original request
      await fetchProfile(accessToken);
    } catch (error) {
      // Refresh failed, logout
      logout();
    }
  }

  function logout() {
    const refreshToken = localStorage.getItem('refreshToken');

    // Revoke refresh token on server
    axios.post('/auth/logout', { refreshToken }).catch(() => {});

    // Clear local storage
    localStorage.removeItem('accessToken');
    localStorage.removeItem('refreshToken');

    setUser(null);
  }

  return (
    <AuthContext.Provider value={{ user, loading, login, logout }}>
      {children}
    </AuthContext.Provider>
  );
}

// Axios interceptor for automatic token refresh
axios.interceptors.response.use(
  response => response,
  async error => {
    const originalRequest = error.config;

    if (error.response?.status === 401 &&
        error.response?.data?.code === 'TOKEN_EXPIRED' &&
        !originalRequest._retry) {

      originalRequest._retry = true;

      try {
        const refreshToken = localStorage.getItem('refreshToken');
        const response = await axios.post('/auth/refresh', {
          refreshToken
        });

        const { accessToken } = response.data;
        localStorage.setItem('accessToken', accessToken);

        // Update authorization header
        originalRequest.headers.Authorization = `Bearer ${accessToken}`;

        // Retry original request
        return axios(originalRequest);
      } catch (refreshError) {
        // Refresh failed, redirect to login
        window.location.href = '/login';
        return Promise.reject(refreshError);
      }
    }

    return Promise.reject(error);
  }
);

// Usage
import { useContext } from 'react';
import { AuthContext } from './authContext';

function LoginPage() {
  const { login } = useContext(AuthContext);
  const [username, setUsername] = useState('');
  const [password, setPassword] = useState('');

  async function handleSubmit(e) {
    e.preventDefault();
    const result = await login(username, password);

    if (result.success) {
      // Redirect to dashboard
      navigate('/dashboard');
    } else {
      alert(result.error);
    }
  }

  return (
    <form onSubmit={handleSubmit}>
      <input value={username} onChange={e => setUsername(e.target.value)} />
      <input type="password" value={password} onChange={e => setPassword(e.target.value)} />
      <button type="submit">Login</button>
    </form>
  );
}

function ProtectedPage() {
  const { user, loading } = useContext(AuthContext);

  if (loading) return <div>Loading...</div>;
  if (!user) return <Navigate to="/login" />;

  return <div>Welcome {user.username}</div>;
}

╔════════════════════════════════════════════════════════════╗
║                   JWT SECURITY BEST PRACTICES              ║
╚════════════════════════════════════════════════════════════╝

1. Short Access Token Expiration
─────────────────────────────────────────────────────────────
✅ 15 minutes or less
✅ Use refresh tokens for extended sessions
❌ Don't use long-lived access tokens

2. Store Tokens Securely
─────────────────────────────────────────────────────────────
Option A: localStorage (Simple, but XSS vulnerable)
Option B: httpOnly cookie (Better, but CSRF vulnerable)
Option C: httpOnly cookie + CSRF token (Best)

// Send token in httpOnly cookie
res.cookie('token', accessToken, {
  httpOnly: true,
  secure: true,
  sameSite: 'strict',
  maxAge: 15 * 60 * 1000
});

3. Use Strong Secrets
─────────────────────────────────────────────────────────────
// ❌ Weak
const JWT_SECRET = 'secret';

// ✅ Strong (256-bit)
const JWT_SECRET = crypto.randomBytes(32).toString('hex');

// Store in environment variable
JWT_SECRET=a1b2c3d4e5f6...

4. Validate All Claims
─────────────────────────────────────────────────────────────
jwt.verify(token, JWT_SECRET, {
  issuer: 'myapp.com',      // ✅ Verify issuer
  audience: 'myapp-users',  // ✅ Verify audience
  maxAge: '15m'             // ✅ Verify age
});

5. Implement Token Revocation
─────────────────────────────────────────────────────────────
// Store active refresh tokens in database
// Check on each request (or use Redis for speed)

// Revoke on logout
await RefreshToken.deleteOne({ userId: user.id });

// Revoke all tokens (password change, security breach)
await RefreshToken.deleteMany({ userId: user.id });

6. Don't Store Sensitive Data
─────────────────────────────────────────────────────────────
// ❌ Don't include
{
  passwordHash: '...',
  ssn: '...',
  creditCard: '...'
}

// ✅ Only include necessary
{
  sub: user.id,
  role: user.role,
  username: user.username
}

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🌐 OAuth 2.0 & Social Login

</div>

### OAuth 2.0 Complete Guide 🔑

```bash
# ═══════════════════════════════════════════
# OAUTH 2.0 FUNDAMENTALS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHAT IS OAUTH 2.0?                       ║
╚════════════════════════════════════════════════════════════╝

OAuth 2.0 = Authorization Framework (NOT authentication!)
─────────────────────────────────────────────────────────────
Purpose: Grant limited access to user resources without sharing passwords

Example Scenario:
• You want to use Canva to edit photos from your Google Drive
• You DON'T give Canva your Google password
• Instead: Google asks "Allow Canva to access your Drive?"
• You approve → Canva gets temporary access token
• Canva can access your Drive (but can't change password, read email, etc.)

Key Players (OAuth Roles):
─────────────────────────────────────────────────────────────
1. Resource Owner (User)
   • The person who owns the data
   • Example: You

2. Client (Application)
   • The app requesting access
   • Example: Canva

3. Authorization Server
   • Issues access tokens
   • Example: Google Auth Server

4. Resource Server
   • Hosts protected resources
   • Example: Google Drive API

The OAuth Flow:
─────────────────────────────────────────────────────────────
User → Client → Authorization Server → User Approves
                                        ↓
                               Authorization Code
                                        ↓
Client → Authorization Server (exchange code for token)
                                        ↓
                               Access Token
                                        ↓
Client → Resource Server (with token) → Protected Resources

# ═══════════════════════════════════════════
# OAUTH 2.0 GRANT TYPES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   AUTHORIZATION CODE FLOW                  ║
╚════════════════════════════════════════════════════════════╝

Most secure & common flow for web apps:
─────────────────────────────────────────────────────────────

Step-by-Step:
1. User clicks "Login with Google"
   ↓
2. Redirect to Google:
   https://accounts.google.com/o/oauth2/v2/auth?
     client_id=YOUR_CLIENT_ID
     &redirect_uri=https://yourapp.com/callback
     &response_type=code
     &scope=openid email profile
     &state=random_string_for_csrf_protection
   ↓
3. User logs in and approves
   ↓
4. Google redirects back with authorization code:
   https://yourapp.com/callback?
     code=AUTHORIZATION_CODE
     &state=random_string_for_csrf_protection
   ↓
5. Exchange code for tokens (backend):
   POST https://oauth2.googleapis.com/token
   {
     code: AUTHORIZATION_CODE,
     client_id: YOUR_CLIENT_ID,
     client_secret: YOUR_CLIENT_SECRET,
     redirect_uri: https://yourapp.com/callback,
     grant_type: authorization_code
   }
   ↓
6. Receive tokens:
   {
     access_token: "ya29.a0AfH6...",
     refresh_token: "1//0gW...",
     expires_in: 3600,
     token_type: "Bearer",
     id_token: "eyJhbGc..."  // JWT with user info
   }
   ↓
7. Use access token to call Google APIs

Security:
─────────────────────────────────────────────────────────────
✅ Authorization code is useless without client_secret
✅ Client secret never exposed to browser
✅ State parameter prevents CSRF
✅ Short-lived authorization code (expires in minutes)

╔════════════════════════════════════════════════════════════╗
║                   PKCE (PROOF KEY FOR CODE EXCHANGE)       ║
╚════════════════════════════════════════════════════════════╝

Enhanced security for public clients (mobile apps, SPAs):
─────────────────────────────────────────────────────────────

Problem: Mobile/SPA apps can't securely store client_secret
Solution: PKCE (pronounced "pixy")

How it works:
1. Generate random string (code_verifier)
   code_verifier = crypto.randomBytes(32).toString('base64url');

2. Hash it (code_challenge)
   code_challenge = base64url(sha256(code_verifier));

3. Send code_challenge in authorization request
   https://accounts.google.com/o/oauth2/v2/auth?
     ...
     &code_challenge=HASH_OF_CODE_VERIFIER
     &code_challenge_method=S256

4. When exchanging code for token, send original code_verifier
   POST /token
   {
     code: AUTHORIZATION_CODE,
     code_verifier: ORIGINAL_CODE_VERIFIER,
     ...
   }

5. Server verifies: sha256(code_verifier) === code_challenge

Security:
─────────────────────────────────────────────────────────────
✅ Even if authorization code is intercepted, attacker can't use it
✅ No client secret needed
✅ Protects against authorization code interception

╔════════════════════════════════════════════════════════════╗
║                   IMPLICIT FLOW (DEPRECATED)               ║
╚════════════════════════════════════════════════════════════╝

⚠️ NO LONGER RECOMMENDED - Use Authorization Code + PKCE instead

How it worked:
─────────────────────────────────────────────────────────────
• Tokens returned directly in URL fragment
• No code exchange step
• Designed for browser-only apps

Why deprecated:
❌ Tokens exposed in browser history
❌ Tokens visible in URL
❌ No refresh tokens
❌ Less secure than Code + PKCE

╔════════════════════════════════════════════════════════════╗
║                   CLIENT CREDENTIALS FLOW                  ║
╚════════════════════════════════════════════════════════════╝

For machine-to-machine (service-to-service):
─────────────────────────────────────────────────────────────

Use case: Backend service needs to access API
No user involved, app authenticates itself

Flow:
POST /token
{
  grant_type: "client_credentials",
  client_id: YOUR_CLIENT_ID,
  client_secret: YOUR_CLIENT_SECRET,
  scope: "api.read api.write"
}

Response:
{
  access_token: "...",
  token_type: "Bearer",
  expires_in: 3600
}

Use cases:
─────────────────────────────────────────────────────────────
✅ Server-to-server communication
✅ Scheduled jobs
✅ Background services
✅ Microservices
❌ Never use for user authentication

╔════════════════════════════════════════════════════════════╗
║                   RESOURCE OWNER PASSWORD (LEGACY)         ║
╚════════════════════════════════════════════════════════════╝

⚠️ ONLY use for legacy systems

User gives username/password directly to app:
─────────────────────────────────────────────────────────────
POST /token
{
  grant_type: "password",
  username: "user@example.com",
  password: "password123",
  client_id: YOUR_CLIENT_ID,
  client_secret: YOUR_CLIENT_SECRET
}

Why avoid:
❌ App handles user credentials (security risk)
❌ Defeats purpose of OAuth
❌ No consent screen
✅ Only use if: Migrating legacy app, high trust environment

# ═══════════════════════════════════════════
# SOCIAL LOGIN IMPLEMENTATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   GOOGLE OAUTH                             ║
╚════════════════════════════════════════════════════════════╝

Setup (Google Cloud Console):
─────────────────────────────────────────────────────────────
1. Go to https://console.cloud.google.com
2. Create project
3. Enable Google+ API
4. Create OAuth 2.0 credentials
5. Set authorized redirect URIs

Implementation (Node.js):
─────────────────────────────────────────────────────────────
const passport = require('passport');
const GoogleStrategy = require('passport-google-oauth20').Strategy;

passport.use(new GoogleStrategy({
    clientID: process.env.GOOGLE_CLIENT_ID,
    clientSecret: process.env.GOOGLE_CLIENT_SECRET,
    callbackURL: '/auth/google/callback',
    scope: ['profile', 'email']
  },
  async (accessToken, refreshToken, profile, done) => {
    try {
      // Check if user exists
      let user = await User.findOne({ googleId: profile.id });

      if (!user) {
        // Create new user
        user = await User.create({
          googleId: profile.id,
          email: profile.emails[0].value,
          name: profile.displayName,
          avatar: profile.photos[0].value,
          provider: 'google'
        });
      } else {
        // Update last login
        await user.update({ lastLogin: new Date() });
      }

      return done(null, user);
    } catch (error) {
      return done(error, null);
    }
  }
));

// Routes
app.get('/auth/google',
  passport.authenticate('google', {
    scope: ['profile', 'email']
  })
);

app.get('/auth/google/callback',
  passport.authenticate('google', {
    failureRedirect: '/login',
    session: false
  }),
  (req, res) => {
    // Generate JWT for user
    const token = jwt.sign(
      { userId: req.user.id },
      process.env.JWT_SECRET,
      { expiresIn: '24h' }
    );

    // Redirect with token
    res.redirect(`/auth/callback?token=${token}`);
  }
);

React Implementation:
─────────────────────────────────────────────────────────────
function GoogleLoginButton() {
  const handleLogin = () => {
    // Redirect to backend Google auth route
    window.location.href = '/auth/google';
  };

  return (
    <button onClick={handleLogin}>
      <img src="/google-icon.svg" alt="Google" />
      Continue with Google
    </button>
  );
}

// Handle callback
// In callback page (/auth/callback)
useEffect(() => {
  const urlParams = new URLSearchParams(window.location.search);
  const token = urlParams.get('token');

  if (token) {
    localStorage.setItem('token', token);
    navigate('/dashboard');
  }
}, []);

╔════════════════════════════════════════════════════════════╗
║                   GITHUB OAUTH                             ║
╚════════════════════════════════════════════════════════════╗

Setup (GitHub):
─────────────────────────────────────────────────────────────
1. Go to Settings → Developer settings → OAuth Apps
2. Create new OAuth app
3. Set Authorization callback URL

Implementation:
─────────────────────────────────────────────────────────────
const GitHubStrategy = require('passport-github2').Strategy;

passport.use(new GitHubStrategy({
    clientID: process.env.GITHUB_CLIENT_ID,
    clientSecret: process.env.GITHUB_CLIENT_SECRET,
    callbackURL: '/auth/github/callback'
  },
  async (accessToken, refreshToken, profile, done) => {
    try {
      let user = await User.findOne({ githubId: profile.id });

      if (!user) {
        user = await User.create({
          githubId: profile.id,
          username: profile.username,
          email: profile.emails?.[0]?.value,
          name: profile.displayName,
          avatar: profile.photos[0].value,
          provider: 'github'
        });
      }

      return done(null, user);
    } catch (error) {
      return done(error, null);
    }
  }
));

app.get('/auth/github',
  passport.authenticate('github', { scope: ['user:email'] })
);

app.get('/auth/github/callback',
  passport.authenticate('github', { failureRedirect: '/login', session: false }),
  (req, res) => {
    const token = jwt.sign({ userId: req.user.id }, process.env.JWT_SECRET);
    res.redirect(`/auth/callback?token=${token}`);
  }
);

╔════════════════════════════════════════════════════════════╗
║                   MULTIPLE PROVIDERS                       ║
╚════════════════════════════════════════════════════════════╝

Unified Social Login Component:
─────────────────────────────────────────────────────────────
function SocialLogin() {
  const providers = [
    { name: 'Google', icon: GoogleIcon, url: '/auth/google' },
    { name: 'GitHub', icon: GitHubIcon, url: '/auth/github' },
    { name: 'Facebook', icon: FacebookIcon, url: '/auth/facebook' },
    { name: 'Twitter', icon: TwitterIcon, url: '/auth/twitter' },
  ];

  return (
    <div className="social-login">
      <p>Or continue with</p>
      <div className="providers">
        {providers.map(provider => (
          <button
            key={provider.name}
            onClick={() => window.location.href = provider.url}
            className="provider-button"
          >
            <provider.icon />
            {provider.name}
          </button>
        ))}
      </div>
    </div>
  );
}

Account Linking:
─────────────────────────────────────────────────────────────
// Allow users to link multiple providers to one account

app.get('/auth/google/link', requireAuth, (req, res, next) => {
  // Store current user ID in session
  req.session.linkUserId = req.user.id;

  passport.authenticate('google', {
    scope: ['profile', 'email']
  })(req, res, next);
});

app.get('/auth/google/link/callback',
  passport.authenticate('google', { session: false }),
  async (req, res) => {
    const existingUserId = req.session.linkUserId;
    const googleProfile = req.user;

    // Link Google account to existing user
    await User.updateOne(
      { _id: existingUserId },
      {
        googleId: googleProfile.googleId,
        $addToSet: { providers: 'google' }
      }
    );

    res.redirect('/settings/accounts');
  }
);

╔════════════════════════════════════════════════════════════╗
║                   OAUTH SECURITY BEST PRACTICES            ║
╚════════════════════════════════════════════════════════════╝

1. Always Use State Parameter
─────────────────────────────────────────────────────────────
// Generate random state
const state = crypto.randomBytes(32).toString('hex');
req.session.oauthState = state;

// Include in authorization URL
const authUrl = `https://provider.com/auth?state=${state}&...`;

// Verify on callback
if (req.query.state !== req.session.oauthState) {
  throw new Error('CSRF attack detected');
}

2. Use PKCE for Public Clients
─────────────────────────────────────────────────────────────
// Always use PKCE for SPAs and mobile apps
const codeVerifier = generateCodeVerifier();
const codeChallenge = await generateCodeChallenge(codeVerifier);

3. Validate ID Tokens
─────────────────────────────────────────────────────────────
// Verify JWT signature and claims
const decoded = jwt.verify(idToken, publicKey, {
  audience: YOUR_CLIENT_ID,
  issuer: 'https://accounts.google.com'
});

// Check nonce (if used)
if (decoded.nonce !== req.session.nonce) {
  throw new Error('Nonce mismatch');
}

4. Secure Token Storage
─────────────────────────────────────────────────────────────
// ❌ Don't store in localStorage (XSS risk)
localStorage.setItem('access_token', token);

// ✅ Store in httpOnly cookie
res.cookie('access_token', token, {
  httpOnly: true,
  secure: true,
  sameSite: 'lax'
});

5. Refresh Tokens Securely
─────────────────────────────────────────────────────────────
// Store refresh tokens in database
// Rotate on each use
// Invalidate all tokens on password change

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 📱 Multi-Factor Authentication

</div>

### MFA Implementation Guide 🔐

```bash
# ═══════════════════════════════════════════
# MULTI-FACTOR AUTHENTICATION (MFA)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   MFA TYPES                                ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Type                     | Security   | UX         | Cost | Use Case      |
| ------------------------ | ---------- | ---------- | ---- | ------------- |
| **SMS OTP**              | ⭐⭐       | ⭐⭐⭐⭐⭐ | $$   | Consumer apps |
| **Email OTP**            | ⭐⭐       | ⭐⭐⭐⭐   | Free | Low-risk apps |
| **TOTP (Authenticator)** | ⭐⭐⭐⭐   | ⭐⭐⭐     | Free | Most apps     |
| **Push Notification**    | ⭐⭐⭐⭐   | ⭐⭐⭐⭐⭐ | $    | Modern apps   |
| **Hardware Key**         | ⭐⭐⭐⭐⭐ | ⭐⭐       | $$$  | High security |
| **Biometric**            | ⭐⭐⭐⭐   | ⭐⭐⭐⭐⭐ | Free | Mobile apps   |

</div>

```bash
# ═══════════════════════════════════════════
# TOTP (TIME-BASED ONE-TIME PASSWORD)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   GOOGLE AUTHENTICATOR STYLE               ║
╚════════════════════════════════════════════════════════════╝

How TOTP Works:
─────────────────────────────────────────────────────────────
1. Server generates secret key
2. User scans QR code (or enters secret manually)
3. Authenticator app generates 6-digit code every 30 seconds
4. User enters code when logging in
5. Server validates code using same algorithm

Algorithm:
─────────────────────────────────────────────────────────────
code = HOTP(secret, floor(current_time / 30))

Implementation (Node.js):
─────────────────────────────────────────────────────────────
const speakeasy = require('speakeasy');
const qrcode = require('qrcode');

// Setup MFA for user
app.post('/mfa/setup', requireAuth, async (req, res) => {
  // Generate secret
  const secret = speakeasy.generateSecret({
    name: `MyApp (${req.user.email})`,
    length: 32
  });

  // Save secret to user (encrypted!)
  await User.updateOne(
    { _id: req.user.id },
    {
      mfaSecret: secret.base32,
      mfaEnabled: false  // Not enabled until verified
    }
  );

  // Generate QR code
  const qrCodeUrl = await qrcode.toDataURL(secret.otpauth_url);

  res.json({
    secret: secret.base32,  // Backup code (show once!)
    qrCode: qrCodeUrl
  });
});

// Verify and enable MFA
app.post('/mfa/verify', requireAuth, async (req, res) => {
  const { token } = req.body;
  const user = await User.findById(req.user.id);

  // Verify token
  const verified = speakeasy.totp.verify({
    secret: user.mfaSecret,
    encoding: 'base32',
    token: token,
    window: 2  // Allow 2 time steps before/after (60 seconds window)
  });

  if (!verified) {
    return res.status(400).json({ error: 'Invalid code' });
  }

  // Enable MFA
  await user.update({ mfaEnabled: true });

  // Generate backup codes
  const backupCodes = generateBackupCodes(10);
  await BackupCode.insertMany(
    backupCodes.map(code => ({
      userId: user.id,
      code: hashBackupCode(code)
    }))
  );

  res.json({
    success: true,
    backupCodes  // Show once, user must save!
  });
});

// Login with MFA
app.post('/auth/login', async (req, res) => {
  const { username, password } = req.body;

  // Validate credentials
  const user = await User.findOne({ username });
  if (!user || !await bcrypt.compare(password, user.passwordHash)) {
    return res.status(401).json({ error: 'Invalid credentials' });
  }

  // Check if MFA enabled
  if (user.mfaEnabled) {
    // Generate temporary token
    const tempToken = jwt.sign(
      { userId: user.id, mfaRequired: true },
      process.env.JWT_SECRET,
      { expiresIn: '5m' }
    );

    return res.json({
      mfaRequired: true,
      tempToken
    });
  }

  // No MFA, return regular token
  const token = generateToken(user);
  res.json({ token });
});

// Verify MFA code
app.post('/auth/mfa/verify', async (req, res) => {
  const { tempToken, mfaCode } = req.body;

  // Verify temp token
  let decoded;
  try {
    decoded = jwt.verify(tempToken, process.env.JWT_SECRET);
    if (!decoded.mfaRequired) {
      return res.status(400).json({ error: 'Invalid token' });
    }
  } catch (error) {
    return res.status(401).json({ error: 'Token expired' });
  }

  // Get user
  const user = await User.findById(decoded.userId);

  // Verify TOTP code
  const verified = speakeasy.totp.verify({
    secret: user.mfaSecret,
    encoding: 'base32',
    token: mfaCode,
    window: 2
  });

  if (!verified) {
    // Check backup codes
    const isBackupCode = await verifyBackupCode(user.id, mfaCode);
    if (!isBackupCode) {
      return res.status(401).json({ error: 'Invalid code' });
    }
  }

  // MFA verified, generate real token
  const token = generateToken(user);
  res.json({ token });
});

// Generate backup codes
function generateBackupCodes(count) {
  const codes = [];
  for (let i = 0; i < count; i++) {
    // Format: XXXX-XXXX (8 digits)
    const code = crypto.randomBytes(4).toString('hex').toUpperCase();
    codes.push(`${code.slice(0, 4)}-${code.slice(4)}`);
  }
  return codes;
}

// Hash backup code before storing
function hashBackupCode(code) {
  return crypto.createHash('sha256').update(code).digest('hex');
}

// Verify and consume backup code
async function verifyBackupCode(userId, code) {
  const hash = hashBackupCode(code);

  const backupCode = await BackupCode.findOne({
    userId,
    code: hash,
    used: false
  });

  if (!backupCode) return false;

  // Mark as used (one-time use)
  await backupCode.update({ used: true, usedAt: new Date() });

  return true;
}

React Component:
─────────────────────────────────────────────────────────────
function MFASetup() {
  const [step, setStep] = useState('setup'); // setup, verify, complete
  const [qrCode, setQrCode] = useState('');
  const [secret, setSecret] = useState('');
  const [backupCodes, setBackupCodes] = useState([]);
  const [code, setCode] = useState('');

  async function setupMFA() {
    const response = await fetch('/mfa/setup', {
      method: 'POST',
      headers: { Authorization: `Bearer ${token}` }
    });

    const data = await response.json();
    setQrCode(data.qrCode);
    setSecret(data.secret);
    setStep('verify');
  }

  async function verifyMFA() {
    const response = await fetch('/mfa/verify', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        Authorization: `Bearer ${token}`
      },
      body: JSON.stringify({ token: code })
    });

    if (response.ok) {
      const data = await response.json();
      setBackupCodes(data.backupCodes);
      setStep('complete');
    } else {
      alert('Invalid code');
    }
  }

  if (step === 'setup') {
    return (
      <div>
        <h2>Enable Two-Factor Authentication</h2>
        <button onClick={setupMFA}>Get Started</button>
      </div>
    );
  }

  if (step === 'verify') {
    return (
      <div>
        <h2>Scan QR Code</h2>
        <img src={qrCode} alt="QR Code" />
        <p>Or enter this code manually:</p>
        <code>{secret}</code>

        <h3>Enter Code from App</h3>
        <input
          value={code}
          onChange={e => setCode(e.target.value)}
          placeholder="000000"
          maxLength={6}
        />
        <button onClick={verifyMFA}>Verify</button>
      </div>
    );
  }

  if (step === 'complete') {
    return (
      <div>
        <h2>✅ MFA Enabled!</h2>
        <p>Save these backup codes (you won't see them again):</p>
        <div className="backup-codes">
          {backupCodes.map((code, i) => (
            <code key={i}>{code}</code>
          ))}
        </div>
        <button onClick={() => downloadBackupCodes(backupCodes)}>
          Download Backup Codes
        </button>
      </div>
    );
  }
}

function MFALogin({ tempToken, onSuccess }) {
  const [code, setCode] = useState('');

  async function verifyCode() {
    const response = await fetch('/auth/mfa/verify', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ tempToken, mfaCode: code })
    });

    if (response.ok) {
      const { token } = await response.json();
      onSuccess(token);
    } else {
      alert('Invalid code');
    }
  }

  return (
    <div>
      <h2>Enter Authentication Code</h2>
      <p>Open your authenticator app and enter the 6-digit code</p>
      <input
        value={code}
        onChange={e => setCode(e.target.value)}
        placeholder="000000"
        maxLength={6}
        autoFocus
      />
      <button onClick={verifyCode}>Verify</button>
      <button onClick={() => setShowBackupCode(true)}>
        Use Backup Code
      </button>
    </div>
  );
}

# ═══════════════════════════════════════════
# SMS-BASED MFA
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SMS ONE-TIME PASSWORD                    ║
╚════════════════════════════════════════════════════════════╝

Implementation (using Twilio):
─────────────────────────────────────────────────────────────
const twilio = require('twilio');
const client = twilio(
  process.env.TWILIO_ACCOUNT_SID,
  process.env.TWILIO_AUTH_TOKEN
);

// Send SMS code
async function sendSMSCode(phoneNumber) {
  // Generate 6-digit code
  const code = Math.floor(100000 + Math.random() * 900000).toString();

  // Store in Redis with 5-minute expiration
  await redis.setex(`sms:${phoneNumber}`, 300, code);

  // Send SMS
  await client.messages.create({
    body: `Your verification code is: ${code}. Valid for 5 minutes.`,
    from: process.env.TWILIO_PHONE_NUMBER,
    to: phoneNumber
  });

  return { success: true };
}

// Verify SMS code
async function verifySMSCode(phoneNumber, code) {
  const storedCode = await redis.get(`sms:${phoneNumber}`);

  if (!storedCode) {
    return { success: false, error: 'Code expired' };
  }

  if (storedCode !== code) {
    return { success: false, error: 'Invalid code' };
  }

  // Delete code after successful verification
  await redis.del(`sms:${phoneNumber}`);

  return { success: true };
}

// Login with SMS MFA
app.post('/auth/login', async (req, res) => {
  // ... validate credentials ...

  if (user.smsEnabled) {
    await sendSMSCode(user.phoneNumber);

    const tempToken = jwt.sign(
      { userId: user.id, mfaRequired: true },
      process.env.JWT_SECRET,
      { expiresIn: '5m' }
    );

    return res.json({
      mfaRequired: true,
      mfaMethod: 'sms',
      tempToken
    });
  }
});

⚠️ SMS Security Issues:
─────────────────────────────────────────────────────────────
❌ SIM swapping attacks
❌ SMS interception
❌ Not encrypted
❌ Relies on phone network
✅ But: Very user-friendly, widely adopted

Better alternatives: TOTP, Push notifications, Hardware keys

# ═══════════════════════════════════════════
# WEBAUTHN / FIDO2 (HARDWARE KEYS)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   HARDWARE SECURITY KEYS                   ║
╚════════════════════════════════════════════════════════════╝

Most secure MFA method:
─────────────────────────────────────────────────────────────
• YubiKey, Google Titan, etc.
• Phishing-resistant
• No codes to type
• Works offline

Implementation (using @simplewebauthn):
─────────────────────────────────────────────────────────────
const {
  generateRegistrationOptions,
  verifyRegistrationResponse,
  generateAuthenticationOptions,
  verifyAuthenticationResponse,
} = require('@simplewebauthn/server');

// Register hardware key
app.post('/mfa/webauthn/register/options', requireAuth, async (req, res) => {
  const user = await User.findById(req.user.id);

  const options = generateRegistrationOptions({
    rpName: 'My App',
    rpID: 'myapp.com',
    userID: user.id,
    userName: user.email,
    attestationType: 'none',
    authenticatorSelection: {
      residentKey: 'discouraged',
      userVerification: 'preferred',
    },
  });

  // Save challenge
  await redis.setex(
    `webauthn:${user.id}`,
    300,
    options.challenge
  );

  res.json(options);
});

app.post('/mfa/webauthn/register/verify', requireAuth, async (req, res) => {
  const user = await User.findById(req.user.id);
  const expectedChallenge = await redis.get(`webauthn:${user.id}`);

  const verification = await verifyRegistrationResponse({
    response: req.body,
    expectedChallenge,
    expectedOrigin: 'https://myapp.com',
    expectedRPID: 'myapp.com',
  });

  if (verification.verified) {
    // Save credential
    await Authenticator.create({
      userId: user.id,
      credentialID: verification.registrationInfo.credentialID,
      credentialPublicKey: verification.registrationInfo.credentialPublicKey,
      counter: verification.registrationInfo.counter,
    });

    res.json({ verified: true });
  } else {
    res.status(400).json({ error: 'Verification failed' });
  }
});

// Authenticate with hardware key
app.post('/auth/webauthn/options', async (req, res) => {
  const { email } = req.body;
  const user = await User.findOne({ email });

  const authenticators = await Authenticator.find({ userId: user.id });

  const options = generateAuthenticationOptions({
    rpID: 'myapp.com',
    allowCredentials: authenticators.map(auth => ({
      id: auth.credentialID,
      type: 'public-key',
      transports: ['usb', 'nfc', 'ble'],
    })),
    userVerification: 'preferred',
  });

  await redis.setex(`webauthn:${user.id}`, 300, options.challenge);

  res.json(options);
});

app.post('/auth/webauthn/verify', async (req, res) => {
  // Verify authentication response
  // Generate JWT if successful
});

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔐 Passwordless Authentication

</div>

### Modern Passwordless Methods 🚀

```bash
# ═══════════════════════════════════════════
# PASSWORDLESS AUTHENTICATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHY PASSWORDLESS?                        ║
╚════════════════════════════════════════════════════════════╝

Problems with Passwords:
─────────────────────────────────────────────────────────────
❌ Users forget them
❌ Use weak passwords
❌ Reuse across sites
❌ Phishing vulnerable
❌ Need secure storage
❌ Password reset flows complex

Passwordless Benefits:
─────────────────────────────────────────────────────────────
✅ Better security
✅ Better UX (no password to remember)
✅ Resistant to phishing
✅ No password database to breach
✅ Faster authentication
✅ Lower support costs

Types of Passwordless:
─────────────────────────────────────────────────────────────
1. Magic Links (email)
2. One-Time Passwords (SMS/Email)
3. Biometric (Face ID, Touch ID)
4. Hardware Keys (WebAuthn)
5. Push Notifications

# ═══════════════════════════════════════════
# MAGIC LINKS (EMAIL)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   EMAIL MAGIC LINKS                        ║
╚════════════════════════════════════════════════════════════╝

How It Works:
─────────────────────────────────────────────────────────────
1. User enters email
2. Server generates secure token
3. Server sends email with link containing token
4. User clicks link
5. Server verifies token
6. User logged in

Implementation:
─────────────────────────────────────────────────────────────
const crypto = require('crypto');
const nodemailer = require('nodemailer');

// Email transporter
const transporter = nodemailer.createTransport({
  host: process.env.SMTP_HOST,
  port: 587,
  secure: false,
  auth: {
    user: process.env.SMTP_USER,
    pass: process.env.SMTP_PASSWORD
  }
});

// Request magic link
app.post('/auth/magic-link', async (req, res) => {
  const { email } = req.body;

  // Validate email
  if (!email || !isValidEmail(email)) {
    return res.status(400).json({ error: 'Invalid email' });
  }

  // Find or create user
  let user = await User.findOne({ email });
  if (!user) {
    user = await User.create({ email });
  }

  // Generate secure token
  const token = crypto.randomBytes(32).toString('hex');

  // Store token with expiration (15 minutes)
  await MagicLink.create({
    token,
    userId: user.id,
    email: user.email,
    expiresAt: new Date(Date.now() + 15 * 60 * 1000)
  });

  // Generate magic link URL
  const magicLink = `${process.env.APP_URL}/auth/verify?token=${token}`;

  // Send email
  await transporter.sendMail({
    from: '"My App" <noreply@myapp.com>',
    to: email,
    subject: '🔐 Your login link',
    html: `
      <h2>Login to My App</h2>
      <p>Click the link below to log in:</p>
      <a href="${magicLink}">Log in to My App</a>
      <p>This link expires in 15 minutes.</p>
      <p>If you didn't request this, you can safely ignore this email.</p>
    `
  });

  // Don't reveal if user exists (security)
  res.json({
    success: true,
    message: 'If that email is registered, we sent a login link'
  });
});

// Verify magic link
app.get('/auth/verify', async (req, res) => {
  const { token } = req.query;

  if (!token) {
    return res.status(400).json({ error: 'Token required' });
  }

  // Find and validate token
  const magicLink = await MagicLink.findOne({
    token,
    used: false,
    expiresAt: { $gt: new Date() }
  });

  if (!magicLink) {
    return res.status(401).json({ error: 'Invalid or expired link' });
  }

  // Mark token as used
  await magicLink.updateOne({ used: true, usedAt: new Date() });

  // Get user
  const user = await User.findById(magicLink.userId);

  // Generate JWT
  const jwtToken = jwt.sign(
    { userId: user.id, email: user.email },
    process.env.JWT_SECRET,
    { expiresIn: '7d' }
  );

  // Redirect with token
  res.redirect(`/auth/callback?token=${jwtToken}`);
});

React Component:
─────────────────────────────────────────────────────────────
function MagicLinkLogin() {
  const [email, setEmail] = useState('');
  const [sent, setSent] = useState(false);
  const [loading, setLoading] = useState(false);

  async function requestMagicLink(e) {
    e.preventDefault();
    setLoading(true);

    try {
      const response = await fetch('/auth/magic-link', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ email })
      });

      if (response.ok) {
        setSent(true);
      }
    } catch (error) {
      alert('Failed to send magic link');
    } finally {
      setLoading(false);
    }
  }

  if (sent) {
    return (
      <div>
        <h2>✉️ Check your email</h2>
        <p>We sent a login link to <strong>{email}</strong></p>
        <p>Click the link in the email to log in.</p>
        <button onClick={() => setSent(false)}>
          Send another link
        </button>
      </div>
    );
  }

  return (
    <form onSubmit={requestMagicLink}>
      <h2>Log in with email</h2>
      <input
        type="email"
        value={email}
        onChange={e => setEmail(e.target.value)}
        placeholder="you@example.com"
        required
      />
      <button type="submit" disabled={loading}>
        {loading ? 'Sending...' : 'Send magic link'}
      </button>
    </form>
  );
}

// Handle callback
function AuthCallback() {
  const [searchParams] = useSearchParams();
  const navigate = useNavigate();

  useEffect(() => {
    const token = searchParams.get('token');
    if (token) {
      localStorage.setItem('token', token);
      navigate('/dashboard');
    }
  }, []);

  return <div>Logging you in...</div>;
}

Security Considerations:
─────────────────────────────────────────────────────────────
✅ Use cryptographically secure random tokens
✅ Short expiration (15 minutes)
✅ One-time use only
✅ Rate limit email sending
✅ Don't reveal if email exists
✅ Log all magic link uses
✅ Consider HTTPS-only

❌ Don't:
• Use predictable tokens
• Allow reuse of tokens
• Have long expiration
• Send to unverified emails

# ═══════════════════════════════════════════
# OTP (ONE-TIME PASSWORD)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   EMAIL/SMS OTP LOGIN                      ║
╚════════════════════════════════════════════════════════════╝

Implementation:
─────────────────────────────────────────────────────────────
// Request OTP
app.post('/auth/otp/request', async (req, res) => {
  const { email } = req.body;

  // Rate limiting (prevent abuse)
  const recentAttempts = await redis.get(`otp-attempts:${email}`);
  if (recentAttempts && parseInt(recentAttempts) >= 3) {
    return res.status(429).json({
      error: 'Too many attempts. Try again in 15 minutes.'
    });
  }

  // Find or create user
  let user = await User.findOne({ email });
  if (!user) {
    user = await User.create({ email });
  }

  // Generate 6-digit OTP
  const otp = Math.floor(100000 + Math.random() * 900000).toString();

  // Store OTP (5 minute expiration)
  await redis.setex(`otp:${email}`, 300, otp);

  // Track attempts
  await redis.incr(`otp-attempts:${email}`);
  await redis.expire(`otp-attempts:${email}`, 900); // 15 min

  // Send email
  await transporter.sendMail({
    from: '"My App" <noreply@myapp.com>',
    to: email,
    subject: 'Your login code',
    html: `
      <h2>Your login code</h2>
      <p>Your verification code is:</p>
      <h1 style="letter-spacing: 0.5em; font-size: 32px;">${otp}</h1>
      <p>This code expires in 5 minutes.</p>
      <p>If you didn't request this, ignore this email.</p>
    `
  });

  res.json({ success: true });
});

// Verify OTP
app.post('/auth/otp/verify', async (req, res) => {
  const { email, otp } = req.body;

  // Get stored OTP
  const storedOtp = await redis.get(`otp:${email}`);

  if (!storedOtp) {
    return res.status(401).json({ error: 'OTP expired' });
  }

  if (storedOtp !== otp) {
    return res.status(401).json({ error: 'Invalid OTP' });
  }

  // OTP valid, delete it
  await redis.del(`otp:${email}`);
  await redis.del(`otp-attempts:${email}`);

  // Get user
  const user = await User.findOne({ email });

  // Generate JWT
  const token = jwt.sign(
    { userId: user.id, email: user.email },
    process.env.JWT_SECRET,
    { expiresIn: '7d' }
  );

  res.json({ token, user: { id: user.id, email: user.email } });
});

React Component:
─────────────────────────────────────────────────────────────
function OTPLogin() {
  const [step, setStep] = useState('email'); // 'email' or 'verify'
  const [email, setEmail] = useState('');
  const [otp, setOtp] = useState('');
  const [loading, setLoading] = useState(false);

  async function requestOTP(e) {
    e.preventDefault();
    setLoading(true);

    try {
      const response = await fetch('/auth/otp/request', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ email })
      });

      if (response.ok) {
        setStep('verify');
      } else {
        const error = await response.json();
        alert(error.error);
      }
    } catch (error) {
      alert('Failed to send code');
    } finally {
      setLoading(false);
    }
  }

  async function verifyOTP(e) {
    e.preventDefault();
    setLoading(true);

    try {
      const response = await fetch('/auth/otp/verify', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ email, otp })
      });

      if (response.ok) {
        const { token } = await response.json();
        localStorage.setItem('token', token);
        navigate('/dashboard');
      } else {
        alert('Invalid code');
      }
    } catch (error) {
      alert('Verification failed');
    } finally {
      setLoading(false);
    }
  }

  if (step === 'email') {
    return (
      <form onSubmit={requestOTP}>
        <h2>Enter your email</h2>
        <input
          type="email"
          value={email}
          onChange={e => setEmail(e.target.value)}
          placeholder="you@example.com"
          required
        />
        <button type="submit" disabled={loading}>
          {loading ? 'Sending...' : 'Send code'}
        </button>
      </form>
    );
  }

  return (
    <form onSubmit={verifyOTP}>
      <h2>Enter verification code</h2>
      <p>We sent a code to {email}</p>
      <input
        type="text"
        value={otp}
        onChange={e => setOtp(e.target.value)}
        placeholder="000000"
        maxLength={6}
        pattern="[0-9]{6}"
        required
        autoFocus
      />
      <button type="submit" disabled={loading}>
        {loading ? 'Verifying...' : 'Verify'}
      </button>
      <button type="button" onClick={() => setStep('email')}>
        Change email
      </button>
    </form>
  );
}

# ═══════════════════════════════════════════
# BIOMETRIC AUTHENTICATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   FACE ID / TOUCH ID                       ║
╚════════════════════════════════════════════════════════════╝

Web Authentication API (WebAuthn):
─────────────────────────────────────────────────────────────
Modern browsers support platform authenticators (Face ID, Touch ID, Windows Hello)

Client-Side Implementation:
─────────────────────────────────────────────────────────────
// Check if WebAuthn is available
const isWebAuthnAvailable = window.PublicKeyCredential !== undefined;

// Check for platform authenticator (Face ID, Touch ID)
const hasPlatformAuthenticator = await PublicKeyCredential
  .isUserVerifyingPlatformAuthenticatorAvailable();

// Register biometric
async function registerBiometric() {
  // Get options from server
  const optionsResponse = await fetch('/auth/biometric/register/options', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'Authorization': `Bearer ${token}`
    }
  });

  const options = await optionsResponse.json();

  // Create credential
  const credential = await navigator.credentials.create({
    publicKey: {
      ...options,
      authenticatorSelection: {
        authenticatorAttachment: 'platform', // Platform = built-in (Face ID, Touch ID)
        userVerification: 'required',
        residentKey: 'preferred'
      }
    }
  });

  // Send to server for verification
  const verifyResponse = await fetch('/auth/biometric/register/verify', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'Authorization': `Bearer ${token}`
    },
    body: JSON.stringify({
      id: credential.id,
      rawId: arrayBufferToBase64(credential.rawId),
      response: {
        clientDataJSON: arrayBufferToBase64(credential.response.clientDataJSON),
        attestationObject: arrayBufferToBase64(credential.response.attestationObject)
      },
      type: credential.type
    })
  });

  return verifyResponse.ok;
}

// Login with biometric
async function loginWithBiometric(email) {
  // Get authentication options
  const optionsResponse = await fetch('/auth/biometric/login/options', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ email })
  });

  const options = await optionsResponse.json();

  // Get credential (triggers Face ID / Touch ID prompt)
  const credential = await navigator.credentials.get({
    publicKey: options
  });

  // Send to server for verification
  const verifyResponse = await fetch('/auth/biometric/login/verify', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      id: credential.id,
      rawId: arrayBufferToBase64(credential.rawId),
      response: {
        clientDataJSON: arrayBufferToBase64(credential.response.clientDataJSON),
        authenticatorData: arrayBufferToBase64(credential.response.authenticatorData),
        signature: arrayBufferToBase64(credential.response.signature),
        userHandle: arrayBufferToBase64(credential.response.userHandle)
      },
      type: credential.type
    })
  });

  const { token } = await verifyResponse.json();
  return token;
}

// Helper function
function arrayBufferToBase64(buffer) {
  return btoa(String.fromCharCode(...new Uint8Array(buffer)));
}

React Component:
─────────────────────────────────────────────────────────────
function BiometricLogin() {
  const [available, setAvailable] = useState(false);
  const [email, setEmail] = useState('');

  useEffect(() => {
    checkBiometricAvailability();
  }, []);

  async function checkBiometricAvailability() {
    if (window.PublicKeyCredential) {
      const available = await PublicKeyCredential
        .isUserVerifyingPlatformAuthenticatorAvailable();
      setAvailable(available);
    }
  }

  async function handleBiometricLogin() {
    try {
      const token = await loginWithBiometric(email);
      localStorage.setItem('token', token);
      navigate('/dashboard');
    } catch (error) {
      if (error.name === 'NotAllowedError') {
        alert('Biometric authentication cancelled');
      } else {
        alert('Authentication failed');
      }
    }
  }

  if (!available) {
    return <div>Biometric authentication not available on this device</div>;
  }

  return (
    <div>
      <h2>Login with Face ID / Touch ID</h2>
      <input
        type="email"
        value={email}
        onChange={e => setEmail(e.target.value)}
        placeholder="Email"
      />
      <button onClick={handleBiometricLogin}>
        🔐 Authenticate
      </button>
    </div>
  );
}

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🏢 Enterprise Solutions

</div>

### Enterprise Authentication Systems 🏛️

```bash
# ═══════════════════════════════════════════
# ENTERPRISE AUTHENTICATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SINGLE SIGN-ON (SSO)                     ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Solution          | Type          | Best For         | Complexity | Cost |
| ----------------- | ------------- | ---------------- | ---------- | ---- |
| **Okta**          | Cloud SSO     | Enterprise       | ⭐⭐⭐     | $$$  |
| **Azure AD**      | Cloud SSO     | Microsoft shops  | ⭐⭐⭐⭐   | $$   |
| **Keycloak**      | Self-hosted   | Open source      | ⭐⭐⭐⭐   | Free |
| **Auth0**         | Cloud         | Modern apps      | ⭐⭐       | $$   |
| **OneLogin**      | Cloud SSO     | Enterprise       | ⭐⭐⭐     | $$$  |
| **Ping Identity** | Cloud/On-prem | Large enterprise | ⭐⭐⭐⭐⭐ | $$$$ |

</div>

```bash
# ═══════════════════════════════════════════
# SAML 2.0 (ENTERPRISE SSO)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SAML AUTHENTICATION                      ║
╚════════════════════════════════════════════════════════════╝

What is SAML:
─────────────────────────────────────────────────────────────
Security Assertion Markup Language
• XML-based protocol
• Used for enterprise SSO
• Older but still widely used

SAML Roles:
─────────────────────────────────────────────────────────────
• Identity Provider (IdP): Okta, Azure AD, OneLogin
• Service Provider (SP): Your application

SAML Flow (SP-Initiated):
─────────────────────────────────────────────────────────────
1. User visits your app
   ↓
2. App redirects to IdP with SAML Request
   ↓
3. User logs in at IdP
   ↓
4. IdP sends SAML Response (assertion) back to app
   ↓
5. App validates assertion
   ↓
6. User logged in

Implementation (Node.js with Passport):
─────────────────────────────────────────────────────────────
const passport = require('passport');
const SamlStrategy = require('passport-saml').Strategy;

passport.use(new SamlStrategy({
    callbackUrl: 'https://myapp.com/auth/saml/callback',
    entryPoint: 'https://idp.example.com/saml/sso',
    issuer: 'myapp.com',
    cert: process.env.SAML_CERT, // IdP certificate
    // Your app's private key (for signing requests)
    privateKey: process.env.SAML_PRIVATE_KEY,
    // Signature algorithm
    signatureAlgorithm: 'sha256'
  },
  async (profile, done) => {
    // profile contains user info from IdP
    try {
      let user = await User.findOne({
        samlNameId: profile.nameID
      });

      if (!user) {
        user = await User.create({
          samlNameId: profile.nameID,
          email: profile.email || profile.nameID,
          firstName: profile.firstName,
          lastName: profile.lastName,
          department: profile.department,
          role: profile.role
        });
      } else {
        // Update user info
        await user.update({
          email: profile.email,
          firstName: profile.firstName,
          lastName: profile.lastName,
          lastLogin: new Date()
        });
      }

      return done(null, user);
    } catch (error) {
      return done(error);
    }
  }
));

// Routes
app.get('/auth/saml',
  passport.authenticate('saml', {
    failureRedirect: '/login',
    failureFlash: true
  })
);

app.post('/auth/saml/callback',
  passport.authenticate('saml', {
    failureRedirect: '/login',
    session: false
  }),
  (req, res) => {
    // Generate JWT
    const token = jwt.sign(
      { userId: req.user.id },
      process.env.JWT_SECRET,
      { expiresIn: '8h' }
    );

    res.redirect(`/auth/callback?token=${token}`);
  }
);

// Metadata endpoint (for IdP configuration)
app.get('/auth/saml/metadata', (req, res) => {
  res.type('application/xml');
  res.send(passport._strategy('saml').generateServiceProviderMetadata());
});

// Logout
app.get('/auth/saml/logout', (req, res) => {
  // Single Logout (SLO)
  passport._strategy('saml').logout(req, (err, requestUrl) => {
    if (err) {
      return res.redirect('/');
    }
    res.redirect(requestUrl);
  });
});

╔════════════════════════════════════════════════════════════╗
║                   KEYCLOAK (OPEN SOURCE SSO)               ║
╚════════════════════════════════════════════════════════════╝

Website: https://keycloak.org
Type: Self-hosted, Open Source

Why Keycloak:
─────────────────────────────────────────────────────────────
✅ Free & open source
✅ Full-featured (SSO, social login, MFA)
✅ Supports SAML, OpenID Connect, OAuth 2.0
✅ User federation (LDAP, Active Directory)
✅ Identity brokering
✅ Fine-grained authorization
✅ Admin UI
✅ Themes & customization

Setup with Docker:
─────────────────────────────────────────────────────────────
# docker-compose.yml
version: '3'
services:
  keycloak:
    image: quay.io/keycloak/keycloak:latest
    environment:
      KEYCLOAK_ADMIN: admin
      KEYCLOAK_ADMIN_PASSWORD: admin
    ports:
      - 8080:8080
    command:
      - start-dev
    volumes:
      - keycloak_data:/opt/keycloak/data

volumes:
  keycloak_data:

# Start
docker-compose up -d

# Access: http://localhost:8080

Integration (Node.js):
─────────────────────────────────────────────────────────────
const Keycloak = require('keycloak-connect');
const session = require('express-session');

// Session store
const memoryStore = new session.MemoryStore();

app.use(session({
  secret: process.env.SESSION_SECRET,
  resave: false,
  saveUninitialized: true,
  store: memoryStore
}));

// Keycloak configuration
const keycloak = new Keycloak({
  store: memoryStore
}, {
  realm: 'myrealm',
  'auth-server-url': 'http://localhost:8080',
  'ssl-required': 'external',
  resource: 'myapp',
  'public-client': true,
  'confidential-port': 0
});

app.use(keycloak.middleware());

// Protected route
app.get('/admin', keycloak.protect('admin'), (req, res) => {
  res.json({
    message: 'Admin only',
    user: req.kauth.grant.access_token.content
  });
});

// Role-based protection
app.get('/manager', keycloak.protect('realm:manager'), (req, res) => {
  res.json({ message: 'Manager access' });
});

React Integration:
─────────────────────────────────────────────────────────────
import Keycloak from 'keycloak-js';

const keycloak = new Keycloak({
  url: 'http://localhost:8080',
  realm: 'myrealm',
  clientId: 'myapp'
});

// Initialize
keycloak.init({
  onLoad: 'login-required',
  checkLoginIframe: false
}).then(authenticated => {
  if (authenticated) {
    console.log('Authenticated');
    console.log('Token:', keycloak.token);
    console.log('User:', keycloak.tokenParsed);
  }
});

// Get token for API calls
const token = keycloak.token;

// Refresh token
keycloak.updateToken(30).then(refreshed => {
  if (refreshed) {
    console.log('Token refreshed');
  }
});

// Logout
keycloak.logout();

# ═══════════════════════════════════════════
# LDAP / ACTIVE DIRECTORY
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   LDAP AUTHENTICATION                      ║
╚════════════════════════════════════════════════════════════╝

For enterprise environments using LDAP/AD:
─────────────────────────────────────────────────────────────
const ldap = require('ldapjs');

// LDAP authentication
async function authenticateLDAP(username, password) {
  return new Promise((resolve, reject) => {
    const client = ldap.createClient({
      url: process.env.LDAP_URL
    });

    // Bind (authenticate)
    const userDN = `uid=${username},ou=users,dc=example,dc=com`;

    client.bind(userDN, password, (err) => {
      if (err) {
        client.unbind();
        return reject(err);
      }

      // Search for user details
      client.search('dc=example,dc=com', {
        filter: `(uid=${username})`,
        scope: 'sub',
        attributes: ['cn', 'mail', 'telephoneNumber', 'title']
      }, (err, res) => {
        if (err) {
          client.unbind();
          return reject(err);
        }

        const entries = [];

        res.on('searchEntry', (entry) => {
          entries.push(entry.object);
        });

        res.on('end', () => {
          client.unbind();
          resolve(entries[0]);
        });

        res.on('error', (err) => {
          client.unbind();
          reject(err);
        });
      });
    });
  });
}

// Login endpoint
app.post('/auth/ldap', async (req, res) => {
  const { username, password } = req.body;

  try {
    const ldapUser = await authenticateLDAP(username, password);

    // Find or create local user
    let user = await User.findOne({ username });
    if (!user) {
      user = await User.create({
        username,
        email: ldapUser.mail,
        name: ldapUser.cn,
        ldapUser: true
      });
    }

    // Generate JWT
    const token = jwt.sign(
      { userId: user.id },
      process.env.JWT_SECRET,
      { expiresIn: '8h' }
    );

    res.json({ token, user });
  } catch (error) {
    res.status(401).json({ error: 'Authentication failed' });
  }
});

Better Approach: Use Keycloak with LDAP Federation
─────────────────────────────────────────────────────────────
Keycloak can integrate with LDAP/AD and handle:
• User sync
• Password policies
• Group mapping
• SSO across apps

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## ⚙️ Implementation Guides

</div>

### Complete Authentication Flows 🔄

```bash
# ═══════════════════════════════════════════
# COMPLETE AUTH SYSTEM ARCHITECTURE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   RECOMMENDED ARCHITECTURE                 ║
╚════════════════════════════════════════════════════════════╝

Hybrid Approach (Best of All Worlds):
─────────────────────────────────────────────────────────────

Primary: JWT (Access + Refresh Tokens)
Secondary: Social Login (OAuth 2.0)
Optional: MFA (TOTP)
Optional: Passwordless (Magic Links)

Architecture:
─────────────────────────────────────────────────────────────
┌─────────────────────────────────────────────────────┐
│ Frontend (React/Vue/Next.js)                        │
│  • Login forms                                      │
│  • Social login buttons                             │
│  • Token storage (httpOnly cookies)                 │
│  • Auto token refresh                               │
└──────────────────┬──────────────────────────────────┘
                   │
                   ↓ HTTPS
┌─────────────────────────────────────────────────────┐
│ API Gateway / Load Balancer                         │
│  • Rate limiting                                    │
│  • DDoS protection                                  │
│  • SSL termination                                  │
└──────────────────┬──────────────────────────────────┘
                   │
                   ↓
┌─────────────────────────────────────────────────────┐
│ Auth Service (Node.js/Python/Go)                    │
│  • User registration                                │
│  • Login (password, social, passwordless)           │
│  • Token generation (JWT)                           │
│  • Token refresh                                    │
│  • MFA verification                                 │
│  • Password reset                                   │
└──────────────────┬──────────────────────────────────┘
                   │
        ┌──────────┼──────────┐
        ↓          ↓          ↓
   ┌────────┐ ┌────────┐ ┌────────┐
   │ Users  │ │ Redis  │ │OAuth  │
   │   DB   │ │(tokens)│ │Provider│
   └────────┘ └────────┘ └────────┘

Database Schema:
─────────────────────────────────────────────────────────────
// users table/collection
{
  id: uuid,
  email: string (unique),
  username: string (unique),
  passwordHash: string (nullable),

  // Profile
  firstName: string,
  lastName: string,
  avatar: string,

  // Auth providers
  googleId: string,
  githubId: string,

  // MFA
  mfaEnabled: boolean,
  mfaSecret: string (encrypted),

  // Metadata
  emailVerified: boolean,
  lastLogin: timestamp,
  createdAt: timestamp,
  updatedAt: timestamp
}

// refresh_tokens
{
  id: uuid,
  token: string (hashed),
  userId: uuid (foreign key),
  expiresAt: timestamp,
  createdAt: timestamp,
  used: boolean
}

// sessions (optional, for session-based)
{
  id: string,
  userId: uuid,
  data: json,
  expiresAt: timestamp
}

// mfa_backup_codes
{
  id: uuid,
  userId: uuid,
  code: string (hashed),
  used: boolean,
  usedAt: timestamp,
  createdAt: timestamp
}

# ═══════════════════════════════════════════
# COMPLETE EXAMPLE: FULL-STACK AUTH
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   BACKEND (Express + JWT)                  ║
╚════════════════════════════════════════════════════════════╝

// server.js
const express = require('express');
const bcrypt = require('bcrypt');
const jwt = require('jsonwebtoken');
const rateLimit = require('express-rate-limit');
const helmet = require('helmet');
const cors = require('cors');
const cookieParser = require('cookie-parser');

const app = express();

// Security middleware
app.use(helmet());
app.use(cors({
  origin: process.env.FRONTEND_URL,
  credentials: true
}));
app.use(express.json());
app.use(cookieParser());

// Rate limiting
const authLimiter = rateLimit({
  windowMs: 15 * 60 * 1000,
  max: 5
});

// Token generation
function generateTokens(user) {
  const accessToken = jwt.sign(
    { userId: user.id, role: user.role },
    process.env.JWT_SECRET,
    { expiresIn: '15m' }
  );

  const refreshToken = jwt.sign(
    { userId: user.id, type: 'refresh' },
    process.env.REFRESH_TOKEN_SECRET,
    { expiresIn: '7d' }
  );

  return { accessToken, refreshToken };
}

// Register
app.post('/auth/register', authLimiter, async (req, res) => {
  try {
    const { email, password, name } = req.body;

    // Validation
    if (!email || !password || !name) {
      return res.status(400).json({ error: 'Missing fields' });
    }

    // Check if user exists
    const existing = await User.findOne({ email });
    if (existing) {
      return res.status(409).json({ error: 'Email already registered' });
    }

    // Hash password
    const passwordHash = await bcrypt.hash(password, 12);

    // Create user
    const user = await User.create({
      email,
      passwordHash,
      name,
      emailVerified: false
    });

    // Send verification email
    await sendVerificationEmail(user.email);

    // Generate tokens
    const { accessToken, refreshToken } = generateTokens(user);

    // Store refresh token
    await RefreshToken.create({
      token: refreshToken,
      userId: user.id,
      expiresAt: new Date(Date.now() + 7 * 24 * 60 * 60 * 1000)
    });

    // Set cookies
    res.cookie('accessToken', accessToken, {
      httpOnly: true,
      secure: true,
      sameSite: 'strict',
      maxAge: 15 * 60 * 1000
    });

    res.cookie('refreshToken', refreshToken, {
      httpOnly: true,
      secure: true,
      sameSite: 'strict',
      maxAge: 7 * 24 * 60 * 60 * 1000,
      path: '/auth/refresh'
    });

    res.status(201).json({
      user: {
        id: user.id,
        email: user.email,
        name: user.name
      }
    });
  } catch (error) {
    console.error('Registration error:', error);
    res.status(500).json({ error: 'Registration failed' });
  }
});

// Login
app.post('/auth/login', authLimiter, async (req, res) => {
  try {
    const { email, password } = req.body;

    // Find user
    const user = await User.findOne({ email });
    if (!user) {
      return res.status(401).json({ error: 'Invalid credentials' });
    }

    // Verify password
    const valid = await bcrypt.compare(password, user.passwordHash);
    if (!valid) {
      return res.status(401).json({ error: 'Invalid credentials' });
    }

    // Check if MFA enabled
    if (user.mfaEnabled) {
      const tempToken = jwt.sign(
        { userId: user.id, mfaRequired: true },
        process.env.JWT_SECRET,
        { expiresIn: '5m' }
      );

      return res.json({ mfaRequired: true, tempToken });
    }

    // Generate tokens
    const { accessToken, refreshToken } = generateTokens(user);

    // Store refresh token
    await RefreshToken.create({
      token: refreshToken,
      userId: user.id,
      expiresAt: new Date(Date.now() + 7 * 24 * 60 * 60 * 1000)
    });

    // Set cookies
    res.cookie('accessToken', accessToken, {
      httpOnly: true,
      secure: true,
      sameSite: 'strict',
      maxAge: 15 * 60 * 1000
    });

    res.cookie('refreshToken', refreshToken, {
      httpOnly: true,
      secure: true,
      sameSite: 'strict',
      maxAge: 7 * 24 * 60 * 60 * 1000,
      path: '/auth/refresh'
    });

    // Update last login
    await user.update({ lastLogin: new Date() });

    res.json({
      user: {
        id: user.id,
        email: user.email,
        name: user.name,
        role: user.role
      }
    });
  } catch (error) {
    console.error('Login error:', error);
    res.status(500).json({ error: 'Login failed' });
  }
});

// Refresh token
app.post('/auth/refresh', async (req, res) => {
  try {
    const { refreshToken } = req.cookies;

    if (!refreshToken) {
      return res.status(401).json({ error: 'No refresh token' });
    }

    // Verify token
    const decoded = jwt.verify(refreshToken, process.env.REFRESH_TOKEN_SECRET);

    // Check if token exists in database
    const storedToken = await RefreshToken.findOne({
      token: refreshToken,
      userId: decoded.userId,
      used: false
    });

    if (!storedToken || storedToken.expiresAt < new Date()) {
      return res.status(401).json({ error: 'Invalid refresh token' });
    }

    // Mark as used
    await storedToken.update({ used: true });

    // Get user
    const user = await User.findById(decoded.userId);

    // Generate new tokens
    const { accessToken, refreshToken: newRefreshToken } = generateTokens(user);

    // Store new refresh token
    await RefreshToken.create({
      token: newRefreshToken,
      userId: user.id,
      expiresAt: new Date(Date.now() + 7 * 24 * 60 * 60 * 1000)
    });

    // Set new cookies
    res.cookie('accessToken', accessToken, {
      httpOnly: true,
      secure: true,
      sameSite: 'strict',
      maxAge: 15 * 60 * 1000
    });

    res.cookie('refreshToken', newRefreshToken, {
      httpOnly: true,
      secure: true,
      sameSite: 'strict',
      maxAge: 7 * 24 * 60 * 60 * 1000,
      path: '/auth/refresh'
    });

    res.json({ success: true });
  } catch (error) {
    res.status(401).json({ error: 'Token refresh failed' });
  }
});

// Logout
app.post('/auth/logout', async (req, res) => {
  const { refreshToken } = req.cookies;

  if (refreshToken) {
    await RefreshToken.deleteOne({ token: refreshToken });
  }

  res.clearCookie('accessToken');
  res.clearCookie('refreshToken', { path: '/auth/refresh' });

  res.json({ success: true });
});

// Auth middleware
const requireAuth = async (req, res, next) => {
  const { accessToken } = req.cookies;

  if (!accessToken) {
    return res.status(401).json({ error: 'Not authenticated' });
  }

  try {
    const decoded = jwt.verify(accessToken, process.env.JWT_SECRET);
    req.user = { id: decoded.userId, role: decoded.role };
    next();
  } catch (error) {
    if (error.name === 'TokenExpiredError') {
      return res.status(401).json({
        error: 'Token expired',
        code: 'TOKEN_EXPIRED'
      });
    }
    res.status(401).json({ error: 'Invalid token' });
  }
};

// Protected route
app.get('/api/profile', requireAuth, async (req, res) => {
  const user = await User.findById(req.user.id);
  res.json(user);
});

app.listen(3000, () => {
  console.log('Server running on port 3000');
});

╔════════════════════════════════════════════════════════════╗
║                   FRONTEND (React + Context)               ║
╚════════════════════════════════════════════════════════════╝

// AuthContext.js
import React, { createContext, useState, useEffect, useContext } from 'react';
import axios from 'axios';

const AuthContext = createContext();

export function AuthProvider({ children }) {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    checkAuth();
  }, []);

  async function checkAuth() {
    try {
      const response = await axios.get('/api/profile', {
        withCredentials: true
      });
      setUser(response.data);
    } catch (error) {
      setUser(null);
    } finally {
      setLoading(false);
    }
  }

  async function login(email, password) {
    try {
      const response = await axios.post('/auth/login',
        { email, password },
        { withCredentials: true }
      );
      setUser(response.data.user);
      return { success: true };
    } catch (error) {
      return {
        success: false,
        error: error.response?.data?.error || 'Login failed'
      };
    }
  }

  async function register(email, password, name) {
    try {
      const response = await axios.post('/auth/register',
        { email, password, name },
        { withCredentials: true }
      );
      setUser(response.data.user);
      return { success: true };
    } catch (error) {
      return {
        success: false,
        error: error.response?.data?.error || 'Registration failed'
      };
    }
  }

  async function logout() {
    try {
      await axios.post('/auth/logout', {}, { withCredentials: true });
      setUser(null);
    } catch (error) {
      console.error('Logout failed:', error);
    }
  }

  return (
    <AuthContext.Provider value={{
      user,
      loading,
      login,
      register,
      logout
    }}>
      {children}
    </AuthContext.Provider>
  );
}

export const useAuth = () => useContext(AuthContext);

// Axios interceptor for token refresh
axios.interceptors.response.use(
  response => response,
  async error => {
    const originalRequest = error.config;

    if (error.response?.status === 401 &&
        error.response?.data?.code === 'TOKEN_EXPIRED' &&
        !originalRequest._retry) {

      originalRequest._retry = true;

      try {
        await axios.post('/auth/refresh', {}, {
          withCredentials: true
        });
        return axios(originalRequest);
      } catch (refreshError) {
        window.location.href = '/login';
        return Promise.reject(refreshError);
      }
    }

    return Promise.reject(error);
  }
);

// LoginPage.js
import { useState } from 'react';
import { useAuth } from './AuthContext';
import { useNavigate } from 'react-router-dom';

function LoginPage() {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');
  const [error, setError] = useState('');
  const { login } = useAuth();
  const navigate = useNavigate();

  async function handleSubmit(e) {
    e.preventDefault();
    setError('');

    const result = await login(email, password);

    if (result.success) {
      navigate('/dashboard');
    } else {
      setError(result.error);
    }
  }

  return (
    <div>
      <h1>Login</h1>
      {error && <div className="error">{error}</div>}

      <form onSubmit={handleSubmit}>
        <input
          type="email"
          value={email}
          onChange={e => setEmail(e.target.value)}
          placeholder="Email"
          required
        />
        <input
          type="password"
          value={password}
          onChange={e => setPassword(e.target.value)}
          placeholder="Password"
          required
        />
        <button type="submit">Login</button>
      </form>
    </div>
  );
}

// ProtectedRoute.js
import { Navigate } from 'react-router-dom';
import { useAuth } from './AuthContext';

function ProtectedRoute({ children }) {
  const { user, loading } = useAuth();

  if (loading) {
    return <div>Loading...</div>;
  }

  if (!user) {
    return <Navigate to="/login" replace />;
  }

  return children;
}

// Usage in App.js
function App() {
  return (
    <AuthProvider>
      <Routes>
        <Route path="/login" element={<LoginPage />} />
        <Route path="/register" element={<RegisterPage />} />
        <Route
          path="/dashboard"
          element={
            <ProtectedRoute>
              <Dashboard />
            </ProtectedRoute>
          }
        />
      </Routes>
    </AuthProvider>
  );
}

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## ✅ Security Best Practices

</div>

### Authentication Security Checklist 🔒

```bash
# ═══════════════════════════════════════════
# SECURITY CHECKLIST
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PASSWORD SECURITY                        ║
╚════════════════════════════════════════════════════════════╝

✅ Password Requirements:
─────────────────────────────────────────────────────────────
☐ Minimum 8 characters (12+ recommended)
☐ Require uppercase AND lowercase
☐ Require numbers
☐ Require special characters
☐ Block common passwords (top 10,000)
☐ Block passwords in data breaches (HaveIBeenPwned API)
☐ No username in password
☐ Password strength meter

✅ Password Storage:
─────────────────────────────────────────────────────────────
☐ Use bcrypt or Argon2 (NEVER plain text!)
☐ Salt rounds ≥ 10 (bcrypt)
☐ Never decrypt passwords (only hash & compare)
☐ Separate password hashes from other data
☐ Encrypt database at rest

✅ Password Reset:
─────────────────────────────────────────────────────────────
☐ Secure token generation (crypto.randomBytes)
☐ Short expiration (15-60 minutes)
☐ One-time use tokens
☐ Invalidate all sessions on password change
☐ Email notification of password change
☐ Rate limit reset requests

╔════════════════════════════════════════════════════════════╗
║                   AUTHENTICATION                           ║
╚════════════════════════════════════════════════════════════╝

✅ Login Security:
─────────────────────────────────────────────────────────────
☐ Rate limiting (5 attempts per 15 min)
☐ Account lockout after failed attempts
☐ CAPTCHA after 3 failed attempts
☐ Log all login attempts
☐ Alert on suspicious login (new device, location)
☐ No user enumeration (same error for invalid user/password)
☐ Timing attack protection (constant-time comparison)

✅ Session Management:
─────────────────────────────────────────────────────────────
☐ Secure session ID generation
☐ HttpOnly cookies
☐ Secure flag (HTTPS only)
☐ SameSite=Strict or Lax
☐ Session timeout (15-30 min idle)
☐ Absolute timeout (24 hours)
☐ Regenerate session ID on login
☐ Invalidate on logout
☐ Concurrent session limits

✅ Token Security (JWT):
─────────────────────────────────────────────────────────────
☐ Short access token expiration (15 min)
☐ Long refresh token expiration (7 days)
☐ Rotate refresh tokens on use
☐ Store refresh tokens in database
☐ Revoke refresh tokens on logout
☐ Strong JWT secret (256-bit)
☐ Verify all JWT claims (iss, aud, exp)
☐ Don't store sensitive data in JWT

╔════════════════════════════════════════════════════════════╗
║                   MULTI-FACTOR AUTHENTICATION              ║
╚════════════════════════════════════════════════════════════╝

✅ MFA Implementation:
─────────────────────────────────────────────────────────────
☐ Offer TOTP (authenticator app)
☐ Provide backup codes (10 one-time codes)
☐ Allow multiple MFA methods
☐ Require MFA for admin accounts
☐ Allow MFA reset with identity verification
☐ Log MFA events

✅ SMS/Email OTP:
─────────────────────────────────────────────────────────────
☐ 6-digit codes
☐ 5-minute expiration
☐ One-time use
☐ Rate limit code generation
☐ Don't send codes to unverified numbers/emails

╔════════════════════════════════════════════════════════════╗
║                   OAUTH & SOCIAL LOGIN                     ║
╚════════════════════════════════════════════════════════════╝

✅ OAuth Security:
─────────────────────────────────────────────────────────────
☐ Use state parameter (CSRF protection)
☐ Use PKCE for public clients
☐ Validate redirect URIs
☐ Don't expose client secrets
☐ Short authorization code lifetime
☐ Rotate refresh tokens
☐ Validate ID tokens (if using OpenID Connect)
☐ Store tokens securely (encrypted, httpOnly)

╔════════════════════════════════════════════════════════════╗
║                   GENERAL SECURITY                         ║
╚════════════════════════════════════════════════════════════╝

✅ Transport Security:
─────────────────────────────────────────────────────────────
☐ HTTPS everywhere (force redirect)
☐ HSTS header
☐ TLS 1.2+ only
☐ Strong cipher suites
☐ Valid SSL certificate

✅ API Security:
─────────────────────────────────────────────────────────────
☐ Rate limiting (per IP, per user)
☐ Input validation
☐ Output sanitization
☐ CORS configuration
☐ Security headers (Helmet.js)
☐ API versioning
☐ Request size limits

✅ Monitoring & Logging:
─────────────────────────────────────────────────────────────
☐ Log authentication events
☐ Log authorization failures
☐ Log security events (password changes, MFA setup)
☐ Monitor for suspicious patterns
☐ Alert on anomalies
☐ Retain logs (90+ days)
☐ Secure log storage

✅ Compliance:
─────────────────────────────────────────────────────────────
☐ GDPR compliance (if EU users)
☐ Privacy policy
☐ Terms of service
☐ Data retention policy
☐ Data deletion mechanism
☐ Breach notification plan

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🎓 Resources & Further Learning

</div>

### Essential Authentication Resources 📚

```
📘 Documentation
   OAuth 2.0 RFC: https://oauth.net/2/
   OpenID Connect: https://openid.net/connect/
   JWT: https://jwt.io/
   WebAuthn: https://webauthn.io/
   OWASP Auth Cheatsheet: https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html

📗 Tools & Services
   Auth0: https://auth0.com
   Firebase Auth: https://firebase.google.com/products/auth
   Supabase Auth: https://supabase.com/auth
   Clerk: https://clerk.dev
   Keycloak: https://keycloak.org

📙 Libraries
   Passport.js: https://passportjs.org
   jsonwebtoken: https://github.com/auth0/node-jsonwebtoken
   bcrypt: https://github.com/kelektiv/node.bcrypt.js
   speakeasy (TOTP): https://github.com/speakeasyjs/speakeasy

🎥 Learning Resources
   OAuth 2.0 Simplified: https://aaronparecki.com/oauth-2-simplified/
   JWT Handbook: https://auth0.com/resources/ebooks/jwt-handbook
   WebAuthn Guide: https://webauthn.guide

🔧 Testing Tools
   JWT Debugger: https://jwt.io
   OAuth Playground: https://oauth.com/playground/
   Password Strength Checker: https://haveibeenpwned.com/

📱 Authenticator Apps
   Google Authenticator
   Microsoft Authenticator
   Authy
   1Password
```

---

<div align="center">

**Built with 🔐 by MrDib, for secure authentication**

_Remember: Authentication is your first line of defense!_ 🛡️

**Stay Secure!** 🔒

</div>
