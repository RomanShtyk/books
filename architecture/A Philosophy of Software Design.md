“A Philosophy of Software Design John Ousterhout”

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