Grokking Functional Programming
X/10

# Chapter 2, Pure Functions

## Definition

- Return a single value
- Result depends only on arguments
- Do not mutate existing values

## Why Pure Functions?

- **State problems**: Imperative/stateful code caused bugs
- **Solution 1 – Copies**: Return/pass copies to avoid side effects
- **Solution 2 – Recalculate**: Don’t store derived values (e.g., discount), recalc when needed
- **Solution 3 – Pass state directly**: Remove boilerplate, pass data into functions

## Testing Benefits

- Easy to test
- Tests double as documentation if concise and clear

# Chapter 3, Immutable Values

## Mutability is Dangerous

- Imperative solution failed due to operations on Java’s `List` mutating arguments.
- Function signatures alone don’t reveal risks; implementations must be checked.

## Fighting Mutability with Copies

- Copy the input list and work only on the copy → avoids surprising side effects.

## Shared Mutable State

- Defined as a variable shared across entities that can be mutated by them.
- Source of unpredictable bugs.

## Immutable Values as a Solution

- Functions that take/return only immutable values prevent unexpected mutations.

## Examples in Practice

- **Java String**: methods return new values (immutable approach).
- **Scala**: built-in immutable collections (`slice`, `append`, `appendAll`).

## Key Idea

- Functional programming = pure functions + immutable values.

# Chapter 4, Functions as values

## Higher-order functions (HOFs)

- Take other functions as parameters and/or return functions.
- Examples: `sortBy`, `map`, `filter`, `foldLeft`.

## Passing functions

- Java uses `Comparator` objects; Scala/FP pass functions directly (`=>` syntax).
- Lists remain **immutable** in Scala, improving robustness.

## Returning functions (Currying)

- Functions can return functions, allowing configuration.
- **Currying**: multiple parameter lists improve readability and type safety.

## foldLeft

- Reduces a list to a single value (e.g., sum).
- Both higher-order and curried (two parameter lists).

## Product types & immutability

- Combine multiple values safely.
- In Scala: `case class`.
- Work naturally with higher-order functions due to immutability.

# Chapter 5, Sequential programs

## 1. Deal with Lists of Lists using `flatten`

- Problem: handling `List[List[String]]` (e.g., books with multiple authors).
- Solution: use `flatten` to merge inner lists into one `List[String]`.

## 2. Write Sequential Programs using `flatMap`

- `flatMap` = `map` + `flatten`.
- Enables functional, pipeline-based sequential programs.
- Replaces traditional `for` loops.

## 3. Improve Readability with **for Comprehensions**

- `for` comprehensions are syntactic sugar for nested `flatMap`/`map` calls.
- Make sequential functional code cleaner and easier to read.

## 4. Use Conditions Inside **for Comprehensions**

- Three filtering methods:
    1. Using `filter` function.
    2. Using **guard expressions** (`if` inside `for`).
    3. Using a filtering function with `flatMap`.
- `filter` and guards work on collections; `flatMap`-based filtering is generic.

## 5. Explore More Types with `flatMap`

- Other types supporting `flatMap`: `Set`, `Option`.
- You can combine multiple types in one `for` comprehension.
- Example use case: build parsers or sequential pipelines using `Option`.

👉 **Core idea:**  
`flatten`, `flatMap`, and `for` comprehensions allow writing readable, functional, sequential programs that work
consistently across multiple types like `List`, `Set`, and `Option`.

# Chapter 6, Error handling

## 1. Handle Errors Without Nulls or Exceptions

- In functional programming, **errors are values**, not control flow mechanisms.
- Instead of `null` or exceptions, use immutable containers like `Option` or `Either`.

## 2. Handle All Corner Cases

- **Checked exceptions** are not composable.
- `Option` and `Either` simplify error handling with **`orElse`**, which combines two immutable results and picks one.
- This approach scales cleanly across complex code.

## 3. Indicate Errors in Function Signatures

- Pure functions explicitly expose potential failure in their **type signatures**:
    - `Option` → result may be missing.
    - `Either` → result may contain an error value.
- The type system forces handling of all possible error cases.

## 4. Compose Bigger Functionalities from Smaller Ones

- Split requirements into small, pure functions, each returning an error-aware value.
- Combine them using **composition** and **`foldLeft`** for “all-or-nothing” error handling.
- The compiler enforces correct handling of all branches.

## 5. Return User-Friendly and Descriptive Errors

- `Either` allows attaching **descriptive messages** (`Left[String]`) instead of generic failures.
- Makes debugging and user feedback clearer.

### Step-by-Step Recap

1. **Higher-order functions** – used for clean error handling (from Chapter 4).
2. **Option** – signal possible absence of value (from Chapter 5).
3. **Functional vs Checked Exceptions** – FP is more composable, readable, and concise.
4. **Handle Many Errors** – use higher-order functions that scale single-error logic.
5. **Either** – return structured, descriptive error information.

👉 **Core idea:**  
Functional error handling replaces `null` and exceptions with **typed, composable, immutable values** (`Option`,
`Either`) that make failure explicit, predictable, and easy to combine.

# Chapter 7, Requirements as types

# Chapter Summary – Newtypes and Algebraic Data Types (ADTs)

## 1. Newtypes and ADTs Overview

- **ADTs (Algebraic Data Types)**:
    - **Sum types** → `enum` in Scala.
    - **Product types** → `case class` in Scala.
- Used to represent **immutable, domain-specific data** safely.
- **Pattern matching** enables clear handling of ADTs in pure functions.
- Compared ADTs with **OOP inheritance**, showing ADTs are more explicit and safer.
- Learned new **higher-order functions** (on `Option`, `List`, etc.) as design tools.

## 2. Model Immutable Data to Minimize Errors

- Avoid primitive obsession: replace raw types with **newtypes** or **domain-specific ADTs**.
- Reduces mistakes and makes models reflect business logic accurately.

## 3. Model Requirements as Immutable Data

- ADTs can serve as **input parameters** to functions, improving safety and readability.
- Function signatures become **self-documenting**, reflecting possible states and outcomes.

## 4. Find Problems in Requirements Using the Compiler

- The compiler becomes a **design ally**, catching logical and structural errors early.
- Replacing primitives with **newtypes/ADTs** improves type safety and prevents invalid states.

## 5. Ensure Logic Runs Only on Valid Data

- Detailed data modeling makes invalid states **impossible to represent**.
- Eliminates many runtime checks and reduces the need for `Either`-based error handling.
- This approach is called **compile-time error prevention** — superior to runtime handling when applicable.

## 6. Relationship Between ADTs and Either

- Both ADTs and `Either` can represent alternatives or branching logic.
- ADTs offer **compile-time guarantees**, while `Either` handles **runtime** validation.

👉 **Core idea:**  
Functional design uses **newtypes and ADTs** to create precise, immutable, type-safe models. This enables the compiler
to enforce correctness, replacing many runtime errors with **compile-time safety** — a cornerstone of robust functional
programming.

# Chapter 8, IO as values

# Chapter Summary – IO and Purely Functional Side Effects

## 1. Represent Side Effects as Values

- **Side-effectful programs** can be represented as **values** using the `IO` type.
- Two main constructors:
    - `IO.delay` → takes a lazily evaluated block of code (deferred execution).
    - `IO.pure` → wraps an already computed value (eager execution, always succeeds).
- These allow **purely functional descriptions of impure operations**.

## 2. Handle Unsafe External Data Sources

- External APIs are **unsafe**—they can fail unpredictably.
- We handle such calls safely by **describing recovery strategies** using:
    - `IO.orElse` for fallbacks and retries.
- Concepts from `Option` and `Either` helped us reason about **IO failures** in a familiar way.

## 3. Safely Persist Data Outside the Program

- Writing data (e.g., storing meetings) is also a side effect.
- Wrapped those operations in `IO.delay`, deferring execution.
- The side effects are only executed when explicitly invoked via:
    - `unsafeRunSync()` — at the program’s boundary, not in the core logic.

## 4. Make Side Effects Explicit in Function Signatures

- Function signatures **reveal behavior**:
    - `List[MeetingTime]` → pure, no side effects.
    - `IO[Option[MeetingTime]]` → may perform IO operations when executed.
- This transparency improves readability, testability, and maintainability.

## 5. Separate Pure and Impure Code

- Introduced the **Functional Core, Imperative Shell** concept:
    - Core → pure, deterministic logic.
    - Shell → handles side effects (IO actions like HTTP calls or console output).
- Clients decide *where and when* to execute IO effects.

## 6. Additional Insights

- Covered only **synchronous programs** here; same ideas extend to **multi-threaded** ones.
- **Retries and fallbacks** may be part of the **business logic** (especially for output actions).
- Emphasized **essential vs. accidental concerns**:
    - Keep essential logic in the pure functional core.
    - Push accidental complexity (like IO) to the edges.

👉 **Core idea:**  
Representing side effects as **first-class values (`IO`)** lets us write programs that are **pure, composable, and
testable**, while still capable of performing real-world actions safely and predictably.

# Chapter 9, Streams as values

Stream-based programming is widely used in several contexts:

- **UI programming:**  
  Streams model user interactions (e.g., clicks, gestures) as event sequences, similar to processing a currency stream.

- **Distributed computing:**  
  Producers and consumers often operate at different speeds on separate nodes.  
  Reactive streams (introduced in **Java 9’s `Flow` API**) provide mechanisms for **backpressure** and coordination.

- **Big data processing:**  
  Streams are ideal for handling data sets too large for memory.  
  Used in systems like **Hadoop** and **Spark**, as well as for geographic data, infinite feeds, and massive files.

No matter the domain, **core stream operations** (like `map`, `filter`, `zip`, etc.) remain applicable across libraries
and languages. Only names differ—your intuition about how streams work will transfer easily.

### a. Declarative Program Flow Design

- Built complex flows **declaratively** using stream combinators:
    - `map`, `filter`, `append`, `eval`, `take`, `orElse`, `sliding`, `zip`, `zipLeft`, `repeat`, `unNone`.
- Leveraged **immutable maps** and **tuples** for predictable, side-effect-free transformations.

### b. Recursion and Laziness

- Used **recursion** to restart processes—particularly for IO retries and recovery.
- Employed **laziness** to **defer computations** until necessary, optimizing both performance and control flow.

### c. Handling IO-Based Streams

- Distinguished between **pure streams** (e.g., of integers) and **IO streams** (side-effectful computations).
- Applied similar functional patterns to both, unifying their handling through abstraction.

### d. Infinite Streams

- Utilized **lazy evaluation** to create **infinite streams** safely and efficiently.
- Controlled them using stream operators (`take`, `zip`, etc.) to avoid unbounded execution.

### e. Time-Dependent Streams

- Modeled **time-based events** using a stream of `Unit` values emitted every second.
- Combined it (via `zip`) with another stream (e.g., API calls) to **produce outputs at fixed intervals**.
- This introduced the foundation of **multi-threaded and concurrent programming**.

👉 **Core takeaway:**  
Streams offer a **unified, declarative, and composable** way to model asynchronous, time-dependent, and potentially
infinite computations—paving the way toward functional **concurrency and reactive programming**.

# Chapter 10, Concurrent programs

# Chapter Summary – Functional Concurrency

## 1. Core Idea

This chapter introduced **functional concurrency** — showing how concepts from sequential FP (pure functions,
immutability, and declarative composition) remain applicable even when dealing with **parallel** and **asynchronous**
computations.  
The goal wasn’t to dive into low-level threading mechanics, but to build an **intuition** for safe, high-level
concurrent programming using pure functional tools.

---

## 2. Key Concepts and Techniques

### a. Declarative Concurrent Program Flows

- Introduced **`parSequence`**, which transforms:

```

List[IO[A]] → IO[List[A]]

```

It’s similar to `sequence`, but executes IO programs **concurrently** instead of sequentially.

- Compared this declarative style to imperative concurrency tools:
- Monitors
- Locks
- Actors
- Thread-safe data structures
- Advantage: **No shared mutable state**, **no race conditions**, **no manual thread management**.

---

### b. Lightweight Virtual Threads (Fibers)

- Concurrency in FP is built on **fibers**—lightweight, user-space threads.
- Unlike system-level `Thread` objects:
- **Fibers are not tied to OS threads**.
- **Thousands can run concurrently** with minimal overhead.
- Many FP runtimes (Cats Effect, ZIO, etc.) and even modern languages (e.g., Kotlin’s coroutines, Java’s Project Loom)
  support this model.

---

### c. Safe Mutable State Across Threads

- Introduced **`Ref[IO, A]`**, a **concurrent-safe mutable reference**.
- Provides atomic updates using **compare-and-swap (CAS)** semantics.
- Conceptually similar to Java’s `AtomicReference`, but **purely functional**.
- Updates are made by providing a **pure function**:

```scala
ref.update(current => newValue)
````

* Guarantees **thread safety** without locking or side effects.

---

### d. Asynchronous Event Processing

* Built a simple **asynchronous communication model** using:

    * `IO.start` — runs a computation in a separate fiber.
    * `FiberIO.cancel` — allows safe cancellation of running fibers.
* This pattern enables background tasks, reactive pipelines, and non-blocking event handling.

---

## 3. Final Insights

* **Concurrency is hard** — even in FP. Always prefer **sequential** code unless parallelism brings clear benefits.
* Use **`parSequence`** and similar combinators to safely exploit concurrency **without dropping into low-level
  primitives**.
* These abstractions provide **massive leverage**: high performance and safety with minimal complexity.

---

👉 **Bottom line:**
Functional concurrency leverages **fibers**, **immutable state models**, and **declarative composition** to make
parallel programming **safe, scalable, and comprehensible**—without the pitfalls of traditional thread-based approaches.

# Chapter 11, Designing functional programs

### a. Functional Core Design

- Used the **functional core + imperative shell** pattern:
    - **Core:** pure functions and immutable data.
    - **Shell:** external modules (like `main`) that configure the core with real input/output operations.
- This separation made the application predictable, testable, and easy to modify.

### b. Type-Driven Modeling

- Started from **requirements** and modeled them explicitly as **types**.
- Followed the iterative principle:  
  **“Make it work → make it right → make it fast.”**
- The resulting type system guided design decisions and improved reliability.

### c. Safe Integration with External APIs via IO

- The **data access layer** was modeled as a set of **three pure functions** (`DataAccess`).
- Only after the core logic (`travelGuide` function) worked, it was connected to a real data source — **Wikidata**.
- Used **Apache Jena** (imperative Java library) to query Wikidata’s **SPARQL endpoint**.
- Despite Jena’s mutability and side effects, integration remained pure thanks to **IO** abstractions.
- The same approach can be applied to **SQL** or other external data systems.

### d. Safe Resource Management

- Apache Jena manages internal resources (connection pools, query contexts) that can **leak** if not released properly.
- Solved this by modeling resources with the **`Resource`** type, which:
    - Describes **acquisition** and **release** logic.
    - Ensures safety even in case of exceptions.
- This pattern generalizes to **any resource** (files, network sockets, etc.).

### e. Performance and Caching

- Improved performance by adding **concurrency** and a **query results cache**.
- The change required only a **small dependency swap**, proving the robustness and modularity of the design.
- The book’s repository also contains additional improvements like **IO timeouts**.

## 3. Final Insights

- Functional programming enables **real-world systems** that are:
    - Safe (no resource leaks)
    - Modular (pure core, impure shell)
    - Efficient (easy to optimize)
- Using **types**, **IO**, and **Resource**, developers can build applications that remain clean and maintainable even
  when interacting with messy, stateful external systems.

# Chapter 12, testing functional programs

## 1. What This Chapter Demonstrated

You used the full FP toolkit to **test pure functions, test IO, find bugs, and clarify requirements**.  
Testing in FP is mostly about:  
**give inputs → assert outputs** — no mocks, no shared state, no nonsense.

### ✅ Test Pure Functions with Examples

- For pure functions, testing = provide inputs → check expected output.
- This is simple because pure functions are deterministic.

### ✅ Test Pure Functions with Properties (Property-Based Testing)

- Property tests helped uncover a **integer overflow bug** in `guideScore`.
- You learned:
    - Properties are stronger than example tests.
    - Properties come from **requirements**, not guesses.
    - Generators (`Gen`) can be custom-built.
    - `Gen` also supports **flatMap**, making generators composable.

### ✅ Test IO Without Mocking Libraries

Two strategies:

1. **Stub IO**
    - When the function consumes external data but doesn’t integrate deeply.
    - You hardcoded `DataAccess` functions returning fixed values to test `travelGuide`.

2. **Use Real Services for Integration**
    - When testing the integration itself.
    - You spun up a real SPARQL server instance and used `Resource` to:
        - start the server
        - ensure proper cleanup
    - Even integration tests can use property-based testing.

### ✅ Test-Driven Development (TDD)

- You implemented a new requirement using TDD:
    - Write failing tests (**red**)
    - Implement the simplest passing version (**green**)
    - Improve the code (**refactor**)
    - Repeat
- The final `travelGuide` implementation emerged through iterative refinement.

## 3. Final Takeaways

- FP makes testing dramatically easier:
    - Pure functions don’t need mocks.
    - IO can be isolated, stubbed, or tested with real servers.
    - Property-based tests catch entire *classes* of bugs.
- Combining these techniques supports:
    - safer refactoring
    - clearer requirements
    - cleaner designs

Testing becomes an extension of FP design instead of an afterthought.

THESE ARE BIG!
Chapter 1: Learning functional programming
• In FP, we tend to focus more on signatures than bodies of functions we use.
• Functions that don’t lie are very important features of FP.
• In FP, we focus on what needs to happen more often than how it should happen.
Chapter 2: Pure functions
• Pure functions are the foundation of functional programming.
• We pass copies of data in FP instead of changing the data in place.
• In FP, we separate concerns into different functions.
• We use three rules to create pure functions, which are less buggy.
Chapter 3: Immutable values
• Avoiding mutability lies at the heart of functional programming.
• We don’t use mutable states in FP—we use immutable ones instead.
• In FP, we just pass immutable values around!
• Immutability makes us focus on relations between values.
Chapter 4: Functions as values
• Some mainstream languages expose APIs that embrace immutability (e.g., Java Streams).
• Functions stored as values are what FP is really about.
• Functions that take functions as parameters are ubiquitous in FP code.
• Functions that don’t lie are crucial for maintainable codebases.
• Functions are treated exactly the same as other values in FP.
• Returning functions is a foundation of designing flexible APIs.
Chapter 5: Sequential programs
• flatMap is the most important function in FP.
• You will find a lot of for comprehensions in functional programs.
• FP is programming with expressions, not statements.
• In FP, we build big programs from small functions.
• FP heavily relies on abstracting common features—you learn once and use them everywhere.
Chapter 6: Error handling
• Indicating an error in FP means returning an immutable value that represents an error.
• In FP, you can focus on implementing one small function without worrying about others.
• FP is programming with expressions; functional programmers don’t use statements.
• In FP, there usually is a function for every problem in your code.
• Functions and values compose very well together—we use them to build big programs from
smaller pieces.
• Handling errors in FP is taking an error value and returning a different value.
• In FP, we prefer compilation errors over runtime crashes.
Chapter 7: Requirements as types
• In FP, we model data so that only valid business combinations are possible.
• In FP, each type has many higher-order functions.
• There is a higher-order function available for all the common use cases!
• Sum type product type combo gives us modeling superpowers.
• In FP, behaviors are separated from the data model.
• In FP, some behaviors can be modeled as data.
Chapter 8: IO as values
• In FP, we push the impurity out of most of our functions.
• In FP, we just pass immutable values around!
• In FP, we treat impure functions as unsafe code.
• When we use a function that returns an IO, we are forced to return an IO as well.
• FP is about transforming immutable values using pure functions, even when handling IO.
• We push the impurity out of the functional core, so it’s easier to test and maintain.
• In FP, we strive to put as many essential concerns as possible inside pure functions.
• Functional programmers treat everything as values.
• In FP, we “solve” a signature by providing the function body.
Appendix B I Functional gems 479
Chapter 9: Streams as values
• In FP, we solve a lot of problems using recursion.
• Lazy evaluation, recursion, and potential infinite executions have a lot in common.
• Types tell a lot about the internals in both IO and streaming programs.
• Streams help to separate concerns in your application.
• Many languages and libraries try to use the power of FP by including stream-like lazy APIs.
Chapter 10: Concurrent programs
• Writing concurrent programs is much easier when we can only deal with immutable values and
pure functions.
• In FP, programmers tend to use atomic references a lot when creating concurrent programs.
• We model concurrently accessible shared mutable states as immutable values.
• In FP, a multi-threaded program can be modeled as an immutable list of sequential programs.
• In functional programs we work with fibers instead of OS-level threads.
Chapter 11: Designing functional programs
• Many OO design principles can be used with pure functions and immutable values (FP).
• IO enables you to use well-established imperative client libraries in your functional programs!
• “Outsourcing” a concern by requiring a new parameter is a very common design practice in FP.
• We model releasable resources as values.
Chapter 12: Testing functional programs
• FP tests are just calling functions and asserting on their outputs.
• Property-based tests help us look at our functions more critically.
• In FP, even generating random test values can be described by a single immutable value.
• We use exactly the same techniques in tests as in production code.
• Resource and IO types help write proper readable and maintainable integration tests.
• Mocking and stubbing are just passing values to functions.
[#] 461 page