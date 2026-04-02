---
description: Explain a specific MASA ruleset with language-specific examples
disable-model-invocation: true
---

# MASA Rule Explanation

Explain the MASA rule or concept: "$ARGUMENTS"

## Available Rules

1. **Data Dressing** — Raw external types forbidden in business logic
2. **Static Dependency Tracing** — All deps via constructor injection
3. **Anemic Delivery** — Handlers only validate + dispatch
4. **Semantic Error Handling** — Infra exceptions caught in integrations
5. **ID Encapsulation** — Domain IDs everywhere, DB auto-increments stay in repos

## Also Explain

- **Pillars** (Modularity, Agency, Semantics, Architecture)
- **Layers** (domain_models, engines, services, integrations, delivery)
- **Dependency Rule** (inward-only imports)

## Output

1. Explain the rule in plain language
2. Show why it matters for agent cognizability
3. Provide a **bad example** (violation) and a **good example** (compliant)
4. If the user's project language is known, use that language; otherwise show examples in Python

Consult `references/pillars.md` for pillar details and `references/rulesets.md` for rule examples in all three languages.
