# Session 01: Project Kickoff — Spec Writing

**Date:** 2026-04-04

## What was done
- Transcribed voice memo with initial product vision
- Wrote full product spec (SPEC.md) through iterative Q&A
- Made key technology decisions

## Decisions made
| Decision | Choice | Why |
|----------|--------|-----|
| Framework | React Native (Expo) | Cross-platform, beginner-friendly, Expo Go for free testing |
| Database | SQLite (on-device) | Privacy-first, no server needed |
| AI approach | BYOM — cloud + local | Gemini free tier to start, local models later |
| Home screen | Logging-first | Lowest friction — open app, log meal immediately |
| iOS testing | Expo Go (free) | No Apple Developer account needed |

## Questions explored
- Web vs native → Expo (native feel, single codebase)
- Where data lives → SQLite file on phone
- What is Expo → Toolchain on React Native, removes native build pain
- What is Replit → Online IDE, not ideal for local-first mobile apps
- Free local models → Gemma 3 via MediaPipe, lower accuracy trade-off
- Hot-swappable AI settings → Yes, switch provider anytime in settings
- How Claude tests mobile apps → Unit/component tests + user is eyes on device

## Process learnings
- Starting with a voice memo → transcript → spec is an effective way to get ideas out fast
- Iterative Q&A with Claude shapes decisions better than trying to spec everything upfront
- Asking "what are the trade-offs" questions leads to more informed choices
