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

Over-specialization is a primary cause of complexity in software

General-purpose code is simpler, cleaner, and easier to understand than specialized code

Design Principles
Module Level

General-purpose APIs create deeper modules with better information hiding
Designing for generality produces simpler, more maintainable interfaces

Code Level

Eliminating special cases simplifies code
Common-case code that handles edge cases reduces complexity

Removing special cases can improve performance

Chapter 7
Different Layer, Different Abstraction

If a system contains adjacent layers with similar abstractions, this is a red flag that suggests a problem with the
class decomposition.
Unfortunately, I haven’t found a better solution than contexts for passing information across layers.

Chapter 8
Pull Complexity Downwards

Pulling complexity down makes the most sense if
(a) the complexity being pulled down is closely related to the class’s existing functionality,
(b) pulling the complexity down will result in simplifications elsewhere in the application, and
(c) pulling the complexity down simplifies the class’s interface.

When developing a module, look for opportunities to take a little bit of extra suffering upon yourself in order to
reduce the suffering of your users.

Chapter 9
Better Together Or Better Apart?

If the same piece of code (or code that is almost the same) appears over and over again, that’s a red flag that you
haven’t found the right abstractions.

Red Flag: Special-General Mixture This red flag occurs when a general-purpose mechanism also contains code specialized
for a particular use of that mechanism. This makes the mechanism more complicated and creates information leakage
between the mechanism and the particular use case: future modifications to the use case are likely to require changes to
the underlying mechanism as well.

Red Flag: Conjoined Methods
It should be possible to understand each method independently. If you can’t understand the implementation of one method
without also understanding the implementation of another, that’s a red flag. This red flag can occur in other contexts
as well: if two pieces of code are physically separated, but each can only be understood by looking at the other, that
is a red flag.

Chapter 10
Define Errors Out Of Existence

Chapter 11
Design it Twice

Designing a system twice is a powerful way to improve the design of the system. The first design is a prototype that
allows you to explore the problem space and understand the requirements. The second design is a more polished
version, you may use 3rd design if you want to further improve the design.

Chapter 12
Comments
**I agree with clean code more, though there are cases that require a comment indeed**

Chapter 13
Comments Should Describe Things that Aren’t Obvious from the Code

Red Flag: Comment Repeats Code
If the information in a comment is already obvious from the code next to the comment, then the comment isn’t helpful.
One example of this is when the comment uses the same words that make up the name of the thing it is describing.

Red Flag: Implementation Documentation Contaminates Interface
This red flag occurs when interface documentation, such as that for a method, describes implementation details that
aren’t needed in order to use the thing being documented.

Chapter 14
Choosing Names
Red Flag: Vague Name
If a variable or method name is broad enough to refer to many different things, then it doesn’t convey much information
to the developer and the underlying entity is more likely to be misused.

Red Flag: Hard to Pick Name
If it’s hard to find a simple name for a variable or method that creates a clear image of the underlying object, that’s
a hint that the underlying object may not have a clean design.

Chapter 15
Write The Comments First
(Use Comments As Part Of The Design Process)
Red flag. The comment that describes a method or variable should be simple and yet complete. If you find it difficult to
write such a comment, that’s an indicator that there may be a problem with the design of the thing you are describing.

**I don't really like this comment driven development**

Chapter 16
Modifying Existing Code

If you’re not making the design better, you are probably making it worse.

Chapter 17
Consistency

Chapter 18
Code Should be Obvious

Red Flag: Nonobvious Code
If the meaning and behavior of code cannot be understood with a quick reading, it is a red flag. Often this means that
there is important information that is not immediately clear to someone reading the code.

Chapter 19
Software Trends