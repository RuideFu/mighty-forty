# **Working with .md files**

To document your progress, each of you will work with a record your progress in a .md file here on GitHub under /Students/Documentation. Here is a list of formatting shortcuts for these markdown files.

## Headings

Use `#` symbols to create headings. More `#` = smaller heading (1 through 6).

```markdown
# Heading 1
## Heading 2
### Heading 3
```

## Text Styling

| What you want | How to write it | Result |
| --- | --- | --- |
| Bold | `**bold text**` | **bold text** |
| Italic | `*italic text*` | *italic text* |
| Bold + Italic | `***both***` | ***both*** |
| Strikethrough | `~~strikethrough~~` | ~~strikethrough~~ |
| Inline code | `` `code` `` | `code` |

## Lists

**Unordered list:**
```markdown
- Item one
- Item two
  - Nested item
```

**Ordered list:**
```markdown
1. First step
2. Second step
3. Third step
```

**Task list (checkboxes):**
```markdown
- [x] Completed task
- [ ] Incomplete task
```

## Links and Images

```markdown
[Link text](https://example.com)
![Alt text for image](https://example.com/image.png)
```

## Code Blocks

Use triple backticks for multi-line code, and specify a language for syntax highlighting.

````markdown
```python
def hello():
    print("Hello, world!")
```
````

## Blockquotes

```markdown
> This is a quote.
> It can span multiple lines.
```

## Tables

```markdown
| Column 1 | Column 2 |
| --- | --- |
| Row 1, Col 1 | Row 1, Col 2 |
| Row 2, Col 1 | Row 2, Col 2 |
```

Use `:---`, `:---:`, or `---:` in the divider row to left-align, center, or right-align columns.

## Horizontal Rule

Three or more dashes, asterisks, or underscores on their own line:

```markdown
---
```

## Line Breaks

Markdown ignores single line breaks. To force one, end a line with **two spaces**, or leave a completely blank line between paragraphs for a new paragraph.

## Escaping Characters

To display a Markdown symbol literally (like `*` or `#`), put a backslash before it:

```markdown
\*not italic\*
```

## GitHub-Specific Extras

- **@mentions**: `@username` links to a GitHub user.
- **Issue/PR references**: `#123` links to issue or pull request #123 in the same repo.
- **Emoji**: `:tada:` renders as 🎉 (see the [GitHub emoji cheat sheet](https://github.com/ikatyang/emoji-cheat-sheet)).
- **Collapsible sections**:
  ```markdown
  <details>
  <summary>Click to expand</summary>

  Hidden content goes here.

  </details>
  ```

## Tips for Clean Files

- Leave a blank line before and after headings, lists, and code blocks — GitHub can render them incorrectly without spacing.
- Keep one blank line between paragraphs; avoid multiple blank lines in a row.
- Use consistent list markers (`-` or `*`, not both) throughout a file.
- Preview your `.md` file on GitHub (or in your editor) before committing to catch formatting mistakes.
