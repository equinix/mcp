# Getting Started with Equinix MCP Servers

This guide explains how to connect to and use Equinix MCP servers. Authentication is handled by your MCP client using OAuth 2.1 with Dynamic Client Registration (DCR) or Client ID Metadata Documents (CIMD). You do not need to create or manage API keys or access tokens manually.

> **📖 Official Documentation:** For comprehensive setup and configuration instructions for all IDEs and clients, refer to the [Equinix MCP Servers Setup and Configuration documentation](https://docs.equinix.com/equinix-api/mcp-servers/overview#setup-and-configuration).

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

For comprehensive setup and configuration instructions for all IDEs and clients, refer to the [Equinix MCP Servers Setup and Configuration documentation](https://docs.equinix.com/equinix-api/mcp-servers/overview#setup-and-configuration).

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

## Security Considerations

### Use a Dedicated MCP User

We strongly recommend creating a separate Equinix user account specifically for MCP access. This provides several benefits:

- **Least Privilege:** Scope the MCP user's permissions to only the projects and resources it needs
- **Audit Trail:** Distinguish MCP actions from your own actions in logs
- **Blast Radius:** If the MCP session is compromised, only the dedicated user's permissions are exposed
- **Easy Revocation:** Disable or remove the MCP user without affecting your own account

**How to create a dedicated MCP user:**
1. In the Equinix Customer Portal, go to **Organization → Users → Invite User**
2. Create a user identity designated for MCP (e.g., `yourname+mcp@yourcompany.com`)
3. Assign the user to only the projects and resources MCP should have access to
4. Authenticate as this user when prompted during the MCP setup flow

### Important Security Notes

- **Token Risk:** The MCP server authenticates using your credentials and operates with the same permissions as the account you use. Any action the MCP server performs is executed as you.
- **Trusted Clients Only:** Only authenticate to Equinix MCP servers through MCP clients that you trust and have installed yourself.
- **Tool Confirmation:** Enable human confirmation in your MCP client for operations that create or modify resources.
- **Audit Trail:** All operations performed through the MCP server are logged and attributable to the authenticated user.

For more security guidance, see the [official security considerations documentation](https://docs.equinix.com/equinix-api/mcp-servers/overview#security-considerations).

## Troubleshooting

### Authentication Failed
**Problem:** Your MCP client cannot authenticate or reports an authorization error.

**Solution:**
- Ensure your Equinix Customer Portal account is active and in good standing
- Try re-authenticating by removing and re-adding the MCP server in your client
- Clear your client's cached credentials if available, then restart and re-authenticate
- Confirm that your account has been added to the Private Beta allowlist

### MCP Server Not Responding
**Problem:** Your MCP client cannot communicate with the MCP server.

**Solution:**
- Verify internet connection can reach `https://mcp.equinix.com/<service>`
- Check that your MCP client configuration file has the correct URL and format
- Restart your MCP client to reinitialize the connection
- Review MCP server logs in your client for specific error messages

### Permission Denied Errors
**Problem:** Operations fail with permission or authorization errors.

**Solution:**
- Ensure the Equinix account you authenticated with has appropriate roles and permissions
- If using a dedicated MCP user, verify the user has been assigned to the correct projects
- Confirm that the account has access to the resources you're trying to manage

### Session Expired
**Problem:** Operations that were previously working begin to fail with authentication errors.

**Solution:** Your MCP client should refresh tokens automatically. If issues persist:
- Restart your MCP client to trigger a new authentication flow
- Complete the browser login flow when prompted
- If the issue persists, remove and re-add the MCP server configuration

For more troubleshooting guidance, see the [official troubleshooting documentation](https://docs.equinix.com/equinix-api/mcp-servers/overview#troubleshooting).

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
- [View all available tools](./TOOLS_REFERENCE.md)
- [Learn about rate limits and quotas](./rate-limits.md)

