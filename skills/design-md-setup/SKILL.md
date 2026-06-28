---
name: design-md-setup
description: Set up or retrofit DESIGN.md in a project using the official google-labs-code/design.md specification and CLI. Use when the user asks to initialize DESIGN.md from scratch, validate/export tokens, or align an existing project with DESIGN.md conventions.
compatibility: Requires Node.js and npm/npx. Uses @google/design.md CLI.
---

# design-md-setup

Practical workflow for adopting `DESIGN.md` as a design-system source of truth for coding agents.

Use this skill when a user wants to:
- create a new `DESIGN.md` file in a greenfield project;
- add `@google/design.md` linting and export commands;
- retrofit an existing repository that already has tokens, Tailwind theme, CSS variables, or design docs;
- validate token references, contrast, and section structure before shipping;
- export design tokens for Tailwind or DTCG interoperability.


## End-to-End Step Flow

Use this sequence as the default execution order.

1. Capture project constraints and setup mode.
- Confirm scope, `from-scratch` vs `adapt-existing`, integration targets, and change policy.

2. Choose design-system baseline via getdesign.md.
- Review and pick a base system from https://getdesign.md/.
- Confirm selected baseline name/style direction with the user and align it to project constraints.

3. Run preflight inventory.
- Detect existing design artifacts, tooling, and runtime readiness.

4. Implement `DESIGN.md`.
- Create or adapt `DESIGN.md` based on selected baseline and repository realities.

5. Validate and integrate.
- Run lint, fix critical findings, and wire scripts/exports when required.

6. Elaborate page-level decisions via RFC skill.
- For each key page/template, run the `rfc` skill to document layout intent, component choices, and acceptance criteria.
- Treat RFC outputs as the source for page-level implementation priorities.

7. Perform final balance check.
- Propose and run a final review with `skills/balance-lens` to check visual/system balance before completion.


## Inputs Required

Before editing files or running setup commands, ask and confirm:

1. Target scope
- Apply to current repository or another directory?

2. Setup mode
- `from-scratch` (new `DESIGN.md`) or `adapt-existing` (merge with current design artifacts)?

3. Existing design sources
- Which sources are canonical today: `tailwind.config.*`, CSS variables, Figma/token JSON exports, style guide docs, component library docs?

4. Tooling integration targets
- Add CLI usage only, or also wire scripts/CI checks (for example `npm scripts`, GitHub Actions, pre-commit hooks)?

5. Change policy
- Merge into existing files (recommended) or replace sections where safe?

If any answer is ambiguous, stop and ask follow-up questions instead of guessing.

## What To Do First

1. Confirm required inputs first.
- Confirm target scope, setup mode, existing design sources, integration targets, and change policy.

2. Choose baseline on getdesign.md.
- Explore https://getdesign.md/ and select the closest design-system base for the confirmed constraints.
- Record the chosen base in the working notes or directly in `DESIGN.md` overview rationale.

3. Detect current design-system context.
- Check for `DESIGN.md`, `tailwind.config.*`, global CSS variable files, token JSON files, and style docs.
- Detect existing npm scripts related to linting/design tokens.

4. Verify local runtime.
- Confirm `node -v`, `npm -v`, and npm registry config.
- If install fails with `ENOVERSIONS`, verify npm uses `https://registry.npmjs.org/`.

5. Decide installation path.
- Fast path: use `npx @google/design.md ...` commands directly.
- Project path: add `@google/design.md` dependency and npm scripts.

6. Choose setup flow.
- No existing design file: run `from-scratch` flow.
- Existing design assets: run `adapt-existing` flow.

## Preflight Detection

Run inventory in target repo:

```bash
pwd
node -v
npm -v
npm config get registry
rg --files -g 'DESIGN.md' -g 'tailwind.config.*' -g '**/*token*.json' -g 'src/**/*.css' -g 'styles/**/*.css' -g 'package.json'
```

Interpretation:
- If `DESIGN.md` does not exist, scaffold a canonical starter.
- If `DESIGN.md` exists, do not overwrite blindly; validate and patch incrementally.
- If Tailwind/CSS tokens exist, treat them as migration inputs for `adapt-existing`.

## Flow A: From Scratch

### Step 1: Install or invoke CLI

Use one of:

```bash
# one-off via npx
npx @google/design.md lint DESIGN.md

# or local dependency
npm install @google/design.md
```

Windows/PowerShell note:

```bash
npx -p @google/design.md designmd lint DESIGN.md
```

### Step 2: Create base DESIGN.md

Create `DESIGN.md` with:
- YAML front matter tokens (`name`, `colors`, `typography`, optional `rounded`, `spacing`, `components`);
- markdown rationale sections in canonical order (`## Overview`, `## Colors`, `## Typography`, `## Layout`, `## Elevation & Depth`, `## Shapes`, `## Components`, `## Do's and Don'ts`).

Minimal starter:

```md
---
version: alpha
name: Project Design System
colors:
  primary: "#1A1C1E"
  secondary: "#6C7278"
  tertiary: "#B8422E"
  neutral: "#F7F5F2"
typography:
  body-md:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: 400
    lineHeight: 1.6
rounded:
  sm: 4px
spacing:
  md: 16px
components:
  button-primary:
    backgroundColor: "{colors.tertiary}"
    textColor: "#FFFFFF"
    rounded: "{rounded.sm}"
    padding: 12px
---

## Overview
Describe the desired visual identity and tone.

## Colors
Map semantic roles to palette choices and usage rules.

## Typography
Define headline/body/label strategy and constraints.

## Layout
Define spacing rhythm, grid model, and density.

## Elevation & Depth
Explain shadow, border, or tonal-layer hierarchy.

## Shapes
Define corner radius language and shape consistency.

## Components
Document behavior for key primitives (buttons, inputs, cards).

## Do's and Don'ts
List enforceable guardrails and anti-patterns.
```

### Step 3: Validate

```bash
npx @google/design.md lint DESIGN.md
```

Fix errors first (for example broken references), then warnings when practical.

### Step 4: Add scripts (optional but recommended)

```json
{
  "scripts": {
    "design:lint": "designmd lint DESIGN.md",
    "design:spec": "designmd spec --rules",
    "design:export:tailwind": "designmd export --format json-tailwind DESIGN.md > tailwind.theme.json",
    "design:export:css": "designmd export --format css-tailwind DESIGN.md > theme.css",
    "design:export:dtcg": "designmd export --format dtcg DESIGN.md > tokens.json"
  }
}
```

Notes:
- `designmd` alias is cross-platform safe, especially on Windows.
- For Unix-only teams, `npx @google/design.md ...` is also acceptable.

## Flow B: Adapt Existing Project

### Step 1: Map existing tokens to DESIGN.md schema

Build a migration map from current sources:
- Tailwind colors/font/radius/spacing -> `colors`, `typography`, `rounded`, `spacing`.
- Component theme objects -> `components`.
- Existing style guide prose -> markdown body sections.

### Step 2: Merge instead of replace

When `DESIGN.md` already exists:
- preserve current token IDs unless there is a clear naming conflict;
- keep existing prose and patch section order only when needed;
- avoid deleting custom extension keys unless user requests strict cleanup.

### Step 3: Validate and resolve findings

Run linter and address highest-impact issues first:
- `broken-ref` (error) must be fixed;
- `contrast-ratio` warnings should be evaluated and corrected for accessibility;
- `section-order` and `unknown-key` warnings should be cleaned up for maintainability.

### Step 4: Wire exports into existing build chain

If project already uses Tailwind or token pipelines:
- add non-destructive export scripts;
- output generated files (`tailwind.theme.json`, `theme.css`, `tokens.json`) to agreed locations;
- avoid replacing existing theme files without explicit approval.

## CI / Automation Integration

Recommended CI check:

```bash
npx @google/design.md lint DESIGN.md
```

Fail pipeline on linter errors; treat warnings per team policy.

Optional regression check (for design-system evolution):

```bash
npx @google/design.md diff DESIGN.md DESIGN.next.md
```

Use in PR workflows to detect token/prose regressions.

## Validation Checklist

Before completion, confirm:
- `DESIGN.md` exists and parses;
- linter runs successfully and errors are resolved;
- npm scripts (if added) run as expected;
- exports generate files in expected formats when requested;
- page-level RFC artifacts were prepared via `rfc` skill for key screens/templates;
- final balance review was proposed (and ideally executed) via `skills/balance-lens`;
- setup mode (`from-scratch` or `adapt-existing`) and merge policy were respected.

## Troubleshooting

1. `npm error ENOVERSIONS` for `@google/design.md`
- Check `npm config get registry`.
- Expected: `https://registry.npmjs.org/`.
- Fix scoped registry misconfig (`@google:registry`) if present.
- Retry after `npm cache clean --force` when needed.

2. Windows command opens markdown file or prints no output
- Use `designmd` alias via:

```bash
npx -p @google/design.md designmd lint DESIGN.md
```

3. Lint errors on token references
- Ensure references use `{path.to.token}` and point to existing values.
- In `components`, composite refs like `{typography.body-md}` are valid.

4. Duplicate section headings
- Keep each canonical `##` section at most once.
- Merge duplicated content instead of repeating headings.

## References

- https://github.com/google-labs-code/design.md
- https://raw.githubusercontent.com/google-labs-code/design.md/main/README.md
- https://raw.githubusercontent.com/google-labs-code/design.md/main/docs/spec.md
- https://www.npmjs.com/package/@google/design.md
