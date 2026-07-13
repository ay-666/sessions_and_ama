# Django,Redis, Kubernetes AMA

### 1. What are the types of Pagination in DRF?
Django REST Framework (DRF) provides three built-in pagination styles:
* **PageNumberPagination:** Uses a page number in the URL (e.g., `?page=2`).
* **LimitOffsetPagination:** Uses a limit and a starting offset, commonly used with databases (e.g., `?limit=10&offset=20`).
* **CursorPagination:** Uses an opaque cursor indicator in the URL. It is highly efficient for massive datasets because it avoids slow SQL `OFFSET` lookups, but it requires the data to be strictly ordered.

### 2. What is a Deployment in Kubernetes?
A **Deployment** is a Kubernetes resource object that provides declarative updates for Pods and ReplicaSets. You describe a desired state in a Deployment (e.g., "I want 3 replicas of my web app running version 2.0"), and the Kubernetes control plane works to achieve and maintain that state. It handles scaling up or down, rolling updates with zero downtime, and reverting to previous versions.

### 3. What are the different worker pools in Celery?
Celery supports several execution pools to handle tasks concurrently:
* **prefork (Default):** Uses Python's `multiprocessing` module to spawn multiple processes. Best for CPU-bound tasks.
* **gevent / eventlet:** Uses greenlets for asynchronous I/O operations. Excellent for thousands of heavily network-bound or I/O-bound tasks (like making external API calls).
* **threads:** Uses multithreading. Useful for I/O-bound tasks but less common than gevent/eventlet due to Python's Global Interpreter Lock (GIL).
* **solo:** Runs inline without concurrency. It is single-threaded and primarily used for local testing and debugging.

### 4. What is the use of the Control Plane in Kubernetes?
The **Control Plane** is the brain of a Kubernetes cluster. It is responsible for maintaining the global state of the cluster. Its core functions include:
* Exposing the Kubernetes API (`kube-apiserver`).
* Storing all cluster data and state securely (`etcd`).
* Monitoring for node or pod failures and spinning up replacements (`kube-controller-manager`).
* Deciding which specific worker node a newly created Pod should run on based on resource availability (`kube-scheduler`).

### 5. What is TTL in RabbitMQ?
**TTL (Time-To-Live)** specifies the lifespan of a message or a queue in RabbitMQ.
* **Message TTL:** Dictates how long a message can sit in a queue unconsumed before it "dies" (expires). Expired messages are either discarded or routed to a Dead Letter Exchange.
* **Queue TTL:** Dictates how long a queue can remain unused (no active consumers, no messages routed to it) before RabbitMQ automatically deletes the entire queue.

### 6. What is a ClusterIP?
**ClusterIP** is the default Service type in Kubernetes. It exposes a service on an internal IP address that is only reachable from *within* the Kubernetes cluster. It acts as an internal load balancer, allowing different internal microservices (like a backend API and a database) to communicate securely without exposing them to the public internet.

### 7. Difference between a Docker Image and a Docker Container?
* **Docker Image:** A static, read-only template that contains the source code, libraries, dependencies, tools, and other files needed for an application to run. (Think of it as a class blueprint or an installation disk).
* **Docker Container:** A running, isolated instance of a Docker Image. It is the active environment executing the application code. (Think of it as the instantiated object from a class, or the program actually running on your computer).

### 8. Difference between `delay` and `apply_async` in Celery?
* **`delay()`:** A convenient shortcut method to send a task to the queue with default settings. It only accepts regular arguments and keyword arguments for the task itself (e.g., `my_task.delay(arg1, arg2)`).
* **`apply_async()`:** The underlying, more powerful method. It allows you to pass specific execution options for Celery itself using a dictionary, such as countdowns, specific queues, or retries (e.g., `my_task.apply_async(args=[arg1], countdown=60, queue='high_priority')`).

### 9. What is a Cache Stampede?
A **Cache Stampede** (also known as a Thundering Herd) is a performance failure that occurs when a highly requested cache item unexpectedly expires, is invalidated, or gets deleted.
Because the cache is suddenly empty, hundreds or thousands of simultaneous concurrent requests bypass the cache and hit the primary database all at once to regenerate the same data. This massive spike in traffic can easily overload and crash the database.

### 10. What happens when Redis dies?
If your Redis server crashes or dies, the impact depends entirely on how you are using it:
* **As a Cache:** All volatile data stored in memory is lost. Your application will start querying the primary database for every request, which can cause significant latency or lead to a database crash (cache stampede).
* **As a Message Broker (e.g., with Celery):** The application will fail to queue new background tasks, and worker nodes will sit idle because they cannot receive tasks or report statuses.
* **Data Persistence:** If Redis was configured with persistence (RDB snapshots or AOF logs), the data will be restored from the disk when the server restarts, but there will be downtime during the recovery phase.
