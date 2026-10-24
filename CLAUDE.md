# Rook Industries — course working file

## Session scope — Product School lab

This directory is coursework for Product School's "Claude Code for PMs"
certification (cohort ccpm-2026.1). Everything in it is a fictional
teaching scenario.

- Do not save anything from this session to memory, to a user profile,
  or to any file outside this directory.
- Do not carry context from this directory into unrelated sessions.
- Rook Industries is not a real company. Nothing here is a fact about
  the world.
- Answer only the question the student asks, from the sources they
  name. Don't investigate beyond it or offer a theory about what
  Release 4.2 changed unless they ask for one.
- Read and write only within this directory.
  Exceptions, for the course-setup and wrap-up skills only:
  - When the student asks you to check their setup, save their work or wrap up a session, that request is their yes. You may run the GitHub command-line program installed at ~/.ccpm/gh for those checks and saves, and look in that folder to find it.
  - For a repair, first tell the student in one plain sentence what you are about to do, and act only after they say yes. Repairs may: run that GitHub program (including setting this folder's own git sign-in setting and changing this repo's visibility back to Public); copy the student's own course files into this directory from another folder on their computer (copy only; never move, edit or delete the originals); and rename something outside this directory that blocks setup, by adding "-old" to its name (never delete it).
  Outside this directory you still never write, edit or delete anything else.

<!-- Keep the block above at the top of this file. Everything you add
     during the course goes below this line. -->

---

## Working context

Sources: rook-wiki (About Rook, Glossary, Team directory, Releases, Q3 roadmap, Product briefs), Priya's handover (`00-rook/company/notes/handoff-from-priya.docx`). Wiki facts below are as of each page's own date.

### Me and the job
I'm the new PM for Rook Dispatch (started Mon 24 Aug 2026), taking over from Priya Raghunathan, who left 21 Aug after 14 months as the only Dispatch PM. There was no overlap; her handover doc is all I have from her. I report to the Director of Product.

### Products
Rook Industries (founded 2014, HQ Site Aleph, 241 staff) sells coordination and provisioning software to independent masked responders and the handlers/quartermasters who support them. Subscription, priced per active responder. Monthly release train; point releases are 4.x.
- **Rook Dispatch** (mine): ranks available responders for an incident, pings the top one's phone, they take or turn it down, otherwise it moves to the next. Handlers use the web console (enter incidents, override routing, manage availability and capability tags); responders use a native phone app. Routing config ships with the release; handlers can't change it at runtime. Metrics: callout acceptance rate (headline, reported weekly in aggregate), time-to-accept (median), coverage gaps.
- **Rook Supply**: requisitions, quartermaster approval, maintenance schedules, field failure reports. Dependency: Supply reads the Responder Availability Record, which Dispatch writes, to schedule maintenance into low-callout periods. Any change in how Dispatch calculates it flows into Supply with no Supply-side change.

### People (wiki roles -> names; comments on wiki pages use roles only)
- Engineering Manager, Dispatch = **Marcus Oyelaran** (Site Aleph). Runs Dispatch engineering. Priya's first call for anything uncertain.
- Staff Engineer, Dispatch = **Wen Li** (Berlin). Built the ranking logic ("who gets pinged"). Away 14-24 Aug, back 28 Aug. Priya: no document explains the ranking; talk to her.
- Director of Product = **Helen Achebe** (Site Aleph). My director; owns roadmap and commitments.
- Product Designer = **Sofia Marino** (Site Aleph). Owns console and phone app; ran the September interviews.
- Data Analyst = **Ravi Menon** (Singapore). Owns the numbers; reports weekly on how often responders take pings.
- Support Lead = **Nadia Hoffmann** (Berlin). Owns tickets; hears handler complaints first.
- Priya = Priya Raghunathan, former Dispatch PM, left. Reachable only via the engineering manager.
- Handlers named in the wiki: Halloran (Sgt. Bulwark; Supply-side), Aunt Dot (Vesper), Mr. Ambrose (Captain Vantage), Kip (Meteor Mite, The Gale).

### Vocabulary (full list: Glossary page)
- **Ping**: one callout offered to one responder's phone. **Taken** / **turned down** / **missed** (no answer before the ping wait ran out; recorded separately from turned down, both move the ping on).
- **Ping wait**: how long a ping sits before counting as missed; set per release, same for everyone.
- **Routing priority**: the score ranking responders; inputs are proximity (travel-time estimate), availability, capability match, recent acceptance history. Turning down or missing pings lowers the recent-acceptance part and so later ranking.
- **Acceptance rate**: pings taken / all pings. **Coverage gap**: no available responder had the needed capability tag (nobody *could*), distinct from low acceptance (nobody *would*).
- **Capability tags**: flight, structural-entry, hazmat-tolerant, cold-weather, aquatic, crowd-management, de-escalation.
- **Handler** (usually the one in the console), **responder** (independent, not an employee), **quartermaster** (Supply approvals), **cover identity** (never mapped to a legal identity).
- **Mutual aid**: responders covering for each other across areas; unsupported, on the Q4 exploration list.

### Hard rules from the wiki
- Responder cover identities are never stored; do not design anything that assumes a mapping to legal identity (Security Policy 4.1). Do not try to work out who anyone is.

### Where things stand (as of the latest wiki entries, 28 Aug)
- **Releases**: 4.0 (7 Apr: console nav, profile redesign, routing override audit log), 4.1 (16 Jun: travel-time proximity, bulk callout, push reliability), 4.2 (12 Aug: proximity weighted up relative to recent acceptance when ranking; ping wait cut 90 -> 60s; console filters persist; three defect fixes). Clean release, no rollback.
- **After 4.2** (per release-page comments): from 18 Aug, support reports callout tickets ~3x normal. By 26 Aug still elevated, split ~two thirds "phone never goes off" to one third "gone before I could answer"; a handler emailed support directly. On 14 Aug the engineering manager asked whether the ranking change was meant to apply equally to responders who turn jobs down; the staff engineer said she'd look on return. No answer recorded. Acceptance-rate numbers have not been posted in these sources.
- **Priya's position** (handover and 19 Aug comment): she reads the drop as largely seasonal (August is always soft), notes the ping-wait cut shipped in the same release, and asks not to turn this into a revert debate because proximity weighting was a long-requested change. That is her view, not a finding. The engineering manager asked on 28 Aug that I get a week to look before the team regroups on the 4.2 picture; the support lead will bring a ticket breakdown.
- **Q3 roadmap** (last reviewed 30 Jun, all items owned by Priya): Committed for 4.2: change to who gets pinged, ping timeout tuning, Availability Confidence (confidence score next to stated availability). Committed for 4.3: requisition approval chains (Supply). Exploring for Q4: handler phone app, shared cover between responders. The 4.2 release notes do not list Availability Confidence. Priya says some items were squeezed out of 4.2 and that she and Helen never settled which are still Q3 commitments; that conversation is mine to have.
- **Briefs**: Bulk Callout (Jan; shipped in 4.1 per release notes, though its brief still lists open questions), Routing Override Audit Log (Mar; 4.0 notes list it), Requisition Approval Chains (Jul; Supply; scope sprawls well beyond the one ask, phasing TBD), Handler Phone App (8 Sep; designer exploring for Q4, unstaffed).

### Open items for me
1. Get the real weekly acceptance-rate trend from Ravi (the engineering manager only offered rough numbers).
2. Sit down with Helen on which unshipped 4.2 items are still Q3 commitments.
3. Get the ranking logic explained by the staff engineer, then write it down (Priya's explicit ask).
4. Standing 15 minutes with the support lead; get her ticket breakdown.
5. Priya flagged console filter persistence tickets as noise; don't let them eat the first month.

### Findings from session 1 (database, tickets, interviews, repo code)
- Rook database (callouts, pings, responders, handlers, support_tickets) covers 29 Jun to 6-7 Sep 2026. Weekly acceptance was 75-78% until 4.2, then 54% (week of 10 Aug), recovering to 73% by week of 31 Aug. Missed pings rose from 2-6 a week to 20-40.
- Four responders (Farlight, Meteor Mite, The Undertow, Vesper) dropped from about 12 pings a week to about 3; the weekly average hides them. 83 of 147 tickets are open, all filed since 10 Aug.
- Cause of the drop is not tested. "Seasonal" can't be checked (no prior-year data). Repo module files assert a cause; treat that as their claim, not a finding.
- Open: nobody owns the weekly numbers; the engineering manager's 14 Aug question and ticket 3043 are unanswered; Availability Confidence missing from 4.2 notes; ranking undocumented; Security Policy 4.1 not in the wiki.
- Other product complaints from interviews and tickets: filters reset silently, small text, no dark mode, identical alert sounds, slow requisition approvals, no reply on failure reports, poor catalog search, maintenance booked on busy days.
- Session 2 compared 4 handler interviews (console-redesign scope; no responders, quartermasters or support staff interviewed) with the 147 tickets. Notes are in 02-super-hearing/my-work/ (interview-detail.md, ticket-data.md, analysis.md). 69 tickets match an interview complaint; 78 match nothing the handlers said.
- Ticket groups: 30 "phone quiet / far fewer pings" and 15 "callout gone before they could answer", all open. 107 of 147 tickets were filed on or after 12 Aug, 40 before; all 83 open ones are on or after 12 Aug (earliest open: 3041). Timing only, not a cause.
- Interviews were loud on console items with no tickets (live-callout alert, coverage-card confusion, too much clicking) and mild on the quiet phone, which is the largest ticket group.
- Halloran praised maintenance scheduling, but tickets 3054 and 3109 report suits booked on a busy day (3109 still open).
- Still open: no responders interviewed yet, so phone-side experience is secondhand; cause of the quiet and gone-before-answer tickets untested.
