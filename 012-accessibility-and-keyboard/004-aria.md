## Basic aria-* Awareness

### 1. What is ARIA?

ARIA stands for:

Accessible Rich Internet Applications

Simple definition:

ARIA provides extra information that helps screen readers understand UI elements and their behavior.

ARIA is primarily used by:

- Screen readers  
- Assistive technologies  

Important:

ARIA does not affect visual layout or styling.

---

### 2. Critical rule (Memorize this)

If a native HTML element exists, use it.

Do not replace semantic HTML with ARIA.

Correct approach:

    <button>Save</button>

Avoid:

    <div role="button">Save</div>

Why?

Native HTML elements are:

- Automatically accessible  
- Keyboard-friendly  
- Screen-reader-friendly  

ARIA is a fallback, not a replacement.

---

### 3. When is ARIA necessary?

ARIA becomes necessary when:

- Building custom UI components  
- HTML alone cannot describe behavior  

Examples:

- Custom dropdowns  
- Custom modals  
- Toggle switches  
- Accordions  
- Complex widgets  

---

### 4. `aria-label` (Most common)

Purpose:

Provides an accessible name when visible text is missing.

Example:

    <button aria-label="Close modal">✖</button>

Why needed:

The icon has no readable text.

Screen readers require a description.

---

### 5. `aria-hidden`

Purpose:

Hides elements from screen readers.

Example:

    <div aria-hidden="true">Decorative icon</div>

Use cases:

- Decorative icons  
- Visual-only elements  
- Non-essential UI  

Important:

Do not hide meaningful content.

---

### 6. `role` (Use carefully)

Purpose:

Describes what an element represents.

Example:

    <div role="button" tabindex="0">Save</div>

Better solution:

    <button>Save</button>

Use `role` only when:

A native HTML equivalent is not possible.

---

### 7. State-related ARIA attributes

Some ARIA attributes describe UI state.

Example:

    <button aria-expanded="false">Menu</button>

When menu opens:

    button.setAttribute("aria-expanded", "true");

Used in:

- Dropdowns  
- Accordions  
- Expandable menus  

State accuracy is essential for accessibility.

---

### 8. ARIA does not add behavior

Critical concept:

ARIA only describes semantics.

ARIA does not:

- Add interactivity  
- Add keyboard support  
- Add event handling  

You must still implement:

- Event listeners  
- Keyboard logic  
- Focus management  

---

### 9. Common beginner mistakes

- Using ARIA instead of semantic HTML  
- Adding ARIA unnecessarily  
- Incorrect ARIA state values  
- Forgetting keyboard support  
- Assuming ARIA fixes accessibility automatically  

---

### 10. One-line mental model

ARIA describes behavior — it does not create behavior
