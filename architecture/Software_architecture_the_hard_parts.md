# Software Architecture: The Hard Parts by Neal Ford

**Key Quote:** "Software architecture is the stuff that’s hard to change later."

## ADRs (Architecture Decision Records)

* **Context:**  Briefly describe the problem and potential solutions.
* **Decision:**  Clearly state the chosen architectural decision with a detailed rationale.
* **Consequences:**  Discuss the impacts of the decision and the considered trade-offs.

## Modern Trade-off Analysis

1. **Identify Entanglement:** Determine what system parts are interconnected.
2. **Analyze Coupling:**  Understand how services interact.
3. **Assess Trade-offs:**  Evaluate the impact of change on dependent systems.

## Why Over How

Prioritize understanding the underlying rationale before implementation details.

## Coupling

* **Static Coupling:**  How services are linked.
* **Dynamic Coupling:**  How services interact at runtime.

**General Advice:**  Minimize cross-service transactions when possible.

## Core Concepts Overview

* **Chapter 1: What Does an Architect Do?**
  * **Architects Shape Systems:** Influence software development through critical decisions.
  * **Tradeoffs are Central:** Navigating tradeoffs is at the heart of architecture.
  * **Communication is Key:**  Architects must effectively convey complex concepts.

* **Chapter 2: Evolutionary Architecture**
  * **Embrace Change:**  Architectures must be adaptable.
  * **Fitness Functions:**  Define quality attributes to guide decision-making.
  * **Incremental Change:**  Favor smaller, iterative improvements to manage risk.

* **Chapter 3: Architecting for Scale**
  * **It's Not Just About Technology:**  Consider people and processes alongside technology.
  * **Data is Often the Bottleneck:**   Storage and access need careful design for scalability.
  * **Premature Scaling is Risky:**  Focus on agility first.

* **Chapter 4: Modular Architectures**
  * **Small, Cohesive Modules:**  Promote reusability, independent development, and understanding.
  * **Strong Contracts, Loose Coupling:**  Prioritize clear interfaces, minimize internal
    dependencies.
  * **Encapsulation:** Keep the system maintainable by hiding implementation details.

* **Chapter 5: Microservices**
  * **Promises:** Modularity, scalability, and team autonomy.
  * **Complexities:**  Inherent challenges of distributed systems, logistical overhead, service
    boundaries.
  * **Not a Magic Solution:**  Carefully assess suitability based on team experience, system
    structure, and operational capacity.

* **Chapter 6: Pulling Apart Operational Data**
* **Data Disintegrators:** Considerations when splitting a database into multiple smaller ones:
    * **Change Control:** Database changes can impact multiple services.
    * **Connection Management:** Monitor database connection limits.
    * **Scalability:** Data partitioning improves scalability.
    * **Fault Tolerance:** Avoid single points of failure.
    * **Architecture Quantum:** Evaluate the need for different database types.

* **Data Integrators:** Challenges when databases span multiple services:
    * **Data Relationships:** Maintain referential integrity.
    * **Database Transactions:** Manage transactions across services.

* **Steps to Splitting a Database**
    * **Analyze and Create Data Domains:** Discover logical groupings of data.
    * **Assign Tables:** Allocate tables to data domains.
    * **Allow Cross-Schema Joins:** Initially maintain connectivity.
    * **Separate Connections:** Isolate database connections per data domain.
    * **Replace Joins with Service Calls:** Refactor to service interactions.
    * **Move to Separate Servers:** Physically split databases.
    * **Cleanup:** Remove connections to the old database.

* **Selecting Database Types:**
    * **Relational:** Best for structured data, complex queries, consistency needs.
    * **Key-Value:** Simple data access with high read/write throughput.
    * **Document:** Rich document structures, multiple indexes.
    * **Column Family:** High volume and high-performance needs.
    * **Graph:** Modeling highly connected data.
    * **NewSQL:** Scalability of NoSQL with ACID properties.
    * **Cloud Native:** A mix of database solutions.
    * **Time-Series:** Optimized for time-based data.
      ![img.png](res/img.png)

## Decomposition Strategies

* **Tactical Forking:**  Suitable for unstructured codebases. Duplicate services and then remove
  redundancy.
* **Component-Based Decomposition:**  Preferred when source code demonstrates clear, well-defined
  components.

![img.png](res/Component-based decomposition.webp)

## Component-based decomposition

1. **Identify and Size Components Pattern**
   * Not too big, not too small == ~ 1-2 standard deviation from average.
   * Size == # statements.
   * Too big –> split.
2. **Gather Common Domain Components Pattern**
   * To eliminate duplication.
   * Shared domain logic, not infrastructure.
   * Mostly a manual process.
3. **Flatten Components Pattern** The Flatten Components decomposition pattern is used to move
   orphaned classes to create well-defined components that exist only as leaf nodes of a directory
   or name‐ space, creating well-defined subdomains (root namespaces) in the process. **Regardless** of
   the direction of flattening, make sure source code files reside only in leaf node namespaces or
   directories so that source code can always be identified within a specific component.
4. **Determine Component Dependencies Pattern**
   * Coupling is the most significant factor in determining the overall success and feasibility of
     breaking a monolith.
   * Both afferent and efferent coupling.
   * Consider refactor to reduce coupling (like splitting a component in two).
5. **Create Component Domains Pattern**
   * Domains =~ service.
   * Package structure: ss.customer.billing.payments.MonthlyBilling,
     app.domain.subdomain.component.class
   * Move components to appropriate domain.
6. **Create Domain Services Pattern**
    * Service-based architecture.
    * Don’t apply this pattern until all domains have been identified and refactored.
