# Bug: Daily goals not persisting after save

**Version:** v0.4
**Date:** 2026-04-06

## Symptom
User updates daily goals in Settings, hits Save, navigates to Home — goals unchanged. Going back to Settings also shows old values.

## Root cause
`getDailyGoals()` query used `ORDER BY effective_from DESC LIMIT 1`. When multiple rows share the same `effective_from` date (e.g., default row + user update both dated today), the order is undefined — SQLite could return any row, typically the oldest.

## Fix
Added `id DESC` as tiebreaker: `ORDER BY effective_from DESC, id DESC LIMIT 1`. The most recently inserted row always wins.
