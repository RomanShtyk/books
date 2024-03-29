# Domain-Driven Design Quickly [Marinescu, Floyd, Avram, Abel]:

7/10 - not bad, gives some common sense rules for architecture design

## Key Concepts

* **The Ubiquitous Language:** A shared glossary for developers and business stakeholders.
* **Entity:** A uniquely identifiable object.
* **Value Object:**  Represents a value, must be immutable.
* **Object Size:**  Keep objects focused by grouping properties conceptually (e.g., address,
  personalInfo).
* **Cohesion:**
    * **Communicational cohesion:**  Group things that change for the same reason.
    * **Functional cohesion:** Group things that work together to achieve a single purpose.

## Patterns & Strategies

* **Customer-Supplier Pattern:** Manage dependencies between teams.
* **Anti-Corruption Layer:** Translate between different domain models.
* **Core Domain:** Focus on the essential heart of your system.

## Best Practices

* **Hands-on Modeling:**  Modelers should actively code.
* **Concrete Scenarios:** Base abstract thinking on real-world use cases.
* **Focused Application:** Use DDD strategically, not for everything.
* **Embrace Experimentation:**  Iterate and expect to learn from mistakes.
