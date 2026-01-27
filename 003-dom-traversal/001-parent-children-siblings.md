### 1. What does “DOM traversal” mean?

**Traversal** simply means:

- Moving around the **DOM tree**

Because the DOM is a tree, you can move:

- **Up** → to a parent  
- **Down** → to children  
- **Sideways** → to siblings  

👉 This movement is called **DOM traversal**.

---

### 2. Why traversal is needed

Very often:

- You select **one element**
- But you need to reach **related elements**

Example scenario:

- User clicks a button  
- You find its **parent card**
- You update something **inside that card**

👉 Traversal makes this possible.

---

### 3. Parent in the DOM

**Parent** = the element directly above another element.

HTML:

    <div class="card">
      <h2>Title</h2>
    </div>

JavaScript:

    const heading = document.querySelector("h2");
    heading.parentElement;

Result:

👉 `<div class="card">`

---

### 4. Children in the DOM

**Children** = elements directly inside another element.

JavaScript:

    const card = document.querySelector(".card");
    card.children;

Important points about `children`:

- It is a **property** of an element
- It returns an **HTMLCollection**
- It contains **only element nodes**
- No text nodes, no comments
- It is **live** (updates if DOM changes)

👉 The HTMLCollection here comes from `children`, not from `querySelector`.

Return value:

👉 **HTMLCollection of child elements**

Example:

    card.children[0]; // <h2>

---

### 5. Siblings in the DOM

**Siblings** = elements on the same level under the same parent.

HTML:

    <ul>
      <li>One</li>
      <li class="active">Two</li>
      <li>Three</li>
    </ul>

JavaScript:

    const active = document.querySelector(".active");

    active.previousElementSibling; // <li>One</li>
    active.nextElementSibling;     // <li>Three</li>

---

### 6. Element-only traversal

Notice these properties:

- `parentElement`
- `children`
- `previousElementSibling`
- `nextElementSibling`

👉 They **ignore text nodes**  
👉 They work **only with elements**

This is usually exactly what you want.

---

### 7. Common beginner mistakes 

❌ Using the wrong property:

    element.parentNode // may give unexpected results

✅ Prefer:

    element.parentElement

Because `parentNode` can return non-element nodes.

---

### 8. One-line mental model

- Parent = **up**
- Children = **down**
- Siblings = **sideways**
