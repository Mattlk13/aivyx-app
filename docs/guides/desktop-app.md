# Aivyx Desktop App

The Aivyx Desktop App provides a graphical interface for interacting with your AI agents.

## Installation

Download from the [Releases page](https://github.com/AivyxDev/aivyx-app/releases/latest).

### Linux
- **AppImage** (recommended) — Works on any distro, no installation needed
- **.deb** — For Ubuntu/Debian: `sudo dpkg -i aivyx-desktop.deb`

### Windows
- **.exe installer** (recommended) — NSIS installer with auto-updater
- **.msi** — For enterprise GPO deployment

## First Launch

1. Open the app — you'll see the **Setup Wizard**
2. Choose your LLM provider (Ollama recommended for privacy)
3. Set your encryption passphrase
4. The wizard creates your encrypted data directory

## Features

### Chat Interface
- Rich markdown rendering with syntax highlighting
- Multi-session support — switch between conversations
- File attachment support
- Agent selection dropdown

### Agent Management
- View and configure your agents
- Set autonomy levels
- Manage capabilities and tools

### Settings
- LLM provider configuration
- Theme preferences
- Auto-update settings

## Auto-Updates

The desktop app checks for updates automatically. When a new version is available:
1. A notification appears in the app
2. Click to download and install
3. The app restarts with the new version

You can also check manually: Help → Check for Updates.

## Technology

The desktop app is built with:
- **Tauri v2** — Rust-based framework for lightweight desktop apps
- **SvelteKit** — Modern reactive UI framework
- **Engine sidecar** — The Aivyx engine runs as a background process managed by the app

## Troubleshooting

### App won't start
- Check that no other instance is running
- Try launching from terminal to see error messages: `aivyx-desktop`

### Engine not connecting
- The engine starts automatically with the app
- Check the logs: `~/.aivyx/logs/`

### Linux AppImage permissions
- Right-click the file → Properties → Permissions → ✅ Allow executing
- Or: `chmod +x aivyx-desktop.AppImage`
