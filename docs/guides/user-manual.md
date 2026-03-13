# Aivyx User Manual

Complete reference for all Aivyx CLI commands.

## Core Commands

### `aivyx init`
Initialize Aivyx for the first time. Creates your encrypted data directory and configures your LLM provider.

### `aivyx run <agent> "<prompt>"`
Single-turn interaction. Ask a question, get an answer.

```bash
aivyx run assistant "Explain closures in Rust"
aivyx run researcher "What are the latest developments in quantum computing?"
aivyx run coder "Review this function for bugs" --file src/main.rs
```

### `aivyx chat <agent>`
Multi-turn interactive conversation with memory.

```bash
aivyx chat assistant
```

### `aivyx tui <agent>`
Full-screen terminal UI with sessions, markdown rendering, and vim-style keybindings.

```bash
aivyx tui assistant
```

### `aivyx voice <agent>`
Real-time voice conversation. Requires a microphone and speaker.

```bash
aivyx voice assistant
```

## Configuration

### `aivyx config set <key> <value>`
Set a configuration value.

```bash
aivyx config set provider ollama
aivyx config set ollama.model llama3.2
aivyx config set autonomy medium     # low, medium, high
```

### `aivyx config get <key>`
Read a configuration value.

### `aivyx config list`
Show all current configuration.

## Secrets

### `aivyx secret set <name>`
Store a secret (API key, token, etc.) in the encrypted store. You'll be prompted to enter the value.

```bash
aivyx secret set OPENAI_API_KEY
aivyx secret set ANTHROPIC_API_KEY
```

### `aivyx secret list`
List stored secret names (values are never displayed).

### `aivyx secret delete <name>`
Remove a stored secret.

## Memory

### `aivyx memory search "<query>"`
Search your agent's encrypted knowledge graph.

### `aivyx memory stats`
Show memory usage statistics.

### `aivyx memory export`
Export memories as encrypted JSON.

## Skills

### `aivyx run <agent> --skill <skill-name>`
Run with a specific skill active.

```bash
aivyx run assistant --skill code-review
aivyx run assistant --skill security-audit
aivyx run assistant --skill deep-research
```

### `aivyx skill list`
List all available skills.

### `aivyx skill create <name>`
Scaffold a new custom skill.

## MCP Tools

### `aivyx mcp add <name> --command "<cmd>"`
Register an MCP server.

```bash
aivyx mcp add github --command "npx -y @modelcontextprotocol/server-github"
aivyx mcp add filesystem --command "npx -y @modelcontextprotocol/server-filesystem ~/Documents"
```

### `aivyx mcp list`
List registered MCP servers.

### `aivyx mcp remove <name>`
Remove an MCP server.

## Agents

### `aivyx agent list`
List all available agents.

### `aivyx agent create <name> --role <role>`
Create a new agent with a specific role.

```bash
aivyx agent create mybot --role assistant
```

## Maintenance

### `aivyx backup`
Create an encrypted backup of all data.

### `aivyx audit verify`
Verify audit log integrity (checks for tampering).

### `aivyx self-update`
Check for and install the latest version.

## Global Flags

| Flag | Description |
|------|-------------|
| `--verbose` / `-v` | Show detailed output |
| `--quiet` / `-q` | Suppress non-essential output |
| `--config <path>` | Use alternative config file |
| `--no-color` | Disable colored output |
