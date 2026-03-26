# MASA Skill — AI Agent Instruction Set

> Teach your AI coding agent the **Modular Agentic Semantic Architecture** (MASA) — a framework that maximizes how well agents can understand, navigate, and safely modify your codebase.

📄 **Read the full study:** [www.masa-framework.org](https://www.masa-framework.org/)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## What Is This?

This repository contains the **MASA skill file** — a structured instruction set that you load into AI coding agents so they follow MASA architectural patterns when writing, reviewing, or refactoring code.

When an agent has this skill loaded, it will:

- **Scaffold** new projects with the correct 5-layer structure
- **Enforce** unidirectional dependency rules between layers
- **Name** files and functions with semantic intent (not technical jargon)
- **Isolate** infrastructure from business logic automatically
- **Detect** architectural violations before they ship

### Supported Languages

- Python
- JavaScript / TypeScript
- Go

## Quick Start

### GitHub Copilot (Custom Instructions)

1. Copy `SKILL.md` to your project root (or `.github/copilot-instructions.md`):

```bash
# Option A: As a project-level skill file
cp SKILL.md your-project/.github/copilot-instructions.md

# Option B: As a standalone file referenced in settings
cp SKILL.md your-project/SKILL.md
```

2. Copilot will automatically pick up the instructions and apply MASA patterns when generating code in that project.

> **Tip:** For VS Code, you can also add it to your workspace settings under `github.copilot.chat.codeGeneration.instructions`.

### Claude Code (Anthropic)

Add the skill as project instructions:

```bash
# Copy to your project
cp SKILL.md your-project/SKILL.md

# Reference it in your CLAUDE.md or project instructions
echo "Follow the architecture rules in SKILL.md" >> your-project/CLAUDE.md
```

Or load it directly in a conversation:

```bash
# In Claude Code CLI
claude --project-instructions SKILL.md
```

### OpenAI Codex

Load the skill as a system-level or project-level instruction:

```bash
# Copy the skill file into your project
cp SKILL.md your-project/SKILL.md

# Reference in your AGENTS.md
echo "Follow the architecture defined in SKILL.md for all code generation." >> your-project/AGENTS.md
```

Codex will use the SKILL.md as architectural context when generating or modifying code within the project.

### Any Other AI Agent

The skill file is plain Markdown with structured rules. You can integrate it with any agent that accepts system prompts or instruction files:

```
Include the contents of SKILL.md in your agent's system prompt or project-level context.
```

## Repository Structure

```
masa-skill/
├── SKILL.md                          # Main skill file (load this into your agent)
├── references/
│   ├── pillars.md                    # The Four Pillars — deep dive
│   ├── rulesets.md                   # Five Agentic Rulesets with examples
│   ├── task-execution-protocol.md    # Step-by-step feature implementation workflow
│   ├── validation.md                 # Violation detection catalog
│   └── languages/
│       ├── python.md                 # Python-specific patterns
│       ├── javascript.md             # JavaScript/TypeScript patterns
│       └── go.md                     # Go patterns
├── LICENSE                           # MIT
└── README.md                         # This file
```

### What Each File Does

| File | Purpose | When to Use |
|------|---------|-------------|
| **`SKILL.md`** | Core skill — all rules, commands, and validation logic | **Always load this** |
| `references/pillars.md` | Detailed explanation of the four architectural pillars | Deep understanding |
| `references/rulesets.md` | Five rulesets with code examples in Python, TS, Go | Implementing features |
| `references/validation.md` | Violation catalog with detection patterns | Code review / auditing |
| `references/task-execution-protocol.md` | Step-by-step workflow for implementing features | New feature development |
| `references/languages/*.md` | Language-specific conventions and project layouts | Starting a new project |

> **Minimum setup:** Just load `SKILL.md`. The references are supplementary — the agent will consult them when needed.

## Available Commands

Once the skill is loaded, the agent responds to these commands:

| Command | What It Does |
|---------|-------------|
| `/masa:new-feature` | Implement a feature following MASA layer rules |
| `/masa:validate` | Check current code for architectural violations |
| `/masa:audit` | Full audit of imports, naming, and layer compliance |
| `/masa:refactor` | Refactor existing code toward MASA patterns |

## The MASA Architecture at a Glance

```
┌─────────────────────────────────────────────┐
│  Delivery        HTTP handlers, CLI, events │
├─────────────────────────────────────────────┤
│  Services        Orchestration, workflows   │
├─────────────────────────────────────────────┤
│  Engines         Pure business logic        │
├─────────────────────────────────────────────┤
│  Integrations    DB repos, API clients      │
├─────────────────────────────────────────────┤
│  Domain Models   Entities, value objects     │
└─────────────────────────────────────────────┘
```

**Dependency rule:** each layer may only import from layers below it.

## Empirical Evidence

MASA has been empirically evaluated against DDD/Clean Architecture baselines across three complexity tiers (low, medium, high) with multiple AI model tiers. Key findings:

- **+30–35% improvement** in composite cognizability score
- **0 architectural violations** (vs. 1–22 in baselines)
- **100% task pass rate** maintained in both architectures

Full experiment data, reproduction instructions, and analysis are available in the companion research repository: **[nicolasfmelo/masa-framework](https://github.com/nicolasfmelo/masa-framework)**

## Contributing

Contributions, critiques, and empirical evaluations are welcome. Open a discussion, submit a pull request, or reach out directly.

## License

[MIT](LICENSE)
