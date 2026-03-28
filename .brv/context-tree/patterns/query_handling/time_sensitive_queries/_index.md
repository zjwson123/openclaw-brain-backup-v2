---
children_hash: 348ebdd0d542dad1f74b816302402af4d92d18628e5f3cd373d0e095d0cd61f9
compression_ratio: 0.5240384615384616
condensation_order: 0
covers: [time_sensitive_query_pattern.md]
covers_token_total: 208
summary_level: d0
token_count: 109
type: summary
---
# Time-Sensitive Query Pattern (d0)

To avoid using stale training data for time-dependent information (e.g., news, model versions), implement the mandatory verification flow:

1. **Session Check**: Always validate `session_status` first.
2. **Time Baseline**: Explicitly verify the current time baseline before initiating queries.

Drill down to `time_sensitive_query_pattern.md` for specific implementation requirements and flow logic.