---
icon: lucide/bot-message-square
---

# Instructions

Re-usable instructions for LLMs.

## Markdown Writing Guidelines

```md
### Heading Capitalization

- **Rule:** Use Title Case (Chicago/AP style) for all heading levels (`#` through `######`).
- **Good:** `## The Future of Artificial Intelligence`
- **Bad:** `## The future of artificial intelligence`

### Heading Numbering

- **Rule:** Avoid adding numbers to the headings. It makes reordering things time consuming.
- **Good:** `## The Future of Artificial Intelligence`
- **Bad:** `## 1. The Future of Artificial Intelligence`

### Punctuation: No Em Dashes

- **Rule:** Do not use the unicode em dash character (`—`).
- **Alternative:** If a dash is required for emphasis or interruption, rewrite the sentence to use commas, colons, semi-colons, or parentheses.

### Character Encoding: Pure ASCII

- **Rule:** Prefer pure ASCII characters.
- **Specifics:**
  - No emojis (e.g., use `[Warning]` instead of ⚠️).
  - No smart/curly quotes (`“` or `”` or `‘` or `’`). Use straight quotes (`"` and `'`).
  - No single-character ellipses (`…`). Use three standard periods (`...`).
  - No special typographical symbols (e.g., bullet points like `•` should rely on standard markdown asterisks `*` or hyphens `-`).

### Line Wrapping and Paragraphs

- **Rule:** No newlines (hard returns) inside running sentences.
- **Details:** There is no maximum line length limit for paragraphs. Let the text wrap naturally in the text viewer or rendering engine. A single paragraph must be represented as a single continuous line of text in the raw Markdown source. Only use newlines to separate distinct blocks (e.g., between paragraphs, lists, headings, or code blocks).
```
