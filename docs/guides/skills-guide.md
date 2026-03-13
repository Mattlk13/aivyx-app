# Skills Guide

Skills are structured capability packages that give your agent specialized behavior for specific tasks.

## Using Built-in Skills

Aivyx includes built-in skills for common tasks:

```bash
aivyx run assistant --skill <skill-name>
```

### Available Skills

| Skill | Description |
|-------|-------------|
| `code-review` | Analyze code for bugs, security issues, and improvements |
| `security-audit` | Scan projects for vulnerabilities and unsafe patterns |
| `deep-research` | Multi-step web research with source synthesis |
| `data-analysis` | Analyze datasets, generate insights and visualizations |
| `tech-writing` | Technical documentation and README generation |
| `refactor` | Suggest and apply code refactoring patterns |
| `debug` | Systematic debugging with hypothesis testing |
| `test-gen` | Generate unit and integration tests |
| `architecture` | Design system architecture and component diagrams |
| `api-design` | Design REST/GraphQL APIs with OpenAPI specs |
| `migration` | Database schema migrations and data transformations |
| `performance` | Profile and optimize code performance |

### Examples

```bash
# Review a Rust project for issues
aivyx run coder --skill code-review

# Research a topic in depth
aivyx run researcher --skill deep-research "Explain WebTransport vs WebSocket"

# Generate tests for a file
aivyx run coder --skill test-gen --file src/auth.rs
```

## Creating Custom Skills

Scaffold a new skill:

```bash
aivyx skill create my-skill
```

This creates a directory with a `SKILL.md` manifest:

```
skills/
└── my-skill/
    └── SKILL.md
```

### SKILL.md Format

A skill manifest defines the agent's behavior:

```yaml
---
name: my-skill
description: What this skill does
tools:
  - web_search
  - file_read
  - file_write
---

## System Prompt

You are a specialist in [domain]. When the user asks you to...

## Instructions

1. First, analyze the request...
2. Then, research relevant information...
3. Finally, produce a structured output...
```

### Key Fields

- **name**: Unique identifier for the skill
- **description**: Human-readable summary
- **tools**: List of tools the agent can use while this skill is active
- **System Prompt**: Instructions that shape the agent's behavior

## Skill Discovery

List all available skills (built-in and custom):

```bash
aivyx skill list
```

Custom skills are loaded from `~/.aivyx/skills/`.
