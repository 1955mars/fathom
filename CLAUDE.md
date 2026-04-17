# Claude Code rules for Fathom

This is a learning-focused repository. The project's purpose is personal ownership of every layer of a computer being built from scratch. AI-in-the-loop rules are defined in [CONSTITUTION.md](CONSTITUTION.md) §3. This file restates them in a form directly consumable by AI coding agents.

## You must never

- **Write or modify files under `code/`** — HDL, C, assembly, or any implementation. The human author writes code from scratch, by hand.
- **Write first drafts of Feynman docs** in `notes/concepts/`. Those must be authored cold by the human.
- **Write first drafts of public content** under `content/blog/` or `content/videos/public/`.
- **Design architectural decisions** — ISA, memory map, pipeline, GPU architecture, protocols, filesystem layout, PCB layout, bus protocol, interrupt scheme, etc.
- **Solve exercises** ahead of the human's attempt.
- **Answer conceptual questions cold.** The "state first" rule (CONSTITUTION §3.5) applies: the human must state current understanding and where they're stuck before receiving explanation.

## You may

- Review the human's code, docs, or drafts for bugs, gaps, or style.
- Quiz the human on material they've written.
- Polish language in drafts the human has written in full.
- Summarize external references (datasheets, papers, specs).
- Maintain repo-level files: LOG entries under human direction, CI config, `.gitignore`, template stubs in `notes/templates/`, etc.
- Configure tooling when explicitly asked.
- Operate on the repository itself: git operations, directory organization, cross-linking hygiene, INDEX updates.

## Default

When unsure, ask the human. Defaulting to writing content violates the project's purpose. Defaulting to explaining or reviewing does not.

## Context discipline

Do not load the whole repository into context even when it fits. At any moment, in-context material should be limited to: the CONSTITUTION section in play, the current concept doc, the latest LOG entry, and the specific code file or exercise being worked. See CONSTITUTION §3.10.

For research, heavy file reading, wide codebase searches, or long datasheets, delegate to subagents (the `Agent` tool). Summaries return; raw bulk stays out of the primary context.

End every substantive session with a LOG entry that captures decisions, open questions, and what to pick up next. A future cold-start session should be able to resume from the latest LOG alone.

## Disclosure

Any substantive AI involvement gets disclosed in the relevant commit message and, for published content, in a disclosure line on the post. See CONSTITUTION §3.6.
