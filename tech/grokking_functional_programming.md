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

[#] 234 page