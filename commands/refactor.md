---
description: Propose a MASA-compliant refactoring of the current code
---

# MASA Refactoring

Analyze the current code and propose a MASA-compliant refactoring plan.

## Process

1. **Identify violations** — scan the code for all MASA rule violations
2. **Map current structure** — document where code currently lives and its dependencies
3. **Design target structure** — show the correct MASA layer placement for each component
4. **Plan migration steps** — ordered list of changes, respecting the 5-layer dependency rule
5. **Generate refactored code** — produce all affected files with correct layer placement

## Key Principles

- Move code to the correct layer, don't just rename it
- Dress raw external types at boundaries — never let them leak into business logic
- Extract pure logic into engines, orchestration into services
- Make all dependencies explicit constructor parameters
- Name everything after business concepts

## Output

For each change:
1. State which layer the file moves to/from and why
2. Show imports explicitly (they are the primary compliance signal)
3. After generating, confirm all MASA rules are satisfied

Never propose a "quick fix" that violates layer boundaries — always show the correct layered solution.

Consult `references/rulesets.md` for rule details and `references/task-execution-protocol.md` for implementation order.
