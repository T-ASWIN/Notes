function cartReducer(state, action) {
  // Checks if the action is to add an item
  if (action.type === "ADD_ITEM") {
    // Finds the index of the item in the cart (if it already exists)
    const existingCartItemIndex = state.items.findIndex(
      (item) => item.id === action.item.id
    );
    // Makes a copy of the current items array
    const updatedItems = [...state.items];

    // If the item is already in the cart
    if (existingCartItemIndex > -1) {
      // Gets the existing item
      const existingItem = state.items[existingCartItemIndex];
      // Creates a new item object with increased quantity
      const updatedItem = {
        ...existingItem,
        quantity: existingItem.quantity + 1,
      };
      // Updates the item in the copied array
      updatedItems[existingCartItemIndex] = updatedItem;
    } else {
      // If the item is not in the cart, adds it with quantity 1
      updatedItems.push({ ...action.item, quantity: 1 });
    }
    // Returns the new state with the updated items array
    return { ...state, items: updatedItems };
  }

  // Checks if the action is to remove an item (not implemented yet)
  if (action.type === "REMOVE_ITEM") {
  }
  // Returns the current state if no action matches
  return state;
}


---

### 🔹 Case 1: Using `a`

If you just put `a` inside an array, the **entire array becomes one element**.

```js
const a = [1, 2, 3];
const c = [a, 4];
console.log(c); 
// [[1, 2, 3], 4]  
// Notice: a is nested as a single array element
```

So here, `c[0]` is the whole array `[1, 2, 3]`.

---

### 🔹 Case 2: Using `...a`

When you use the spread operator (`...a`), it **unpacks** the elements of `a` and places them individually into the new array.

```js
const a = [1, 2, 3];
const c = [...a, 4];
console.log(c);
// [1, 2, 3, 4]  
// Elements of a are spread out
```

Now `c[0]` is `1`, not `[1,2,3]`.

---

### ✅ Summary

* `a` → puts the **whole array** as a single item inside another array.
* `...a` → spreads/unpacks the **elements of the array** into the new array.

---

👉 A good way to remember:

* `a` → "keep it as it is"
* `...a` → "open the box and take everything out"


---

### 🔹 Case 1: Using `obj` directly

If you just put `obj` inside another object, it becomes a **property with the object inside**:

```js
const obj = { name: "Aswin", age: 22 };

const c = { obj, city: "Tirupur" };

console.log(c);
// {
//   obj: { name: "Aswin", age: 22 },  
//   city: "Tirupur"
// }
```

👉 Here, `obj` is nested as a whole object under the key `obj`.

---

### 🔹 Case 2: Using `{...obj}`

When you spread `obj`, it **copies its key–value pairs** into the new object:

```js
const obj = { name: "Aswin", age: 22 };

const c = { ...obj, city: "Tirupur" };

console.log(c);
// {
//   name: "Aswin",
//   age: 22,
//   city: "Tirupur"
// }
```

👉 Here, the keys of `obj` (`name`, `age`) are directly added to `c`.

---

### ✅ Summary

* `obj` → keeps the whole object as **one nested property**.
* `{...obj}` → unpacks all properties of `obj` into the new object (shallow copy).

---

⚡ Extra tip: If the same key exists in both objects, the **last one wins**:

```js
const obj1 = { name: "Aswin", age: 22 };
const obj2 = { age: 23, city: "Tirupur" };

const c = { ...obj1, ...obj2 };

console.log(c);
// { name: "Aswin", age: 23, city: "Tirupur" }
```

Here, `age: 22` from `obj1` got overwritten by `age: 23` from `obj2`.

---


---

### 🔹 What is `reduce()`?

`reduce()` is an **array method** in JavaScript that takes all the values in an array and **reduces them into a single result** (number, string, object, etc.).

It works like this:

```js
array.reduce((accumulator, currentValue) => {
  // combine accumulator and currentValue
  return updatedValue;
}, initialValue);
```

* **accumulator** → stores the running total/result.
* **currentValue** → the current element in the array.
* **initialValue** → the starting value for the accumulator.

---

### 🔹 Simple Example

Count the sum of numbers:

```js
const numbers = [1, 2, 3, 4];

const sum = numbers.reduce((acc, curr) => {
  return acc + curr;
}, 0);

console.log(sum); // 10
```

👉 Flow:

* Start with `acc = 0`
* (0 + 1) → 1
* (1 + 2) → 3
* (3 + 3) → 6
* (6 + 4) → 10 ✅

---

### 🔹 Your Example (Cart Items)

```js
const totalCartItems = cartCtx.items.reduce((totalNumberOfItems, item) => {
  return totalNumberOfItems + item.quantity;
}, 0);
```

👉 Imagine your cart looks like this:

```js
cartCtx.items = [
  { name: "Burger", quantity: 2 },
  { name: "Pizza", quantity: 1 },
  { name: "Coke", quantity: 3 }
];
```

**Step by step reduce:**

* Start: `totalNumberOfItems = 0`
* Add Burger (2) → 0 + 2 = 2
* Add Pizza (1) → 2 + 1 = 3
* Add Coke (3) → 3 + 3 = 6

✅ Final result: `6`

So it gives you **total items in the cart**.

---

### 🔹 Real-world Use Cases of `reduce()`

1. **Sum of numbers** → `reduce` is great for totals.
2. **Counting items** → e.g., cart items in your code.
3. **Flattening arrays** → `[[1,2],[3,4]] → [1,2,3,4]`.
4. **Grouping data** → count how many times each item appears.
5. **Building objects** → transform arrays into objects.

---

⚡In short:
👉 `reduce()` = a smart way to loop through an array and build **one final value** from it.

