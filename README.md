<img src="logo.png" alt="Goldsky" width="80" />

# Goldsky Docs MCP server

A remote MCP server that lets AI assistants search and read the [Goldsky documentation](https://docs.goldsky.com). Goldsky provides onchain data for apps and finance teams: Feeds (REST APIs for wallet balances and transfers, token prices, Polymarket prediction-market data, and block data, payable per request with x402), prebuilt onchain datasets, Turbo pipelines, Subgraphs, Mirror, and Edge RPC across 150+ chains.

- Endpoint: `https://docs.goldsky.com/mcp`
- Transport: Streamable HTTP
- Authentication: none. No API key or account is needed.
- MCP Registry name: `com.goldsky/docs`

The server reads public documentation only. It does not access your Goldsky account, wallets, or data. To use the products the docs describe, create a Goldsky account and API key at [app.goldsky.com](https://app.goldsky.com).

This repository holds the listing README only. The server is hosted by Goldsky.

## Tools

| Tool | What it does |
|---|---|
| `search_goldsky` | Searches the Goldsky docs and returns matching pages with titles and links. |
| `query_docs_filesystem_goldsky` | Reads full doc pages, including code samples and API references. |
| `submit_feedback` | Reports a problem with a docs page (missing, wrong, or out of date). |

## Configure

### VS Code and GitHub Copilot

Add to `.vscode/mcp.json` in your workspace, or run **MCP: Add Server** from the command palette:

```json
{
  "servers": {
    "goldsky-docs": {
      "type": "http",
      "url": "https://docs.goldsky.com/mcp"
    }
  }
}
```

### Claude Code

```bash
claude mcp add --transport http goldsky-docs https://docs.goldsky.com/mcp
```

### Cursor

Add to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "goldsky-docs": {
      "url": "https://docs.goldsky.com/mcp"
    }
  }
}
```

### Other clients

Any client that supports remote MCP servers over Streamable HTTP can connect to `https://docs.goldsky.com/mcp` with no authentication. See [docs.goldsky.com/mcp-server](https://docs.goldsky.com/mcp-server) for more clients.

## Use

Ask your assistant a Goldsky question. It calls the docs tools and answers with links to the pages it used. Examples:

- "How do I get a wallet's token balances with Goldsky Feeds?"
- "How do I get a wallet's Polymarket positions with Goldsky Feeds?"
- "How do I send a Turbo pipeline's output to a Postgres database?"
- "How do I migrate my subgraph from The Graph to Goldsky?"
- "How much does Goldsky Edge RPC cost?"

## Related

- [goldsky-agent](https://github.com/goldsky-io/goldsky-agent): the Goldsky plugin for Claude Code, Cursor, Codex, and Gemini CLI. It adds skills for building pipelines, subgraphs, and RPC setups, and includes this docs server.
- [Goldsky docs](https://docs.goldsky.com)
- Support: [docs.goldsky.com/getting-support](https://docs.goldsky.com/getting-support)
