---
title: Writing Notes
date: 2026-11-11
---

Notes are Markdown files in `_notes/Public/`, readable in Obsidian. A note needs a title and, ideally, a date:

```yaml
---
title: Writing Notes
date: 2026-11-11
---
```

Link with `[[Note Title]]`, `[[Note Title\|custom text]]` (escape the pipe, or Markdown reads the line as a table), `[[Note Title#Heading]]`, or `[[Label::https://example.com]]` for an external link.

Footnotes become margin notes, next to the sentence they belong to.[^margin] Every note ends with *Links to this note*: the notes that link here, each with the sentence the link sits in.

To keep a note off the site, add `published: false` (the file stays in the repository), or put it in `_notes/Private/`, which is never built or committed. Links to such notes show as plain text until they're published.

See [[Topics and Threads]] for the top bar.

[^margin]: Like this one. Write `Claim.[^id]` in the text and `[^id]: the aside` below.
