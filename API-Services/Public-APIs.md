<div align="center">

# 🌐 Public APIs - Power Your Projects! 🌐

![APIs](https://img.shields.io/badge/APIs-Public_&_Free-blue?style=for-the-badge&logo=api)
![Resources](https://img.shields.io/badge/Resources-Ready_to_Use-green?style=for-the-badge)
![Projects](https://img.shields.io/badge/Projects-Build_Anything-orange?style=for-the-badge)

### _Connect your apps to the world_ 🚀

**Thousands of free APIs waiting for you to use!** ✨

</div>

---

## 📚 Table of Contents

- [🎯 What Are Public APIs](#-what-are-public-apis)
- [🌤️ Weather APIs](#️-weather-apis)
- [😂 Fun & Random APIs](#-fun--random-apis)
- [📰 News & Information](#-news--information)
- [💰 Finance & Crypto](#-finance--crypto)
- [🎬 Entertainment](#-entertainment)
- [🗺️ Maps & Location](#️-maps--location)
- [📧 Communication](#-communication)
- [🔍 Search & Data](#-search--data)
- [🎨 Images & Media](#-images--media)
- [🤖 AI & Machine Learning](#-ai--machine-learning)
- [🔐 Authentication](#-authentication)
- [💡 API Best Practices](#-api-best-practices)
- [📊 API Collections](#-api-collections)

---

<div align="center">

## 🎯 What Are Public APIs

</div>

```

### Understanding Public APIs 🌟

# ═══════════════════════════════════════════

# WHAT ARE PUBLIC APIs?

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ API BASICS                                                 ║
╚════════════════════════════════════════════════════════════╝

What is an API?
─────────────────────────────────────────────────────────────
API = Application Programming Interface

Think of it as:
• A waiter at a restaurant
• You (client) → Waiter (API) → Kitchen (server)
• You order (request) → Kitchen prepares → Waiter brings (response)

In Programming:
• Your app requests data
• API processes request
• API returns data
• Your app uses data

Example:
─────────────────────────────────────────────────────────────
Weather App:

1. You: "What's the weather in Tokyo?"
2. App calls Weather API
3. API returns: "25°C, Sunny"
4. App displays to you

Public API:
─────────────────────────────────────────────────────────────
✅ Available for public use
✅ Often free (with limits)
✅ Well-documented
✅ Easy to integrate
✅ No special permission needed (usually)

╔════════════════════════════════════════════════════════════╗
║ WHY USE PUBLIC APIs?                                       ║
╚════════════════════════════════════════════════════════════╝

Benefits:
─────────────────────────────────────────────────────────────

1. Save Time ⏰
   • Don't reinvent the wheel
   • Ready-made functionality
   • Focus on your app's unique features

2. Access Data 📊
   • Real-time information
   • Massive databases
   • Expert-maintained data

3. Add Features ⚡
   • Payment processing
   • Social login
   • Maps and location
   • AI capabilities
   • And much more!

4. Cost Effective 💰
   • Many are free
   • Cheaper than building yourself
   • Pay only for what you use

5. Professional Quality ✨
   • Tested and reliable
   • Maintained by experts
   • Regular updates
   • Good documentation

Real World Examples:
─────────────────────────────────────────────────────────────
• Uber uses Google Maps API
• Spotify uses various music APIs
• Twitter uses authentication APIs
• Weather apps use weather APIs
• Every app uses multiple APIs!

╔════════════════════════════════════════════════════════════╗
║ API TYPES                                                  ║
╚════════════════════════════════════════════════════════════╝

By Access:
─────────────────────────────────────────────────────────────

Free Tier:
• No cost up to limit
• Good for learning
• Small projects
• Example: OpenWeather (1000 calls/day free)

Freemium:
• Basic features free
• Advanced features paid
• Most common model
• Example: Google Maps (some free, some paid)

Paid Only:
• No free tier
• Enterprise solutions
• High-volume usage
• Example: Some financial APIs

By Authentication:
─────────────────────────────────────────────────────────────

No Auth:
• Completely open
• No API key needed
• Limited features
• Example: Some joke APIs

API Key:
• Simple authentication
• Get key from website
• Include in requests
• Most common

OAuth:
• More secure
• User authorization
• Access user data
• Example: Twitter, GitHub

╔════════════════════════════════════════════════════════════╗
║ HOW APIs WORK                                              ║
╚════════════════════════════════════════════════════════════╝

REST API (Most Common):
─────────────────────────────────────────────────────────────

HTTP Methods:
• GET: Retrieve data
• POST: Send data
• PUT: Update data
• DELETE: Remove data

Request Structure:
─────────────────────────────────────────────────────────────
URL: https://api.example.com/endpoint
Method: GET
Headers:

- Authorization: Bearer YOUR_API_KEY
- Content-Type: application/json
  Body (if POST): { "name": "value" }

Response:
─────────────────────────────────────────────────────────────
Status Code: 200 (success)
Body: {
"data": "result",
"status": "ok"
}

Common Status Codes:
─────────────────────────────────────────────────────────────
200 - OK (success)
201 - Created
400 - Bad Request (your mistake)
401 - Unauthorized (need auth)
403 - Forbidden (not allowed)
404 - Not Found
429 - Too Many Requests (rate limit)
500 - Server Error (their mistake)

╔════════════════════════════════════════════════════════════╗
║ GETTING STARTED                                            ║
╚════════════════════════════════════════════════════════════╝

Step-by-Step:
─────────────────────────────────────────────────────────────

1. Find API
   • Browse this guide
   • Check API directories
   • Read documentation

2. Sign Up (if needed)
   • Create account
   • Get API key
   • Check rate limits

3. Test It
   • Use Postman or curl
   • Make simple request
   • Understand response

4. Integrate
   • Add to your app
   • Handle errors
   • Respect rate limits

5. Deploy
   • Secure your keys
   • Monitor usage
   • Handle scaling

Tools You'll Need:
─────────────────────────────────────────────────────────────
• Postman (test APIs)
• curl (command line)
• Browser DevTools
• Your favorite language
• API documentation

```

---

<div align="center">

## 🌤️ Weather APIs

</div>

### Get Weather Data 🌡️

```

# ═══════════════════════════════════════════

# WEATHER APIs

# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║ OPENWEATHER                                                ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐⭐ (5/5) - Most Popular
🔗 URL: openweathermap.org/api
💰 Free: 1,000 calls/day
🎯 Best For: Weather data

Features:
─────────────────────────────────────────────────────────────
✅ Current weather
✅ 5-day forecast
✅ Historical data
✅ Weather maps
✅ Air pollution data
✅ UV index
✅ 200,000+ cities

Free Tier:
• 1,000 API calls/day
• 60 calls/minute
• Current weather
• 5-day forecast
• Perfect for learning!

Example:
─────────────────────────────────────────────────────────────

```

OpenWeather API example:

```javascript
// Get current weather
const API_KEY = 'your_api_key';
const city = 'Tokyo';

fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${API_KEY}&units=metric`)
  .then(response => response.json())
  .then(data => {
    console.log(`Temperature: ${data.main.temp}°C`);
    console.log(`Weather: ${data.weather[0].description}`);
    console.log(`Humidity: ${data.main.humidity}%`);
  });

// Response:
{
  "main": {
    "temp": 25.5,
    "humidity": 60
  },
  "weather": [{
    "description": "clear sky"
  }]
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   WEATHERAPI                               ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐⋆ (4.5/5)
🔗 URL: weatherapi.com
💰 Free: 1M calls/month
🎯 Best For: Generous free tier

Features:
─────────────────────────────────────────────────────────────
✅ Real-time weather
✅ Forecast up to 14 days
✅ Historical weather
✅ Astronomy data
✅ Time zone
✅ Sports data

Free Tier:
• 1,000,000 calls/month!
• 3-day forecast
• Current weather
• Very generous

╔════════════════════════════════════════════════════════════╗
║                   WTTR.IN                                  ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐ (4/5)
🔗 URL: wttr.in
💰 Free: Unlimited
🎯 Best For: Terminal/simple use

Features:
─────────────────────────────────────────────────────────────
✅ Console-friendly
✅ ASCII art weather
✅ No API key needed
✅ Multiple formats
✅ Moon phases

Example:
─────────────────────────────────────────────────────────────
```

wttr.in example:

```bash
# In terminal
curl wttr.in/Tokyo

# In browser
https://wttr.in/Tokyo

# JSON format
curl wttr.in/Tokyo?format=j1

# For code
fetch('https://wttr.in/Tokyo?format=j1')
  .then(r => r.json())
  .then(data => console.log(data));
```

```
╔════════════════════════════════════════════════════════════╗
║                   WEATHER API COMPARISON                   ║
╚════════════════════════════════════════════════════════════╝

Best For:
─────────────────────────────────────────────────────────────
• Most Popular: OpenWeather
• Most Generous: WeatherAPI (1M/month!)
• Simplest: wttr.in (no key needed)
• Most Features: OpenWeather or WeatherAPI
```

---

<div align="center">

## 😂 Fun & Random APIs

</div>

### Add Fun to Your Projects 🎉

```
# ═══════════════════════════════════════════
# FUN & RANDOM APIs
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   RANDOM JOKE APIS                         ║
╚════════════════════════════════════════════════════════════╝

Official Joke API:
─────────────────────────────────────────────────────────────
🔗 URL: official-joke-api.appspot.com
💰 Free: Unlimited
🎯 No API key needed!

Endpoints:
```

Joke API example:

```javascript
// Random joke
fetch('https://official-joke-api.appspot.com/random_joke')
  .then(r => r.json())
  .then(joke => {
    console.log(joke.setup);
    console.log(joke.punchline);
  });

// Response:
{
  "id": 1,
  "type": "general",
  "setup": "What do you call a bear with no teeth?",
  "punchline": "A gummy bear!"
}

// 10 random jokes
fetch('https://official-joke-api.appspot.com/random_ten')

// Specific type
fetch('https://official-joke-api.appspot.com/jokes/programming/random')
```

```
JokeAPI:
─────────────────────────────────────────────────────────────
🔗 URL: v2.jokeapi.dev
💰 Free: 100 requests/minute
🎯 More categories

Features:
• Programming jokes
• Dark humor
• Puns
• Miscellaneous
• Filter options
```

JokeAPI example:

```javascript
// Get programming joke
fetch("https://v2.jokeapi.dev/joke/Programming?type=single")
  .then((r) => r.json())
  .then((data) => console.log(data.joke));

// Two-part joke
fetch("https://v2.jokeapi.dev/joke/Any?type=twopart")
  .then((r) => r.json())
  .then((data) => {
    console.log(data.setup);
    console.log(data.delivery);
  });
```

```
╔════════════════════════════════════════════════════════════╗
║                   RANDOM FACTS & QUOTES                    ║
╚════════════════════════════════════════════════════════════╝

Quotable:
─────────────────────────────────────────────────────────────
🔗 URL: api.quotable.io
💰 Free: Unlimited
🎯 Famous quotes
```

Quotable API:

```javascript
// Random quote
fetch('https://api.quotable.io/random')
  .then(r => r.json())
  .then(quote => {
    console.log(`"${quote.content}"`);
    console.log(`- ${quote.author}`);
  });

// Response:
{
  "content": "The only way to do great work is to love what you do.",
  "author": "Steve Jobs",
  "tags": ["inspirational"]
}

// Quote by author
fetch('https://api.quotable.io/quotes?author=albert-einstein')

// Random inspirational quote
fetch('https://api.quotable.io/random?tags=inspirational')
```

```
Random Useless Facts:
─────────────────────────────────────────────────────────────
🔗 URL: uselessfacts.jsph.pl
💰 Free: Unlimited
```

Useless Facts:

```javascript
fetch("https://uselessfacts.jsph.pl/random.json?language=en")
  .then((r) => r.json())
  .then((data) => console.log(data.text));

// Example: "Honey never spoils."
```

```
╔════════════════════════════════════════════════════════════╗
║                   RANDOM DATA GENERATORS                   ║
╚════════════════════════════════════════════════════════════╝

Random User Generator:
─────────────────────────────────────────────────────────────
🔗 URL: randomuser.me
💰 Free: 5,000 requests/day
🎯 Fake user data for testing
```

Random User API:

```javascript
// Generate random user
fetch('https://randomuser.me/api/')
  .then(r => r.json())
  .then(data => {
    const user = data.results[0];
    console.log(`Name: ${user.name.first} ${user.name.last}`);
    console.log(`Email: ${user.email}`);
    console.log(`Photo: ${user.picture.large}`);
  });

// Multiple users
fetch('https://randomuser.me/api/?results=10')

// Specific nationality
fetch('https://randomuser.me/api/?nat=us,gb,fr')

// Only certain fields
fetch('https://randomuser.me/api/?inc=name,email,picture')

// Response:
{
  "results": [{
    "name": {
      "first": "John",
      "last": "Doe"
    },
    "email": "john.doe@example.com",
    "picture": {
      "large": "https://randomuser.me/api/portraits/men/75.jpg"
    }
  }]
}
```

```
UUID Generator:
─────────────────────────────────────────────────────────────
🔗 URL: uuidtools.com/api
💰 Free: Unlimited
```

UUID API:

```javascript
// Generate UUID
fetch("https://api.uuidtools.com/generate/v4")
  .then((r) => r.json())
  .then((data) => console.log(data[0]));

// Example: "550e8400-e29b-41d4-a716-446655440000"
```

```
╔════════════════════════════════════════════════════════════╗
║                   RANDOM IMAGES                            ║
╚════════════════════════════════════════════════════════════╝

Lorem Picsum:
─────────────────────────────────────────────────────────────
🔗 URL: picsum.photos
💰 Free: Unlimited
🎯 Placeholder images
```

Lorem Picsum:

```html
<!-- Random image (500x300) -->
<img src="https://picsum.photos/500/300" />

<!-- Specific image -->
<img src="https://picsum.photos/id/237/500/300" />

<!-- Grayscale -->
<img src="https://picsum.photos/500/300?grayscale" />

<!-- Blur -->
<img src="https://picsum.photos/500/300?blur=2" />
```

```javascript
// Get image info
fetch("https://picsum.photos/v2/list?page=1&limit=10")
  .then((r) => r.json())
  .then((images) => console.log(images));
```

```
Dog API:
─────────────────────────────────────────────────────────────
🔗 URL: dog.ceo/api
💰 Free: Unlimited
🎯 Random dog pictures!
```

Dog API:

```javascript
// Random dog image
fetch("https://dog.ceo/api/breeds/image/random")
  .then((r) => r.json())
  .then((data) => console.log(data.message));

// Multiple random dogs
fetch("https://dog.ceo/api/breeds/image/random/3");

// Specific breed
fetch("https://dog.ceo/api/breed/husky/images/random");

// List all breeds
fetch("https://dog.ceo/api/breeds/list/all");
```

```
Cat API:
─────────────────────────────────────────────────────────────
🔗 URL: thecatapi.com
💰 Free: 1,000 requests/month
🎯 Cat pictures with more features
```

Cat API:

```javascript
// Random cat
fetch("https://api.thecatapi.com/v1/images/search")
  .then((r) => r.json())
  .then((data) => console.log(data[0].url));

// With breeds info
fetch("https://api.thecatapi.com/v1/images/search?has_breeds=1");
```

```
╔════════════════════════════════════════════════════════════╗
║                   FUN API IDEAS                            ║
╚════════════════════════════════════════════════════════════╝

Project Ideas:
─────────────────────────────────────────────────────────────
1. Daily Quote App
   • Random quote each day
   • Share on social media
   • Save favorites

2. Joke Generator
   • Random jokes on button click
   • Filter by category
   • Rate jokes

3. Random Profile Generator
   • Generate fake users for testing
   • Export to JSON
   • Multiple formats

4. Pet Picture Gallery
   • Random dogs/cats
   • Vote on favorites
   • Share functionality

5. Motivational Dashboard
   • Quote of the day
   • Inspiring image
   • Fun fact
   • Weather widget
```

---

<div align="center">

## 📰 News & Information

</div>

### Stay Informed 📡

```
# ═══════════════════════════════════════════
# NEWS & INFORMATION APIs
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   NEWS API                                 ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐⭐ (5/5)
🔗 URL: newsapi.org
💰 Free: 100 requests/day
🎯 Best For: News aggregation

Features:
─────────────────────────────────────────────────────────────
✅ 80,000+ news sources
✅ Real-time news
✅ Search articles
✅ Category filtering
✅ Language support
✅ Date filtering

Free Tier:
• 100 requests/day
• Developer license
• Latest news (24h)
• 50 sources

Example:
─────────────────────────────────────────────────────────────
```

News API example:

```javascript
const API_KEY = 'your_api_key';

// Top headlines
fetch(`https://newsapi.org/v2/top-headlines?country=us&apiKey=${API_KEY}`)
  .then(r => r.json())
  .then(data => {
    data.articles.forEach(article => {
      console.log(article.title);
      console.log(article.url);
      console.log('---');
    });
  });

// Search articles
fetch(`https://newsapi.org/v2/everything?q=bitcoin&apiKey=${API_KEY}`)

// By category
fetch(`https://newsapi.org/v2/top-headlines?category=technology&apiKey=${API_KEY}`)

// By source
fetch(`https://newsapi.org/v2/top-headlines?sources=bbc-news&apiKey=${API_KEY}`)

// Response:
{
  "status": "ok",
  "totalResults": 38,
  "articles": [{
    "source": {
      "id": "bbc-news",
      "name": "BBC News"
    },
    "author": "BBC",
    "title": "Article Title",
    "description": "Article description...",
    "url": "https://bbc.com/article",
    "urlToImage": "https://bbc.com/image.jpg",
    "publishedAt": "2024-12-24T10:00:00Z",
    "content": "Full content..."
  }]
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   HACKER NEWS API                          ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐ (4/5)
🔗 URL: github.com/HackerNews/API
💰 Free: Unlimited
🎯 Best For: Tech news
```

Hacker News API:

```javascript
// Top stories
fetch("https://hacker-news.firebaseio.com/v0/topstories.json")
  .then((r) => r.json())
  .then((ids) => {
    // Get first story
    return fetch(`https://hacker-news.firebaseio.com/v0/item/${ids[0]}.json`);
  })
  .then((r) => r.json())
  .then((story) => {
    console.log(story.title);
    console.log(story.url);
  });

// Best stories
fetch("https://hacker-news.firebaseio.com/v0/beststories.json");

// New stories
fetch("https://hacker-news.firebaseio.com/v0/newstories.json");

// Ask HN
fetch("https://hacker-news.firebaseio.com/v0/askstories.json");
```

```
╔════════════════════════════════════════════════════════════╗
║                   REDDIT API                               ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐ (4/5)
🔗 URL: reddit.com/dev/api
💰 Free: 60 requests/minute
🎯 Best For: Community content

Simple Access (No Auth):
─────────────────────────────────────────────────────────────
```

Reddit API:

```javascript
// Subreddit posts
fetch("https://www.reddit.com/r/programming.json")
  .then((r) => r.json())
  .then((data) => {
    data.data.children.forEach((post) => {
      console.log(post.data.title);
      console.log(post.data.url);
    });
  });

// Top posts
fetch("https://www.reddit.com/r/programming/top.json?t=day");

// Hot posts
fetch("https://www.reddit.com/r/programming/hot.json");

// Search
fetch(
  "https://www.reddit.com/r/programming/search.json?q=javascript&restrict_sr=1"
);

// User profile
fetch("https://www.reddit.com/user/username.json");
```

```
╔════════════════════════════════════════════════════════════╗
║                   WIKIPEDIA API                            ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐⭐ (5/5)
🔗 URL: mediawiki.org/wiki/API
💰 Free: Unlimited (reasonable use)
🎯 Best For: Encyclopedia data
```

Wikipedia API:

```javascript
// Search Wikipedia
fetch(
  "https://en.wikipedia.org/w/api.php?action=opensearch&search=JavaScript&limit=5&format=json&origin=*"
)
  .then((r) => r.json())
  .then((data) => {
    console.log(data[1]); // Titles
    console.log(data[3]); // URLs
  });

// Get article content
fetch(
  "https://en.wikipedia.org/w/api.php?action=query&titles=JavaScript&prop=extracts&exintro=1&format=json&origin=*"
)
  .then((r) => r.json())
  .then((data) => console.log(data.query.pages));

// Random article
fetch("https://en.wikipedia.org/api/rest_v1/page/random/summary")
  .then((r) => r.json())
  .then((article) => {
    console.log(article.title);
    console.log(article.extract);
  });
```

---

<div align="center">

## 💰 Finance & Crypto

</div>

### Financial Data 💵

```
# ═══════════════════════════════════════════
# FINANCE & CRYPTO APIs
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   COINBASE (Crypto)                        ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐⋆ (4.5/5)
🔗 URL: developers.coinbase.com
💰 Free: Public data unlimited
🎯 Best For: Crypto prices
```

Coinbase API:

```javascript
// Get Bitcoin price
fetch("https://api.coinbase.com/v2/prices/BTC-USD/spot")
  .then((r) => r.json())
  .then((data) => {
    console.log(`Bitcoin: $${data.data.amount}`);
  });

// Multiple cryptocurrencies
const cryptos = ["BTC", "ETH", "DOGE"];
Promise.all(
  cryptos.map((coin) =>
    fetch(`https://api.coinbase.com/v2/prices/${coin}-USD/spot`).then((r) =>
      r.json()
    )
  )
).then((results) => {
  results.forEach((data) => {
    console.log(`${data.data.base}: $${data.data.amount}`);
  });
});

// Exchange rates
fetch("https://api.coinbase.com/v2/exchange-rates?currency=BTC")
  .then((r) => r.json())
  .then((data) => console.log(data.data.rates));
```

```
╔════════════════════════════════════════════════════════════╗
║                   COINGECKO (Crypto)                       ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐⭐ (5/5)
🔗 URL: coingecko.com/api
💰 Free: 10-50 calls/minute
🎯 Best For: Comprehensive crypto data
```

CoinGecko API:

```javascript
// Current price
fetch(
  "https://api.coingecko.com/api/v3/simple/price?ids=bitcoin,ethereum&vs_currencies=usd"
)
  .then((r) => r.json())
  .then((data) => console.log(data));
// { bitcoin: { usd: 45000 }, ethereum: { usd: 3000 } }

// Trending coins
fetch("https://api.coingecko.com/api/v3/search/trending")
  .then((r) => r.json())
  .then((data) => console.log(data.coins));

// Market data
fetch(
  "https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=10"
)
  .then((r) => r.json())
  .then((coins) => {
    coins.forEach((coin) => {
      console.log(`${coin.name}: $${coin.current_price}`);
    });
  });
```

```
╔════════════════════════════════════════════════════════════╗
║                   EXCHANGE RATES                           ║
╚════════════════════════════════════════════════════════════╝

ExchangeRate-API:
─────────────────────────────────────────────────────────────
🔗 URL: exchangerate-api.com
💰 Free: 1,500 requests/month
🎯 Best For: Currency conversion
```

Exchange Rate API:

```javascript
// Latest rates
fetch("https://api.exchangerate-api.com/v4/latest/USD")
  .then((r) => r.json())
  .then((data) => {
    console.log(`1 USD = ${data.rates.EUR} EUR`);
    console.log(`1 USD = ${data.rates.JPY} JPY`);
  });

// Convert currency
function convertCurrency(amount, from, to) {
  return fetch(`https://api.exchangerate-api.com/v4/latest/${from}`)
    .then((r) => r.json())
    .then((data) => {
      const rate = data.rates[to];
      return amount * rate;
    });
}

convertCurrency(100, "USD", "EUR").then((result) =>
  console.log(`100 USD = ${result.toFixed(2)} EUR`)
);
```

---

<div align="center">

## 🎬 Entertainment

</div>

### Movies, Music, Games 🎮

```
# ═══════════════════════════════════════════
# ENTERTAINMENT APIs
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   TMDB (Movies & TV)                       ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐⭐ (5/5)
🔗 URL: themoviedb.org/documentation/api
💰 Free: Unlimited (registration required)
🎯 Best For: Movie database

Features:
─────────────────────────────────────────────────────────────
✅ Movie information
✅ TV shows
✅ Cast & crew
✅ Images & posters
✅ Ratings & reviews
✅ Trending content
```

TMDB API example:

```javascript
const API_KEY = "your_api_key";

// Search movies
fetch(
  `https://api.themoviedb.org/3/search/movie?api_key=${API_KEY}&query=inception`
)
  .then((r) => r.json())
  .then((data) => {
    console.log(data.results[0].title);
    console.log(data.results[0].overview);
  });

// Get movie details
fetch(`https://api.themoviedb.org/3/movie/550?api_key=${API_KEY}`)
  .then((r) => r.json())
  .then((movie) => {
    console.log(movie.title);
    console.log(movie.tagline);
    console.log(`Rating: ${movie.vote_average}/10`);
  });

// Trending movies
fetch(`https://api.themoviedb.org/3/trending/movie/week?api_key=${API_KEY}`);

// Popular TV shows
fetch(`https://api.themoviedb.org/3/tv/popular?api_key=${API_KEY}`);

// Movie images
const posterPath = data.results[0].poster_path;
const imageUrl = `https://image.tmdb.org/t/p/w500${posterPath}`;
```

```
╔════════════════════════════════════════════════════════════╗
║                   SPOTIFY                                  ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐⋆ (4.5/5)
🔗 URL: developer.spotify.com
💰 Free: With rate limits
🎯 Best For: Music data

Features:
─────────────────────────────────────────────────────────────
✅ Search tracks
✅ Artist info
✅ Album details
✅ Playlists
✅ Audio features
✅ Recommendations

Note: Requires OAuth for most features
```

```
╔════════════════════════════════════════════════════════════╗
║                   POKEMON API                              ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐⋆ (4.5/5)
🔗 URL: pokeapi.co
💰 Free: Unlimited
🎯 Best For: Pokemon data
```

Pokemon API:

```javascript
// Get Pokemon
fetch("https://pokeapi.co/api/v2/pokemon/pikachu")
  .then((r) => r.json())
  .then((pokemon) => {
    console.log(`Name: ${pokemon.name}`);
    console.log(`Height: ${pokemon.height}`);
    console.log(`Weight: ${pokemon.weight}`);
    console.log(`Types: ${pokemon.types.map((t) => t.type.name).join(", ")}`);
    console.log(`Sprite: ${pokemon.sprites.front_default}`);
  });

// List all Pokemon
fetch("https://pokeapi.co/api/v2/pokemon?limit=151")
  .then((r) => r.json())
  .then((data) => {
    data.results.forEach((p) => console.log(p.name));
  });

// Get Pokemon by ID
fetch("https://pokeapi.co/api/v2/pokemon/25"); // Pikachu

// Get abilities
fetch("https://pokeapi.co/api/v2/ability/static");
```

```
╔════════════════════════════════════════════════════════════╗
║                   GAMING APIs                              ║
╚════════════════════════════════════════════════════════════╝

RAWG Video Games Database:
─────────────────────────────────────────────────────────────
🔗 URL: rawg.io/apidocs
💰 Free: 20,000 requests/month
🎯 Best For: Game database
```

RAWG API:

```javascript
const API_KEY = "your_api_key";

// Search games
fetch(`https://api.rawg.io/api/games?key=${API_KEY}&search=minecraft`)
  .then((r) => r.json())
  .then((data) => {
    data.results.forEach((game) => {
      console.log(`${game.name} - Rating: ${game.rating}`);
    });
  });

// Get game details
fetch(`https://api.rawg.io/api/games/3498?key=${API_KEY}`)
  .then((r) => r.json())
  .then((game) => {
    console.log(game.name);
    console.log(game.description);
    console.log(`Released: ${game.released}`);
  });

// Upcoming games
fetch(
  `https://api.rawg.io/api/games?key=${API_KEY}&dates=2024-12-01,2025-12-31`
);
```

---

<div align="center">

## 🗺️ Maps & Location

</div>

### Geolocation Services 📍

```
# ═══════════════════════════════════════════
# MAPS & LOCATION APIs
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   GOOGLE MAPS                              ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐⭐ (5/5)
🔗 URL: developers.google.com/maps
💰 Free: $200 credit/month
🎯 Best For: Complete mapping solution

Features:
─────────────────────────────────────────────────────────────
✅ Interactive maps
✅ Geocoding
✅ Directions
✅ Places
✅ Street View
✅ Time zones

Free Tier:
• $200 free credit/month
• 28,000 map loads
• Good for small/medium apps
```

Google Maps example:

```html
<!-- Embed map -->
<iframe
  width="600"
  height="450"
  style="border:0"
  loading="lazy"
  src="https://www.google.com/maps/embed/v1/place?key=YOUR_API_KEY&q=Tokyo+Tower"
>
</iframe>
```

```javascript
// Geocoding (address to coordinates)
fetch(
  `https://maps.googleapis.com/maps/api/geocode/json?address=1600+Amphitheatre+Parkway,+Mountain+View,+CA&key=${API_KEY}`
)
  .then((r) => r.json())
  .then((data) => {
    const location = data.results[0].geometry.location;
    console.log(`Lat: ${location.lat}, Lng: ${location.lng}`);
  });

// Reverse geocoding (coordinates to address)
fetch(
  `https://maps.googleapis.com/maps/api/geocode/json?latlng=40.714224,-73.961452&key=${API_KEY}`
)
  .then((r) => r.json())
  .then((data) => {
    console.log(data.results[0].formatted_address);
  });
```

```
╔════════════════════════════════════════════════════════════╗
║                   MAPBOX                                   ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐⋆ (4.5/5)
🔗 URL: mapbox.com
💰 Free: 50,000 loads/month
🎯 Best For: Custom styled maps

Features:
─────────────────────────────────────────────────────────────
✅ Custom map styles
✅ 3D terrain
✅ Navigation
✅ Geocoding
✅ Vector tiles
✅ Beautiful defaults
```

```
╔════════════════════════════════════════════════════════════╗
║                   IP GEOLOCATION                           ║
╚════════════════════════════════════════════════════════════╝

ipapi:
─────────────────────────────────────────────────────────────
🔗 URL: ipapi.co
💰 Free: 1,000 requests/day
🎯 Best For: IP to location
```

IP Geolocation:

```javascript
// Get visitor's location from IP
fetch("https://ipapi.co/json/")
  .then((r) => r.json())
  .then((data) => {
    console.log(`City: ${data.city}`);
    console.log(`Country: ${data.country_name}`);
    console.log(`Lat: ${data.latitude}, Lng: ${data.longitude}`);
    console.log(`IP: ${data.ip}`);
  });

// Specific IP
fetch("https://ipapi.co/8.8.8.8/json/")
  .then((r) => r.json())
  .then((data) => console.log(data));
```

---

<div align="center">

## 📧 Communication

</div>

### Email & SMS APIs 📨

```
# ═══════════════════════════════════════════
# COMMUNICATION APIs
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   EMAIL APIs                               ║
╚════════════════════════════════════════════════════════════╝

SendGrid:
─────────────────────────────────────────────────────────────
🔗 URL: sendgrid.com
💰 Free: 100 emails/day
🎯 Best For: Transactional emails

Mailgun:
─────────────────────────────────────────────────────────────
🔗 URL: mailgun.com
💰 Free: 100 emails/day
🎯 Best For: Developer-friendly

EmailJS:
─────────────────────────────────────────────────────────────
🔗 URL: emailjs.com
💰 Free: 200 emails/month
🎯 Best For: Client-side emails
```

EmailJS example:

```javascript
// Send email from client-side
emailjs
  .send("service_id", "template_id", {
    to_email: "user@example.com",
    from_name: "Your Name",
    message: "Hello from my app!",
  })
  .then(
    (response) => console.log("Email sent!", response),
    (error) => console.log("Failed...", error)
  );
```

```
╔════════════════════════════════════════════════════════════╗
║                   SMS APIs                                 ║
╚════════════════════════════════════════════════════════════╝

Twilio:
─────────────────────────────────────────────────────────────
🔗 URL: twilio.com
💰 Free: Trial credit
🎯 Best For: SMS & Voice

Note: Most SMS APIs require payment
Free tiers usually give trial credits
```

---

<div align="center">

## 🔍 Search & Data

</div>

### Data & Search APIs 🔎

```
# ═══════════════════════════════════════════
# SEARCH & DATA APIs
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   GITHUB                                   ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐⭐ (5/5)
🔗 URL: docs.github.com/rest
💰 Free: 60 requests/hour (5,000 auth)
🎯 Best For: GitHub data
```

GitHub API:

```javascript
// Get user info
fetch("https://api.github.com/users/octocat")
  .then((r) => r.json())
  .then((user) => {
    console.log(`Name: ${user.name}`);
    console.log(`Repos: ${user.public_repos}`);
    console.log(`Followers: ${user.followers}`);
  });

// Get user repos
fetch("https://api.github.com/users/octocat/repos")
  .then((r) => r.json())
  .then((repos) => {
    repos.forEach((repo) => {
      console.log(`${repo.name} - ⭐ ${repo.stargazers_count}`);
    });
  });

// Search repositories
fetch("https://api.github.com/search/repositories?q=javascript&sort=stars")
  .then((r) => r.json())
  .then((data) => {
    data.items.forEach((repo) => {
      console.log(`${repo.full_name} - ⭐ ${repo.stargazers_count}`);
    });
  });

// Trending repos (unofficial)
fetch(
  "https://api.github.com/search/repositories?q=created:>2024-12-01&sort=stars&order=desc"
);
```

```
╔════════════════════════════════════════════════════════════╗
║                   JSON PLACEHOLDER                         ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐⭐ (5/5)
🔗 URL: jsonplaceholder.typicode.com
💰 Free: Unlimited
🎯 Best For: Testing & prototyping
```

JSON Placeholder:

```javascript
// Get posts
fetch("https://jsonplaceholder.typicode.com/posts")
  .then((r) => r.json())
  .then((posts) => console.log(posts));

// Get single post
fetch("https://jsonplaceholder.typicode.com/posts/1")
  .then((r) => r.json())
  .then((post) => console.log(post));

// Create post (fake)
fetch("https://jsonplaceholder.typicode.com/posts", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({
    title: "My Post",
    body: "Content here",
    userId: 1,
  }),
})
  .then((r) => r.json())
  .then((data) => console.log(data));

// Available resources:
// /posts - 100 posts
// /comments - 500 comments
// /albums - 100 albums
// /photos - 5000 photos
// /todos - 200 todos
// /users - 10 users
```

---

<div align="center">

## 🎨 Images & Media

</div>

### Media APIs 📸

```
# ═══════════════════════════════════════════
# IMAGES & MEDIA APIs
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   UNSPLASH                                 ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐⭐ (5/5)
🔗 URL: unsplash.com/developers
💰 Free: 50 requests/hour
🎯 Best For: High-quality photos
```

Unsplash API:

```javascript
const ACCESS_KEY = "your_access_key";

// Random photo
fetch(`https://api.unsplash.com/photos/random?client_id=${ACCESS_KEY}`)
  .then((r) => r.json())
  .then((photo) => {
    console.log(photo.urls.regular);
    console.log(`By: ${photo.user.name}`);
  });

// Search photos
fetch(
  `https://api.unsplash.com/search/photos?query=nature&client_id=${ACCESS_KEY}`
)
  .then((r) => r.json())
  .then((data) => {
    data.results.forEach((photo) => {
      console.log(photo.urls.small);
    });
  });

// Random photo by topic
fetch(
  `https://api.unsplash.com/photos/random?topics=nature&client_id=${ACCESS_KEY}`
);
```

```
╔════════════════════════════════════════════════════════════╗
║                   GIPHY                                    ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐⋆ (4.5/5)
🔗 URL: developers.giphy.com
💰 Free: SDK limits apply
🎯 Best For: GIFs
```

Giphy API:

```javascript
const API_KEY = "your_api_key";

// Search GIFs
fetch(
  `https://api.giphy.com/v1/gifs/search?api_key=${API_KEY}&q=funny+cat&limit=10`
)
  .then((r) => r.json())
  .then((data) => {
    data.data.forEach((gif) => {
      console.log(gif.images.fixed_height.url);
    });
  });

// Trending GIFs
fetch(`https://api.giphy.com/v1/gifs/trending?api_key=${API_KEY}&limit=10`);

// Random GIF
fetch(`https://api.giphy.com/v1/gifs/random?api_key=${API_KEY}&tag=happy`);

// Get GIF by ID
fetch(`https://api.giphy.com/v1/gifs/FiGiRei2ICzzG?api_key=${API_KEY}`);
```

---

<div align="center">

## 🤖 AI & Machine Learning

</div>

### AI-Powered APIs 🧠

```
# ═══════════════════════════════════════════
# AI & MACHINE LEARNING APIs
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   OPENAI                                   ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐⭐ (5/5)
🔗 URL: platform.openai.com
💰 Paid: Pay per use
🎯 Best For: ChatGPT, GPT-4

Features:
─────────────────────────────────────────────────────────────
✅ ChatGPT API
✅ GPT-4
✅ DALL-E (images)
✅ Whisper (speech-to-text)
✅ Embeddings

Note: Requires payment, but very powerful!
```

```
╔════════════════════════════════════════════════════════════╗
║                   HUGGING FACE                             ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐ (4/5)
🔗 URL: huggingface.co/inference-api
💰 Free: Rate limited
🎯 Best For: Open-source AI models

Features:
─────────────────────────────────────────────────────────────
✅ Text generation
✅ Translation
✅ Sentiment analysis
✅ Question answering
✅ Image classification
```

---

<div align="center">

## 🔐 Authentication

</div>

### Auth Services 🔒

```
# ═══════════════════════════════════════════
# AUTHENTICATION APIs
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   AUTH0                                    ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐⭐ (5/5)
🔗 URL: auth0.com
💰 Free: 7,000 users
🎯 Best For: Complete auth solution

Features:
─────────────────────────────────────────────────────────────
✅ Social login
✅ Email/password
✅ Multi-factor auth
✅ User management
✅ Easy integration

╔════════════════════════════════════════════════════════════╗
║                   FIREBASE AUTH                            ║
╚════════════════════════════════════════════════════════════╝

📊 Rating: ⭐⭐⭐⭐⭐ (5/5)
🔗 URL: firebase.google.com
💰 Free: Unlimited
🎯 Best For: Google integration

Features:
─────────────────────────────────────────────────────────────
✅ Social providers
✅ Email/password
✅ Phone auth
✅ Anonymous auth
✅ Easy setup
```

---

<div align="center">

## 💡 API Best Practices

</div>

### Using APIs Effectively 🎯

```
# ═══════════════════════════════════════════
# API BEST PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SECURITY                                 ║
╚════════════════════════════════════════════════════════════╝

1. Protect Your API Keys
─────────────────────────────────────────────────────────────

❌ NEVER do this:
```

Bad practice:

```javascript
// DON'T hardcode API keys in frontend!
const API_KEY = "sk_live_123456789"; // ❌ Visible to everyone!
fetch(`https://api.example.com/data?key=${API_KEY}`);
```

```
✅ DO this:
```

Good practice:

```javascript
// Use environment variables
const API_KEY = process.env.API_KEY;

// Or backend proxy
fetch("/api/data") // Your backend handles the API key
  .then((r) => r.json());
```

```
2. Use Environment Variables
─────────────────────────────────────────────────────────────
```

Environment setup:

```bash
# .env file (NEVER commit this!)
API_KEY=your_secret_key_here
DATABASE_URL=your_database_url
```

```javascript
// Access in code
require("dotenv").config();
const apiKey = process.env.API_KEY;
```

```
3. Add .env to .gitignore
─────────────────────────────────────────────────────────────
```

Gitignore:

```
# .gitignore
.env
.env.local
.env.*.local
```

```
╔════════════════════════════════════════════════════════════╗
║                   ERROR HANDLING                           ║
╚════════════════════════════════════════════════════════════╝

Always Handle Errors:
─────────────────────────────────────────────────────────────
```

Error handling:

```javascript
// Good error handling
async function fetchData(url) {
  try {
    const response = await fetch(url);

    // Check if request was successful
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }

    const data = await response.json();
    return data;
  } catch (error) {
    console.error("Error fetching data:", error);
    // Show user-friendly message
    return null;
  }
}

// Usage
const data = await fetchData("https://api.example.com/data");
if (data) {
  // Use data
} else {
  // Handle error (show message to user)
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   RATE LIMITING                            ║
╚════════════════════════════════════════════════════════════╝

Respect Rate Limits:
─────────────────────────────────────────────────────────────
• Don't spam the API
• Cache responses when possible
• Use pagination
• Implement retry logic
```

Rate limiting:

```javascript
// Simple cache
const cache = new Map();
const CACHE_DURATION = 5 * 60 * 1000; // 5 minutes

async function fetchWithCache(url) {
  // Check cache first
  if (cache.has(url)) {
    const cached = cache.get(url);
    if (Date.now() - cached.timestamp < CACHE_DURATION) {
      return cached.data;
    }
  }

  // Fetch if not cached
  const data = await fetch(url).then((r) => r.json());
  cache.set(url, {
    data,
    timestamp: Date.now(),
  });

  return data;
}

// Retry logic
async function fetchWithRetry(url, retries = 3) {
  for (let i = 0; i < retries; i++) {
    try {
      const response = await fetch(url);
      if (response.ok) {
        return await response.json();
      }

      // If rate limited, wait and retry
      if (response.status === 429) {
        await new Promise((resolve) => setTimeout(resolve, 1000 * (i + 1)));
        continue;
      }

      throw new Error(`HTTP ${response.status}`);
    } catch (error) {
      if (i === retries - 1) throw error;
      await new Promise((resolve) => setTimeout(resolve, 1000));
    }
  }
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   OPTIMIZATION                             ║
╚════════════════════════════════════════════════════════════╝

1. Batch Requests
─────────────────────────────────────────────────────────────
```

Batch requests:

```javascript
// Bad: Multiple separate requests
const user1 = await fetch("/api/users/1").then((r) => r.json());
const user2 = await fetch("/api/users/2").then((r) => r.json());
const user3 = await fetch("/api/users/3").then((r) => r.json());

// Good: Batch request
const users = await fetch("/api/users?ids=1,2,3").then((r) => r.json());
```

```
2. Use Async/Await with Promise.all
─────────────────────────────────────────────────────────────
```

Parallel requests:

```javascript
// Slow: Sequential (6 seconds total)
const weather = await fetch("/api/weather");
const news = await fetch("/api/news");
const stocks = await fetch("/api/stocks");

// Fast: Parallel (2 seconds total - all at once!)
const [weather, news, stocks] = await Promise.all([
  fetch("/api/weather").then((r) => r.json()),
  fetch("/api/news").then((r) => r.json()),
  fetch("/api/stocks").then((r) => r.json()),
]);
```

```
3. Pagination
─────────────────────────────────────────────────────────────
```

Pagination example:

```javascript
// Don't fetch all at once
async function getAllUsers() {
  let allUsers = [];
  let page = 1;
  let hasMore = true;

  while (hasMore) {
    const response = await fetch(`/api/users?page=${page}&limit=100`);
    const data = await response.json();

    allUsers = [...allUsers, ...data.users];
    hasMore = data.users.length === 100;
    page++;
  }

  return allUsers;
}
```

```
╔════════════════════════════════════════════════════════════╗
║                   TESTING APIs                             ║
╚════════════════════════════════════════════════════════════╝

Tools for Testing:
─────────────────────────────────────────────────────────────

1. Postman
   • GUI for API testing
   • Save requests
   • Test collections
   • Generate code

2. curl (command line)
```

Using curl:

```bash
# GET request
curl https://api.example.com/data

# With headers
curl -H "Authorization: Bearer TOKEN" \
     https://api.example.com/data

# POST request
curl -X POST \
     -H "Content-Type: application/json" \
     -d '{"name":"MrDib"}' \
     https://api.example.com/users

# Pretty print JSON
curl https://api.example.com/data | jq
```

```
3. Browser DevTools
   • Network tab
   • See all requests
   • Copy as fetch/curl
   • Debug responses
```

---

<div align="center">

## 📊 API Collections

</div>

### Discover More APIs 🔍

```
# ═══════════════════════════════════════════
# API DIRECTORIES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   BEST API DIRECTORIES                     ║
╚════════════════════════════════════════════════════════════╝

1. Public APIs GitHub
─────────────────────────────────────────────────────────────
🔗 URL: github.com/public-apis/public-apis
⭐ 280k+ stars
📦 1400+ APIs categorized

The Ultimate List:
• Free and paid APIs
• Categorized
• Auth requirements listed
• HTTPS support noted
• CORS support noted

Categories include:
• Animals
• Anime
• Anti-Malware
• Art & Design
• Books
• Business
• Calendar
• Cloud Storage
• Continuous Integration
• Cryptocurrency
• Currency Exchange
• Data Validation
• Development
• Dictionaries
• Documents & Productivity
• Environment
• Events
• Finance
• Food & Drink
• Games & Comics
• Geocoding
• Government
• Health
• Jobs
• Machine Learning
• Music
• News
• Open Data
• Open Source Projects
• Patent
• Personality
• Phone
• Photography
• Programming
• Science & Math
• Security
• Shopping
• Social
• Sports & Fitness
• Test Data
• Text Analysis
• Tracking
• Transportation
• URL Shorteners
• Vehicle
• Video
• Weather

2. RapidAPI
─────────────────────────────────────────────────────────────
🔗 URL: rapidapi.com
🎯 API Marketplace
💰 Many free tiers

Features:
• 40,000+ APIs
• Single API key for all
• Test in browser
• Code snippets
• Pricing comparison

3. API List
─────────────────────────────────────────────────────────────
🔗 URL: apilist.fun
🎯 Curated collection
💰 Mostly free

Simple directory:
• Clean interface
• Quick search
• Direct links
• Free focus

4. Any API
─────────────────────────────────────────────────────────────
🔗 URL: any-api.com
🎯 API search engine
💰 Mixed

Search across:
• Multiple sources
• Real-time results
• Filter by category
```

---

<div align="center">

## 🎯 Summary

</div>

### Start Building! 🚀

```
╔════════════════════════════════════════════════════════════╗
║                   YOUR API TOOLKIT                         ║
╚════════════════════════════════════════════════════════════╝

Essential APIs to Know:
─────────────────────────────────────────────────────────────

Must-Have:
✅ OpenWeather (weather data)
✅ News API (news content)
✅ JSONPlaceholder (testing)
✅ Random User (test data)
✅ GitHub API (repos & users)

Fun APIs:
✅ Joke APIs (entertainment)
✅ Dog/Cat APIs (cute pictures!)
✅ Quote APIs (inspiration)
✅ Pokemon API (nostalgia)

Professional:
✅ Google Maps (location)
✅ Stripe (payments)
✅ SendGrid (emails)
✅ Auth0 (authentication)

╔════════════════════════════════════════════════════════════╗
║                   PROJECT IDEAS                            ║
╚════════════════════════════════════════════════════════════╝

Beginner Projects:
─────────────────────────────────────────────────────────────
1. Weather App
   • Use OpenWeather API
   • Show current weather
   • 5-day forecast
   • Location search

2. Movie Search
   • Use TMDB API
   • Search movies
   • Display posters
   • Show ratings

3. Random Quote Generator
   • Use Quotable API
   • Display random quotes
   • Tweet functionality
   • Save favorites

4. GitHub Profile Viewer
   • Use GitHub API
   • Show user stats
   • List repos
   • Display contributions

5. News Aggregator
   • Use News API
   • Filter by category
   • Search articles
   • Save for later

Intermediate Projects:
─────────────────────────────────────────────────────────────
1. Crypto Dashboard
   • Multiple crypto APIs
   • Live prices
   • Charts
   • Portfolio tracker

2. Social Media Dashboard
   • Aggregate multiple APIs
   • Show stats
   • Post scheduling
   • Analytics

3. Location-based App
   • Google Maps API
   • IP Geolocation
   • Place search
   • Directions

Advanced Projects:
─────────────────────────────────────────────────────────────
1. Full-Stack App
   • Multiple APIs
   • Authentication
   • Database
   • Real-time updates

2. AI-Powered App
   • OpenAI API
   • Image generation
   • Text analysis
   • Chatbot

╔════════════════════════════════════════════════════════════╗
║                   GETTING STARTED CHECKLIST                ║
╚════════════════════════════════════════════════════════════╝

Today:
─────────────────────────────────────────────────────────────
☐ Pick one API from this guide
☐ Sign up and get API key
☐ Make your first request
☐ Console.log the response
☐ Celebrate! 🎉

This Week:
─────────────────────────────────────────────────────────────
☐ Try 5 different APIs
☐ Build simple weather app
☐ Add error handling
☐ Deploy to GitHub Pages
☐ Share with friends

This Month:
─────────────────────────────────────────────────────────────
☐ Build 3 API-based projects
☐ Learn API best practices
☐ Combine multiple APIs
☐ Add to portfolio
☐ Start charging for API projects! 💰

Remember:
─────────────────────────────────────────────────────────────
"Every app uses APIs.
Master APIs, master modern development!"

Now go build something amazing! 🚀
```

---

<div align="center">

**Built with 🌐 by MrDib, for API enthusiasts**

_Remember: "APIs are the building blocks of modern applications!"_ ✨

**Happy Coding!** 🔌

</div>

---

## 🔗 Related Guides

- [Email Services](./Email-Services.md)
- [Payment Gateways](./Payment-Gateways.md)
- [Maps & Location](./Maps-Location.md)
- [Backend Development](../Development/Backend/API-Development.md)

---

## 📊 Quick Reference Card

### **Top Free APIs:**

| Category     | API             | Free Tier | Best For            |
| ------------ | --------------- | --------- | ------------------- |
| **Weather**  | OpenWeather     | 1,000/day | Current + Forecast  |
| **News**     | News API        | 100/day   | Headlines           |
| **Images**   | Unsplash        | 50/hour   | High-quality photos |
| **Fun**      | Joke API        | Unlimited | Random jokes        |
| **Testing**  | JSONPlaceholder | Unlimited | Fake data           |
| **GitHub**   | GitHub API      | 60/hour   | Repo data           |
| **Crypto**   | CoinGecko       | 50/min    | Coin prices         |
| **Movies**   | TMDB            | Unlimited | Movie info          |
| **Location** | ipapi           | 1,000/day | IP to location      |
| **Quotes**   | Quotable        | Unlimited | Famous quotes       |

### **Quick Start Template:**

```javascript
// Basic API fetch
async function fetchAPI(url) {
  try {
    const response = await fetch(url);
    if (!response.ok) throw new Error("API Error");
    return await response.json();
  } catch (error) {
    console.error("Error:", error);
    return null;
  }
}

// Usage
const data = await fetchAPI("https://api.example.com/data");
```

### **Security Checklist:**

- ✅ Never commit API keys
- ✅ Use environment variables
- ✅ Implement rate limiting
- ✅ Handle errors properly
- ✅ Cache when possible

---
