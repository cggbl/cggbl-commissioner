# Rebuilding the Claude project

1. In Claude, create a Project named **CGGBL Commissioner's Assistant**.
2. Paste `PROJECT_INSTRUCTIONS.md` into the project's instructions.
3. Add to project files:
   - `CGGBL_Commissioner_Runbook.md`
   - `Draft_Night_template.html`
   - this season's registration export and the vendor's jersey order file (from the league drive, never from this repository)
4. Start a chat: "New season. I'm the new rec director. Read the runbook and tell me what you need from me first."

## Keeping it in sync

- When a rule changes, update the runbook in the project **and** commit it here. Bump the version line at the top.
- When the template changes, commit the new `Draft_Night_template.html` here before draft night.
- Claude's chat memory doesn't transfer. The runbook is the only record that does.
