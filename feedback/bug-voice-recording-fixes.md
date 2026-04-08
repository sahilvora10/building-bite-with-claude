# Bug: Voice recording failures (v0.5)

**Date:** 2026-04-07

## Bug 1: "Failed to stop recording"
**Symptom:** Tapping stop after recording always errored.
**Root cause:** `useState` for the recording instance was stale inside the `stopRecording` closure — React state hadn't updated by the time the function ran.
**Fix:** Switched to `useRef` for the recording instance so it's always current.

## Bug 2: "Cannot read property base64 of undefined"
**Symptom:** After fixing stop, reading the audio file as base64 crashed.
**Root cause:** `FileSystem.EncodingType.Base64` was undefined at runtime in SDK 54.
**Fix:** Used string literal `'base64'` instead of the enum.

## Bug 3: "readAsStringAsync from expo-file-system is deprecated"
**Symptom:** After fixing the encoding, the import itself was deprecated.
**Root cause:** SDK 54 moved the old `expo-file-system` API to a legacy path.
**Fix:** Changed import to `expo-file-system/legacy`.
