## Focus Management

### 1. What is focus?

Simple definition (memorize this):

Focus is the element that is currently active and receiving keyboard input.

Important rules:

- Only one element can be focused at a time  
- Focus determines where keyboard input goes  
- Focus is central to keyboard navigation  

---

### 2. How users move focus (Critical behavior)

Keyboard users rely on standard interactions:

- Tab → Move focus forward  
- Shift + Tab → Move focus backward  
- Enter / Space → Activate focused element  

These behaviors are expected across all interfaces.

---

### 3. Elements focusable by default

Certain elements automatically participate in focus navigation:

    <button>
    <a href="...">
    <input>
    <select>
    <textarea>

These are called **interactive elements**.

They are accessible without additional configuration.

---

### 4. Non-focusable elements (Important limitation)

Elements such as:

    <div>
    <span>
    <p>

Are **not focusable by default**.

Result:

- Keyboard users cannot reach them  
- Keyboard users cannot interact with them  

This often causes hidden accessibility issues.

---

### 5. Programmatically focusing elements

JavaScript can move focus manually:

    element.focus();

Example:

    input.focus();

Common use cases:

- Auto-focus first input  
- Moving focus into dialogs  
- Guiding keyboard flows  
- Error handling UX  

---

### 6. Real-world example: modal focus

When opening a modal:

Focus must move inside the modal.

Example:

    openModal();
    modal.querySelector("button").focus();

Why this is necessary:

- Prevents focus remaining behind overlay  
- Keeps keyboard navigation logical  
- Avoids user confusion  

---

### 7. Removing focus (Rare usage)

JavaScript can remove focus:

    element.blur();

Used sparingly:

- Closing modals  
- Resetting interaction state  

---

### 8. Focus order matters

Focus follows **DOM order**, not visual layout.

Problematic structure:

    <button>Save</button>
    <input />

This produces unnatural navigation flow.

Best practice:

Structure DOM in logical interaction order.

---

### 9. Visual focus indicators (Critical for usability)

Browsers display focus using outlines.

Dangerous pattern:

    :focus {
      outline: none;
    }

Why this is harmful:

- Keyboard users lose positional awareness  
- Accessibility is severely degraded  

Safer alternative:

    :focus {
      outline: 2px solid blue;
    }

Always preserve visible focus indicators.

---

### 10. Common beginner mistakes

- Removing focus outlines  
- Forgetting to move focus into modals  
- Building mouse-only interactions  
- Allowing focus behind overlays  
- Poor DOM structure  

---

### 11. One-line mental model

If users cannot see focus, the interface becomes unusable
