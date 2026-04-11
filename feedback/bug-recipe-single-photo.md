# Bug: Recipe analysis only used first photo

**Version:** v0.7
**Date:** 2026-04-08

## Symptom
User attached 4 photos to a recipe but Gemini only analyzed the first one — recipe name and nutrition reflected only the first image.

## Root cause
`RecipesScreen` passed `imageBase64: photos[0].base64` to the provider, ignoring the rest.

## Fix
- Added `imagesBase64?: string[]` to `FoodInput` interface
- Updated Gemini provider to loop through all images and add each as `inlineData`
- Recipe screen now passes `imagesBase64: photos.map(p => p.base64)` — all photos sent together
