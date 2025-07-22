
---

### ✅ How React Handles DOM Updates

1. **Virtual DOM & Snapshot Comparison**
   React uses a **Virtual DOM** to improve performance. Whenever there is a change in state or props, React:

   * Creates a **new virtual DOM snapshot**.
   * **Compares** it with the **previous snapshot** to detect changes.
   * Determines **what part of the real DOM** needs to be updated.

2. **Component Rendering Behavior**

   * If a component is **not affected by the update** (its props/state haven’t changed):

     * The **component function is not re-executed**.
     * React **reuses the last rendered output**.
   * If a component **is affected by the update**:

     * Its **function is re-executed** to get new JSX.
     * The new output is compared via the virtual DOM diffing process.


---

## 🧠 What is `.reduce()`?

The `reduce()` method is used to take all items in an array and reduce them to **a single value** (like a total, average, object, etc.).

---

### 🔹 Syntax:

```js
array.reduce((accumulator, currentValue) => {
  // do something
  return updatedAccumulator;
}, initialValue);
```

---

## ✅ Example 1: Add all numbers in an array

```js
const numbers = [1, 2, 3, 4];
const total = numbers.reduce((sum, num) => sum + num, 0);

console.log(total); // 10
```

### How it works:

| Step | sum | num | Result |
| ---- | --- | --- | ------ |
| 1    | 0   | 1   | 1      |
| 2    | 1   | 2   | 3      |
| 3    | 3   | 3   | 6      |
| 4    | 6   | 4   | 10     |

---

## ✅ Example 2: Find the maximum value

```js
const numbers = [5, 2, 9, 1, 7];
const max = numbers.reduce((maxSoFar, num) => {
  return num > maxSoFar ? num : maxSoFar;
}, numbers[0]);

console.log(max); // 9
```

---

## ✅ Example 3: Count how many times each word appears

```js
const fruits = ['apple', 'banana', 'apple', 'orange', 'banana'];
const count = fruits.reduce((acc, fruit) => {
  acc[fruit] = (acc[fruit] || 0) + 1;
  return acc;
}, {});

console.log(count);
// { apple: 2, banana: 2, orange: 1 }
```

---

## ✅ Example 4: Flatten a 2D array

```js
const nested = [[1, 2], [3, 4], [5]];
const flat = nested.reduce((acc, arr) => acc.concat(arr), []);

console.log(flat); // [1, 2, 3, 4, 5]
```

---

## ✅ Example 5: Create a string from an array

```js
const words = ["I", "love", "React"];
const sentence = words.reduce((acc, word) => acc + " " + word);

console.log(sentence); // "I love React"
```

---

## 🔁 In Short:

`reduce()` goes through every item in the array and lets you **carry forward a value (accumulator)** to build up a final result.

---

### 🔴 `setChosenCount(userValue)` – *Why this can be problematic*

This is a **direct update**:

```js
setChosenCount(userValue);
```

* React batches state updates.
* If you call multiple `setState` one after another, like:

  ```js
  setChosenCount(chosenCount + 1);
  setChosenCount(chosenCount + 1);
  ```

  It might **not increment twice**, because `chosenCount` may still hold the old value (not the updated one).

---

### ✅ `setChosenCount(prevValue => prevValue + 1)` – *Why this is safer and preferred*

This is an **updater function**:

```js
setChosenCount((prevValue) => prevValue + 1);
```

* It ensures React uses the **most up-to-date** state (`prevValue`) when updating.
* Works **reliably even when state updates are batched** or asynchronous.

---

### ✅ Simple analogy:

Think of `setState(value)` as saying:

> “Update the count to this specific number.”

While `setState(prev => prev + 1)` says:

> “Whatever the current count is when you process this, add 1 to it.”

---

### ✅ When is `setCount(value)` okay?

It's **totally fine** if you're:

* only calling `setState` **once**
* and don't care about **previous value**

Example:

```js
setChosenCount(10); // perfectly fine
```

But if your update **depends on the previous state**, always use the updater form.

---


   * React builds a **component tree** representing the UI.
   * It identifies the **minimal set of changes** by comparing the new virtual DOM with the old one.
   * Then, it **efficiently updates the real DOM** — only the parts that changed — without reloading the whole page.

---

