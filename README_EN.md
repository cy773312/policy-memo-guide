<div align="right">

**[中文](README.md)** | English

</div>

<div align="center">

# policy-memo-guide

**A focused skill for turning analysis, notes, and research into real policy memos.**

[![Skill](https://img.shields.io/badge/Skill-policy--memo--guide-111827)](#)
[![Language](https://img.shields.io/badge/language-Chinese%20first%20%7C%20English-0f766e)](#)
[![Genre](https://img.shields.io/badge/genre-Policy%20Memo-7c3aed)](#)
[![Reference](https://img.shields.io/badge/reference-Duke%20Writing%20Studio-b45309)](references/duke-policy-memo-guide.md)
[![Optimized%20with](https://img.shields.io/badge/optimized%20with-darwin--skill-2563eb)](https://github.com/alchaincyf/darwin-skill)

</div>

---

## What This Is

`policy-memo-guide` is a writing skill for agent workflows. It is designed for one job: helping an agent produce decision-oriented policy memos instead of drifting into generic essays or analysis.

It is especially useful when the user wants to:

- convert notes or research into a formal `policy memo`
- produce a `memo-ready outline` when key details are still missing
- rewrite an existing analysis into memo format
- keep recommendations, audience, and executive summary discipline front and center

---

## Why It Exists

Strong models often know what a policy memo *looks like*, but still fail in recurring ways:

- they over-ask for clarification when partial progress is possible
- they produce general analysis instead of a memo
- they bury the recommendation too late
- they lose decision-maker focus when the prompt is underspecified

This skill is built to reduce those failure modes.

---

## Core Principles

The skill is grounded in the Duke Writing Studio policy memo guide and pushes four habits:

1. **Audience-first**
   Start with who the memo is for and what decision they need to make.

2. **Inverted pyramid**
   Put the most important conclusion first, then supporting detail.

3. **Executive-summary discipline**
   The main claim should be visible even on a fast skim.

4. **Outline-before-stall**
   If the context is incomplete, produce useful structure first rather than replying with only questions.

---

## Good Fit

Typical trigger requests:

- “Help me write a policy memo for the mayor’s office”
- “Turn this analysis into a policy memorandum”
- “Rewrite this brief as a policy memo for the minister”
- “My professor wants this background paper turned into a policy memo”
- “I do not have a final recommendation yet, but help me scaffold the memo”

Not a good fit for:

- standard academic essays
- literature reviews
- op-eds
- generic writing tasks without memo structure

---

## Output Modes

The skill does not force every request into the same deliverable. It routes to the lightest useful output:

| Mode | When to use it | Result |
| --- | --- | --- |
| `Full memo` | The request is sufficiently specified | Draft the full memo |
| `Memo-ready outline` | Key details are missing but structure is possible | Provide a usable scaffold with assumptions |
| `Rewrite` | The user already has a draft, notes, or a brief | Convert it into memo form |
| `Recommendation options` | The recommendation is not stable yet | Offer options, then name the strongest one |

---

## Example Prompts

```text
Please turn the following analysis into a policy memo for the mayor's office on whether to expand night bus service.
```

```text
Turn my notes on export controls and semiconductor supply chains into a policy memo for the Minister of Trade.
```

```text
I have a background analysis, but my professor wants a policy memo. The audience and recommendation are still unclear. Help me build the structure first.
```

---

## Repository Layout

```text
policy-memo-guide/
├── SKILL.md
├── README.md
├── README_EN.md
├── test-prompts.json
├── agents/
│   └── openai.yaml
└── references/
    └── duke-policy-memo-guide.md
```

---

## References

- Duke Writing Studio Policy Memo Guide
- Cleaned in-repo reference: [`references/duke-policy-memo-guide.md`](references/duke-policy-memo-guide.md)
- Original Duke PDF: `https://twp.duke.edu/sites/twp.duke.edu/files/file-attachments/policy-memo.original.pdf`

---

## Iterative Optimization

This skill was iteratively refined with **[darwin-skill](https://github.com/alchaincyf/darwin-skill)** rather than polished in one pass.

The optimization loop was intentionally disciplined:

- score across 8 dimensions
- modify only one weak dimension per round
- evaluate with independent subagents
- compare with-skill vs baseline behavior
- revert changes when the weighted score does not improve

So this repository captures a tested working version, not just a manually edited draft.

---

## Quick Use

Put this directory into your skill folder:

```bash
mkdir -p ~/.codex/skills
cp -R policy-memo-guide ~/.codex/skills/
```

Then invoke it explicitly:

```text
Use $policy-memo-guide to turn my notes into a concise policy memo for a named audience.
```

Or trigger it naturally with a memo-writing request.

---

## Who This Is For

- students writing policy memos
- policy, IR, or public administration researchers
- anyone converting research notes into decision-facing documents
- anyone who wants agent outputs to stay memo-shaped under ambiguity

---

## Status

The current version has already gone through independent subagent scoring and regression-style prompt evaluation. It is usable as a stable working release, with future iterations likely to focus on:

- stronger edge-case handling
- higher with-skill performance under ambiguity
- fewer unnecessary clarification questions

