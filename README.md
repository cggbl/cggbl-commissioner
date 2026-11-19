# CGGBL Commissioner Toolkit

Everything a CGGBL rec league director needs to run registration through draft night, and to hand it to the next director.

| What | Where |
|---|---|
| Draft Night page (live, passphrase-locked) | `index.html`, published by GitHub Pages |
| Rules for every phase | `claude-project/CGGBL_Commissioner_Runbook.md` |
| Claude project setup | `claude-project/SETUP.md` |
| Draft Night page source | `claude-project/Draft_Night_template.html` |
| Season history (counts, decisions, next bib) | `seasons/` |
| New or outgoing director | `HANDOFF.md` |

## How a season runs

1. Registration exports go into the Claude project each week. Claude returns the weekly report.
2. At close, Claude produces the registration-close package: team plans, bibs, eval sheets, and a new `index.html`.
3. The commissioner replaces `index.html` here. The page updates within a minute or two.
4. Draft facilitators open the page link, enter the season passphrase, and run the draft. Results go to recleague@cggbl.com.

## This repository is public

GitHub Pages is free only for public repositories. That's fine because:

- `index.html` holds player data only in encrypted form. Nothing shows without the passphrase.
- Nothing else here contains player or parent information, and `.gitignore` blocks spreadsheets, PDFs and data files.

Never commit a registration list, jersey order, eval sheet, division file or draft results. Never write the passphrase anywhere in this repository.
