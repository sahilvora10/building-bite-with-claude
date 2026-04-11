# Bug: Non-food images logged as 0-calorie cards

**Version:** v0.7
**Date:** 2026-04-08

## Symptom
Submitting photos of non-food items (e.g. a person, a microphone) either logged a "no food detected" card with 0 calories, or hallucinated food (mic → "dark soft drink eg cola").

## Root cause
No validation on AI results before inserting into meals table. Any response from Gemini was saved regardless of confidence or calorie count.

## Fix
Added a guard after AI analysis: if `confidence < 0.3` or `calories === 0`, show a fun rejection alert and don't insert the meal. Four randomized messages like "That doesn't look like something you'd eat!"
