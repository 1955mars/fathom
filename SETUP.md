# Fathom Setup

One-time setup for working on Fathom locally.

## Prerequisites

- `git` and `gh` (GitHub CLI) installed and authenticated as `1955mars`
- [Obsidian](https://obsidian.md) — free personal use
- Any text editor, terminal

## First-time Obsidian setup

1. Install Obsidian.
2. Open Obsidian → "Open folder as vault" → select the `fathom` repo root.
3. Enable community plugins when prompted. Obsidian reads `.obsidian/community-plugins.json` and will prompt to install the whitelist:
   - **Dataview**
   - **Excalidraw**
   - **Templater**
4. Install only these three. Adding anything else requires amending `CONSTITUTION.md` §2.6.

## Templates

Templater templates live in `notes/templates/` (to be created as we start capturing concepts). Point Templater at that folder in its settings.

## macOS Time Machine

Ensure Time Machine is configured and running on this machine. GitHub is primary backup; Time Machine is the belt-and-suspenders local safety net. See `CONSTITUTION.md` §2.11.

## What not to do

- Do not put this folder inside iCloud Drive, Dropbox, or OneDrive. Real-time-sync services conflict with git internals and Obsidian's workspace files.
- Do not commit anything under `content/videos/private/`. Those are gate-test recordings per §1.4, and are gitignored.
- Do not add Obsidian plugins outside the whitelist without amending the constitution.

## Reference clones

External projects we study for inspiration live at the sibling path `/Users/mansoor/references/`, not inside Fathom. Currently: `references/FPGC` (MIT). Internal rule: read to understand, write from scratch.
