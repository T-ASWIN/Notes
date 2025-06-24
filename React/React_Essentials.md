
## 1️⃣ State

State is like a variable that lives inside your component. When it changes, React re-renders the UI.

```js
const [count, setCount] = useState(0);
````

* `count` → current value
* `setCount` → function to change it
* `useState(0)` → initial value = 0

### 🌀 Why Use State?

React re-renders the component when state changes.

```js
<button onClick={() => setCount(count + 1)}>Click Me</button>
```

Every click:

1. Updates the state
2. Re-renders the component

---

### ✅ When to Use `useState`

| Situation                        | Should Use `useState`? | Example Value                      |
| -------------------------------- | ---------------------- | ---------------------------------- |
| User input                       | ✅ Yes                  | `email`, `name`, `password`        |
| Button clicks / toggles          | ✅ Yes                  | `isVisible`, `count`, `darkMode`   |
| Conditional display (e.g. error) | ✅ Yes                  | `error`, `formSubmitted`           |
| Data fetched from backend        | ✅ Yes                  | `userProfile`, `posts`, `products` |
| Static content / constants       | ❌ No (use `const`)     | `headingText`, `apiKey`            |

---

### 🧪 Example: Login Form

```js
const [email, setEmail] = useState('');
const [password, setPassword] = useState('');
const [submitted, setSubmitted] = useState(false);
const [error, setError] = useState('');
```

---

## 2️⃣ Strict Mode

Strict mode is a wrapper that helps highlight problems in your app (only in development).

### ✅ How to Use It

**Option 1 – `index.jsx`:**

```js
import React from 'react';

<React.StrictMode>
  <App />
</React.StrictMode>
```

**Option 2 – In any component:**

```js
import { StrictMode } from 'react';

<StrictMode>
  <App />
</StrictMode>
```

🧪 It runs components **twice** in dev mode to help catch issues.

---

## 3️⃣ Updating Arrays or Objects (Immutably)

Always create a new copy when updating state.

```js
function(prev) {
  return [...prev, newItem];
}
```

### ✅ Example: Add Todo

```js
function addTodo(task) {
  setTodos(prev => [
    ...prev,
    { id: Date.now(), task, completed: false }
  ]);
}
```

---

## 4️⃣ Return (Short-Circuiting Functions)

Using `return` can exit early from a function.

```js
if (!input.trim()) return;
```

💡 Prevents further execution if the condition is met.

---

## 5️⃣ Event Handling in React

Use events to capture user actions.

### ✅ Simple Input Handler

```js
<input
  type="text"
  onChange={(event) => console.log(event.target.value)}
/>
```

### 🧪 Full Example

```js
import { useState } from 'react';

function MyForm() {
  const [name, setName] = useState('');

  function handleChange(event) {
    console.log(event.target.value);
    setName(event.target.value);
  }

  return (
    <div>
      <input type="text" onChange={handleChange} />
      <p>Hello, {name}</p>
    </div>
  );
}
```

### 🧾 Output Flow:

1. You type `Aswin`
2. Console logs every letter
3. UI updates: `Hello, Aswin`

---

### 🔍 Event Breakdown

| Concept              | Description                   |
| -------------------- | ----------------------------- |
| `event`              | Event object from the browser |
| `event.target`       | The HTML input element        |
| `event.target.value` | What the user typed           |

---

## 🧼 Final Notes

* Use state to track changes
* Keep components pure and predictable
* Use StrictMode for better debugging

```

---

## 📦 Uploading to GitHub

Make sure the file is named **`README.md`** and placed in the root of your repo. GitHub automatically renders it beautifully.

---

Would you like me to help you **generate this as a downloadable file** or help you **push it to your GitHub repo**?
```
