---
description: Generate the full MASA directory skeleton for a language
---

# MASA Project Scaffold

Generate the complete MASA directory structure for the language: "$ARGUMENTS"

If no language is specified, ask the user which language to use (Python, JavaScript/TypeScript, or Go).

## Directory Structure to Generate

```text
/src
├── /domain_models      # Pure data structures — no imports from other layers
├── /engines            # Pure stateless business logic — no I/O
├── /services           # Orchestration — coordinates engines + integrations
├── /integrations
│   ├── /database
│   │   ├── /models     # ORM/DB schemas — never leave this folder
│   │   └── /repos      # Translate DB models → domain models
│   └── /external_apis  # Third-party service clients
└── /delivery
    ├── /http            # Thin route handlers — validate + dispatch only
    └── /schemas         # API DTOs — never leave this folder
```

## For Each Directory

1. Create the directory with an appropriate init/index file
2. Add a brief comment explaining the layer's purpose and rules
3. Include a sample file demonstrating the correct pattern for that layer

## Language-Specific

Load the appropriate language guide from `references/languages/` for:
- Python: `references/languages/python.md`
- JavaScript/TypeScript: `references/languages/javascript.md`
- Go: `references/languages/go.md`

Follow the language-specific conventions for project layout, dependency injection patterns, and file naming.
