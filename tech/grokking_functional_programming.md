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

# Chapter 2, Immutable Values

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
  [#] 48 page