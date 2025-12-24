<div align="center">

# 🌐 API Development

### _Building robust, scalable, and secure APIs_ 🚀

![REST](https://img.shields.io/badge/REST-API-blue?style=for-the-badge)
![GraphQL](https://img.shields.io/badge/GraphQL-E10098?style=for-the-badge&logo=graphql)
![Security](https://img.shields.io/badge/Security-First-green?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 API Fundamentals](#-api-fundamentals)
- [⚡ Node.js Frameworks](#-nodejs-frameworks)
- [🔄 REST API Design](#-rest-api-design)
- [🎨 GraphQL APIs](#-graphql-apis)
- [🔐 Authentication & Authorization](#-authentication--authorization)
- [✅ Validation & Sanitization](#-validation--sanitization)
- [📚 API Documentation](#-api-documentation)
- [🛡️ Security Best Practices](#️-security-best-practices)
- [🧪 Testing APIs](#-testing-apis)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 API Fundamentals

</div>

### Understanding APIs 📖

```javascript
// ═══════════════════════════════════════════
// What is an API?
// ═══════════════════════════════════════════

/*
API (Application Programming Interface)
- Contract between client and server
- Defines how to request data
- Defines how data is returned
- Language and platform agnostic

Common API Styles:
1. REST (Representational State Transfer)
   - Resource-based URLs
   - HTTP methods (GET, POST, PUT, DELETE)
   - Stateless
   - Most common

2. GraphQL
   - Query language
   - Single endpoint
   - Client specifies exact data needed
   - Reduces over-fetching

3. RPC (Remote Procedure Call)
   - Action-based
   - gRPC, JSON-RPC
   - Often used for microservices

4. WebSocket
   - Real-time bidirectional
   - Persistent connection
   - Chat, live updates
*/

// ═══════════════════════════════════════════
// HTTP Methods & Use Cases
// ═══════════════════════════════════════════

/*
GET    - Retrieve data (Safe, Idempotent)
POST   - Create new resource
PUT    - Update entire resource (Idempotent)
PATCH  - Partial update
DELETE - Remove resource (Idempotent)
HEAD   - Get headers only
OPTIONS - Get supported methods

Idempotent: Same request multiple times = same result
Safe: Doesn't modify server state
*/

// ═══════════════════════════════════════════
// HTTP Status Codes
// ═══════════════════════════════════════════

/*
2xx - Success
  200 OK               - Request succeeded
  201 Created          - Resource created
  204 No Content       - Success, no response body

3xx - Redirection
  301 Moved Permanently
  302 Found (Temporary)
  304 Not Modified

4xx - Client Errors
  400 Bad Request      - Invalid syntax
  401 Unauthorized     - Authentication required
  403 Forbidden        - No permission
  404 Not Found        - Resource doesn't exist
  422 Unprocessable    - Validation error
  429 Too Many Requests

5xx - Server Errors
  500 Internal Server Error
  502 Bad Gateway
  503 Service Unavailable
  504 Gateway Timeout
*/
```

---

<div align="center">

## ⚡ Node.js Frameworks

</div>

### Express.js - The Minimalist 🚀

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install express
npm install cors helmet morgan compression
npm install express-validator express-rate-limit
```

```javascript
// ═══════════════════════════════════════════
// Basic Express Server
// ═══════════════════════════════════════════

import express from "express";
import cors from "cors";
import helmet from "helmet";
import morgan from "morgan";
import compression from "compression";
import rateLimit from "express-rate-limit";

const app = express();

// ═══════════════════════════════════════════
// Middleware Setup
// ═══════════════════════════════════════════

// Security headers
app.use(helmet());

// CORS
app.use(
  cors({
    origin: process.env.ALLOWED_ORIGINS?.split(","),
    credentials: true,
  })
);

// Body parsing
app.use(express.json({ limit: "10mb" }));
app.use(express.urlencoded({ extended: true, limit: "10mb" }));

// Compression
app.use(compression());

// Logging
app.use(morgan("combined"));

// Rate limiting
const limiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100, // 100 requests per windowMs
  message: "Too many requests, please try again later",
  standardHeaders: true,
  legacyHeaders: false,
});

app.use("/api/", limiter);

// ═══════════════════════════════════════════
// Routes
// ═══════════════════════════════════════════

// Health check
app.get("/health", (req, res) => {
  res.json({
    status: "OK",
    timestamp: new Date().toISOString(),
    uptime: process.uptime(),
    environment: process.env.NODE_ENV,
  });
});

// API routes
import userRoutes from "./routes/users.js";
import postRoutes from "./routes/posts.js";

app.use("/api/users", userRoutes);
app.use("/api/posts", postRoutes);

// ═══════════════════════════════════════════
// Error Handling
// ═══════════════════════════════════════════

// 404 handler
app.use((req, res) => {
  res.status(404).json({
    success: false,
    error: {
      message: "Route not found",
      path: req.path,
    },
  });
});

// Global error handler
app.use((err, req, res, next) => {
  console.error(err.stack);

  const statusCode = err.statusCode || 500;
  const message = err.message || "Internal Server Error";

  res.status(statusCode).json({
    success: false,
    error: {
      message,
      ...(process.env.NODE_ENV === "development" && {
        stack: err.stack,
      }),
    },
  });
});

// ═══════════════════════════════════════════
// Start Server
// ═══════════════════════════════════════════

const PORT = process.env.PORT || 3000;

app.listen(PORT, () => {
  console.log(`🚀 Server running on port ${PORT}`);
  console.log(`📚 Environment: ${process.env.NODE_ENV}`);
  console.log(`🔗 http://localhost:${PORT}`);
});

// Graceful shutdown
process.on("SIGTERM", () => {
  console.log("SIGTERM received, shutting down gracefully");
  process.exit(0);
});
```

**📦 Express Resources:**

- Docs: https://expressjs.com/
- Middleware: https://expressjs.com/en/resources/middleware.html

> **💡 Pro Tip:** Express is minimal by design. Add only the middleware you need to keep it fast and lean!

---

### Fastify - High Performance ⚡

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install fastify
npm install @fastify/cors @fastify/helmet @fastify/rate-limit
```

```javascript
// ═══════════════════════════════════════════
// Fastify Server
// ═══════════════════════════════════════════

import Fastify from "fastify";
import cors from "@fastify/cors";
import helmet from "@fastify/helmet";
import rateLimit from "@fastify/rate-limit";

const fastify = Fastify({
  logger: true,
  ajv: {
    customOptions: {
      removeAdditional: "all",
      coerceTypes: true,
      useDefaults: true,
    },
  },
});

// Register plugins
await fastify.register(cors);
await fastify.register(helmet);
await fastify.register(rateLimit, {
  max: 100,
  timeWindow: "15 minutes",
});

// ═══════════════════════════════════════════
// Routes with Schema Validation
// ═══════════════════════════════════════════

const userSchema = {
  type: "object",
  properties: {
    name: { type: "string", minLength: 2 },
    email: { type: "string", format: "email" },
    age: { type: "integer", minimum: 0 },
  },
  required: ["name", "email"],
};

fastify.post(
  "/api/users",
  {
    schema: {
      body: userSchema,
      response: {
        201: {
          type: "object",
          properties: {
            id: { type: "string" },
            name: { type: "string" },
            email: { type: "string" },
          },
        },
      },
    },
  },
  async (request, reply) => {
    const user = await db.users.create(request.body);
    reply.code(201).send(user);
  }
);

// ═══════════════════════════════════════════
// Hooks (Middleware)
// ═══════════════════════════════════════════

fastify.addHook("onRequest", async (request, reply) => {
  request.startTime = Date.now();
});

fastify.addHook("onResponse", async (request, reply) => {
  const duration = Date.now() - request.startTime;
  fastify.log.info(`Request took ${duration}ms`);
});

// Start server
try {
  await fastify.listen({ port: 3000 });
} catch (err) {
  fastify.log.error(err);
  process.exit(1);
}
```

**📦 Fastify Resources:**

- Docs: https://www.fastify.io/
- Why: 2x faster than Express, built-in schema validation

> **💡 Pro Tip:** Fastify's schema validation catches errors early and improves performance through JSON serialization!

---

### NestJS - Enterprise Grade 🦅

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm i -g @nestjs/cli
nest new my-api
cd my-api
npm run start:dev
```

```typescript
// ═══════════════════════════════════════════
// Controller (users.controller.ts)
// ═══════════════════════════════════════════

import {
  Controller,
  Get,
  Post,
  Put,
  Delete,
  Body,
  Param,
  Query,
  UseGuards,
  HttpCode,
  HttpStatus,
} from "@nestjs/common";
import { UsersService } from "./users.service";
import { CreateUserDto, UpdateUserDto } from "./dto";
import { JwtAuthGuard } from "../auth/guards/jwt-auth.guard";
import { RolesGuard } from "../auth/guards/roles.guard";
import { Roles } from "../auth/decorators/roles.decorator";

@Controller("users")
export class UsersController {
  constructor(private readonly usersService: UsersService) {}

  @Get()
  async findAll(
    @Query("page") page: number = 1,
    @Query("limit") limit: number = 10
  ) {
    return this.usersService.findAll({ page, limit });
  }

  @Get(":id")
  async findOne(@Param("id") id: string) {
    return this.usersService.findOne(id);
  }

  @Post()
  @HttpCode(HttpStatus.CREATED)
  async create(@Body() createUserDto: CreateUserDto) {
    return this.usersService.create(createUserDto);
  }

  @Put(":id")
  @UseGuards(JwtAuthGuard)
  async update(@Param("id") id: string, @Body() updateUserDto: UpdateUserDto) {
    return this.usersService.update(id, updateUserDto);
  }

  @Delete(":id")
  @UseGuards(JwtAuthGuard, RolesGuard)
  @Roles("admin")
  @HttpCode(HttpStatus.NO_CONTENT)
  async remove(@Param("id") id: string) {
    return this.usersService.remove(id);
  }
}

// ═══════════════════════════════════════════
// Service (users.service.ts)
// ═══════════════════════════════════════════

import { Injectable, NotFoundException } from "@nestjs/common";
import { PrismaService } from "../prisma/prisma.service";
import { CreateUserDto, UpdateUserDto } from "./dto";

@Injectable()
export class UsersService {
  constructor(private prisma: PrismaService) {}

  async findAll({ page, limit }) {
    const skip = (page - 1) * limit;

    const [users, total] = await Promise.all([
      this.prisma.user.findMany({ skip, take: limit }),
      this.prisma.user.count(),
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

  async findOne(id: string) {
    const user = await this.prisma.user.findUnique({ where: { id } });

    if (!user) {
      throw new NotFoundException(`User with ID ${id} not found`);
    }

    return user;
  }

  async create(createUserDto: CreateUserDto) {
    return this.prisma.user.create({ data: createUserDto });
  }

  async update(id: string, updateUserDto: UpdateUserDto) {
    await this.findOne(id); // Check if exists
    return this.prisma.user.update({
      where: { id },
      data: updateUserDto,
    });
  }

  async remove(id: string) {
    await this.findOne(id); // Check if exists
    await this.prisma.user.delete({ where: { id } });
  }
}

// ═══════════════════════════════════════════
// DTO (dto/create-user.dto.ts)
// ═══════════════════════════════════════════

import { IsEmail, IsString, IsInt, MinLength, Min, Max } from "class-validator";

export class CreateUserDto {
  @IsString()
  @MinLength(2)
  name: string;

  @IsEmail()
  email: string;

  @IsInt()
  @Min(0)
  @Max(150)
  age: number;
}
```

**📦 NestJS Resources:**

- Docs: https://docs.nestjs.com/
- Why: TypeScript-first, decorators, DI, batteries included

> **💡 Pro Tip:** NestJS is perfect for large teams and enterprise apps. Built-in support for GraphQL, WebSockets, microservices, and more!

---

<div align="center">

## 🔄 REST API Design

</div>

### RESTful Principles & Best Practices 📐

```javascript
// ═══════════════════════════════════════════
// URL Design Patterns
// ═══════════════════════════════════════════

/*
✅ GOOD: Resource-based URLs

GET    /api/users           - List users
GET    /api/users/:id       - Get single user
POST   /api/users           - Create user
PUT    /api/users/:id       - Update user (full)
PATCH  /api/users/:id       - Update user (partial)
DELETE /api/users/:id       - Delete user

GET    /api/users/:id/posts - Get user's posts
POST   /api/users/:id/posts - Create post for user

❌ BAD: Action-based URLs

GET    /api/getUsers
POST   /api/createUser
POST   /api/deleteUser
GET    /api/user-posts/:id
*/

// ═══════════════════════════════════════════
// Complete REST API Example
// ═══════════════════════════════════════════

import express from "express";
import { body, param, query, validationResult } from "express-validator";

const router = express.Router();

// ═══════════════════════════════════════════
// Middleware
// ═══════════════════════════════════════════

// Validation error handler
const validate = (req, res, next) => {
  const errors = validationResult(req);
  if (!errors.isEmpty()) {
    return res.status(400).json({
      success: false,
      errors: errors.array(),
    });
  }
  next();
};

// ═══════════════════════════════════════════
// GET /api/users - List with filtering & pagination
// ═══════════════════════════════════════════

router.get(
  "/",
  [
    query("page").optional().isInt({ min: 1 }),
    query("limit").optional().isInt({ min: 1, max: 100 }),
    query("search").optional().isString(),
    query("role").optional().isIn(["user", "admin", "moderator"]),
    query("sort").optional().isIn(["name", "email", "createdAt"]),
    query("order").optional().isIn(["asc", "desc"]),
  ],
  validate,
  async (req, res, next) => {
    try {
      const page = parseInt(req.query.page) || 1;
      const limit = parseInt(req.query.limit) || 10;
      const search = req.query.search;
      const role = req.query.role;
      const sort = req.query.sort || "createdAt";
      const order = req.query.order || "desc";

      const skip = (page - 1) * limit;

      // Build query
      const where = {};
      if (search) {
        where.OR = [
          { name: { contains: search, mode: "insensitive" } },
          { email: { contains: search, mode: "insensitive" } },
        ];
      }
      if (role) {
        where.role = role;
      }

      // Execute query
      const [users, total] = await Promise.all([
        db.user.findMany({
          where,
          skip,
          take: limit,
          orderBy: { [sort]: order },
          select: {
            id: true,
            name: true,
            email: true,
            role: true,
            createdAt: true,
          },
        }),
        db.user.count({ where }),
      ]);

      res.json({
        success: true,
        data: users,
        pagination: {
          page,
          limit,
          total,
          totalPages: Math.ceil(total / limit),
          hasNext: page < Math.ceil(total / limit),
          hasPrev: page > 1,
        },
      });
    } catch (error) {
      next(error);
    }
  }
);

// ═══════════════════════════════════════════
// GET /api/users/:id - Get single user
// ═══════════════════════════════════════════

router.get("/:id", [param("id").isUUID()], validate, async (req, res, next) => {
  try {
    const user = await db.user.findUnique({
      where: { id: req.params.id },
      include: {
        posts: {
          take: 5,
          orderBy: { createdAt: "desc" },
        },
      },
    });

    if (!user) {
      return res.status(404).json({
        success: false,
        error: {
          message: "User not found",
          code: "USER_NOT_FOUND",
        },
      });
    }

    res.json({
      success: true,
      data: user,
    });
  } catch (error) {
    next(error);
  }
});

// ═══════════════════════════════════════════
// POST /api/users - Create user
// ═══════════════════════════════════════════

router.post(
  "/",
  [
    body("name").trim().isLength({ min: 2, max: 100 }),
    body("email").isEmail().normalizeEmail(),
    body("password").isLength({ min: 8 }),
    body("role").optional().isIn(["user", "admin", "moderator"]),
  ],
  validate,
  async (req, res, next) => {
    try {
      // Check if email exists
      const existingUser = await db.user.findUnique({
        where: { email: req.body.email },
      });

      if (existingUser) {
        return res.status(409).json({
          success: false,
          error: {
            message: "Email already exists",
            code: "EMAIL_EXISTS",
          },
        });
      }

      // Hash password
      const hashedPassword = await bcrypt.hash(req.body.password, 10);

      // Create user
      const user = await db.user.create({
        data: {
          ...req.body,
          password: hashedPassword,
        },
        select: {
          id: true,
          name: true,
          email: true,
          role: true,
          createdAt: true,
        },
      });

      res.status(201).json({
        success: true,
        data: user,
      });
    } catch (error) {
      next(error);
    }
  }
);

// ═══════════════════════════════════════════
// PATCH /api/users/:id - Partial update
// ═══════════════════════════════════════════

router.patch(
  "/:id",
  [
    param("id").isUUID(),
    body("name").optional().trim().isLength({ min: 2 }),
    body("email").optional().isEmail().normalizeEmail(),
  ],
  validate,
  authenticateToken,
  async (req, res, next) => {
    try {
      // Check if user is updating their own profile or is admin
      if (req.user.id !== req.params.id && req.user.role !== "admin") {
        return res.status(403).json({
          success: false,
          error: {
            message: "Not authorized to update this user",
            code: "FORBIDDEN",
          },
        });
      }

      const user = await db.user.update({
        where: { id: req.params.id },
        data: req.body,
        select: {
          id: true,
          name: true,
          email: true,
          role: true,
          updatedAt: true,
        },
      });

      res.json({
        success: true,
        data: user,
      });
    } catch (error) {
      if (error.code === "P2025") {
        return res.status(404).json({
          success: false,
          error: {
            message: "User not found",
            code: "USER_NOT_FOUND",
          },
        });
      }
      next(error);
    }
  }
);

// ═══════════════════════════════════════════
// DELETE /api/users/:id - Delete user
// ═══════════════════════════════════════════

router.delete(
  "/:id",
  [param("id").isUUID()],
  validate,
  authenticateToken,
  authorize("admin"),
  async (req, res, next) => {
    try {
      await db.user.delete({
        where: { id: req.params.id },
      });

      res.status(204).send();
    } catch (error) {
      if (error.code === "P2025") {
        return res.status(404).json({
          success: false,
          error: {
            message: "User not found",
            code: "USER_NOT_FOUND",
          },
        });
      }
      next(error);
    }
  }
);

export default router;
```

> **💡 Pro Tip:** Use plural nouns for resources (/users not /user). Use nested routes for relationships. Always validate input!

<div align="center">

## 🎨 GraphQL APIs

</div>

### Modern API with GraphQL 🚀

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install @apollo/server graphql
npm install @graphql-tools/schema
```

```javascript
// ═══════════════════════════════════════════
// Apollo Server Setup
// ═══════════════════════════════════════════

import { ApolloServer } from "@apollo/server";
import { startStandaloneServer } from "@apollo/server/standalone";

// Type definitions
const typeDefs = `#graphql
  type User {
    id: ID!
    name: String!
    email: String!
    role: Role!
    posts: [Post!]!
    createdAt: String!
    updatedAt: String!
  }

  type Post {
    id: ID!
    title: String!
    content: String!
    published: Boolean!
    author: User!
    createdAt: String!
  }

  enum Role {
    USER
    ADMIN
    MODERATOR
  }

  input CreateUserInput {
    name: String!
    email: String!
    password: String!
    role: Role = USER
  }

  input UpdateUserInput {
    name: String
    email: String
  }

  input CreatePostInput {
    title: String!
    content: String!
    published: Boolean = false
  }

  type Query {
    # Users
    users(
      page: Int = 1
      limit: Int = 10
      search: String
      role: Role
    ): UserConnection!

    user(id: ID!): User
    me: User

    # Posts
    posts(
      published: Boolean
      authorId: ID
      page: Int = 1
      limit: Int = 10
    ): PostConnection!

    post(id: ID!): Post
  }

  type Mutation {
    # Auth
    login(email: String!, password: String!): AuthPayload!
    register(input: CreateUserInput!): AuthPayload!
    logout: Boolean!

    # Users
    createUser(input: CreateUserInput!): User!
    updateUser(id: ID!, input: UpdateUserInput!): User!
    deleteUser(id: ID!): Boolean!

    # Posts
    createPost(input: CreatePostInput!): Post!
    updatePost(id: ID!, input: CreatePostInput!): Post!
    deletePost(id: ID!): Boolean!
    publishPost(id: ID!): Post!
  }

  type Subscription {
    postCreated: Post!
    postPublished: Post!
    userUpdated(id: ID!): User!
  }

  type AuthPayload {
    token: String!
    user: User!
  }

  type UserConnection {
    edges: [User!]!
    pageInfo: PageInfo!
    totalCount: Int!
  }

  type PostConnection {
    edges: [Post!]!
    pageInfo: PageInfo!
    totalCount: Int!
  }

  type PageInfo {
    hasNextPage: Boolean!
    hasPreviousPage: Boolean!
    startCursor: String
    endCursor: String
  }
`;

// ═══════════════════════════════════════════
// Resolvers
// ═══════════════════════════════════════════

const resolvers = {
  Query: {
    users: async (_, { page, limit, search, role }, { dataSources, user }) => {
      if (!user) throw new Error("Not authenticated");

      const skip = (page - 1) * limit;

      const where = {};
      if (search) {
        where.OR = [
          { name: { contains: search, mode: "insensitive" } },
          { email: { contains: search, mode: "insensitive" } },
        ];
      }
      if (role) {
        where.role = role;
      }

      const [users, total] = await Promise.all([
        dataSources.userAPI.getUsers({ where, skip, take: limit }),
        dataSources.userAPI.countUsers({ where }),
      ]);

      return {
        edges: users,
        pageInfo: {
          hasNextPage: page < Math.ceil(total / limit),
          hasPreviousPage: page > 1,
        },
        totalCount: total,
      };
    },

    user: async (_, { id }, { dataSources, user }) => {
      if (!user) throw new Error("Not authenticated");
      return dataSources.userAPI.getUser(id);
    },

    me: async (_, __, { user, dataSources }) => {
      if (!user) throw new Error("Not authenticated");
      return dataSources.userAPI.getUser(user.id);
    },

    posts: async (_, { published, authorId, page, limit }, { dataSources }) => {
      const skip = (page - 1) * limit;

      const where = {};
      if (published !== undefined) where.published = published;
      if (authorId) where.authorId = authorId;

      const [posts, total] = await Promise.all([
        dataSources.postAPI.getPosts({ where, skip, take: limit }),
        dataSources.postAPI.countPosts({ where }),
      ]);

      return {
        edges: posts,
        pageInfo: {
          hasNextPage: page < Math.ceil(total / limit),
          hasPreviousPage: page > 1,
        },
        totalCount: total,
      };
    },
  },

  Mutation: {
    login: async (_, { email, password }, { dataSources }) => {
      const user = await dataSources.userAPI.verifyCredentials(email, password);
      const token = generateToken(user);
      return { token, user };
    },

    register: async (_, { input }, { dataSources }) => {
      const user = await dataSources.userAPI.createUser(input);
      const token = generateToken(user);
      return { token, user };
    },

    createPost: async (_, { input }, { user, dataSources, pubsub }) => {
      if (!user) throw new Error("Not authenticated");

      const post = await dataSources.postAPI.createPost({
        ...input,
        authorId: user.id,
      });

      pubsub.publish("POST_CREATED", { postCreated: post });

      return post;
    },

    deleteUser: async (_, { id }, { user, dataSources }) => {
      if (!user || user.role !== "ADMIN") {
        throw new Error("Not authorized");
      }

      await dataSources.userAPI.deleteUser(id);
      return true;
    },
  },

  // Field resolvers
  User: {
    posts: async (user, _, { dataSources }) => {
      return dataSources.postAPI.getPostsByUser(user.id);
    },
  },

  Post: {
    author: async (post, _, { dataSources }) => {
      return dataSources.userAPI.getUser(post.authorId);
    },
  },

  Subscription: {
    postCreated: {
      subscribe: (_, __, { pubsub }) => pubsub.asyncIterator(["POST_CREATED"]),
    },
  },
};

// ═══════════════════════════════════════════
// Create Server
// ═══════════════════════════════════════════

const server = new ApolloServer({
  typeDefs,
  resolvers,
  formatError: (error) => {
    console.error(error);
    return {
      message: error.message,
      code: error.extensions.code,
      ...(process.env.NODE_ENV === "development" && {
        stack: error.stack,
      }),
    };
  },
});

const { url } = await startStandaloneServer(server, {
  listen: { port: 4000 },
  context: async ({ req }) => {
    const token = req.headers.authorization?.replace("Bearer ", "");
    const user = token ? verifyToken(token) : null;

    return {
      user,
      dataSources: {
        userAPI: new UserAPI(),
        postAPI: new PostAPI(),
      },
    };
  },
});

console.log(`🚀 GraphQL Server ready at ${url}`);
```

**📦 GraphQL Resources:**

- Apollo Server: https://www.apollographql.com/docs/apollo-server/
- GraphQL: https://graphql.org/

> **💡 Pro Tip:** GraphQL eliminates over-fetching and under-fetching. Clients get exactly the data they need in a single request!

---

<div align="center">

## 🔐 Authentication & Authorization

</div>

### JWT Authentication 🔑

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install jsonwebtoken bcryptjs
npm install @types/jsonwebtoken @types/bcryptjs -D
```

```javascript
// ═══════════════════════════════════════════
// Auth Utilities
// ═══════════════════════════════════════════

import jwt from 'jsonwebtoken';
import bcrypt from 'bcryptjs';

const JWT_SECRET = process.env.JWT_SECRET;
const JWT_EXPIRES_IN = process.env.JWT_EXPIRES_IN || '7d';
const REFRESH_TOKEN_SECRET = process.env.REFRESH_TOKEN_SECRET;

// ═══════════════════════════════════════════
// Password Hashing
// ═══════════════════════════════════════════

export const hashPassword = async (password) => {
  const salt = await bcrypt.genSalt(10);
  return bcrypt.hash(password, salt);
};

export const verifyPassword = async (password, hash) => {
  return bcrypt.compare(password, hash);
};

// ═══════════════════════════════════════════
// JWT Token Generation
// ═══════════════════════════════════════════

export const generateAccessToken = (user) => {
  return jwt.sign(
    {
      id: user.id,
      email: user.email,
      role: user.role,
    },
    JWT_SECRET,
    {
      expiresIn: JWT_EXPIRES_IN,
      issuer: 'your-app',
      audience: 'your-app-users',
    }
  );
};

export const generateRefreshToken = (user) => {
  return jwt.sign(
    { id: user.id },
    REFRESH_TOKEN_SECRET,
    { expiresIn: '30d' }
  );
};

export const verifyToken = (token) => {
  try {
    return jwt.verify(token, JWT_SECRET);
  } catch (error) {
    if (error.name === 'TokenExpiredError') {
      throw new Error('Token expired');
    }
    throw new Error('Invalid token');
  }
};

// ═══════════════════════════════════════════
# Auth Middleware
// ═══════════════════════════════════════════

export const authenticateToken = async (req, res, next) => {
  const authHeader = req.headers.authorization;
  const token = authHeader?.startsWith('Bearer ')
    ? authHeader.substring(7)
    : null;

  if (!token) {
    return res.status(401).json({
      success: false,
      error: {
        message: 'Authentication required',
        code: 'NO_TOKEN',
      },
    });
  }

  try {
    const decoded = verifyToken(token);
    req.user = decoded;
    next();
  } catch (error) {
    return res.status(401).json({
      success: false,
      error: {
        message: error.message,
        code: 'INVALID_TOKEN',
      },
    });
  }
};

// ═══════════════════════════════════════════
// Role-Based Authorization
// ═══════════════════════════════════════════

export const authorize = (...allowedRoles) => {
  return (req, res, next) => {
    if (!req.user) {
      return res.status(401).json({
        success: false,
        error: {
          message: 'Authentication required',
          code: 'NOT_AUTHENTICATED',
        },
      });
    }

    if (!allowedRoles.includes(req.user.role)) {
      return res.status(403).json({
        success: false,
        error: {
          message: 'Insufficient permissions',
          code: 'FORBIDDEN',
          requiredRoles: allowedRoles,
        },
      });
    }

    next();
  };
};

// ═══════════════════════════════════════════
// Auth Routes
// ═══════════════════════════════════════════

import { Router } from 'express';

const router = Router();

// Register
router.post('/register', async (req, res, next) => {
  try {
    const { email, password, name } = req.body;

    // Check if user exists
    const existingUser = await db.user.findUnique({ where: { email } });
    if (existingUser) {
      return res.status(409).json({
        success: false,
        error: {
          message: 'Email already registered',
          code: 'EMAIL_EXISTS',
        },
      });
    }

    // Hash password
    const hashedPassword = await hashPassword(password);

    // Create user
    const user = await db.user.create({
      data: {
        email,
        name,
        password: hashedPassword,
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

    // Save refresh token
    await db.refreshToken.create({
      data: {
        token: refreshToken,
        userId: user.id,
        expiresAt: new Date(Date.now() + 30 * 24 * 60 * 60 * 1000),
      },
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
});

// Login
router.post('/login', async (req, res, next) => {
  try {
    const { email, password } = req.body;

    // Find user
    const user = await db.user.findUnique({ where: { email } });

    if (!user) {
      return res.status(401).json({
        success: false,
        error: {
          message: 'Invalid credentials',
          code: 'INVALID_CREDENTIALS',
        },
      });
    }

    // Verify password
    const isValid = await verifyPassword(password, user.password);

    if (!isValid) {
      return res.status(401).json({
        success: false,
        error: {
          message: 'Invalid credentials',
          code: 'INVALID_CREDENTIALS',
        },
      });
    }

    // Generate tokens
    const accessToken = generateAccessToken(user);
    const refreshToken = generateRefreshToken(user);

    // Save refresh token
    await db.refreshToken.create({
      data: {
        token: refreshToken,
        userId: user.id,
        expiresAt: new Date(Date.now() + 30 * 24 * 60 * 60 * 1000),
      },
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
});

// Refresh Token
router.post('/refresh', async (req, res, next) => {
  try {
    const { refreshToken } = req.body;

    if (!refreshToken) {
      return res.status(401).json({
        success: false,
        error: {
          message: 'Refresh token required',
          code: 'NO_REFRESH_TOKEN',
        },
      });
    }

    // Verify refresh token
    const decoded = jwt.verify(refreshToken, REFRESH_TOKEN_SECRET);

    // Check if token exists and not expired
    const storedToken = await db.refreshToken.findFirst({
      where: {
        token: refreshToken,
        userId: decoded.id,
        expiresAt: { gt: new Date() },
        revoked: false,
      },
    });

    if (!storedToken) {
      return res.status(401).json({
        success: false,
        error: {
          message: 'Invalid or expired refresh token',
          code: 'INVALID_REFRESH_TOKEN',
        },
      });
    }

    // Get user
    const user = await db.user.findUnique({ where: { id: decoded.id } });

    // Generate new access token
    const accessToken = generateAccessToken(user);

    res.json({
      success: true,
      data: { accessToken },
    });
  } catch (error) {
    next(error);
  }
});

// Logout
router.post('/logout', authenticateToken, async (req, res, next) => {
  try {
    const { refreshToken } = req.body;

    // Revoke refresh token
    await db.refreshToken.updateMany({
      where: {
        token: refreshToken,
        userId: req.user.id,
      },
      data: {
        revoked: true,
      },
    });

    res.json({
      success: true,
      message: 'Logged out successfully',
    });
  } catch (error) {
    next(error);
  }
});

// Get current user
router.get('/me', authenticateToken, async (req, res, next) => {
  try {
    const user = await db.user.findUnique({
      where: { id: req.user.id },
      select: {
        id: true,
        email: true,
        name: true,
        role: true,
        createdAt: true,
      },
    });

    res.json({
      success: true,
      data: user,
    });
  } catch (error) {
    next(error);
  }
});

export default router;
```

> **💡 Pro Tip:** Use refresh tokens for long-lived sessions. Store them securely and implement token rotation for better security!

---

<div align="center">

## ✅ Validation & Sanitization

</div>

### Input Validation with express-validator 🛡️

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install express-validator
```

```javascript
// ═══════════════════════════════════════════
// Validation Middleware
// ═══════════════════════════════════════════

import { body, param, query, validationResult } from "express-validator";

// Validation error handler
export const validate = (req, res, next) => {
  const errors = validationResult(req);

  if (!errors.isEmpty()) {
    return res.status(400).json({
      success: false,
      errors: errors.array().map((err) => ({
        field: err.param,
        message: err.msg,
        value: err.value,
      })),
    });
  }

  next();
};

// ═══════════════════════════════════════════
// Common Validation Rules
// ═══════════════════════════════════════════

export const userValidation = {
  create: [
    body("name")
      .trim()
      .isLength({ min: 2, max: 100 })
      .withMessage("Name must be between 2-100 characters")
      .escape(),

    body("email")
      .isEmail()
      .withMessage("Must be a valid email")
      .normalizeEmail()
      .custom(async (email) => {
        const user = await db.user.findUnique({ where: { email } });
        if (user) {
          throw new Error("Email already exists");
        }
        return true;
      }),

    body("password")
      .isLength({ min: 8 })
      .withMessage("Password must be at least 8 characters")
      .matches(
        /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]/
      )
      .withMessage(
        "Password must contain uppercase, lowercase, number and special character"
      ),

    body("age")
      .optional()
      .isInt({ min: 0, max: 150 })
      .withMessage("Age must be between 0-150"),

    body("website").optional().isURL().withMessage("Must be a valid URL"),

    body("role")
      .optional()
      .isIn(["user", "admin", "moderator"])
      .withMessage("Invalid role"),
  ],

  update: [
    param("id").isUUID().withMessage("Invalid user ID"),
    body("name").optional().trim().isLength({ min: 2, max: 100 }),
    body("email").optional().isEmail().normalizeEmail(),
  ],
};

// Usage in routes
router.post("/users", userValidation.create, validate, async (req, res) => {
  // If we reach here, validation passed
  const user = await createUser(req.body);
  res.status(201).json({ data: user });
});
```

> **💡 Pro Tip:** Always validate and sanitize user input. Never trust client data. Use custom validators for complex business logic!

---

<div align="center">

## 📚 API Documentation

</div>

### Swagger/OpenAPI Documentation 📖

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install swagger-ui-express swagger-jsdoc
```

```javascript
// ═══════════════════════════════════════════
// Swagger Configuration
// ═══════════════════════════════════════════

import swaggerJsdoc from "swagger-jsdoc";
import swaggerUi from "swagger-ui-express";

const options = {
  definition: {
    openapi: "3.0.0",
    info: {
      title: "My API",
      version: "1.0.0",
      description: "A comprehensive API documentation",
      contact: {
        name: "API Support",
        email: "support@example.com",
      },
    },
    servers: [
      {
        url: "http://localhost:3000/api",
        description: "Development server",
      },
      {
        url: "https://api.example.com",
        description: "Production server",
      },
    ],
    components: {
      securitySchemes: {
        bearerAuth: {
          type: "http",
          scheme: "bearer",
          bearerFormat: "JWT",
        },
      },
      schemas: {
        User: {
          type: "object",
          required: ["name", "email"],
          properties: {
            id: {
              type: "string",
              format: "uuid",
              description: "User ID",
            },
            name: {
              type: "string",
              minLength: 2,
              maxLength: 100,
            },
            email: {
              type: "string",
              format: "email",
            },
            role: {
              type: "string",
              enum: ["user", "admin", "moderator"],
              default: "user",
            },
            createdAt: {
              type: "string",
              format: "date-time",
            },
          },
        },
        Error: {
          type: "object",
          properties: {
            success: {
              type: "boolean",
              example: false,
            },
            error: {
              type: "object",
              properties: {
                message: { type: "string" },
                code: { type: "string" },
              },
            },
          },
        },
      },
    },
    security: [
      {
        bearerAuth: [],
      },
    ],
  },
  apis: ["./routes/*.js", "./models/*.js"],
};

const specs = swaggerJsdoc(options);

// Setup in Express
app.use(
  "/api-docs",
  swaggerUi.serve,
  swaggerUi.setup(specs, {
    explorer: true,
    customCss: ".swagger-ui .topbar { display: none }",
  })
);

// ═══════════════════════════════════════════
// Document Routes with JSDoc
// ═══════════════════════════════════════════

/**
 * @swagger
 * /users:
 *   get:
 *     summary: Get all users
 *     tags: [Users]
 *     parameters:
 *       - in: query
 *         name: page
 *         schema:
 *           type: integer
 *           default: 1
 *         description: Page number
 *       - in: query
 *         name: limit
 *         schema:
 *           type: integer
 *           default: 10
 *         description: Number of items per page
 *     responses:
 *       200:
 *         description: List of users
 *         content:
 *           application/json:
 *             schema:
 *               type: object
 *               properties:
 *                 success:
 *                   type: boolean
 *                 data:
 *                   type: array
 *                   items:
 *                     $ref: '#/components/schemas/User'
 *                 pagination:
 *                   type: object
 *                   properties:
 *                     page:
 *                       type: integer
 *                     limit:
 *                       type: integer
 *                     total:
 *                       type: integer
 */
router.get("/users", getUsers);

/**
 * @swagger
 * /users/{id}:
 *   get:
 *     summary: Get user by ID
 *     tags: [Users]
 *     parameters:
 *       - in: path
 *         name: id
 *         required: true
 *         schema:
 *           type: string
 *           format: uuid
 *     responses:
 *       200:
 *         description: User found
 *         content:
 *           application/json:
 *             schema:
 *               type: object
 *               properties:
 *                 success:
 *                   type: boolean
 *                 data:
 *                   $ref: '#/components/schemas/User'
 *       404:
 *         description: User not found
 *         content:
 *           application/json:
 *             schema:
 *               $ref: '#/components/schemas/Error'
 */
router.get("/users/:id", getUser);
```

**📦 Swagger Resources:**

- Swagger UI: https://swagger.io/tools/swagger-ui/
- OpenAPI Spec: https://swagger.io/specification/

> **💡 Pro Tip:** Good documentation is as important as good code. Use Swagger for interactive API docs that developers can test directly!

---

<div align="center">

## 🛡️ Security Best Practices

</div>

### Protecting Your API 🔒

```javascript
// ═══════════════════════════════════════════
// Rate Limiting
// ═══════════════════════════════════════════

import rateLimit from 'express-rate-limit';
import RedisStore from 'rate-limit-redis';

// Basic rate limiting
const limiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100, // 100 requests per windowMs
  message: 'Too many requests from this IP',
  standardHeaders: true,
  legacyHeaders: false,
});

// With Redis (for distributed systems)
const redisLimiter = rateLimit({
  store: new RedisStore({
    client: redisClient,
    prefix: 'rl:',
  }),
  windowMs: 15 *
  60 \* 1000,
  max: 100,
});

app.use('/api/', redisLimiter);

// Stricter limits for auth endpoints
const authLimiter = rateLimit({
windowMs: 15 _ 60 _ 1000,
max: 5, // Only 5 login attempts per 15 minutes
message: 'Too many login attempts, please try again later',
skipSuccessfulRequests: true, // Don't count successful requests
});

app.use('/api/auth/login', authLimiter);
app.use('/api/auth/register', authLimiter);

// ═══════════════════════════════════════════
// CORS Configuration
// ═══════════════════════════════════════════

import cors from 'cors';

// Basic CORS
app.use(cors());

// Production CORS
const corsOptions = {
origin: function (origin, callback) {
const allowedOrigins = process.env.ALLOWED_ORIGINS?.split(',') || [];

    // Allow requests with no origin (mobile apps, Postman)
    if (!origin) return callback(null, true);

    if (allowedOrigins.indexOf(origin) !== -1) {
      callback(null, true);
    } else {
      callback(new Error('Not allowed by CORS'));
    }

},
credentials: true,
optionsSuccessStatus: 200,
methods: ['GET', 'POST', 'PUT', 'PATCH', 'DELETE'],
allowedHeaders: ['Content-Type', 'Authorization'],
exposedHeaders: ['X-Total-Count', 'X-Page-Number'],
maxAge: 86400, // 24 hours
};

app.use(cors(corsOptions));

// ═══════════════════════════════════════════
// Helmet - Security Headers
// ═══════════════════════════════════════════

import helmet from 'helmet';

app.use(helmet({
contentSecurityPolicy: {
directives: {
defaultSrc: ["'self'"],
styleSrc: ["'self'", "'unsafe-inline'"],
scriptSrc: ["'self'"],
imgSrc: ["'self'", 'data:', 'https:'],
},
},
hsts: {
maxAge: 31536000, // 1 year
includeSubDomains: true,
preload: true,
},
frameguard: {
action: 'deny',
},
noSniff: true,
xssFilter: true,
}));

// ═══════════════════════════════════════════
// Request Sanitization
// ═══════════════════════════════════════════

import mongoSanitize from 'express-mongo-sanitize';
import xss from 'xss-clean';

// Prevent NoSQL injection
app.use(mongoSanitize({
replaceWith: '\_',
onSanitize: ({ req, key }) => {
console.warn(`Sanitized ${key} in request`);
},
}));

// Prevent XSS attacks
app.use(xss());

// ═══════════════════════════════════════════
// API Key Authentication
// ═══════════════════════════════════════════

const validateApiKey = async (req, res, next) => {
const apiKey = req.headers['x-api-key'];

if (!apiKey) {
return res.status(401).json({
success: false,
error: {
message: 'API key required',
code: 'NO_API_KEY',
},
});
}

// Check if API key is valid
const isValid = await db.apiKey.findFirst({
where: {
key: apiKey,
active: true,
expiresAt: { gt: new Date() },
},
});

if (!isValid) {
return res.status(401).json({
success: false,
error: {
message: 'Invalid API key',
code: 'INVALID_API_KEY',
},
});
}

// Track API key usage
await db.apiKeyUsage.create({
data: {
apiKeyId: isValid.id,
endpoint: req.path,
method: req.method,
},
});

req.apiKey = isValid;
next();
};

// ═══════════════════════════════════════════
// Request ID & Logging
// ═══════════════════════════════════════════

import { v4 as uuidv4 } from 'uuid';

app.use((req, res, next) => {
req.id = uuidv4();
res.setHeader('X-Request-ID', req.id);

const start = Date.now();

res.on('finish', () => {
const duration = Date.now() - start;
console.log({
requestId: req.id,
method: req.method,
path: req.path,
statusCode: res.statusCode,
duration: `${duration}ms`,
ip: req.ip,
userAgent: req.get('user-agent'),
});
});

next();
});

// ═══════════════════════════════════════════
// HTTPS Redirect (Production)
// ═══════════════════════════════════════════

app.use((req, res, next) => {
if (process.env.NODE_ENV === 'production' && !req.secure) {
return res.redirect(301, `https://${req.headers.host}${req.url}`);
}
next();
});
```

> **💡 Pro Tip:** Security is not optional! Always use HTTPS in production, implement rate limiting, validate all inputs, and keep dependencies updated!

---

<div align="center">

## 🧪 Testing APIs

</div>

### API Testing with Jest & Supertest 🔬

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install -D jest supertest @types/jest @types/supertest
npm install -D ts-jest
```

```javascript
// ═══════════════════════════════════════════
// Jest Configuration (jest.config.js)
// ═══════════════════════════════════════════

export default {
  preset: "ts-jest",
  testEnvironment: "node",
  coverageDirectory: "coverage",
  collectCoverageFrom: [
    "src/**/*.{js,ts}",
    "!src/**/*.test.{js,ts}",
    "!src/**/*.spec.{js,ts}",
  ],
  testMatch: ["**/__tests__/**/*.[jt]s", "**/?(*.)+(spec|test).[jt]s"],
  setupFilesAfterEnv: ["<rootDir>/src/test/setup.ts"],
};

// ═══════════════════════════════════════════
// Test Setup (test/setup.ts)
// ═══════════════════════════════════════════

import { PrismaClient } from "@prisma/client";

const prisma = new PrismaClient();

beforeAll(async () => {
  // Connect to test database
  await prisma.$connect();
});

afterAll(async () => {
  // Cleanup and disconnect
  await prisma.$disconnect();
});

beforeEach(async () => {
  // Clean database before each test
  await prisma.user.deleteMany();
  await prisma.post.deleteMany();
});

// ═══════════════════════════════════════════
// API Integration Tests
// ═══════════════════════════════════════════

import request from "supertest";
import app from "../app";

describe("User API", () => {
  describe("POST /api/users", () => {
    it("should create a new user", async () => {
      const userData = {
        name: "John Doe",
        email: "john@example.com",
        password: "Password123!",
      };

      const response = await request(app)
        .post("/api/users")
        .send(userData)
        .expect(201);

      expect(response.body.success).toBe(true);
      expect(response.body.data).toHaveProperty("id");
      expect(response.body.data.email).toBe(userData.email);
      expect(response.body.data).not.toHaveProperty("password");
    });

    it("should return 400 for invalid email", async () => {
      const response = await request(app)
        .post("/api/users")
        .send({
          name: "John Doe",
          email: "invalid-email",
          password: "Password123!",
        })
        .expect(400);

      expect(response.body.success).toBe(false);
      expect(response.body.errors).toBeDefined();
    });

    it("should return 409 for duplicate email", async () => {
      const userData = {
        name: "John Doe",
        email: "john@example.com",
        password: "Password123!",
      };

      // Create first user
      await request(app).post("/api/users").send(userData);

      // Try to create duplicate
      const response = await request(app)
        .post("/api/users")
        .send(userData)
        .expect(409);

      expect(response.body.success).toBe(false);
      expect(response.body.error.code).toBe("EMAIL_EXISTS");
    });
  });

  describe("GET /api/users", () => {
    it("should return paginated users", async () => {
      // Create test users
      await Promise.all([
        createUser({ name: "User 1", email: "user1@example.com" }),
        createUser({ name: "User 2", email: "user2@example.com" }),
        createUser({ name: "User 3", email: "user3@example.com" }),
      ]);

      const response = await request(app)
        .get("/api/users?page=1&limit=2")
        .expect(200);

      expect(response.body.data).toHaveLength(2);
      expect(response.body.pagination.total).toBe(3);
      expect(response.body.pagination.hasNext).toBe(true);
    });
  });

  describe("GET /api/users/:id", () => {
    it("should return user by id", async () => {
      const user = await createUser({
        name: "John Doe",
        email: "john@example.com",
      });

      const response = await request(app)
        .get(`/api/users/${user.id}`)
        .expect(200);

      expect(response.body.data.id).toBe(user.id);
      expect(response.body.data.email).toBe(user.email);
    });

    it("should return 404 for non-existent user", async () => {
      const fakeId = "00000000-0000-0000-0000-000000000000";

      const response = await request(app)
        .get(`/api/users/${fakeId}`)
        .expect(404);

      expect(response.body.error.code).toBe("USER_NOT_FOUND");
    });
  });

  describe("Authentication", () => {
    it("should login with valid credentials", async () => {
      const password = "Password123!";
      const user = await createUser({
        email: "john@example.com",
        password: await hashPassword(password),
      });

      const response = await request(app)
        .post("/api/auth/login")
        .send({
          email: user.email,
          password,
        })
        .expect(200);

      expect(response.body.data).toHaveProperty("accessToken");
      expect(response.body.data).toHaveProperty("refreshToken");
      expect(response.body.data.user.email).toBe(user.email);
    });

    it("should return 401 for invalid credentials", async () => {
      const response = await request(app)
        .post("/api/auth/login")
        .send({
          email: "nonexistent@example.com",
          password: "WrongPassword123!",
        })
        .expect(401);

      expect(response.body.error.code).toBe("INVALID_CREDENTIALS");
    });
  });

  describe("Protected Routes", () => {
    let token: string;
    let user: any;

    beforeEach(async () => {
      user = await createUser({
        name: "John Doe",
        email: "john@example.com",
      });
      token = generateAccessToken(user);
    });

    it("should access protected route with valid token", async () => {
      const response = await request(app)
        .get("/api/auth/me")
        .set("Authorization", `Bearer ${token}`)
        .expect(200);

      expect(response.body.data.id).toBe(user.id);
    });

    it("should return 401 without token", async () => {
      await request(app).get("/api/auth/me").expect(401);
    });

    it("should return 401 with invalid token", async () => {
      await request(app)
        .get("/api/auth/me")
        .set("Authorization", "Bearer invalid-token")
        .expect(401);
    });
  });
});

// ═══════════════════════════════════════════
// Helper Functions
// ═══════════════════════════════════════════

async function createUser(data: Partial<User>) {
  return prisma.user.create({
    data: {
      name: data.name || "Test User",
      email: data.email || `test${Date.now()}@example.com`,
      password: data.password || (await hashPassword("Password123!")),
      role: data.role || "user",
    },
  });
}
```

**📦 Testing Resources:**

- Jest: https://jestjs.io/
- Supertest: https://github.com/visionmedia/supertest

> **💡 Pro Tip:** Write tests for happy paths AND error cases. Aim for >80% code coverage. Test authentication, authorization, and edge cases!

---

<div align="center">

## 💡 Best Practices

</div>

### API Development Best Practices ⭐

```javascript
// ═══════════════════════════════════════════
// 1. Consistent Response Format
// ═══════════════════════════════════════════

// ✅ GOOD: Consistent structure
{
  "success": true,
  "data": { /* ... */ },
  "pagination": { /* ... */ },
  "timestamp": "2025-12-15T10:30:00Z"
}

{
  "success": false,
  "error": {
    "message": "User not found",
    "code": "USER_NOT_FOUND",
    "details": []
  },
  "timestamp": "2025-12-15T10:30:00Z"
}

// ❌ BAD: Inconsistent responses
{ "user": {} }
{ "error": "Failed" }
{ "ok": true, "result": {} }

// ═══════════════════════════════════════════
// 2. Proper HTTP Status Codes
// ═══════════════════════════════════════════

// ✅ GOOD: Use appropriate codes
200 - OK (successful GET, PUT, PATCH)
201 - Created (successful POST)
204 - No Content (successful DELETE)
400 - Bad Request (validation errors)
401 - Unauthorized (authentication required)
403 - Forbidden (no permission)
404 - Not Found
409 - Conflict (duplicate email)
422 - Unprocessable Entity (semantic errors)
429 - Too Many Requests
500 - Internal Server Error

// ❌ BAD: Always returning 200
res.status(200).json({ error: 'User not found' })

// ═══════════════════════════════════════════
// 3. Versioning
// ═══════════════════════════════════════════

// URL versioning (recommended)
/api/v1/users
/api/v2/users

// Header versioning
Accept: application/vnd.myapi.v1+json

// Query parameter (not recommended)
/api/users?version=1

// ═══════════════════════════════════════════
// 4. Pagination
// ═══════════════════════════════════════════

// ✅ GOOD: Offset-based pagination
GET /api/users?page=2&limit=20

// Cursor-based pagination (better for large datasets)
GET /api/users?cursor=eyJpZCI6MTAwfQ&limit=20

// ═══════════════════════════════════════════
// 5. Filtering & Sorting
// ═══════════════════════════════════════════

// Filter
GET /api/users?role=admin&status=active

// Sort
GET /api/users?sort=createdAt&order=desc
GET /api/users?sort=-createdAt  // - for descending

// Search
GET /api/users?search=john

// ═══════════════════════════════════════════
// 6. Field Selection
// ═══════════════════════════════════════════

// Return only specific fields
GET /api/users?fields=id,name,email

// ═══════════════════════════════════════════
// 7. Error Handling
// ═══════════════════════════════════════════

// Custom error class
class APIError extends Error {
  constructor(message, statusCode, code) {
    super(message);
    this.statusCode = statusCode;
    this.code = code;
    this.isOperational = true;
  }
}

// Usage
throw new APIError('User not found', 404, 'USER_NOT_FOUND');

// Global error handler
app.use((err, req, res, next) => {
  if (err.isOperational) {
    return res.status(err.statusCode).json({
      success: false,
      error: {
        message: err.message,
        code: err.code,
      },
    });
  }

  // Unexpected error
  console.error('UNEXPECTED ERROR:', err);
  res.status(500).json({
    success: false,
    error: {
      message: 'Internal server error',
      code: 'INTERNAL_ERROR',
    },
  });
});

// ═══════════════════════════════════════════
// 8. Async Error Handling
// ═══════════════════════════════════════════

// Wrapper to catch async errors
const asyncHandler = (fn) => (req, res, next) => {
  Promise.resolve(fn(req, res, next)).catch(next);
};

// Usage
router.get('/users', asyncHandler(async (req, res) => {
  const users = await db.user.findMany();
  res.json({ data: users });
}));

// ═══════════════════════════════════════════
// 9. Environment Configuration
// ═══════════════════════════════════════════

// Use dotenv
import dotenv from 'dotenv';
dotenv.config();

// Validate required env vars
const requiredEnvVars = [
  'NODE_ENV',
  'PORT',
  'DATABASE_URL',
  'JWT_SECRET',
];

for (const envVar of requiredEnvVars) {
  if (!process.env[envVar]) {
    throw new Error(`Missing required env var: ${envVar}`);
  }
}

// ═══════════════════════════════════════════
// 10. Graceful Shutdown
// ═══════════════════════════════════════════

let server;

const startServer = async () => {
  server = app.listen(PORT, () => {
    console.log(`Server running on port ${PORT}`);
  });
};

const gracefulShutdown = async (signal) => {
  console.log(`${signal} received, shutting down gracefully`);

  server.close(async () => {
    console.log('HTTP server closed');

    // Close database connections
    await prisma.$disconnect();

    console.log('Database disconnected');
    process.exit(0);
  });

  // Force shutdown after 10 seconds
  setTimeout(() => {
    console.error('Forced shutdown');
    process.exit(1);
  }, 10000);
};

process.on('SIGTERM', () => gracefulShutdown('SIGTERM'));
process.on('SIGINT', () => gracefulShutdown('SIGINT'));

startServer();
```

---

### Performance Optimization 🚀

```javascript
// ═══════════════════════════════════════════
// 1. Caching with Redis
// ═══════════════════════════════════════════

import Redis from 'ioredis';

const redis = new Redis(process.env.REDIS_URL);

const cacheMiddleware = (duration = 300) => async (req, res, next) => {
  if (req.method !== 'GET') return next();

  const key = `cache:${req.originalUrl}`;
  const cached = await redis.get(key);

  if (cached) {
    return res.json(JSON.parse(cached));
  }

  // Override res.json to cache response
  const originalJson = res.json.bind(res);
  res.json = (data) => {
    redis.setex(key, duration, JSON.stringify(data));
    return originalJson(data);
  };

  next();
};

// Usage
router.get('/users', cacheMiddleware(300), getUsers);

// ═══════════════════════════════════════════
// 2. Database Query Optimization
// ═══════════════════════════════════════════

// ✅ GOOD: Select only needed fields
const users = await prisma.user.findMany({
  select: {
    id: true,
    name: true,
    email: true,
  },
});

// ❌ BAD: Select all fields
const users = await prisma.user.findMany();

// ✅ GOOD: Use pagination
const users = await prisma.user.findMany({
  skip: (page - 1) * limit,
  take: limit,
});

// ✅ GOOD: Use indexes
// In Prisma schema:
@@index([email])
@@index([createdAt])

// ═══════════════════════════════════════════
// 3. Compression
// ═══════════════════════════════════════════

import compression from 'compression';

app.use(compression({
  filter: (req, res) => {
    if (req.headers['x-no-compression']) {
      return false;
    }
    return compression.filter(req, res);
  },
  level: 6,
}));
```

---

<div align="center">

**Built with 🌐 by MrDib, for Backend Developers**

_"A good API is like a good joke - it works on the first try!"_

**Happy Building!** 🚀

**If you found this helpful, give it a ⭐ star and share with fellow developers!**

</div>

---

### Contributing 🤝

Found better patterns? Want to add examples? Contributions are welcome!

1. Fork the repository
2. Add your API examples
3. Update best practices
4. Submit a pull request

---

### License 📄

This guide is open source and available under the MIT License.

---

<div align="center">

**Stay secure. Keep building. Ship robust APIs!** 💪✨

🌐 **#APIDeployment** 🌐 **#DevResourceVault** 🌐 **#MrDib** 🌐

### Remember

> _"Security is not an afterthought"_

> _"Always validate input, sanitize output"_

> _"Document your API like your job depends on it"_

> _"Test early, test often"_

> _"Monitor everything in production"_

</div>

---

<div align="center">

**Now go forth and build amazing APIs!** 🌟🌐

</div>
