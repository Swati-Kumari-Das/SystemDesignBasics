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

---

## Summary
- **CAP is about trade-offs** → You can’t have it all in a distributed system.  
- The **system requirements** define which two properties should be prioritized.  

<img width="530" height="461" alt="image" src="https://github.com/user-attachments/assets/fa05e2a7-7a70-4a61-b89c-55751242cf9d" />

