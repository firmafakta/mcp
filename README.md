<img src="icon.svg" alt="" width="64" height="64">

# Firmafakta MCP

A remote MCP server over the Swedish company registers (SCB, Bolagsverket, PRV). Your AI
assistant counts and lists companies by industry, place and size, and looks up single companies
by organisation number.

```
https://mcp.firmafakta.se
```

You need a Firmafakta account; the free plan is enough to try it. Sign in with OAuth when your
client asks, or send an API key (see below). This repository holds the listing metadata and these
instructions; the server itself is not open source.

## Install as a plugin

This repository is also a plugin marketplace. The Firmafakta plugin brings two servers: a free
one you can use at once, without an account (10 credits a month), and your account's, which you
log in to when you want more (a free account gives 100 a month).

**Claude Code:**

```sh
/plugin marketplace add firmafakta/mcp
/plugin install firmafakta@firmafakta
```

**Claude** (claude.ai, Desktop): add the marketplace `firmafakta/mcp` under
Customize, then install Firmafakta.

**ChatGPT and Codex:** add the plugin marketplace `firmafakta/mcp`, then install
Firmafakta.

**Cursor:** add the marketplace `firmafakta/mcp`, then install Firmafakta.

The free server is `https://mcp.firmafakta.se/free`; it needs no login.

## Install

**Claude** (claude.ai, Desktop, mobile): [add Firmafakta as a connector](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=Firmafakta&connectorUrl=https%3A%2F%2Fmcp.firmafakta.se), then sign in and approve.

**Claude Code:**

```sh
claude mcp add --transport http firmafakta https://mcp.firmafakta.se
```

**Cursor:** [add to Cursor](https://cursor.com/en/install-mcp?name=firmafakta&config=eyJ1cmwiOiJodHRwczovL21jcC5maXJtYWZha3RhLnNlIn0%3D)

**VS Code:**

```sh
code --add-mcp '{"name":"firmafakta","type":"http","url":"https://mcp.firmafakta.se"}'
```

**ChatGPT:** under Plugins or Apps, click **+** and choose Add custom MCP server with the address above. What your plan allows,
and whether developer mode must be on, is in
[OpenAI's help article](https://help.openai.com/en/articles/12584461-developer-mode-and-mcp-apps-in-chatgpt).

**Other clients:** add a remote (Streamable HTTP) MCP server with the address above.

Step by step: [firmafakta.se/en/ai](https://firmafakta.se/en/ai/).

## API key

For agents that cannot sign in with OAuth: create a key under My account on
[firmafakta.se](https://firmafakta.se/) and send it on every request as
`Authorization: Bearer <key>`.

## Tools

| Tool | What it does |
|---|---|
| `firmafakta_describe` | The segment language, the fields and the plan each needs, your plan, credits and prices |
| `firmafakta_find_codes` | Finds SNI industry codes, municipalities, counties and other codes by text |
| `firmafakta_count` | Counts a segment and reads it back in words |
| `firmafakta_fetch` | Fetches a segment's companies or workplaces, a page at a time |
| `firmafakta_lookup` | Everything on one company, by organisation number |
| `firmafakta_company` | A company as the public company page shows it, by organisation number or name, free |
| `firmafakta_save` | Saves a segment to your account |
| `firmafakta_load` | Lists or loads saved segments |

Counting and fetching cost credits, the same credits as on the web; `firmafakta_describe` tells
the assistant the prices, so it can ask you before it spends. Sole proprietorships are counted but
never listed.

## Try

- How many construction companies with 10 to 49 employees are there in Halland?
- Find all accounting firms in Gothenburg municipality and give me the list.
- Same again, but only the ones started in the last five years.

## Support

support@firmafakta.se · [Pricing](https://firmafakta.se/en/priser/) ·
[Privacy](https://firmafakta.se/en/integritet/) · [Terms](https://firmafakta.se/en/villkor/)
