<div align="center">

# 🔄 State Management in React

### _Taming complexity with the right tools_ 🎯

![State](https://img.shields.io/badge/State-Under_Control-blue?style=for-the-badge)
![Performance](https://img.shields.io/badge/Performance-Optimized-green?style=for-the-badge)
![DX](https://img.shields.io/badge/DX-Amazing-purple?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 Understanding State](#-understanding-state)
- [🐻 Zustand](#-zustand)
- [🔴 Redux Toolkit](#-redux-toolkit)
- [⚛️ Jotai](#️-jotai)
- [🎪 Valtio](#-valtio)
- [👻 MobX](#-mobx)
- [🧬 Recoil](#-recoil)
- [🤖 XState](#-xstate)
- [🔌 Context API](#-context-api)
- [📊 Comparison](#-comparison)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Understanding State

</div>

### Types of State 📦

```javascript
// ═══════════════════════════════════════════
// 1. Local Component State
// ═══════════════════════════════════════════

function Counter() {
  const [count, setCount] = useState(0);
  // Used only in this component
  return <div>{count}</div>;
}

// ═══════════════════════════════════════════
// 2. Shared State (Multiple Components)
// ═══════════════════════════════════════════

// Use: Context API, Zustand, Jotai
const useUIStore = create((set) => ({
  sidebarOpen: false,
  toggleSidebar: () =>
    set((state) => ({
      sidebarOpen: !state.sidebarOpen,
    })),
}));

// ═══════════════════════════════════════════
// 3. Server State (From API)
// ═══════════════════════════════════════════

// Use: TanStack Query, SWR (NOT global state!)
const { data: users } = useQuery({
  queryKey: ["users"],
  queryFn: fetchUsers,
});

// ═══════════════════════════════════════════
// 4. URL State (Search params, routes)
// ═══════════════════════════════════════════

// Use: React Router, Next.js router
const [searchParams, setSearchParams] = useSearchParams();
const query = searchParams.get("q");

// ═══════════════════════════════════════════
// 5. Form State
// ═══════════════════════════════════════════

// Use: React Hook Form, Formik
const { register, handleSubmit } = useForm();
```

> **💡 Pro Tip:** Don't put server state in global state managers! Use TanStack Query or SWR instead. They handle caching, refetching, and synchronization automatically.

---

### Decision Tree 🌳

```
Need State Management?
│
├─ Is it server data (API)?
│  └─ Use TanStack Query or SWR ✅
│
├─ Is it form data?
│  └─ Use React Hook Form or Formik ✅
│
├─ Is it URL-based?
│  └─ Use React Router or Next.js router ✅
│
├─ Used in 1-2 components?
│  └─ Use useState or useReducer ✅
│
├─ Shared across many components?
│  ├─ Simple state? → Zustand or Jotai ✅
│  ├─ Complex state? → Redux Toolkit ✅
│  └─ Need time-travel debugging? → Redux Toolkit ✅
│
└─ State machines?
   └─ Use XState ✅
```

---

<div align="center">

## 🐻 Zustand

</div>

### Simple, Fast, and Scalable 💪

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install zustand
```

```javascript
// ═══════════════════════════════════════════
// Basic Store
// ═══════════════════════════════════════════

import { create } from "zustand";

const useStore = create((set) => ({
  // State
  count: 0,
  user: null,

  // Actions
  increment: () => set((state) => ({ count: state.count + 1 })),
  decrement: () => set((state) => ({ count: state.count - 1 })),
  reset: () => set({ count: 0 }),
  setUser: (user) => set({ user }),
}));

// Usage in components
function Counter() {
  const count = useStore((state) => state.count);
  const increment = useStore((state) => state.increment);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>+1</button>
    </div>
  );
}

// Select multiple values
function Dashboard() {
  const { count, user, increment } = useStore();
  return <div>{/* ... */}</div>;
}

// ═══════════════════════════════════════════
// Async Actions
// ═══════════════════════════════════════════

const useUserStore = create((set) => ({
  user: null,
  loading: false,
  error: null,

  fetchUser: async (id) => {
    set({ loading: true, error: null });
    try {
      const response = await fetch(`/api/users/${id}`);
      const user = await response.json();
      set({ user, loading: false });
    } catch (error) {
      set({ error: error.message, loading: false });
    }
  },

  updateUser: async (id, data) => {
    const response = await fetch(`/api/users/${id}`, {
      method: "PATCH",
      body: JSON.stringify(data),
    });
    const user = await response.json();
    set({ user });
  },
}));

// ═══════════════════════════════════════════
// With Persistence (localStorage)
// ═══════════════════════════════════════════

import { persist, createJSONStorage } from "zustand/middleware";

const usePersistentStore = create(
  persist(
    (set) => ({
      theme: "dark",
      language: "en",
      setTheme: (theme) => set({ theme }),
      setLanguage: (language) => set({ language }),
    }),
    {
      name: "app-storage",
      storage: createJSONStorage(() => localStorage),
    }
  )
);

// ═══════════════════════════════════════════
// With DevTools
// ═══════════════════════════════════════════

import { devtools } from "zustand/middleware";

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
// With Immer (for nested state)
// ═══════════════════════════════════════════

import { immer } from "zustand/middleware/immer";

const useImmerStore = create(
  immer((set) => ({
    nested: {
      deep: {
        value: 0,
      },
    },

    // Direct mutation with Immer!
    increment: () =>
      set((state) => {
        state.nested.deep.value++;
      }),
  }))
);

// ═══════════════════════════════════════════
// Complete Advanced Store
// ═══════════════════════════════════════════

import { create } from "zustand";
import { persist, devtools, subscribeWithSelector } from "zustand/middleware";
import { immer } from "zustand/middleware/immer";

const useAppStore = create(
  devtools(
    persist(
      subscribeWithSelector(
        immer((set, get) => ({
          // State
          user: null,
          todos: [],
          ui: {
            theme: "dark",
            sidebarOpen: true,
            modals: {
              settings: false,
              profile: false,
            },
          },

          // Actions
          setUser: (user) => set({ user }),
          logout: () => set({ user: null }),

          addTodo: (todo) =>
            set((state) => {
              state.todos.push({
                id: Date.now(),
                ...todo,
                completed: false,
              });
            }),

          toggleTodo: (id) =>
            set((state) => {
              const todo = state.todos.find((t) => t.id === id);
              if (todo) todo.completed = !todo.completed;
            }),

          toggleTheme: () =>
            set((state) => {
              state.ui.theme = state.ui.theme === "dark" ? "light" : "dark";
            }),

          openModal: (name) =>
            set((state) => {
              state.ui.modals[name] = true;
            }),

          closeModal: (name) =>
            set((state) => {
              state.ui.modals[name] = false;
            }),

          // Computed values (getters)
          getCompletedTodos: () => get().todos.filter((t) => t.completed),
          getPendingTodos: () => get().todos.filter((t) => !t.completed),
        }))
      ),
      {
        name: "app-storage",
        partialize: (state) => ({
          user: state.user,
          ui: state.ui,
        }),
      }
    ),
    {
      name: "App Store",
    }
  )
);

// ═══════════════════════════════════════════
// Subscribe to Changes
// ═══════════════════════════════════════════

// Subscribe to specific state
const unsubscribe = useAppStore.subscribe(
  (state) => state.user,
  (user, previousUser) => {
    console.log("User changed:", user);
  }
);

// Subscribe to all changes
const unsubAll = useAppStore.subscribe((state, prevState) => {
  console.log("State changed:", state);
});

// Cleanup
unsubscribe();

// ═══════════════════════════════════════════
// Outside React Components
// ═══════════════════════════════════════════

// Get state
const state = useAppStore.getState();
console.log(state.user);

// Update state
useAppStore.setState({ user: newUser });

// Subscribe
useAppStore.subscribe((state) => {
  console.log(state);
});
```

**📦 Zustand Resources:**

- Docs: https://zustand-demo.pmnd.rs/
- Size: <1kb (gzipped)
- GitHub: https://github.com/pmndrs/zustand

> **💡 Pro Tip:** Zustand is perfect for 90% of apps. No providers, no boilerplate, works outside React. Use persist middleware for localStorage, devtools for debugging!

---

<div align="center">

## 🔴 Redux Toolkit

</div>

### Modern Redux Without the Pain 🔧

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

import { createSlice, createAsyncThunk } from '@reduxjs/toolkit';

// Async thunk for API calls
export const fetchUser = createAsyncThunk(
    'user/fetch',
    async (userId, { rejectWithValue }) => {
        try {
            const response = await fetch(`/api/users/${userId}`);
            if (!response.ok) throw new Error('Failed to fetch');
            return response.json();
        } catch (error) {
            return rejectWithValue(error.message);
        }
    }
);

const userSlice = createSlice({
    name: 'user',
    initialState: {
        data: null,
        status: 'idle', // 'idle' | 'loading' | 'succeeded' | 'failed'
        error: null,
    },
    reducers: {
        setUser: (state, action) => {
            state.data = action.payload;
        },
        logout: (state) => {
            state.data = null;
            state.status = 'idle';
        },
        updateProfile: (state, action) => {
            // Immer allows direct mutation!
            state.data.name = action.payload.name;
            state.data.email = action.payload.email;
        },
    },
    extraReducers: (builder) => {
        builder
            .addCase(fetchUser.pending, (state) => {
                state.status = 'loading';
                state.error = null;
            })
            .addCase(fetchUser.fulfilled, (state, action) => {
                state.status = 'succeeded';
                state.data = action.payload;
            })
            .addCase(fetchUser.rejected, (state, action) => {
                state.status = 'failed';
                state.error = action.payload;
            });
    },
});

export const { setUser, logout, updateProfile } = userSlice.actions;
export default userSlice.reducer;

// ═══════════════════════════════════════════
// Configure Store
// ═══════════════════════════════════════════

import { configureStore } from '@reduxjs/toolkit';
import userReducer from './features/user/userSlice';
import todosReducer from './features/todos/todosSlice';

export const store = configureStore({
    reducer: {
        user: userReducer,
        todos: todosReducer,
    },
    middleware: (getDefaultMiddleware) =>
        getDefaultMiddleware({
            serializableCheck: false, // If using non-serializable data
        }),
    devTools: process.env.NODE_ENV !== 'production',
});

// Infer types for TypeScript
export type RootState = ReturnType<typeof store.getState>;
export type AppDispatch = typeof store.dispatch;

// ═══════════════════════════════════════════
// Setup Provider
// ═══════════════════════════════════════════

import { Provider } from 'react-redux';
import { store } from './store';

function App() {
    return (
        <Provider store={store}>
            <YourApp />
        </Provider>
    );
}

// ═══════════════════════════════════════════
// Custom Hooks (TypeScript)
// ═══════════════════════════════════════════

import { TypedUseSelectorHook, useDispatch, useSelector } from 'react-redux';
import type { RootState, AppDispatch } from './store';

export const useAppDispatch = () => useDispatch<AppDispatch>();
export const useAppSelector: TypedUseSelectorHook<RootState> = useSelector;

// ═══════════════════════════════════════════
// Using in Components
// ═══════════════════════════════════════════

import { useAppDispatch, useAppSelector } from './hooks';
import { fetchUser, updateProfile } from './features/user/userSlice';

function UserProfile() {
    const dispatch = useAppDispatch();
    const { data: user, status, error } = useAppSelector((state) => state.user);

    useEffect(() => {
        if (status === 'idle') {
            dispatch(fetchUser(userId));
        }
    }, [status, dispatch, userId]);

    const handleUpdate = (updates) => {
        dispatch(updateProfile(updates));
    };

    if (status === 'loading') return <div>Loading...</div>;
    if (status === 'failed') return <div>Error: {error}</div>;
    if (!user) return null;

    return (
        <div>
            <h1>{user.name}</h1>
            <p>{user.email}</p>
            <button onClick={() => handleUpdate({ name: 'New Name' })}>
                Update Profile
            </button>
        </div>
    );
}

// ═══════════════════════════════════════════
// RTK Query (API Slices)
// ═══════════════════════════════════════════

import { createApi, fetchBaseQuery } from '@reduxjs/toolkit/query/react';

export const api = createApi({
    reducerPath: 'api',
    baseQuery: fetchBaseQuery({ baseUrl: '/api' }),
    tagTypes: ['User', 'Post'],
    endpoints: (builder) => ({
        getUser: builder.query({
            query: (id) => `users/${id}`,
            providesTags: (result, error, id) => [{ type: 'User', id }],
        }),
        updateUser: builder.mutation({
            query: ({ id, ...patch }) => ({
                url: `users/${id}`,
                method: 'PATCH',
                body: patch,
            }),
            invalidatesTags: (result, error, { id }) => [{ type: 'User', id }],
        }),
    }),
});

export const { useGetUserQuery, useUpdateUserMutation } = api;

// Usage
function UserProfile({ userId }) {
    const { data: user, isLoading, error } = useGetUserQuery(userId);
    const [updateUser, { isLoading: isUpdating }] = useUpdateUserMutation();

    if (isLoading) return <div>Loading...</div>;

    return (
        <div>
            <h1>{user.name}</h1>
            <button
                onClick={() => updateUser({ id: userId, name: 'New Name' })}
                disabled={isUpdating}
            >
                Update
            </button>
        </div>
    );
}
```

**📦 Redux Toolkit Resources:**

- Docs: https://redux-toolkit.js.org/
- Size: ~12kb (gzipped)
- Why: When you need complex state logic or time-travel debugging

> **💡 Pro Tip:** Redux Toolkit fixes Redux's boilerplate problem. Use RTK Query for server state - it's like TanStack Query but integrated with Redux!

<div align="center">

## ⚛️ Jotai

</div>

### Atomic State Management 💎

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

import { atom } from "jotai";

// Primitive atoms
export const countAtom = atom(0);
export const userAtom = atom(null);
export const todosAtom = atom([]);

// Derived atoms (computed)
export const doubleCountAtom = atom((get) => get(countAtom) * 2);

export const completedTodosAtom = atom((get) =>
  get(todosAtom).filter((todo) => todo.completed)
);

export const todoStatsAtom = atom((get) => {
  const todos = get(todosAtom);
  return {
    total: todos.length,
    completed: todos.filter((t) => t.completed).length,
    pending: todos.filter((t) => !t.completed).length,
  };
});

// Write-only atoms
export const incrementAtom = atom(
  null, // No read function
  (get, set) => {
    set(countAtom, get(countAtom) + 1);
  }
);

// Read-write atoms
export const upperCaseAtom = atom(
  (get) => get(textAtom).toUpperCase(),
  (get, set, newText) => {
    set(textAtom, newText.toLowerCase());
  }
);

// ═══════════════════════════════════════════
// Async Atoms
// ═══════════════════════════════════════════

// Async read
export const userDataAtom = atom(async (get) => {
  const userId = get(userIdAtom);
  const response = await fetch(`/api/users/${userId}`);
  return response.json();
});

// With parameters
export const userByIdAtom = atom(async (get) => {
  const id = get(userIdAtom);
  if (!id) return null;

  const response = await fetch(`/api/users/${id}`);
  return response.json();
});

// Async write
export const updateUserAtom = atom(null, async (get, set, updates) => {
  const user = get(userAtom);
  const response = await fetch(`/api/users/${user.id}`, {
    method: "PATCH",
    body: JSON.stringify(updates),
  });
  const updated = await response.json();
  set(userAtom, updated);
});

// ═══════════════════════════════════════════
// Using in Components
// ═══════════════════════════════════════════

import { useAtom, useAtomValue, useSetAtom } from "jotai";

// Read and write
function Counter() {
  const [count, setCount] = useAtom(countAtom);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount((c) => c + 1)}>Increment</button>
    </div>
  );
}

// Read only
function Display() {
  const count = useAtomValue(countAtom);
  const doubleCount = useAtomValue(doubleCountAtom);

  return (
    <div>
      <p>Count: {count}</p>
      <p>Double: {doubleCount}</p>
    </div>
  );
}

// Write only
function Controls() {
  const increment = useSetAtom(incrementAtom);

  return <button onClick={increment}>+1</button>;
}

// ═══════════════════════════════════════════
// With React Suspense
// ═══════════════════════════════════════════

function UserProfile() {
  // This suspends while loading!
  const user = useAtomValue(userDataAtom);

  return <div>{user.name}</div>;
}

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <UserProfile />
    </Suspense>
  );
}

// ═══════════════════════════════════════════
// Atom Families (Dynamic Atoms)
// ═══════════════════════════════════════════

import { atomFamily } from "jotai/utils";

// Create atoms on demand
const todoAtomFamily = atomFamily((id) =>
  atom(async () => {
    const response = await fetch(`/api/todos/${id}`);
    return response.json();
  })
);

function TodoItem({ id }) {
  const todo = useAtomValue(todoAtomFamily(id));
  return <div>{todo.title}</div>;
}

// ═══════════════════════════════════════════
// Persistence
// ═══════════════════════════════════════════

import { atomWithStorage } from "jotai/utils";

const themeAtom = atomWithStorage("theme", "dark");
const languageAtom = atomWithStorage("language", "en");

// ═══════════════════════════════════════════
// DevTools
// ═══════════════════════════════════════════

import { useAtomDevtools } from "jotai-devtools";

function DebugCounter() {
  const [count, setCount] = useAtom(countAtom);
  useAtomDevtools(countAtom, { name: "count" });

  return <button onClick={() => setCount((c) => c + 1)}>{count}</button>;
}
```

**📦 Jotai Resources:**

- Docs: https://jotai.org/
- Size: ~3kb (gzipped)
- Why: Atomic approach, minimal re-renders, Suspense-ready

> **💡 Pro Tip:** Jotai is perfect for fine-grained reactivity. Components only re-render when the atoms they use change. Great for complex state dependencies!

---

<div align="center">

## 🎪 Valtio

</div>

### Proxy-Based State 🪄

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install valtio
```

```javascript
// ═══════════════════════════════════════════
// Create Proxy State
// ═══════════════════════════════════════════

import { proxy, useSnapshot, subscribe } from 'valtio';
import { devtools } from 'valtio/utils';

// Simple proxy
const state = proxy({
    count: 0,
    text: '',
    nested: {
        value: 0,
    },
});

// Complex proxy
const appState = proxy({
    user: null,
    todos: [],
    ui: {
        theme: 'dark',
        sidebarOpen: true,
        modals: {
            settings: false,
            profile: false,
        },
    },
});

// Enable devtools
devtools(appState, { name: 'app', enabled: true });

// ═══════════════════════════════════════════
// Direct Mutations (No Actions Needed!)
// ═══════════════════════════════════════════

// Just mutate!
state.count++;
state.text = 'Hello';
state.nested.value = 42;

// Arrays work too
appState.todos.push({ id: 1, text: 'Learn Valtio', completed: false });
appState.todos[0].completed = true;

// Objects
appState.user = { name: 'MrDib', email: 'mrdib@example.com' };
appState.ui.theme = 'light';
appState.ui.modals.settings = true;

// You can still use functions for organization
function increment() {
    state.count++;
}

function addTodo(text) {
    appState.todos.push({
        id: Date.now(),
        text,
        completed: false,
    });
}

function toggleTodo(id) {
    const todo = appState.todos.find(t => t.id === id);
    if (todo) {
        todo.completed = !todo.completed;
    }
}

// ═══════════════════════════════════════════
# Using in Components
// ═══════════════════════════════════════════

function Counter() {
    const snap = useSnapshot(state);

    return (
        <div>
            <p>Count: {snap.count}</p>
            <button onClick={() => state.count++}>+1</button>
            <button onClick={() => state.count--}>-1</button>
        </div>
    );
}

function TodoList() {
    const snap = useSnapshot(appState);

    return (
        <ul>
            {snap.todos.map(todo => (
                <li key={todo.id} onClick={() => toggleTodo(todo.id)}>
                    <span style={{
                        textDecoration: todo.completed ? 'line-through' : 'none'
                    }}>
                        {todo.text}
                    </span>
                </li>
            ))}
        </ul>
    );
}

// ═══════════════════════════════════════════
// Computed Values
// ═══════════════════════════════════════════

import { derive } from 'valtio/utils';

const derived = derive({
    completedCount: (get) =>
        get(appState).todos.filter(t => t.completed).length,

    pendingCount: (get) =>
        get(appState).todos.filter(t => !t.completed).length,

    completionRate: (get) => {
        const todos = get(appState).todos;
        if (todos.length === 0) return 0;
        const completed = todos.filter(t => t.completed).length;
        return (completed / todos.length) * 100;
    },
});

function Stats() {
    const snap = useSnapshot(derived);

    return (
        <div>
            <p>Completed: {snap.completedCount}</p>
            <p>Pending: {snap.pendingCount}</p>
            <p>Rate: {snap.completionRate.toFixed(1)}%</p>
        </div>
    );
}

// ═══════════════════════════════════════════
// Subscribe to Changes
// ═══════════════════════════════════════════

// Subscribe to all changes
const unsubscribe = subscribe(appState, () => {
    console.log('State changed:', appState);
});

// Subscribe to specific property
const unsubUser = subscribe(appState.user, () => {
    console.log('User changed:', appState.user);
});

// Cleanup
unsubscribe();

// ═══════════════════════════════════════════
// Async Operations
// ═══════════════════════════════════════════

async function fetchUser(id) {
    appState.user = { loading: true };

    try {
        const response = await fetch(`/api/users/${id}`);
        const user = await response.json();
        appState.user = user;
    } catch (error) {
        appState.user = { error: error.message };
    }
}

// ═══════════════════════════════════════════
// Persistence
// ═══════════════════════════════════════════

import { proxyWithPersist } from 'valtio-persist';

const persistedState = proxyWithPersist({
    name: 'app-storage',
    initialState: {
        theme: 'dark',
        language: 'en',
    },
    persistStrategies: 'localStorage',
});
```

**📦 Valtio Resources:**

- Docs: https://valtio.pmnd.rs/
- Size: ~3.5kb (gzipped)
- Why: Mutate state directly, simple mental model

> **💡 Pro Tip:** Valtio is great if you like Vue's reactivity or MobX's simplicity. Just mutate the proxy and components update automatically!

---

<div align="center">

## 👻 MobX

</div>

### Object-Oriented Reactive State 🎯

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install mobx mobx-react-lite
```

```javascript
// ═══════════════════════════════════════════
// Create Observable Store
// ═══════════════════════════════════════════

import { makeAutoObservable, runInAction, flow } from "mobx";

class UserStore {
  user = null;
  loading = false;
  error = null;

  constructor() {
    makeAutoObservable(this);
  }

  // Actions
  setUser(user) {
    this.user = user;
  }

  // Async actions with runInAction
  async fetchUser(id) {
    this.loading = true;
    this.error = null;

    try {
      const response = await fetch(`/api/users/${id}`);
      const user = await response.json();

      runInAction(() => {
        this.user = user;
        this.loading = false;
      });
    } catch (error) {
      runInAction(() => {
        this.error = error.message;
        this.loading = false;
      });
    }
  }

  // Async with flow (generator-based)
  fetchUserFlow = flow(function* (id) {
    this.loading = true;
    this.error = null;

    try {
      const response = yield fetch(`/api/users/${id}`);
      const user = yield response.json();
      this.user = user;
    } catch (error) {
      this.error = error.message;
    } finally {
      this.loading = false;
    }
  });

  // Computed values
  get isAuthenticated() {
    return this.user !== null;
  }

  get userName() {
    return this.user?.name || "Guest";
  }
}

// Create store instance
const userStore = new UserStore();

// ═══════════════════════════════════════════
// Using in Components
// ═══════════════════════════════════════════

import { observer } from "mobx-react-lite";

const UserProfile = observer(() => {
  const { user, loading, error, isAuthenticated } = userStore;

  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error}</div>;
  if (!isAuthenticated) return <div>Not logged in</div>;

  return <div>{user.name}</div>;
});

// ═══════════════════════════════════════════
// Context Pattern
// ═══════════════════════════════════════════

import { createContext, useContext } from "react";

class RootStore {
  constructor() {
    this.userStore = new UserStore();
    this.todoStore = new TodoStore();
  }
}

const StoreContext = createContext(new RootStore());

export const useStore = () => useContext(StoreContext);

// Usage
const TodoList = observer(() => {
  const { todoStore } = useStore();

  return (
    <ul>
      {todoStore.todos.map((todo) => (
        <li key={todo.id}>{todo.text}</li>
      ))}
    </ul>
  );
});
```

**📦 MobX Resources:**

- Docs: https://mobx.js.org/
- Size: ~15kb (gzipped)
- Why: OOP approach, automatic tracking

> **💡 Pro Tip:** MobX is great if you prefer OOP. Use `makeAutoObservable` for automatic tracking, `observer` HOC for reactive components!

---

<div align="center">

## 🔌 Context API

</div>

### Built-in React State Sharing 🎯

```javascript
// ═══════════════════════════════════════════
// Basic Context
// ═══════════════════════════════════════════

import { createContext, useContext, useState } from "react";

const ThemeContext = createContext();

export function ThemeProvider({ children }) {
  const [theme, setTheme] = useState("dark");

  const toggleTheme = () => {
    setTheme((prev) => (prev === "dark" ? "light" : "dark"));
  };

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
}

export const useTheme = () => useContext(ThemeContext);

// Usage
function App() {
  return (
    <ThemeProvider>
      <Header />
      <Main />
    </ThemeProvider>
  );
}

function Header() {
  const { theme, toggleTheme } = useTheme();

  return (
    <header className={theme}>
      <button onClick={toggleTheme}>Toggle Theme</button>
    </header>
  );
}

// ═══════════════════════════════════════════
// With useReducer (For Complex State)
// ═══════════════════════════════════════════

import { createContext, useContext, useReducer } from "react";

// Reducer
function todoReducer(state, action) {
  switch (action.type) {
    case "ADD_TODO":
      return [
        ...state,
        {
          id: Date.now(),
          text: action.payload,
          completed: false,
        },
      ];
    case "TOGGLE_TODO":
      return state.map((todo) =>
        todo.id === action.payload
          ? { ...todo, completed: !todo.completed }
          : todo
      );
    case "DELETE_TODO":
      return state.filter((todo) => todo.id !== action.payload);
    default:
      return state;
  }
}

// Context
const TodoContext = createContext();

export function TodoProvider({ children }) {
  const [todos, dispatch] = useReducer(todoReducer, []);

  const addTodo = (text) => {
    dispatch({ type: "ADD_TODO", payload: text });
  };

  const toggleTodo = (id) => {
    dispatch({ type: "TOGGLE_TODO", payload: id });
  };

  const deleteTodo = (id) => {
    dispatch({ type: "DELETE_TODO", payload: id });
  };

  return (
    <TodoContext.Provider
      value={{
        todos,
        addTodo,
        toggleTodo,
        deleteTodo,
      }}
    >
      {children}
    </TodoContext.Provider>
  );
}

export const useTodos = () => useContext(TodoContext);

// ═══════════════════════════════════════════
// Multiple Contexts
// ═══════════════════════════════════════════

function App() {
  return (
    <AuthProvider>
      <ThemeProvider>
        <TodoProvider>
          <YourApp />
        </TodoProvider>
      </ThemeProvider>
    </AuthProvider>
  );
}

// ═══════════════════════════════════════════
// Performance Optimization
// ═══════════════════════════════════════════

import { useMemo } from "react";

function OptimizedProvider({ children }) {
  const [state, setState] = useState(initialState);

  // Memoize value to prevent unnecessary re-renders
  const value = useMemo(
    () => ({
      state,
      actions: {
        increment: () => setState((s) => ({ ...s, count: s.count + 1 })),
        decrement: () => setState((s) => ({ ...s, count: s.count - 1 })),
      },
    }),
    [state]
  );

  return <MyContext.Provider value={value}>{children}</MyContext.Provider>;
}

// Split contexts to avoid re-renders
const StateContext = createContext();
const DispatchContext = createContext();

function SplitProvider({ children }) {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <StateContext.Provider value={state}>
      <DispatchContext.Provider value={dispatch}>
        {children}
      </DispatchContext.Provider>
    </StateContext.Provider>
  );
}

// Only re-render when state changes
function Reader() {
  const state = useContext(StateContext);
  return <div>{state.count}</div>;
}

// Never re-renders (dispatch is stable)
function Writer() {
  const dispatch = useContext(DispatchContext);
  return <button onClick={() => dispatch({ type: "INCREMENT" })}>+</button>;
}
```

**📦 Context API Resources:**

- Docs: https://react.dev/reference/react/useContext
- Size: 0kb (built-in)
- Why: Simple state sharing without external libraries

> **💡 Pro Tip:** Context is great for theme, auth, i18n - things that change rarely. For frequently changing state, use Zustand or Jotai to avoid re-render issues!

---

<div align="center">

## 📊 Comparison

</div>

### State Management Library Comparison 🔍

| Library           | Size  | Learning Curve | Boilerplate | Re-renders | Best For       |
| ----------------- | ----- | -------------- | ----------- | ---------- | -------------- |
| **Zustand**       | <1kb  | Easy           | None        | Minimal    | Most apps      |
| **Jotai**         | 3kb   | Easy           | None        | Minimal    | Atomic state   |
| **Valtio**        | 3.5kb | Easy           | None        | Minimal    | Mutable style  |
| **Redux Toolkit** | 12kb  | Medium         | Low         | More       | Complex apps   |
| **MobX**          | 15kb  | Medium         | Low         | Minimal    | OOP fans       |
| **Recoil**        | 21kb  | Medium         | Low         | Minimal    | Facebook stack |
| **XState**        | 16kb  | Hard           | High        | Minimal    | State machines |
| **Context**       | 0kb   | Easy           | Medium      | More       | Simple sharing |

---

### Feature Comparison 🎯

| Feature           | Zustand | Redux Toolkit | Jotai | Valtio | Context |
| ----------------- | ------- | ------------- | ----- | ------ | ------- |
| **No Provider**   | ✅      | ❌            | ❌    | ✅     | ❌      |
| **TypeScript**    | ✅      | ✅            | ✅    | ✅     | ✅      |
| **DevTools**      | ✅      | ✅            | ✅    | ✅     | ✅      |
| **Persistence**   | ✅      | ⚠️            | ✅    | ✅     | ❌      |
| **Async**         | ✅      | ✅            | ✅    | ✅     | ✅      |
| **Time Travel**   | ❌      | ✅            | ❌    | ❌     | ❌      |
| **Suspense**      | ❌      | ❌            | ✅    | ❌     | ❌      |
| **Computed**      | Manual  | Manual        | ✅    | ✅     | Manual  |
| **Outside React** | ✅      | ✅            | ❌    | ✅     | ❌      |

---

<div align="center">

## 💡 Best Practices

</div>

### When to Use What? 🤔

```javascript
// ═══════════════════════════════════════════
// Server State (From APIs)
// ═══════════════════════════════════════════

// ❌ DON'T: Put in global state
const useStore = create((set) => ({
  users: [],
  fetchUsers: async () => {
    const users = await api.getUsers();
    set({ users });
  },
}));

// ✅ DO: Use TanStack Query or SWR
const { data: users } = useQuery({
  queryKey: ["users"],
  queryFn: fetchUsers,
});

// ═══════════════════════════════════════════
// Local Component State
// ═══════════════════════════════════════════

// ❌ DON'T: Use global state for local UI
const useStore = create((set) => ({
  modalOpen: false,
  setModalOpen: (open) => set({ modalOpen: open }),
}));

// ✅ DO: Use useState
function Modal() {
  const [isOpen, setIsOpen] = useState(false);
  return <div>{/* ... */}</div>;
}

// ═══════════════════════════════════════════
// Shared Client State
// ═══════════════════════════════════════════

// ✅ DO: Use Zustand, Jotai, or Context
const useUIStore = create((set) => ({
  theme: "dark",
  sidebarOpen: true,
  toggleTheme: () =>
    set((state) => ({
      theme: state.theme === "dark" ? "light" : "dark",
    })),
}));

// ═══════════════════════════════════════════
// Form State
// ═══════════════════════════════════════════

// ❌ DON'T: Use global state for forms
// ✅ DO: Use React Hook Form or Formik

import { useForm } from "react-hook-form";

function Form() {
  const { register, handleSubmit } = useForm();
  return <form>{/* ... */}</form>;
}
```

---

### State Colocation 📍

```javascript
// ═══════════════════════════════════════════
// Keep State Close to Where It's Used
// ═══════════════════════════════════════════

// ❌ BAD: Everything in global state
const useStore = create((set) => ({
  searchQuery: "",
  activeTab: "home",
  modalOpen: false,
  // ... 50 more properties
}));

// ✅ GOOD: Split by domain
const useAuthStore = create((set) => ({
  user: null,
  token: null,
  login: (user, token) => set({ user, token }),
}));

const useUIStore = create((set) => ({
  theme: "dark",
  sidebarOpen: true,
}));

// ✅ BETTER: Keep local state local
function SearchBar() {
  const [query, setQuery] = useState("");
  // Only used here? Keep it here!
}
```

---

### Performance Tips ⚡

```javascript
// ═══════════════════════════════════════════
// Zustand - Select Only What You Need
// ═══════════════════════════════════════════

// ❌ BAD: Selects entire store
function Component() {
  const store = useStore();
  return <div>{store.count}</div>;
}

// ✅ GOOD: Select specific values
function Component() {
  const count = useStore((state) => state.count);
  return <div>{count}</div>;
}

// ✅ BETTER: Shallow comparison for objects
import { shallow } from "zustand/shallow";

function Component() {
  const { count, user } = useStore(
    (state) => ({ count: state.count, user: state.user }),
    shallow
  );
}

// ═══════════════════════════════════════════
// Context - Split Contexts
// ═══════════════════════════════════════════

// ❌ BAD: Single context with all state
const AppContext = createContext({
  user: null,
  theme: "dark",
  todos: [],
  // Changes cause all consumers to re-render
});

// ✅ GOOD: Separate contexts
const UserContext = createContext();
const ThemeContext = createContext();
const TodoContext = createContext();

// ═══════════════════════════════════════════
// Redux - Use Selectors
// ═══════════════════════════════════════════

import { createSelector } from "@reduxjs/toolkit";

// Memoized selector
const selectCompletedTodos = createSelector([(state) => state.todos], (todos) =>
  todos.filter((t) => t.completed)
);
```

---

### Common Patterns 🎯

```javascript
// ═══════════════════════════════════════════
// Loading States
// ═══════════════════════════════════════════

const useDataStore = create((set) => ({
  data: null,
  loading: false,
  error: null,

  fetchData: async () => {
    set({ loading: true, error: null });
    try {
      const data = await api.getData();
      set({ data, loading: false });
    } catch (error) {
      set({ error: error.message, loading: false });
    }
  },
}));

// ═══════════════════════════════════════════
// Optimistic Updates
// ═══════════════════════════════════════════

const useTodoStore = create((set, get) => ({
  todos: [],

  toggleTodo: async (id) => {
    // Optimistically update
    const oldTodos = get().todos;
    set({
      todos: oldTodos.map((t) =>
        t.id === id ? { ...t, completed: !t.completed } : t
      ),
    });

    try {
      await api.toggleTodo(id);
    } catch (error) {
      // Rollback on error
      set({ todos: oldTodos });
    }
  },
}));

// ═══════════════════════════════════════════
// Undo/Redo
// ═══════════════════════════════════════════

const useHistoryStore = create((set, get) => ({
  present: initialState,
  past: [],
  future: [],

  setState: (newState) => {
    const { present, past } = get();
    set({
      present: newState,
      past: [...past, present],
      future: [],
    });
  },

  undo: () => {
    const { present, past, future } = get();
    if (past.length === 0) return;

    const previous = past[past.length - 1];
    set({
      present: previous,
      past: past.slice(0, -1),
      future: [present, ...future],
    });
  },

  redo: () => {
    const { present, past, future } = get();
    if (future.length === 0) return;

    const next = future[0];
    set({
      present: next,
      past: [...past, present],
      future: future.slice(1),
    });
  },
}));
```

---

<div align="center">

## 🎓 Decision Guide

### _Choose the Right Tool_ 🎯

</div>

```
Start Here:
│
├─ Building a simple app?
│  └─ Use useState + Context ✅
│
├─ Need shared state across many components?
│  ├─ Simple state? → Zustand ✅
│  ├─ Like atoms? → Jotai ✅
│  └─ Like mutations? → Valtio ✅
│
├─ Large enterprise app?
│  └─ Redux Toolkit ✅
│
├─ Need state machines?
│  └─ XState ✅
│
├─ Object-oriented style?
│  └─ MobX ✅
│
└─ Working with server data?
   └─ DON'T use state management!
      Use TanStack Query or SWR ✅
```

---

### MrDib's Recommendations 🏆

```yaml
Small Projects (< 10 components):
  - useState + Context
  - No external library needed

Medium Projects (10-50 components):
  Primary: Zustand
  Alternative: Jotai
  Why: Simple, no boilerplate, great DX

Large Projects (50+ components):
  Primary: Zustand or Redux Toolkit
  Secondary: Jotai for specific features
  Why: Scalable, maintainable, team-friendly

Enterprise:
  Primary: Redux Toolkit
  Why: Time-travel debugging, middleware, tooling

Always Use:
  - TanStack Query for server state
  - React Hook Form for forms
  - Keep state colocated when possible
```

---

<div align="center">

## 🎯 Quick Setup Guide

### _Get Started Fast_ 🚀

</div>

```bash
# ═══════════════════════════════════════════
# My Recommended Stack (2025)
# ═══════════════════════════════════════════

# Client state
npm install zustand

# Server state
npm install @tanstack/react-query

# Forms
npm install react-hook-form zod

# That's it! 🎉

# ═══════════════════════════════════════════
# Alternative Stack
# ═══════════════════════════════════════════

# Atomic state
npm install jotai

# Server state
npm install swr

# Forms
npm install react-hook-form

# ═══════════════════════════════════════════
# Enterprise Stack
# ═══════════════════════════════════════════

# State management
npm install @reduxjs/toolkit react-redux

# Server state (integrated)
# RTK Query is included

# Forms
npm install react-hook-form @hookform/resolvers zod
```

---

<div align="center">

**Built with 🔄 by MrDib, for State Masters**

_"The best state management is the one you don't need!"_

**Happy State Managing!** 🎯

**If you found this helpful, give it a ⭐ star and share with fellow developers!**

</div>

---

### Contributing 🤝

Found a better pattern? Want to add examples? Contributions are welcome!

1. Fork the repository
2. Add your state management examples
3. Update comparison tables
4. Submit a pull request

---

### License 📄

This guide is open source and available under the MIT License.

---

<div align="center">

**Stay organized. Keep state simple. Build better apps!** 💪✨

🔄 **#StateManagement** 🔄 **#DevResourceVault** 🔄 **#MrDib** 🔄

### Remember

> _"The best state is local state"_

> _"Server state ≠ Client state"_

> _"Don't over-engineer - start simple"_

> _"Colocation > Centralization"_

> _"Performance matters, but measure first"_

</div>

---

<div align="center">

**Now go forth and manage state like a pro!** 🌟🔄

</div>
