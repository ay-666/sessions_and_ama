# DRF, SQL & JavaScript AMA

### 1. Difference between REST and APIs?
* **API (Application Programming Interface):** A broad concept referring to any set of rules and protocols that allow one software application to communicate with another. APIs can be built using various architectures (e.g., SOAP, GraphQL, gRPC, or REST).
* **REST (Representational State Transfer):** A specific architectural style for designing networked applications and web APIs. It relies on stateless communication and standard HTTP methods. 

### 2. Will Mixins work without mentioning GenericAPIView?
No, they generally will not work on their own. In Django REST Framework (DRF), Mixins (like `CreateModelMixin` or `ListModelMixin`) only provide the underlying action logic (such as `.create()` or `.list()`). They do not inherit from standard View classes and do not contain the HTTP handler methods (like `.get()` or `.post()`). 
They must be paired with `GenericAPIView` because `GenericAPIView` provides the core infrastructure (like `get_queryset()`, `get_serializer()`, and pagination) that the Mixins rely on to function.

### 3. What is the Secret Key in JWT?
In JSON Web Tokens (JWT), the secret key is a highly secure, private string stored only on your server (usually in environment variables). 
When a user logs in, the server uses this secret key alongside a cryptographic algorithm to sign the token. When the client sends the token back in future requests, the server uses the exact same secret key to verify the signature. This guarantees that the token's payload has not been tampered with or forged by a malicious user.

### 4. What is `serializer.is_valid()`?
In DRF, `serializer.is_valid()` is a mandatory method used to validate incoming data against the rules and constraints defined in your serializer and database models. 
* You must call it before attempting to access `serializer.validated_data` or calling `serializer.save()`.
* It returns a boolean (`True` if the data passes all validation checks, `False` if it fails).
* If you pass `raise_exception=True` (i.e., `serializer.is_valid(raise_exception=True)`), it will automatically return a `400 Bad Request` HTTP response to the client if the data is invalid, along with the specific error messages.

### 5. Why do we pass `many=True` in serializers?
By default, a DRF serializer expects to process a single object instance (like one specific user or one blog post). 
You pass `many=True` when instantiating the serializer to explicitly tell it that it will be handling a *collection* or *list* of objects (such as an entire QuerySet of multiple records). 

### 6. What are the different types of SQL commands?
SQL commands are grouped into five main categories:
1.  **DQL (Data Query Language):** Used to fetch data. (`SELECT`)
2.  **DDL (Data Definition Language):** Used to define or alter the database structure. (`CREATE`, `ALTER`, `DROP`, `TRUNCATE`)
3.  **DML (Data Manipulation Language):** Used to modify the data inside the tables. (`INSERT`, `UPDATE`, `DELETE`)
4.  **DCL (Data Control Language):** Used to manage user permissions and security. (`GRANT`, `REVOKE`)
5.  **TCL (Transaction Control Language):** Used to manage database transactions. (`COMMIT`, `ROLLBACK`, `SAVEPOINT`)

### 7. What are the types of Pagination in DRF?
DRF provides three built-in pagination styles:
1.  **PageNumberPagination:** The most common style. It accepts a page number in the URL query parameters (e.g., `?page=3`).
2.  **LimitOffsetPagination:** Used frequently in databases. It accepts a limit (how many items to return) and an offset (where to start counting from) (e.g., `?limit=10&offset=20`).
3.  **CursorPagination:** The most efficient for massive datasets. It uses an opaque cursor string in the URL to navigate forward and backward. It avoids the performance hits associated with SQL `OFFSET` clauses, but requires the data to be strictly ordered (usually by a timestamp).

### 8. What is `lookup_field` in DRF?
In DRF's generic views and viewsets, `lookup_field` is a property that tells the view which model field should be used to retrieve an individual database record. 
By default, it is set to `'pk'` (Primary Key / ID). If you want your API URLs to use a different unique identifier—like a user's username or an article's slug (e.g., `/api/users/johndoe/`)—you would override it by setting `lookup_field = 'username'` in your view.

### 9. What is the Temporal Dead Zone (TDZ) in JavaScript?
The Temporal Dead Zone (TDZ) is a specific behavior in JavaScript related to variables declared with `let` and `const`. 
It refers to the period between the moment a block of scope is entered and the moment the variable is actually initialized with a value. During this "dead zone," the variable exists in memory, but attempting to access or log it will throw a `ReferenceError`. (This differs from `var`, which would simply return `undefined` due to hoisting).
