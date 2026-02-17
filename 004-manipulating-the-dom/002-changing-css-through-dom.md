## Changing CSS Through the DOM

### 1. How CSS normally works (quick reminder)

Normally:

- CSS lives in `.css` files  
- Classes control styles  
- HTML defines structure  
- CSS defines appearance  

JavaScript allows us to:

- Change styles dynamically  
- React to user actions  
- Create interactive UI behavior  

---

### 2. The `style` property (inline styles)

Every DOM element has a `.style` property.

Example:

    const box = document.querySelector(".box");

    box.style.color = "red";
    box.style.backgroundColor = "yellow";

👉 This adds **inline CSS**:

    <div style="color: red; background-color: yellow"></div>

Important idea:

`.style` modifies **inline styles**, not CSS files.

---

### 3. Important rule about CSS properties

CSS properties often use hyphens:

    background-color

JavaScript uses camelCase:

    backgroundColor

Rule:

👉 **Hyphenated CSS → camelCase in JavaScript**

Examples:

- `font-size` → `fontSize`
- `margin-top` → `marginTop`
- `border-radius` → `borderRadius`

---

### 4. Reading styles (common confusion)

Example:

    box.style.color;

This:

- Reads **only inline styles**
- Does **NOT read styles from CSS files**

Example CSS:

    .box {
      color: blue;
    }

JavaScript:

    box.style.color; // ""

Why?

👉 Because the style is not inline.

---

### 5. Why inline styles are not ideal

Heavy use of `.style` can cause problems:

- Hard to maintain  
- Overrides CSS rules  
- Not reusable  
- Mixes styling with logic  

👉 Avoid excessive inline styling.

---

### 6. Best practice: change classes instead

Instead of:

    box.style.display = "none";

Prefer:

    box.classList.add("hidden");

CSS:

    .hidden {
      display: none;
    }

Benefits:

- Cleaner code  
- Scalable styling  
- Reusable logic  
- Easier maintenance  

---

### 7. When should `.style` be used?

`.style` is perfectly fine for:

- Small dynamic values  
- Calculated sizes  
- Simple animations  

Example:

    box.style.width = progress + "%";

👉 Ideal for values computed at runtime.

---

### 8. Common beginner mistakes

Forgetting camelCase:

    box.style.background-color = "red"; // ❌ invalid

Correct:

    box.style.backgroundColor = "red";

---

Overusing inline styles:

    box.style.margin = "...";
    box.style.padding = "...";

Better handled via CSS classes.

---

### 9. One-line mental model 

Use `.style` for **small dynamic values**.  
Use **CSS classes** for real styling.
