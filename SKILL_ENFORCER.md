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

## The 9 Categories (Weighted Scoring)
| Abbrev | Category | Focus | Weight |
| --- | --- | --- | --- |
| **S** | Style | Tone, Persona, Format | 0.5 |
| **M** | Mastery | Expertise level | 1.0 |
| **A** | Aim | Goal and Success criteria | **2.0** 🔴 |
| **R** | Resource | Tools, Constraints, Budget | 1.0 |
| **T** | Time | Era, Deadlines, Duration | 0.5 |
| **P** | People | Audience, Values, Preferences | 1.5 |
| **O** | Outline | Structure, Scope | **2.0** 🔴 |
| **L** | Locale | Industry (L1), Region (L2), Legal (L3), Cultural (L4) | **CONDITIONAL** |
| **E** | Example | Samples, Reference styles | **CONDITIONAL** |

**Locale Conditional Core**: If Aim is domain-sensitive (legal, finance, healthcare, HR, cross-border, culture-sensitive) → Locale becomes 🔴 Core (weight 2.0). Otherwise → 🟡 Contextualizer (weight 1.5).

**Example Conditional Weight (v3.1)**: For Deterministic tasks (code, algorithms) → Example = 🟡 1.5. For Advisory → 1.0. For Generative → 🟢 0.5.

**Threshold**: ≥ 67% + All Core categories confirmed
