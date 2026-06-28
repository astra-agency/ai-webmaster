---
name: balance-lens
description: "Evaluate and improve the technology–aesthetics balance in web design projects. Use when reviewing UI, generating design feedback, planning layouts, choosing visual direction, or auditing the harmony between function and beauty in interfaces, sites, and digital products."
argument-hint: "[design review URL, figma link, screenshots, or description of the work to evaluate]"
---

# Balance Lens — Technology & Aesthetics in Design

## Purpose

This skill provides a structured framework for evaluating and improving the balance between **technology** (functionality, performance, code quality) and **aesthetics** (visual design, usability, emotional resonance) in web and digital design projects.

The core idea: **not a compromise, but mutual amplification.** Technology unlocks new creative possibilities for design; aesthetics makes products not just functional but pleasant, intuitive, and emotionally resonant.

## When to use

Activate this skill when the user:

- Asks to review a design, UI, or interface for balance
- Wants feedback on a website, landing page, or app
- Mentions "balance", "looks vs feels", "tech vs design"
- Is deciding between a functional approach and a visual approach
- Asks for design direction or visual language recommendations
- References responsive design, accessibility, performance alongside aesthetics
- Says the project feels "too cold/technical" or "too decorative/impractical"

## The Balance Framework

The framework evaluates designs across **6 dimensions**:

### 1. Form Follows Function

A core principle of technical aesthetics: aesthetic value grows from how well a technical task is solved. If the structure is logical, it becomes expressive by itself — no extra "decoration" needed.

**Checklist:**
- [ ] Does the visual design naturally communicate the purpose of each element?
- [ ] Can you remove decorative elements and still have a clear, usable interface?
- [ ] Do layout, hierarchy, and spacing reflect logical content structure?
- [ ] Are interactive elements self-explanatory through their design alone?

### 2. Integrated Approach

Instead of designing function first and "making it pretty" later, the designer thinks about both simultaneously, constantly checking:

**Checklist:**
- [ ] Is the visual language present from the wireframe/prototype stage, not added after?
- [ ] Do aesthetic choices support — not hinder — usability and clarity?
- [ ] Do technical constraints enrich the visual direction (e.g., performance requirements → clean minimalism)?
- [ ] Are design decisions and technical decisions made in conversation, not sequentially?

### 3. Leveraging Technology's Capabilities

Every technology has constraints but also unique creative affordances. The task is to see and use this potential.

**Checklist:**
- [ ] Are CSS Grid, container queries, or modern layout used for expressive composition, not just structure?
- [ ] Are animations, transitions, and micro-interactions meaningful — not decorative?
- [ ] Does the design use the medium's native strengths (scroll, responsive, interactive, dynamic)?
- [ ] Are technical features (dark mode, reduced motion, print styles) treated as design features?

### 4. Softening Technology

Technology can feel cold or "alien" in certain contexts. Balance is achieved through contrast and integration.

**Checklist:**
- [ ] Is there a balance of "warm" elements (typography choice, color palette, texture, imagery) with "cold" technical ones?
- [ ] Are complex technical features integrated seamlessly (invisible when not needed)?
- [ ] Is the overall tone appropriate to the context (professional, playful, minimal, cozy)?
- [ ] Are accessibility and inclusive design built in as part of the aesthetic, not bolted on?

### 5. Juxtaposition of Contrasting Elements

Balance often emerges at the intersection of opposites — handwritten calligraphy with 3D animation, craft techniques with machine precision.

**Checklist:**
- [ ] Is there intentional contrast in texture, style, or era (e.g., hand-drawn elements + digital animation)?
- [ ] Does the combination feel purposeful, not random or chaotic?
- [ ] Are contrasting elements held together by a consistent design system (grid, color, spacing)?
- [ ] Does the contrast serve the message or brand story?

### 6. Perceptual Alignment

Research shows: functionally perfect objects are perceived as more beautiful; aesthetically pleasing objects are perceived as more usable. This reciprocal effect should be intentional.

**Checklist:**
- [ ] Is the UI's aesthetic quality working to increase perceived usability?
- [ ] Is the functionality so polished it becomes part of the aesthetic experience?
- [ ] Are affordances visually clear — does the user instinctively know what's clickable?
- [ ] Does the overall experience feel coherent: the visual vibe matches the actual behavior?

## Anti-Patterns to Flag

Watch for these common balance issues and flag them explicitly:

| Anti-Pattern | How It Looks | Suggested Fix |
|---|---|---|
| **Overload** | Too many visual effects OR too many technical controls | Strip to essentials; use progressive disclosure |
| **Decoration for decoration's sake** | Icons, gradients, animations with no functional purpose | Remove or make functional (e.g., animation as feedback) |
| **Context mismatch** | Industrial/cold design in a warm context (spa, kid's app) | Adjust palette, typography, imagery to match context |
| **Tech-first design** | Looks like an admin panel, functional but no soul | Add typographic rhythm, whitespace, color hierarchy |
| **Design-first neglect** | Beautiful mockup that's impossible to implement performantly | Check feasibility early; simplify animations; use platform-native patterns |
| **Uniformity trap** | Everything looks the same — no hierarchy, no emphasis | Establish clear visual hierarchy: size, weight, spacing, color |

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

## Principles

1. **Technology and aesthetics amplify each other** — the goal is not compromise, but synergy
2. **Context is everything** — what works for a dashboard doesn't work for a spa website
3. **Be specific, not vague** — instead of "make it prettier", say "add vertical rhythm and reduce visual noise"
4. **Function creates beauty** — a logical, well-engineered solution is inherently aesthetic
5. **Beauty creates function** — an attractive interface is perceived as more usable and trustworthy

## Usage Examples

### Example 1: Landing page review

> **User:** "Review my saas landing page at example.com"
> **You:** Run the framework in chat, or systematically evaluate and output a structured review.

### Example 2: Visual direction exploration

> **User:** "I'm building a meditation app. Should I go warm/illustrative or clean/minimal?"
> **You:** Use the framework to explore how each direction scores on the 6 dimensions given the context (audience, platform, brand).

### Example 3: Design audit

> **User:** "Something feels off about our dashboard. It's functional but nobody likes using it."
> **You:** Run through all 6 dimensions focusing on the perceptual alignment (#6) and softening technology (#4) dimensions.

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

## Integration with Other Skills

- **web-design-patterns** — after balance review, use design patterns to implement specific fixes
- **copywriting/chief-editor** — ensure tone of voice (TOV) matches visual direction
- **page-cro** — check if balance changes affect conversion (CRO vs aesthetics trade-off)
- **seo-audit** — check technical SEO after visual changes