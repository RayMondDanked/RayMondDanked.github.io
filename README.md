# raymonddanked.github.io

Personal site built with [Quarto](https://quarto.org). Live at
<https://raymonddanked.github.io>.

## Publishing a new post

1. Create a folder under `posts/` named after the post slug, e.g.
   `posts/black-box-optimization/`.
2. Inside it, create `index.qmd` with YAML front matter:

```yaml
   ---
   title: "Post title"
   date: 2026-09-02
   categories: [optimization, julia]
   ---
```

3. Write the body below the front matter. Any images the post uses go
   in the same folder and are referenced relatively: `![](figure.png)`.
4. Preview locally: `quarto preview`
5. Commit the source and deploy:

```powershell
   git add .
   git commit -m "Add post: <title>"
   git push
   quarto publish gh-pages
```

The listing on the home page updates itself — no index to edit by hand.

## Branches

- `main` — source. What you write and version.
- `gh-pages` — built HTML. Managed entirely by `quarto publish`; never
  edit it directly.

`quarto publish gh-pages` only updates `gh-pages`. Pushing to `main` is
a separate step, and skipping it means the source history falls behind
what's published.

## Local preview

```powershell
quarto preview     # live-reloading server, Ctrl+C to stop
quarto render      # build to _site/ without serving
```

In VSCode, Ctrl+Shift+K renders the current document.

## Layout

```
_quarto.yml     site config: title, navbar, theme, format
index.qmd       home page (auto-generated post listing)
about.qmd       about page
styles.css      custom CSS
posts/          one folder per post, each with index.qmd
_site/          build output (gitignored, do not commit)
```

## Environment

Quarto is at `C:\Users\Veerawat\AppData\Local\quarto`, with `bin/` on
the user PATH. If `quarto` stops resolving, that PATH entry is the first
thing to check.

## Notes

- Math uses KaTeX (`html-math-method: katex` in `_quarto.yml`).
  `$inline$` and `$$display$$` both work.
- Executable code blocks require a Jupyter kernel. Python works already;
  Julia would need IJulia installed.
- GitHub Pages serves from the `gh-pages` branch, root folder. That is
  set under Settings → Pages and should not need changing again.