## Document Object

### 1. Where does `document` come from?

We already know this mental model:

- `window` = browser tab  
- `document` = lives inside `window`  

So technically:

    window.document

But since `document` is **global**, we usually write just:

    document

👉 `document` is **provided by the browser**, not by JavaScript itself.

---

### 2. What is the Document Object?

**Simple definition (memorize this):**

The **document object** represents the loaded HTML page and provides access to the DOM.

In simpler words:

- `document` = your webpage
- It is the **entry point** to the DOM
- Every DOM operation starts from here

---

### 3. Why `document` is so important

Without `document`:

- ❌ You cannot select elements  
- ❌ You cannot modify HTML  
- ❌ You cannot listen to DOM events  

Example:

    document.getElementById("title");

What this means:

👉 “Hey `document`, give me the element with this ID”

---

### 4. What does `document` actually contain?

`document` holds:

- The **entire DOM tree**
- Methods to:
  - Select elements
  - Create elements
  - Modify elements
- Information about the page itself

So `document` is both:
- a **representation** of the page
- a **controller** for the page

---

### 5. `document` vs DOM 

- **DOM** → the structure (tree of nodes)
- **document** → JavaScript object that represents and controls that structure

👉 Think of it like this:

DOM = building  
document = remote control for the building  

👉 `document` is the **handle** to the DOM.

---

### 6. Commonly used `document` properties

Some very important ones (just understand, no memorizing yet):

- `document.title`
- `document.body`
- `document.head`
- `document.URL`

Example:

    document.title = "New Page Title";

This **instantly changes the browser tab title**.

---

### 7. `document` methods (preview)

We’ll learn these deeply later, but for now just recognize them:

- `document.getElementById()`
- `document.querySelector()`
- `document.querySelectorAll()`

All of them:

- 👉 Start with `document`
- 👉 Reach into the DOM tree

---

### 8. `document` is also a node

Important concept 👇

- `document` itself is a **node**
- It is the **root node** of the DOM tree

So the DOM tree starts like this:

    document
     └── html
         └── body

Everything else lives under this.

---

### 9. Very common beginner mistake

❌ Thinking `document` is the HTML file

Correct understanding ✅

- HTML file → static text on disk
- `document` → live object in browser memory

When the page reloads:

- Old `document` is destroyed
- A **new `document`** is created

---

### 10. One-line mental model (lock this in)

- Window is the **browser**
- Document is the **page**
- DOM is the **structure of that page**
