# Demo MCP Server

A minimal [Model Context Protocol](https://modelcontextprotocol.io) server built with FastMCP: the smallest working example I use as a template before building larger servers ([study-buddy](https://github.com/eshitakundu/study-buddy), [flowchart-mcp-server](https://github.com/eshitakundu/flowchart-mcp-server), [hn-mcp-server](https://github.com/eshitakundu/hn-mcp-server), [github-ranker-remote-mcp-server](https://github.com/eshitakundu/github-ranker-remote-mcp-server)).

## Tools

| Tool | Input | Returns |
|---|---|---|
| `greet` | `name: str` | A friendly greeting picked at random |
| `get_timestamp` | none | Current time as ISO string, Unix timestamp, formatted date and weekday |

Both tools use typed signatures and docstrings, which FastMCP turns into the tool schema and descriptions the client model sees.

## Run it

Requires Python 3.12+ and [uv](https://docs.astral.sh/uv/).

```bash
git clone https://github.com/eshitakundu/demo-mcp-server.git
cd demo-mcp-server
uv sync

uv run mcp dev main.py        # open the MCP Inspector to call the tools
uv run python main.py         # or run over stdio
```

## Use it in Claude Desktop

Add this to `claude_desktop_config.json` (Settings → Developer → Edit config), with the path to your clone:

```json
{
  "mcpServers": {
    "demo": {
      "command": "uv",
      "args": ["run", "--directory", "/path/to/demo-mcp-server", "python", "main.py"]
    }
  }
}
```

Restart Claude Desktop, then ask it to greet you or tell you the time.

## Stack

Python · FastMCP · MCP Python SDK · uv
