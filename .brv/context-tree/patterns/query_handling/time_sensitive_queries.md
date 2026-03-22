---
title: Time Sensitive Queries
tags: []
keywords: []
importance: 50
recency: 1
maturity: draft
createdAt: '2026-03-22T01:06:58.772Z'
updatedAt: '2026-03-22T01:06:58.772Z'
---
## Raw Concept
**Task:**
Handle time-sensitive information queries

**Files:**
- memory/patterns.md
- memory/feedback.md

**Flow:**
Obtain current time -> search news/releases -> verify results timestamps

**Timestamp:** 2026-03-22

## Narrative
### Structure
Pattern for searching and verifying time-sensitive data.

### Highlights
Critical severity for ignoring temporal context.

### Rules
MUST obtain current time first before searching news/model releases.
DO NOT use training cutoff knowledge for current events.
VERIFY search result timestamps.

## Facts
- **time_sensitive_queries**: Must obtain current time (session_status or system) before searching news/model releases [convention]
- **time_sensitive_pitfalls**: Ignoring actual year/month or using training cutoff is a critical pitfall [convention]
