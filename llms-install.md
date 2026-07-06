# Installing the DocuWriter.ai MCP Server (for Cline and other agents)

This is a **remote** MCP server. There is **no package to install, no repository to clone, and no build step**. Installation means adding one remote-server entry to the client's MCP configuration. Follow these steps exactly.

## Server details

- Name: `docuwriter`
- URL: `https://app.docuwriter.ai/mcp`
- Transport: Streamable HTTP (`streamableHttp`)
- Authentication: OAuth 2.1 — the client handles the OAuth flow automatically on first connect. Do **not** ask the user for an API key; there is none.

## Cline

Add the server to Cline's MCP settings file `cline_mcp_settings.json` (do not overwrite existing entries — merge into `mcpServers`):

```json
{
  "mcpServers": {
    "docuwriter": {
      "url": "https://app.docuwriter.ai/mcp",
      "type": "streamableHttp",
      "disabled": false
    }
  }
}
```

After saving, Cline will connect to the server. On first use the user is prompted in their browser to sign in to DocuWriter.ai and authorize access. A DocuWriter.ai account is required (a free trial is available at https://www.docuwriter.ai).

## Generic remote-MCP client

If the client uses a different config schema, add a remote/HTTP MCP server with:

- URL: `https://app.docuwriter.ai/mcp`
- Transport: streamable HTTP
- Auth: OAuth 2.1 (autodiscovered via the `WWW-Authenticate` header / `.well-known/oauth-protected-resource`)

## Verifying the connection

Once configured, the server should expose 72 tools (documentation generation, full documentation trees, semantic search, Autopilot suggestions, spaces/documents, teams, and webhooks). If no tools appear, confirm the user completed the OAuth sign-in prompt and has an active DocuWriter.ai account.
