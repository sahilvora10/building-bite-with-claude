# Session 14: Edit/Delete Meals + Recipes

**Date:** 2026-04-12

## What was done
- Edit meals: tap a meal card → modal with food description → Gemini re-analyzes → updates entry in place
- Delete meals: delete button in edit modal + confirmation dialog
- Edit recipes: tap a recipe card → opens creation form pre-filled with name, servings, and saved ingredients as editable chips
- Ingredients editing: remove chips with ✕, add new ones via input field, all sent to Gemini on re-analysis
- Photos only on new recipe creation (not in edit) — avoids DB bloat from storing full base64 images
- Photo buttons moved below thumbnails for better layout
- Recipe photo limit bumped from 4 to 10
- Custom app icon added (red apple with bite mark, orange gradient)
- Platform strategy documented (PWA vs Apple Developer vs Android-only)

## Files changed
- `src/db/database.ts` — added updateMeal, deleteMeal, updateRecipe functions
- `src/screens/HomeScreen.tsx` — meal card tap-to-edit modal with Gemini re-analysis, delete
- `src/screens/RecipesScreen.tsx` — recipe edit reuses creation form, ingredient chips, photo layout fix

## Design decisions
- Meal edit sends corrected text description to Gemini rather than manually editing macro numbers — keeps AI as source of truth
- Recipe edit shows ingredients (editable) but no photos — photos are large base64 in DB, not worth loading back
- No long-press gestures — everything accessible via tap, explicit buttons for delete
- Fun modal copy: "AI got it wrong? Tell it what you really ate and we'll fix the math."

## Bugs fixed
- Saved photos not displaying in recipe edit (data URI rendering issue) — resolved by removing photos from edit entirely
- Photo add buttons overlapping with thumbnails — moved buttons to separate row below
- Ingredients not showing in recipe edit — changed condition to always show in edit mode
- Pushed directly to master by mistake — reverted and moved to feature branch

## Next up
- Merge to master after testing
- Build APK from master
- Decide on platform strategy (PWA vs native)
