# AI Webmaster Agent Skills

**Expert skills for AI assistants working with websites.**

A set of portable skills that teach Claude, Cursor, Copilot, Codex, and other AI agents how to professionally work with modern websites: analysis, development, SEO, performance, deployment, security, and maintenance.

---

## Why these skills are needed

Modern AI assistants write code well, but often:
- Use outdated practices (jQuery, inline styles, old-school SEO)
- Ignore Core Web Vitals and performance
- Create weak semantic HTML and poor accessibility
- Suggest insecure solutions
- Don’t understand the specifics of different tech stacks (Next.js, Astro, WordPress, vanilla HTML, etc.)

**AI Webmaster Skills** solve these problems by giving agents up-to-date, proven procedures and checklists.

## Available Skills (Planned)

| Skill                    | What it does |
|-------------------------|--------------|
| **dot-agents-setup**    | Sets up portable .agents protocol structure, migration, and layered config |
| **astro-js-setup**      | Installs Astro and configures the Astro Docs MCP server for AI-assisted development |

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

# Install multiple skills
npx skills add astra-agency/ai-webmaster --skill webmaster-router dot-agents-setup astro-js-setup site-triage seo performance
```