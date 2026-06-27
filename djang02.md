# Django Advanced Concepts AMA

### 1. In Django, do we have to write custom code to check if a user is logged in?
No, we do not need to write custom logic from scratch. Django provides built-in authentication tools to handle this effortlessly:
* **In Views:** We can check the boolean `request.user.is_authenticated`.
* **View Decorators:** For function-based views, We can use the `@login_required` decorator to automatically block unauthenticated users.
* **Class-Based Views:** We can inherit from `LoginRequiredMixin`.
* **In Templates:** We can use the template tag `{% if user.is_authenticated %}` to show or hide HTML elements.

### 2. Difference between `annotate` vs `aggregate`?
Both are used for database calculations (like Sum, Count, Avg), but they apply to the data differently:
* **`aggregate()`**: Calculates a **single summary value** for the *entire* QuerySet. It evaluates immediately and returns a Python dictionary. 
* **`annotate()`**: Calculates a value for **each individual item** inside the QuerySet. It returns a QuerySet of objects, where each object has a new dynamic attribute attached to it.

### 3. Can you create a `templates` folder inside a Django app?
Yes, it is actually the recommended best practice for app portability. 

### 4. What is lazy evaluation in QuerySets?
Lazy evaluation means that creating a QuerySet does **not** instantly execute a database query. filter, slice, and chain a QuerySet multiple times, and Django will not touch the database until the QuerySet is explicitly "evaluated". This optimizes performance by minimizing database hits.

### 5. Difference between `null=True` and `blank=True`?
* **`null=True` (Database Level):** Tells the database to allow storing empty values as `NULL`. It is strictly about the database schema.
* **`blank=True` (Validation Level):** Tells Django's form validation (and the Django Admin) that the field is allowed to be submitted empty.

### 6. How do you add a custom error manually in forms?
We can add custom errors by overriding the `clean()` method (for cross-field validation) or `clean_<fieldname>()` methods (for specific fields) in `forms.Form` or `forms.ModelForm`.
To trigger the error, you raise a `ValidationError` or use `add_error()`:
```python
from django import forms
from django.core.exceptions import ValidationError

class MyForm(forms.Form):
    age = forms.IntegerField()

    def clean_age(self):
        age = self.cleaned_data.get('age')
        if age < 18:
            raise ValidationError("You must be at least 18 years old.") # Adds error to the field
        return age

```

### 7. What are some common `request` attributes in Django?

When a view receives an HTTP request, Django passes an `HttpRequest` object (named `request`). Common attributes include:

* `request.method`: The HTTP method used (e.g., `'GET'`, `'POST'`).
* `request.GET`: A dictionary-like object containing URL query parameters.
* `request.POST`: A dictionary-like object containing submitted form data.
* `request.user`: Represents the currently logged-in user.
* `request.path`: The string representing the URL path (e.g., `/about/`).
* `request.META`: A dictionary containing standard HTTP headers and server context (like `REMOTE_ADDR` for the user's IP).

### 8. What does `request.user` return?

* If the user is currently logged in, it returns a **`User` model instance** representing that specific user in the database.
* If the user is *not* logged in, it returns an instance of **`AnonymousUser`** (a built-in Django object that mimics the User interface but always returns `False` for `is_authenticated`).

### 9. How do you solve the N+1 query problem?


* **`select_related()`**: Used for single-valued relationships (Foreign Key, One-to-One). It uses a SQL `JOIN` to pull the related data in the exact same initial query.
* **`prefetch_related()`**: Used for multi-valued relationships (Many-to-Many, Reverse Foreign Key). It does a separate lookup for the related objects in Python and joins them together in memory, reducing the queries to exactly 2.

```

```
