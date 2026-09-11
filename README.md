# Connections for Cursor and Grok Bot

Connections is an AI-first business platform: events with ticketing, contacts, the Deal Flow
marketplace, notes and memory, and payments, reachable from any assistant through one hosted
MCP server. This plugin adds that server to Cursor and Grok Bot. Nothing runs locally; you sign in
with your Connections account in the browser the first time a tool is called.

[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](LICENSE)

## Install

- **Cursor:** Customize / Marketplace, search **Connections**, then Add.
- **Grok Bot:** sidebar account, **Settings -> Plugins**, search **Connections**, then Add.

The first tool call opens a Connections sign-in page. Approve it once and the session persists.
There is no API key or token to paste, and the plugin never asks for one.

Until the marketplace listing is live, add the same server to Cursor's `mcp.json` yourself:

```json
{
  "mcpServers": {
    "connections": {
      "url": "https://studio.connections.icu/v1/mcp"
    }
  }
}
```

## What you can do from the prompt

- Host an event: create it, price tickets through Stripe, invite guests and send the invites.
- Contacts: import a list, search it, and pick who to invite or follow up with.
- Deal Flow: browse live marketplace deals and post your own (posting is for paying members).
- Notes and memory: notes and agent memories persist across every assistant you connect.
- Payments: onboard to Stripe and create products through the Pay plane.

Start with the `connections_pulse` tool: it answers who you are, which workspace you are bound
to, what is live on Deal Flow, and what to do next.

## Authentication and network endpoints

The plugin connects only to `https://studio.connections.icu/v1/mcp`, over streamable HTTP.
Authentication is OAuth 2.1 with PKCE (S256) and dynamic client registration, against
`accounts.connections.icu`.

- `https://studio.connections.icu/v1/mcp` - hosted MCP server
- `https://studio.connections.icu/.well-known/oauth-protected-resource` - protected-resource metadata
- `https://accounts.connections.icu/oauth/authorize`, `/oauth/token`, `/oauth` - OAuth 2.1 and registration

No API key, secret or environment variable is read or stored, and nothing is written to disk. The
plugin ships an MCP server definition and nothing else: no rules, skills, agents, commands, hooks
or scripts. Tools are scoped to the workspaces the signed-in account can already access.

## Links

- Connect page with steps for every assistant: https://studio.connections.icu/connect
- Agent guide (machine-readable manual): https://studio.connections.icu/v1/agent-guide
- Pricing: https://pass.connections.icu (free base plan; Pass Pro from $39.99/mo)
- Terms: https://connections.icu/terms
- Support: support@connections.icu

## License

The files in this repository are MIT licensed. Use of the hosted service is governed by the
Connections terms.
