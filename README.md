# Pombity plugin for Claude Code

Connects Claude Code to [Pombity](https://docs.pombity.com) — texting for your application, with the compliance built in — through its remote MCP server at `https://mcp.pombity.com/mcp`.

The server exposes eight tools: `send_text`, `send_email`, `preview_message`, `check_consent`, `get_delivery_report`, `get_usage`, `request_verified_destination`, `confirm_verified_destination`. Consent, STOP/HELP, quiet hours, verified destinations, and quotas are enforced server-side — every refusal carries a named error code, so an agent never has to re-implement the rules.

## Install

1. Get an API key (see the [quickstart](https://docs.pombity.com)). Use a sandbox key (`ak_test_…`) to try it — sandbox sends never reach a carrier and come back with realistic delivery reports.
2. Put the key in the environment that launches Claude Code, then restart it:

   ```sh
   export POMBITY_API_KEY=ak_test_…
   ```

3. In Claude Code:

   ```
   /plugin marketplace add aricsoftware/pombity-plugin
   /plugin install pombity@pombity
   ```

   Or from the shell: `claude plugin marketplace add aricsoftware/pombity-plugin && claude plugin install pombity@pombity`.

4. Check `/mcp` — the `pombity` server should list its eight tools.

The key is read from `POMBITY_API_KEY` at connection time and is never stored in this plugin or your project.

## Claude Desktop extension (.mcpb)

`mcpb/` builds the Claude Desktop extension: a bundled [`mcp-remote`](https://github.com/geelen/mcp-remote) bridge to the same remote server. Install prompts for your API key and stores it in the OS keychain (`user_config`, sensitive). Download `pombity-<version>.mcpb` from this repository's Releases and double-click it (or Claude Desktop → Settings → Extensions → Install Extension…).

Build it yourself:

```sh
cd mcpb && npm install --omit=dev && npx -y @anthropic-ai/mcpb pack
```

## License

MIT — see [LICENSE](LICENSE).
