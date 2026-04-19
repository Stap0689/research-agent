# Research Agent

![Research Agent](assets/hero.png)

Claude Code skills for structured, evidence-based research using Google NotebookLM as the corpus engine.

## The Problem

LLMs generate plausible-sounding research that cites nothing, skips disconfirmation, and collapses nuance into confident summaries. The output reads well. The methodology behind it is absent.

## How This Works

Two skills. **research-agent** controls the methodology: source quality gates, question escalation, bias countermeasures, completion criteria. **notebooklm** provides the corpus: programmatic access to Google NotebookLM via [notebooklm-py](https://github.com/teng-lin/notebooklm-py), including features not in the web UI.

The research-agent enforces a 7-phase workflow derived from intelligence community analytic standards (ICD 203, Richards Heuer SATs), PRISMA systematic review methodology, Popper falsifiability, Tetlock superforecasting, and ACRL/SIFT information literacy.

### Phases

| Phase | What Happens |
|-------|-------------|
| 0. Scope | Define the research question, select output mode, declare application context (optional) |
| 1. Collection | Create notebook, run deep research, validate imports, audit source quality |
| 2. Expansion | Targeted queries to fill gaps. Each import triggers dedup guard and source audit |
| 3. Research Journey | Three sub-phases: Exploratory (map the territory), Crystallization (test with falsification), Application (apply to target context) |
| 4. Synthesis | NotebookLM produces a structured summary shaped by the output mode |
| 5. Findings Document | 10-section Analytic Pyramid with calibrated confidence, intelligence gaps, falsification record |
| 6. Completion Gates | Six gates. Methodological veracity, survival of disconfirmation, linchpin stability, consensus through dissent, calibrated confidence, falsifiability commitment |
| 7. Delivery | Findings document written to disk, notebook index updated for cross-topic tracking |

### Output Modes

| Mode | When to Use |
|------|------------|
| Synthesis | You need to understand a topic |
| Implementation Spec | You need to build something from research findings |
| Decision Brief | You need a yes/no/conditional recommendation |
| Technical Reference | You need an exhaustive catalog of mechanisms and parameters |
| Evaluation Report | You need to stress-test a design document against external evidence |

## Notebook Persona

NotebookLM is not queried cold. In Phase 1, the skill configures a research persona that governs how NotebookLM responds for the entire session:

```
You are a research corpus analyst supporting a multi-phase research investigation.
Your role is to extract, synthesize, and present evidence from the loaded sources
with maximum rigor.

RULES — apply to EVERY response:
1. ALWAYS cite specific sources by name for every factual claim. Never assert
   without citation.
2. Distinguish what sources explicitly state (findings) from what you infer
   (interpretation). Label each clearly.
3. When sources disagree, present BOTH positions with the evidence basis for each.
   Do not silently pick a side.
4. Identify what the sources do NOT cover that is relevant to the question.
   Gaps are as important as findings.
5. Flag single-source claims — note when a finding rests on only one source vs.
   multiple independent sources.
6. Never fabricate, extrapolate beyond what sources support, or fill gaps with
   general knowledge. If the corpus does not cover it, say so.
```

The persona also adapts response style to question type. Broad exploratory questions get landscape mapping with coverage assessments. Targeted questions get precise answers with full citation chains. Evaluation questions get claim-by-claim cross-referencing against evidence.

Response length is set to `longer`. The research workflow needs depth, not brevity.

## What Gets Enforced

**Source quality.** A 5-tier credibility hierarchy gates every source. Social media, YouTube, Reddit, vendor marketing, and unattributed content are rejected on sight. Q&A cannot begin until 15 Tier 1-3 sources are loaded. Fast research imports trigger stricter filtering (Tier 1-2 only for primary evidence).

**Bias countermeasures.** Five named biases (confirmation, satisficing, anchoring, availability heuristic, mirror imaging) each have a structural intervention. Analysis of Competing Hypotheses, devil's advocate protocol, premortem analysis, and red hat analysis run during synthesis. These are not optional checks.

**Question rigor.** A 5-round depth escalation ladder moves from parameter definition (starbursting) through structural decomposition, falsification probing, cognitive reframing, and metacognitive critique. Phase 3A discovers. Phase 3B tests. Phase 3C applies.

**Completion standards.** Six gates must pass before research is declared complete. Gate 2 (survival of disconfirmation) cannot be skipped. Findings, insights, and recommendations are three distinct levels that are never collapsed into a single list.

## Application Context

You can seed the notebook with a context document (a design spec, architecture doc, or any reference material). Phase 3C then applies the research findings against that context. If no context is provided, Phase 3C is skipped and the output is general-purpose research.

This is declared in Phase 0 and propagates through the entire workflow.

## Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- [notebooklm-py](https://github.com/teng-lin/notebooklm-py): `pip install notebooklm-py`
- NotebookLM authenticated: `notebooklm login`

## Install

```bash
cp -r research-agent/ ~/.claude/skills/research-agent/
cp -r notebooklm/ ~/.claude/skills/notebooklm/
```

## Usage

The skill activates on research-intent prompts:

```
Research the current state of retrieval-augmented generation architectures
Evaluate this design document against current best practices
Give me an implementation spec for vector similarity search with HNSW
```

Claude creates the notebook, collects and audits sources, runs the structured Q&A journey, applies completion gates, and writes the Research Findings Document to `./research-findings/`.

A `notebook-index.json` file tracks all research notebooks, their output modes, confidence levels, and findings document paths. Use it to run cross-topic synthesis in a follow-up session.

## File Structure

```
research-agent/
  SKILL.md                        Main skill: phase orchestration, autonomy rules, data handling
  BIAS-PREVENTION.md              5 cognitive biases, devil's advocate, premortem
  COMPLETION-AND-DELIVERABLES.md  6 completion gates, Analytic Pyramid, confidence language
  NOTEBOOKLM-INTEGRATION.md      CLI reference, rate limits, timeout recovery, note conventions
  QUESTION-FRAMEWORKS.md          5-round depth ladder, AIMS scoping, phase-question mapping
  SOURCE-QUALITY.md               5-tier hierarchy, SIFT method, triangulation, acceptance criteria

notebooklm/
  SKILL.md                        NotebookLM CLI: full command reference, workflows, error handling
```

## License

MIT
