
---

### 🔁 React Context Recap

In React, **Context** lets you share data (like theme, user info, or cart) across components **without passing props** at every level.

You create context like this:

```js
const MyContext = React.createContext("default value");
```

---

### 🧠 What does this line do?

```js
React.createContext("default value");
```

It sets the **default value** of the context to `"default value"`.

---

### ✅ Now the key point you asked about:

> "The default value is only used if a component is **not wrapped** with the provider."

---

### 💡 Simple Example:

```jsx
const MyContext = React.createContext("default value");

function MyComponent() {
  const value = React.useContext(MyContext);
  return <p>{value}</p>;
}
```

Now look at two different cases:

---

#### ✅ Case 1: **With Provider**

```jsx
<MyContext.Provider value="real value">
  <MyComponent />
</MyContext.Provider>
```

👉 Output: `real value`
Because `MyComponent` is wrapped inside the provider, it uses the provided value.

---

#### ❌ Case 2: **Without Provider**

```jsx
<MyComponent />
```

👉 Output: `default value`
Because `MyComponent` is **not wrapped** in `<MyContext.Provider>`, it uses the **default value** set in `createContext`.

---

### 🎯 Final Summary (in one line):

> The default value is only used when no `<Provider>` is wrapping the component trying to read the context.


---

## ✅ **10) Standard = useContext, Alternative = `<CartContext.Consumer>`**

### 🔁 What's the difference?

1. **Standard (modern)**:

```js
const cart = useContext(CartContext);
```

2. **Alternative (older)**:

```jsx
<CartContext.Consumer>
  {(cart) => <h1>{cart}</h1>}
</CartContext.Consumer>
```

---

### ⚠️ Why use `<Consumer>`?

* Useful in **class components** (because `useContext()` only works in **function components**).
* Sometimes used when you want **more control or nesting multiple contexts**.

---

### ✅ Full Example:

```jsx
<CartContext.Consumer>
  {(cart) => (
    <div>
      <h2>Items in Cart: {cart.length}</h2>
      {/* You can pass `cart` to other child components here */}
    </div>
  )}
</CartContext.Consumer>
```

---

## ✅ Summary Table:

| Feature                      | `useContext`                 | `<Context.Consumer>`                 |
| ---------------------------- | ---------------------------- | ------------------------------------ |
| Syntax                       | `const value = useContext()` | Function as a child (`render props`) |
| Works in Function Components | ✅                            | ✅                                    |
| Works in Class Components    | ❌                            | ✅                                    |
| Recommended                  | ✅ (modern standard)          | ⛔ (legacy/when needed)               |

---


