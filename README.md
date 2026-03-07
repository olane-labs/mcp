# Olane MCP Server

Claude Code plugin for [Olane](https://olane.com) — ontology graph-powered development context.

## Installation

```bash
# Install the Olane CLI first
brew install olane-labs/tap/olane
# or: npm install -g @olane/o-cli

# Authenticate
olane login
olane setup

# In Claude Code:
/plugin marketplace add olane-labs/mcp
/plugin install olane@olane
```

## Tools

| Tool | Description |
|------|-------------|
| `check_project_status` | Check project indexing and authentication state |
| `ingest_code` | Ingest source code into the knowledge graph |
| `ingest_text` | Ingest text into the knowledge graph |
| `cosync_analyze` | Analyze entities with confidence scoring |
| `cosync_question` | Ask questions about the ontology |
| `search_entities` | Search for entities in the knowledge graph |
| `get_score` | Get cosync scores for entities |
| `get_task_cosync` | Get cosync context for a task |
| `get_learning_requests` | Get learning requests for low-scoring entities |

## How It Works

The plugin runs `olane copass --mcp` which starts a unified MCP server over stdio. All authentication and encryption is handled by the Olane CLI — no separate local/remote servers needed.

## Requirements

- [Olane CLI](https://www.npmjs.com/package/@olane/o-cli?activeTab=readme) v2.0.0+
- An Olane account (`olane login`)

## License

MIT
