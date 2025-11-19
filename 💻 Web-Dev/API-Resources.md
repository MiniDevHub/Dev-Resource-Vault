<div align="center">

# 🌐 API Resources & Tools 🌐

### _Everything you need to build, test, and consume APIs like a boss_ 🚀

![APIs](https://img.shields.io/badge/APIs-RESTful-green?style=for-the-badge)
![GraphQL](https://img.shields.io/badge/GraphQL-Ready-purple?style=for-the-badge)

</div>

---

<div align="center">

## 🛠️ API Development Tools

</div>

### API Testing & Documentation 📝

```

⚡ Postman → https://postman.com

- Industry standard
- Collections & environments
- Automated testing
- Team collaboration
- Free tier available

🌩️ Thunder Client → VSCode Extension

- Lightweight alternative
- Inside VSCode
- Collections support
- No separate app

🦊 Insomnia → https://insomnia.rest

- Clean interface
- GraphQL support
- Plugin system
- Open source core

🔥 Hoppscotch → https://hoppscotch.io

- Open source
- Web-based
- Real-time collab
- PWA support

📚 Swagger/OpenAPI → https://swagger.io

- API documentation
- Interactive docs
- Code generation
- Industry standard

🎯 Bruno → https://usebruno.com

- Offline-first
- Git-friendly
- No cloud sync
- Privacy focused

```

---

<div align="center">

## 📡 Public APIs

</div>

### Free APIs for Testing & Learning 🆓

```

🎮 Fun & Games

- PokeAPI → https://pokeapi.co
- Marvel API → https://developer.marvel.com
- RAWG Video Games → https://rawg.io/apidocs
- D&D 5e API → https://www.dnd5eapi.co
- Rick and Morty → https://rickandmortyapi.com
- Studio Ghibli → https://ghibliapi.herokuapp.com

📊 Data & Information

- REST Countries → https://restcountries.com
- Open Weather Map → https://openweathermap.org/api
- News API → https://newsapi.org
- COVID-19 API → https://covid19api.com
- SpaceX API → https://github.com/r-spacex/SpaceX-API
- NASA APIs → https://api.nasa.gov

🎨 Media & Content

- Unsplash API → https://unsplash.com/developers
- Pexels API → https://www.pexels.com/api
- GIPHY API → https://developers.giphy.com
- YouTube API → https://developers.google.com/youtube
- Spotify API → https://developer.spotify.com
- SoundCloud API → https://developers.soundcloud.com

💰 Finance & Crypto

- CoinGecko API → https://www.coingecko.com/api
- Fixer.io → https://fixer.io
- Alpha Vantage → https://www.alphavantage.co
- IEX Cloud → https://iexcloud.io
- Blockchain.com → https://www.blockchain.com/api

🛠️ Developer Tools

- GitHub API → https://docs.github.com/rest
- JSONPlaceholder → https://jsonplaceholder.typicode.com
- ReqRes → https://reqres.in
- HTTPBin → https://httpbin.org
- Random User → https://randomuser.me

```

### Massive API Collections 📚

```

📖 Public APIs List → https://github.com/public-apis/public-apis

- 1400+ public APIs
- Categorized
- Auth info
- CORS support

🎯 RapidAPI → https://rapidapi.com

- API marketplace
- 35,000+ APIs
- Single SDK
- Billing handled

📚 API List → https://apilist.fun

- Curated list
- Categories
- Search function
- Quality focused

```

---

<div align="center">

## 🔧 API Development Frameworks

</div>

### REST API Frameworks 🌐

```javascript
// 🟢 Express.js (Node.js)
const express = require('express')
const app = express()

app.get('/api/users', (req, res) => {
  res.json({ users: [] })
})

app.listen(3000)

// 🚀 Fastify (Node.js - Faster alternative)
const fastify = require('fastify')()

fastify.get('/api/users', async (request, reply) => {
  return { users: [] }
})

fastify.listen({ port: 3000 })

// 🦕 Deno with Oak
import { Application } from "https://deno.land/x/oak/mod.ts"

const app = new Application()
app.use((ctx) => {
  ctx.response.body = { message: "Hello API!" }
})

await app.listen({ port: 3000 })

// 🐍 FastAPI (Python)
from fastapi import FastAPI

app = FastAPI()

@app.get("/api/users")
def read_users():
    return {"users": []}

// 💎 Ruby on Rails API
rails new myapi --api
rails generate controller Users index show create update destroy
```

### GraphQL Frameworks 📊

```javascript
// 🚀 Apollo Server
const { ApolloServer, gql } = require("apollo-server");

const typeDefs = gql`
  type Query {
    hello: String
    users: [User]
  }

  type User {
    id: ID!
    name: String!
    email: String!
  }
`;

const resolvers = {
  Query: {
    hello: () => "Hello world!",
    users: () => [],
  },
};

const server = new ApolloServer({ typeDefs, resolvers });
server.listen().then(({ url }) => {
  console.log(`Server ready at ${url}`);
});

// 📊 GraphQL Yoga
import { createYoga } from "graphql-yoga";
import { createServer } from "http";

const yoga = createYoga({
  schema: {
    typeDefs: /* GraphQL */ `
      type Query {
        hello: String
      }
    `,
    resolvers: {
      Query: {
        hello: () => "Hello from Yoga!",
      },
    },
  },
});

const server = createServer(yoga);
server.listen(4000);
```

---

<div align="center">

## 🔐 API Authentication

</div>

### Authentication Methods 🔒

```javascript
// 🔑 JWT Authentication
const jwt = require("jsonwebtoken");

// Generate token
const token = jwt.sign({ userId: user.id }, process.env.JWT_SECRET, {
  expiresIn: "24h",
});

// Verify token
const authMiddleware = (req, res, next) => {
  const token = req.headers.authorization?.split(" ")[1];

  if (!token) {
    return res.status(401).json({ error: "No token provided" });
  }

  try {
    const decoded = jwt.verify(token, process.env.JWT_SECRET);
    req.userId = decoded.userId;
    next();
  } catch (error) {
    res.status(401).json({ error: "Invalid token" });
  }
};

// 🔐 OAuth 2.0 with Passport
const passport = require("passport");
const GoogleStrategy = require("passport-google-oauth20").Strategy;

passport.use(
  new GoogleStrategy(
    {
      clientID: GOOGLE_CLIENT_ID,
      clientSecret: GOOGLE_CLIENT_SECRET,
      callbackURL: "/auth/google/callback",
    },
    (accessToken, refreshToken, profile, done) => {
      // Handle user data
      return done(null, profile);
    }
  )
);

// 🗝️ API Key Authentication
const apiKeyAuth = (req, res, next) => {
  const apiKey = req.headers["x-api-key"];

  if (!apiKey || apiKey !== process.env.API_KEY) {
    return res.status(403).json({ error: "Invalid API key" });
  }

  next();
};

app.use("/api", apiKeyAuth);
```

---

<div align="center">

## 📊 API Monitoring & Analytics

</div>

### Monitoring Tools 📈

```
🔍 Datadog           → https://datadoghq.com
   - Full-stack monitoring
   - API performance
   - Custom dashboards
   - Alerting

📊 New Relic         → https://newrelic.com
   - APM solution
   - Real-time insights
   - Error tracking
   - Performance monitoring

🎯 Postman Monitor   → https://postman.com/monitors
   - API monitoring
   - Scheduled runs
   - Response validation
   - Team alerts

📈 Uptime Robot      → https://uptimerobot.com
   - Uptime monitoring
   - 50 monitors free
   - Status pages
   - Multiple alerts

🔔 Better Uptime     → https://betteruptime.com
   - Modern monitoring
   - Status pages
   - Incident management
   - On-call scheduling
```

---

<div align="center">

## 🚀 API Best Practices

</div>

### RESTful API Design 📐

```javascript
// ✅ GOOD: RESTful endpoints
GET    /api/users          // Get all users
GET    /api/users/:id      // Get specific user
POST   /api/users          // Create user
PUT    /api/users/:id      // Update user
DELETE /api/users/:id      // Delete user

// ✅ GOOD: Nested resources
GET    /api/users/:id/posts
POST   /api/users/:id/posts

// ❌ BAD: Non-RESTful
GET    /api/getUsers
POST   /api/deleteUser
GET    /api/user_list

// ✅ GOOD: Versioning
/api/v1/users
/api/v2/users

// ✅ GOOD: Filtering, sorting, pagination
GET /api/users?status=active&sort=created_at:desc&page=2&limit=20

// ✅ GOOD: Standard status codes
200 OK
201 Created
204 No Content
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
500 Internal Server Error

// ✅ GOOD: Consistent response format
{
  "status": "success",
  "data": {
    "users": []
  },
  "meta": {
    "page": 1,
    "totalPages": 10,
    "totalCount": 100
  }
}

// Error response
{
  "status": "error",
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Email is required",
    "field": "email"
  }
}
```

### API Security Checklist 🔒

```
✅ Use HTTPS everywhere
✅ Implement authentication (JWT, OAuth)
✅ Rate limiting
✅ Input validation
✅ CORS configuration
✅ API versioning
✅ Request/response logging
✅ Error handling
✅ Data encryption
✅ API key rotation
✅ SQL injection prevention
✅ XSS protection
```

---

<div align="center">

## 🧪 API Testing

</div>

### Testing Strategies 🎯

```javascript
// 🧪 Jest + Supertest
const request = require("supertest");
const app = require("./app");

describe("User API", () => {
  test("GET /api/users", async () => {
    const response = await request(app)
      .get("/api/users")
      .expect(200)
      .expect("Content-Type", /json/);

    expect(response.body.data).toHaveProperty("users");
    expect(Array.isArray(response.body.data.users)).toBe(true);
  });

  test("POST /api/users", async () => {
    const newUser = {
      name: "MrDib",
      email: "mrdib@example.com",
    };

    const response = await request(app)
      .post("/api/users")
      .send(newUser)
      .expect(201);

    expect(response.body.data.user).toMatchObject(newUser);
  });
});

// 🎭 API Contract Testing with Pact
const { pactWith } = require("jest-pact");

pactWith({ consumer: "Frontend", provider: "UserAPI" }, (provider) => {
  describe("User API", () => {
    test("get user by id", async () => {
      await provider.addInteraction({
        state: "user exists",
        uponReceiving: "a request for user",
        withRequest: {
          method: "GET",
          path: "/api/users/1",
        },
        willRespondWith: {
          status: 200,
          body: {
            id: 1,
            name: "MrDib",
          },
        },
      });

      // Test implementation
    });
  });
});
```

---

<div align="center">

## 🔧 API Gateway & Management

</div>

### API Gateway Solutions 🚪

```
🌩️ AWS API Gateway   → https://aws.amazon.com/api-gateway
   - Fully managed
   - Auto scaling
   - Security features
   - AWS integration

🔷 Kong              → https://konghq.com
   - Open source
   - Plugin ecosystem
   - Multi-cloud
   - Enterprise features

🚀 Tyk              → https://tyk.io
   - Open source gateway
   - GraphQL support
   - Developer portal
   - Analytics

📡 Apigee           → https://cloud.google.com/apigee
   - Google Cloud
   - Full lifecycle
   - Monetization
   - Enterprise

🎯 Zuul             → https://github.com/Netflix/zuul
   - Netflix OSS
   - JVM based
   - Dynamic routing
   - Load balancing
```

---

<div align="center">

## 📚 API Documentation

</div>

### Documentation Tools 📖

```
📚 Swagger/OpenAPI   → https://swagger.io
   - Industry standard
   - Interactive docs
   - Code generation

📖 Redoc            → https://github.com/Redocly/redoc
   - OpenAPI renderer
   - Beautiful docs
   - Three-panel design

🎯 Slate            → https://slatedocs.github.io/slate
   - Static docs
   - Markdown based
   - Beautiful output

📝 Docusaurus       → https://docusaurus.io
   - Facebook's tool
   - Versioning
   - Search built-in

🚀 ReadMe           → https://readme.com
   - SaaS solution
   - Interactive docs
   - API metrics
   - Developer hub
```

---

<div align="center">

## 💡 MrDib's API Tips

</div>

### Design Principles :

1. **Keep it simple** - Don't over-engineer
2. **Be consistent** - Same patterns everywhere
3. **Version early** - Plan for changes
4. **Document everything** - Future you will thank you
5. **Think about errors** - They will happen
6. **Cache wisely** - Performance matters
7. **Monitor always** - Know when things break

### Common Mistakes to Avoid :

- ❌ Exposing database IDs directly
- ❌ No rate limiting
- ❌ Poor error messages
- ❌ Ignoring HTTP standards
- ❌ No API versioning
- ❌ Inconsistent naming
- ❌ No pagination for lists

---

<div align="center">

_Remember: A good API is like a good joke - if you have to explain it, it's not that good! 🎭_

</div>
