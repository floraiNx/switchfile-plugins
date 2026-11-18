---
name: convert-files
description: Convert files with switchfile, for example PDF to Markdown for an LLM or RAG pipeline, PDF to XLSX, DOCX to PDF, HEIC to JPG, MKV to MP4 or WAV to MP3. Use when the user asks to convert, export or change the format of a local file or a file at a URL, to read a PDF or Office document as Markdown or JSON, or asks which formats a conversion supports.
---

# Convert files with switchfile

The switchfile MCP server runs at `https://mcp.switchfile.io/mcp`. The user signs in once with a switchfile account.
Its tools: `convert_url`, `create_upload`, `convert_upload`, `get_conversion`, `list_formats`,
`check_pdf_accessibility` and `account`.

## A local file

1. Call `create_upload` with `filename` (the name with its extension, which sets the input format) and `size` in
   bytes.
2. Send the file with HTTP PUT to the returned `url`, adding the returned headers if there are any:
   `curl -sS -T "/absolute/path/report.pdf" "<url>"`
3. Call `convert_upload` with `upload_id` and `to`, for example `md`, `xlsx`, `pdf` or `png`.
4. Download every result link right away (links expire) and save it next to the input file, unless the user wants
   another place: `curl -sS -L -o "/absolute/path/report.md" "<link>"`. Do not overwrite an existing file without
   asking.

## A file at a public URL

Call `convert_url` with `url` and `to`. Pass `filename` when the URL does not show the format, for example
`report.docx`.

## Reading documents

- To read a PDF or an Office document as text, convert it to `md`. Tables become pipe tables, and each page starts
  with a comment such as `<!-- page 4 -->` that you can cite.
- To work with the content as data, convert it to `json`: each page lists its text blocks, and tables come as cells
  with row and column.
- If you are unsure whether a conversion exists, call `list_formats` with `input` (for example `pdf`). It returns
  the targets with their minimum credits.

## Results and errors

- A longer conversion returns an `id` instead of links. Call `get_conversion` with `id` and `wait` up to 25 until it
  has finished.
- Several results, for example one PNG per PDF page, come as several links.
- If the tools report that the user is not signed in, ask the user to connect switchfile in Cursor's MCP settings.
- If the daily free quota or the credits are used up, tell the user. `account` shows the balance and when the free
  quota resets.
