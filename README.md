# Carrier Ledger

Look up U.S. trucking companies and freight brokers in FMCSA public records before you book or pay them. Every fact cites the FMCSA dataset it came from.

- Website: https://carrierledger.tryneverclosed.com
- Remote MCP server (Streamable HTTP, no sign-in): `https://carrierledger.tryneverclosed.com/mcp`
- Official MCP Registry name: `dev.workers.neoaethel.carrier-ledger/carrier-ledger`
- Also listed in the Claude Connectors Directory: https://claude.ai/directory/carrier-ledger

This repository holds documentation only. It contains no server code.

## Tools

All three tools are read-only. They never return phone numbers or email addresses.

| Tool | What it does |
|---|---|
| `lookup_carrier` | Looks up one carrier or broker by USDOT number (for example `2544963`) or MC number (for example `MC-885837`). Returns operating authority, liability insurance and bond on file, suspension or revocation notices, and plain-English red flags, each with its FMCSA dataset. |
| `check_carrier_list` | Checks up to 25 carriers or brokers at once (USDOT numbers, or up to 10 MC numbers) and returns each one's most important red flag, urgent ones first. |
| `recent_suspension_notices` | Lists carriers and brokers FMCSA recently served an involuntary suspension notice (usually because insurance was cancelled), with the date each one takes effect. Until that date FMCSA still shows them as "Active". |

## Add it to your client

VS Code / GitHub Copilot (`.vscode/mcp.json`):

```json
{
  "servers": {
    "carrier-ledger": {
      "type": "http",
      "url": "https://carrierledger.tryneverclosed.com/mcp"
    }
  }
}
```

Any other MCP client: add a remote (Streamable HTTP) server with the URL above. No key is needed.

## Example prompts

- "Check carrier USDOT 2544963 before I book them for a load."
- "Screen this shortlist for red flags: 2544963, 80806"
- "Which carriers did FMCSA recently serve suspension notices to? Show 5."

## Where the data comes from

Carrier Ledger copies public FMCSA datasets published on data.transportation.gov and links each fact to its dataset. Some datasets update daily, so a record can lag FMCSA's own site by a day.

## Limits

- U.S. FMCSA records only.
- It is not a carrier rating and not a vetting decision. It gives your team the facts faster.
- Not affiliated with FMCSA or the U.S. DOT.

## Pricing

The MCP tools are free. On the website, watching carriers for changes is free for 5 carriers; $29 a month covers 250, with a 14-day free trial.

## Links

- Privacy: https://carrierledger.tryneverclosed.com/privacy
- Terms: https://carrierledger.tryneverclosed.com/terms
- Support: https://carrierledger.tryneverclosed.com/support
