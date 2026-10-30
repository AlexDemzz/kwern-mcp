# Kwern MCP server

A remote MCP server at `https://api.kwern.app/mcp` for [Kwern](https://kwern.app), marketing agents that wait for your yes.

It reads and writes a product's marketing workspace: its foundation doc, growth plan and memory, its connector snapshots, its approval feed, its recommendations and its journal, plus the open skills library. It also calls your connectors' own APIs for your agent, signed by Kwern, so your credentials stay in Kwern.

It never runs a skill, never starts an agent, and never spends a token on Kwern's side. The model on the other end is yours.

This repository holds the server's description only. The server is hosted; there is nothing to install.

## Add it to a client

In Claude Code:

```
claude mcp add --transport http kwern https://api.kwern.app/mcp
```

Any MCP client that speaks streamable HTTP and OAuth works the same way: point it at the same URL. The first call opens Kwern's consent screen in your browser, where you pick the account and whether the client may write. Everything is bound to the account the token was issued for.

A Kwern account is needed: plans start at $29 a month ([pricing](https://kwern.app/pricing)).

## What it exposes

Resources: `kwern://products`, `kwern://skills`, and per product `kwern://products/{id}/{name}` for `foundation`, `growth-plan`, `memory`, `launch`, `snapshots`, `outputs`, `feed`, `recommendations`, `journal`.

Read tools: `list_products`, `state`, `list_proposals`, `get_proposal`, `read_connector_api`.

Write tools, on a write token only: `approve_proposal`, `mark_proposal_done`, `record_reply`, `reject_proposal`, `write_foundation_doc`, `edit_loop`, `upload_media`, `create_post`, `edit_post`, `move_post`, `write_connector_api`.

## Docs

- Setup and every tool: https://docs.kwern.app/mcp
- The MCP page: https://kwern.app/mcp
- Official MCP Registry name: `app.kwern/kwern` (`server.json` in this repository)
