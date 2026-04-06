# Journey: Building a Calorie Tracker with Claude

This repo documents the process of building a mobile app end-to-end with AI assistance — capturing what worked, what didn't, and how to get better at it.

## Structure

```
journey/
├── conversations/     # Transcripts and summaries of each Claude session
│   └── 01-topic.md    # Numbered sequentially
├── prompts/           # Prompts that worked well (and ones that didn't)
│   └── 01-topic.md    # What was asked, what was produced, what was learned
├── summaries/         # End-of-session summaries of work done
│   └── 01-topic.md    # Changes made, decisions taken, bugs fixed
├── feedback/          # What to do differently next time
│   └── 01-topic.md    # Feedback loops, corrections, process improvements
└── README.md          # This file
```

## Naming Convention

Files are numbered sequentially (`01-`, `02-`, ...) and given a short descriptive suffix.

## Session Log

| # | Date | Topic | Key Learnings |
|---|------|-------|---------------|
| 01 | 2026-04-04 | Project kickoff — spec writing | Start with spec before code; ask Claude questions to shape decisions; voice memo → transcript → spec workflow |
| 02 | 2026-04-04 | Version roadmap | Break MVP into tiny vertical slices; each version should be usable on its own |
| 03 | 2026-04-04 | v0.1 build | Full pipeline in ~5 files; BYOM abstraction from day 1; home screen = logging screen for lowest friction |
| 04 | 2026-04-05 | v0.1 testing | Use tunnel mode for WSL2; always `npx expo install`; curl-test APIs first; screenshots not video for Claude feedback |
| 05 | 2026-04-05 | v0.2 build — photo input | AI layer was already ready for images from day 1; BYOM abstraction paid off; expo-image-picker handles permissions cleanly |
| 06 | 2026-04-05 | v0.3 build — rings + goals | react-native-svg for custom rings; database migrations additive (new table, no breaking changes); reusable components pay off early |
