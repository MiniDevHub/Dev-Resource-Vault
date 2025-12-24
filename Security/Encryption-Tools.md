<div align="center">

# 🔐 Encryption Tools - Complete Security Guide

![Encryption](https://img.shields.io/badge/Encryption-Tools-blue?style=for-the-badge&logo=letsencrypt)
![Security](https://img.shields.io/badge/Security-First-red?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-All_Levels-green?style=for-the-badge)

### _Because data protection is non-negotiable_ 🛡️

**Unencrypted data = Exposed data** 🔓

</div>

---

## 📚 Table of Contents

- [🎯 Encryption Fundamentals](#-encryption-fundamentals)
- [🔑 Symmetric Encryption](#-symmetric-encryption)
- [🔐 Asymmetric Encryption](#-asymmetric-encryption)
- [#️⃣ Hashing & Integrity](#️⃣-hashing--integrity)
- [🔒 TLS/SSL](#-tlsssl)
- [💬 End-to-End Encryption](#-end-to-end-encryption)
- [🗝️ Key Management](#️-key-management)
- [📧 Email Encryption (PGP/GPG)](#-email-encryption-pgpgpg)
- [💾 Disk Encryption](#-disk-encryption)
- [📡 Network Encryption](#-network-encryption)
- [🛠️ Encryption Libraries](#️-encryption-libraries)
- [✅ Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Encryption Fundamentals

</div>

### Understanding Encryption 🔐

```bash
# ═══════════════════════════════════════════
# WHAT IS ENCRYPTION?
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ENCRYPTION BASICS                        ║
╚════════════════════════════════════════════════════════════╝

Definition:
─────────────────────────────────────────────────────────────
Encryption = Converting readable data (plaintext) into
             unreadable format (ciphertext)

Purpose:
─────────────────────────────────────────────────────────────
• Confidentiality: Keep data secret
• Integrity: Detect tampering
• Authentication: Verify identity
• Non-repudiation: Prove authorship

The Flow:
─────────────────────────────────────────────────────────────
Plaintext → [Encryption with Key] → Ciphertext
              "Hello World"              "x8j#Km2@pL"

Ciphertext → [Decryption with Key] → Plaintext
              "x8j#Km2@pL"              "Hello World"

# ═══════════════════════════════════════════
# ENCRYPTION vs ENCODING vs HASHING
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   KEY DIFFERENCES                          ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Aspect           | Encoding             | Encryption        | Hashing          |
| ---------------- | -------------------- | ----------------- | ---------------- |
| **Purpose**      | Transform format     | Secure data       | Verify integrity |
| **Reversible**   | ✅ Yes (no key)      | ✅ Yes (with key) | ❌ No (one-way)  |
| **Security**     | ❌ None              | ✅ High           | ✅ High          |
| **Key Required** | No                   | Yes               | No               |
| **Output Size**  | Variable             | Variable          | Fixed            |
| **Use Case**     | Data transmission    | Data protection   | Password storage |
| **Examples**     | Base64, URL encoding | AES, RSA          | SHA-256, bcrypt  |

</div>

```bash
# ═══════════════════════════════════════════
# EXAMPLES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ENCODING                                 ║
╚════════════════════════════════════════════════════════════╝

Base64 Encoding:
─────────────────────────────────────────────────────────────
// Encode
const text = "Hello World";
const encoded = Buffer.from(text).toString('base64');
// "SGVsbG8gV29ybGQ="

// Decode
const decoded = Buffer.from(encoded, 'base64').toString();
// "Hello World"

⚠️ NOT SECURE - Anyone can decode!
Use: Binary data in text format (emails, JSON)

╔════════════════════════════════════════════════════════════╗
║                   ENCRYPTION                               ║
╚════════════════════════════════════════════════════════════╝

AES Encryption:
─────────────────────────────────────────────────────────────
const crypto = require('crypto');

// Encrypt
const key = crypto.randomBytes(32);
const iv = crypto.randomBytes(16);
const cipher = crypto.createCipheriv('aes-256-gcm', key, iv);

let encrypted = cipher.update('Hello World', 'utf8', 'hex');
encrypted += cipher.final('hex');
const authTag = cipher.getAuthTag();

// Result: Ciphertext (useless without key)

// Decrypt (requires same key!)
const decipher = crypto.createDecipheriv('aes-256-gcm', key, iv);
decipher.setAuthTag(authTag);

let decrypted = decipher.update(encrypted, 'hex', 'utf8');
decrypted += decipher.final('utf8');
// "Hello World"

✅ SECURE - Requires key to decrypt
Use: Protecting sensitive data

╔════════════════════════════════════════════════════════════╗
║                   HASHING                                  ║
╚════════════════════════════════════════════════════════════╝

SHA-256 Hash:
─────────────────────────────────────────────────────────────
const crypto = require('crypto');

const hash = crypto.createHash('sha256')
  .update('Hello World')
  .digest('hex');

// "a591a6d40bf420404a011733cfb7b190d62c65bf0bcda32b57b277d9ad9f146e"

// Same input = Same output (always)
const hash2 = crypto.createHash('sha256')
  .update('Hello World')
  .digest('hex');

console.log(hash === hash2); // true

// Different input = Different output
const hash3 = crypto.createHash('sha256')
  .update('Hello World!')  // Added !
  .digest('hex');

console.log(hash === hash3); // false

❌ CANNOT be reversed (one-way function)
✅ SECURE - Can verify but not decode
Use: Passwords, data integrity verification

# ═══════════════════════════════════════════
# ENCRYPTION TYPES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SYMMETRIC vs ASYMMETRIC                  ║
╚════════════════════════════════════════════════════════════╝

SYMMETRIC (Same Key)
─────────────────────────────────────────────────────────────
         [Encryption Key]
                ↓
    Plaintext → [Encrypt] → Ciphertext
                               ↓
         [Same Encryption Key]
                ↓
    Ciphertext → [Decrypt] → Plaintext

Characteristics:
• One key for both encryption & decryption
• Fast (good for large data)
• Key distribution problem (how to share key securely?)

Algorithms: AES, ChaCha20, DES (deprecated)

ASYMMETRIC (Key Pair)
─────────────────────────────────────────────────────────────
         [Public Key]
              ↓
  Plaintext → [Encrypt] → Ciphertext
                             ↓
          [Private Key]
              ↓
  Ciphertext → [Decrypt] → Plaintext

Characteristics:
• Two keys: Public (encrypt) & Private (decrypt)
• Slow (good for small data)
• No key distribution problem (share public key freely)

Algorithms: RSA, ECC, ElGamal

Hybrid Approach (Best of Both):
─────────────────────────────────────────────────────────────
1. Generate random symmetric key
2. Encrypt data with symmetric key (fast)
3. Encrypt symmetric key with public key (secure sharing)
4. Send: encrypted data + encrypted symmetric key

Recipient:
1. Decrypt symmetric key with private key
2. Decrypt data with symmetric key

This is how TLS/SSL works! 🔒

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔑 Symmetric Encryption

</div>

### AES (Advanced Encryption Standard) 🔐

```bash
# ═══════════════════════════════════════════
# AES ENCRYPTION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   AES - THE GOLD STANDARD                  ║
╚════════════════════════════════════════════════════════════╝

What is AES:
─────────────────────────────────────────────────────────────
• Advanced Encryption Standard
• Adopted by US government (2001)
• Used worldwide
• Considered unbreakable with current technology

Key Sizes:
─────────────────────────────────────────────────────────────
• AES-128: 128-bit key (fast, secure)
• AES-192: 192-bit key (more secure)
• AES-256: 256-bit key (most secure)

Recommendation: AES-256 for sensitive data

Modes of Operation:
─────────────────────────────────────────────────────────────
• CBC (Cipher Block Chaining): Traditional
• GCM (Galois/Counter Mode): ✅ RECOMMENDED (authenticated)
• CTR (Counter): Good for parallel processing
• ECB (Electronic Codebook): ❌ NEVER USE (insecure)

# ═══════════════════════════════════════════
# AES-256-GCM IMPLEMENTATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   COMPLETE AES IMPLEMENTATION              ║
╚════════════════════════════════════════════════════════════╝

Node.js Implementation:
─────────────────────────────────────────────────────────────
const crypto = require('crypto');

class AESEncryption {
  constructor() {
    this.algorithm = 'aes-256-gcm';
    this.keyLength = 32; // 256 bits
    this.ivLength = 16;  // 128 bits
  }

  // Generate a secure encryption key
  generateKey() {
    return crypto.randomBytes(this.keyLength);
  }

  // Encrypt data
  encrypt(plaintext, key) {
    // Validate key length
    if (key.length !== this.keyLength) {
      throw new Error(`Key must be ${this.keyLength} bytes`);
    }

    // Generate random IV (Initialization Vector)
    const iv = crypto.randomBytes(this.ivLength);

    // Create cipher
    const cipher = crypto.createCipheriv(this.algorithm, key, iv);

    // Encrypt
    let encrypted = cipher.update(plaintext, 'utf8', 'hex');
    encrypted += cipher.final('hex');

    // Get authentication tag (GCM mode)
    const authTag = cipher.getAuthTag();

    // Return encrypted data with IV and auth tag
    return {
      encrypted,
      iv: iv.toString('hex'),
      authTag: authTag.toString('hex')
    };
  }

  // Decrypt data
  decrypt(encryptedData, key) {
    // Validate key length
    if (key.length !== this.keyLength) {
      throw new Error(`Key must be ${this.keyLength} bytes`);
    }

    const { encrypted, iv, authTag } = encryptedData;

    // Create decipher
    const decipher = crypto.createDecipheriv(
      this.algorithm,
      key,
      Buffer.from(iv, 'hex')
    );

    // Set authentication tag
    decipher.setAuthTag(Buffer.from(authTag, 'hex'));

    // Decrypt
    let decrypted = decipher.update(encrypted, 'hex', 'utf8');
    decrypted += decipher.final('utf8');

    return decrypted;
  }

  // Encrypt and encode as single string
  encryptToString(plaintext, key) {
    const encrypted = this.encrypt(plaintext, key);

    // Combine into single string: iv:authTag:encrypted
    return `${encrypted.iv}:${encrypted.authTag}:${encrypted.encrypted}`;
  }

  // Decrypt from string
  decryptFromString(encryptedString, key) {
    const [iv, authTag, encrypted] = encryptedString.split(':');

    return this.decrypt({ encrypted, iv, authTag }, key);
  }
}

// Usage Example:
─────────────────────────────────────────────────────────────
const aes = new AESEncryption();

// Generate key (store securely!)
const key = aes.generateKey();
console.log('Key:', key.toString('hex'));

// Encrypt
const plaintext = 'This is secret data';
const encrypted = aes.encrypt(plaintext, key);
console.log('Encrypted:', encrypted);

// Decrypt
const decrypted = aes.decrypt(encrypted, key);
console.log('Decrypted:', decrypted); // "This is secret data"

// Encrypt to single string (easier storage)
const encryptedString = aes.encryptToString(plaintext, key);
console.log('Encrypted String:', encryptedString);

const decryptedFromString = aes.decryptFromString(encryptedString, key);
console.log('Decrypted:', decryptedFromString);

╔════════════════════════════════════════════════════════════╗
║                   PRACTICAL USE CASES                      ║
╚════════════════════════════════════════════════════════════╝

1. Encrypt Database Fields
─────────────────────────────────────────────────────────────
// User model with encrypted SSN
const userSchema = new mongoose.Schema({
  name: String,
  email: String,
  ssnEncrypted: String  // Encrypted SSN
});

// Save with encryption
async function createUser(name, email, ssn) {
  const key = Buffer.from(process.env.ENCRYPTION_KEY, 'hex');
  const encryptedSSN = aes.encryptToString(ssn, key);

  return await User.create({
    name,
    email,
    ssnEncrypted: encryptedSSN
  });
}

// Retrieve with decryption
async function getUserSSN(userId) {
  const user = await User.findById(userId);
  const key = Buffer.from(process.env.ENCRYPTION_KEY, 'hex');

  return aes.decryptFromString(user.ssnEncrypted, key);
}

2. Encrypt Files
─────────────────────────────────────────────────────────────
const fs = require('fs');

function encryptFile(inputPath, outputPath, key) {
  const plaintext = fs.readFileSync(inputPath, 'utf8');
  const encrypted = aes.encryptToString(plaintext, key);
  fs.writeFileSync(outputPath, encrypted);
}

function decryptFile(inputPath, outputPath, key) {
  const encrypted = fs.readFileSync(inputPath, 'utf8');
  const decrypted = aes.decryptFromString(encrypted, key);
  fs.writeFileSync(outputPath, decrypted);
}

// Usage
const key = aes.generateKey();
encryptFile('secret.txt', 'secret.enc', key);
decryptFile('secret.enc', 'secret-decrypted.txt', key);

3. Encrypt API Payloads
─────────────────────────────────────────────────────────────
// Encrypt sensitive data before sending
app.post('/api/sensitive', async (req, res) => {
  const sensitiveData = {
    ssn: '123-45-6789',
    creditCard: '4111-1111-1111-1111',
    password: 'supersecret'
  };

  // Encrypt entire payload
  const key = Buffer.from(process.env.API_ENCRYPTION_KEY, 'hex');
  const encrypted = aes.encryptToString(
    JSON.stringify(sensitiveData),
    key
  );

  // Send encrypted
  await externalAPI.post('/endpoint', { data: encrypted });
});

// Decrypt on receive
app.post('/api/receive', (req, res) => {
  const key = Buffer.from(process.env.API_ENCRYPTION_KEY, 'hex');
  const decrypted = aes.decryptFromString(req.body.data, key);
  const data = JSON.parse(decrypted);

  // Use decrypted data
  console.log(data);
});

# ═══════════════════════════════════════════
# CHACHA20-POLY1305
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   MODERN ALTERNATIVE TO AES                ║
╚════════════════════════════════════════════════════════════╝

ChaCha20-Poly1305:
─────────────────────────────────────────────────────────────
• Modern cipher by Daniel J. Bernstein
• Faster than AES on devices without hardware acceleration
• Used by Google, Cloudflare, Signal
• Recommended for mobile devices

Implementation:
─────────────────────────────────────────────────────────────
const crypto = require('crypto');

function encryptChaCha20(plaintext, key) {
  const iv = crypto.randomBytes(12); // ChaCha20 uses 12-byte nonce

  const cipher = crypto.createCipheriv('chacha20-poly1305', key, iv, {
    authTagLength: 16
  });

  let encrypted = cipher.update(plaintext, 'utf8', 'hex');
  encrypted += cipher.final('hex');

  const authTag = cipher.getAuthTag();

  return {
    encrypted,
    iv: iv.toString('hex'),
    authTag: authTag.toString('hex')
  };
}

function decryptChaCha20(encryptedData, key) {
  const { encrypted, iv, authTag } = encryptedData;

  const decipher = crypto.createDecipheriv(
    'chacha20-poly1305',
    key,
    Buffer.from(iv, 'hex'),
    { authTagLength: 16 }
  );

  decipher.setAuthTag(Buffer.from(authTag, 'hex'));

  let decrypted = decipher.update(encrypted, 'hex', 'utf8');
  decrypted += decipher.final('utf8');

  return decrypted;
}

When to use ChaCha20 vs AES:
─────────────────────────────────────────────────────────────
Use AES:
✅ Server-side encryption
✅ Hardware with AES-NI support
✅ Enterprise compliance requirements

Use ChaCha20:
✅ Mobile devices
✅ IoT devices
✅ Systems without hardware AES
✅ Need constant-time implementation

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔐 Asymmetric Encryption

</div>

### RSA & Elliptic Curve Cryptography 🔑

```bash
# ═══════════════════════════════════════════
# RSA ENCRYPTION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   RSA PUBLIC KEY CRYPTOGRAPHY              ║
╚════════════════════════════════════════════════════════════╝

What is RSA:
─────────────────────────────────────────────────────────────
• Rivest-Shamir-Adleman (1977)
• Most widely used asymmetric algorithm
• Based on factoring large prime numbers
• Used for: Digital signatures, key exchange, email encryption

Key Sizes:
─────────────────────────────────────────────────────────────
• RSA-1024: ❌ Deprecated (insecure)
• RSA-2048: ✅ Standard (secure)
• RSA-3072: ✅ High security
• RSA-4096: ✅ Maximum security (slower)

Recommendation: RSA-2048 minimum, RSA-4096 for high security

How it works:
─────────────────────────────────────────────────────────────
Public Key:  Can be shared with anyone
Private Key: Must be kept secret

Encrypt with Public Key  → Only Private Key can decrypt
Sign with Private Key    → Only Public Key can verify

# ═══════════════════════════════════════════
# RSA IMPLEMENTATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   COMPLETE RSA SETUP                       ║
╚════════════════════════════════════════════════════════════╝

Generate RSA Key Pair:
─────────────────────────────────────────────────────────────
const crypto = require('crypto');

// Generate key pair
const { publicKey, privateKey } = crypto.generateKeyPairSync('rsa', {
  modulusLength: 4096,  // Key size in bits
  publicKeyEncoding: {
    type: 'spki',
    format: 'pem'
  },
  privateKeyEncoding: {
    type: 'pkcs8',
    format: 'pem',
    cipher: 'aes-256-cbc',
    passphrase: 'your-secure-passphrase'  // Encrypt private key
  }
});

console.log('Public Key:\n', publicKey);
console.log('Private Key:\n', privateKey);

// Save to files
const fs = require('fs');
fs.writeFileSync('public-key.pem', publicKey);
fs.writeFileSync('private-key.pem', privateKey);

Encrypt with RSA:
─────────────────────────────────────────────────────────────
class RSAEncryption {
  // Encrypt with public key
  encrypt(plaintext, publicKey) {
    const buffer = Buffer.from(plaintext, 'utf8');

    const encrypted = crypto.publicEncrypt(
      {
        key: publicKey,
        padding: crypto.constants.RSA_PKCS1_OAEP_PADDING,
        oaepHash: 'sha256'
      },
      buffer
    );

    return encrypted.toString('base64');
  }

  // Decrypt with private key
  decrypt(encryptedData, privateKey, passphrase) {
    const buffer = Buffer.from(encryptedData, 'base64');

    const decrypted = crypto.privateDecrypt(
      {
        key: privateKey,
        passphrase: passphrase,
        padding: crypto.constants.RSA_PKCS1_OAEP_PADDING,
        oaepHash: 'sha256'
      },
      buffer
    );

    return decrypted.toString('utf8');
  }

  // Sign data with private key
  sign(data, privateKey, passphrase) {
    const sign = crypto.createSign('SHA256');
    sign.update(data);
    sign.end();

    const signature = sign.sign({
      key: privateKey,
      passphrase: passphrase
    });

    return signature.toString('base64');
  }

  // Verify signature with public key
  verify(data, signature, publicKey) {
    const verify = crypto.createVerify('SHA256');
    verify.update(data);
    verify.end();

    return verify.verify(publicKey, Buffer.from(signature, 'base64'));
  }
}

Usage Example:
─────────────────────────────────────────────────────────────
const rsa = new RSAEncryption();

// Read keys
const publicKey = fs.readFileSync('public-key.pem', 'utf8');
const privateKey = fs.readFileSync('private-key.pem', 'utf8');
const passphrase = 'your-secure-passphrase';

// Encrypt (with public key)
const plaintext = 'Secret message';
const encrypted = rsa.encrypt(plaintext, publicKey);
console.log('Encrypted:', encrypted);

// Decrypt (with private key)
const decrypted = rsa.decrypt(encrypted, privateKey, passphrase);
console.log('Decrypted:', decrypted); // "Secret message"

// Sign data (prove authenticity)
const data = 'Important document';
const signature = rsa.sign(data, privateKey, passphrase);
console.log('Signature:', signature);

// Verify signature
const isValid = rsa.verify(data, signature, publicKey);
console.log('Valid signature:', isValid); // true

╔════════════════════════════════════════════════════════════╗
║                   HYBRID ENCRYPTION (RSA + AES)            ║
╚════════════════════════════════════════════════════════════╝

Problem: RSA is slow for large data
Solution: Use RSA to encrypt AES key, use AES to encrypt data

Implementation:
─────────────────────────────────────────────────────────────
class HybridEncryption {
  constructor() {
    this.aes = new AESEncryption();
    this.rsa = new RSAEncryption();
  }

  // Encrypt large data with hybrid approach
  encrypt(plaintext, recipientPublicKey) {
    // 1. Generate random AES key
    const aesKey = this.aes.generateKey();

    // 2. Encrypt data with AES (fast)
    const encryptedData = this.aes.encryptToString(plaintext, aesKey);

    // 3. Encrypt AES key with RSA (secure key exchange)
    const encryptedKey = this.rsa.encrypt(
      aesKey.toString('hex'),
      recipientPublicKey
    );

    // 4. Return both
    return {
      data: encryptedData,
      key: encryptedKey
    };
  }

  // Decrypt hybrid encrypted data
  decrypt(encrypted, privateKey, passphrase) {
    // 1. Decrypt AES key with RSA
    const aesKeyHex = this.rsa.decrypt(
      encrypted.key,
      privateKey,
      passphrase
    );
    const aesKey = Buffer.from(aesKeyHex, 'hex');

    // 2. Decrypt data with AES
    const plaintext = this.aes.decryptFromString(encrypted.data, aesKey);

    return plaintext;
  }
}

// Usage
const hybrid = new HybridEncryption();

// Encrypt large data
const largeData = 'A'.repeat(1000000); // 1MB of data
const encrypted = hybrid.encrypt(largeData, publicKey);

// Decrypt
const decrypted = hybrid.decrypt(encrypted, privateKey, passphrase);

console.log('Success:', decrypted === largeData); // true

Benefits:
─────────────────────────────────────────────────────────────
✅ Fast (AES for bulk data)
✅ Secure (RSA for key exchange)
✅ No need to share AES key separately
✅ This is how HTTPS works!

# ═══════════════════════════════════════════
# ELLIPTIC CURVE CRYPTOGRAPHY (ECC)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ECC - SMALLER, FASTER                    ║
╚════════════════════════════════════════════════════════════╝

What is ECC:
─────────────────────────────────────────────────────────────
• Modern alternative to RSA
• Smaller keys, same security
• Faster computation
• Better for mobile/IoT

Key Size Comparison:
─────────────────────────────────────────────────────────────
RSA-2048  ≈ ECC-224  (same security)
RSA-3072  ≈ ECC-256  (same security)
RSA-7680  ≈ ECC-384  (same security)
RSA-15360 ≈ ECC-521  (same security)

Recommended Curves:
─────────────────────────────────────────────────────────────
• P-256 (secp256r1): Standard, widely supported
• P-384 (secp384r1): High security
• P-521 (secp521r1): Maximum security
• Curve25519: Modern, fast (used by Signal, WhatsApp)

Implementation:
─────────────────────────────────────────────────────────────
// Generate ECC key pair
const { publicKey, privateKey } = crypto.generateKeyPairSync('ec', {
  namedCurve: 'secp256k1',  // Bitcoin uses this curve
  publicKeyEncoding: {
    type: 'spki',
    format: 'pem'
  },
  privateKeyEncoding: {
    type: 'pkcs8',
    format: 'pem'
  }
});

// ECDH (Elliptic Curve Diffie-Hellman) - Shared Secret
const alice = crypto.createECDH('secp256k1');
alice.generateKeys();

const bob = crypto.createECDH('secp256k1');
bob.generateKeys();

// Both derive same shared secret
const aliceSecret = alice.computeSecret(bob.getPublicKey());
const bobSecret = bob.computeSecret(alice.getPublicKey());

console.log('Shared secret match:', aliceSecret.equals(bobSecret)); // true

// Use shared secret as AES key
const aesKey = crypto.createHash('sha256').update(aliceSecret).digest();

// Now both can encrypt/decrypt with same key!

Use Cases:
─────────────────────────────────────────────────────────────
✅ TLS/SSL (modern websites use ECC)
✅ Cryptocurrency (Bitcoin, Ethereum)
✅ Mobile apps (smaller keys = faster)
✅ IoT devices (less computational power needed)
✅ End-to-end encryption (Signal, WhatsApp)

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## #️⃣ Hashing & Integrity

</div>

### Cryptographic Hash Functions 🔒

```bash
# ═══════════════════════════════════════════
# HASHING FUNDAMENTALS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHAT IS HASHING?                         ║
╚════════════════════════════════════════════════════════════╝

Definition:
─────────────────────────────────────────────────────────────
Hashing = One-way transformation of data to fixed-size output

Properties:
─────────────────────────────────────────────────────────────
1. Deterministic: Same input → Same output (always)
2. Fast: Quick to compute
3. One-way: Cannot reverse (infeasible to find input from hash)
4. Avalanche Effect: Small change in input → Completely different hash
5. Collision Resistant: Hard to find two inputs with same hash

Example:
─────────────────────────────────────────────────────────────
Input:  "Hello"
SHA-256: "185f8db32271fe25f561a6fc938b2e264306ec304eda518007d1764826381969"

Input:  "Hello!"  (added !)
SHA-256: "334d016f755cd6dc58c53a86e183882f8ec14f52fb05345887c8a5edd42c87b7"

Completely different!

Use Cases:
─────────────────────────────────────────────────────────────
• Password storage (with salting)
• Data integrity verification
• Digital signatures
• Blockchain
• File deduplication
• Checksum verification
```

<div align="center">

| Algorithm   | Output Size | Security  | Speed   | Use Case                |
| ----------- | ----------- | --------- | ------- | ----------------------- |
| **MD5**     | 128-bit     | ❌ Broken | Fast    | ❌ Don't use            |
| **SHA-1**   | 160-bit     | ❌ Broken | Fast    | ❌ Don't use            |
| **SHA-256** | 256-bit     | ✅ Secure | Fast    | ✅ General purpose      |
| **SHA-512** | 512-bit     | ✅ Secure | Fast    | ✅ High security        |
| **SHA-3**   | Variable    | ✅ Secure | Medium  | ✅ Modern standard      |
| **BLAKE2**  | Variable    | ✅ Secure | Fastest | ✅ Performance critical |
| **bcrypt**  | 184-bit     | ✅ Secure | Slow    | ✅ Password hashing     |
| **Argon2**  | Variable    | ✅ Secure | Slow    | ✅ Password hashing     |

</div>

```bash
# ═══════════════════════════════════════════
# HASHING IMPLEMENTATIONS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SHA-256 HASHING                          ║
╚════════════════════════════════════════════════════════════╝

Basic SHA-256:
─────────────────────────────────────────────────────────────
const crypto = require('crypto');

function hash(data) {
  return crypto.createHash('sha256')
    .update(data)
    .digest('hex');
}

console.log(hash('Hello World'));
// "a591a6d40bf420404a011733cfb7b190d62c65bf0bcda32b57b277d9ad9f146e"

File Hashing:
─────────────────────────────────────────────────────────────
const fs = require('fs');
const crypto = require('crypto');

function hashFile(filename) {
  return new Promise((resolve, reject) => {
    const hash = crypto.createHash('sha256');
    const stream = fs.createReadStream(filename);

    stream.on('data', (data) => hash.update(data));
    stream.on('end', () => resolve(hash.digest('hex')));
    stream.on('error', reject);
  });
}

// Usage
const fileHash = await hashFile('large-file.zip');
console.log('File hash:', fileHash);

// Verify file integrity
const expectedHash = '...';
if (fileHash === expectedHash) {
  console.log('✅ File integrity verified');
} else {
  console.log('❌ File has been tampered with!');
}

╔════════════════════════════════════════════════════════════╗
║                   HMAC (KEYED HASHING)                     ║
╚════════════════════════════════════════════════════════════╝

What is HMAC:
─────────────────────────────────────────────────────────────
Hash-based Message Authentication Code
• Hash + Secret Key
• Verifies both integrity AND authenticity
• Used in JWT, API signatures, webhooks

Implementation:
─────────────────────────────────────────────────────────────
function createHMAC(message, secret) {
  return crypto.createHmac('sha256', secret)
    .update(message)
    .digest('hex');
}

function verifyHMAC(message, signature, secret) {
  const expected = createHMAC(message, secret);
  return crypto.timingSafeEqual(
    Buffer.from(signature),
    Buffer.from(expected)
  );
}

// Usage
const secret = 'my-secret-key';
const message = 'Important data';

const signature = createHMAC(message, secret);
console.log('Signature:', signature);

// Verify
const isValid = verifyHMAC(message, signature, secret);
console.log('Valid:', isValid); // true

// Tampered message
const isValid2 = verifyHMAC('Tampered data', signature, secret);
console.log('Valid:', isValid2); // false

Use Cases:
─────────────────────────────────────────────────────────────
1. JWT Tokens
─────────────────────────────────────────────────────────────
// JWT = header.payload.signature
// signature = HMAC-SHA256(header + payload, secret)

2. Webhook Signatures
─────────────────────────────────────────────────────────────
// GitHub webhook verification
app.post('/webhook', (req, res) => {
  const signature = req.headers['x-hub-signature-256'];
  const payload = JSON.stringify(req.body);

  const expected = 'sha256=' + createHMAC(payload, process.env.WEBHOOK_SECRET);

  if (!crypto.timingSafeEqual(Buffer.from(signature), Buffer.from(expected))) {
    return res.status(401).send('Invalid signature');
  }

  // Process webhook
  res.send('OK');
});

3. API Request Signing
─────────────────────────────────────────────────────────────
// Sign API request
const timestamp = Date.now();
const data = JSON.stringify(requestBody);
const signaturePayload = `${timestamp}.${data}`;
const signature = createHMAC(signaturePayload, apiSecret);

axios.post('/api/endpoint', requestBody, {
  headers: {
    'X-Timestamp': timestamp,
    'X-Signature': signature
  }
});

// Verify on server
const timestamp = req.headers['x-timestamp'];
const signature = req.headers['x-signature'];
const data = JSON.stringify(req.body);
const payload = `${timestamp}.${data}`;

if (!verifyHMAC(payload, signature, apiSecret)) {
  return res.status(401).send('Invalid signature');
}

╔════════════════════════════════════════════════════════════╗
║                   PASSWORD HASHING                         ║
╚════════════════════════════════════════════════════════════╝

❌ NEVER use simple hashing for passwords!
─────────────────────────────────────────────────────────────
// ❌ DON'T DO THIS
const passwordHash = crypto.createHash('sha256')
  .update(password)
  .digest('hex');

// Why bad?
// • Too fast (easy to brute force)
// • No salt (rainbow table attacks)
// • Same password = same hash

✅ Use bcrypt or Argon2
─────────────────────────────────────────────────────────────
const bcrypt = require('bcrypt');

// Hash password
const saltRounds = 12;
const passwordHash = await bcrypt.hash(password, saltRounds);

// Verify password
const isValid = await bcrypt.compare(inputPassword, passwordHash);

// Why good?
// • Slow by design (prevents brute force)
// • Automatic salting
// • Adaptive (can increase rounds as hardware improves)

See [Web-Security.md](../Web-Security.md) for complete password hashing guide

╔════════════════════════════════════════════════════════════╗
║                   MERKLE TREES (BLOCKCHAIN)                ║
╚════════════════════════════════════════════════════════════╝

What is a Merkle Tree:
─────────────────────────────────────────────────────────────
Tree of hashes used to verify large data structures efficiently

Structure:
                    Root Hash
                   /         \
              Hash A         Hash B
             /     \        /     \
         Hash 1  Hash 2  Hash 3  Hash 4
            |       |       |       |
          Data1   Data2   Data3   Data4

Implementation:
─────────────────────────────────────────────────────────────
class MerkleTree {
  constructor(leaves) {
    this.leaves = leaves.map(l => this.hash(l));
    this.layers = [this.leaves];
    this.createTree();
  }

  hash(data) {
    return crypto.createHash('sha256').update(data).digest('hex');
  }

  createTree() {
    let currentLayer = this.leaves;

    while (currentLayer.length > 1) {
      const nextLayer = [];

      for (let i = 0; i < currentLayer.length; i += 2) {
        const left = currentLayer[i];
        const right = currentLayer[i + 1] || left; // Duplicate if odd
        const combined = this.hash(left + right);
        nextLayer.push(combined);
      }

      this.layers.push(nextLayer);
      currentLayer = nextLayer;
    }
  }

  getRoot() {
    return this.layers[this.layers.length - 1][0];
  }

  getProof(index) {
    let proof = [];
    let currentIndex = index;

    for (let i = 0; i < this.layers.length - 1; i++) {
      const layer = this.layers[i];
      const isRightNode = currentIndex % 2;
      const siblingIndex = isRightNode ? currentIndex - 1 : currentIndex + 1;

      if (siblingIndex < layer.length) {
        proof.push({
          hash: layer[siblingIndex],
          position: isRightNode ? 'left' : 'right'
        });
      }

      currentIndex = Math.floor(currentIndex / 2);
    }

    return proof;
  }

  verify(leaf, proof, root) {
    let hash = this.hash(leaf);

    for (const node of proof) {
      hash = node.position === 'left'
        ? this.hash(node.hash + hash)
        : this.hash(hash + node.hash);
    }

    return hash === root;
  }
}

// Usage
const data = ['transaction1', 'transaction2', 'transaction3', 'transaction4'];
const tree = new MerkleTree(data);

console.log('Root:', tree.getRoot());

// Verify transaction
const proof = tree.getProof(1); // Prove transaction2 is in tree
const isValid = tree.verify('transaction2', proof, tree.getRoot());
console.log('Valid:', isValid); // true

// Used in: Bitcoin, Ethereum, Git, IPFS

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔒 TLS/SSL

</div>

### Transport Layer Security 🌐

```bash
# ═══════════════════════════════════════════
# TLS/SSL FUNDAMENTALS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHAT IS TLS/SSL?                         ║
╚════════════════════════════════════════════════════════════╝

Definition:
─────────────────────────────────────────────────────────────
TLS (Transport Layer Security) = Protocol for secure communication

Purpose:
─────────────────────────────────────────────────────────────
• Encryption: Prevent eavesdropping
• Authentication: Verify server identity
• Integrity: Detect tampering

HTTPS = HTTP + TLS
─────────────────────────────────────────────────────────────
http://example.com   ❌ Unencrypted
https://example.com  ✅ Encrypted with TLS

TLS Versions:
─────────────────────────────────────────────────────────────
• SSL 2.0: ❌ Deprecated (1995)
• SSL 3.0: ❌ Deprecated (1996)
• TLS 1.0: ❌ Deprecated (1999)
• TLS 1.1: ❌ Deprecated (2006)
• TLS 1.2: ✅ Secure (2008)
• TLS 1.3: ✅ Modern (2018) - Faster, more secure

Use: TLS 1.2+ only!

# ═══════════════════════════════════════════
# TLS HANDSHAKE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   HOW TLS WORKS                            ║
╚════════════════════════════════════════════════════════════╝

TLS 1.2 Handshake (Simplified):
─────────────────────────────────────────────────────────────
Client                                        Server
  │                                              │
  │──────── ClientHello ──────────────────────→ │
  │  • TLS version                               │
  │  • Supported ciphers                         │
  │  • Random bytes                              │
  │                                              │
  │←─────── ServerHello ───────────────────────│
  │  • Chosen TLS version                        │
  │  • Chosen cipher                             │
  │  • Server certificate                        │
  │  • Random bytes                              │
  │                                              │
  │──────── ClientKeyExchange ─────────────────→│
  │  • Pre-master secret (encrypted with         │
  │    server's public key from certificate)     │
  │                                              │
  │←─────── Finished ──────────────────────────│
  │                                              │
  │──────── Finished ──────────────────────────→│
  │                                              │
  │═══════ Encrypted Communication ═══════════→│
  │                                              │

Both sides derive:
• Master Secret (from pre-master secret + random bytes)
• Session Keys (symmetric keys for AES encryption)

TLS 1.3 Handshake (Faster - 1-RTT):
─────────────────────────────────────────────────────────────
• Fewer round trips (faster)
• Forward secrecy required
• Removed weak algorithms
• Encrypted handshake

Result: ~40% faster than TLS 1.2

# ═══════════════════════════════════════════
# SSL/TLS CERTIFICATES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SSL CERTIFICATES                         ║
╚════════════════════════════════════════════════════════════╝

What is an SSL Certificate:
─────────────────────────────────────────────────────────────
Digital document that:
• Proves ownership of a domain
• Contains public key
• Signed by Certificate Authority (CA)
• Enables HTTPS

Certificate Contents:
─────────────────────────────────────────────────────────────
• Domain name (example.com)
• Organization details
• Public key
• Validity period (expiration date)
• Issuer (CA)
• Digital signature

Types of Certificates:
─────────────────────────────────────────────────────────────
1. Domain Validated (DV)
   • Cheapest/Free
   • Only verifies domain ownership
   • Quick issuance
   • Use: Personal sites, blogs
   • Provider: Let's Encrypt (free)

2. Organization Validated (OV)
   • Verifies organization
   • More trust
   • Manual verification
   • Use: Business websites

3. Extended Validation (EV)
   • Highest validation
   • Shows organization in address bar
   • Expensive
   • Use: Banks, e-commerce

4. Wildcard
   • Covers all subdomains
   • Example: *.example.com
   • Covers: app.example.com, api.example.com, etc.

5. Multi-Domain (SAN)
   • Multiple domains in one certificate
   • Example: example.com, example.net, example.org

# ═══════════════════════════════════════════
# LET'S ENCRYPT (FREE SSL)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   FREE SSL CERTIFICATES                    ║
╚════════════════════════════════════════════════════════════╝

Let's Encrypt:
─────────────────────────────────────────────────────────────
• Free SSL certificates
• Automated issuance and renewal
• Domain Validated (DV)
• Trusted by all browsers
• 90-day validity (auto-renew)

Website: https://letsencrypt.org

Setup with Certbot:
─────────────────────────────────────────────────────────────
# Install Certbot
# Ubuntu/Debian
sudo apt install certbot python3-certbot-nginx

# macOS
brew install certbot

# Get certificate (Nginx)
sudo certbot --nginx -d example.com -d www.example.com

# Get certificate (Apache)
sudo certbot --apache -d example.com

# Get certificate (standalone - no web server)
sudo certbot certonly --standalone -d example.com

# Manual verification (DNS)
sudo certbot certonly --manual --preferred-challenges dns -d example.com

# Auto-renewal (runs twice daily)
sudo certbot renew

# Test renewal
sudo certbot renew --dry-run

Nginx Configuration:
─────────────────────────────────────────────────────────────
# /etc/nginx/sites-available/example.com

server {
    listen 80;
    server_name example.com www.example.com;

    # Redirect HTTP to HTTPS
    return 301 https://$server_name$request_uri;
}

server {
    listen 443 ssl http2;
    server_name example.com www.example.com;

    # SSL certificate files (Certbot adds these)
    ssl_certificate /etc/letsencrypt/live/example.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;

    # SSL configuration
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers HIGH:!aNULL:!MD5;
    ssl_prefer_server_ciphers on;

    # HSTS
    add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;

    # OCSP Stapling
    ssl_stapling on;
    ssl_stapling_verify on;
    ssl_trusted_certificate /etc/letsencrypt/live/example.com/chain.pem;

    # Your application
    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}

Node.js HTTPS Server:
─────────────────────────────────────────────────────────────
const https = require('https');
const fs = require('fs');
const express = require('express');

const app = express();

// SSL certificate files
const options = {
  key: fs.readFileSync('/etc/letsencrypt/live/example.com/privkey.pem'),
  cert: fs.readFileSync('/etc/letsencrypt/live/example.com/fullchain.pem')
};

// Create HTTPS server
https.createServer(options, app).listen(443, () => {
  console.log('HTTPS Server running on port 443');
});

// Redirect HTTP to HTTPS
const http = require('http');
http.createServer((req, res) => {
  res.writeHead(301, { Location: `https://${req.headers.host}${req.url}` });
  res.end();
}).listen(80);

app.get('/', (req, res) => {
  res.send('Secure HTTPS connection! 🔒');
});

Docker with Let's Encrypt:
─────────────────────────────────────────────────────────────
# docker-compose.yml
version: '3'

services:
  nginx:
    image: nginx:alpine
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf
      - ./certbot/conf:/etc/letsencrypt
      - ./certbot/www:/var/www/certbot
    depends_on:
      - app

  certbot:
    image: certbot/certbot
    volumes:
      - ./certbot/conf:/etc/letsencrypt
      - ./certbot/www:/var/www/certbot
    entrypoint: "/bin/sh -c 'trap exit TERM; while :; do certbot renew; sleep 12h & wait $${!}; done;'"

  app:
    build: .
    expose:
      - "3000"

# Initial certificate
docker-compose run --rm certbot certonly --webroot \
  -w /var/www/certbot \
  -d example.com -d www.example.com \
  --email admin@example.com \
  --agree-tos \
  --no-eff-email

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 💬 End-to-End Encryption

</div>

### E2EE Implementation 🔐

```bash
# ═══════════════════════════════════════════
# END-TO-END ENCRYPTION (E2EE)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHAT IS E2EE?                            ║
╚════════════════════════════════════════════════════════════╝

Definition:
─────────────────────────────────────────────────────────────
Encryption where only sender and recipient can read messages
Server cannot decrypt (even if compromised)

How it works:
─────────────────────────────────────────────────────────────
Alice                  Server               Bob
  │                      │                   │
  │──── Public Key ──────┼────────────────→ │
  │                      │                   │
  │ ←──────────────────┼──── Public Key ───│
  │                      │                   │
  │                      │                   │
  │── Encrypted Message ─→│                  │
  │   (with Bob's pubkey) │                  │
  │                      │──────────────────→│
  │                      │  (Server can't    │
  │                      │   read this!)     │
  │                      │                   │
  │                      │                   │ Decrypt with
  │                      │                   │ private key
  │                      │                   │
  │                      │ ←─── Reply ──────│
  │                      │                   │
  │ ←────────────────────│                  │

Examples: Signal, WhatsApp, iMessage, Telegram Secret Chats

# ═══════════════════════════════════════════
# SIGNAL PROTOCOL (THE GOLD STANDARD)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SIGNAL PROTOCOL OVERVIEW                 ║
╚════════════════════════════════════════════════════════════╝

Used by:
─────────────────────────────────────────────────────────────
• Signal (duh!)
• WhatsApp
• Facebook Messenger (secret conversations)
• Google Messages (RCS)
• Skype (private conversations)

Features:
─────────────────────────────────────────────────────────────
✅ Perfect Forward Secrecy: Compromising one key doesn't compromise past messages
✅ Future Secrecy: Can recover from key compromise
✅ Deniability: Can't prove who sent message
✅ Asynchronous: Works even if recipient offline

Simplified Implementation (Concept):
─────────────────────────────────────────────────────────────
// Using libsignal-protocol (JavaScript)
const SignalProtocolStore = require('./InMemorySignalProtocolStore');
const {
  KeyHelper,
  SignalProtocolAddress,
  SessionBuilder,
  SessionCipher
} = require('@signalapp/libsignal-client');

// Initialize for Alice
async function initializeAlice() {
  const aliceStore = new SignalProtocolStore();

  // Generate identity key pair
  const identityKeyPair = await KeyHelper.generateIdentityKeyPair();

  // Generate registration ID
  const registrationId = await KeyHelper.generateRegistrationId();

  // Store identity
  await aliceStore.put('identityKey', identityKeyPair);
  await aliceStore.put('registrationId', registrationId);

  // Generate pre-keys
  const preKey = await KeyHelper.generatePreKey(1);
  await aliceStore.storePreKey(1, preKey.keyPair);

  // Generate signed pre-key
  const signedPreKey = await KeyHelper.generateSignedPreKey(
    identityKeyPair,
    1
  );
  await aliceStore.storeSignedPreKey(1, signedPreKey.keyPair);

  return {
    store: aliceStore,
    registrationId,
    identityKey: identityKeyPair.pubKey,
    preKey: preKey.keyPair.pubKey,
    signedPreKey: {
      keyId: 1,
      publicKey: signedPreKey.keyPair.pubKey,
      signature: signedPreKey.signature
    }
  };
}

// Send encrypted message
async function sendMessage(senderStore, recipientAddress, recipientPreKeyBundle, message) {
  // Build session
  const sessionBuilder = new SessionBuilder(senderStore, recipientAddress);
  await sessionBuilder.processPreKey(recipientPreKeyBundle);

  // Encrypt message
  const sessionCipher = new SessionCipher(senderStore, recipientAddress);
  const ciphertext = await sessionCipher.encrypt(Buffer.from(message));

  return ciphertext;
}

// Receive encrypted message
async function receiveMessage(recipientStore, senderAddress, ciphertext) {
  const sessionCipher = new SessionCipher(recipientStore, senderAddress);

  // Decrypt
  const plaintext = await sessionCipher.decrypt(ciphertext);

  return plaintext.toString('utf8');
}

# ═══════════════════════════════════════════
# SIMPLE E2EE CHAT (PRACTICAL EXAMPLE)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   BASIC E2EE MESSAGING                     ║
╚════════════════════════════════════════════════════════════╝

Using RSA + AES (Simpler, Educational):
─────────────────────────────────────────────────────────────
class E2EEMessaging {
  constructor() {
    this.users = new Map(); // user_id → { publicKey, privateKey }
    this.messages = new Map(); // message_id → encrypted message
  }

  // User registers (generates keys)
  async registerUser(userId) {
    const { publicKey, privateKey } = crypto.generateKeyPairSync('rsa', {
      modulusLength: 2048,
      publicKeyEncoding: { type: 'spki', format: 'pem' },
      privateKeyEncoding: { type: 'pkcs8', format: 'pem' }
    });

    this.users.set(userId, { publicKey, privateKey });

    // Only share public key
    return { userId, publicKey };
  }

  // Send encrypted message
  sendMessage(senderId, recipientId, message) {
    const recipient = this.users.get(recipientId);
    if (!recipient) throw new Error('Recipient not found');

    // 1. Generate random AES key
    const aesKey = crypto.randomBytes(32);
    const iv = crypto.randomBytes(16);

    // 2. Encrypt message with AES
    const cipher = crypto.createCipheriv('aes-256-gcm', aesKey, iv);
    let encrypted = cipher.update(message, 'utf8', 'hex');
    encrypted += cipher.final('hex');
    const authTag = cipher.getAuthTag();

    // 3. Encrypt AES key with recipient's public key
    const encryptedKey = crypto.publicEncrypt(
      recipient.publicKey,
      aesKey
    );

    // 4. Store encrypted message (server can't read this!)
    const messageId = crypto.randomBytes(16).toString('hex');
    this.messages.set(messageId, {
      senderId,
      recipientId,
      encryptedMessage: encrypted,
      encryptedKey: encryptedKey.toString('base64'),
      iv: iv.toString('hex'),
      authTag: authTag.toString('hex'),
      timestamp: new Date()
    });

    return messageId;
  }

  // Receive encrypted message
  receiveMessage(messageId, recipientId) {
    const msg = this.messages.get(messageId);
    if (!msg || msg.recipientId !== recipientId) {
      throw new Error('Message not found');
    }

    const recipient = this.users.get(recipientId);

    // 1. Decrypt AES key with private key
    const aesKey = crypto.privateDecrypt(
      recipient.privateKey,
      Buffer.from(msg.encryptedKey, 'base64')
    );

    // 2. Decrypt message with AES
    const decipher = crypto.createDecipheriv(
      'aes-256-gcm',
      aesKey,
      Buffer.from(msg.iv, 'hex')
    );
    decipher.setAuthTag(Buffer.from(msg.authTag, 'hex'));

    let decrypted = decipher.update(msg.encryptedMessage, 'hex', 'utf8');
    decrypted += decipher.final('utf8');

    return {
      from: msg.senderId,
      message: decrypted,
      timestamp: msg.timestamp
    };
  }
}

// Usage
const messaging = new E2EEMessaging();

// Alice and Bob register
const alice = await messaging.registerUser('alice');
const bob = await messaging.registerUser('bob');

// Alice sends encrypted message to Bob
const messageId = messaging.sendMessage(
  'alice',
  'bob',
  'Hey Bob, this is a secret message! 🔒'
);

console.log('Message encrypted and stored');

// Server cannot read the message!
// Only Bob can decrypt it

// Bob receives message
const decrypted = messaging.receiveMessage(messageId, 'bob');
console.log('Bob received:', decrypted.message);

WebSocket Real-Time E2EE Chat:
─────────────────────────────────────────────────────────────
// Server (server.js)
const WebSocket = require('ws');
const wss = new WebSocket.Server({ port: 8080 });

const users = new Map(); // userId → websocket

wss.on('connection', (ws) => {
  let userId;

  ws.on('message', (data) => {
    const msg = JSON.parse(data);

    switch (msg.type) {
      case 'register':
        userId = msg.userId;
        users.set(userId, ws);

        // Broadcast user's public key to others
        broadcast({
          type: 'user-joined',
          userId: msg.userId,
          publicKey: msg.publicKey
        }, userId);
        break;

      case 'message':
        // Forward encrypted message to recipient
        const recipientWs = users.get(msg.recipientId);
        if (recipientWs) {
          recipientWs.send(JSON.stringify({
            type: 'message',
            from: userId,
            encryptedMessage: msg.encryptedMessage,
            encryptedKey: msg.encryptedKey,
            iv: msg.iv,
            authTag: msg.authTag
          }));
        }
        break;
    }
  });

  ws.on('close', () => {
    users.delete(userId);
  });
});

function broadcast(msg, excludeUserId) {
  users.forEach((ws, id) => {
    if (id !== excludeUserId) {
      ws.send(JSON.stringify(msg));
    }
  });
}

// Client (client.js)
class E2EEChatClient {
  constructor(userId) {
    this.userId = userId;
    this.ws = new WebSocket('ws://localhost:8080');
    this.users = new Map(); // userId → publicKey
    this.generateKeys();

    this.ws.onopen = () => {
      this.register();
    };

    this.ws.onmessage = (event) => {
      this.handleMessage(JSON.parse(event.data));
    };
  }

  generateKeys() {
    const { publicKey, privateKey } = crypto.generateKeyPairSync('rsa', {
      modulusLength: 2048,
      publicKeyEncoding: { type: 'spki', format: 'pem' },
      privateKeyEncoding: { type: 'pkcs8', format: 'pem' }
    });

    this.publicKey = publicKey;
    this.privateKey = privateKey;
  }

  register() {
    this.ws.send(JSON.stringify({
      type: 'register',
      userId: this.userId,
      publicKey: this.publicKey
    }));
  }

  handleMessage(msg) {
    switch (msg.type) {
      case 'user-joined':
        console.log(`${msg.userId} joined`);
        this.users.set(msg.userId, msg.publicKey);
        break;

      case 'message':
        const decrypted = this.decryptMessage(msg);
        console.log(`${msg.from}: ${decrypted}`);
        break;
    }
  }

  sendMessage(recipientId, message) {
    const recipientPublicKey = this.users.get(recipientId);
    if (!recipientPublicKey) {
      throw new Error('Recipient not found');
    }

    // Generate AES key
    const aesKey = crypto.randomBytes(32);
    const iv = crypto.randomBytes(16);

    // Encrypt message
    const cipher = crypto.createCipheriv('aes-256-gcm', aesKey, iv);
    let encrypted = cipher.update(message, 'utf8', 'hex');
    encrypted += cipher.final('hex');
    const authTag = cipher.getAuthTag();

    // Encrypt AES key
    const encryptedKey = crypto.publicEncrypt(
      recipientPublicKey,
      aesKey
    );

    // Send
    this.ws.send(JSON.stringify({
      type: 'message',
      recipientId,
      encryptedMessage: encrypted,
      encryptedKey: encryptedKey.toString('base64'),
      iv: iv.toString('hex'),
      authTag: authTag.toString('hex')
    }));
  }

  decryptMessage(msg) {
    // Decrypt AES key
    const aesKey = crypto.privateDecrypt(
      this.privateKey,
      Buffer.from(msg.encryptedKey, 'base64')
    );

    // Decrypt message
    const decipher = crypto.createDecipheriv(
      'aes-256-gcm',
      aesKey,
      Buffer.from(msg.iv, 'hex')
    );
    decipher.setAuthTag(Buffer.from(msg.authTag, 'hex'));

    let decrypted = decipher.update(msg.encryptedMessage, 'hex', 'utf8');
    decrypted += decipher.final('utf8');

    return decrypted;
  }
}

// Usage
const alice = new E2EEChatClient('alice');
const bob = new E2EEChatClient('bob');

// After both connected
setTimeout(() => {
  alice.sendMessage('bob', 'Secret message! 🔒');
}, 2000);

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🗝️ Key Management

</div>

### Secure Key Storage & Rotation 🔑

```bash
# ═══════════════════════════════════════════
# KEY MANAGEMENT FUNDAMENTALS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   KEY MANAGEMENT CHALLENGES                ║
╚════════════════════════════════════════════════════════════╝

The Problem:
─────────────────────────────────────────────────────────────
• How to store keys securely?
• How to share keys with team?
• How to rotate keys?
• What if a key is compromised?
• How to manage keys across environments?

Solutions:
─────────────────────────────────────────────────────────────
1. Environment Variables (Basic)
2. Encrypted Configuration Files
3. Key Management Services (KMS)
4. Hardware Security Modules (HSM)
5. Secret Management Tools

# ═══════════════════════════════════════════
# KEY STORAGE METHODS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   1. ENVIRONMENT VARIABLES                 ║
╚════════════════════════════════════════════════════════════╝

Simplest Approach:
─────────────────────────────────────────────────────────────
# .env
ENCRYPTION_KEY=a1b2c3d4e5f6...
DATABASE_PASSWORD=supersecret
JWT_SECRET=anothersecret

# Load in Node.js
require('dotenv').config();

const encryptionKey = Buffer.from(
  process.env.ENCRYPTION_KEY,
  'hex'
);

Security:
─────────────────────────────────────────────────────────────
✅ Better than hardcoding
✅ Different keys per environment
✅ Not in version control (.gitignore)

❌ Keys stored in plain text on server
❌ Visible to anyone with server access
❌ No audit trail
❌ Hard to rotate

Best for: Development, small projects

╔════════════════════════════════════════════════════════════╗
║                   2. ENCRYPTED CONFIG FILES                ║
╚════════════════════════════════════════════════════════════╝

Using git-crypt:
─────────────────────────────────────────────────────────────
# Install
brew install git-crypt

# Initialize in repo
git-crypt init

# Add team member (GPG key)
git-crypt add-gpg-user user@example.com

# Mark files for encryption (.gitattributes)
secrets.json filter=git-crypt diff=git-crypt
.env.production filter=git-crypt diff=git-crypt

# Files are encrypted in git, decrypted locally!

Using SOPS (Secrets OPerationS):
─────────────────────────────────────────────────────────────
# Install
brew install sops

# Create encrypted file
sops secrets.yaml

# Edit (auto decrypts in editor)
sops secrets.yaml

# Decrypt to stdout
sops -d secrets.yaml

# Encrypt with AWS KMS
sops --kms arn:aws:kms:... secrets.yaml

Benefits:
✅ Encrypted in version control
✅ Team collaboration
✅ Audit trail
✅ Can use cloud KMS

╔════════════════════════════════════════════════════════════╗
║                   3. AWS KMS (KEY MANAGEMENT SERVICE)      ║
╚════════════════════════════════════════════════════════════╝

What is AWS KMS:
─────────────────────────────────────────────────────────────
• Managed encryption service
• Keys never leave AWS
• Automatic key rotation
• Access control with IAM
• Audit logging

Setup:
─────────────────────────────────────────────────────────────
const AWS = require('aws-sdk');
const kms = new AWS.KMS({ region: 'us-east-1' });

// Encrypt data
async function encrypt(plaintext, keyId) {
  const params = {
    KeyId: keyId,
    Plaintext: plaintext
  };

  const result = await kms.encrypt(params).promise();
  return result.CiphertextBlob.toString('base64');
}

// Decrypt data
async function decrypt(ciphertext) {
  const params = {
    CiphertextBlob: Buffer.from(ciphertext, 'base64')
  };

  const result = await kms.decrypt(params).promise();
  return result.Plaintext.toString();
}

// Generate data key (for envelope encryption)
async function generateDataKey(keyId) {
  const params = {
    KeyId: keyId,
    KeySpec: 'AES_256'
  };

  const result = await kms.generateDataKey(params).promise();

  return {
    plaintext: result.Plaintext,
    encrypted: result.CiphertextBlob.toString('base64')
  };
}

// Usage
const keyId = 'arn:aws:kms:us-east-1:123456789:key/...';

// Encrypt database password
const encryptedPassword = await encrypt('mypassword', keyId);
console.log('Encrypted:', encryptedPassword);

// Store encrypted password
await saveToSSM(encryptedPassword);

// Decrypt when needed
const password = await decrypt(encryptedPassword);

Envelope Encryption (for large data):
─────────────────────────────────────────────────────────────
// Don't encrypt large data directly with KMS (limits apply)
// Instead: Envelope encryption

// 1. Generate data key with KMS
const { plaintext: dataKey, encrypted: encryptedDataKey } =
  await generateDataKey(keyId);

// 2. Encrypt data with data key (AES)
const aes = new AESEncryption();
const encryptedData = aes.encrypt(largeData, dataKey);

// 3. Store encrypted data + encrypted data key
await store({
  data: encryptedData,
  key: encryptedDataKey  // Only this needs KMS to decrypt
});

// 4. To decrypt:
const stored = await retrieve();
const dataKey = await decrypt(stored.key);  // KMS decrypt
const data = aes.decrypt(stored.data, Buffer.from(dataKey));

╔════════════════════════════════════════════════════════════╗
║                   4. HASHICORP VAULT                       ║
╚════════════════════════════════════════════════════════════╝

What is Vault:
─────────────────────────────────────────────────────────────
• Secret management tool
• Dynamic secrets
• Encryption as a service
• Audit logging
• Open source + Enterprise

Setup (Docker):
─────────────────────────────────────────────────────────────
# Start Vault
docker run --cap-add=IPC_LOCK \
  -e 'VAULT_DEV_ROOT_TOKEN_ID=myroot' \
  -p 8200:8200 \
  vault:latest

# Set environment
export VAULT_ADDR='http://localhost:8200'
export VAULT_TOKEN='myroot'

# Write secret
vault kv put secret/myapp/db \
  username=admin \
  password=supersecret

# Read secret
vault kv get secret/myapp/db

Node.js Integration:
─────────────────────────────────────────────────────────────
const vault = require('node-vault')({
  endpoint: 'http://localhost:8200',
  token: process.env.VAULT_TOKEN
});

// Read secret
async function getSecret(path) {
  const result = await vault.read(path);
  return result.data.data;
}

// Write secret
async function setSecret(path, data) {
  await vault.write(path, { data });
}

// Usage
const dbConfig = await getSecret('secret/myapp/db');
console.log('Username:', dbConfig.username);
console.log('Password:', dbConfig.password);

Dynamic Secrets:
─────────────────────────────────────────────────────────────
// Vault generates temporary credentials

// Enable database secrets engine
await vault.write('sys/mounts/database', {
  type: 'database'
});

// Configure PostgreSQL connection
await vault.write('database/config/postgres', {
  plugin_name: 'postgresql-database-plugin',
  connection_url: 'postgresql://{{username}}:{{password}}@localhost:5432/mydb',
  allowed_roles: 'readonly',
  username: 'vault',
  password: 'vaultpass'
});

// Create role
await vault.write('database/roles/readonly', {
  db_name: 'postgres',
  creation_statements: [
    'CREATE ROLE "{{name}}" WITH LOGIN PASSWORD \'{{password}}\' VALID UNTIL \'{{expiration}}\';',
    'GRANT SELECT ON ALL TABLES IN SCHEMA public TO "{{name}}";'
  ],
  default_ttl: '1h',
  max_ttl: '24h'
});

// Generate temporary credentials
const creds = await vault.read('database/creds/readonly');
console.log('Username:', creds.data.username);
console.log('Password:', creds.data.password);
console.log('Expires in 1 hour');

// Vault automatically revokes after TTL!

╔════════════════════════════════════════════════════════════╗
║                   5. DOPPLER (MODERN SECRETS)              ║
╚════════════════════════════════════════════════════════════╝

What is Doppler:
─────────────────────────────────────────────────────────────
• Modern secrets management
• Sync across environments
• Team collaboration
• CLI + API
• Free tier available

Setup:
─────────────────────────────────────────────────────────────
# Install
brew install dopplerhq/cli/doppler

# Login
doppler login

# Setup in project
doppler setup

# Run app with secrets
doppler run -- npm start

# Secrets are injected as environment variables
# No .env file needed!

Integration:
─────────────────────────────────────────────────────────────
// No code changes needed!
// Secrets available as process.env

const dbPassword = process.env.DATABASE_PASSWORD;
const apiKey = process.env.API_KEY;

// Or use SDK for dynamic fetching
const { DopplerSDK } = require('@dopplerhq/node-sdk');

const doppler = new DopplerSDK({
  accessToken: process.env.DOPPLER_TOKEN
});

const secrets = await doppler.secrets.list({
  project: 'myproject',
  config: 'production'
});

# ═══════════════════════════════════════════
# KEY ROTATION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   KEY ROTATION STRATEGY                    ║
╚════════════════════════════════════════════════════════════╝

Why Rotate Keys:
─────────────────────────────────────────────────────────────
• Limit exposure if key compromised
• Compliance requirements
• Best practice

Rotation Frequency:
─────────────────────────────────────────────────────────────
• Encryption keys: 90 days
• API keys: 30-90 days
• Database passwords: 90 days
• SSL certificates: 90 days (Let's Encrypt)
• Root keys: Annually

Rotation Strategy:
─────────────────────────────────────────────────────────────
// Multi-key system (zero-downtime rotation)

class KeyRotation {
  constructor() {
    this.keys = [
      {
        id: 1,
        key: Buffer.from(process.env.ENCRYPTION_KEY_1, 'hex'),
        active: true,
        createdAt: new Date('2024-01-01')
      },
      {
        id: 2,
        key: Buffer.from(process.env.ENCRYPTION_KEY_2, 'hex'),
        active: true,  // Old key still valid for decryption
        createdAt: new Date('2023-10-01')
      }
    ];
  }

  // Encrypt with newest key
  encrypt(plaintext) {
    const activeKey = this.keys.find(k => k.active && this.isNewest(k));
    const aes = new AESEncryption();
    const encrypted = aes.encryptToString(plaintext, activeKey.key);

    // Prepend key ID
    return `${activeKey.id}:${encrypted}`;
  }

  // Decrypt with any valid key
  decrypt(encryptedWithId) {
    const [keyId, encrypted] = encryptedWithId.split(':');
    const key = this.keys.find(k => k.id === parseInt(keyId));

    if (!key || !key.active) {
      throw new Error('Key not found or inactive');
    }

    const aes = new AESEncryption();
    return aes.decryptFromString(encrypted, key.key);
  }

  // Re-encrypt data with new key
  async reEncrypt(oldEncrypted) {
    const plaintext = this.decrypt(oldEncrypted);
    return this.encrypt(plaintext);
  }

  isNewest(key) {
    return !this.keys.some(k => k.createdAt > key.createdAt);
  }
}

// Rotation process:
// 1. Generate new key
// 2. Add to key list (mark active)
// 3. New encryptions use new key
// 4. Old data can still be decrypted with old keys
// 5. Background job re-encrypts old data
// 6. After all data re-encrypted, deactivate old key

Automated Rotation Script:
─────────────────────────────────────────────────────────────
// rotate-keys.js
async function rotateEncryptionKeys() {
  console.log('Starting key rotation...');

  // 1. Generate new key
  const newKey = crypto.randomBytes(32);
  const newKeyId = Date.now();

  // 2. Store new key in KMS/Vault
  await vault.write(`secret/keys/${newKeyId}`, {
    key: newKey.toString('hex'),
    createdAt: new Date().toISOString()
  });

  // 3. Update application config (add new key)
  await updateConfig({
    ENCRYPTION_KEY_CURRENT: newKeyId,
    [`ENCRYPTION_KEY_${newKeyId}`]: newKey.toString('hex')
  });

  // 4. Restart application (rolling restart for zero downtime)
  await restartApplication();

  // 5. Re-encrypt data
  const records = await db.collection('sensitive_data').find({
    keyId: { $ne: newKeyId }
  });

  for (const record of records) {
    const decrypted = decrypt(record.encrypted, record.keyId);
    const reEncrypted = encrypt(decrypted, newKeyId);

    await db.collection('sensitive_data').updateOne(
      { _id: record._id },
      { $set: { encrypted: reEncrypted, keyId: newKeyId } }
    );
  }

  console.log(`Re-encrypted ${records.length} records`);

  // 6. Deactivate old keys (after grace period)
  const oldKeys = await vault.list('secret/keys');
  for (const keyPath of oldKeys) {
    const key = await vault.read(keyPath);
    const age = Date.now() - new Date(key.data.createdAt);

    if (age > 30 * 24 * 60 * 60 * 1000) { // 30 days
      await vault.delete(keyPath);
      console.log(`Deleted old key: ${keyPath}`);
    }
  }

  console.log('Key rotation complete!');
}

// Run monthly
schedule.scheduleJob('0 0 1 * *', rotateEncryptionKeys);

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 📧 Email Encryption (PGP/GPG)

</div>

### Pretty Good Privacy 📨

```bash
# ═══════════════════════════════════════════
# PGP/GPG EMAIL ENCRYPTION
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHAT IS PGP/GPG?                         ║
╚════════════════════════════════════════════════════════════╝

PGP (Pretty Good Privacy):
─────────────────────────────────────────────────────────────
• Created by Phil Zimmermann (1991)
• Standard for email encryption
• Uses public key cryptography

GPG (GNU Privacy Guard):
─────────────────────────────────────────────────────────────
• Free, open-source implementation of PGP
• Compatible with PGP
• Command-line tool

Use Cases:
─────────────────────────────────────────────────────────────
• Encrypted email
• File encryption
• Code signing (Git commits)
• Package signing

# ═══════════════════════════════════════════
# GPG SETUP
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   GETTING STARTED WITH GPG                 ║
╚════════════════════════════════════════════════════════════╝

Install:
─────────────────────────────────────────────────────────────
# macOS
brew install gpg

# Linux
sudo apt install gpg

# Windows
# Download from: https://gpg4win.org

Generate Key Pair:
─────────────────────────────────────────────────────────────
# Generate key
gpg --full-generate-key

# Options:
# 1. Kind of key: RSA and RSA (default)
# 2. Key size: 4096
# 3. Expiration: 1y (1 year)
# 4. Real name: Your Name
# 5. Email: your@email.com
# 6. Comment: (optional)
# 7. Passphrase: (strong password!)

# List keys
gpg --list-keys

# Output:
# pub   rsa4096 2024-01-01 [SC] [expires: 2025-01-01]
#       ABCD1234EF567890...
# uid           [ultimate] Your Name <your@email.com>
# sub   rsa4096 2024-01-01 [E] [expires: 2025-01-01]

Export Keys:
─────────────────────────────────────────────────────────────
# Export public key (share this!)
gpg --armor --export your@email.com > public-key.asc

# Export private key (keep secret!)
gpg --armor --export-secret-keys your@email.com > private-key.asc

# Import someone's public key
gpg --import their-public-key.asc

Encrypt & Decrypt:
─────────────────────────────────────────────────────────────
# Encrypt file
gpg --encrypt --recipient their@email.com secret.txt
# Creates: secret.txt.gpg

# Encrypt and sign
gpg --encrypt --sign --recipient their@email.com secret.txt

# Decrypt
gpg --decrypt secret.txt.gpg > secret-decrypted.txt

# Decrypt to stdout
gpg --decrypt secret.txt.gpg

Sign Files:
─────────────────────────────────────────────────────────────
# Sign a file (creates .sig file)
gpg --sign document.pdf
# Creates: document.pdf.gpg

# Clearsign (text visible + signature)
gpg --clearsign message.txt
# Creates: message.txt.asc

# Detached signature (separate file)
gpg --detach-sign document.pdf
# Creates: document.pdf.sig

# Verify signature
gpg --verify document.pdf.sig document.pdf

Git Commit Signing:
─────────────────────────────────────────────────────────────
# Configure Git to use GPG
git config --global user.signingkey YOUR_KEY_ID
git config --global commit.gpgsign true

# Sign a commit
git commit -S -m "Signed commit"

# Verify commits
git log --show-signature

# View signature
git verify-commit HEAD

# GitHub/GitLab will show "Verified" badge ✅

╔════════════════════════════════════════════════════════════╗
║                   EMAIL ENCRYPTION                         ║
╚════════════════════════════════════════════════════════════╝

Email Clients with PGP Support:
─────────────────────────────────────────────────────────────
• Thunderbird + Enigmail
• Apple Mail + GPGTools
• Outlook + Gpg4win
• ProtonMail (built-in)

Encrypt Email (Command Line):
─────────────────────────────────────────────────────────────
# Write email
cat > email.txt << EOF
To: recipient@example.com
From: sender@example.com
Subject: Encrypted Email

This is a secret message!
EOF

# Encrypt
gpg --encrypt --armor \
    --recipient recipient@example.com \
    email.txt

# Creates: email.txt.asc
# Send this as email body

# Recipient decrypts:
gpg --decrypt email.txt.asc

Node.js Integration (openpgp):
─────────────────────────────────────────────────────────────
const openpgp = require('openpgp');

// Generate key pair
async function generateKeyPair(name, email, passphrase) {
  const { privateKey, publicKey } = await openpgp.generateKey({
    type: 'rsa',
    rsaBits: 4096,
    userIDs: [{ name, email }],
    passphrase
  });

  return { privateKey, publicKey };
}

// Encrypt message
async function encryptMessage(message, publicKeyArmored) {
  const publicKey = await openpgp.readKey({ armoredKey: publicKeyArmored });

  const encrypted = await openpgp.encrypt({
    message: await openpgp.createMessage({ text: message }),
    encryptionKeys: publicKey
  });

  return encrypted;
}

// Decrypt message
async function decryptMessage(encryptedMessage, privateKeyArmored, passphrase) {
  const privateKey = await openpgp.decryptKey({
    privateKey: await openpgp.readPrivateKey({ armoredKey: privateKeyArmored }),
    passphrase
  });

  const message = await openpgp.readMessage({
    armoredMessage: encryptedMessage
  });

  const { data: decrypted } = await openpgp.decrypt({
    message,
    decryptionKeys: privateKey
  });

  return decrypted;
}

// Sign and encrypt
async function signAndEncrypt(message, senderPrivateKey, recipientPublicKey, passphrase) {
  const privateKey = await openpgp.decryptKey({
    privateKey: await openpgp.readPrivateKey({ armoredKey: senderPrivateKey }),
    passphrase
  });

  const publicKey = await openpgp.readKey({ armoredKey: recipientPublicKey });

  const encrypted = await openpgp.encrypt({
    message: await openpgp.createMessage({ text: message }),
    encryptionKeys: publicKey,
    signingKeys: privateKey
  });

  return encrypted;
}

// Usage
const { privateKey, publicKey } = await generateKeyPair(
  'John Doe',
  'john@example.com',
  'my-passphrase'
);

const encrypted = await encryptMessage(
  'Secret message',
  publicKey
);

const decrypted = await decryptMessage(
  encrypted,
  privateKey,
  'my-passphrase'
);

console.log('Decrypted:', decrypted);

Web Crypto API (Browser):
─────────────────────────────────────────────────────────────
// Modern browsers have built-in crypto

// Generate key pair
const keyPair = await window.crypto.subtle.generateKey(
  {
    name: 'RSA-OAEP',
    modulusLength: 2048,
    publicExponent: new Uint8Array([1, 0, 1]),
    hash: 'SHA-256'
  },
  true,
  ['encrypt', 'decrypt']
);

// Encrypt
const encoder = new TextEncoder();
const data = encoder.encode('Secret message');

const encrypted = await window.crypto.subtle.encrypt(
  { name: 'RSA-OAEP' },
  keyPair.publicKey,
  data
);

// Decrypt
const decrypted = await window.crypto.subtle.decrypt(
  { name: 'RSA-OAEP' },
  keyPair.privateKey,
  encrypted
);

const decoder = new TextDecoder();
const message = decoder.decode(decrypted);

console.log('Decrypted:', message);

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 💾 Disk Encryption

</div>

### Full Disk Encryption 🔒

```bash
# ═══════════════════════════════════════════
# DISK ENCRYPTION TOOLS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   FULL DISK ENCRYPTION                     ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Tool            | Platform | Type           | Security | Performance |
| --------------- | -------- | -------------- | -------- | ----------- |
| **BitLocker**   | Windows  | Full disk      | ✅ High  | ⭐⭐⭐⭐    |
| **FileVault**   | macOS    | Full disk      | ✅ High  | ⭐⭐⭐⭐⭐  |
| **LUKS**        | Linux    | Full disk      | ✅ High  | ⭐⭐⭐⭐    |
| **VeraCrypt**   | All      | Container/disk | ✅ High  | ⭐⭐⭐      |
| **Cryptomator** | All      | Cloud files    | ✅ High  | ⭐⭐⭐⭐    |

</div>

```bash
# ═══════════════════════════════════════════
# FILEVAULT (macOS)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ENABLE FILEVAULT                         ║
╚════════════════════════════════════════════════════════════╝

GUI Method:
─────────────────────────────────────────────────────────────
1. System Preferences → Security & Privacy
2. FileVault tab
3. Click "Turn On FileVault"
4. Choose recovery method:
   • iCloud account (recommended)
   • Recovery key (save it!)
5. Restart and encrypt

Command Line:
─────────────────────────────────────────────────────────────
# Enable FileVault
sudo fdesetup enable

# Check status
sudo fdesetup status

# List users
sudo fdesetup list

# Generate recovery key
sudo fdesetup changerecovery -personal

What it does:
─────────────────────────────────────────────────────────────
✅ Encrypts entire disk (XTS-AES-128)
✅ Transparent (no performance impact)
✅ Integrated with macOS
✅ Hardware acceleration (T2/Apple Silicon)

# ═══════════════════════════════════════════
# BITLOCKER (Windows)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ENABLE BITLOCKER                         ║
╚════════════════════════════════════════════════════════════╝

GUI Method:
─────────────────────────────────────────────────────────────
1. Right-click drive → "Turn on BitLocker"
2. Choose unlock method:
   • Password
   • Smart card
   • Both
3. Save recovery key
4. Encrypt

Command Line (PowerShell):
─────────────────────────────────────────────────────────────
# Enable BitLocker
Enable-BitLocker -MountPoint "C:" -EncryptionMethod XtsAes256 -UsedSpaceOnly

# With password
$SecureString = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
Enable-BitLocker -MountPoint "C:" -PasswordProtector -Password $SecureString

# Check status
Get-BitLockerVolume -MountPoint "C:"

# Backup recovery key
Backup-BitLockerKeyProtector -MountPoint "C:" -KeyProtectorId $KeyID

What it does:
─────────────────────────────────────────────────────────────
✅ Encrypts entire drive (AES-128/256)
✅ TPM integration
✅ Transparent
✅ Enterprise features

# ═══════════════════════════════════════════
# LUKS (Linux)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   LINUX UNIFIED KEY SETUP                  ║
╚════════════════════════════════════════════════════════════╝

Encrypt New Partition:
─────────────────────────────────────────────────────────────
# Format partition with LUKS
sudo cryptsetup luksFormat /dev/sdb1

# Open encrypted partition
sudo cryptsetup luksOpen /dev/sdb1 encrypted_disk

# Create filesystem
sudo mkfs.ext4 /dev/mapper/encrypted_disk

# Mount
sudo mount /dev/mapper/encrypted_disk /mnt/secure

# Unmount and close
sudo umount /mnt/secure
sudo cryptsetup luksClose encrypted_disk

Encrypt Existing Data:
─────────────────────────────────────────────────────────────
# Backup data first!
# Use cryptsetup-reencrypt

sudo cryptsetup-reencrypt /dev/sdb1 --new --reduce-device-size 32M

Auto-mount on Boot:
─────────────────────────────────────────────────────────────
# /etc/crypttab
encrypted_disk /dev/sdb1 none luks

# /etc/fstab
/dev/mapper/encrypted_disk /mnt/secure ext4 defaults 0 2

# With key file (for automatic unlock)
# Generate key
dd if=/dev/urandom of=/root/luks-key bs=512 count=1
chmod 400 /root/luks-key

# Add key to LUKS
sudo cryptsetup luksAddKey /dev/sdb1 /root/luks-key

# Update crypttab
encrypted_disk /dev/sdb1 /root/luks-key luks

# ═══════════════════════════════════════════
# VERACRYPT (Cross-Platform)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   VERACRYPT CONTAINERS                     ║
╚════════════════════════════════════════════════════════════╝

What is VeraCrypt:
─────────────────────────────────────────────────────────────
• Successor to TrueCrypt
• Cross-platform (Windows, macOS, Linux)
• Creates encrypted containers or encrypts partitions
• Strong encryption (AES, Serpent, Twofish)
• Hidden volumes (plausible deniability)

Create Encrypted Container:
─────────────────────────────────────────────────────────────
# Command line
veracrypt --text --create /path/to/container.tc

# Options:
# 1. Volume type: Normal or hidden
# 2. Size: e.g., 1G
# 3. Encryption: AES
# 4. Hash: SHA-512
# 5. Filesystem: ext4 or FAT
# 6. Password: Strong password!
# 7. Random data: Move mouse randomly

Mount Container:
─────────────────────────────────────────────────────────────
# Mount
veracrypt --text /path/to/container.tc /mnt/veracrypt1

# Unmount
veracrypt --text --dismount /mnt/veracrypt1

# Unmount all
veracrypt --text --dismount

GUI: Much easier, just use the application!

# ═══════════════════════════════════════════
# CRYPTOMATOR (Cloud Storage)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ENCRYPT CLOUD FILES                      ║
╚════════════════════════════════════════════════════════════╝

What is Cryptomator:
─────────────────────────────────────────────────────────────
• Encrypt files before uploading to cloud
• Works with Dropbox, Google Drive, OneDrive, etc.
• Transparent encryption (virtual drive)
• Open source
• Client-side encryption (cloud provider can't read)

Setup:
─────────────────────────────────────────────────────────────
1. Install Cryptomator
2. Create vault in cloud folder
   ~/Dropbox/MyCryptoVault
3. Set strong password
4. Unlock vault (mounts as drive)
5. Add files to vault
6. Files automatically encrypted before sync

How it works:
─────────────────────────────────────────────────────────────
Your Files               Encrypted Files (in cloud)
  documents/              d/
    secret.pdf       →      AB/CD/ENCRYPTED_NAME_1.c9r
    photo.jpg        →      EF/GH/ENCRYPTED_NAME_2.c9r

• Files encrypted individually (AES-256)
• Filenames encrypted
• Directory structure obfuscated
• Cloud provider sees encrypted blobs

Benefits:
─────────────────────────────────────────────────────────────
✅ Zero-knowledge encryption
✅ Works with any cloud provider
✅ Transparent to apps (use like normal drive)
✅ Open source (audited)
✅ Cross-platform

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 📡 Network Encryption

</div>

### VPN & Secure Tunnels 🌐

```bash
# ═══════════════════════════════════════════
# VPN (VIRTUAL PRIVATE NETWORK)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   VPN PROTOCOLS                            ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Protocol        | Security   | Speed      | Use Case     | Encryption |
| --------------- | ---------- | ---------- | ------------ | ---------- |
| **OpenVPN**     | ⭐⭐⭐⭐⭐ | ⭐⭐⭐     | General use  | AES-256    |
| **WireGuard**   | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | Modern VPN   | ChaCha20   |
| **IPSec/IKEv2** | ⭐⭐⭐⭐   | ⭐⭐⭐⭐   | Mobile       | AES-256    |
| **PPTP**        | ⭐         | ⭐⭐⭐⭐⭐ | ❌ Don't use | Weak       |
| **L2TP/IPSec**  | ⭐⭐⭐     | ⭐⭐⭐     | Legacy       | AES-256    |

</div>

```bash
# ═══════════════════════════════════════════
# WIREGUARD (MODERN & FAST)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WIREGUARD SETUP                          ║
╚════════════════════════════════════════════════════════════╝

Install:
─────────────────────────────────────────────────────────────
# Ubuntu/Debian
sudo apt install wireguard

# macOS
brew install wireguard-tools

# Windows/iOS/Android
# Download from: https://www.wireguard.com/install/

Generate Keys:
─────────────────────────────────────────────────────────────
# Generate private key
wg genkey | tee privatekey | wg pubkey > publickey

# Or combined
umask 077
wg genkey > private.key
wg pubkey < private.key > public.key

Server Configuration:
─────────────────────────────────────────────────────────────
# /etc/wireguard/wg0.conf

[Interface]
Address = 10.0.0.1/24
ListenPort = 51820
PrivateKey = SERVER_PRIVATE_KEY

# Enable IP forwarding
PostUp = sysctl -w net.ipv4.ip_forward=1
PostUp = iptables -A FORWARD -i wg0 -j ACCEPT
PostUp = iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

PostDown = iptables -D FORWARD -i wg0 -j ACCEPT
PostDown = iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE

# Client 1
[Peer]
PublicKey = CLIENT1_PUBLIC_KEY
AllowedIPs = 10.0.0.2/32

# Client 2
[Peer]
PublicKey = CLIENT2_PUBLIC_KEY
AllowedIPs = 10.0.0.3/32

Start Server:
─────────────────────────────────────────────────────────────
# Start
sudo wg-quick up wg0

# Stop
sudo wg-quick down wg0

# Enable on boot
sudo systemctl enable wg-quick@wg0

# Check status
sudo wg show

Client Configuration:
─────────────────────────────────────────────────────────────
# /etc/wireguard/wg0.conf

[Interface]
Address = 10.0.0.2/24
PrivateKey = CLIENT_PRIVATE_KEY
DNS = 1.1.1.1

[Peer]
PublicKey = SERVER_PUBLIC_KEY
Endpoint = server.example.com:51820
AllowedIPs = 0.0.0.0/0  # Route all traffic through VPN
PersistentKeepalive = 25

Connect Client:
─────────────────────────────────────────────────────────────
sudo wg-quick up wg0

Why WireGuard is Great:
─────────────────────────────────────────────────────────────
✅ Fast (faster than OpenVPN)
✅ Simple (4,000 lines of code vs OpenVPN's 100,000+)
✅ Modern cryptography (ChaCha20, Curve25519)
✅ Built into Linux kernel (5.6+)
✅ Low latency
✅ Battery efficient (mobile)

# ═══════════════════════════════════════════
# SSH TUNNELING
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SSH PORT FORWARDING                      ║
╚════════════════════════════════════════════════════════════╝

Local Port Forwarding:
─────────────────────────────────────────────────────────────
# Forward local port to remote service
ssh -L 8080:localhost:80 user@server.com

# Now: localhost:8080 → server.com:80 (encrypted!)

# Use case: Access remote database securely
ssh -L 5432:localhost:5432 user@db-server.com
# Connect to: localhost:5432 (reaches remote PostgreSQL)

Remote Port Forwarding:
─────────────────────────────────────────────────────────────
# Expose local service to remote server
ssh -R 8080:localhost:3000 user@server.com

# Use case: Share local dev server with team
# server.com:8080 → your localhost:3000

Dynamic Port Forwarding (SOCKS Proxy):
─────────────────────────────────────────────────────────────
# Create SOCKS proxy
ssh -D 1080 user@server.com

# Configure browser to use SOCKS proxy localhost:1080
# All browser traffic now encrypted through SSH tunnel!

# Command line with proxy
curl --socks5 localhost:1080 https://example.com

SSH VPN (tun/tap):
─────────────────────────────────────────────────────────────
# Full VPN over SSH
sudo ssh -w 0:0 root@server.com

# Requires:
# PermitTunnel yes (in /etc/ssh/sshd_config)
# Tunnel=yes (in /etc/ssh/ssh_config)

# ═══════════════════════════════════════════
# STUNNEL (TLS WRAPPER)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ADD TLS TO ANY SERVICE                   ║
╚════════════════════════════════════════════════════════════╝

What is stunnel:
─────────────────────────────────────────────────────────────
Wraps unencrypted protocols in TLS

Install:
─────────────────────────────────────────────────────────────
sudo apt install stunnel4

Example: Encrypt Redis Connection:
─────────────────────────────────────────────────────────────
# Server config (/etc/stunnel/stunnel.conf)
[redis-server]
accept = 6380
connect = 127.0.0.1:6379
cert = /etc/stunnel/cert.pem
key = /etc/stunnel/key.pem

# Client config
[redis-client]
client = yes
accept = 127.0.0.1:6379
connect = redis-server.com:6380
CAfile = /etc/stunnel/ca.pem

# Now Redis traffic is encrypted!

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🛠️ Encryption Libraries

</div>

### Popular Crypto Libraries 📚

```bash
# ═══════════════════════════════════════════
# ENCRYPTION LIBRARIES BY LANGUAGE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   NODE.JS / JAVASCRIPT                     ║
╚════════════════════════════════════════════════════════════╝

1. crypto (Built-in)
─────────────────────────────────────────────────────────────
const crypto = require('crypto');

// ✅ Built into Node.js
// ✅ Full-featured
// ✅ No dependencies
// Use for: All crypto operations

2. tweetnacl
─────────────────────────────────────────────────────────────
const nacl = require('tweetnacl');

// ✅ Small, fast
// ✅ Modern cryptography
// ✅ Audited
// Use for: Public key crypto, signatures

3. bcrypt / argon2
─────────────────────────────────────────────────────────────
const bcrypt = require('bcrypt');
const argon2 = require('argon2');

// ✅ Password hashing
// Use for: Storing passwords

4. jsonwebtoken
─────────────────────────────────────────────────────────────
const jwt = require('jsonwebtoken');

// ✅ JWT creation/verification
// Use for: Authentication tokens

5. openpgp.js
─────────────────────────────────────────────────────────────
const openpgp = require('openpgp');

// ✅ PGP/GPG in JavaScript
// ✅ Email encryption
// Use for: Email/file encryption

╔════════════════════════════════════════════════════════════╗
║                   PYTHON                                   ║
╚════════════════════════════════════════════════════════════╝

1. cryptography
─────────────────────────────────────────────────────────────
from cryptography.fernet import Fernet

# ✅ High-level crypto
# ✅ Well-designed API
# ✅ Recommended
# Use for: General encryption

# Example
key = Fernet.generate_key()
f = Fernet(key)

encrypted = f.encrypt(b"Secret message")
decrypted = f.decrypt(encrypted)

2. pycryptodome
─────────────────────────────────────────────────────────────
from Crypto.Cipher import AES
from Crypto.Random import get_random_bytes

# ✅ Low-level crypto primitives
# ✅ Compatible with PyCrypto
# Use for: Advanced crypto operations

3. passlib
─────────────────────────────────────────────────────────────
from passlib.hash import argon2

# ✅ Password hashing
# ✅ Multiple algorithms
# Use for: Password storage

hash = argon2.hash("password")
argon2.verify("password", hash)  # True

4. PyNaCl
─────────────────────────────────────────────────────────────
import nacl.secret
import nacl.utils

# ✅ Modern crypto (libsodium)
# ✅ Easy to use
# Use for: Modern encryption

╔════════════════════════════════════════════════════════════╗
║                   GOLANG                                   ║
╚════════════════════════════════════════════════════════════╝

1. crypto/* (Standard Library)
─────────────────────────────────────────────────────────────
import (
    "crypto/aes"
    "crypto/cipher"
    "crypto/rand"
    "crypto/rsa"
    "crypto/sha256"
)

// ✅ Built-in
// ✅ Production-ready
// Use for: All crypto needs

2. golang.org/x/crypto
─────────────────────────────────────────────────────────────
import "golang.org/x/crypto/bcrypt"

// ✅ Extended crypto
// ✅ Modern algorithms
// Use for: Additional algorithms (bcrypt, scrypt, etc.)

hash, _ := bcrypt.GenerateFromPassword([]byte("password"), 12)
err := bcrypt.CompareHashAndPassword(hash, []byte("password"))

3. age
─────────────────────────────────────────────────────────────
import "filippo.io/age"

// ✅ Modern file encryption
// ✅ Replacement for GPG
// Use for: File encryption

╔════════════════════════════════════════════════════════════╗
║                   RUST                                     ║
╚════════════════════════════════════════════════════════════╝

1. ring
─────────────────────────────────────────────────────────────
use ring::aead;
use ring::rand;

// ✅ Fast, safe
// ✅ BoringSSL-based
// Use for: TLS, AEAD encryption

2. sodiumoxide
─────────────────────────────────────────────────────────────
use sodiumoxide::crypto::secretbox;

// ✅ libsodium bindings
// ✅ Easy to use correctly
// Use for: Modern crypto

3. argon2
─────────────────────────────────────────────────────────────
use argon2::{self, Config};

// ✅ Password hashing
// Use for: Passwords

let hash = argon2::hash_encoded(
    b"password",
    b"randomsalt",
    &Config::default()
).unwrap();

╔════════════════════════════════════════════════════════════╗
║                   JAVA                                     ║
╚════════════════════════════════════════════════════════════╝

1. javax.crypto (Built-in)
─────────────────────────────────────────────────────────────
import javax.crypto.Cipher;
import javax.crypto.KeyGenerator;
import javax.crypto.SecretKey;

// ✅ Built into JDK
// ✅ Standard
// Use for: General crypto

2. Bouncy Castle
─────────────────────────────────────────────────────────────
import org.bouncycastle.jce.provider.BouncyCastleProvider;

// ✅ Comprehensive
// ✅ More algorithms
// Use for: Advanced crypto needs

3. Google Tink
─────────────────────────────────────────────────────────────
import com.google.crypto.tink.*;

// ✅ Misuse-resistant
// ✅ Google-maintained
// Use for: Safer crypto API

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## ✅ Best Practices

</div>

### Encryption Security Checklist 🔒

```bash
# ═══════════════════════════════════════════
# ENCRYPTION BEST PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   GENERAL PRINCIPLES                       ║
╚════════════════════════════════════════════════════════════╝

✅ DO:
─────────────────────────────────────────────────────────────
☐ Use proven algorithms (AES-256, RSA-2048+, SHA-256+)
☐ Use established libraries (don't roll your own crypto!)
☐ Keep libraries updated
☐ Use authenticated encryption (GCM, Poly1305)
☐ Generate cryptographically secure random numbers
☐ Use unique IVs/nonces for each encryption
☐ Protect private keys (never share, store securely)
☐ Rotate encryption keys regularly
☐ Encrypt data at rest AND in transit
☐ Use TLS 1.2+ for network communication
☐ Implement perfect forward secrecy
☐ Hash passwords with bcrypt/Argon2 (never plain SHA-256!)
☐ Use HMAC for message authentication
☐ Test encryption/decryption thoroughly
☐ Have key backup and recovery procedures

❌ DON'T:
─────────────────────────────────────────────────────────────
☐ Don't invent your own crypto algorithms
☐ Don't use ECB mode (use GCM, CBC, CTR)
☐ Don't use MD5 or SHA-1 (broken)
☐ Don't use single DES or 3DES (weak)
☐ Don't reuse IVs/nonces
☐ Don't store keys in code or version control
☐ Don't use Math.random() for crypto
☐ Don't encrypt without authentication
☐ Don't ignore certificate warnings
☐ Don't use short keys (< 2048-bit RSA, < 256-bit symmetric)

╔════════════════════════════════════════════════════════════╗
║                   ALGORITHM SELECTION                      ║
╚════════════════════════════════════════════════════════════╝

Symmetric Encryption:
─────────────────────────────────────────────────────────────
✅ RECOMMENDED:
• AES-256-GCM (best balance)
• ChaCha20-Poly1305 (modern, fast on mobile)
• AES-256-CTR + HMAC-SHA256

❌ AVOID:
• DES, 3DES (broken/weak)
• RC4 (broken)
• AES-ECB (insecure mode)
• Any custom algorithm

Asymmetric Encryption:
─────────────────────────────────────────────────────────────
✅ RECOMMENDED:
• RSA-2048 (minimum), RSA-4096 (high security)
• ECC P-256, P-384, P-521
• Curve25519 (modern)

❌ AVOID:
• RSA-1024 (too weak)
• Custom curves

Hashing:
─────────────────────────────────────────────────────────────
✅ RECOMMENDED:
• SHA-256, SHA-384, SHA-512
• SHA-3
• BLAKE2

For Passwords:
• bcrypt (cost factor ≥ 12)
• Argon2id (memory-hard)
• scrypt

❌ AVOID:
• MD5 (broken)
• SHA-1 (broken)
• Plain SHA-256 for passwords (too fast)

╔════════════════════════════════════════════════════════════╗
║                   KEY MANAGEMENT                           ║
╚════════════════════════════════════════════════════════════╝

Key Generation:
─────────────────────────────────────────────────────────────
✅ Use crypto.randomBytes() (Node.js)
✅ Use secrets module (Python)
✅ Use crypto/rand (Go)
✅ Use SecureRandom (Java)

❌ Never use Math.random() or predictable sources

Key Storage:
─────────────────────────────────────────────────────────────
✅ Environment variables (basic)
✅ Key Management Services (AWS KMS, Azure Key Vault)
✅ Hardware Security Modules (HSM)
✅ Secret management tools (Vault, Doppler)
✅ Encrypted configuration files

❌ Never:
• Hardcode in source code
• Commit to version control
• Store in plaintext on disk
• Share via email/Slack
• Include in Docker images

Key Rotation:
─────────────────────────────────────────────────────────────
Frequency:
• Data encryption keys: 90 days
• API keys: 30-90 days
• TLS certificates: 90 days
• Root keys: Annually

Process:
1. Generate new key
2. Mark old key as deprecated (still usable for decryption)
3. Use new key for all new encryption
4. Re-encrypt existing data with new key
5. Retire old key after grace period

╔════════════════════════════════════════════════════════════╗
║                   COMMON MISTAKES                          ║
╚════════════════════════════════════════════════════════════╝

1. Using Encryption Without Authentication
─────────────────────────────────────────────────────────────
❌ BAD:
const cipher = crypto.createCipheriv('aes-256-cbc', key, iv);
const encrypted = cipher.update(data) + cipher.final();

✅ GOOD:
const cipher = crypto.createCipheriv('aes-256-gcm', key, iv);
const encrypted = cipher.update(data) + cipher.final();
const authTag = cipher.getAuthTag();  // ✅ Authentication!

2. Reusing IV/Nonce
─────────────────────────────────────────────────────────────
❌ BAD:
const iv = Buffer.from('1234567890123456');  // Fixed IV!

✅ GOOD:
const iv = crypto.randomBytes(16);  // ✅ Random IV each time

3. Storing Keys Insecurely
─────────────────────────────────────────────────────────────
❌ BAD:
const ENCRYPTION_KEY = 'mysecretkey';  // ❌ In code!

✅ GOOD:
const ENCRYPTION_KEY = process.env.ENCRYPTION_KEY;  // ✅ From env

4. Using Weak Key Derivation
─────────────────────────────────────────────────────────────
❌ BAD:
const key = crypto.createHash('md5').update(password).digest();

✅ GOOD:
const key = crypto.pbkdf2Sync(password, salt, 100000, 32, 'sha512');

5. Not Validating Certificates
─────────────────────────────────────────────────────────────
❌ BAD:
process.env.NODE_TLS_REJECT_UNAUTHORIZED = '0';  // ❌ Disables validation!

✅ GOOD:
// Leave validation enabled (default)
// Use valid certificates

╔════════════════════════════════════════════════════════════╗
║                   TESTING ENCRYPTION                       ║
╚════════════════════════════════════════════════════════════╝

Test Cases:
─────────────────────────────────────────────────────────────
☐ Encrypt → Decrypt → Verify original data
☐ Test with different data sizes (small, large, empty)
☐ Test with special characters, unicode
☐ Test with binary data
☐ Verify ciphertext is different from plaintext
☐ Verify same plaintext → different ciphertext (due to random IV)
☐ Test decryption with wrong key fails
☐ Test decryption with tampered ciphertext fails
☐ Test key rotation process
☐ Performance test (encrypt/decrypt speed)
☐ Test backward compatibility after updates

Example Tests:
─────────────────────────────────────────────────────────────
describe('AES Encryption', () => {
  test('should encrypt and decrypt correctly', () => {
    const plaintext = 'Secret message';
    const key = aes.generateKey();

    const encrypted = aes.encrypt(plaintext, key);
    const decrypted = aes.decrypt(encrypted, key);

    expect(decrypted).toBe(plaintext);
  });

  test('should fail with wrong key', () => {
    const plaintext = 'Secret message';
    const key1 = aes.generateKey();
    const key2 = aes.generateKey();

    const encrypted = aes.encrypt(plaintext, key1);

    expect(() => {
      aes.decrypt(encrypted, key2);
    }).toThrow();
  });

  test('should produce different ciphertext each time', () => {
    const plaintext = 'Secret message';
    const key = aes.generateKey();

    const encrypted1 = aes.encrypt(plaintext, key);
    const encrypted2 = aes.encrypt(plaintext, key);

    expect(encrypted1).not.toEqual(encrypted2);  // Different IVs
  });
});

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🎓 Resources & Further Learning

</div>

### Essential Encryption Resources 📚

```
📘 Books
   Applied Cryptography - Bruce Schneier
   Cryptography Engineering - Ferguson, Schneier, Kohno
   Serious Cryptography - Jean-Philippe Aumasson

📗 Online Courses
   Cryptography I - Dan Boneh (Coursera)
   Applied Cryptography - Udacity
   Practical Cryptography for Developers

📙 Standards & Specifications
   NIST Cryptographic Standards: https://csrc.nist.gov/
   RFC 5246 - TLS 1.2: https://tools.ietf.org/html/rfc5246
   RFC 8446 - TLS 1.3: https://tools.ietf.org/html/rfc8446

🔧 Tools
   OpenSSL: https://www.openssl.org/
   GnuPG: https://gnupg.org/
   Let's Encrypt: https://letsencrypt.org/
   WireGuard: https://www.wireguard.com/

📱 Testing Tools
   SSL Labs: https://www.ssllabs.com/ssltest/
   testssl.sh: https://testssl.sh/
   CyberChef: https://gchq.github.io/CyberChef/

💬 Communities
   r/crypto: https://reddit.com/r/crypto
   Crypto StackExchange: https://crypto.stackexchange.com/
   IACR: https://www.iacr.org/

🎥 YouTube Channels
   Computerphile (cryptography videos)
   LiveOverflow (practical crypto)
   Christof Paar (crypto lectures)
```

---

<div align="center">

**Built with 🔐 by MrDib, for secure communications**

_Remember: "Anyone can invent a cipher that they themselves cannot break"_ 🛡️

**Stay Encrypted!** 🔒

---

### 🔗 Related Guides

- [Web Security](./Web-Security.md)
- [Authentication Tools](./Authentication-Tools.md)
- [Security Scanners](./Security-Scanners.md)

</div>
