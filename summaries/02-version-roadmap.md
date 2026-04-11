# Version Roadmap

## v0.1 — "It works on my phone"
Text logging + Gemini API + SQLite + today's meal list with running calorie total.
Proves the full pipeline: Expo → UI → API call → SQLite → display.

## v0.2 — Photo input
Camera + gallery → send image to Gemini → calories + macros.

## v0.3 — Rings dashboard
Apple-style circular progress rings for calories, protein, carbs, fat + daily goals.

## v0.4 — Settings screen
BYOM: swap provider, enter API key, set daily goals.

## v0.5 — Voice input
Record audio → send to AI → transcription + nutrition analysis.

## v0.6 — Streaks + notifications
Duolingo-style streak tracking + local reminders to log meals.

## v0.7 — Recipe builder
Multi-photo recipe input → per-serving breakdown → save locally for re-logging.

## v0.8 — Summaries
Daily and weekly summaries with macro breakdowns and trends.

## v0.9 — Extended history + meal time tags
Extend summaries beyond 7 days (scrollable full history) + meal time tags (breakfast/lunch/dinner/snack).

## v1.0 — MVP complete
All core features stable and working.
Transition from Expo Go to standalone build via EAS Build.

### UI fix backlog (post-v1.0)
- Custom app icon for the APK (replace default Expo icon)
- Keyboard overlaps carbs/fat inputs on Settings screen (Android)
- Ring overflow shadow effect (needs Skia, not possible in Expo Go)
- Meal card flickering on re-render

### Feature backlog (post-v1.0)
- Edit/delete logged meals: tap to edit values or swipe to delete and re-log
- AI provider showdown: run all providers on the same meal input and compare results side-by-side (fun/experimental feature)
- Export data: CSV export of all meals for backup
- Search meals: find past meals by name

## Post-v1.0 — Future

### Widgets
- Android home screen widget showing today's rings/calories (requires dev build + native module)
- iOS widget (requires Apple Developer account)

### Testing / Automation
- Automated device testing: explore connecting Android device via ADB over WSL2, then Claude can run UI tests (Maestro/Detox) or drive the app via adb shell commands to self-test after each build

### Design / Engineering
- Caching: cache AI results for repeated meals (e.g. "oats with milk" shouldn't hit the API every time)
- Deterministic results: same input should yield consistent nutrition values — explore temperature=0, seed params, or local lookup table for common foods
- In-app metrics: track API latency, cache hit rate, meals logged per day, app load time — visible in a debug/stats screen
- Lightweight footprint: audit bundle size, lazy-load screens, minimize dependencies, keep SQLite queries fast

### Deployment

**Current status (v1.0 MVP):**
- **Android**: standalone APK via EAS Build — daily testing device, fully working
- **iOS**: Expo Go only (free) — needs dev server running, no notifications. Daily driver phone but no standalone build without Apple Developer account ($99/year)
- **Web**: not yet supported

**Platform strategy (needs decision):**
- Option A: **PWA (Progressive Web App)** — free on all platforms, installs to iOS home screen, no App Store needed. Requires swapping SQLite → IndexedDB, expo-av → Web Audio API. Same React + TypeScript skills transfer. Every future app also works on iOS/Android/desktop for free.
- Option B: **Apple Developer Program ($99/year)** — standalone iOS builds via EAS, TestFlight distribution. Worth it if building multiple native apps. Only way to get push notifications + widgets on iOS.
- Option C: **Stay Android-native + Expo Go on iOS** — no cost, but iOS experience is limited (server required, no notifications)

**Context:** User's daily phone is iOS, Android is for testing. Planning more apps beyond Bite. PWA route would give free iOS access for all future apps.
