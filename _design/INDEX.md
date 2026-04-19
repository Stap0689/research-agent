# Project Index: open-source-research-agent

**Last Updated:** 2026-04-19
**Harness Version:** n/a (public distribution — harness conventions apply on the private development side)
**Active Plan:** None (contribution workflow TBD)
**Current Phase:** N/A

---

## Active Work

| Plan Folder | Phase | Status | Latest Handoff |
|-------------|-------|--------|----------------|
| — | — | — | — |

---

## Open Handoffs (awaiting next session)

- None.

---

## Recent ADRs (last 5)

- None yet. `_design/adrs/` seeded by harness Phase B retrofit 2026-04-19. Reserved for public-distribution decisions (e.g., upstream sync naming).

---

## Key Files & Purposes (manually maintained)

| File | Purpose |
|------|---------|
| `research-agent/SKILL.md` | 7-phase research methodology enforcement |
| `research-agent/BIAS-PREVENTION.md` | Bias countermeasure reference |
| `research-agent/COMPLETION-AND-DELIVERABLES.md` | Phase-close deliverables + Analytic Pyramid |
| `research-agent/NOTEBOOKLM-INTEGRATION.md` | Integration patterns with the notebooklm skill |
| `research-agent/QUESTION-FRAMEWORKS.md` | Question escalation ladder + frameworks |
| `research-agent/SOURCE-QUALITY.md` | Source quality gates + tier definitions |
| `notebooklm/SKILL.md` | Full NotebookLM API wrapper + CLI reference |
| `assets/` | README hero image + supporting media |

---

## Code Index Artifacts (not auto-regenerated)

- `_design/code-index.json` — absent; repo ships markdown + assets only (no `.py` files)
- `_design/code-index-compact.md` — absent
- `_design/OPEN-SOURCE-RESEARCH-AGENT-REFERENCE.md` — master reference (public-distribution)

---

## Distribution Notes

This repo is a public skills distribution. It deliberately has **no `CLAUDE.md`** and **no `.claude/settings.json`** — the repository is consumed as skills by end users, not developed against by Claude Code, and it must not depend on private harness paths under `~/projects/.harness/`. Private development state lives off-repo.

This `INDEX.md` exists for structural parity with other harness-retrofit projects; it is **not** `@import`ed from any CLAUDE.md (since there is none).

---

*This file is part of the canonical `_design/` tree documented in `~/projects/.harness/HARNESS.md`.*
