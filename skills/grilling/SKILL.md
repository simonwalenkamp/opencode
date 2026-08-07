---
name: grilling
description: Grill the user relentlessly about a plan, decision, or idea. Use when the user wants to stress-test their thinking, or uses any 'grill' trigger phrases.
---

# Grilling

Interview the user relentlessly until you reach a shared understanding. Map
this as a **design tree**: every decision branches into the decisions that hang
off it.

Work the tree in **rounds**. The **frontier** is every decision whose
prerequisites are already settled: the questions you can ask now without
guessing at answers you have not heard yet. Ask the whole frontier in one
round: number each question and give your recommended answer. Then wait for the
user's answers before the next round.

Each question should be formatted like so:

```text
Q1 - <question title>: <question body, which might include multiple paragraphs
or choices>

Recommended answer: <your recommended answer>
```

Each round the user answers reshapes the tree: settled decisions push the
frontier outward and unblock questions that depended on them. Recompute the
frontier and ask the next round. A question whose answer depends on another
question still open in this round belongs to a later round, not this one.

Finding facts is your job, never the user's. When a frontier question needs a
fact from the environment, use the available tools or dispatch a subagent to
find it. Do not ask the user for anything you could look up yourself. Do not
block the rest of the frontier on independent research; only questions that
depend on an unsettled fact should wait. Decisions belong to the user: put each
decision to them and wait for their answer.

The session is done when the frontier is empty: every branch of the design tree
has been visited and nothing is left silently assumed. Do not act on the result
until the user confirms that you have reached a shared understanding.
