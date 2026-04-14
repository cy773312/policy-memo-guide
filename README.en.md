# Policy Memo Guide Skill

<p align="center">
  <strong>A Codex skill for real policy memo writing</strong><br />
  Turns analysis, notes, and research into decision-facing policy memos instead of generic essays.
</p>

<p align="center">
  <a href="./README.md">中文版</a> ·
  <a href="./SKILL.md">View SKILL.md</a> ·
  <a href="https://github.com/alchaincyf/darwin-skill">Darwin Skill Optimizer</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Codex-Skill-111827?style=flat-square" alt="Codex Skill" />
  <img src="https://img.shields.io/badge/Language-Chinese%20first-0f766e?style=flat-square" alt="Chinese first" />
  <img src="https://img.shields.io/badge/Use-Policy%20Memo-7c3aed?style=flat-square" alt="Policy Memo" />
  <a href="https://github.com/alchaincyf/darwin-skill">
    <img src="https://img.shields.io/badge/Iteratively%20optimized-Darwin%20Skill-2563eb?style=flat-square" alt="Optimized with Darwin Skill" />
  </a>
</p>

<p align="center">
  <sub>Chinese-first repository. English readers can start here.</sub>
</p>

## One-line Summary

`policy-memo-guide` is a skill built specifically for **policy memo** tasks.  
Its goal is not just “formal writing,” but helping an agent reliably do the things memo writing actually requires:

- identify the audience and decision point first
- surface the recommendation early
- produce a `memo-ready outline` when information is incomplete
- stay memo-shaped instead of drifting into general analysis

## Good Fit

This skill is especially useful for:

- memos for mayors, ministers, principals, directors, or similar named audiences
- rewriting research notes or policy analysis into memo form
- assignments where a professor or manager says “do not write an essay, write a memo”
- situations where the recommendation is not fully stable yet, but the structure must be built now
- agent workflows that need decision-facing writing rather than commentary

It is **not primarily for**:

- standard academic essays
- literature reviews
- opinion pieces
- generic writing tasks without memo structure

## What the Skill Does

Instead of forcing every request into one deliverable, it routes to the most useful output mode for the current context.

By default it supports 4 result types:

1. `Full memo`
2. `Memo-ready outline`
3. `Rewrite`
4. `Recommendation options`

Its core value can be summarized in four moves:

| Capability | What it does |
|---|---|
| lock audience / issue / recommendation early | prevents generic “policy analysis” drift |
| enforce inverted-pyramid organization | keeps recommendation and decision logic near the top |
| produce structure before stalling | reduces unnecessary clarification loops |
| preserve memo-first constraints | prevents output from sliding into essay form |

## Trigger Examples

Good direct triggers:

```text
Please turn the following analysis into a policy memo for the mayor's office.
```

```text
Rewrite this as a policy memo for the Ministry of Education.
```

```text
Turn this into a policy memo for the Minister of Trade.
```

```text
My professor wants this background paper turned into a policy memo. Help me scaffold it first.
```

It also fits more casual requests:

- “help me turn this into a memo”
- “do not make it an essay”
- “give me a memo outline first”
- “rewrite this for a decision-maker”

## Output Style

The target is not “formal writing” in the abstract. The target is **actual memo behavior**.

That means the skill tries to keep outputs:

- audience-specific
- recommendation-first
- executive-summary disciplined
- skimmable through headings
- explicit about assumptions and uncertainty

Typical output features include:

- `To / From / Date / RE`
- `Executive Summary`
- recommendation-first section headings
- concise tradeoff / implementation framing

## Quick Install

If your Codex skills live under `$CODEX_HOME/skills`:

```bash
git clone https://github.com/cy773312/policy-memo-guide.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/policy-memo-guide"
```

Or copy the directory manually:

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R policy-memo-guide "${CODEX_HOME:-$HOME/.codex}/skills/"
```

## Repository Layout

```text
policy-memo-guide/
├── README.md
├── README.en.md
├── SKILL.md
├── test-prompts.json
├── agents/
│   └── openai.yaml
└── references/
    └── duke-policy-memo-guide.md
```

## Why This Skill Deserves to Exist

Policy memo is a classic genre that models often only *approximately* get right:

- they know the term
- but still write generic analysis
- recommendations appear too late
- and incomplete inputs often trigger too many questions

This skill exists to pull the workflow back toward memo discipline:

- define the audience and decision point first
- decide between full memo, outline, or options mode
- produce output in an inverted-pyramid, decision-facing form

## Iterative Optimization with Darwin Skill

This repository was not written in a single pass. It was iteratively refined with [`darwin-skill`](https://github.com/alchaincyf/darwin-skill).

The optimization loop was closer to hill-climbing than ordinary editing:

1. score the skill
2. modify one weak point per round
3. rescore after the change
4. run independent `with_skill / baseline` evaluation through subagents
5. keep the change only if the weighted score improves; otherwise revert

The main optimization themes included:

- when to ask questions vs when to proceed with an outline
- when to switch directly into full memo mode
- whether memo formatting constraints were strong enough
- whether edge cases still stayed memo-first

So this is not just a “nicely written” skill. It is a repeatedly evaluated and filtered one.

## Design Principles

- Audience first
- Recommendation early
- Outline before stall
- Memo over essay
- Clarity over vague theory language

## Related Files

- Main skill file: [SKILL.md](./SKILL.md)
- UI metadata: [agents/openai.yaml](./agents/openai.yaml)
- Duke reference material: [references/duke-policy-memo-guide.md](./references/duke-policy-memo-guide.md)
- Darwin optimizer: [darwin-skill](https://github.com/alchaincyf/darwin-skill)

## License

This repository does not yet include a license file. If you want open reuse terms, adding `MIT` or `Apache-2.0` would be the cleanest next step.

