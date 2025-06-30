
---

## 🔄 What is `onChange`?

`onChange` is an **event handler** in React.
It runs **whenever a form input changes** — like:

* Typing in a text box
* Selecting a radio button
* Choosing from a dropdown

---

## 🧠 What’s happening in your example?

You're using **React state** to:

1. Store the name typed into the input box ✅
2. Store the selected shipping option (radio button) ✅

---

## ✍️ Let's break your code

### ✅ 1. `useState` — creating memory

```js
const [name, setName] = useState();
const [shipping, setShipping] = useState();
```

React creates two pieces of memory:

* One to store the `name`
* One to store the `shipping` method

---

### ✅ 2. `handleClick` — when typing in the input

```js
function handleClick(event) {
  setName(event.target.value);
}
```

Every time you type something, this function runs:

* `event.target.value` gives you what you typed
* `setName(...)` saves it into the `name` state

---

### ✅ 3. Text Input

```jsx
<input value={name} onChange={handleClick} />
```

* `value={name}`: This shows whatever is stored in `name` inside the input box.
* `onChange={handleClick}`: Every time you type, it runs `handleClick` to update the state.

---

### ✅ 4. Showing name in UI

```jsx
<p>Name: {name}</p>
```

* Displays the current value of `name` on screen.

---

### ✅ 5. Radio Buttons

```jsx
<label>
  <input 
    type="radio" 
    value="Pick up" 
    checked={shipping === "Pick up"} 
    onChange={handleShipping}
  />
  Pick up
</label>
```

```jsx
<label>
  <input 
    type="radio" 
    value="Delivery" 
    checked={shipping === "Delivery"} 
    onChange={handleShipping}
  />
  Delivery
</label>
```

### 🔍 What happens here?

* User selects **one option**
* `onChange={handleShipping}` runs
* Inside `handleShipping`, you do:

  ```js
  setShipping(event.target.value);
  ```

  → This saves either `"Pick up"` or `"Delivery"` to state
* `checked={shipping === "Pick up"}` makes sure only the selected one is marked ✅

---

### 🧠 Final Simple Summary

| Element                   | What it does                              |
| ------------------------- | ----------------------------------------- |
| `onChange`                | Runs when user types or selects something |
| `event.target.value`      | Gets the typed/selected value             |
| `setName` / `setShipping` | Saves the value into state                |
| `value={state}`           | Keeps the input in sync with the state    |
| `checked={...}`           | Checks if radio button should be selected |

---

### ✅ Output Example:

If you:

* Type `"Aswin"` in the input → screen shows: `Name: Aswin`
* Select `"Delivery"` → only that radio button is selected

---
