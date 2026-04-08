# Bug: Raw Gemini API error shown to user

**Version:** v0.4
**Date:** 2026-04-07

## Symptom
When Gemini free tier rate limit (429) is hit, the full raw JSON error response is dumped in an alert dialog — unreadable and scary for users.

## Root cause
`gemini.ts` error handler threw the raw `response.text()` as the error message.

## Fix
Added specific handling for 429 (rate limit), 401/403 (bad key), and a generic fallback — all with user-friendly messages.
