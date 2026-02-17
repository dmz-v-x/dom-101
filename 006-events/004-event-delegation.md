## Event Delegation — Efficient Event Handling

### 1. What problem does delegation solve?

Consider this HTML:

    <ul id="list">
      <li>Apple</li>
      <li>Banana</li>
      <li>Mango</li>
    </ul>

Goal:

- Click any `<li>`
- Run some logic

A common beginner approach:

    document.querySelectorAll("li").forEach(li => {
      li.addEventListener("click", () => {
        console.log(li.textContent);
      });
    });

---

#### Problems with this approach

- Too many event listeners  
- Poor performance at scale  
- Newly added `<li>` elements will not work  
- Unnecessary memory usage  

This approach becomes fragile in real applications.

---

### 2. The idea behind delegation

**Simple definition (memorize this):**

Event delegation means attaching **one listener to a parent element** and handling events from its children using **event bubbling**.

---

### 3. Why delegation works

Delegation works because of **event bubbling**.

When clicking a list item:

    li → ul → body → document → window

👉 The event travels upward.

👉 The parent can detect events originating from its children.

---

### 4. Correct delegated solution

    const list = document.getElementById("list");

    list.addEventListener("click", (event) => {
      if (event.target.tagName === "LI") {
        console.log(event.target.textContent);
      }
    });

---

### 5. What is happening internally?

When a user clicks an `<li>`:

1. The event starts at the clicked element  
2. `event.target` references that element  
3. The event bubbles upward  
4. The parent listener runs  
5. We inspect `event.target`  

👉 One listener handles all children.

---

### 6. Why `event.target` is critical

Without `event.target`:

- You would not know which child triggered the event  

Delegation relies on:

Event Bubbling + Event Target

This combination is extremely powerful.

---

### 7. Dynamic elements now work

Example:

    const li = document.createElement("li");
    li.textContent = "Orange";
    list.append(li);

Result:

👉 Clicking "Orange" works immediately  
👉 No new listener required  

This is a major advantage.

---

### 8. Real-world uses of delegation

Event delegation is widely used in:

- Todo lists  
- Tables  
- Menus  
- Forms  
- Dynamic dashboards  
- Infinite scrolling interfaces  

Modern frameworks heavily rely on delegation internally.

---

### 9. Common beginner mistakes

- Attaching listeners to each child  
- Forgetting to check `event.target`  
- Comparing incorrect elements  
- Writing logic on the wrong node  

Delegation requires careful targeting logic.

---

### 10. One-line mental model

Delegate events to **parents**, not children.
