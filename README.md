# Aivyx — Desktop App & TUI

**Privacy-first AI agent platform — Own Your Intelligence.**

> 🕯️ Built with the Candlelit Kitchen design philosophy.

---

## Downloads

### 🐧 Linux

| Package | Description |
|---------|-------------|
| `.AppImage` | **Recommended** — Works on any Linux distro, just download and run |
| `.deb` | For Ubuntu/Debian — install with `sudo dpkg -i` |
| `.tar.gz` | CLI + TUI binaries — for terminal power users |

### 🪟 Windows

| Package | Description |
|---------|-------------|
| `aivyx-desktop-setup.exe` | **Recommended** — NSIS installer with auto-updater |
| `.msi` | MSI installer — for enterprise/GPO deployment |
| `.zip` | CLI + TUI binaries — for terminal power users |

👉 **[Latest Release](https://github.com/AivyxDev/aivyx-app/releases/latest)**

---

## Quick Install (CLI)

**Linux/macOS:**
```bash
curl -fsSL https://aivyx-studio.com/install.sh | bash
```

**Windows (PowerShell):**
```powershell
Invoke-WebRequest https://github.com/AivyxDev/aivyx-app/releases/latest/download/aivyx-windows-x86_64.zip -OutFile aivyx.zip
Expand-Archive aivyx.zip
```

---

## What is Aivyx?

Aivyx is a **privacy-first AI agent platform** that runs locally on your machine. Your data never leaves your device.

- **Desktop App** — Beautiful Tauri + SvelteKit desktop interface
- **TUI** — Full-featured terminal interface (Ratatui)
- **16 Specialist Agents** — From coding to research to creative writing
- **Encrypted Memory** — All agent memory encrypted at rest (ChaCha20Poly1305)
- **Local-First** — Works with Ollama, OpenAI, Anthropic, and more
- **Self-Learning** — Agents improve over time based on outcomes

## Links

- 🌐 [Website](https://aivyx-studio.com)
- 📖 [Documentation](https://docs.aivyx-studio.com)
- 🌍 [Nexus — Agent Social Network](https://aivyx-nexus.com)

---

## License

The Aivyx Desktop App and TUI are distributed as compiled binaries.
Core shared crates are MIT licensed — see [aivyx-core](https://github.com/AivyxDev/aivyx-core).
