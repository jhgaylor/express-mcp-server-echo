# Express MCP Server

A stateless Model Context Protocol (MCP) server built with Express and TypeScript.

## Features

- Stateless MCP server implementation with modern Streamable HTTP transport
- TypeScript for type safety
- Express.js for HTTP handling

## Requirements

- Node.js 18+ 
- npm or yarn

## Installation

```bash
# Clone the repository (or download)
git clone https://github.com/your-username/sample-express-mcp-server.git
cd sample-express-mcp-server

# Install dependencies
npm install
```

## Development

```bash
# Build the TypeScript code
npm run build

# Run in development mode with auto-reloading
npm run dev

# Run tests (when added)
npm test
```

## Server Structure

```
src/
  ├── index.ts                # Main application entry point
  ├── server.ts               # Server configuration and setup
  ├── middleware/             # Express middleware
  │   ├── validate.ts         # Request validation
  │   └── error-handler.ts    # Global error handling
  └── tools/                  # MCP tools organized by category
      ├── math.ts             # Math calculation tools
      └── text.ts             # Text manipulation tools
```

## Available Tools

### Math Tools

- `add`: Add two numbers
- `subtract`: Subtract one number from another
- `multiply`: Multiply two numbers
- `divide`: Divide one number by another

### Text Tools

- `uppercase`: Convert text to uppercase
- `lowercase`: Convert text to lowercase
- `reverse`: Reverse the characters in a string
- `wordCount`: Count the number of words in a text

## MCP Protocol

This server implements the [Model Context Protocol](https://modelcontextprotocol.io/) (MCP), a standardized way for LLMs to interact with external data and functionality. It exposes a stateless API endpoint that responds to JSON-RPC requests.

### API Usage

Send a POST request to `/mcp` with a JSON-RPC payload:

```bash
curl -X POST http://localhost:3001/mcp \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "method": "callTool",
    "params": {
      "name": "add",
      "arguments": {
        "a": 5,
        "b": 7
      }
    },
    "id": 1
  }'
```

## Adding New Tools

To add new tools, create a new file in the `src/tools` directory following the pattern in the existing files, then register your module in `src/server.ts`.

## License

[ISC](LICENSE) 