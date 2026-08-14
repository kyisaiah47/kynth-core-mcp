# Installing the ParseRail MCP server

ParseRail is a documents-to-JSON + finished-job AI toolkit (39 endpoints: invoice/receipt/statement extraction, contract analysis, PII redaction, chargeback evidence, research, and more) billed per successful task from one credit wallet.

## 1. Get an API key

Create a free account at https://api.kynth.studio/dashboard — 500 free credits monthly, no card required. Copy your key (`ksk_live_…`).

## 2. Configure the server

The server runs from npm via stdio; the only configuration is the `KYNTH_API_KEY` environment variable.

```json
{
  "mcpServers": {
    "kynth-core": {
      "command": "npx",
      "args": ["-y", "@kynth/api-mcp"],
      "env": {
        "KYNTH_API_KEY": "ksk_live_your_key_here"
      }
    }
  }
}
```

- **Cline**: add the block above to `cline_mcp_settings.json` (MCP Servers → Configure).
- **Claude Code**: `claude mcp add kynth-core -e KYNTH_API_KEY=ksk_live_… -- npx -y @kynth/api-mcp`
- **Claude (custom connector, no install)**: use the hosted URL `https://api.kynth.studio/mcp` with your key.
- **Cursor / VS Code**: same JSON under their MCP settings; the server also lives in the official MCP registry as `studio.kynth/core`.

## 3. Verify

Ask your agent to run the `parse` tool on any PDF/image URL — a valid key returns schema-valid JSON and burns credits only on success. Errors cost nothing.

## Troubleshooting

- `401 unauthorized`: the key is missing/typo'd — it must start `ksk_live_`.
- `402 insufficient credits`: top up or wait for the monthly free refresh.
- Node 18+ is required for `npx`; the package has zero runtime dependencies beyond the MCP SDK.
