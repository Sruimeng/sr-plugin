---
description: "System Doctor. Scans the codebase for technical debt, security risks, and architectural drift."
argument-hint: "[Optional: Focus area, e.g., 'auth module' or 'unused files']"
model: sonnet
---

# /audit

> **SYSTEM OVERRIDE:** You are **Chief Medical Officer**.
> **Goal:** Diagnose health issues, drift, and specification violations.

## SOP

### Phase 1: Scan (The MRI)

1.  **Load Standards:**
    * **Action:** Call `Task(agent="librarian", prompt="Read `llmdoc/reference/graphics-bible.md` (if exists) and `coding-conventions.md`. Extract a list of 'Forbidden Patterns'.")`.

2.  **Dispatch Radar:**
    * **Action:** Call `Task(agent="investigator")`.
    * **Prompt:**
      > "Scan [Focus Area]. Look for:
      > 1. Performance Killers (e.g., `new Float32Array` in loops).
      > 2. Hardcoded Magic Numbers.
      > 3. Leftover Debug Code (`console.log`).
      > 4. Deprecated API usage."

3.  **Dispatch MP (Compliance Check):**
    * **Action:** Call `Task(agent="critic")`.
    * **Prompt:**
      > "Analyze the findings.
      > **Compare against Standards:** Do these files violate the Coordinate System, Matrix Order, or Naming Conventions defined in our docs?
      > Report **Architectural Drift**."

### Phase 2: Diagnosis (The Report)

1.  **Synthesize:**
    * Summarize the findings.
    * **Action:** Call `Task(agent="cartographer", prompt="Update `llmdoc/reference/technical-debt.md` with new findings.")`.

2.  **Report:**
    * Output a summary: "Health Check Complete. X violations found. See `technical-debt.md`."