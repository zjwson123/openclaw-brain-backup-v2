---
title: Time-Sensitive Query Pattern
tags: []
keywords: []
importance: 50
recency: 1
maturity: draft
createdAt: '2026-03-28T01:04:44.455Z'
updatedAt: '2026-03-28T01:04:44.455Z'
---
## Raw Concept
**Task:**
Handle time-sensitive queries correctly

**Flow:**
Verify time baseline -> Check session_status -> Query info

**Timestamp:** 2026-03-28

## Narrative
### Structure
Pattern to prevent using outdated training data for current information.

### Rules
Always verify current time baseline before querying time-sensitive info (news, tech, model versions). Always check session_status first.

## Facts
- **time_sensitive_queries**: Always verify current time baseline before querying time-sensitive info [convention]
- **time_sensitive_queries**: Check session_status first to prevent using outdated training data [convention]
