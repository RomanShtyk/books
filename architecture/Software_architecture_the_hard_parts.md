#book Software Architecture: The Hard Parts by Neal Ford

“software architecture is the stuff that’s hard to change later.”

ADR: A short record noun phrase containing the architecture decision
Context
In this section of the ADR we will add a short one- or two-sentence description of the problem, and
list the alternative solutions.
Decision
In this section we will state the architecture decision and provide a detailed justification of the
decision.
Consequences
In this section of the ADR we will describe any consequences after the decision is applied, and also
discuss the trade-offs that were considered.

Modern trade-off analysis:

1. Find what parts are entangled together.
2. Analyze how they are coupled to one another.
3. Assess trade-offs by determining the impact of change on interdependent systems.

Why is more important than how

static coupling describes how services are wired together, whereas dynamic coupling describes how
services call one another at runtime

general advice: try to avoid cross-service transactions

If the codebase is decomposable, the next step is to determine if the source code is largely an
unstructured mess with no clearly definable components. If that’s the case, then tactical forking is
probably the right approach. However, if the source code files are structured in a way that combines
like functionality within well-defined components, then use a component-based decomposition
approach.

Chapter 1: What Does an Architect Do?
Architects Shape Systems: Rather than simply designing, architects influence the form and evolution
of software systems through key decisions.
Tradeoffs are Central: Architecture is about navigating tradeoffs. There's rarely a single "right"
answer, but understanding the consequences of these choices is crucial.
Communication is Key: Architects must effectively communicate complex ideas to diverse stakeholders,
from developers to business executives.

Chapter 2: Evolutionary Architecture
Embrace Change: Software systems constantly evolve. Architectures must be adaptable, not rigid.
Fitness Functions: Define clear quality attributes (scalability, performance, etc.) to guide
decision-making and measure an architecture's "fitness" over time.
Incremental Change: Favor small, iterative architectural changes. This allows for course correction
and reduces the risk of big failures.

Chapter 3: Architecting for Scale
It's Not Just About Technology: Scaling involves people and processes as much as technology choices.
Data is Often the Bottleneck: Data storage and access patterns can become scaling limits if not
carefully designed.
Premature Scaling is Risky: Obsessing over scaling too early can lead to over-engineered solutions
that stifle agility.

Chapter 4: Modular Architectures
Build with Small, Cohesive Modules: Well-defined modules promote reusability, independent
development, and easier understanding of the system.
Strong Contracts, Loose Coupling: Modules should have clear interfaces (contracts) while minimizing
dependencies on each other's internals.
Hiding Implementation Details: Encapsulation within modules keeps the system maintainable and allows
for change without cascading effects.
