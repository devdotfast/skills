---
name: deslop
description: Run upon completion of a coding task, pre-review.
---

There are two phases to deslopping your work. First, you must clean up commit history. After that, run a pass to de-slop the tests in the codebase.

## Phase 1: Revising History

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

What you are trying to optimize here is a notion of abstraction / black boxing with this approach. e.g. for a chain of commits like `A -> B`, once the user has accepted the changes in `A`, they don't want to have to reason about them much further in `B`. You're trying to help the reader effectively abstract out parts of the implementation when reading the code.

Other helpful rules of thumb:
- Large changes are very confusing when they also involve a behavior change.
- When possible, restructure a large behavior change into a large no-op refactor commit and THEN a small behavioral change.
  - This pattern is generalizable across PRs, etc. Useful for stacked PRs as well as commit-by-commit reviews
  - This is a really powerful tool for e.g. mechanical renames etc.
- In terms of the definition of a "large change", think more in Jon Osterhaut's "shallow vs. deep module" approach. A less helpful, but more precise rule of thumb is >500 LoC as a "large change" (but, again, 500 LoC isolated behind a simple interface -- a deep module -- is not a "large change")
- The idea is that a large API surface change is much more complicated to reason about than an isolated one
- Think in terms of *abstraction* for the reviewer. They should be able to "black box" implementation.

## Phase 2: Clean Up Unit Tests

- For each commit in the new history, go through and take a look at the unit tests you've added
- Assume you have absolutely no idea how to write unit tests, i.e. you're a complete moron in this department. You probably should delete the ones you've added, right?
- I will say this again, because this really needs to sink in: bias towards deleting unit tests you've added
- This is especially true if it does not materially change code coverage
- It's ok to have a drop in code coverage for less wonky unit tests
- ALWAYS ALWAYS (this is *IMPORTANT*) delete change detector tests: https://testing.googleblog.com/2015/01/testing-on-toilet-change-detector-tests.html. TL;DR - does the test act on the *API* that the code exposes, or does it act like a checksum over the contents of the underlying algorithm
- For example, a test on a sorting algorithm should test that a list passed in is sorted, not the specifics of the sorting implementation 
