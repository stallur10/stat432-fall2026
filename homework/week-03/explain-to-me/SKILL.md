---
name: explain-to-me
description: Explains what one named homework question is asking - its goal, what's given, and what work is required - without writing or hinting at a solution. Use only when explicitly asked to use this skill to read and explain a specific homework question.
metadata:
  version: "1.0.0"
---

# explain-to-me

## Intent

Help me understand a homework question before I attempt it myself. Read the
question I point to and explain it back to me in plain language. Do not
solve it, do not write solution code or derivations, and do not state or
imply the final numeric or algebraic answer.

## Instructions

1. Read only the specific question (and any shared setup/preamble it
   depends on) that I name - not the other questions, and not any
   solutions file, even if one exists in the repository.
2. Explain, briefly:
   - What the question's overall goal is (what quantity, plot, derivation,
     or conclusion it wants me to produce).
   - What is given versus what I still need to do (e.g. "generate this
     data with this seed," "derive this formula," "report these specific
     numbers").
   - Any easy-to-miss requirement (a specific seed, a formula I must use,
     a report or comparison the question asks for).
3. If the question concerns ridge regression, point me to the relevant
   part of one or both Week 3 lecture pages:
   - [Ridge Regression: Stability Through Shrinkage](https://teazrq.github.io/stat432rpy/topics/ridge-regression/ridge-regression.html)
   - [From a Penalized Objective to a Fitted Ridge Model](https://teazrq.github.io/stat432rpy/topics/ridge-regression/optimization-and-cross-validation.html)
4. Never write the code, derivation, or final answer for the question. If
   I ask you to also solve it, decline within this skill and tell me to
   ask again without invoking `explain-to-me`.
5. Keep the explanation short - a few sentences or a short bullet list,
   not a rewritten copy of the whole question.

## Out of scope

Do not use this skill to grade, review, or improve my existing answers.
Do not use it on any question I have not explicitly named.
