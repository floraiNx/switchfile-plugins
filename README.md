# switchfile plugins for Claude Code

Convert files on your computer from Claude Code with [switchfile](https://switchfile.io): video, audio, images,
documents, ebooks and more. The result is saved next to the input file.

## Install

```
/plugin marketplace add floraiNx/switchfile-plugins
/plugin install switchfile@switchfile
```

Set your API key before you start Claude Code. Create one at https://switchfile.io/dashboard/keys.

```bash
export SWITCHFILE_API_KEY=your_key
```

Requires Node.js 18 or newer. The plugin runs the MCP server from the npm package
[`switchfile-mcp`](https://www.npmjs.com/package/switchfile-mcp).

Other clients (Codex, Cursor, VS Code): see https://switchfile.io/developers#mcp.

## License

MIT, Aura UG (haftungsbeschränkt).
