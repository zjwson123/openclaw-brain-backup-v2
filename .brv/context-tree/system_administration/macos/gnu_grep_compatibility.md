---
title: GNU Grep Compatibility
tags: []
keywords: []
importance: 50
recency: 1
maturity: draft
createdAt: '2026-03-22T01:06:58.619Z'
updatedAt: '2026-03-22T01:06:58.619Z'
---
## Raw Concept
**Task:**
Fix macOS grep compatibility for Xiaoyuzhou podcast transcription

**Changes:**
- Switched to GNU grep for Perl regex support

**Files:**
- memory/agent-reach-xiaoyuzhou-fix.md

**Flow:**
brew install grep -> Update PATH to include gnubin -> Run transcription script

**Timestamp:** 2026-03-22

## Narrative
### Structure
Path update for GNU grep compatibility on macOS.

### Dependencies
Requires Homebrew and `grep` package.

### Highlights
Fixes issues where scripts using `grep -P` fail on macOS due to BSD grep limitations.

### Rules
Always use GNU grep when Perl-compatible regular expressions (-P) are required in shell scripts on macOS.

## Facts
- **macos_grep_compatibility**: macOS BSD grep does not support -P (Perl regex) [environment]
- **gnu_grep_installation**: GNU grep can be installed via Homebrew: brew install grep [project]
- **gnu_grep_path**: GNU grep path for Homebrew is /opt/homebrew/opt/grep/libexec/gnubin [environment]
