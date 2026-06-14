# Tareq Al-Ahdal — personal academic site (Quarto)

A vibrant, multi-section personal site: a bio-first homepage, plus
**Publications**, **Projects**, **Blog**, and **About** pages. Built with
[Quarto](https://quarto.org). Blog posts are `.qmd` files; the listings and
RSS feed update automatically.

Live at: **https://alahdalta1.github.io** (after publishing — see below)

---

## Preview locally

From inside this folder, in PowerShell:

```
quarto preview
```

Opens the site in your browser and live-reloads as you edit. Stop with Ctrl-C.
Build once (output → `_site/`):

```
quarto render
```

> The example blog posts use plain code blocks that **display without running**,
> so you don't need R or Python installed to preview or publish. When you want
> code to actually execute, change ` ``` r ` to ` ```{r} ` (and install R), or
> ` ``` python ` to ` ```{python} ` (and install Python + the `reticulate` R package).

---

## Editing each page

| Page | File | What to change |
|------|------|----------------|
| Homepage | `index.qmd` | Bio text, stats, the few featured items |
| Publications | `publications.qmd` | Each paper is a `::: {.pub} … :::` block |
| Projects | `projects.qmd` | Each repo is an `<a class="proj-card">…</a>` block |
| Blog | `blog.qmd` | Auto-lists everything in `posts/` |
| About | `about.qmd` | Bio, interests, photo |
| Colors | `theme.scss` + `styles.css` | Palette is teal → indigo |

**Add a photo:** drop `profile.jpg` into `images/`, then in `about.qmd` change
`image: images/logo.png` to `image: images/profile.jpg`. To use it in the
homepage hero too, replace the `TA` placeholder block in `index.qmd`.

**Add a publication:** copy a `::: {.pub} … :::` block in `publications.qmd`,
change the badge class (`lancet` / `iscience` / `other`), title, venue, and tags.

**Add a blog post:** make `posts/my-post/index.qmd` with a header
(`title`, `description`, `date`, `categories`) and write below it.

---

## Publish to GitHub Pages

### First time
1. Create a **public** repo on GitHub named exactly `alahdalta1.github.io`
2. In this folder (PowerShell):
   ```
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/alahdalta1/alahdalta1.github.io.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Source: GitHub Actions**
   (the workflow in `.github/workflows/publish.yml` renders + deploys on every push)
4. Wait ~1–2 min → live at **https://alahdalta1.github.io**

   *Simpler alternative:* run `quarto publish gh-pages` locally instead of steps 2–3.

### Every update after
```
git add .
git commit -m "Update"
git push
```
The site rebuilds itself.
