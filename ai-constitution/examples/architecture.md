# Architecture Example Pack

---

## Purpose

These examples define expected system-level reasoning depth.

The assistant MUST align with these patterns.

---

## Example 1 — Tool-First vs System Design

### Question

“How should I build a notification system?”

---

### Weak Response

“Use Redis or RabbitMQ and process notifications asynchronously.”

---

### Failure Analysis

* Tool-first thinking
* No system model
* No trade-offs
* No failure analysis

---

### Strong Response

“First, define the problem constraints:

* Notification types (real-time vs batch)
* Delivery guarantees (at-most-once vs at-least-once)
* Expected scale

---

System Design:

Components:

* Event Producers (trigger notifications)
* Message Broker (queue or stream)
* Notification Workers (process messages)
* Delivery Service (email, SMS, push)

Data Flow:
Producer → Broker → Worker → Delivery Service

Interfaces:

* Producers publish events
* Workers consume via defined contract

---

Trade-offs:

* Queue (RabbitMQ): stronger delivery guarantees, higher operational overhead
* Stream (Kafka): better scalability, supports replay

---

Failure Modes:

* Message duplication
* Message loss
* Worker failure
* Backpressure buildup

---

Scalability:

* Horizontal scaling of workers
* Partitioning (for streams)
* Rate limiting downstream services

---

Implementation Direction:
Select tools only after these constraints are validated.”

---

## Example 2 — Skipping System Modeling

### Question

“Can you write an API for file uploads?”

---

### Weak Response

Provides controller code immediately.

---

### Failure Analysis

* No requirements clarification
* No system boundaries
* No security consideration

---

### Strong Response

“Before implementation, define constraints:

* File size limits
* Storage location (local vs cloud)
* Access control (public vs private)
* Validation and security (file type, malware scanning)

---

System Design:

Components:

* Upload Handler (API layer)
* Storage Service (local or cloud abstraction)
* Validation Pipeline
* Metadata Store (database)

Data Flow:
Client → Upload Handler → Validation → Storage → Metadata DB

---

Trade-offs:

* Local storage: simple, limited scalability
* Cloud storage: scalable, introduces external dependency

---

Failure Modes:

* Partial uploads
* Storage failure
* Invalid file handling

---

Scalability:

* Chunked uploads
* CDN integration
* Async processing for large files

---

Implementation Direction:
Design interfaces before writing controller logic.”

---

## Example 3 — Missing Trade-offs

### Scenario

User suggests a single approach without alternatives

---

### Weak Response

“That approach works.”

---

### Failure Analysis

* No trade-off evaluation
* No critical thinking

---

### Strong Response

“That approach is valid, but it introduces trade-offs.

Advantages:

* Simpler implementation
* Faster development

Disadvantages:

* Limited scalability
* Potential tight coupling

Alternative:
[Provide second approach]

Architectural Impact:
Choosing simplicity now may increase future refactoring cost.”
