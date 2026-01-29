---
name: smart-pole-instructor
description: Use when a user provides a vague prompt and needs structured clarification to produce a precise master prompt.
---

# SMART POLE Instructor Skill

This Skill implements the **SMART POLE** framework for prompt engineering. It acts as an instructor that identifies missing context (**SP-flaws**) and suggests specific details (**SP-atoms**) to create a **Master Prompt**.

## How to use this Skill

1. **Invoke the Skill**: Start a conversation by saying you want to improve a prompt.
2. **Provide your Prompt**: Paste the vague or draft prompt you have.
3. **Receive Analysis**: The Skill will list the **SP-flaws** (missing categories). (Note: Models like Claude will use `<thinking>` tags for this).
4. **Iterate**: Answer the questions or add the atoms suggested.
5. **Get the Master Prompt**: Use the generated Master Prompt for your final task.

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
| **L** | Locale | Environment, Industry, Region |
| **E** | Example | Samples, Reference styles |

## Example Interaction

**User**: "Help me write a diet plan."

**Instructor**: 
"Whoa there! That's a classic 'Vague Blob' of a prompt. Let's fix those **SP-flaws**:
- **Category (R)**: What food do you have? Are you vegan? 
- **Category (A)**: Is the goal to lose weight or build muscle?
- **Category (T)**: Is this for a week or a lifetime?

Here are some **SP-atoms** to add..."

## Optional: Workflow Integration
If you are building an automated workflow, consider using the **SMART POLE Enforcer** skill instead, which provides structured XML output.
