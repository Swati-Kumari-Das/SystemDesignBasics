# System Design

System design is the process of designing the elements of a system such as the **architecture**, **modules and components**, the **interfaces** of those components, and the **data** that flows through the system.  

---

## High-Level Design (HLD)
High-Level Design provides an overview of the system architecture and the main components that would be developed for the resulting product.

- System architecture details  
- Database design  
- Services and processes  
- Relationships between various modules  

---

## Low-Level Design (LLD)
Low-Level Design describes the detailed design of each element mentioned in the High-Level Design.

- Classes  
- Interfaces  
- Relationships between different classes  
- Actual logic of various components  
# Monolithic Architecture

## What is Architecture?
**Architecture** refers to the internal design details used for building applications.

---

## What is Monolithic Architecture?
If all the components and functionalities of a project are **entangled and combined in a single codebase**, then that is a **Monolithic Application**.  

Monolithic Architecture is also known as a **Centralised System**.

---

## Key Characteristics
- All modules are combined into a single codebase  
- Deployed as **one unit**  
- Less complex to start with  
- Easier to understand → Higher productivity  

---

## When is Monolithic Architecture Good?
- When we are just **starting a project**  
- All modules are in a single system, so fewer **network calls** are needed compared to other architectures  
- Comparatively **easier to secure**  
- **Integration testing** is simpler  
- Less confusion for developers  

---

## Advantages
- Simpler to develop and deploy (especially for small projects)  
- Higher developer productivity in the early stages  
- Easier to test and secure  
- Reduced network overhead since everything is in one system  

---

## Disadvantages
- **Single point of failure**: if one module has a bug, the entire system can break  
- **Tightly coupled**: updating one module requires redeploying the entire system  
- **Technology lock-in**: changing the programming language or framework for one module affects the whole system  
- Harder to scale → you must scale the entire application, not just the part that needs more resources  

---


# Distributed System

## What is a Distributed System?
A **Distributed System** is a collection of multiple individual systems connected through a network that share resources, communicate, and coordinate to achieve common goals.


---
<img width="964" height="484" alt="image" src="https://github.com/user-attachments/assets/976ff7e1-0d96-4459-b483-7d08713538bb" />

---
## Advantages
- **Scalable** → Can handle increasing workloads by adding more machines  
- **Low Latency** → Tasks can be processed closer to the user or data source  
- **No Single Point of Failure** → System keeps running even if one machine fails  

---

## Disadvantages
- **Complex** → More difficult to design and maintain than a single system  
- **Management Required** → Needs load balancing and monitoring tools  
- **Difficult to Secure** → More systems mean more attack surfaces  
- **Message Loss** → Communication between nodes can fail, causing data loss or delays

# Latency in Systems

## What is Latency?
**Latency** = Network Delay + Computational Delay  

- In **Monolithic Architecture** → Latency comes only from **computational delay**  
- In **Distributed Architecture** → Latency = **computational delay + network delay**  


## Network Delay

**Network Delay** is the time taken for data to travel across the network from one system (or node) to another.  
It depends on factors like:  
- Physical distance between systems  
- Network bandwidth (capacity of data transfer)  
- Network congestion (traffic load)  
- Routing and switching delays  

💡 Example:  
When you search for a product in an e-commerce app:  
- The time taken for your request to travel from your phone to the server (and the response to come back) is the **network delay**.  
## Computational Delay

**Computational Delay** is the time taken by the system to process a request after it is received.  
It depends on factors like:  
- CPU speed and efficiency  
- Amount of data to be processed  
- Algorithm complexity  
- Memory and disk usage  

💡 Example:  
When you search for a product in an e-commerce app, the time taken by the server to query the database, apply filters, and prepare the result before sending it back is the **computational delay**.  

---

## How to Reduce Latency?

### 1. Caching
- **Caching** is the process of storing information for a set period of time on a computer.  
- It allows frequently accessed data to be served faster without recalculating or fetching it from the database every time.  

### 2. CDN (Content Delivery Network)
- **CDNs** are geographically distributed networks of proxy servers.  
- Their main objective is to **serve content to users more quickly** by bringing it closer to their location.  

### 3. Upgrading
- Upgrading infrastructure (faster servers, optimized code, better network) also helps reduce computational and network delays.  


# Throughput in Systems

## What is Throughput?
**Throughput** = Volume of work or information flowing through a system.  

- It represents the **amount of data transmitted per unit of time**  
- Measured in **bits per second (bps)**  
- Think of it as the **process flow rate** of the system  

---

## Throughput in Different Architectures
- **Monolithic Architecture** → Throughput is usually **less** (limited resources, single system)  
- **Distributed Systems** → Throughput can be scaled almost **without limit** using load balancers and additional nodes  

---

## Causes of Low Throughput
- **High Latency** → Delays in computation or network  
- **Protocol Overhead** → Extra information added during communication  
- **Network Congestion** → Too many requests or heavy traffic in the system  

---

## Improving Throughput
- **CDN (Content Delivery Network)** → Delivers content closer to users, reducing network bottlenecks  
- **Caching** → Stores frequently used data, reducing repeated computation and database queries  
- **Distributed Systems (DS)** → Scale horizontally by adding more nodes to handle larger workloads  
- **Load Balancer** → Distributes requests across multiple servers, avoiding overload on a single node  
- **Upgrade Resources** → Improve server capacity (CPU, memory, storage, network speed) for faster processing  

# Availability in Systems

## What is Availability?
**Availability** is the ability of a system to remain operational and accessible even when failures occur.  
A highly available system ensures that users can access services with minimal downtime.

- **Fault Tolerance** is directly proportional to **Availability**.  
  (More fault tolerance → Higher availability)

---

## How to Increase Availability?

### 1. Replication
- Process of **copying data or synchronizing state** between nodes.  
- Ensures if one node fails, another can serve the same data.  
- Replication usually includes **redundancy**.

### 2. Redundancy
- Having **backup components** (servers, databases, or networks).  
- If one fails, the backup immediately takes over.  
- Prevents single points of failure.

### 3. Fault Tolerance
- System’s ability to **continue operating correctly even when some components fail**.  
- Achieved through replication, redundancy, and robust error handling.

### 4. Load Balancing
- Distributes traffic across multiple servers.  
- Prevents any single server from becoming a bottleneck or point of failure.  
- Improves both performance and availability.

---

## Quick Example
- In a **monolithic system**, if the single server crashes → entire system is down.  
- In a **distributed system**, with replication + load balancing → traffic is rerouted to healthy servers, so the system stays available.  

# Consistency in Systems

## What is Consistency?
**Consistency** means that all clients accessing the system should see the same data at the same time.  

- A system is **consistent** when every client gets the same, correct, and most recent data.  
- If some clients see outdated or uncommitted data (called a **dirty read**), then the system is **not consistent**.  

---

## Consistency in Architectures
- **Monolithic Architecture** → Consistency is easier to maintain since all data is in a single system.  
- **Distributed Systems** → Consistency is harder to achieve because data is replicated across multiple nodes. Updates may take time to propagate to all replicas.  

---

## Factors Improving Consistency
- **Improving Network Bandwidth** → Faster synchronization between nodes.  
- **Stop the Read** → Temporarily block reads until updates are complete.  
- **Replication with Distance-Aware Strategies** → Prioritize updates to closer nodes first to reduce inconsistency.  

---

## Types of Consistency

### 1. Strong Consistency
- The system does **not allow read operations** until **all replicas are updated**.  
- Guarantees that every client sees the latest data.  
- ✅ Always correct, ❌ Slower due to waiting.  

### 2. Eventual Consistency
- The system **allows reads** even before all replicas are updated.  
- Some clients may see old data, but eventually all replicas will converge to the latest version.  
- ✅ Faster, ❌ May show stale data temporarily.  

### 3. Weak Consistency
- The system does **not guarantee** that all clients will see the most recent data.  
- Useful in cases like **real-time streaming or gaming**, where **speed is more important than accuracy**.  
- ✅ Very fast, ❌ No strong guarantees on correctness.  

---
# CAP Theorem

## What is CAP Theorem?
The **CAP Theorem** states that in a **distributed system**, it is impossible to simultaneously guarantee all three properties:  

- **C – Consistency** → Every client sees the same data at the same time.  
- **A – Availability** → The system is always up and responds to every request.  
- **P – Partition Tolerance** → The system continues to function even if network failures occur and nodes cannot communicate.  

👉 According to CAP, a distributed system can only provide **two of the three guarantees** at the same time. The third one must be compromised.  

---

## Trade-offs in CAP Theorem

### 1. Consistency + Partition Tolerance (CP System)
- **What it provides**: Strong consistency and fault tolerance.  
- **Compromises**: Availability is reduced (system may reject requests during failures).  
- **Example**: Traditional databases like HBase, MongoDB (in some configurations).  

---

### 2. Partition Tolerance + Availability (AP System)
- **What it provides**: System stays up and tolerant to network failures.  
- **Compromises**: Consistency is weaker (may serve stale data).  
- **Example**: DynamoDB, Cassandra.  

---

### 3. Availability + Consistency (CA System)
- **What it provides**: Data is consistent and system is available when no partitions exist.  
- **Compromises**: Partition tolerance (system fails if there is a network partition).  
- **Example**: Relational databases like MySQL, PostgreSQL (single-node setup).

# Important Note about CAP Theorem

In practice, **Partition Tolerance (P) is mandatory** for distributed systems, because network failures are unavoidable.  
Therefore, the real design choice is between:  

- **Consistency (C)** → All clients always see the same data, but the system may reject some requests during partitions.  
- **Availability (A)** → The system always responds, but some clients may see outdated data during partitions.  

👉 So, in real-world distributed systems, we always pick **CP** or **AP** trade-offs.  
The **CA combination** exists only in theory (single-node or non-distributed systems).  


---

## Summary
- **CAP is about trade-offs** → You can’t have it all in a distributed system.  
- The **system requirements** define which two properties should be prioritized.  

<img width="530" height="461" alt="image" src="https://github.com/user-attachments/assets/fa05e2a7-7a70-4a61-b89c-55751242cf9d" />

# Lamport Logical Clock

## What is Lamport Logical Clock?
A **Lamport Logical Clock** is a method used in distributed systems to **order events** (decide which happened before which) when there is **no global clock**.  

It was introduced by **Leslie Lamport** to solve the problem of **event ordering** in distributed environments.

---

## How it Works
1. **Each process** in the system maintains its own logical clock (an integer counter).  
2. **Rules**:
   - **Rule 1**: Every time a process performs an internal event, it increments its clock by 1.  
   - **Rule 2**: When a process sends a message, it includes its current clock value in the message.  
   - **Rule 3**: When a process receives a message, it updates its clock to:  
     ```
     max(local clock, received clock) + 1
     ```
3. Using this, we can decide the order of events, even if they occurred on different machines.  

---

## Example
- Process P1 sends a message with timestamp **5**.  
- Process P2’s clock is currently **3**.  
- When P2 receives the message, it updates its clock to **max(3, 5) + 1 = 6**.  
- This way, events are ordered consistently across the system.  

---

## Limitations
- Lamport clocks can tell us the **order of events**, but **cannot tell if two events are truly concurrent**.  
- For that, **Vector Clocks** are used.  

# Scalability

## What is Scalability?
**Scalability** is the ability of a system to handle increasing workloads (more users, data, or requests) by **adding resources**.  
A scalable system can grow without performance loss.  

---

## Types of Scalability

### 1. Vertical Scaling (Scaling Up)
Adding **more power** (CPU, RAM, storage) to a single server.  

- Example: Upgrading from 8 GB RAM to 32 GB RAM on the same machine.  

**✅ Pros**  
- Easy to implement  
- Less power consumption (fewer machines)  
- Easy to manage and maintain (only one system)  

**❌ Cons**  
- **Single point of failure** → If the server goes down, the whole system is unavailable  
- **Limited scale** → Bound by the maximum hardware capacity  
- Can become expensive when upgrading high-end hardware  

---

### 2. Horizontal Scaling (Scaling Out)
Adding **more servers** to distribute the load.  

- Example: Adding 5 more servers and using a load balancer to handle requests.  

**✅ Pros**  
- Overcomes all major drawbacks of vertical scaling  
- No single point of failure → If one server fails, others keep running  
- Virtually unlimited scaling by adding more nodes  
- Cost-efficient with commodity hardware  

**❌ Cons**  
- More complex to implement (requires load balancing, distributed databases, replication)  
- Higher operational overhead (monitoring and managing many servers)  

---

## Quick Analogy
- **Vertical Scaling** → Upgrading a single restaurant’s kitchen with bigger ovens.  
- **Horizontal Scaling** → Opening more restaurant branches to serve more customers.

  # Redundancy and Replication

## What is Redundancy?
**Redundancy** is the duplication of nodes or components so that when one node or component fails, another duplicate node is available to serve customers.  
It ensures **higher availability** by avoiding single points of failure.  

---

## Types of Redundancy

### 1. Active Redundancy
- All redundant units are **active and operational** at the same time.  
- Multiple nodes are connected to a **load balancer**.  
- Each node receives an **equal share of load**.  
- ✅ Advantage: Better resource utilization and fault tolerance.  

### 2. Passive Redundancy
- Only **one node is active**, while others remain **idle (standby mode)**.  
- If the active node fails, the passive node becomes active and continues serving requests.  
- ✅ Advantage: Simpler to implement.  
- ❌ Drawback: Standby resources are underutilized.  

---

## Replication

**Replication** = **Redundancy + Synchronization**  

It means not only having duplicate nodes (redundancy), but also **synchronizing data** between them to ensure consistency.

### Master-Slave Replication
- All **read and write operations** go to the **master node**.  
- If the master goes down, one of the slaves is promoted to master.  
- Ensures **availability** and **fault tolerance**.  

#### Synchronous Replication
- Changes are written to **master and slave at the same time**.  
- ✅ Strong consistency.  
- ❌ Slower (higher latency).  

#### Asynchronous Replication
- Changes are written to **master first**, then queued and written to slaves later.  
- ✅ Faster (low latency).  
- ❌ May serve stale data (eventual consistency).

  # Load Balancer

## What is Load Balancing?
**Load Balancing** is the process of efficiently distributing incoming network traffic across multiple servers (nodes) in a distributed system.  

It ensures:  
- **High scalability**  
- **High throughput**  
- **High availability**  

---

## Roles of a Load Balancer
- **Equal Distribution** → Distributes load evenly over all nodes  
- **Health Checks** → Detects if a node is not operational and routes requests to healthy nodes  
- **Ensures Reliability** → Maintains high availability and prevents overload  

---

## When to Use Load Balancing
- ❌ Not needed in **monolithic** or **vertically scaled systems** (single server).  
- ✅ Essential in **microservices** and **distributed systems** where traffic needs to be shared among many servers.  

---

## Challenges of Load Balancing
- **Single Point of Failure** → If the load balancer fails, client-server communication breaks.  
  - ✅ Solution: Use **redundancy** (active load balancer + passive backup).  

---

## Advantages of Load Balancing
- **Optimisation** → Better resource utilization and lower response time.  
- **Better User Experience** → Reduces latency and errors.  
- **Prevents Downtime** → Routes traffic only to operational servers.  
- **Flexibility** → Can re-route traffic during failures or maintenance.  
- **Scalability** → Handles sudden traffic spikes by adding servers.  
- **Redundancy** → Provides fault tolerance by redirecting traffic in case of server failure.  

---

## Load Balancing Algorithms

### Static Algorithms
1. **Round Robin** → Requests are distributed in rotation order.  
2. **Weighted Round Robin** → Like Round Robin but gives priority to servers with higher capacity.  
3. **IP Hash Algorithm** → Uses a hash of the client’s IP address to assign a server.  
4. **Source IP Hash** → Combines source and destination IPs to generate a hash key for request routing.  

### Dynamic Algorithms
1. **Least Connections** → Routes traffic to the server with the fewest active connections.  
2. **Least Response Time** → Routes requests to the server with the fastest response time.  

---
# Caching

## What is Caching?
**Caching** is the process of temporarily storing frequently accessed data in a faster storage (like memory) so future requests can be served more quickly.  

- Reduces latency  
- Improves system performance  
- Decreases database load  

💡 Example: When you revisit a website, your browser loads some data (like images, CSS files) from the cache instead of downloading it again.  

---

## Types of Caching

### 1. Client-Side Caching
- Data is stored on the client (e.g., browser cache, cookies, local storage).  
- ✅ Example: Web browsers caching images, CSS, and JavaScript files.  

### 2. Server-Side Caching
- Data is stored on the application server.  
- ✅ Example: A web server caching rendered HTML pages to avoid regenerating them for each user.  

### 3. Database Caching
- Frequently queried data is cached in memory.  
- ✅ Example: Using **Redis** or **Memcached** to store results of expensive database queries.  

### 4. Content Delivery Network (CDN) Caching
- Static content (images, videos, files) is cached on geographically distributed servers.  
- ✅ Example: Cloudflare CDN caching website assets for faster global delivery.  

### 5. Application/Distributed Caching
- Frequently accessed data is stored in a distributed cache system shared across multiple servers.  
- ✅ Example: Session caching in **Redis** for a distributed web application.  

---

## When to Use Caching?
- When the same data is requested frequently (e.g., user profiles, product listings).  
- When reducing latency is critical (e.g., serving content to global users).  
- When database load needs to be minimized.  
- When serving **static content** (e.g., images, videos, files).  
- When scaling systems to handle high traffic efficiently.  

❌ Avoid caching when:  
- Data changes very frequently and stale data can cause issues (e.g., real-time stock trading systems).  
- Strong consistency is required.  

 # Cache Eviction Strategies

## What is Cache Eviction?
Since cache storage is limited, **eviction strategies** define how to decide which data should be removed (evicted) when the cache is full, to make room for new data.

---

## Common Cache Eviction Policies

### 1. **LRU (Least Recently Used)**
- Removes the data that was least recently accessed.
- Assumes recently used data will be used again soon.
- ✅ Example: Browser history cache.

---

### 2. **LFU (Least Frequently Used)**
- Removes the data accessed the least number of times.
- Focuses on frequency of access.
- ✅ Example: An app cache where some rarely used features’ data is removed first.

---

### 3. **MRU (Most Recently Used)**
- Removes the data that was most recently accessed.
- Useful when older data is more likely to be reused.
- ✅ Example: In a music app, the most recently played song might be removed, assuming the user won’t play it again immediately.

---

### 4. **FIFO (First In First Out)**
- Removes the oldest data that entered the cache first.
- Works like a queue.
- ✅ Example: A print job buffer.

---

### 5. **LIFO (Last In First Out)**
- Removes the most recent data that entered the cache last.
- Works like a stack.
- ✅ Example: Undo operations in text editors.

---

### 6. **RR (Random Replacement)**
- Randomly removes any cache entry.
- Simple but unpredictable.
- ✅ Example: Used in hardware-level cache when tracking usage is expensive.

---

## Choosing a Strategy
- **LRU** → Best when recent access patterns matter (most common).  
- **LFU** → Best when some items are accessed very frequently.  
- **MRU** → Best when older data is more important than recent.  
- **FIFO/LIFO** → Simple to implement, used in some buffer systems.  
- **RR** → Used when tracking access history is too costly.  


# File-Based Storage System

## What is it?
A **File-Based Storage System** is a database management approach where data is stored directly in the form of files.  
Each file contains records, and applications must handle data retrieval, updates, and management manually.  

---

## Challenges of File-Based Systems

1. **Data Redundancy**
   - The same data may be stored in multiple files, leading to duplication and wasted storage.  
   - ❌ Example: Customer details saved separately in multiple files for billing and support.

2. **Poor Security**
   - File systems provide limited access control compared to modern databases.  
   - Unauthorized users may easily access or modify files.  

3. **Slow Performance**
   - Searching, updating, and retrieving data from large files is inefficient.  
   - No indexing or optimized query mechanisms → slower operations compared to DBMS.  

---

## Why Move Beyond File-Based Systems?
Modern **Database Management Systems (DBMS)** solve these challenges with:  
- Centralized data management  
- Improved security & access control  
- Reduced redundancy via normalization  
- Faster queries with indexing & optimization  

# Relational Database Management System (RDBMS)

## What is RDBMS?
An **RDBMS (Relational Database Management System)** is software that allows performing operations on a relational database, where data is stored in structured tables and relationships are defined between them.

---

## Key Features

- **Software** → Manages relational databases.  
- **Operations** → Store, manage, query, and retrieve data.  
- **Tables** → Data is represented in the form of rows & columns.  
- **Foreign Keys** → Relationships between tables are established using foreign keys.  

---

## Advantages of RDBMS

1. **No Data Redundancy and Inconsistency**  
   - Centralized storage avoids duplicate data.  

2. **Data Searching**  
   - Built-in SQL querying makes searching fast and efficient (no external program needed).  

3. **Data Concurrency**  
   - Provides locking mechanisms to allow multiple users to work simultaneously without conflicts.  

4. **Data Integrity**  
   - Enforces rules to maintain correct data (e.g., numeric columns can’t store alphabets).  
   - Unlike file systems, constraints are automatically checked.  

---

## Disadvantages of RDBMS

1. **Rigid Schema**  
   - Schema must be defined beforehand; not flexible for unstructured data.  

2. **High Cost**  
   - Licensing and maintenance can be expensive.  

3. **Scalability Issues**  
   - Vertical scaling is easier, but horizontal scaling (sharding) is difficult to implement.  

---
# NoSQL Databases

## What is NoSQL?
**NoSQL** stands for *Non-SQL* or *Non-Relational Database*.  
It provides flexible schema and horizontal scaling, unlike traditional RDBMS.  

NoSQL is an **umbrella term** for multiple types of databases.  

---

## Types of NoSQL Databases

### 1. Key-Value Database
- Data is stored as **key-value pairs** (like a dictionary).  
- Very fast lookups, widely used for **caching**.  
- ✅ Example: **Redis**, **Amazon DynamoDB**.  
- 💡 Use Case: Session management in web apps, caching user preferences.  

---

### 2. Document Database
- Data is stored in **JSON-like documents**.  
- Each document can have a different structure (dynamic schema).  
- ✅ Example: **MongoDB**, **CouchDB**.  
- 💡 Use Case: Content management systems (e.g., storing product catalogs in **e-commerce apps** like Amazon).  

---

### 3. Columnar Database
- Data is stored **column-wise instead of row-wise**.  
- Great for **analytical queries & aggregation**.  
- ✅ Example: **Apache Cassandra**, **HBase**.  
- 💡 Use Case: Large-scale **data analytics**, time-series data (e.g., Netflix analyzing user watch history).  

---

### 4. Graph Database
- Data is stored as **nodes and relationships** (graph structure).  
- Perfect for analyzing **networks & connections**.  
- ✅ Example: **Neo4j**, **Amazon Neptune**.  
- 💡 Use Case: **Social networks** like Facebook, LinkedIn (friends, followers, connections).  

---

## Hybrid Approach: NewSQL
- **Combines strengths of RDBMS & NoSQL**.  
- Provides **relationships (from RDBMS)** + **dynamic schema & horizontal scaling (from NoSQL)**.  
- ✅ Example: **Google Spanner**, **CockroachDB**.  

---

## When to Use NoSQL?
- When schema flexibility is required.  
- When dealing with very large-scale data.  
- When horizontal scaling is a priority.  

# Polyglot Persistence

## What is Polyglot Persistence?
**Polyglot Persistence** is the practice of using **different types of databases** (RDBMS, NoSQL, Graph, Columnar, etc.) in the same application, depending on the specific use case.  

Instead of forcing one database type for all requirements, the best-suited database is chosen for each feature.  

---

## Why Polyglot Persistence?
- Different parts of an application have different data needs.  
- No single database can efficiently handle all workloads.  
- Improves performance, scalability, and flexibility.  
<img width="745" height="426" alt="image" src="https://github.com/user-attachments/assets/ed17bb73-868b-4fa7-a1ca-8da6ee9a66dc" />

---

## Example Use Case
Imagine an **E-commerce Application**:  
- **RDBMS (MySQL / PostgreSQL)** → Orders, transactions, and inventory (structured relational data).  
- **NoSQL Document DB (MongoDB)** → Product catalogs (flexible schema, different attributes for each product).  
- **Key-Value Store (Redis)** → Shopping cart & session data (fast lookups).  
- **Graph DB (Neo4j)** → Product recommendations based on user connections or similar purchases.  
- **Columnar DB (Cassandra)** → Analytics on user behavior (fast aggregations on massive datasets).  

---

## Benefits
- Each database is used for what it does best.  
- Better performance & scalability.  
- Flexibility for evolving business needs.  

## Challenges
- Increased complexity in system design.  
- Requires expertise in multiple databases.  
- Harder to maintain and manage.  

# Normalization vs Denormalization

## Normalization
- Process of structuring data into **multiple related tables**.  
- Goal: **Eliminate redundancy** and ensure **data integrity**.  
- ✅ Example: Storing customer details in one table and orders in another, linked via a foreign key.  

---

## Denormalization
- Process of **combining data into a single table** or adding redundancy back into a database.  
- Goal: **Optimize performance** (mainly faster reads).  
- Often used in distributed systems where reducing network calls is critical.  

---

## Benefits of Denormalization
- ⚡ Faster data read operations.  
- 📋 Easier management and convenience for queries.  
- 🔄 High data availability.  
- 🌐 Fewer network calls (no need to join across multiple tables).  

---

## Challenges of Denormalization
- 📦 **Redundant data** → Wastage of memory.  
- 🔀 **Data inconsistency** → Same data stored in multiple places may get out of sync.  
- 🖊️ **Slower write operations** → Multiple updates needed for redundant fields.  
- ⚙️ Increased complexity in database design.  

---

## When to Use
- **Normalization** → Best when consistency, integrity, and storage efficiency are priorities.  
- **Denormalization** → Best when read performance and query speed are critical, especially in large-scale or distributed systems.  
# Indexing in Databases

## What is Indexing?
- **Indexing** creates a **lookup table** for a column, which stores the column values and pointers to the rows containing those values.  
- This allows the database to find records faster without scanning the entire table.  

---

## How It Works
- Indexes are usually stored using a **B-Tree data structure**.  
- B-Trees are balanced, multi-level search trees that make lookups efficient.  
- ✅ Before Indexing → Query Time Complexity = **O(n)** (linear search).  
- ✅ After Indexing → Query Time Complexity = **O(log n)** (tree search).  

---

## When to Use Indexing
- Best for **read-intensive databases** where queries are frequent.  
- Great for searching large datasets quickly.  

---

## When *Not* to Use Indexing
- ❌ **Write-intensive databases** → Every insert, update, or delete requires updating the index, which slows down performance.  
- ❌ **Small databases** → Overhead of maintaining an index is unnecessary since full scans are already fast.  

---

## Summary
- Indexing improves **read/query performance**.  
- Use for **large, read-heavy databases**.  
- Avoid for **write-heavy or small databases**.  

# Synchronous Communication

## What is Synchronous Communication?
- **Synchronous communication** means a **blocking call**, where the sender waits for the receiver to respond before continuing.  
- Ensures **consistency and reliability** in transactions.  

---

## Key Characteristics
- Blocking in nature → caller is paused until response arrives.  
- Strong **consistency** → ensures both parties are in sync.  
- Often used in **transactional systems**.  

---

## Industrial Use Cases
1. **Stock Market** 📈  
   - Trades must be executed in real-time with guaranteed consistency.  

2. **Bank Payments** 🏦  
   - Money transfer requires immediate confirmation from both banks.  

3. **Ticket Booking** 🎟️  
   - Seats must be locked and confirmed instantly to avoid double booking.  

4. **Real-Time Decision Making** ⚡  
   - Critical applications (e.g., healthcare systems, fraud detection) rely on immediate responses.  

---

## Summary
- ✅ Guarantees **accuracy and consistency**.  
- ❌ Can lead to **delays** if the receiver is slow or unavailable.  
- Best suited for **mission-critical, real-time systems**.  
# Asynchronous Communication

## What is Asynchronous Communication?
- **Asynchronous communication** is **non-blocking**.  
- The sender does not wait for an immediate response from the receiver.  
- The system continues other tasks while waiting for the result.  

---

## Key Characteristics
- Non-blocking in nature → improves responsiveness.  
- Helps achieve **scalability** in distributed systems.  
- Suitable for **long-running tasks**.  
- Response can be processed later (via callbacks, queues, or notifications).  

---

## When is Asynchronous Communication Necessary?

1. **Computation Takes a Lot of Time** ⏳  
   - Useful when processing is heavy (e.g., video rendering, ML model training).  

2. **Scalability of Applications** 📈  
   - Allows systems to handle many concurrent requests efficiently (e.g., chat systems, microservices).  

3. **Avoid Cascading Failure** 🔄  
   - If one service is slow or down, async queues prevent the entire system from failing.  

---

## Real-World Examples
- **Email sending** → User clicks "send", but the app doesn’t wait for the mail server.  
- **Food delivery apps** → Order is placed instantly, updates arrive asynchronously (order confirmed, out for delivery).  
- **Notification systems** → Push notifications may arrive later, but the app continues to function.  

---

## Summary
- ✅ Great for **long-running, high-scale, fault-tolerant** systems.  
- ❌ Not ideal when **immediate consistency** or real-time confirmation is required.

# Message-Based Communication

## 📌 Core Concept
- A **client (producer)** sends a request in the form of a **message**.  
- A **consumer** processes the request and may send back a response (also as a message).  
- Communication is **asynchronous** → the client is **not blocked** while waiting for a reply.  

---

## 🔑 Key Components
1. **Producer** → Service that creates and sends the message.  
2. **Consumer** → Service that receives and processes the message.  
3. **Agent (Message Broker)** → The intermediary (e.g., **Kafka**, **RabbitMQ**) that routes messages between producers and consumers.  

---

## 📨 Communication Models

### 1. Point-to-Point (P2P) Model
- **One producer → One consumer**.  
- A message is consumed by exactly **one receiver**.  
- Example: **Order Service → Payment Service**.  

### 2. Publish-Subscribe (Pub/Sub) Model
- **One producer → Many consumers**.  
- All subscribers to a topic receive the same message.  
- Example: **Notification Service** (send updates to **mobile app, email, SMS**).  

---

## ⚙️ Tools for Message-Based Communication
- **Apache Kafka**  
  - Distributed event streaming platform.  
  - Best for **Pub/Sub** at high scale.  
  - Real-time data pipelines and event-driven systems.  

- **RabbitMQ**  
  - Traditional message broker with flexible routing.  
  - Works well for **P2P** and **Pub/Sub**.  
  - Reliable delivery with acknowledgments.  

---

## ✅ Benefits
- Decoupling between services.  
- Asynchronous → **non-blocking** communication.  
- Fault tolerance → retries if a service is down.  
- Scales easily across distributed systems.  

---

## 📊 Quick Comparison

| Feature                  | Synchronous Communication | Point-to-Point (P2P) | Publish-Subscribe (Pub/Sub) |
|--------------------------|----------------------------|-----------------------|-----------------------------|
| Blocking?                | Yes (client waits)         | No (async)            | No (async)                  |
| Consumers per message    | 1                          | 1                     | Many                        |
| Use Cases                | Banking transactions, ticket booking | Order → Payment | Notifications, streaming data |
| Examples                 | REST API, gRPC             | RabbitMQ Queue        | Kafka Topics, RabbitMQ Exchange |

---

# 🌐 Web Server

## 📝 Core Concept
A **web server** is a combination of hardware and software that ensures web applications are always **up and running**, serving client requests over the internet.

---

## 🖥️ Hardware Side
- A **computer** that stores:
  - Website component files (HTML, CSS, JavaScript, images, etc.)
  - Web server software
- Connects to the **Internet** and exchanges data with client devices.

---

## ⚙️ Software Side
- Includes an **HTTP server**:
  - Understands **URLs** (web addresses) and the **HTTP protocol**.
  - Delivers website content to the user’s browser through domain names.
- Examples: **Apache, Nginx, Microsoft IIS**.

---

## 🔄 How It Works
1. A **browser** sends a request for a file (HTML, CSS, JS, image, etc.) using **HTTP**.  
2. The request reaches the **web server hardware**.  
3. The **HTTP server software**:  
   - Finds the requested file.  
   - Sends it back as an **HTTP response**.  
4. If the file is missing → returns a **404 error**.  

---


---

✅ **In short**:  
A **web server** = **Hardware (stores files)** + **Software (HTTP server to process requests)** → makes websites accessible to users.
# 📡 Communication Models in Client-Server Systems

## 🔑 What is a Protocol?
A **protocol** defines the rules, syntax, semantics, and timing of communication, along with error recovery methods.  
Examples: **HTTP, WebSocket, TCP, UDP**.

---

## 🖇️ Communication Models

### 1. Push
- **Definition**: The server proactively sends events/data to the client.  
- **Characteristic**: Proactive from the **server side**.  
- **Benefit**: Reduces server load (no repeated client polling).  

---

### 2. Pull / Polling
- **Definition**: Client sends a request, and the server responds.  
- **Characteristic**: Client repeatedly asks the server for new data.  
- **Downside**: Inefficient; high network usage.  

---

### 3. Long Polling
- **Definition**: Client sends a request, and the server holds the connection open until new data is available.  
- **Disadvantages**:  
  - Ordering issues  
  - Server stays busy (maintaining open connections)  

---

### 4. Socket
- **Definition**: A **socket** is an endpoint of a two-way connection between two nodes over a network.  
- **Characteristic**: Full **two-way communication** (bi-directional).  
- **Use Cases**:  
  - Real-time chat applications  
  - Online multiplayer gaming  

---

### 5. Server-Sent Events (SSE)
- **Definition**: Client subscribes to a server "stream"; server continuously pushes messages until one side closes.  
- **Characteristics**:  
  - **One-way connection** (Server → Client)  
  - **Long-lived connection**  
- **Examples**:  
  - Live sports score updates  
  - Real-time news feeds  

---

## 📌 Key Distinction
- **Push API**:  
  - Works via **service workers**  
  - Can send notifications **even when the site/app is not open** (e.g., mobile/desktop push notifications).  

- **SSE / WebSockets**:  
  - Work only when the user has the website/app **open in the browser**.  

---

## ⚙️ Protocol Mapping
- **Polling / Long Polling / SSE** → use **HTTP**.  
- **WebSockets** → use the **WebSocket protocol** (`ws://` or `wss://`) over TCP.  
- **Sockets (general)** → low-level connections using **TCP or UDP**.  

---

✅ **In short**: Communication models define *how* clients and servers exchange data. Protocols like **HTTP, TCP, WebSocket** provide the foundation, while models like **Polling, Push, SSE, and Sockets** are the strategies built on top.


# 🌐 Web Applications and Architectures

## 🔎 What is a Web Application?
- A **web application** is an application that runs on the internet.  
- **Difference between Website and Web Application**:  
  - **Website** → Static, mostly informational.  
  - **Web Application** → Dynamic, interactive, involves **client-server communication**.  

---

## 🖇️ Client-Server Interaction
- **Client**: The system that **initiates communication** over the network.  
  Examples: Mobile apps, web-based consoles, laptops.  
- **Server**: The system that **receives and processes requests** over the network.  
- Note: A **web server** can also act as a **client** when requesting data from another server.  

---

## ⚡ Requirements for Communication
- **Language Independent** (can work across platforms/languages)  
- **Fast** (low latency)  
- **Lightweight** (minimal overhead)  
- **Works over the Network**  

---

## 🔗 REST (Representational State Transfer)
A style/standard to enable communication between client and server.  
- For REST, the **server must expose REST APIs**.  
- REST API = **URI + HTTP Verb**  

### HTTP Verbs:
- **POST** → Create  
- **GET** → Read  
- **PUT** → Update  
- **DELETE** → Delete  

👉 Example: `173.76.310.45:7001/ios/nflx/plan-listing`  

---

## 🏛️ Service-Oriented Architecture (SOA)
- An architecture style that promotes **loose coupling** and **granular applications**.  
- Focus: **Reusability of components**.  

### ✅ Advantages
- Selective scaling  
- Different tech stacks can be used  
- Loose coupling  
- Agile development  

### ❌ Disadvantages
- Higher latency  
- Complex to secure  
- Cascading failures  
- Complex to understand  

---

## 🧩 Microservices Architecture
- An **evolved version of SOA**.  
- Most granular design → every service is **completely independent**.  
- Focus: **Decoupling** rather than reusability.  

### 🔄 SOA vs Microservices

| Feature | SOA | Microservices |
|---------|-----|---------------|
| Data Storage | Services can share | Independent for each microservice |
| Scalability | Less scalable | Highly scalable |
| Deployment | Time-consuming | Easy & faster |
| Focus | Reusability | Decoupling |

---

## 🏗️ N-Tier Architecture
- A web application can be designed with multiple **tiers (layers)**.  
- A **tier** = logical separation of components.  

### Types of Tiers:
- **1-Tier** → All components (frontend, backend, database) deployed on the same machine.  
- **2-Tier** → Frontend on one layer, Backend + Database on another.  
- **3-Tier** → Frontend, Backend, and Database each separated into independent layers.  

### ✅ Advantages of Tier Architecture:
- Easier modifications and updates  
- Dedicated roles/tasks for each layer  
- Improves maintainability and scalability  

---

## 📌 Key Takeaways
- **REST** enables lightweight communication using **HTTP verbs**.  
- **SOA** focuses on **reuse**; **Microservices** focus on **independence and scalability**.  
- **N-Tier architecture** separates concerns and improves maintainability of applications.  

# 🔐 Authentication vs Authorization

## 🧾 Authentication
- **Definition**: Verifies **who you are**.  
- **Purpose**: To confirm the identity of the user/system.  
- **Examples**:  
  - Login with username & password  
  - OTP verification  
  - Biometric authentication (fingerprint, face ID)  

---

## 🛡️ Authorization
- **Definition**: Defines **what you can do**.  
- **Purpose**: To control access levels and permissions after authentication.  
- **Examples**:  
  - Admin can create/delete users, but a regular user cannot  
  - A user can view their own bank balance but not others’  
  - Role-based access in applications (Admin, Manager, User)  

---

## 🔑 Key Difference

| Aspect            | Authentication ✅ | Authorization ✅ |
|-------------------|------------------|------------------|
| **Meaning**       | Confirms identity | Grants access rights |
| **Question**      | "Who are you?" | "What can you do?" |
| **Process**       | Done **before** authorization | Done **after** authentication |
| **Example**       | Entering email + password | Accessing admin dashboard |

---

👉 In short:  
- **Authentication = Identity**  
- **Authorization = Permissions**

# 🔐 Authentication Methods

## 1️⃣ Basic Authentication
- **Definition**: Client sends the **username and password** with each request (usually in the HTTP header).
- **Mechanism**: 
  - `Authorization: Basic <Base64(username:password)>`
  - The server decodes and verifies credentials.
- **Pros**: Very simple to implement.
- **Cons**: 
  - Credentials are sent with every request (even if Base64 encoded, it’s not secure).  
  - Should only be used with **HTTPS**.  
  - No session management.

---

## 2️⃣ Token-Based Authentication
- **Definition**: Instead of sending username & password on every request, the server issues a **token** after successful login.
- **Mechanism**:
  1. Client sends username & password **once**.
  2. Server validates and returns a **token** (e.g., JWT).  
  3. Client includes the token in every subsequent request:  
     `Authorization: Bearer <token>`
  4. Server verifies the token → grants/denies access.
- **Pros**: 
  - Credentials are not repeatedly sent.  
  - Tokens can have an expiry time → more secure.  
  - Scales well for distributed systems (stateless).  
- **Cons**: 
  - Token theft can still be a risk.  
  - Token revocation can be tricky.

---

## 3️⃣ OAuth (Open Authorization)
- **Definition**: An **authorization framework** that allows third-party applications to access a user’s resources **without sharing credentials**.
- **How it works**:
  - Instead of giving your password, you authorize a third-party app to access limited data (using **access tokens**).
- **Real-World Examples**:
  - "Login with Google" or "Login with Facebook".  
  - A fitness app accessing your Google Fit data.  
- **Roles in OAuth**:
  - **Resource Owner**: The user (you).  
  - **Client**: The application requesting access.  
  - **Authorization Server**: Issues tokens (e.g., Google, Facebook).  
  - **Resource Server**: Hosts protected resources (e.g., Gmail, Google Drive).  
- **Pros**:
  - Highly secure → no need to share passwords with third-party apps.  
  - Fine-grained control over access (scope).  
- **Cons**:
  - More complex to implement.  
  - If OAuth provider is down, third-party logins fail.

---

## 📌 Summary
- **Basic Auth** → Username & Password on every request (simple but insecure).  
- **Token Auth** → Server issues a reusable token after login (stateless, more secure).  
- **OAuth** → Authorization framework that allows **delegated access** using tokens (used by Google/Facebook logins).

  # 🛡️ Proxy Server

## 🔎 What is a Proxy Server?
- A **proxy server** is hardware or software that acts as an **intermediary** between a client and an application/server.  
- It provides a **gateway** between the user and the internet.

---

## ⚙️ How it Works
Client → [ Proxy Server ] → Server


- The **client** sends a request to the proxy.  
- The **proxy server** forwards the request to the destination server.  
- The **server** responds to the proxy, which then returns the response to the client.  
- ✅ The **server does not directly know the client**.

---

## 🎯 Benefits of Proxy Servers
- Hides client identity (anonymity).  
- Can filter traffic (security/firewall).  
- Helps in caching frequently accessed data.  
- Provides controlled access to restricted resources.  

---

# 🔄 Forward Proxy vs Reverse Proxy

## 🖥️ Forward Proxy
- **Definition**: A forward proxy sits **in front of the client** and hides the client’s identity.  
- **Flow**:  
Client → [ Forward Proxy ] → Server

- **Use Cases**:
- Anonymity for clients (server doesn’t know the client).  
- Access control (restricting clients to certain sites).  
- Bypassing geo-restrictions or firewalls.  

---

## 🖥️ Reverse Proxy
- **Definition**: A reverse proxy sits **in front of the server** and hides the server’s identity.  
- **Flow**:  
Client → [ Reverse Proxy ] → Server(s)

- **When to Use Reverse Proxy?**
- To **hide server details** from clients.  
- To make users feel like there’s only **one unified server**.  
- To provide **load balancing** across multiple backend servers.  
- To **swap or upgrade backend servers** without disrupting user traffic.  
- To **filter/block certain client requests** (security).  

---

## 📌 Key Difference
| Proxy Type        | Hides   | Positioned In Front Of | Used For |
|-------------------|---------|------------------------|----------|
| **Forward Proxy** | Client  | Client                 | Anonymity, access control, bypassing restrictions |
| **Reverse Proxy** | Server  | Server                 | Security, load balancing, scalability, server management |

---

## ⚙️ Real-World Examples

### 🔹 Forward Proxy
- **Squid Proxy**: Used for caching, filtering, and anonymity.  
- **Tor**: Routes traffic through multiple proxies for anonymity.  

### 🔹 Reverse Proxy
- **NGINX**  
- Can serve as a reverse proxy, load balancer, and cache.  
- Example config:
  ```nginx
  server {
      listen 80;
      server_name myapp.com;

      location / {
          proxy_pass http://backend_server;
      }
  }
  ```

- **Apache HTTP Server (mod_proxy)**  
- Reverse proxy module for Apache.  
- Example config:
  ```apache
  <VirtualHost *:80>
      ServerName myapp.com
      ProxyPreserveHost On
      ProxyPass / http://backend_server/
      ProxyPassReverse / http://backend_server/
  </VirtualHost>
  ```

---

✅ **Summary**:  
- **Forward Proxy** → Protects/represents the **client**.  
- **Reverse Proxy** → Protects/represents the **server**.  
- **NGINX & Apache** are the most widely used **reverse proxies** in production.  
