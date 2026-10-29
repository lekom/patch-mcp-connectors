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

- `list_phone_numbers`: List available outbound sources and the default source.
- `place_call`: Start an authorized real call with a destination, objective and the callee’s local IANA timezone. Optional `source_number_id` selects an enabled, published outbound source.
- `get_call`: Retrieve call status, outcome, transcript and recording when available.
- `list_calls`: Browse your recent calls with pagination.
- `end_call`: Stop an active call.
- `get_phone_number`: Inspect your connected caller ID.
- `set_call_visibility`: Explicitly publish a call or make it private again.

Calls are private by default. Public call sharing exposes call details, transcripts and audio to anyone with the link. Calls are recorded with a spoken disclosure. Never use Patch for emergencies. Supported routes and usage depend on your account and destination. Route eligibility is checked when placing the call; the response includes estimated usage. There is no standalone `estimate_call` tool. Gather the timezone from reliable context or ask, rather than guessing from the number. Texting is currently unavailable.

## Staging management expansion

PR #317 adds customer management to staging: account setup, numbers, agents, voices, connected tools, synthetic tests and billing. This is separate from the production calling surface above. Existing integrations do not gain permissions automatically. When available on the target deployment, a host must explicitly request the needed `calls`, `configuration`, `numbers`, `connectors`, `billing` and `account` scopes with `:read` or `:manage` through OAuth consent; manage includes read. Omitted scopes retain historical calling access, and refresh cannot expand it. Do not add invented OAuth scope fields to connector manifests.

## Documentation

- [Setup and client guides](https://www.patchmcp.com/docs)
- [Generated tool reference](https://www.patchmcp.com/docs/tools)
- [Machine-readable reference](https://www.patchmcp.com/docs/tools.json)
- [Privacy policy](https://www.patchmcp.com/privacy)
- [Terms of service](https://www.patchmcp.com/terms)
- [Glama connector](https://glama.ai/mcp/connectors/com.patchmcp/patch)
- Official MCP Registry identifier: `com.patchmcp/patch`

The hosted service is operated by Manu Labs, LLC. Usage is governed by the service's terms and applicable account limits.
