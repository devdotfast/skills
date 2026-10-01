---
name: deslop
description: Run upon completion of a coding task, pre-review.
disable-model-invocation: true
---

There are three phases to deslopping your work. First, you must clean up commit history. After that, run a pass to de-slop the tests in the codebase. Finally, run a pass over documentation.

Where possible, run phases in parallel; this is quite tricky w/ Phase 1, but Phases 2 + 3 are quite parallelizable. Use your best judgement.

## Phase 1: Revising History

[deslop-commits](../deslop-commits/SKILL.md)

## Phase 2: Clean Up Unit Tests

[deslop-tests](../deslop-tests/SKILL.md)

## Phase 3: Clean Up Documentation + Ask for help if necessary

[deslop-comments](../deslop-comments/SKILL.md)
