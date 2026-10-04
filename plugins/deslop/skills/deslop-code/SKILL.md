---
name: deslop-code
description: clean up code layering and unnecessary abstractions in drive-by fixes
disable-model-invocation: true
---

There are a few great levers when cleaning up code:

1. Cleaning up dead code. Analyze every line of the commit. Your reviewer will nitpick. Ask yourself: did this HAVE to change? If not, revert it.
2. Creating a drive-by fix PR or commit in the code to make it read better overall. Improves code quality and makes it easier to reason about.

## Part 1: Cleaning up dead code

Be aggressive when deleting code; question the user if things are ok to delete but perhaps aren't covered in E2E tests or (formal) specifications (may be a missing edge case). Consult git history, trace storage, issue tracking, slack, etc. to autonomously come to a conclusion autonomously if you can; only refer to the human if you can't be sure.

## Part 2: Improving Codebase Quality

Think in terms of John Ousterhout's "A Philosophy of Software Design"; specifically, in optimizing for deep modules over shallow ones. You want narrow interfaces which provide deep functionality.

These sort of changes work best as no-op cleanup commits or PRs. Do not mix behavior changes with them if at all possible. You are trying to set up some "drive-by fixes" that leave the code better than you found it.

It's best to write code like this from the start, but often coding changes leave room for consolidation; imagine a callstack that looks like:

```
handle_checkout()       # A
  -> create_order()     # B'
    -> insert_order()   # C
```

where, in the process of feature work, B' has been modified.

This is a great opportunity to look at A & C and consider whether those abstractions are shallow. Some rules of thumb:

- Consider only the production code from the perspective of a new reader. How many hops do they need to "jump" in a codebase on this callstack to get to the "meat" of the functionality? You are trying to minimize the number of those hops for that person.
- Ignore unit tests when thinking about this. Typically unit tests are fragile and tied to implementation.
- Small, tiny functions which just call out to each other, unnecessary interfaces to provide "abstraction" are typically smells of this. i.e. it is very painful to read code that requires >1 jump to understand what an abstraction actually *does*.

Once you refactor, you can repeat this process recursively (collapsing adjacent shallow layers of abstraction to form deeper modules).

Example of a great diff:

```diff
 def run(args):
-  return f(args)
-
-def f(args):
   a, b = unpack(args)
   return g(a, b)
 
 def g(a, b):
   # do something
```
