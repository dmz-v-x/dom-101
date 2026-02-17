## `tabindex`

### 1. What is `tabindex`?

Simple definition (memorize this):

`tabindex` controls whether an element can receive focus and how it participates in keyboard navigation.

It answers two key questions:

- Can this element receive focus?  
- When will it receive focus?  

---

### 2. Default focus behavior (Important reminder)

By default:

Focusable elements:

    <button>
    <input>
    <a href="...">
    <select>
    <textarea>

Non-focusable elements:

    <div>
    <span>
    <p>

This is why this pattern fails for keyboard users:

    <div onclick="openMenu()">Menu</div>

Keyboard users cannot focus or activate it.

---

### 3. `tabindex="0"` (Most important value)

Example:

    <div tabindex="0">Menu</div>

What this does:

- Makes the element focusable  
- Inserts it into the natural tab order  

This is the recommended value for custom interactive elements.

Example:

    menu.addEventListener("keydown", (event) => {
      if (event.key === "Enter") {
        openMenu();
      }
    });

Now:

- Tab → Focus element  
- Enter → Activate behavior  

---

### 4. `tabindex="-1"` (Programmatic focus only)

Example:

    <div tabindex="-1">Modal</div>

What this does:

- Element is NOT reachable via Tab  
- Element CAN be focused via JavaScript  

Example:

    modal.focus();

Used for:

- Modals  
- Dialogs  
- Toasts  
- Error messages  
- Controlled focus flows  

---

### 5. Positive tabindex values (Avoid this)

Example:

    <div tabindex="1">Bad Pattern</div>

Why this is problematic:

- Overrides natural tab order  
- Creates confusing navigation  
- Breaks accessibility expectations  

Best practice:

Do not use positive tabindex values.

---

### 6. Summary table

| Value | Meaning | Recommended |
|-------|----------|-------------|
| 0     | Focusable, natural order | Yes |
| -1    | Focusable via JS only | Yes |
| >0    | Custom navigation order | No |

---

### 7. Real-world example: accessible card

HTML:

    <div class="card" tabindex="0">
      Product Card
    </div>

JavaScript:

    card.addEventListener("keydown", (event) => {
      if (event.key === "Enter") {
        openProduct();
      }
    });

Result:

- Card becomes keyboard-accessible  
- Behavior matches user expectations  

---

### 8. Common beginner mistakes

- Making every element focusable  
- Using positive tabindex values  
- Forgetting keyboard event handlers  
- Supporting only mouse interactions  

---

### 9. One-line mental model

If an element behaves like a button, it must be accessible like one
