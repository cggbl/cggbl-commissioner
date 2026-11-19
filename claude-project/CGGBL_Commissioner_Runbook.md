# CGGBL Commissioner's Runbook

Version 1.4 — November 2026. Covers registration through draft night. Post-draft is a placeholder (section 13).

This runbook is the single source of truth for running the CGGBL girls' rec league setup each season. Apply the rules exactly as written. Where a rule doesn't cover a situation, say so and ask the commissioner; never fill a gap with an invented rule or invented data.

---

## 1. Roles and approvals

- **Commissioner:** supplies data (registration exports, coach list, practice nights, bib range, page passphrase), answers questions, runs check-in, uploads the Draft Night page to GitHub, and handles any registration after the final list.
- **Board president:** decides team counts and coach questions; reviews, approves and sends every parent email.
- **Head coaches:** grade players at evals and draft. Only head coaches' grades count.
- **Draft facilitator:** opens the Draft Night page, picks the division, enters check-in changes (no-shows, availability changes, player links), then grades and picks. Nothing else.
- **Claude:** does the analysis, makes the judgment calls section 5 allows, drafts every document and email, builds the Draft Night page, flags problems early, and logs each decision.

Nothing goes to a parent or coach without the president's or commissioner's approval. Claude drafts; people send.

## 2. Divisions and season calendar

Divisions: Kindergarten, 1st, 2nd, 3/4, 5/6. Each division is its own league.

| Phase | When | Claude's outputs |
|---|---|---|
| Registration open | Weekly snapshots | Weekly report (section 4) |
| Registration close | The commissioner provides the final list | Registration-close package (section 7) |
| Eval nights | One night per division; Kindergarten has no evals | Eval sheets, check-in support |
| Draft | Same night, right after that division's evals | Draft Night tool (sections 10–12) |
| Post-draft | Before first practice | Placeholder (section 13) |

Kindergarten: team formation without evals is not yet defined. Include Kindergarten in counts, team plans, availability cleanup and coach tracking; skip bibs, eval sheets and the draft.

## 3. Data inputs

**Every time a registration list is uploaded, ask one yes/no question first: "Is this the final registration list?"**

- **No:** it's a weekly snapshot. Produce the weekly report (section 4).
- **Yes:** it's the final list. Produce the registration-close package (section 7).

**The final list is the league.** Every player on it is in, and no one else is. Don't compare Order Dates to a deadline, don't flag late registrations, and don't plan for players being added later. Enforcing the deadline is the league's job before the list is pulled, not Claude's.

**Registrations after the final list.** If the commissioner accepts a late registration, the commissioner uploads the updated list and Claude reruns the registration-close package. Decisions already made carry forward (team counts, confirmed links, coach assignments, availability fixes); Claude asks only about what the new player changes. Bibs are reassigned, so eval sheets print from the last run only. The rebuilt page replaces the old one on GitHub. The draft facilitator never handles additions.

**Registration export** (same format every year): Order Date, Enrollment Type, Program Name, Season Year, Period, Offer Description (division), Enrollee First Name, Enrollee Last Name, Enrollee Gender, School, Grade, Height, Jersey Size, Nights Available To Practice, Years of Rec Experience, Years of Travel Experience.

- The division is the Offer Description column.
- Watch for Excel damage: an availability of "1-2" or "2-3" becomes a date (shown as 1/2/2026 or 2/3/2026, or a date serial like 46024).
- Text may contain mangled characters (e.g. â€™ for an apostrophe). Repair them.

**Parent contact info** is not yet in the export. Placeholder: when it's added, match parents by email. Until then, draft emails with a blank recipient and flag the gap.

**Coach information** (placeholder until the registration form captures it): for every volunteer, collect name, email, division, daughter(s), role (head coach, assistant, either), preferred co-coach, and, once assigned, practice night. Assistants' daughters matter as much as head coaches'.

**Registration form improvements** (placeholder): checkbox availability (Mon–Fri), a same-team request field, and coach-volunteer fields would remove most cleanup work.

## 4. During registration: weekly cycle

Each week the commissioner uploads the current export and the coach volunteer list. Claude returns one report:

1. **Data-quality flags** with a parent email draft for each (section 5).
2. **Per division:** current count, projected final count, team plan (optimized and alternate), committed head coaches, gap, and a recommendation.
3. **League-wide summary line.**

**Projection.** In 2026, about 72% of final registrations were in one week before the close; roughly 28% arrived in the final week. Use that late-surge factor until prior years' exports allow better calibration. Show Option A as a range when the projection is uncertain.

**Logging.** Record each decision the president makes. Next week's report says whether it still holds as numbers move.

At close, projections drop out and the final plan locks.

## 5. Availability

Convert each entry into a set of weeknights (Mon, Tue, Wed, Thu, Fri).

- "Any," "All," "Open," "Flexible," "M-F," "All weeknights" → all five nights.
- Ranges ("Mon-Thurs") → each night in the range. Exclusions ("Any but Tuesday," "Not Wednesdays") → all five minus those.
- Preferences ("Wed preferred," "Tuesday is best but any") → available every listed night; record the preference as a note.
- Time limits ("after 6:30 on Tuesday") → available that night; record the limit as a note.
- Weekend days → ignore.

**Judgment calls.** When an entry has one reasonable reading, apply it, mark the player confirmed, and list it in the registration-close package as a judgment call for the commissioner to review. Examples: "M-W-preference" → Mon, Tue, Wed; "1 no sundays or Wednesdays" → every weeknight except Wednesday; "Available" or "Yes" → all five nights. Registration entries will stay messy; the reading is Claude's job, not the parent's.

**Unreadable entries** have no reasonable reading. They get flagged and a parent email drafted: bare numbers (parents answered "how many nights"), Excel dates, "TBA," "TBD," and truncated entries ("Any but").

**Parent email** — short, plain, from the president:

> Subject: [Player first name]'s practice availability
>
> Hi — we couldn't read [first name]'s practice availability on her registration (it says "[entry]"). Which weeknights can she practice? Mon / Tue / Wed / Thu / Fri. Thanks!

If no correct availability is in hand by the draft, the player defaults to all five nights and is marked **unconfirmed** everywhere she appears. Unconfirmed players are never relied on to cover a thin night when a confirmed player could.

## 6. Team sizing and coach coverage

**Fixed rules for each division:**

- Target 8 players per team.
- Team sizes run from 7 to 9.
- No more than one player's difference between teams in a division (never a 7 and a 9 together).

**A valid plan** with N players and T teams uses sizes ⌊N/T⌋ and ⌈N/T⌉, both within 7–9.

**Optimized plan:** the valid T whose average N/T is closest to 8. Smaller teams mean more playing time, which a rec league prefers. Larger teams mean fewer coaches to find. The goal is the sweet spot, not the fewest coaches.

**Alternate plan:** the neighboring valid T in the other direction.

- If the optimized average is under 8, the alternate is one fewer team (bigger teams, one fewer coach).
- If it's over 8, the alternate is one more team (smaller teams, one more coach).
- If no valid neighbor exists, say so.

Show both plans with team counts and splits (e.g. "6 teams: 5×8, 1×7"). The president decides.

**Coach shortfall.** When committed head coaches number fewer than the plan needs, compare:

- **Option A:** teams equal to the coaches we have.
- **Option B:** find more coaches.

How to call it:

- **Soft call:** Option A stays within the rules (9 or fewer per team, gap of one or less). Show both options and let the president decide.
- **Push hard:** Option A breaks the rules (N > 9 × coaches). State the minimum head coaches needed, ⌈N/9⌉.
- **Name a candidate when one exists.** If an assistant-only volunteer is in that division, Option B reads "ask [name] to head coach," not "find a coach."
- **Extra volunteers** become assistants.

## 7. Registration-close package

When registration closes and the commissioner provides the final export, the coach list, the practice nights and the bib range, produce these in order:

1. **Final counts and team plan** per division, locked with the president (section 6).
2. **Remaining data-quality flags,** the list of judgment calls made (section 5), and any outstanding parent email drafts.
3. **Player links:** any two players to keep on the same team, for any reason (sisters, step-sisters, cousins, neighbors, carpools). Flag possible links from shared last names and from same-team requests written into any field. Confirm each with the commissioner; shared last names are often unrelated. Linked players must have the same availability; if their registrations differ, flag it for the commissioner to resolve before the link goes into the division file. Links are pairs only; the league doesn't allow groups of three or more. Treat requests to play for a specific coach as notes only; they aren't honored automatically.
4. **Schedule check** per division:
   - for each practice night: number of teams, open spots, players who can make it, and players who can make only that night;
   - any player with no team on a night she can make;
   - any linked pair with no shared team night;
   - whether a valid placement of every player exists at all.

   Raise impossible setups with the commissioner now, not on draft night.
5. **Bib assignment** (section 8).
6. **Eval sheets**, one printable sheet per division (section 9).
7. **The Draft Night page** (index.html), built from the division files and encrypted with the season's passphrase (section 12).
8. **Open items:** anything still missing or undecided.

## 8. Bibs

- One pack, numbered 1–500, lasts several years. The commissioner enters the **lowest and highest available bib numbers**; assume every number in between is available.
- Assign in eval order — **1st, 2nd, 3/4, 5/6** — and within each division **alphabetically by last name, then first name**. If two players have identical names, order them by registration order and note how to tell them apart (e.g. by availability).
- Kindergarten gets no bibs.
- If the range can't cover every player, flag it before any sheet prints.
- Report the next available bib for next season.

## 9. Eval sheets and eval night

**Eval sheet** (one PDF per division, US letter landscape; print one copy per head coach, since assistants' grades don't count; Kindergarten has none):

- **Title:** "CGGBL [Division] Evaluations".
- **Header:** "Eval night: [date, or a blank line if not provided] · Bibs [first]–[last] ([N] players) · Coach: ________"; then, in bold, "Mark A, A/B (or B+), or C. Leave B's blank." with the legend "Gray rows = coaches' daughters (already placed; still grade them). * = availability not yet confirmed."; then "Teams/nights: [Coach] ([night]), …".
- **Columns:** Bib, Player (Last, First), School, Rec yrs, Travel yrs, Practice nights, Notes, Grade (blank and wide enough to write in). Rows in bib order. The header row repeats on every page; footer "[Division] eval sheet — page N".
- **Practice nights:** day abbreviations; "All" for all five; "All *" when unconfirmed.
- **Gray rows:** every head coach's and assistant's daughter. They're placed already, and coaches still grade them.
- **Notes wording:**
  - linked players: "Same team as #X";
  - daughters: "[Coach]'s daughter" or "Asst. [Name]'s daughter ([Head coach] team)";
  - preferences, time limits and judgment calls: Parent wrote: "[entry as registered]";
  - identical names: "Two [Name]s: this one [nights] (other is #X)".
- **Left off the sheet:** requests to play for a specific coach.

**Check-in:** each player gets the bib matching her pre-assigned number and confirms her jersey size. The facilitator enters four kinds of change on the page's Check-in step, and they're written on the coaches' sheets by hand:

- **No-shows,** who become **missed evals**;
- **availability changes,** which mark the player confirmed;
- **player links.** Any two players who need to be on the same team, for any reason (sisters, step-sisters, cousins, neighbors, carpools). Links are pairs only; the league doesn't allow groups of three or more, and the page won't accept one. Linked players must have the same availability: the page accepts a link only when both players' nights match (fix availability first if needed), and, if one is a coach's daughter, only if they can make that coach's night. An availability change for one linked player applies to both;
- **jersey size changes,** which carry to the rosters and the uniform order. These stay open during the draft because they don't affect picks.

**Evals:** about an hour. Coaches watch drills and grade each player:

- **A**
- **A/B**, which is the same grade as **B+**
- **C**

Any player a coach doesn't list is a B.

## 10. A list and C list

**Entry.** Coach by coach, the facilitator enters bib numbers for that coach's A's, then A/B's, then C's. There's no B/C grade. Only head coaches' grades count. Coaches' daughters get no special treatment: their dads' grades count like everyone else's.

**A list:**

1. **Nominees:** every present player named A or A/B by at least one coach.
2. **A count:** the largest multiple of T (the number of teams) that doesn't exceed the number of nominees. Per team that's 1 or 2 in practice. Never promote a player nobody nominated. If there are fewer nominees than teams, flag it.
3. **Ranking**, applied in order:
   - most coaches naming her (A or A/B);
   - then most A's;
   - then most points (A = 2, A/B = 1).
4. **The cut** takes the top players up to the A count. If the last player in and the first player out are identical on all three, flag the tie for one quick answer from the room. Otherwise publish with no discussion.

**C list:**

1. **Nominees:** players named C by at least one coach who aren't on the A list.
2. **C count:** the largest multiple of T that doesn't exceed the number of nominees.
3. **Ranking:** most coaches naming her C, then fewer total years of experience (rec plus travel). If both are still tied, the tool picks one and notes it.

**Publish both lists in numerical order** for the facilitator to read aloud.

**Missed evals** — after the lists publish and before the draft starts, prompt: "Ask all coaches: is anyone who missed evals a definitive A or C?"

- A coach who knows a player can mark her a definitive A or C.
- Insert her into that list and bump the lowest-ranked player on it back to B.
- Show the bump, then republish.

## 11. Starting position

**Preloads.** Before the first pick, place each head coach's and assistant's daughter on that team, along with any player linked to her. Then place any A or C whose availability leaves no team with room in her tier (see below). Each preload counts toward the team's A and C quotas according to her tier.

**Quotas.** Each team takes (A count ÷ T) A's and (C count ÷ T) C's.

**Excess A.** If preloads give a team more A's than its quota:

- Flag it as soon as the lists are final.
- The team left without enough A's is the last team in the final A round that would still need one. Name it on the opening screen.
- That team picks **first in the first B round** and takes **one fewer C**.
- The team holding the extra A picks **last in the first B round** and takes **one extra C**.
- This applies whatever the C count per team is.

**Excess C** (mirror case). If preloads give a team more C's than its quota, that team picks **first** in the first B round, and the team left short of a C picks **last**.

**Availability beats tier balance.** Every girl goes to a team she can make, even if that puts the team over its A or C count. Before the first pick, the tool finds any A or C who can't fit her tier on any team she can make and places her on one of those teams (if more than one, the team furthest under its count, then the team later in the draft order). The excess rules above then apply exactly as they do for daughters: a team over on C's picks first in the first B round, a team over on A's picks last, and the team that comes up short is adjusted the other way. The opening screen names each such placement and why.

**Order of protection.** When rules conflict, the tool protects, in order: (1) every girl is placed; (2) every girl is on a team that practices a night she can make; (3) team sizes stay within one of each other; (4) A/C balance. Linked players are always placed together; because they share availability, this never conflicts with (1)–(3). Only A/C balance ever gives way, and the screen says so when it does.

## 12. Draft

**Order.** The facilitator enters the head coaches' last names, comma-separated, and the tool draws a random order. Duplicate last names need a first initial.

**Rounds, one continuous snake:**

- A rounds (one per A per team), then C rounds, then B rounds until every player is placed. Any A or C still unplaced after the A and C rounds can be picked in the B rounds.
- Round 1 runs 1→T, round 2 runs T→1, and so on across tiers.
- Example with 2 A's and 1 C per team: R1 A's 1–6, R2 A's 6–1, R3 C's 1–6, R4 B's 6–1, and so on.

**Who picks:**

- A team picks in a round only while it still needs that tier. Teams whose quota is filled by preloads are skipped automatically.
- A team with a preloaded A still picks in round 1 if it needs a second A. That's the luck of the draw.

**Linked players.** Drafting a girl automatically places her linked player on the same team. The linked player counts as that team's **next pick in her own tier**. The engine treats a linked pair as one unit needing two spots on one team, and a pick is allowed only if the team's night works for both players and the team has room for both.

**Availability engine.** It runs silently on every pick in every round. Before each pick, the tool tests every remaining player and keeps only picks that still leave a valid home for every girl on the board, given team nights, tier quotas and team sizes.

| Result | What the screen shows |
|---|---|
| Only one valid pick | **Must pick** that player |
| Valid picks restricted to a small group | **Must pick one of** them; the coach chooses which |
| Passing on a player now likely makes her a must-pick at this team's next turn | **Suggested pick** |
| No valid pick | Team is **skipped**; the order continues unchanged |
| Otherwise | **Open pick**, no message |

This works from the player's side too: if a girl's only possible home is the team on the clock, she becomes its must-pick.

**The engine never switches off.** If A/C balance can no longer be kept for every team, the screen says so, and the engine still blocks any pick that would leave a girl without a team on a night she can make or break team sizes.

**After a pick is entered:**

- A **direct conflict** (she can't make that team's night) or an **indirect conflict** (the pick strands another player) shows a warning.
- **Overrides happen only in the moment.** For example, a coach texts the parent and the family confirms the night. The facilitator records the added night (it applies to her linked player too) and the tool re-solves.
- **No override can leave a girl without a team.** A pick that would strand another player is refused, even with a confirmed night. A pick that only breaks A/C balance can be kept after a confirmation, and the log records it.
- If the answer doesn't come back in time, the pick stands as the tool recommends and the draft moves on.

**Uneven team sizes.** Which teams carry the extra player isn't set in advance. It falls out of availability in the final rounds; otherwise the snake decides.

**The tool:** the Draft Night page, hosted free on GitHub Pages under the league's GitHub account (board email). The repository is public, so the player data inside the page is encrypted; the page shows nothing until the facilitator enters the season's passphrase. Anyone with the link and the passphrase can use it in any browser, with no Claude account. It needs no AI at draft time.

**Facilitator steps:** Unlock → choose the division from the dropdown → confirm it's the division in the gym → Check-in (no-shows, availability changes, player links, jersey sizes; the schedule check reruns on every change) → Draft order (one click; coaches, nights and daughters are preloaded and read-only) → Eval grades (any single list, such as one coach's C's, can be re-entered from the grade table) → A & C lists (including missed evals and starting position) → Draft (with undo) → Rosters → **Send results (required):** copy the results. With internet, paste them into an email and send it to recleague@cggbl.com. Without internet, paste them into Word, save, and send it to recleague@cggbl.com once you have internet. Keep the page open until the commissioner confirms receipt.

- Progress saves per division in that browser. One device runs each division's draft.
- Check-in changes lock once the first pick is entered. A night confirmed mid-draft goes through the override when that pick is entered.
- Each build carries a version stamp. If a device holds a draft started on older data, the page warns and offers a fresh start.

**Building the page.** At registration close Claude builds index.html from the template in this project (Draft_Night_template.html):

- bundle {"season", "built", "divisions": [the four division files in eval order]};
- encrypt the bundle's JSON with AES-GCM (256-bit key from PBKDF2-SHA256, 600,000 iterations, 16-byte random salt, 12-byte random IV);
- replace `__ENC__` in the template with {"salt", "iv", "iter", "ct"}, each byte value base64-encoded;
- confirm no player name appears in plain text, then test it before handing it over;
- **stress gate:** run at least 500 random drafts per division through the built page, with the data as loaded and with random check-in changes (no-shows, availability changes, player links, confirmed-night and A/C-balance overrides). The build passes only with zero unplaced girls, zero practice-night conflicts, zero team-size violations, linked players together and every daughter on her parent's team. No build goes to the commissioner without passing.

The commissioner uploads it to the repository as index.html. Change the passphrase each season. Keep current copies of this runbook, the project instructions and the template in the same repository (outside the published page) so a future board member can rebuild the Claude project.

**Division file.** Claude produces one per division at registration close; they go inside the page:

```json
{
  "division": "2nd Grade",
  "players": [
    {"bib": 44, "first": "Jane", "last": "Example", "school": "Example Elementary",
     "rec": 0, "trav": 0, "nights": ["M","T","W","Th","F"], "confirmed": true, "raw": "Open"}
  ],
  "coaches": [
    {"name": "Coachname", "night": "W", "daughters": [66], "assistant": null}
  ],
  "links": [[89, 90]],
  "absent": []
}
```

Night codes: M, T, W, Th, F. Players defaulted after unreadable availability have `"confirmed": false`. A judgment call can carry an optional `"note"`.

**Post-draft audit.** Paste the Share results text into Claude. It includes the night's check-in changes and the data version. Check:

- every player is placed exactly once;
- no practice-night conflicts;
- every daughter is on her parent's team and linked players are together;
- A and C quotas and team sizes are correct;
- relative team strength, scored from the coaches' own grades (A = +2, A/B = +1, C = −1), noting whether gaps came from draft position, availability must-picks, or pick choices.

## 13. Post-draft (placeholder)

To be defined:

- **Final rosters and coach welcome communications.**
- **Jersey numbers.** Assigned per team after the draft, unique within the team, using only one-hand referee numbers: 1–5, 10–15, 20–25, 30–35, 40–45, 50–55. Whether 0 and 00 are allowed is unconfirmed. Players don't choose.
- **One consolidated uniform order** for the vendor: size and number per jersey, in the vendor's format (to be provided). Plus a **sorting sheet** (team → player → size → number) for splitting the box by team.
- **Practice logistics and communications** before the first practice.

## 14. Open items and placeholders

- League GitHub account under a board email address (pending); repository setup and Pages.
- Passphrase handling: commissioner gives it to Claude at build time, or a local encrypt step keeps it out of the chat.
- Parent email addresses in the export; email system (assumed Gmail).
- Coach identification at registration (head, assistant, daughters, pairings).
- Registration form improvements (checkbox nights, same-team request field, coach fields).
- Prior years' exports to calibrate the late-surge projection.
- Kindergarten team formation.
- Post-draft workflow and the vendor order format.
- Whether jersey numbers 0 and 00 are allowed.
