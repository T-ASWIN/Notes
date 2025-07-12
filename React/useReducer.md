
---

## 🧠 What is `useReducer`?

`useReducer` is a **React Hook** that is an alternative to `useState` for managing **complex state logic**, especially when:

* State depends on **previous state**
* You have **multiple related state updates**
* You want to keep logic **organized and testable**

---

## ✅ When should you use `useReducer`?

| Use Case                            | Use `useState` | Use `useReducer`          |
| ----------------------------------- | -------------- | ------------------------- |
| Simple state (toggle, input)        | ✅ Yes          | ❌ No                      |
| Multiple state values               | ✅ Maybe        | ✅ Yes                     |
| Complex updates (add/remove/update) | ❌ No           | ✅ Yes                     |
| State based on action types         | ❌ No           | ✅ Yes                     |
| Shared logic between components     | ❌ No           | ✅ Yes (can be abstracted) |

---

## 📦 Real-world Use Cases

1. **Shopping Cart** – Add, remove, update items ✅ (You're doing this!)
2. **Form Handling** – Field validation, error tracking
3. **Authentication** – Login, logout, user info
4. **State machine** – Like tab switching or modal management
5. **Undo/redo functionality** – e.g., in an editor

---

## 🔁 How `useReducer` works

```jsx
const [state, dispatch] = useReducer(reducerFunction, initialState);
```

* `state` – current state value
* `dispatch(action)` – used to trigger state changes
* `reducerFunction(state, action)` – a pure function that returns new state based on the action

---

## ⚙️ Basic Example – Counter

```jsx
import { useReducer } from "react";

const initialState = { count: 0 };

function reducer(state, action) {
  if (action.type === "INCREMENT") {
    return { count: state.count + 1 };
  }
  if (action.type === "DECREMENT") {
    return { count: state.count - 1 };
  }
  return state;
}

export default function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <>
      <h1>{state.count}</h1>
      <button onClick={() => dispatch({ type: "DECREMENT" })}>-</button>
      <button onClick={() => dispatch({ type: "INCREMENT" })}>+</button>
    </>
  );
}
```

---

## 🧩 Why use `useReducer` instead of `useState`?

| Benefit                          | Explanation                                      |
| -------------------------------- | ------------------------------------------------ |
| Cleaner logic                    | Keeps complex updates in one place (`reducer`)   |
| Centralized actions              | Easier to debug, test, and track changes         |
| Useful with Context API          | Combine with context for global state management |
| Better performance in some cases | Avoids deep object spreading in component body   |

---

## ⚠️ Rules of `useReducer`

1. ✅ Reducer must be a **pure function** (no side effects, only returns updated state).
2. ✅ Always return a **new object** from the reducer.
3. ❌ Do not mutate `state` directly inside reducer.
4. ✅ Dispatch with an object: `{ type: "ACTION_NAME", payload: data }`.
5. ✅ Works well with `useContext` for global-like state.

---

## 🧠 Recap Summary

| Concept      | Description                                                      |
| ------------ | ---------------------------------------------------------------- |
| `useReducer` | Manages complex state logic using actions                        |
| `dispatch()` | Function that triggers reducer execution                         |
| `reducer()`  | Pure function returning new state                                |
| Best for     | Forms, carts, toggling views, authentication, multi-step wizards |

---

## 📊 **Real-world Usage: `useState` vs `useReducer`**

| Hook         | Common Usage in Projects |
| ------------ | ------------------------ |
| `useState`   | **80–90%** of the time   |
| `useReducer` | **10–20%** of the time   |

---

## ✅ Why is `useState` more common?

* It's **simpler and quicker** for most UI cases:

  * Inputs, toggles, modals
  * Small component-level state
* Easier to read and maintain for **basic apps**

```jsx
const [count, setCount] = useState(0);
```

---

## ✅ When does `useReducer` become useful?

* In **medium to large** apps
* When:

  * State transitions are complex
  * You manage **a list of items** (e.g., cart, todos)
  * State depends on **previous state**
  * You use **Context API** for global state

---

## 📦 Example Projects:

| Project Type                      | `useState` | `useReducer`      |
| --------------------------------- | ---------- | ----------------- |
| Portfolio website                 | ✅ Mostly   | ❌ Rare            |
| Shopping cart app                 | ✅ Some     | ✅ Often           |
| Form with validation              | ✅ Fields   | ✅ Logic           |
| Authentication (login/logout)     | ✅ Status   | ✅ User reducer    |
| Dashboard with filters            | ✅ Basic    | ✅ Filters/actions |
| Large app (with Redux or Context) | ❌ Minimal  | ✅ Central logic   |

---

## 🚀 Professional Projects (like React + Redux apps):

In large production systems (e.g., Amazon, Spotify dashboards):

* You might **start with `useState`**
* But for shared or complex logic, you'll switch to:

  * `useReducer`
  * Redux (which is just a glorified reducer)
  * Zustand, Recoil, Jotai (modern global state managers)

---

## 🧠 Tip for You (as a developer):

Start with `useState`, and **switch to `useReducer`** when:

* You’re duplicating similar `setState` logic
* You're managing a list (cart, todos, products)
* You have multiple interdependent state changes
* You want to keep logic centralized for reuse

---

Awesome! Here's a simple and clear **cheat sheet + flowchart** to help you decide:

---

## 🧾 ✅ useState vs useReducer – **Cheat Sheet**

| Scenario                                                         | Use `useState` ✅ | Use `useReducer` ✅ |
| ---------------------------------------------------------------- | ---------------- | ------------------ |
| Toggling a value (e.g., show/hide modal)                         | ✅                | ❌                  |
| Handling form inputs (1–2 fields)                                | ✅                | ❌                  |
| Managing multiple independent values (title, content, status...) | ✅                | ❌                  |
| Updating a list (add, delete, update items)                      | ❌                | ✅                  |
| State updates depend on **previous state**                       | ❌                | ✅                  |
| You want to organize logic into a **single function**            | ❌                | ✅                  |
| You want to use with **Context API for global state**            | ❌                | ✅                  |
| Managing **complex state transitions** (e.g., wizard steps)      | ❌                | ✅                  |
| You need a **testable, centralized** state management logic      | ❌                | ✅                  |

---

## 📊 Flowchart: When to Use useState vs useReducer

```
         ┌────────────────────────────┐
         │ Is the state simple?      │
         │ (toggle, input, flag...)  │
         └────────────┬──────────────┘
                      │ Yes
                      ▼
              ┌─────────────┐
              │  useState   │
              └─────────────┘
                      ▲
                      │ No
         ┌────────────┴─────────────┐
         │ Is the state made of     │
         │ multiple fields or logic?│
         └────────────┬─────────────┘
                      │ Yes
                      ▼
              ┌──────────────┐
              │ useReducer   │
              └──────────────┘
```

---

## 🛠 Examples for Practice:

| Project                       | Recommended Hook |
| ----------------------------- | ---------------- |
| Counter app                   | `useState`       |
| Todo app                      | `useReducer`     |
| Auth login/logout             | `useReducer`     |
| Theme toggle (light/dark)     | `useState`       |
| Shopping cart                 | `useReducer`     |
| Filter/search list            | `useReducer`     |
| Contact form (2–3 fields)     | `useState`       |
| Complex form with validations | `useReducer`     |

---


