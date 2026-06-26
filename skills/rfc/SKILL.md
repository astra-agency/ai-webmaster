---
name: rfc
description: "Create RFC (Request for Comments) documents from scratch or from rough notes using the project's RFC template. Supports RFP (Request for Proposals) generation for external contractors. Use when drafting RFCs, converting notes to RFC structure, preparing RFPs, or writing architecture proposals."
argument-hint: "[idea or link to notes for the RFC]"
---

# RFC — Create RFC documents using the embedded project template

## Purpose

This skill helps create RFC documents according to the project's RFC process. It can:

- Generate RFCs from scratch using the standard template sections
- Convert rough notes, roadmaps, discussions, and chat threads into structured RFC documents
- Create RFPs (Requests for Proposals) — an RFC variant adapted for external contractors and commercial bids

## RFP vs RFC

**RFP** (Request for Proposals) is an RFC adapted for external contractors. It may also be called **SoW** (Statement of Work) or **Specification**.

| Aspect                  | RFC                                      | RFP                                      |
| ----------------------- | ---------------------------------------- | ---------------------------------------- |
| **Audience**            | Internal — team, stakeholders            | External — potential contractors         |
| **Purpose**             | Align on key decisions                   | Collect commercial proposals             |
| **Confidentiality**     | Internal document                        | May carry NDA restrictions               |

### Acceptance criteria — mandatory section

In RFPs (and RFCs), **acceptance criteria** are the key component. This section is **mandatory** and must be in the **top 5** sections of the document (typically right after the requirements and before the commercial proposal).

Acceptance criteria must include:

- **Functional** — which requirements must be met (cross-referenced to the requirements section)
- **Non-functional** — performance, security, scalability
- **Deliverable format** — what is handed over (code, documentation, reports, demo)
- **Timeline and milestones** — checkpoints and acceptance conditions per stage
- **Acceptance procedure** — how verification is done (tests, demo, audit, UAT)

## When to use

Activate this skill when the user:

- Asks "write an RFC", "create an RFC", "draft an RFC"
- Wants to turn an idea or notes into an RFC document
- Mentions "proposal", "architecture decision", "breaking change"
- References the RFC process or template from the project's `rfc-approach.md`
- Asks for "RFP", "Statement of Work", "specification", "request for proposals"
- Wants to prepare a document for external contractors

## Workflow

### Step 1. Gather context

Understand the context. Ask clarifying questions if needed.

### Step 2. Determine scope

Ask the user (if not explicitly stated):

- **Short title** for the RFC (becomes the folder name and heading)
- **Source of the idea**: from scratch, from a roadmap, from a discussion
- **Key participants**: author, responsible parties (delivery lead, discovery lead, coordination lead), development team, stakeholders

### Step 3. Choose template level and create the RFC

The primary template (Full RFC) is embedded below. For **WWH** (What-Why-How) or **Minimal** RFCs, fill in the corresponding sections directly.

1. Create folder `rfc/<short-name>/`
2. For **WWH** (What-Why-How) or **Minimal** — fill directly using the relevant sections from the embedded template
3. For **Full** — copy or fill the embedded template below

### Step 4. Naming and placement

- RFC folder: `rfc/<short-name>/`
- RFC file: `rfc/<short-name>/rfc.md`
- Diagrams and images go in the same folder
- Folder name: kebab-case, in English, reflects the topic (e.g., `account-for-investors`)

**RFP in the same tree:** RFP files live alongside RFCs — `rfp/<short-name>/rfp.md`. Contractor proposals are collected in `rfp/<short-name>/offers/`, one file per vendor (e.g., `offers/vendor-a.md`, `offers/vendor-b.md`).

### Step 5. Create an RFP (if needed)

If the user asks for RFP / Statement of Work / Specification:

1. Create the RFP alongside the RFC in a subfolder: `rfp/<short-name>/rfp.md`
2. Copy the RFC structure but adapt the content:
   - **Context** — strip internal details, keep the business problem
   - **Requirements** — detail functional + non-functional specs
   - **Acceptance criteria** — **mandatory section in the top 5** (see above)
   - **Commercial proposal** — new section: format, what to include (cost, timeline, team, experience)
   - **Submission deadline** — due date, response format, contacts
3. Add a confidentiality notice (NDA if needed)
4. Remove internal sections: team risks, rollback plan, metrics
5. Create a subfolder `rfp/<short-name>/offers/` for contractor proposals

Note: RFP is the technical code-level name. The document itself is usually called **Statement of Work**, **Specification**, or **Technical Specification** depending on context.

## Principles

1. **Follow the template** — use Full / WWH / Minimal depending on scope
2. **Be specific** — avoid vague language, base statements on facts and data from the roadmap or notes
3. **If information is missing** — note it in the "Open Questions" section, do not invent

## Embedded Full RFC Template

Below is the complete Full RFC template. Use it when the RFC scope requires a thorough document covering all aspects of the proposal.

```markdown
## RFC: [short title]

### Introduction

[1-3 sentences: summary of the problem and the proposed recommendation. What are we doing?]

### Goals & Motivation

[Why are we making this change, what problem are we solving, what value does it bring? What's the desired outcome? Why now? Why does it matter?]

### Components & Design

[How do we plan to proceed, scope, constraints? Key decisions.]

#### Use Cases

- [Use case 1: who, what action, what expected result]
- [Use case 2: who, what action, what expected result]

#### Functional Requirements

- [Requirement 1]
- [Requirement 2]

#### Non-Functional Requirements

- [Performance, security, scalability]

#### Technical & Architecture Details

- [Architecture decisions, technologies, integrations]

### Acceptance Criteria

[How will we know when the solution is ready]

- Criteria must be concrete, measurable, and achievable.
- Each criterion is formulated as a condition that, when met, means "done".

### Roadmap

[What steps, in what order, what dependencies and sequencing considerations]

### Optional Sections

#### Open Questions

- [Question 1: what's unclear, what needs to be resolved]
- [Question 2: what's unclear, what needs to be resolved]

#### Alternatives

If there are two or more possible solutions, describe and compare them. This helps make an informed decision and account for trade-offs.

### Solution Options

#### Option A: [name]

**Pros:**

- ...

**Cons:**

- ...

**Trade-offs:**

- ...

#### Option B: [name]

**Pros:**

- ...

**Cons:**

- ...

**Trade-offs:**

- ...

### Recommendation

[Which one we choose and why]
```