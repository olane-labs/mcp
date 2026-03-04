# CoSync MCP Servers

Claude Code plugin marketplace for [CoSync](https://copass.id) — knowledge graph-powered development context.

## Installation

```bash
/plugin marketplace add olane-labs/mcp
/plugin install cosync-remote@olane
/plugin install cosync-local@olane
```

## Plugins

### cosync-remote

Remote MCP server for knowledge graph ingestion, entity search, ontology analysis, and CoSync developer integration.

- **Transport:** HTTP (`https://mcp.copass.id/mcp`)
- **No local install required** — connects directly to the hosted server

**Tools:** `check_project_status`, `ingest_code`, `ingest_text`, `ontology_analyze`, `ontology_question`, `search_entities`, `get_score`, `get_task_cosync`, `get_learning_requests`

### cosync-local

Local encryption and project setup plugin. Session tokens and AES-256-GCM encryption — keys never leave your machine.

- **Transport:** stdio (installed via `uvx olane-cosync-local`)
- **Requires:** Python 3.10+, [uv](https://docs.astral.sh/uv/)

**Tools:** `generate_session_token`, `encrypt_payload`, `encrypt_file`, `setup_project`, `update_auth_token`, `set_cosync_encryption_key`

## Session Initialization

Both plugins work together. At the start of every session:

1. `generate_session_token` (cosync-local) — returns a session token
2. `check_project_status` (cosync-remote) — checks project indexing state
3. `setup_project` (cosync-local) — if hooks are not installed

All cosync-remote tools require the `encryption_token` from step 1. For ingestion tools, encrypt payloads first with `encrypt_payload` (cosync-local).

## License

MIT
