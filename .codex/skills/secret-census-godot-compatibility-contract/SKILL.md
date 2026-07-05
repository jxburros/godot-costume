---
name: secret-census-godot-compatibility-contract
description: "Use when changing the Secret Census `.census.json` export contract, `GODOT_COMPATIBILITY.md`, Godot importer mappings, Festival resources, ID semantics, format versions, or excluded secret fields."
---

# Secret Census to Godot Compatibility Contract

## Best-Fit Repositories

- `Secret-Census`
- `godot-costume`
- `Costume-Game-2`

## Godot Export Contract Map

- Export owner: `Secret-Census/src/lib/godot-export.ts`; contract tests live in `Secret-Census/tests/godot-export.test.ts`.
- Type source of truth: `Secret-Census/src/types.ts`; v1 exports records mostly verbatim, stripping visual/audio fields such as `imageUrl`.
- Locked top-level v1 shape: `format`, `formatVersion`, `exportedAt`, `game`, `settings`, `npcs`, `locations`, `items`, `outfits`, `plotHooks`, and `events`.
- Locked format values: `format` is `secret-census-world`; `formatVersion` is `1`.
- Locked record families: `NPC`, `Location`, `Item`, `Outfit`, `PlotHook`, and `GameEvent`, plus nested `Rumor`, `Relationship`, `CustomField`, `DialogueEntry`, `LocationOption`, and `StageAvailability`.
- Excluded fields: provider keys, sync credentials, tokens, raw model/provider settings, and v1 visual/audio content.

## Workflow

- Read both contract copies: `Secret-Census/GODOT_COMPATIBILITY.md` and `godot-costume/modules/festival/SECRET_CENSUS_COMPATIBILITY.md` when available.
- Classify every field change as locked, optional additive, excluded, or breaking version bump.
- Update exporter and importer together for breaking changes, and keep neutral defaults for partial worlds.
- Preserve stable opaque IDs and resource class/property mappings.

## Guardrails

- Do not bump `formatVersion` without importer support.
- Do not rename, remove, or change meaning of locked fields casually.
- Do not include visual/audio content or credentials in version 1 unless the contract is intentionally extended.

## Validation

- Generate a sample `.census.json`.
- Import it in Godot or validate against importer expectations.
- Diff both contract docs for sync.
