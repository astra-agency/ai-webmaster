---
name: balance-lens
description: "Evaluate and improve the technology–aesthetics balance in web design projects. Use when reviewing UI, generating design feedback, planning layouts, choosing visual direction, or auditing the harmony between function and beauty in interfaces, sites, and digital products."
argument-hint: "[design review URL, figma link, screenshots, or description of the work to evaluate]"
---

# Balance Lens — Technology & Aesthetics in Design

## Purpose

This skill provides a structured framework for evaluating and improving the balance between **technology** (functionality, performance, code quality) and **aesthetics** (visual design, usability, emotional resonance) in web and digital design projects.

The core idea: **not a compromise, but mutual amplification.** Technology unlocks new creative possibilities for design; aesthetics makes products not just functional but pleasant, intuitive, and emotionally resonant.

The concept sits at the intersection of several established design traditions: **technical aesthetics** (where engineering logic becomes expressive), **functional beauty** (where utility creates elegance), and **emotional design** (where positive aesthetics improve perceived usability).

## When to use

Activate this skill when the user:

- Asks to review a design, UI, or interface for balance
- Wants feedback on a website, landing page, or app
- Mentions "balance", "looks vs feels", "tech vs design"
- Is deciding between a functional approach and a visual approach
- Asks for design direction or visual language recommendations
- References responsive design, accessibility, performance alongside aesthetics
- Says the project feels "too cold/technical" or "too decorative/impractical"
- Is evaluating a design system, component library, or brand guidelines
- Wants to integrate with or build on top of aesthetic UI skills (TypeUI, frontend-design, etc.)

## The Balance Framework

The framework evaluates designs across **6 dimensions**. Each dimension maps to a core principle and a concrete checklist.

---

### 1. Form Follows Function

> *"Good design makes a product useful. Good design is aesthetic."* — Dieter Rams

A core principle of technical aesthetics: aesthetic value grows from how well a technical task is solved. If the structure is logical, it becomes expressive by itself — no extra "decoration" needed.

**Checklist:**
- [ ] Does the visual design naturally communicate the purpose of each element?
- [ ] Can you remove decorative elements and still have a clear, usable interface?
- [ ] Do layout, hierarchy, and spacing reflect logical content structure?
- [ ] Are interactive elements self-explanatory through their design alone?

**Related principle (Dieter Rams #4):** *Good design makes a product understandable* — the design clarifies the product's structure and function without an instruction manual.

---

### 2. Integrated Approach

Instead of designing function first and "making it pretty" later, the designer thinks about both simultaneously, constantly checking the feedback loop.

**Checklist:**
- [ ] Is the visual language present from the wireframe/prototype stage, not added after?
- [ ] Do aesthetic choices support — not hinder — usability and clarity?
- [ ] Do technical constraints enrich the visual direction (e.g., performance requirements lead to clean minimalism)?
- [ ] Are design decisions and technical decisions made in conversation, not sequentially?

**Reference:** Don Norman's *Emotional Design* framework — the **behavioral level** (usability, efficiency, error rates) and **visceral level** (look, feel, tone) should be designed together, not sequentially.

---

### 3. Leveraging Technology's Capabilities

Every technology has constraints but also unique creative affordances. The task is to see and use this potential.

**Checklist:**
- [ ] Are CSS Grid, container queries, or modern layout used for expressive composition, not just structure?
- [ ] Are animations, transitions, and micro-interactions meaningful — not decorative?
- [ ] Does the design use the medium's native strengths (scroll, responsive, interactive, dynamic)?
- [ ] Are technical features (dark mode, reduced motion, print styles) treated as design features?

**Reference:** The Centre Pompidou (Paris) — exposed structural systems and services (escalators, pipes) become the visual aesthetic. In web terms: making layout systems, responsive behaviors, and interaction patterns visible rather than hiding them.

---

### 4. Softening Technology

Technology can feel cold or "alien" in certain contexts. Balance is achieved through contrast, warmth, and seamless integration.

**Checklist:**
- [ ] Is there a balance of "warm" elements (typography, color palette, texture, imagery) with "cold" technical ones?
- [ ] Are complex technical features integrated seamlessly (invisible when not needed)?
- [ ] Is the overall tone appropriate to the context (professional, playful, minimal, cozy)?
- [ ] Are accessibility and inclusive design built in as part of the aesthetic, not bolted on?

**Reference:** Norman's **reflective level** — how a product fits into someone's identity and life. Warmth is often achieved through thoughtful reflective design (microcopy, brand personality, meaningful details), not just visual decoration.

---

### 5. Juxtaposition of Contrasting Elements

Balance often emerges at the intersection of opposites — handwritten calligraphy with 3D animation, craft techniques with machine precision.

**Checklist:**
- [ ] Is there intentional contrast in texture, style, or era (hand-drawn + digital, brutalist + soft)?
- [ ] Does the combination feel purposeful, not random or chaotic?
- [ ] Are contrasting elements held together by a consistent design system (grid, color, spacing)?
- [ ] Does the contrast serve the message or brand story?

**Examples in practice:**
- **Neubrutalism** — stark grids and system fonts + playful colors and rounded details
- **Cute-alism** — brutalist blocks + kawaii-inspired visuals
- **Brutalist + minimalist hybrids** — start from a minimalist base (clear hierarchy, reduced elements), selectively add brutalist traits (stark grids, system fonts) where they reinforce the brand story

---

### 6. Perceptual Alignment / Aesthetic-Usability Effect

> *"Attractive things work better."* — Don Norman

Research shows: functionally perfect objects are perceived as more beautiful; aesthetically pleasing objects are perceived as more usable. This reciprocal effect should be intentional, not accidental.

The **aesthetic-usability effect** (Kurosu & Kashimura, 1995) demonstrated that perceived ease of use correlates more strongly with aesthetics than with actual usability. Users "believe that things that look better will work better."

**Checklist:**
- [ ] Is the UI's aesthetic quality working to increase perceived usability?
- [ ] Is the functionality so polished it becomes part of the aesthetic experience?
- [ ] Are affordances visually clear — does the user instinctively know what's clickable?
- [ ] Does the overall experience feel coherent: the visual vibe matches the actual behavior?

**⚠️ Risk:** The aesthetic-usability effect can *mask* genuine usability problems in testing. Users may say a beautiful interface is "easy to use" even when objective metrics show otherwise. Always validate with task performance data, not just opinions.

---

## Anti-Patterns to Flag

Watch for these common balance issues and flag them explicitly:

| Anti-Pattern | How It Looks | Suggested Fix |
|---|---|---|
| **Overload** | Too many visual effects (animations, gradients) OR too many technical controls (switches, options) | Strip to essentials; use progressive disclosure |
| **Decoration for decoration's sake** | Icons, gradients, animations with no functional purpose | Remove or make functional (e.g., animation as feedback, icon as affordance) |
| **Context mismatch** | Industrial/cold design in a warm context (spa, meditation app, kid's app) | Adjust palette, typography, imagery to match context |
| **Tech-first design** | Looks like an admin panel — functional but no soul | Add typographic rhythm, whitespace, color hierarchy, micro-interactions |
| **Design-first neglect** | Beautiful mockup that's impossible to implement performantly | Check feasibility early; simplify animations; use platform-native patterns |
| **Uniformity trap** | Everything looks the same — no hierarchy, no emphasis | Establish clear visual hierarchy: size, weight, spacing, color |
| **Polished dysfunction** | Beautiful UI that hides poor navigation or weak information scent | Run usability testing; measure task success alongside visual satisfaction |
| **AI-slop uniformity** | Inter/Roboto/Arial fonts, purple gradients on white, generic component libraries, cookie-cutter layouts | Adopt distinct visual tone before writing code; use CSS custom properties for a custom design system |

---

## Workflow

### Step 1: Gather context

Ask the user (if not already provided):

- **What is being reviewed?** — URL, Figma link, screenshot, description
- **Project type** — landing page, web app, e-commerce, dashboard, portfolio, blog
- **Audience** — who uses this? B2B, B2C, creative, technical, general?
- **Current stage** — wireframe, prototype, production, redesign?
- **Specific concerns** — anything they already feel is off-balance?

### Step 2: Run the framework

Evaluate the design against the **6 dimensions** above. For each dimension:

- Note what's working well
- Note what could be improved
- Score from 1 (poor) to 5 (excellent)

### Step 3: Identify anti-patterns

Scan for the anti-patterns table. Flag any that apply, with specific examples from the design.

### Step 4: Generate recommendations

For each weak dimension or flagged anti-pattern, provide:

- **Specific, actionable recommendation** — not "improve aesthetics" but "add 8px vertical rhythm and reduce font weight variation from 4 stops to 2"
- **Priority** — P0 (must fix), P1 (should fix), P2 (nice to have)
- **Trade-offs** — what this change might affect (performance, complexity, visual impact)

### Step 5: Synthesize

Write a concise summary that covers:

1. **Overall balance score** (out of 30, from 6 dimensions × 5 points)
2. **Top 3 strengths** — what's working
3. **Top 3 improvements** — highest priority changes
4. **Feeling** — how the design actually *feels* to use, in plain language

---

## Output Format

When producing a full review, structure it as:

```markdown
## Balance Lens Review: [Project Name]

### Scores

| Dimension | Score (1-5) | Notes |
|---|---|---|
| Form Follows Function | 4 | Logical layout, clear hierarchy |
| Integrated Approach | 3 | Aesthetic added after wireframes |
| Leveraging Tech | 5 | Great use of scroll animations |
| Softening Technology | 2 | Feels cold, no textures/warmth |
| Juxtaposition | 3 | Could use more intentional contrast |
| Perceptual Alignment | 4 | UI feels as good as it works |

**Total: 21/30**

### What's Working

1. [strength]
2. [strength]
3. [strength]

### Needs Improvement

| Priority | Issue | Recommendation |
|---|---|---|
| P1 | Dimension 4 (cold feel) | Add warm accent color and rounded corners |
| P1 | Dimension 2 (sequential design) | Next iteration: design visual language in wireframes |
| P2 | Dimension 5 (juxtaposition) | Try one hand-drawn illustration element |

### Anti-Patterns Detected

- **Tech-first design** — admin panel feel in a consumer app (P1)

### Summary

[2-3 sentence synthesis of how the design feels and what to prioritize]
```

---

## Principles

1. **Technology and aesthetics amplify each other** — the goal is not compromise, but synergy
2. **Context is everything** — what works for a dashboard doesn't work for a spa website
3. **Be specific, not vague** — instead of "make it prettier", say "add vertical rhythm and reduce visual noise"
4. **Function creates beauty** — a logical, well-engineered solution is inherently aesthetic
5. **Beauty creates function** — an attractive interface is perceived as more usable and trustworthy
6. **Validation must be behavioral, not just attitudinal** — the aesthetic-usability effect can mask flaws in subjective feedback

---

## Practical Cheat-Sheet: Quick Visual Rules

Use these as a quick reference when generating specific design recommendations:

### Typography
- Start with a base of ~16px for body text
- Limit to 1-2 type families (one for headings, one for body, or just one versatile family)
- Line length: ~60-75 characters
- Headings: tighter line-height (1.1-1.3), body: looser (1.5-1.7)
- Use weight contrast, not size contrast alone — pair a bold weight for headings with regular for body

### Color
- Maximum 3 base colors + 1 accent + neutrals (grays)
- Every color should have a semantic role (primary action, success, warning, error, info, neutral)
- Use HSL/CSS custom properties — allows theming, dark mode, and accessibility overrides
- Ensure WCAG 2.1 AA contrast ratio (4.5:1 for body text, 3:1 for large text)

### Spacing & Layout
- Use a consistent scale (e.g., 4px base: 4, 8, 12, 16, 24, 32, 48, 64, 96)
- Start with more whitespace than feels comfortable; tighten only where needed
- Group related elements, clearly separate unrelated ones
- Use CSS Grid for 2D layouts, Flexbox for 1D — don't fight the technology

### Motion
- Duration: 150-300ms for micro-interactions (hover, focus), 300-500ms for transitions
- Easing: use cubic-bezier, not linear — ease-out for user-initiated actions, ease-in-out for state changes
- Every animation should communicate something: feedback, attention, relationship, hierarchy
- Respect `prefers-reduced-motion`

---

## Design Systems: Balance Evaluation

When evaluating a design system (rather than a single page), adjust the framework:

| Dimension | Design System Question |
|---|---|
| Form Follows Function | Does the system make it easy to build clear, purposeful UIs? |
| Integrated Approach | Are design tokens (color, spacing, typography) co-developed with components and usage docs? |
| Leveraging Tech | Does the system use platform-native features (container queries, CSS layers, custom properties)? |
| Softening Technology | Does the system include direction on personality, microcopy, motion? |
| Juxtaposition | Does the system allow meaningful visual variation while maintaining consistency? |
| Perceptual Alignment | Do system components feel as good as they work when assembled into real UIs? |

**For brand–tech–UX alignment specifically, evaluate:**
1. **Brand axis** — design tokens reflect brand values (colors, typography, tone)
2. **UX axis** — patterns and interaction guidelines ensure coherent, intuitive flows
3. **Engineering axis** — components are versioned, accessible, performant, themable

---

## Ecosystem & Integration

### TypeUI / Aesthetic UI Skills

Balance Lens is a **meta-skill** — it evaluates *how* technology and aesthetics relate in a design. It can be used alongside:

- **TypeUI skills** (typeui.sh) — prescriptive aesthetic presets (modern, paper, brutalist, etc.). Use Balance Lens to evaluate which preset fits your context, then use TypeUI to implement it.
- **Anthropic's frontend-design skill** — bold visual tone selection + production implementation. Use Balance Lens to justify the tone choice and audit the result.
- **Aesthetic UI Design skill** — mood inference and token generation. Use Balance Lens to validate the mood-to-token mapping.

Workflow: Choose tone → Balance Lens audit → TypeUI or other skill implementation → Balance Lens re-audit.

### skills.sh Compatibility

Balance Lens follows the skills.sh SKILL.md format (frontmatter + structured markdown). It can be installed via:
```bash
npx skills add <repo-path> --skill balance-lens
```

---

## Recommended Companion Skills

These are the best-regarded design skills from the TypeUI ecosystem, Anthropic, and community registries. Use them alongside Balance Lens — let the lens audit and justify the direction, then these skills implement it.

### How to install

All TypeUI skills: `npx typeui.sh pull <slug>` (drops a SKILL.md into your project).

After installing, pass Balance Lens over the result to verify the tech–aesthetics balance.

### Core Aesthetic Presets (TypeUI Registry)

These are the most popular and battle-tested design presets from the TypeUI ecosystem. Each fills a specific visual niche.

| Skill | Slug | Best For | Balance Lens Context |
|---|---|---|---|
| **Modern** | `modern` | General web apps, SaaS, startups — clean, production-ready defaults | Strong baseline for most projects; watch for uniformity trap |
| **Minimal** | `minimal` | Content-first sites, portfolios, documentation | Pushes function-forward; excellent for Form Follows Function dimension |
| **Paper** | `paper` | Editorial, blogs, long-form content — soft off-white surfaces, warm texture | Strongest in Softening Technology dimension (warm, tactile) |
| **Neobrutalism** | `neobrutalism` | Bold, standout interfaces — hard shadows, thick borders, vivid colors | Excellent for Juxtaposition & Leveraging Tech dimensions |
| **Brutalism** | `brutalism` | Raw, high-contrast, structural honesty | Tests Form Follows Function to its extreme |
| **Refined** | `refined` | Premium, serif-forward editorial design | Balanced across all dimensions; often scores highest Perceptual Alignment |
| **Bento** | `bento` | Dashboard, grid-based layouts, metrics displays | Strong in Leveraging Tech (CSS Grid heavy) and Form Follows Function |
| **Glassmorphism** | `glassmorphism` | Creative sites, modern portfolio, futuristic UI | Pushes Leveraging Tech dimension; watch for Overload anti-pattern |

### Anthropic's Recommended Tones

Anthropic's `frontend-design` skill forces a bold, intentional tone choice. These 11 tones map to Balance Lens dimensions as follows:

| Tone | Description | Strongest Dimension | Best Context |
|---|---|---|---|
| **Brutally minimal** | Extreme reduction, maximum whitespace, minimal color | Form Follows Function (#1) | Portfolio, docs, creative studios |
| **Maximalist chaos** | Dense information, layered elements, strong patterns | Juxtaposition (#5) | Art sites, music, experimental |
| **Retro-futuristic** | Vintage shapes + modern typography, CRT/monitor vibes | Leveraging Tech (#3) | Tech brands, gaming, indie SaaS |
| **Organic / natural** | Flowing shapes, soft colors, nature-inspired textures | Softening Tech (#4) | Wellness, meditation, eco-brands |
| **Luxury / refined** | Gold accents, generous whitespace, serif typography | Perceptual Alignment (#6) | Premium products, fashion, finance |
| **Playful / toy-like** | Rounded everything, bright saturated colors, bouncy motion | Softening Tech (#4) + Juxtaposition (#5) | Kids, games, creative tools |
| **Editorial / magazine** | Large typography, hero images, columned layout | Integrated Approach (#2) | Media, blogs, publishing |
| **Brutalist / raw** | System fonts, exposed grids, no polish | Form Follows Function (#1) | Personal sites, experimental |
| **Art deco / geometric** | Symmetrical patterns, gold/black palette, sharp angles | Leveraging Tech (#3) | Cultural institutions, luxury |
| **Soft / pastel** | Muted colors, rounded corners, gentle gradients | Softening Tech (#4) | Lifestyle, health, food |
| **Industrial / utilitarian** | Monospace, dark palette, functional layout, tool-like | Form Follows Function (#1) | Dev tools, dashboards, CLI UIs |

### Situational Recommendations

| If You're Building... | Recommended Skill(s) | Why |
|---|---|---|
| SaaS dashboard | `modern` + `dashboard` | Clean, functional, data-dense; watch for Tech-first anti-pattern |
| Editorial / blog | `paper` + `editorial` + `refined` | Warm, readable, typography-forward |
| Creative portfolio | Anthropic's *Maximalist chaos* or *Brutalist/raw* | Stand out; push Juxtaposition dimension |
| E-commerce | `modern` + `bento` + `spacious` | Trust + clarity + room for product visuals |
| Dev tool / API docs | *Industrial/utilitarian* or `minimal` + `mono` | Honest, functional, fast; strong Form Follows Function |
| Wellness / meditation | *Organic/natural* or *Soft/pastel* + `paper` | Warm, calm, high Softening dimension |
| Corporate / enterprise | `corporate` + `professional` + `enterprise` | Trustworthy, consistent; watch for Uniformity trap |
| Experimental / art | *Maximalist chaos* or `artistic` + `vibrant` | Push boundaries; use Balance Lens to check usability |

### Workflow with Balance Lens

1. Use Balance Lens to evaluate the project goals and constraints (Step 1-2 of the workflow)
2. Select a companion skill from the tables above based on the context
3. Install the skill (`npx typeui.sh pull <slug>`) or prompt an agent with the Anthropic tone
4. Run Balance Lens again on the generated output to verify the technology–aesthetics balance
5. Iterate until all 6 dimensions score 3+ and no anti-patterns remain

---

## References & Further Reading

### Foundational Books

| Book | Author | Relevance |
|---|---|---|
| *The Design of Everyday Things* | Don Norman | Core principles of usability, affordances, signifiers |
| *Emotional Design* | Don Norman | 3 levels of design (visceral, behavioral, reflective); aesthetic-usability effect |
| *Refactoring UI* | Adam Wathan & Steve Schoger | Practical UI tactics for developers — hierarchy, spacing, color, typography |
| *Don't Make Me Think* | Steve Krug | Usability fundamentals for web interfaces |
| *100 Things Every Designer Needs to Know About People* | Susan Weinschenk | Perceptual psychology applied to design |
| *Universal Principles of Design* | Lidwell, Holden & Butler | 125 design principles including aesthetic-usability effect, form follows function |

### Influential Designers & Principles

- **Dieter Rams' 10 Principles of Good Design** (Braun) — the foundational statement of functional beauty
- **Charles & Ray Eames** — "Design is a plan for arranging elements in such a way as best to accomplish a particular purpose"
- **Louis Sullivan** — "Form ever follows function" (1896, the original formulation)
- **Centre Pompidou** (Renzo Piano & Richard Rogers) — exposed infrastructure as aesthetic (the original "tech as beauty" in architecture)

### Design Systems (Public References)

| System | Characteristics |
|---|---|
| **Google Material Design** | Deep, opinionated visual language with exhaustive technical specs |
| **IBM Carbon Design System** | Enterprise-grade, coded React/web components, strong accessibility |
| **Atlassian Design System** | "Simple, intuitive, beautiful" at SaaS scale |
| **Shopify Polaris** | Merchant-focused, admin-oriented with strong brand coherence |

### Web-Specific Resources

- **Refactoring UI** (refactoringui.com) — book + screencast series for developers
- **Laws of UX** (lawsofux.com) — concise summaries of design psychology principles
- **Every Layout** (every-layout.dev) — algorithmic layout techniques using CSS
- **TypeUI Design Skills** (typeui.sh) — 77+ aesthetic presets for AI agents

### Academic / Conceptual

- **Aesthetic-Usability Effect** — Kurosu & Kashimura (1995), original study on ATM interfaces
- **Technical Aesthetics** — Soviet design philosophy (1950s-80s): systematic, principle-driven design at the intersection of engineering and art
- **Bauhaus** — "Form follows function" origin in modern design education
- **High-Tech Architecture** (Centre Pompidou, Lloyd's Building) — engineering as visual expression

---

## Integration with Other Skills

- **web-design-patterns** — after balance review, implement specific fixes
- **copywriting/chief-editor** — ensure tone of voice matches visual direction
- **page-cro** — check if balance changes affect conversion (CRO vs aesthetics trade-off)
- **seo-audit** — check technical SEO after visual changes
- **design-md** — align with design.md workflows for formal design specs
- **marketing-md** — ensure visual and marketing strategies are aligned
