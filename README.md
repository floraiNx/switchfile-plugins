# switchfile plugins for Claude Code and Cursor

Convert files on your computer from Claude Code with [switchfile](https://switchfile.io): video, audio, images,
documents, ebooks and more. The result is saved next to the input file.

## Install

```
/plugin install switchfile --marketplace floraiNx/switchfile-plugins
```

On older Claude Code versions:

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

## Cursor

The Cursor plugin in `plugins/switchfile-cursor` uses the hosted server `https://mcp.switchfile.io/mcp`: you sign in
with your switchfile account, no API key needed. It adds the same `convert-files` skill, adapted to the hosted tools.
See [its README](plugins/switchfile-cursor/README.md).

Other clients (Codex, VS Code): see https://switchfile.io/developers#mcp.

## License

MIT, Aura UG (haftungsbeschränkt).
