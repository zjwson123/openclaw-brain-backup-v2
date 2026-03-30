---
children_hash: df477268762d9d6b60f262fe11fb821b04f6b7d02b95d29260cb4b9f7b24dee7
compression_ratio: 0.42900763358778626
condensation_order: 3
covers: [architecture/_index.md, facts/_index.md, memory/_index.md, patterns/_index.md]
covers_token_total: 1310
summary_level: d3
token_count: 562
type: summary
---
# Structural Knowledge Summary (Level d3)

This summary synthesizes core architectural, operational, and behavioral conventions across the domains of Architecture, Facts, Memory, and Patterns.

### Architecture: Error Handling and Stability
The architecture domain centers on the **Admit-Fix-Learn** lifecycle, a mandatory four-stage framework (Acknowledge, Fix, Analyze, Update) for all system incidents. 
* **Operational Application**: Specific stability protocols for OpenClaw (detailed in `openclaw_crash_troubleshooting.md`) mandate versioning $\ge$ 2026.3.28, with automated remediation triggers for persistent instability.
* **Drill-down**: See `architecture/error_handling/_index.md` for lifecycle details and incident documentation conventions.

### Facts: Developer Productivity
The facts domain serves as a repository for project-specific definitions and metadata.
* **Developer Efficiency**: The scope has been re-formalized to "Developer Efficiency Tools" (开发提效工具) to better align with project intent.
* **Drill-down**: Refer to `facts/project/_index.md` and `developer_efficiency_tools.md` for attribution and tool classifications.

### Memory: Importance-Based Management
The system employs a hierarchical memory management policy, categorizing information on a 1-5 importance scale to dictate storage longevity.
* **Policy**: Data rated 4-5 (Core Identity, Decisions, Patterns) is preserved in long-term storage; 2-3 (Background) is archived in daily logs; 1 (Transient) is discarded.
* **Drill-down**: See `memory/management/_index.md` and `memory_importance_scoring.md` for specific implementation criteria.

### Patterns: Behavioral and Query Conventions
This domain codifies mandatory procedural conventions for agent interactions and information retrieval.
* **Query Handling**: A strict **Time-Sensitive Query Protocol** is enforced to prevent reliance on stale training data. Syntheses must be verified against current session baselines and result timestamps.
* **Architectural Mandate**: Failure to account for temporal context is classified as a critical severity error.
* **Drill-down**: Refer to `patterns/query_handling/_index.md` and `time_sensitive_query_pattern.md` for procedural requirements and verification flows.