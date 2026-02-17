## DOM vs BOM

### 1. What problem does BOM solve?

DOM = Page structure

But real applications often need to:

- Redirect users  
- Read the current URL  
- Access browser history  
- Detect browser or device information  
- Respond to navigation actions  

These operations are **not related to HTML elements**.

They belong to the **browser environment**.

This is where BOM becomes important.

---

### 2. What is DOM? (Quick reminder)

**DOM (Document Object Model)**

The DOM represents:

- The HTML page  
- A tree of elements  
- The page content and structure  

Used for:

- Selecting elements  
- Modifying UI  
- Handling events  

Examples:

    document.getElementById("btn");
    document.querySelector("p");

Mental model:

DOM = Everything inside the page

---

### 3. What is BOM?

**Simple definition (memorize this):**

BOM (Browser Object Model) represents the browser environment surrounding the page.

BOM allows JavaScript to interact with:

- URL  
- Browser history  
- Navigation  
- Screen information  
- Browser metadata  

Mental model:

BOM = Everything outside the page

---

### 4. The key difference

| DOM                     | BOM                         |
|--------------------------|------------------------------|
| Page content             | Browser environment          |
| HTML elements            | URL, history, browser info   |
| Controlled via document  | Controlled via window APIs   |

Examples:

DOM interaction:

    document.querySelector("button");

BOM interaction:

    window.location
    window.history

---

### 5. Important relationship

Critical concept:

DOM is part of BOM.

Everything lives under the **window object**.

---

### 6. Visual mental model

    window (BOM)
     ├── document (DOM)
     │    ├── html
     │    ├── body
     │    └── elements
     ├── location
     ├── history
     └── navigator

`window` is the global browser object.

DOM is accessed through:

    window.document

---

### 7. Why full-stack developers must understand BOM

Real applications depend heavily on BOM features:

- Redirect after login  
- Reading query parameters  
- Handling back/forward navigation  
- Detecting browser/device information  
- Managing navigation flows  

This knowledge is fundamental, not optional.

---

### 8. One-line mental model

DOM = What exists inside the page  
BOM = The browser environment around the page
