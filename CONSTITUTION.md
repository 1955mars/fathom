# Fathom Constitution

*The rules I set for myself at the start of this project, so future-me doesn't quietly drift from past-me's intentions.*

This document defines four interlocking systems: **learning**, **organization**, **AI-in-the-loop**, and **content**. Only §1 is drafted. The project does not begin Phase 0 until all four are complete.

---

## 1. Learning system

### 1.1 Principle

The Feynman technique is the central learning mechanism. Every concept is considered owned only when I can explain it — from scratch, without reference material — in a way a less-informed version of myself would fully understand. The explanation *is* the artifact; the ability to produce the explanation is the test.

This single choice cascades: notes, ownership test, gap detection, and content seeds all flow from the same mechanism.

### 1.2 Audience

The audience for every Feynman explanation is **my past self** — a version of me with solid EE/CS fundamentals but no knowledge of the specific topic being explained. This audience:

- Expects rigor, not hand-waving
- Understands math, circuits, and computation basics
- Expects motivation before mechanism ("why" before "how")
- Does not tolerate jargon used without definition

Writing for someone too expert shrinks explanations into terse shorthand; writing for someone too naive inflates them into filler. Past-self is the anchor.

### 1.3 What counts as a concept

A concept is any idea I could reasonably be asked to whiteboard-explain in 2–10 minutes.

- **Too granular** (30 seconds or less) — fold into the parent concept's explanation. A NAND truth table belongs inside the NAND gate concept, not as its own doc.
- **Too coarse** (30+ minutes) — break into sub-concepts first. "The CPU" is not a concept; its decoder, ALU, register file, control path, and pipelining each are.

If uncertain: if the natural written form is a few paragraphs with one headline idea, the size is right.

### 1.4 The artifact

Every concept produces **two artifacts**, in this order:

1. **Written Feynman doc** — markdown in `notes/<source>/<concept>.md`. The durable, indexable, searchable form. This is the source of truth.
2. **Spoken private recording** — an unedited audio or video take of me explaining the concept out loud. Lives in `content/videos/private/` (gitignored, not distributed). This is the fluency test, not public content.

**Public content** (polished blog post, edited video) is a separate, selective layer. It is *not* required for every concept. The public artifact is built later, on top of the Feynman doc, for concepts judged worth publishing.

### 1.5 Success criterion — the "done" test

A concept is owned only when **all three** pass, in sequence:

1. **Cold write** — sit down with no reference material and write the explanation in one sitting.
2. **Fluid speak** — record a single take explaining the concept without a script and without stalling on what to say next. Retakes allowed only for mic or environment issues, not for forgetting content.
3. **Next-day re-read** — re-read the written doc 24+ hours later; it still reads clear. If the next-day me trips on any sentence, the concept isn't owned. Revise and re-test from step 1.

### 1.6 Scope — every concept

Every concept encountered gets the full Feynman treatment, not just the ones that feel important at the time. The concepts skipped because they "feel simple" are the ones that quietly hollow out the foundation.

The only exception is granularity (§1.3): sub-concepts fully contained in a parent's explanation don't need their own doc. They must appear explicitly in the parent's explanation — no jargon pass-throughs.

### 1.7 Gate — hard

No progress to the next chapter, lab, or module until every concept in the current one has passed the success criterion (§1.5).

"Progress" means *starting new material*. It does not include:

- Writing other concepts' Feynman docs from the current batch (parallel work within the batch)
- Reading reference material that supports an in-progress concept
- Administrative work (repo, LOG, tooling)

Deferred debt compounds catastrophically in a multi-year project. The gate is the brake that keeps the foundation solid.

### 1.8 Gap handling

Two kinds of gap will appear.

- **Present gap** — I try the cold write and can't. Expected, good; the mechanism is working. Return to source material, re-learn, retry.
- **Past gap** — weeks or months later, in the middle of later work, I discover a concept I thought I owned is hollow. Protocol: stop the current work, open the stale doc, re-run the full success criterion. Log the discovery in `LOG/` so the hollow-rate is visible over time.

If the same concept goes hollow twice, the second rewrite is canonical, and the failure mode (what I missed the first time) is appended to the doc.

### 1.9 Concepts that resist Feynman

Some things genuinely require formal tools — timing diagrams, waveforms, HDL code, math derivations — to explain. "Feynman" in Fathom means *plain-language explanation plus whatever formal artifact is genuinely necessary.*

The sin is padding with formalism to hide not understanding, not using formalism where it belongs. The test: can I explain the *intuition* before pulling out the formalism? If yes, include both. If the intuition isn't there, I don't understand the thing yet.

### 1.10 Spaced repetition (stub — to expand later)

Because the artifact is an explanation, retention testing means rehearsing the explanation. Anki-style cards get a concept name on the front and the prompt "explain X" on the back; answering means delivering the Feynman explanation from memory, cold. Review cadence and tooling to be decided in a later revision.

---

## 2. Organization system

### 2.1 Tool

**Obsidian** is the primary interface over the repository's markdown. Markdown files remain the source of truth; Obsidian is a lens, not a dependency. If Obsidian disappears tomorrow, every file stays readable and editable in any text editor. This constraint is enforced by keeping vault contents as plain markdown and `.obsidian/` config minimal.

### 2.2 Vault scope

The entire Fathom repository is a single Obsidian vault. One `.obsidian/` folder lives at the repo root. This is deliberate: notes, code files, LOG entries, and blog drafts are all linkable by the same syntax, and the graph view spans the whole project.

### 2.3 Folder roles for knowledge

- **`notes/<source>/`** — source-bound notes: chapter summaries, exercise solutions, running questions, margin notes. One folder per source material (e.g., `notes/nand2tetris/`, `notes/harris-harris/`).
- **`notes/concepts/`** — the canonical home for Feynman docs. One file per concept, source-agnostic.
- A concept is *born* in a source folder (as rough running notes) and *graduates* to `notes/concepts/` once it passes the §1.5 success criterion. Use `git mv` when graduating so history is preserved.

Rationale: concepts like "two's complement" appear in multiple books and labs. A single canonical file, backlinked from each source, prevents drift and duplication.

### 2.4 Filenames

- Kebab-case slug filenames: `nand-gate.md`, `twos-complement.md`, `single-cycle-datapath.md`.
- First line inside each file is the pretty title as a top-level heading: `# Two's Complement`.
- Wikilinks reference by slug: `[[nand-gate]]`. Obsidian displays the heading if present.
- LOG entries use ISO-8601 filenames: `LOG/2026-04-17.md`.

### 2.5 Required cross-links

Non-negotiable. The knowledge graph is only useful if the edges are there.

1. **Every concept doc** has, near its end, sections linking to:
   - **Sources** — where this was learned (book + chapter, lab, paper)
   - **Prerequisites** — concepts that must be owned before this one is readable
   - **Enables** — concepts that become readable once this one is owned
2. **Every LOG entry** links to the concepts worked on, commits made, and blockers encountered that day.
3. **Every blog post draft** links to the concept docs it builds on.

### 2.6 Plugin whitelist

Only three plugins are permitted at project start:

- **Excalidraw** — hand-drawn diagrams (timing, waveforms, sketches)
- **Dataview** — auto-generated indexes and status tables
- **Templater** — templates for Feynman docs, LOG entries, blog posts

No theme plugins, no dashboard kits, no "second brain starter" packs. Adding a plugin requires a §2 amendment (commit message must reference it). The whitelist lives in `.obsidian/community-plugins.json` and is committed.

### 2.7 `.obsidian/` git policy

Vault configuration is mostly ignored; only the plugin whitelist is tracked, so the vault is reproducible on a fresh clone.

- **Committed:** `.obsidian/community-plugins.json`
- **Ignored:** everything else in `.obsidian/` (workspace state, caches, graph view, plugin binaries, themes, app settings)

### 2.8 Tags

Tags are deliberate and limited. The taxonomy at project start:

- **Phase:** `#phase-0`, `#phase-1`, `#phase-2`, `#phase-3`, `#phase-4`, `#phase-5`, `#phase-6`
- **Domain:** `#hardware`, `#software`, `#toolchain`, `#os`, `#networking`, `#gpu`, `#pcb`
- **Tool:** `#tool/verilog`, `#tool/c`, `#tool/kicad`, `#tool/yosys`, `#tool/icarus`, etc.
- **Status (concept lifecycle):** `#status/draft`, `#status/cold-write`, `#status/fluid-speak`, `#status/passed`, `#status/hollow`

Adding a new tag *category* requires a §2 amendment. Individual tags within existing categories can be added freely.

### 2.9 Indexes

- **`notes/INDEX.md`** — hand-curated top-level map. The "table of contents" for the brain. Updated at natural milestones.
- **Dataview tables** — auto-generated per-phase, per-source, per-status indexes, defined as Dataview queries embedded in the relevant markdown files.

Findability at year-four scale depends on both: hand-curated for narrative navigation, auto-generated for exhaustive listing.

### 2.10 Concept ↔ code link

When a concept is implemented in code (e.g., the ALU concept in `code/phase-1-cpu/alu.v`):

- The concept doc has an **Implementation** section linking to the code file(s).
- The code file's top comment links back to the concept doc.

Closes the loop between theory (the Feynman doc) and implementation. Enforced by convention.

### 2.11 Backup

- **Primary:** GitHub remote. Push at the end of every working session, minimum daily.
- **Secondary:** macOS Time Machine. Must be configured before Phase 0 begins.
- **Forbidden:** iCloud Drive, Dropbox, OneDrive, or any real-time-sync service on the `fathom/` folder. These conflict with git internals and Obsidian's workspace state and cause real data loss, not theoretical.

### 2.12 Forbidden patterns

- Silently renaming concept files (breaks wikilinks). Always `git mv` and fix inbound links in the same commit.
- Orphan concept docs (no inbound links). Every concept must be reachable from at least one source doc or another concept.
- Committing private recordings (§1.4). `content/videos/private/` is gitignored; verify before push.
- Putting anything else in `.obsidian/` under version control without a §2 amendment.

## 3. AI-in-the-loop rules

*pending*

## 4. Content system

*pending*
