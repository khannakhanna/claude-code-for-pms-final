# QA report: score recovery prototype

**Date:** 2026-11-07
**Brief tested against:** `05-super-speed/brief.md`
**Staging build:** `05-super-speed/prototype.html` (treated as the staging build; opened as a local file)
**Method:** real browser. Headless Google Chrome loaded a copy of the page (in the scratchpad, so the build itself was not touched) with a test script added that clicks the controls and reads what the page shows. Clock-based checks (the 60-second timeout) ran on Chrome's virtual clock.

## 1. Verdict

**Pass with one note.** 18 of 19 criteria passed, 1 failed. All 15 "Must" criteria passed. The one failure (AC7) is a "Should" item and comes from the wording of the criterion. A first run found a second failure (AC19); it was fixed and retested (section 7).

| Result | Count |
|---|---|
| Pass | 18 |
| Fail | 1 (AC7) |
| Blocked | 0 |
| Not testable here | 3 requirements (section 5) |

What matters most:
1. The scoring, recovery, marker and 90/60 second behaviour all match the brief, including the edges (floor, ceiling, and the 7th take needed from zero).
2. On the first run, the screen titled "Kip's handler console" did not show Kip's responders (AC19). The console was changed to list Meteor Mite and The Gale and retested: it now passes.
3. Under "None", the phone shows 2 pings in week 0, not 1 as the criterion said (AC7). This is a wording problem in the criterion, not a defect against the brief.

## 2. Acceptance criteria and results

| ID | Requirement (brief) | Expected | Actual | Result |
|---|---|---|---|---|
| AC1 | "Old misses… lose weight" | With recovery on, the score rises every week 0 to 6 and stays at or below 0.50 | 0.05, 0.21, 0.31, 0.38, 0.42, 0.45, 0.47 | Pass |
| AC2 | "nothing ever fades" | With None, the score stays 0.05 and no marker shows | 0.05 in every week; marker never shown | Pass |
| AC3 | "Quiet responders reappear in the rankings" | Rank never gets worse; better at week 6 than week 0 | The quiet responder's rank 5, 5, 5, 4, 4, 4, 4 (after the AC19 fix) | Pass |
| AC4 | "A 'recovering' marker" | Marker shows while score is below 0.50 | Week 3, score 0.38: row shows "Recovering ↑" | Pass |
| AC5 | marker, negative cases | No marker under None, Before 4.2, or once score is 0.50 or more | None: no; Before 4.2: no; score 0.87: no | Pass |
| AC6 | "phone app says the ping rate is recovering" | Message with recovery; none under None | "Your ping rate is recovering" shown; under None: "the app does not say why" | Pass |
| AC7 | "Pings come back" | Higher at week 6 than week 0 with recovery; stays at 1 under None | Recovery: 2, 3, 5, 7, 9, 10, 11. None: 2, 1, 1, 1, 1, 1, 1 | **Fail** (see F2) |
| AC8 | "missed or turned-down… costs 0.12" | Miss 5 and Turn down 5 give identical scores and ranks | Identical from 0.05 (hits floor) and from a 0.47 start: 0.35, 0.23, 0.11, 0.00, 0.00 both ways | Pass |
| AC9 | "a taken ping adds 0.08" | +0.08 per take, 0.45 after five | 0.13, 0.21, 0.29, 0.37, 0.45 | Pass |
| AC10 | scoring limits | Floor 0.00; ceiling 1.00 | Miss 10 stops at 0.00; Before 4.2 start 0.90 then 0.98, 1.00, 1.00, 1.00, 1.00 | Pass |
| AC11 | "6-7 takes in a row from zero" | First reaches 0.50 or more on the 7th take | From 0.00: after 5 takes 0.40, 6th 0.48, 7th 0.56 | Pass |
| AC12 | a missed ping | Skip-ahead and a full 60-second run-out both log Missed, −0.12 | Start 0.47; skip-ahead gave Missed 0.35; waiting 61 s gave Missed 0.23 | Pass |
| AC13 | "ping wait (90 to 60 seconds)" | Countdown starts at 90 Before, 60 After | 90 and 60 | Pass |
| AC14 | "ranking weights (proximity up)" | 0.45/0.40/0.15 Before; 0.60/0.25/0.15 After | Both shown as expected | Pass |
| AC15 | before vs after 4.2 | Before 4.2: Vesper 1st; recovery and slider disabled | Rank 1; both disabled | Pass |
| AC16 | "17 pings, 5 taken, 3 turned down, 9 missed" | Replay logs those counts and ends at 0.00 | 17 events: 5 taken, 3 turned down, 9 missed; final 0.00 | Pass |
| AC17 | state | Clear empties the log and resets; switching release clears simulated pings | Log empty, Vesper back to 0.05; release switch emptied a 5-ping log | Pass |
| AC18 | usability | Rows reachable by Tab and opened with Enter; no sideways scroll at 375 px | Rows all focusable; Enter opened "Nightwell"; at 375 px the page was 375 wide with no overflow | Pass |
| AC19 | "Kip handles Meteor Mite and The Gale" | The console titled Kip's lists his responders | First run: rows were Nightwell, Captain Vantage, The Longcast, Example D, Vesper; neither Meteor Mite nor The Gale. After the fix: Nightwell, The Gale, Captain Vantage, The Longcast, Meteor Mite | Pass (after fix) |

## 3. Findings

**F1 · Minor · AC19 · Fixed and retested: The "Kip's handler console" listed other people's responders.**
- Steps: open the page, look at the console card.
- Expected: Kip's responders, per the brief ("Kip handles Meteor Mite and The Gale, both in Eastgate").
- Actual: five responders from other areas and handlers, with Vesper (Aunt Dot's, Old Town) in the middle.
- Fix: the console now shows an Eastgate callout with Meteor Mite and The Gale among the ranked responders, and the first screen note says one simulated quiet responder drives both screens (Meteor Mite on the console, Vesper on the phone).
- Why it mattered: the brief's story for Kip is Meteor Mite going quiet while The Gale gets busier. The prototype does not show that, and Helen could notice the mismatch.

**F2 · Note · AC7: The criterion was imprecise.**
- Under "None" the phone shows 2 pings in week 0 and 1 from week 1. The criterion said "stays at 1".
- The intent (pings do not come back without recovery) holds, and the brief does not specify a week 0 figure. No build defect. Recorded as a Fail because the approved criterion was not changed after the result.

**F3 · Note · The prototype contains choices the brief does not make.**
- Recovery closes 35% of the gap each week, so Vesper is still at 0.47 after six weeks and never reaches 0.50 in that time.
- A "Quiet" tag appears below 0.30 under None. Before 4.2 starts Vesper at 0.90 and ranks first.
- One simulated quiet responder drives both screens, shown as Meteor Mite on Kip's console and Vesper on the phone. In the real data their patterns differ (Meteor Mite: 14 pings since 12 Aug, 3 taken, 3 turned down, 8 missed; Vesper: 17 pings, 5 taken, 3 turned down, 9 missed).
- All are example values. They should be confirmed before anyone treats the prototype as a specification.

**F4 · Note · Test method.**
- My first run read the wrong column (the match score instead of the recent-acceptance score) and reported six false failures. I corrected the script and reran everything before recording results. Those first numbers are not used here.
- AC8 passed on the first try only because every ping hit the 0.00 floor, so I added a rerun from a higher starting score. The stronger rerun passed too.

## 4. Gaps and questions in the brief

- The recovery rate is not specified. The prototype's 35% a week is invented.
- "A stretch without new misses" has no length, so "pings come back" cannot be tested precisely.
- The brief says a responder who "has stopped taking work" should stay low, but gives no rule for that, so it cannot be tested.
- The success measure has no target (how many responders, how many weeks).
- It is not stated whether the console already shows Kip anything about why a responder ranks where they do; the brief says this was not checked.

## 5. Not tested

- **Success measure** (responders pinged less than half as often as before 4.2; weeks spent quiet): the prototype has no report for it.
- **"Without an override":** the prototype has no override feature.
- **Whether recovery fixes real quiet responders:** needs real data.
- **Real phone behaviour:** a real Tab key sequence and touch use were not exercised. Keyboard support was checked by sending the Enter key and by checking that rows are focusable.
- **Appearance:** colours, spacing and dark mode were not checked.

## 6. Approval record

The 19 acceptance criteria were shown to the user as a table and approved as written ("Approve all 19") before any test ran. No criteria were added, removed or changed. Two checks were strengthened in method only (AC8, AC18); their expected results were not changed.

## 7. Retest after the AC19 fix

- The prototype was changed after the first run: the console's responders now include Meteor Mite and The Gale and the callout is in Eastgate.
- All 19 criteria were run again on the changed build, with the same method. Result: 18 pass, AC7 still fails for the reason in F2.
- Rank-based results changed because the list of responders changed (AC3: ranks 5, 5, 5, 4, 4, 4, 4). Every criterion still met its expected result.
- The stronger AC8 check (from a 0.47 start) and the 375 px width check (AC18) were also rerun and passed.
