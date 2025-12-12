---
description: "Handles complex tasks via Complexity Assessment, routing to Fast Execution or Deep Investigation with mandatory documentation sync."
argument-hint: "[A complex goal or task]"
---

# /withScout

This command handles tasks by first performing a **Complexity Assessment**, then choosing the appropriate workflow, and finally ensuring the project documentation is updated.

## When to use

- **Use when:** The request is non-trivial (requires reading >1 file, understanding system logic, or making changes).
- **Suggest when:** A single agent cannot safely complete the task without prior information gathering.
- **Example (Complex):** "User: Add JWT token refresh functionality compliant with industry standards."
- **Example (Simple):** "User: Fix the typo in the login button text."

## Workflow

This command follows an **Assess → Route → Action → Document** workflow.

### Phase 1: Assess & Route

1.  **Complexity Assessment (CRITICAL):**
    * **Goal:** Immediately determine task complexity **(Low, Medium, or High)** based on the request.
    * **Decision:**
        * **If Low (Fast Track):** Proceed directly to **Phase 3 (Fast Execution)**.
        * **If Medium/High (Deep Track):** Proceed to **Phase 2 (Deep Investigation)**.

### Phase 2: Deep Investigation (For Medium/High Complexity)

1.  **Deconstruct & Plan (MANDATORY SPLIT):**
    * **NO SINGLE THREAD:** You MUST NOT assign all work to a single investigator.
    * **Split Strategy:** You must split the investigation into at least two distinct dimensions:
        * **Dimension A (Internal):** Project structure, existing logic, file relationships.
        * **Dimension B (External/Concept):** Third-party library usage, official docs, industry best practices for the feature, security patterns.
    * *Example:* "Investigator 1: Map current Auth flow." + "Investigator 2: Search web for best practices on JWT rotation."

2.  **Parallel Investigation:**
    * Use the `Task` tool to launch `investigator` agents for Dimension A and Dimension B **simultaneously**.
    * **Constraint:** Each investigator's report **MUST** include the structured `<ExecutionPlan>` tag.

3.  **Synthesize & Evaluate:**
    * Merge reports from all investigators.
    * Combine "External Best Practices" with "Internal Code Reality" to form the final plan.

4.  **Iterate or Execute:**
    * **Insufficient Info:** Formulate new questions and repeat Step 2.
    * **Sufficient Info:** Proceed to **Phase 3 (Deep Execution)**.

### Phase 3: Execution (Adaptive)

* **Scenario A: Fast Execution (Low Complexity)**
    * The `worker` agent executes the task based on a brief self-generated plan.
    * **Validation:** Worker MUST run basic checks (lint/syntax) after modification.

* **Scenario B: Deep Execution (Medium/High Complexity)**
    * The `worker` agent executes the task based on the comprehensive `<ExecutionPlan>` from Phase 2.
    * **Validation:** Worker MUST run verification (tests/types) after modification.

### Phase 4: Documentation & Closure (MANDATORY)

1.  **Synthesize to `/llmdoc`:**
    * Review the **changes made** in Phase 3 and the **findings** in `.scout-reports`.
    * **Decision:** Does this task introduce new concepts, change APIs, or update architecture?
        * **Yes:** You MUST update the relevant files in `/llmdoc` (or create new ones). **Extract** the permanent value from the temporary `.scout-reports` and consolidate it into the permanent documentation.
        * **No:** Explicitly state "No architectural documentation update required."

2.  **Final Report:**
    * Deliver the result, summarizing the complexity, investigation insights, actions taken, and **documentation updates**.