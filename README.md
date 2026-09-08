# Research Exercise 2

A small local tool for writing a course research exercise in markdown and exporting it
as a standalone HTML file. The paper is a FASB Accounting Standards Codification
exercise for ACC-242.

The editor is a single HTML page with no build step, no framework, and no bundler.
Split view by default: markdown source on the left, live preview on the right. Edits
are kept in localStorage, so they survive a reload. Reset to original discards them
and reloads the markdown file.

Download HTML writes a self-contained copy of the rendered paper with all CSS inlined
and no scripts, so it opens offline and prints to PDF cleanly. Download Markdown saves
the source.

## Running it

Open `index.html` in a browser.

Browsers block `fetch` on `file://` URLs, so when opened that way the page falls back
to a copy of the markdown inlined in `index.html`. To have it read the real file
instead, serve the folder and open it over http:

    python3 -m http.server

Then visit http://localhost:8000. Both paths render the same document.

## Files

- `index.html` — the editor, preview, and HTML exporter, in one page
- `research_exercise_2.md` — the paper itself, the source of truth for its text
- `vendor/marked.min.js` — markdown parser
- `.gitignore` — local tooling and editor files

## Third party code

`vendor/marked.min.js` is [marked](https://github.com/markedjs/marked) v12.0.2, MIT
licensed, committed to the repo on purpose so the tool works offline with no install
step. Everything else here is original.
