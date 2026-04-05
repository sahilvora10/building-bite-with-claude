# Workflow: Bite + Building Bite with Claude

## Two repos, clear boundaries

### `bite` (the app)
**Save here:** All application code, config, spec, assets.
**Commit when:**
- A feature or sub-feature is working
- A bug is fixed
- Spec is updated with a decision
- Any code change, no matter how small

**Commit style:** Short, conventional commits
```
feat: add text meal logging
fix: calorie total not updating
docs: update spec with BYOM settings flow
```

### `building-bite-with-claude` (the journey)
**Save here:** Process learnings, session summaries, prompts, feedback.
**Commit when:**
- End of every session (mandatory)
- A particularly good or bad prompt is worth recording
- A feedback loop or correction happens that's worth remembering
- A workflow insight or process improvement is discovered

**Commit style:** Session-based
```
session-01: spec writing — decisions and learnings
session-02: v0.1 scaffolding — expo setup lessons
```

---

## Session workflow

### Starting a session
1. Tell Claude what you want to work on
2. Claude reads the spec + roadmap to pick up context
3. Work begins

### During a session
- Claude commits to `bite` after each working increment
- If something interesting happens (good prompt, bad output, correction), note it for the journey

### Ending a session (or hitting daily limit)

**When you feel the limit approaching or want to stop:**

Tell Claude: **"Let's wrap up"**

Claude will:
1. **Commit all working code** to `bite` (never leave uncommitted changes)
2. **Write a session summary** in `building-bite-with-claude/journey/summaries/`
   - What was built
   - Decisions made
   - Bugs encountered and fixed
   - What's next (so the next session can pick up immediately)
3. **Commit the journey repo**
4. **Push both repos**

### Resuming next day
Tell Claude: **"Let's pick up where we left off"**

Claude will:
1. Read the latest session summary
2. Read the spec + roadmap
3. Check git status of both repos
4. Continue from where things stopped

---

## What goes where — quick reference

| Thing | Repo |
|-------|------|
| Source code | bite |
| SPEC.md | bite |
| package.json, app.json, configs | bite |
| Session summaries | building-bite-with-claude |
| Prompt examples (good and bad) | building-bite-with-claude |
| Feedback / corrections log | building-bite-with-claude |
| Version roadmap | building-bite-with-claude |
| Voice memos / transcripts | building-bite-with-claude |
| This workflow doc | root (shared) |

---

## Git management

Claude handles all git operations:
- Staging, committing, pushing
- Never force-pushes
- Never amends without asking
- Commits frequently in small increments
- User supervises and approves

## Daily limit strategy

On the Pro tier, when the limit is close:
- Claude prioritizes committing and summarizing over writing new code
- The summary acts as a "save state" — complete enough that any Claude session can resume
- No work is ever lost between sessions
