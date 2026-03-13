# Getting Started with Aivyx

This guide walks you through installing Aivyx and having your first conversation with an AI agent.

## Prerequisites

- **Linux** (x86_64) or **Windows** (x86_64)
- An LLM provider: [Ollama](https://ollama.ai) (local, free), OpenAI, Anthropic, or Google Gemini

## Installation

### Option 1: Desktop App (Recommended)

Download the latest release from the [Releases page](https://github.com/AivyxDev/aivyx-app/releases/latest).

**Linux:**
- `.AppImage` — Works on any distro. Right-click → Properties → Allow executing → double-click.
- `.deb` — For Ubuntu/Debian: `sudo dpkg -i aivyx-desktop.deb`

**Windows:**
- `.exe` installer — Recommended. Includes auto-updater.
- `.msi` — For enterprise/GPO deployment.

### Option 2: CLI + TUI

Download the tarball from the [Releases page](https://github.com/AivyxDev/aivyx-app/releases/latest):

```bash
# Linux
tar xzf aivyx-linux-x86_64.tar.gz
sudo mv aivyx-cli /usr/local/bin/aivyx
sudo mv aivyx-tui /usr/local/bin/aivyx-tui
```

### Option 3: Install Script

```bash
curl -fsSL https://aivyx-studio.com/install.sh | bash
```

## First-Time Setup

Run the initialization wizard:

```bash
aivyx init
```

This will:
1. Create your encrypted data directory (`~/.aivyx`)
2. Ask you to choose an LLM provider
3. Set your encryption passphrase
4. Bootstrap your first agent

### Setting Up Ollama (Local, Free)

```bash
# Install Ollama
curl -fsSL https://ollama.ai/install.sh | sh

# Pull a model
ollama pull llama3.2

# Configure Aivyx to use it
aivyx config set provider ollama
aivyx config set ollama.model llama3.2
```

### Setting Up a Cloud Provider

```bash
# OpenAI
aivyx config set provider openai
aivyx secret set OPENAI_API_KEY

# Anthropic
aivyx config set provider anthropic
aivyx secret set ANTHROPIC_API_KEY

# Google Gemini
aivyx config set provider gemini
aivyx secret set GEMINI_API_KEY
```

API keys are stored in Aivyx's encrypted secret store — never in plaintext.

## Your First Conversation

```bash
# Single question
aivyx run assistant "What is the Rust ownership model?"

# Interactive chat
aivyx chat assistant

# Terminal UI (recommended)
aivyx tui assistant
```

## Next Steps

- Read the [User Manual](user-manual.md) for all CLI commands
- Try [Skills](skills-guide.md) for specialized tasks
- Connect [MCP tools](mcp-guide.md) for external integrations
- Explore the [Desktop App](desktop-app.md)
