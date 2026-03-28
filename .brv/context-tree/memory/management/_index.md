---
children_hash: 381ecdd2208b102cbd20b63b6c78e8caae196eb512d00439194c0151c97b7282
compression_ratio: 0.9836956521739131
condensation_order: 1
covers: [memory_importance_scoring.md]
covers_token_total: 184
summary_level: d1
token_count: 181
type: summary
---
### Memory Importance Scoring
The system implements a structured memory management policy based on a 1-5 importance scale to determine storage longevity and location. This framework ensures critical knowledge is persisted while ephemeral data is managed efficiently.

Key Storage Policies:
- Score 5 (Core Identity/Decisions): Persisted to long-term storage (e.g., MEMORY.md or domain-specific files).
- Score 4 (Projects/Patterns/Preferences): Persisted to long-term storage.
- Score 2-3 (Background/Short-term): Stored in daily logs (memory/YYYY-MM-DD.md).
- Score 1 (Chat/Transient): Ignored or relegated to daily logs.

For detailed implementation criteria and classification logic, refer to memory_importance_scoring.md.