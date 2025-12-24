<div align="center">

# 💚 Vue.js Ecosystem

### _The progressive framework that developers actually enjoy_ ✨

![Vue](https://img.shields.io/badge/Vue-3.4+-42b883?style=for-the-badge&logo=vue.js)
![Nuxt](https://img.shields.io/badge/Nuxt-3.x-00DC82?style=for-the-badge&logo=nuxt.js)
![Ecosystem](https://img.shields.io/badge/Ecosystem-Mature-green?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [💚 Vue Fundamentals](#-vue-fundamentals)
- [🏗️ Meta-Frameworks](#️-meta-frameworks)
- [🎨 UI Libraries](#-ui-libraries)
- [🍍 State Management](#-state-management)
- [🗂️ Routing](#️-routing)
- [🔧 VueUse Composables](#-vueuse-composables)
- [📝 Form Handling](#-form-handling)
- [🧪 Testing](#-testing)
- [🛠️ Developer Tools](#️-developer-tools)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 💚 Vue Fundamentals

</div>

### Modern Vue (3.4+) 🚀

```bash
# ═══════════════════════════════════════════
# Create New Vue App
# ═══════════════════════════════════════════

# Vite (Recommended - Fast!)
npm create vue@latest my-app
cd my-app
npm install
npm run dev

# Options during setup:
# ✔ TypeScript? Yes
# ✔ JSX Support? No
# ✔ Vue Router? Yes
# ✔ Pinia? Yes
# ✔ Vitest? Yes
# ✔ ESLint? Yes
# ✔ Prettier? Yes

# Nuxt (Full-stack)
npx nuxi@latest init my-app
```

```vue
<!-- ═══════════════════════════════════════════ -->
<!-- Single File Component (SFC) -->
<!-- ═══════════════════════════════════════════ -->

<script setup>
import { ref, computed, watch, onMounted } from "vue";

// Reactive state
const count = ref(0);
const message = ref("Hello, Vue!");

// Computed properties
const doubleCount = computed(() => count.value * 2);

// Methods
const increment = () => {
  count.value++;
};

// Watchers
watch(count, (newVal, oldVal) => {
  console.log(`Count changed from ${oldVal} to ${newVal}`);
});

// Lifecycle
onMounted(() => {
  console.log("Component mounted!");
});
</script>

<template>
  <div class="container">
    <h1>{{ message }}</h1>
    <p>Count: {{ count }}</p>
    <p>Double: {{ doubleCount }}</p>
    <button @click="increment">Increment</button>
  </div>
</template>

<style scoped>
.container {
  padding: 2rem;
}

button {
  padding: 0.5rem 1rem;
  background: #42b883;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background: #35a372;
}
</style>
```

```vue
<!-- ═══════════════════════════════════════════ -->
<!-- Composition API Patterns -->
<!-- ═══════════════════════════════════════════ -->

<script setup>
import { ref, reactive, toRefs } from 'vue'

// ref - for primitives
const count = ref(0)
const message = ref('Hello')

// reactive - for objects
const state = reactive({
  user: null,
  loading: false,
  todos: []
})

// Destructure with toRefs
const { user, loading, todos } = toRefs(state)

// Update reactive values
count.value++ // ref needs .value
state.user = { name: 'MrDib' } // reactive doesn't

// ═══════════════════════════════════════════
// Props & Emits
// ═══════════════════════════════════════════

const props = defineProps({
  title: String,
  count: {
    type: Number,
    default: 0
  }
})

const emit = defineEmits(['update', 'delete'])

const handleUpdate = () => {
  emit('update', { id: 1, name: 'Updated' })
}

// ═══════════════════════════════════════════
// TypeScript Support
// ═══════════════════════════════════════════

interface User {
  id: number
  name: string
  email: string
}

const user = ref<User | null>(null)

const props = defineProps<{
  title: string
  count?: number
}>()

const emit = defineEmits<{
  update: [value: User]
  delete: [id: number]
}>()
</script>

<template>
  <div>
    <h2>{{ props.title }}</h2>
    <button @click="handleUpdate">Update</button>
  </div>
</template>
```

```vue
<!-- ═══════════════════════════════════════════ -->
<!-- Composables (Custom Hooks) -->
<!-- ═══════════════════════════════════════════ -->

<script setup>
// composables/useCounter.js
import { ref, computed } from "vue";

export function useCounter(initialValue = 0) {
  const count = ref(initialValue);

  const double = computed(() => count.value * 2);

  const increment = () => count.value++;
  const decrement = () => count.value--;
  const reset = () => (count.value = initialValue);

  return {
    count,
    double,
    increment,
    decrement,
    reset,
  };
}

// composables/useFetch.js
export function useFetch(url) {
  const data = ref(null);
  const error = ref(null);
  const loading = ref(false);

  const fetchData = async () => {
    loading.value = true;
    error.value = null;

    try {
      const response = await fetch(url);
      data.value = await response.json();
    } catch (e) {
      error.value = e;
    } finally {
      loading.value = false;
    }
  };

  onMounted(fetchData);

  return { data, error, loading, refetch: fetchData };
}

// Usage in component
import { useCounter } from "@/composables/useCounter";
import { useFetch } from "@/composables/useFetch";

const { count, increment } = useCounter(0);
const { data: users, loading } = useFetch("/api/users");
</script>
```

**📦 Vue Resources:**

- Docs: https://vuejs.org/
- Tutorial: https://vuejs.org/tutorial/
- Playground: https://play.vuejs.org/

> **💡 Pro Tip:** Always use `<script setup>` - it's more concise and performs better. Composition API is the future, but Options API still works for backward compatibility!

---

<div align="center">

## 🏗️ Meta-Frameworks

</div>

### Nuxt - The Vue Framework 🚀

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npx nuxi@latest init my-app
cd my-app
npm install
npm run dev
```

```vue
<!-- ═══════════════════════════════════════════ -->
<!-- File-Based Routing (No router needed!) -->
<!-- ═══════════════════════════════════════════ -->

<!-- pages/index.vue -->
<template>
  <div>
    <h1>Home Page</h1>
    <NuxtLink to="/about">About</NuxtLink>
  </div>
</template>

<!-- pages/about.vue -->
<template>
  <div>
    <h1>About Page</h1>
  </div>
</template>

<!-- pages/blog/[id].vue -->
<script setup>
const route = useRoute();
const { data: post } = await useFetch(`/api/posts/${route.params.id}`);
</script>

<template>
  <article>
    <h1>{{ post.title }}</h1>
    <p>{{ post.content }}</p>
  </article>
</template>

<!-- ═══════════════════════════════════════════ -->
<!-- Layouts -->
<!-- ═══════════════════════════════════════════ -->

<!-- layouts/default.vue -->
<template>
  <div>
    <header>
      <nav>Navigation</nav>
    </header>
    <main>
      <slot />
      <!-- Page content renders here -->
    </main>
    <footer>Footer</footer>
  </div>
</template>

<!-- pages/index.vue -->
<script setup>
definePageMeta({
  layout: "default",
});
</script>

<!-- ═══════════════════════════════════════════ -->
<!-- Data Fetching -->
<!-- ═══════════════════════════════════════════ -->

<script setup>
// Server-side fetch
const { data: posts } = await useFetch("/api/posts");

// With options
const { data, pending, error, refresh } = await useFetch("/api/posts", {
  method: "GET",
  headers: {
    Authorization: "Bearer token",
  },
  transform: (data) => {
    return data.map((post) => ({
      ...post,
      date: new Date(post.date),
    }));
  },
});

// Lazy fetch (client-side only)
const { data: users } = await useLazyFetch("/api/users");

// Async data
const { data: user } = await useAsyncData("user", () => $fetch("/api/user"));
</script>

<!-- ═══════════════════════════════════════════ -->
<!-- Server API Routes -->
<!-- ═══════════════════════════════════════════ -->

// server/api/posts.get.ts export default defineEventHandler(async (event) => {
const posts = await db.posts.findMany() return posts }) //
server/api/posts/[id].get.ts export default defineEventHandler(async (event) =>
{ const id = getRouterParam(event, 'id') const post = await
db.posts.findUnique({ where: { id } }) return post }) //
server/api/posts.post.ts export default defineEventHandler(async (event) => {
const body = await readBody(event) const post = await db.posts.create({ data:
body }) return post })

<!-- ═══════════════════════════════════════════ -->
<!-- Auto-imports (No import needed!) -->
<!-- ═══════════════════════════════════════════ -->

<script setup>
// These are auto-imported:
// - ref, reactive, computed, watch (from Vue)
// - useRoute, useRouter, navigateTo (from Nuxt)
// - useFetch, useAsyncData (from Nuxt)
// - All your composables from /composables
// - All your components from /components

const count = ref(0); // ✅ Works!
const router = useRouter(); // ✅ Works!
const { data } = await useFetch("/api/posts"); // ✅ Works!
</script>

<!-- ═══════════════════════════════════════════ -->
<!-- Nuxt Config -->
<!-- ═══════════════════════════════════════════ -->

// nuxt.config.ts export default defineNuxtConfig({ devtools: { enabled: true },
modules: [ '@nuxtjs/tailwindcss', '@pinia/nuxt', '@vueuse/nuxt', ],
runtimeConfig: { // Private (server-only) apiSecret: process.env.API_SECRET, //
Public (exposed to client) public: { apiBase: process.env.API_BASE_URL } }, app:
{ head: { title: 'My Nuxt App', meta: [ { name: 'description', content: 'My
amazing Nuxt app' } ] } } })
```

**📦 Nuxt Resources:**

- Docs: https://nuxt.com/docs
- Modules: https://nuxt.com/modules
- Examples: https://nuxt.com/docs/examples

> **💡 Pro Tip:** Nuxt 3 is like Next.js but for Vue. File-based routing, auto-imports, and server routes make development incredibly fast. Use it for all production Vue apps!

---

<div align="center">

## 🎨 UI Libraries

</div>

### Element Plus - Enterprise Ready 💎

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install element-plus
npm install @element-plus/icons-vue
```

```vue
<!-- ═══════════════════════════════════════════ -->
<!-- Setup -->
<!-- ═══════════════════════════════════════════ -->

<script setup>
// main.js
import { createApp } from "vue";
import ElementPlus from "element-plus";
import "element-plus/dist/index.css";

const app = createApp(App);
app.use(ElementPlus);
</script>

<!-- ═══════════════════════════════════════════ -->
<!-- Components -->
<!-- ═══════════════════════════════════════════ -->

<script setup>
import { ElMessage } from "element-plus";
import { Search } from "@element-plus/icons-vue";

const form = reactive({
  name: "",
  email: "",
  region: "",
});

const handleSubmit = () => {
  ElMessage.success("Form submitted!");
};
</script>

<template>
  <el-container>
    <el-header>
      <h1>My App</h1>
    </el-header>

    <el-main>
      <el-card>
        <template #header>
          <span>User Form</span>
        </template>

        <el-form :model="form" label-width="120px">
          <el-form-item label="Name">
            <el-input v-model="form.name" />
          </el-form-item>

          <el-form-item label="Email">
            <el-input v-model="form.email" type="email" />
          </el-form-item>

          <el-form-item label="Region">
            <el-select v-model="form.region" placeholder="Select">
              <el-option label="Zone 1" value="zone1" />
              <el-option label="Zone 2" value="zone2" />
            </el-select>
          </el-form-item>

          <el-form-item>
            <el-button type="primary" @click="handleSubmit"> Submit </el-button>
          </el-form-item>
        </el-form>
      </el-card>

      <el-table :data="tableData" style="width: 100%; margin-top: 20px">
        <el-table-column prop="date" label="Date" width="180" />
        <el-table-column prop="name" label="Name" width="180" />
        <el-table-column prop="address" label="Address" />
      </el-table>
    </el-main>
  </el-container>
</template>
```

**📦 Element Plus Resources:**

- Docs: https://element-plus.org/
- Components: 80+
- Why: Enterprise-grade, comprehensive

> **💡 Pro Tip:** Element Plus is perfect for admin dashboards and enterprise apps. Comprehensive component library with excellent documentation!

---

### Vuetify - Material Design ⚡

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install vuetify @mdi/font
```

```vue
<script setup>
// main.js
import { createVuetify } from "vuetify";
import "vuetify/styles";
import "@mdi/font/css/materialdesignicons.css";

const vuetify = createVuetify({
  theme: {
    defaultTheme: "dark",
  },
});

app.use(vuetify);
</script>

<template>
  <v-app>
    <v-app-bar color="primary">
      <v-app-bar-title>My App</v-app-bar-title>
      <v-spacer></v-spacer>
      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <v-container>
        <v-row>
          <v-col cols="12" md="6">
            <v-card>
              <v-card-title>Card Title</v-card-title>
              <v-card-text>Card content</v-card-text>
              <v-card-actions>
                <v-btn color="primary">Action</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>
```

**📦 Vuetify Resources:**

- Docs: https://vuetifyjs.com/
- Components: 100+
- Why: Material Design, most popular

> **💡 Pro Tip:** Vuetify is the most popular Vue UI library. Great for Material Design fans!

---

<div align="center">

## 🍍 State Management

</div>

### Pinia - Modern State Management 🎯

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install pinia
```

```javascript
// ═══════════════════════════════════════════
// Setup
// ═══════════════════════════════════════════

// main.js
import { createPinia } from 'pinia'

const pinia = createPinia()
app.use(pinia)

// ═══════════════════════════════════════════
// Define Store
// ═══════════════════════════════════════════

// stores/user.js
import { defineStore } from 'pinia'

export const useUserStore = defineStore('user', {
  state: () => ({
    user: null,
    token: null,
    loading: false,
  }),

  getters: {
    isAuthenticated: (state) => !!state.token,
    userName: (state) => state.user?.name || 'Guest',
    userRole: (state) => state.user?.role || 'user',
  },

  actions: {
    async login(credentials) {
      this.loading = true
      try {
        const response = await fetch('/api/login', {
          method: 'POST',
          body: JSON.stringify(credentials),
        })
        const data = await response.json()
        this.user = data.user
        this.token = data.token
      } catch (error) {
        console.error('Login failed:', error)
      } finally {
        this.loading = false
      }
    },

    logout() {
      this.user = null
      this.token = null
    },

    async fetchProfile() {
      const response = await fetch('/api/profile', {
        headers: {
          'Authorization': `Bearer ${this.token}`
        }
      })
      this.user = await response.json()
    },
  },
})

// ═══════════════════════════════════════════
// Composition API Style (Alternative)
// ═══════════════════════════════════════════

export const useUserStore = defineStore('user', () => {
  const user = ref(null)
  const token = ref(null)
  const loading = ref(false)

  const isAuthenticated = computed(() => !!token.value)
  const userName = computed(() => user.value?.name || 'Guest')

  async function login(credentials) {
    loading.value = true
    try {
      const response = await fetch('/api/login', {
        method: 'POST',
        body: JSON.stringify(credentials),
      })
      const data = await response.json()
      user.value = data.user
      token.value = data.token
    } finally {
      loading.value = false
    }
  }

  function logout() {
    user.value = null
    token.value = null
  }

  return {
    user,
    token,
    loading,
    isAuthenticated,
    userName,
    login,
    logout,
  }
})

// ═══════════════════════════════════════════
// Using in Components
// ═══════════════════════════════════════════

<script setup>
import { useUserStore } from '@/stores/user'
import { storeToRefs } from 'pinia'

const userStore = useUserStore()

// Destructure with reactivity
const { user, isAuthenticated, userName } = storeToRefs(userStore)

// Actions don't need storeToRefs
const { login, logout } = userStore

const handleLogin = async () => {
  await login({ email: 'user@example.com', password: 'password' })
}
</script>

<template>
  <div>
    <p v-if="isAuthenticated">Welcome, {{ userName }}!</p>
    <button @click="handleLogin">Login</button>
    <button @click="logout">Logout</button>
  </div>
</template>

// ═══════════════════════════════════════════
// Persist State
// ═══════════════════════════════════════════

npm install pinia-plugin-persistedstate

// main.js
import piniaPluginPersistedstate from 'pinia-plugin-persistedstate'

const pinia = createPinia()
pinia.use(piniaPluginPersistedstate)

// store with persistence
export const useUserStore = defineStore('user', {
  state: () => ({
    user: null,
    token: null,
  }),
  persist: true, // ✨ Magic!
})
```

**📦 Pinia Resources:**

- Docs: https://pinia.vuejs.org/
- Why: Official, simple, TypeScript-first

> **💡 Pro Tip:** Pinia is the official state management for Vue 3. Much simpler than Vuex, with better TypeScript support!

<div align="center">

## 🗂️ Routing

</div>

### Vue Router - Official Routing 🧭

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install vue-router
```

```javascript
// ═══════════════════════════════════════════
// Router Setup
// ═══════════════════════════════════════════

// router/index.js
import { createRouter, createWebHistory } from "vue-router";

const routes = [
  {
    path: "/",
    name: "Home",
    component: () => import("@/views/Home.vue"),
  },
  {
    path: "/about",
    name: "About",
    component: () => import("@/views/About.vue"),
  },
  {
    path: "/users/:id",
    name: "UserProfile",
    component: () => import("@/views/UserProfile.vue"),
    props: true, // Pass route params as props
  },
  {
    path: "/dashboard",
    component: () => import("@/layouts/Dashboard.vue"),
    meta: { requiresAuth: true },
    children: [
      {
        path: "",
        name: "DashboardHome",
        component: () => import("@/views/DashboardHome.vue"),
      },
      {
        path: "settings",
        name: "Settings",
        component: () => import("@/views/Settings.vue"),
      },
    ],
  },
  {
    path: "/:pathMatch(.*)*",
    name: "NotFound",
    component: () => import("@/views/NotFound.vue"),
  },
];

const router = createRouter({
  history: createWebHistory(),
  routes,
  scrollBehavior(to, from, savedPosition) {
    if (savedPosition) {
      return savedPosition;
    } else {
      return { top: 0 };
    }
  },
});

// Navigation Guards
router.beforeEach((to, from, next) => {
  const userStore = useUserStore();

  if (to.meta.requiresAuth && !userStore.isAuthenticated) {
    next("/login");
  } else {
    next();
  }
});

export default router;
```

```vue
<!-- ═══════════════════════════════════════════ -->
<!-- Using Router in Components -->
<!-- ═══════════════════════════════════════════ -->

<script setup>
import { useRouter, useRoute } from "vue-router";

const router = useRouter();
const route = useRoute();

// Get route params
const userId = computed(() => route.params.id);

// Get query params
const search = computed(() => route.query.search);

// Navigation
const goToHome = () => {
  router.push("/");
};

const goToUser = (id) => {
  router.push({ name: "UserProfile", params: { id } });
};

const goBack = () => {
  router.back();
};

// With query params
const searchUsers = (query) => {
  router.push({
    name: "Users",
    query: { search: query, page: 1 },
  });
};
</script>

<template>
  <div>
    <!-- Navigation Links -->
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
      <RouterLink :to="{ name: 'UserProfile', params: { id: 123 } }">
        User Profile
      </RouterLink>
    </nav>

    <!-- Route View -->
    <RouterView />

    <!-- Named Routes -->
    <RouterView name="sidebar" />

    <!-- With Transition -->
    <RouterView v-slot="{ Component }">
      <Transition name="fade">
        <component :is="Component" />
      </Transition>
    </RouterView>
  </div>
</template>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
```

**📦 Vue Router Resources:**

- Docs: https://router.vuejs.org/
- Guide: https://router.vuejs.org/guide/

> **💡 Pro Tip:** Use lazy loading for routes to improve performance. Navigation guards are perfect for authentication checks!

---

<div align="center">

## 🔧 VueUse Composables

</div>

### 200+ Essential Composables 🛠️

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install @vueuse/core
```

```vue
<!-- ═══════════════════════════════════════════ -->
<!-- Browser APIs -->
<!-- ═══════════════════════════════════════════ -->

<script setup>
import {
  useLocalStorage,
  useSessionStorage,
  useMouse,
  useWindowSize,
  useMediaQuery,
  useClipboard,
  useTitle,
  useFavicon,
  useOnline,
  useGeolocation,
  useDark,
  useToggle,
} from "@vueuse/core";

// Local Storage (reactive!)
const theme = useLocalStorage("theme", "dark");
const user = useLocalStorage("user", null);

// Session Storage
const tempData = useSessionStorage("temp", {});

// Mouse position
const { x, y } = useMouse();

// Window size
const { width, height } = useWindowSize();

// Media queries
const isMobile = useMediaQuery("(max-width: 768px)");
const prefersDark = useMediaQuery("(prefers-color-scheme: dark)");

// Clipboard
const { text, copy, copied, isSupported } = useClipboard();

const copyToClipboard = async () => {
  await copy("Hello, World!");
};

// Document title
useTitle("My Amazing App");

// Favicon
useFavicon("/favicon.ico");

// Online status
const online = useOnline();

// Geolocation
const { coords, error } = useGeolocation();

// Dark mode
const isDark = useDark();
const toggleDark = useToggle(isDark);
</script>

<template>
  <div>
    <p>Mouse: {{ x }}, {{ y }}</p>
    <p>Window: {{ width }} x {{ height }}</p>
    <p>Mobile: {{ isMobile }}</p>
    <p>Online: {{ online }}</p>
    <p>Copied: {{ copied }}</p>

    <button @click="copyToClipboard">Copy</button>
    <button @click="toggleDark()">Toggle Dark Mode</button>
  </div>
</template>

<!-- ═══════════════════════════════════════════ -->
<!-- Async & Data -->
<!-- ═══════════════════════════════════════════ -->

<script setup>
import {
  useFetch,
  useAsyncState,
  useDebounce,
  useThrottle,
  useInterval,
  useTimeout,
} from "@vueuse/core";

// Fetch with automatic retry
const { data, error, isFetching, execute } = useFetch("/api/users", {
  refetch: true,
}).json();

// Async state
const { state, isLoading, error } = useAsyncState(async () => {
  const response = await fetch("/api/data");
  return response.json();
}, null);

// Debounce
const search = ref("");
const debouncedSearch = useDebounce(search, 500);

watch(debouncedSearch, (value) => {
  // API call only after 500ms of no typing
  searchAPI(value);
});

// Throttle
const scrollHandler = useThrottle(() => {
  console.log("Scrolled!");
}, 200);

// Interval
const { counter, pause, resume } = useInterval(1000);

// Timeout
const { ready, start, stop } = useTimeout(3000);
</script>

<!-- ═══════════════════════════════════════════ -->
<!-- Element & Component -->
<!-- ═══════════════════════════════════════════ -->

<script setup>
import {
  useElementSize,
  useElementVisibility,
  useIntersectionObserver,
  useResizeObserver,
  useScroll,
} from "@vueuse/core";

const el = ref(null);

// Element size
const { width, height } = useElementSize(el);

// Element visibility
const targetIsVisible = useElementVisibility(el);

// Intersection Observer
const { stop } = useIntersectionObserver(el, ([{ isIntersecting }]) => {
  if (isIntersecting) {
    console.log("Element is visible!");
  }
});

// Resize Observer
useResizeObserver(el, (entries) => {
  const entry = entries[0];
  const { width, height } = entry.contentRect;
  console.log(`Size: ${width} x ${height}`);
});

// Scroll
const { x, y, isScrolling, arrivedState } = useScroll(window);
</script>

<template>
  <div ref="el">
    <p>Size: {{ width }} x {{ height }}</p>
    <p>Visible: {{ targetIsVisible }}</p>
  </div>
</template>
```

**📦 VueUse Resources:**

- Docs: https://vueuse.org/
- Functions: 200+ composables
- Playground: https://play.vueuse.org/

> **💡 Pro Tip:** VueUse is a must-have for Vue 3 projects. It provides composables for everything - browser APIs, animations, sensors, and more!

---

<div align="center">

## 📝 Form Handling

</div>

### VeeValidate - Form Validation 📋

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install vee-validate yup
```

```vue
<!-- ═══════════════════════════════════════════ -->
<!-- Form with Validation -->
<!-- ═══════════════════════════════════════════ -->

<script setup>
import { useForm, useField } from "vee-validate";
import * as yup from "yup";

// Validation schema
const schema = yup.object({
  email: yup.string().email().required(),
  password: yup.string().min(8).required(),
  name: yup.string().required(),
  age: yup.number().positive().integer().required(),
});

// Setup form
const { handleSubmit, errors, isSubmitting } = useForm({
  validationSchema: schema,
});

// Setup fields
const { value: email } = useField("email");
const { value: password } = useField("password");
const { value: name } = useField("name");
const { value: age } = useField("age");

// Submit handler
const onSubmit = handleSubmit(async (values) => {
  console.log("Form values:", values);
  await submitToAPI(values);
});
</script>

<template>
  <form @submit="onSubmit">
    <div>
      <label>Name</label>
      <input v-model="name" type="text" />
      <span class="error">{{ errors.name }}</span>
    </div>

    <div>
      <label>Email</label>
      <input v-model="email" type="email" />
      <span class="error">{{ errors.email }}</span>
    </div>

    <div>
      <label>Password</label>
      <input v-model="password" type="password" />
      <span class="error">{{ errors.password }}</span>
    </div>

    <div>
      <label>Age</label>
      <input v-model.number="age" type="number" />
      <span class="error">{{ errors.age }}</span>
    </div>

    <button type="submit" :disabled="isSubmitting">
      {{ isSubmitting ? "Submitting..." : "Submit" }}
    </button>
  </form>
</template>

<style scoped>
.error {
  color: red;
  font-size: 0.875rem;
}
</style>
```

**📦 VeeValidate Resources:**

- Docs: https://vee-validate.logaretm.com/
- Why: Powerful validation, Yup integration

> **💡 Pro Tip:** VeeValidate works great with Yup or Zod for schema validation. Perfect for complex forms!

---

<div align="center">

## 🧪 Testing

</div>

### Vitest + Vue Test Utils 🔬

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install -D vitest @vue/test-utils @vitest/ui
npm install -D jsdom
```

```javascript
// ═══════════════════════════════════════════
// Vitest Config
// ═══════════════════════════════════════════

// vitest.config.js
import { defineConfig } from "vitest/config";
import vue from "@vitejs/plugin-vue";

export default defineConfig({
  plugins: [vue()],
  test: {
    globals: true,
    environment: "jsdom",
  },
});
```

```javascript
// ═══════════════════════════════════════════
// Component Tests
// ═══════════════════════════════════════════

// Counter.spec.js
import { mount } from "@vue/test-utils";
import { describe, it, expect } from "vitest";
import Counter from "@/components/Counter.vue";

describe("Counter", () => {
  it("renders initial count", () => {
    const wrapper = mount(Counter);
    expect(wrapper.text()).toContain("Count: 0");
  });

  it("increments count on button click", async () => {
    const wrapper = mount(Counter);

    const button = wrapper.find("button");
    await button.trigger("click");

    expect(wrapper.text()).toContain("Count: 1");
  });

  it("accepts initial value prop", () => {
    const wrapper = mount(Counter, {
      props: {
        initialValue: 10,
      },
    });

    expect(wrapper.text()).toContain("Count: 10");
  });
});

// ═══════════════════════════════════════════
// Testing with Pinia
// ═══════════════════════════════════════════

import { setActivePinia, createPinia } from "pinia";

describe("User Store", () => {
  beforeEach(() => {
    setActivePinia(createPinia());
  });

  it("logs in user", async () => {
    const store = useUserStore();

    await store.login({ email: "test@example.com", password: "password" });

    expect(store.isAuthenticated).toBe(true);
    expect(store.user).toBeTruthy();
  });
});

// ═══════════════════════════════════════════
// Testing Composables
// ═══════════════════════════════════════════

import { useCounter } from "@/composables/useCounter";

describe("useCounter", () => {
  it("increments count", () => {
    const { count, increment } = useCounter(0);

    expect(count.value).toBe(0);
    increment();
    expect(count.value).toBe(1);
  });
});
```

**📦 Testing Resources:**

- Vitest: https://vitest.dev/
- Vue Test Utils: https://test-utils.vuejs.org/

> **💡 Pro Tip:** Vitest is fast and has great Vue support. Use Vue Test Utils for component testing!

---

<div align="center">

## 🛠️ Developer Tools

</div>

### Essential Vue DevTools 🔧

```bash
# ═══════════════════════════════════════════
# Vue DevTools Browser Extension
# ═══════════════════════════════════════════

Chrome: https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd
Firefox: https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/

Features:
  ✅ Component tree inspection
  ✅ Pinia/Vuex state debugging
  ✅ Router inspection
  ✅ Performance profiling
  ✅ Timeline for events

# ═══════════════════════════════════════════
# Vite DevTools
# ═══════════════════════════════════════════

Built into Vite:
  ✅ Fast HMR
  ✅ Module graph
  ✅ Instant feedback

# ═══════════════════════════════════════════
# Nuxt DevTools
# ═══════════════════════════════════════════

// nuxt.config.ts
export default defineNuxtConfig({
  devtools: { enabled: true }
})

Features:
  ✅ Component inspector
  ✅ Route viewer
  ✅ State management
  ✅ API routes inspector
  ✅ Asset inspector
```

---

<div align="center">

## 💡 Best Practices

</div>

### Vue Best Practices 2025 ⭐

```vue
<!-- ═══════════════════════════════════════════ -->
<!-- Component Structure -->
<!-- ═══════════════════════════════════════════ -->

<!-- ✅ GOOD: Use <script setup> -->
<script setup>
import { ref, computed } from "vue";

const count = ref(0);
const double = computed(() => count.value * 2);
</script>

<!-- ❌ BAD: Options API for new projects -->
<script>
export default {
  data() {
    return { count: 0 };
  },
  computed: {
    double() {
      return this.count * 2;
    },
  },
};
</script>

<!-- ═══════════════════════════════════════════ -->
<!-- Props & Emits -->
<!-- ═══════════════════════════════════════════ -->

<!-- ✅ GOOD: Define props & emits -->
<script setup>
const props = defineProps({
  title: String,
  count: {
    type: Number,
    default: 0,
  },
});

const emit = defineEmits(["update", "delete"]);
</script>

<!-- ✅ BETTER: TypeScript -->
<script setup lang="ts">
interface Props {
  title: string;
  count?: number;
}

const props = withDefaults(defineProps<Props>(), {
  count: 0,
});

const emit = defineEmits<{
  update: [value: number];
  delete: [id: string];
}>();
</script>

<!-- ═══════════════════════════════════════════ -->
<!-- Composables -->
<!-- ═══════════════════════════════════════════ -->

<!-- ✅ GOOD: Extract reusable logic -->
// composables/useAuth.js export function useAuth() { const user = ref(null)
const isAuthenticated = computed(() => !!user.value) const login = async
(credentials) => { user.value = await api.login(credentials) } return { user,
isAuthenticated, login } }

<!-- ═══════════════════════════════════════════ -->
<!-- Performance -->
<!-- ═══════════════════════════════════════════ -->

<!-- ✅ GOOD: Use v-memo for expensive renders -->
<template>
  <div v-memo="[item.id, item.selected]">
    {{ item.name }}
  </div>
</template>

<!-- ✅ GOOD: Use v-once for static content -->
<template>
  <div v-once>
    {{ staticContent }}
  </div>
</template>

<!-- ✅ GOOD: Lazy load components -->
<script setup>
const HeavyComponent = defineAsyncComponent(() =>
  import("./HeavyComponent.vue")
);
</script>
```

---

### Project Structure 📁

```
src/
├── assets/              # Static assets
├── components/          # Reusable components
│   ├── ui/             # Generic UI components
│   └── features/       # Feature-specific
├── composables/         # Composition functions
│   ├── useAuth.js
│   └── useFetch.js
├── layouts/             # Layout components
├── pages/              # Route pages (Nuxt)
├── router/             # Router configuration
├── stores/             # Pinia stores
│   ├── user.js
│   └── todos.js
├── utils/              # Utility functions
├── App.vue
└── main.js
```

---

<div align="center">

## 🏆 MrDib's Vue Stack 2025

### _The Winning Combination_ 🚀

</div>

```yaml
Framework: "Nuxt 3"
Language: "TypeScript"
Styling: "Tailwind CSS"
UI Library: "Element Plus or Naive UI"
State: "Pinia"
Forms: "VeeValidate + Yup"
Utils: "VueUse"
Testing: "Vitest + Vue Test Utils"
Deployment: "Vercel or Netlify"

Why This Stack: ✅ Modern & maintainable
  ✅ Excellent TypeScript support
  ✅ Great developer experience
  ✅ Production-ready
  ✅ Performant by default
```

---

<div align="center">

**Built with 💚 by MrDib, for Vue Developers**

_"Vue makes building UIs enjoyable. The ecosystem makes it unstoppable!"_

**Happy Coding!** 🚀

**If you found this helpful, give it a ⭐ star and share with fellow developers!**

</div>

---

### Contributing 🤝

Found a great Vue library? Want to add examples? Contributions are welcome!

1. Fork the repository
2. Add your examples
3. Update comparison tables
4. Submit a pull request

---

### License 📄

This guide is open source and available under the MIT License.

---

<div align="center">

**Stay progressive. Keep building. Ship with Vue!** 💪✨

💚 **#Vue** 💚 **#DevResourceVault** 💚 **#MrDib** 💚

### Remember

> _"Vue is approachable, versatile, and performant"_

> _"Composition API > Options API for new projects"_

> _"Nuxt makes Vue development a breeze"_

> _"Always use TypeScript for better DX"_

> _"VueUse is your best friend"_

</div>

---

<div align="center">

**Now go forth and build amazing things with Vue!** 🌟💚

</div>
