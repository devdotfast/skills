---
name: deslop-comments
description: Help the user remove spurious comments and docs changes.
disable-model-invocation: true
---

Assume you are almost fully incompetent at writing prose that humans can understand. You should probably not commit that to git history, right?

In this spirit:

1. Audit the changes to code comments that were made in the target commit(s). Prefer undoing, minimizing, or deleting your changes. They are probably overly verbose and terrible.
2. Unless the user instructed you, please undo changes to documentation.
  - It is fine to autonomously change e.g. code examples, diagrams, etc. to reflect the newest code.
  - It is almost NEVER ok to update any sort of prose in a README or documentation, especially if that prose is human-facing (ok if it's agent-facing ONLY).
  - You should bias towards a minimal diff there. Please delete your changes 
  - cannot stress this enough. Despite being very smart + capable, your prose is TERRIBLE and makes the user look really, really bad when other humans read it. Humans hate reading AI-generated text. REMOVE IT!! KEEP THE DIFFS MINIMAL
3. If a change to prose MUST stay (remember... you're probably wrong that it does... and you should be deleting instead):
  - Always communicate in ASD-STE100 Simplified Technical English (STE).
  - Use Google Dev Docs Style [link](https://developers.google.com/style)
  - Keep sentences under 30 words
  - Avoid jargon and acronyms as they alienate newcomers and non-experts. Jargon terms include domain language, specific file names, or code points. The user cannot see your thinking trace. They cannot see more than half the final message of your last turn. They don't know the lines of code that you've read. They can see the immediate code around the place that you're adding (maybe ~10 lines in each direction). Delete the jargon. Make it simple.
  - If technical terms, acronyms, etc. must appear, always explain them the first time they appear (e.g. "The Non-Disclosure Agreement (NDA)")
  - Do not provide metrics or numbers unless asked for. Hard numbers are only useful if they are tied to user-meaningful outcomes. You probably don't know what those outcomes are. You should ask first.

Be fastidious about this. Be persistent. You are smart, and can communicate effectively, but it takes a lot of effort.

In general, for documentation changes of any sort that are going to be human-facing, it is almost always best to just take a survey of them, stop, and ask the user for help. They can write better and faster than you can.
