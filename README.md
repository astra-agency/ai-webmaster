# AI Webmaster Agent Skills

**Expert skills for AI assistants working with modern open source websites and stacks.**

A set of portable skills that teach OpenCode, VS Code, Claude, Cursor, Copilot, Codex, and other AI agents how to professionally work with modern open source websites, developer tools, and ecosystems: analysis, development, SEO, performance, deployment, security, and maintenance.

The main focus is practical open source tooling and ecosystems: OpenCode, OpenClaw, OpenRouter, Astro JS, WordPress, and adjacent web stacks that teams actually use in production.

---

## Why these skills are needed

Modern AI assistants write code well, but often:
- Use outdated practices (jQuery, inline styles, old-school SEO)
- Ignore Core Web Vitals and performance
- Create weak semantic HTML and poor accessibility
- Suggest insecure solutions
- Don’t understand the specifics of different tech stacks (Next.js, Astro, WordPress, vanilla HTML, etc.)

This project is especially aimed at open source-first workflows, where agents need to understand both the tools themselves and the conventions around integrating them into real developer environments.

**AI Webmaster Skills** solve these problems by giving agents up-to-date, proven procedures and checklists.

## Available Skills (Planned)

| Skill                    | What it does |
|-------------------------|--------------|
| **dot-agents-setup**    | Sets up portable .agents protocol structure, migration, and layered config |
| **astro-js-setup**      | Installs Astro and configures the Astro Docs MCP server for AI-assisted development |
| **wp-setup**            | Sets up a modern WordPress development workflow for AI-assisted work on open source CMS projects |
| **design-md-setup**     | Sets up or retrofits DESIGN.md workflows using @google/design.md (lint, diff, export, spec) |
| **marketing-md-setup**  | Sets up or retrofits MARKETING.md Marketing-as-Code workflows using core + companion architecture |

---

## Installation

### Fastest way (recommended)

```bash
# List all available skills
npx skills add astra-agency/ai-webmaster --list

# Install a specific skill
npx skills add astra-agency/ai-webmaster --skill dot-agents-setup

# Install Astro setup skill
npx skills add astra-agency/ai-webmaster --skill astro-js-setup

# Install WordPress setup skill
npx skills add astra-agency/ai-webmaster --skill wp-setup

# Install DESIGN.md setup skill
npx skills add astra-agency/ai-webmaster --skill design-md-setup

# Install MARKETING.md setup skill
npx skills add astra-agency/ai-webmaster --skill marketing-md-setup


```