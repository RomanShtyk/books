Tidy First? by Kent Beck

## Part I: Types of Tidying

* Guard Clauses
* Dead Code
* Normalize Symmetries
* New Interface, Old Implementation
* Reading Order
* Cohesion Order
* Move Declaration and Initialization Together
* Explaining Variables
* Explaining Constants
* Explicit Parameters
* Chunk Statements
* Extract Helper
* One Pile
* Explaining Comments
* Delete Redundant Comments

## Part II. Managing

* Separate Tidying - it depends on your teams workflow, but small tidying PRs are better
* Chaining - make tiny changes and keep yourself from, start with basic tidings and they will show what to tidy next.
* Batch Sizes - size of tiding changes, should be optimized for the least possible conflicts and faster PR reviews
* Tidy never when:
  • You’re never changing this code again.
  • There’s nothing to learn by improving the design.
* Tidy later when:
  • You have a big batch of tidying to do without immediate payoff.
  • There’s eventual payoff for completing the tidying.
  • You can tidy in little batches.
* Tidy after when:
  • Waiting until next time to tidy first will be more expensive.
  • You won’t feel a sense of completion if you don’t tidy after.
* Tidy first when:
  • It will pay off immediately, either in improved comprehension or in cheaper behavior changes.
  • You know what to tidy and how.

## Part III. Theory

* Beneficially Relating Elements - definition on system design
* Structure and Behavior -
* Time value and Optionality
* A Dollar Today > A Dollar Tomorrow
* Options
* Options Versus Cash Flows - main trade off, do now or do later
* Reversible Structure Changes - avoid irreversible changes by using feature-flags to make them reversible. Irreversible
  should be double-triple-checked because they are very hard to fix later
* Constantine’s Equivalence - cost(software) ±= coupling
* Coupling vs decoupling - you shouldn’t bother to squeeze out every last bit of coupling. The coupling created in doing
  so isn’t worth it.

Tidy First?

* Cost — Will tidying make costs smaller, later, or less likely?
* Revenue — Will tidying make revenue larger, sooner, or more likely?
* Coupling — Will tidying make it so I need to change fewer elements?
* Cohesion — Will tidying make it so the elements I need to change are in a smaller, more concentrated scope?