---
children_hash: 3385fbe54284ed96d9119dba172016d9ba048dab5705312104dc700be80f428f
compression_ratio: 0.7479674796747967
condensation_order: 2
covers: [management/_index.md]
covers_token_total: 246
summary_level: d2
token_count: 184
type: summary
---
# Memory Management Overview

The system utilizes a memory management policy defined in `memory_importance_scoring.md`, which categorizes data on a 1-5 importance scale to optimize storage longevity and location.

## Storage Policy Framework
- **Importance 4-5 (Core Identity, Decisions, Projects, Patterns):** Assigned to long-term storage, including `MEMORY.md` and relevant domain-specific files.
- **Importance 2-3 (Background, Short-term):** Directed to daily log files located in `memory/YYYY-MM-DD.md`.
- **Importance 1 (Transient):** Classified as ephemeral; data is relegated to daily logs or discarded.

For specific classification logic and implementation criteria, refer to the full details in `memory_importance_scoring.md`.