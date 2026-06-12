# JavaScript & Web Development AMA

### 1. What does the Fetch API return?

The Fetch API returns a **`Promise`** that resolves to a **`Response`** object. This `Response` object represents the HTTP response from the server. To access the actual data , one must call its built-in body-parsing methods, such as `.json()` or `.text()`, which also return Promises.

### 2. What is the use of the DOM?

The **Document Object Model (DOM)** is a programming interface for web documents. Its primary uses are:

* Connecting a web page to programming languages like JavaScript.
* Representing the structure of an HTML or XML document as a logical tree of nodes.
* Allowing scripts to dynamically access, add, delete, modify, and style HTML elements and attributes on a live webpage.

### 3. What is a Promise?

A **Promise** is a JavaScript object representing the eventual completion (or failure) of an asynchronous operation. It acts as a placeholder for a value that is not immediately available. A Promise always exists in one of three states:

* `pending`: Initial state; the operation is still running.
* `fulfilled`: The operation completed successfully.
* `rejected`: The operation failed with an error.

### 4. What are real-world use cases of Asynchronous JavaScript?

Asynchronous JavaScript allows tasks to run in the background without freezing or blocking the user interface. Real-world examples include:

* **Fetching Data:** Fetching live product feeds, weather updates, or user profiles from a remote database/API.
* **Timers and Autosave:** Triggering a feature after a delay or periodically background-saving a document draft.
* **Media Loading:** Streaming video/audio streams or lazy-loading high-resolution images as the user scrolls.
* **Real-time Communication:** Listening for incoming chat messages via WebSockets without needing a page refresh.

### 5. What is Callback Hell?

**Callback Hell** (also known as the "Pyramid of Doom") occurs when multiple asynchronous operations are heavily nested inside one another using callback functions.

```javascript
getData(function(a) {
    getMoreData(a, function(b) {
        getEvenMoreData(b, function(c) {
            // Nesting continues...
        });
    });
});

```

This pattern results in deeply indented code that is incredibly difficult to read, maintain, and debug. Modern JavaScript avoids callback hell by using Promises or `async/await`.

### 6. Difference between Primitive and Non-Primitive data types, and their mutability?

* **Primitive Types** (e.g., String, Number, Boolean, Null, Undefined, Symbol, BigInt):
* **Storage:** Stored directly by value on the stack memory.
* **Mutability:** They are completely **immutable** (cannot be changed). When you alter a primitive variable, you are reassigning a fresh value to it, not mutating the original value in memory.


* **Non-Primitive Types** (e.g., Objects, Arrays, Functions):
* **Storage:** Stored by reference on the heap memory.
* **Mutability:** They are **mutable** (can be changed). You can add, edit, or remove properties inside an object or array without altering its underlying memory address reference.



### 7. Which method in a Promise always runs?

The **`.finally()`** method always executes once a Promise is settled, regardless of whether it was successfully fulfilled (`.then()`) or rejected (`.catch()`). It is commonly used to perform cleanup actions, like turning off a loading spinner.

### 8. What are the instance methods of a Promise?

A Promise instance contains three primary prototype methods:

1. **`.then(onFulfilled, onRejected)`:** Handles the successful resolution of a promise.
2. **`.catch(onRejected)`:** Handles any errors or rejections that occur during execution (shorthand for `.then(null, onRejected)`).
3. **`.finally(onFinally)`:** Executes a callback when the promise finishes, regardless of the outcome.

### 9. What is `Promise.all`?

`Promise.all()` is a static method that accepts an array (or iterable) of promises and aggregates their results into a single returned Promise.

* **Success:** It resolves only when **all** input promises resolve successfully, returning an array of their resolved values in the exact same order.
* **Failure:** It operates on a "fail-fast" mechanism. If even a single promise rejects, the entire `Promise.all()` statement rejects immediately with that error, ignoring all other resolved promises.

### 10. By using which property can we add or remove classes to elements in JavaScript?

You use the **`element.classList`** property. It provides built-in methods to manipulate CSS classes cleanly:

* `element.classList.add("class-name")` — Adds a class.
* `element.classList.remove("class-name")` — Removes a class.
* `element.classList.toggle("class-name")` — Adds the class if missing, or removes it if already present.

### 11. What are the types of built-in errors in JavaScript?

When code fails, JavaScript throws specific built-in error instances:

* **SyntaxError:** Thrown when code violates the spelling or grammatical rules of JavaScript (e.g., missing brackets).
* **ReferenceError:** Thrown when attempting to access a variable that has not been declared or initialized.
* **TypeError:** Thrown when an operation is performed on an incompatible data type (e.g., executing a number as a function like `true()`).
* **RangeError:** Thrown when a numeric value falls outside its allowed boundaries or limits (e.g., creating an array with a negative length).
* **URIError:** Thrown when global URI encoding/decoding functions (like `decodeURIComponent()`) receive invalid parameters.

### 12. Difference between `Promise.all` and `Promise.allSettled`?

* **`Promise.all()`:** Fails immediately if any individual promise is rejected. It is best used when your tasks depend on one another and you require every single one to succeed.
* **`Promise.allSettled()`:** Never fails early. It waits until every promise in the array is complete (either fulfilled or rejected) and returns an array of objects describing the outcome status and value/reason for each individual item.

### 13. Name some common JavaScript events.

* **Mouse Events:** `click`, `dblclick`, `mouseover`, `mouseleave`.
* **Keyboard Events:** `keydown`, `keyup`.
* **Form Events:** `submit`, `change`, `input`, `focus`, `blur`.
* **Window/Document Events:** `DOMContentLoaded`, `load`, `resize`, `scroll`.

### 14. Difference between the Microtask Queue and Callback (Macrotask) Queue?

Both queues coordinate asynchronous callbacks via the Event Loop, but they are weighted by priority:

* **Microtask Queue (Higher Priority):** Handles callbacks originating from Promises (`.then/catch/finally`), `async/await` expressions, and `MutationObserver`. The Event Loop will completely empty the entire Microtask Queue before executing anything else.
* **Callback Queue / Macrotask Queue (Lower Priority):** Handles callbacks from operations like `setTimeout()`, `setInterval()`, DOM events, and network requests. It executes its items one at a time, re-checking the Microtask Queue in between items.

### 15. Are primitive data types in JavaScript considered Objects?

**No, primitive data types are not objects.** They are simple, atomic values that lack properties or methods.

However, when you attempt to invoke a method on a primitive (e.g., executing `"hello".toUpperCase()`), JavaScript automatically and temporarily wraps the primitive value in its corresponding Object wrapper (like the `String()` object), processes the method, and immediately discards the temporary wrapper object. This behavior is called **autoboxing**.
