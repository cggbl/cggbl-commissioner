# Handoff

## What you're inheriting

1. **League email account** (recleague@cggbl.com). Owns everything below. Draft results arrive here.
2. **GitHub organization** owned by the league email account. Holds this repository and publishes the Draft Night page.
3. **Claude project.** Claude projects can't be transferred between accounts. You rebuild it in about 15 minutes from `claude-project/` (see `SETUP.md`). The runbook carries every rule; nothing lives only in the old project.
4. **League drive** (under the league email). Registration exports, jersey orders, eval sheets and draft results by season.

## Credentials (board password manager, not a personal phone)

- League email password and its recovery phone/email
- GitHub login for the league account, its 2FA method, and its **recovery codes**. Losing 2FA without recovery codes locks the account permanently.
- Domain registrar login for cggbl.com, if the email runs on that domain. If the domain lapses, the email and everything tied to it go with it.
- Current season's Draft Night passphrase (changed every season)

## Incoming director: first week

- [ ] Get the league email login and confirm you can receive mail
- [ ] Create your own GitHub account; the outgoing director adds you as an **Owner** of the organization
- [ ] Confirm the Pages link opens and asks for a passphrase
- [ ] Rebuild the Claude project (`claude-project/SETUP.md`)
- [ ] Read the runbook start to finish, then the latest file in `seasons/`
- [ ] Get access to the league drive

## Outgoing director: last week

- [ ] Commit the final runbook, project instructions and template
- [ ] Fill in this season's file in `seasons/` (counts, decisions, next available bib, open items)
- [ ] Move any season files from personal drives to the league drive
- [ ] Add the incoming director as GitHub organization Owner, then remove yourself
- [ ] Rotate the league email password and update recovery info to the board's
- [ ] Hand over credentials through the board password manager

## Rule of thumb

If it was decided in a chat and isn't in the runbook, it doesn't survive the handoff. Write it into the runbook.
