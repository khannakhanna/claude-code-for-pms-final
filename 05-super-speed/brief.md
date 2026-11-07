# Dispatch: let a quiet responder earn their way back

For Helen · from the Dispatch PM · a draft to react to, not a decision to ship

## The problem
Since 4.2 (12 Aug), four responders (Farlight, Meteor Mite, The Undertow, Vesper) went from about 12 pings a week to 0-3. After 12 Aug they missed 33 of 56 pings (59%) against 14% for the other 12; the turned-down share didn't rise. The weekly acceptance rate, back to about 73%, hid this.

Dispatch scores recent acceptance: a taken ping adds 0.08, a missed or turned-down one costs 0.12, and nothing ever fades. A low score means few pings, so few chances to climb back (about 6-7 takes in a row from zero). 4.2 changed the ping wait (90 to 60 seconds) and the ranking weights (proximity up) together. We don't yet know which drove the misses.

## What we'd build instead of changing a number
**Score recovery over time.** Old misses and turn-downs lose weight, so a rough patch fades without the responder winning it back one ping at a time. A 2019 note in the code already asks this: a bad month "shouldn't still be carrying it in the spring", but if someone "has stopped taking work, we probably want that to stick until they take work again". Our design has to answer that second half.

Unlike reverting the ping wait, it changes what happens to a person after a bad stretch. We aren't recommending a revert: we can't yet say which 4.2 change caused the misses, and recovery helps either way.

**Success measure:** not the weekly rate. Count responders pinged less than half as often as before 4.2, and weeks spent quiet (Ravi to confirm this can be reported per responder).

## For Kip (handler) and Meteor Mite (quiet responder)
Kip handles Meteor Mite and The Gale, both in Eastgate. Meteor Mite was pinged on 62 of 118 Eastgate callouts before 12 Aug and 9 of 57 since; The Gale on 76 of 118, then 54 of 57. Since 12 Aug Meteor Mite has had 14 pings (3 taken, 3 turned down, 8 missed); the last taken ping was 19 Aug. We haven't checked what the console shows Kip today.
- Meteor Mite reappears in the rankings, with a "recovering" marker that shows why someone is ranked where they are.
- Pings come back after a stretch without new misses, and the phone app says the ping rate is recovering, so a quiet phone isn't a mystery.

Vesper (Aunt Dot's, Old Town) shows the same pattern: 17 pings since 12 Aug (5 taken, 3 turned down, 9 missed). The prototype can follow either.

*Our inference: no responders have been interviewed, and no ticket mentions Meteor Mite, Vesper, or their handlers.*

## Not proven
- Why the first misses happened. Late answerers (60-90 seconds) now missing fits the code, but the data has no answer times. Priya reads the drop as seasonal; there is no earlier-year data to check.
- Whether recovery is enough if the 60-second wait keeps causing misses.

## Questions for you
1. Marcus asked on 14 Aug whether the 4.2 ranking change was meant to apply equally to responders who turn jobs down. Wen said she'd look; the latest wiki comment (28 Aug) shows no answer. The code counts a miss and a turn-down the same ("we asked and we didn't get a yes"). Was that a decision?
2. Do you want answer-time data before we decide?

A clickable prototype (`prototype.html`) shows Kip's console and the phone, with a switch between Meteor Mite and Vesper.
