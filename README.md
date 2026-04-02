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

### Claude Code (Plugin)

Install as a Claude Code plugin for the best experience — includes slash commands and auto-invoked skills:

```bash
# Install from the official Claude Code marketplace (in review)
/plugin install masa

# Or add from the GitHub marketplace manually
/plugin marketplace add nicolasfmelo/masa-skill
/plugin install masa@masa-skill
```

Once installed, you get these slash commands:

| Command | What It Does |
|---------|-------------|
| `/masa:new-feature [description]` | Walk through the 5-step protocol for a new feature |
| `/masa:validate` | Audit current code for MASA compliance |
| `/masa:audit [layer]` | Full audit of a layer's imports, naming, and compliance |
| `/masa:refactor` | Propose a MASA-compliant refactoring |
| `/masa:explain [rule]` | Explain a ruleset with language-specific examples |
| `/masa:scaffold [language]` | Generate the full MASA directory skeleton |

Plus, the **masa-framework** skill is auto-invoked by Claude when it detects architecture-related tasks.

#### Example Use Cases

```bash
# Scaffold a new Python project with the full MASA directory structure
/masa:scaffold python

# Implement a new feature following the 5-layer protocol
/masa:new-feature create JWT authentication system

# Audit the services layer for dependency violations
/masa:audit services

# Check if the current file follows MASA rules
/masa:validate

# Refactor legacy code toward MASA compliance
/masa:refactor

# Learn about a specific rule with code examples
/masa:explain data-dressing
```

### Claude Code (Standalone)

If you prefer not to use the plugin, add the skill as project instructions:

```bash
# Copy to your project
cp SKILL.md your-project/SKILL.md

# Reference it in your CLAUDE.md or project instructions
echo "Follow the architecture rules in SKILL.md" >> your-project/CLAUDE.md
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
├── .claude-plugin/
│   └── plugin.json                   # Claude Code plugin manifest
├── commands/                         # User-invocable slash commands (/masa:*)
│   ├── new-feature.md
│   ├── validate.md
│   ├── audit.md
│   ├── refactor.md
│   ├── explain.md
│   └── scaffold.md
├── skills/
│   └── masa-framework/
│       └── SKILL.md                  # Auto-invoked skill (model-triggered)
├── SKILL.md                          # Standalone skill file (for non-plugin agents)
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
| **`.claude-plugin/plugin.json`** | Plugin manifest for Claude Code | Plugin installation |
| **`commands/*.md`** | Slash commands (`/masa:new-feature`, etc.) | User-invoked commands |
| **`skills/masa-framework/SKILL.md`** | Auto-invoked skill — Claude uses it automatically | Architecture tasks |
| **`SKILL.md`** | Standalone skill file for non-plugin agents | Copilot, Codex, etc. |
| `references/pillars.md` | Detailed explanation of the four architectural pillars | Deep understanding |
| `references/rulesets.md` | Five rulesets with code examples in Python, TS, Go | Implementing features |
| `references/validation.md` | Violation catalog with detection patterns | Code review / auditing |
| `references/task-execution-protocol.md` | Step-by-step workflow for implementing features | New feature development |
| `references/languages/*.md` | Language-specific conventions and project layouts | Starting a new project |

> **Plugin users:** Just install the plugin — everything works automatically.
> **Non-plugin users:** Load `SKILL.md` into your agent. The references are supplementary.

## Available Commands

Once the plugin is installed (or skill is loaded), these commands are available:

| Command | What It Does |
|---------|-------------|
| `/masa:new-feature [description]` | Walk through the 5-step protocol for a new feature |
| `/masa:validate` | Audit current code for MASA compliance |
| `/masa:audit [layer]` | Full audit of a layer's imports, naming, and compliance |
| `/masa:refactor` | Propose a MASA-compliant refactoring |
| `/masa:explain [rule]` | Explain a ruleset with language-specific examples |
| `/masa:scaffold [language]` | Generate the full MASA directory skeleton |

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
