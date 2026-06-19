# Backend & Web Development Q&A

### 1. How to make a directory a package in Python?

To make a directory a regular package in Python, we need to create a file named `__init__.py` inside that directory. This file can be completely empty.
### 2. What is the output of `console.log(true + true)` in JavaScript?

The output is **`2`**.

### 3. Give some examples of JavaScript event names.

Commonly used DOM and browser event names include:

* **Mouse Events:** `click`, `dblclick`, `mouseover`, `mouseenter`, `mouseleave`
* **Keyboard Events:** `keydown`, `keypress`, `keyup`
* **Form Events:** `submit`, `change`, `input`, `focus`, `blur`
* **Document/Window Events:** `DOMContentLoaded`, `load`, `resize`, `scroll`

### 4. What is REST?

**REST** stands for **REpresentational State Transfer**. It is an architectural style designed for distributed web APIs. A RESTful API relies on a stateless, client-server protocol—almost always HTTP—and uses standard HTTP methods (`GET`, `POST`, `PUT`, `DELETE`) to perform operations on resources, which are uniquely identified by URIs/URLs.

### 5. What is the default database for Django?

The default database for Django is **SQLite**. When you generate a new project using the `django-admin startproject` command, the `settings.py` file is pre-configured to look for an identity file called `db.sqlite3` in your root directory.

### 6. What is Django?

Django is a high-level, open-source Python web framework designed for rapid development and clean, design. It follows a "batteries-included" philosophy, providing built-in tools for common requirements like an Object-Relational Mapper (ORM), user authentication, a customizable admin interface, data validation, and security protections out of the box. It traditionally follows the **MVT (Model-View-Template)** architecture pattern.

### 7. Why is PATCH preferred over PUT in HTTP?

* **`PUT`** is idempotent and designed to completely *replace* a target resource. If you send a payload missing certain fields, those omitted fields might be cleared, overwritten, or reset to null by the server.
* **`PATCH`** is designed for *partial updates*. It only modifies the specific fields provided in the request payload while leaving the rest of the resource intact.

`PATCH` is preferred for updating large resources because it saves network bandwidth and protects against accidental data loss when modifying subset attributes.

### 8. What are some real-life examples of debouncing?

Debouncing limits the rate at which a high-frequency function executes, delaying execution until a specific amount of time has passed since the last event. Real-life examples include:

* **Search Box Auto-Suggestions:** Waiting to call the backend API until a user pauses typing for 300ms, rather than firing an API request on every single keystroke.
* **Window Resizing:** Waiting until the user finishes dragging the corner of a browser window before re-calculating page layouts or re-rendering complex charts.
* **Payment/Submit Buttons:** Disabling or ignoring repeated clicks on a "Buy Now" button so a rapid double-click does not accidentally charge a customer twice.

### 9. Which status code indicates a client error?

Client errors are represented by the **4xx** series of HTTP status codes. Common examples include:

* `400 Bad Request` (Malformed syntax)
* `401 Unauthorized` (Authentication required)
* `403 Forbidden` (Authenticated but lacks permission)
* `404 Not Found` (Resource does not exist)

### 10. Difference between a Web Server and an Application Server?

* **Web Server:** Primarily designed to handle HTTP requests and serve static assets like HTML pages, CSS files, images, and client-side JavaScript (e.g., Nginx, Apache).
* **Application Server:** Designed to process dynamic business logic by interacting with databases, handling transaction queues, and running server-side code (like Python, Java, or C#). It may support protocols beyond HTTP (e.g., RPC, gRPC) and often sits behind a web server (e.g., Gunicorn, Apache Tomcat).

### 11. Difference between Vertical Scaling and Horizontal Scaling?

* **Vertical Scaling (Scale-Up):** Adding more power (more CPU cores, more RAM, or faster storage) to a single existing server. It is easy to implement but hits an absolute hardware ceiling and usually requires downtime to upgrade.
* **Horizontal Scaling (Scale-Out):** Adding more machine instances to your infrastructure pool and distributing incoming traffic among them via a load balancer. It offers virtually infinite scalability and provides high availability, as traffic can bypass a failed machine instance.

### 12. Difference between HTTP 401 and 403 status codes?

* **`401 Unauthorized`:** The request requires authentication. The user has either not logged in at all or provided invalid credentials.
* **`403 Forbidden`:** The server understands who the user is, but they do not possess the necessary authorization roles or clearance permissions to access the resource.

### 13. What is the status code for an Internal Server Error?

The status code is **`500 Internal Server Error`**.
