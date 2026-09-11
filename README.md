# mcp-snippetbox

MCP server template I base new tools on

## Highlights

- Notes path set by MCP_NOTES_FILE or --notes-file
- Every tool carries a real docstring, so clients get descriptions
- Five tools: add / get / update / delete / list notes
- Atomic saves (temp file + os.replace) behind a write lock
- Includes a Claude Desktop config snippet with absolute paths
- A missing note raises instead of returning the string 'not found'

## Usage

```bash
# claude_desktop_config.json  (use ABSOLUTE paths: Claude does not
# run from the repo directory, so a bare "server.py" is not found)
# {
#   "mcpServers": {
#     "notes-box": {
#       "command": "python",
#       "args": ["/abs/path/to/mcp-snippetbox/server.py"],
#       "env": {"MCP_NOTES_FILE": "/abs/path/to/notes.json"}
#     }
#   }
# }
python server.py --help
```

## Getting started

```bash
pip install -r requirements.txt
```

## Project structure

```text
├── .github/
│   └── workflows/
│       └── ci.yml
├── docs/
│   ├── development.md
│   ├── faq.md
│   ├── roadmap.md
│   └── usage.md
├── examples/
│   └── quickstart.md
├── tests/
│   └── test_notes.py
├── .gitignore
├── CHANGELOG.md
├── CONTRIBUTING.md
├── LICENSE
├── requirements.txt
└── server.py
```

## Development

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
python -m pytest -q
```

## Changelog

- `0.1.1` - fix edge case in argument parsing
- `0.1.0` - first working version

## License

MIT - see [LICENSE](LICENSE).
