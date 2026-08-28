
---

## `docs/ai-assisted-workflow.md`

Aquí sí quiero que seas un poco más específica. **Este documento puede ser particularmente valioso para esa vacante**, porque ellos explícitamente trabajan con IA + Playwright y quieren alguien que no confíe ciegamente en la IA.

```markdown
# AI-Assisted Quality Engineering Workflow

## Purpose

This document defines how AI is used within the Quality Engineering Lab
to support testing, analysis, automation, documentation, and learning.

The objective is not to replace QA judgment with AI-generated output, but
to use AI to increase productivity while maintaining human ownership of
quality decisions.

---

## Core Principle

> **AI-generated output is a proposal, not evidence.**

AI can generate test cases, suggest assertions, identify potential risks,
write automation code, or analyze requirements.

However, generated output may contain:

- Incorrect assumptions
- Missing edge cases
- Invalid assertions
- Incorrect technical implementations
- Misinterpretations of business rules
- False confidence
- Outdated or incomplete information

Therefore, AI output must be reviewed and validated before being used as
part of the testing process.

---

## Human-in-the-Loop Workflow

```mermaid
flowchart TD
    A[Requirement / Context]
    B[AI Assistance]
    C[QA Review]
    D[Challenge Assumptions]
    E[Execute / Validate]
    F[Collect Evidence]
    G[Quality Decision]

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G
