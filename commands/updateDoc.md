---
description: "Synchronizes /llmdoc with recent code changes and investigation insights, acting as a documentation gardener."
argument-hint: "[Optional: specific focus area]"
model: sonnet
---

# /updateDoc

This command synchronizes the `/llmdoc` "Retrieval Map" with the latest code reality. It bridges the gap between *what* changed (code) and *why* it changed (investigation context).

## When to use

- **Use when:** Code changes have been committed, and you need to solidify the new reality into the knowledge base.
- **Suggest when:** A `worker` completes a complex task, especially one involving a `.scout-report`.

## Actions

1.  **Step 1: Context Gathering & Impact Analysis**
    - **Read Code:** Run `git diff HEAD` (or staged) to see *what* changed.
    - **Read Context (CRITICAL):** Scan the `.scout-reports/` directory for recent findings. Extract the "Key Insights" and "Relations" to understand *why* changes were made.
    - **Concept Extraction:** Identify which *Core Concepts*, *Architectural Flows*, or *APIs* were touched.
    - **Staleness Check:** Identify which existing documents are now obsolete, contradictory, or incorrect.

2.  **Step 2: Documentation Gardening (Content-Only Mode)**
    - Invoke `recorder` agents for each impacted concept.
    - **Prompt:**
      "**Task:** Sync documentation for concept **`<concept_name>`**.
      **1. Synthesize:** Combine the code diff (The Reality) with the `.scout-report` (The Rationale).
      **2. Prune & Update:** Do not just append. **Rewrite** outdated sections. If a feature was removed, **DELETE** the corresponding documentation.
      **3. Format:** Strictly follow the `<ContentFormat_...>` structures.
      **4. Minimality:** Be concise. This is a map for LLMs, not a novel.
      **5. Mode:** Operate in `content-only` mode."

3.  **Step 3: Global Indexing (Full Mode)**
    - Invoke a single `recorder` agent.
    - **Task:** "Re-scan `/llmdoc`. Update `index.md` to remove broken links to deleted files, add new files, and ensure the map is fully traversable. Operate in `full` mode."