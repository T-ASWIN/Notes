
---

### 🧠 Example:

#### ✅ No Side Effect:

```js
function add(a, b) {
  return a + b;
}
```

> It just returns a value. Nothing else happens. No side effect.

---

#### ❌ With Side Effect:

```js
function saveName(name) {
  localStorage.setItem('userName', name);
}
```

> This affects something **outside the function** (localStorage). That's a side effect.

---

### 🧾 Common Side Effects in React:

* Fetching data (`fetch`, `axios`)
* Changing the DOM manually
* Using `setTimeout` or `setInterval`
* Logging to the console
* Saving to local storage
* Subscribing to events (like window resize)
* Updating a global variable or browser tab title

---

### 💡 Why it matters in React:

React is **declarative** — it wants to manage the UI **based on state**.
So, you need to tell React **when** and **how** to run side effects using `useEffect()` — so it doesn't run them at the wrong time.

---

### 📌 In short:

> A **side effect** is anything that **touches or changes something outside your function.**
> React controls this using the `useEffect` hook.

