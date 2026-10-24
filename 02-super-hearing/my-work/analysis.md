# Do interview complaints match tickets?

Sources: `interview-detail.md` (4 handler interviews, 2-5 Sep 2026) and `ticket-data.md` (147 support tickets, 29 Jun to 7 Sep 2026). Matched by meaning, not wording. Counts are tickets, not distinct problems. "After 12 Aug" means filed on or after the 4.2 release date, by filing date only. This file does not test a cause.

| Complaint | Interviews (of 4) | Tickets | Before 12 Aug | After 12 Aug | Match |
|---|---|---|---|---|---|
| Callout gone before answering | 3 | 15 | 0 | 15 | Yes |
| Quiet phone / uneven workload | 2 | 30 | 0 | 30 | Partial (no "swamped" ticket) |
| Text too small | 2 | 2 | 1 | 1 | Yes |
| Filters reset silently | 1 | 4 | 0 | 4 | Yes |
| Same alert sound | 1 | 2 | 1 | 1 | Partial (tickets ask per alert type) |
| No dark mode | 1 | 4 | 2 | 2 | Yes |
| Tag legend buried | 1 | 2 | 1 | 1 | Yes |
| Slow requisitions | 1 | 4 | 1 | 3 | Yes |
| No reply on failure reports | 1 | 2 | 1 | 1 | Yes |
| Poor catalog search | 1 | 2 | 1 | 1 | Yes |
| Praise: filters saved (thank-yous) | 1 | 2 | 0 | 2 | Yes |
| Live callout easy to miss | 2 | | | | No ticket |
| Cards tell different stories | 1 | | | | No ticket |
| Too much clicking | 1 | | | | No ticket |
| Everything else (missing features, defects, Supply, billing, other filter issues) | | 78 | 32 | 46 | No interview |
| **Total** | | **147** | **40** | **107** | |

## Key points

- 10 of 13 interview complaints are matched by tickets, 2 of them partly. 3 have no ticket.
- 69 of 147 tickets match an interview complaint. 78 match nothing the handlers said.
- The biggest ticket groups are the quiet phone (30) and callout gone (15). They are 45 of the 83 open tickets, and the interviews mentioned them least.
- All 45 of those tickets, and all 83 open tickets, were filed on or after 12 Aug. None of the callout tickets came before it.
- Filters reset silently has 4 tickets, all after 12 Aug. The other matched complaints are split between before and after.
- One contradiction: Halloran praised maintenance scheduling, but two tickets (3054, 3109) report suits booked on a busy day.

## Where the two piles disagree

They agree on the problems and disagree on how big each one is. The interviews were scoped to the console, so they lean that way. The tickets lean toward the phone and callouts.

### Loud in the interviews, rare or missing in the tickets

| Interview complaint | Interviews | Tickets |
|---|---|---|
| Live callout hard to miss on the console | 2 of 4 | 0 |
| Coverage cards tell different stories | 1 of 4 | 0 |
| Too much clicking to confirm status | 1 of 4 | 0 |
| Text too small (top ask for Ambrose and Dot) | 2 of 4 | 2 of 147 |
| Responder swamped with jobs (Kip's The Gale) | 1 of 4 | 0 |

Dark mode is the opposite case: Kip's one ask, and it has 4 tickets, so it is clearly shared.

### All over the tickets, missing or faint in the interviews

| Ticket theme | Tickets | In interviews |
|---|---|---|
| Phone quiet: far fewer pings | 30 | Only Dot and Kip, and mildly. Dot said "I don't mind", and Kip couldn't say why. |
| Missing features: handover notes, leave status, second sign-in, export | 14 | Not raised |
| Technical defects: logouts, slow loads, photo, phone number | 13 | Not raised |
| Filter follow-ups: wrong computer, wrong person's filters, hard-to-see badge, can't clear all | 10 | Only Ambrose's silent reset |
| Layout: detail panel covers map, feed jumps to top, list sorting, shortcuts | 10 | Not raised |
| Supply logistics: back-orders, wrong size, wrong delivery, late reminders | 16 | Only Halloran's three |
| Duplicate pings and accidental declines | 6 | Not raised |
| Screen reader, billing, how-to | 11 | Not raised |

The quiet-phone gap is the biggest one. It is the largest ticket group, and the one the handlers described most calmly. The tickets are blunter: "starting to wonder if im still even in the system."

### Where they directly disagree

- Maintenance scheduling: Halloran said it "hasn't done that in a while". Two tickets say suits were booked on the marathon day, and one (3109, 29 Aug) is still open.
- The console: Halloran called it "fine". 78 tickets match nothing the interviews said.
- Callouts: the interviews treated "gone before I could answer" as one complaint among several. In the tickets it is 15, and every one is open.

### Timing

Several interview complaints (dark mode, small text, tag legend, alert sound) have tickets from before 12 Aug, so they look long-standing. The quiet-phone and callout-gone tickets all start after 12 Aug, and none was filed earlier.

### Caveats

Four interviews against 147 tickets is not a fair comparison of size. The interviews were scoped to the console, so they asked about it and little else. Neither pile tells you the cause.
