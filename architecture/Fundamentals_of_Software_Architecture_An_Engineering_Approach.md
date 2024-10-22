# Fundamentals of Software Architecture: An Engineering Approach by Mark Richards & Neal Ford

**Rating**: 8/10 – Hard to comprehend  
**Key Takeaway**: Architecture is about the important stuff… whatever that is. :)  
Everything in software architecture is a trade-off.  
Architecture is the stuff you can’t Google.  
There are no right or wrong answers in architecture—only trade-offs.

---

## **Anti-Patterns**

### **Frozen Caveman Anti-Pattern**

- Manifestation: Architects burned in the past by poor decisions or unexpected occurrences, making them particularly
  cautious in the future.

---

## **Metrics**

### **Instability Metric**

- Determines the volatility of a codebase:  
  `Instability = Efferent (outgoing) / (Efferent (outgoing) + Afferent (incoming))`

### **Abstractness**

- Ratio of abstract artifacts (abstract classes, interfaces) to concrete artifacts (implementations).

### **Distance from the Main Sequence**

- Formula:  
  `D = |A + I − 1|`  
  The result should be closer to 1.

---

## **Connascence**

Two components are **connascent** if a change in one would require the other to be modified to maintain overall system
correctness.

### **Static Connascence**

- Refers to source-code-level coupling (as opposed to execution-time coupling in dynamic connascence).

### **Types of Static Connascence:**

1. **Connascence of Name (CoN)**:  
   Multiple components must agree on the name of an entity.
2. **Connascence of Type (CoT)**:  
   Multiple components must agree on the type of an entity.
3. **Connascence of Meaning (CoM) or Connascence of Convention (CoC)**:  
   Multiple components must agree on the meaning of particular values.
4. **Connascence of Position (CoP)**:  
   Multiple entities must agree on the order of values.
5. **Connascence of Algorithm (CoA)**:  
   Multiple components must agree on a particular algorithm.

### **Dynamic Connascence**

1. **Connascence of Execution (CoE)**:  
   The order of execution of multiple components is important.
2. **Connascence of Timing (CoT)**:  
   The timing of the execution of multiple components is important.
3. **Connascence of Values (CoV)**:  
   Occurs when several values are interrelated and must change together.
4. **Connascence of Identity (CoI)**:  
   Occurs when multiple components must reference the same entity.

---

## **Rules for Connascence**

1. **Rule of Degree**:  
   Convert strong forms of connascence into weaker forms.
2. **Rule of Locality**:  
   As the distance between software elements increases, use weaker forms of connascence.

---

## **Non-Functional Requirements (NFR)**

- Architects created this term to distinguish architecture characteristics from functional requirements.

### **Architecture Characteristic Criteria**:

1. Specifies a non-domain design consideration.
2. Influences some structural aspect of the design.
3. Is critical or important to application success.

---

## **Architecture Characteristics**

### **Operational Characteristics**:

- Availability
- Continuity
- Performance
- Recoverability
- Reliability/Safety
- Robustness
- Scalability

### **Structural Characteristics**:

- Configurability
- Extensibility
- Installability
- Leverageability/Reuse
- Localization
- Maintainability
- Portability
- Upgradability

### **Cross-Cutting Characteristics**:

- Accessibility
- Archivability
- Authentication
- Authorization
- Legal Compliance
- Privacy
- Security
- Supportability
- Usability

---

## **General Principles**

- **Never shoot for the best architecture, but rather the least worst architecture.**
- **There are no wrong answers in architecture, only expensive ones.**
- **Architects must ensure that developers understand the purpose of the fitness function before imposing it on them.**

---

## **Coupling**

### **Stamp Coupling**

- Occurs when modules share a composite data structure and use only parts of it (e.g., passing a whole record to a
  function that needs only one field of it).

#### **Resolution**:

- Create private RESTful API endpoints.
- Use field selectors in the contract.
- Use GraphQL to decouple contracts.
- Use value-driven contracts with consumer-driven contracts (CDCs).
- Use internal messaging endpoints.

---

## **Fallacies of Distributed Computing**

1. The Network Is NOT Reliable.
2. Latency Is NOT Zero.
3. Bandwidth Is NOT Infinite.
4. The Network Is NOT Secure.
5. The Topology Does NOT Never Change.
6. There Is NOT Only One Administrator.
7. Transport Cost Is NOT Zero.
8. The Network Is NOT Homogeneous.

---

## **Architecture Styles**

### **Layered Architecture Style**

- **Strengths**: Overall cost and simplicity.

### **Pipeline Architecture Style**

- **Strengths**: Overall cost and simplicity combined with modularity.

#### **Pipeline Components**:

1. **Producer**: The starting point of a process, outbound only, sometimes called the source.
2. **Transformer**: Accepts input, optionally performs a transformation, then forwards it (similar to map in functional
   programming).
3. **Tester**: Accepts input, tests criteria, optionally produces output (similar to reduce in functional programming).
4. **Consumer**: Termination point of the pipeline, sometimes persists results or displays them on a UI.

### **Microkernel Architecture Style**

- **Strengths**: Simplicity and overall cost.
- **Weaknesses**: Scalability, fault tolerance, and extensibility.

### **Service-Based Architecture Style**

- Logical partitioning in the database should be fine-grained to better control changes.
- **Strengths**: Simplicity, overall cost, testability, deployability, fault tolerance, and availability.
- **Weaknesses**: Scalability and elasticity.

### **Event-Driven Architecture Style**

- **Strengths**: Performance, scalability, and fault tolerance.
- **Weaknesses**: Simplicity and testability.

### **Space-Based Architecture Style**

- **Strengths**: Scalability and high-performance distributed systems.
- **Weaknesses**: Complexity, testing challenges, and high cost of testing.

### **Microservices Architecture Style**

- **Negative Trade-Off**: Reuse creates coupling.
- **Guidelines**: Avoid transactions in microservices; focus on fixing granularity instead.
- **Compensating Transaction Framework**: Sends undo commands to previous writes on failure.
- **When Transactions Are Necessary**: If they are the dominant feature of the architecture, mistakes were made.

---

## **Decision Criteria**

1. Understand important aspects of the domain.
2. Consider architecture characteristics that impact structure.
3. Data architecture and organizational factors.
4. Knowledge of process, teams, and operational concerns.
5. Domain/architecture isomorphism.
6. Monolith vs. distributed systems.
7. Where should data live?
8. What communication styles between services—synchronous or asynchronous?  
   (Use synchronous by default, asynchronous when necessary.)

---

## **Risk Analysis**

- When leveraging the risk matrix, consider the **impact dimension** first and the **likelihood dimension** second.

---

## **Anti-Patterns**

### **Architecture Sinkhole Anti-Pattern**

- Occurs when requests move from layer to layer with no business logic being performed at each layer.

### **Cover Your Assets Anti-Pattern**

- Document-driven processes produce less-than-useful requirements and specifications, avoiding important decisions to
  evade mistakes. To avoid this, authors elaborate on alternatives instead of making decisions.

---