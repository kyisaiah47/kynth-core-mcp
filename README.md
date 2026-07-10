# @kynth/api-mcp

An [MCP](https://modelcontextprotocol.io) server for **[Kynth Core](https://api.kynth.studio)** — gives Claude, Cursor, and any Model Context Protocol client native tools to parse documents, extract fields, redact PII, analyze contracts, fight chargebacks, and enrich companies.

## Setup

Get a key (and 500 free credits) at **[api.kynth.studio](https://api.kynth.studio)**, then add the server to your MCP client config.

**Claude Code:**

```bash
claude mcp add kynth-core -e KYNTH_API_KEY=ksk_live_… -- npx -y @kynth/api-mcp
```

**Claude Desktop / Cursor** (`mcpServers` config):

```json
{
  "mcpServers": {
    "kynth-core": {
      "command": "npx",
      "args": ["-y", "@kynth/api-mcp"],
      "env": { "KYNTH_API_KEY": "ksk_live_…" }
    }
  }
}
```

## Tools

| Tool | What it does |
| --- | --- |
| `kynth_parse` | Document (invoice/EOB/COI, PDF/image/text) → structured JSON |
| `kynth_extract` | Pull named fields out of any text |
| `kynth_classify` | Label text against your taxonomy |
| `kynth_summarize` | Summary + key points + action items |
| `kynth_redact` | Strip PII/PHI from text |
| `kynth_sentiment` | Sentiment, aspects, and themes |
| `kynth_contract` | Contract → parties, terms, obligations, risk flags |
| `kynth_chargeback` | Dispute details → representment packet |
| `kynth_enrich` | Domain or email → company profile |
| `kynth_account` | Credit balance |

Documents can be passed as `fileUrl`, raw `text`, or `fileBase64` + `fileMimeType`.

## Pricing

Pay-per-call credits, no subscription — you're only charged on a successful call. See [api.kynth.studio/docs](https://api.kynth.studio/docs).

MIT © Kynth Studios
