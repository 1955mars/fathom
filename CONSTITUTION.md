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
- **Secondary:** macOS Time Machine configured on an external USB-C SSD (or equivalent). **Required within 30 days of Phase 0 start**, not before.
- **Forbidden:** iCloud Drive, Dropbox, OneDrive, or any real-time-sync service on the `fathom/` folder. These conflict with git internals and Obsidian's workspace state and cause real data loss, not theoretical.

**Rationale for the 30-day delay.** During the first 30 days of Phase 0, GitHub is sole backup. This is acceptable because (a) early Phase 0 work is entirely git-backed — no meaningful local-only state exists yet; and (b) buying an external SSD before the project has proven consistency is premature hardware investment. If the project is still active at day 30, the hardware commitment is earned and Time Machine is configured then.

**"Day 30" definition.** 30 calendar days measured from the first LOG entry tagged `#phase-0-start`. The pre-Phase-0 setup period does not count toward the 30.

### 2.12 Forbidden patterns

- Silently renaming concept files (breaks wikilinks). Always `git mv` and fix inbound links in the same commit.
- Orphan concept docs (no inbound links). Every concept must be reachable from at least one source doc or another concept.
- Committing private recordings (§1.4). `content/videos/private/` is gitignored; verify before push.
- Putting anything else in `.obsidian/` under version control without a §2 amendment.

## 3. AI-in-the-loop rules

### 3.1 Principle

The purpose of Fathom is personal ownership of every layer of the computer I'm building. AI is a powerful tool that can short-circuit ownership invisibly — often without me noticing until months later, when a topic I thought I knew turns out hollow. This section defines allowed and forbidden uses so convenience does not erode depth.

AI in Fathom is a **tutor, reviewer, and editor** — never an author, designer, or answer-vending machine. Every artifact in this repository is mine first; AI involvement is post-hoc and audit-trailed.

### 3.2 Tool inventory

**Permitted:**
- Conversational AI (Claude, ChatGPT, Gemini, or equivalent) for explanation, critique, quizzing, review.

**Forbidden:**
- Inline code completion (GitHub Copilot, Cursor Tab, Codeium, Supermaven, or equivalent) anywhere in `code/`. The friction of typing code yourself is part of the learning. Not disabled for convenience.

**Currently disallowed, amendment required to adopt:**
- Agentic coding tools (Cursor Composer, Claude Code in write mode, Aider, etc.) operating on `code/`, `hardware/`, or `notes/concepts/`. Permitted for repo-level maintenance only: LOG entries, CI, `.gitignore`, cross-linking hygiene, setup scripts.

### 3.3 Allowed uses

- **Explain concepts** I'm confused about, after I've stated my current understanding and specific confusion (see §3.5).
- **Find gaps** in a Feynman doc I've already drafted cold.
- **Quiz me** on material I've written, using the concept file as reference.
- **Review code** I've already written, for bugs, style, clarity, and alignment with documented intent.
- **Polish language** in blog drafts I've already written in full.
- **Summarize external references** (datasheets, papers, specs) I don't have time to read cover-to-cover.
- **Translate jargon** — look up a term or acronym I don't recognize.
- **Devil's advocate** on design decisions I've made, to stress-test my reasoning.

### 3.4 Forbidden uses

- Writing HDL, C, assembly, or any implementation file in Fathom — at all. Not even as "scaffold I'll rewrite."
- Producing the first draft of a Feynman doc in `notes/concepts/`. First drafts are cold, mine, and without AI assistance.
- Designing any architectural decision: ISA, memory map, pipeline, GPU architecture, protocol, filesystem layout, PCB layout, bus protocol, interrupt scheme, etc.
- Writing the first draft of any blog post or video script intended for publication.
- Solving an exercise before I've attempted it in full.
- Answering a conceptual question cold, before I've stated what I think and where I'm stuck.

### 3.5 The "state first" rule

Before asking AI a question about understanding, I must state:

1. What I currently believe the answer is, or "I don't know — here's my best guess."
2. Where specifically I'm stuck.
3. What reference material I've already consulted.

Non-negotiable. This is what preserves the struggle that creates ownership. Asking "what is X?" cold is forbidden; asking "I think X is Y because Z, but I can't reconcile it with W — where am I wrong?" is the permitted shape.

### 3.6 Disclosure

**Standing AI policy page.** A public-facing summary of §3 is published on the blog (as `ai-policy.md` or equivalent), kept in sync with this section. Audience transparency is part of doing this in public.

**Per-post disclosure.** Every public blog post and video ends with one line describing AI's role in producing it. Examples:

- "AI was not used in producing this post."
- "AI was used to review this post for gaps; no content was AI-generated."
- "AI was used to polish phrasing in the introduction and conclusion."

No puffery, no hedging. A reader should be able to trust the disclosure verbatim.

### 3.7 Archival

- **`ai/prompts/`** — reusable prompt templates (code review, concept quizzing, Feynman-doc gap review, etc.). Committed. Populated as patterns emerge.
- **`ai/transcripts/`** — saved transcripts that shaped a decision or milestone. Filenames: `YYYY-MM-DD-short-slug.md`. Committed.
- **Ephemeral use not archived.** Examples: looking up a term, a quick sanity check, a one-off explanation.

Heuristic: if the conversation changed my mind about something, or if future-me would benefit from seeing what I asked and why, save it.

### 3.8 Amendment (stricter than other sections)

§3 exists specifically to protect the ownership principle. Loosening its restrictions (i.e., permitting something previously forbidden) requires:

1. A written argument in a new LOG entry explaining why the restriction is no longer serving the project's goal.
2. A **7-day cooling-off period** before the amendment can be applied. The period forces the decision out of whatever frustration or shortcut-craving triggered it.
3. The commit applying the amendment must reference the LOG entry.

Tightening restrictions (making §3 stricter) does not require a cooling-off period.

### 3.9 Machine-readable enforcement

`CLAUDE.md` at the repo root restates §3 in a form directly consumable by AI coding agents (Claude Code, Aider, Cursor, others). Any AI agent operating on this repository is expected to read and follow `CLAUDE.md`. It is the human author's responsibility to ensure each tool loads that file.

### 3.10 Session and context hygiene

A large context window does not imply uniform attention. Early content gets under-weighted; middle content gets *poisoned* by later repetition or subtle contradiction; long sessions silently lose quality. Across sessions, the AI has no conversational memory — the project's durable state must live in files. These rules protect quality over a multi-year project.

**Session size.** One session per meaningful unit — per chapter, per concept, per milestone. Not per day, not per phase. Marathons dilute attention; split them. When substantive work has been running 3+ hours, stop, commit, and start fresh.

**LOG as handoff.** Every session ends with a LOG entry capturing what would be lost if the conversation disappeared: decisions, open questions, what to pick up next. A cold-start future session reading the latest LOG entry should be able to resume without reconstructing yesterday.

**Context-load discipline.** Even when the whole repository *fits*, the whole repository should not be loaded into context. At any moment, in-context material is limited to: the CONSTITUTION section in play, the current concept doc, the latest LOG entry, and the specific code file or exercise being worked. Reading "for completeness" hurts attention on the real work.

**Delegate to subagents.** Research, large-file reading, wide codebase searches, long datasheets — delegate to the Agent tool. Subagents run in isolated context; only their summary returns. This preserves the primary session for decisions and synthesis.

**Memory files stay indexical.** The auto-loaded memory files at `~/.claude/projects/-Users-mansoor/memory/` are pointers, not knowledge dumps. Project memory growing past ~100 lines is a warning sign; refactor into smaller focused files.

**Prefer fresh over compacted.** Claude Code's `/compact` is lossy. When a session is heavy, ending and restarting produces cleaner context than compacting. Restart unless there is a specific reason not to.

**Exception.** Multi-topic setup sessions — like the one that produced the original CONSTITUTION — are allowed when topics genuinely interlock and the work isn't substantive learning. Phase work is not such an exception.

## 4. Content system

### 4.1 Principle

Publishing is a first-class output of Fathom, not an afterthought. But publishing overhead can eat a multi-year project if the system is wrong. §4 makes publishing cheap enough to actually happen and strict enough to remain meaningful.

The content system sits *on top of* the learning system. **Every public piece builds on a Feynman doc that already exists.** Content is never the first draft; content is the polished derivative.

### 4.2 Channels

The Fathom content stack, in priority order:

- **GitHub README** (always visible) — phase status, latest milestones, links to posts and videos. The live homepage.
- **Long-form blog** (primary channel) — polished posts built on top of Feynman docs. In-repo markdown, static-site generated, deployed to a custom domain.
- **YouTube** (secondary) — long-form videos of real work: bring-up, debugging, explanations. Added when audio/recording setup is good enough; not before.
- **Short-form** (X/Mastodon/Bluesky) — in-the-moment discoveries, milestone teasers, short threads. Free-form.
- **Aggregators** (Hacker News, relevant subreddits) — used *only* on major milestones (end of phase, significant demo). Not for individual blog posts unless they stand alone.
- **Newsletter** — deferred. May be added later if audience asks. Amendment required.

### 4.3 Cadence

- **Long-form (blog, video):** milestone-driven. A post goes out when a meaningful milestone lands — not on a calendar. Rationale: a fixed schedule forces filler; filler hollows a project's reputation faster than silence does.
- **Short-form:** free-form. On-whim when something genuinely worth sharing happens.
- **README:** updated at every milestone commit.
- **LOG:** daily during active working days (not public-facing content, but visible in the public repo).

A "milestone" is: a batch of concepts passing the §1.5 success criterion; a phase transition; a working demo (blink-an-LED counts); a significant rewrite or correction; a discovered gap worth explaining.

### 4.4 Hosting

- **Source:** in-repo static site. Markdown + frontmatter at `content/blog/`. Built and deployed by CI on push to `main`.
- **Generator:** **Quartz** is the default (Obsidian-native — `[[wikilinks]]` and graph view render on the web). **Astro** is the fallback if Quartz becomes limiting. Final choice made at infrastructure-setup time.
- **Deploy target:** Cloudflare Pages or GitHub Pages. Free tier, custom domain supported.
- **Domain:** registered before the first post goes live. TBD at setup time (candidates: `fathom.dev`, `fathom.build`, a subdomain of a personal domain).

### 4.5 Brand and voice

- **Author attribution:** real name, "Mansoor." No pseudonym.
- **Project attribution:** content is project-branded — posts are "from Fathom," not "Mansoor's blog." The project is the persistent identity.
- **Voice:** technical, personal, precise. First-person. Not tutorial, not clickbait. Model to aim for: *a skilled engineer explaining their own work to a peer who hasn't seen it.*
- **Visual identity:** start with typography only (repo logo, favicon). Evolve after the first ~10 posts, once voice has settled. Do not spend time on branding before writing exists.

### 4.6 Draft pipeline

1. Feynman doc(s) for the relevant concept(s) pass the §1.5 success criterion.
2. Draft file created at `content/blog/drafts/YYYY-MM-DD-slug.md`.
3. Draft written in full by me (§3.4 applies — AI does not produce the first draft).
4. AI review allowed (§3.3): gap-check and language polish on the complete draft.
5. Draft re-read 24+ hours later; revise if unclear (same principle as §1.5).
6. When ready: `git mv content/blog/drafts/… content/blog/published/…`, update frontmatter with publish date and disclosure line, commit, push. CI builds and deploys.
7. If a concept referenced in a published post later goes hollow (§1.8) and the post is affected: publish a revision. Keep the original accessible; add a changelog section.

### 4.7 Disclosure and integrity

Every published post ends with three sections:

- **AI disclosure line** (see §3.6).
- **Primary sources** — links to the concept docs, commits, and code files underlying the post. A reader can dig as deep as they want.
- **Corrections** (if any) — updates made since initial publish.

No affiliate links, no sponsored content, no tracking beyond what the static host needs. Advertising or sponsorship, if ever considered, requires an amendment.

### 4.8 First post

The first post is **"Why Fathom"** — a meta-post explaining the project, the constitution, and the invitation to follow along. It publishes *when I am ready to start sharing*, not before. "Ready" means: comfortable with the Feynman workflow in practice; confident enough in the learning cadence that adding a public audience will not pressure it; enough concept docs and LOG entries in the repo that the post has substance to point at.

Waiting is explicit and deliberate. Publishing too early risks making content cadence compete with learning cadence — exactly what §4.1 was written to prevent. Better to publish real depth later than shallow progress early.

### 4.9 Infrastructure setup timing

Blog infrastructure (static site generator, hosting, domain, CI) is configured *when I decide to start publishing*, not as a gate on Phase 0. Setup is itself a milestone; once it lands, the first post follows on a short cadence.

The LOG is still written from day one (§2.9, §4.3). A public repo with an honest lab notebook communicates progress to anyone who looks, even without a formal blog.

### 4.10 Amendment

§4 can be amended to adjust cadence, add channels, change hosting, or update the brand. No cooling-off period required (unlike §3).

The one rule that cannot be relaxed by amendment: §4.1's principle that content is always derivative of a Feynman doc that already exists.
