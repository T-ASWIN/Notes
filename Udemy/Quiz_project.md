
In JavaScript, the difference between using **`()`** and **`{}`** in an arrow function is all about what you're **returning**.

---

### 🔁 What you're using:

```js
QUESTIONS[activeQuestionIndex].answers.map((answer) => (
  <li className="answer" key={answer}>
    <button onClick={() => handleClick(answer)}>{answer}</button>
  </li>
));
```

This uses **`()`**, which **implicitly returns** the JSX inside.

---

### ✅ Why this works:

* `()` in arrow functions means: **"return this expression implicitly"**.
* JSX is **just JavaScript syntax**, and JSX elements are **expressions**.
* So using `()` returns the JSX without needing a `return` keyword.

---

### ❌ If you used `{}`:

```js
.map((answer) => {
  <li>...</li>; // This returns nothing! (undefined)
})
```

This won't work, because:

* When using `{}`, you must **explicitly return** something.
* If you forget `return`, it returns `undefined`.

---

### ✅ Correct with `{}`:

```js
.map((answer) => {
  return (
    <li className="answer" key={answer}>
      <button onClick={() => handleClick(answer)}>{answer}</button>
    </li>
  );
});
```

---

### 📌 Summary:

| Syntax    | Behavior               |
| --------- | ---------------------- |
| `( ... )` | Implicit return        |
| `{ ... }` | Need explicit `return` |

✅ So use `()` when returning a single expression (like JSX) directly.

