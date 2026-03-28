---
children_hash: 85b47a1b336e9429cf6cff61717fc0d62f0c917035de5209effed5cc8cc72ec4
compression_ratio: 0.6220806794055201
condensation_order: 1
covers: [context.md, time_sensitive_queries.md, time_sensitive_queries/_index.md]
covers_token_total: 471
summary_level: d1
token_count: 293
type: summary
---
# Structural Summary: Query Handling (d1)

The Query Handling domain consolidates conventions for information retrieval, focusing on temporal awareness, verification, and structured search strategies.

## Core Pattern: Time-Sensitive Queries
To prevent reliance on stale training data, all queries concerning current events, news, or model versions must adhere to a mandatory verification flow:

*   **Mandatory Flow**: Implement a session check via `session_status`, establish a current time baseline, and verify search result timestamps before processing.
*   **Key Rules**:
    *   MUST obtain current time prior to initiating news or release searches.
    *   DO NOT utilize training cutoff data for time-dependent information.
    *   Ignoring temporal context is categorized as a critical severity pitfall.
*   **Associated Resources**: 
    *   `memory/patterns.md` and `memory/feedback.md` provide implementation context.
    *   Refer to `time_sensitive_query_pattern.md` for specific logic and implementation requirements.

For further details on specific query handling implementations, drill down into individual topic files within the `query_handling/` domain.