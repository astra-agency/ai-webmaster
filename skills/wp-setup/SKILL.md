---
name: wp-setup
description: Bootstrap a WordPress-ready AI workflow in the current repository by asking setup questions, installing official skills from WordPress/agent-skills, and configuring local development environment defaults.
compatibility: Targets WordPress 6.9+ (PHP 7.2.24+). Filesystem-based agent with bash + node.
---

# wp-setup

## When to use

Use this skill when the user asks to:

- prepare a repository for WordPress development with AI assistance;
- install official WordPress skills from `WordPress/agent-skills`;
- decide which skills should be installed for current tasks;
- configure local WordPress environment (`wp-env` and/or Playground);
- standardize repo-level setup for team usage.

## Inputs required

Before running any installation command, ask these questions.

1. Scope and target repo
- Which repo should receive the setup?
- Install scope: `project` (recommended) or `global`?

2. Assistant targets
- Which clients should be configured?
- Allowed targets: `vscode`, `codex`, `claude`, `cursor`.

3. Skill set mode
- Install `all` official WordPress skills, or `selected` only?
- If selected, ask for specific skill names (for example: `wp-plugin-development`, `wp-wpcli-and-ops`, `wp-playground`, `wp-performance`, `wp-phpstan`, `wp-abilities-api`).

4. Local environment mode
- Choose environment profile:
  - `wp-env` (persistent local dev with Docker),
  - `playground` (ephemeral fast sandbox),
  - `both`.

5. Local runtime constraints
- Confirm Docker availability (required for `wp-env`, often helpful for tooling).
- Confirm Node.js version (`>= 20.18` recommended for Playground tooling).
- Ask whether WP-CLI is required now.

If any answer is missing or ambiguous, stop and ask a follow-up instead of guessing.

## Procedure

### 0) Guardrails

1. Confirm environment is local dev, not production.
2. Explain that install steps can create/update:
- `.github/skills/`
- `.codex/skills/`
- `.claude/skills/`
- `.cursor/skills/`
- optional local environment files like `.wp-env.json`
3. Get explicit approval before writing files.

### 1) Detect current repo readiness

Run in target repository:

```bash
pwd
node -v
npm -v
docker --version
rg --files -g 'AGENTS.md' -g '.wp-env.json' -g 'package.json'
```

If `AGENTS.md` exists, use it as canonical project command source.

### 2) Install official WordPress skills (preferred: `npx skills add`)

Use official source:
- `https://github.com/WordPress/agent-skills`

List available skills first:

```bash
npx skills add WordPress/agent-skills --list
```

Install skills according to chosen mode:

```bash
# selected skills (example)
npx skills add WordPress/agent-skills --skill wp-plugin-development wp-wpcli-and-ops wp-playground

# all skills (run repeatedly or with selected list captured from --list)
# if tool supports batch install for all, prefer that path
```

When global install was requested, use:

```bash
npx skills add WordPress/agent-skills --skill wp-plugin-development --global
```

If `npx skills add` is unavailable, use manual official fallback.

### 3) Fallback install via skillpack scripts (official repo flow)

```bash
git clone https://github.com/WordPress/agent-skills.git
cd agent-skills
node shared/scripts/skillpack-build.mjs --clean

# project-level install into target repo
node shared/scripts/skillpack-install.mjs --dest=<target-repo> --targets=codex,vscode,claude,cursor

# optional selected skills only
node shared/scripts/skillpack-install.mjs --dest=<target-repo> --targets=codex,vscode,claude,cursor --skills=wp-plugin-development,wp-wpcli-and-ops,wp-playground
```

Use `--dry-run` first if user asked for preview.

### 4) Configure local WordPress environment in repo

#### Option A: `wp-env`

If user chose `wp-env` or `both`:

1. Ensure `@wordpress/env` is available (local dev dependency preferred).
2. Add/verify `.wp-env.json` in repo root with minimal predictable setup.
3. Add scripts in `package.json` if missing:
- `wp-env:start`
- `wp-env:stop`
- `wp-env:destroy`
4. Start environment:

```bash
npx wp-env start
```

#### Option B: `playground`

If user chose `playground` or `both`:

```bash
npx @wp-playground/cli@latest server --auto-mount
```

For blueprint execution:

```bash
npx @wp-playground/cli@latest run-blueprint --blueprint=<file-or-url>
```

### 5) Ensure key official skills are present for local workflows

For local setup and operations, prioritize these official skills:

- `wp-wpcli-and-ops`
- `wp-playground`
- `wp-performance`
- `wp-phpstan`
- `wp-plugin-development`
- `wp-abilities-api` (when targeting capability checks)

If user requested “all skills”, install all published skills from WordPress source.

## Verification

After setup, verify and report:

1. Skill directories exist in chosen targets.
- Examples: `.github/skills`, `.codex/skills`, `.claude/skills`, `.cursor/skills`.
2. Installed WP skill names are listed and match user choice.
3. Environment status:
- `wp-env`: `npx wp-env start` succeeds.
- `playground`: local server starts and prints local URL.
4. If `AGENTS.md` exists, confirm setup does not contradict documented commands.

Provide a short final report with:
- chosen scope and targets;
- installed skills list;
- environment mode configured;
- next command user can run immediately.

## Failure modes / debugging

1. `npx skills add` command not found.
- Use skillpack fallback (`skillpack-build.mjs` + `skillpack-install.mjs`).

2. `--dest is required` during skillpack install.
- Provide absolute/relative repo path in `--dest=<target-repo>`.

3. Docker missing for `wp-env`.
- Skip `wp-env` and proceed with `playground`, or ask user to install Docker.

4. Permission issues writing global skills.
- Retry with project scope, or ask user to run command with proper permissions.

5. Existing local skill customizations are overwritten.
- Re-run with merge mode when using skillpack:

```bash
node shared/scripts/skillpack-install.mjs --dest=<target-repo> --targets=codex,vscode,claude,cursor --mode=merge
```

## Escalation

Escalate to the user when:

- multiple conflicting setup standards exist across repo docs;
- production-like environment might be affected;
- required tooling cannot be installed due to policy restrictions;
- user must choose between global and project scope for shared team workflow.

Do not proceed with destructive or broad replacement steps until the user confirms.