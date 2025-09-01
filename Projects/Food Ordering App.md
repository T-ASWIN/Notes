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

