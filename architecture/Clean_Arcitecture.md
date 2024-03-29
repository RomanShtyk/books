# book Clean Architecture: A Craftsman's Guide to Software Structure and Design

9/10 - must read, but too many stories from life

**The goal of software architecture is to minimize the human resources required to build and
maintain the required system.**

**The overconfidence will drive the redesign into the same mess as the original project.**

* If you give me a program that works perfectly but is impossible to change, then it won’t work when
  the requirements change, and I won’t be able to make it work. Therefore the program will become
  useless.
* If you give me a program that does not work but is easy to change, then I can make it work, and
  keep it working as requirements change. Therefore the program will remain continually useful.

**Paradigms:**

* STRUCTURED PROGRAMMING - imposes discipline on direct transfer of control (no goto)
* OBJECT-ORIENTED PROGRAMMING - imposes discipline on indirect transfer of control.
* FUNCTIONAL PROGRAMMING - imposes discipline upon assignment (basically all is immutable)

**Indeed, the way encapsulation is partially repaired is by introducing the public, private, and
protected keywords into the language. This, however, was a hack necessitated by the technical need
for the compiler to see those variables in the header file.**

**Variables in functional languages do not vary.**

**Version control systems are good examples of event sourcing - particularly Git. Each commit is
stored as an event representing a change of state - files/lines to be added/removed. Git is a
distributed version control system.**

**SRP - A module should be responsible to one, and only one, actor.**

**Gather into components those classes that change for the same reasons and at the same times.
Separate into different components those classes that change at different times and for different
reasons.**

**Don’t force users of a component to depend on things they don’t need.**

* SDP - Stable Dependency Principle
* SAP - Stable Abstractions Principle
* CCP - Common Closure Principle

**Any organization that designs a system will produce a design whose structure is a copy of the
organization’s communication structure.**

**A strict definition of “level” is “the distance from the inputs and outputs.”**

**Source code dependencies must point only inward, toward higher-level policies.**

The Humble Object pattern is a design pattern that was originally identified as a way to help unit
testers to separate behaviors that are hard to test from behaviors that are easy to test.

Gateways are polymorphic interfaces that contain methods for every create, read, update, or delete
operation that can be performed by the application on the database.

Android app developers write firmware when they don’t separate their business logic from the Android
API.

1. “First make it work.” You are out of business if it doesn’t work.
2. “Then make it right.” Refactor the code so that you and others can understand it and evolve it as
   needs change or are better understood.
3. “Then make it fast.” Refactor the code for “needed” performance.

Something I see on a regular basis is an overly liberal use of the public access modifier in
languages such as Java. It’s almost as if we, as developers, instinctively use the public keyword
without thinking (Hello Kotlin)

“Périphérique anti-pattern of ports and adapters.” - basically call data from ui layer

The whole point is to highlight that your best design intentions can be destroyed in a flash if you
don’t consider the intricacies of the implementation strategy.
