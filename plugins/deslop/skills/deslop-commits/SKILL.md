---
name: deslop-commits
description: Clean up commit history of an AI-generated change.
disable-model-invocation: true
---

First step is to clean up git history (e.g. via rebase) to make the change read more clean. You have two levers available to you:

- Stacked branches or PRs:
  - independently mergable chunks of work
  - these must compile, tests must pass, etc.
- Inside each branch / PR:
  - you can break up things into commit-by-commit changes
  - use this to "create a story" for the commit; e.g. to isolate changes from each other.
  - in this case, each commit does NOT have to even compile
  - e.g. one commit might sketch out the interface + the consumer of an API
  - following commit might fill out the implementation

These two approaches can and should be composed.

What you are trying to optimize here is a notion of abstraction / black boxing with this approach. e.g. for a chain of commits like `A -> B`, once the user has accepted the changes in `A`, they don't want to have to reason about them much further in `B`. You're trying to help the reader effectively abstract out parts of the implementation when reading the code.

Other helpful rules of thumb:
- Large changes are very confusing when they also involve a behavior change.
- When possible, restructure a large behavior change into a large no-op refactor commit and THEN a small behavioral change.
  - This pattern is generalizable across PRs, etc. Useful for stacked PRs as well as commit-by-commit reviews
  - This is a really powerful tool for e.g. mechanical renames etc.
- In terms of the definition of a "large change", think more in John Ousterhout's "shallow vs. deep module" approach. A less helpful, but more precise rule of thumb is >500 LoC as a "large change" (but, again, 500 LoC isolated behind a simple interface -- a deep module -- is not a "large change")
- Rule of thumb: each commit should involve ONE and only ONE logical change (both in a stacked PR and in a commit-by-commit approach)
- The idea is that a large API surface change is much more complicated to reason about than an isolated one
- Think in terms of *abstraction* for the reviewer. They should be able to "black box" implementation.
