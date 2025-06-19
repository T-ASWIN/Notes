
---

### 🛠 Fixing Your Code:

1. **Color Comparison Error**
   You're checking `selectedColor === green`, but `green` is not defined.
   👉 Hint: Use string literals for color names (e.g., `'green'` instead of `green`).

2. **`if else` Syntax Issue**
   Your `if else` statements are not valid JavaScript.
   👉 Hint: The correct syntax is `else if`, not `if else`.

3. **Invalid `style` Prop**
   You're using `style={text-color:{value}}`, which is not valid JSX.
   👉 Hint: The `style` prop takes an object. Use camelCase for CSS properties like `color`.

4. **Casing Mismatch**
   You’re passing `value` to `Test1Child`, but it's not used inside.
   👉 Hint: You don’t actually need to pass `value` unless you're using it inside the child.

5. **Capitalization in Options**
   You're comparing `'Green'`, `'Red'`, etc., but setting the state as lowercase `'green'` etc.
   👉 Hint: Make sure the case matches when comparing strings.


---

### ✅ **When to use props**

#### 1. **Passing value from Parent ➝ Child:**

You use **props** when the **parent** wants to send data or functions to the **child**.

**Example:**

```jsx
<Child username="Aswin" />
```

Here, `username` is a prop. The child can now use it like:

```jsx
function Child({ username }) {
  return <p>{username}</p>;
}
```

---

### ❌ **Unnecessary prop**

If the **child** does not use a prop (like `value` in your code), **you don't need to pass it**.

---

### 🔁 **Sending value from Child ➝ Parent**

To send data **from child to parent**, you don’t need to pass a value —
You pass a **function as a prop** from the parent, and the child **calls** that function with the data.

**Example:**

```jsx
// Parent
<Test1Child onColorSelect={handleColorSelect} />
```

```jsx
// Child
<select onChange={(e) => onColorSelect(e.target.value)}></select>
```

Here, `onColorSelect` is a function passed as a prop from parent, and the child is giving data *back* to the parent by calling it.

---

### ✅ Final Rule:

* ✅ **Use props** when: Parent ➝ Child (data or function)
* ✅ **Use callback functions** (passed as props) when: Child ➝ Parent (data via function)
* ❌ Don’t pass props if the child doesn’t use them



