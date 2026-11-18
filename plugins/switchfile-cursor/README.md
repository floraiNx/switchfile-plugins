# switchfile plugin for Cursor

Adds the hosted switchfile MCP server (`https://mcp.switchfile.io/mcp`) and the `convert-files` skill. The agent can
then convert files from your project or from a URL, for example a PDF to Markdown with its tables for an LLM or RAG
pipeline, a PDF to XLSX, or `talk.mkv` to MP4. Results are saved next to the input file.

## Setup

1. Install the plugin from the marketplace.
2. Open the MCP settings in Cursor and connect switchfile. A switchfile page opens where you sign in with your
   switchfile account (or create one) and allow access. No API key is needed.

Conversions count toward your daily free quota and credits, like API requests. The free quota is 20 files a day.

## Examples

- "Convert docs/annual-report.pdf to Markdown and keep the tables."
- "Turn invoices/march.pdf into an Excel file."
- "Convert https://example.com/slides.pptx to PDF."

## Links

- Documentation: https://switchfile.io/docs/mcp
- Privacy policy: https://switchfile.io/privacy
- Support: hello@switchfile.io

MIT License, Aura UG (haftungsbeschränkt).
