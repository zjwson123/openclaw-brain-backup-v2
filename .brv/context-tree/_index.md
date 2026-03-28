---
children_hash: 9159dcff380b931a23914619992605e3b605e74f72297bd84ad81611dfa9ae69
compression_ratio: 0.3919558359621451
condensation_order: 3
covers: [architecture/_index.md, facts/_index.md, memory/_index.md, patterns/_index.md]
covers_token_total: 1268
summary_level: d3
token_count: 497
type: summary
---
# Structural Summary: Knowledge Architecture (d3)

This overview synthesizes the core domains, procedural patterns, and management frameworks governing the system.

## 1. Architectural & Error Management (architecture/)
The architecture domain centers on the **Admit-Fix-Learn** lifecycle, a mandatory four-step process (Acknowledge, Fix, Analyze, Update) for systemic reliability. 
*   **Key Focus**: Errors are treated as critical data points for root cause analysis (RCA).
*   **Accountability**: All error logs must be recorded in `patterns.md` or `feedback.md`.
*   **Drill-down**: See `architecture/error_handling/_index.md` and `admit_fix_learn_pattern.md`.

## 2. Pattern Behavioral Framework (patterns/)
This domain dictates agent operational procedures, specifically query handling and interaction conventions.
*   **Time-Sensitive Query Protocol**: Mandates a verification flow that prohibits reliance on stale training data. Agents must perform a `session_status` check and validate temporal metadata before synthesis.
*   **Key Reference**: `patterns/query_handling/_index.md` and `time_sensitive_query_pattern.md`.

## 3. Memory & Storage Policy (memory/)
Memory management utilizes a 1-5 importance scoring system to optimize data longevity.
*   **Importance 4-5**: Core identity, decisions, and patterns; stored in long-term files like `MEMORY.md`.
*   **Importance 2-3**: Background/short-term data; relegated to daily logs in `memory/YYYY-MM-DD.md`.
*   **Importance 1**: Ephemeral data; discarded or logged transiently.
*   **Drill-down**: See `memory/management/_index.md` and `memory_importance_scoring.md`.

## 4. Project Facts & Productivity (facts/)
Maintains project-specific metadata and tool definitions.
*   **Developer Efficiency**: Formally defined as "Developer Efficiency Tools" (开发提效工具) to focus on developer experience (DX).
*   **Drill-down**: See `facts/project/_index.md` and `developer_efficiency_tools.md` for attribution and classification logic.