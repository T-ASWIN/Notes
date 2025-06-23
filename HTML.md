1)link

2)iframe

3)descriptive list

4)behavior of HTML tags

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

Here’s a **short and clear explanation** of **HTML Lists**, including the description list example you shared:

---

## 🔟 HTML Lists

### ✅ 1. **Ordered List** `<ol>`

* Numbers items automatically (1, 2, 3…)

```html
<ol>
  <li>Item One</li>
  <li>Item Two</li>
</ol>
```

---

### ✅ 2. **Unordered List** `<ul>`

* Bullets before each item

```html
<ul>
  <li>Milk</li>
  <li>Eggs</li>
</ul>
```

---

### ✅ 3. **Description List** `<dl>`

Used to define **terms** and their **descriptions** (like a glossary).

```html
<dl>
  <dt>HTML</dt>
  <dd>Standard language for creating web pages.</dd>

  <dt>CSS</dt>
  <dd>Used to style and layout web pages.</dd>

  <dt>JavaScript</dt>
  <dd>Adds interactivity to websites.</dd>
</dl>
```

---

### 🧠 Tags Used in Description List

| Tag    | Meaning                         |
| ------ | ------------------------------- |
| `<dl>` | Description List (container)    |
| `<dt>` | Description Term (like a title) |
| `<dd>` | Description Details/Definition  |

---

Let me know if you'd like a visual version (image/PDF/markdown file) of this for GitHub or study notes!

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


### 🔹 HTML Registration Form 

1. **Basic Setup**

```html
<!DOCTYPE html> → Declares HTML5  
<meta charset="UTF-8"> → Supports special characters  
<meta name="viewport"> → Responsive layout  
<title>Form</title> → Page title
```

---

2. **Form Tag**

```html
<form action="./submit" method="get">
```

* `action`: Where data goes
* `method="get"`: Sends data in URL

---

3. **Input Fields**

```html
<input type="text"> → Name  
<input type="email"> → Email  
<input type="number"> → Age  
<input type="date"> → DOB  
<input type="password"> → Password  
<input type="file"> → Resume Upload
```

---

4. **Dropdowns**

```html
<select id="gender"> → Gender  
<optgroup> → Groups time slots  
<select id="time"> → Select Time
```

---

5. **Textarea**

```html
<textarea> → For 'About Yourself'
```

---

6. **Radio Buttons**

```html
<input type="radio" name="fav_language"> → Choose one language
```

---

7. **Checkboxes**

```html
<input type="checkbox" name="skills"> → Multiple skill selection
```

---

8. **Buttons**

```html
<input type="submit"> → Submit form  
<input type="reset"> → Reset form
```

---
9. **required**
this field is need to be filled

```html
required
```

---
10. **Pattern**
pattern is used to set rules to the input

```html
pattern ="[a-zA-Z .]+"
```
---
11. **Pattern in Number**

```html
pattern ="[6789]{1}[0-9]{9}"
```

---
12. **Number restriction**
set limitation to number value

```html
min ="1" max = "100"
```
---
13. **Password Restriction**

```html
minlength ="8"
```


## Example Code

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registration Form</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        table {
            margin: auto;
            padding: 40px;
            border: 2px solid #6d3434;
            border-radius: 60px;
            background-color: #d7d3d3;
        }
        td {
            padding: 10px;
        }
        h1 {
            text-align: center;
        }
        
    </style>
</head>
<body>
    <h1>Registration Form</h1>
    <form action="" method="get">
        <table>
            <tr>
                <td><label for="name">Name</label></td>
                <td><input type="text" id="name" placeholder="Enter Name" required pattern ="[a-zA-Z .]+"></td>
            </tr>
            <tr>
                <td><label for="Email">Email</label></td>
                <td><input type="email" id="Email" placeholder="Enter Email"></td>
            </tr>
            <tr>
                <td><label for="age">Age</label></td>
                <td><input type="number" id="age" placeholder="Enter age" min ="1" max = "100" value="20" read only></td>
            </tr>
            <tr>
                <td><label for="dob">Date of Birth</label></td>
                <td><input type="date" id="dob" ></td>
            </tr>
            <tr>
                <td><label for ="PhoneNumber">Phone Number</label></td>
                <td><input type ="text" id="PhoneNumber" pattern ="[6789]{1}[0-9]{9}"></td>
            </tr>
            <tr>
                <td><label for="password">Password</label></td>
                <td><input type="password" id="password" placeholder="Enter password" required minlength ="8"></td>
            </tr>
            <tr>
                <td><label for="Resume">Upload Resume</label></td>
                <td><input type="file" id="Resume"></td>
            </tr>
            <tr>
                <td><label for="gender">Gender</label></td>
                <td>
                    <select id="gender">
                        <option value="Male">Male</option>
                        <option value="Female">Female</option>
                    </select>
                </td>
            </tr>
            <tr>
                <td><label for ="range">Range</label></td>
                <td><input type ="range" id ="range"></td>
            </tr>
            <tr>
                <td><label for="message">About Yourself</label></td>
                <td><textarea id="message" rows="4" cols="40" placeholder="50 Words Minimum"></textarea></td>
            </tr>
            <tr>
                <td><label for="time">Choose Time</label></td>
                <td>
                    <select id="time" name="time">
                        <optgroup label="Morning">
                            <option value="9:00">9:00</option>
                            <option value="10:00">10:00</option>
                        </optgroup>
                        <optgroup label="Afternoon">
                            <option value="1:00">1:00</option>
                            <option value="2:00">2:00</option>
                        </optgroup>
                    </select>
                </td>
            </tr>
            <tr>
                <td>Favorite Web Language:</td>
                <td>
                    <input type="radio" id="html" name="fav_language" value="HTML">
                    <label for="html">HTML</label><br>
                    <input type="radio" id="css" name="fav_language" value="CSS">
                    <label for="css">CSS</label><br>
                    <input type="radio" id="javascript" name="fav_language" value="JavaScript">
                    <label for="javascript">JavaScript</label>
                </td>
            </tr>
            <tr>
                <td>Select The Skills You Know:</td>
                <td>
                    <input type="checkbox" id="github" name="skills" value="github">
                    <label for="github">GitHub</label><br>
                    <input type="checkbox" id="Communication" name="skills" value="Communication">
                    <label for="Communication">Communication</label><br>
                    <input type="checkbox" id="Apptitude" name="skills" value="Apptitude">
                    <label for="Apptitude">Aptitude</label>
                </td>
            </tr>
            <tr>
                <td >
                    <input type="submit" value="Submit">
                    <input type="reset" value="Reset Form">
                </td>
            </tr>
        </table>
    </form>
</body>
</html>

```
---

### ✅ 1. `readonly`

* 🟢 **What it does:** You can see and **copy** the input, but **can’t change** it.
* 🧠 **Use it when**: You want to show a value that the user should **not edit**, like a generated ID.

```html
<input type="text" value="Read Only Name" readonly>
```

---

### ✅ 2. `hidden`

* 🟢 **What it does:** Completely **hides** the element from the page.
* 🧠 **Use it when**: You want to store data that should not be seen (e.g., user ID).

```html
<input type="text" value="Hidden Data" hidden>
```

> 📌 Note: It's not shown on the page, but its value can still be submitted with the form.

---

### ✅ 3. `disabled`

* 🟢 **What it does:** Input is **grayed out**, and you **can’t click, type, or submit** it.
* 🧠 **Use it when**: The option is **temporarily unavailable**.

```html
<input type="text" value="Disabled Input" disabled>
```

> ❗ Note: Unlike `readonly`, `disabled` inputs **do not get submitted** in a form.

---

### 🟨 Summary Table:

| Attribute  | Visible?       | Editable? | Submittable? |
| ---------- | -------------- | --------- | ------------ |
| `readonly` | ✅ Yes          | ❌ No      | ✅ Yes        |
| `hidden`   | ❌ No           | ❌ No      | ✅ Yes        |
| `disabled` | ✅ Yes (grayed) | ❌ No      | ❌ No         |

---

### ✅ 1. `<nav>` – Navigation

* 🟢 **Used for:** Menus or links to move around the website
* 🧠 **Think of:** A navbar or sidebar with links

```html
<nav>
  <a href="#home">Home</a> |
  <a href="#about">About</a> |
  <a href="#contact">Contact</a>
</nav>
```

---

### ✅ 2. `<header>` – Top Section

* 🟢 **Used for:** Page or section titles, logos, or top content
* 🧠 **Think of:** The top part of a page like a newspaper headline

```html
<header>
  <h1>My Blog</h1>
  <p>Welcome to my website</p>
</header>
```

---

### ✅ 3. `<section>` – Group of Content

* 🟢 **Used for:** Dividing content into sections by topic
* 🧠 **Think of:** Each chapter in a book

```html
<section>
  <h2>Services</h2>
  <p>We offer web design, SEO, and development.</p>
</section>
```

---

### ✅ 4. `<article>` – Independent Content

* 🟢 **Used for:** Standalone content like blog posts, news, reviews
* 🧠 **Think of:** A full blog post or news article

```html
<article>
  <h2>Tips to Learn HTML</h2>
  <p>Start with basic tags like p, h1, and img...</p>
</article>
```

---

### ✅ 5. `<footer>` – Bottom Section

* 🟢 **Used for:** Copyright info, contact links, or social media
* 🧠 **Think of:** The bottom of a newspaper or website

```html
<footer>
  <p>&copy; 2025 My Website. All rights reserved.</p>
</footer>
```

---

### 📌 Summary Table:

| Tag         | Purpose                  | Real-World Meaning     |
| ----------- | ------------------------ | ---------------------- |
| `<nav>`     | Navigation links         | Table of contents/menu |
| `<header>`  | Top section/title/logo   | Newspaper heading      |
| `<section>` | Logical block of content | Book chapter           |
| `<article>` | Self-contained content   | Blog/news post         |
| `<footer>`  | Bottom info or links     | Page footer            |

---

### ✅ `<aside>` – **Side Content**

---

#### 🔹 **What it does:**

The `<aside>` tag is used to show **extra content** that is **related but not essential** to the main content.

---

#### 🧠 **Think of it like:**

> A **sidebar** on a blog or news website that shows ads, tips, author info, or links to related articles.

---

### 🧾 Example:

```html
<main>
  <article>
    <h2>How to Learn HTML</h2>
    <p>Start by understanding the basic tags like p, h1, a, and img...</p>
  </article>

  <aside>
    <h3>Related Tips</h3>
    <ul>
      <li><a href="#">Best HTML editors</a></li>
      <li><a href="#">Top HTML interview questions</a></li>
    </ul>
  </aside>
</main>
```

---

### ✅ Summary:

| Tag       | Purpose                     | Where it's used                    |
| --------- | --------------------------- | ---------------------------------- |
| `<aside>` | Shows extra or side content | Sidebars, tips, related links, ads |

---

### 1️⃣ **Inline Elements**

* 👀 Only take up as much **width as needed**
* 🧱 Appear **next to each other** (in the same line)
* 🎯 Example: `<a>`, `<span>`, `<strong>`, `<img>`

```html
<p>This is <strong>inline</strong> text.</p>
```

➡️ The word **"inline"** appears on the **same line** as the rest of the text.

---

### 2️⃣ **Block Elements**

* 📦 Take up **full width** of the page
* 📥 Always start on a **new line**
* 🧱 Example: `<div>`, `<p>`, `<h1>` to `<h6>`, `<section>`

```html
<p>This is a paragraph.</p>
<p>This is another one.</p>
```

➡️ Each paragraph appears on a **new line**.

---

### 3️⃣ **Self-Closing Tags**

* ✂ No separate closing tag
* ✅ Often used for elements that **don’t hold content**
* 🧱 Example: `<img>`, `<br>`, `<hr>`, `<input>`

```html
<img src="cat.jpg" alt="cat">
<br>
<hr>
```

➡️ These tags are **short** and **stand alone**.

---

### 4️⃣ **Open and Closing Tags**

* 🧩 Most elements need an **opening and closing pair**
* 📦 Closing tag has a **slash `/`**
* 🧱 Example: `<p>content</p>`, `<h1>title</h1>`

```html
<p>This is a paragraph.</p>
```

---

### 📝 Summary Table

| Type             | Tag Format               | Example               |
| ---------------- | ------------------------ | --------------------- |
| Inline Element   | On the same line         | `<a>Link</a>`         |
| Block Element    | Starts on new line       | `<div>Box</div>`      |
| Self-Closing Tag | No content inside        | `<img src="cat.jpg">` |
| Open/Close Tag   | Opening + closing needed | `<p>Text</p>`         |

---
