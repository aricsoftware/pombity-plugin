# Documents of record — pombity-plugin

Index required by the documents-of-record standing rule (Projects/CLAUDE.md, Michael 2026-11-05): every document in this repository that describes its behavior to someone outside the code, with what it describes and which code, configuration, or decision it depends on. This repository is public — everything in it is customer-facing. A session that changes a dependency updates the matching document in the same session and says so in its report; a session that adds such a document adds it here in the same commit.

- `README.md` — the install document of record for the Claude Code plugin and the Claude Desktop extension; depends on the MCP endpoint https://mcp.pombity.com/mcp, the eight-tool surface (messaging-service Messaging.Mcp), and the GitHub release that carries the packed `.mcpb`.
- `.mcp.json` — the plugin's server wiring users actually run (endpoint URL, `Authorization: Bearer ${POMBITY_API_KEY}`); depends on the mcp.pombity.com hostname and messaging's API-key auth.
- `mcpb/manifest.json` — the Desktop extension manifest (bundled mcp-remote bridge, sensitive `api_key` user_config); depends on the same endpoint and on mcp-remote's CLI arguments — repack and re-release (`cd mcpb && npm install --omit=dev && npx -y @anthropic-ai/mcpb pack`) when either changes.
