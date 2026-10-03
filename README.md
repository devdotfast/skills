# /dev/fast skills (WIP)

Agent skills from /dev/fast. WIP / in alpha - not for external use yet.

## deslop

Deslop your coding agent's work.

Invoke the installed skill as `/deslop`. The skill is composed of 4 sub-skills which are independently useful:

1. `/deslop-commits`: clean up commit history autonomously to make it easier to review.
2. `/deslop-tests`: clean up spurious unit tests.
3. `/deslop-comments`: clean up agent-written prose, comments, docs, etc.
4. `/deslop-code`: clean up unnecessary layering + abstractions in the codebase ("drive-by fixes")

### Install

Install the skill in your choice of coding agent:

```sh
npx skills add devdotfast/skills --skill deslop
```
For a managed plugin install instead, use the marketplace for your agent:

```sh
# Claude Code
claude plugin marketplace add devdotfast/skills
claude plugin install deslop@devdotfast

# Codex
codex plugin marketplace add devdotfast/skills
codex plugin add deslop@devdotfast
```
