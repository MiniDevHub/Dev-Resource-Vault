<div align="center">

# 🗄️ Databases

### _Store, query, and manage data like a pro_ 💾

![SQL](https://img.shields.io/badge/SQL-PostgreSQL-blue?style=for-the-badge&logo=postgresql)
![NoSQL](https://img.shields.io/badge/NoSQL-MongoDB-green?style=for-the-badge&logo=mongodb)
![Cache](https://img.shields.io/badge/Cache-Redis-red?style=for-the-badge&logo=redis)

</div>

---

## 📚 Table of Contents

- [🎯 Database Fundamentals](#-database-fundamentals)
- [🐘 PostgreSQL & Prisma](#-postgresql--prisma)
- [🍃 MongoDB & Mongoose](#-mongodb--mongoose)
- [🚀 Redis Caching](#-redis-caching)
- [🔄 Database Migrations](#-database-migrations)
- [📊 Query Optimization](#-query-optimization)
- [🔐 Database Security](#-database-security)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Database Fundamentals

</div>

### SQL vs NoSQL 📖

```javascript
// ═══════════════════════════════════════════
// SQL Databases (Relational)
// ═══════════════════════════════════════════

/*
Structure: Tables with rows and columns
Schema: Fixed, predefined
Relationships: Foreign keys, joins
Examples: PostgreSQL, MySQL, SQLite

✅ Best for:
- Complex queries
- Transactions (ACID)
- Structured data
- Data integrity
- Reporting

❌ Not ideal for:
- Unstructured data
- Horizontal scaling
- Rapid schema changes
*/

// ═══════════════════════════════════════════
// NoSQL Databases (Non-Relational)
// ═══════════════════════════════════════════

/*
Structure: Documents, key-value, graphs, columns
Schema: Flexible, dynamic
Relationships: Embedded or references
Examples: MongoDB, Redis, Firebase

✅ Best for:
- Unstructured data
- Horizontal scaling
- Flexible schemas
- Real-time data
- High throughput

❌ Not ideal for:
- Complex transactions
- Complex joins
- Data consistency critical apps
*/

// ═══════════════════════════════════════════
// When to Use What?
// ═══════════════════════════════════════════

/*
Use SQL when:
- Banking/Finance apps (transactions)
- E-commerce (inventory, orders)
- CRM/ERP systems
- Reporting systems
- Complex relationships

Use NoSQL when:
- Social media feeds
- Real-time analytics
- Content management
- IoT data
- Gaming leaderboards

Use Both (Polyglot Persistence):
- PostgreSQL for core data
- Redis for caching
- MongoDB for logs/analytics
*/
```

---

<div align="center">

## 🐘 PostgreSQL & Prisma

</div>

### Modern Database Stack 🚀

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

# Install Prisma
npm install -D prisma
npm install @prisma/client

# Initialize Prisma
npx prisma init

# This creates:
# - prisma/schema.prisma
# - .env file with DATABASE_URL
```

```prisma
// ═══════════════════════════════════════════
// Prisma Schema (prisma/schema.prisma)
// ═══════════════════════════════════════════

generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

// ═══════════════════════════════════════════
// User Model
// ═══════════════════════════════════════════

model User {
  id            String    @id @default(cuid())
  email         String    @unique
  name          String
  password      String
  role          Role      @default(USER)
  emailVerified Boolean   @default(false)
  avatar        String?

  // Relations
  posts         Post[]
  profile       Profile?
  comments      Comment[]
  sessions      Session[]

  // Timestamps
  createdAt     DateTime  @default(now())
  updatedAt     DateTime  @updatedAt
  lastLogin     DateTime?

  // Indexes
  @@index([email])
  @@index([role])
  @@index([createdAt])
}

// ═══════════════════════════════════════════
// Profile Model (One-to-One)
// ═══════════════════════════════════════════

model Profile {
  id        String   @id @default(cuid())
  bio       String?  @db.Text
  website   String?
  location  String?

  // Social links
  twitter   String?
  github    String?
  linkedin  String?

  // One-to-One with User
  userId    String   @unique
  user      User     @relation(fields: [userId], references: [id], onDelete: Cascade)

  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
}

// ═══════════════════════════════════════════
// Post Model (One-to-Many)
// ═══════════════════════════════════════════

model Post {
  id          String     @id @default(cuid())
  title       String
  slug        String     @unique
  content     String     @db.Text
  excerpt     String?
  published   Boolean    @default(false)
  featured    Boolean    @default(false)
  views       Int        @default(0)

  // Relations
  authorId    String
  author      User       @relation(fields: [authorId], references: [id], onDelete: Cascade)

  categories  Category[]
  tags        Tag[]
  comments    Comment[]

  // Timestamps
  createdAt   DateTime   @default(now())
  updatedAt   DateTime   @updatedAt
  publishedAt DateTime?

  // Indexes
  @@index([authorId])
  @@index([published])
  @@index([slug])
  @@index([createdAt])
  @@index([authorId, published])
}

// ═══════════════════════════════════════════
// Comment Model (Nested)
// ═══════════════════════════════════════════

model Comment {
  id        String    @id @default(cuid())
  content   String    @db.Text

  // Relations
  postId    String
  post      Post      @relation(fields: [postId], references: [id], onDelete: Cascade)

  authorId  String
  author    User      @relation(fields: [authorId], references: [id], onDelete: Cascade)

  // Self-referencing (nested comments)
  parentId  String?
  parent    Comment?  @relation("CommentReplies", fields: [parentId], references: [id], onDelete: Cascade)
  replies   Comment[] @relation("CommentReplies")

  createdAt DateTime  @default(now())
  updatedAt DateTime  @updatedAt

  @@index([postId])
  @@index([authorId])
  @@index([parentId])
}

// ═══════════════════════════════════════════
// Many-to-Many Relations
// ═══════════════════════════════════════════

model Category {
  id        String   @id @default(cuid())
  name      String   @unique
  slug      String   @unique
  posts     Post[]

  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt

  @@index([slug])
}

model Tag {
  id        String   @id @default(cuid())
  name      String   @unique
  slug      String   @unique
  posts     Post[]

  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt

  @@index([slug])
}

// ═══════════════════════════════════════════
// Session Model (for auth)
// ═══════════════════════════════════════════

model Session {
  id        String   @id @default(cuid())
  token     String   @unique
  userId    String
  user      User     @relation(fields: [userId], references: [id], onDelete: Cascade)
  expiresAt DateTime

  createdAt DateTime @default(now())

  @@index([userId])
  @@index([token])
  @@index([expiresAt])
}

// ═══════════════════════════════════════════
// Enums
// ═══════════════════════════════════════════

enum Role {
  USER
  MODERATOR
  ADMIN
  SUPER_ADMIN
}
```

```javascript
// ═══════════════════════════════════════════
// Prisma Client Setup
// ═══════════════════════════════════════════

import { PrismaClient } from '@prisma/client';

// Singleton pattern
const globalForPrisma = global as unknown as { prisma: PrismaClient };

export const prisma = globalForPrisma.prisma || new PrismaClient({
  log: process.env.NODE_ENV === 'development'
    ? ['query', 'error', 'warn']
    : ['error'],
});

if (process.env.NODE_ENV !== 'production') {
  globalForPrisma.prisma = prisma;
}

// Graceful shutdown
process.on('beforeExit', async () => {
  await prisma.$disconnect();
});

// ═══════════════════════════════════════════
// CRUD Operations
// ═══════════════════════════════════════════

// Create
const user = await prisma.user.create({
  data: {
    email: 'user@example.com',
    name: 'John Doe',
    password: hashedPassword,
    profile: {
      create: {
        bio: 'Developer',
        website: 'https://example.com',
      },
    },
  },
  include: {
    profile: true,
  },
});

// Read (Find Many)
const users = await prisma.user.findMany({
  where: {
    role: 'USER',
    emailVerified: true,
  },
  select: {
    id: true,
    name: true,
    email: true,
    _count: {
      select: {
        posts: true,
      },
    },
  },
  orderBy: {
    createdAt: 'desc',
  },
  skip: 0,
  take: 10,
});

// Read (Find Unique)
const user = await prisma.user.findUnique({
  where: { email: 'user@example.com' },
  include: {
    profile: true,
    posts: {
      where: { published: true },
      orderBy: { createdAt: 'desc' },
      take: 5,
    },
  },
});

// Update
const updated = await prisma.user.update({
  where: { id: userId },
  data: {
    name: 'Updated Name',
    profile: {
      update: {
        bio: 'New bio',
      },
    },
  },
});

// Upsert (Create or Update)
const user = await prisma.user.upsert({
  where: { email: 'user@example.com' },
  update: {
    name: 'Updated Name',
  },
  create: {
    email: 'user@example.com',
    name: 'New User',
    password: hashedPassword,
  },
});

// Delete
await prisma.user.delete({
  where: { id: userId },
});

// Delete Many
await prisma.post.deleteMany({
  where: {
    published: false,
    createdAt: {
      lt: new Date('2024-01-01'),
    },
  },
});

// ═══════════════════════════════════════════
// Advanced Queries
// ═══════════════════════════════════════════

// Complex filtering
const posts = await prisma.post.findMany({
  where: {
    AND: [
      { published: true },
      {
        OR: [
          { title: { contains: 'prisma', mode: 'insensitive' } },
          { content: { contains: 'prisma', mode: 'insensitive' } },
        ],
      },
      {
        categories: {
          some: {
            name: { in: ['Technology', 'Tutorial'] },
          },
        },
      },
      {
        author: {
          role: { not: 'ADMIN' },
        },
      },
    ],
  },
  include: {
    author: {
      select: {
        name: true,
        email: true,
      },
    },
    categories: true,
    tags: true,
    _count: {
      select: {
        comments: true,
      },
    },
  },
  orderBy: [
    { featured: 'desc' },
    { views: 'desc' },
    { createdAt: 'desc' },
  ],
});

// Aggregations
const stats = await prisma.post.aggregate({
  where: { published: true },
  _count: true,
  _avg: { views: true },
  _sum: { views: true },
  _max: { views: true },
  _min: { views: true },
});

// Group By
const postsByAuthor = await prisma.post.groupBy({
  by: ['authorId'],
  where: { published: true },
  _count: {
    id: true,
  },
  _avg: {
    views: true,
  },
  having: {
    views: {
      _avg: {
        gt: 100,
      },
    },
  },
});

// ═══════════════════════════════════════════
// Transactions
// ═══════════════════════════════════════════

// Sequential operations (all or nothing)
const [user, post] = await prisma.$transaction([
  prisma.user.create({ data: userData }),
  prisma.post.create({ data: postData }),
]);

// Interactive transactions
await prisma.$transaction(async (tx) => {
  const user = await tx.user.create({ data: userData });

  const post = await tx.post.create({
    data: {
      ...postData,
      authorId: user.id,
    },
  });

  // Increment user's post count
  await tx.user.update({
    where: { id: user.id },
    data: {
      // Custom logic here
    },
  });
});

// ═══════════════════════════════════════════
// Raw SQL (when needed)
// ═══════════════════════════════════════════

// Raw query
const users = await prisma.$queryRaw`
  SELECT u.*, COUNT(p.id) as post_count
  FROM "User" u
  LEFT JOIN "Post" p ON u.id = p."authorId"
  GROUP BY u.id
  HAVING COUNT(p.id) > 5
  ORDER BY post_count DESC
`;

// Execute raw
await prisma.$executeRaw`
  UPDATE "Post"
  SET views = views + 1
  WHERE id = ${postId}
`;

// ═══════════════════════════════════════════
// Pagination Helper
// ═══════════════════════════════════════════

async function paginate(model, { page = 1, limit = 10, where = {}, orderBy = {} }) {
  const skip = (page - 1) * limit;

  const [data, total] = await Promise.all([
    prisma[model].findMany({
      where,
      orderBy,
      skip,
      take: limit,
    }),
    prisma[model].count({ where }),
  ]);

  return {
    data,
    pagination: {
      page,
      limit,
      total,
      totalPages: Math.ceil(total / limit),
      hasNext: page < Math.ceil(total / limit),
      hasPrev: page > 1,
    },
  };
}

// Usage
const result = await paginate('post', {
  page: 2,
  limit: 20,
  where: { published: true },
  orderBy: { createdAt: 'desc' },
});
```

**📦 Prisma Resources:**

- Docs: https://www.prisma.io/docs
- Studio: https://www.prisma.io/studio (GUI for your database)
- Playground: https://playground.prisma.io/

> **💡 Pro Tip:** Prisma is type-safe by default! Your database schema becomes TypeScript types. Use Prisma Studio to visually explore and edit your data!

---

<div align="center">

## 🍃 MongoDB & Mongoose

</div>

### Document Database with Mongoose 📄

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install mongoose
```

```javascript
// ═══════════════════════════════════════════
// MongoDB Connection
// ═══════════════════════════════════════════

import mongoose from "mongoose";

const connectDB = async () => {
  try {
    await mongoose.connect(process.env.MONGODB_URI, {
      // No longer needed in Mongoose 6+
      // useNewUrlParser: true,
      // useUnifiedTopology: true,
    });

    console.log("MongoDB connected successfully");
  } catch (error) {
    console.error("MongoDB connection error:", error);
    process.exit(1);
  }
};

// Connection events
mongoose.connection.on("connected", () => {
  console.log("Mongoose connected to MongoDB");
});

mongoose.connection.on("error", (err) => {
  console.error("Mongoose connection error:", err);
});

mongoose.connection.on("disconnected", () => {
  console.log("Mongoose disconnected");
});

// Graceful shutdown
process.on("SIGINT", async () => {
  await mongoose.connection.close();
  process.exit(0);
});

export default connectDB;

// ═══════════════════════════════════════════
// User Model
// ═══════════════════════════════════════════

import mongoose from "mongoose";
import bcrypt from "bcryptjs";

const userSchema = new mongoose.Schema(
  {
    email: {
      type: String,
      required: [true, "Email is required"],
      unique: true,
      lowercase: true,
      trim: true,
      match: [/^\S+@\S+\.\S+$/, "Please enter a valid email"],
    },
    name: {
      type: String,
      required: [true, "Name is required"],
      trim: true,
      minlength: [2, "Name must be at least 2 characters"],
      maxlength: [100, "Name cannot exceed 100 characters"],
    },
    password: {
      type: String,
      required: [true, "Password is required"],
      minlength: [8, "Password must be at least 8 characters"],
      select: false, // Don't return password by default
    },
    role: {
      type: String,
      enum: ["user", "moderator", "admin"],
      default: "user",
    },
    avatar: {
      type: String,
      default: null,
    },
    emailVerified: {
      type: Boolean,
      default: false,
    },
    profile: {
      bio: {
        type: String,
        maxlength: [500, "Bio cannot exceed 500 characters"],
      },
      website: String,
      location: String,
      socials: {
        twitter: String,
        github: String,
        linkedin: String,
      },
    },
    posts: [
      {
        type: mongoose.Schema.Types.ObjectId,
        ref: "Post",
      },
    ],
    lastLogin: Date,
  },
  {
    timestamps: true, // createdAt, updatedAt
    toJSON: { virtuals: true },
    toObject: { virtuals: true },
  }
);

// ═══════════════════════════════════════════
// Indexes
// ═══════════════════════════════════════════

userSchema.index({ email: 1 });
userSchema.index({ role: 1 });
userSchema.index({ createdAt: -1 });
userSchema.index({ email: 1, role: 1 }); // Compound index

// Text search index
userSchema.index({ name: "text", "profile.bio": "text" });

// ═══════════════════════════════════════════
// Virtual Fields
// ═══════════════════════════════════════════

userSchema.virtual("postCount").get(function () {
  return this.posts.length;
});

userSchema.virtual("fullProfile").get(function () {
  return {
    name: this.name,
    email: this.email,
    avatar: this.avatar,
    ...this.profile,
  };
});

// ═══════════════════════════════════════════
// Instance Methods
// ═══════════════════════════════════════════

userSchema.methods.comparePassword = async function (candidatePassword) {
  return bcrypt.compare(candidatePassword, this.password);
};

userSchema.methods.generateAuthToken = function () {
  return jwt.sign(
    { id: this._id, email: this.email, role: this.role },
    process.env.JWT_SECRET,
    { expiresIn: "7d" }
  );
};

userSchema.methods.toPublicJSON = function () {
  const user = this.toObject();
  delete user.password;
  return user;
};

// ═══════════════════════════════════════════
// Static Methods
// ═══════════════════════════════════════════

userSchema.statics.findByEmail = function (email) {
  return this.findOne({ email: email.toLowerCase() });
};

userSchema.statics.findActiveUsers = function () {
  return this.find({
    emailVerified: true,
    lastLogin: { $gte: new Date(Date.now() - 30 * 24 * 60 * 60 * 1000) },
  });
};

// ═══════════════════════════════════════════
// Middleware (Hooks)
// ═══════════════════════════════════════════

// Pre-save: Hash password
userSchema.pre("save", async function (next) {
  if (!this.isModified("password")) return next();

  try {
    const salt = await bcrypt.genSalt(12);
    this.password = await bcrypt.hash(this.password, salt);
    next();
  } catch (error) {
    next(error);
  }
});

// Pre-save: Update timestamps
userSchema.pre("save", function (next) {
  this.updatedAt = new Date();
  next();
});

// Post-save: Log creation
userSchema.post("save", function (doc) {
  console.log(`User created: ${doc.email}`);
});

// Pre-remove: Cascade delete
userSchema.pre("remove", async function (next) {
  await mongoose.model("Post").deleteMany({ author: this._id });
  next();
});

export const User = mongoose.model("User", userSchema);

// ═══════════════════════════════════════════
// Usage Examples
// ═══════════════════════════════════════════

// Create
const user = await User.create({
  email: "user@example.com",
  name: "John Doe",
  password: "securepassword123",
  profile: {
    bio: "Developer",
    website: "https://example.com",
  },
});

// Find with population
const users = await User.find({ role: "user" })
  .populate("posts", "title createdAt")
  .select("-password")
  .sort("-createdAt")
  .limit(10);

// Find one
const user = await User.findOne({ email: "user@example.com" }).select(
  "+password"
); // Include password field

// Update
const updated = await User.findByIdAndUpdate(
  userId,
  { $set: { name: "New Name" } },
  { new: true, runValidators: true }
);

// Increment
await User.findByIdAndUpdate(userId, { $inc: { "profile.views": 1 } });

// Push to array
await User.findByIdAndUpdate(userId, { $push: { posts: postId } });

// Delete
await User.findByIdAndDelete(userId);

// Aggregation
const stats = await User.aggregate([
  { $match: { role: "user" } },
  {
    $group: {
      _id: "$role",
      count: { $sum: 1 },
      avgPosts: { $avg: { $size: "$posts" } },
    },
  },
]);

// Text search
const results = await User.find({
  $text: { $search: "developer javascript" },
});
```

**📦 Mongoose Resources:**

- Docs: https://mongoosejs.com/docs/
- MongoDB University: https://university.mongodb.com/

> **💡 Pro Tip:** Use Mongoose middleware (hooks) for business logic like password hashing, cascading deletes, and logging. Always index frequently queried fields!

---

<div align="center">

## 🚀 Redis Caching

</div>

### High-Performance Caching Layer ⚡

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install redis
npm install ioredis  # Alternative client (recommended)
```

```javascript
// ═══════════════════════════════════════════
# Redis Client Setup
// ═══════════════════════════════════════════

import Redis from 'ioredis';

const redis = new Redis({
  host: process.env.REDIS_HOST || 'localhost',
  port: process.env.REDIS_PORT || 6379,
  password: process.env.REDIS_PASSWORD,
  db: 0,
  retryStrategy: (times) => {
    const delay = Math.min(times * 50, 2000);
    return delay;
  },
});

redis.on('connect', () => {
  console.log('Redis connected');
});

redis.on('error', (err) => {
  console.error('Redis error:', err);
});

export default redis;

// ═══════════════════════════════════════════
// Cache Service
// ═══════════════════════════════════════════

class CacheService {
  constructor(redisClient) {
    this.redis = redisClient;
    this.defaultTTL = 3600; // 1 hour
  }

  // ═══════════════════════════════════════════
  // Basic Operations
  // ═══════════════════════════════════════════

  async get(key) {
    try {
      const value = await this.redis.get(key);
      return value ? JSON.parse(value) : null;
    } catch (error) {
      console.error('Cache get error:', error);
      return null;
    }
  }

  async set(key, value, ttl = this.defaultTTL) {
    try {
      await this.redis.setex(
        key,
        ttl,
        JSON.stringify(value)
      );
      return true;
    } catch (error) {
      console.error('Cache set error:', error);
      return false;
    }
  }

  async del(key) {
    try {
      await this.redis.del(key);
      return true;
    } catch (error) {
      console.error('Cache delete error:', error);
      return false;
    }
  }

  async exists(key) {
    return await this.redis.exists(key);
  }

  async expire(key, ttl) {
    return await this.redis.expire(key, ttl);
  }

  async ttl(key) {
    return await this.redis.ttl(key);
  }

  // ═══════════════════════════════════════════
  // Pattern-Based Operations
  // ═══════════════════════════════════════════

  async invalidatePattern(pattern) {
    try {
      const keys = await this.redis.keys(pattern);
      if (keys.length > 0) {
        await this.redis.del(...keys);
      }
      return keys.length;
    } catch (error) {
      console.error('Pattern invalidation error:', error);
      return 0;
    }
  }

  // ═══════════════════════════════════════════
  // Cache with Tags
  // ═══════════════════════════════════════════

  async setWithTags(key, value, tags = [], ttl = this.defaultTTL) {
    try {
      // Store the value
      await this.set(key, value, ttl);

      // Associate with tags
      for (const tag of tags) {
        await this.redis.sadd(`tag:${tag}`, key);
        await this.redis.expire(`tag:${tag}`, ttl);
      }

      return true;
    } catch (error) {
      console.error('Cache with tags error:', error);
      return false;
    }
  }

  async invalidateTag(tag) {
    try {
      const keys = await this.redis.smembers(`tag:${tag}`);

      if (keys.length > 0) {
        await this.redis.del(...keys);
        await this.redis.del(`tag:${tag}`);
      }

      return keys.length;
    } catch (error) {
      console.error('Tag invalidation error:', error);
      return 0;
    }
  }

  // ═══════════════════════════════════════════
  // Cache-Aside Pattern
  // ═══════════════════════════════════════════

  async remember(key, fetchFn, ttl = this.defaultTTL) {
    // Try to get from cache
    let value = await this.get(key);

    if (value !== null) {
      return value;
    }

    // Fetch from source
    value = await fetchFn();

    // Store in cache
    await this.set(key, value, ttl);

    return value;
  }

  // ═══════════════════════════════════════════
  // Increment/Decrement
  // ═══════════════════════════════════════════

  async increment(key, amount = 1) {
    return await this.redis.incrby(key, amount);
  }

  async decrement(key, amount = 1) {
    return await this.redis.decrby(key, amount);
  }

  // ═══════════════════════════════════════════
  // List Operations
  // ═══════════════════════════════════════════

  async lpush(key, ...values) {
    return await this.redis.lpush(key, ...values.map(v => JSON.stringify(v)));
  }

  async rpush(key, ...values) {
    return await this.redis.rpush(key, ...values.map(v => JSON.stringify(v)));
  }

  async lrange(key, start, stop) {
    const values = await this.redis.lrange(key, start, stop);
    return values.map(v => JSON.parse(v));
  }

  // ═══════════════════════════════════════════
  // Set Operations
  // ═══════════════════════════════════════════

  async sadd(key, ...members) {
    return await this.redis.sadd(key, ...members);
  }

  async smembers(key) {
    return await this.redis.smembers(key);
  }

  async sismember(key, member) {
    return await this.redis.sismember(key, member);
  }
}

export const cacheService = new CacheService(redis);

// ═══════════════════════════════════════════
// Cache Middleware
// ═══════════════════════════════════════════

export const cacheMiddleware = (duration = 300) => {
  return async (req, res, next) => {
    // Only cache GET requests
    if (req.method !== 'GET') {
      return next();
    }

    const key = `cache:${req.originalUrl || req.url}`;

    try {
      const cached = await cacheService.get(key);

      if (cached) {
        return res.json(cached);
      }

      // Override res.json to cache the response
      const originalJson = res.json.bind(res);

      res.json = (data) => {
        cacheService.set(key, data, duration);
        return originalJson(data);
      };

      next();
    } catch (error) {
      console.error('Cache middleware error:', error);
      next();
    }
  };
};

// ═══════════════════════════════════════════
// Usage Examples
// ═══════════════════════════════════════════

// Simple caching
router.get('/users', cacheMiddleware(600), async (req, res) => {
  const users = await db.user.findMany();
  res.json({ data: users });
});

// Cache-aside pattern
async function getUser(userId) {
  return await cacheService.remember(
    `user:${userId}`,
    async () => {
      return await db.user.findUnique({ where: { id: userId } });
    },
    3600 // Cache for 1 hour
  );
}

// Invalidate cache on update
router.put('/users/:id', async (req, res) => {
  const user = await db.user.update({
    where: { id: req.params.id },
    data: req.body,
  });

  // Invalidate user cache
  await cacheService.del(`user:${req.params.id}`);

  // Invalidate list cache
  await cacheService.invalidatePattern('cache:/api/users*');

  res.json({ data: user });
});

// Rate limiting with Redis
async function checkRateLimit(userId, limit = 100, window = 60) {
  const key = `ratelimit:${userId}`;
  const current = await redis.incr(key);

  if (current === 1) {
    await redis.expire(key, window);
  }

  if (current > limit) {
    throw new Error('Rate limit exceeded');
  }

  return {
    remaining: limit - current,
    resetIn: await redis.ttl(key),
  };
}
```

**📦 Redis Resources:**

- Docs: https://redis.io/docs/
- ioredis: https://github.com/luin/ioredis

> **💡 Pro Tip:** Use Redis for caching, rate limiting, sessions, and pub/sub. Perfect for high-traffic applications. Remember to set TTL on all cached data!

<div align="center">

## 🔄 Database Migrations

</div>

### Managing Schema Changes 📝

```bash
# ═══════════════════════════════════════════
# Prisma Migrations
# ═══════════════════════════════════════════

# Create migration from schema changes
npx prisma migrate dev --name add_user_fields

# Apply migrations in production
npx prisma migrate deploy

# Reset database (development only!)
npx prisma migrate reset

# View migration status
npx prisma migrate status

# Create migration without applying
npx prisma migrate dev --create-only

# Generate Prisma Client after schema changes
npx prisma generate

# Open Prisma Studio (GUI)
npx prisma studio
```

```javascript
// ═══════════════════════════════════════════
// Migration Best Practices
// ═══════════════════════════════════════════

/*
1. Always test migrations in development first
2. Backup production database before migrating
3. Use migrations for schema changes, not data
4. Keep migrations small and focused
5. Never modify applied migrations
6. Use descriptive migration names
7. Review SQL before deploying
*/

// ═══════════════════════════════════════════
// Data Migration Example
// ═══════════════════════════════════════════

// migrations/20240101_migrate_user_roles.ts
import { PrismaClient } from "@prisma/client";

const prisma = new PrismaClient();

async function migrateUserRoles() {
  console.log("Starting user role migration...");

  try {
    // Get all users with old role system
    const users = await prisma.user.findMany({
      where: {
        oldRole: { not: null },
      },
    });

    console.log(`Found ${users.length} users to migrate`);

    // Migrate in batches
    const batchSize = 100;
    for (let i = 0; i < users.length; i += batchSize) {
      const batch = users.slice(i, i + batchSize);

      await prisma.$transaction(
        batch.map((user) =>
          prisma.user.update({
            where: { id: user.id },
            data: {
              role: mapOldRoleToNew(user.oldRole),
              oldRole: null, // Remove old field
            },
          })
        )
      );

      console.log(
        `Migrated ${Math.min(i + batchSize, users.length)} / ${users.length}`
      );
    }

    console.log("Migration completed successfully!");
  } catch (error) {
    console.error("Migration failed:", error);
    throw error;
  } finally {
    await prisma.$disconnect();
  }
}

function mapOldRoleToNew(oldRole) {
  const mapping = {
    basic: "USER",
    premium: "USER",
    mod: "MODERATOR",
    admin: "ADMIN",
  };
  return mapping[oldRole] || "USER";
}

// Run migration
migrateUserRoles();
```

---

<div align="center">

## 📊 Query Optimization

</div>

### Making Queries Fast ⚡

```javascript
// ═══════════════════════════════════════════
// Indexing Strategies
// ═══════════════════════════════════════════

/*
Prisma Schema Indexes:
*/

model User {
  id        String   @id @default(cuid())
  email     String   @unique  // Automatic unique index
  name      String
  role      Role
  createdAt DateTime @default(now())

  // Single-column indexes
  @@index([email])
  @@index([createdAt])

  // Compound indexes (order matters!)
  @@index([role, createdAt])
  @@index([createdAt, role])  // Different from above!

  // Partial index (PostgreSQL)
  @@index([email], name: "active_users_email", where: "deleted_at IS NULL")
}

/*
When to create indexes:
✅ Foreign keys
✅ Columns in WHERE clauses
✅ Columns in ORDER BY
✅ Columns in JOIN conditions
✅ Columns frequently searched

❌ Don't index:
- Small tables (< 1000 rows)
- Columns rarely queried
- Columns with low cardinality (few unique values)
- Write-heavy tables (indexes slow writes)
*/

// ═══════════════════════════════════════════
// Query Optimization Techniques
// ═══════════════════════════════════════════

// ❌ BAD: N+1 Query Problem
const users = await prisma.user.findMany();
for (const user of users) {
  // This creates N additional queries!
  const posts = await prisma.post.findMany({
    where: { authorId: user.id },
  });
}

// ✅ GOOD: Use includes/select
const users = await prisma.user.findMany({
  include: {
    posts: true, // Single query with JOIN
  },
});

// ✅ BETTER: Only select needed fields
const users = await prisma.user.findMany({
  select: {
    id: true,
    name: true,
    email: true,
    posts: {
      select: {
        id: true,
        title: true,
      },
      where: { published: true },
      take: 5,
    },
  },
});

// ═══════════════════════════════════════════
// Pagination Best Practices
// ═══════════════════════════════════════════

// ❌ BAD: Offset pagination for large datasets
// Performance degrades with higher page numbers
const posts = await prisma.post.findMany({
  skip: page * limit,  // Gets slower as page increases!
  take: limit,
});

// ✅ GOOD: Cursor-based pagination
const posts = await prisma.post.findMany({
  take: limit,
  skip: cursor ? 1 : 0,
  cursor: cursor ? { id: cursor } : undefined,
  orderBy: { createdAt: 'desc' },
});

const nextCursor = posts.length === limit
  ? posts[posts.length - 1].id
  : null;

// ═══════════════════════════════════════════
// Batch Operations
// ═══════════════════════════════════════════

// ❌ BAD: Multiple individual queries
for (const email of emails) {
  await prisma.user.create({ data: { email } });
}

// ✅ GOOD: Batch create
await prisma.user.createMany({
  data: emails.map(email => ({ email })),
  skipDuplicates: true,
});

// ❌ BAD: Loading all data into memory
const allUsers = await prisma.user.findMany();
allUsers.forEach(user => {
  // Process user
});

// ✅ GOOD: Process in batches
const batchSize = 1000;
let cursor = null;

while (true) {
  const users = await prisma.user.findMany({
    take: batchSize,
    skip: cursor ? 1 : 0,
    cursor: cursor ? { id: cursor } : undefined,
  });

  if (users.length === 0) break;

  for (const user of users) {
    // Process user
  }

  cursor = users[users.length - 1].id;
}

// ═══════════════════════════════════════════
// Query Analysis
// ═══════════════════════════════════════════

// Enable query logging in Prisma
const prisma = new PrismaClient({
  log: [
    { emit: 'event', level: 'query' },
    { emit: 'stdout', level: 'error' },
    { emit: 'stdout', level: 'warn' },
  ],
});

prisma.$on('query', (e) => {
  console.log('Query:', e.query);
  console.log('Duration:', e.duration, 'ms');
});

// Explain query (PostgreSQL)
const result = await prisma.$queryRaw`
  EXPLAIN ANALYZE
  SELECT * FROM "User"
  WHERE email = 'user@example.com';
`;

// ═══════════════════════════════════════════
// Caching Strategies
// ═══════════════════════════════════════════

class DatabaseService {
  async getUserWithCache(userId) {
    // Try cache first
    const cached = await cacheService.get(`user:${userId}`);
    if (cached) return cached;

    // Query database
    const user = await prisma.user.findUnique({
      where: { id: userId },
      include: { profile: true },
    });

    // Cache result
    if (user) {
      await cacheService.set(`user:${userId}`, user, 3600);
    }

    return user;
  }

  async updateUser(userId, data) {
    const user = await prisma.user.update({
      where: { id: userId },
      data,
    });

    // Invalidate cache
    await cacheService.del(`user:${userId}`);

    return user;
  }
}

// ═══════════════════════════════════════════
// Connection Pooling
// ═══════════════════════════════════════════

// Prisma handles connection pooling automatically
// Configure in DATABASE_URL:

/*
postgresql://user:password@localhost:5432/mydb?connection_limit=10

Options:
- connection_limit: Max connections (default: unlimited)
- pool_timeout: Wait time for connection (default: 10s)
- connect_timeout: Connection timeout (default: 5s)
*/

// For serverless (Vercel, AWS Lambda)
// Use connection pooler like PgBouncer or Supabase Pooler

/*
postgresql://user:password@pooler.supabase.com:6543/postgres?pgbouncer=true
*/
```

> **💡 Pro Tip:** Use `EXPLAIN ANALYZE` to understand query performance. Create indexes on frequently queried columns. Use cursor-based pagination for large datasets!

---

<div align="center">

## 🔐 Database Security

</div>

### Protecting Your Data 🛡️

```javascript
// ═══════════════════════════════════════════
// 1. SQL Injection Prevention
// ═══════════════════════════════════════════

// ❌ DANGEROUS: Never concatenate user input!
const userId = req.params.id;
const query = `SELECT * FROM users WHERE id = '${userId}'`;
// Attacker can input: ' OR '1'='1

// ✅ SAFE: Use parameterized queries
const user = await prisma.user.findUnique({
  where: { id: userId }, // Prisma sanitizes this
});

// ✅ SAFE: Even with raw queries
const users = await prisma.$queryRaw`
  SELECT * FROM "User"
  WHERE email = ${userEmail}
`; // Prisma uses parameterized queries

// ═══════════════════════════════════════════
// 2. Access Control
// ═══════════════════════════════════════════

// Row-Level Security (RLS) in PostgreSQL
/*
-- Enable RLS
ALTER TABLE posts ENABLE ROW LEVEL SECURITY;

-- Policy: Users can only see their own posts
CREATE POLICY user_posts_policy ON posts
  FOR SELECT
  USING (author_id = current_user_id());

-- Policy: Admins can see all posts
CREATE POLICY admin_posts_policy ON posts
  FOR SELECT
  USING (
    EXISTS (
      SELECT 1 FROM users
      WHERE id = current_user_id()
      AND role = 'admin'
    )
  );
*/

// Application-level access control
async function getUserPosts(userId, requestingUserId, requestingUserRole) {
  const where = {};

  // Non-admins can only see their own posts
  if (requestingUserRole !== 'admin') {
    if (userId !== requestingUserId) {
      throw new Error('Unauthorized');
    }
    where.authorId = userId;
  } else {
    // Admins can see anyone's posts
    where.authorId = userId;
  }

  return prisma.post.findMany({ where });
}

// ═══════════════════════════════════════════
// 3. Sensitive Data Protection
// ═══════════════════════════════════════════

// Always exclude sensitive fields by default
model User {
  id       String @id
  email    String
  password String // Never return this!
  ssn      String? // Encrypt at rest
}

// Use select or omit
const user = await prisma.user.findUnique({
  where: { id: userId },
  select: {
    id: true,
    email: true,
    name: true,
    // password explicitly excluded
  },
});

// Helper function
function sanitizeUser(user) {
  const { password, ssn, ...safe } = user;
  return safe;
}

// ═══════════════════════════════════════════
// 4. Encryption at Rest
// ═══════════════════════════════════════════

import crypto from 'crypto';

const ENCRYPTION_KEY = process.env.ENCRYPTION_KEY; // 32 bytes
const IV_LENGTH = 16;

function encrypt(text) {
  const iv = crypto.randomBytes(IV_LENGTH);
  const cipher = crypto.createCipheriv(
    'aes-256-cbc',
    Buffer.from(ENCRYPTION_KEY, 'hex'),
    iv
  );

  let encrypted = cipher.update(text, 'utf8', 'hex');
  encrypted += cipher.final('hex');

  return iv.toString('hex') + ':' + encrypted;
}

function decrypt(text) {
  const parts = text.split(':');
  const iv = Buffer.from(parts.shift(), 'hex');
  const encryptedText = parts.join(':');

  const decipher = crypto.createDecipheriv(
    'aes-256-cbc',
    Buffer.from(ENCRYPTION_KEY, 'hex'),
    iv
  );

  let decrypted = decipher.update(encryptedText, 'hex', 'utf8');
  decrypted += decipher.final('utf8');

  return decrypted;
}

// Use for sensitive fields
async function storeUserSSN(userId, ssn) {
  const encryptedSSN = encrypt(ssn);

  await prisma.user.update({
    where: { id: userId },
    data: { ssn: encryptedSSN },
  });
}

// ═══════════════════════════════════════════
// 5. Database Credentials
// ═══════════════════════════════════════════

/*
✅ DO:
- Store in environment variables
- Use secrets manager (AWS Secrets Manager, HashiCorp Vault)
- Rotate credentials regularly
- Use read-only replicas when possible
- Implement connection encryption (SSL/TLS)

❌ DON'T:
- Commit credentials to git
- Use default passwords
- Share credentials in plain text
- Use same credentials for all environments
*/

// Environment-based configuration
const getDatabaseUrl = () => {
  const env = process.env.NODE_ENV;

  switch (env) {
    case 'production':
      return process.env.DATABASE_URL_PROD;
    case 'staging':
      return process.env.DATABASE_URL_STAGING;
    default:
      return process.env.DATABASE_URL_DEV;
  }
};

// SSL/TLS connection
/*
DATABASE_URL="postgresql://user:pass@host:5432/db?sslmode=require"
*/

// ═══════════════════════════════════════════
// 6. Audit Logging
// ═══════════════════════════════════════════

model AuditLog {
  id        String   @id @default(cuid())
  userId    String?
  action    String
  table     String
  recordId  String?
  changes   Json?
  ip        String?
  userAgent String?
  createdAt DateTime @default(now())

  @@index([userId])
  @@index([table])
  @@index([createdAt])
}

async function logDatabaseAction(action, userId, table, recordId, changes) {
  await prisma.auditLog.create({
    data: {
      action,
      userId,
      table,
      recordId,
      changes,
      ip: req.ip,
      userAgent: req.headers['user-agent'],
    },
  });
}

// Middleware to log all changes
prisma.$use(async (params, next) => {
  const result = await next(params);

  if (['create', 'update', 'delete'].includes(params.action)) {
    await logDatabaseAction(
      params.action,
      currentUser?.id,
      params.model,
      params.args.where?.id,
      params.args.data
    );
  }

  return result;
});

// ═══════════════════════════════════════════
// 7. Backups
// ═══════════════════════════════════════════

/*
Automated backup strategy:

1. Daily backups (keep 7 days)
2. Weekly backups (keep 4 weeks)
3. Monthly backups (keep 12 months)

PostgreSQL backup:
pg_dump -U username -d database > backup.sql

Restore:
psql -U username -d database < backup.sql

Cloud provider backups:
- AWS RDS: Automated backups
- Supabase: Point-in-time recovery
- DigitalOcean: Daily backups
*/
```

> **💡 Pro Tip:** Never store passwords in plain text! Use parameterized queries to prevent SQL injection. Encrypt sensitive data at rest. Always backup your database!

---

<div align="center">

## 💡 Best Practices

</div>

### Database Development Guidelines ⭐

```javascript
// ═══════════════════════════════════════════
// 1. Schema Design
// ═══════════════════════════════════════════

/*
✅ DO:
- Use meaningful table and column names
- Normalize data (avoid redundancy)
- Use appropriate data types
- Add timestamps (createdAt, updatedAt)
- Use foreign keys for relationships
- Add indexes on foreign keys
- Use soft deletes (deletedAt) when needed

❌ DON'T:
- Store JSON when relational would work
- Use VARCHAR(255) for everything
- Skip foreign key constraints
- Forget to add indexes
- Store calculated values
*/

// Good schema example
model Order {
  id          String      @id @default(cuid())
  orderNumber String      @unique
  status      OrderStatus @default(PENDING)
  total       Decimal     @db.Decimal(10, 2)

  customerId  String
  customer    User        @relation(fields: [customerId], references: [id])

  items       OrderItem[]

  createdAt   DateTime    @default(now())
  updatedAt   DateTime    @updatedAt
  deletedAt   DateTime?

  @@index([customerId])
  @@index([status])
  @@index([createdAt])
}

// ═══════════════════════════════════════════
// 2. Query Patterns
// ═══════════════════════════════════════════

// ✅ GOOD: Reusable query functions
class UserRepository {
  async findById(id) {
    return prisma.user.findUnique({
      where: { id },
      select: this.publicFields,
    });
  }

  async findByEmail(email) {
    return prisma.user.findUnique({
      where: { email },
    });
  }

  async list({ page = 1, limit = 10, role }) {
    const where = {};
    if (role) where.role = role;

    const [users, total] = await Promise.all([
      prisma.user.findMany({
        where,
        skip: (page - 1) * limit,
        take: limit,
        orderBy: { createdAt: 'desc' },
      }),
      prisma.user.count({ where }),
    ]);

    return {
      data: users,
      pagination: {
        page,
        limit,
        total,
        totalPages: Math.ceil(total / limit),
      },
    };

}

get publicFields() {
return {
id: true,
name: true,
email: true,
avatar: true,
role: true,
createdAt: true,
};
}
}

// ═══════════════════════════════════════════
// 3. Transaction Management
// ═══════════════════════════════════════════

// ✅ GOOD: Use transactions for related operations
async function transferMoney(fromUserId, toUserId, amount) {
return await prisma.$transaction(async (tx) => {
// Deduct from sender
const sender = await tx.account.update({
where: { userId: fromUserId },
data: { balance: { decrement: amount } },
});

    if (sender.balance < 0) {
      throw new Error('Insufficient funds');
    }

    // Add to receiver
    await tx.account.update({
      where: { userId: toUserId },
      data: { balance: { increment: amount } },
    });

    // Log transaction
    await tx.transaction.create({
      data: {
        fromUserId,
        toUserId,
        amount,
        type: 'TRANSFER',
      },
    });

    return true;

});
}

// ❌ BAD: Separate operations (not atomic)
async function transferMoneyBad(fromUserId, toUserId, amount) {
await prisma.account.update({
where: { userId: fromUserId },
data: { balance: { decrement: amount } },
});
// If this fails, money disappears! 💸
await prisma.account.update({
where: { userId: toUserId },
data: { balance: { increment: amount } },
});
}

// ═══════════════════════════════════════════
// 4. Error Handling
// ═══════════════════════════════════════════

// ✅ GOOD: Handle database errors properly
async function createUser(data) {
try {
const user = await prisma.user.create({ data });
return { success: true, user };
} catch (error) {
// Prisma error codes
if (error.code === 'P2002') {
// Unique constraint violation
return {
success: false,
error: 'Email already exists',
code: 'DUPLICATE_EMAIL',
};
}

    if (error.code === 'P2025') {
      // Record not found
      return {
        success: false,
        error: 'User not found',
        code: 'NOT_FOUND',
      };
    }

    // Log unexpected errors
    console.error('Database error:', error);

    return {
      success: false,
      error: 'Database error',
      code: 'DATABASE_ERROR',
    };

}
}

// Common Prisma error codes
/_
P2002: Unique constraint violation
P2003: Foreign key constraint violation
P2025: Record not found
P2014: Relation violation
P2016: Query interpretation error
_/

// ═══════════════════════════════════════════
// 5. Data Validation
// ═══════════════════════════════════════════

// ✅ GOOD: Validate before database operations
import { z } from 'zod';

const userSchema = z.object({
email: z.string().email(),
name: z.string().min(2).max(100),
age: z.number().int().min(0).max(150).optional(),
});

async function createUserSafe(data) {
// Validate input
const validated = userSchema.parse(data);

// Check business rules
const existingUser = await prisma.user.findUnique({
where: { email: validated.email },
});

if (existingUser) {
throw new Error('Email already exists');
}

// Create user
return await prisma.user.create({
data: validated,
});
}

// ═══════════════════════════════════════════
// 6. Performance Monitoring
// ═══════════════════════════════════════════

// Track slow queries
prisma.$use(async (params, next) => {
const start = Date.now();
const result = await next(params);
const duration = Date.now() - start;

// Log slow queries
if (duration > 1000) {
console.warn(`Slow query detected (${duration}ms):`, {
model: params.model,
action: params.action,
args: params.args,
});
}

return result;
});

// ═══════════════════════════════════════════
// 7. Testing
// ═══════════════════════════════════════════

// Use separate test database
// .env.test
/_
DATABASE_URL="postgresql://user:pass@localhost:5432/myapp_test"
_/

// Setup test database
import { PrismaClient } from '@prisma/client';

let prisma: PrismaClient;

beforeAll(async () => {
prisma = new PrismaClient();
await prisma.$connect();
});

afterAll(async () => {
await prisma.$disconnect();
});

beforeEach(async () => {
// Clean database before each test
await prisma.user.deleteMany();
await prisma.post.deleteMany();
});

// Test example
describe('User Repository', () => {
it('should create user', async () => {
const user = await prisma.user.create({
data: {
email: 'test@example.com',
name: 'Test User',
password: 'hashedPassword',
},
});

    expect(user).toBeDefined();
    expect(user.email).toBe('test@example.com');

});

it('should not create duplicate email', async () => {
await prisma.user.create({
data: {
email: 'test@example.com',
name: 'Test User',
password: 'hashedPassword',
},
});

    await expect(
      prisma.user.create({
        data: {
          email: 'test@example.com',
          name: 'Another User',
          password: 'hashedPassword',
        },
      })
    ).rejects.toThrow();

});
});

// ═══════════════════════════════════════════
// 8. Database Seeding
// ═══════════════════════════════════════════

// prisma/seed.ts
import { PrismaClient } from '@prisma/client';

const prisma = new PrismaClient();

async function main() {
console.log('Seeding database...');

// Create admin user
const admin = await prisma.user.upsert({
where: { email: 'admin@example.com' },
update: {},
create: {
email: 'admin@example.com',
name: 'Admin User',
password: await hashPassword('admin123'),
role: 'ADMIN',
},
});

console.log('Created admin:', admin);

// Create test users
for (let i = 1; i <= 10; i++) {
await prisma.user.create({
data: {
email: `user${i}@example.com`,
name: `Test User ${i}`,
password: await hashPassword('password123'),
role: 'USER',
},
});
}

console.log('Created 10 test users');

// Create sample posts
const users = await prisma.user.findMany();

for (const user of users) {
await prisma.post.create({
data: {
title: `Post by ${user.name}`,
content: 'Sample content',
authorId: user.id,
published: true,
},
});
}

console.log('Created sample posts');
console.log('Seeding completed!');
}

main()
.catch((e) => {
console.error(e);
process.exit(1);
})
.finally(async () => {
await prisma.$disconnect();
});

// Add to package.json:
/_
{
"prisma": {
"seed": "ts-node prisma/seed.ts"
}
}
_/

// Run seed:
// npx prisma db seed

// ═══════════════════════════════════════════
// 9. Environment-Specific Configurations
// ═══════════════════════════════════════════

// Development
/_
DATABASE_URL="postgresql://localhost:5432/myapp_dev"
_/

// Testing
/_
DATABASE_URL="postgresql://localhost:5432/myapp_test"
_/

// Staging
/_
DATABASE_URL="postgresql://staging-host:5432/myapp_staging?sslmode=require"
_/

// Production
/_
DATABASE_URL="postgresql://prod-host:5432/myapp_prod?sslmode=require&connection_limit=10"
_/

// ═══════════════════════════════════════════
// 10. Database Maintenance
// ═══════════════════════════════════════════

/\*
Regular maintenance tasks:

1. Monitor slow queries

   - Enable query logging
   - Analyze with EXPLAIN
   - Add missing indexes

2. Vacuum database (PostgreSQL)

   - Removes dead rows
   - Updates statistics
   - VACUUM ANALYZE;

3. Monitor database size

   - Check table sizes
   - Archive old data
   - Compress large tables

4. Update statistics

   - ANALYZE table_name;

5. Check and optimize indexes

   - Find unused indexes
   - Remove duplicate indexes
   - Reindex if needed

6. Monitor connection pool

   - Check active connections
   - Identify connection leaks
   - Optimize pool size

7. Review backup strategy

   - Test restores regularly
   - Verify backup integrity
   - Update retention policy

8. Security audits
   - Review user permissions
   - Check for SQL injection
   - Rotate credentials
     \*/
```

---

### Quick Reference 📋

```javascript
// ═══════════════════════════════════════════
// Prisma Client Cheat Sheet
// ═══════════════════════════════════════════

// CRUD Operations
prisma.model.create({ data: {} })
prisma.model.createMany({ data: [] })
prisma.model.findUnique({ where: {} })
prisma.model.findFirst({ where: {} })
prisma.model.findMany({ where: {} })
prisma.model.update({ where: {}, data: {} })
prisma.model.updateMany({ where: {}, data: {} })
prisma.model.upsert({ where: {}, create: {}, update: {} })
prisma.model.delete({ where: {} })
prisma.model.deleteMany({ where: {} })

// Aggregations
prisma.model.count({ where: {} })
prisma.model.aggregate({ _count: true, _sum: {}, _avg: {} })
prisma.model.groupBy({ by: [], _count: true })

// Filters
{ equals: value }
{ not: value }
{ in: [values] }
{ notIn: [values] }
{ lt: value }  // less than
{ lte: value } // less than or equal
{ gt: value }  // greater than
{ gte: value } // greater than or equal
{ contains: value }
{ startsWith: value }
{ endsWith: value }

// Logical operators
{ AND: [] }
{ OR: [] }
{ NOT: {} }

// Relations
{ include: { relation: true } }
{ select: { field: true } }
{ where: { relation: { some: {} } } }
{ where: { relation: { every: {} } } }
{ where: { relation: { none: {} } } }
```

---

<div align="center">

## 🎓 Database Selection Guide

### _Choose the Right Tool_ 🎯

</div>

```yaml
For E-commerce:
  Primary: PostgreSQL with Prisma
  Cache: Redis
  Why: ACID transactions, complex queries

For Social Media:
  Primary: PostgreSQL for users/auth
  Secondary: MongoDB for feeds/posts
  Cache: Redis
  Why: Mix of structured and unstructured data

For Real-time Apps:
  Primary: Firebase/Supabase
  Cache: Redis
  Why: Real-time sync, built-in auth

For Analytics:
  Primary: ClickHouse or TimescaleDB
  Cache: Redis
  Why: Time-series data, fast aggregations

For Content Management:
  Primary: MongoDB
  Cache: Redis
  Why: Flexible schema, document storage

MrDib's Recommended Stack:
  Database: PostgreSQL
  ORM: Prisma
  Cache: Redis (ioredis)
  Hosting: Supabase or Railway
  Why: Modern, type-safe, scalable
```

---

<div align="center">

**Built with 🗄️ by MrDib, for Data-Driven Developers**

_"A good database design is the foundation of a great application!"_

**Happy Data Managing!** 💾

**If you found this helpful, give it a ⭐ star and share with fellow developers!**

</div>

---

### Contributing 🤝

Found better database patterns? Want to add examples? Contributions are welcome!

1. Fork the repository
2. Add your database examples
3. Update best practices
4. Submit a pull request

---

### License 📄

This guide is open source and available under the MIT License.

---

<div align="center">

**Stay normalized. Keep querying. Build scalable!** 💪✨

🗄️ **#Databases** 🗄️ **#DevResourceVault** 🗄️ **#MrDib** 🗄️

### Remember

> _"Normalize until it hurts, denormalize until it works"_

> _"Index your queries, not your database"_

> _"Transactions save lives (and data integrity)"_

> _"Cache aggressively, invalidate wisely"_

> _"Backup everything, test restores regularly"_

</div>

---

<div align="center">

**Now go forth and build data-driven applications!** 🌟🗄️

</div>
