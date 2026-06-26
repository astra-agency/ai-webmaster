---
name: astro-js-setup
description: Set up a new Astro project and configure the Astro Docs MCP server for AI-assisted development. Use when the user asks to install Astro, bootstrap a fresh Astro site, or connect an AI tool to the Astro documentation through MCP.
---

# astro-js-setup

Practical workflow for starting a new Astro project and wiring in the Astro Docs MCP server so AI tools can use current Astro documentation.

Use this skill when a user wants to:
- create a new Astro app from scratch;
- install Astro with the recommended CLI flow;
- confirm the local prerequisites for Astro development;
- add the Astro Docs MCP server to an AI coding tool;
- keep AI-generated Astro code aligned with current docs and setup conventions.

## Inputs Required

Before writing files or running bootstrap commands, ask and confirm:

1. Target scope
- Current repository or a new directory?

1.1 Project layout
- Use a dedicated Astro app directory?
- Default for greenfield setup: `astro/` in repository root.
- For existing repos, detect and reuse the current Astro root.

2. Existing project state
- Is this a greenfield Astro setup or an existing project that must be preserved?

3. MCP target
- Which AI client should receive MCP config (`vscode`, `codex`, `claude`, `cursor`, or other)?

4. Change policy
- Should existing config be merged in place (recommended) or replaced where safe?

If any answer is unclear, stop and ask a follow-up instead of guessing.

## Directory placement contract

Use these placement rules unless the user explicitly overrides them:

- Astro application root: `astro/`
- New Astro scaffolding should be created inside `astro/`, not mixed into repository root
- Agent/MCP config files remain where the selected client expects them (root or client-specific config paths)

If an existing project already has Astro in another location, preserve that location and adapt in place.

## What To Do First

1. Detect existing configuration and skills first.
  - Check for `package.json`, `astro.config.*`, `src/pages/`, and skill/config folders.
  - Check for existing MCP config used by the selected client.
  - If files already exist, switch to adaptation flow instead of fresh scaffold flow.
2. Check the local Node.js version.
   - Astro requires Node.js v22.12.0 or higher.
   - Odd-numbered Node.js releases such as v23 are not supported.
3. Prefer the official install flow.
   - Use `npm create astro@latest` for a new project.
   - Install dependencies if the wizard did not do it automatically.
4. Decide how the AI tool should connect to MCP.
   - Use the native MCP integration if the tool supports remote HTTP servers.
   - Otherwise, use the tool’s documented MCP connector or local proxy setup.

## Preflight Detection

Run a quick inventory in the target directory before changes:

```bash
pwd
node -v
npm -v
rg --files -g 'package.json' -g 'astro.config.*' -g 'src/pages/**' -g 'AGENTS.md' -g '.agents/**' -g '.github/skills/**' -g '.codex/**' -g '.claude/**' -g '.cursor/**'
rg --files -g 'astro/**'
```

Interpretation:
- If no Astro files exist, continue with canonical fresh setup in `astro/`.
- If Astro files exist, do not re-bootstrap; adapt existing config and dependencies.
- If MCP config already exists, merge `Astro docs` entry without deleting other servers.

## Canonical Setup Flow

### Step 1: Create The Astro Project

Run:

```bash
npm create astro@latest astro
```

If you already know the integrations you need, add them during project creation with `--add`.

Examples:

```bash
npm create astro@latest astro -- --add react
npm create astro@latest astro -- --add react --add partytown
```

If you want a starter template, use `--template` with an official example or a GitHub repository.

For existing Astro projects:
- skip re-running `npm create astro@latest`;
- run dependency and config checks only;
- apply additive updates (do not replace user files unless explicitly approved).

### Step 2: Install Dependencies And Enter The Project

If the wizard skipped dependency installation:

```bash
cd astro
npm install
```

Then `cd` into the project directory if needed.

### Step 3: Verify The Basic Astro Files

For a manual setup or a quick sanity check, make sure the project includes:
- `src/pages/index.astro`
- `astro.config.mjs`
- `tsconfig.json`
- `public/` for static assets

Astro also supports a simple starting page and a config file with `defineConfig({})`.

### Step 4: Configure The Astro Docs MCP Server

Astro provides a remote MCP server for live documentation access.

Server details:
- Name: Astro Docs
- URL: `https://mcp.docs.astro.build/mcp`
- Transport: Streamable HTTP

Use the server configuration format supported by the target AI tool. A generic MCP config looks like this:

```json
{
  "mcpServers": {
    "Astro docs": {
      "type": "http",
      "url": "https://mcp.docs.astro.build/mcp"
    }
  }
}
```

For tools that require a local proxy, follow the tool-specific MCP docs and point the proxy at the same Astro URL.

If MCP config already exists:
- preserve all existing `mcpServers` entries;
- add or update only the Astro Docs server block;
- avoid changing unrelated transport or auth fields.

## Adaptation Rules For Existing Config

When configuration is already present:
- prefer merge over replacement;
- keep file style and key ordering consistent with existing project conventions;
- avoid destructive edits to existing scripts, integrations, or MCP servers;
- ask before renaming/deleting files or changing behavior-affecting defaults.

Trigger clarifying questions when:
- multiple MCP config files exist and source of truth is unclear;
- Astro version and Node version constraints conflict;
- existing scripts differ from recommended commands.

### Step 5: Use Astro Best Practices In Agent Prompts

When prompting an AI tool on an Astro project, steer it toward current docs and official commands:
- start with `npm create astro@latest` for fresh projects;
- use `astro add` for official integrations when possible;
- verify current APIs before generating code;
- prefer the official Astro docs MCP server over stale model memory;
- remind the tool to check the latest Astro guidance for newer features like sessions, actions, and content collections.

## Recommended Validation

After setup, confirm:
- `npm run dev` starts successfully;
- the dev server is reachable;
- the AI tool can query the Astro Docs MCP server;
- generated Astro code follows current docs instead of outdated patterns.

## Troubleshooting

If setup fails:
- re-check the Node.js version;
- verify the MCP server URL is exactly `https://mcp.docs.astro.build/mcp`;
- confirm the AI tool supports remote HTTP MCP servers or has the correct proxy configuration;
- use the Astro install and AI docs as the source of truth.

## References

- https://docs.astro.build/en/install-and-setup/
- https://docs.astro.build/en/guides/build-with-ai/