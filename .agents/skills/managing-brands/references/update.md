# Update Brand

Update brand colors, typography, and style, then sync to all design-system files.

## Overview

This workflow updates all three together:
1. `docs/brand-guidelines.md`: human-readable brand doc
2. `assets/design-tokens.json`: token source of truth
3. `assets/design-tokens.css`: generated CSS variables

If the project uses the `brand-identity` skill, confirm with the user before changing any value it defines.

## Workflow

### Step 1: Gather Brand Input

Ask the user for:

**Theme Selection:**
- Theme name (e.g., "Ocean Professional", "Electric Creative", "Forest Calm")

**Primary Color:**
- Color name (e.g., "Ocean Blue", "Coral", "Forest Green")
- Hex code (e.g., #3B82F6)

**Secondary Color:**
- Color name (e.g., "Golden Amber", "Electric Purple")
- Hex code

**Accent Color:**
- Color name (e.g., "Emerald", "Neon Mint")
- Hex code

**Brand Mood (for AI image generation):**
- Mood keywords (e.g., "professional, trustworthy, premium" or "bold, creative, energetic")

### Step 2: Update Brand Guidelines

Edit `docs/brand-guidelines.md`:

1. **Quick Reference table**: update color names and hex codes
2. **Brand Concept section**: update theme name and description
3. **Color Palette section**: update Primary, Secondary, and Accent colors with shades
4. **AI Image Generation section**: update base prompt, keywords, and mood descriptors

### Step 3: Sync to Design Tokens

Preview first, then write (run from the project root):
```bash
node .agents/skills/managing-brands/scripts/sync-brand-to-tokens.cjs --dry-run
node .agents/skills/managing-brands/scripts/sync-brand-to-tokens.cjs
```

This will:
- Update `assets/design-tokens.json` with the new color names and values
- Regenerate `assets/design-tokens.css` with the correct CSS variables (via the `building-design-systems` skill)

### Step 4: Verify Sync

Confirm all files are updated:
```bash
# Check brand context extraction
node .agents/skills/managing-brands/scripts/inject-brand-context.cjs --json | head -30

# Check CSS variables
grep "primary" assets/design-tokens.css | head -5
```

### Step 5: Report

Output summary:
- Theme: [name]
- Primary: [name] ([hex])
- Secondary: [name] ([hex])
- Accent: [name] ([hex])
- Files updated: brand-guidelines.md, design-tokens.json, design-tokens.css

## Files Modified

| File | Purpose |
|------|---------|
| `docs/brand-guidelines.md` | Human-readable brand documentation |
| `assets/design-tokens.json` | Token definitions (primitive→semantic→component) |
| `assets/design-tokens.css` | CSS variables for UI components |

## Skills Used

- `managing-brands`: brand context extraction and sync
- `building-design-systems`: token generation

## Example Requests

- "Update the brand colors" (interactive: gather all input in Step 1)
- "Switch the brand to Ocean Professional" (theme hint)
- "Use the midnight purple preset" (quick preset)

## Color Presets

If the user names a preset, use these defaults:

| Preset | Primary | Secondary | Accent |
|--------|---------|-----------|--------|
| ocean-professional | #3B82F6 Ocean Blue | #F59E0B Golden Amber | #10B981 Emerald |
| electric-creative | #FF6B6B Coral | #9B5DE5 Electric Purple | #00F5D4 Neon Mint |
| forest-calm | #059669 Forest Green | #92400E Warm Brown | #FBBF24 Sunlight |
| midnight-purple | #7C3AED Violet | #EC4899 Pink | #06B6D4 Cyan |
| sunset-warm | #F97316 Orange | #DC2626 Red | #FACC15 Yellow |

## Important

- **Always sync all three files.** Never update brand-guidelines.md alone.
- **Verify extraction.** Run inject-brand-context.cjs after the update to confirm.
