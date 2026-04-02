---
description: Full audit of an entire MASA layer for imports, naming, and compliance
---

# MASA Layer Audit

Perform a full architectural audit of the layer specified: "$ARGUMENTS"

If no layer is specified, audit the entire `src/` directory.

## Valid Layers

- `domain_models` — Pure data structures, no imports from other layers
- `engines` — Pure stateless business logic, no I/O
- `services` — Orchestration, coordinates engines + integrations
- `integrations` — DB repos, external API clients
- `delivery` — HTTP handlers, CLI, schemas

## Audit Steps

1. **List all files** in the target layer
2. **Check every import** — flag any that violate the dependency rule (inward-only)
3. **Check naming** — files/folders must be named after business concepts, not technical roles
4. **Check rule compliance** per layer:
   - `domain_models`: no imports from other layers, pure data
   - `engines`: no I/O, no side effects, pure functions
   - `services`: no direct DB/HTTP calls (must go through integrations)
   - `integrations`: catches infra exceptions, re-raises as domain exceptions
   - `delivery`: only validates + dispatches, no decision logic
5. **Report findings** with violation format

## Output

Provide a summary table of files checked, violations found, and an overall compliance score.

Consult `references/validation.md` for detection patterns and `references/rulesets.md` for rule details.
