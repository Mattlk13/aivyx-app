# Aivyx Security Model

Aivyx is built with a security-first architecture. This document explains how your data is protected.

## Encryption at Rest

All stored data is encrypted using **ChaCha20Poly1305** authenticated encryption.

- **Key Derivation**: HKDF-SHA256 derives unique keys from your passphrase
- **Per-field encryption**: Individual data fields are encrypted separately
- **Authenticated**: Poly1305 MAC prevents undetected tampering
- **Your passphrase is never stored** — only derived key material exists in memory

## Key Management

- Keys are derived at session start when you enter your passphrase
- Key material is held in memory only for the duration of the session
- On process exit, all key material is zeroed using the `zeroize` crate
- No master key file exists on disk

## Secrets Store

API keys and tokens are stored in an encrypted secrets vault:

```bash
aivyx secret set OPENAI_API_KEY
# Value is encrypted with your session key before writing to disk
```

Secrets are decrypted only when needed and never logged or displayed.

## Audit Trail

- Every agent action is logged to an append-only audit log
- Audit entries are chained with HMAC-SHA256, creating a tamper-evident chain
- Verify integrity anytime: `aivyx audit verify`
- If any entry has been modified, the chain breaks and verification fails

## Capability-Based Security

Agents operate under a **capability model**:
- Each agent has an explicit list of permitted tools
- Agents cannot access tools not in their profile
- File system access is scoped to allowed directories
- Network access requires explicit tool grants

## Autonomy Levels

Control how much freedom your agents have:

| Level | Behavior |
|-------|----------|
| **Low** | Agent asks for approval before every action |
| **Medium** | Agent acts independently for safe operations, asks for risky ones |
| **High** | Agent acts autonomously with minimal interruption |

Set via: `aivyx config set autonomy low`

## Third-Party Providers

When using cloud LLM providers:
- Your prompts are sent to the provider you choose
- Aivyx's local encryption protects data at rest, but cannot control how providers handle data in transit
- For maximum privacy, use **Ollama** for fully local inference
- Provider API keys are stored encrypted, never in plaintext config files

## What Aivyx Does NOT Do

- ❌ No telemetry or analytics
- ❌ No crash reporting
- ❌ No usage tracking
- ❌ No phone-home requests
- ❌ No data collection of any kind
