---
description: "Direct Action Mode: Bypasses deep investigation but maintains quality control via Critic."
argument-hint: "[Specific, explicit code instruction]"
model: sonnet
---

# /do

> **SYSTEM OVERRIDE:** You are in **Direct Execution Mode**.
> **Goal:** Execute immediately -> Verify -> Sync.
> **Constraint:** Speed is key, but DO NOT break the build.

## Mandatory Workflow

### Step 1: Execute (The Strike)

1.  **Dispatch Worker:**
    * You **MUST** use the `Task` tool to launch the `worker` agent.
    * **Prompt:**
      > "[DIRECT ACTION] Context: User authorized this specific change.
      > **Instruction:** {{USER_INPUT}}
      > **Constraint:** Execute immediately. Ensure NO placeholders. Verify after change."

### Step 2: Safety Check (The Critic)

1.  **Dispatch Critic:**
    * **Action:** Call `Task(agent="critic", prompt="Quick review of the files modified by Worker. Strict check for: 1. Console logs. 2. Laziness (placeholders). 3. Syntax errors.")`.
    * **Decision Logic:**
        * **IF PASS:** Proceed to Step 3.
        * **IF FAIL:**
            * **Action:** Call `Task(agent="worker", prompt="Fix issues reported by Critic: [Insert Report].")`.
            * *Note:* Allow max 1 retry loop for speed. If still failing, stop and report to user.

### Step 3: Auto-Sync (The Recorder)

1.  **Dispatch Recorder:**
    * **Condition:** Only if Step 2 PASSED.
    * **Action:** Call `Task(agent="recorder")`.
    * **Prompt:**
      > "Sync /llmdoc based on recent changes.
      > **Context:** This was a Direct Action (`/do`). There is NO strategy file.
      > **Intent:** {{USER_INPUT}}.
      > **Source:** Read `git diff`."

## Example Behavior
* User: `/do Rename 'Login' to 'SignIn'`
* **You:** `Task(worker)` -> `Task(critic)` -> `Task(recorder)`