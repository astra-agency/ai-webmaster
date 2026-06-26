---
name: marketing-md-setup
description: Set up or retrofit MARKETING.md (Marketing-as-Code) using the core + companion architecture from the Marketing-MD-Agentic-Standard. Use when the user asks to create MARKETING.md, migrate from ad-hoc marketing prompts/project-context files, or standardize agentic marketing context across tools.
compatibility: Markdown + YAML. Works best in repos that use Agent Skills and version-controlled AI context files.
---

# marketing-md-setup

Practical workflow for adopting `MARKETING.md` as a machine-readable marketing system of record for AI agents.

Use this skill when a user wants to:
- initialize `MARKETING.md` in a new repository;
- migrate from scattered prompt notes or `project-context` style files;
- standardize brand voice, personas, campaign defaults, and safety rules for multiple agents;
- adopt the core/companion architecture for role-based context loading;
- enforce conservative guardrails (approval gates, suppression, anti-hallucination) in AI marketing workflows.

## Inputs Required

Before creating or editing files, ask and confirm:

1. Target scope
- Apply in current repository or another directory?

2. Setup mode
- `from-scratch` (new `MARKETING.md`) or `adapt-existing` (merge with current docs)?

3. Business profile
- What vertical/business model is this for (SaaS, e-commerce, agency, marketplace, etc.)?
- Any jurisdiction/compliance constraints (GDPR, CAN-SPAM, local laws)?

4. Agent roles in scope now
- Which agents exist today (content, campaign, paid, lifecycle, analytics, personalization, crisis)?
- Which companion files are required immediately vs later?

5. Oversight policy
- Desired autonomy tiers (`full_autonomy`, `notify_and_proceed`, `notify_and_wait`, `human_only`)?
- Which actions must always require human approval?

6. Change policy
- Merge into existing files (recommended) or replace where safe?

If any answer is ambiguous, stop and ask a follow-up instead of guessing.

## What To Do First

1. Inventory existing context files.
- Check for `MARKETING.md`, `project-context*`, `.agents/`, `AGENTS.md`, `.github/skills/**`, `.codex/**`, `.claude/**`, `.cursor/**`.

2. Detect existing marketing docs.
- Check for strategy docs, campaign playbooks, voice/tone docs, KPI docs, compliance notes.

3. Choose setup flow.
- No `MARKETING.md`: run `from-scratch`.
- Existing docs/context: run `adapt-existing` and preserve prior intent.

4. Establish safety baseline.
- `SAFETY.MD` must be created/updated first among companion files.

## Preflight Detection

Run in target repository:

```bash
pwd
rg --files -g 'MARKETING.md' -g 'companion/**/*.MD' -g 'companion/**/*.md' -g '*project-context*' -g 'AGENTS.md' -g '.agents/**' -g '.github/skills/**' -g '.codex/**' -g '.claude/**' -g '.cursor/**'
rg -n "brand voice|persona|kpi|approval|suppression|utm|campaign" -g '*.md'
```

Interpretation:
- If `MARKETING.md` is missing, scaffold a core file plus companion directory.
- If `MARKETING.md` exists, patch incrementally and avoid destructive rewrites.
- If only `project-context` exists, map it into structured `MARKETING.md` sections.

## Canonical File Architecture

Expected structure:

```text
MARKETING.md
companion/
  SAFETY.MD
  BUDGET.MD
  CALENDAR.MD
  CAMPAIGNS.MD
  CHANNELS.MD
  COMPETITORS.MD
  CONTENT.MD
  EXPERIMENTATION.MD
  LIFECYCLE.MD
  MEASUREMENT.MD
  MESSAGING.MD
  PARTNERS.MD
  PERSONALIZATION.MD
  PRICING.MD
  SIGNALS.MD
  VISUAL.MD
```

Loading policy:
- Every agent session must read `MARKETING.md` + `SAFETY.MD`.
- Other companion files load by role and task.

## Flow A: From Scratch

### Step 1: Create core + companion skeleton

Create:
- `MARKETING.md`
- `companion/`
- `companion/SAFETY.MD` (mandatory first companion)

Add remaining companion files only when required by active agent roles.

### Step 2: Add minimum viable MARKETING.md sections

At minimum include:
- What this file is (authoritative agent config)
- Business identity
- Voice & tone
- Customer personas
- Campaign types and defaults
- KPI framework
- Suppression & compliance rules
- Human approval gates
- Prohibited actions
- Versioning and review cadence
- AI autonomy/safety guardrails
- Companion file registry

Use YAML for machine-readable policy and prose for qualitative guidance.

Starter skeleton:

```md
# MARKETING.MD

## What This File Is
Core marketing configuration read by all agents at session start.

## 1. Business Identity
```yaml
brand:
  name: "[Fill in]"
  category: "[Fill in]"
  business_model: "[Fill in]"
```

## 2. Voice & Tone
- Core voice attributes
- Channel-specific tone modulation
- Allowed/prohibited language

## 3. Customer Personas
- Persona definitions
- Persona quick reference table

## 4. Campaign Types
- Campaign type defaults and KPI mapping

## 5. KPI Framework
```yaml
anomaly_detection:
  lookback_window_days: [N]
  sensitivity: "[low | medium | high]"
```

## 6. Suppression & Compliance Rules
```yaml
global_suppression:
  unsubscribes: immediate_permanent
```

## 7. Human Approval Gates
- Define `notify_and_wait` decisions explicitly

## 8. Prohibited Actions
- Never send to suppressed addresses
- Never launch paid without human confirmation

## 9. Versioning
```yaml
marketing_md:
  version: "1.0.0"
  review_cadence: "Quarterly"
```

## 10. AI Autonomy & Safety Guardrails
```yaml
autonomy_levels:
  full_autonomy: []
  notify_and_proceed: []
  notify_and_wait: []
  human_only: []
```

## 11. Companion File Registry
- Registry with role-based loading rules
```

### Step 3: Create SAFETY.MD immediately

`SAFETY.MD` should include:
- crisis severity levels;
- kill switch conditions and owner;
- escalation matrix;
- holding statement templates;
- blocked topics/claims list;
- restart criteria after incident.

### Step 4: Add role-driven companions

Add only files needed for current agent roles.

Examples:
- Content agent: `MESSAGING.MD`, `CONTENT.MD`.
- Campaign/Paid agent: `CAMPAIGNS.MD`, `BUDGET.MD`, `PRICING.MD`, `CHANNELS.MD`.
- Analytics/Optimization agent: `MEASUREMENT.MD`, `EXPERIMENTATION.MD`.
- Lifecycle/Triggered agent: `LIFECYCLE.MD`, `SIGNALS.MD`, `PERSONALIZATION.MD`.

## Flow B: Adapt Existing Project

### Step 1: Map existing docs to MARKETING.md sections

Typical mapping:
- brand deck / positioning notes -> Business Identity + Voice/Tone
- ICP docs -> Personas
- campaign playbooks -> Campaign Types
- dashboard/KPI docs -> KPI Framework
- legal/compliance docs -> Suppression & Compliance
- internal approval SOP -> Human Approval Gates

### Step 2: Merge, do not overwrite

When files already exist:
- preserve IDs and naming conventions where possible;
- keep valid existing decisions unless user requests replacement;
- convert unstructured rules to YAML blocks when they control behavior.

### Step 3: Enforce anti-hallucination structure

Add or validate in `MESSAGING.MD`:
- approved claims library (human-curated);
- explicit rule: omit unverified claims;
- source requirement for stats/testimonials/comparative claims.

### Step 4: Encode conservative fail defaults

Ensure fallback behavior is explicit:
- unknown suppression status -> treat as suppressed;
- unknown budget status -> pause spend and alert;
- missing channel rule -> do not execute action;
- ambiguous compliance state -> escalate to human.

## Validation Checklist

Before completion, confirm:
- `MARKETING.md` exists and includes core policy sections.
- `companion/SAFETY.MD` exists and is referenced as universal load.
- Autonomy tiers are explicit and actionable.
- Approval gates and prohibited actions are machine-readable or unambiguous.
- Claims governance exists (`approved claims` policy).
- Review cadence is defined (recommended: quarterly).
- Files are in version control and update history is trackable.

## Troubleshooting

1. File is too long/noisy for every agent session
- Keep only universal rules in `MARKETING.md`.
- Move role-specific detail to companions.

2. Agents produce inconsistent messaging
- Tighten personas and channel tone rules.
- Centralize facts in `MESSAGING.MD` approved claims library.

3. Unsafe autonomous behavior
- Move risky actions into `notify_and_wait` or `human_only`.
- Add circuit breakers in `SAFETY.MD`.

4. Existing docs conflict with new structure
- Preserve old docs as source material, but create canonical mappings in `MARKETING.md`.
- Ask user which source is authoritative where conflicts remain.

## Execution Guidance

When invoked, do this sequence:
1. Run preflight inventory.
2. Confirm setup mode (`from-scratch` or `adapt-existing`).
3. Build/update `MARKETING.md` core.
4. Ensure `SAFETY.MD` exists and loads universally.
5. Add only necessary companion files for active roles.
6. Validate autonomy, approvals, suppression, and claims governance.
7. Summarize file tree and recommended next companion files.

## References

- https://github.com/benkohcc/Marketing-MD-Agentic-Standard
- https://raw.githubusercontent.com/benkohcc/Marketing-MD-Agentic-Standard/main/MARKETING.md
- https://ddpa.ru/kb/ai/marketing/
- https://ddpa.ru/kb/ai/marketing/marketing-md/
- https://ddpa.ru/kb/ai/marketing/marketing-md-standard/
- https://ddpa.ru/kb/ai/marketing/marketing-skills/
