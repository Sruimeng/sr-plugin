---
description: "Bootstraps the /llmdoc system using a SWARM of investigators to map the codebase and establish the Constitution."
argument-hint: ""
model: sonnet
---

# /initDoc

> **SYSTEM OVERRIDE:** You are the **Expedition Commander**.
> **Goal:** Rapid Terraforming & Constitutional Convention.
> **Strategy:** Skill Injection -> Saturation Reconnaissance -> Parallel Cartography.

## SOP (Standard Operating Procedure)

### Phase 1: Context & Skill Setup (The War Room)

1.  **Load Architecture Persona:**
    * **Action:** Call `Read("contexts/plan.md")`.
    * **Mindset:** "I am the Architect. I map the territory, I do not dig the ditches."

2.  **Load Law:**
    * **Action:** Call `Read("skills/style-hemingway.md")`.
    * **Constraint:** All generated documentation must follow the **Iceberg Principle** (High signal, low noise).

### Phase 2: Bootstrap the Constitution (Layer 0)

1.  **Establish Doc Standards:**
    * **Action:** Check if `llmdoc/guides/doc-standard.md` exists.
    * **If Missing:** Call `Task(agent="cartographer")`.
    * **Prompt:**
      > "Create `llmdoc/guides/doc-standard.md`.
      > **Content:** Define the 4 Laws of Docs: 1. Frontmatter Mandatory. 2. Type-First. 3. Pseudocode Logic. 4. No Meta-talk.
      > **Skill:** Apply `style-hemingway.md`."

### Phase 3: Saturation Reconnaissance (The Swarm)

1.  **Deploy Survey Team:**
    * **Action:** Launch **6 Investigators IMMEDIATELY and CONCURRENTLY**.
    * **Assignments:**
        * **🏗️ Investigator Alpha (Infra):** `Task(agent="investigator", prompt="Read build/dependency manifests: package.json/tsconfig.json, Cargo.toml, go.mod, pyproject.toml/requirements.txt, CMakeLists.txt/compile_commands.json, vcpkg.json/conanfile.*, build.gradle/pom.xml/*.csproj, docker-compose.yml. Identify Tech Stack, Build Tools, and Dependencies.")`
        * **🗺️ Investigator Beta (Structure):** `Task(agent="investigator", prompt="Run 'tree -L 2 -d src/'. Identify High-Level Architecture (Monolith/Microservices) and Core Modules.")`
        * **💾 Investigator Gamma (Data):** `Task(agent="investigator", prompt="Search for database schemas (prisma, sql, mongoose) or core Interface definitions. Map the Data Model.")`
        * **🔌 Investigator Delta (API):** `Task(agent="investigator", prompt="Search for Controller files, API routes, or GraphQL resolvers. Identify Entry Points.")`
        * **🛠️ Investigator Epsilon (Utils):** `Task(agent="investigator", prompt="Scan 'src/utils', 'src/common', 'src/shared'. List reusable helper functions to prevent reinvention.")`
        * **⚖️ Investigator Omega (The Lawyer):** `Task(agent="investigator", prompt="**CRITICAL MISSION:** Find the 'Implicit Constitution'. 1. Check Math libs for Coordinate System/Matrix Order. 2. **Audit Style:** Does current code violate `style-hemingway` (e.g. AbstractManagerImpl, Deep Nesting)? Report the 'Style Gap'.")`

2.  **Await Intel:**
    * Wait for ALL 6 reports to return.

### Phase 4: Mass Cartography (Parallel Mapping)

1.  **Synthesize & Dispatch:**
    * **Constraint:** All Cartographers MUST be instructed to load `skills/style-hemingway.md`.
    * **Action:** Call `Task` for each document type:

    * **Layer 1: The Constitution (Highest Priority)**
        * **Cartographer Prime:** `Task(agent="cartographer", prompt="Context: [Omega Report]. Tasks:\n1. Create /llmdoc/reference/constitution.md (Tech Rules).\n2. **Persist the Style Law:** Create /llmdoc/reference/style-hemingway.md based on the active Skill.\n3. Define Forbidden Patterns based on Omega's findings. **Skill:** Load `skills/style-hemingway.md`.")`

    * **Layer 2: The Territory**
        * **Cartographer A:** `Task(agent="cartographer", prompt="Context: [Infra Report]. Create /llmdoc/reference/tech-stack.md. **Skill:** Load `skills/style-hemingway.md`.")`
        * **Cartographer B:** `Task(agent="cartographer", prompt="Context: [Data Report]. Create /llmdoc/reference/data-models.md. Use Type-First definitions. **Skill:** Load `skills/style-hemingway.md`.")`
        * **Cartographer C:**
