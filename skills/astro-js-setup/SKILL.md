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

## What To Do First

1. Check the local Node.js version.
   - Astro requires Node.js v22.12.0 or higher.
   - Odd-numbered Node.js releases such as v23 are not supported.
2. Prefer the official install flow.
   - Use `npm create astro@latest` for a new project.
   - Install dependencies if the wizard did not do it automatically.
3. Decide how the AI tool should connect to MCP.
   - Use the native MCP integration if the tool supports remote HTTP servers.
   - Otherwise, use the tool’s documented MCP connector or local proxy setup.

## Canonical Setup Flow

### Step 1: Create The Astro Project

Run:

```bash
npm create astro@latest
```

If you already know the integrations you need, add them during project creation with `--add`.

Examples:

```bash
npm create astro@latest -- --add react
npm create astro@latest -- --add react --add partytown
```

If you want a starter template, use `--template` with an official example or a GitHub repository.

### Step 2: Install Dependencies And Enter The Project

If the wizard skipped dependency installation:

```bash
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