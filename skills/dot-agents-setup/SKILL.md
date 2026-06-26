---
name: dot-agents-setup
description: Set up, migrate, and maintain a portable .agents directory based on dotagentsprotocol.com. Use when the user asks to initialize .agents, standardize agent config across tools, migrate from vendor-specific folders, configure layered global/workspace overlays, or prepare shareable .dotagents bundles.
---

# dot-agents-setup

Practical workflow for adopting the .agents Protocol in any codebase.

Use this skill when a user wants to:
- initialize a new .agents setup;
- migrate from .cursor, .claude, .github/copilot-instructions.md, and scattered configs;
- standardize MCP, skills, sub-agents, tasks, and memories in one place;
- prepare a repository-safe workspace layer for team collaboration;
- package/share installable .dotagents bundles.

## What The Protocol Is

The .agents Protocol is an open directory convention that co-locates agent configuration in one predictable tree.

Core ideas:
- One directory: .agents/
- Open standards convergence: MCP, AGENTS.md, Skills, sub-agents, tasks, memories
- Vendor-neutral and git-friendly
- Layered configuration:
  - global base at ~/.agents/
  - project overrides at ./.agents/

## Canonical Structure

Recommended structure:

```text
.agents/
├── agents.md
├── system-prompt.md
├── mcp.json
├── models.json
├── skills/
│   └── example-skill/
│       └── skill.md
├── agents/
│   └── example-agent/
│       ├── agent.md
│       └── config.json
├── tasks/
│   └── example-task/
│       └── task.md
└── memories/
    └── project-notes.md
```

## Setup Procedure

### Step 1: Decide Scope

Choose one of the following:
- Global only: use ~/.agents for personal defaults
- Workspace only: use ./.agents for repository-specific config
- Layered (recommended): both, with workspace overriding global

Before creating anything, detect existing state:
- existing `~/.agents` and/or `./.agents` trees;
- existing vendor configs (`.cursor`, `.claude`, `.github/copilot-instructions.md`);
- existing skills/agents/tasks/memories IDs that may conflict.

If state is ambiguous, ask follow-up questions before writing files.

### Step 2: Create Directory Tree

```bash
# global
mkdir -p ~/.agents/{skills,agents,tasks,memories}

# workspace - project context
mkdir -p .agents/{skills,agents,tasks,memories}
```

### Step 3: Add Baseline Files

Create these files first:
- .agents/agents.md
- .agents/mcp.json
- .agents/system-prompt.md (optional, but recommended)
- .agents/models.json (optional)

Minimal agents.md template:

```markdown
---
kind: agents
---

# Project Guidelines
- Follow existing project conventions
- Run tests before proposing completion
- Prefer minimal, reviewable diffs
```

Minimal mcp.json template:

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["@mcp/server-filesystem", "."],
      "transport": "stdio"
    }
  }
}
```

### Step 4: Add First Skill

Create .agents/skills/<id>/skill.md.

Template:

```markdown
---
id: code-review
name: Code Review Expert
description: Reviews code for correctness, risk, and test gaps
enabled: true
---

Review changes for:
- Behavior regressions
- Security and privacy concerns
- Missing tests
```

### Step 5: Add One Sub-Agent (Optional)

Create .agents/agents/<id>/agent.md.

Template:

```markdown
---
id: code-reviewer
name: Code Reviewer
description: Specialized review agent
role: delegation-target
enabled: true
connection-type: internal
---

You are a code review specialist. Focus on risk, regressions, and tests.
```

### Step 6: Add One Repeat Task (Optional)

Create .agents/tasks/<id>/task.md.

Template:

```markdown
---
kind: task
id: daily-review
name: Daily Review
intervalMinutes: 60
enabled: true
runOnStartup: false
---

Review open pull requests and summarize status.
```

## Migration Workflow (Vendor Folders -> .agents)

1. Inventory current sources:
- .cursor rules/prompts
- .claude configs
- .github/copilot-instructions.md
- ad-hoc prompt markdown files

2. Normalize by intent:
- General project guidance -> .agents/agents.md
- Reusable procedures -> .agents/skills/*/skill.md
- Specialist role prompts -> .agents/agents/*/agent.md
- Automation cadences -> .agents/tasks/*/task.md
- Durable notes/preferences -> .agents/memories/*.md

3. Keep names stable and semantic IDs deterministic:
- kebab-case for folder IDs
- one concept per file

4. Validate startup behavior in your target tools.

5. Commit incrementally:
- initial scaffold
- migrated guidance
- migrated skills
- migrated agents/tasks/memories

### Adaptation Policy For Existing Configs

If `.agents` already exists:
- do not overwrite files blindly;
- merge new content into existing files where feasible;
- preserve existing IDs and only introduce new IDs when needed;
- prefer additive migration and archive deprecated files only after confirmation.

If migration collides with existing IDs or naming:
- ask user whether to keep, replace, or rename conflicting items;
- document the chosen conflict strategy in the final report.

## Overlay Rules To Preserve

When both layers exist:
- Merge order: defaults <- config.json <- ~/.agents <- ./.agents
- Workspace layer wins on conflicts
- JSON files merge by top-level keys (shallow merge)
- Skills/agents/tasks/memories merge by ID; workspace item overrides global item with same ID

## Safety And Governance Checklist

Before calling setup complete, ensure:
- All files are plain JSON or Markdown
- No secrets committed (API keys, tokens)
- IDs are unique and stable
- Instructions are specific and testable
- Skills are task-oriented, not generic essays
- Workspace .agents is committed only if it is team-safe

## Packaging For Sharing

For public sharing as a .dotagents bundle:
- include only public-safe defaults;
- provide summary, tags, author, and compatibility notes;
- exclude private memories and secrets;
- test install handoff in a clean environment before publishing.

## Agent Execution Guidance

When invoked, do this sequence:
1. Detect whether .agents already exists globally and/or in workspace.
2. Detect existing configs/skills and map potential conflicts.
3. Ask user for desired scope (global, workspace, layered) only if ambiguous.
4. Confirm merge-vs-replace strategy when existing files are present.
5. Scaffold required directories and baseline files.
6. Migrate existing guidance into normalized locations.
7. Add at least one concrete skill and validate file structure.
8. Summarize resulting tree and next operational steps.

## Quick Verification Commands

```bash
# show tree
find .agents -maxdepth 4 -print | sort

# find missing required files
for f in agents.md mcp.json; do
  [ -f ".agents/$f" ] || echo "missing: .agents/$f"
done

# detect probable secrets accidentally committed in .agents
rg -n "(api[_-]?key|secret|token|BEGIN PRIVATE KEY)" .agents
```

## References

- https://dotagentsprotocol.com/
- https://hub.dotagentsprotocol.com/
- https://github.com/aj47/dotagentsprotocol-website
