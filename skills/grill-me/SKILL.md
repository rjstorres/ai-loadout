---
name: grill-me
description: A relentless interview to sharpen a plan or design, asked through the AskUserQuestion tool.
disable-model-invocation: true
---

Interview the user relentlessly until you reach a shared understanding. Map this as a **design tree**: every decision branches into the decisions that hang off it.

Work the tree in **rounds**. The **frontier** is every decision whose prerequisites are already settled: the questions you can ask _now_ without guessing at answers you haven't heard yet. Ask the whole frontier in one round, then wait for the answers before the next round.

## Asking a round

Ask every question with the `AskUserQuestion` tool. Never ask a question as plain chat text.

- Each question can have multiple anwsers. Put your recommended answer first and end its label with "(Recommended)".
- The tool adds "Other" by itself. Do not add your own "Other" option.
- Keep `header` to 12 characters or fewer, naming the decision (e.g. "Storage", "Auth", "Scope").
- Put the trade-off of each option in its `description`, so the user can decide from the question alone.
- Use `preview` when the options are concrete things to compare side by side: code, schemas, layouts, diagrams.
- Use `multiSelect: true` only when the options are not mutually exclusive.

## Between rounds

Each round of answers reshapes the tree: settled decisions push the frontier outward and unblock questions that depended on them. Recompute the frontier and ask the next round. A question whose answer depends on another question still open in this round belongs to a _later_ round, not this one.

When an answer arrives through "Other" or a note, read it as a decision and fold it into the tree. If it opens new branches, they join the frontier.

## Facts versus decisions

Finding _facts_ is your job, never the user's. Never present an awnser as 'unverified'. When a frontier question needs a fact from the environment (filesystem, tools, etc.), dispatch a sub-agent with a fresh context window to find it. Do not ask the user for anything you could look up yourself. Do not block on it: a running exploration is an unsettled prerequisite, so only the questions downstream of it wait for the sub-agent to report. Ask the rest of the frontier now. The _decisions_ are the user's: put each to them and wait.

## Done

The session is done when the frontier is empty: every branch of the design tree visited, nothing left silently assumed. Then write a short summary of every decision in plain chat text, and ask one final `AskUserQuestion` to confirm it is the shared understanding. Do not act on it until the user confirms.
