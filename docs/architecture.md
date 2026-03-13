# Aivyx Architecture

Aivyx is built as a modular Rust application with a three-repository design.

## Repository Structure

| Repository | Purpose | Visibility |
|------------|---------|------------|
| [aivyx-app](https://github.com/AivyxDev/aivyx-app) | Desktop app, TUI, and CLI releases | Public |
| [aivyx-core](https://github.com/AivyxDev/aivyx-core) | Shared Rust crates (10 crates) | Public |
| aivyx | Engine, server, and orchestration | Private |

## How It Works

```
┌──────────────────────────────────────────────┐
│                  Interfaces                   │
│   Desktop (Tauri)  │  TUI  │  CLI  │  Voice  │
├──────────────────────────────────────────────┤
│                  Engine API                   │
│         REST + WebSocket (90+ endpoints)      │
├──────────────────────────────────────────────┤
│              Agent Orchestration              │
│   Memory │ Skills │ Tools │ Team Sessions     │
├──────────────────────────────────────────────┤
│            Encrypted Storage Layer            │
│   ChaCha20Poly1305  │  HKDF-SHA256 keys      │
├──────────────────────────────────────────────┤
│               LLM Providers                   │
│  Ollama (local) │ OpenAI │ Anthropic │ Gemini │
└──────────────────────────────────────────────┘
```

## Core Crates (aivyx-core)

The shared foundation is split into 10 focused crates:

| Crate | Purpose |
|-------|---------|
| `aivyx-agent` | Agent profiles, capabilities, and tool definitions |
| `aivyx-config` | Configuration, skill manifests, and settings |
| `aivyx-crypto` | Encryption (ChaCha20Poly1305), key derivation (HKDF-SHA256) |
| `aivyx-llm` | Multi-provider LLM abstraction (Ollama, OpenAI, Anthropic, Gemini) |
| `aivyx-memory` | Knowledge graph, semantic triples, vector search |
| `aivyx-mcp` | Model Context Protocol client (stdio + SSE transports) |
| `aivyx-storage` | Encrypted SQLite storage layer |
| `aivyx-tools` | Built-in tool implementations (46+ tools) |
| `aivyx-types` | Shared type definitions |
| `aivyx-audit` | HMAC-authenticated audit logging |

## Key Design Principles

1. **Privacy by default** — All data encrypted at rest with user-derived keys
2. **Local-first** — Full functionality without internet (using Ollama)
3. **Modular** — Each crate has a single, well-defined responsibility
4. **Zero telemetry** — No analytics, no tracking, no phone-home
5. **Capability-based security** — Agents can only use tools explicitly granted to them
