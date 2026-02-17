## Working with Attributes — getAttribute and setAttribute

### 1. What is an attribute? 

Example HTML:

    <button id="saveBtn" disabled title="Save data">Save</button>

Here:

- `id`
- `disabled`
- `title`

These are **attributes**.

Attributes provide extra information about an element.

They define configuration, metadata, and behavior hints.

---

### 2. Two ways to access attributes (Important)

There are two related but different mechanisms:

1. **DOM properties**

        element.id
        element.disabled

2. **Attribute methods**

        getAttribute()
        setAttribute()

In this topic, we focus on **attribute methods**.

---

### 3. `getAttribute()` — Reading attributes

**Simple definition:**

`getAttribute()` reads the **exact value from the HTML markup**.

Example:

    const btn = document.querySelector("button");

    btn.getAttribute("id");     // "saveBtn"
    btn.getAttribute("title");  // "Save data"

If the attribute does not exist:

    btn.getAttribute("foo"); // null

Important:

The return value is always a **string or null**.

---

### 4. `setAttribute()` — Setting attributes

**Simple definition:**

`setAttribute()` adds or updates an attribute.

Example:

    btn.setAttribute("disabled", "true");

Resulting HTML:

    <button disabled="true">Save</button>

Another example:

    btn.setAttribute("title", "Click to save");

The attribute is updated directly in the DOM.

---

### 5. Removing attributes (Quick awareness)

    btn.removeAttribute("disabled");

Result:

The button becomes clickable again.

---

### 6. Attribute methods vs DOM properties (Important clarity)

Example:

    btn.id                     // DOM property
    btn.getAttribute("id")     // HTML attribute

In many cases, they produce the same value.

But conceptually:

- **Attributes** → Reflect HTML markup  
- **Properties** → Reflect live element state  

Example difference:

    input.value                 // current live value
    input.getAttribute("value") // initial HTML value

Beginner rule of thumb:

Use attribute methods when working with **custom attributes**.

---

### 7. Real-world use case (Very common)

Example HTML:

    <button id="deleteBtn" data-id="42">Delete</button>

JavaScript:

    btn.getAttribute("data-id"); // "42"

This pattern is heavily used in production:

- Backend identifiers
- Metadata storage
- UI logic linking

---

### 8. Common beginner mistakes

Incorrect assumption:

    btn.getAttribute("data-id"); // "42"

Attributes always return **strings**.

If needed:

    Number(btn.getAttribute("data-id"));

---

Incorrect usage:

    btn.getAttribute(data-id); // error

Correct:

    btn.getAttribute("data-id");

---

### 9. One-line mental model

Attributes live in HTML.  
getAttribute reads HTML.  
setAttribute updates HTML.
