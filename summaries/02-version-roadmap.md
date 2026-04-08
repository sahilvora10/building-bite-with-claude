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

## v0.9 — History screen + polish
Scrollable meal history by day + UI cleanup.

### UI fix backlog (for v0.9)
- Custom app icon for the APK (replace default Expo icon)
- Keyboard overlaps carbs/fat inputs on Settings screen (Android)
- Ring overflow shadow effect (needs Skia, not possible in Expo Go)
- Meal card flickering on re-render

### Feature backlog
- Non-food image handling: reject with a fun alert instead of logging a 0-calorie card
- Edit/delete logged meals: tap to edit values or swipe to delete and re-log
- AI provider showdown: run all providers on the same meal input and compare results side-by-side (fun/experimental feature)

## v1.0 — MVP complete
All core features stable and working.
Transition from Expo Go to standalone build via EAS Build.

## Post-v1.0 — Future

### Widgets
- Android home screen widget showing today's rings/calories (requires dev build + native module)
- iOS widget (requires Apple Developer account)

### Design / Engineering
- Caching: cache AI results for repeated meals (e.g. "oats with milk" shouldn't hit the API every time)
- Deterministic results: same input should yield consistent nutrition values — explore temperature=0, seed params, or local lookup table for common foods
- In-app metrics: track API latency, cache hit rate, meals logged per day, app load time — visible in a debug/stats screen
- Lightweight footprint: audit bundle size, lazy-load screens, minimize dependencies, keep SQLite queries fast

### Deployment
- **Android**: standalone APK/AAB via EAS Build — installable without Expo Go or Play Store
- **iOS**: requires Apple Developer account ($99/year) for standalone install or TestFlight
- **Web**: possible but needs storage abstraction (expo-sqlite is native-only → IndexedDB or similar) and image picker adjustments
