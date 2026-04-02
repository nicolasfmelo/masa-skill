---
description: Audit the current file or selection for MASA architectural compliance
---

# MASA Validation

Audit the current code for MASA compliance. Check every rule and report violations.

## Checklist

For each file or code block, verify:

1. **Layer placement** — Is the file in the correct layer directory?
2. **Dependency direction** — Does it only import from layers below it?
3. **Data Dressing** — Are raw external types (HTTP bodies, DB rows, API responses) dressed into domain models at the boundary?
4. **Static Dependency Tracing** — Are all dependencies injected via constructor? No globals, no service locators, no DI container magic?
5. **Anemic Delivery** — Do handlers only validate + dispatch? No decision logic?
6. **Semantic Error Handling** — Are infra exceptions caught in integrations and re-raised as domain exceptions?
7. **ID Encapsulation** — Are domain IDs (UUID/tags) used everywhere? No DB auto-increments leaking out?
8. **Semantic Naming** — Are files/folders named after business concepts, not technical roles?

## Output Format

For each violation found, report:

```
⚠️ MASA Violation: [Rule Name]

What's wrong: [one sentence]
Why it matters: [which agent failure mode this causes]
Fix: [specific corrective action]

[corrected code snippet]
```

If no violations are found, confirm compliance and list which rules were checked.

Consult `references/validation.md` for the full violation catalog and detection patterns.
