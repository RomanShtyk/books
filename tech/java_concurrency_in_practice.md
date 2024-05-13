## Java Concurrency in Practice

by Brian Goetz

#### Chapter 1: Introduction

* *Safety* means "nothing bad ever happens," while *liveness* means "something good eventually happens."
* Compromising safety often means compromising correctness. An example is a race condition between multiple threads.
* A liveness failure in a single-threaded program can be an infinite loop. In a multithreaded program, it could be
  deadlock, starvation, or livelock.
* While liveness means that something good *eventually* happens, performance means that it will happen *quickly*.
* Context switches have significant costs, including saving and restoring execution context, less of locality, and
  spending CPU time on scheduling threads instead of running them.

#### Chapter 2: Thread Safety

* Writing thread-safe code is, at its core, about managing access to shared, mutable state.
* Whenever more than one thread accesses a given state variable, and one of them might write to it, they all must
  coordinate their access to it using synchronization.
* A broken program shares mutable state without synchronization. Either don't share the state, make it immutable, or use
  synchronization upon every access.
* It is far easier to design a class to be thread-safe than to retrofit it for safety later.
* The same object-oriented techniques that help you write well-organized, maintainable classes -- such as encapsulation
  and data hiding -- can also help you create thread-safe classes.
* A program that consists entirely of thread-safe classes may not be thread-safe, and a thread-safe program may contain
  classes that are not thread-safe.

##### 2.1: What is thread safety?

* A class is thread-safe if it behaves correctly when accessed from multiple threads, regardless of their scheduling or
  interleaving of execution, and with no additional synchronization or coordination by the calling code.
* Thread-safe classes encapsulate any needed synchronization so that clients need not provide their own.

##### 2.2: Atomicity

* A race condition occurs when the correctness of a computation depends on the relative timing or interleaving of
  multiple threads.
* The most common type of race condition is *check-then-act*, where an observation could have become invalid between the
  time you observed it and the time you acted on it, causing a problem.
* Read-modify-write operations require knowing a previous value and ensuring that no one else changes or uses that value
  while you are in mid-update.
* Check-then-act and read-modify-write sequences are compound actions, or sequences that must be executed atomically in
  order to remain thread-safe.

##### 2.3: Locking

* Mutual exclusion locks, or mutexes, means that at most one thread may own a lock. If thread A attempts to acquire a
  lock by thread B, it blocks until B releases it.
* Reentrancy means that locks are acquired on a per-thread rather than per-invocation basis. Each lock is associated
  with an acquisition count and an owning thread.

##### 2.4: Guarding state with locks

* For each mutable state variable that may be accessed by more than one thread, all accesses to that variable must be
  performed by the same lock held. The variable is *guarded* by the lock.
* When a class has invariants that involve more than one state variable, we must ensure that each variable participating
  in the invariant must be guarded by the same lock.

##### 2.5: Liveness and performance

* Acquiring and releasing a lock has some overhead, so do not break down guarded blocks too far, even if this would not
  compromise atomicity.
* When implementing a synchronization policy, resist the temptation to prematurely sacrifice simplicity (potentially
  compromising safety) for the sake of performance.
* Avoid holding locks during lengthy computations or operations at risk of not completing quickly, such as when
  performing disk or network I/O.

#### Chapter 3: Sharing Objects

##### 3.1: Visibility

* To ensure visibility of memory writes across threads, you must use synchronization.
* There is no guarantee that operations in one thread will be performed in the order given by the program, as long as
  the reordering is not detectable from within *that* thread.
* Because of reordering, attempts to reason about the order in which memory actions "must" happen in insufficiently
  synchronized multithreaded programs will almost certainly be incorrect.
* Unless synchronization is used every time a variable is accessed, it is possible for a thread to read a stale value
  for that variable.
* Stale data can cause serious and confusing failures such as unexpected exceptions, corrupted data structures,
  inaccurate computations, and infinite loops.
* *Out-of-thin-air safety* is when a variable reads a thread without synchronization, it reads a value that was actually
  written by another thread instead of some random value.
* With the Java Memory Model, the values of variables that were visible to thread A prior to releasing a lock are
  guaranteed to be visible to thread B upon acquiring the same lock.
* Variables marked with the `volatile` keyword are not reordered with other memory operations, and are not put in caches
  where they are hidden from other processors.
* A `volatile` variable can be used for a completion, interruption, or status flag, but the semantics are not strong
  enough to make the increment operation atomic, for example.
* Locking is not just about mutual exclusion; it is also about memory visibility. To ensure that all threads see the
  most up‐ to‐date values of shared mutable variables, the reading and writing threads must synchronize on a common
  lock.
* The semantics of `volatile` are not strong enough to make the increment operation (count++) **atomic**, unless you can
  guarantee that the variable is written only from a **single** thread.
* You can use volatile variables only when all the following criteria are met:
  • Writes to the variable do not depend on its current value, or you can ensure that only a single thread ever updates
  the value;
  • The variable does not participate in invariants with other state variables; and
  • Locking is not required for any other reason while the variable is being accessed.

##### 3.2: Publication and escape

* *Publishing* an object means making it available to code outside of its current scope. An object that is published
  when it should not have been is said to have *escaped*.
* Any object that is *reachable* from a published object by following some chain of nonprivate field references and
  method calls has also been published.
* Once an object escapes, you have to assume that another class or thread may, maliciously or carelessly, misuse it.
  This is a compelling reason to use encapsulation.
* An object is in a predictable, consistent state only after its constructor returns, so publishing an object (
  via `this`) from within its constructor can publish an incompletely constructed object.
* You can avoid this improper construction by using a private constructor and a public static factory method.

##### 3.3: Thread confinement

* If data is only accessed by a single thread, then no synchronization is needed. This technique is called *thread
  confinement*.
* *Ad-hoc thread confinement* is when the responsibility for maintaining thread confinement falls entirely on the
  implementation.
* Thread confinement is often a consequence of deciding to implement a particular subsystem, such as the GUI, as a
  single thread. The simplicity benefit of such a system outweighs the fragility of ad-hoc thread confinement.
* *Stack confinement* is a special case of thread confinement in which an object can only be reached through local
  variables. Local variables are intrinsically confined to the executing thread.

##### 3.4: Immutability

* Immutable objects are simple, because they can only have one state. Immutable objects are also safe, because you can
  freely share and publish them without the need to make defensive copies.
* An object is immutable if its state cannot be modified after construction, all its fields are `final`, and it is
  properly constructed, i.e. the `this` reference does not escape during construction.
* Whenever a group of related data items but be acted upon atomically, consider creating an immutable holder class for
  them.

##### 3.5: Safe publication

* Simply storing a reference to an object into a public field is not enough to publish that object safely. Improper
  publication allows another thread to observe a partially constructed object.
* However, immutable objects can be used safely by any thread without additional synchronization, even when
  synchronization is not used to publish them.
* To publish an object safely, both the reference to the object and the object's state must be made visible to other
  threads at the same time.
* Objects that are not technically immutable, but whose state will not be modified after publication, are called
  *effectively immutable*. Such objects, when safely published, can be used safely by any thread without additional
  synchronization.
* While effectively immutable objects must be safely published, mutable objects must be safely published, and mus the
  either thread-safe or guarded by a lock.
* Many concurrency errors stem from failing to understand the "rules of engagement" for a shared object. When you
  publish an object, document how it should be accessed.

###### 3.5.3. Safe Publication Idioms

* To publish an object safely, both the reference to the object and the object's state must be made visible to other
  threads at the same time. A properly constructed object can be safely published by:
  • Initializing an object reference from a static initializer;
  • Storing a reference to it into a volatile field or AtomicReference;
  • Storing a reference to it into a final field of a properly constructed object; or
  • Storing a reference to it into a field that is properly guarded by a lock.
* The ConcurrentHashMap class is similar to HashMap, except it’s thread-safe and allows modification while iterating
  over it.

###### 3.5.4. Effectively Immutable Objects

* Static initializers are executed by the JVM at class initialization time; because of internal synchronization in the
  JVM, this mechanism is guaranteed to safely publish any objects initialized in this way
* Safely published effectively immutable objects can be used safely by any thread without additional synchronization.

###### 3.5.5. Mutable Objects

* The publication requirements for an object depend on its mutability:
  • Immutable objects can be published through any mechanism;
  • Effectively immutable objects must be safely published;
  • Mutable objects must be safely published, and must be either thread‐safe or guarded by a lock.

###### 3.5.6. Sharing Objects Safely

* The most useful policies for using and sharing objects in a concurrent program are:
  **Thread‐confined.** A thread‐confined object is owned exclusively by and confined to one thread, and can be modified
  by its owning thread.
  **Shared read‐only.** A shared read‐only object can be accessed concurrently by multiple threads without additional
  synchronization, but cannot be modified by any thread. Shared read‐only objects include immutable and effectively
  immutable objects.
  **Shared thread‐safe.** A thread‐safe object performs synchronization internally, so multiple threads can freely
  access it through its public interface without further synchronization.
  **Guarded.** A guarded object can be accessed only with a specific lock held. Guarded objects include those that are
  encapsulated within other thread‐safe objects and published objects that are known to be guarded by a specific lock.

#### Chapter 4: Composing Objects

##### 4.1: Designing a thread-safe class

* Designing a thread-safe class requires identifying the invariants that constrain the state variables, and establishing
  a policy for managing concurrent access to them.
* The smaller the *state space* of an object or variable, the easier it is to reason about. Use `final` fields to reduce
  the state space.
* Operations with state-based preconditions are called *state-dependent*.
* Ownership implies control, but once you publish a reference to a mutable object, you no longer have exclusive control,
  but at best "shared ownership."

##### 4.2: Instance confinement

* Encapsulating data within an object confines access to the data to the object's methods, making it easier to ensure
  that the data is always accessed with the appropriate lock held.
* Instance confinement also allows different state variables to be held by different locks.
* Confined objects can also escape by publishing other objects such as iterators or inner class instances that may
  indirectly publish the confined objects.
* Using a private lock prohibits client code from acquiring it, whereas a publicly accessible lock allows client code to
  participate in its synchronization policy, perhaps incorrectly.

##### 4.3: Delegating thread safety

* A class with multiple independent thread-safe state variables and no operations that have any invalid state
  transitions can delegate thread safety to the underlying state variables.
* If a state variable is thread-safe, does not participate in any invariants that constrain its value, and has no
  prohibited state transitions for any of its operations, then it can be safely published.

##### 4.4: Adding functionality to existing thread-safe classes

* Extending a class to support a thread-safe operation is more fragile than adding code directly to the class, as its
  synchronization policy is now distributed over multiple source files.
* Just as subclassing violates encapsulation of implementation, client-side locking violates encapsulation of
  synchronization policy.

##### 4.5: Documenting synchronization policies

* Document a class's thread safety guarantees for its clients; document its synchronization policy for its maintainers.
* If you want clients to be able to create new atomic operations on your class, you must document which locks they
  should acquire to do so safely.
* If you must guess whether a class is thread-safe, improve the quality of your guess by interpreting the specification
  by someone who must implement it versus someone who will merely use it.