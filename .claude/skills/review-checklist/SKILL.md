---
name: review-checklist
description: Checks a product brief against six yes/no tests - it names who owns it, says how we'll know it worked, keeps the same scope from start to finish, explains the problem before the fix, gives management enough to decide and act, and describes the situation in terms of the people affected, in plain language. Use when the user points at a brief (a file path, a wiki page, or pasted text) and asks to review it, check it, or run the review checklist.
---

# Review checklist

Check one brief, or several, against the six tests below. You report; you do not rewrite the brief.

## Before you start

- The user points at a brief: a file path, a wiki page, or pasted text. If they point at a folder, check every brief in it. If you can't tell which brief they mean, ask once.
- Read the whole brief before judging any test. Scope, problem-before-fix, and whether it reads clearly can only be judged from start to finish.
- Judge only what the brief says. Don't use outside knowledge to fill a gap: if the brief doesn't say it, the answer is no.

## The six tests

1. **Owner named.** A person, a role, or a team is named as responsible for the work (for example "Marcus's team" or "the Dispatch PM"). Passing: a named owner. Failing: no owner, or only a wish that someone will take it on ("nobody's picked it up yet", "needs an owner").
2. **Success measure.** The brief says how anyone would know it worked: a number, a before/after comparison, or an observable change. Describing what gets built or logged is not a success measure.
3. **Scope stays the same.** The ask at the start is the ask at the end. Fail it when the document adds new requirements, features or audiences partway through, especially after saying how small or contained the ask is. Phasing that is stated up front counts as bounded; scope that creeps does not.
4. **Problem before the fix.** The problem is described before the solution is. Fail it when the brief opens with the solution (what we'd build and what it would do) and only reaches the problem later.
5. **Ready for management to decide.** Someone senior who has not followed the work could read it cold, understand what is going on and why it matters, and know what they are being asked to do. Pass only if all three hold:
   - the situation and its importance are stated up front, without needing background that is not in the brief;
   - there is a clear call to action: a specific decision, approval or next step is asked for, and it is clear who is being asked;
   - the brief gives the key facts that decision rests on, including what is still unknown.
   Fail it when the reader is left to work out what is wanted, or when the ask is only a vague "thoughts?" or "let me know".
6. **Customer-centric, plain language.** The situation is explained through what the people affected (customers, users, the people who use the product) experience, and a non-specialist can follow it. Fail it when the brief explains the situation mainly in internal or technical terms, such as code constants, formulas, scoring values, release internals, or unexplained jargon and acronyms, or when it never says what the affected people see or feel. A technical detail is fine if it is short, explained, and supports the people-first story. Quote the clearest examples of jargon in the flag line.

## Report format

For each brief, one block:

```
<brief name>
  owner named ................. yes / NO - flagged
  success measure ............. yes / NO - flagged
  scope stays bounded ......... yes / NO - flagged
  problem stated before fix ... yes / NO - flagged
  ready for management ........ yes / NO - flagged
  customer-centric, plain ..... yes / NO - flagged
  -> <one line per flag: what's wrong, with a short quote or the section where you saw it>
```

- Mark a pass with "yes" and a fail with "NO - flagged". Never mark something half-passing: pick one and explain it in the flag line.
- Each flag line says what is missing or where it goes wrong, in plain words, and quotes the brief where that helps.
- If a brief passes all six, write "-> no flags".
- End with a one-line tally, such as "4 briefs checked, 4 flagged, 1 flag each".

## Rules

- Don't edit or rewrite the brief, and don't suggest replacement wording unless the user asks.
- If part of the brief is missing, unreadable, or clearly unfinished, say so instead of guessing, and mark the affected tests as flagged with that reason.
- Rook content stays inside the course folder. Don't save anything from a review to memory or outside this directory.
