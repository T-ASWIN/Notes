

## 🌐 HTML & Web Essentials

### 1️⃣ Anchor Tags and `href`

* `<a>` stands for **anchor**.
* `href` is the **hypertext reference** (destination URL).

```html
<a href="https://example.com">Visit Site</a>
```


### 2️⃣ `<pre>` Tag

Displays **preformatted** text exactly as written:

```html
<pre>
  Line 1
  Line 2
</pre>
```

---

### 3️⃣ 🔍 How a Search Engine Works

```
User Types a Query
        ↓
Search Engine Receives Query
        ↓
┌─────────────┐
│  Crawling   │  ← Bots visit websites
└─────────────┘
        ↓
┌─────────────┐
│  Indexing   │  ← Organizing data
└─────────────┘
        ↓
┌──────────────┐
│  Ranking     │  ← Algorithms rank results
└──────────────┘
        ↓
┌────────────────────┐
│ Results Displayed  │  ← SERP (Results Page)
└────────────────────┘
        ↓
User Clicks a Result
```

---

### 4️⃣ Domain & TLDs

A **domain name** is the address of a website (like `google.com`).

#### Top-Level Domains:

| TLD    | Description              | Example          |
| ------ | ------------------------ | ---------------- |
| `.com` | Commercial               | `google.com`     |
| `.org` | Non-Profit Organization  | `wikipedia.org`  |
| `.net` | Network services         | `slideshare.net` |
| `.edu` | Educational Institutions | `mit.edu`        |
| `.gov` | Government               | `nasa.gov`       |
| `.in`  | India-based              | `nic.in`         |
| `.uk`  | UK-based                 | `bbc.co.uk`      |

---

### 5️⃣ HTML Form Example

```html
<form action="/submit" method="post">
  <label for="name">Name</label>
  <input type="text" id="name" name="name" placeholder="Enter name"><br><br>

  <label for="email">Email</label>
  <input type="email" id="email" name="email" placeholder="Enter email"><br><br>

  <label for="password">Password</label>
  <input type="password" id="password" name="password" required><br><br>

  <label for="phone">Phone</label>
  <input type="tel" id="phone" name="phone"><br><br>

  <button type="submit">Submit</button>
</form>
```

---

### 6️⃣ CSS Properties

| Property                    | Description                    |
| --------------------------- | ------------------------------ |
| `color`                     | Text color                     |
| `background-color`          | Background color               |
| `padding`                   | Space **inside** the element   |
| `margin`                    | Space **outside** the element  |
| `border`                    | Outline around elements        |
| `text-align`                | Text alignment                 |
| `font-size` / `font-weight` | Size / boldness of text        |
| `text-decoration`           | Underline, strikethrough, etc. |
| `border-radius`             | Rounds corners                 |
| `cursor`                    | Mouse pointer on hover         |

#### Cursor Values

| Value         | Effect                |
| ------------- | --------------------- |
| `pointer`     | Hand icon             |
| `text`        | Text selection cursor |
| `move`        | Move symbol           |
| `not-allowed` | Blocked symbol        |

#### Example:

```css
a:hover {
  color: red;
  background-color: yellow;
}
```

---

### 7️⃣ Metadata

* Meta = **data about data**
* `<meta>` is used in the `<head>` for SEO, charset, viewport, etc.

---

### 8️⃣ Favicon

```html
<link rel="icon" href="favicon.png" type="image/x-icon">
```

---

### 9️⃣ Units: `rem`, `em`, `%`, `px`

* `%` — use mostly for width (not recommended for height)
* `rem` / `em` — scalable font sizing
* `px` — fixed pixel size

---

### 🔗 Anchor Tag for Same Page Navigation

```html
<a href="#section-id">Go to Section</a>
...
<h2 id="section-id">Target Section</h2>
```

Use `target="_blank"` to open in a new tab.

---

### 10️⃣ Lists

* **Ordered List `<ol>`**
* **Unordered List `<ul>`**
* **Description List:**

```html
<dl>
  <dt>HTML</dt>
  <dd>Markup language</dd>
</dl>
```

---

### 11️⃣ Media Tags

* `<img>` — Images
* `<video>` — Video
* `<audio>` — Audio
* `<iframe>` — Embed websites or YouTube
* `<picture>` — Responsive images with media types

---

### 12️⃣ Attribute Reference

| Attribute | Purpose                          |
| --------- | -------------------------------- |
| `rel`     | Relation (e.g. stylesheet, icon) |
| `href`    | Hyperlink Reference              |

---

### 13️⃣ GET vs POST

| Method | Description                                  |
| ------ | -------------------------------------------- |
| `GET`  | Sends data via **URL** (limited data)        |
| `POST` | Sends data via **body** (secure, large data) |

---

## ✅ Bonus Tips

* `lorem100` → Generates 100 random placeholder words in VS Code.
* `<center>` (HTML4) → Avoid; use CSS instead.
* Use `script` tag for JavaScript.
* Scale in `<meta>` controls zoom on mobile.

---
