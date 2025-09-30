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

[#] 48 page