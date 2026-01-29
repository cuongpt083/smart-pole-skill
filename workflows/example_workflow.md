# Example: SMART POLE Integrated Workflow

This workflow demonstrates how to use the SMART POLE Skill as a gatekeeper for a coding task.

## Workflow Steps

1.  **Requirement Gathering (SMART POLE Enforcer)**
    *   **Agent**: SMART POLE Enforcer.
    *   **Input**: User's initial (potentially vague) request.
    *   **Task**: Interact with the user to identify `SP-flaws` and collect `SP-atoms`.
    *   **Exit Condition**: Agent outputs a `<master_prompt>` XML block.

2.  **Context Extraction**
    *   **System Action**: Parse the XML output from Step 1.
    *   **Variable**: Set `$OPTIMIZED_PROMPT` = content of `<master_prompt>`.

3.  **Execution (VIBE Coding)**
    *   **Agent**: Senior Developer / VIBE Coder.
    *   **Input**: `$OPTIMIZED_PROMPT`.
    *   **Task**: Implement the code based on the highly detailed, structured requirements provided by the SMART POLE Enforcer.

## Why this works?
By forcing the "Execution Agent" to wait for the "SMART POLE Enforcer," we ensure that no code is written until the **Aim**, **Constraints**, **Stack**, and **Audience** are perfectly defined. This eliminates the "Garbage In, Garbage Out" problem common in AI workflows.
