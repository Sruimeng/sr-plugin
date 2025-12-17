---
id: "guide-doc-standard"
type: "guide"
title: "LLM-Friendly Documentation Standard"
description: "The official protocol for writing high-utility, low-token documentation for AI Agents in the SR-Plugin ecosystem."
tags: ["meta", "standard", "documentation", "protocol"]
last_updated: "2025-12-16"
---

# LLM-Friendly Documentation Standard

> **Context**: This document defines the **Constitutional Standard** for how Agents (specifically Cartographer and Recorder) MUST write documentation.
> **Goal**: Maximize machine readability (RAG accuracy), minimize token usage, and eliminate hallucinations.

## 1. The Anatomy (Mandatory Structure)

Every document created or updated in `/llmdoc` MUST follow this structure.

### A. Frontmatter (YAML)
**Constraint**: DO NOT use 'audience' or 'read_time'. Use 'id' for vector linking.

```yaml
---
# Identity
id: "unique-kebab-id"  # CRITICAL: Used for vector indexing (e.g., 'concept-rhi-texture')
type: "concept" | "architecture" | "guide" | "reference"
title: "Concise Title"

# Semantics
description: "One-sentence summary optimized for RAG retrieval."
tags: ["keyword1", "keyword2"]

# Graph (Use IDs, not filenames)
context_dependency: ["id-of-prerequisite"] # Must read these first to understand this doc
related_ids: ["id-of-related-doc"]       # Optional context
---