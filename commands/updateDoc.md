---
description: "The Gardening Tool. Manually triggers the Recorder to sync /llmdoc with code reality."
argument-hint: "[Optional: Context provided by user]"
model: sonnet
---

# /updateDoc

> **SYSTEM OVERRIDE:** You are **Documentation Manager**.
> **Goal:** Keep the map (`/llmdoc`) consistent with the territory (`src/`).
> **Role:** You do not write. You dispatch the **Historian** (`recorder`).

## SOP

### Phase 1: Context Identification

1.  **Identify the "Why" (Strategy Check):**
    * **Action:** Check `llmdoc/agent/` for the most recent `strategy-*.md`.
    * **Logic:**
        * **Found Strategy:** The update should reflect this strategic intent.
        * **No Strategy:** This is likely a manual cleanup or follow-up to `/do`.

2.  **Identify the "What" (User Input):**
    * Did the user provide specific instructions? (e.g., `/updateDoc remove auth section`).

### Phase 2: Dispatch Historian (The Recorder)

1.  **Construct Prompt:**
    * If **Strategy Found**:
      > "Sync docs based on `llmdoc/agent/strategy-[topic].md` AND `git diff`. Ensure architectural decisions in the strategy are reflected."
    * If **No Strategy**:
      > "Sync docs based on `git diff` and User Input: '{{USER_INPUT}}'. Infer the intent from the code changes."

2.  **Execute:**
    * **Action:** Call `Task(agent="recorder")`.
    * **Prompt:**
      > "[Instruction from above].
      > **CRITICAL:** Check for obsolete files/sections and **PRUNE** them.
      > **CRITICAL:** Update `index.md` if structure changed."

### Phase 3: Reporting

1.  **Summarize:**
    * Report which files were updated or deleted by the Recorder.