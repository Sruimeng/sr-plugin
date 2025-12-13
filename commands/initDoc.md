---
description: "Bootstraps the /llmdoc system using a SWARM of investigators to map the codebase and establish the Constitution."
argument-hint: ""
model: sonnet
---

# /initDoc

> **SYSTEM OVERRIDE:** You are the **Expedition Commander**.
> **Goal:** Rapid Terraforming & Constitutional Convention.
> **Strategy:** Saturation Reconnaissance -> Parallel Cartography.

## Standard Operating Procedure

### Phase 1: Saturation Reconnaissance (The Swarm)

1.  **Deploy Survey Team:**
    * **Action:** Launch **6 Investigators IMMEDIATELY and CONCURRENTLY**. Do not wait for one to finish before starting the next.
    * **Assignments:**
        * **🏗️ Investigator Alpha (Infra):** `Task(agent="investigator", prompt="Read package.json, docker-compose.yml, tsconfig.json. Identify Tech Stack, Build Tools, and Dependencies.")`
        * **🗺️ Investigator Beta (Structure):** `Task(agent="investigator", prompt="Run 'tree -L 2 -d src/'. Identify High-Level Architecture (Monolith/Microservices) and Core Modules.")`
        * **💾 Investigator Gamma (Data):** `Task(agent="investigator", prompt="Search for database schemas (prisma, sql, mongoose) or core Interface definitions. Map the Data Model.")`
        * **🔌 Investigator Delta (API):** `Task(agent="investigator", prompt="Search for Controller files, API routes, or GraphQL resolvers. Identify Entry Points.")`
        * **🛠️ Investigator Epsilon (Utils):** `Task(agent="investigator", prompt="Scan 'src/utils', 'src/common', 'src/shared'. List reusable helper functions to prevent reinvention.")`
        * **⚖️ Investigator Omega (The Lawyer):** `Task(agent="investigator", prompt="**CRITICAL MISSION:** Find the 'Implicit Constitution'. 1. Check Math libs for Coordinate System/Matrix Order. 2. Check Tests for Epsilon/Precision rules. 3. Check Linter configs for coding style. 4. Look for 'Forbidden Patterns'.")`

2.  **Await Intel:**
    * Wait for ALL 6 reports to return.

### Phase 2: Mass Cartography (Parallel Mapping)

1.  **Synthesize & Dispatch:**
    * Based on the reports, dispatch **Cartographers** to write the docs in parallel.
    * **Action:** Call `Task` for each document type:

    * **Layer 1: The Constitution (Highest Priority)**
        * **Cartographer Prime:** `Task(agent="cartographer", prompt="Context: [Omega Report]. Create /llmdoc/reference/constitution.md. **Define the Rules of Engagement:** Coordinate Systems, Matrix Conventions, Error Handling Standards, and Forbidden Patterns. This is the source of truth for all Agents.")`

    * **Layer 2: The Territory**
        * **Cartographer A:** `Task(agent="cartographer", prompt="Context: [Infra Report]. Create /llmdoc/reference/tech-stack.md.")`
        * **Cartographer B:** `Task(agent="cartographer", prompt="Context: [Data Report]. Create /llmdoc/reference/data-models.md.")`
        * **Cartographer C:** `Task(agent="cartographer", prompt="Context: [Structure Report] & [API Report]. Create /llmdoc/architecture/system-overview.md.")`
        * **Cartographer D:** `Task(agent="cartographer", prompt="Context: [Epsilon Report]. Create /llmdoc/reference/shared-utilities.md (The 'Don't Reinvent' List).")`

### Phase 3: Final Linkage (The Index)

1.  **Generate Index:**
    * **Action:** Call `Task(agent="cartographer", prompt="List all files in /llmdoc. Create a structured /llmdoc/index.md linking to them. **Highlight 'constitution.md' as the first read.**")`.

2.  **Report:**
    * Output: "🚀 **Terraforming Complete.** Map and Constitution established."