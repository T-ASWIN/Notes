
---

### 🧠 **Why `{{ }}` (double braces) is used in React:**

React uses **JSX** — which looks like HTML, but it's actually **JavaScript inside**.

In JSX, to pass a **JavaScript object** as a prop or style, you do this:

```jsx
<Component someProp={{ key: "value" }} />
```

The **outer `{}`** tells JSX:

> "Hey, the value inside is JavaScript."

The **inner `{}`** is the actual **JavaScript object**.

---

### 📦 **Use Case 1: Passing an object as a prop**

```jsx
function MovieCard({ movie }) {
  return <p>{movie.name}</p>;
}

function App() {
  const movie = { name: "Inception", year: 2010 };

  return <MovieCard movie={movie} />; // ✅ single brace: passing variable
}
```

But if you don’t want to use a variable and pass the object directly:

```jsx
return <MovieCard movie={{ name: "Inception", year: 2010 }} />; // ✅ double braces
```

Here:

* **Outer `{}`** = “this is JS”
* **Inner `{}`** = the object itself

---

### 🎨 **Use Case 2: Inline styles in JSX**

```jsx
return (
  <div style={{ color: "red", fontSize: "20px" }}>
    Hello
  </div>
);
```

* Outer `{}` = React expects JS here.
* Inner `{}` = actual style object (`{ color: "red" }`).

---

### 🔑 **Summary**

| Pattern | Meaning                                                 |
| ------- | ------------------------------------------------------- |
| `{}`    | Insert JavaScript inside JSX                            |
| `{{ }}` | Insert a **JavaScript object** (used in props or style) |

So **`movie={{ name: "X" }}`** means:

> "Hey React, I'm passing a JS object to the `movie` prop."

---

### ✅ **Example 1: Inline Styles**

```jsx
function App() {
  return (
    <div style={{ color: 'blue', backgroundColor: 'lightgray' }}>
      Hello, styled with inline CSS!
    </div>
  );
}
```

* ✅ `style={{ ... }}` → outer `{}` = JS expression, inner `{}` = style object.

---

### ✅ **Example 2: Passing Object as a Prop**

```jsx
function MovieCard({ movie }) {
  return <p>{movie.name} ({movie.year})</p>;
}

function App() {
  return (
    <MovieCard movie={{ name: 'Inception', year: 2010 }} />
  );
}
```

* ✅ `movie={{ name: 'Inception' }}` → passing an **object directly** to a child component.

---

### ✅ **Example 3: Using Conditional Style Based on a Value**

```jsx
function App() {
  const isActive = true;

  return (
    <div
      style={{
        color: isActive ? 'green' : 'gray',
        fontWeight: isActive ? 'bold' : 'normal',
      }}
    >
      User Status
    </div>
  );
}
```

* ✅ Logic inside object, wrapped in outer `{}`.

---

### ✅ **Example 4: Dynamic Object Literal Inside JSX**

```jsx
function App() {
  return (
    <div>
      {JSON.stringify({ name: 'React', version: 18 })}
    </div>
  );
}
```

* ✅ `{{ name: 'React' }}` — inside JSX, we print an object.

---

### ✅ **Example 5: Nesting an Object Inline (for config/settings)**

```jsx
function ConfigBox({ settings }) {
  return <pre>{JSON.stringify(settings, null, 2)}</pre>;
}

function App() {
  return (
    <ConfigBox
      settings={{
        theme: 'dark',
        layout: { sidebar: true, navbar: false },
      }}
    />
  );
}
```

* ✅ Passing a deeply nested object using double braces.

---

### 🔁 Summary Table:

| Use Case                | Syntax                              | Meaning                        |
| ----------------------- | ----------------------------------- | ------------------------------ |
| Inline CSS styling      | `style={{ color: "red" }}`          | JS object inside JSX           |
| Object as a prop        | `movie={{ name: "X" }}`             | Object literal passed directly |
| Conditional style       | `style={{ color: isDark ? ... }}`   | Use JS logic inside object     |
| Nested object in props  | `config={{ theme: { dark: true }}}` | Structured settings            |
| Inline object rendering | `{JSON.stringify({ a: 1 })}`        | Printing object in JSX         |


```js
const handleSearch = (event) => {
  event.preventDefault();
};
```

Instead of:

```js
function handleSearch(event) {
  event.preventDefault();
}
```

---

### ✅ You **can** use a normal function inside a functional component

Both work. But here's **why arrow functions are usually preferred** inside React components:

---

### 🔍 1. **Arrow functions preserve the `this` context**

Although not critical inside functional components (because `this` isn’t used like in class components), arrow functions are still safer when:

* Passing functions down as props
* Binding callbacks inside event listeners

For example, in **class components**, you'd need to bind regular functions:

```js
class App extends React.Component {
  constructor() {
    super();
    this.handleClick = this.handleClick.bind(this); // required for normal function
  }

  handleClick() {
    console.log(this); // needs binding
  }
}
```

But with arrow functions:

```js
handleClick = () => {
  console.log(this); // always works correctly
};
```

---

### ✅ 2. **Arrow functions are more concise and cleaner**

This is mostly **stylistic and modern practice**:

```js
// modern
const handleChange = (e) => {};

// older
function handleChange(e) {}
```

---

### ✅ 3. **Arrow functions avoid function hoisting confusion**

Regular functions are hoisted (you can use them before they are defined), but arrow functions are not.

So React developers prefer declaring functions using `const` before using them — **no confusion** about where the function is defined.

---

### ⚖️ Summary:

| Use Arrow Function `(e) => {}`                            | Use Normal Function `function()`    |
| --------------------------------------------------------- | ----------------------------------- |
| ✅ Inside functional components                            | ✅ OK, but less common               |
| ✅ For event handlers                                      | ✅ OK if you don’t use `this`        |
| ✅ When you want a consistent `this` (in class components) | ❌ Needs binding in class components |
| ✅ Modern & concise syntax                                 | ⚠️ Longer, old-style                |

---

💡 In your code:

```js
const handleSearch = (event) => {
  event.preventDefault();
};
```

---

### ✅ **What is `preventDefault()`?**

In JavaScript (especially in forms), some elements have **default behavior**.

For example:

* A **form** tries to **submit** and reload the page.
* A **link (`<a>`)** navigates to a new page.
* A **checkbox** toggles its check state.

> `event.preventDefault()` **stops that default behavior** from happening.

---

### 🧠 **Simple Meaning:**

> “Hey browser, don’t do what you normally do. I’ll handle it myself.”

---

### 🧪 Use Case 1: **Form Submission in React**

```jsx
function handleSubmit(event) {
  event.preventDefault(); // 🚫 stop page reload
  console.log("Form submitted!");
}

return (
  <form onSubmit={handleSubmit}>
    <button type="submit">Submit</button>
  </form>
);
```

✅ Without `preventDefault()`, the form will reload the page and you'll **lose all your React state**.

---

### 🧪 Use Case 2: **Stop a link from navigating**

```jsx
function handleClick(event) {
  event.preventDefault(); // 🚫 stop navigating
  console.log("Link was clicked, but not followed.");
}

return (
  <a href="https://example.com" onClick={handleClick}>
    Click me
  </a>
);
```

✅ Now the link won’t take you to `example.com`.

---

### 🔁 Summary Table:

| Element       | Default Behavior       | `preventDefault()`                  |
| ------------- | ---------------------- | ----------------------------------- |
| `<form>`      | Submits & reloads page | Stops form submission               |
| `<a href="">` | Goes to link           | Stops navigation                    |
| `<checkbox>`  | Toggles value          | Stops checkbox behavior (rare case) |

---

### 💬 In Your Case (Search Form):

```jsx
<form onSubmit={handleSearch}>
```

You **must** use:

```js
event.preventDefault();
```

To **prevent the form from refreshing the page** and losing your typed input.

---


