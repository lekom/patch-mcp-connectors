# Patch MCP

[Patch MCP](https://www.patchmcp.com) lets AI assistants make real outbound phone calls from your own verified phone number and retrieve answers, transcripts and recordings.

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

Sign in through the client's OAuth flow and verify your phone number. No local server process or API key is required. Public MCP initialization and tool discovery work without authentication; tool execution and account data require OAuth.

## Tools

- `estimate_call`: Check destination support and estimated usage before dialing.
- `place_call`: Start a real phone call with a specific objective.
- `get_call`: Retrieve call status, outcome, transcript and recording when available.
- `list_calls`: Browse your recent calls with pagination.
- `end_call`: Stop an active call.
- `get_phone_number`: Inspect your connected caller ID.
- `set_call_visibility`: Explicitly publish a call or make it private again.

Calls are private by default. Public call sharing exposes call details, transcripts and audio to anyone with the link. Calls are recorded with a spoken disclosure. Never use Patch for emergencies. Supported routes and usage depend on your account and destination; use `estimate_call` before calling. Texting is currently unavailable.

## Documentation

- [Setup and client guides](https://www.patchmcp.com/docs)
- [Privacy policy](https://www.patchmcp.com/privacy)
- [Terms of service](https://www.patchmcp.com/terms)
- [Glama connector](https://glama.ai/mcp/connectors/com.patchmcp/patch)
- Official MCP Registry identifier: `com.patchmcp/patch`

The hosted service is operated by Manu Labs, LLC. Usage is governed by the service's terms and applicable account limits.
