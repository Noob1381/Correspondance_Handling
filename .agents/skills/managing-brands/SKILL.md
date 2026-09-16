---
name: managing-brands
description: Provides brand-management frameworks and tooling for brand voice, visual identity, messaging, logo usage, asset naming and approval, color and typography specs, and syncing brand guidelines into design tokens. Use when creating or updating brand guidelines, defining tone of voice, auditing brand consistency, validating or organizing brand assets, extracting colors from images, or when the user mentions brand guidelines, style guide, brand voice, messaging framework, or brand compliance.
---

# Managing Brands

Frameworks, a starter template, and Node scripts for defining a brand and keeping everything consistent with it. Adapted from [ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) `brand` (MIT, see `LICENSE`).

## When to use this skill
- Creating brand guidelines, or updating brand colors, fonts, or tone.
- Writing messaging frameworks or voice/tone rules.
- Reviewing copy, assets, or UI for brand compliance.
- Organizing, naming, validating, or approving brand assets.
- Syncing brand colors into design tokens / CSS variables.

## Precedence
- If the `brand-identity` skill applies to the project, it is the source of truth for that brand's values (colors, fonts, voice). Use this skill for process and frameworks only. Never overwrite brand-identity values with presets or invented values.
- Never invent brand rules. Use only what the user supplied or what already exists in the project's guidelines.

## Project files this skill works with

| File | Role |
|------|------|
| `docs/brand-guidelines.md` | Human-readable source of truth |
| `assets/design-tokens.json` | Token definitions (primitive → semantic → component) |
| `assets/design-tokens.css` | Generated CSS variables |

## Workflow

Pick the task and copy its checklist.

**New brand guidelines**
```markdown
- [ ] Copy templates/brand-guidelines-starter.md → docs/brand-guidelines.md
- [ ] Fill it in with the user (voice, visual identity, color, typography, logo, messaging; see Resources)
- [ ] Preview the token sync with --dry-run, then run it
- [ ] Verify with inject-brand-context.cjs --json
```

**Update brand colors/theme**: follow [`references/update.md`](references/update.md).

**Review / audit**
```markdown
- [ ] Read docs/brand-guidelines.md (or the brand-identity skill)
- [ ] Walk references/consistency-checklist.md; for assets also references/approval-checklist.md
- [ ] Validate assets with validate-asset.cjs; compare image colors with extract-colors.cjs
- [ ] Report each issue with file, rule broken, and fix
```

## Instructions

### Running the scripts
- Requires Node.js (built-in modules only).
- Run from the **project root**. The scripts read and write `docs/` and `assets/` relative to the working directory.
- Paths below assume this skill is at `.agents/skills/managing-brands/`. Otherwise use the absolute path to this skill directory.
- If flags are unclear, read the usage comment at the top of the script. Do not edit the scripts to work around errors.

```bash
node .agents/skills/managing-brands/scripts/inject-brand-context.cjs           # brand summary for prompts
node .agents/skills/managing-brands/scripts/inject-brand-context.cjs --json
node .agents/skills/managing-brands/scripts/validate-asset.cjs <asset-path>    # naming, size, format
node .agents/skills/managing-brands/scripts/extract-colors.cjs --palette       # print brand palette
node .agents/skills/managing-brands/scripts/extract-colors.cjs <image-path>    # compare image to palette
```

### Syncing guidelines → tokens (validate before writing)
```bash
node .agents/skills/managing-brands/scripts/sync-brand-to-tokens.cjs --dry-run   # 1. preview
node .agents/skills/managing-brands/scripts/sync-brand-to-tokens.cjs             # 2. write
```
- Always dry-run first when `assets/design-tokens.json` already exists, and show the user what changes.
- Writes `assets/design-tokens.json`, then regenerates `assets/design-tokens.css` with the `building-design-systems` skill's `generate-tokens.cjs`. That skill must be installed as a sibling folder.
- Never update `docs/brand-guidelines.md` alone. Keep all three files in sync.

## Resources

| Topic | File |
|-------|------|
| Update brand (workflow + presets) | [`references/update.md`](references/update.md) |
| Voice & tone | [`references/voice-framework.md`](references/voice-framework.md) |
| Visual identity | [`references/visual-identity.md`](references/visual-identity.md) |
| Messaging | [`references/messaging-framework.md`](references/messaging-framework.md) |
| Color palette management | [`references/color-palette-management.md`](references/color-palette-management.md) |
| Typography specs | [`references/typography-specifications.md`](references/typography-specifications.md) |
| Logo usage | [`references/logo-usage-rules.md`](references/logo-usage-rules.md) |
| Asset organization | [`references/asset-organization.md`](references/asset-organization.md) |
| Consistency checklist | [`references/consistency-checklist.md`](references/consistency-checklist.md) |
| Approval checklist | [`references/approval-checklist.md`](references/approval-checklist.md) |
| Guideline doc structure | [`references/brand-guideline-template.md`](references/brand-guideline-template.md) |
| Starter guidelines doc | [`templates/brand-guidelines-starter.md`](templates/brand-guidelines-starter.md) |

Related skills: `building-design-systems` (tokens), `designing-brand-assets` (logos, banners, social images), `designing-ui-ux`.
