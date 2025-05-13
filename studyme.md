### 1. **Vertical Scaling (Scale Up)**

**Definition:**
Increasing the capacity of a single machine by adding more CPU, RAM, or storage.

**Example:**
Suppose your web server is running on a machine with 4 GB of RAM and it starts to struggle under load. You upgrade it to a machine with 16 GB RAM and a faster processor.

**Pros:**

* Simpler to implement.
* No need to modify the application.

**Cons:**

* Limited by the hardware capacity.
* Downtime is often needed to upgrade.

---

### 2. **Horizontal Scaling (Scale Out)**

**Definition:**
Adding more machines or nodes to distribute the load.

**Example:**
Instead of one web server, you add 3 more and distribute traffic among all 4 using a load balancer.

**Pros:**

* Virtually unlimited scaling.
* More fault-tolerant.

**Cons:**

* More complex to manage.
* Requires the application to be designed for distributed environments.

---

### 3. **Caching**

**Definition:**
Storing frequently accessed data in fast storage (like memory) to reduce load and improve speed.

**Example:**
A user requests a blog post. Instead of querying the database each time, the post is stored in a cache (like Redis or Memcached). Subsequent requests retrieve it from the cache.

**Types:**

* **In-memory cache:** Redis, Memcached.
* **Browser cache:** Static resources (images, CSS) cached on the client.

**Pros:**

* Reduces database load.
* Speeds up responses.

**Cons:**

* Needs cache invalidation strategy.
* Stale data risk.

---

### 4. **Load Balancing**

**Definition:**
Distributes incoming traffic across multiple servers to ensure no single server is overwhelmed.

**Example:**
You have 3 application servers. A load balancer (like NGINX or AWS ELB) distributes incoming user requests among them.

**Types:**

* **Round-robin**
* **Least connections**
* **IP hash**

**Pros:**

* Improves availability.
* Enables horizontal scaling.

**Cons:**

* Needs proper health checks.
* Can become a bottleneck if not redundant.

---

### 5. **Database Replication**

**Definition:**
Copying data from one database server to one or more replicas to increase availability and read scalability.

**Example:**
A MySQL master database is replicated to 2 slave databases. Reads go to slaves, writes go to the master.

**Types:**

* **Master-slave**
* **Master-master**
* **Asynchronous vs synchronous**

**Pros:**

* Improves read performance.
* High availability and fault tolerance.

**Cons:**

* Write operations still go to one node (usually).
* Risk of replication lag.

---

### 6. **Database Partitioning (Sharding)**

**Definition:**
Splitting a large database into smaller parts (shards), each holding a portion of the data.

**Example:**
An e-commerce site partitions user data by region: US users in one database, EU users in another.

**Types:**

* **Horizontal partitioning:** Split rows.
* **Vertical partitioning:** Split columns.

**Pros:**

* Allows scaling writes.
* Each shard can be on a separate server.

**Cons:**

* Complex to implement and maintain.
* Cross-shard queries are hard.

---

### Summary Table:

| Technique             | Purpose                       | Example                               |
| --------------------- | ----------------------------- | ------------------------------------- |
| Vertical Scaling      | Increase capacity of one node | Upgrade server from 4 GB to 16 GB RAM |
| Horizontal Scaling    | Add more nodes                | Add more web servers                  |
| Caching               | Speed up access               | Use Redis for frequent queries        |
| Load Balancing        | Distribute traffic            | NGINX sends requests to 3 app servers |
| Database Replication  | Improve read availability     | MySQL master-slave setup              |
| Database Partitioning | Scale database writes         | Shard users by region across DBs      |
