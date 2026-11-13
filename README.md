# Linzer Lattice

A Jekyll theme for linked Markdown notes that read left to right. **Demo: https://heseltime.github.io/linzer-lattice/**

Following a link opens the note as a new pane beside the one you're reading, as in [Andy Matuschak's working notes](https://notes.andymatuschak.org/). Topics run one way, threads of reading run across them, and the home page draws all of it as a lattice, or, at the press of a button, as the top of a Linzer torte.

It runs on GitHub Pages as is: no plugins beyond the standard ones, no build step. It's used by [volcel](https://heseltime.github.io/volcel/).

## Features

- **Stacked panes.** Links open to the right; older panes fold to a spine. Follow a different link from an earlier pane and the path branches. The open panes stay in the URL (`?stackedNotes=…`). Phones get one note per page.
- **Topics and threads.** Any note with `topic: true` appears in the top bar. Under each title, the topics that reach the note, directly or two links away.
- **The lattice.** The home page lists every note by date against every topic, with a dot where they cross. Click a crossing, note or topic to see it on the torte.
- **The torte.** A full-screen view of the whole lattice as a Linzer torte: topics and notes as woven pastry strips, a drop of redcurrant jam on each crossing. Hover for labels, click to open, arrow keys to walk it.
- **Markdown first.** `[[Wiki links]]` (Obsidian style), margin notes from footnotes, *Links to this note* with the sentence each link sits in, search, KaTeX.
- **Hiding.** `published: false` keeps a note off the site; `_notes/Private/` keeps it off GitHub too. Links to either show as plain text until published.
- Light and dark mode (following the system until chosen), five background styles, keyboard and screen-reader support, reduced-motion support.

## Use it

1. **Copy the repository**: fork it, or download it and push to your own repo.
2. **Edit `_config.yml`**: `title`, `description`, `url` and `baseurl` (for `https://you.github.io/notes` use `url: "https://you.github.io"` and `baseurl: "/notes"`; for a user site or custom domain, `baseurl: ""`), `footer.copyright`, and optionally `parent_site`, `background` and `torte`.
3. **Replace the demo notes** in `_notes/Public/` with your own, and point `unfold:` in `pages/notes.md` at a note to open beside the home page (or remove it).
4. **Publish**: on GitHub, Settings → Pages → deploy from `main`, root.

## Writing

```markdown
---
title: Observability
topic: true        # optional: a topic in the top bar
order: 1           # optional: its place there
label: Observ.     # optional: its text there
emoji: 🔭          # optional, topics only
date: 2026-11-13
---

A [[Note Title]], a [[Note Title\|label]], a [[Note#Heading]], an external
[[Label::https://example.com]] link, and a margin note.[^aside]

[^aside]: Footnotes show up in the right margin.
```

Escape the pipe in `[[Note\|label]]`, or Markdown reads the line as a table.

## Configuration

| Key | Values | Default |
|:--|:--|:--|
| `background` | `trellis`, `lattice-dots`, `dawn`, `paper`, `plain` | `paper` |
| `torte.max_notes` / `torte.max_notes_small` | notes shown on the torte (wide screens / phones); the newest, plus the one you came from | `21` / `12` |
| `parent_site` | `title`, `url`, `icon`, `hint`: a second entry in the sun menu | none |
| `privatelinks.msg` | hint on links to unpublished notes | "This note hasn't been published yet." |

The logo and favicon are `assets/img/logo-badge.svg` and `assets/img/favicon.svg`.

## Preview

With Docker:

```bash
docker run --rm -p 4000:4000 -v "$PWD":/srv/site -w /srv/site ruby:3.1.1-alpine3.15 \
  sh -c "apk add --no-cache build-base && gem install bundler:2.4.22 && bundle install && bundle exec jekyll serve --host 0.0.0.0 --config _config.yml,debug.yml --unpublished"
```

Open http://localhost:4000. `--unpublished` shows `published: false` notes with a "Hidden" banner.

## Code

| File | What it does |
|:--|:--|
| `assets/js/stack.js` | panes, URL state, folding, unfolding |
| `assets/js/wikilinks.js` | `[[links]]`, previews, unpublished links |
| `assets/js/sidenotes.js` | footnotes into margin notes |
| `assets/js/lattice.js` | crossings, the All notes lattice, the thread line |
| `assets/js/torte.js` | the torte view |
| `assets/css/stack.css` | layout, colours, dark mode |
| `_includes/GardenData.html` | note and link data for the scripts |
| `_includes/Backlinks.html` | *Links to this note* |
| `_layouts/Post.html` | the page shell |

## Credits

By [Jack Heseltine](https://heseltime.github.io/). Built on [Jekyll Garden](https://github.com/Jekyll-Garden/jekyll-garden.github.io) (MIT), after [Simply Jekyll](https://github.com/raghudotcc/simply-jekyll). The reading model follows [Andy Matuschak's notes](https://notes.andymatuschak.org/); none of its code is used. Search by [Lunr](https://lunrjs.com/), math by [KaTeX](https://katex.org/).

## License

MIT, see `LICENSE`.
