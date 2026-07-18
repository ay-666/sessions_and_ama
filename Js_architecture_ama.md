# JavaScript & Architecture AMA

### 1. Is JavaScript interpreted or compiled?
Modern JavaScript engines (like Google Chrome's V8) use **Just-In-Time (JIT) compilation**. This means the engine compiles the JavaScript into optimized machine code just a fraction of a second before it executes, giving it the performance benefits of a compiled language while maintaining the flexibility of an interpreted one.

### 2. What are Promise states?
A Promise in JavaScript always exists in one of three mutually exclusive states:
* **Pending:** The initial state. The asynchronous operation has not completed yet.
* **Fulfilled:** The operation completed successfully, and the promise now has a resolved value.
* **Rejected:** The operation failed, and the promise has a reason (error) for the failure.

### 3. Difference between RabbitMQ and Apache Kafka?
* **RabbitMQ:** A traditional message broker. It uses a "smart broker, dumb consumer" model. It is ideal for complex routing, task queues (like Celery), and ensuring that a specific message is processed exactly once by a worker and then deleted.
* **Apache Kafka:** A distributed event streaming platform. It uses a "dumb broker, smart consumer" model. It is designed for massive throughput and append-only log retention. Messages are kept for a set retention period, allowing multiple different consumers to replay and read the same stream of events at their own pace.

### 4. What is Event Delegation?
**Event Delegation** is a JavaScript pattern where you attach a single event listener to a parent element instead of attaching individual listeners to dozens of child elements. It utilizes **event bubbling** . When a child is clicked, the parent catches the event, and you use `event.target` to determine exactly which child triggered it. This saves memory and automatically handles dynamic elements added later.

### 5. What is the Microtask Queue?
The **Microtask Queue** is a high-priority queue in the JavaScript Event Loop. It specifically handles callbacks from Promises (`.then()`, `.catch()`, `.finally()`), `async/await`, and `MutationObserver`. The Event Loop will completely empty the Microtask Queue before it moves on to process anything in the standard Macrotask Queue (like `setTimeout`).

### 6. Difference between Debouncing and Throttling?
Both are techniques to limit the rate at which a function fires, but they act differently:
* **Debouncing:** Delays the execution of a function until a certain amount of idle time has passed since the last event. (e.g., "Wait 300ms after the user completely stops typing before firing the search API").
* **Throttling:** Limits the execution of a function to a strict, steady maximum frequency. (e.g., "No matter how fast the user scrolls, only fire the layout calculation exactly once every 100ms").

### 7. What is the return type of `NaN`?
In JavaScript, `NaN` stands for "Not-a-Number". However, if you check its type using the `typeof` operator:
```javascript
typeof NaN; // Returns "number"

```

### 8. What is the Event Loop?

The **Event Loop** is the secret behind JavaScript's asynchronous, non-blocking behavior despite being single-threaded. It constantly monitors two things: the **Call Stack** (where code is currently executing) and the **Task Queues**. If the Call Stack is empty, the Event Loop takes the first waiting callback from the queues and pushes it onto the Call Stack to be executed.

### 9. What is Block Scope?

**Block Scope** means that a variable is only accessible within the specific block of code (defined by curly braces `{}`) in which it was declared. In JavaScript, variables declared with `let` and `const` are block-scoped.
*(For example, a `let` variable defined inside an `if` statement or a `for` loop cannot be accessed from outside those curly braces).*

### 10. How does browser rendering work?

When a browser loads a webpage, it follows a critical rendering path:

1. **DOM Tree:** Parses the HTML to create the Document Object Model.
2. **CSSOM Tree:** Parses the CSS to create the CSS Object Model.
3. **Render Tree:** Combines the DOM and CSSOM to create a tree of only the visible elements.
4. **Layout (Reflow):** Calculates the exact geometric position and size of every node on the screen.
5. **Paint:** Fills in the pixels on the screen (colors, text, shadows).

### 11. What is Currying?

**Currying** is a functional programming technique in JavaScript where a function that takes multiple arguments is transformed into a sequence of nested functions, each taking a single argument.

* **Standard function:** `add(a, b)`
* **Curried function:** `add(a)(b)`

```javascript
// Curried example:
function add(a) {
  return function(b) {
    return a + b;
  }
}
add(5)(10); // Returns 15

```
