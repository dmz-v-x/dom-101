## element.dataset — Working with data-* 

### 1. What is `dataset`?

Simple definition (memorize this):

`dataset` is a JavaScript object that provides direct access to an element’s `data-*` attributes.

Conceptually:

HTML attributes → JavaScript object

---

### 2. Basic example

HTML:

    <button id="btn" data-id="42" data-user-name="john">Delete</button>

JavaScript:

    const btn = document.getElementById("btn");

    console.log(btn.dataset.id);       // "42"
    console.log(btn.dataset.userName); // "john"

Important:

- No need for `getAttribute()`
- Cleaner and more readable syntax

---

### 3. Important conversion rule (Critical)

HTML uses kebab-case:

    data-user-name

JavaScript uses camelCase:

    element.dataset.userName

Rule:

kebab-case → camelCase

Examples:

- `data-product-id` → `dataset.productId`
- `data-user-role` → `dataset.userRole`

---

### 4. Setting data using `dataset`

Example:

    btn.dataset.status = "active";

This automatically creates:

    data-status="active"

Important:

JavaScript updates the actual DOM attribute.

---

### 5. Deleting dataset values

Example:

    delete btn.dataset.status;

Result:

The corresponding attribute is removed from the DOM.

---

### 6. Dataset values are always strings (Important)

Example:

    btn.dataset.id; // "42"

Even if the value looks numeric, it is still a string.

Convert manually when required:

    Number(btn.dataset.id);

---

### 7. Real-world delegation example (Very Important)

HTML:

    <ul id="products">
      <li data-id="101" data-price="999">Phone</li>
      <li data-id="102" data-price="499">Headphones</li>
    </ul>

JavaScript:

    products.addEventListener("click", (e) => {
      if (e.target.tagName === "LI") {
        const id = e.target.dataset.id;
        const price = Number(e.target.dataset.price);

        console.log(id, price);
      }
    });

Why this pattern is powerful:

- Each element carries its own data  
- No complex lookup logic  
- Works naturally with delegation  

---

### 8. Why `dataset` is preferred over `getAttribute()`

Advantages:

- Cleaner syntax  
- JavaScript-friendly naming  
- Less error-prone  
- Designed specifically for `data-*` attributes  

Use `getAttribute()` when:

- You need raw attribute access  
- You are working with non-data attributes  

---

### 9. Common beginner mistakes

- Forgetting camelCase conversion  
- Assuming values are numbers  
- Mixing `dataset` with non-standard attributes  

Correct understanding:

- HTML naming rules still apply  
- Values are always strings  

---

### 10. One-line mental model

`data-*` lives in HTML  
`dataset` is how JavaScript interacts with it
