# Install the Court Rules MCP server

Court Rules is a hosted remote MCP server. Nothing is built or run locally.

- Endpoint: `https://mcp.courtrules.app/mcp` (Streamable HTTP)
- Authentication: OAuth sign-in, or an API key from <https://console.courtrules.app> sent as `Authorization: Bearer <api_key>`
- No credentials are needed to reach the endpoint; every request without one gets `401` with an OAuth discovery header.

## Cline

1. Open the MCP Servers panel (the server icon in the Cline sidebar) and choose **Remote Servers**.
2. Add a server named `court-rules` with URL `https://mcp.courtrules.app/mcp`.
3. When Cline shows a sign-in prompt, approve the connection in the browser. To use an API key instead, add the header below and skip sign-in.

Equivalent entry in `cline_mcp_settings.json` (API key variant):

```json
{
  "mcpServers": {
    "court-rules": {
      "type": "streamableHttp",
      "url": "https://mcp.courtrules.app/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

For sign-in instead of an API key, remove the whole `headers` object and approve the OAuth prompt when it appears.

Verify the connection by asking Cline to list the covered courts, or: "What are Judge Amon's page limits for a summary judgment brief?"

## Other clients

- Claude Code: `claude mcp add --transport http court-rules https://mcp.courtrules.app/mcp`
- Cursor, Windsurf, Claude Desktop: JSON config with `"url": "https://mcp.courtrules.app/mcp"`; approve the sign-in prompt when the client asks.
- Full documentation: <https://docs.courtrules.app/guides/mcp-court-rules>
