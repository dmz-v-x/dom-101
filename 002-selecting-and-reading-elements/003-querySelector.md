## Selecting and Reading Elements - querySelector

### 1. Why do we need `querySelector`?

So far you’ve seen:

- `getElementById` → works with **id only**
- `getElementsByClassName` → works with **class only**

But real HTML is usually **more complex**:

- Nested elements
- Combinations of selectors
- Very specific targeting needs

👉 We need a **more powerful and flexible selector**.

That selector is **`querySelector`**.

---

### 2. What is `querySelector`?

**Simple definition:**

`querySelector` returns the **FIRST element** that matches a **CSS selector**.

This means:

- You are **not limited** to only id or class
- You can use **any valid CSS selector**

Syntax:

    document.querySelector("selector");

Read it like English:

👉 “Hey document, give me the first element that matches this CSS selector”

---

### 3. It uses CSS selectors 

This is the key idea.

👉 **Anything that works in CSS works here too.**

Examples:

    document.querySelector("#title");   // id selector
    document.querySelector(".item");    // class selector
    document.querySelector("p");        // tag selector
    document.querySelector("div p");    // nested selector

If you know CSS selectors, you already know how to use `querySelector`.

---

### 4. What does it return?

    const el = document.querySelector(".item");

It returns:

- ✅ **ONE element**
- ❌ NOT a list
- ❌ NOT a collection

If multiple elements match the selector:

👉 Only the **first matching element** is returned.

---

### 5. What if nothing matches?

Just like `getElementById`:

    document.querySelector(".unknown");

Return value:

    null

👉 Always be careful and assume it **might return `null`**.

---

### 6. Why is `querySelector` so popular?

Because it is:

- One method for almost everything
- Very readable
- Extremely flexible
- Works with complex DOM structures
- Used heavily in modern JavaScript

Framework mental model:

- Libraries like React internally use **similar selector logic**

---

### 7. Common beginner mistakes

❌ Forgetting `#` or `.`:

    document.querySelector("title"); 
    // selects <title> tag, NOT id="title"

❌ Expecting multiple elements:

    document.querySelector(".item").length; // ❌ undefined

👉 Remember: `querySelector` returns **only one element**.

---

### 8. Real-world example

HTML:

    <ul>
      <li class="item">A</li>
      <li class="item">B</li>
    </ul>

JavaScript:

    const firstItem = document.querySelector(".item");
    firstItem.style.color = "blue";

Result:

- Only **A** becomes blue

---

### 9. One-line mental model

`querySelector` returns the **FIRST element** that matches a **CSS selector**.
