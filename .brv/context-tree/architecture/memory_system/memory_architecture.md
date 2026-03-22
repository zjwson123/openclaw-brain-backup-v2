---
title: Memory Architecture
tags: []
keywords: []
importance: 50
recency: 1
maturity: draft
createdAt: '2026-03-22T01:06:59.232Z'
updatedAt: '2026-03-22T01:06:59.232Z'
---
## Raw Concept
**Task:**
Document OpenClaw 2-tier memory architecture and storage rules

**Files:**
- MEMORY.md
- memory/patterns.md
- memory/decisions.md
- memory/contacts.md
- memory/projects.md

**Flow:**
Information -> Scored (1-5) -> Directed to Long-term (>=4) or Daily Logs (2-3)

**Timestamp:** 2026-03-22

## Narrative
### Structure
2-tier system: Long-term (specialized files) + Short-term (daily logs).

### Highlights
Uses a scoring system (1-5) to determine storage location. Core identity and patterns are prioritized for long-term storage.

### Rules
Rule: Score >= 4 to long-term, 2-3 to daily logs.

## Facts
- **memory_tier_system**: OpenClaw uses a 2-tier memory system: Long-term and Short-term. [project]
- **long_term_memory_files**: Long-term memory is stored in MEMORY.md and specialized files like patterns.md, decisions.md, contacts.md, and projects.md. [project]
- **short_term_memory_location**: Short-term memory is stored in daily logs at memory/YYYY-MM-DD.md. [project]
- **memory_scoring_criteria**: Memory decision criteria: 5=core identity/decisions, 4=projects/patterns, 3=background info, 2=short-term, 1=chat. [convention]
- **memory_storage_rule**: Memory storage rule: Score >= 4 goes to long-term memory; Score 2-3 goes to daily logs. [convention]
