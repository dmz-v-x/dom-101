# `append`, `prepend`, `before`, `after` — Placing Elements

### 1. Why placement matters

When you create an element, you must decide:

- Inside which element should it go?  
- At the start or end?  
- Before or after another element?  

DOM placement methods control exactly this.

---

### 2. `append()` — Add at the END (inside)

**Simple definition:**

`append()` inserts an element as the **last child** of a parent.

HTML:

    <ul id="list">
      <li>A</li>
    </ul>

JavaScript:

    const li = document.createElement("li");
    li.textContent = "B";

    document.getElementById("list").append(li);

Result:

    <ul>
      <li>A</li>
      <li>B</li>
    </ul>

👉 The new element is added **at the end**.

---

### 3. `prepend()` — Add at the START (inside)

**Simple definition:**

`prepend()` inserts an element as the **first child**.

JavaScript:

    list.prepend(li);

Result:

    <ul>
      <li>B</li>
      <li>A</li>
    </ul>

👉 The new element appears **at the beginning**.

---

### 4. `before()` — Add BEFORE an element (outside)

**Simple definition:**

`before()` inserts an element **before the selected element**.

HTML:

    <p id="ref">Hello</p>

JavaScript:

    ref.before(newEl);

Result:

    <p>New</p>
    <p>Hello</p>

👉 The new element is placed **outside**, before the reference element.

---

### 5. `after()` — Add AFTER an element (outside)

**Simple definition:**

`after()` inserts an element **after the selected element**.

JavaScript:

    ref.after(newEl);

Result:

    <p>Hello</p>
    <p>New</p>

👉 The new element is placed **outside**, after the reference element.

---

### 6. Visual summary

Outside the element:

    before
    [ element ]
    after

Inside the element:

    prepend
    [ children ]
    append

---

### 7. Important behavior (VERY IMPORTANT)

A DOM element can exist in **only ONE place**.

Example:

    parent.append(child);
    otherParent.append(child);

👉 The element **moves**, it is **not copied**.

This is a very common beginner confusion.

---

### 8. Common beginner mistakes

- Reusing the same element expecting duplicates  
- Expecting automatic copying  

Correct understanding:

👉 Elements are **moved**, not cloned.

To create copies, use:

    cloneNode()

(covered separately)

---

### 9. One-line mental model

- `append()` / `prepend()` → inside  
- `before()` / `after()` → outside
