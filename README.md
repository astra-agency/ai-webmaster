# AI Webmaster Agent Skills

**Expert skills for AI assistants working with modern open source websites and stacks.**

url: https://github.com/astra-agency/ai-webmaster

A set of portable skills that teach OpenCode, VS Code, Claude, Cursor, Copilot, Codex, and other AI agents how to professionally work with modern open source websites, developer tools, and ecosystems: analysis, development, SEO, performance, deployment, security, and maintenance.

The main focus is practical open source tooling and ecosystems: OpenCode, OpenClaw, OpenRouter, Astro JS, WordPress, and adjacent web stacks that teams actually use in production.

---

## Installation


### Basic, Context and Spec Driven Development
```bash
# List all available skills
npx skills add astra-agency/ai-webmaster --list

# Install all skills from this repository
npx skills add astra-agency/ai-webmaster --all

# Install a specific skill
npx skills add astra-agency/ai-webmaster --skill dot-agents-setup

# Install RFC skill
npx skills add astra-agency/ai-webmaster --skill rfc

```

### Design UI/UX Setup Skills

```bash
# Install DESIGN.md setup skill
npx skills add astra-agency/ai-webmaster --skill design-md-setup

npx skills add astra-agency/ai-webmaster --skill balance-lens
```

### Website Framework Setup Skills

```bash

# Install Astro setup skill
npx skills add astra-agency/ai-webmaster --skill astro-js-setup

# Install WordPress setup skill
npx skills add astra-agency/ai-webmaster --skill wp-setup
```


## Links and recommended resources

### Design UI/UX
- https://github.com/bergside/awesome-design-skills
- https://www.skills.sh/google-labs-code/stitch-skills/design-md
- https://www.skills.sh/anthropics/skills/frontend-design
- https://getdesign.md/
- https://www.tasteskill.dev/
- https://github.com/nextlevelbuilder/ui-ux-pro-max-skill

## Why these skills are needed

Modern AI assistants write code well, but often:
- Use outdated practices (jQuery, inline styles, old-school SEO)
- Ignore Core Web Vitals and performance
- Create weak semantic HTML and poor accessibility
- Suggest insecure solutions
- Don't understand the specifics of different tech stacks (Next.js, Astro, WordPress, vanilla HTML, etc.)

This project is especially aimed at open source-first workflows, where agents need to understand both the tools themselves and the conventions around integrating them into real developer environments.

**AI Webmaster Skills** solve these problems by giving agents up-to-date, proven procedures and checklists.

## Available Skills

- **dot-agents-setup:** **Sets up portable .agents protocol structure, migration, and layered config**
- **astro-js-setup:** **Installs Astro in `astro/` by default and configures the Astro Docs MCP server for AI-assisted development**
- **wp-setup:** **Sets up a modern WordPress workflow with `wordpress/` as default app root for AI-assisted CMS development**
- **design-md-setup:** **Sets up or retrofits DESIGN.md workflows using @google/design.md (lint, diff, export, spec)**
- **marketing-md-setup:** **Sets up or retrofits MARKETING.md Marketing-as-Code workflows using core + companion architecture**
- **infrastructure-md-setup:** **Sets up or retrofits INFRASTRUCTURE.md workflows for Infrastructure-as-Code guidance and guardrails**
- **wiki-llm-setup:** **Sets up or retrofits an LLM Wiki workflow with all assets inside `wiki/` (`wiki/raw`, index/log, derived pages)**
- **rfc:** **Creates RFC (Request for Comments) documents from scratch or from rough notes, using the project's RFC template. Supports RFP (Request for Proposals) generation for external contractors.**
- **balance-lens:** **Provides tools and workflows for evaluating and balancing different aspects of a project, such as performance, accessibility, and maintainability.**

---



## Multi-Repo Setup In One Repository

You can keep all project components in a single repository and still use these skills cleanly.

Recommended top-level layout:

```text
.
├── astro/
├── wordpress/
├── wiki/
└── skills/ (optional local custom skills)
```

How it maps to setup skills:

- `astro-js-setup` -> scaffolds and maintains the Astro app in `astro/`.
- `wp-setup` -> scaffolds and maintains WordPress runtime in `wordpress/`.
- `wiki-llm-setup` -> keeps LLM knowledge assets inside `wiki/` (including `wiki/raw/`, `wiki/index.md`, `wiki/log.md`).

Why this works well:

- one repository for product code, CMS layer, and AI knowledge base;
- independent app roots reduce accidental config mixing;
- shared CI/CD, issues, and docs in one place;
- easier onboarding for teams that use both Astro and WordPress.

Suggested workflow:

1. Run Astro setup and point it to `astro/`.
2. Run WordPress setup and point it to `wordpress/`.
3. Run Wiki setup and point it to `wiki/`.
4. Keep root-level agent configs (`.github/skills`, `.codex`, `.claude`, `.cursor`) shared for the whole repository.

