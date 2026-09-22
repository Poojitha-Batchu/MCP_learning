# Expense Tracker MCP Server

A local FastMCP server that stores expenses in SQLite and exposes expense tools
to MCP clients.

## Requirements

- Python 3.11 or newer
- [uv](https://docs.astral.sh/uv/)
- FastMCP 4 (installed from `pyproject.toml`)

## Run locally

Run these commands from the project root:

```powershell
uv sync
uv run fastmcp run main.py
```

For development with automatic reloads:

```powershell
uv run fastmcp run main.py --reload
```

The server creates `expenses.db` next to `main.py` on first run.

## MCP Inspector

Start the Inspector UI with:

```powershell
uv run fastmcp dev inspector main.py
```

FastMCP opens the Inspector in a browser. `fastmcp dev main.py` is an older
command format; in FastMCP 4, `dev` requires the `inspector` subcommand.

## Claude Desktop

Install the server from the project root:

```powershell
uv run fastmcp install <--config-path Claude-path> claude-desktop main.py
```

End the Claude task from task manager.

Then fully quit and reopen Claude Desktop. Find the server under:

**Settings -> Developer -> Local MCP servers**

Do not use **Add connector**; that menu is separate from local MCP servers.

On Windows, the standard Claude Desktop configuration file is:

```text
C:\Users\<username>\AppData\Roaming\Claude\claude_desktop_config.json
```

If Claude Desktop is installed from the Microsoft Store, its application data
may also be under:

```text
C:\Users\<username>\AppData\Local\Packages\Claude_pzs8sxrjxfjjc\LocalCache\Roaming\Claude
```

## Available MCP components

Tools:

- `add_expense`: Add an expense with a date, amount, category, optional
	subcategory, and optional note.
- `list_expenses`: List expenses within an inclusive date range.
- `summarize`: Summarize totals by category, optionally filtered by category.

Resource:

- `expense://categories`: Read the categories from `categories.json`.
