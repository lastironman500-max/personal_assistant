# Notion Dual-Write Rule

## Trigger

After EVERY file write (using the Write tool) in this project, you MUST also create a corresponding Notion page in the "Assistant Results" database.

## How to Write to Notion

Use `mcp__claude_ai_Notion__notion-create-pages` with:

```json
{
  "parent": {
    "data_source_id": "60f254a1-1326-42f0-8f5a-629a52b3ebd4"
  },
  "pages": [
    {
      "properties": {
        "Title": "<descriptive title for the output>",
        "Source File": "<absolute path of the file written>",
        "Type": "<one of: PRD, Analysis, User Story, Research, Notes, Strategy, Spec, Other>",
      },
      "content": "<the file content, converted to Notion-flavored Markdown>"
    }
  ]
}
```

## Rules

1. The Notion page content should match the file content. Convert any non-standard markdown to Notion-flavored markdown if needed.
2. Choose the most appropriate "Type" value based on the content. When unsure, use "Other".
3. Use a descriptive "Title" — not just the filename. Summarize what the content is about.
4. Always include the full "Source File" path so the file and Notion page can be cross-referenced.
5. Do NOT skip the Notion write for any reason. If the Notion write fails, inform the user.
6. Do NOT create a Notion page for files that are configuration, rules, or gitignore files (e.g., `.gitignore`, `.claude/rules/*`, `package.json`). Only mirror substantive content files.

## Exceptions

Skip the Notion write for:
- `.gitignore`, `.env`, config files
- `.claude/` directory files (rules, agents, settings)
- `node_modules/`, `package.json`, `package-lock.json`
- Binary files, images
- Test files (`*.test.*`, `*.spec.*`)
