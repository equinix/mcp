# Getting Started with Equinix MCP Servers

This guide explains how to connect to and use Equinix MCP servers. Authentication is handled by your MCP client using OAuth 2.1 with Dynamic Client Registration (DCR) or Client ID Metadata Documents (CIMD). You do not need to create or manage API keys or access tokens manually.

## Prerequisites

- An Equinix account ([Create one](https://portal.equinix.com))
- A compatible MCP client (VS Code, Claude Desktop, Cursor, etc.)

## Authentication

Equinix MCP servers use OAuth 2.1 for authentication. For client registration, the server supports both Dynamic Client Registration (DCR) and Client ID Metadata Documents (CIMD). Your MCP client selects the mechanism it supports — most MCP clients today use DCR, while some (such as Visual Studio Code) support CIMD as well. Either way, your MCP client handles the entire authentication flow and token lifecycle.

### How It Works

1. Add the MCP server URL to your MCP client's configuration (see Setup and Configuration below).
2. Your MCP client detects that an auth token is missing and prompts you to connect.
3. A browser window opens where you log in with your Equinix Customer Portal credentials.
4. You review a consent page describing the permissions and scopes being granted and approve the connection.
5. Your MCP client receives and stores tokens automatically and refreshes them in the background.
6. After completing this flow once, you remain authenticated until you revoke access or your session ends.

### Token Lifecycle

- Tokens are automatically refreshed by your MCP client; no manual token management is required.
- If your session is revoked or expires, your MCP client will prompt you to re-authenticate using the same browser flow.

## Setup and Configuration

To connect an Equinix MCP server, add the server URL to your MCP client's configuration file. When the client connects for the first time, it will initiate the authentication flow described above.

Below are example instructions for common MCP clients. The exact format varies by client, but the pattern is the same: add the server URL, save the config, restart the client, and follow the browser prompt on first use.

### VS Code

1. Install the **MCP Servers** extension from the Marketplace.
2. Open settings: `Code → Preferences → Settings`.
3. Search for "MCP" and add your server entries (no Authorization header required):

```json
{
  "servers": {
    "fabric": {
      "type": "http",
      "url": "https://mcp.equinix.com/fabric"
    },
    "peering-insights": {
      "type": "http",
      "url": "https://mcp.equinix.com/peeringInsights"
    }
  }
}
```

4. Restart VS Code. On first use the client will open a browser window to complete the OAuth flow.

### Claude Desktop

1. Locate your Claude Desktop config file:
   - **macOS:** `~/.claude_desktop_config.json`
   - **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

2. Add the server URL (the client handles authentication):

```json
{
  "mcpServers": {
    "fabric": {
      "url": "https://mcp.equinix.com/fabric"
    }
  }
}
```

3. Save and restart Claude Desktop. Follow the browser prompt to authenticate on first connect.

### Cursor IDE

1. Open **Settings → Extensions → MCP**.
2. Click **Add Server** and fill in:
   - **Name:** fabric
   - **URL:** https://mcp.equinix.com/fabric
3. Repeat for other servers and restart Cursor. The client will open the browser-based OAuth flow on first use.

## Test Your Connection

### From Your MCP Client

**VS Code:**
```
@mcp fabric search_connections
```

**Claude Desktop:**
```
Can you list my Fabric connections?
```

If the client completes the OAuth flow successfully, you'll see your connections listed.

### MCP Inspector

For debugging, use the MCP Inspector:

```bash
# Install if needed
npm install -g @modelcontextprotocol/inspector

# Run inspector
mcp-inspector
```

Then:
1. Open http://localhost:5000
2. Add server URL: `https://mcp.equinix.com/fabric`
3. Follow the inspector's prompts to complete authentication and test tool calls

## Use MCP Tools

### Fabric MCP Examples

```bash
# List your connections
@mcp fabric search_connections --limit 10
```

## Security Best Practices

- Use the client-managed OAuth flow and rely on the client for token storage and refresh.
- Revoke access from your Equinix account when a client is no longer needed.
- Approve only the scopes required by a client.
- Secure devices where MCP clients run (disk encryption, OS updates, credential stores).

## Troubleshooting

### Connection Refused

**Problem:** "Cannot connect to server"

**Solution:**
- Verify the server URL is correct
- Check your network connection
- Ensure the client is allowed to open a browser for authentication
- Wait a moment and retry

### Authentication Failures

**Problem:** "Authentication failed" or browser flow did not complete

**Solution:**
- Ensure you completed the browser consent flow
- Check browser pop-up blockers and OS-level URL handlers
- Revoke the client and retry the connection flow

### Tools Not Showing

**Problem:** "No tools available from MCP server"

**Solution:**
- Restart your IDE/client
- Verify server configuration is correct
- Check network connectivity
- Test with MCP Inspector
- Review server logs for errors

## Getting Help

- **Documentation:** Review server-specific guides
- **API Status:** Check [status.equinix.com](https://status.equinix.com)
- **Support:** Contact support@equinix.com
- **Community:** Visit [GitHub Discussions](https://github.com/MicrosoftDocs/mcp/discussions)

## What's Next?

- [Create and manage Fabric connections](./servers/fabric-mcp.md)
- [Optimize peering with Insights](./servers/peering-insights-mcp.md)
- [View all available tools](./TOOLS_REFERENCE.md)
- [Learn about rate limits and quotas](./rate-limits.md)

