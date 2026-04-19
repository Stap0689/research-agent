# OPEN-SOURCE-RESEARCH-AGENT-REFERENCE

**Status:** Active (public distribution)
**Last Major Update:** 2026-04-19
**Harness Version:** n/a — this is a public skills repo; harness conventions apply on the private development side only

---

## 1. Purpose & Scope

Public GitHub distribution of two Claude Code skills — `research-agent` and `notebooklm` — that enable structured, evidence-based research using Google NotebookLM as the corpus engine. The `research-agent` skill enforces a 7-phase methodology derived from intelligence community analytic standards (ICD 203, Richards Heuer SATs), PRISMA, Popper falsifiability, Tetlock superforecasting, and ACRL/SIFT. The `notebooklm` skill provides programmatic access to Google NotebookLM via notebooklm-py.

The repository is the sanitized export of the private development work. No private-skill internals, no enterprise identifiers, no personal references.

---

## 2. Zone Mapping

This repository is a skills distribution — markdown + assets only, no runtime code or pipeline. The canonical four-zone model (control-plane / pipeline / observability / _design) does not apply directly.

| Zone | Realization | Notes |
|------|-------------|-------|
| control-plane | n/a | No runtime configuration or orchestration in this repo |
| pipeline | `research-agent/`, `notebooklm/` | Skill directories — each carries a `SKILL.md` plus supporting markdown |
| observability | n/a | No runtime — observability applies to consumers of the skills |
| _design | `_design/` | Project knowledge (canonical harness path) |

---

## 3. Layer / Module Table

| Path | Role |
|------|------|
| `research-agent/SKILL.md` | Methodology enforcement (7-phase workflow, source audit, bias countermeasures) |
| `research-agent/BIAS-PREVENTION.md` | Bias countermeasure reference |
| `research-agent/COMPLETION-AND-DELIVERABLES.md` | Phase-close deliverables + 10-section Analytic Pyramid |
| `research-agent/NOTEBOOKLM-INTEGRATION.md` | Integration patterns with the notebooklm skill |
| `research-agent/QUESTION-FRAMEWORKS.md` | Question escalation ladder + framework patterns |
| `research-agent/SOURCE-QUALITY.md` | Source quality gates + tier definitions |
| `notebooklm/SKILL.md` | Full NotebookLM API wrapper + CLI reference |
| `assets/` | README hero image + supporting media |

---

## 4. Dependencies & Constraints

**External:**
- Google NotebookLM (account required; OAuth handled by notebooklm-py)
- `notebooklm-py` CLI — https://github.com/teng-lin/notebooklm-py

**Hard constraints:**
- No private references (AIMIS, enterprise identifiers, internal tooling paths)
- No dependence on private host-local paths in skill content

---

## 5. Canonical Conventions (Deviations)

| Convention | Deviation | Why |
|------------|-----------|-----|
| Top-level control-plane/, pipeline/, observability/ directories | Not created | No runtime code to organize — this is a skills-only repo |
| .claude/settings.json with local harness hook | Not created | `~/projects/.harness/` is private; public repo must not depend on it |
| CLAUDE.md | Not created | Repo is consumed as skills by end users, not developed as a code project |
| Plan folders + handoffs under _design/project/ | Seeded empty | Reserved for future contribution process; not yet in use |

---

## 6. Plan History (Closed Plans, Chronological)

None — this distribution tracks upstream skill revisions via git history, not phased plans.

---

## 7. Open Plans

None — contribution workflow TBD.

---

## 8. ADR Index

None yet. `_design/adrs/` reserved for architectural decisions about the public distribution (e.g., naming scheme for upstream sync).

---

## 9. Migration Notes

### 2026-04-19 — Harness Phase B retrofit

Created `_design/` directory with the canonical subtree (adrs/, specs/, concept/, project/{plans, findings, trackers}/) plus this master reference. No source files moved. No CLAUDE.md or .claude/settings.json added — the repo is a skills distribution, not a developed-against codebase, and must not depend on private harness paths.

---

*Master reference is the semantic single source of truth for this public distribution. Private development state lives off-repo.*
