---
children_hash: ed9b3ff9b5d1af7be7b96542e17e80e17cf6992a627158c4637d91c91f29a295
compression_ratio: 0.9265033407572383
condensation_order: 2
covers: [context.md, query_handling/_index.md]
covers_token_total: 449
summary_level: d2
token_count: 416
type: summary
---
# Structural Summary: Patterns and Query Handling (d2)

This domain defines the foundational behavioral and procedural conventions for agent task execution and information retrieval.

## Domain Overview: Patterns
The `patterns` domain (see `patterns/context.md`) establishes standard operating procedures for agent behavior. It focuses on query handling, interaction conventions, and error recovery strategies, while intentionally excluding project-specific implementation details or tool-specific documentation.

## Core Component: Query Handling
The `query_handling` topic (see `query_handling/_index.md`) defines the mandatory framework for processing information requests, prioritizing temporal accuracy and verification.

### Time-Sensitive Query Protocol
To mitigate risks associated with stale training data, the following mandatory flow is enforced:
*   **Verification Flow**: Every time-sensitive query must initiate with a `session_status` check, establish a current time baseline, and validate search result timestamps against the current date before synthesis.
*   **Architectural Mandate**: Reliance on training cutoff data for time-dependent information is prohibited. Failure to account for temporal context is classified as a critical severity error.
*   **Implementation References**:
    *   `time_sensitive_query_pattern.md`: Contains the specific logic and procedural requirements for query processing.
    *   `memory/patterns.md` and `memory/feedback.md`: Provide broader implementation context and historical feedback loops.

For granular implementation details, refer to the individual topic files within the `query_handling/` sub-directory.