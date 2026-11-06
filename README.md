# Patch MCP

[Patch MCP](https://www.patchmcp.com) gives AI assistants a phone workspace: make outbound calls, configure agents to answer incoming calls, and review call outcomes, transcripts and available recordings.

This repository contains public connection metadata and marketplace manifests for the hosted Patch MCP service.

## Connect

Add this remote Streamable HTTP server to your MCP client:

```json
{
  "mcpServers": {
    "patch": {
      "url": "https://www.patchmcp.com/mcp"
    }
  }
}
```

Sign in through the client's OAuth flow. Verify your caller ID to call from your own number; eligible accounts can also configure Patch phone numbers. No local server process or API key is required. Public MCP initialization and tool discovery work without authentication; tool execution and account data require OAuth.

## Tools

Start with `get_capabilities` to discover available actions, permissions and prerequisites. Depending on your account and granted scopes, you can:

- Place and stop outbound calls with `place_call` and `end_call`.
- Check a call with `get_call` and browse calls and agent tests with `list_activity`.
- List and manage phone numbers, configure inbound and outbound agents, and select voices.
- Connect external tools to agents and run synthetic agent tests.
- Review account and billing information.

The hosted server supplies the current tool definitions. See the [tool reference](https://www.patchmcp.com/docs/tools) for details. Availability depends on account features, permissions and destination. Additional permissions require reconnecting and approving the requested scopes.

Calls are private by default. Public call sharing exposes call details, transcripts and audio to anyone with the link. Never use Patch for emergencies.

## Documentation

- [Setup and client guides](https://www.patchmcp.com/docs)
- [Privacy policy](https://www.patchmcp.com/privacy)
- [Terms of service](https://www.patchmcp.com/terms)
- [Glama connector](https://glama.ai/mcp/connectors/com.patchmcp/patch)
- Official MCP Registry identifier: `com.patchmcp/patch`

The hosted service is operated by Manu Labs, LLC. Usage is governed by the service's terms and applicable account limits.
