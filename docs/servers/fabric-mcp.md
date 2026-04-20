# Fabric MCP Server

The Fabric MCP server is hosted at `https://mcp.equinix.com/fabric` and can be used with MCP-compatible AI agents.

For general information on MCP server setup and configuration, see [MCP Server Overview](overview.md).

:::warning[Private Beta]
The Fabric MCP Server is currently in Private Beta. If you are interested in joining the Beta program, please email [fabric-intelligence-support@equinix.com](mailto:fabric-intelligence-support@equinix.com) or reach out to your Equinix account representative.
:::


## Tools

The Fabric MCP server exposes the following MCP tools that allow AI assistants to interact with your Equinix Fabric resources. Each tool corresponds to a specific Fabric API endpoint.

:::important
We recommend enabling human confirmation for tool execution, especially for operations that create, update, or delete resources. This helps prevent unintended changes to your Fabric infrastructure.
:::

:::note[Current Limitations]
Delete functionality is not currently supported in the Fabric MCP Server. This includes deletion of connections, ports, and Cloud Routers.
:::

### Connections

| Tool                | Description                                                                     | API Endpoint                                                                                  |
|---------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------| 
| `create_connection` | Create a new Fabric Connection                                                  | [Create Connection](/api-catalog/fabricv4/#tag/Connections/operation/createConnection)        |
| `search_connection` | Search for Fabric Connections using advanced filtering, pagination, and sorting | [Search Connection](/api-catalog/fabricv4/#tag/Connections/operation/searchConnections)       |
| `update_connection` | Update an Equinix Fabric Connection using its UUID                              | [Update Connection](/api-catalog/fabricv4/#tag/Connections/operation/updateConnectionByUuid)  |
| `validate_connection` | Validate a Fabric Connection configuration before creation                      | [Validate Connection](/api-catalog/fabricv4/#tag/Connections/operation/validateConnections)   |
| `retry_connection_action` | Perform actions on a Fabric Connection                                          | [Connection Actions](/api-catalog/fabricv4/#tag/Connections/operation/createConnectionAction) |

### Fabric Metros

| Tool | Description | API Endpoint |
| ----- | ----- | ----- | 
| `get_metro` | Retrieve detailed information about a specific Fabric Metro by passing its Metro Code | [Get Metro by Code](/api-catalog/fabricv4/#tag/Metros/operation/getMetroByCode) |
| `list_metro` | Fetch all metros available in Fabric | [Get All Metros](/api-catalog/fabricv4/#tag/Metros/operation/getMetros) |

### Ports

| Tool | Description | API Endpoint |
| ----- | ----- | ----- | 
| `get_port` | Retrieve detailed information about a specific Fabric Port by passing its UUID | [Get Port by UUID](/api-catalog/fabricv4/#tag/Ports/operation/getPortByUuid) |
| `search_port` | Search for Fabric Ports using advanced filtering, pagination, and sorting | [Search Ports](/api-catalog/fabricv4/#tag/Ports/operation/searchPorts) |
| `update_port` | Update a Fabric Port configuration | [Update Port](/api-catalog/fabricv4/#tag/Ports/operation/updatePortByUuid) |
| `get_vlan_port` | Get VLAN configurations for a specific port | [Get Port VLANs](/api-catalog/fabricv4/#tag/Ports/operation/getVlans) |

### Cloud Routers

| Tool | Description | API Endpoint |
| ----- | ----- | ----- | 
| `search_router` | Search for Equinix Fabric Cloud Routers using advanced filtering, pagination, and sorting | [Search Cloud Routers](/api-catalog/fabricv4/#tag/Cloud-Routers/operation/searchCloudRouters) |
| `create_router` | Create a new Fabric Cloud Router | [Create Cloud Router](/api-catalog/fabricv4/#tag/Cloud-Routers/operation/createCloudRouter) |
| `update_router` | Update an existing Fabric Cloud Router | [Update Cloud Router](/api-catalog/fabricv4/#tag/Cloud-Routers/operation/updateCloudRouterByUuid) |
| `get_router_package` | Get details about a Cloud Router package | [Get Router Package](/api-catalog/fabricv4/#tag/Cloud-Routers/operation/getCloudRouterPackageByCode) |
| `create_router_commands` | Initiate router commands such as ping or traceroute | [Create Router Commands](/api-catalog/fabricv4/#tag/Cloud-Routers/operation/createCloudRouterCommand) |
| `search_router_commands` | Search for router command execution results | [Search Router Commands](/api-catalog/fabricv4/#tag/Cloud-Routers/operation/searchCloudRouterCommands) |
| `search_routes` | Search for routes including advertised, received, and active routes | [Search Routes](https://docs.equinix.com/fabric-cloud-router/fcr-api/manage-routing-tables-api/) |
| `load_routes` | Create route table actions for a Cloud Router | [Create Route Actions](/api-catalog/fabricv4/#tag/Cloud-Routers/operation/createCloudRouterAction) |

### Routing Protocols

| Tool            | Description                                                         | API Endpoint                                                                                                              |
|-----------------|---------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------| 
| `get_routing_protocols` | Search for a Routing Protocol using connection                      | [Get Routing Protocols](/api-catalog/fabricv4/#tag/Routing-Protocols/operation/getConnectionRoutingProtocols)             |
| `create_routing_protocols` | Create a new Routing Protocol                                       | [Create Routing Protocols](/api-catalog/fabricv4/#tag/Routing-Protocols/operation/createConnectionRoutingProtocol)        |
| `update_routing_protocols` | Update an existing Routing Protocol                                 | [Update Routing Protocols](/api-catalog/fabricv4/#tag/Routing-Protocols/operation/patchConnectionRoutingProtocolByUuid)   |
| `replace_routing_protocols` | Replace an existing Routing Protocol                                | [Update Routing Protocols](/api-catalog/fabricv4/#tag/Routing-Protocols/operation/replaceConnectionRoutingProtocolByUuid) |

### Projects

| Tool | Description | API Endpoint |
| ----- | ----- | ----- | 
| `search_projects` | Fetch all projects available in Equinix Resource Manager | [Get Projects](/api-catalog/getprojectsv2/#tag/Project/operation/getAllProjects) |

### Pricing

| Tool | Description | API Endpoint |
| ----- | ----- | ----- | 
| `search_prices` | Search for pricing information across Fabric resources | [Search Prices](/api-catalog/fabricv4/#tag/Prices/operation/searchPrices) |

### Precision Time

| Tool | Description | API Endpoint |
| ----- | ----- | ----- | 
| `get_time_service` | Retrieve detailed information about a specific Precision Time service by UUID | [Get Time Service](/api-catalog/fabricv4/#tag/Precision-Time/operation/getTimeServicesById) |
| `search_time_service` | Search for Equinix Precision Time services | [Search Time Services](/api-catalog/fabricv4/#tag/Precision-Time/operation/searchTimeServices) |
| `update_time_service` | Update a Precision Time service configuration | [Update Time Service](/api-catalog/fabricv4/#tag/Precision-Time/operation/updateTimeServicesById) |

### Service Profiles

| Tool | Description | API Endpoint |
| ----- | ----- | ----- | 
| `search_service_profile` | Search for Fabric Service Profiles using advanced filtering | [Search Service Profiles](/api-catalog/fabricv4/#tag/Service-Profiles/operation/searchServiceProfiles) |
| `create_service_profile` | Create a new Fabric Service Profile | [Create Service Profile](/api-catalog/fabricv4/#tag/Service-Profiles/operation/createServiceProfile) |
| `update_service_profile` | Update an existing Service Profile | [Update Service Profile](/api-catalog/fabricv4/#tag/Service-Profiles/operation/updateServiceProfileByUuid) |
| `replace_service_profile` | Replace a Service Profile configuration | [Replace Service Profile](/api-catalog/fabricv4/#tag/Service-Profiles/operation/putServiceProfileByUuid) |
| `get_service_profile_metros` | Get metro information for a specific Service Profile | [Get Service Profile Metros](/api-catalog/fabricv4/#tag/Service-Profiles/operation/getServiceProfileMetrosByUuid) |

### Service Tokens

| Tool | Description | API Endpoint |
| ----- | ----- | ----- | 
| `search_service_tokens` | Search for Fabric Service Tokens | [Search Service Tokens](/api-catalog/fabricv4/#tag/Service-Tokens/operation/searchServiceTokens) |
| `create_service_token` | Create a new Service Token | [Create Service Token](/api-catalog/fabricv4/#tag/Service-Tokens/operation/createServiceToken) |
| `update_service_token` | Update an existing Service Token | [Update Service Token](/api-catalog/fabricv4/#tag/Service-Tokens/operation/updateServiceTokenByUuid) |

### Route Filters

| Tool | Description | API Endpoint |
| ----- | ----- | ----- | 
| `search_route_filter` | Search for Cloud Router Route Filters | [Search Route Filters](/api-catalog/fabricv4/#tag/Route-Filters/operation/searchRouteFilters) |
| `create_route_filter` | Create a new Route Filter for traffic management | [Create Route Filter](/api-catalog/fabricv4/#tag/Route-Filters/operation/createRouteFilter) |
| `update_route_filter` | Update an existing Route Filter configuration | [Update Route Filter](/api-catalog/fabricv4/#tag/Route-Filters/operation/patchRouteFilterByUuid) |

### Route Filter Rules

| Tool | Description | API Endpoint |
| ----- | ----- | ----- | 
| `get_all_route_filter_rules` | List all rules for a specific Route Filter | [List Route Filter Rules](/api-catalog/fabricv4/#tag/Route-Filter-Rules/operation/getRouteFilterRules) |
| `get_route_filter_rule` | Get detailed information about a specific Route Filter Rule | [Get Route Filter Rule](/api-catalog/fabricv4/#tag/Route-Filter-Rules/operation/getRouteFilterRuleByUuid) |
| `create_route_filter_rule` | Create new rules for a Route Filter | [Create Route Filter Rules](/api-catalog/fabricv4/#tag/Route-Filter-Rules/operation/createRouteFilterRule) |
| `update_route_filter_rule` | Update an existing Route Filter Rule | [Update Route Filter Rule](/api-catalog/fabricv4/#tag/Route-Filter-Rules/operation/patchRouteFilterRuleByUuid) |

### Route Aggregation

| Tool                       | Description | API Endpoint                                                                                        |
|----------------------------| ----- |-----------------------------------------------------------------------------------------------------| 
| `search_route_aggregation` | Search for Cloud Router Route Aggregation | [Search Route Aggregation](/api-catalog/fabricv4/#tag/Route-Aggregations/operation/searchRouteAggregations) |
| `create_route_aggregation` | Create a new Route Aggregation for traffic management | [Create Route Aggregation](/api-catalog/fabricv4/#tag/Route-Aggregations/operation/createRouteAggregation) |
| `update_route_aggregation` | Update an existing Route Aggregation configuration | [Update Route Aggregation](/api-catalog/fabricv4/#tag/Route-Aggregations/operation/patchRouteAggregationByUuid) |

### Route Aggregation Rules

| Tool                                     | Description                                                      | API Endpoint                                                                                                  |
|------------------------------------------|------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------| 
| `get_all_route_aggregation_rules` | List all rules for a specific Route Aggregation                  | [List Route Aggregation Rules](/api-catalog/fabricv4/#tag/Route-Aggregation-Rules/operation/getRouteAggregationRules) |
| `get_route_aggregation_rule`      | Get detailed information about a specific Route Aggregation Rule | [Get Route Aggregation Rule](/api-catalog/fabricv4/#tag/Route-Aggregation-Rules/operation/getRouteAggregationRuleByUuid) |
| `create_route_aggregation_rule`   | Create new rules for a Route Aggregation                              | [Create Route Aggregation Rules](/api-catalog/fabricv4/#tag/Route-Aggregation-Rules/operation/createRouteAggregationRule) |
| `update_route_aggregation_rule`   | Update an existing Route Aggregation Rule                             | [Update Route Aggregation Rule](/api-catalog/fabricv4/#tag/Route-Aggregation-Rules/operation/patchRouteAggregationRuleByUuid) |


### Observability - Streams

| Tool                                     | Description                                                             | API Endpoint                                                                                                           |
|------------------------------------------|-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------| 
| `list_streams`                     | List all telemetry streams in your account                              | [Get Streams](/api-catalog/fabricv4/#tag/Streams/operation/getStreams)                                                 |
| `get_stream_details`               | Get detailed information about a specific stream                        | [Get Stream Details](/api-catalog/fabricv4/#tag/Streams/operation/getStreamByUuid)                                     |
| `create_stream`                    | Create a new telemetry stream                                           | [Create Stream](/api-catalog/fabricv4/#tag/Streams/operation/createStreams)                                            |
| `update_stream`                    | Update an existing telemetry stream                                     | [Update Stream](/api-catalog/fabricv4/#tag/Streams/operation/updateStreamByUuid)                                       |
| `list_stream_attached_assets`      | List assets attached to a stream                                        | [List Stream Assets](/api-catalog/fabricv4/#tag/Streams/operation/getStreamAssetByUuid)                                |
| `get_stream_attached_asset_details` | Get details about a specific asset attached to a stream                 | [Get Stream Asset Details](/api-catalog/fabricv4/#tag/Streams/operation/getStreamAssetByUuid)                          |
| `attach_stream_asset`              | Attach an asset to a telemetry stream                                   | [Attach Asset to Stream](/api-catalog/fabricv4/#tag/Streams/operation/updateStreamAssetByUuid)                         |
| `search_attached_assets`           | Search for assets attached to a telemetry stream                        | [Search Asset to Stream](/api-catalog/fabricv4/#tag/Streams/operation/getStreamsAssets)                                |
| `list_stream_subscriptions`        | List all telemetry stream subscription for a specific telementry Stream | [List Stream Subscription](/api-catalog/fabricv4/#tag/Stream-Subscriptions/operation/getStreamSubscriptions)           |
| `get_stream_subscription_details`  | Get details about a specific telemetry stream subscription              | [Get Stream Subscription](/api-catalog/fabricv4/#tag/Stream-Subscriptions/operation/getStreamSubscriptionByUuid)       |
| `create_stream_subscription`       | Create a new telemetry stream subscription                              | [Create Stream Subscription](/api-catalog/fabricv4/#tag/Stream-Subscriptions/operation/createStreamSubscriptions)      |
| `update_stream_subscription`      | Update an existing telemetry stream subscription                        | [Update Stream Subscription](/api-catalog/fabricv4/#tag/Stream-Subscriptions/operation/updateStreamSubscriptionByUuid) |

### Observability - Stream Alert Rules

| Tool | Description | API Endpoint |
| ----- | ----- | ----- | 
| `list_stream_alert_rules` | List all alert rules for a stream | [Get Alert Rules](/api-catalog/fabricv4/#tag/Stream-Alert-Rules/operation/getStreamAlertRules) |
| `get_stream_alert_rule_details` | Get detailed information about a specific alert rule | [Get Alert Rule Details](/api-catalog/fabricv4/#tag/Stream-Alert-Rules/operation/getStreamAlertRuleByUuid) |
| `create_stream_alert_rule` | Create a new alert rule for a stream | [Create Alert Rule](/api-catalog/fabricv4/#tag/Stream-Alert-Rules/operation/createStreamAlertRules) |
| `update_stream_alert_rule` | Update an existing alert rule | [Update Alert Rule](/api-catalog/fabricv4/#tag/Stream-Alert-Rules/operation/updateStreamAlertRuleByUuid) |

### Observability - Cloud Events

| Tool | Description | API Endpoint |
| ----- | ----- | ----- | 
| `get_cloud_event` | Get details about a specific cloud event | [Get Cloud Event](/api-catalog/fabricv4/#tag/Cloud-Events/operation/getCloudEventByAssetId) |
| `search_cloud_events` | Search for cloud events across your Fabric resources | [Search Cloud Events](/api-catalog/fabricv4/#tag/Cloud-Events/operation/searchCloudEvents) |

### Observability - Metrics

| Tool | Description | API Endpoint |
| ----- | ----- | ----- | 
| `get_metrics` | Get metrics for a specific asset by asset ID | [Get Metrics](/api-catalog/fabricv4/#tag/Metrics/operation/getMetricByAssetId) |
| `search_metrics` | Search for metrics across multiple assets | [Search Metrics](/api-catalog/fabricv4/#tag/Metrics/operation/searchMetrics) |



## Example Commands

Once you have configured the Fabric MCP server in your AI agent, you can use natural language to interact with your Fabric resources. The following are examples of common queries:

### Basic Queries

- **"Show me all active connections in the SV metro."** – Searches for and displays all active connections in the Silicon Valley metro.
- **"Which ports are currently over-utilized or have negative available bandwidth?"** – Analyzes port utilization to identify capacity issues.
- **"Summarize all my Fabric Cloud Routers."** – Provides an overview of all Cloud Routers in your account.
- **"How do I create a Cloud Router and what projects can I use?"** – Guides you through the Cloud Router creation process and lists available projects.
- **"Can you update the bandwidth for the connection named `<connection_name>`?"** – Modifies the bandwidth allocation for a specific connection.
- **"Can you ping this router-based connection?"** – Executes a ping command to test connectivity through a Cloud Router connection.

### Advanced Queries

The MCP server can help with complex analysis and optimization tasks:

- **"We're looking to rationalize our network footprint. Can you analyze our active and provisioned port, router, and connection utilization across all metros, identify underutilized resources, and suggest optimization strategies to reduce our monthly costs while maintaining performance? Also, can you suggest adding redundancy options to improve resiliency of our network?"** – Performs comprehensive network analysis to identify cost optimization opportunities while maintaining or improving network resilience.
- **"Find metros where we should establish redundant paths but currently don't have them."** – Analyzes network topology to identify single points of failure across metros and recommends redundancy improvements.
- **"Analyze our connection patterns and identify any single points of failure in our network topology."** – Examines connection architecture to detect vulnerabilities and suggest architectural improvements.