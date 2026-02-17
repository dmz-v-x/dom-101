## `data-*` Attributes — Storing Custom Data in HTML

### 1. What problem do data-* attributes solve?

Consider this HTML:

    <button>Delete</button>

Question:

How does JavaScript know what to delete?

Common incorrect solutions:

- Using IDs everywhere  
- Parsing text content  
- Hidden inputs  
- Custom non-standard attributes  

These approaches quickly become fragile and hard to maintain.

---

### 2. What are data-* attributes?

Simple definition (memorize this):

`data-*` attributes are custom attributes designed specifically for storing data in HTML.

Syntax:

    data-anything="value"

Example:

    <button data-id="42" data-role="admin">Delete</button>

Important:

- Fully valid HTML  
- Browser-supported  
- No hacks required  

---

### 3. Why data-* attributes are special

`data-*` attributes are:

- Officially supported by HTML  
- Safe and predictable  
- Readable and maintainable  
- Designed for DOM ↔ JavaScript communication  

This is the correct way to attach metadata to elements.

---

### 4. Reading data-* using getAttribute()

    const btn = document.querySelector("button");

    btn.getAttribute("data-id");   // "42"
    btn.getAttribute("data-role"); // "admin"

Important:

Values are always returned as strings.

---

### 5. Real-world usage with event delegation

HTML:

    <ul id="users">
      <li data-id="1">Alice</li>
      <li data-id="2">Bob</li>
    </ul>

JavaScript:

    users.addEventListener("click", (e) => {
      if (e.target.tagName === "LI") {
        console.log("User ID:", e.target.getAttribute("data-id"));
      }
    });

Why this pattern is powerful:

- One listener handles many elements  
- Each element carries its own data  
- No complex mapping logic required  

---

### 6. Naming rules (Important)

Valid examples:

    data-user-id
    data-product-name

Invalid example:

    dataUserId

Rules:

- Must be lowercase  
- Use hyphens  

---

### 7. When should you use data-* attributes?

Use data-* when:

- You need element-specific data  
- You want clean DOM ↔ JavaScript communication  
- You are building dynamic interfaces  

Avoid when:

- Data belongs purely in JavaScript state  

---

### 8. Common beginner mistakes

Incorrect:

    <button userid="1">

Correct:

    <button data-id="1">

---

Incorrect assumption:

    "42" ≠ 42

If needed:

    Number(element.getAttribute("data-id"))

---

### 9. One-line mental model

data-* attributes are the standard way to store custom data in HTML.
