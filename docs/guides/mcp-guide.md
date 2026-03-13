# MCP Integration Guide

Aivyx supports the [Model Context Protocol (MCP)](https://modelcontextprotocol.io) for connecting external tools and data sources to your agents.

## What is MCP?

MCP is an open standard that lets AI agents interact with external services through a unified protocol. Instead of building custom integrations, you connect MCP servers that expose tools your agent can use.

## Adding MCP Servers

```bash
aivyx mcp add <name> --command "<command>"
```

### Popular MCP Servers

```bash
# GitHub — repos, issues, PRs, code search
aivyx mcp add github --command "npx -y @modelcontextprotocol/server-github"

# Filesystem — read/write files in a directory
aivyx mcp add files --command "npx -y @modelcontextprotocol/server-filesystem ~/Documents"

# Brave Search — web search via Brave API
aivyx mcp add brave --command "npx -y @modelcontextprotocol/server-brave-search"

# SQLite — query local databases
aivyx mcp add db --command "npx -y @modelcontextprotocol/server-sqlite ~/data.db"

# Slack — messages, channels
aivyx mcp add slack --command "npx -y @modelcontextprotocol/server-slack"
```

### Setting Environment Variables for MCP Servers

Some servers need API keys. Set them as environment variables before running:

```bash
# For servers that need API keys
export GITHUB_TOKEN="your-token"
aivyx mcp add github --command "npx -y @modelcontextprotocol/server-github"
```

Or use Aivyx's encrypted secret store and reference secrets in your config.

## Managing MCP Servers

```bash
# List all registered servers
aivyx mcp list

# Remove a server
aivyx mcp remove github

# Test a server connection
aivyx mcp test github
```

## How It Works

1. When you register an MCP server, Aivyx stores the command in your config
2. When an agent needs external tools, Aivyx starts the MCP server process
3. Tools are discovered automatically via the MCP protocol
4. The agent can call tools just like built-in ones
5. Results are cached (5-minute TTL) to minimize redundant calls

## Transport Types

Aivyx supports two MCP transport types:

- **stdio** (default) — Communicates via stdin/stdout with a local process
- **SSE** — Connects to a remote HTTP server using Server-Sent Events

```bash
# Remote SSE server
aivyx mcp add remote-tools --url "https://mcp.example.com/sse"
```

## Using MCP Tools in Conversations

Once registered, MCP tools appear automatically in your agent's tool list:

```bash
aivyx chat assistant
# Agent now has access to GitHub, filesystem, etc.
```

The agent decides when to use external tools based on your request.
