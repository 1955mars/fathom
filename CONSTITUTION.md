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

*pending*

## 3. AI-in-the-loop rules

*pending*

## 4. Content system

*pending*
