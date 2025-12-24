<div align="center">

# 🔐 Authentication & Authorization

### _Securing applications the right way_ 🛡️

![Auth](https://img.shields.io/badge/Auth-Secure-green?style=for-the-badge)
![JWT](https://img.shields.io/badge/JWT-Token_Based-blue?style=for-the-badge)
![OAuth](https://img.shields.io/badge/OAuth-2.0-red?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 Authentication Basics](#-authentication-basics)
- [🔑 JWT Authentication](#-jwt-authentication)
- [🍪 Session-Based Auth](#-session-based-auth)
- [🌐 OAuth 2.0](#-oauth-20)
- [📱 Multi-Factor Authentication](#-multi-factor-authentication)
- [👮 Role-Based Access Control](#-role-based-access-control)
- [🔒 Security Best Practices](#-security-best-practices)
- [📧 Email Verification](#-email-verification)
- [🔑 Password Reset](#-password-reset)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Authentication Basics

</div>

### Understanding Authentication vs Authorization 📖

```javascript
// ═══════════════════════════════════════════
// Authentication - "Who are you?"
// ═══════════════════════════════════════════

/*
Authentication verifies identity:
- Login with email/password
- OAuth (Google, GitHub)
- Biometric (fingerprint, face)
- API keys
- Magic links
*/

// ═══════════════════════════════════════════
// Authorization - "What can you do?"
// ═══════════════════════════════════════════

/*
Authorization controls access:
- Role-Based (RBAC): admin, user, moderator
- Permission-Based: read:posts, write:posts
- Resource-Based: only owner can edit
- Attribute-Based (ABAC): complex rules
*/

// ═══════════════════════════════════════════
// Common Authentication Methods
// ═══════════════════════════════════════════

/*
1. JWT (JSON Web Tokens)
   ✅ Stateless
   ✅ Scalable
   ✅ Cross-domain
   ❌ Can't revoke easily
   Best for: APIs, microservices

2. Session-Based
   ✅ Easy to revoke
   ✅ Server controls session
   ❌ Requires session storage
   ❌ Not scalable
   Best for: Traditional web apps

3. OAuth 2.0
   ✅ Third-party login
   ✅ No password management
   ✅ Standard protocol
   ❌ Complex setup
   Best for: Social login

4. API Keys
   ✅ Simple
   ✅ Good for services
   ❌ Less secure
   Best for: Machine-to-machine
*/
```

---

<div align="center">

## 🔑 JWT Authentication

</div>

### Complete JWT Implementation 🚀

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install jsonwebtoken bcryptjs
npm install cookie-parser
```

```javascript
// ═══════════════════════════════════════════
// JWT Utilities
// ═══════════════════════════════════════════

import jwt from "jsonwebtoken";
import bcrypt from "bcryptjs";

const JWT_SECRET = process.env.JWT_SECRET;
const JWT_REFRESH_SECRET = process.env.JWT_REFRESH_SECRET;
const JWT_EXPIRES_IN = "15m"; // Short-lived access token
const REFRESH_EXPIRES_IN = "7d"; // Long-lived refresh token

// ═══════════════════════════════════════════
// Password Hashing
// ═══════════════════════════════════════════

export const hashPassword = async (password) => {
  const salt = await bcrypt.genSalt(12); // 12 rounds is secure
  return bcrypt.hash(password, salt);
};

export const verifyPassword = async (password, hash) => {
  return bcrypt.compare(password, hash);
};

// ═══════════════════════════════════════════
// Token Generation
// ═══════════════════════════════════════════

export const generateAccessToken = (user) => {
  const payload = {
    id: user.id,
    email: user.email,
    role: user.role,
  };

  return jwt.sign(payload, JWT_SECRET, {
    expiresIn: JWT_EXPIRES_IN,
    issuer: "your-app",
    audience: "your-app-users",
  });
};

export const generateRefreshToken = (user) => {
  const payload = {
    id: user.id,
    tokenVersion: user.tokenVersion, // For token invalidation
  };

  return jwt.sign(payload, JWT_REFRESH_SECRET, {
    expiresIn: REFRESH_EXPIRES_IN,
  });
};

// ═══════════════════════════════════════════
// Token Verification
// ═══════════════════════════════════════════

export const verifyAccessToken = (token) => {
  try {
    return jwt.verify(token, JWT_SECRET);
  } catch (error) {
    if (error.name === "TokenExpiredError") {
      throw new Error("Access token expired");
    }
    if (error.name === "JsonWebTokenError") {
      throw new Error("Invalid access token");
    }
    throw error;
  }
};

export const verifyRefreshToken = (token) => {
  try {
    return jwt.verify(token, JWT_REFRESH_SECRET);
  } catch (error) {
    throw new Error("Invalid refresh token");
  }
};

// ═══════════════════════════════════════════
// Authentication Middleware
// ═══════════════════════════════════════════

export const authenticateToken = async (req, res, next) => {
  try {
    // Extract token from header or cookie
    const token = extractToken(req);

    if (!token) {
      return res.status(401).json({
        success: false,
        error: {
          message: "Authentication required",
          code: "NO_TOKEN",
        },
      });
    }

    // Verify token
    const decoded = verifyAccessToken(token);

    // Attach user to request
    req.user = decoded;

    // Optional: Load full user from database
    const user = await db.user.findUnique({
      where: { id: decoded.id },
      select: {
        id: true,
        email: true,
        name: true,
        role: true,
      },
    });

    if (!user) {
      return res.status(401).json({
        success: false,
        error: {
          message: "User not found",
          code: "USER_NOT_FOUND",
        },
      });
    }

    req.user = user;
    next();
  } catch (error) {
    return res.status(401).json({
      success: false,
      error: {
        message: error.message,
        code: "INVALID_TOKEN",
      },
    });
  }
};

// ═══════════════════════════════════════════
// Extract Token Helper
// ═══════════════════════════════════════════

const extractToken = (req) => {
  // 1. Check Authorization header
  const authHeader = req.headers.authorization;
  if (authHeader?.startsWith("Bearer ")) {
    return authHeader.substring(7);
  }

  // 2. Check cookies
  if (req.cookies?.accessToken) {
    return req.cookies.accessToken;
  }

  // 3. Check query parameter (not recommended, but useful for debugging)
  if (req.query?.token) {
    return req.query.token;
  }

  return null;
};

// ═══════════════════════════════════════════
// Auth Routes
// ═══════════════════════════════════════════

import { Router } from "express";
import { body, validationResult } from "express-validator";

const router = Router();

// ═══════════════════════════════════════════
// Register
// ═══════════════════════════════════════════

router.post(
  "/register",
  [
    body("email").isEmail().normalizeEmail(),
    body("password")
      .isLength({ min: 8 })
      .matches(/^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])/)
      .withMessage(
        "Password must contain uppercase, lowercase, number and special character"
      ),
    body("name").trim().isLength({ min: 2, max: 100 }),
  ],
  async (req, res, next) => {
    try {
      // Validate input
      const errors = validationResult(req);
      if (!errors.isEmpty()) {
        return res.status(400).json({
          success: false,
          errors: errors.array(),
        });
      }

      const { email, password, name } = req.body;

      // Check if user exists
      const existingUser = await db.user.findUnique({
        where: { email },
      });

      if (existingUser) {
        return res.status(409).json({
          success: false,
          error: {
            message: "Email already registered",
            code: "EMAIL_EXISTS",
          },
        });
      }

      // Hash password
      const hashedPassword = await hashPassword(password);

      // Create user
      const user = await db.user.create({
        data: {
          email,
          password: hashedPassword,
          name,
          tokenVersion: 0,
        },
        select: {
          id: true,
          email: true,
          name: true,
          role: true,
        },
      });

      // Generate tokens
      const accessToken = generateAccessToken(user);
      const refreshToken = generateRefreshToken(user);

      // Store refresh token in database
      await db.refreshToken.create({
        data: {
          token: refreshToken,
          userId: user.id,
          expiresAt: new Date(Date.now() + 7 * 24 * 60 * 60 * 1000),
        },
      });

      // Set tokens in cookies (httpOnly for security)
      res.cookie("accessToken", accessToken, {
        httpOnly: true,
        secure: process.env.NODE_ENV === "production",
        sameSite: "strict",
        maxAge: 15 * 60 * 1000, // 15 minutes
      });

      res.cookie("refreshToken", refreshToken, {
        httpOnly: true,
        secure: process.env.NODE_ENV === "production",
        sameSite: "strict",
        maxAge: 7 * 24 * 60 * 60 * 1000, // 7 days
      });

      res.status(201).json({
        success: true,
        data: {
          user,
          accessToken,
          refreshToken,
        },
      });
    } catch (error) {
      next(error);
    }
  }
);

// ═══════════════════════════════════════════
// Login
// ═══════════════════════════════════════════

router.post(
  "/login",
  [body("email").isEmail().normalizeEmail(), body("password").notEmpty()],
  async (req, res, next) => {
    try {
      const errors = validationResult(req);
      if (!errors.isEmpty()) {
        return res.status(400).json({
          success: false,
          errors: errors.array(),
        });
      }

      const { email, password } = req.body;

      // Find user
      const user = await db.user.findUnique({
        where: { email },
      });

      if (!user) {
        return res.status(401).json({
          success: false,
          error: {
            message: "Invalid credentials",
            code: "INVALID_CREDENTIALS",
          },
        });
      }

      // Verify password
      const isValid = await verifyPassword(password, user.password);

      if (!isValid) {
        return res.status(401).json({
          success: false,
          error: {
            message: "Invalid credentials",
            code: "INVALID_CREDENTIALS",
          },
        });
      }

      // Update last login
      await db.user.update({
        where: { id: user.id },
        data: { lastLogin: new Date() },
      });

      // Generate tokens
      const accessToken = generateAccessToken(user);
      const refreshToken = generateRefreshToken(user);

      // Store refresh token
      await db.refreshToken.create({
        data: {
          token: refreshToken,
          userId: user.id,
          expiresAt: new Date(Date.now() + 7 * 24 * 60 * 60 * 1000),
        },
      });

      // Set cookies
      res.cookie("accessToken", accessToken, {
        httpOnly: true,
        secure: process.env.NODE_ENV === "production",
        sameSite: "strict",
        maxAge: 15 * 60 * 1000,
      });

      res.cookie("refreshToken", refreshToken, {
        httpOnly: true,
        secure: process.env.NODE_ENV === "production",
        sameSite: "strict",
        maxAge: 7 * 24 * 60 * 60 * 1000,
      });

      res.json({
        success: true,
        data: {
          user: {
            id: user.id,
            email: user.email,
            name: user.name,
            role: user.role,
          },
          accessToken,
          refreshToken,
        },
      });
    } catch (error) {
      next(error);
    }
  }
);

// ═══════════════════════════════════════════
// Refresh Token
// ═══════════════════════════════════════════

router.post("/refresh", async (req, res, next) => {
  try {
    const refreshToken = req.cookies?.refreshToken || req.body.refreshToken;

    if (!refreshToken) {
      return res.status(401).json({
        success: false,
        error: {
          message: "Refresh token required",
          code: "NO_REFRESH_TOKEN",
        },
      });
    }

    // Verify refresh token
    const decoded = verifyRefreshToken(refreshToken);

    // Check if token exists in database and not expired
    const storedToken = await db.refreshToken.findFirst({
      where: {
        token: refreshToken,
        userId: decoded.id,
        expiresAt: { gt: new Date() },
        revoked: false,
      },
      include: {
        user: {
          select: {
            id: true,
            email: true,
            name: true,
            role: true,
            tokenVersion: true,
          },
        },
      },
    });

    if (!storedToken) {
      return res.status(401).json({
        success: false,
        error: {
          message: "Invalid or expired refresh token",
          code: "INVALID_REFRESH_TOKEN",
        },
      });
    }

    // Check token version (for invalidating all tokens)
    if (storedToken.user.tokenVersion !== decoded.tokenVersion) {
      return res.status(401).json({
        success: false,
        error: {
          message: "Token has been invalidated",
          code: "TOKEN_INVALIDATED",
        },
      });
    }

    // Generate new tokens
    const newAccessToken = generateAccessToken(storedToken.user);
    const newRefreshToken = generateRefreshToken(storedToken.user);

    // Delete old refresh token
    await db.refreshToken.delete({
      where: { id: storedToken.id },
    });

    // Store new refresh token
    await db.refreshToken.create({
      data: {
        token: newRefreshToken,
        userId: storedToken.user.id,
        expiresAt: new Date(Date.now() + 7 * 24 * 60 * 60 * 1000),
      },
    });

    // Set new cookies
    res.cookie("accessToken", newAccessToken, {
      httpOnly: true,
      secure: process.env.NODE_ENV === "production",
      sameSite: "strict",
      maxAge: 15 * 60 * 1000,
    });

    res.cookie("refreshToken", newRefreshToken, {
      httpOnly: true,
      secure: process.env.NODE_ENV === "production",
      sameSite: "strict",
      maxAge: 7 * 24 * 60 * 60 * 1000,
    });

    res.json({
      success: true,
      data: {
        accessToken: newAccessToken,
        refreshToken: newRefreshToken,
      },
    });
  } catch (error) {
    next(error);
  }
});

// ═══════════════════════════════════════════
// Logout
// ═══════════════════════════════════════════

router.post("/logout", authenticateToken, async (req, res, next) => {
  try {
    const refreshToken = req.cookies?.refreshToken || req.body.refreshToken;

    if (refreshToken) {
      // Delete specific refresh token
      await db.refreshToken.deleteMany({
        where: {
          token: refreshToken,
          userId: req.user.id,
        },
      });
    }

    // Clear cookies
    res.clearCookie("accessToken");
    res.clearCookie("refreshToken");

    res.json({
      success: true,
      message: "Logged out successfully",
    });
  } catch (error) {
    next(error);
  }
});

// ═══════════════════════════════════════════
// Logout All Devices
// ═══════════════════════════════════════════

router.post("/logout-all", authenticateToken, async (req, res, next) => {
  try {
    // Delete all refresh tokens for this user
    await db.refreshToken.deleteMany({
      where: { userId: req.user.id },
    });

    // Increment token version to invalidate all existing tokens
    await db.user.update({
      where: { id: req.user.id },
      data: { tokenVersion: { increment: 1 } },
    });

    // Clear cookies
    res.clearCookie("accessToken");
    res.clearCookie("refreshToken");

    res.json({
      success: true,
      message: "Logged out from all devices",
    });
  } catch (error) {
    next(error);
  }
});

// =══════════════════════════════════════════
// Get Current User
// ═══════════════════════════════════════════

router.get("/me", authenticateToken, async (req, res, next) => {
  try {
    const user = await db.user.findUnique({
      where: { id: req.user.id },
      select: {
        id: true,
        email: true,
        name: true,
        role: true,
        avatar: true,
        createdAt: true,
        emailVerified: true,
      },
    });

    res.json({
      success: true,
      data: { user },
    });
  } catch (error) {
    next(error);
  }
});

export default router;
```

**📦 JWT Resources:**

- JWT.io: https://jwt.io/
- jsonwebtoken: https://github.com/auth0/node-jsonwebtoken

> **💡 Pro Tip:** Use short-lived access tokens (15min) and long-lived refresh tokens (7 days). Store refresh tokens in httpOnly cookies for security!

---

<div align="center">

## 🍪 Session-Based Auth

</div>

### Traditional Session Authentication 🔒

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install express-session connect-redis redis
npm install express-mysql-session mysql2
```

```javascript
// ═══════════════════════════════════════════
// Session Configuration
// ═══════════════════════════════════════════

import session from "express-session";
import RedisStore from "connect-redis";
import { createClient } from "redis";

// Create Redis client
const redisClient = createClient({
  url: process.env.REDIS_URL,
  legacyMode: true,
});

redisClient.connect().catch(console.error);

// Session middleware
app.use(
  session({
    store: new RedisStore({ client: redisClient }),
    secret: process.env.SESSION_SECRET,
    resave: false,
    saveUninitialized: false,
    name: "sessionId",
    cookie: {
      secure: process.env.NODE_ENV === "production",
      httpOnly: true,
      maxAge: 1000 * 60 * 60 * 24 * 7, // 7 days
      sameSite: "strict",
    },
  })
);

// ═══════════════════════════════════════════
// Session Auth Routes
// ═══════════════════════════════════════════

// Login
router.post("/login", async (req, res) => {
  const { email, password } = req.body;

  const user = await db.user.findUnique({ where: { email } });

  if (!user || !(await verifyPassword(password, user.password))) {
    return res.status(401).json({ error: "Invalid credentials" });
  }

  // Store user in session
  req.session.userId = user.id;
  req.session.role = user.role;

  // Regenerate session ID (prevent session fixation)
  req.session.regenerate((err) => {
    if (err) return res.status(500).json({ error: "Session error" });

    req.session.userId = user.id;
    req.session.role = user.role;

    res.json({
      success: true,
      user: {
        id: user.id,
        email: user.email,
        name: user.name,
      },
    });
  });
});

// Logout
router.post("/logout", (req, res) => {
  req.session.destroy((err) => {
    if (err) return res.status(500).json({ error: "Logout failed" });

    res.clearCookie("sessionId");
    res.json({ success: true, message: "Logged out" });
  });
});

// Session middleware
const requireSession = (req, res, next) => {
  if (!req.session.userId) {
    return res.status(401).json({ error: "Authentication required" });
  }
  next();
};
```

> **💡 Pro Tip:** Use Redis for session storage in production. Memory store is only for development!

---

<div align="center">

## 🌐 OAuth 2.0

</div>

### Social Login with Passport.js 🚀

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install passport passport-google-oauth20 passport-github2
npm install passport-facebook passport-twitter
```

```javascript
// ═══════════════════════════════════════════
// Passport Configuration
// ═══════════════════════════════════════════

import passport from "passport";
import { Strategy as GoogleStrategy } from "passport-google-oauth20";
import { Strategy as GitHubStrategy } from "passport-github2";

// ═══════════════════════════════════════════
// Google OAuth Strategy
// ═══════════════════════════════════════════

passport.use(
  new GoogleStrategy(
    {
      clientID: process.env.GOOGLE_CLIENT_ID,
      clientSecret: process.env.GOOGLE_CLIENT_SECRET,
      callbackURL: "/api/auth/google/callback",
      scope: ["profile", "email"],
    },
    async (accessToken, refreshToken, profile, done) => {
      try {
        // Find or create user
        let user = await db.user.findUnique({
          where: { googleId: profile.id },
        });

        if (!user) {
          // Check if email exists
          const existingUser = await db.user.findUnique({
            where: { email: profile.emails[0].value },
          });

          if (existingUser) {
            // Link Google account to existing user
            user = await db.user.update({
              where: { id: existingUser.id },
              data: { googleId: profile.id },
            });
          } else {
            // Create new user
            user = await db.user.create({
              data: {
                googleId: profile.id,
                email: profile.emails[0].value,
                name: profile.displayName,
                avatar: profile.photos[0]?.value,
                emailVerified: true, // Google emails are verified
                provider: "google",
              },
            });
          }
        }

        return done(null, user);
      } catch (error) {
        return done(error, null);
      }
    }
  )
);

// ═══════════════════════════════════════════
// GitHub OAuth Strategy
// ═══════════════════════════════════════════

passport.use(
  new GitHubStrategy(
    {
      clientID: process.env.GITHUB_CLIENT_ID,
      clientSecret: process.env.GITHUB_CLIENT_SECRET,
      callbackURL: "/api/auth/github/callback",
      scope: ["user:email"],
    },
    async (accessToken, refreshToken, profile, done) => {
      try {
        let user = await db.user.findUnique({
          where: { githubId: profile.id },
        });

        if (!user) {
          const email = profile.emails?.[0]?.value;

          user = await db.user.create({
            data: {
              githubId: profile.id,
              email,
              username: profile.username,
              name: profile.displayName || profile.username,
              avatar: profile.photos[0]?.value,
              provider: "github",
              emailVerified: profile.emails?.[0]?.verified || false,
            },
          });
        }

        return done(null, user);
      } catch (error) {
        return done(error, null);
      }
    }
  )
);

// ═══════════════════════════════════════════
// OAuth Routes
// ═══════════════════════════════════════════

// Google login
router.get(
  "/google",
  passport.authenticate("google", { scope: ["profile", "email"] })
);

// Google callback
router.get(
  "/google/callback",
  passport.authenticate("google", {
    session: false,
    failureRedirect: `${process.env.CLIENT_URL}/login?error=google_auth_failed`,
  }),
  async (req, res) => {
    // Generate JWT for the user
    const accessToken = generateAccessToken(req.user);
    const refreshToken = generateRefreshToken(req.user);

    // Store refresh token
    await db.refreshToken.create({
      data: {
        token: refreshToken,
        userId: req.user.id,
        expiresAt: new Date(Date.now() + 7 * 24 * 60 * 60 * 1000),
      },
    });

    // Redirect to frontend with tokens
    res.redirect(
      `${process.env.CLIENT_URL}/auth/callback?` +
        `accessToken=${accessToken}&` +
        `refreshToken=${refreshToken}`
    );
  }
);

// GitHub login
router.get(
  "/github",
  passport.authenticate("github", { scope: ["user:email"] })
);

// GitHub callback
router.get(
  "/github/callback",
  passport.authenticate("github", {
    session: false,
    failureRedirect: `${process.env.CLIENT_URL}/login?error=github_auth_failed`,
  }),
  async (req, res) => {
    const accessToken = generateAccessToken(req.user);
    const refreshToken = generateRefreshToken(req.user);

    await db.refreshToken.create({
      data: {
        token: refreshToken,
        userId: req.user.id,
        expiresAt: new Date(Date.now() + 7 * 24 * 60 * 60 * 1000),
      },
    });

    res.redirect(
      `${process.env.CLIENT_URL}/auth/callback?` +
        `accessToken=${accessToken}&` +
        `refreshToken=${refreshToken}`
    );
  }
);
```

**📦 OAuth Resources:**

- Passport.js: https://www.passportjs.org/
- OAuth 2.0: https://oauth.net/2/

> **💡 Pro Tip:** Store OAuth tokens securely. Never expose client secrets. Use PKCE for mobile apps!

---

<div align="center">

## 📱 Multi-Factor Authentication

</div>
Two-Factor Authentication (2FA) 🔒

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install speakeasy qrcode
```

```javascript
// ═══════════════════════════════════════════
// 2FA Setup
// ═══════════════════════════════════════════

import speakeasy from "speakeasy";
import QRCode from "qrcode";

// ═══════════════════════════════════════════
// Generate 2FA Secret
// ═══════════════════════════════════════════

router.post("/2fa/setup", authenticateToken, async (req, res, next) => {
  try {
    // Check if 2FA is already enabled
    const user = await db.user.findUnique({
      where: { id: req.user.id },
    });

    if (user.twoFactorEnabled) {
      return res.status(400).json({
        success: false,
        error: {
          message: "2FA is already enabled",
          code: "2FA_ALREADY_ENABLED",
        },
      });
    }

    // Generate secret
    const secret = speakeasy.generateSecret({
      name: `YourApp (${user.email})`,
      issuer: "YourApp",
      length: 32,
    });

    // Generate QR code
    const qrCodeUrl = await QRCode.toDataURL(secret.otpauth_url);

    // Store temporary secret (not yet enabled)
    await db.user.update({
      where: { id: req.user.id },
      data: {
        twoFactorSecret: secret.base32,
        twoFactorEnabled: false,
      },
    });

    res.json({
      success: true,
      data: {
        secret: secret.base32,
        qrCode: qrCodeUrl,
        otpauthUrl: secret.otpauth_url,
      },
    });
  } catch (error) {
    next(error);
  }
});

// ═══════════════════════════════════════════
// Verify and Enable 2FA
// ═══════════════════════════════════════════

router.post("/2fa/verify", authenticateToken, async (req, res, next) => {
  try {
    const { token } = req.body;

    if (!token) {
      return res.status(400).json({
        success: false,
        error: {
          message: "2FA token required",
          code: "TOKEN_REQUIRED",
        },
      });
    }

    const user = await db.user.findUnique({
      where: { id: req.user.id },
    });

    if (!user.twoFactorSecret) {
      return res.status(400).json({
        success: false,
        error: {
          message: "2FA not set up",
          code: "2FA_NOT_SETUP",
        },
      });
    }

    // Verify token
    const verified = speakeasy.totp.verify({
      secret: user.twoFactorSecret,
      encoding: "base32",
      token,
      window: 2, // Allow 2 time steps before and after
    });

    if (!verified) {
      return res.status(400).json({
        success: false,
        error: {
          message: "Invalid 2FA token",
          code: "INVALID_2FA_TOKEN",
        },
      });
    }

    // Generate backup codes
    const backupCodes = Array.from({ length: 10 }, () =>
      Math.random().toString(36).substring(2, 10).toUpperCase()
    );

    // Hash backup codes
    const hashedBackupCodes = await Promise.all(
      backupCodes.map((code) => hashPassword(code))
    );

    // Enable 2FA
    await db.user.update({
      where: { id: req.user.id },
      data: {
        twoFactorEnabled: true,
        backupCodes: hashedBackupCodes,
      },
    });

    res.json({
      success: true,
      message: "2FA enabled successfully",
      data: {
        backupCodes, // Show once, user must save these
      },
    });
  } catch (error) {
    next(error);
  }
});

// ═══════════════════════════════════════════
// Login with 2FA
// ═══════════════════════════════════════════

router.post("/login/2fa", async (req, res, next) => {
  try {
    const { email, password, twoFactorToken } = req.body;

    // Find user
    const user = await db.user.findUnique({ where: { email } });

    if (!user || !(await verifyPassword(password, user.password))) {
      return res.status(401).json({
        success: false,
        error: {
          message: "Invalid credentials",
          code: "INVALID_CREDENTIALS",
        },
      });
    }

    // Check if 2FA is enabled
    if (user.twoFactorEnabled) {
      if (!twoFactorToken) {
        return res.status(403).json({
          success: false,
          error: {
            message: "2FA token required",
            code: "2FA_REQUIRED",
          },
        });
      }

      // Verify 2FA token
      const verified = speakeasy.totp.verify({
        secret: user.twoFactorSecret,
        encoding: "base32",
        token: twoFactorToken,
        window: 2,
      });

      if (!verified) {
        // Try backup codes
        let backupCodeValid = false;

        for (let i = 0; i < user.backupCodes.length; i++) {
          if (await verifyPassword(twoFactorToken, user.backupCodes[i])) {
            backupCodeValid = true;

            // Remove used backup code
            const updatedCodes = [...user.backupCodes];
            updatedCodes.splice(i, 1);

            await db.user.update({
              where: { id: user.id },
              data: { backupCodes: updatedCodes },
            });

            break;
          }
        }

        if (!backupCodeValid) {
          return res.status(401).json({
            success: false,
            error: {
              message: "Invalid 2FA token",
              code: "INVALID_2FA_TOKEN",
            },
          });
        }
      }
    }

    // Generate tokens
    const accessToken = generateAccessToken(user);
    const refreshToken = generateRefreshToken(user);

    // Store refresh token
    await db.refreshToken.create({
      data: {
        token: refreshToken,
        userId: user.id,
        expiresAt: new Date(Date.now() + 7 * 24 * 60 * 60 * 1000),
      },
    });

    res.json({
      success: true,
      data: {
        user: {
          id: user.id,
          email: user.email,
          name: user.name,
        },
        accessToken,
        refreshToken,
      },
    });
  } catch (error) {
    next(error);
  }
});

// ═══════════════════════════════════════════
// Disable 2FA
// ═══════════════════════════════════════════

router.post("/2fa/disable", authenticateToken, async (req, res, next) => {
  try {
    const { password } = req.body;

    const user = await db.user.findUnique({
      where: { id: req.user.id },
    });

    // Verify password
    if (!(await verifyPassword(password, user.password))) {
      return res.status(401).json({
        success: false,
        error: {
          message: "Invalid password",
          code: "INVALID_PASSWORD",
        },
      });
    }

    // Disable 2FA
    await db.user.update({
      where: { id: req.user.id },
      data: {
        twoFactorEnabled: false,
        twoFactorSecret: null,
        backupCodes: [],
      },
    });

    res.json({
      success: true,
      message: "2FA disabled successfully",
    });
  } catch (error) {
    next(error);
  }
});
```

**📦 2FA Resources:**

- Speakeasy: https://github.com/speakeasyjs/speakeasy
- TOTP: https://tools.ietf.org/html/rfc6238

> **💡 Pro Tip:** Always provide backup codes! Users can lose their authenticator app. Store backup codes hashed, just like passwords!

---

<div align="center">

## 👮 Role-Based Access Control

</div>

### RBAC Implementation 🛡️

```javascript
// ═══════════════════════════════════════════
// Role Definitions
// ═══════════════════════════════════════════

export const ROLES = {
  USER: "user",
  MODERATOR: "moderator",
  ADMIN: "admin",
  SUPER_ADMIN: "super_admin",
};

// Role hierarchy
const ROLE_HIERARCHY = {
  [ROLES.USER]: 0,
  [ROLES.MODERATOR]: 1,
  [ROLES.ADMIN]: 2,
  [ROLES.SUPER_ADMIN]: 3,
};

// ═══════════════════════════════════════════
// Permission Definitions
// ═══════════════════════════════════════════

export const PERMISSIONS = {
  // User permissions
  "user:read": [ROLES.USER, ROLES.MODERATOR, ROLES.ADMIN, ROLES.SUPER_ADMIN],
  "user:update:own": [
    ROLES.USER,
    ROLES.MODERATOR,
    ROLES.ADMIN,
    ROLES.SUPER_ADMIN,
  ],
  "user:delete:own": [
    ROLES.USER,
    ROLES.MODERATOR,
    ROLES.ADMIN,
    ROLES.SUPER_ADMIN,
  ],

  // Post permissions
  "post:create": [ROLES.USER, ROLES.MODERATOR, ROLES.ADMIN, ROLES.SUPER_ADMIN],
  "post:update:own": [
    ROLES.USER,
    ROLES.MODERATOR,
    ROLES.ADMIN,
    ROLES.SUPER_ADMIN,
  ],
  "post:delete:own": [
    ROLES.USER,
    ROLES.MODERATOR,
    ROLES.ADMIN,
    ROLES.SUPER_ADMIN,
  ],
  "post:update:any": [ROLES.MODERATOR, ROLES.ADMIN, ROLES.SUPER_ADMIN],
  "post:delete:any": [ROLES.MODERATOR, ROLES.ADMIN, ROLES.SUPER_ADMIN],

  // Admin permissions
  "user:update:any": [ROLES.ADMIN, ROLES.SUPER_ADMIN],
  "user:delete:any": [ROLES.ADMIN, ROLES.SUPER_ADMIN],
  "role:assign": [ROLES.ADMIN, ROLES.SUPER_ADMIN],

  // Super admin only
  "admin:create": [ROLES.SUPER_ADMIN],
  "admin:delete": [ROLES.SUPER_ADMIN],
};

// ═══════════════════════════════════════════
// Role Middleware
// ═══════════════════════════════════════════

export const requireRole = (...allowedRoles) => {
  return (req, res, next) => {
    if (!req.user) {
      return res.status(401).json({
        success: false,
        error: {
          message: "Authentication required",
          code: "NOT_AUTHENTICATED",
        },
      });
    }

    if (!allowedRoles.includes(req.user.role)) {
      return res.status(403).json({
        success: false,
        error: {
          message: "Insufficient permissions",
          code: "FORBIDDEN",
          requiredRoles: allowedRoles,
          userRole: req.user.role,
        },
      });
    }

    next();
  };
};

// ═══════════════════════════════════════════
// Permission Middleware
// ═══════════════════════════════════════════

export const requirePermission = (permission) => {
  return (req, res, next) => {
    if (!req.user) {
      return res.status(401).json({
        success: false,
        error: {
          message: "Authentication required",
          code: "NOT_AUTHENTICATED",
        },
      });
    }

    const allowedRoles = PERMISSIONS[permission] || [];

    if (!allowedRoles.includes(req.user.role)) {
      return res.status(403).json({
        success: false,
        error: {
          message: "Insufficient permissions",
          code: "FORBIDDEN",
          permission,
        },
      });
    }

    next();
  };
};

// ═══════════════════════════════════════════
// Resource Ownership Middleware
// ═══════════════════════════════════════════

export const requireOwnership = (resourceType, idParam = "id") => {
  return async (req, res, next) => {
    try {
      const resourceId = req.params[idParam];

      // Fetch resource
      const resource = await db[resourceType].findUnique({
        where: { id: resourceId },
      });

      if (!resource) {
        return res.status(404).json({
          success: false,
          error: {
            message: `${resourceType} not found`,
            code: "RESOURCE_NOT_FOUND",
          },
        });
      }

      // Check ownership or admin
      if (
        resource.userId !== req.user.id &&
        !ROLE_HIERARCHY[req.user.role] >= ROLE_HIERARCHY[ROLES.MODERATOR]
      ) {
        return res.status(403).json({
          success: false,
          error: {
            message: "Access denied",
            code: "NOT_OWNER",
          },
        });
      }

      req.resource = resource;
      next();
    } catch (error) {
      next(error);
    }
  };
};

// ═══════════════════════════════════════════
// Usage Examples
// ═══════════════════════════════════════════

// Only admin can access
router.delete(
  "/users/:id",
  authenticateToken,
  requireRole(ROLES.ADMIN, ROLES.SUPER_ADMIN),
  async (req, res) => {
    await deleteUser(req.params.id);
    res.status(204).send();
  }
);

// Permission-based
router.post(
  "/posts",
  authenticateToken,
  requirePermission("post:create"),
  async (req, res) => {
    const post = await createPost(req.user.id, req.body);
    res.status(201).json({ data: post });
  }
);

// Resource ownership
router.put(
  "/posts/:id",
  authenticateToken,
  requireOwnership("post"),
  async (req, res) => {
    const post = await updatePost(req.params.id, req.body);
    res.json({ data: post });
  }
);
```

> **💡 Pro Tip:** Use permission-based authorization for flexibility. Roles can have different permissions in different environments!

---

<div align="center">

## 📧 Email Verification

</div>

### Email Verification Flow 📬

```javascript
// ═══════════════════════════════════════════
// Send Verification Email
// ═══════════════════════════════════════════

import crypto from "crypto";
import nodemailer from "nodemailer";

const generateVerificationToken = () => {
  return crypto.randomBytes(32).toString("hex");
};

router.post("/send-verification", authenticateToken, async (req, res, next) => {
  try {
    const user = await db.user.findUnique({
      where: { id: req.user.id },
    });

    if (user.emailVerified) {
      return res.status(400).json({
        success: false,
        error: {
          message: "Email already verified",
          code: "ALREADY_VERIFIED",
        },
      });
    }

    // Generate token
    const token = generateVerificationToken();
    const expiresAt = new Date(Date.now() + 24 * 60 * 60 * 1000); // 24 hours

    // Store token
    await db.verificationToken.create({
      data: {
        token,
        userId: user.id,
        type: "email_verification",
        expiresAt,
      },
    });

    // Send email
    const verificationUrl = `${process.env.CLIENT_URL}/verify-email?token=${token}`;

    await sendEmail({
      to: user.email,
      subject: "Verify your email",
      html: `
        <h1>Verify your email address</h1>
        <p>Click the link below to verify your email:</p>
        <a href="${verificationUrl}">Verify Email</a>
        <p>This link expires in 24 hours.</p>
      `,
    });

    res.json({
      success: true,
      message: "Verification email sent",
    });
  } catch (error) {
    next(error);
  }
});

// ═══════════════════════════════════════════
// Verify Email
// ═══════════════════════════════════════════

router.post("/verify-email", async (req, res, next) => {
  try {
    const { token } = req.body;

    // Find token
    const verificationToken = await db.verificationToken.findFirst({
      where: {
        token,
        type: "email_verification",
        expiresAt: { gt: new Date() },
        used: false,
      },
      include: { user: true },
    });

    if (!verificationToken) {
      return res.status(400).json({
        success: false,
        error: {
          message: "Invalid or expired token",
          code: "INVALID_TOKEN",
        },
      });
    }

    // Mark email as verified
    await db.user.update({
      where: { id: verificationToken.userId },
      data: { emailVerified: true },
    });

    // Mark token as used
    await db.verificationToken.update({
      where: { id: verificationToken.id },
      data: { used: true },
    });

    res.json({
      success: true,
      message: "Email verified successfully",
    });
  } catch (error) {
    next(error);
  }
});
```

---

<div align="center">

## 🔑 Password Reset

</div>

### Password Reset Flow 🔄

```javascript
// ═══════════════════════════════════════════
// Request Password Reset
// ═══════════════════════════════════════════

router.post("/forgot-password", async (req, res, next) => {
  try {
    const { email } = req.body;

    const user = await db.user.findUnique({ where: { email } });

    // Don't reveal if email exists (security)
    if (!user) {
      return res.json({
        success: true,
        message: "If email exists, reset link will be sent",
      });
    }

    // Generate reset token
    const token = crypto.randomBytes(32).toString("hex");
    const expiresAt = new Date(Date.now() + 60 * 60 * 1000); // 1 hour

    // Store token
    await db.verificationToken.create({
      data: {
        token,
        userId: user.id,
        type: "password_reset",
        expiresAt,
      },
    });

    // Send email
    const resetUrl = `${process.env.CLIENT_URL}/reset-password?token=${token}`;

    await sendEmail({
      to: user.email,
      subject: "Reset your password",
      html: `
        <h1>Reset your password</h1>
        <p>Click the link below to reset your password:</p>
        <a href="${resetUrl}">Reset Password</a>
        <p>This link expires in 1 hour.</p>
        <p>If you didn't request this, please ignore this email.</p>
      `,
    });

    res.json({
      success: true,
      message: "If email exists, reset link will be sent",
    });
  } catch (error) {
    next(error);
  }
});

// ═══════════════════════════════════════════
// Reset Password
// ═══════════════════════════════════════════

router.post("/reset-password", async (req, res, next) => {
  try {
    const { token, password } = req.body;

    // Find token
    const resetToken = await db.verificationToken.findFirst({
      where: {
        token,
        type: "password_reset",
        expiresAt: { gt: new Date() },
        used: false,
      },
      include: { user: true },
    });

    if (!resetToken) {
      return res.status(400).json({
        success: false,
        error: {
          message: "Invalid or expired token",
          code: "INVALID_TOKEN",
        },
      });
    }

    // Hash new password
    const hashedPassword = await hashPassword(password);

    // Update password and increment token version
    await db.user.update({
      where: { id: resetToken.userId },
      data: {
        password: hashedPassword,
        tokenVersion: { increment: 1 }, // Invalidate all tokens
      },
    });

    // Mark token as used
    await db.verificationToken.update({
      where: { id: resetToken.id },
      data: { used: true },
    });

    // Delete all refresh tokens for this user
    await db.refreshToken.deleteMany({
      where: { userId: resetToken.userId },
    });

    res.json({
      success: true,
      message: "Password reset successfully",
    });
  } catch (error) {
    next(error);
  }
});
```

---

<div align="center">

## 💡 Best Practices

</div>

### Authentication Security Checklist ✅

```javascript
// ═══════════════════════════════════════════
// Password Security
// ═══════════════════════════════════════════

/*
✅ Use bcrypt with 12+ rounds
✅ Enforce strong passwords (min 8 chars, uppercase, lowercase, number, special)
✅ Never store passwords in plain text
✅ Never log passwords
✅ Implement password history (prevent reuse)
✅ Add password strength meter
*/

// ═══════════════════════════════════════════
// Token Security
// ═══════════════════════════════════════════

/*
✅ Use short-lived access tokens (15 minutes)
✅ Use long-lived refresh tokens (7 days)
✅ Store refresh tokens in database
✅ Implement token rotation
✅ Add token versioning for invalidation
✅ Use httpOnly cookies for web
✅ Validate token expiry
✅ Sign tokens with strong secret (256+ bits)
*/

// ═══════════════════════════════════════════
// Session Security
// ═══════════════════════════════════════════

/*
✅ Use secure session storage (Redis)
✅ Set httpOnly, secure, sameSite cookies
✅ Regenerate session ID after login
✅ Implement session timeout
✅ Limit concurrent sessions
✅ Store session metadata (IP, user agent)
*/

// ═══════════════════════════════════════════
// General Security
// ═══════════════════════════════════════════

/*
✅ Implement rate limiting
✅ Use HTTPS everywhere
✅ Validate all inputs
✅ Sanitize user data
✅ Implement CSRF protection
✅ Use security headers (Helmet)
✅ Log authentication events
✅ Monitor for suspicious activity
✅ Implement account lockout after failed attempts
✅ Use 2FA for sensitive operations
*/

// Rate limiting example
import rateLimit from "express-rate-limit";

const loginLimiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 5, // 5 attempts
  message: "Too many login attempts, please try again later",
  standardHeaders: true,
  legacyHeaders: false,
});

router.post("/login", loginLimiter, loginHandler);

// Account lockout
const MAX_FAILED_ATTEMPTS = 5;
const LOCKOUT_DURATION = 30 * 60 * 1000; // 30 minutes

async function checkAccountLockout(userId) {
  const user = await db.user.findUnique({ where: { id: userId } });

  if (user.lockedUntil && user.lockedUntil > new Date()) {
    throw new Error("Account is locked");
  }

  return user;
}

async function recordFailedAttempt(userId) {
  const user = await db.user.findUnique({ where: { id: userId } });

  const failedAttempts = user.failedLoginAttempts + 1;

  if (failedAttempts >= MAX_FAILED_ATTEMPTS) {
    await db.user.update({
      where: { id: userId },
      data: {
        failedLoginAttempts: failedAttempts,
        lockedUntil: new Date(Date.now() + LOCKOUT_DURATION),
      },
    });
    throw new Error("Account locked due to too many failed attempts");
  }

  await db.user.update({
    where: { id: userId },
    data: { failedLoginAttempts: failedAttempts },
  });
}

async function resetFailedAttempts(userId) {
  await db.user.update({
    where: { id: userId },
    data: {
      failedLoginAttempts: 0,
      lockedUntil: null,
    },
  });
}
```

---

<div align="center">

**Built with 🔐 by MrDib, for Secure Applications**

_"Security is not a feature, it's a requirement!"_

**Happy Securing!** 🛡️

**If you found this helpful, give it a ⭐ star and share with fellow developers!**

</div>

---

### Contributing 🤝

Found better security practices? Want to add examples? Contributions are welcome!

1. Fork the repository
2. Add your security examples
3. Update best practices
4. Submit a pull request

---

### License 📄

This guide is open source and available under the MIT License.

---

<div align="center">

**Stay secure. Keep learning. Protect your users!** 💪✨

🔐 **#Authentication** 🔐 **#DevResourceVault** 🔐 **#MrDib** 🔐

### Remember

> _"Never trust, always verify"_

> _"Security is a process, not a product"_

> _"Defense in depth - multiple layers of security"_

> _"Fail securely - never expose sensitive info in errors"_

> _"Keep secrets secret - never commit credentials"_

</div>

---

<div align="center">

**Now go forth and build secure applications!** 🌟🔐

</div>
