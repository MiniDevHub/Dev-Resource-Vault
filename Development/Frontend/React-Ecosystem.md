<div align="center">

# ⚛️ React Ecosystem

### _The complete toolkit for building modern React applications_ 🚀

![React](https://img.shields.io/badge/React-18.3+-blue?style=for-the-badge&logo=react)
![Ecosystem](https://img.shields.io/badge/Ecosystem-Rich-green?style=for-the-badge)
![Community](https://img.shields.io/badge/Community-Huge-purple?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [⚛️ React Fundamentals](#️-react-fundamentals)
- [🏗️ Meta-Frameworks](#️-meta-frameworks)
- [🎣 Essential Hooks](#-essential-hooks)
- [🗂️ Routing](#️-routing)
- [🔄 State Management](#-state-management)
- [📡 Data Fetching](#-data-fetching)
- [📝 Form Handling](#-form-handling)
- [🎨 UI Libraries](#-ui-libraries)
- [🎬 Animation](#-animation)
- [🧪 Testing](#-testing)
- [🛠️ Developer Tools](#️-developer-tools)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## ⚛️ React Fundamentals

</div>

### Modern React (18.3+) 🚀

```bash
# ═══════════════════════════════════════════
# Create New React App
# ═══════════════════════════════════════════

# Vite (Recommended - Fast!)
npm create vite@latest my-app -- --template react
cd my-app
npm install
npm run dev

# With TypeScript
npm create vite@latest my-app -- --template react-ts

# Next.js (Full-stack)
npx create-next-app@latest my-app

# Remix
npx create-remix@latest my-app
```

```jsx
// ═══════════════════════════════════════════
// Modern React Component Patterns
// ═══════════════════════════════════════════

import { useState, useEffect, useMemo, useCallback } from "react";

// Functional Component with Hooks
function Counter() {
  const [count, setCount] = useState(0);

  const increment = () => setCount((c) => c + 1);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}

// With Props & TypeScript
interface UserCardProps {
  name: string;
  age: number;
  onEdit?: (id: string) => void;
}

function UserCard({ name, age, onEdit }: UserCardProps) {
  return (
    <div className="user-card">
      <h3>{name}</h3>
      <p>Age: {age}</p>
      {onEdit && <button onClick={() => onEdit("123")}>Edit</button>}
    </div>
  );
}

// ═══════════════════════════════════════════
// Core Hooks
// ═══════════════════════════════════════════

function DataFetchingComponent() {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);

  // Side effects
  useEffect(() => {
    async function fetchData() {
      const response = await fetch("/api/data");
      const json = await response.json();
      setData(json);
      setLoading(false);
    }

    fetchData();

    // Cleanup
    return () => {
      console.log("Component unmounting");
    };
  }, []); // Empty deps = run once

  // Memoized expensive calculation
  const processedData = useMemo(() => {
    if (!data) return null;
    return data.map((item) => item.value * 2);
  }, [data]);

  // Memoized callback
  const handleClick = useCallback((id) => {
    console.log("Clicked:", id);
  }, []);

  if (loading) return <div>Loading...</div>;

  return (
    <div>
      {processedData?.map((value, i) => (
        <div key={i} onClick={() => handleClick(i)}>
          {value}
        </div>
      ))}
    </div>
  );
}

// ═══════════════════════════════════════════
// Context API
// ═══════════════════════════════════════════

import { createContext, useContext } from "react";

// Create context
const ThemeContext = createContext("light");

// Provider
function App() {
  const [theme, setTheme] = useState("dark");

  return (
    <ThemeContext.Provider value={theme}>
      <Header />
      <Main />
    </ThemeContext.Provider>
  );
}

// Consumer
function Header() {
  const theme = useContext(ThemeContext);
  return <header className={theme}>Header</header>;
}

// ═══════════════════════════════════════════
// Custom Hooks
// ═══════════════════════════════════════════

function useLocalStorage(key, initialValue) {
  const [value, setValue] = useState(() => {
    const stored = localStorage.getItem(key);
    return stored ? JSON.parse(stored) : initialValue;
  });

  useEffect(() => {
    localStorage.setItem(key, JSON.stringify(value));
  }, [key, value]);

  return [value, setValue];
}

// Usage
function Settings() {
  const [theme, setTheme] = useLocalStorage("theme", "dark");

  return (
    <select value={theme} onChange={(e) => setTheme(e.target.value)}>
      <option value="light">Light</option>
      <option value="dark">Dark</option>
    </select>
  );
}
```

**📦 React Resources:**

- Docs: https://react.dev/
- New Docs (Beta): https://react.dev/learn
- GitHub: https://github.com/facebook/react

> **💡 Pro Tip:** Always use functional components with hooks. Class components are legacy. Use TypeScript for better developer experience and fewer bugs!

---

<div align="center">

## 🏗️ Meta-Frameworks

</div>

### Next.js - The React Framework 🔺

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npx create-next-app@latest my-app
cd my-app
npm run dev
```

```jsx
// ═══════════════════════════════════════════
// App Router (Next.js 13+)
// ═══════════════════════════════════════════

// app/page.tsx - Home page
export default function HomePage() {
    return (
        <div>
            <h1>Welcome to Next.js!</h1>
        </div>
    );
}

// app/about/page.tsx - About page
export default function AboutPage() {
    return <div>About Us</div>;
}

// ═══════════════════════════════════════════
// Server Components (Default in App Router)
// ═══════════════════════════════════════════

// This runs on the server!
async function UserList() {
    const users = await fetch('https://api.example.com/users', {
        cache: 'no-store' // or 'force-cache'
    }).then(res => res.json());

    return (
        <ul>
            {users.map(user => (
                <li key={user.id}>{user.name}</li>
            ))}
        </ul>
    );
}

// ═══════════════════════════════════════════
// Client Components
// ═══════════════════════════════════════════

'use client'; // Mark as client component

import { useState } from 'react';

export function Counter() {
    const [count, setCount] = useState(0);

    return (
        <button onClick={() => setCount(count + 1)}>
            Count: {count}
        </button>
    );
}

// ═══════════════════════════════════════════
// Dynamic Routes
// ═══════════════════════════════════════════

// app/blog/[slug]/page.tsx
export default async function BlogPost({ params }) {
    const post = await fetchPost(params.slug);

    return (
        <article>
            <h1>{post.title}</h1>
            <p>{post.content}</p>
        </article>
    );
}

// Generate static params
export async function generateStaticParams() {
    const posts = await fetchAllPosts();

    return posts.map((post) => ({
        slug: post.slug,
    }));
}

// ═══════════════════════════════════════════
// API Routes
// ═══════════════════════════════════════════

// app/api/users/route.ts
import { NextResponse } from 'next/server';

export async function GET() {
    const users = await fetchUsers();
    return NextResponse.json(users);
}

export async function POST(request: Request) {
    const body = await request.json();
    const user = await createUser(body);
    return NextResponse.json(user, { status: 201 });
}

// ═══════════════════════════════════════════
// Layouts (Shared UI)
// ═══════════════════════════════════════════

// app/layout.tsx
export default function RootLayout({ children }) {
    return (
        <html lang="en">
            <body>
                <nav>Navigation</nav>
                {children}
                <footer>Footer</footer>
            </body>
        </html>
    );
}

// Nested layout: app/blog/layout.tsx
export default function BlogLayout({ children }) {
    return (
        <div>
            <aside>Blog Sidebar</aside>
            <main>{children}</main>
        </div>
    );
}

// ═══════════════════════════════════════════
// Loading & Error States
// ═══════════════════════════════════════════

// app/loading.tsx
export default function Loading() {
    return <div>Loading...</div>;
}

// app/error.tsx
'use client';

export default function Error({ error, reset }) {
    return (
        <div>
            <h2>Something went wrong!</h2>
            <button onClick={() => reset()}>Try again</button>
        </div>
    );
}

// ═══════════════════════════════════════════
// Metadata
// ═══════════════════════════════════════════

export const metadata = {
    title: 'My App',
    description: 'Welcome to my app',
    openGraph: {
        title: 'My App',
        description: 'Welcome to my app',
        images: ['/og-image.png'],
    },
};
```

**📦 Next.js Resources:**

- Docs: https://nextjs.org/docs
- Learn: https://nextjs.org/learn
- Examples: https://github.com/vercel/next.js/tree/canary/examples

> **💡 Pro Tip:** Next.js App Router is the future - learn it! Server Components reduce JavaScript sent to the client. Use Client Components only when needed (interactivity, hooks, browser APIs).

---

### Remix - Full Stack React Framework 🎨

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npx create-remix@latest my-app
cd my-app
npm run dev
```

```jsx
// ═══════════════════════════════════════════
// Route with Loader & Action
// ═══════════════════════════════════════════

// app/routes/posts.$postId.tsx
import { json } from "@remix-run/node";
import { useLoaderData, Form } from "@remix-run/react";

// Server-side data loading
export async function loader({ params }) {
  const post = await fetchPost(params.postId);
  return json({ post });
}

// Server-side form handling
export async function action({ request }) {
  const formData = await request.formData();
  const comment = await createComment({
    text: formData.get("text"),
  });
  return json({ comment });
}

// Component
export default function Post() {
  const { post } = useLoaderData();

  return (
    <div>
      <h1>{post.title}</h1>
      <p>{post.content}</p>

      <Form method="post">
        <input name="text" />
        <button type="submit">Add Comment</button>
      </Form>
    </div>
  );
}
```

**📦 Remix Resources:**

- Docs: https://remix.run/docs
- Why: Progressive enhancement, nested routing

> **💡 Pro Tip:** Remix is great for forms-heavy apps. It works without JavaScript!

---

<div align="center">

## 🎣 Essential Hooks

</div>

### React Use - 50+ Hooks Collection 🪝

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install react-use
```

```jsx
// ═══════════════════════════════════════════
// Popular Hooks from react-use
// ═══════════════════════════════════════════

import {
  useLocalStorage,
  useDebounce,
  useMediaQuery,
  useToggle,
  useInterval,
  useCopyToClipboard,
  useTitle,
  useFavicon,
  usePrevious,
  useMount,
  useUnmount,
  useUpdateEffect,
} from "react-use";

function HooksExample() {
  // Local storage
  const [user, setUser] = useLocalStorage("user", null);

  // Debounce
  const [search, setSearch] = useState("");
  const debouncedSearch = useDebounce(search, 500);

  // Media query
  const isMobile = useMediaQuery("(max-width: 768px)");

  // Toggle
  const [isOpen, toggle] = useToggle(false);

  // Interval
  useInterval(() => {
    console.log("Tick");
  }, 1000);

  // Copy to clipboard
  const [state, copyToClipboard] = useCopyToClipboard();

  // Document title
  useTitle("My Page Title");

  // Previous value
  const [count, setCount] = useState(0);
  const prevCount = usePrevious(count);

  // Lifecycle
  useMount(() => console.log("Component mounted"));
  useUnmount(() => console.log("Component will unmount"));
  useUpdateEffect(() => {
    console.log("Component updated, but not on mount");
  }, [count]);

  return <div>{/* Your component */}</div>;
}
```

**📦 React Use Resources:**

- Docs: https://github.com/streamich/react-use
- Hooks: 50+ utility hooks

> **💡 Pro Tip:** React Use saves you from writing common hooks. Check if the hook you need already exists before creating your own!

---

<div align="center">

## 🗂️ Routing

</div>

### React Router - Client-Side Routing 🛤️

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install react-router-dom
```

```jsx
// ═══════════════════════════════════════════
// React Router v6
// ═══════════════════════════════════════════

import {
    createBrowserRouter,
    RouterProvider,
    Route,
    Link,
    Outlet,
    useParams,
    useNavigate,
    useSearchParams,
    useLoaderData,
} from 'react-router-dom';

// ═══════════════════════════════════════════
// Modern Router Setup (Data Router)
// ═══════════════════════════════════════════

const router = createBrowserRouter([
    {
        path: '/',
        element: <Root />,
        errorElement: <ErrorPage />,
        loader: rootLoader,
        children: [
            {
                index: true,
                element: <HomePage />,
            },
            {
                path: 'about',
                element: <AboutPage />,
            },
            {
                path: 'users',
                element: <UsersLayout />,
                children: [
                    {
                        index: true,
                        element: <UsersList />,
                        loader: usersLoader,
                    },
                    {
                        path: ':userId',
                        element: <UserProfile />,
                        loader: userLoader,
                    },
                ],
            },
        ],
    },
]);

function App() {
    return <RouterProvider router={router} />;
}

// ═══════════════════════════════════════════
// Layout Component
// ═══════════════════════════════════════════

function Root() {
    return (
        <div>
            <nav>
                <Link to="/">Home</Link>
                <Link to="/about">About</Link>
                <Link to="/users">Users</Link>
            </nav>
            <main>
                <Outlet /> {/* Child routes render here */}
            </main>
        </div>
    );
}

// ═══════════════════════════════════════════
// Data Loading
// ═══════════════════════════════════════════

async function usersLoader() {
    const response = await fetch('/api/users');
    return response.json();
}

async function userLoader({ params }) {
    const response = await fetch(`/api/users/${params.userId}`);
    return response.json();
}

function UserProfile() {
    const user = useLoaderData();
    return <div>{user.name}</div>;
}

// ═══════════════════════════════════════════
// Navigation Hooks
// ═══════════════════════════════════════════

function Example() {
    const { userId } = useParams();
    const navigate = useNavigate();
    const [searchParams, setSearchParams] = useSearchParams();

    const handleClick = () => {
        navigate('/dashboard');
        // Or with state
        navigate('/dashboard', { state: { from: 'home' } });
    };

    const query = searchParams.get('q');
    const updateQuery = (value) => {
        setSearchParams({ q: value });
    };

    return <div>{/* ... */}</div>;
}

// ═══════════════════════════════════════════
// Protected Routes
// ═══════════════════════════════════════════

function ProtectedRoute({ children }) {
    const { user } = useAuth();
    const navigate = useNavigate();

    useEffect(() => {
        if (!user) {
            navigate('/login');
        }
    }, [user, navigate]);

    return user ? children : null;
}

// In router
{
    path: 'dashboard',
    element: (
        <ProtectedRoute>
            <Dashboard />
        </ProtectedRoute>
    ),
}
```

**📦 React Router Resources:**

- Docs: https://reactrouter.com/
- Tutorial: https://reactrouter.com/en/main/start/tutorial

> **💡 Pro Tip:** Use the Data Router API (createBrowserRouter) - it enables data loading, actions, and better error handling!

---

<div align="center">

## 🔄 State Management

</div>

### Zustand - Bear-y Simple 🐻

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install zustand
```

```javascript
// ═══════════════════════════════════════════
# Create Store
// ═══════════════════════════════════════════

import { create } from 'zustand';
import { persist, devtools } from 'zustand/middleware';

// Simple store
const useStore = create((set) => ({
    bears: 0,
    increasePopulation: () => set((state) => ({ bears: state.bears + 1 })),
    removeAllBears: () => set({ bears: 0 }),
}));

// Usage in components
function BearCounter() {
    const bears = useStore((state) => state.bears);
    return <h1>{bears} bears around here...</h1>;
}

function Controls() {
    const increasePopulation = useStore((state) => state.increasePopulation);
    return <button onClick={increasePopulation}>Add bear</button>;
}

// ═══════════════════════════════════════════
// Advanced Store with Persistence
// ═══════════════════════════════════════════

const useAuthStore = create(
    devtools(
        persist(
            (set, get) => ({
                user: null,
                token: null,

                login: (user, token) => set({ user, token }),
                logout: () => set({ user: null, token: null }),

                updateProfile: (updates) => set((state) => ({
                    user: { ...state.user, ...updates }
                })),
            }),
            {
                name: 'auth-storage',
            }
        )
    )
);
```

**📦 Zustand Resources:**

- Docs: https://zustand-demo.pmnd.rs/
- Size: <1kb
- Why: Simple, no boilerplate, performant

> **💡 Pro Tip:** Zustand is perfect for most apps. No providers, no context, just works!

### Redux Toolkit - The Redux Standard 🔴

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install @reduxjs/toolkit react-redux
```

```javascript
// ═══════════════════════════════════════════
// Create Slice
// ═══════════════════════════════════════════

import { createSlice, configureStore } from "@reduxjs/toolkit";

const counterSlice = createSlice({
  name: "counter",
  initialState: { value: 0 },
  reducers: {
    increment: (state) => {
      state.value += 1; // Immer makes this work!
    },
    decrement: (state) => {
      state.value -= 1;
    },
    incrementByAmount: (state, action) => {
      state.value += action.payload;
    },
  },
});

export const { increment, decrement, incrementByAmount } = counterSlice.actions;

// ═══════════════════════════════════════════
// Configure Store
// ═══════════════════════════════════════════

const store = configureStore({
  reducer: {
    counter: counterSlice.reducer,
  },
});

// ═══════════════════════════════════════════
// Setup Provider
// ═══════════════════════════════════════════

import { Provider } from "react-redux";

function App() {
  return (
    <Provider store={store}>
      <Counter />
    </Provider>
  );
}

// ═══════════════════════════════════════════
// Use in Components
// ═══════════════════════════════════════════

import { useSelector, useDispatch } from "react-redux";

function Counter() {
  const count = useSelector((state) => state.counter.value);
  const dispatch = useDispatch();

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => dispatch(increment())}>+</button>
      <button onClick={() => dispatch(decrement())}>-</button>
      <button onClick={() => dispatch(incrementByAmount(5))}>+5</button>
    </div>
  );
}

// ═══════════════════════════════════════════
// Async Actions (Thunks)
// ═══════════════════════════════════════════

import { createAsyncThunk } from "@reduxjs/toolkit";

const fetchUser = createAsyncThunk("user/fetch", async (userId) => {
  const response = await fetch(`/api/users/${userId}`);
  return response.json();
});

const userSlice = createSlice({
  name: "user",
  initialState: { data: null, loading: false, error: null },
  reducers: {},
  extraReducers: (builder) => {
    builder
      .addCase(fetchUser.pending, (state) => {
        state.loading = true;
      })
      .addCase(fetchUser.fulfilled, (state, action) => {
        state.loading = false;
        state.data = action.payload;
      })
      .addCase(fetchUser.rejected, (state, action) => {
        state.loading = false;
        state.error = action.error.message;
      });
  },
});
```

**📦 Redux Toolkit Resources:**

- Docs: https://redux-toolkit.js.org/
- Why: When you need complex state logic

> **💡 Pro Tip:** Redux Toolkit fixes Redux's boilerplate problem. Only use Redux when you need time-travel debugging or complex state logic. For most apps, Zustand is simpler!

---

<div align="center">

## 📡 Data Fetching

</div>

### TanStack Query - Server State Management 👑

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install @tanstack/react-query
npm install @tanstack/react-query-devtools
```

```jsx
// ═══════════════════════════════════════════
// Setup
// ═══════════════════════════════════════════

import {
  QueryClient,
  QueryClientProvider,
  useQuery,
  useMutation,
  useQueryClient,
} from "@tanstack/react-query";
import { ReactQueryDevtools } from "@tanstack/react-query-devtools";

const queryClient = new QueryClient({
  defaultOptions: {
    queries: {
      staleTime: 5 * 60 * 1000,
      cacheTime: 10 * 60 * 1000,
      retry: 3,
      refetchOnWindowFocus: false,
    },
  },
});

function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <YourApp />
      <ReactQueryDevtools initialIsOpen={false} />
    </QueryClientProvider>
  );
}

// ═══════════════════════════════════════════
// Queries (Fetching Data)
// ═══════════════════════════════════════════

function Posts() {
  const { data, isLoading, isError, error, refetch } = useQuery({
    queryKey: ["posts"],
    queryFn: async () => {
      const response = await fetch("/api/posts");
      if (!response.ok) throw new Error("Failed to fetch");
      return response.json();
    },
  });

  if (isLoading) return <div>Loading...</div>;
  if (isError) return <div>Error: {error.message}</div>;

  return (
    <div>
      {data.map((post) => (
        <div key={post.id}>{post.title}</div>
      ))}
      <button onClick={() => refetch()}>Refresh</button>
    </div>
  );
}

// Query with parameters
function UserProfile({ userId }) {
  const { data: user } = useQuery({
    queryKey: ["user", userId],
    queryFn: () => fetchUser(userId),
    enabled: !!userId, // Only fetch if userId exists
  });

  return <div>{user?.name}</div>;
}

// ═══════════════════════════════════════════
// Mutations (Creating/Updating Data)
// ═══════════════════════════════════════════

function CreatePost() {
  const queryClient = useQueryClient();

  const mutation = useMutation({
    mutationFn: (newPost) => {
      return fetch("/api/posts", {
        method: "POST",
        body: JSON.stringify(newPost),
      });
    },
    onSuccess: () => {
      // Invalidate and refetch
      queryClient.invalidateQueries({ queryKey: ["posts"] });
    },
  });

  const handleSubmit = (e) => {
    e.preventDefault();
    mutation.mutate({ title: "New Post", content: "..." });
  };

  return (
    <form onSubmit={handleSubmit}>
      <button type="submit" disabled={mutation.isLoading}>
        {mutation.isLoading ? "Creating..." : "Create Post"}
      </button>
      {mutation.isError && <div>Error: {mutation.error.message}</div>}
      {mutation.isSuccess && <div>Post created!</div>}
    </form>
  );
}

// ═══════════════════════════════════════════
// Optimistic Updates
// ═══════════════════════════════════════════

const updateMutation = useMutation({
  mutationFn: updatePost,
  onMutate: async (newPost) => {
    await queryClient.cancelQueries({ queryKey: ["posts"] });
    const previousPosts = queryClient.getQueryData(["posts"]);

    queryClient.setQueryData(["posts"], (old) =>
      old.map((post) => (post.id === newPost.id ? newPost : post))
    );

    return { previousPosts };
  },
  onError: (err, newPost, context) => {
    queryClient.setQueryData(["posts"], context.previousPosts);
  },
  onSettled: () => {
    queryClient.invalidateQueries({ queryKey: ["posts"] });
  },
});

// ═══════════════════════════════════════════
// Pagination
// ═══════════════════════════════════════════

function PaginatedPosts() {
  const [page, setPage] = useState(1);

  const { data, isPreviousData } = useQuery({
    queryKey: ["posts", page],
    queryFn: () => fetchPosts(page),
    keepPreviousData: true,
  });

  return (
    <div>
      {data?.posts.map((post) => (
        <div key={post.id}>{post.title}</div>
      ))}
      <button
        onClick={() => setPage((p) => Math.max(1, p - 1))}
        disabled={page === 1}
      >
        Previous
      </button>
      <button
        onClick={() => setPage((p) => p + 1)}
        disabled={isPreviousData || !data?.hasMore}
      >
        Next
      </button>
    </div>
  );
}

// ═══════════════════════════════════════════
// Infinite Scroll
// ═══════════════════════════════════════════

import { useInfiniteQuery } from "@tanstack/react-query";

function InfinitePosts() {
  const { data, fetchNextPage, hasNextPage, isFetchingNextPage } =
    useInfiniteQuery({
      queryKey: ["posts"],
      queryFn: ({ pageParam = 1 }) => fetchPosts(pageParam),
      getNextPageParam: (lastPage) => lastPage.nextPage,
    });

  return (
    <div>
      {data?.pages.map((page, i) => (
        <div key={i}>
          {page.posts.map((post) => (
            <div key={post.id}>{post.title}</div>
          ))}
        </div>
      ))}
      <button
        onClick={() => fetchNextPage()}
        disabled={!hasNextPage || isFetchingNextPage}
      >
        {isFetchingNextPage ? "Loading..." : "Load More"}
      </button>
    </div>
  );
}
```

**📦 TanStack Query Resources:**

- Docs: https://tanstack.com/query/latest
- DevTools: Built-in and amazing!
- Why: Best-in-class server state management

> **💡 Pro Tip:** TanStack Query is essential for modern React apps. It handles caching, refetching, and synchronization automatically. Use it with Zustand for complete state management!

---

<div align="center">

## 📝 Form Handling

</div>

### React Hook Form - Performant Forms ⚡

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install react-hook-form
npm install @hookform/resolvers zod
```

```jsx
// ═══════════════════════════════════════════
// Basic Form
// ═══════════════════════════════════════════

import { useForm } from "react-hook-form";

function LoginForm() {
  const {
    register,
    handleSubmit,
    formState: { errors, isSubmitting },
  } = useForm();

  const onSubmit = async (data) => {
    console.log(data);
    await loginUser(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input
        {...register("email", {
          required: "Email is required",
          pattern: {
            value: /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$/i,
            message: "Invalid email",
          },
        })}
        placeholder="Email"
      />
      {errors.email && <span>{errors.email.message}</span>}

      <input
        type="password"
        {...register("password", {
          required: "Password is required",
          minLength: {
            value: 8,
            message: "Password must be at least 8 characters",
          },
        })}
        placeholder="Password"
      />
      {errors.password && <span>{errors.password.message}</span>}

      <button type="submit" disabled={isSubmitting}>
        {isSubmitting ? "Logging in..." : "Login"}
      </button>
    </form>
  );
}

// ═══════════════════════════════════════════
// With Zod Schema Validation
// ═══════════════════════════════════════════

import { zodResolver } from "@hookform/resolvers/zod";
import { z } from "zod";

const schema = z.object({
  email: z.string().email("Invalid email"),
  password: z.string().min(8, "Password must be at least 8 characters"),
  age: z.number().min(18, "Must be 18 or older"),
  acceptTerms: z.boolean().refine((val) => val === true, {
    message: "You must accept terms",
  }),
});

function SignupForm() {
  const {
    register,
    handleSubmit,
    formState: { errors },
  } = useForm({
    resolver: zodResolver(schema),
  });

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input {...register("email")} />
      {errors.email && <span>{errors.email.message}</span>}

      <input type="password" {...register("password")} />
      {errors.password && <span>{errors.password.message}</span>}

      <input type="number" {...register("age", { valueAsNumber: true })} />
      {errors.age && <span>{errors.age.message}</span>}

      <label>
        <input type="checkbox" {...register("acceptTerms")} />
        Accept Terms
      </label>
      {errors.acceptTerms && <span>{errors.acceptTerms.message}</span>}

      <button type="submit">Sign Up</button>
    </form>
  );
}

// ═══════════════════════════════════════════
// Dynamic Fields
// ═══════════════════════════════════════════

import { useFieldArray } from "react-hook-form";

function DynamicForm() {
  const { control, register } = useForm({
    defaultValues: {
      users: [{ name: "" }],
    },
  });

  const { fields, append, remove } = useFieldArray({
    control,
    name: "users",
  });

  return (
    <form>
      {fields.map((field, index) => (
        <div key={field.id}>
          <input {...register(`users.${index}.name`)} />
          <button type="button" onClick={() => remove(index)}>
            Remove
          </button>
        </div>
      ))}
      <button type="button" onClick={() => append({ name: "" })}>
        Add User
      </button>
    </form>
  );
}
```

**📦 React Hook Form Resources:**

- Docs: https://react-hook-form.com/
- Size: ~9kb
- Why: Best performance, minimal re-renders

> **💡 Pro Tip:** React Hook Form + Zod is the modern standard for forms. Uncontrolled components = better performance!

---

<div align="center">

## 🎨 UI Libraries

</div>

### shadcn/ui - Copy & Paste Components 🎭

```bash
# ═══════════════════════════════════════════
# Installation (One-time setup)
# ═══════════════════════════════════════════

npx shadcn-ui@latest init

# Add components as needed
npx shadcn-ui@latest add button
npx shadcn-ui@latest add dialog
npx shadcn-ui@latest add form
```

```jsx
// ═══════════════════════════════════════════
// Usage (Components are in your codebase!)
// ═══════════════════════════════════════════

import { Button } from "@/components/ui/button";
import {
  Dialog,
  DialogContent,
  DialogDescription,
  DialogHeader,
  DialogTitle,
  DialogTrigger,
} from "@/components/ui/dialog";

function Example() {
  return (
    <Dialog>
      <DialogTrigger asChild>
        <Button variant="outline">Open Dialog</Button>
      </DialogTrigger>
      <DialogContent>
        <DialogHeader>
          <DialogTitle>Are you sure?</DialogTitle>
          <DialogDescription>This action cannot be undone.</DialogDescription>
        </DialogHeader>
      </DialogContent>
    </Dialog>
  );
}
```

**📦 shadcn/ui Resources:**

- Docs: https://ui.shadcn.com/
- Why: Own the code, customize everything

> **💡 Pro Tip:** shadcn/ui is not an npm package - it copies components to your project. Full control!

---

### Radix UI - Headless Components 🦸

```bash
# ═══════════════════════════════════════════
# Installation (Per component)
# ═══════════════════════════════════════════

npm install @radix-ui/react-dialog
npm install @radix-ui/react-dropdown-menu
npm install @radix-ui/react-tabs

```

```jsx
// ═══════════════════════════════════════════
// Radix UI - Unstyled, Accessible
// ═══════════════════════════════════════════

import * as Dialog from "@radix-ui/react-dialog";
import * as DropdownMenu from "@radix-ui/react-dropdown-menu";

function DialogExample() {
  return (
    <Dialog.Root>
      <Dialog.Trigger asChild>
        <button className="btn">Open</button>
      </Dialog.Trigger>
      <Dialog.Portal>
        <Dialog.Overlay className="dialog-overlay" />
        <Dialog.Content className="dialog-content">
          <Dialog.Title>Dialog Title</Dialog.Title>
          <Dialog.Description>Dialog description goes here</Dialog.Description>
          <Dialog.Close asChild>
            <button>Close</button>
          </Dialog.Close>
        </Dialog.Content>
      </Dialog.Portal>
    </Dialog.Root>
  );
}
```

**📦 Radix UI Resources:**

- Docs: https://www.radix-ui.com/
- Why: Accessible primitives, full control over styles

> **💡 Pro Tip:** Radix UI is perfect for building custom design systems. shadcn/ui is built on top of Radix!

---

<div align="center">

## 🎬 Animation

</div>

### Framer Motion - Production-Ready Animations ✨

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install framer-motion
```

```jsx
// ═══════════════════════════════════════════
// Basic Animations
// ═══════════════════════════════════════════

import { motion } from "framer-motion";

function FadeIn() {
  return (
    <motion.div
      initial={{ opacity: 0, y: 20 }}
      animate={{ opacity: 1, y: 0 }}
      transition={{ duration: 0.5 }}
    >
      Content fades in!
    </motion.div>
  );
}

// ═══════════════════════════════════════════
// Gesture Animations
// ═══════════════════════════════════════════

function InteractiveCard() {
  return (
    <motion.div
      whileHover={{ scale: 1.05 }}
      whileTap={{ scale: 0.95 }}
      drag
      dragConstraints={{ left: -100, right: 100 }}
    >
      Drag me!
    </motion.div>
  );
}

// ═══════════════════════════════════════════
// Variants (Reusable Animations)
// ═══════════════════════════════════════════

const containerVariants = {
  hidden: { opacity: 0 },
  visible: {
    opacity: 1,
    transition: {
      staggerChildren: 0.1,
    },
  },
};

const itemVariants = {
  hidden: { y: 20, opacity: 0 },
  visible: { y: 0, opacity: 1 },
};

function StaggerList() {
  return (
    <motion.ul variants={containerVariants} initial="hidden" animate="visible">
      {items.map((item) => (
        <motion.li key={item.id} variants={itemVariants}>
          {item.text}
        </motion.li>
      ))}
    </motion.ul>
  );
}

// ═══════════════════════════════════════════
// Layout Animations (Magic!)
// ═══════════════════════════════════════════

function LayoutAnimation() {
  const [isOpen, setIsOpen] = useState(false);

  return (
    <motion.div
      layout
      onClick={() => setIsOpen(!isOpen)}
      style={{
        width: isOpen ? 300 : 150,
        height: isOpen ? 200 : 100,
      }}
    >
      <motion.h2 layout>Title</motion.h2>
      {isOpen && <motion.p layout>Content</motion.p>}
    </motion.div>
  );
}

// ═══════════════════════════════════════════
// Exit Animations
// ═══════════════════════════════════════════

import { AnimatePresence } from "framer-motion";

function Modal({ isOpen, onClose }) {
  return (
    <AnimatePresence>
      {isOpen && (
        <motion.div
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
          exit={{ opacity: 0 }}
          className="modal-backdrop"
          onClick={onClose}
        >
          <motion.div
            initial={{ scale: 0.8, opacity: 0 }}
            animate={{ scale: 1, opacity: 1 }}
            exit={{ scale: 0.8, opacity: 0 }}
            className="modal"
            onClick={(e) => e.stopPropagation()}
          >
            <h2>Modal Content</h2>
          </motion.div>
        </motion.div>
      )}
    </AnimatePresence>
  );
}

// ═══════════════════════════════════════════
// Scroll Animations
// ═══════════════════════════════════════════

import { useScroll, useTransform } from "framer-motion";

function ParallaxSection() {
  const { scrollYProgress } = useScroll();
  const y = useTransform(scrollYProgress, [0, 1], [0, -100]);
  const opacity = useTransform(scrollYProgress, [0, 0.5, 1], [1, 0.5, 0]);

  return <motion.div style={{ y, opacity }}>Parallax effect!</motion.div>;
}
```

**📦 Framer Motion Resources:**

- Docs: https://www.framer.com/motion/
- Examples: https://www.framer.com/motion/examples/
- Why: Powerful, production-ready, great DX

> **💡 Pro Tip:** Framer Motion's layout animations are magical - they automatically animate size and position changes. Use AnimatePresence for exit animations!

---

<div align="center">

## 🧪 Testing

</div>

### Vitest + React Testing Library 🔬

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install -D vitest @vitest/ui
npm install -D @testing-library/react @testing-library/jest-dom
npm install -D @testing-library/user-event
npm install -D jsdom
```

```javascript
// ═══════════════════════════════════════════
// Vitest Config (vitest.config.js)
// ═══════════════════════════════════════════

import { defineConfig } from "vitest/config";
import react from "@vitejs/plugin-react";

export default defineConfig({
  plugins: [react()],
  test: {
    globals: true,
    environment: "jsdom",
    setupFiles: "./src/test/setup.js",
  },
});

// ═══════════════════════════════════════════
// Setup File (src/test/setup.js)
// ═══════════════════════════════════════════

import { expect, afterEach } from "vitest";
import { cleanup } from "@testing-library/react";
import * as matchers from "@testing-library/jest-dom/matchers";

expect.extend(matchers);
afterEach(() => cleanup());
```

```jsx
// ═══════════════════════════════════════════
// Component Tests
// ═══════════════════════════════════════════

import { render, screen, fireEvent, waitFor } from "@testing-library/react";
import userEvent from "@testing-library/user-event";
import { describe, it, expect, vi } from "vitest";

// Component
function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

// Tests
describe("Counter", () => {
  it("renders with initial count", () => {
    render(<Counter />);
    expect(screen.getByText("Count: 0")).toBeInTheDocument();
  });

  it("increments count on button click", async () => {
    const user = userEvent.setup();
    render(<Counter />);

    const button = screen.getByRole("button", { name: /increment/i });
    await user.click(button);

    expect(screen.getByText("Count: 1")).toBeInTheDocument();
  });
});

// ═══════════════════════════════════════════
// Async Component Tests
// ═══════════════════════════════════════════

function UserProfile({ userId }) {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetchUser(userId).then((data) => {
      setUser(data);
      setLoading(false);
    });
  }, [userId]);

  if (loading) return <div>Loading...</div>;

  return <div>{user.name}</div>;
}

// Test
it("displays user name after loading", async () => {
  const mockUser = { name: "John Doe" };
  vi.spyOn(global, "fetch").mockResolvedValueOnce({
    json: async () => mockUser,
  });

  render(<UserProfile userId="123" />);

  expect(screen.getByText("Loading...")).toBeInTheDocument();

  await waitFor(() => {
    expect(screen.getByText("John Doe")).toBeInTheDocument();
  });
});

// ═══════════════════════════════════════════
// Testing with Context
// ═══════════════════════════════════════════

function renderWithProviders(component) {
  return render(
    <QueryClientProvider client={queryClient}>
      <ThemeProvider>{component}</ThemeProvider>
    </QueryClientProvider>
  );
}

it("renders with theme", () => {
  renderWithProviders(<MyComponent />);
  expect(screen.getByRole("button")).toHaveClass("dark-theme");
});

// ═══════════════════════════════════════════
// Mock Functions
// ═══════════════════════════════════════════

it("calls onClick handler", async () => {
  const handleClick = vi.fn();
  const user = userEvent.setup();

  render(<Button onClick={handleClick}>Click me</Button>);

  await user.click(screen.getByRole("button"));

  expect(handleClick).toHaveBeenCalledTimes(1);
});
```

**📦 Testing Resources:**

- Vitest: https://vitest.dev/
- React Testing Library: https://testing-library.com/react
- Why: Fast, modern, great DX

> **💡 Pro Tip:** Test behavior, not implementation. Focus on what users see and do, not internal state!

---

<div align="center">

## 🛠️ Developer Tools

</div>

### Essential React DevTools 🔧

```bash
# ═══════════════════════════════════════════
# React DevTools Browser Extension
# ═══════════════════════════════════════════

Chrome: https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi
Firefox: https://addons.mozilla.org/en-US/firefox/addon/react-devtools/

Features:
  ✅ Component tree inspection
  ✅ Props & state debugging
  ✅ Performance profiling
  ✅ Hook inspection
  ✅ Component source location

# ═══════════════════════════════════════════
# TanStack Query DevTools
# ═══════════════════════════════════════════

import { ReactQueryDevtools } from '@tanstack/react-query-devtools';

<QueryClientProvider client={queryClient}>
    <App />
    <ReactQueryDevtools initialIsOpen={false} />
</QueryClientProvider>

Features:
  ✅ Query cache inspection
  ✅ Network waterfall
  ✅ Manual refetch controls
  ✅ Query details

# ═══════════════════════════════════════════
# Redux DevTools
# ═══════════════════════════════════════════

const store = configureStore({
    reducer: rootReducer,
    devTools: process.env.NODE_ENV !== 'production',
});

Features:
  ✅ Action history
  ✅ Time travel debugging
  ✅ State diff viewer
  ✅ Action replay

# ═══════════════════════════════════════════
# Error Boundaries
# ═══════════════════════════════════════════

class ErrorBoundary extends React.Component {
    constructor(props) {
        super(props);
        this.state = { hasError: false };
    }

    static getDerivedStateFromError(error) {
        return { hasError: true };
    }

    componentDidCatch(error, errorInfo) {
        console.error('Error:', error, errorInfo);
    }

    render() {
        if (this.state.hasError) {
            return <h1>Something went wrong.</h1>;
        }

        return this.props.children;
    }
}

// Or use react-error-boundary
import { ErrorBoundary } from 'react-error-boundary';

<ErrorBoundary
    FallbackComponent={ErrorFallback}
    onError={(error, errorInfo) => {
        logErrorToService(error, errorInfo);
    }}
>
    <App />
</ErrorBoundary>
```

---

<div align="center">

## 💡 Best Practices

</div>

### React Best Practices 2025 ⭐

```jsx
// ═══════════════════════════════════════════
// Component Structure
// ═══════════════════════════════════════════

// ✅ GOOD: Small, focused components
function UserCard({ user }) {
  return (
    <div className="user-card">
      <Avatar src={user.avatar} />
      <UserInfo name={user.name} email={user.email} />
      <UserActions userId={user.id} />
    </div>
  );
}

// ❌ BAD: Giant components with too much logic
function UserCard({ user }) {
  // 500 lines of code...
}

// ═══════════════════════════════════════════
// Props
// ═══════════════════════════════════════════

// ✅ GOOD: Destructure props
function Button({ label, onClick, variant = "primary" }) {
  return <button onClick={onClick}>{label}</button>;
}

// ❌ BAD: Use props object directly
function Button(props) {
  return <button onClick={props.onClick}>{props.label}</button>;
}

// ✅ GOOD: Use TypeScript
interface ButtonProps {
  label: string;
  onClick: () => void;
  variant?: "primary" | "secondary";
}

// ═══════════════════════════════════════════
// State Management
// ═══════════════════════════════════════════

// ✅ GOOD: Keep state close to where it's used
function TodoList() {
  const [todos, setTodos] = useState([]);
  // Use todos only in this component
}

// ✅ GOOD: Use proper state management
// - useState for local component state
// - Context for theme, auth
// - Zustand for global client state
// - TanStack Query for server state

// ❌ BAD: Everything in global state
// ❌ BAD: Prop drilling 5 levels deep

// ═══════════════════════════════════════════
// Performance
// ═══════════════════════════════════════════

// ✅ GOOD: Memoize expensive calculations
const sortedUsers = useMemo(
  () => users.sort((a, b) => a.name.localeCompare(b.name)),
  [users]
);

// ✅ GOOD: Memoize callbacks passed to children
const handleClick = useCallback(() => {
  console.log("clicked");
}, []);

// ✅ GOOD: Use React.memo for expensive components
const ExpensiveComponent = React.memo(({ data }) => {
  // Complex rendering
});

// ❌ BAD: Premature optimization
// Don't memoize everything!

// ═══════════════════════════════════════════
// Conditional Rendering
// ═══════════════════════════════════════════

// ✅ GOOD: Early returns
function UserProfile({ user }) {
  if (!user) return null;
  if (user.loading) return <Loading />;
  if (user.error) return <Error />;

  return <div>{user.name}</div>;
}

// ❌ BAD: Nested ternaries
return (
  <div>
    {user ? (
      user.loading ? (
        <Loading />
      ) : user.error ? (
        <Error />
      ) : (
        <div>{user.name}</div>
      )
    ) : null}
  </div>
);

// ═══════════════════════════════════════════
// Naming
// ═══════════════════════════════════════════

// ✅ GOOD: Descriptive names
const [isModalOpen, setIsModalOpen] = useState(false);
const handleSubmit = () => {};
const filteredUsers = users.filter(/* ... */);

// ❌ BAD: Unclear names
const [flag, setFlag] = useState(false);
const fn = () => {};
const data2 = data.filter(/* ... */);
```

---

### Project Structure 📁

```
src/
├── components/          # Reusable components
│   ├── ui/             # Generic UI components
│   │   ├── Button.tsx
│   │   ├── Input.tsx
│   │   └── Modal.tsx
│   └── features/       # Feature-specific components
│       ├── auth/
│       └── dashboard/
├── hooks/              # Custom hooks
│   ├── useAuth.ts
│   ├── useLocalStorage.ts
│   └── useDebounce.ts
├── lib/                # Utility functions
│   ├── api.ts
│   ├── utils.ts
│   └── constants.ts
├── stores/             # State management
│   ├── authStore.ts
│   └── uiStore.ts
├── types/              # TypeScript types
│   ├── api.ts
│   └── models.ts
├── pages/              # Route components (Next.js/Remix)
│   ├── index.tsx
│   └── about.tsx
└── App.tsx
```

---

<div align="center">

## 🏆 MrDib's React Stack 2025

### _The Ultimate Setup_ 🚀

</div>

```yaml
Framework: "Next.js 14 (App Router)"
Language: "TypeScript"
Styling: "Tailwind CSS"
UI Components: "shadcn/ui + Radix UI"
State Management: "Zustand + TanStack Query"
Forms: "React Hook Form + Zod"
Animation: "Framer Motion"
Testing: "Vitest + React Testing Library"
Hooks: "react-use"
Dev Tools: "React DevTools + TanStack Query DevTools"
Deployment: "Vercel"

Why This Stack: ✅ Modern & maintained
  ✅ Excellent TypeScript support
  ✅ Great developer experience
  ✅ Production-ready
  ✅ Performant by default
  ✅ Strong community
```

---

<div align="center">

## 🎓 Learning Resources

### _Master React_ 📚

</div>

**Official:**

- React Docs: https://react.dev/
- Next.js Docs: https://nextjs.org/docs
- TanStack Query: https://tanstack.com/query/latest

**Courses:**

- Epic React by Kent C. Dodds
- Next.js 14 Masterclass
- React Query Essentials

**YouTube Channels:**

- Theo - t3.gg
- Jack Herrington
- Web Dev Simplified
- Fireship

**Practice:**

- Frontend Mentor: https://frontendmentor.io/
- React Challenges: https://react-challenges.vercel.app/

---

<div align="center">

**Built with ⚛️ by MrDib, for React Developers**

_"React makes building UIs a joy. The ecosystem makes it unstoppable!"_

**Happy Coding!** 🚀

**If you found this helpful, give it a ⭐ star and share with fellow developers!**

</div>

---

### Contributing 🤝

Found a great React library? Want to add examples? Contributions are welcome!

1. Fork the repository
2. Add your examples
3. Update the comparison tables
4. Submit a pull request

---

### License 📄

This guide is open source and available under the MIT License.

---

<div align="center">

**Stay reactive. Keep building. Ship amazing apps!** 💪✨

⚛️ **#React** ⚛️ **#DevResourceVault** ⚛️ **#MrDib** ⚛️

### Remember

> _"The best code is code you don't have to write - use the ecosystem!"_

> _"Server state ≠ Client state - use the right tools"_

> _"Performance matters, but premature optimization doesn't"_

> _"TypeScript is your friend, not your enemy"_

</div>

---

<div align="center">

**Now go forth and build the future with React!** 🌟⚛️

</div>
