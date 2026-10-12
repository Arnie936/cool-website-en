# Setting up the DataForSEO MCP

Read this only when the optional SEO phase was chosen and the connection, login,
or credit balance needs to be sorted out. A change to this skill is not an
instruction to install DataForSEO right now or to retrieve paid data.

## 1. Detect and reuse an existing connection

First check the available tools and, if present, the active client's native MCP
management. Configured, logged in, and actually callable are three different
states. Do not install a second copy just because a server has a different
name. Do not print secrets when listing a configuration.

The intended remote endpoint is exactly:

```text
https://mcp.dataforseo.com/v3/mcp
```

That is the server address, not an API password. A plain web request to it can
fail even though the MCP works. Check the connection through the MCP client. Do
not silently fall back to an older endpoint or a different provider.

If the connection is missing, offer it concretely:

> DataForSEO is not connected yet. Should I set up the MCP now using the server
> address? After that, you log in to DataForSEO.

If permission to set it up has already been given, go ahead. Without that
permission, independent website work can continue. If the user only supplied
the URL above together with the instruction to connect, do not ask needless
questions about server name, transport, or a local package.

## 2. Account and starter credit

If there is no account yet, offer this link supplied by the user, unchanged:

[Create a DataForSEO account](https://l.dataforseo.com/4yxLJhK)

Explain: this promotional link was stated to come with 5 US dollars of starter
credit. Check the offer and the credit actually granted during sign-up or in the
account. Do not claim a bonus has already been credited. The link is for
onboarding, not for the client's website.

Status as checked on 2026-09-20: the promotional link answered the automated
check with HTTP 403; the general official MCP product page mentioned 1 dollar of
trial credit. That does not disprove a separate offer, but it does not confirm
5 dollars either. Current account data takes precedence over this note.

A small, bounded keyword/SERP start can be possible with a small balance.
Whether 5 dollars is enough depends on scope, endpoints, access, and prices. Do
not promise sufficient credit for every project or available trial endpoints.
The user completes account/email verification and any required acceptance of
terms themselves. Never ask for a password in the chat. Do not book a top-up or
any paid add-on.

## 3. Connect in the client actually in use

Prefer remote HTTP with OAuth where both client and server offer it. Do not
install a local server, Docker, or Node packages when the URL is enough. Use the
integrated browser for any browser interaction.

For a local Codex client with the CLI available, this is the setup path after
consent. First check the current CLI help and reuse existing entries; an
existing entry with the same name must not be overwritten if it belongs to a
different service.

```powershell
codex mcp add dataforseo --url https://mcp.dataforseo.com/v3/mcp
```

If the add command already completed a successful login, do not force a second
one. Otherwise:

```powershell
codex mcp login dataforseo
```

Walk the user through the login the client generates. Do not claim a result
before the client reports success. If a reload or a new chat is required,
explain it with the concrete next step; save the SEO status and open work in
the project first.

For a different client, use its native way of adding a remote MCP. The local
Codex configuration does not connect a hosted chat. If plugins are needed
there, use the existing plugin management to search for DataForSEO and offer the
actual install/connect dialog. Do not invent plugin IDs, buttons, or commands.
If automatic setup is not possible there, guide the user through the few UI
steps actually needed and carry on with independent work in parallel.

If OAuth does not work in the specific client, check the error and the official
guide. DataForSEO also supports HTTP Basic with the API login and API password
from the API Access section. Only use a protected credential store supported by
the active client. Base64 is not encryption. Never write credentials into
project files, prompts, logs, or version control. Do not configure a Basic token
as a Bearer token. Do not change global auth setup on a hunch.

## 4. Check connection and access separately

1. Discover tools through the current client. The v3 documentation describes
   `docs_index`, `docs_list_sections`, `docs_search`, and `api_request`. Use the
   names and arguments from the schemas actually offered.
2. Run a relevant documentation query. That confirms tool access, but does not
   yet prove paid API data access.
3. Determine credit balance and required access rights through documented
   account/usage information or the user's dashboard. Check the tool
   description for possible costs; do not pass off a paid smoke test as free. If
   needed, use the first budgeted research call as the data-access test instead
   of buying an extra test call.
4. After the first data call, check the HTTP, top-level, and task status plus
   the result. HTTP 200 alone does not mean the SEO query succeeded.

On authentication errors, fix the login; on missing product access, discuss a
suitable alternative; on missing credit, stop the research. Do not repeatedly
start identical paid jobs. Report status precisely:
`not set up`, `login pending`, `tools reachable`, `data access confirmed`.

## Sources and updates

Before setting up, check these official sources whenever something is unclear
or tool behavior has changed. Do not blindly copy old auth examples.

- [Remote endpoint and client connection](https://dataforseo.com/model-context-protocol)
- [OAuth connection](https://dataforseo.com/help-center/connecting-the-remote-dataforseo-mcp-server-using-oauth)
- [v3 tools and documentation workflow](https://dataforseo.com/help-center/dataforseo-new-mcp-server-and-cli-connection-a-quickstart-guide)
- [Codex MCP configuration](https://developers.openai.com/codex/mcp)
- [General trial credit and usage-based costs](https://dataforseo.com/seo-mcp-server)
