---
name: convert-files
description: Convert files between formats with switchfile, for example MKV to MP4, HEIC to JPG, DOCX to PDF, PDF to PNG pages, WAV to MP3, Markdown to PDF. Use when the user asks to convert, export or change the format of a local file or a file at a URL, to extract PDF pages as images, or asks which formats or options a conversion supports.
---

# Convert files with switchfile

The switchfile MCP server provides these tools: `convert_file`, `convert_url`, `list_formats`, `get_conversion` and
`account`.

## Steps

1. Use absolute paths. Resolve relative paths against the current project directory before calling a tool.
2. If you are unsure whether a conversion exists, or the user asks for a setting (quality, codec, size, page range),
   call `list_formats` with `from` and `to`. It returns whether the pair is supported, its credits and its options.
   Use only option names and values from that answer.
3. Call `convert_file` with `input_path` (or `input_paths` for several files with the same target) and `to`. Pass
   `output_dir` only if the user wants the result somewhere else than next to the input.
4. Report the saved paths from `outputs`, and any `notes`. Mention the credits used if they are above zero.

## Results and errors

- Several results (for example one PNG per PDF page) are saved as `name-1.png`, `name-2.png`, ...
- `OUTPUT_EXISTS`: a file with the result name already exists. Ask the user before setting `overwrite` to true, or
  use another `output_dir`.
- `status: "pending"`: the conversion is still running, or its result is not fully saved yet. Make the
  `get_conversion` call that `next_step` names, with `wait_seconds` up to 30, until it is finished. Repeating it
  continues an interrupted download; files listed in `outputs` are already saved.
- `status: "not_started"`: `timeout_seconds` was reached before this file started. Nothing was uploaded and no
  credits were used; convert it again in a new call.
- `NO_API_KEY` or `UNAUTHENTICATED`: the user needs an API key from https://switchfile.io/dashboard/keys in the
  environment variable `SWITCHFILE_API_KEY`, then a restart of Claude Code.
- `CREDITS_EXCEEDED` or `QUOTA_EXCEEDED`: tell the user; `account` shows the balance and when the free quota resets.
- `UNSUPPORTED_PAIR`: call `list_formats` with `from` to suggest a supported target.

For a file at a public URL, use `convert_url` with `url`, `to` and `output_dir`; the file does not pass through this
computer on the way in.

## Without the MCP server

If the tools are not available, the same works on the command line (Node.js 18 or newer):

```bash
npx -y -p switchfile-mcp switchfile convert /path/to/input.mkv --to mp4
npx -y -p switchfile-mcp switchfile formats --from pdf --to png
```
