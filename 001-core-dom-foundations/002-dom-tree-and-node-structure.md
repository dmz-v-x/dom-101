## DOM Tree & Node Structure

### 1. What happens when you open a webpage?

When you type a URL and press **Enter**, the browser does many things (DNS lookup, networking, etc.),  
but **for understanding the DOM**, we only care about this part 👇

👉 The browser **receives the HTML file** from the server.

At this moment:

- The HTML is **still just plain text**
- It is **not interactive**
- JavaScript **cannot work with it yet**

So right now, the browser has only received **raw HTML text**, nothing more.

---

### 2. Browser parses the HTML

**Parsing** simply means:

> Reading something carefully and understanding its structure.

So the browser:

- Reads the HTML **from top to bottom**
- Identifies **opening tags** and **closing tags**
- Understands **nesting** (what is inside what)

Example HTML:

    <body>
      <h1>Hello</h1>
      <p>Welcome</p>
    </body>

What the browser understands:

- `<h1>` is **inside** `<body>`
- `<p>` is **also inside** `<body>`
- `<h1>` and `<p>` are **siblings**

Parsing is about **understanding relationships**, not creating visuals yet.

---

### 3. Browser converts HTML into objects

Now comes the **most important step** 👇

👉 For **every part of the HTML**, the browser creates **objects in memory**.

For example:

- `<body>` → Body element object
- `<h1>` → Heading element object
- `<p>` → Paragraph element object
- Text like `"Hello"` → Text object

These objects:

- Have **properties** (like `innerText`, `style`, `id`)
- Have **methods** (like `appendChild`, `remove`, `addEventListener`)
- Can be **accessed and modified using JavaScript**

👉 The complete collection of these objects is called the **DOM**.

-------------------------------------------------------------------------

### 4. DOM is created as a TREE

The browser does **not** store elements randomly.

It stores them in a **tree structure**, because HTML itself is nested.

Example HTML:

    <html>
      <body>
        <h1>Hello</h1>
        <p>Welcome</p>
      </body>
    </html>

Mental view of the DOM tree:

    Document
     └── html
         └── body
             ├── h1
             │    └── "Hello"
             └── p
                  └── "Welcome"

This structure is called the **DOM Tree**.

- There is **one root**
- Every node has **relationships**
- Order and nesting matter

-------------------------------------------------------------------------

### 5. What is a Node?

In the DOM:

👉 **Everything is a node**

This includes:

- HTML elements
- Text inside elements
- Comments
- The document itself

#### Common node types

1. Document node
- The **topmost node**
- Represents the **entire page**

2. Element nodes
- HTML tags like `<div>`, `<p>`, `<h1>`

3. Text nodes
- The **actual text content** inside elements

Example:

    <h1>Hello</h1>

- `<h1>` → element node
- `"Hello"` → text node

This separation is very important to understand DOM behavior later.

-------------------------------------------------------------------------

### 6. Parent, Child, and Sibling (tree relationships)

Because the DOM is a tree, nodes have **relationships**.

Example:

    <div>
      <p>Hello</p>
      <span>World</span>
    </div>

Relationships:

- `<div>` → **parent**
- `<p>` and `<span>` → **children**
- `<p>` and `<span>` → **siblings**

👉 This is why we can **navigate (traverse)** the DOM using JavaScript.

-------------------------------------------------------------------------

### 7. Why this structure is powerful

Because of this tree structure, JavaScript can:

- Find specific elements
- Move up and down the tree
- Modify only what is needed
- Avoid reloading or changing the whole page

This structure is the foundation of:

- DOM traversal
- Event bubbling and capturing
- Efficient UI updates
- How libraries like React *think* about the UI

-------------------------------------------------------------------------

### 8. One clean mental summary

    Browser receives HTML text
           ↓
    Browser parses the HTML
           ↓
    Browser creates JavaScript objects
           ↓
    Objects are organized as a tree
           ↓
    This tree is the DOM

-------------------------------------------------------------------------

### 9. Very common beginner confusion

❌ “The DOM tree exists inside the HTML file”

✅ Reality:

- HTML file → **static text on disk**
- DOM tree → **live structure in browser memory**

You can **inspect** the DOM using DevTools,  
but it does **not live inside your HTML file**.

HTML is the input.  
DOM is what the browser builds from it.
