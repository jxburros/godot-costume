---
name: festival-narrative-loop-designer
description: "Use when changing Festival of Disguises narrative puzzle loops, costumes, outfit-gated dialogue, day phase resets, weather, notebook knowledge persistence, secrets, rumors, or Gemini-powered story features."
---

# Festival Narrative Loop Designer

## Best-Fit Repositories

- `Costume-Game-2`
- `Secret-Census`
- `godot-costume`

## Workflow

- Read README gameplay model and any Secret Census compatibility docs before adding story data.
- Track each content change through location, NPC, costume/outfit, dialogue gate, notebook discovery, and reset persistence.
- Separate run-local state from accumulated notebook knowledge.
- Keep Gemini features optional and key-safe.

## Guardrails

- Do not make one costume unlock unrelated dialogue without documenting the gate.
- Do not reset persistent notebook knowledge during day-loop reset.
- Do not hardcode AI output as canonical world data without validation.

## Validation

- Run build/tests.
- Smoke one full Morning/Afternoon/Night loop.
- Verify notebook persistence across reload/reset.
