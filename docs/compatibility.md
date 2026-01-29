# Compatibility Guide: Loading SMART POLE Skills

This guide explains how to load the SMART POLE skills into different AI coding and chat tools.

## 1. ChatGPT Codex (Custom GPTs / Instructions)
ChatGPT works best when the system prompt is pasted into the "Custom Instructions" or used to create a "Custom GPT".

- **Step 1**: Copy the content of `prompts/system_prompt.md`.
- **Step 2**: Go to **ChatGPT > Customize ChatGPT > How would you like ChatGPT to respond?**
- **Step 3**: Paste the prompt there.
- **Tip**: If using for workflows, use `prompts/system_prompt_enforcer.md` instead.

## 2. Claude Code
Claude Code (and Claude.ai) has excellent support for structured thinking.

- **Manual Loading**: Paste the system prompt at the start of your session.
- **Project Context**: If using Claude Code in a terminal, you can add the `SKILL.md` or `prompts/system_prompt.md` to your project's `.claudecode/custom_instructions.md` (if supported by your version) or simply reference it.
- **Feature**: If `<thinking>` tags are supported, Claude will show a "Chain of Thought" view. Otherwise, the analysis is internal.

## 3. OpenCode / General LLMs
For OpenCode or any other model (Llama 3, DeepSeek, etc.):

- **System Role**: If the interface allows setting a "System Role/Prompt," use the content of `prompts/system_prompt.md` (Instructor) or `prompts/system_prompt_enforcer.md` (Enforcer).
- **Few-Shot**: These models benefit greatly from the **Example (E)** category in the SMART POLE framework. Ensure you provide a concrete example if the model seems to struggle with the persona.

## 4. Summary of Tags
| Tag | Purpose | Tool Support |
| --- | --- | --- |
| `<thinking>` | Internal analysis/Chain of Thought | Optional; only if supported. |
| `<master_prompt>` | Final optimized output | Used for machine parsing & extraction. |
