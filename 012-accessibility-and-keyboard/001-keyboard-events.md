## Keyboard Events

### 1. Why keyboard accessibility matters

Not all users:

- Use a mouse  
- Can use a mouse  
- Prefer using a mouse  

Many users rely entirely on the keyboard:

- Tab → Move focus  
- Enter → Activate elements  
- Space → Toggle controls  
- Arrow keys → Navigate components  

If an interface only works with mouse clicks, it is not accessible.

---

### 2. Keyboard events you must understand

There are three primary keyboard events:

- `keydown`
- `keyup`
- `keypress` (deprecated)

Recommended:

Use `keydown` and `keyup`.

Avoid:

Do not use `keypress`.

Reason:

It is outdated and behaves inconsistently across browsers.

---

### 3. `keydown` (Most important)

Simple definition:

`keydown` fires when a key is pressed down.

Example:

    document.addEventListener("keydown", (event) => {
      console.log(event.key);
    });

Example outputs:

- Enter → `"Enter"`  
- Escape → `"Escape"`  
- a → `"a"`  

This event is widely used for UI control logic.

---

### 4. `event.key` vs `event.code`

Important distinction:

#### `event.key`

Represents:

What the user intended.

Examples:

    event.key → "a"
    event.key → "Enter"
    event.key → "Escape"

Characteristics:

- Respects keyboard language  
- Reflects user intent  

Best choice for accessibility logic.

---

#### `event.code`

Represents:

Physical key location.

Examples:

    event.code → "KeyA"
    event.code → "Enter"

Characteristics:

- Ignores keyboard layout  
- Based on hardware position  

Useful for game controls or shortcuts tied to physical keys.

---

### 5. Common keyboard interactions

| Key        | Typical Use Case |
|------------|------------------|
| Enter      | Activate / Submit |
| Space      | Toggle controls   |
| Escape     | Close dialogs     |
| Arrow keys | Navigate UI       |
| Tab        | Move focus        |

These behaviors are expected by users.

---

### 6. Example: Closing a modal with Escape

    document.addEventListener("keydown", (event) => {
      if (event.key === "Escape") {
        closeModal();
      }
    });

Why this is important:

- Matches user expectations  
- Improves accessibility  
- Standard UX pattern  

---

### 7. Making non-button elements keyboard-accessible

Problematic pattern:

    <div onclick="doSomething()">Click</div>

Issue:

Keyboard users cannot activate this.

Improved pattern:

    div.addEventListener("keydown", (event) => {
      if (event.key === "Enter" || event.key === " ") {
        doSomething();
      }
    });

Important note:

True accessibility also requires proper focus handling (covered with `tabindex`).

---

### 8. Common beginner mistakes

- Handling only mouse clicks  
- Ignoring keyboard interactions  
- Using deprecated `keypress`  
- Checking numeric key codes  
- Using `event.code` for UI logic  

---

### 9. One-line mental model

If something is interactive, it must be usable via keyboard
