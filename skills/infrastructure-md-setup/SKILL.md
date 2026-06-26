---
name: infrastructure-md-setup
description: Set up or retrofit INFRASTRUCTURE.md / Infrastructure-as-Code guidance in a repository using the IaC principles, tooling, and best practices from the ddpa.ru knowledge base article. Use when the user wants a repo-level infrastructure doc, an IaC decision guide, or a practical agent workflow for infrastructure management centered on Terraform, Ansible, wp-env, and GitHub Actions.
---

# infrastructure-md-setup

Practical workflow for adopting `INFRASTRUCTURE.md` as a machine-readable infrastructure-as-code guide for AI agents.

Use this skill when a user wants to:
- create a new `INFRASTRUCTURE.md` file in a greenfield repository;
- retrofit an existing infrastructure or DevOps guide into a structured IaC document;
- standardize how agents describe, plan, and review infrastructure changes;
- capture core IaC principles, tool choices, and guardrails in one place;
- align local development, infrastructure code, and CI workflows around Terraform, Ansible, wp-env, and GitHub Actions;
- distinguish IaC from PaaS-style deployment workflows.

## Inputs Required

Before writing files or proposing repo changes, ask and confirm:

1. Target scope
- Apply to the current repository or another directory?

2. Setup mode
- `from-scratch` (new `INFRASTRUCTURE.md`) or `adapt-existing` (merge with current docs)?

3. Infrastructure scope
- Is this document for cloud infrastructure, Kubernetes platforms, server configuration, or all of the above?

4. Preferred IaC approach
- `declarative`, `imperative`, `hybrid`, or mixed by use case?

5. Tooling baseline
- Which tools are canonical today: Terraform/OpenTofu, Ansible, wp-env, GitHub Actions, Pulumi, Crossplane, Helm, CloudFormation, Packer, or platform-specific tooling?

6. Change policy
- Merge into existing files (recommended) or replace sections where safe?

If any answer is ambiguous, stop and ask a follow-up instead of guessing.

## What To Do First

1. Detect current infrastructure context.
- Check for `INFRASTRUCTURE.md`, `README.md`, `docs/`, `infra/`, `terraform/`, `modules/`, `k8s/`, `.github/workflows/`, `package.json`, and `Dockerfile`.
- Check for `.wp-env.json`, `wp-env` scripts, `ansible.cfg`, `inventory/`, `playbooks/`, and workflow files under `.github/workflows/`.
- Look for existing IaC docs, runbooks, platform notes, and cloud provider manifests.

2. Classify the current infrastructure model.
- Determine whether the repo is mostly declarative IaC, imperative automation, hybrid code-based provisioning, or application-only deployment.

3. Decide setup flow.
- No existing infrastructure doc: run `from-scratch`.
- Existing docs or runbooks: run `adapt-existing` and preserve prior intent.

4. Anchor on the article’s core concepts.
- Use declarativity, idempotency, reproducibility, controllability, policy-as-code, state management, modules, and Git-based change control as the primary framing.

## Preflight Detection

Run a quick inventory in the target repo:

```bash
pwd
rg --files -g 'INFRASTRUCTURE.md' -g 'README.md' -g 'docs/**' -g 'infra/**' -g 'terraform/**' -g 'modules/**' -g 'k8s/**' -g '.github/workflows/**' -g 'Dockerfile' -g 'docker-compose*.yml' -g 'package.json'
rg -n "Terraform|OpenTofu|Pulumi|Ansible|Crossplane|Helm|CloudFormation|Packer|GitOps|policy-as-code|drift" -g '*.md' -g '*.yml' -g '*.yaml' -g '*.tf' -g '*.ts' -g '*.py'
```

Interpretation:
- If `INFRASTRUCTURE.md` does not exist, scaffold a canonical starter.
- If `INFRASTRUCTURE.md` exists, validate and patch incrementally; do not overwrite blindly.
- If multiple IaC toolchains exist, identify the one that is actually authoritative before editing.

## Flow A: From Scratch

### Step 1: Create the base `INFRASTRUCTURE.md`

Create `INFRASTRUCTURE.md` with sections aligned to the article:
- overview of the infrastructure model;
- what IaC is and how it is used in the repo;
- key principles;
- supported approaches;
- canonical tools and where they are used;
- environment/provider matrix;
- common scenarios;
- best practices and guardrails;
- relation to PaaS or app-only deployment;
- references.

Starter skeleton:

```md
# Infrastructure as Code

## Overview
Describe the repo’s infrastructure philosophy and operational goals.

## What IaC Means Here
Explain what is managed by code, what is manual, and what is out of scope.

## Key Principles
- Declarativity
- Idempotency
- Reproducibility
- Controllability
- Policy-as-Code

## Approaches
- Declarative
- Imperative
- Hybrid

## Tooling
- Terraform / OpenTofu
- Ansible
- wp-env
- GitHub Actions

## Environments and Providers
Document clouds, clusters, and environment-specific ownership.

## Scenarios
- Greenfield environment bootstrap
- Cloud migration
- CI/CD for infrastructure
- Disaster recovery
- Compliance and audit

## Best Practices
- Everything in Git
- Modular reuse
- GitOps-style review
- Security checks
- Drift detection
- Least privilege

## IaC vs PaaS
Clarify where infrastructure code ends and hosted deployment platforms begin.

## References
Link the canonical docs and source material.
```

### Step 2: Make tool choices explicit

Document the selected toolchain by use case:
- Terraform/OpenTofu for declarative cloud infrastructure and modules;
- Ansible for imperative server orchestration;
- wp-env for reproducible local WordPress development environments;
- GitHub Actions for CI, validation, and deployment orchestration;
- Packer for machine image creation.

### Step 3: Encode the operating rules

Add rules for:
- Git-based review before apply;
- state management and drift detection;
- policy-as-code checks such as Open Policy Agent or Checkov;
- workflow gates and approvals in GitHub Actions for sensitive infrastructure changes;
- minimal privileges for runners;
- no manual production drift without explicit approval.

### Step 4: Validate

If the repository has IaC tooling, run the most relevant checks:
- `terraform fmt` / `tofu fmt` for Terraform/OpenTofu code;
- `terraform validate` / `tofu validate` for module sanity;
- `ansible-lint` for Ansible content;
- `npx wp-env start` for local WordPress environment sanity when the repo uses `wp-env`;
- `actionlint` for GitHub Actions workflow validation;
- `checkov` or equivalent for policy checks.

## Flow B: Adapt Existing Project

### Step 1: Map existing docs into the canonical structure

Typical mapping:
- runbooks and setup notes -> Overview + What IaC Means Here;
- module docs -> Tooling + Environments and Providers;
- WordPress local dev notes -> Tooling + Environments and Providers, with `wp-env` commands and scripts;
- CI/CD docs -> GitHub Actions workflow rules and validation;
- incident or DR docs -> Scenarios;
- security standards -> Best Practices + operating rules;
- hosting/platform docs -> IaC vs PaaS.

### Step 2: Merge instead of replace

When `INFRASTRUCTURE.md` already exists:
- preserve the repo’s current source of truth;
- keep existing tool names and environment names unless they are wrong;
- patch only the sections needed to improve clarity or structure.

### Step 3: Resolve conflicts deliberately

If the repo contains multiple approaches:
- choose the approach that is actually deployed;
- note secondary tools as supporting infrastructure, not the primary standard;
- ask before deleting or renaming any infrastructure directories.

## Validation Checklist

Before completion, confirm:
- `INFRASTRUCTURE.md` exists and reflects the repo’s real infrastructure model;
- the main IaC tools are named consistently, especially Terraform, Ansible, `wp-env`, and GitHub Actions;
- state, drift, and policy checks are documented;
- local WordPress workflow notes are aligned with `wp-env` if the repo uses WordPress;
- workflow validation rules are documented for GitHub Actions if CI is part of the setup;
- the IaC vs PaaS boundary is clear;
- references point to the canonical source material.

## Troubleshooting

1. Multiple IaC tools appear to conflict.
- Treat this as a documentation and ownership problem first, not a tooling problem.
- Identify the authoritative path by deployment or ownership reality.

2. State or drift behavior is undocumented.
- Add explicit rules for where state lives, who can mutate it, and how drift is checked.

3. The repo is app-only, with infrastructure handled elsewhere.
- Keep the file narrow and document only the integration boundary and responsibilities.

## References

- https://ddpa.ru/kb/it/devops/infrastructure-as-code/