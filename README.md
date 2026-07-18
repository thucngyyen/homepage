# homepage

Single-file portfolio page (`index.html`). No framework, no build step.

- **Edit projects**: open `index.html`, replace the `.project` blocks marked `PLACEHOLDER`.
- **Deploy**: push to GitHub, then enable Pages in repo Settings → Pages → Deploy from branch → `main` / root.
- **Run locally**: `python3 -m http.server 8000` from the repo root, then open <http://localhost:8000>. (The blog needs an HTTP server — it `fetch()`es markdown, which browsers block on `file://`.)

## Writing a new blog post

1. Create `blog/my-post-title.md` with `title` and `date` frontmatter. The filename (minus `.md`) becomes the URL: `blog/?post=my-post-title`.

   ```markdown
   ---
   title: my post title
   date: 2026-07-17
   ---

   body goes here…
   ```

2. Add the filename — just the name — to `blog/posts.json`. Order doesn't matter; the list reads `title`/`date` from each file's frontmatter and sorts by date, newest first.

   ```json
   ["my-post-title.md"]
   ```

3. Preview locally, commit, push. Done — no build step.

Supported markdown: `#`–`###` headings, paragraphs, `-` lists, `> ` quotes, fenced code blocks, inline `` `code` ``, `**bold**`, `*italic*`, and `[links](url)`. No tables or images (the parser in `blog/index.html` is ~50 lines — extend it if you need more).
