---
name: policy-memo-guide
description: |
  Draft policy memos and convert notes, analysis, or research into formal policy memorandum format.
  Use when the user asks for a policy memo, policy memorandum, policy brief in memo form,
  政策备忘录, 政策建议备忘录, 决策备忘录, or wants existing analysis rewritten for a specific decision-maker.
  Trigger on requests such as "帮我写一份给市长/部长/校长的政策备忘录", "把这份分析改成 policy memo",
  "turn this into a memo for the minister", or "rewrite this brief as a policy memorandum".
  Supports Chinese and English requests, preserves the user's working language unless told otherwise,
  and follows Duke Writing Studio guidance on audience focus, executive summary, inverted-pyramid organization,
  concrete word choice, and fast readability for decision-makers.
---

# Policy Memo Guide

Use this skill to turn rough analysis into a concise, decision-ready policy memo for a named audience.

## Quick Route

- Need to know whether the skill applies: read `When To Use`.
- Need missing info from the user: read `Required Inputs`.
- Need to decide whether to draft a memo, outline, or options set: read `Drafting Workflow` step 2.
- Need exact response shape: read `Output Modes And Templates`.

Primary reference: `references/duke-policy-memo-guide.md`
Read it when you need the full Duke Writing Studio guidance or want to sanity-check structure and tone.

## Reference Use

Use the Duke reference selectively:
- read it when the user asks for Duke-style compliance, memo format justification, or stricter adherence to the original handout;
- read it when you need to check the rationale for executive summaries, subheadings, or inverted-pyramid organization;
- do not quote or restate the whole reference when the current skill instructions already cover the task.

Use `test-prompts.json` only for evaluation or regression checking, not as user-facing content.

Resource routing:
- `references/duke-policy-memo-guide.md`: use for format justification, Duke-style alignment, or checking why a section belongs in the memo.
- `test-prompts.json`: use only to evaluate whether the skill still handles incomplete-input, full-memo, and outline-first scenarios well.

## When To Use

Trigger this skill when the user:
- asks for a `policy memo`, `policy memorandum`, `memo`, `政策备忘录`, or similar document;
- wants to convert analysis, notes, briefing materials, or recommendations into a formal policy document;
- needs a memo written for a specific decision-maker, office, client, or internal stakeholder.

Do not use this skill for essays, academic literature reviews, or persuasive op-eds unless the user explicitly wants memo format.

## Default Operating Rules

- Preserve the user's language by default. If the request is in Chinese, draft in Chinese unless the user asks for English. If the request is in English, keep the memo in English.
- If the user provides an assignment prompt or house style, follow that over this default skill.
- If the user wants revision rather than drafting, improve the existing memo instead of starting from zero.
- If the user asks for "policy brief" but the surrounding request clearly expects memo structure, use memo format and say so only if clarification matters.

## Required Inputs

Before drafting, identify these three essentials:
- `Audience`: who will read the memo and what authority they have.
- `Issue`: the decision, problem, or policy question the memo addresses.
- `Core recommendation`: the main action, choice, or judgment the memo will advance.

Helpful supporting inputs:
- writer role or title;
- date or deadline;
- decision context and relevant facts;
- alternatives considered;
- implementation constraints, costs, risks, or tradeoffs.

If any essential input is missing, ask brief targeted questions. Prefer 1-3 questions max. If the user already supplied enough context, do not ask again; infer reasonable defaults and label them as assumptions.

### Preferred Intake Questions

Use these in the smallest number needed:
- `Audience`: Who is the memo for, and what decision do they need to make?
- `Issue`: What specific policy problem, choice, or situation is the memo addressing?
- `Recommendation`: What action do you currently think the memo should recommend?

If the user has only raw material, ask for:
- any must-include facts, figures, or constraints;
- whether alternatives or risks should be explicitly compared;
- target length if it matters.

### Confirmation Checkpoint

Pause and confirm before drafting only when one of these is true:
- there are 2 or more plausible audiences and the choice would materially change the memo;
- there are multiple recommendations with non-obvious tradeoffs and the user has not indicated a preference;
- the user's assignment prompt conflicts with default memo structure or language.

If none of these apply, proceed with the strongest reasonable assumption and label it briefly in the draft.

After drafting, pause once more only if the memo depends on a material assumption that could reverse the recommendation. In that case, show the draft with a short assumptions note and ask whether to revise against a different assumption set.

Do not pause for confirmation when only minor details are missing, such as the exact date, writer title, or perfect section naming, if you can still produce a solid memo or memo-ready outline.

## Drafting Workflow

### Workflow Route

| If the request looks like... | Use this mode | Immediate next move |
| --- | --- | --- |
| "Write/draft a policy memo" with enough context | `Full memo` | Draft the memo directly |
| rough notes or research without a stable recommendation | `Recommendation options` or `Memo-ready outline` | identify the strongest provisional recommendation first |
| an existing essay, brief, or analysis that needs conversion | `Rewrite` | extract audience, issue, and recommendation before rewriting |
| missing audience or missing decision point | `Memo-ready outline` | ask the minimum missing questions or label assumptions |

### 1. Clarify the decision context

Determine:
- what the audience needs to decide;
- what the memo is trying to accomplish;
- what facts are solid versus interpretive judgments;
- what limitations or uncertainties must be acknowledged.

Never present opinions as facts. Support recommendations with logic, evidence, and realistic alternatives.

### 2. Choose the right deliverable

Pick one before drafting:
- `Full memo`: when the user asks for a complete document.
- `Memo-ready outline`: when the user is still thinking or key facts are missing.
- `Rewrite`: when the user already has analysis, notes, or a draft to convert.
- `Recommendation options`: when the user does not yet know the main recommendation.

If the recommendation is unclear, do not stall. Provide 2-3 realistic options, name the strongest one, and label it as a provisional recommendation.

Then commit to the chosen mode and do not mix formats unless the user asks for both.

### 3. Build the memo around the main recommendation

Use an inverted pyramid at every level:
- start the memo with the most important conclusion;
- start each section with its main point;
- place detail, evidence, and secondary background after the lead claim.

A reader should understand the main point after one quick read, or by reading only the first sentence of each section.

### 4. Draft in standard policy memo format

Unless the user specifies another template, use:

```text
To: [audience name, title]
From: [writer name, title]
Date: [date]
RE: [specific action-oriented subject line]

Executive Summary
[One paragraph summarizing the issue, recommendation, and why it matters.]

[Section heading stating the section's takeaway]
[Paragraph(s) with the key point first, then supporting detail.]

[Section heading stating the section's takeaway]
[Paragraph(s) with the key point first, then supporting detail.]

[Section heading stating the section's takeaway]
[Recommendation, implementation implications, risks, or alternatives.]
```

Preferred section types:
- decision context or background;
- key analysis or options;
- recommendation;
- tradeoffs, risks, or implementation steps.

Use bold or clearly marked subheadings when formatting allows. Make subheadings informative enough that the reader can skim them and still follow the argument.

Useful heading patterns for full memos:
- `Why [current issue] requires action now`
- `Why [option or actor] is the key constraint`
- `Why [recommended action] is the strongest choice`
- `What tradeoffs or implementation risks remain`

### 5. Handle evidence and uncertainty explicitly

- If evidence is strong, make the recommendation direct and specific.
- If evidence is partial, keep the recommendation but state the assumptions.
- If evidence is thin or disputed, narrow the claim and identify what would change the recommendation.
- If the user supplies opinions only, convert them into clearly labeled judgments and note what evidence would be needed to strengthen them.

## Style Rules

Follow these rules closely:
- Be concise, organized, professional, and audience-specific.
- Lead with the recommendation or central claim, not with a long setup.
- Keep context brief in the executive summary; expand later only as needed.
- Prefer concrete wording over vague abstractions.
- Cut throat-clearing, generic theory, and unnecessary scene-setting.
- Avoid logical fallacies and unsupported causal claims.
- Present realistic alternatives and acknowledge limitations.

## Word Choice Guidance

When possible, replace vague words with direct alternatives:

| Vague | Prefer |
| --- | --- |
| facilitate | help, enable, support |
| indicate | show, say, suggest |
| concept | idea, proposal, approach |

Also prefer:
- active verbs over nominalizations;
- specific actors over passive constructions;
- plain language over inflated academic phrasing.

## Output Modes And Templates

Choose the lightest deliverable that matches the request:
- If the user wants a full memo, produce the complete document.
- If the user is still thinking, provide a memo-ready outline plus the missing inputs.
- If the user gives raw notes, first extract the audience, issue, and recommendation, then draft.
- If evidence is thin, write a cautious memo that clearly flags assumptions and information gaps.

### Response Order

Keep the final response in this order:
- for a full memo: assumptions line if needed, then the memo itself with no extra preamble;
- for an outline: missing inputs first if truly necessary, then the memo-ready outline;
- for recommendation options: options first, then the recommended option, then the memo structure to use next.

When the user has given enough context to sketch the memo but not enough to finalize every detail, prefer producing a memo-ready outline with labeled assumptions instead of replying with only clarification questions.

### Memo-Ready Outline

Use:

```text
Audience:
Issue:
Provisional recommendation:

Executive Summary
[2-4 sentences]

Section 1 heading
- key point
- support needed

Section 2 heading
- key point
- support needed

Section 3 heading
- recommendation / tradeoffs / implementation
```

### Recommendation Options Mode

Use when the core recommendation is missing:

```text
Option 1: [action]
- upside:
- downside:

Option 2: [action]
- upside:
- downside:

Recommended option:
- why this is the strongest memo position now:
- what evidence would strengthen it:
```

## Edge Cases

- If the audience is unknown, propose the most plausible audience and mark it as an assumption.
- If the user gives too much background, compress aggressively and keep only decision-relevant facts near the top.
- If the user asks for a memo "based on" research, do not dump literature review prose into the memo.
- If the prompt appears academic and memo-like at the same time, preserve memo structure but obey any grading instructions the user provides.
- If the user requests citations, include them succinctly; otherwise do not let citation formatting overwhelm readability.
- If the user wants only a rewrite of tone or structure, preserve the user's underlying position unless they ask you to rethink the recommendation.
- If the available evidence is too thin for a confident recommendation, switch to a cautious memo or outline and name the missing evidence explicitly.
- If the user asks for a very short memo, keep the header and executive summary, then reduce the body to only the highest-value sections.
- If a professor, employer, or institution provides a required template, treat that template as binding and use this skill only for memo logic, clarity, and prioritization.

## Quality Check Before Responding

Confirm that the draft:
- names a real audience;
- states the recommendation early;
- includes an executive summary;
- uses informative subheadings;
- follows inverted-pyramid order within sections;
- distinguishes facts from judgments;
- uses concrete, clear wording;
- fits the user's language and assignment constraints.

If the memo fails any of these checks, revise before returning it.
