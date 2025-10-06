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


[#] 186 page