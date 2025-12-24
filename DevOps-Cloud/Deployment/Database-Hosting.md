<div align="center">

# 💾 Database Hosting - Complete Guide

### _Managed databases for production applications_ 🗄️

![Database](https://img.shields.io/badge/Database-Production%20Ready-purple?style=for-the-badge)
![Scale](https://img.shields.io/badge/Scale-Auto%20Scaling-green?style=for-the-badge)
![Reliable](https://img.shields.io/badge/Reliable-99.9%25%20Uptime-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Guide-Complete-gold?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 Choosing Your Database](#-choosing-your-database)
- [🐘 PostgreSQL Hosting](#-postgresql-hosting)
  - [Supabase](#-supabase)
  - [Neon](#-neon)
  - [Railway PostgreSQL](#-railway-postgresql)
  - [Render PostgreSQL](#-render-postgresql)
- [🐬 MySQL Hosting](#-mysql-hosting)
  - [PlanetScale](#-planetscale)
  - [Railway MySQL](#-railway-mysql)
- [🍃 MongoDB Hosting](#-mongodb-hosting)
  - [MongoDB Atlas](#-mongodb-atlas)
  - [Railway MongoDB](#-railway-mongodb)
- [⚡ Redis Hosting](#-redis-hosting)
  - [Upstash](#-upstash)
  - [Redis Cloud](#-redis-cloud)
- [🔥 Firebase & Firestore](#-firebase--firestore)
- [🌍 Distributed Databases](#-distributed-databases)
- [🔄 Database Migration](#-database-migration)
- [🔐 Security Best Practices](#-security-best-practices)
- [📊 Performance Optimization](#-performance-optimization)
- [💰 Cost Optimization](#-cost-optimization)
- [🔧 Backup & Recovery](#-backup--recovery)
- [🐛 Troubleshooting](#-troubleshooting)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Choosing Your Database

_The ultimate database decision guide_ 🌲

</div>

### Understanding Database Types

```
╔═══════════════════════════════════════════════════════════╗
║                  DATABASE TYPES EXPLAINED                  ║
╚═══════════════════════════════════════════════════════════╝

1. RELATIONAL (SQL) DATABASES
┌────────────────────────────────────────────────────────┐
│  PostgreSQL, MySQL, MariaDB                            │
│                                                        │
│  Structure:                                            │
│  ┌─────────────┐  ┌─────────────┐                     │
│  │   Users     │  │    Posts    │                     │
│  ├─────────────┤  ├─────────────┤                     │
│  │ id (PK)     │  │ id (PK)     │                     │
│  │ name        │  │ user_id (FK)│───┐                 │
│  │ email       │  │ title       │   │                 │
│  │ created_at  │  │ content     │   │                 │
│  └─────────────┘  └─────────────┘   │                 │
│         ▲                            │                 │
│         └────────────────────────────┘                 │
│                                                        │
│  ✅ PROS:                                              │
│  • Strong consistency (ACID)                          │
│  • Complex queries (JOINs)                            │
│  • Data integrity enforced                            │
│  • Mature ecosystem                                    │
│  • Transactions support                                │
│                                                        │
│  ❌ CONS:                                              │
│  • Schema changes can be complex                      │
│  • Vertical scaling limits                            │
│  • Not ideal for unstructured data                    │
│                                                        │
│  🎯 USE WHEN:                                          │
│  • Data has relationships                             │
│  • Need ACID transactions                             │
│  • Complex queries required                           │
│  • Data structure is well-defined                     │
└────────────────────────────────────────────────────────┘

2. DOCUMENT DATABASES (NoSQL)
┌────────────────────────────────────────────────────────┐
│  MongoDB, Firestore, DynamoDB                          │
│                                                        │
│  Structure:                                            │
│  {                                                     │
│    "_id": "user123",                                   │
│    "name": "MrDib",                                    │
│    "email": "email@example.com",                       │
│    "posts": [                                          │
│      {                                                 │
│        "id": "post1",                                  │
│        "title": "My Post",                             │
│        "content": "...",                               │
│        "tags": ["tech", "coding"]                      │
│      }                                                 │
│    ],                                                  │
│    "preferences": {                                    │
│      "theme": "dark",                                  │
│      "notifications": true                             │
│    }                                                   │
│  }                                                     │
│                                                        │
│  ✅ PROS:                                              │
│  • Flexible schema                                     │
│  • Horizontal scaling                                  │
│  • Fast for simple queries                            │
│  • Good for nested data                               │
│  • Easy to get started                                │
│                                                        │
│  ❌ CONS:                                              │
│  • No built-in joins                                  │
│  • Data duplication common                            │
│  • Eventual consistency (some)                        │
│  • Complex transactions harder                        │
│                                                        │
│  🎯 USE WHEN:                                          │
│  • Schema changes frequently                          │
│  • Need to scale horizontally                         │
│  • Storing varied/nested data                         │
│  • Real-time applications                             │
└────────────────────────────────────────────────────────┘

3. KEY-VALUE STORES
┌────────────────────────────────────────────────────────┐
│  Redis, Upstash, DynamoDB                              │
│                                                        │
│  Structure:                                            │
│  Key              → Value                              │
│  ─────────────────────────────────────                 │
│  user:123:name    → "MrDib"                            │
│  user:123:email   → "email@example.com"                │
│  session:abc123   → {...session data...}              │
│  cache:posts:all  → [...cached posts...]              │
│                                                        │
│  ✅ PROS:                                              │
│  • Extremely fast (in-memory)                         │
│  • Simple data model                                   │
│  • Excellent for caching                              │
│  • Low latency                                         │
│  • Highly scalable                                     │
│                                                        │
│  ❌ CONS:                                              │
│  • No complex queries                                 │
│  • Limited data types                                  │
│  • Not for primary storage                            │
│  • Memory constraints                                  │
│                                                        │
│  🎯 USE WHEN:                                          │
│  • Caching frequently accessed data                   │
│  • Session storage                                     │
│  • Real-time analytics                                │
│  • Rate limiting                                       │
│  • Message queues                                      │
└────────────────────────────────────────────────────────┘

4. TIME-SERIES DATABASES
┌────────────────────────────────────────────────────────┐
│  TimescaleDB, InfluxDB                                 │
│                                                        │
│  Structure:                                            │
│  Timestamp              Metric      Value              │
│  ─────────────────────────────────────────             │
│  2024-01-01 10:00:00   cpu_usage   45.2               │
│  2024-01-01 10:01:00   cpu_usage   47.8               │
│  2024-01-01 10:02:00   cpu_usage   43.1               │
│                                                        │
│  🎯 USE WHEN:                                          │
│  • Storing metrics/logs                               │
│  • IoT sensor data                                     │
│  • Application monitoring                             │
│  • Financial tick data                                │
└────────────────────────────────────────────────────────┘

═══════════════════════════════════════════════════════════

DECISION TREE:

START: What are you building?
   │
   ├─❓ E-commerce / SaaS / Traditional app?
   │  └─✅ PostgreSQL (Supabase, Neon)
   │     • Structured data
   │     • Relationships important
   │     • Need transactions
   │
   ├─❓ Real-time chat / Collaborative app?
   │  └─✅ Firestore or MongoDB
   │     • Real-time sync
   │     • Flexible schema
   │     • Offline support
   │
   ├─❓ Need caching / sessions?
   │  └─✅ Redis (Upstash)
   │     • Fast access
   │     • Temporary data
   │     • Rate limiting
   │
   ├─❓ Mobile app with auth?
   │  └─✅ Firebase or Supabase
   │     • Auth included
   │     • File storage
   │     • Real-time
   │
   ├─❓ Analytics / Metrics?
   │  └─✅ TimescaleDB or InfluxDB
   │     • Time-series data
   │     • Aggregations
   │     • Retention policies
   │
   └─❓ Content-heavy site?
      └─✅ PostgreSQL with full-text search
         • Complex queries
         • Search functionality
         • JSON support

═══════════════════════════════════════════════════════════

POLYGLOT PERSISTENCE (Using multiple databases):

Modern App Architecture:
┌────────────────────────────────────────────┐
│  Frontend (React, Vue, etc.)               │
└────────────────────────────────────────────┘
                    ↓
┌────────────────────────────────────────────┐
│  API Layer (Node.js, Python, etc.)         │
└────────────────────────────────────────────┘
         ↓              ↓              ↓
   ┌─────────┐   ┌──────────┐   ┌─────────┐
   │PostgreSQL│   │  Redis   │   │   S3    │
   │(Primary) │   │ (Cache)  │   │ (Files) │
   └─────────┘   └──────────┘   └─────────┘

Example:
• PostgreSQL → User accounts, orders, products
• Redis → Session data, caching, rate limiting
• S3/Cloudinary → Images, videos, files
• Elasticsearch → Full-text search

Benefits:
✅ Use right tool for each job
✅ Better performance
✅ More flexibility
```

### Comparison Matrix

```
═══════════════════════════════════════════════════════════
DATABASE HOSTING COMPARISON
═══════════════════════════════════════════════════════════

POSTGRESQL PROVIDERS:

┌─────────────┬────────────┬─────────────┬──────────────┬──────┐
│ Provider    │ Free Tier  │ Best Feature│ Paid From    │ Rating│
├─────────────┼────────────┼─────────────┼──────────────┼──────┤
│ Supabase    │ 500MB      │ Auth+Storage│ $25/mo       │ ⭐⭐⭐⭐⭐│
│             │ 2 projects │ included    │              │      │
├─────────────┼────────────┼─────────────┼──────────────┼──────┤
│ Neon        │ 3GB        │ Serverless  │ $19/mo       │ ⭐⭐⭐⭐⭐│
│             │ Branching  │ Autoscaling │              │      │
├─────────────┼────────────┼─────────────┼──────────────┼──────┤
│ Railway     │ Included   │ Integrated  │ Usage-based  │ ⭐⭐⭐⭐ │
│             │ w/project  │ Platform    │ ~$5/mo       │      │
├─────────────┼────────────┼─────────────┼──────────────┼──────┤
│ Render      │ None (paid)│ Backups     │ $7/mo        │ ⭐⭐⭐⭐ │
│             │            │ included    │              │      │
├─────────────┼────────────┼─────────────┼──────────────┼──────┤
│ AWS RDS     │ 750hrs/yr  │ Enterprise  │ $15/mo+      │ ⭐⭐⭐⭐ │
│             │ (1st year) │ features    │              │      │
└─────────────┴────────────┴─────────────┴──────────────┴──────┘

MYSQL PROVIDERS:

┌─────────────┬────────────┬─────────────┬──────────────┬──────┐
│ Provider    │ Free Tier  │ Best Feature│ Paid From    │ Rating│
├─────────────┼────────────┼─────────────┼──────────────┼──────┤
│ PlanetScale │ 5GB        │ DB Branching│ $29/mo       │ ⭐⭐⭐⭐⭐│
│             │ 1B reads   │ Schema diffs│              │      │
├─────────────┼────────────┼─────────────┼──────────────┼──────┤
│ Railway     │ Included   │ Easy setup  │ Usage-based  │ ⭐⭐⭐⭐ │
│             │ w/project  │             │ ~$5/mo       │      │
├─────────────┼────────────┼─────────────┼──────────────┼──────┤
│ AWS RDS     │ 750hrs/yr  │ Proven      │ $15/mo+      │ ⭐⭐⭐⭐ │
│             │            │ Reliable    │              │      │
└─────────────┴────────────┴─────────────┴──────────────┴──────┘

MONGODB PROVIDERS:

┌─────────────┬────────────┬─────────────┬──────────────┬──────┐
│ Provider    │ Free Tier  │ Best Feature│ Paid From    │ Rating│
├─────────────┼────────────┼─────────────┼──────────────┼──────┤
│ MongoDB     │ 512MB      │ Official    │ $9/mo        │ ⭐⭐⭐⭐⭐│
│ Atlas       │ Shared     │ Atlas Search│              │      │
├─────────────┼────────────┼─────────────┼──────────────┼──────┤
│ Railway     │ Included   │ Integrated  │ Usage-based  │ ⭐⭐⭐⭐ │
│             │ w/project  │             │ ~$5/mo       │      │
└─────────────┴────────────┴─────────────┴──────────────┴──────┘

REDIS PROVIDERS:

┌─────────────┬────────────┬─────────────┬──────────────┬──────┐
│ Provider    │ Free Tier  │ Best Feature│ Paid From    │ Rating│
├─────────────┼────────────┼─────────────┼──────────────┼──────┤
│ Upstash     │ 10k cmds   │ Serverless  │ $0.2/100k    │ ⭐⭐⭐⭐⭐│
│             │ /day       │ Pay-per-use │ requests     │      │
├─────────────┼────────────┼─────────────┼──────────────┼──────┤
│ Redis Cloud │ 30MB       │ Official    │ $5/mo        │ ⭐⭐⭐⭐ │
│             │            │ Redis Labs  │              │      │
├─────────────┼────────────┼─────────────┼──────────────┼──────┤
│ Railway     │ Included   │ Easy        │ Usage-based  │ ⭐⭐⭐⭐ │
│             │ w/project  │             │ ~$3/mo       │      │
└─────────────┴────────────┴─────────────┴──────────────┴──────┘

REAL-TIME DATABASES:

┌─────────────┬────────────┬─────────────┬──────────────┬──────┐
│ Provider    │ Free Tier  │ Best Feature│ Paid From    │ Rating│
├─────────────┼────────────┼─────────────┼──────────────┼──────┤
│ Firebase    │ 1GB storage│ Real-time   │ Pay-as-go    │ ⭐⭐⭐⭐⭐│
│ Firestore   │ 50k reads  │ Offline sync│ ~$25/mo      │      │
├─────────────┼────────────┼─────────────┼──────────────┼──────┤
│ Supabase    │ 500MB      │ PostgreSQL  │ $25/mo       │ ⭐⭐⭐⭐⭐│
│             │ Realtime   │ + Real-time │              │      │
└─────────────┴────────────┴─────────────┴──────────────┴──────┘

RECOMMENDATIONS BY USE CASE:

🎯 Startup/MVP:
   → Supabase (PostgreSQL + Auth + Storage)
   → PlanetScale (MySQL with branching)

💰 Budget-Conscious:
   → Railway (all-in-one, pay-as-you-go)
   → Neon (generous free tier)
   → Supabase (free tier is great)

🚀 High Performance:
   → PlanetScale (horizontal scaling)
   → Neon (serverless autoscaling)
   → Upstash Redis (for caching)

🏢 Enterprise:
   → AWS RDS/Aurora
   → Google Cloud SQL
   → Azure Database

🔥 Real-time Apps:
   → Firebase/Firestore
   → Supabase (realtime PostgreSQL)

📱 Mobile Apps:
   → Firebase (SDK + Auth)
   → Supabase (SDK + Auth)

🎮 Gaming:
   → MongoDB Atlas (flexible schema)
   → DynamoDB (low latency)
```

---

<div align="center">

## 🐘 PostgreSQL Hosting

_The world's most advanced open source database_ 🎯

</div>

### ⚡ Supabase

**Open source Firebase alternative powered by PostgreSQL**

```
🌐 Website → https://supabase.com
🎯 Best For → Full-stack apps needing auth, database, storage
💰 Pricing  → Free: 500MB DB, 1GB file storage, 50k MAU
             Paid: $25/month for 8GB DB, 100GB storage
⚡ Features → PostgreSQL, Auth, Storage, Edge Functions, Realtime
🔧 Support  → JavaScript, Python, Dart, C#, Swift, Kotlin
```

#### 📥 Supabase Setup

```bash
# ═══════════════════════════════════════════
# INSTALLATION & SETUP
# ═══════════════════════════════════════════

# Create project at supabase.com
# Get your project URL and anon key

# Install client library
npm install @supabase/supabase-js

# For React/Next.js
npm install @supabase/auth-helpers-nextjs
npm install @supabase/auth-helpers-react

# For authentication UI
npm install @supabase/auth-ui-react @supabase/auth-ui-shared
```

#### 📝 Supabase Configuration

```javascript
// ═══════════════════════════════════════════
// lib/supabase.js - Client Setup
// ═══════════════════════════════════════════

import { createClient } from "@supabase/supabase-js";

// Environment variables
const supabaseUrl = process.env.NEXT_PUBLIC_SUPABASE_URL;
const supabaseAnonKey = process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY;

export const supabase = createClient(supabaseUrl, supabaseAnonKey);

// With custom options
export const supabaseWithOptions = createClient(supabaseUrl, supabaseAnonKey, {
  auth: {
    autoRefreshToken: true,
    persistSession: true,
    detectSessionInUrl: true,
  },
  db: {
    schema: "public",
  },
  global: {
    headers: {
      "x-custom-header": "my-app",
    },
  },
});

// ═══════════════════════════════════════════
// CRUD OPERATIONS
// ═══════════════════════════════════════════

// CREATE
async function createPost(title, content, userId) {
  const { data, error } = await supabase
    .from("posts")
    .insert([
      {
        title,
        content,
        user_id: userId,
        created_at: new Date().toISOString(),
      },
    ])
    .select();

  if (error) throw error;
  return data;
}

// READ
async function getPosts() {
  const { data, error } = await supabase
    .from("posts")
    .select("*")
    .order("created_at", { ascending: false });

  if (error) throw error;
  return data;
}

// READ with JOIN
async function getPostsWithAuthors() {
  const { data, error } = await supabase
    .from("posts")
    .select(
      `
      *,
      author:users (
        id,
        name,
        email,
        avatar_url
      )
    `
    )
    .order("created_at", { ascending: false });

  if (error) throw error;
  return data;
}

// READ with filtering
async function getPublishedPosts() {
  const { data, error } = await supabase
    .from("posts")
    .select("*")
    .eq("published", true)
    .gte("created_at", "2024-01-01")
    .order("created_at", { ascending: false })
    .limit(10);

  if (error) throw error;
  return data;
}

// UPDATE
async function updatePost(id, updates) {
  const { data, error } = await supabase
    .from("posts")
    .update(updates)
    .eq("id", id)
    .select();

  if (error) throw error;
  return data;
}

// DELETE
async function deletePost(id) {
  const { error } = await supabase.from("posts").delete().eq("id", id);

  if (error) throw error;
}

// ═══════════════════════════════════════════
// REAL-TIME SUBSCRIPTIONS
// ═══════════════════════════════════════════

// Subscribe to changes
const subscription = supabase
  .channel("posts_channel")
  .on(
    "postgres_changes",
    {
      event: "*", // INSERT, UPDATE, DELETE, or *
      schema: "public",
      table: "posts",
    },
    (payload) => {
      console.log("Change detected:", payload);

      if (payload.eventType === "INSERT") {
        console.log("New post:", payload.new);
      }

      if (payload.eventType === "UPDATE") {
        console.log("Updated post:", payload.new);
        console.log("Old values:", payload.old);
      }

      if (payload.eventType === "DELETE") {
        console.log("Deleted post:", payload.old);
      }
    }
  )
  .subscribe();

// Unsubscribe
subscription.unsubscribe();

// ═══════════════════════════════════════════
// AUTHENTICATION
// ═══════════════════════════════════════════

// Sign up with email
async function signUp(email, password) {
  const { data, error } = await supabase.auth.signUp({
    email,
    password,
  });

  if (error) throw error;
  return data;
}

// Sign in with email
async function signIn(email, password) {
  const { data, error } = await supabase.auth.signInWithPassword({
    email,
    password,
  });

  if (error) throw error;
  return data;
}

// Sign in with OAuth
async function signInWithGoogle() {
  const { data, error } = await supabase.auth.signInWithOAuth({
    provider: "google",
    options: {
      redirectTo: "http://localhost:3000/auth/callback",
    },
  });

  if (error) throw error;
  return data;
}

// Sign out
async function signOut() {
  const { error } = await supabase.auth.signOut();
  if (error) throw error;
}

// Get current user
async function getCurrentUser() {
  const {
    data: { user },
  } = await supabase.auth.getUser();
  return user;
}

// Listen to auth changes
supabase.auth.onAuthStateChange((event, session) => {
  console.log("Auth event:", event);
  console.log("Session:", session);

  if (event === "SIGNED_IN") {
    console.log("User signed in");
  }

  if (event === "SIGNED_OUT") {
    console.log("User signed out");
  }
});

// ═══════════════════════════════════════════
// FILE STORAGE
// ═══════════════════════════════════════════

// Upload file
async function uploadFile(file, bucket = "avatars") {
  const fileName = `${Date.now()}_${file.name}`;

  const { data, error } = await supabase.storage
    .from(bucket)
    .upload(fileName, file, {
      cacheControl: "3600",
      upsert: false,
    });

  if (error) throw error;
  return data;
}

// Get public URL
function getPublicUrl(path, bucket = "avatars") {
  const { data } = supabase.storage.from(bucket).getPublicUrl(path);

  return data.publicUrl;
}

// Download file
async function downloadFile(path, bucket = "avatars") {
  const { data, error } = await supabase.storage.from(bucket).download(path);

  if (error) throw error;
  return data;
}

// Delete file
async function deleteFile(path, bucket = "avatars") {
  const { error } = await supabase.storage.from(bucket).remove([path]);

  if (error) throw error;
}

// List files
async function listFiles(folder = "", bucket = "avatars") {
  const { data, error } = await supabase.storage.from(bucket).list(folder, {
    limit: 100,
    offset: 0,
    sortBy: { column: "created_at", order: "desc" },
  });

  if (error) throw error;
  return data;
}

// ═══════════════════════════════════════════
// EDGE FUNCTIONS (Serverless)
// ═══════════════════════════════════════════

// Invoke edge function
async function invokeFunction(functionName, payload) {
  const { data, error } = await supabase.functions.invoke(functionName, {
    body: payload,
  });

  if (error) throw error;
  return data;
}

// Example: Send email via edge function
async function sendEmail(to, subject, body) {
  return await invokeFunction("send-email", {
    to,
    subject,
    body,
  });
}
```

#### 🗄️ Supabase Database Schema

```sql
-- ═══════════════════════════════════════════
-- Create tables in Supabase SQL Editor
-- ═══════════════════════════════════════════

-- Enable UUID extension
create extension if not exists "uuid-ossp";

-- Users table (extends auth.users)
create table public.profiles (
  id uuid references auth.users on delete cascade not null primary key,
  username text unique,
  full_name text,
  avatar_url text,
  bio text,
  created_at timestamp with time zone default timezone('utc'::text, now()) not null,
  updated_at timestamp with time zone default timezone('utc'::text, now()) not null
);

-- Enable Row Level Security (RLS)
alter table public.profiles enable row level security;

-- RLS Policies
create policy "Public profiles are viewable by everyone"
  on profiles for select
  using ( true );

create policy "Users can insert their own profile"
  on profiles for insert
  with check ( auth.uid() = id );

create policy "Users can update own profile"
  on profiles for update
  using ( auth.uid() = id );

-- Posts table
create table public.posts (
  id uuid default uuid_generate_v4() primary key,
  user_id uuid references public.profiles(id) on delete cascade not null,
  title text not null,
  content text,
  published boolean default false,
  created_at timestamp with time zone default timezone('utc'::text, now()) not null,
  updated_at timestamp with time zone default timezone('utc'::text, now()) not null
);

-- Enable RLS
alter table public.posts enable row level security;

-- RLS Policies for posts
create policy "Published posts are viewable by everyone"
  on posts for select
  using ( published = true );

create policy "Users can view their own posts"
  on posts for select
  using ( auth.uid() = user_id );

create policy "Users can insert their own posts"
  on posts for insert
  with check ( auth.uid() = user_id );

create policy "Users can update their own posts"
  on posts for update
  using ( auth.uid() = user_id );

create policy "Users can delete their own posts"
  on posts for delete
  using ( auth.uid() = user_id );

-- Indexes for performance
create index posts_user_id_idx on public.posts(user_id);
create index posts_created_at_idx on public.posts(created_at desc);
create index posts_published_idx on public.posts(published) where published = true;

-- Full-text search
create index posts_title_content_idx on public.posts
  using gin(to_tsvector('english', title || ' ' || coalesce(content, '')));

-- Function to automatically update updated_at
create or replace function public.handle_updated_at()
returns trigger as $$
begin
  new.updated_at = now();
  return new;
end;
$$ language plpgsql;

-- Trigger for updated_at
create trigger handle_updated_at
  before update on public.profiles
  for each row
  execute procedure public.handle_updated_at();

create trigger handle_updated_at
  before update on public.posts
  for each row
  execute procedure public.handle_updated_at();

-- ═══════════════════════════════════════════
-- FULL-TEXT SEARCH FUNCTION
-- ═══════════════════════════════════════════

create or replace function search_posts(search_query text)
returns setof posts
language sql
stable
as $$
  select *
  from posts
  where published = true
  and to_tsvector('english', title || ' ' || coalesce(content, '')) @@ plainto_tsquery('english', search_query)
  order by ts_rank(to_tsvector('english', title || ' ' || coalesce(content, '')), plainto_tsquery('english', search_query)) desc;
$$;

-- Use in JavaScript:
-- const { data } = await supabase.rpc('search_posts', { search_query: 'keyword' });
```

#### 💡 Supabase Pro Tips

```javascript
// ═══════════════════════════════════════════
// PERFORMANCE OPTIMIZATION
// ═══════════════════════════════════════════

// 1. Use select() to fetch only needed columns
const { data } = await supabase.from("posts").select("id, title, created_at"); // ✅ Only needed columns
// .select('*'); // ❌ Fetches everything

// 2. Pagination
const pageSize = 10;
const page = 1;

const { data, error } = await supabase
  .from("posts")
  .select("*", { count: "exact" })
  .range((page - 1) * pageSize, page * pageSize - 1);

// 3. Use indexes for filtered queries
// Create index in SQL Editor:
// create index posts_user_published_idx on posts(user_id, published);

// 4. Batch inserts
const { data } = await supabase.from("posts").insert([
  { title: "Post 1", content: "..." },
  { title: "Post 2", content: "..." },
  { title: "Post 3", content: "..." },
]);

// ═══════════════════════════════════════════
// ERROR HANDLING
// ═══════════════════════════════════════════

async function safeQuery() {
  const { data, error } = await supabase.from("posts").select("*");

  if (error) {
    // Log error
    console.error("Supabase error:", error.message);

    // Handle specific errors
    if (error.code === "PGRST116") {
      console.error("Resource not found");
    }

    // Return or throw
    throw new Error(`Database error: ${error.message}`);
  }

  return data;
}

// ═══════════════════════════════════════════
// SECURITY BEST PRACTICES
// ═══════════════════════════════════════════

// 1. Always use RLS (Row Level Security)
// Enable it on all tables

// 2. Use service role key only on server
// Server-side (Next.js API route)
import { createClient } from "@supabase/supabase-js";

const supabaseAdmin = createClient(
  process.env.NEXT_PUBLIC_SUPABASE_URL,
  process.env.SUPABASE_SERVICE_ROLE_KEY // Server-only!
);

// 3. Validate user input
function validatePostData(data) {
  if (!data.title || data.title.length < 3) {
    throw new Error("Title must be at least 3 characters");
  }

  if (data.title.length > 200) {
    throw new Error("Title too long");
  }

  return true;
}

// 4. Use prepared statements (automatic in Supabase)
// All queries are parameterized by default

// ═══════════════════════════════════════════
// CACHING STRATEGY
// ═══════════════════════════════════════════

// Client-side caching with SWR or React Query
import useSWR from "swr";

const fetcher = async () => {
  const { data } = await supabase.from("posts").select("*");
  return data;
};

function Posts() {
  const { data, error, isLoading } = useSWR("posts", fetcher, {
    revalidateOnFocus: false,
    revalidateOnReconnect: false,
  });

  // ...
}

// ═══════════════════════════════════════════
// DATABASE FUNCTIONS (Stored Procedures)
// ═══════════════════════════════════════════

// Create in SQL Editor:
/*
create or replace function increment_post_views(post_id uuid)
returns void as $$
  update posts
  set view_count = view_count + 1
  where id = post_id;
$$ language sql volatile;
*/

// Call from JavaScript:
const { data, error } = await supabase.rpc("increment_post_views", {
  post_id: "uuid-here",
});
```

---

### 💡 Neon

**Serverless PostgreSQL with instant branching**

```
🌐 Website → https://neon.tech
🎯 Best For → Serverless apps, development workflows, preview environments
💰 Pricing  → Free: 3GB storage, 3 projects
             Paid: $19/month for 10GB, autoscaling
⚡ Features → Serverless, Branching, Autoscaling, Point-in-time restore
🔧 Support  → Any PostgreSQL client library
```

#### 📥 Neon Setup

```bash
# ═══════════════════════════════════════════
# INSTALLATION & SETUP
# ═══════════════════════════════════════════

# Create account at neon.tech
# Create project and get connection string

# Install Neon CLI
npm install -g neonctl

# Login
neonctl auth

# List projects
neonctl projects list

# Create branch (like git branch!)
neonctl branches create --project-id your-project-id --name dev

# ═══════════════════════════════════════════
# CONNECTION STRING FORMAT
# ═══════════════════════════════════════════

# Format:
# postgres://[user]:[password]@[endpoint]/[dbname]?sslmode=require

# Example:
# postgres://user:pass@ep-cool-darkness-123456.us-east-2.aws.neon.tech/neondb?sslmode=require
```

#### 📝 Neon Configuration

```javascript
// ═══════════════════════════════════════════
// Node.js with pg (node-postgres)
// ═══════════════════════════════════════════

import { Pool } from 'pg';

const pool = new Pool({
  connectionString: process.env.DATABASE_URL,
  ssl: { rejectUnauthorized: false }
});

// Query
const { rows } = await pool.query('SELECT * FROM users');

// With parameters
const { rows } = await pool.query(
  'SELECT * FROM users WHERE email = $1',
  ['user@example.com']
);

// Transaction
const client = await pool.connect();
try {
  await client.query('BEGIN');
  await client.query('UPDATE accounts SET balance = balance - $1 WHERE id = $2', [100, 1]);
  await client.query('UPDATE accounts SET balance = balance + $1 WHERE id = $2', [100, 2]);
  await client.query('COMMIT');
} catch (e) {
  await client.query('ROLLBACK');
  throw e;
} finally {
  client.release();
}

// ═══════════════════════════════════════════
// Prisma ORM
// ═══════════════════════════════════════════

// prisma/schema.prisma
datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

generator client {
  provider = "prisma-client-js"
}

model User {
  id        Int      @id @default(autoincrement())
  email     String   @unique
  name      String?
  posts     Post[]
  createdAt DateTime @default(now())
}

model Post {
  id        Int      @id @default(autoincrement())
  title     String
  content   String?
  published Boolean  @default(false)
  author    User     @relation(fields: [authorId], references: [id])
  authorId  Int
  createdAt DateTime @default(now())
}

// Generate client
// npx prisma generate

// Use Prisma Client
import { PrismaClient } from '@prisma/client';

const prisma = new PrismaClient();

// Create user
const user = await prisma.user.create({
  data: {
    email: 'user@example.com',
    name: 'MrDib',
    posts: {
      create: [
        { title: 'First Post', content: 'Hello World!' }
      ]
    }
  },
  include: {
    posts: true
  }
});

// Query with relations
const users = await prisma.user.findMany({
  include: {
    posts: {
      where: { published: true }
    }
  }
});

// ═══════════════════════════════════════════
// Drizzle ORM (Lightweight alternative)
// ═══════════════════════════════════════════

import { drizzle } from 'drizzle-orm/node-postgres';
import { pgTable, serial, text, timestamp, boolean } from 'drizzle-orm/pg-core';
import { Pool } from 'pg';

const pool = new Pool({
  connectionString: process.env.DATABASE_URL
});

const db = drizzle(pool);

// Define schema
const users = pgTable('users', {
  id: serial('id').primaryKey(),
  email: text('email').notNull().unique(),
  name: text('name'),
  createdAt: timestamp('created_at').defaultNow()
});

const posts = pgTable('posts', {
  id: serial('id').primaryKey(),
  title: text('title').notNull(),
  content: text('content'),
  published: boolean('published').default(false),
  authorId: serial('author_id').references(() => users.id),
  createdAt: timestamp('created_at').defaultNow()
});

// Query
const allUsers = await db.select().from(users);

// With where
const publishedPosts = await db
  .select()
  .from(posts)
  .where(eq(posts.published, true));

// ═══════════════════════════════════════════
// DATABASE BRANCHING (Git for Databases!)
// ═══════════════════════════════════════════

// Create development branch
neonctl branches create --project-id your-project --name dev

// Create feature branch from dev
neonctl branches create --project-id your-project --name feature-auth --parent dev

// Get connection string for branch
neonctl connection-string feature-auth

// Use different connection strings per environment:
// .env.development
DATABASE_URL=postgres://...@ep-dev-123.neon.tech/neondb

// .env.production
DATABASE_URL=postgres://...@ep-main-456.neon.tech/neondb

// When feature is ready, merge changes:
// 1. Test in feature branch
// 2. Deploy to production with main branch connection string
// 3. Delete feature branch
neonctl branches delete feature-auth

// ═══════════════════════════════════════════
// POINT-IN-TIME RESTORE
// ═══════════════════════════════════════════

// Restore to specific timestamp
neonctl branches create --project-id your-project \
  --name recovery \
  --parent main \
  --timestamp "2024-01-15T10:30:00Z"

// Use recovery branch to inspect/recover data
```

#### 💡 Neon Pro Tips

```javascript
// ═══════════════════════════════════════════
// AUTOSCALING & COMPUTE OPTIMIZATION
// ═══════════════════════════════════════════

// Neon automatically scales compute based on load
// - Scales down to zero when idle (saves costs!)
// - Scales up when traffic increases

// Connection pooling (recommended)
import { neon, neonConfig } from '@neondatabase/serverless';

// For serverless environments
neonConfig.fetchConnectionCache = true;

const sql = neon(process.env.DATABASE_URL);

// Query (HTTP-based, no persistent connection)
const users = await sql`SELECT * FROM users`;

// ═══════════════════════════════════════════
// COLD START OPTIMIZATION
// ═══════════════════════════════════════════

// Use HTTP queries for serverless (faster cold starts)
import { neon } from '@neondatabase/serverless';

const sql = neon(process.env.DATABASE_URL);

// Direct SQL execution (no connection overhead)
const result = await sql`
  SELECT * FROM users WHERE email = ${email}
`;

// ═══════════════════════════════════════════
// MIGRATION WORKFLOW
// ═══════════════════════════════════════════

// 1. Create branch for migration
neonctl branches create --name migration-001

// 2. Apply migration to branch
DATABASE_URL=<branch-connection-string> npx prisma migrate dev

// 3. Test thoroughly

// 4. Apply to production
DATABASE_URL=<main-connection-string> npx prisma migrate deploy

// 5. Delete migration branch
neonctl branches delete migration-001

// ═══════════════════════════════════════════
// MONITORING & ANALYTICS
// ═══════════════════════════════════════════

// Check branch usage
neonctl branches list --project-id your-project

// View metrics in Neon dashboard:
// - Active time
// - Compute time
// - Data transfer
// - Storage size
```

---

### 🚂 Railway PostgreSQL

**Integrated PostgreSQL with Railway platform**

```
🌐 Website → https://railway.app
🎯 Best For → Full-stack apps on Railway platform
💰 Pricing  → Usage-based (included in Railway project)
             ~$5-10/month for small DB
⚡ Features → Automatic backups, metrics, logs
🔧 Support  → Any PostgreSQL client
```

#### 📥 Railway PostgreSQL Setup

```bash
# ═══════════════════════════════════════════
# SETUP
# ═══════════════════════════════════════════

# Add PostgreSQL to Railway project
railway add postgresql

# Connection string automatically available as:
# DATABASE_URL

# View variables
railway variables

# Connect locally for debugging
railway run psql

# ═══════════════════════════════════════════
# BACKUP & RESTORE
# ═══════════════════════════════════════════

# Backups are automatic on Railway

# Download backup (via UI)
# Project → PostgreSQL → Backups → Download

# Restore from backup
# Project → PostgreSQL → Backups → Restore
```

#### 📝 Railway PostgreSQL Usage

```javascript
// Same as standard PostgreSQL connection
import { Pool } from "pg";

const pool = new Pool({
  connectionString: process.env.DATABASE_URL,
  ssl: { rejectUnauthorized: false },
});

// Railway provides these environment variables automatically:
// - DATABASE_URL (connection string)
// - PGHOST
// - PGPORT
// - PGUSER
// - PGPASSWORD
// - PGDATABASE
```

---

<div align="center">

## 🐬 MySQL Hosting

_Popular relational database for web applications_ 🌐

</div>

### 🌍 PlanetScale

**Serverless MySQL with database branching**

```
🌐 Website → https://planetscale.com
🎯 Best For → Scalable MySQL apps, development workflows
💰 Pricing  → Free: 5GB storage, 1 billion row reads/month
             Paid: $29/month for 10GB, 10 billion reads
⚡ Features → Branching, schema migrations, horizontal sharding
🔧 Support  → Standard MySQL protocol, Prisma
```

#### 📥 PlanetScale Setup

```bash
# ═══════════════════════════════════════════
# INSTALLATION
# ═══════════════════════════════════════════

# Install CLI
brew install planetscale/tap/pscale

# Or via script
curl -fsSL https://raw.githubusercontent.com/planetscale/cli/main/install.sh | sh

# Login
pscale auth login

# ═══════════════════════════════════════════
# DATABASE MANAGEMENT
# ═══════════════════════════════════════════

# Create database
pscale database create my-database --region us-east

# List databases
pscale database list

# Create branch (like git!)
pscale branch create my-database dev

# Create deploy request (like PR)
pscale deploy-request create my-database dev

# ═══════════════════════════════════════════
# CONNECTION
# ═══════════════════════════════════════════

# Get connection string
pscale connect my-database main --port 3309

# Connection string format:
# mysql://user:password@host/database?sslmode=require
```

#### 📝 PlanetScale Configuration

```javascript
// ═══════════════════════════════════════════
// Prisma with PlanetScale
// ═══════════════════════════════════════════

// prisma/schema.prisma
datasource db {
  provider = "mysql"
  url      = env("DATABASE_URL")
  relationMode = "prisma" // Important for PlanetScale!
}

generator client {
  provider = "prisma-client-js"
}

model User {
  id        String   @id @default(cuid())
  email     String   @unique
  name      String?
  posts     Post[]
  createdAt DateTime @default(now())

  @@index([email])
}

model Post {
  id        String   @id @default(cuid())
  title     String
  content   String?  @db.Text
  published Boolean  @default(false)
  authorId  String
  author    User     @relation(fields: [authorId], references: [id])
  createdAt DateTime @default(now())

  @@index([authorId])
  @@index([published])
}

// Important: Use @@index instead of foreign key constraints
// PlanetScale doesn't support foreign keys

// ═══════════════════════════════════════════
// Node.js with mysql2
// ═══════════════════════════════════════════

import mysql from 'mysql2/promise';

const connection = await mysql.createConnection({
  host: process.env.DB_HOST,
  user: process.env.DB_USER,
  password: process.env.DB_PASSWORD,
  database: process.env.DB_NAME,
  ssl: {
    rejectUnauthorized: true
  }
});

// Query
const [rows] = await connection.execute(
  'SELECT * FROM users WHERE email = ?',
  ['user@example.com']
);

// ═══════════════════════════════════════════
// DATABASE BRANCHING WORKFLOW
// ═══════════════════════════════════════════

// 1. Create development branch
pscale branch create my-database dev

// 2. Connect to dev branch
pscale connect my-database dev --port 3309

// 3. Make schema changes on dev branch
// Run migrations with Prisma:
DATABASE_URL="mysql://..." npx prisma db push

// 4. Create deploy request
pscale deploy-request create my-database dev

// 5. Review schema diff in UI
// Shows what will change in production

// 6. Deploy to production
pscale deploy-request deploy my-database <deploy-request-number>

// 7. Delete dev branch (optional)
pscale branch delete my-database dev

// ═══════════════════════════════════════════
// SCHEMA MIGRATIONS
// ═══════════════════════════════════════════

// PlanetScale handles migrations via branching
// No need for migration files!

// Workflow:
// 1. Create branch
// 2. Modify schema on branch (prisma db push)
// 3. Test changes
// 4. Create deploy request
// 5. Review and deploy

// View schema
pscale shell my-database main

// In shell:
SHOW TABLES;
DESCRIBE users;
```

#### 💡 PlanetScale Pro Tips

```bash
# ═══════════════════════════════════════════
# PERFORMANCE OPTIMIZATION
# ═══════════════════════════════════════════

# 1. Add indexes for frequently queried columns
# In Prisma schema:
model User {
  email String @unique
  name  String

  @@index([email])
  @@index([name])
}

# 2. Use connection pooling
# PlanetScale has built-in connection pooling

# 3. Enable query insights
# View slow queries in PlanetScale dashboard
# Insights → Query Statistics

# 4. Use read-only regions (Pro plan)
# Reduces latency for global users

# ═══════════════════════════════════════════
# MONITORING
# ═══════════════════════════════════════════

# View database insights
pscale database show my-database

# Monitor queries
# Dashboard → Insights → Queries

# Set up alerts
# Dashboard → Settings → Notifications

# ═══════════════════════════════════════════
# BACKUP & RESTORE
# ═══════════════════════════════════════════

# Backups are automatic (daily)
# Restore by creating branch from backup point

# Create branch from backup
pscale branch create my-database recovery \
  --restore --timestamp "2024-01-15T10:00:00Z"

# ═══════════════════════════════════════════
# SECURITY
# ═══════════════════════════════════════════

# Create password with specific permissions
pscale password create my-database main password-name \
  --role read-only

# Delete password
pscale password delete my-database main password-id

# IP restrictions (Enterprise plan)
# Dashboard → Settings → IP Allow List
```

---

<div align="center">

## 🍃 MongoDB Hosting

_Flexible document database for modern apps_ 📄

</div>

### 📊 MongoDB Atlas

**Fully managed MongoDB in the cloud**

```
🌐 Website → https://mongodb.com/cloud/atlas
🎯 Best For → Flexible schemas, rapid development, mobile apps
💰 Pricing  → Free: 512MB storage (shared cluster)
             Paid: $9/month for dedicated cluster
⚡ Features → Atlas Search, Charts, Realm, Data API
🔧 Support  → Official MongoDB drivers for all languages
```

#### 📥 MongoDB Atlas Setup

```bash
# ═══════════════════════════════════════════
# SETUP
# ═══════════════════════════════════════════

# 1. Create account at mongodb.com/cloud/atlas
# 2. Create cluster (Free M0 tier available)
# 3. Create database user
# 4. Add IP address to whitelist (0.0.0.0/0 for all)
# 5. Get connection string

# Connection string format:
# mongodb+srv://<username>:<password>@cluster.mongodb.net/<dbname>?retryWrites=true&w=majority

# Install MongoDB driver
npm install mongodb

# Or Mongoose ODM
npm install mongoose
```

#### 📝 MongoDB Atlas Configuration

```javascript
// ═══════════════════════════════════════════
// Native MongoDB Driver
// ═══════════════════════════════════════════

import { MongoClient } from "mongodb";

const client = new MongoClient(process.env.MONGODB_URI);

async function run() {
  try {
    await client.connect();
    const database = client.db("myapp");
    const users = database.collection("users");

    // Insert
    const result = await users.insertOne({
      name: "MrDib",
      email: "email@example.com",
      createdAt: new Date(),
    });

    // Find
    const user = await users.findOne({ email: "email@example.com" });

    // Update
    await users.updateOne(
      { email: "email@example.com" },
      { $set: { name: "Updated Name" } }
    );

    // Delete
    await users.deleteOne({ email: "email@example.com" });

    // Find many with filter
    const allUsers = await users
      .find({
        createdAt: { $gte: new Date("2024-01-01") },
      })
      .toArray();
  } finally {
    await client.close();
  }
}

run().catch(console.error);

// ═══════════════════════════════════════════
// Mongoose ODM (Object Data Modeling)
// ═══════════════════════════════════════════

import mongoose from "mongoose";

// Connect
await mongoose.connect(process.env.MONGODB_URI);

// Define Schema
const userSchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
    trim: true,
  },
  email: {
    type: String,
    required: true,
    unique: true,
    lowercase: true,
    trim: true,
  },
  age: {
    type: Number,
    min: 0,
    max: 120,
  },
  posts: [
    {
      type: mongoose.Schema.Types.ObjectId,
      ref: "Post",
    },
  ],
  createdAt: {
    type: Date,
    default: Date.now,
  },
});

// Add methods
userSchema.methods.getFullName = function () {
  return this.name;
};

// Add static methods
userSchema.statics.findByEmail = function (email) {
  return this.findOne({ email });
};

// Add indexes
userSchema.index({ email: 1 });
userSchema.index({ createdAt: -1 });

// Create Model
const User = mongoose.model("User", userSchema);

// CRUD Operations

// Create
const user = new User({
  name: "MrDib",
  email: "email@example.com",
  age: 25,
});
await user.save();

// Or
const newUser = await User.create({
  name: "MrDib",
  email: "email@example.com",
});

// Read
const users = await User.find();
const user = await User.findById(userId);
const user = await User.findOne({ email: "email@example.com" });

// With conditions
const activeUsers = await User.find({
  age: { $gte: 18 },
  createdAt: { $gte: new Date("2024-01-01") },
});

// With population (joins)
const userWithPosts = await User.findById(userId).populate("posts");

// Update
await User.findByIdAndUpdate(
  userId,
  { name: "Updated Name" },
  { new: true } // Return updated document
);

// Or
user.name = "Updated Name";
await user.save();

// Delete
await User.findByIdAndDelete(userId);

// Or
await User.deleteOne({ email: "email@example.com" });

// ═══════════════════════════════════════════
// AGGREGATION PIPELINE
// ═══════════════════════════════════════════

// Complex queries with aggregation
const stats = await User.aggregate([
  // Match stage (filter)
  {
    $match: {
      createdAt: { $gte: new Date("2024-01-01") },
    },
  },
  // Group stage
  {
    $group: {
      _id: "$age",
      count: { $sum: 1 },
      avgAge: { $avg: "$age" },
    },
  },
  // Sort stage
  {
    $sort: { count: -1 },
  },
  // Limit stage
  {
    $limit: 10,
  },
]);

// Lookup (join) example
const usersWithPosts = await User.aggregate([
  {
    $lookup: {
      from: "posts",
      localField: "_id",
      foreignField: "authorId",
      as: "posts",
    },
  },
  {
    $project: {
      name: 1,
      email: 1,
      postCount: { $size: "$posts" },
    },
  },
]);

// ═══════════════════════════════════════════
// TEXT SEARCH
// ═══════════════════════════════════════════

// Create text index
userSchema.index({ name: "text", bio: "text" });

// Search
const results = await User.find({
  $text: { $search: "developer nodejs" },
});

// With Atlas Search (advanced)
const searchResults = await User.aggregate([
  {
    $search: {
      index: "default",
      text: {
        query: "developer",
        path: ["name", "bio"],
      },
    },
  },
]);

// ═══════════════════════════════════════════
// TRANSACTIONS
// ═══════════════════════════════════════════

const session = await mongoose.startSession();
session.startTransaction();

try {
  // Operations in transaction
  await User.create([{ name: "User 1" }], { session });
  await Post.create([{ title: "Post 1", authorId: userId }], { session });

  // Commit transaction
  await session.commitTransaction();
} catch (error) {
  // Rollback on error
  await session.abortTransaction();
  throw error;
} finally {
  session.endSession();
}

// ═══════════════════════════════════════════
// CHANGE STREAMS (Real-time)
// ═══════════════════════════════════════════

const changeStream = User.watch();

changeStream.on("change", (change) => {
  console.log("Change detected:", change);

  if (change.operationType === "insert") {
    console.log("New user:", change.fullDocument);
  }

  if (change.operationType === "update") {
    console.log("Updated user:", change.documentKey);
  }
});

// Close stream
changeStream.close();
```

#### 💡 MongoDB Atlas Pro Tips

```javascript
// ═══════════════════════════════════════════
// PERFORMANCE OPTIMIZATION
// ═══════════════════════════════════════════

// 1. Create compound indexes for common queries
userSchema.index({ email: 1, createdAt: -1 });

// 2. Use projection to fetch only needed fields
const users = await User.find({}, "name email"); // Only name and email

// 3. Use lean() for read-only queries (faster)
const users = await User.find().lean(); // Returns plain objects

// 4. Use select() to exclude fields
const users = await User.find().select("-password -__v");

// 5. Pagination
const page = 1;
const limit = 10;
const users = await User.find()
  .skip((page - 1) * limit)
  .limit(limit);

// 6. Monitor slow queries in Atlas
// Dashboard → Performance Advisor

// ═══════════════════════════════════════════
// SCHEMA VALIDATION
// ═══════════════════════════════════════════

const userSchema = new mongoose.Schema({
  email: {
    type: String,
    required: [true, "Email is required"],
    unique: true,
    validate: {
      validator: function (v) {
        return /^[\w-\.]+@([\w-]+\.)+[\w-]{2,4}$/.test(v);
      },
      message: "Invalid email format",
    },
  },
  age: {
    type: Number,
    min: [0, "Age cannot be negative"],
    max: [120, "Age too high"],
  },
});

// ═══════════════════════════════════════════
// MIDDLEWARE (Hooks)
// ═══════════════════════════════════════════

// Pre-save hook
userSchema.pre("save", async function (next) {
  // Hash password before saving
  if (this.isModified("password")) {
    this.password = await bcrypt.hash(this.password, 10);
  }
  next();
});

// Post-save hook
userSchema.post("save", function (doc) {
  console.log("User saved:", doc._id);
});

// ═══════════════════════════════════════════
// ATLAS FEATURES
// ═══════════════════════════════════════════

// 1. Atlas Search (Elasticsearch-like search)
// Create search index in Atlas UI
// Use $search in aggregation

// 2. Atlas Charts (Data visualization)
// Create charts in Atlas UI

// 3. Atlas Data API (REST API for MongoDB)
// Enable in Atlas UI
// Access via HTTPS endpoint

// 4. Atlas App Services (formerly Realm)
// Backend-as-a-Service
// Authentication, GraphQL, Triggers

// ═══════════════════════════════════════════
// BACKUP & RESTORE
// ═══════════════════════════════════════════

// Backups are automatic in Atlas (continuous)
// Restore via Atlas UI:
// Cluster → Backup → Restore

// Point-in-time restore available on M10+ clusters
```

---

<div align="center">

## ⚡ Redis Hosting

_In-memory data store for caching and real-time apps_ 🚀

</div>

### 🚀 Upstash

**Serverless Redis with per-request pricing**

```
🌐 Website → https://upstash.com
🎯 Best For → Serverless apps, edge computing, pay-per-use
💰 Pricing  → Free: 10k commands/day
             Paid: $0.2 per 100k requests
⚡ Features → Global replication, REST API, low latency
🔧 Support  → Redis protocol, REST API, SDKs
```

#### 📥 Upstash Setup

```bash
# ═══════════════════════════════════════════
# SETUP
# ═══════════════════════════════════════════

# 1. Create account at upstash.com
# 2. Create database
# 3. Get REST URL and token

# Install SDK
npm install @upstash/redis
```

#### 📝 Upstash Configuration

```javascript
// ═══════════════════════════════════════════
// Upstash Redis SDK (Recommended for serverless)
// ═══════════════════════════════════════════

import { Redis } from "@upstash/redis";

const redis = new Redis({
  url: process.env.UPSTASH_REDIS_REST_URL,
  token: process.env.UPSTASH_REDIS_REST_TOKEN,
});

// Basic operations
await redis.set("key", "value");
const value = await redis.get("key");
await redis.del("key");

// With expiration (TTL in seconds)
await redis.setex("session:123", 3600, "session-data"); // Expires in 1 hour

// Increment
await redis.incr("counter");
await redis.incrby("counter", 5);

// Lists
await redis.lpush("queue", "item1", "item2");
await redis.rpush("queue", "item3");
const item = await redis.lpop("queue");
const items = await redis.lrange("queue", 0, -1);

// Sets
await redis.sadd("tags", "javascript", "nodejs", "redis");
const tags = await redis.smembers("tags");
const exists = await redis.sismember("tags", "nodejs");

// Hashes (objects)
await redis.hset("user:123", {
  name: "MrDib",
  email: "email@example.com",
  age: 25,
});
const user = await redis.hgetall("user:123");
const name = await redis.hget("user:123", "name");

// Sorted Sets (with scores)
await redis.zadd("leaderboard", { score: 100, member: "user1" });
await redis.zadd("leaderboard", { score: 200, member: "user2" });
const top = await redis.zrange("leaderboard", 0, 9, { rev: true }); // Top 10

// ═══════════════════════════════════════════
// CACHING PATTERN
// ═══════════════════════════════════════════

async function getCachedData(key, fetchFn, ttl = 3600) {
  // Try cache first
  const cached = await redis.get(key);
  if (cached) {
    return typeof cached === "string" ? JSON.parse(cached) : cached;
  }

  // Fetch data
  const data = await fetchFn();

  // Cache it
  await redis.setex(key, ttl, JSON.stringify(data));

  return data;
}

// Usage
const posts = await getCachedData(
  "posts:all",
  async () => {
    // Fetch from database
    return await db.query("SELECT * FROM posts");
  },
  300 // 5 minutes
);

// ═══════════════════════════════════════════
// RATE LIMITING
// ═══════════════════════════════════════════

import { Ratelimit } from "@upstash/ratelimit";

const ratelimit = new Ratelimit({
  redis,
  limiter: Ratelimit.slidingWindow(10, "10 s"), // 10 requests per 10 seconds
  analytics: true,
});

async function checkRateLimit(identifier) {
  const { success, limit, remaining, reset } = await ratelimit.limit(
    identifier
  );

  if (!success) {
    throw new Error("Rate limit exceeded");
  }

  return { remaining, reset };
}

// Usage in API route
app.post("/api/action", async (req, res) => {
  const ip = req.ip;

  try {
    await checkRateLimit(ip);
    // Process request
    res.json({ success: true });
  } catch (error) {
    res.status(429).json({ error: "Too many requests" });
  }
});

// Different rate limit strategies
const ratelimitStrict = new Ratelimit({
  redis,
  limiter: Ratelimit.fixedWindow(5, "1 m"), // 5 requests per minute
});

const ratelimitToken = new Ratelimit({
  redis,
  limiter: Ratelimit.tokenBucket(10, "1 m", 50), // Token bucket algorithm
});

// ═══════════════════════════════════════════
// SESSION STORAGE
// ═══════════════════════════════════════════

async function createSession(userId, sessionData) {
  const sessionId = crypto.randomUUID();
  const key = `session:${sessionId}`;

  await redis.setex(
    key,
    86400, // 24 hours
    JSON.stringify({
      userId,
      ...sessionData,
      createdAt: Date.now(),
    })
  );

  return sessionId;
}

async function getSession(sessionId) {
  const key = `session:${sessionId}`;
  const data = await redis.get(key);

  if (!data) return null;

  return typeof data === "string" ? JSON.parse(data) : data;
}

async function destroySession(sessionId) {
  const key = `session:${sessionId}`;
  await redis.del(key);
}

// ═══════════════════════════════════════════
// DISTRIBUTED LOCKS
// ═══════════════════════════════════════════

async function acquireLock(resource, ttl = 10000) {
  const lockKey = `lock:${resource}`;
  const lockId = crypto.randomUUID();

  const acquired = await redis.set(lockKey, lockId, {
    nx: true, // Only set if not exists
    px: ttl, // TTL in milliseconds
  });

  if (!acquired) return null;

  return {
    id: lockId,
    release: async () => {
      // Only release if we still own the lock
      const current = await redis.get(lockKey);
      if (current === lockId) {
        await redis.del(lockKey);
      }
    },
  };
}

// Usage
const lock = await acquireLock("critical-section", 5000);
if (!lock) {
  throw new Error("Could not acquire lock");
}

try {
  // Critical section
  await performCriticalOperation();
} finally {
  await lock.release();
}

// ═══════════════════════════════════════════
// PUB/SUB (Real-time messaging)
// ═══════════════════════════════════════════

// Publisher
await redis.publish(
  "notifications",
  JSON.stringify({
    type: "new_message",
    userId: "123",
    message: "Hello!",
  })
);

// Subscriber (in separate process/worker)
const subscriber = redis.duplicate();
await subscriber.subscribe("notifications", (message) => {
  const data = JSON.parse(message);
  console.log("Received:", data);
});
```

#### 💡 Upstash Pro Tips

```javascript
// ═══════════════════════════════════════════
// BEST PRACTICES
// ═══════════════════════════════════════════

// 1. Use pipelines for multiple commands
const pipeline = redis.pipeline();
pipeline.set("key1", "value1");
pipeline.set("key2", "value2");
pipeline.incr("counter");
await pipeline.exec();

// 2. Set appropriate TTLs
// - Sessions: 24 hours
// - Cache: 5-60 minutes
// - Rate limits: Based on window

// 3. Use namespace prefixes
const CACHE_PREFIX = "cache:";
const SESSION_PREFIX = "session:";
const LOCK_PREFIX = "lock:";

await redis.set(`${CACHE_PREFIX}posts`, data);

// 4. Monitor usage
// Dashboard → Metrics
// - Commands per second
// - Memory usage
// - Hit rate

// 5. Use global replication for low latency
// Enable in Upstash dashboard

// 6. Handle errors gracefully
try {
  const value = await redis.get("key");
} catch (error) {
  console.error("Redis error:", error);
  // Fallback to database or return stale data
}

// ═══════════════════════════════════════════
// COST OPTIMIZATION
// ═══════════════════════════════════════════

// 1. Use longer TTLs for static data
await redis.setex("config", 86400, data); // 24 hours

// 2. Batch operations with pipeline
// Counts as fewer commands

// 3. Use appropriate data structures
// - String: Simple values
// - Hash: Objects
// - Set: Unique items
// - Sorted Set: Ranked data

// 4. Delete expired keys
// Upstash automatically deletes expired keys

// 5. Monitor command count
// Upstash dashboard → Usage
```

---

<div align="center">

## 🔥 Firebase & Firestore

_Google's real-time database platform_ 📱

</div>

### 🔥 Firebase

**Complete app development platform with real-time database**

```
🌐 Website → https://firebase.google.com
🎯 Best For → Mobile apps, real-time features, rapid development
💰 Pricing  → Free: 1GB storage, 50k reads/day
             Paid: Pay-as-you-go (Blaze plan)
⚡ Features → Firestore, Auth, Storage, Functions, Hosting
🔧 Support  → JavaScript, iOS, Android, Flutter, Unity
```

#### 📥 Firebase Setup

```bash
# ═══════════════════════════════════════════
# INSTALLATION
# ═══════════════════════════════════════════

# Install Firebase SDK
npm install firebase

# Install Firebase Admin SDK (for server-side)
npm install firebase-admin

# Install Firebase CLI
npm install -g firebase-tools

# Login
firebase login

# Initialize project
firebase init

# Deploy
firebase deploy
```

#### 📝 Firebase Configuration

```javascript
// ═══════════════════════════════════════════
// Client-side Firebase Setup
// ═══════════════════════════════════════════

import { initializeApp } from "firebase/app";
import {
  getFirestore,
  collection,
  doc,
  getDocs,
  getDoc,
  addDoc,
  setDoc,
  updateDoc,
  deleteDoc,
  query,
  where,
  orderBy,
  limit,
  onSnapshot,
} from "firebase/firestore";
import {
  getAuth,
  createUserWithEmailAndPassword,
  signInWithEmailAndPassword,
  signOut,
  onAuthStateChanged,
} from "firebase/auth";
import { getStorage, ref, uploadBytes, getDownloadURL } from "firebase/storage";

// Firebase config (from Firebase Console)
const firebaseConfig = {
  apiKey: process.env.NEXT_PUBLIC_FIREBASE_API_KEY,
  authDomain: process.env.NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN,
  projectId: process.env.NEXT_PUBLIC_FIREBASE_PROJECT_ID,
  storageBucket: process.env.NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET,
  messagingSenderId: process.env.NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID,
  appId: process.env.NEXT_PUBLIC_FIREBASE_APP_ID,
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
const db = getFirestore(app);
const auth = getAuth(app);
const storage = getStorage(app);

// ═══════════════════════════════════════════
// FIRESTORE CRUD OPERATIONS
// ═══════════════════════════════════════════

// CREATE (add with auto-generated ID)
async function createPost(data) {
  const docRef = await addDoc(collection(db, "posts"), {
    title: data.title,
    content: data.content,
    authorId: data.authorId,
    createdAt: new Date(),
    published: false,
  });

  console.log("Document created with ID:", docRef.id);
  return docRef.id;
}

// CREATE (set with custom ID)
async function createUserProfile(userId, data) {
  await setDoc(doc(db, "users", userId), {
    name: data.name,
    email: data.email,
    createdAt: new Date(),
  });
}

// READ (single document)
async function getPost(postId) {
  const docRef = doc(db, "posts", postId);
  const docSnap = await getDoc(docRef);

  if (docSnap.exists()) {
    return { id: docSnap.id, ...docSnap.data() };
  } else {
    throw new Error("Post not found");
  }
}

// READ (all documents)
async function getAllPosts() {
  const querySnapshot = await getDocs(collection(db, "posts"));
  const posts = [];

  querySnapshot.forEach((doc) => {
    posts.push({ id: doc.id, ...doc.data() });
  });

  return posts;
}

// READ (with query)
async function getPublishedPosts() {
  const q = query(
    collection(db, "posts"),
    where("published", "==", true),
    orderBy("createdAt", "desc"),
    limit(10)
  );

  const querySnapshot = await getDocs(q);
  const posts = [];

  querySnapshot.forEach((doc) => {
    posts.push({ id: doc.id, ...doc.data() });
  });

  return posts;
}

// UPDATE
async function updatePost(postId, updates) {
  const docRef = doc(db, "posts", postId);
  await updateDoc(docRef, {
    ...updates,
    updatedAt: new Date(),
  });
}

// DELETE
async function deletePost(postId) {
  await deleteDoc(doc(db, "posts", postId));
}

// ═══════════════════════════════════════════
// REAL-TIME LISTENERS
// ═══════════════════════════════════════════

// Listen to single document
function listenToPost(postId, callback) {
  const unsubscribe = onSnapshot(
    doc(db, "posts", postId),
    (doc) => {
      if (doc.exists()) {
        callback({ id: doc.id, ...doc.data() });
      }
    },
    (error) => {
      console.error("Error listening to post:", error);
    }
  );

  return unsubscribe; // Call to stop listening
}

// Listen to collection with query
function listenToPosts(callback) {
  const q = query(
    collection(db, "posts"),
    where("published", "==", true),
    orderBy("createdAt", "desc")
  );

  const unsubscribe = onSnapshot(q, (querySnapshot) => {
    const posts = [];
    querySnapshot.forEach((doc) => {
      posts.push({ id: doc.id, ...doc.data() });
    });
    callback(posts);
  });

  return unsubscribe;
}

// Usage in React
import { useEffect, useState } from "react";

function Posts() {
  const [posts, setPosts] = useState([]);

  useEffect(() => {
    const unsubscribe = listenToPosts(setPosts);
    return () => unsubscribe(); // Cleanup
  }, []);

  return (
    <div>
      {posts.map((post) => (
        <div key={post.id}>{post.title}</div>
      ))}
    </div>
  );
}

// ═══════════════════════════════════════════
// AUTHENTICATION
// ═══════════════════════════════════════════

// Sign up
async function signUp(email, password) {
  const userCredential = await createUserWithEmailAndPassword(
    auth,
    email,
    password
  );
  return userCredential.user;
}

// Sign in
async function signIn(email, password) {
  const userCredential = await signInWithEmailAndPassword(
    auth,
    email,
    password
  );
  return userCredential.user;
}

// Sign out
async function logout() {
  await signOut(auth);
}

// Listen to auth state
onAuthStateChanged(auth, (user) => {
  if (user) {
    console.log("User signed in:", user.uid);
  } else {
    console.log("User signed out");
  }
});

// Get current user
const currentUser = auth.currentUser;

// ═══════════════════════════════════════════
// FILE STORAGE
// ═══════════════════════════════════════════

// Upload file
async function uploadFile(file, path) {
  const storageRef = ref(storage, path);
  const snapshot = await uploadBytes(storageRef, file);
  const downloadURL = await getDownloadURL(snapshot.ref);
  return downloadURL;
}

// Usage
async function uploadAvatar(file, userId) {
  const url = await uploadFile(file, `avatars/${userId}`);

  // Update user profile with avatar URL
  await updateDoc(doc(db, "users", userId), {
    avatarUrl: url,
  });

  return url;
}

// ═══════════════════════════════════════════
// SUBCOLLECTIONS
// ═══════════════════════════════════════════

// Add comment to post
async function addComment(postId, commentData) {
  const commentsRef = collection(db, "posts", postId, "comments");
  const docRef = await addDoc(commentsRef, {
    text: commentData.text,
    authorId: commentData.authorId,
    createdAt: new Date(),
  });
  return docRef.id;
}

// Get comments for post
async function getComments(postId) {
  const commentsRef = collection(db, "posts", postId, "comments");
  const q = query(commentsRef, orderBy("createdAt", "desc"));
  const querySnapshot = await getDocs(q);

  const comments = [];
  querySnapshot.forEach((doc) => {
    comments.push({ id: doc.id, ...doc.data() });
  });

  return comments;
}

// ═══════════════════════════════════════════
// BATCH OPERATIONS
// ═══════════════════════════════════════════

import { writeBatch } from "firebase/firestore";

async function batchUpdate() {
  const batch = writeBatch(db);

  // Add multiple operations
  const ref1 = doc(db, "posts", "post1");
  batch.update(ref1, { published: true });

  const ref2 = doc(db, "posts", "post2");
  batch.update(ref2, { published: true });

  const ref3 = doc(db, "posts", "post3");
  batch.delete(ref3);

  // Commit batch (atomic operation)
  await batch.commit();
}

// ═══════════════════════════════════════════
// TRANSACTIONS
// ═══════════════════════════════════════════

import { runTransaction } from "firebase/firestore";

async function transferPoints(fromUserId, toUserId, amount) {
  await runTransaction(db, async (transaction) => {
    const fromRef = doc(db, "users", fromUserId);
    const toRef = doc(db, "users", toUserId);

    const fromDoc = await transaction.get(fromRef);
    const toDoc = await transaction.get(toRef);

    if (!fromDoc.exists() || !toDoc.exists()) {
      throw new Error("User not found");
    }

    const fromPoints = fromDoc.data().points;
    const toPoints = toDoc.data().points;

    if (fromPoints < amount) {
      throw new Error("Insufficient points");
    }

    transaction.update(fromRef, { points: fromPoints - amount });
    transaction.update(toRef, { points: toPoints + amount });
  });
}

// ═══════════════════════════════════════════
// SECURITY RULES (Firestore Rules)
// ═══════════════════════════════════════════

/*
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Users can read/write their own profile
    match /users/{userId} {
      allow read: if true;
      allow write: if request.auth != null && request.auth.uid == userId;
    }

    // Posts
    match /posts/{postId} {
      // Anyone can read published posts
      allow read: if resource.data.published == true;

      // Authors can read their own posts
      allow read: if request.auth != null
                  && request.auth.uid == resource.data.authorId;

      // Authenticated users can create posts
      allow create: if request.auth != null
                    && request.resource.data.authorId == request.auth.uid;

      // Authors can update their own posts
      allow update: if request.auth != null
                    && request.auth.uid == resource.data.authorId;

      // Authors can delete their own posts
      allow delete: if request.auth != null
                    && request.auth.uid == resource.data.authorId;

      // Comments subcollection
      match /comments/{commentId} {
        allow read: if true;
        allow create: if request.auth != null;
        allow update, delete: if request.auth != null
                              && request.auth.uid == resource.data.authorId;
      }
    }
  }
}
*/
```

#### 💡 Firebase Pro Tips

```javascript
// ═══════════════════════════════════════════
// PERFORMANCE OPTIMIZATION
// ═══════════════════════════════════════════

// 1. Use indexes for complex queries
// Firebase will prompt you to create them
// Or create manually in Firebase Console

// 2. Denormalize data for faster reads
// Instead of joins, duplicate data
const post = {
  id: "post1",
  title: "My Post",
  author: {
    id: "user1",
    name: "MrDib",
    avatar: "url",
  },
};

// 3. Use pagination
import { startAfter, getDocs, query, limit } from "firebase/firestore";

async function getPaginatedPosts(lastDoc = null, pageSize = 10) {
  let q = query(
    collection(db, "posts"),
    orderBy("createdAt", "desc"),
    limit(pageSize)
  );

  if (lastDoc) {
    q = query(q, startAfter(lastDoc));
  }

  const snapshot = await getDocs(q);
  const posts = [];
  let lastVisible = null;

  snapshot.forEach((doc) => {
    posts.push({ id: doc.id, ...doc.data() });
    lastVisible = doc;
  });

  return { posts, lastVisible };
}

// 4. Use offline persistence
import { enableIndexedDbPersistence } from "firebase/firestore";

enableIndexedDbPersistence(db).catch((err) => {
  if (err.code === "failed-precondition") {
    console.log("Multiple tabs open");
  } else if (err.code === "unimplemented") {
    console.log("Browser not supported");
  }
});

// ═══════════════════════════════════════════
// COST OPTIMIZATION
// ═══════════════════════════════════════════

// 1. Minimize reads with listeners
// Instead of polling, use onSnapshot

// 2. Use get() instead of onSnapshot when real-time not needed
const posts = await getDocs(collection(db, "posts"));

// 3. Limit query results
const q = query(collection(db, "posts"), limit(10));

// 4. Use indexes to avoid full collection scans

// 5. Monitor usage in Firebase Console
// Usage and billing → Usage

// ═══════════════════════════════════════════
// SERVER-SIDE (ADMIN SDK)
// ═══════════════════════════════════════════

// Use Admin SDK for server-side operations
import admin from "firebase-admin";

admin.initializeApp({
  credential: admin.credential.cert({
    projectId: process.env.FIREBASE_PROJECT_ID,
    clientEmail: process.env.FIREBASE_CLIENT_EMAIL,
    privateKey: process.env.FIREBASE_PRIVATE_KEY.replace(/\\n/g, "\n"),
  }),
});

const db = admin.firestore();

// No security rules apply - full access
const users = await db.collection("users").get();

// Verify ID token
const decodedToken = await admin.auth().verifyIdToken(idToken);
const uid = decodedToken.uid;
```

---

<div align="center">

## 🌍 Distributed Databases

_Global scale and high availability_ 🌐

</div>

### Comparison Overview

```
═══════════════════════════════════════════════════════════
DISTRIBUTED DATABASE COMPARISON
═══════════════════════════════════════════════════════════

┌──────────────┬─────────────┬──────────────┬─────────────┐
│ Feature      │ CockroachDB │ FaunaDB      │ DynamoDB    │
├──────────────┼─────────────┼──────────────┼─────────────┤
│ Type         │ SQL         │ Document     │ Key-Value   │
├──────────────┼─────────────┼──────────────┼─────────────┤
│ Consistency  │ Strong      │ Strong       │ Eventual/   │
│              │             │              │ Strong      │
├──────────────┼─────────────┼──────────────┼─────────────┤
│ Multi-region │ ✅ Native   │ ✅ Native    │ ✅ Setup    │
├──────────────┼─────────────┼──────────────┼─────────────┤
│ Scaling      │ Horizontal  │ Serverless   │ Automatic   │
├──────────────┼─────────────┼──────────────┼─────────────┤
│ Query Lang   │ SQL         │ FQL/GraphQL  │ PartiQL     │
├──────────────┼─────────────┼──────────────┼─────────────┤
│ Use Case     │ RDBMS alt   │ Serverless   │ AWS apps    │
├──────────────┼─────────────┼──────────────┼─────────────┤
│ Free Tier    │ Limited     │ Generous     │ 25GB        │
└──────────────┴─────────────┴──────────────┴─────────────┘

🎯 CHOOSE COCKROACHDB IF:
• Need SQL with global distribution
• Replacing PostgreSQL at scale
• Strong consistency required
• Complex transactions needed

🎯 CHOOSE FAUNADB IF:
• Building serverless apps
• Need flexible schema
• GraphQL API preferred
• Pay-per-use model

🎯 CHOOSE DYNAMODB IF:
• Deep AWS integration
• Key-value access patterns
• Need predictable low latency
• AWS expertise available
```

---

<div align="center">

## 🔄 Database Migration

_Moving data safely and efficiently_ 🚚

</div>

### Migration Strategies

```bash
# ═══════════════════════════════════════════
# SCHEMA MIGRATIONS (SQL)
# ═══════════════════════════════════════════

# Using Prisma Migrate
npx prisma migrate dev --name add_users_table
npx prisma migrate deploy

# Using Knex.js
npx knex migrate:make add_users_table
npx knex migrate:latest
npx knex migrate:rollback

# Using Flyway
flyway migrate
flyway undo

# ═══════════════════════════════════════════
# DATA MIGRATION BETWEEN DATABASES
# ═══════════════════════════════════════════

# Export from PostgreSQL
pg_dump -h source-host -U user -d dbname > backup.sql

# Import to new PostgreSQL
psql -h target-host -U user -d dbname < backup.sql

# MongoDB export
mongodump --uri="mongodb://source-uri" --out=/backup

# MongoDB import
mongorestore --uri="mongodb://target-uri" /backup

# ═══════════════════════════════════════════
# MIGRATION TOOLS
# ═══════════════════════════════════════════

# pgLoader (PostgreSQL to anything)
brew install pgloader

# Example: MySQL to PostgreSQL
pgloader mysql://user:pass@localhost/dbname \
         postgresql://user:pass@localhost/dbname

# AWS Database Migration Service (DMS)
# For large-scale migrations
# Supports: Oracle, SQL Server, MySQL, PostgreSQL, MongoDB
```

### Migration Example Scripts

```javascript
// ═══════════════════════════════════════════
// DATA MIGRATION SCRIPT (MongoDB to PostgreSQL)
// ═══════════════════════════════════════════

import { MongoClient } from "mongodb";
import { Pool } from "pg";

const mongoClient = new MongoClient(process.env.MONGODB_URI);
const pgPool = new Pool({ connectionString: process.env.DATABASE_URL });

async function migrateUsers() {
  try {
    await mongoClient.connect();
    const mongodb = mongoClient.db("myapp");
    const users = mongodb.collection("users");

    // Get all users from MongoDB
    const cursor = users.find();
    let count = 0;

    while (await cursor.hasNext()) {
      const user = await cursor.next();

      // Insert into PostgreSQL
      await pgPool.query(
        `INSERT INTO users (id, name, email, created_at)
         VALUES ($1, $2, $3, $4)
         ON CONFLICT (id) DO NOTHING`,
        [user._id.toString(), user.name, user.email, user.createdAt]
      );

      count++;
      if (count % 100 === 0) {
        console.log(`Migrated ${count} users...`);
      }
    }

    console.log(`✅ Migration complete: ${count} users`);
  } catch (error) {
    console.error("❌ Migration failed:", error);
  } finally {
    await mongoClient.close();
    await pgPool.end();
  }
}

migrateUsers();

// ═══════════════════════════════════════════
// ZERO-DOWNTIME MIGRATION STRATEGY
// ═══════════════════════════════════════════

/*
DUAL-WRITE PATTERN:

Phase 1: Setup
┌──────────────┐
│ Application  │
│    ↓         │
│  Old DB      │
└──────────────┘

Phase 2: Dual Write (start writing to both)
┌──────────────┐
│ Application  │
│    ↓   ↓     │
│  Old   New   │
│   DB    DB   │
└──────────────┘

Phase 3: Backfill (copy old data to new)
┌──────────────┐
│ Application  │
│    ↓   ↓     │
│  Old   New   │
│   DB    DB   │
│     ↓       │
│  Migration   │
│   Script     │
└──────────────┘

Phase 4: Read from New (verify)
┌──────────────┐
│ Application  │
│    ↓   ↓     │
│  Old   New   │← Read from here
│   DB    DB   │
└──────────────┘

Phase 5: Stop dual write
┌──────────────┐
│ Application  │
│       ↓      │
│      New     │
│       DB     │
└──────────────┘

Phase 6: Remove old DB
*/

// Implementation example
class DualWriteUserRepository {
  constructor(oldDb, newDb) {
    this.oldDb = oldDb;
    this.newDb = newDb;
    this.readFromNew = process.env.READ_FROM_NEW === "true";
  }

  async create(userData) {
    // Write to both databases
    const [oldResult, newResult] = await Promise.all([
      this.oldDb.users.insertOne(userData),
      this.newDb.query("INSERT INTO users ..."),
    ]);

    return this.readFromNew ? newResult : oldResult;
  }

  async findById(id) {
    if (this.readFromNew) {
      // Try new DB first
      const result = await this.newDb.query(
        "SELECT * FROM users WHERE id = $1",
        [id]
      );
      if (result.rows.length > 0) return result.rows[0];

      // Fallback to old DB
      return await this.oldDb.users.findOne({ _id: id });
    } else {
      return await this.oldDb.users.findOne({ _id: id });
    }
  }
}
```

---

<div align="center">

## 🔐 Security Best Practices

_Protect your data_ 🛡️

</div>

### Security Checklist

```bash
# ═══════════════════════════════════════════
# CONNECTION SECURITY
# ═══════════════════════════════════════════

✅ Always use SSL/TLS connections
   postgresql://user:pass@host/db?sslmode=require

✅ Never commit connection strings to Git
   Use environment variables

✅ Rotate database passwords regularly
   Update every 90 days minimum

✅ Use connection pooling with limits
   Prevent connection exhaustion attacks

✅ Restrict database access by IP
   Whitelist only necessary IPs

# ═══════════════════════════════════════════
# AUTHENTICATION & AUTHORIZATION
# ═══════════════════════════════════════════

✅ Use separate database users per service
   app-user (read/write)
   readonly-user (read only)
   admin-user (full access)

✅ Grant minimum required permissions
   GRANT SELECT, INSERT ON users TO app_user;

✅ Never use root/admin credentials in apps
   Create dedicated service accounts

✅ Implement Row-Level Security (RLS)
   PostgreSQL/Supabase feature

# ═══════════════════════════════════════════
# SQL INJECTION PREVENTION
# ═══════════════════════════════════════════

# ❌ NEVER do this (vulnerable to SQL injection)
const query = `SELECT * FROM users WHERE email = '${userInput}'`;

# ✅ ALWAYS use parameterized queries
const { rows } = await pool.query(
  'SELECT * FROM users WHERE email = $1',
  [userInput]
);

# ✅ Use ORMs with built-in protection
const user = await prisma.user.findUnique({
  where: { email: userInput }
});

# ═══════════════════════════════════════════
# DATA ENCRYPTION
# ═══════════════════════════════════════════

✅ Encrypt data at rest
   Enable in database settings

✅ Encrypt data in transit (SSL/TLS)
   Enforce encrypted connections

✅ Encrypt sensitive fields (app-level)
   Passwords, SSN, credit cards

# Example: Encrypt sensitive data
import crypto from 'crypto';

const algorithm = 'aes-256-gcm';
const key = Buffer.from(process.env.ENCRYPTION_KEY, 'hex');

function encrypt(text) {
  const iv = crypto.randomBytes(16);
  const cipher = crypto.createCipheriv(algorithm, key, iv);

  let encrypted = cipher.update(text, 'utf8', 'hex');
  encrypted += cipher.final('hex');

  const authTag = cipher.getAuthTag();

  return {
    encrypted,
    iv: iv.toString('hex'),
    authTag: authTag.toString('hex')
  };
}

function decrypt(encrypted, iv, authTag) {
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

# ═══════════════════════════════════════════
# BACKUP & DISASTER RECOVERY
# ═══════════════════════════════════════════

✅ Enable automatic backups
   Daily minimum, hourly for critical data

✅ Test restore procedures regularly
   Verify backups actually work

✅ Store backups in different region/provider
   Protection against regional outages

✅ Encrypt backup files
   Prevent data leaks from backups

# ═══════════════════════════════════════════
# MONITORING & AUDITING
# ═══════════════════════════════════════════

✅ Enable query logging
   Track suspicious queries

✅ Monitor failed login attempts
   Detect brute force attacks

✅ Set up alerts for unusual activity
   Large data exports, schema changes

✅ Regular security audits
   Review permissions, users, queries

# ═══════════════════════════════════════════
# COMPLIANCE
# ═══════════════════════════════════════════

✅ GDPR compliance (if EU users)
   - Right to deletion
   - Right to export data
   - Data retention policies

✅ PCI DSS (if handling payment data)
   - Encrypt card data
   - Secure network
   - Regular testing

✅ HIPAA (if healthcare data)
   - Access controls
   - Audit trails
   - Encryption
```

---

<div align="center">

## 📊 Performance Optimization

_Make your database blazing fast_ ⚡

</div>

### Optimization Strategies

```sql
-- ═══════════════════════════════════════════
-- INDEXING (Most Important!)
-- ═══════════════════════════════════════════

-- Single column index
CREATE INDEX idx_users_email ON users(email);

-- Composite index (order matters!)
CREATE INDEX idx_posts_user_created ON posts(user_id, created_at DESC);

-- Partial index (smaller, faster)
CREATE INDEX idx_posts_published ON posts(published)
WHERE published = true;

-- Full-text search index (PostgreSQL)
CREATE INDEX idx_posts_search ON posts
USING gin(to_tsvector('english', title || ' ' || content));

-- View index usage
-- PostgreSQL
SELECT
    schemaname,
    tablename,
    indexname,
    idx_scan as index_scans,
    idx_tup_read as tuples_read,
    idx_tup_fetch as tuples_fetched
FROM pg_stat_user_indexes
ORDER BY idx_scan DESC;

-- ═══════════════════════════════════════════
-- QUERY OPTIMIZATION
-- ═══════════════════════════════════════════

-- Use EXPLAIN to analyze queries
EXPLAIN ANALYZE
SELECT * FROM posts
WHERE user_id = 123
AND published = true
ORDER BY created_at DESC;

-- Avoid SELECT *
-- ❌ Bad
SELECT * FROM users;

-- ✅ Good
SELECT id, name, email FROM users;

-- Use LIMIT for large result sets
SELECT * FROM posts
WHERE published = true
ORDER BY created_at DESC
LIMIT 20;

-- Use COUNT(*) efficiently
-- ❌ Slow for large tables
SELECT COUNT(*) FROM posts;

-- ✅ Faster (if approximate is okay)
SELECT reltuples::bigint AS estimate
FROM pg_class
WHERE relname = 'posts';

-- Avoid N+1 queries
-- ❌ Bad (N+1 queries)
const posts = await db.query('SELECT * FROM posts');
for (const post of posts) {
    post.author = await db.query(
        'SELECT * FROM users WHERE id = $1',
        [post.user_id]
    );
}

-- ✅ Good (1 query with JOIN)
SELECT
    posts.*,
    users.name as author_name,
    users.email as author_email
FROM posts
JOIN users ON posts.user_id = users.id;

-- ═══════════════════════════════════════════
-- CONNECTION POOLING
-- ═══════════════════════════════════════════

import { Pool } from 'pg';

const pool = new Pool({
    connectionString: process.env.DATABASE_URL,
    max: 20,                    // Maximum connections
    idleTimeoutMillis: 30000,   // Close idle connections after 30s
    connectionTimeoutMillis: 2000, // Timeout for new connections
});

// ═══════════════════════════════════════════
-- CACHING
-- ═══════════════════════════════════════════

-- Application-level caching with Redis
import { Redis } from '@upstash/redis';

const redis = new Redis({
    url: process.env.UPSTASH_REDIS_REST_URL,
    token: process.env.UPSTASH_REDIS_REST_TOKEN
});

async function getCachedPosts() {
    const cacheKey = 'posts:recent';

    // Try cache first
    const cached = await redis.get(cacheKey);
    if (cached) {
        return JSON.parse(cached);
    }

    // Query database
    const posts = await db.query(`
        SELECT * FROM posts
        WHERE published = true
        ORDER BY created_at DESC
        LIMIT 20
    `);

    // Cache for 5 minutes
    await redis.setex(cacheKey, 300, JSON.stringify(posts));

    return posts;
}

-- ═══════════════════════════════════════════
-- PAGINATION
-- ═══════════════════════════════════════════

-- Offset pagination (simple but slow for large offsets)
SELECT * FROM posts
ORDER BY created_at DESC
LIMIT 20 OFFSET 100;

-- Cursor-based pagination (faster)
SELECT * FROM posts
WHERE created_at < '2024-01-01 12:00:00'
ORDER BY created_at DESC
LIMIT 20;

-- ═══════════════════════════════════════════
-- DENORMALIZATION (For Read-Heavy Workloads)
-- ═══════════════════════════════════════════

-- Instead of joining every time
SELECT posts.*, users.name
FROM posts
JOIN users ON posts.user_id = users.id;

-- Store author name in posts table
CREATE TABLE posts (
    id SERIAL PRIMARY KEY,
    title TEXT,
    user_id INT,
    author_name TEXT, -- Denormalized!
    created_at TIMESTAMP
);

-- Update when user changes name (trade-off)
UPDATE posts SET author_name = 'New Name' WHERE user_id = 123;

-- ═══════════════════════════════════════════
-- MONITORING SLOW QUERIES
-- ═══════════════════════════════════════════

-- PostgreSQL: Log slow queries
-- In postgresql.conf:
-- log_min_duration_statement = 1000  # Log queries > 1 second

-- Query to find slow queries
SELECT
    calls,
    total_time,
    mean_time,
    query
FROM pg_stat_statements
ORDER BY mean_time DESC
LIMIT 10;
```

---

<div align="center">

## 💰 Cost Optimization

_Save money without sacrificing performance_ 💸

</div>

### Cost-Saving Strategies

```bash
# ═══════════════════════════════════════════
# RIGHT-SIZING YOUR DATABASE
# ═══════════════════════════════════════════

# Don't over-provision
# Start small, scale up when needed

# PostgreSQL/MySQL:
# - Small project: 512MB-1GB RAM
# - Medium project: 2-4GB RAM
# - Large project: 8GB+ RAM

# Monitor actual usage:
# - CPU utilization (should be <70% avg)
# - Memory usage (should have headroom)
# - Storage growth rate

# ═══════════════════════════════════════════
# STORAGE OPTIMIZATION
# ═══════════════════════════════════════════

# 1. Archive old data
# Move historical data to cheaper storage (S3, etc.)

# PostgreSQL: Create archive table
CREATE TABLE posts_archive (LIKE posts INCLUDING ALL);

# Move old posts (older than 2 years)
INSERT INTO posts_archive
SELECT * FROM posts
WHERE created_at < NOW() - INTERVAL '2 years';

DELETE FROM posts
WHERE created_at < NOW() - INTERVAL '2 years';

# 2. Vacuum database regularly
# PostgreSQL
VACUUM ANALYZE posts;

# 3. Delete unused indexes
# Find unused indexes
SELECT schemaname, tablename, indexname
FROM pg_stat_user_indexes
WHERE idx_scan = 0
AND indexname NOT LIKE '%_pkey';

# Drop unused index
DROP INDEX IF EXISTS idx_unused;

# 4. Compress old data
# Use PostgreSQL TOAST compression
ALTER TABLE posts
ALTER COLUMN content SET STORAGE EXTENDED;

# ═══════════════════════════════════════════
# CONNECTION OPTIMIZATION
# ═══════════════════════════════════════════

# Use connection pooling (PgBouncer for PostgreSQL)
# Reduces connection overhead

# For serverless: Use HTTP-based queries
# - Neon serverless driver
# - Upstash Redis REST API

# ═══════════════════════════════════════════
# READ REPLICAS (Only if needed!)
# ═══════════════════════════════════════════

# Use read replicas for:
# - Separating read from write load
# - Running analytics queries
# - Geographic distribution

# Don't use read replicas if:
# - You have low traffic
# - Caching would be cheaper
# - Your app is simple

# ═══════════════════════════════════════════
# CHOOSE THE RIGHT DATABASE TYPE
# ═══════════════════════════════════════════

# Serverless databases (Neon, PlanetScale) for:
# - Variable traffic
# - Development environments
# - Pay for what you use

# Dedicated databases for:
# - Consistent high traffic
# - Predictable workloads
# - Better cost at scale

# ═══════════════════════════════════════════
# MONITORING & ALERTS
# ═══════════════════════════════════════════

# Set up billing alerts
# - 50% of budget
# - 80% of budget
# - 100% of budget

# Monitor key metrics:
# - Storage growth rate
# - Query volume
# - Connection count
# - Cache hit rate
```

---

<div align="center">

## 🔧 Backup & Recovery

_Protect your data_ 💾

</div>

### Backup Strategies

```bash
# ═══════════════════════════════════════════
# POSTGRESQL BACKUPS
# ═══════════════════════════════════════════

# Full backup (pg_dump)
pg_dump -h hostname -U username -d database > backup.sql

# With compression
pg_dump -h hostname -U username -d database | gzip > backup.sql.gz

# Custom format (faster restore)
pg_dump -h hostname -U username -Fc database > backup.dump

# Restore from backup
psql -h hostname -U username -d database < backup.sql
# Or custom format
pg_restore -h hostname -U username -d database backup.dump

# Backup specific table
pg_dump -h hostname -U username -d database -t users > users_backup.sql

# Automated backup script
#!/bin/bash
DATE=$(date +%Y%m%d_%H%M%S)
BACKUP_DIR="/backups"
DATABASE="myapp"

pg_dump -h $DB_HOST -U $DB_USER -d $DATABASE | \
gzip > $BACKUP_DIR/${DATABASE}_${DATE}.sql.gz

# Keep only last 7 days
find $BACKUP_DIR -name "*.sql.gz" -mtime +7 -delete

# Upload to S3
aws s3 cp $BACKUP_DIR/${DATABASE}_${DATE}.sql.gz \
s3://my-backups/postgres/

# ═══════════════════════════════════════════
# MONGODB BACKUPS
# ═══════════════════════════════════════════

# Backup entire database
mongodump --uri="mongodb://user:pass@host/database" --out=/backup

# Backup specific collection
mongodump --uri="mongodb://..." --collection=users --out=/backup

# Restore
mongorestore --uri="mongodb://..." /backup

# Automated backup
#!/bin/bash
DATE=$(date +%Y%m%d_%H%M%S)
mongodump --uri="$MONGODB_URI" --out=/backup/mongo_$DATE
tar -czf /backup/mongo_$DATE.tar.gz /backup/mongo_$DATE
rm -rf /backup/mongo_$DATE

# ═══════════════════════════════════════════
# MANAGED DATABASE BACKUPS
# ═══════════════════════════════════════════

# Most managed services (Supabase, Railway, etc.) have:
# - Automatic daily backups
# - Point-in-time recovery
# - One-click restore

# Supabase: Project → Database → Backups
# Railway: Project → Database → Backups
# PlanetScale: Database → Backups

# ═══════════════════════════════════════════
# DISASTER RECOVERY PLAN
# ═══════════════════════════════════════════

# 1. Backup frequency
#    - Critical data: Hourly
#    - Normal data: Daily
#    - Archives: Weekly

# 2. Backup retention
#    - Daily: Keep 7 days
#    - Weekly: Keep 4 weeks
#    - Monthly: Keep 12 months

# 3. Test restores monthly
#    Verify backups are restorable

# 4. Document recovery procedures
#    Step-by-step guide

# 5. Calculate Recovery Point Objective (RPO)
#    How much data loss is acceptable?
#    - RPO = 0: Continuous replication
#    - RPO = 1 hour: Hourly backups
#    - RPO = 24 hours: Daily backups

# 6. Calculate Recovery Time Objective (RTO)
#    How quickly must service be restored?
#    - RTO = 1 hour: Hot standby
#    - RTO = 4 hours: Warm standby
#    - RTO = 24 hours: Cold backup
```

---

<div align="center">

## 🐛 Troubleshooting

_Common issues and solutions_ 🔧

</div>

### Common Problems

```bash
# ═══════════════════════════════════════════
# CONNECTION ISSUES
# ═══════════════════════════════════════════

# Problem: "connection refused"
# Solutions:
# 1. Check if database is running
# 2. Verify connection string
# 3. Check firewall/security groups
# 4. Ensure SSL settings are correct

# Problem: "too many connections"
# Solutions:
# 1. Implement connection pooling
# 2. Close connections properly
# 3. Increase max_connections (if needed)
# 4. Find and kill idle connections

# PostgreSQL: Find idle connections
SELECT pid, usename, state, query
FROM pg_stat_activity
WHERE state = 'idle'
AND state_change < NOW() - INTERVAL '30 minutes';

# Kill idle connections
SELECT pg_terminate_backend(pid)
FROM pg_stat_activity
WHERE state = 'idle'
AND state_change < NOW() - INTERVAL '30 minutes';

# ═══════════════════════════════════════════
# PERFORMANCE ISSUES
# ═══════════════════════════════════════════

# Problem: Slow queries
# Solutions:
# 1. Add indexes
# 2. Optimize query
# 3. Increase resources
# 4. Implement caching

# Find slow queries (PostgreSQL)
SELECT
    calls,
    mean_time,
    max_time,
    query
FROM pg_stat_statements
WHERE mean_time > 1000  -- More than 1 second
ORDER BY mean_time DESC;

# Problem: High CPU usage
# Solutions:
# 1. Optimize expensive queries
# 2. Add indexes
# 3. Reduce query frequency
# 4. Scale up resources

# Problem: Running out of storage
# Solutions:
# 1. Archive old data
# 2. Delete unnecessary data
# 3. Vacuum database
# 4. Increase storage

# PostgreSQL: Check table sizes
SELECT
    schemaname,
    tablename,
    pg_size_pretty(pg_total_relation_size(schemaname||'.'||tablename)) AS size
FROM pg_tables
WHERE schemaname NOT IN ('pg_catalog', 'information_schema')
ORDER BY pg_total_relation_size(schemaname||'.'||tablename) DESC;

# MongoDB: Check collection sizes
db.stats()
db.collection.stats()

# ═══════════════════════════════════════════
# DATA CORRUPTION
# ═══════════════════════════════════════════

# Problem: Data inconsistency
# Solutions:
# 1. Restore from backup
# 2. Use transactions properly
# 3. Implement foreign key constraints
# 4. Add validation at application level

# PostgreSQL: Check for corruption
SELECT * FROM pg_stat_database_conflicts;

# Problem: Lost data after crash
# Solutions:
# 1. Enable WAL (Write-Ahead Logging)
# 2. Use synchronous commits
# 3. Verify backup integrity
# 4. Test disaster recovery

# ═══════════════════════════════════════════
# MIGRATION ISSUES
# ═══════════════════════════════════════════

# Problem: Migration fails
# Solutions:
# 1. Test migration on staging first
# 2. Use transactions (if supported)
# 3. Create rollback plan
# 4. Migrate in batches

# Problem: Downtime during migration
# Solutions:
# 1. Use blue-green deployment
# 2. Implement dual-write pattern
# 3. Use database replication
# 4. Schedule during low-traffic

# ═══════════════════════════════════════════
# AUTHENTICATION ERRORS
# ═══════════════════════════════════════════

# Problem: "authentication failed"
# Solutions:
# 1. Verify credentials
# 2. Check user permissions
# 3. Reset password
# 4. Check IP whitelist

# PostgreSQL: Check user permissions
SELECT * FROM pg_roles WHERE rolname = 'username';

# Grant permissions
GRANT SELECT, INSERT, UPDATE ON ALL TABLES IN SCHEMA public TO username;

# ═══════════════════════════════════════════
# DEBUGGING TIPS
# ═══════════════════════════════════════════

# 1. Enable query logging
# PostgreSQL: log_statement = 'all'
# MongoDB: db.setProfilingLevel(2)

# 2. Use EXPLAIN to analyze queries
EXPLAIN ANALYZE SELECT * FROM users WHERE email = 'test@example.com';

# 3. Monitor connection pool
console.log('Pool stats:', pool.totalCount, pool.idleCount);

# 4. Check database logs
# Supabase: Project → Logs
# Railway: Service → Logs
# AWS RDS: CloudWatch Logs

# 5. Test connection locally
psql -h hostname -U username -d database
mongo "mongodb://connection-string"

# 6. Use database health check queries
-- PostgreSQL
SELECT 1;
SELECT version();

-- MongoDB
db.adminCommand({ ping: 1 })

# 7. Monitor resource usage
-- PostgreSQL: Current connections
SELECT count(*) FROM pg_stat_activity;

-- PostgreSQL: Database size
SELECT pg_database_size('database_name');

-- PostgreSQL: Cache hit ratio (should be >99%)
SELECT
    sum(heap_blks_read) as heap_read,
    sum(heap_blks_hit) as heap_hit,
    sum(heap_blks_hit) / (sum(heap_blks_hit) + sum(heap_blks_read)) as ratio
FROM pg_statio_user_tables;
```

---

<div align="center">

## 💡 Best Practices

_Production-ready database management_ ⭐

</div>

### Development Best Practices

```javascript
// ═══════════════════════════════════════════
// CONNECTION MANAGEMENT
// ═══════════════════════════════════════════

// ✅ DO: Use connection pooling
import { Pool } from 'pg';

const pool = new Pool({
  connectionString: process.env.DATABASE_URL,
  max: 20,
  idleTimeoutMillis: 30000,
  connectionTimeoutMillis: 2000,
});

// ✅ DO: Close connections properly
async function queryDatabase() {
  const client = await pool.connect();
  try {
    const result = await client.query('SELECT * FROM users');
    return result.rows;
  } finally {
    client.release(); // Always release!
  }
}

// ❌ DON'T: Create new connection for each query
// This exhausts connection limits
async function badQuery() {
  const client = new Client({ connectionString: process.env.DATABASE_URL });
  await client.connect();
  const result = await client.query('SELECT * FROM users');
  await client.end();
  return result;
}

// ═══════════════════════════════════════════
// QUERY PATTERNS
// ═══════════════════════════════════════════

// ✅ DO: Use parameterized queries (prevents SQL injection)
const { rows } = await pool.query(
  'SELECT * FROM users WHERE email = $1',
  [userEmail]
);

// ❌ DON'T: Concatenate user input into queries
const query = `SELECT * FROM users WHERE email = '${userEmail}'`; // DANGEROUS!

// ✅ DO: Use transactions for multi-step operations
const client = await pool.connect();
try {
  await client.query('BEGIN');
  await client.query('UPDATE accounts SET balance = balance - $1 WHERE id = $2', [amount, fromId]);
  await client.query('UPDATE accounts SET balance = balance + $1 WHERE id = $2', [amount, toId]);
  await client.query('COMMIT');
} catch (e) {
  await client.query('ROLLBACK');
  throw e;
} finally {
  client.release();
}

// ✅ DO: Fetch only needed columns
const { rows } = await pool.query('SELECT id, name, email FROM users');

// ❌ DON'T: Fetch everything if you don't need it
const { rows } = await pool.query('SELECT * FROM users');

// ✅ DO: Use indexes for frequently queried columns
// Add index in migration:
CREATE INDEX idx_users_email ON users(email);

// ✅ DO: Implement pagination
async function getPaginatedUsers(page = 1, limit = 20) {
  const offset = (page - 1) * limit;
  const { rows } = await pool.query(
    'SELECT * FROM users ORDER BY created_at DESC LIMIT $1 OFFSET $2',
    [limit, offset]
  );
  return rows;
}

// ═══════════════════════════════════════════
// ERROR HANDLING
// ═══════════════════════════════════════════

// ✅ DO: Handle database errors gracefully
async function safeQuery() {
  try {
    const { rows } = await pool.query('SELECT * FROM users');
    return rows;
  } catch (error) {
    console.error('Database error:', error.message);

    // Handle specific errors
    if (error.code === '23505') {
      throw new Error('Duplicate entry');
    }

    if (error.code === '23503') {
      throw new Error('Foreign key constraint violation');
    }

    // Generic error
    throw new Error('Database operation failed');
  }
}

// ✅ DO: Implement retry logic for transient errors
async function queryWithRetry(query, params, maxRetries = 3) {
  for (let i = 0; i < maxRetries; i++) {
    try {
      return await pool.query(query, params);
    } catch (error) {
      // Retry on connection errors
      if (error.code === 'ECONNREFUSED' || error.code === 'ETIMEDOUT') {
        if (i === maxRetries - 1) throw error;
        await new Promise(resolve => setTimeout(resolve, 1000 * (i + 1)));
        continue;
      }
      throw error;
    }
  }
}

// ═══════════════════════════════════════════
// SCHEMA DESIGN
// ═══════════════════════════════════════════

// ✅ DO: Normalize data appropriately
-- Good: Normalized structure
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  email VARCHAR(255) UNIQUE NOT NULL,
  name VARCHAR(255)
);

CREATE TABLE posts (
  id SERIAL PRIMARY KEY,
  user_id INT REFERENCES users(id),
  title TEXT NOT NULL,
  content TEXT,
  created_at TIMESTAMP DEFAULT NOW()
);

// ✅ DO: Add constraints
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  email VARCHAR(255) UNIQUE NOT NULL,
  age INT CHECK (age >= 0 AND age <= 120),
  created_at TIMESTAMP DEFAULT NOW() NOT NULL
);

// ✅ DO: Use appropriate data types
-- String: VARCHAR(n), TEXT
-- Numbers: INTEGER, BIGINT, DECIMAL
-- Date/Time: TIMESTAMP, DATE, TIME
-- JSON: JSONB (PostgreSQL)
-- Boolean: BOOLEAN
-- UUID: UUID

// ✅ DO: Add indexes for foreign keys
CREATE INDEX idx_posts_user_id ON posts(user_id);

// ✅ DO: Use UNIQUE constraints
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  email VARCHAR(255) UNIQUE NOT NULL,
  username VARCHAR(50) UNIQUE NOT NULL
);

// ═══════════════════════════════════════════
// ENVIRONMENT-SPECIFIC CONFIGS
// ═══════════════════════════════════════════

// ✅ DO: Use different databases per environment
// .env.development
DATABASE_URL=postgresql://localhost/myapp_dev

// .env.test
DATABASE_URL=postgresql://localhost/myapp_test

// .env.production
DATABASE_URL=postgresql://prod-host/myapp_prod

// ✅ DO: Use migrations for schema changes
// Never modify production database manually

// ✅ DO: Test migrations on staging first
// Before applying to production

// ═══════════════════════════════════════════
// SECURITY PRACTICES
// ═══════════════════════════════════════════

// ✅ DO: Store connection strings in environment variables
const connectionString = process.env.DATABASE_URL;

// ❌ DON'T: Commit credentials to Git
// Add .env to .gitignore

// ✅ DO: Use SSL/TLS in production
const pool = new Pool({
  connectionString: process.env.DATABASE_URL,
  ssl: process.env.NODE_ENV === 'production'
    ? { rejectUnauthorized: false }
    : false
});

// ✅ DO: Rotate credentials regularly
// Change passwords every 90 days

// ✅ DO: Use read-only connections for read-only operations
const readOnlyPool = new Pool({
  connectionString: process.env.READ_REPLICA_URL
});

// ═══════════════════════════════════════════
// MONITORING & LOGGING
// ═══════════════════════════════════════════

// ✅ DO: Log slow queries
const start = Date.now();
const result = await pool.query('SELECT * FROM users');
const duration = Date.now() - start;

if (duration > 1000) {
  console.warn(`Slow query (${duration}ms):`, 'SELECT * FROM users');
}

// ✅ DO: Monitor connection pool
setInterval(() => {
  console.log('Pool stats:', {
    total: pool.totalCount,
    idle: pool.idleCount,
    waiting: pool.waitingCount
  });
}, 60000);

// ✅ DO: Set up alerts for errors
// Use Sentry, Datadog, or similar

// ✅ DO: Track query performance
import { Counter, Histogram } from 'prom-client';

const queryCounter = new Counter({
  name: 'db_queries_total',
  help: 'Total number of database queries'
});

const queryDuration = new Histogram({
  name: 'db_query_duration_seconds',
  help: 'Database query duration'
});

async function monitoredQuery(query, params) {
  queryCounter.inc();
  const start = Date.now();

  try {
    return await pool.query(query, params);
  } finally {
    queryDuration.observe((Date.now() - start) / 1000);
  }
}
```

### Deployment Checklist

```bash
# ═══════════════════════════════════════════
# PRE-PRODUCTION CHECKLIST
# ═══════════════════════════════════════════

✅ Database Setup
   ☐ Created production database
   ☐ Set up SSL/TLS
   ☐ Configured firewall rules
   ☐ Whitelisted application IPs
   ☐ Created database users with minimal permissions

✅ Schema & Migrations
   ☐ All migrations tested in staging
   ☐ Rollback scripts prepared
   ☐ Indexes created for common queries
   ☐ Foreign key constraints in place
   ☐ Check constraints validated

✅ Security
   ☐ Connection strings in environment variables
   ☐ No credentials in code
   ☐ SSL/TLS enabled
   ☐ Strong passwords set
   ☐ Row-level security configured (if needed)
   ☐ Backup encryption enabled

✅ Performance
   ☐ Connection pooling configured
   ☐ Indexes created
   ☐ Query optimization done
   ☐ Caching strategy implemented
   ☐ Load testing completed

✅ Backup & Recovery
   ☐ Automatic backups enabled
   ☐ Backup retention policy set
   ☐ Restore procedure tested
   ☐ Point-in-time recovery available
   ☐ Backups stored in different region

✅ Monitoring
   ☐ Query logging enabled
   ☐ Slow query alerts set up
   ☐ Connection monitoring configured
   ☐ Storage alerts configured
   ☐ Error tracking enabled (Sentry, etc.)

✅ Documentation
   ☐ Connection instructions documented
   ☐ Schema documented
   ☐ Migration process documented
   ☐ Backup/restore procedures documented
   ☐ Troubleshooting guide created

✅ Testing
   ☐ Unit tests passing
   ☐ Integration tests passing
   ☐ Load tests completed
   ☐ Disaster recovery tested
   ☐ Failover tested (if applicable)
```

---

<div align="center">

## 🎯 Quick Reference

_Essential commands at your fingertips_ ⚡

</div>

### PostgreSQL Quick Reference

```sql
-- ═══════════════════════════════════════════
-- CONNECTION
-- ═══════════════════════════════════════════

-- Connect to database
psql -h hostname -U username -d database

-- Connection string format
postgresql://username:password@hostname:5432/database?sslmode=require

-- ═══════════════════════════════════════════
-- DATABASE OPERATIONS
-- ═══════════════════════════════════════════

-- List databases
\l

-- Connect to database
\c database_name

-- Show current database
SELECT current_database();

-- Database size
SELECT pg_size_pretty(pg_database_size('database_name'));

-- ═══════════════════════════════════════════
-- TABLE OPERATIONS
-- ═══════════════════════════════════════════

-- List tables
\dt

-- Describe table
\d table_name

-- Table size
SELECT pg_size_pretty(pg_total_relation_size('table_name'));

-- Row count
SELECT COUNT(*) FROM table_name;

-- ═══════════════════════════════════════════
-- INDEX OPERATIONS
-- ═══════════════════════════════════════════

-- List indexes
\di

-- Create index
CREATE INDEX idx_name ON table_name(column_name);

-- Drop index
DROP INDEX idx_name;

-- Unused indexes
SELECT schemaname, tablename, indexname
FROM pg_stat_user_indexes
WHERE idx_scan = 0;

-- ═══════════════════════════════════════════
-- USER & PERMISSIONS
-- ═══════════════════════════════════════════

-- List users
\du

-- Create user
CREATE USER username WITH PASSWORD 'password';

-- Grant permissions
GRANT SELECT, INSERT, UPDATE ON table_name TO username;

-- Revoke permissions
REVOKE ALL ON table_name FROM username;

-- ═══════════════════════════════════════════
-- QUERY OPTIMIZATION
-- ═══════════════════════════════════════════

-- Analyze query
EXPLAIN ANALYZE SELECT * FROM users WHERE email = 'test@example.com';

-- Vacuum table
VACUUM ANALYZE table_name;

-- Reindex
REINDEX TABLE table_name;

-- ═══════════════════════════════════════════
-- MONITORING
-- ═══════════════════════════════════════════

-- Active connections
SELECT * FROM pg_stat_activity;

-- Slow queries
SELECT query, mean_time
FROM pg_stat_statements
ORDER BY mean_time DESC
LIMIT 10;

-- Database statistics
SELECT * FROM pg_stat_database;

-- ═══════════════════════════════════════════
-- BACKUP & RESTORE
-- ═══════════════════════════════════════════

-- Backup
pg_dump -h hostname -U username database > backup.sql

-- Restore
psql -h hostname -U username database < backup.sql

-- Backup with compression
pg_dump database | gzip > backup.sql.gz

-- Restore compressed
gunzip -c backup.sql.gz | psql database
```

### MongoDB Quick Reference

```javascript
// ═══════════════════════════════════════════
// CONNECTION
// ═══════════════════════════════════════════

// Connect
mongosh "mongodb://username:password@hostname/database"

// Connection string format
mongodb+srv://username:password@cluster.mongodb.net/database

// ═══════════════════════════════════════════
// DATABASE OPERATIONS
// ═══════════════════════════════════════════

// Show databases
show dbs

// Use database
use database_name

// Current database
db.getName()

// Database stats
db.stats()

// ═══════════════════════════════════════════
// COLLECTION OPERATIONS
// ═══════════════════════════════════════════

// Show collections
show collections

// Collection stats
db.collection_name.stats()

// Count documents
db.collection_name.countDocuments()

// ═══════════════════════════════════════════
// CRUD OPERATIONS
// ═══════════════════════════════════════════

// Insert
db.users.insertOne({ name: "MrDib", email: "email@example.com" })
db.users.insertMany([{ name: "User1" }, { name: "User2" }])

// Find
db.users.find()
db.users.findOne({ email: "email@example.com" })
db.users.find({ age: { $gte: 18 } })

// Update
db.users.updateOne({ _id: ObjectId("...") }, { $set: { name: "New Name" } })
db.users.updateMany({ active: false }, { $set: { status: "inactive" } })

// Delete
db.users.deleteOne({ _id: ObjectId("...") })
db.users.deleteMany({ createdAt: { $lt: new Date("2020-01-01") } })

// ═══════════════════════════════════════════
// INDEXES
// ═══════════════════════════════════════════

// List indexes
db.collection_name.getIndexes()

// Create index
db.collection_name.createIndex({ field: 1 })  // 1 = ascending, -1 = descending

// Create compound index
db.collection_name.createIndex({ field1: 1, field2: -1 })

// Create unique index
db.collection_name.createIndex({ email: 1 }, { unique: true })

// Drop index
db.collection_name.dropIndex("index_name")

// ═══════════════════════════════════════════
// AGGREGATION
// ═══════════════════════════════════════════

// Basic aggregation
db.users.aggregate([
  { $match: { age: { $gte: 18 } } },
  { $group: { _id: "$country", count: { $sum: 1 } } },
  { $sort: { count: -1 } }
])

// ═══════════════════════════════════════════
// BACKUP & RESTORE
// ═══════════════════════════════════════════

// Backup
mongodump --uri="mongodb://..." --out=/backup

// Restore
mongorestore --uri="mongodb://..." /backup

// Backup specific collection
mongodump --uri="mongodb://..." --collection=users --out=/backup
```

### Redis Quick Reference

```bash
# ═══════════════════════════════════════════
# CONNECTION
# ═══════════════════════════════════════════

# Connect to Redis
redis-cli -h hostname -p 6379 -a password

# Test connection
PING

# ═══════════════════════════════════════════
# STRINGS
# ═══════════════════════════════════════════

# Set value
SET key value

# Get value
GET key

# Set with expiration (seconds)
SETEX key 3600 value

# Increment
INCR counter
INCRBY counter 5

# Delete
DEL key

# Check if exists
EXISTS key

# ═══════════════════════════════════════════
# LISTS
# ═══════════════════════════════════════════

# Push to list
LPUSH list value
RPUSH list value

# Pop from list
LPOP list
RPOP list

# Get range
LRANGE list 0 -1

# List length
LLEN list

# ═══════════════════════════════════════════
# SETS
# ═══════════════════════════════════════════

# Add to set
SADD set member

# Get all members
SMEMBERS set

# Check membership
SISMEMBER set member

# Set size
SCARD set

# ═══════════════════════════════════════════
# HASHES
# ═══════════════════════════════════════════

# Set hash field
HSET hash field value

# Get hash field
HGET hash field

# Get all hash
HGETALL hash

# Delete hash field
HDEL hash field

# ═══════════════════════════════════════════
# SORTED SETS
# ═══════════════════════════════════════════

# Add to sorted set
ZADD leaderboard 100 player1

# Get range
ZRANGE leaderboard 0 -1
ZREVRANGE leaderboard 0 9  # Top 10

# Get score
ZSCORE leaderboard player1

# ═══════════════════════════════════════════
# KEYS & EXPIRATION
# ═══════════════════════════════════════════

# List all keys (careful in production!)
KEYS *

# Set expiration
EXPIRE key 3600

# Check TTL
TTL key

# Remove expiration
PERSIST key

# ═══════════════════════════════════════════
# INFO & MONITORING
# ═══════════════════════════════════════════

# Server info
INFO

# Memory info
INFO memory

# Monitor commands in real-time
MONITOR

# Slow log
SLOWLOG GET 10
```

---

<div align="center">

## 🎓 Learning Resources

_Master database management_ 📚

</div>

### Official Documentation

```
🐘 PostgreSQL
   → https://postgresql.org/docs

🐬 MySQL
   → https://dev.mysql.com/doc

🍃 MongoDB
   → https://docs.mongodb.com

⚡ Redis
   → https://redis.io/docs

🔥 Firebase
   → https://firebase.google.com/docs

⚡ Supabase
   → https://supabase.com/docs

🌍 PlanetScale
   → https://planetscale.com/docs

💡 Neon
   → https://neon.tech/docs
```

### Books & Courses

```
📚 Books:
   • "PostgreSQL: Up and Running" by Regina Obe
   • "Designing Data-Intensive Applications" by Martin Kleppmann
   • "MongoDB: The Definitive Guide" by Shannon Bradshaw
   • "High Performance MySQL" by Baron Schwartz

🎓 Courses:
   • Prisma's Data Guide
   • MongoDB University (Free)
   • PostgreSQL Tutorial (postgresqltutorial.com)
   • Use The Index, Luke (indexing guide)
```

### Community & Support

```
💬 Forums & Communities:
   • Stack Overflow
   • Reddit /r/PostgreSQL, /r/mongodb
   • Discord servers (Supabase, PlanetScale)
   • Database Administrators Stack Exchange

🎥 YouTube Channels:
   • Hussein Nasser
   • Fireship
   • Traversy Media
```

---

<div align="center">

## 🎉 Conclusion

</div>

**Congratulations!** You now have a comprehensive guide to database hosting! 🚀

### Key Takeaways:

✅ **Choose Wisely**: Select database based on your use case
✅ **Start Simple**: Use managed services, scale later
✅ **Security First**: Encrypt, backup, monitor
✅ **Optimize Early**: Indexes, caching, connection pooling
✅ **Monitor Always**: Know what's happening in production
✅ **Backup Everything**: Test restores regularly
✅ **Document Well**: Future you will be grateful

### Recommended Stack by Project Type:

```
🎯 Simple Web App:
   → Supabase (PostgreSQL + Auth + Storage)
   → Upstash Redis (Caching)

🚀 SaaS Application:
   → Neon or PlanetScale (Primary DB)
   → Upstash Redis (Sessions/Cache)
   → S3 (File storage)

📱 Mobile App:
   → Firebase/Firestore (Real-time + Auth)
   → Cloud Storage (Files)

🏢 Enterprise:
   → AWS RDS/Aurora (PostgreSQL/MySQL)
   → ElastiCache (Redis)
   → S3 (Storage)

💰 Budget-Conscious:
   → Railway (All-in-one)
   → Or Supabase Free Tier
```

### Final Checklist:

```bash
✅ Database created and accessible
✅ Connection string secure (environment variable)
✅ SSL/TLS enabled
✅ Indexes created for common queries
✅ Backup strategy in place
✅ Monitoring configured
✅ Security rules/permissions set
✅ Performance tested
✅ Documentation written
✅ Team trained
```

---

<div align="center">

**Built with 💾 by MrDib for Database Engineers**

_May your queries be fast, your data be safe, and your backups always restore!_ ⚡

**Now go build something with reliable data storage!** 🎉

---

**Found this helpful? Star the repo ⭐ and share with fellow developers!**

_Happy Database Hosting!_ 🚀

</div>
