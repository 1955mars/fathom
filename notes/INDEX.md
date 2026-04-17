# Index

*Hand-curated map of the Fathom knowledge graph. Updated at natural milestones (end of chapter, end of module, end of phase).*

## By phase

- **Phase 0 — Foundations** — pending (starts after CONSTITUTION is complete)
- Phase 1 — First CPU on real FPGA — pending
- Phase 2 — Toolchain and bare-metal C — pending
- Phase 3 — Filesystem, OS, user programs — pending
- Phase 4 — GPU, HDMI, framebuffer — pending
- Phase 5 — Networking — pending
- Phase 6 — Custom PCB, case, standalone machine — pending

## Concept catalog

*Concepts graduate here as they pass the [[CONSTITUTION|§1.5 success criterion]]. See [[CONSTITUTION]] §2.3.*

(none yet — project not in Phase 0 until CONSTITUTION is complete)

## Dataview auto-indexes

*These tables auto-populate as concept docs are tagged. They require the Dataview plugin to render.*

### Passed concepts, grouped by phase

```dataview
TABLE WITHOUT ID file.link AS Concept, phase, source
FROM "notes/concepts"
WHERE contains(file.tags, "#status/passed")
SORT phase ASC, file.name ASC
```

### Concepts in progress

```dataview
TABLE WITHOUT ID file.link AS Concept, file.tags AS Tags, file.mtime AS "Last edit"
FROM "notes/concepts"
WHERE contains(file.tags, "#status/draft") OR contains(file.tags, "#status/cold-write") OR contains(file.tags, "#status/fluid-speak")
SORT file.mtime DESC
```

### Hollow concepts (rewrite pending)

```dataview
LIST
FROM "notes/concepts"
WHERE contains(file.tags, "#status/hollow")
```
