# Equinix MCP Servers Repository

Official repository containing Model Context Protocol (MCP) servers and guidance for integrating them with AI assistants and language models.

## 📋 Table of Contents

- [Overview](#overview)
- [Available Servers](#available-servers)
- [Server Tools](#server-tools)
- [Installation & Getting Started](#-installation--getting-started)
- [Configuration](#configuration)
- [Troubleshooting](#-troubleshooting)
- [Support](#-support)

## Overview

This repository provides standardized MCP server implementations that enable AI assistants and language models to securely interact with external APIs and services. MCP is an open protocol that allows structured access to resources and operations.

> **Status:** Some servers may be in Private Beta. Contact your account representative or submit an inquiry to learn about beta access.

## Available Servers

| Server Name | Endpoint | Description |
|-------------|----------|-------------|
| **Fabric MCP** | `https://mcp.equinix.com/fabric` | Interact with Equinix Fabric resources |
| **Peering Insights MCP** | `https://mcp.equinix.com/peeringInsights` | Manage Internet Exchange and peering resources |

## Server Tools

Each MCP server exposes a set of tools for interacting with its respective API. Tools are organized by server below.

### Fabric MCP Server

**Location:** `https://mcp.equinix.com/fabric`

Available tools:
- Reference: [All Fabric tools](./docs/TOOLS_REFERENCE.md#fabric-mcp-tools)

### Peering Insights MCP Server

**Location:** `https://mcp.equinix.com/peeringInsights`

## 🌐 MCP Server Endpoints

MCP servers are accessible via standardized HTTP endpoints that support the Model Context Protocol. These endpoints work with any compatible MCP client.

**Standard Configuration:**
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

> **Note:** These URLs are designed for use within compliant MCP clients only. Direct browser access will return a `405 Method Not Allowed` error. Use VS Code, Claude Desktop, or the MCP Inspector instead.

## 🔌 Installation & Getting Started

Choose your preferred client for quick setup:

| Client | Installation | Guide |
|--------|--------------|-------|
| **VS Code** | Install "MCP Servers" extension from Marketplace | [VS Code MCP Guide](https://code.visualstudio.com/docs/copilot/chat/mcp-servers) |
| **Claude Desktop** | Add via "Add custom connector" in settings | [Claude Desktop Guide](https://modelcontextprotocol.io/docs/develop/connect-remote-servers) |
| **Visual Studio** | Built-in support (VS 2022 or later) | [Visual Studio Guide](https://learn.microsoft.com/en-us/visualstudio/ide/mcp-servers?view=vs-2022) |
| **Cursor IDE** | Install via Cursor settings panel | [Cursor MCP Guide](https://docs.cursor.com/context/model-context-protocol) |

### 🚀 Quick Setup

New to Equinix MCP? Start here: **[Getting Started Guide →](./docs/getting-started.md)**

This guide covers:
This guide covers:
- Authentication (OAuth 2.1 — DCR/CIMD)
- Setting up your preferred MCP client
- Testing your connection
- Running your first commands
- Security best practices

## Configuration

### Basic Setup

1. Copy the MCP server endpoint URL from the [Available Servers](#available-servers) table
2. Add it to your client's configuration file
3. Restart your IDE or client application
4. Verify the connection in your MCP client interface


## ⚠️ Troubleshooting

| Issue | Solution |
|-------|----------|
| **Connection errors** | Verify your network connection and ensure the server URL is correctly entered in your MCP client configuration |
| **Tools not appearing** | Restart your IDE/client application and verify the MCP server is properly installed and connected |
| **HTTP 405 error** | This occurs when accessing the endpoint in a web browser. Use your MCP client (VS Code, Claude Desktop, etc.) or [MCP Inspector](https://modelcontextprotocol.io/docs/tools/inspector) instead |
| **Authentication failures** | Ensure you completed the client browser consent flow and that the MCP client is configured with the correct server URL. If the client can't open a browser, check pop-up blockers and OS URL handlers. |
| **Slow responses** | Check your network latency and server status. Consider retrying requests if network conditions are poor |

## 🆘 Support

- **Documentation:** [Complete documentation in `/docs`](./docs/)


- **Issues:** [Report bugs or request features](https://github.com/equinix/mcp/issues)
- **Email:** Contact support with specific server requirements fabric-intelligence-support@equinix.com
---

## 📚 Documentation Index

| Resource | Purpose |
|----------|---------|
| [Getting Started](./docs/getting-started.md) | First-time setup and configuration |
| [Fabric MCP Server](./docs/servers/fabric-mcp.md) | Connection management workflows and examples |
| [Peering Insights Server](./docs/servers/peering-insights-mcp.md) | Peering optimization and analysis |

## Additional Resources

- [MCP Official Documentation](https://modelcontextprotocol.io/)
- [MCP Inspector Tool](https://modelcontextprotocol.io/docs/tools/inspector)
- [Building Custom MCP Clients](https://modelcontextprotocol.io/docs/develop/client)

