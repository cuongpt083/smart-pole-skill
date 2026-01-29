---
name: smart-pole-enforcer
description: Use when building agentic workflows that require strict SMART POLE validation and machine-readable XML output.
---

# SMART POLE Enforcer Skill

This "Enforcer" version of the SMART POLE Skill is designed for **Agentic Workflows**. It acts as a mandatory gatekeeper that will not release control until the requirements are perfectly defined.

## Key Differences
- **Output**: Terminates with a `<master_prompt>` XML block for automated parsing.
- **Workflow**: Designed to be Step 1 in an agentic chain.
- **Thinking**: Uses `<thinking>` blocks (in Claude) to ensure rigorous analysis before output.

## How to use this Skill
1. **Configure**: Set this skill as the entry point for your agent.
2. **Execute**: The agent will interview the user.
3. **Capture**: Watch for the XML block to trigger the next step.

## The 9 Categories
| Abbrev | Category | Focus |
| --- | --- | --- |
| **S** | Style | Tone, Persona, Format |
| **M** | Mastery | Expertise level |
| **A** | Aim | Goal and Success criteria |
| **R** | Resource | Tools, Constraints, Budget |
| **T** | Time | Era, Deadlines, Duration |
| **P** | People | Audience, Values, Preferences |
| **O** | Outline | Structure, Scope |
| **L** | Locale | Industry, Region |
| **E** | Example | Samples, Reference styles |
