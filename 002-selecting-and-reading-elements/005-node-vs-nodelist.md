## Node vs NodeList

### 1. First, what is a Node? (very simple)

**Simple definition:**

A **Node** is a **single item** in the DOM tree.

Remember:

👉 **Everything in the DOM is a node**

That includes:

- Elements  
- Text  
- Comments  
- The document itself  

---

### 2. Types of nodes (just awareness)

You don’t need to memorize numbers — just understand the **types**.

#### Document node
- Represents the **entire page**

#### Element node
- HTML elements like `<div>`, `<p>`, `<h1>`

#### Text node
- The **text inside elements**

Example:

    <p>Hello</p>

- `<p>` → element node  
- `"Hello"` → text node  

---

### 3. What is a NodeList?

**Simple definition:**

A **NodeList** is a **collection (list) of nodes**.

You usually get a NodeList when:

- You select **multiple elements**
- You **traverse** the DOM

Example:

    document.querySelectorAll("p");

This returns:

👉 A **NodeList of `<p>` nodes**

---

### 4. Node vs NodeList (clear difference)

| Node                | NodeList              |
|---------------------|-----------------------|
| Single item         | Collection of items   |
| One node            | Many nodes            |
| Directly modifiable | Needs looping         |
| No `length`         | Has `length`          |

Example:

    const el = document.querySelector("p");      // Node
    const list = document.querySelectorAll("p"); // NodeList

---

### 5. Why does NodeList exist?

Because sometimes:

- You want **ONE** thing  
- Sometimes you want **MANY** things  

JavaScript cannot guess your intent, so the browser gives you:

- **Node** → when selecting one
- **NodeList** → when selecting many

---

### 6. NodeList behavior (important)

A NodeList:

- Is **static** (in most cases)
- Does **NOT auto-update**
- Supports `forEach`

Example:

    list.forEach(node => {
      node.style.color = "red";
    });

---

### 7. Common beginner mistakes

❌ Treating a NodeList like a single node:

    list.textContent = "Hi"; // ❌ error

❌ Forgetting to loop:

    list.style.color = "red"; // ❌ error

👉 Always loop when working with a NodeList.

---

### 8. One-line mental model

- **Node** = one DOM item  
- **NodeList** = list of DOM items
