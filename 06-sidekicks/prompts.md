# 06 · Sidekicks — prompts

**Context:** You joined Rook two weeks ago as PM on Dispatch.
Release 4.2 shipped on 12 August, just before you arrived, and
landed badly. You've spent five sessions on it: finding out what
went wrong, then building the fix nobody had — a working prototype,
by hand, in one sitting, for one room.

At the end of the session, type wrap up, and Claude Code saves the
prompts you wrote yourself below — not the starter prompt — updates
CLAUDE.md, and saves your work to GitHub. By Module 6 this file is a
prompt library built from your own questions.

---

### 1.
Start with Module 6 now

### 2.
Make a skill called review-checklist. When I point it at a brief, it checks that the brief: names who owns it, says how we'll know it worked, keeps the same scope start to finish, and explains the problem before the fix.

### 3.
/review-checklist @05-super-speed/brief.md

### 4.
i want to add more tests in /review-checklist.
1. make sure that brief should have enough information for management to understand and call to action.
2. Make sure the brief is customer centric enough to explain the situation rather having multiple technical jargons and information.

### 5.
/review-checklist @05-super-speed/brief.md

### 6.
Make a skill called qa-testing. When I point to the product brief that outlines the requirements & the staging environment where the code build against it is housed, it creates robust acceptance criteria’s, validate’s them with me, performs the tests & generates a document with all findings.

Run a test on the my brief & assume we’ve built the prototype in a staging environment.
