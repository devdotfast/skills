---
name: deslop
description: Run upon completion of a coding task, pre-review.
disable-model-invocation: true
---

There are four phases to deslopping your work. First, you must clean up commit history. After that, run a pass to de-slop the tests in the codebase and a pass to deslop the actual code. You can use the clean commit history to iterate commit-by-commit to help bound your search and attention. Finally, run a pass over documentation.

Where possible, run phases in parallel; this is quite tricky w/ Phase 1, but Phases 2 onwards are quite parallelizable. Use your best judgement.

## Phase 1: Revising History

[deslop-commits](../deslop-commits/SKILL.md)

## Phase 2: Clean Up Unit Tests

[deslop-tests](../deslop-tests/SKILL.md)

## Phase 3: Clean up unnecessary abstractions in code

[deslop-code](../deslop-code/SKILL.md)

If necessary, you can revisit Phase 1 here.

## Phase 4: Clean Up Documentation + Ask for help if necessary

[deslop-comments](../deslop-comments/SKILL.md)
