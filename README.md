# CoSync MCP Servers

Claude Code plugin marketplace for [CoSync](https://olane.com/cosync) by [Olane](https://olane.com) — knowledge graph-powered development context.

## Installation

```bash
claude
/plugin marketplace add olane-labs/mcp
/plugin install cosync-remote@olane
/plugin install cosync-local@olane
tell claude "setup cosync"
```

## Plugins

### cosync-remote

Remote MCP server for knowledge graph ingestion, entity search, ontology analysis, and CoSync developer integration.

- **Transport:** HTTP (`https://mcp.copass.id/mcp`)
- **No local install required** — connects directly to the hosted server

**Tools:**

| Tool | Description |
|------|-------------|
| `check_project_status` | Check project indexing and authentication state |
| `ingest_code` | Ingest source code into the knowledge graph |
| `ingest_text` | Ingest text into the knowledge graph |
| `cosync_analyze` | Analyze entities with confidence scoring |
| `cosync_question` | Ask questions about the ontology |
| `search_entities` | Search for entities in the knowledge graph |
| `get_score` | Get CoSync scores for entities |
| `get_task_cosync` | Get CoSync context for a task |
| `get_learning_requests` | Get learning requests for low-scoring entities |

### cosync-local

Local encryption and project setup plugin. Session tokens and AES-256-GCM encryption — keys never leave your machine.

- **Transport:** stdio (installed via `uvx olane-cosync-local`)
- **Requires:** Python 3.10+, [uv](https://docs.astral.sh/uv/)

**Tools:**

| Tool | Description |
|------|-------------|
| `generate_session_token` | Session token via DEK wrapping (call at session start) |
| `encrypt_payload` | AES-256-GCM encrypt text |
| `encrypt_file` | AES-256-GCM encrypt a file |
| `setup_project` | Write hooks, scripts, config for a project |
| `update_auth_token` | Persist a fresh auth token to config |
| `set_cosync_encryption_key` | Write a master key (migration/team sharing) |

## Session Initialization

Both plugins work together. At the start of every session:

1. `generate_session_token` (cosync-local) — returns a session token
2. `check_project_status` (cosync-remote) — checks project indexing state
3. `setup_project` (cosync-local) — if hooks are not installed

All cosync-remote tools require the `encryption_token` from step 1. For ingestion tools, encrypt payloads first with `encrypt_payload` (cosync-local).

## License

MIT
