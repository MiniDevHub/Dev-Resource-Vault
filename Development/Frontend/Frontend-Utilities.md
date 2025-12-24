<div align="center">

# 🔧 Frontend Utility Libraries

### _The essential toolkit for modern web development_ 🛠️

![Utilities](https://img.shields.io/badge/Utilities-100+-orange?style=for-the-badge)
![Productivity](https://img.shields.io/badge/Productivity-10x-green?style=for-the-badge)
![DX](https://img.shields.io/badge/DX-Amazing-purple?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [📅 Date & Time](#-date--time)
- [🔄 State Management](#-state-management)
- [📡 Data Fetching](#-data-fetching)
- [📝 Form Handling](#-form-handling)
- [✅ Validation](#-validation)
- [🔔 Notifications](#-notifications)
- [🆔 ID Generation](#-id-generation)
- [📁 File Handling](#-file-handling)
- [📋 Clipboard & Copy](#-clipboard--copy)
- [🎨 Styling Utilities](#-styling-utilities)
- [🔍 Search & Filter](#-search--filter)
- [⚡ Performance](#-performance)
- [💡 Tips & Best Practices](#-tips--best-practices)

---

<div align="center">

## 📅 Date & Time

</div>

### Day.js - Modern, Lightweight Date Library ⏰

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install dayjs
```

```javascript
// ═══════════════════════════════════════════
// Setup with Plugins
// ═══════════════════════════════════════════

import dayjs from "dayjs";
import relativeTime from "dayjs/plugin/relativeTime";
import customParseFormat from "dayjs/plugin/customParseFormat";
import utc from "dayjs/plugin/utc";
import timezone from "dayjs/plugin/timezone";
import duration from "dayjs/plugin/duration";
import calendar from "dayjs/plugin/calendar";

// Extend dayjs
dayjs.extend(relativeTime);
dayjs.extend(customParseFormat);
dayjs.extend(utc);
dayjs.extend(timezone);
dayjs.extend(duration);
dayjs.extend(calendar);

// ═══════════════════════════════════════════
// Basic Usage
// ═══════════════════════════════════════════

// Current date/time
const now = dayjs();

// Parse date
const date = dayjs("2025-12-25");
const customFormat = dayjs("25-12-2025", "DD-MM-YYYY");

// Format dates
dayjs().format(); // 2025-12-15T10:30:00+05:30
dayjs().format("YYYY-MM-DD"); // 2025-12-15
dayjs().format("MMM DD, YYYY"); // Dec 15, 2025
dayjs().format("dddd, MMMM D, YYYY"); // Monday, December 15, 2025
dayjs().format("h:mm A"); // 10:30 AM

// ═══════════════════════════════════════════
// Manipulate Dates
// ═══════════════════════════════════════════

// Add time
dayjs().add(7, "day");
dayjs().add(1, "month");
dayjs().add(1, "year");

// Subtract time
dayjs().subtract(7, "day");
dayjs().subtract(1, "month");

// Start/End of time periods
dayjs().startOf("month");
dayjs().endOf("month");
dayjs().startOf("year");
dayjs().endOf("week");

// ═══════════════════════════════════════════
// Relative Time
// ═══════════════════════════════════════════

dayjs().fromNow(); // a few seconds ago
dayjs("2025-01-01").fromNow(); // 12 months ago
dayjs("2026-01-01").fromNow(); // in a year
dayjs().to(dayjs("2026-01-01")); // in a year

// ═══════════════════════════════════════════
// Timezone Support
// ═══════════════════════════════════════════

// Set timezone
const tokyo = dayjs.tz("2025-12-15", "Asia/Tokyo");
const newYork = dayjs.tz("2025-12-15", "America/New_York");
const kolkata = dayjs.tz("2025-12-15", "Asia/Kolkata");

// Convert timezone
dayjs().tz("America/Los_Angeles").format();

// ═══════════════════════════════════════════
// Calendar Time
// ═══════════════════════════════════════════

dayjs().calendar(); // Today at 10:30 AM
dayjs().subtract(1, "day").calendar(); // Yesterday at 10:30 AM
dayjs().add(1, "day").calendar(); // Tomorrow at 10:30 AM

// ═══════════════════════════════════════════
// Duration
// ═══════════════════════════════════════════

const duration = dayjs.duration(2, "hours");
duration.humanize(); // 2 hours
duration.asMinutes(); // 120
duration.asSeconds(); // 7200

// ═══════════════════════════════════════════
// Comparison
// ═══════════════════════════════════════════

const date1 = dayjs("2025-12-15");
const date2 = dayjs("2025-12-20");

date1.isBefore(date2); // true
date1.isAfter(date2); // false
date1.isSame(date2); // false
date1.isBetween("2025-12-01", "2025-12-31"); // true

// ═══════════════════════════════════════════
// Utility Functions
// ═══════════════════════════════════════════

// User-friendly date formatter
function formatUserDate(date) {
  const now = dayjs();
  const then = dayjs(date);
  const diffDays = now.diff(then, "day");

  if (diffDays === 0) return "Today";
  if (diffDays === 1) return "Yesterday";
  if (diffDays < 7) return then.format("dddd");
  if (diffDays < 30) return `${diffDays} days ago`;
  return then.format("MMM D, YYYY");
}

// Time ago helper
function timeAgo(date) {
  return dayjs(date).fromNow();
}

// Is date in range
function isInRange(date, start, end) {
  return dayjs(date).isBetween(start, end, null, "[]");
}

// Get age from birthdate
function calculateAge(birthdate) {
  return dayjs().diff(dayjs(birthdate), "year");
}
```

**📦 Day.js Resources:**

- Docs: https://day.js.org/docs/en/installation/installation
- Size: 2kb (gzipped)
- Why: 2x smaller than Moment.js, same API

> **💡 Pro Tip:** Day.js is immutable - all operations return a new instance. Always use plugins for extended functionality to keep bundle size small!

---

### date-fns - Functional Date Utility 📆

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install date-fns
```

```javascript
// ═══════════════════════════════════════════
# Basic Usage (Tree-shakeable!)
// ═══════════════════════════════════════════

import {
    format,
    parse,
    addDays,
    subDays,
    startOfMonth,
    endOfMonth,
    isAfter,
    isBefore,
    differenceInDays,
    formatDistanceToNow,
    isWeekend,
    isToday,
    isYesterday,
    isTomorrow,
} from 'date-fns';

// Format dates
format(new Date(), 'yyyy-MM-dd');                    // 2025-12-15
format(new Date(), 'MMM dd, yyyy');                  // Dec 15, 2025
format(new Date(), 'EEEE, MMMM do, yyyy');          // Monday, December 15th, 2025

// Parse dates
const date = parse('12/15/2025', 'MM/dd/yyyy', new Date());

// Add/subtract
const nextWeek = addDays(new Date(), 7);
const lastWeek = subDays(new Date(), 7);

// Start/end of periods
const monthStart = startOfMonth(new Date());
const monthEnd = endOfMonth(new Date());

// Comparisons
isAfter(new Date('2025-12-20'), new Date('2025-12-15'));  // true
isBefore(new Date('2025-12-10'), new Date('2025-12-15')); // true

// Distance
differenceInDays(new Date('2025-12-25'), new Date('2025-12-15')); // 10
formatDistanceToNow(new Date('2025-12-01'));              // about 14 days ago

// Checks
isWeekend(new Date());
isToday(new Date());
isYesterday(new Date('2025-12-14'));
```

**📦 date-fns Resources:**

- Docs: https://date-fns.org/docs
- Size: Tree-shakeable (only import what you use)
- Why: Pure functions, immutable, TypeScript support

> **💡 Pro Tip:** Use date-fns when you need tree-shaking. Use Day.js when you want a smaller default bundle and Moment.js-like API!

---

<div align="center">

## 🔄 State Management

</div>

### Zustand - Bear-y Simple State 🐻

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install zustand
```

```javascript
// ═══════════════════════════════════════════
// Create Store
// ═══════════════════════════════════════════

import { create } from "zustand";
import { persist, devtools } from "zustand/middleware";

// Simple store
const useStore = create((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
  decrement: () => set((state) => ({ count: state.count - 1 })),
  reset: () => set({ count: 0 }),
}));

// With persistence
const usePersistentStore = create(
  persist(
    (set, get) => ({
      user: null,
      theme: "dark",

      setUser: (user) => set({ user }),
      logout: () => set({ user: null }),
      toggleTheme: () =>
        set((state) => ({
          theme: state.theme === "dark" ? "light" : "dark",
        })),
    }),
    {
      name: "app-storage",
    }
  )
);

// With devtools
const useDevStore = create(
  devtools(
    (set) => ({
      bears: 0,
      increasePopulation: () =>
        set((state) => ({
          bears: state.bears + 1,
        })),
    }),
    {
      name: "Bear Store",
    }
  )
);

// ═══════════════════════════════════════════
// Usage in Components
// ═══════════════════════════════════════════

function Counter() {
  const count = useStore((state) => state.count);
  const increment = useStore((state) => state.increment);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}

// Select multiple values
function Dashboard() {
  const { count, increment, decrement } = useStore();

  return <div>{/* ... */}</div>;
}

// ═══════════════════════════════════════════
// Advanced Patterns
// ═══════════════════════════════════════════

// Async actions
const useAsyncStore = create((set) => ({
  users: [],
  loading: false,
  error: null,

  fetchUsers: async () => {
    set({ loading: true, error: null });
    try {
      const response = await fetch("/api/users");
      const users = await response.json();
      set({ users, loading: false });
    } catch (error) {
      set({ error: error.message, loading: false });
    }
  },
}));

// Computed values
const useComputedStore = create((set, get) => ({
  todos: [],
  addTodo: (todo) =>
    set((state) => ({
      todos: [...state.todos, todo],
    })),

  // Computed
  completedTodos: () => get().todos.filter((t) => t.completed),
  pendingTodos: () => get().todos.filter((t) => !t.completed),
}));
```

**📦 Zustand Resources:**

- Docs: https://zustand-demo.pmnd.rs/
- Size: <1kb
- Why: Simple, no boilerplate, works outside React

> **💡 Pro Tip:** Zustand is perfect for 90% of state management needs. No providers, no boilerplate, just works!

---

### Jotai - Atomic State Management ⚛️

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install jotai
```

```javascript
// ═══════════════════════════════════════════
// Create Atoms
// ═══════════════════════════════════════════

import { atom, useAtom, useAtomValue, useSetAtom } from "jotai";

// Primitive atom
const countAtom = atom(0);
const nameAtom = atom("MrDib");

// Derived atom (computed)
const doubleCountAtom = atom((get) => get(countAtom) * 2);

// Write-only atom
const incrementAtom = atom(null, (get, set) =>
  set(countAtom, get(countAtom) + 1)
);

// Async atom
const userAtom = atom(async () => {
  const response = await fetch("/api/user");
  return response.json();
});

// ═══════════════════════════════════════════
// Usage
// ═══════════════════════════════════════════

function Counter() {
  const [count, setCount] = useAtom(countAtom);
  const doubleCount = useAtomValue(doubleCountAtom);

  return (
    <div>
      <p>Count: {count}</p>
      <p>Double: {doubleCount}</p>
      <button onClick={() => setCount((c) => c + 1)}>Increment</button>
    </div>
  );
}

// Read-only
function Display() {
  const count = useAtomValue(countAtom);
  return <div>Count: {count}</div>;
}

// Write-only
function Incrementer() {
  const increment = useSetAtom(incrementAtom);
  return <button onClick={increment}>+1</button>;
}
```

**📦 Jotai Resources:**

- Docs: https://jotai.org/
- Size: ~3kb
- Why: Atomic approach, minimal re-renders, TypeScript-first

> **💡 Pro Tip:** Use Jotai when you want fine-grained reactivity and don't want global state. Perfect for complex state dependencies!

---

<div align="center">

## 📡 Data Fetching

</div>

### TanStack Query (React Query) - The Data Fetching King 👑

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install @tanstack/react-query
npm install @tanstack/react-query-devtools
```

```javascript
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

// Create client
const queryClient = new QueryClient({
  defaultOptions: {
    queries: {
      staleTime: 5 * 60 * 1000, // 5 minutes
      cacheTime: 10 * 60 * 1000, // 10 minutes
      retry: 3,
      refetchOnWindowFocus: false,
    },
  },
});

// Wrap app
function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <YourApp />
      <ReactQueryDevtools initialIsOpen={false} />
    </QueryClientProvider>
  );
}

// ═══════════════════════════════════════════
// Queries (GET)
// ═══════════════════════════════════════════

function Users() {
  const { data, isLoading, isError, error, refetch } = useQuery({
    queryKey: ["users"],
    queryFn: async () => {
      const response = await fetch("/api/users");
      if (!response.ok) throw new Error("Failed to fetch");
      return response.json();
    },
  });

  if (isLoading) return <div>Loading...</div>;
  if (isError) return <div>Error: {error.message}</div>;

  return (
    <div>
      {data.map((user) => (
        <div key={user.id}>{user.name}</div>
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
    enabled: !!userId, // Only run if userId exists
  });

  return <div>{user?.name}</div>;
}

// ═══════════════════════════════════════════
// Mutations (POST/PUT/DELETE)
// ═══════════════════════════════════════════

function CreateUser() {
  const queryClient = useQueryClient();

  const mutation = useMutation({
    mutationFn: (newUser) => {
      return fetch("/api/users", {
        method: "POST",
        body: JSON.stringify(newUser),
      });
    },
    onSuccess: () => {
      // Invalidate and refetch
      queryClient.invalidateQueries({ queryKey: ["users"] });
    },
    onError: (error) => {
      console.error("Failed:", error);
    },
  });

  const handleSubmit = (userData) => {
    mutation.mutate(userData);
  };

  return (
    <div>
      <button
        onClick={() => handleSubmit({ name: "John" })}
        disabled={mutation.isLoading}
      >
        {mutation.isLoading ? "Creating..." : "Create User"}
      </button>
      {mutation.isError && <div>Error: {mutation.error.message}</div>}
      {mutation.isSuccess && <div>User created!</div>}
    </div>
  );
}

// ═══════════════════════════════════════════
// Optimistic Updates
// ═══════════════════════════════════════════

const updateMutation = useMutation({
  mutationFn: updateUser,
  onMutate: async (newUser) => {
    // Cancel outgoing refetches
    await queryClient.cancelQueries({ queryKey: ["users"] });

    // Snapshot previous value
    const previousUsers = queryClient.getQueryData(["users"]);

    // Optimistically update
    queryClient.setQueryData(["users"], (old) =>
      old.map((user) => (user.id === newUser.id ? newUser : user))
    );

    return { previousUsers };
  },
  onError: (err, newUser, context) => {
    // Rollback on error
    queryClient.setQueryData(["users"], context.previousUsers);
  },
  onSettled: () => {
    // Refetch after error or success
    queryClient.invalidateQueries({ queryKey: ["users"] });
  },
});

// ═══════════════════════════════════════════
// Pagination
// ═══════════════════════════════════════════

function PaginatedUsers() {
  const [page, setPage] = useState(1);

  const { data, isPreviousData } = useQuery({
    queryKey: ["users", page],
    queryFn: () => fetchUsers(page),
    keepPreviousData: true, // Keep showing old data while fetching
  });

  return (
    <div>
      {data?.users.map((user) => (
        <div key={user.id}>{user.name}</div>
      ))}
      <button onClick={() => setPage((p) => p - 1)} disabled={page === 1}>
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

function InfiniteUsers() {
  const { data, fetchNextPage, hasNextPage, isFetchingNextPage } =
    useInfiniteQuery({
      queryKey: ["users"],
      queryFn: ({ pageParam = 1 }) => fetchUsers(pageParam),
      getNextPageParam: (lastPage, pages) => lastPage.nextPage,
    });

  return (
    <div>
      {data?.pages.map((page, i) => (
        <div key={i}>
          {page.users.map((user) => (
            <div key={user.id}>{user.name}</div>
          ))}
        </div>
      ))}
      <button
        onClick={() => fetchNextPage()}
        disabled={!hasNextPage || isFetchingNextPage}
      >
        {isFetchingNextPage
          ? "Loading more..."
          : hasNextPage
          ? "Load More"
          : "Nothing more to load"}
      </button>
    </div>
  );
}
```

**📦 TanStack Query Resources:**

- Docs: https://tanstack.com/query/latest
- Size: ~13kb
- Why: Caching, automatic refetching, optimistic updates

> **💡 Pro Tip:** React Query eliminates the need for global state for server data. Use it with Zustand/Jotai for client state!

### SWR - Stale-While-Revalidate 🔄

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install swr
```

```javascript
// ═══════════════════════════════════════════
// Basic Usage
// ═══════════════════════════════════════════

import useSWR from "swr";

// Fetcher function
const fetcher = (url) => fetch(url).then((res) => res.json());

function Profile() {
  const { data, error, isLoading, mutate } = useSWR("/api/user", fetcher);

  if (isLoading) return <div>Loading...</div>;
  if (error) return <div>Failed to load</div>;

  return (
    <div>
      <h1>{data.name}</h1>
      <button onClick={() => mutate()}>Refresh</button>
    </div>
  );
}

// Global configuration
import { SWRConfig } from "swr";

function App() {
  return (
    <SWRConfig
      value={{
        refreshInterval: 3000,
        fetcher: (url) => fetch(url).then((res) => res.json()),
      }}
    >
      <YourApp />
    </SWRConfig>
  );
}

// Conditional fetching
function User({ id }) {
  const { data } = useSWR(id ? `/api/user/${id}` : null, fetcher);
  return <div>{data?.name}</div>;
}

// Mutation
async function updateUser() {
  await mutate("/api/user", updateUserAPI(), {
    optimisticData: newData,
    rollbackOnError: true,
  });
}
```

**📦 SWR Resources:**

- Docs: https://swr.vercel.app/
- Size: ~5kb
- Why: Lightweight alternative to React Query

> **💡 Pro Tip:** SWR is great for simpler use cases. Use React Query for complex scenarios with more control!

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
```

```javascript
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
    // Submit to API
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input
        {...register("email", {
          required: "Email is required",
          pattern: {
            value: /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$/i,
            message: "Invalid email address",
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
// Advanced Features
// ═══════════════════════════════════════════

function AdvancedForm() {
  const {
    register,
    handleSubmit,
    watch,
    setValue,
    reset,
    formState: { errors, isDirty, isValid },
  } = useForm({
    mode: "onChange", // Validate on change
    defaultValues: {
      username: "",
      email: "",
      age: 0,
    },
  });

  // Watch specific field
  const username = watch("username");

  // Watch all fields
  const watchAllFields = watch();

  // Programmatically set value
  const setRandomEmail = () => {
    setValue("email", "random@example.com");
  };

  // Reset form
  const resetForm = () => {
    reset();
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input {...register("username")} />
      <p>Username: {username}</p>

      <button type="button" onClick={setRandomEmail}>
        Set Random Email
      </button>
      <button type="button" onClick={resetForm}>
        Reset
      </button>

      <button type="submit" disabled={!isDirty || !isValid}>
        Submit
      </button>
    </form>
  );
}

// ═══════════════════════════════════════════
// With Yup/Zod Validation
// ═══════════════════════════════════════════

import { yupResolver } from "@hookform/resolvers/yup";
import * as yup from "yup";

const schema = yup
  .object({
    email: yup.string().email().required(),
    password: yup.string().min(8).required(),
    age: yup.number().positive().integer().required(),
  })
  .required();

function ValidatedForm() {
  const {
    register,
    handleSubmit,
    formState: { errors },
  } = useForm({
    resolver: yupResolver(schema),
  });

  return <form>{/* ... */}</form>;
}

// With Zod
import { zodResolver } from "@hookform/resolvers/zod";
import * as z from "zod";

const zodSchema = z.object({
  email: z.string().email(),
  password: z.string().min(8),
  age: z.number().positive(),
});

function ZodForm() {
  const { register, handleSubmit } = useForm({
    resolver: zodResolver(zodSchema),
  });

  return <form>{/* ... */}</form>;
}

// ═══════════════════════════════════════════
// Field Arrays (Dynamic Fields)
// ═══════════════════════════════════════════

import { useFieldArray } from "react-hook-form";

function DynamicForm() {
  const { control, register } = useForm();
  const { fields, append, remove } = useFieldArray({
    control,
    name: "users",
  });

  return (
    <div>
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
    </div>
  );
}
```

**📦 React Hook Form Resources:**

- Docs: https://react-hook-form.com/
- Size: ~9kb
- Why: Best performance, less re-renders, great DX

> **💡 Pro Tip:** React Hook Form uses uncontrolled components for better performance. Perfect for large forms!

---

### Formik - Battle-Tested Form Library 📋

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install formik
```

```javascript
// ═══════════════════════════════════════════
// Basic Usage
// ═══════════════════════════════════════════

import { Formik, Form, Field, ErrorMessage } from "formik";
import * as Yup from "yup";

const validationSchema = Yup.object({
  email: Yup.string().email("Invalid email").required("Required"),
  password: Yup.string().min(8, "Too short").required("Required"),
});

function SignupForm() {
  return (
    <Formik
      initialValues={{ email: "", password: "" }}
      validationSchema={validationSchema}
      onSubmit={(values, { setSubmitting }) => {
        setTimeout(() => {
          alert(JSON.stringify(values, null, 2));
          setSubmitting(false);
        }, 400);
      }}
    >
      {({ isSubmitting }) => (
        <Form>
          <Field type="email" name="email" />
          <ErrorMessage name="email" component="div" />

          <Field type="password" name="password" />
          <ErrorMessage name="password" component="div" />

          <button type="submit" disabled={isSubmitting}>
            Submit
          </button>
        </Form>
      )}
    </Formik>
  );
}
```

**📦 Formik Resources:**

- Docs: https://formik.org/docs/overview
- Size: ~13kb
- Why: Mature, well-documented, integrates with Yup

> **💡 Pro Tip:** Formik is great for complex forms with nested objects. Use React Hook Form for better performance!

---

<div align="center">

## ✅ Validation

</div>

### Zod - TypeScript-First Schema Validation 🛡️

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install zod
```

```javascript
// ═══════════════════════════════════════════
// Basic Schema
// ═══════════════════════════════════════════

import { z } from "zod";

// Define schema
const userSchema = z.object({
  email: z.string().email(),
  password: z.string().min(8),
  age: z.number().positive().int(),
  website: z.string().url().optional(),
  acceptTerms: z.boolean(),
});

// Validate data
const result = userSchema.safeParse({
  email: "user@example.com",
  password: "password123",
  age: 25,
  acceptTerms: true,
});

if (result.success) {
  console.log(result.data); // Typed data!
} else {
  console.log(result.error.errors); // Validation errors
}

// ═══════════════════════════════════════════
// Advanced Validation
// ═══════════════════════════════════════════

// String validation
const stringSchema = z
  .string()
  .min(3, "Too short")
  .max(100, "Too long")
  .email("Invalid email")
  .url("Invalid URL")
  .regex(/^[a-z]+$/, "Lowercase only")
  .trim()
  .toLowerCase();

// Number validation
const numberSchema = z
  .number()
  .positive("Must be positive")
  .int("Must be integer")
  .min(0)
  .max(100)
  .multipleOf(5);

// Array validation
const arraySchema = z
  .array(z.string())
  .min(1, "At least one item")
  .max(10, "Max 10 items")
  .nonempty();

// Object validation
const addressSchema = z.object({
  street: z.string(),
  city: z.string(),
  zipCode: z.string().regex(/^\d{5}$/),
});

// Nested objects
const userWithAddressSchema = z.object({
  name: z.string(),
  address: addressSchema,
});

// ═══════════════════════════════════════════
// Advanced Features
// ═══════════════════════════════════════════

// Union types
const stringOrNumber = z.union([z.string(), z.number()]);

// Enums
const roleSchema = z.enum(["admin", "user", "guest"]);

// Nullable/Optional
const nullableString = z.string().nullable();
const optionalString = z.string().optional();

// Default values
const withDefaults = z.object({
  name: z.string().default("Anonymous"),
  role: z.enum(["user", "admin"]).default("user"),
});

// Transformations
const transformSchema = z
  .string()
  .transform((val) => val.toLowerCase())
  .transform((val) => val.trim());

// Refinements (custom validation)
const passwordSchema = z
  .string()
  .min(8)
  .refine((val) => /[A-Z]/.test(val), {
    message: "Must contain uppercase letter",
  })
  .refine((val) => /[0-9]/.test(val), {
    message: "Must contain number",
  });

// ═══════════════════════════════════════════
// With React Hook Form
// ═══════════════════════════════════════════

import { zodResolver } from "@hookform/resolvers/zod";
import { useForm } from "react-hook-form";

const formSchema = z.object({
  email: z.string().email(),
  password: z.string().min(8),
});

function ZodForm() {
  const {
    register,
    handleSubmit,
    formState: { errors },
  } = useForm({
    resolver: zodResolver(formSchema),
  });

  return <form onSubmit={handleSubmit(onSubmit)}>{/* ... */}</form>;
}

// ═══════════════════════════════════════════
// Extract TypeScript Types
// ═══════════════════════════════════════════

type User = z.infer<typeof userSchema>;
// type User = { email: string; password: string; age: number; ... }
```

**📦 Zod Resources:**

- Docs: https://zod.dev/
- Size: ~8kb
- Why: TypeScript-first, automatic type inference

> **💡 Pro Tip:** Zod is the modern choice for validation. Use it everywhere - forms, APIs, environment variables!

---

### Yup - Schema Validation Classic 📏

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install yup
```

```javascript
// ═══════════════════════════════════════════
// Basic Schema
// ═══════════════════════════════════════════

import * as yup from "yup";

const schema = yup.object({
  email: yup.string().email().required(),
  password: yup.string().min(8).required(),
  age: yup.number().positive().integer().required(),
  website: yup.string().url().nullable(),
  createdOn: yup.date().default(() => new Date()),
});

// Validate
schema
  .validate({ email: "test@example.com", password: "pass1234", age: 25 })
  .then((valid) => console.log(valid))
  .catch((err) => console.log(err.errors));

// Validate sync
try {
  schema.validateSync(data);
} catch (err) {
  console.log(err.errors);
}
```

**📦 Yup Resources:**

- Docs: https://github.com/jquense/yup
- Size: ~10kb
- Why: Mature, widely used, integrates with Formik

> **💡 Pro Tip:** Yup is battle-tested but Zod has better TypeScript support. Choose based on your needs!

---

<div align="center">

## 🔔 Notifications

</div>

### React Hot Toast - Lightweight Toast Notifications 🍞

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install react-hot-toast
```

```javascript
// ═══════════════════════════════════════════
// Setup
// ═══════════════════════════════════════════

import toast, { Toaster } from "react-hot-toast";

function App() {
  return (
    <div>
      <Toaster
        position="top-right"
        reverseOrder={false}
        gutter={8}
        toastOptions={{
          duration: 4000,
          style: {
            background: "#363636",
            color: "#fff",
          },
          success: {
            duration: 3000,
            iconTheme: {
              primary: "green",
              secondary: "white",
            },
          },
        }}
      />
      <YourApp />
    </div>
  );
}

// ═══════════════════════════════════════════
// Basic Usage
// ═══════════════════════════════════════════

function Notifications() {
  // Basic toast
  const notify = () => toast("Hello World");

  // Success
  const success = () => toast.success("Successfully saved!");

  // Error
  const error = () => toast.error("Something went wrong!");

  // Loading
  const loading = () => toast.loading("Saving...");

  // Promise-based
  const saveData = async () => {
    const promise = fetch("/api/save");

    toast.promise(promise, {
      loading: "Saving...",
      success: "Saved successfully!",
      error: "Failed to save",
    });
  };

  // Custom toast
  const custom = () => {
    toast.custom((t) => (
      <div className={`custom-toast ${t.visible ? "show" : "hide"}`}>
        <span>Custom content!</span>
        <button onClick={() => toast.dismiss(t.id)}>Dismiss</button>
      </div>
    ));
  };

  // Dismiss specific toast
  const dismissible = () => {
    const toastId = toast("Dismissible", {
      duration: Infinity,
    });

    setTimeout(() => toast.dismiss(toastId), 3000);
  };

  return (
    <div>
      <button onClick={notify}>Basic</button>
      <button onClick={success}>Success</button>
      <button onClick={error}>Error</button>
      <button onClick={loading}>Loading</button>
      <button onClick={saveData}>Promise</button>
    </div>
  );
}
```

**📦 React Hot Toast Resources:**

- Docs: https://react-hot-toast.com/
- Size: ~5kb
- Why: Lightweight, beautiful defaults, great DX

> **💡 Pro Tip:** React Hot Toast is the modern choice - smaller and more flexible than React Toastify!

---

### Sonner - Beautiful Toast Component 🎵

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install sonner
```

```javascript
// ═══════════════════════════════════════════
// Setup
// ═══════════════════════════════════════════

import { Toaster, toast } from "sonner";

function App() {
  return (
    <div>
      <Toaster richColors position="top-right" />
      <YourApp />
    </div>
  );
}

// ═══════════════════════════════════════════
// Usage
// ═══════════════════════════════════════════

function Notifications() {
  // Basic
  toast("Event has been created");

  // With description
  toast("Event has been created", {
    description: "Monday, January 3rd at 6:00pm",
  });

  // Success/Error/Warning/Info
  toast.success("Data saved successfully");
  toast.error("Something went wrong");
  toast.warning("Be careful!");
  toast.info("New update available");

  // Promise
  toast.promise(fetch("/api/data"), {
    loading: "Loading...",
    success: "Data loaded",
    error: "Error loading data",
  });

  // Custom action
  toast("Event created", {
    action: {
      label: "Undo",
      onClick: () => console.log("Undo"),
    },
  });

  return <button onClick={() => toast("Hello")}>Show Toast</button>;
}
```

**📦 Sonner Resources:**

- Docs: https://sonner.emilkowal.ski/
- Size: ~3kb
- Why: Beautiful, accessible, performant

> **💡 Pro Tip:** Sonner is the newest and most beautiful option. Great for modern apps!

---

<div align="center">

## 🆔 ID Generation

</div>

### nanoid - Tiny Unique ID Generator 🔑

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install nanoid
```

```javascript
// ═══════════════════════════════════════════
// Basic Usage
// ═══════════════════════════════════════════

import { nanoid } from "nanoid";

// Generate ID
const id = nanoid(); // "V1StGXR8_Z5jdHi6B-myT"

// Custom length
const shortId = nanoid(10); // "IRFa-VaY2b"
const longId = nanoid(32); // Very secure!

// ═══════════════════════════════════════════
// Custom Alphabet
// ═══════════════════════════════════════════

import { customAlphabet } from "nanoid";

// Numbers only
const numbersOnly = customAlphabet("1234567890", 10);
numbersOnly(); // "4872394729"

// Lowercase only
const lowercase = customAlphabet("abcdefghijklmnopqrstuvwxyz", 8);
lowercase(); // "kjhgfdsa"

// URL-safe
const urlSafe = customAlphabet(
  "0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz-_",
  21
);

// ═══════════════════════════════════════════
// Practical Uses
// ═══════════════════════════════════════════

// Database IDs
const userId = nanoid();
const orderId = nanoid();

// File names
const fileName = `upload_${nanoid()}.jpg`;

// Session IDs
const sessionId = nanoid(32); // Extra secure

// Short codes
const referralCode = customAlphabet(
  "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789",
  8
)();
// "A3B7K2M9"
```

**📦 nanoid Resources:**

- Docs: https://github.com/ai/nanoid
- Size: 130 bytes!
- Why: Tiny, fast, URL-safe, secure

> **💡 Pro Tip:** Use nanoid for most IDs. Use UUID when you need RFC 4122 compliance!

---

### UUID - Standard Unique Identifiers 🌐

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install uuid
```

```javascript
// ═══════════════════════════════════════════
# Basic Usage
// ═══════════════════════════════════════════

import { v4 as uuidv4, v5 as uuidv5, validate, version } from 'uuid';

// Random UUID (v4)
const id = uuidv4();  // "9b1deb4d-3b7d-4bad-9bdd-2b0d7b3dcb6d"

// Namespace UUID (v5) - deterministic
const MY_NAMESPACE = '1b671a64-40d5-491e-99b0-da01ff1f3341';
const id5 = uuidv5('Hello, World!', MY_NAMESPACE);
// Always generates same ID for same input

// Validate
validate(id);  // true
validate('not-a-uuid');  // false

// Get version
version(id);  // 4
```

**📦 UUID Resources:**

- Docs: https://github.com/uuidjs/uuid
- Size: ~3kb
- Why: Standard, widely supported

> **💡 Pro Tip:** Use UUIDs when you need universal compatibility. Use nanoid for everything else!

---

<div align="center">

## 📁 File Handling

</div>

### React Dropzone - File Upload Made Easy 📤

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install react-dropzone
```

```javascript
// ═══════════════════════════════════════════
// Basic Usage
// ═══════════════════════════════════════════

import { useDropzone } from "react-dropzone";

function FileUpload() {
  const onDrop = useCallback((acceptedFiles) => {
    acceptedFiles.forEach((file) => {
      const reader = new FileReader();

      reader.onload = () => {
        console.log(reader.result);
      };

      reader.readAsDataURL(file);
    });
  }, []);

  const {
    getRootProps,
    getInputProps,
    isDragActive,
    isDragReject,
    acceptedFiles,
  } = useDropzone({
    onDrop,
    accept: {
      "image/*": [".png", ".jpg", ".jpeg", ".gif"],
    },
    maxFiles: 5,
    maxSize: 5242880, // 5MB
  });

  return (
    <div
      {...getRootProps()}
      style={{
        border: "2px dashed #ccc",
        padding: "20px",
        cursor: "pointer",
      }}
    >
      <input {...getInputProps()} />
      {isDragActive ? (
        <p>Drop the files here...</p>
      ) : isDragReject ? (
        <p>File type not accepted!</p>
      ) : (
        <p>Drag & drop files here, or click to select</p>
      )}

      {acceptedFiles.length > 0 && (
        <ul>
          {acceptedFiles.map((file) => (
            <li key={file.name}>
              {file.name} - {file.size} bytes
            </li>
          ))}
        </ul>
      )}
    </div>
  );
}

// ═══════════════════════════════════════════
// With Preview
// ═══════════════════════════════════════════

function ImageUploadWithPreview() {
  const [files, setFiles] = useState([]);

  const { getRootProps, getInputProps } = useDropzone({
    accept: { "image/*": [] },
    onDrop: (acceptedFiles) => {
      setFiles(
        acceptedFiles.map((file) =>
          Object.assign(file, {
            preview: URL.createObjectURL(file),
          })
        )
      );
    },
  });

  // Clean up previews
  useEffect(() => {
    return () => files.forEach((file) => URL.revokeObjectURL(file.preview));
  }, [files]);

  return (
    <div>
      <div {...getRootProps()}>
        <input {...getInputProps()} />
        <p>Drop images here</p>
      </div>

      <div style={{ display: "flex", gap: "10px", marginTop: "20px" }}>
        {files.map((file) => (
          <div key={file.name}>
            <img
              src={file.preview}
              alt={file.name}
              style={{ width: "100px", height: "100px", objectFit: "cover" }}
            />
            <p>{file.name}</p>
          </div>
        ))}
      </div>
    </div>
  );
}
```

**📦 React Dropzone Resources:**

- Docs: https://react-dropzone.js.org/
- Size: ~8kb
- Why: Accessible, customizable, file validation

> **💡 Pro Tip:** Always clean up object URLs created with `URL.createObjectURL()` to prevent memory leaks!

---

<div align="center">

## 📋 Clipboard & Copy

</div>

### use-clipboard-copy - Simple Copy Hook 📄

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install use-clipboard-copy
```

```javascript
// ═══════════════════════════════════════════
// Basic Usage
// ═══════════════════════════════════════════

import useClipboard from "use-clipboard-copy";

function CopyButton() {
  const clipboard = useClipboard();

  return (
    <div>
      <input ref={clipboard.target} value="https://example.com" readOnly />
      <button onClick={clipboard.copy}>
        {clipboard.copied ? "Copied!" : "Copy"}
      </button>
    </div>
  );
}

// Copy custom text
function CustomCopy() {
  const clipboard = useClipboard();

  const copyCode = () => {
    const code = `console.log('Hello, World!');`;
    clipboard.copy(code);
  };

  return (
    <button onClick={copyCode}>
      {clipboard.copied ? "✓ Copied" : "Copy Code"}
    </button>
  );
}
```

**📦 use-clipboard-copy Resources:**

- Docs: https://github.com/wsmd/use-clipboard-copy
- Size: ~1kb
- Why: Simple, works great

> **💡 Pro Tip:** Show visual feedback when copying - users need to know the action succeeded!

---

### Modern Clipboard API (Native) 🆕

```javascript
// ═══════════════════════════════════════════
// Copy to Clipboard (Native)
// ═══════════════════════════════════════════

async function copyToClipboard(text) {
  try {
    await navigator.clipboard.writeText(text);
    console.log("Copied to clipboard!");
    return true;
  } catch (err) {
    console.error("Failed to copy:", err);
    return false;
  }
}

// Read from Clipboard
async function readFromClipboard() {
  try {
    const text = await navigator.clipboard.readText();
    console.log("Clipboard contents:", text);
    return text;
  } catch (err) {
    console.error("Failed to read:", err);
    return null;
  }
}

// React Hook
function useClipboard() {
  const [copied, setCopied] = useState(false);

  const copy = async (text) => {
    try {
      await navigator.clipboard.writeText(text);
      setCopied(true);
      setTimeout(() => setCopied(false), 2000);
      return true;
    } catch (err) {
      console.error("Copy failed:", err);
      return false;
    }
  };

  return { copied, copy };
}

// Usage
function CopyButton({ text }) {
  const { copied, copy } = useClipboard();

  return (
    <button onClick={() => copy(text)}>{copied ? "✓ Copied!" : "Copy"}</button>
  );
}
```

> **💡 Pro Tip:** The native Clipboard API is modern and supported in all evergreen browsers. Use it without dependencies when possible!

---

<div align="center">

## 🎨 Styling Utilities

</div>

### clsx / classnames - Conditional Classes 🎭

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install clsx
# or
npm install classnames
```

```javascript
// ═══════════════════════════════════════════
// clsx Usage (Smaller, Faster)
// ═══════════════════════════════════════════

import clsx from "clsx";

// Basic
clsx("foo", "bar"); // 'foo bar'
clsx("foo", true && "bar", false && "baz"); // 'foo bar'

// Objects
clsx({ foo: true, bar: false, baz: true }); // 'foo baz'

// Arrays
clsx(["foo", "bar"]); // 'foo bar'

// Mixed
clsx("foo", { bar: true }, ["baz", { qux: false }]); // 'foo bar baz'

// React component
function Button({ primary, large, disabled, className }) {
  return (
    <button
      className={clsx(
        "btn",
        primary && "btn-primary",
        large && "btn-large",
        disabled && "btn-disabled",
        className
      )}
    >
      Click me
    </button>
  );
}

// With Tailwind
function Card({ featured, className }) {
  return (
    <div
      className={clsx(
        "rounded-lg p-4 shadow-md",
        featured ? "border-2 border-blue-500" : "border border-gray-200",
        className
      )}
    >
      Content
    </div>
  );
}
```

**📦 clsx Resources:**

- Docs: https://github.com/lukeed/clsx
- Size: 228 bytes!
- Why: Tiny, fast, clean API

> **💡 Pro Tip:** clsx is 2x faster and smaller than classnames. Use it for all conditional class logic!

---

### tailwind-merge - Merge Tailwind Classes 🎨

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install tailwind-merge
```

```javascript
// ═══════════════════════════════════════════
// Problem it Solves
// ═══════════════════════════════════════════

// Without tailwind-merge
<div className="px-2 py-1 px-4"> {/* px-2 AND px-4 both applied! */}

// With tailwind-merge
import { twMerge } from 'tailwind-merge';

twMerge('px-2 py-1', 'px-4');  // 'py-1 px-4' (px-2 removed!)

// ═══════════════════════════════════════════
// Usage with Components
// ═══════════════════════════════════════════

function Button({ className, ...props }) {
    return (
        <button
            className={twMerge(
                'px-4 py-2 bg-blue-500 text-white rounded',
                className
            )}
            {...props}
        />
    );
}

// Usage - className props override defaults
<Button className="bg-red-500 px-6">
    {/* Results in: py-2 text-white rounded bg-red-500 px-6 */}
</Button>

// ═══════════════════════════════════════════
// With clsx (Best of Both!)
// ═══════════════════════════════════════════

import { clsx } from 'clsx';
import { twMerge } from 'tailwind-merge';

function cn(...inputs) {
    return twMerge(clsx(inputs));
}

// Usage
function Card({ featured, className }) {
    return (
        <div
            className={cn(
                'rounded-lg p-4',
                featured && 'border-2 border-blue-500',
                className
            )}
        >
            Content
        </div>
    );
}
```

**📦 tailwind-merge Resources:**

- Docs: https://github.com/dcastil/tailwind-merge
- Size: ~2kb
- Why: Properly merges conflicting Tailwind classes

> **💡 Pro Tip:** Always use tailwind-merge with component libraries to prevent class conflicts!

---

<div align="center">

## 🔍 Search & Filter

</div>

### Fuse.js - Fuzzy Search 🔎

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install fuse.js
```

```javascript
// ═══════════════════════════════════════════
// Basic Usage
// ═══════════════════════════════════════════

import Fuse from "fuse.js";

const data = [
  { title: "JavaScript: The Good Parts", author: "Douglas Crockford" },
  { title: "JavaScript: The Definitive Guide", author: "David Flanagan" },
  { title: "Python Crash Course", author: "Eric Matthes" },
];

const fuse = new Fuse(data, {
  keys: ["title", "author"],
  threshold: 0.3, // 0.0 = perfect match, 1.0 = match anything
});

// Search
const results = fuse.search("java");
console.log(results);
// [
//   { item: { title: 'JavaScript: The Good Parts', ... }, refIndex: 0 },
//   { item: { title: 'JavaScript: The Definitive Guide', ... }, refIndex: 1 }
// ]

// ═══════════════════════════════════════════
// Advanced Configuration
// ═══════════════════════════════════════════

const advancedFuse = new Fuse(data, {
  keys: [
    { name: "title", weight: 0.7 }, // Title more important
    { name: "author", weight: 0.3 },
  ],
  threshold: 0.4,
  distance: 100,
  minMatchCharLength: 2,
  includeScore: true,
  useExtendedSearch: true,
});

// Extended search
advancedFuse.search("'python"); // Exact match
advancedFuse.search("^Java"); // Starts with
advancedFuse.search("!crash"); // Exclude

// ═══════════════════════════════════════════
// React Hook
// ═══════════════════════════════════════════

function useFuseSearch(data, options) {
  const [query, setQuery] = useState("");

  const fuse = useMemo(() => new Fuse(data, options), [data, options]);

  const results = useMemo(
    () =>
      query
        ? fuse.search(query)
        : data.map((item, refIndex) => ({ item, refIndex })),
    [fuse, query]
  );

  return { results, setQuery, query };
}

// Usage
function SearchableList() {
  const { results, setQuery, query } = useFuseSearch(books, {
    keys: ["title", "author"],
    threshold: 0.3,
  });

  return (
    <div>
      <input
        type="text"
        value={query}
        onChange={(e) => setQuery(e.target.value)}
        placeholder="Search books..."
      />
      {results.map(({ item }) => (
        <div key={item.id}>
          <h3>{item.title}</h3>
          <p>{item.author}</p>
        </div>
      ))}
    </div>
  );
}
```

**📦 Fuse.js Resources:**

- Docs: https://fusejs.io/
- Size: ~12kb
- Why: Powerful fuzzy search, works client-side

> **💡 Pro Tip:** Fuse.js is perfect for client-side search. For large datasets, use server-side search instead!

---

### match-sorter - Simple List Filtering 📋

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install match-sorter
```

```javascript
// ═══════════════════════════════════════════
// Basic Usage
// ═══════════════════════════════════════════

import { matchSorter } from "match-sorter";

const users = [
  { name: "John Doe", email: "john@example.com" },
  { name: "Jane Smith", email: "jane@example.com" },
  { name: "Bob Johnson", email: "bob@example.com" },
];

// Simple filter
matchSorter(users, "john", { keys: ["name"] });
// Returns: [{ name: 'John Doe', ... }, { name: 'Bob Johnson', ... }]

// Multiple keys
matchSorter(users, "john", { keys: ["name", "email"] });

// With ranking
matchSorter(users, "doe", {
  keys: [{ key: "name", threshold: matchSorter.rankings.CONTAINS }, "email"],
});

// React hook
function useFilter(data, keys) {
  const [filter, setFilter] = useState("");

  const filtered = useMemo(
    () => matchSorter(data, filter, { keys }),
    [data, filter, keys]
  );

  return { filtered, filter, setFilter };
}
```

**📦 match-sorter Resources:**

- Docs: https://github.com/kentcdodds/match-sorter
- Size: ~3kb
- Why: Simple, fast, good for basic filtering

> **💡 Pro Tip:** match-sorter is great for simple filtering. Use Fuse.js when you need fuzzy search!

---

<div align="center">

## ⚡ Performance

</div>

### Lodash - Utility Functions 🔧

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install lodash
# Better: Import only what you need
npm install lodash-es
```

```javascript
// ═══════════════════════════════════════════
// Import Only What You Need (Tree-shakeable)
// ═══════════════════════════════════════════

import debounce from "lodash/debounce";
import throttle from "lodash/throttle";
import cloneDeep from "lodash/cloneDeep";
import isEqual from "lodash/isEqual";
import merge from "lodash/merge";
import uniq from "lodash/uniq";

// ═══════════════════════════════════════════
// Debounce - Delay execution
// ═══════════════════════════════════════════

function SearchInput() {
  const [query, setQuery] = useState("");

  // Debounce API call
  const debouncedSearch = useMemo(
    () =>
      debounce((value) => {
        console.log("Searching for:", value);
        // API call here
      }, 500),
    []
  );

  const handleChange = (e) => {
    const value = e.target.value;
    setQuery(value);
    debouncedSearch(value);
  };

  // Cleanup
  useEffect(() => {
    return () => {
      debouncedSearch.cancel();
    };
  }, [debouncedSearch]);

  return <input value={query} onChange={handleChange} />;
}

// ═══════════════════════════════════════════
// Throttle - Limit execution rate
// ═══════════════════════════════════════════

function ScrollComponent() {
  const handleScroll = useMemo(
    () =>
      throttle(() => {
        console.log("Scrolled!");
        // Expensive operation
      }, 200),
    []
  );

  useEffect(() => {
    window.addEventListener("scroll", handleScroll);
    return () => {
      window.removeEventListener("scroll", handleScroll);
      handleScroll.cancel();
    };
  }, [handleScroll]);

  return <div>Scroll me</div>;
}

// ═══════════════════════════════════════════
// Deep Clone
// ═══════════════════════════════════════════

const original = { a: 1, b: { c: 2 } };
const copy = cloneDeep(original);

copy.b.c = 3;
console.log(original.b.c); // 2 (unchanged!)

// ═══════════════════════════════════════════
// Deep Equality
// ═══════════════════════════════════════════

const obj1 = { a: 1, b: { c: 2 } };
const obj2 = { a: 1, b: { c: 2 } };

obj1 === obj2; // false (different references)
isEqual(obj1, obj2); // true (same structure and values)

// Use in React
function MyComponent({ user }) {
  const prevUser = usePrevious(user);

  useEffect(() => {
    if (!isEqual(user, prevUser)) {
      console.log("User changed!");
    }
  }, [user, prevUser]);
}

// ═══════════════════════════════════════════
// Useful Utilities
// ═══════════════════════════════════════════

// Remove duplicates
uniq([1, 2, 2, 3, 4, 4]); // [1, 2, 3, 4]

// Deep merge objects
const defaults = { a: 1, b: { c: 2 } };
const custom = { b: { d: 3 } };
merge({}, defaults, custom); // { a: 1, b: { c: 2, d: 3 } }

// Chunk array
chunk([1, 2, 3, 4, 5], 2); // [[1, 2], [3, 4], [5]]

// Group by
const users = [
  { name: "John", age: 25 },
  { name: "Jane", age: 25 },
];
groupBy(users, "age"); // { 25: [{ name: 'John', ... }, { name: 'Jane', ... }] }
```

**📦 Lodash Resources:**

- Docs: https://lodash.com/docs/
- Size: ~24kb (full), tree-shakeable
- Why: Battle-tested utilities

> **💡 Pro Tip:** Always import individual functions, never the entire library! Use lodash-es for better tree-shaking!

---

### use-debounce - React Debounce Hook 🎯

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install use-debounce
```

```javascript
// ═══════════════════════════════════════════
// Debounce Value
// ═══════════════════════════════════════════

import { useDebounce } from "use-debounce";

function SearchComponent() {
  const [text, setText] = useState("");
  const [debouncedText] = useDebounce(text, 500);

  useEffect(() => {
    // This runs only after user stops typing for 500ms
    if (debouncedText) {
      searchAPI(debouncedText);
    }
  }, [debouncedText]);

  return (
    <input
      value={text}
      onChange={(e) => setText(e.target.value)}
      placeholder="Search..."
    />
  );
}

// ═══════════════════════════════════════════
// Debounce Callback
// ═══════════════════════════════════════════

import { useDebouncedCallback } from "use-debounce";

function FormComponent() {
  const saveForm = useDebouncedCallback((values) => {
    console.log("Saving:", values);
    // API call
  }, 1000);

  return <input onChange={(e) => saveForm({ field: e.target.value })} />;
}

// With options
const debouncedSave = useDebouncedCallback(saveForm, 1000, {
  leading: true,
  trailing: true,
  maxWait: 2000,
});
```

**📦 use-debounce Resources:**

- Docs: https://github.com/xnimorz/use-debounce
- Size: ~1kb
- Why: Simple, React-specific, performant

> **💡 Pro Tip:** Debounce search inputs, auto-save forms, and window resize handlers for better performance!

---

### React Virtualized / React Window - List Virtualization 📜

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install react-window
```

```javascript
// ═══════════════════════════════════════════
// Fixed Size List
// ═══════════════════════════════════════════

import { FixedSizeList } from "react-window";

function VirtualizedList({ items }) {
  const Row = ({ index, style }) => (
    <div style={style}>
      Item {index}: {items[index]}
    </div>
  );

  return (
    <FixedSizeList
      height={400}
      itemCount={items.length}
      itemSize={35}
      width="100%"
    >
      {Row}
    </FixedSizeList>
  );
}

// ═══════════════════════════════════════════
// Variable Size List
// ═══════════════════════════════════════════

import { VariableSizeList } from "react-window";

function VariableList({ items }) {
  const getItemSize = (index) => {
    // Return different heights based on content
    return items[index].length > 50 ? 80 : 40;
  };

  const Row = ({ index, style }) => <div style={style}>{items[index]}</div>;

  return (
    <VariableSizeList
      height={400}
      itemCount={items.length}
      itemSize={getItemSize}
      width="100%"
    >
      {Row}
    </VariableSizeList>
  );
}
```

**📦 React Window Resources:**

- Docs: https://react-window.vercel.app/
- Size: ~6kb
- Why: Render only visible items, huge performance boost

> **💡 Pro Tip:** Use virtualization for lists with 100+ items. It dramatically improves performance!

---

<div align="center">

## 💡 Tips & Best Practices

</div>

### Bundle Size Optimization 📦

```bash
# ═══════════════════════════════════════════
# Analyze Bundle Size
# ═══════════════════════════════════════════

# Webpack Bundle Analyzer
npm install --save-dev webpack-bundle-analyzer

# Vite
npm install --save-dev rollup-plugin-visualizer

# ═══════════════════════════════════════════
# Import Strategies
# ═══════════════════════════════════════════

# ❌ BAD: Import entire library
import _ from 'lodash';
import * as R from 'ramda';

# ✅ GOOD: Import specific functions
import debounce from 'lodash/debounce';
import map from 'lodash/map';

# ✅ BETTER: Use tree-shakeable version
import { debounce, map } from 'lodash-es';
```

---

### Performance Checklist ⚡

```
Performance Optimization:
  ✅ Use code splitting (React.lazy, dynamic imports)
  ✅ Debounce expensive operations
  ✅ Virtualize long lists (react-window)
  ✅ Memoize expensive calculations (useMemo)
  ✅ Use production builds
  ✅ Lazy load images
  ✅ Tree-shake unused code
  ✅ Monitor bundle size
  ✅ Use CDN for static assets
  ✅ Implement proper caching strategies

State Management:
  ✅ Use React Query for server state
  ✅ Use Zustand/Jotai for client state
  ✅ Don't put server data in global state
  ✅ Minimize re-renders
  ✅ Use proper data normalization

Developer Experience:
  ✅ Use TypeScript
  ✅ Use ESLint + Prettier
  ✅ Use proper error boundaries
  ✅ Implement proper logging
  ✅ Use proper dev tools
  ✅ Document complex utilities
```

---

### Library Selection Guide 🎯

```
Choose Libraries Based On:

1. Bundle Size
   - Check bundlephobia.com
   - Prefer smaller alternatives
   - Look for tree-shakeable options

2. Maintenance
   - Active development (recent commits)
   - Good issue response time
   - Regular releases
   - Large community

3. Documentation
   - Clear examples
   - TypeScript support
   - Migration guides
   - Good error messages

4. Performance
   - Benchmark if critical
   - Check real-world usage
   - Monitor runtime cost
   - Consider alternatives

5. Dependencies
   - Fewer dependencies = better
   - Check dependency tree
   - Avoid dependency conflicts
   - Security considerations
```

---

### Quick Reference Table 📊

| Category           | Library         | Size           | Best For              |
| ------------------ | --------------- | -------------- | --------------------- |
| **Date/Time**      | Day.js          | 2kb            | Modern date handling  |
| **State**          | Zustand         | <1kb           | Simple global state   |
| **Data Fetching**  | TanStack Query  | 13kb           | Server state          |
| **Forms**          | React Hook Form | 9kb            | Performant forms      |
| **Validation**     | Zod             | 8kb            | TypeScript validation |
| **Notifications**  | React Hot Toast | 5kb            | Toast messages        |
| **IDs**            | nanoid          | 130b           | Unique IDs            |
| **Files**          | React Dropzone  | 8kb            | File uploads          |
| **Classes**        | clsx            | 228b           | Conditional classes   |
| **Search**         | Fuse.js         | 12kb           | Fuzzy search          |
| **Utils**          | Lodash-es       | Tree-shakeable | Utilities             |
| **Virtualization** | React Window    | 6kb            | Long lists            |

---

<div align="center">

## 🎓 Essential Utility Combinations

### _MrDib's Recommended Stack_ 🌟

</div>

**For Most Projects:**

```bash
npm install dayjs zustand @tanstack/react-query
npm install react-hook-form zod
npm install react-hot-toast nanoid clsx
```

**For Complex Apps:**

```bash
# Above plus:
npm install lodash-es fuse.js react-window
npm install tailwind-merge use-debounce
```

**Minimal Setup:**

```bash
npm install dayjs zustand react-hook-form
npm install clsx nanoid
```

---

<div align="center">

**Built with 🔧 by MrDib, for Frontend Developers**

_"The right utility at the right time makes all the difference!"_

**Happy Coding!** ⚡

**If you found this helpful, give it a ⭐ star and share with fellow developers!**

</div>

---

### Contributing 🤝

Found a great utility? Want to add examples? Contributions are welcome!

1. Fork the repository
2. Add your utility examples
3. Update the comparison table
4. Submit a pull request

---

### License 📄

This guide is open source and available under the MIT License.

---

<div align="center">

**Stay efficient. Keep coding. Use the right tools!** 🚀

🔧 **#FrontendUtilities** 🔧 **#DevResourceVault** 🔧 **#MrDib** 🔧

### Remember

> _"Don't reinvent the wheel - use battle-tested utilities!"_

> _"Small bundle size = happy users"_

> _"Always tree-shake your dependencies"_

> _"Performance is a feature"_

</div>

---

<div align="center">

**Now go forth and build amazing things with these powerful utilities!** 💪✨

</div>
