# Hello World MCP Server

A simple example server implementation using the Model Context Protocol (MCP) that demonstrates how to create a basic MCP server with a greeting tool.

## Overview

This project is a demonstration of the Model Context Protocol (MCP) server implementation. It provides a simple "say-hello" tool that greets users by name. The server is built using TypeScript and the official MCP SDK.

## Features

- MCP server implementation using TypeScript
- Simple greeting tool that accepts a name parameter
- Standard I/O (stdio) transport for communication
- Type-safe parameter validation using Zod

## Prerequisites

- Node.js (v14 or higher)
- npm (v6 or higher)

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd hello-world-mcp
```

2. Install dependencies:
```bash
npm install
```

3. Build the project:
```bash
npm run build
```

## Usage

After building the project, you can use the server in two ways:

### As a Command Line Tool

The server is available as a command-line tool named `say-hello`. You can use it after installing the package globally:

```bash
npm install -g .
say-hello
```

### As a Library

You can also use the server programmatically in your own code:

```typescript
import { McpServer } from "@modelcontextprotocol/sdk/server/mcp.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";

const server = new McpServer({
  name: "hello-world",
  version: "1.0.0",
  capabilities: {
    resources: {},
    tools: {},
  },
});

// Use the server...
```

## Project Structure

```
hello-world-mcp/
├── build/           # Compiled JavaScript files
├── public/          # Public assets
├── server.ts        # Main server implementation
├── package.json     # Project configuration and dependencies
├── tsconfig.json    # TypeScript configuration
└── README.md        # This file
```

## Dependencies

- `@modelcontextprotocol/sdk`: The official MCP SDK
- `zod`: Runtime type checking and validation
- `typescript`: TypeScript compiler and type definitions
- `@types/node`: TypeScript definitions for Node.js

## Development

To modify the server:

1. Make changes to `server.ts`
2. Rebuild the project:
```bash
npm run build
```

## License

This project is licensed under the terms included in the LICENSE file.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Support

For issues and feature requests, please create an issue in the repository.

## Configuration

To use this MCP server with Claude desktop, you need to configure it in your Claude desktop configuration file:

1. Navigate to your Claude desktop configuration directory:
   - Windows: `%APPDATA%\Claude\claude_desktop_config.json`
   - macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
   - Linux: `~/.config/Claude/claude_desktop_config.json`

2. Add the following configuration to your `claude_desktop_config.json`:
```json
{
  "mcpServers": {
    "hello": {
      "command": "node",
      "args": [
        "<path-to-your-project>/build/server.js"
      ]
    }
  }
}
```

Replace `<path-to-your-project>` with the absolute path to your project directory.

For example, if your project is located at `C:\Users\username\Projects\hello-world-mcp`, the configuration would look like:
```json
{
  "mcpServers": {
    "hello": {
      "command": "node",
      "args": [
        "C:\\Users\\username\\Projects\\hello-world-mcp\\build\\server.js"
      ]
    }
  }
}
```

Note: Make sure to use double backslashes (`\\`) in the Windows path.

## Verifying the Connection

After configuring the MCP server:

1. Restart Claude Desktop to apply the configuration changes
2. In the Claude Desktop interface, look for the "Search and Tools" button below the text input area
3. Click on "Search and Tools" to verify that the MCP server is connected
4. You should see the "hello" MCP server listed in the available tools

If you don't see the MCP server listed, double-check your configuration file path and ensure the server is running correctly.
