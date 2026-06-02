# HTML/CSS AMA

### 1. What is `background-position`?
The `background-position` property in CSS sets the initial position of a background image within its container. By default, background images are placed in the top-left corner. You can specify positions using:
* **Keywords**: `top`, `bottom`, `left`, `right`, `center` (e.g., `background-position: center right;`)
* **Length values**: Pixels, ems, or rems (e.g., `background-position: 20px 50px;`)
* **Percentages**: (e.g., `background-position: 50% 50%;` which centers the image)

### 2. Difference between uppercase `<BR>` and lowercase `<br>`?
In standard HTML , tags are case-insensitive. Therefore, `<BR>` and `<br>` function identically to insert a line break.

### 3. Use of `order` in Flexbox?
The `order` property controls the layout order of items inside a Flexbox container. 
* By default, all flex items have an `order` value of `0` and appear in the order they are written in the HTML source code.
* You can assign negative or positive integers to rearrange them visually (e.g., `order: -1` moves an item to the front, while `order: 1` moves it toward the end) without altering the underlying HTML structure.

### 4. What is `&nbsp;`?
`&nbsp;` stands for **Non-Breaking Space**. It is an HTML character entity used for two primary purposes:
1. **Preventing line breaks**: It creates a space between two words that forces them to stay together on the same line (e.g., keeping a number and its unit like `10 USD` from breaking apart).
2. **Forcing extra spaces**: HTML natively collapses multiple consecutive spaces into a single space. Using multiple `&nbsp;` entities allows you to force extra visible spaces.

### 5. How to send a mail link?
To create a link that opens the user's default email client, use the standard HTML anchor tag (`<a>`) with the `mailto:` prefix in the `href` attribute:
```html
<a href="mailto:someone@example.com">Send Email</a>

```

### 6. What is the `for` attribute in a `<label>`?

The `for` attribute binds a `<label>` element directly to an form input element (like a textbox, checkbox, or radio button).

* The value of the `for` attribute must exactly match the `id` attribute of the input it describes.

```html
<label for="username">Username:</label>
<input type="text" id="username">

```

### 7. Difference between "In the flow" vs "Out of the flow" in CSS?

* **In the flow (In-flow)**: This is the default layout behavior. Elements take up space in the document, and subsequent elements position themselves relative to them. Block elements stack vertically, and inline elements sit side-by-side.
* **Out of the flow (Out-of-flow)**: When an element is removed from the normal layout flow, surrounding elements behave as if it does not exist and occupy its space. Elements are taken out of flow using properties like `position: absolute`, `position: fixed`, or `float`.

### 8. What is `grid-template-columns`?

`grid-template-columns` is a CSS Grid property used to define the number and widths of columns in a grid layout. You can define specific sizes, percentages, or flexible fractional units (`fr`):

```css
.grid-container {
  display: grid;
  grid-template-columns: 200px 1fr 2fr; 
}

```

### 9. Difference between `justify-content` vs `align-items`?

Both are alignment properties used in Flexbox and CSS Grid, but they operate on different axes:

* **`justify-content`**: Aligns items along the **main axis** (horizontally by default in a row-based layout). Controls spacing options like `flex-start`, `center`, `space-between`, and `space-around`.
* **`align-items`**: Aligns items along the **cross axis** (vertically by default in a row-based layout). Controls options like `flex-start`, `center`, `stretch`, and `baseline`.

### 10. What is `overflow`?

The `overflow` property specifies whether to clip content or add scrollbars when an element's content is too large to fit inside its specified layout box. Common values include:

* `visible` (Default): The content is not clipped and renders outside the element's box.
* `hidden`: The content is clipped, and the remaining text/images become invisible.
* `scroll`: The content is clipped, and the browser adds scrollbars to allow viewing.
* `auto`: Scrollbars are automatically added *only if* the content exceeds the element's size limits.

### 11. What is `target="_blank"`?

`target="_blank"` is an attribute applied to anchor links (`<a>`) that instructs the browser to open the clicked link in a brand-new tab or window.


### 12. What is the `required` attribute in HTML forms?

The `required` attribute is a boolean attribute that can be added to form input fields (like `<input>`, `<select>`, or `<textarea>`). When present, it forces the browser to natively validate the field, preventing the user from submitting the form until that specific input has been filled out.

### 13. Difference between `:nth-child` vs `:nth-of-type`?

Both are CSS pseudo-class selectors used to target elements based on their order, but they filter patterns differently:

* **`:nth-child(n)`**: Looks at all sibling elements regardless of their tag type. It checks if the item is the *n-th* child of its parent, and *then* checks if it matches the specified selector type.
* **`:nth-of-type(n)`**: Filters out all other elements first to only look at siblings of the *exact same tag type*, and then selects the *n-th* element within that specific group.
