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
| **webmaster-router**    | Main router: detects site type and routes to the appropriate skills |
| **dot-agents-setup**    | Sets up portable .agents protocol structure, migration, and layered config |
| **site-triage**         | Automatically detects the tech stack (Next.js, Astro, WP, Vite, Webflow, etc.) |
| **html-css-js**         | Modern HTML, CSS (including Tailwind, CSS Modules), JavaScript/TypeScript best practices |
| **seo**                 | On-page SEO, technical SEO, Schema.org, Core Web Vitals, indexing |
| **performance**         | Speed optimization, images, bundle analysis, Lighthouse |
| **deployment**          | Vercel, Netlify, Cloudflare Pages, Docker, CI/CD |
| **security**            | Security headers, CSP, HTTPS, form protection, vulnerability scanning |
| **analytics**           | GA4, GTM, privacy-first analytics, consent management |
| **wordpress**           | (Optional) Specifics for WordPress sites |
| **nextjs** / **astro**  | Specialized skills for popular frameworks |

---

## Installation

### Fastest way (recommended)

```bash
# List all available skills
npx skills add astra-agency/ai-webmaster --list

# Install a specific skill
npx skills add astra-agency/ai-webmaster --skill dot-agents-setup

# Install multiple skills
npx skills add astra-agency/ai-webmaster --skill webmaster-router dot-agents-setup site-triage seo performance
```