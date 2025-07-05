
---

## 🔍 `find()` vs `findIndex()` in JavaScript

| Method        | What it returns                                  | Use case                                      |
| ------------- | ------------------------------------------------ | --------------------------------------------- |
| `find()`      | The **actual element** that matches              | When you want to **access** the item          |
| `findIndex()` | The **index (position)** of the matching element | When you want to **modify** or **replace** it |

---

### ✅ 1. `find()`

```js
const result = array.find((item) => item.id === 'p1');
```

🔹 **Returns the object/item itself**

```js
{
  id: 'p1',
  title: 'T-shirt',
  price: 499
}
```

📌 Use it when you **want to read** or use the item directly.

---

### ✅ 2. `findIndex()`

```js
const index = array.findIndex((item) => item.id === 'p1');
```

🔹 **Returns the position** of that item in the array:

```js
2  // for example, if 'p1' is at index 2
```

📌 Use it when you need to **update**, **replace**, or **remove** the item using array methods like:

```js
array[index] = updatedItem;
array.splice(index, 1);
```

---

### 🧾 Example

```js
const products = [
  { id: 'p1', title: 'T-shirt' },
  { id: 'p2', title: 'Jeans' },
  { id: 'p3', title: 'Cap' },
];

// find() → gives the item
const product = products.find((item) => item.id === 'p2');
// result: { id: 'p2', title: 'Jeans' }

// findIndex() → gives the index
const index = products.findIndex((item) => item.id === 'p2');
// result: 1
```

---

## 🧠 Summary

| Feature      | `find()`                 | `findIndex()`                |
| ------------ | ------------------------ | ---------------------------- |
| Returns      | Matching **element**     | Matching **index** (number)  |
| Use when     | You need the item itself | You need to change/remove it |
| Returns `-1` | If no match found        | Same behavior                |

---

