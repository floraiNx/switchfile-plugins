# switchfile plugin for Claude Code

Adds the switchfile MCP server (`npx -y switchfile-mcp`) and the `convert-files` skill. Claude can then convert files
on your computer, for example `talk.mkv` to MP4 or `scan.pdf` to one PNG per page, and the result is saved next to
the input.

Install (Claude Code 2.1.275 or later):

```
/plugin install switchfile --marketplace floraiNx/switchfile-plugins
```

Set your API key before you start Claude Code. Create one at https://switchfile.io/dashboard/keys.

```bash
export SWITCHFILE_API_KEY=your_key
```

Requires Node.js 18 or newer.
