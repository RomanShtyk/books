“A Philosophy of Software Design by John Ousterhout”

Chapter 1: Introduction (It's All About Complexity)

Complexity is the core limitation: Programming is only constrained by our ability to understand systems we create, not
physical laws or coordination—if you can visualize it, you can implement it

Complexity accumulates inevitably

Waterfall model fails for software whereas incremental development works: Agile approaches design/implement/evaluate
small subsets iteratively, fixing problems
while systems are still small and leveraging software's malleability

Design is continuous: Software design never ends—it spans the entire system lifecycle because incremental development
requires ongoing design thinking and adjustments

Chapter 2: “The Nature of Complexity”

**Complexity** is anything related to the structure of a software system that makes it hard to understand and modify the
system.

Symptoms of complexity include:

- Change amplification: The first symptom of complexity is that a seemingly simple change requires code modifications in
  many different places.
- Cognitive load: The second symptom of complexity is cognitive load, which refers to how much a developer needs to know
  in order to complete a task. Sometimes an approach that requires more lines of code is actually simpler, because it
  reduces cognitive load.
- Unknown unknowns: The third symptom of complexity is that it is not obvious which pieces of code must be modified to
  complete a task, or what information a developer must have to carry out the task successfully.

Complexity comes from an accumulation of dependencies and obscurities. As complexity increases, it leads to change
amplification, a high cognitive load, and unknown unknowns

Chapter 3
Working Code Isn’t Enough

Tactical programming is getting task done without regard for the overall design of the system. It is often the default
approach, but it leads to complexity and maintenance problems.

Invest 20% into improving the design of system, this approach will outpace the tactical approach in the middle run

Chapter 4
Modules Should Be Deep

The best modules are those whose interfaces are much simpler than their implementations, these are called deep.
The extreme of the “classes should be small” approach is a syndrome I call **classitis**

Chapter 5
Information Hiding (and Leakage)

**Red Flag:** Information Leakage
Information leakage occurs when the same knowledge is used in multiple places, such as
two different classes that both understand the format of a particular type of file.

**Red Flag:** Temporal Decomposition
In temporal decomposition, execution order is reflected in the code structure:
operations that happen at different times are in different methods or classes. If the same knowledge is used at
different points in execution, it gets encoded in multiple places, resulting in information leakage.

Information hiding can often be improved by making a class slightly larger.

If the API for a commonly used feature forces users to learn about other features that are rarely used, this increases
the cognitive load on users who don’t need the rarely used features.

Chapter 6
General-Purpose Modules are Deeper

