#book Fundamentals of Software Architecture. An Engineering Approach by Mark Richards & Neal Ford
8/10 hard to comprehend
Architecture is about the important stuff…whatever that is. :)
Everything in software architecture is a trade-off.
Architecture is the stuff you can’t Google.
There are no right or wrong answers in architecture—only trade-offs.

The Frozen Caveman Anti-Pattern manifests in architects who have been burned in the past by a poor
decision or unexpected occurrence, making them particularly cautious in the future

The instability metric determines the volatility of a code base (efferent(out) / efferent(out) +
afferent(in))

Abstractness is the ratio of abstract artifacts (abstract classes, interfaces, and so on) to
concrete
artifacts (implementation).

Distance from the Main Sequence D=|A+I−1| should be closer to 1

Two components are connascent if a change in one would require the other to be modified in order to
maintain the overall correctness of the system.

Static connascence refers to source-code-level coupling (as opposed to execution-time coupling
Dynamic connascence)

Connascence of Name (CoN)
Multiple components must agree on the name of an entity.

Connascence of Type (CoT)
Multiple components must agree on the type of an entity.

Connascence of Meaning (CoM) or Connascence of Convention (CoC)
Multiple components must agree on the meaning of particular values

Connascence of Position (CoP)
Multiple entities must agree on the order of values.

Connascence of Algorithm (CoA)
Multiple components must agree on a particular algorithm.

DYNAMIC CONNASCENCE

Connascence of Execution (CoE)
The order of execution of multiple components is important.

Connascence of Timing (CoT)
The timing of the execution of multiple components is important.

Connascence of Values (CoV)
Occurs when several values relate on one another and must change together.

Connascence of Identity (CoI)
Occurs when multiple components must reference the same entity.

Rule of Degree: convert strong forms of connascence into weaker forms of connascence
Rule of Locality: as the distance between software elements increases, use weaker forms of
connascence

NFR: Architects created that term to distinguish architecture characteristics from functional
requirements

An architecture characteristic meets three criteria:
• Specifies a nondomain design consideration
• Influences some structural aspect of the design
• Is critical or important to application success

Architecture Characteristic:
Operationals: Availability, Continuity, Performance, Recoverability,Reliability/Safety, Robustness,
Scalability
Structural: Configurability, Extensibility, Installability,Leveragability/Reuse, Localization,
Maintainability, Portability, Upgradability
Cross-Cutting: Accessibility, Archivability, Authentication, Authorization, Legal Compliance,
Privacy, Security, Supportability, Usability.

Never shoot for the best architecture, but rather the least worst architecture.

There are no wrong answers in architecture, only expensive ones.

Architects must ensure that developers understand the purpose of the fitness function before
imposing it on them.

Stamp coupling occurs when modules share a composite data structure and use only parts of it,
possibly different parts (e.g., passing a whole record to a function that needs only one field of
it). Resolve with:
• Create private RESTful API endpoints
• Use field selectors in the contract
• Use GraphQL to decouple contracts
• Use value-driven contracts with consumer-driven contracts (CDCs)
• Use internal messaging endpoints

Fallacies of distributed computing:
1.The Network Is NOT Reliable
2.Latency Is NOT Zero
3.Bandwidth Is NOT Infinite
4.The Network Is NOT Secure
5.The Topology NOT Never Changes

6. There Is NOT Only One Administrator
7. Transport Cost Is NOT Zero
8. The Network Is NOT Homogeneous

Architecture sinkhole anti-pattern - occurs when requests move from layer to layer as simple
pass-through processing with no business logic performed within each layer

Layered Architecture Style - Overall cost and simplicity are the primary strengths of the layered
architecture style.

Pipeline Architecture Style - Overall cost and simplicity combined with modularity are the primary
strengths of the pipeline
architecture style.
Filters:
Producer
The starting point of a process, outbound only, sometimes called the source.
Transformer
Accepts input, optionally performs a transformation on some or all of the data, then forwards it to
the outbound pipe. Functional advocates will recognize this feature as map.
Tester
Accepts input, tests one or more criteria, then optionally produces output, based on the test.
Functional programmers will recognize this as similar to reduce.
Consumer
The termination point for the pipeline flow. Consumers sometimes persist the final result of the
pipeline process to a database, or they may display the final results on a user interface screen.

Microkernel Architecture Style:
Similar to the layered architecture style, simplicity and overall cost are the main strengths of the
microkernel architecture style, and scalability, fault tolerance, and extensibility its main
weaknesses.

Service-Based Architecture Style:
Make the logical partitioning in the database as fine-grained as possible while still maintaining
well-
defined data domains to better control database changes within a service-based architecture.
Simplicity and overall cost are two other drivers that differentiate this architecture style from
other,
more expensive and complex distributed architectures, such as microservices, event-driven
architecture, or even space-based architecture.
Scalability only rates three stars due to the coarse-grained nature of the services, and
correspondingly, elasticity only two stars.
Breaking apart an application into separately deployed
domain services using this architecture style allows for faster change (agility), better test
coverage
due to the limited scope of the domain (testability), and the ability for more frequent deployments
carrying less risk than a large monolith (deployability).
Fault tolerance and overall application availability also rate high for service-based architecture.

Event-Driven Architecture Style:
Mediator(orchestrator) and Broker(choreographer) styles
This style gains five stars for performance, scalability, and fault tolerance, the primary strengths
of this architecture style, but overall simplicity and testability rate relatively low. Finally,
event-driven architectures are highly evolutionary

Space-Based Architecture Style:
Distribute both processing and data storage across multiple servers, creating a "shared nothing"
system.
Data isn't stored on a central server, but rather accessible by all processing units involved.
Overall, space-based architecture offers a powerful approach for building scalable and
high-performance distributed applications, especially for scenarios requiring real-time processing
and fast data access.
Space-based architecture is a very complicated architecture style due to the use of caching and
eventual consistency of the primary data store, which is the ultimate system of record.
Scalability and elasticity make testing in this architecture style extremely challenging and costly.
Simulating hundreds of thousands of concurrent users at peak load requires complex and expensive
setups. This often forces high-volume testing into production environments, posing significant risk
to regular operations.

Microservices Architecture:
The negative trade-off of reuse is coupling!!!
Don’t do transactions in microservices—fix granularity instead!
Compensating transaction framework - sends undo to previous writes on fail
A few transactions across services is sometimes necessary; if it’s the dominant feature of the
architecture, mistakes were made!

Decision Criteria:
The domain - Architects should understand many important aspects of the domain
Architecture characteristics that impact structure
Data architecture
Organizational factors
Knowledge of process, teams, and operational concerns
Domain/architecture isomorphism
Monolith versus distributed
Where should data live?
What communication styles between services—synchronous or asynchronous?(Use synchronous by default,
asynchronous when necessary.)

Analyzing Architecture Risk:
When leveraging the risk matrix to qualify the risk, consider the impact dimension first and the
likelihood dimension second.

Cover Your Assets Anti-pattern
Document-driven software processes often produce less-than-useful requirements and specifications
because the authors evade making important decisions. To avoid making a mistake, the authors take a
safer course and elaborate upon alternatives.
