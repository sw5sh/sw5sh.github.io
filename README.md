# Anish Biswas — Academic Homepage (Jekyll)

Plain, fast, no build-tool learning curve. One HTML page + two YAML files.

## Edit content
- **Name, role, bio, footer links (CV/Scholar/GitHub/Email):** edit `_config.yml`.
- **Publications:** edit `_data/publications.yml` — add/remove/reorder entries freely; each is a plain YAML block:
  ```yaml
  - year: "2025"
    title: "Paper Title"
    authors: "Anish Biswas, Coauthor Name, et al."
    venue: "Conference '25"
    pdf: "https://link-to-pdf"   # omit this line if no PDF
    code: "https://github.com/..." # omit this line if no code
    link: "#"                    # where the title links to
  ```
  Your own name in `authors` is automatically bolded — just spell it exactly as in `_config.yml`'s `name`.
- **Photo:** replace `assets/photo.jpg` with your own (square-ish works best — it's shown at 112×112 with slightly rounded corners).

## Run locally
Requires Ruby (macOS/Linux usually have it; Windows: use WSL or RubyInstaller).

```
gem install bundler
bundle install
bundle exec jekyll serve
```

If you're on **Ruby 3.4+** and see `cannot load such file -- erb` (or similar for `csv`/`logger`/`base64`), that's expected — those became separate gems in 3.4 and Jekyll doesn't list them as dependencies yet. The Gemfile in this repo already adds them explicitly, so just re-run:
```
bundle install
bundle exec jekyll serve
```

Open http://localhost:4000 — edits to any file auto-rebuild.

## Deploy — GitHub Pages (free, recommended)
1. Push this folder to a GitHub repo.
2. Repo Settings → Pages → Source: "Deploy from a branch" → pick `main` (or add a GitHub Actions workflow if you want the newest Jekyll version — GitHub Pages' built-in Jekyll support pins an older version but works fine for a page this simple).
3. Your site is live at `https://<username>.github.io/<repo>/` within a minute or two of pushing.

If you use a **custom domain**, add a `CNAME` file with your domain name at the project root, and set `url`/`baseurl` in `_config.yml` accordingly.

## Why this instead of the Next.js version
Zero client-side JavaScript, no hydration, no framework runtime — this is close to the fastest a webpage can load. Editing is YAML/Markdown, not TypeScript/JSX. Trade-off: no interactivity — but this page doesn't need any.
