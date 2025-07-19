Memoization is essentially just caching. Imagine a complex function that is slow to run which takes a as an argument. In order to speed up this function, you can cache the results of running the function so that when the function is run with the same inputs you can use the cached value instead of recomputing the value. This would look something like this.
---

## 🧠 Concepts Explained

### 1. `React.memo(Component)`

* **What it does**: Prevents re-rendering of a component **if props haven’t changed**.
* **Used for**: Functional components that receive props.
* **How it works**: Compares **previous props** with **new props** using shallow comparison.
* **Useful when**: Component renders are expensive, and props don’t change frequently.

✅ Prevents unnecessary re-renders
❌ Adds prop comparison overhead (avoid for fast-changing props)

#### ✅ Syntax:

```jsx
const MyComponent = React.memo(function MyComponent(props) {
  return <div>{props.name}</div>;
});
```

---

### 2. `useMemo(() => computeFn, [deps])`

* **What it does**: Caches a **computed value** unless dependencies change.
* **Used for**: Expensive computations you don’t want to repeat on every render.

✅ Avoids recalculating on every render
❌ Don’t use if computation is cheap

#### ✅ Syntax:

```jsx
const expensiveValue = useMemo(() => computeExpensive(number), [number]);
```

---

### 3. `useCallback(() => fn, [deps])`

* **What it does**: Caches a **function reference** unless dependencies change.
* **Used for**: Passing stable functions to memoized components or useEffect.

✅ Prevents child components from re-rendering due to new function reference
❌ Useless if you’re not passing the function as a prop

#### ✅ Syntax:

```jsx
const handleClick = useCallback(() => {
  console.log("Clicked");
}, []);
```

---

## ✅ Your Code Breakdown

```js
const initialCountIsPrime = useMemo(
  () => isPrime(initialCount),
  [initialCount]
);
```

* 🧠 This avoids re-running `isPrime()` unless `initialCount` changes.
* ✅ Good usage — `isPrime()` is an **expensive calculation**.

---

```js
const handleDecrement = useCallback(function handleDecrement() {
  setCounter((prevCounter) => prevCounter - 1);
}, []);
```

* 🧠 This keeps `handleDecrement` the **same across renders**, unless dependencies change.
* ✅ Useful if `IconButton` is wrapped in `memo`.

---

> ❗ You're not using `React.memo()` here, but commented it:

```js
// const Counter = memo(
```

If you uncomment that and wrap `Counter`, it’ll **only re-render when `initialCount` changes** — assuming no internal state triggers render.

```js
export default memo(Counter);
```

---

## 🧪 When & Where to Use

| Hook            | Use Case Example                               | Good For                                       |
| --------------- | ---------------------------------------------- | ---------------------------------------------- |
| `memo()`        | Prevent re-render of `<ListItem item={...} />` | Component only changes on props                |
| `useMemo()`     | Caching a filtered/processed array             | Expensive calculations                         |
| `useCallback()` | Stable `onClick`, `onChange` handlers          | Prevent child rerenders or in `useEffect` deps |

---

### 🧰 Example: `useMemo` in a Filter

```jsx
const filteredUsers = useMemo(() => {
  return users.filter((user) => user.name.includes(search));
}, [search, users]);
```

---

### 🧰 Example: `memo()` with Child Component

```jsx
const ProductItem = React.memo(function ProductItem({ name }) {
  console.log("Rendered:", name);
  return <div>{name}</div>;
});
```

Used in parent:

```jsx
<ProductItem name="Laptop" />
```

---

### 🧰 Example: `useCallback` with `memo`

```jsx
const handleBuy = useCallback(() => {
  addToCart(productId);
}, [productId]);

<ProductItem name="Laptop" onBuy={handleBuy} />
```

Avoids creating a new `onBuy` function on every render.

---

## 🧠 Key Rules Recap

| Rule                                                              | Why                                                   |
| ----------------------------------------------------------------- | ----------------------------------------------------- |
| Don’t wrap everything with `memo()`                               | Adds unnecessary prop comparisons                     |
| Only use `useMemo()` for expensive calculations                   | Otherwise adds complexity without benefit             |
| Use `useCallback()` when passing functions to memoized components | Prevents re-render from new function reference        |
| Don’t memoize components with fast-changing props                 | `memo` will always compare and re-render anyway       |
| Use profiler to measure whether optimization helps                | Optimization without measurement can harm performance |

---

## ✅ Final Thoughts

In your code:

* `useMemo` is **correctly used** to avoid recalculating primality.
* `useCallback` is **well used** for stable event handlers.
* You could **wrap the component in `memo()`** if it doesn’t re-render based on external parent state.

---

## 🧠 `useMemo` vs `useCallback`

| Feature     | `useMemo`                                       | `useCallback`                                 |
| ----------- | ----------------------------------------------- | --------------------------------------------- |
| ✅ Purpose   | Caches a **computed value**                     | Caches a **function definition**              |
| 🔁 Returns  | A **value** (e.g., array, object, number, etc.) | A **function**                                |
| 📦 Use case | Expensive calculations                          | Prevent re-creating functions on every render |
| 🧠 Prevents | Unnecessary recalculations                      | Unnecessary re-renders in child components    |
| 📌 Syntax   | `useMemo(() => compute(), [deps])`              | `useCallback(() => fn(), [deps])`             |

---

## ✅ Example 1: `useMemo` (for values)

```jsx
const sortedList = useMemo(() => {
  return items.sort((a, b) => a - b);
}, [items]);
```

* `useMemo` **avoids sorting again** if `items` hasn’t changed.

---

## ✅ Example 2: `useCallback` (for functions)

```jsx
const handleClick = useCallback(() => {
  console.log("Clicked!");
}, []);
```

* `useCallback` returns the **same function reference** across renders (unless deps change).
* Helps if you're passing this to a memoized child component (to avoid its re-render).

---

## 🧪 Real Use Case in a Component

```jsx
const filteredItems = useMemo(() => {
  return items.filter(item => item.includes(search));
}, [items, search]);

const handleSearchChange = useCallback((event) => {
  setSearch(event.target.value);
}, []);
```

* `useMemo` here avoids re-filtering `items` unnecessarily.
* `useCallback` ensures `handleSearchChange` remains the **same function** across renders — useful if passed to a memoized `<SearchInput />`.

---

## 🧠 Simple Rule

| Goal                                             | Hook          |
| ------------------------------------------------ | ------------- |
| 🧮 Cache a value (number, array, object, etc.)   | `useMemo`     |
| 🖱️ Cache a function (event handlers, callbacks) | `useCallback` |

---

