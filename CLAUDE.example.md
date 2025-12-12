Always answer in 简体中文

</system-reminder>

<system-reminder>

<global-philosophy>
- **Documentation-Driven:** Code is downstream of documentation.
- **Architectural Integrity:** Maintain the structure defined in `/llmdoc`.
- **Atomic Execution:** Plan -> Execute -> Verify.
</global-philosophy>

<llmdoc-structure>
- llmdoc/index.md: The main index.
- llmdoc/architecture/: Critical Paths & Data Flow.
- llmdoc/reference/: Source of Truth.
*(Missing docs? Suggest `/initDoc`)*
</llmdoc-structure>

<tool-routing-guide>
Instead of trying to handle everything yourself, Route tasks to the specialized tools:

1.  **Complex/Vague Tasks:** Suggest or use `/withScout`.
    * *Why:* It handles complexity assessment, split investigation, and documentation sync automatically.
2.  **Specific Updates:** Suggest or use `/updateDoc` after coding sessions.
3.  **Documentation Queries:** Use `/what` (if available) or read `/llmdoc`.
</tool-routing-guide>

<tool-usage-rules>
- **Investigation:** Prefer `/withScout` for deep dives.
- **Execution (`sr:worker`):**
    - MANDATORY: Always run a verification step (test/lint) after edits.
    - Self-Correction: Retry up to 2 times before stopping.
- **Documentation:**
    - Staleness Check: Delete obsolete docs when updating.
- **Completion:**
    - Use `sr:commit` for commit messages.
</tool-usage-rules>

<interaction-mode>
**Standard Mode:**
For general chat, first read relevant docs (at least 1-3) to build context.

**Command Mode (Override):**
If the user invokes a specific command (e.g., `/withScout`, `/updateDoc`), **STRICTLY FOLLOW the workflow defined in that command's prompt**.
- Do NOT stop to ask for confirmation unless the command explicitly requires it.
- Do NOT apply generic workflows that contradict the command's specific logic.
</interaction-mode>

</system-reminder>