## Children vs Children Nodes

### 1. Why does this topic exist?

You might naturally expect this to be true:

    element.children === element.childNodes

But that is ❌ **NOT true**.

Understanding **why** they are different will save you from **very confusing DOM bugs**.

---

### 2. What is `children`?

**Simple definition:**

`children` returns **only HTML element nodes**.

Important points:

- Ignores **text nodes**
- Ignores **comment nodes**
- Returns an **HTMLCollection**
- It is a **LIVE** collection

Example:

    element.children

👉 You get **only element elements**, nothing else.

---

### 3. What is `childNodes`?

**Simple definition:**

`childNodes` returns **ALL nodes**.

This includes:

- Element nodes  
- Text nodes (spaces, new lines)  
- Comment nodes  

Return type:

- **NodeList**
- Usually **STATIC**

Example:

    element.childNodes

👉 You get **everything the browser sees**.

---

### 4. Visual example 

HTML:

    <div>
      <p>Hello</p>
      <span>World</span>
    </div>

Visually, it looks like there are **2 children**, right?

But what the browser actually sees is:

    div
     ├── text node (newline / space)
     ├── p
     ├── text node (newline / space)
     ├── span
     ├── text node (newline / space)

👉 Line breaks and spaces are **real text nodes**.

---

### 5. Compare the results

    const div = document.querySelector("div");

    div.children.length;     // 2
    div.childNodes.length;   // 5 

Why the difference?

👉 **Whitespace counts as text nodes**.

---

### 6. Practical difference

Using `children` (safe):

    div.children[0].style.color = "red";

✔️ Works exactly as expected.

Using `childNodes` (dangerous):

    div.childNodes[0].style.color = "red"; // ❌ text node

❌ Causes errors or unexpected behavior.

---

### 7. When should you use which?

#### Use `children` when:

- You want **elements only**
- You are manipulating the UI
- In **99% of real-world cases**

#### Use `childNodes` when:

- You explicitly need **text nodes**
- Rare and advanced use cases

---

### 8. Common beginner mistake

❌ Accidentally using `childNodes`:

    element.childNodes[1].textContent = "Hi"; // unpredictable

Because indexes may point to **text nodes**, not elements.

---

### 9. One-line mental model

- `children` = **elements only**
- `childNodes` = **everything**
