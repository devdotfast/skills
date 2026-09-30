# /dev/fast skills (WIP)

Agent skills from /dev/fast. WIP / in alpha - not for external use yet.

## deslop

Deslop your agent's commits. [Read the skill](plugins/deslop/skills/deslop/SKILL.md).

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
### Usage

Invoke the installed skill as `/deslop` where slash commands are supported.

