# Scientific Lab Website Template

A [Quarto](https://quarto.org/)-based template for building static scientific lab and project websites. Renders to HTML (GitHub Pages), PDF (via Typst), MS Word, and GitHub Flavored Markdown.

All dependencies are managed through [pixi](https://pixi.sh/) — no manual installation of Quarto or other tools required.

## Quick start

### 1. Install pixi

```bash
curl -fsSL https://pixi.sh/install.sh | bash
```

### 2. Clone and preview

```bash
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
pixi run preview
```

This opens a live-reloading preview at `http://localhost:8000`.

### 3. Build the site

```bash
pixi run render
```

Output goes to `public/`.

## Customizing the template

### Site configuration

Edit `_quarto.yml` to change:

- **`website.title`** — your lab or project name
- **`website.site-url`** — your GitHub Pages URL
- **`website.navbar`** — top navigation links
- **`website.sidebar`** — sidebar navigation for research pages
- **`website.page-footer`** — footer text

### Colors and branding

Edit `_helper/theme.scss` — change the four color variables at the top:

```scss
$lab-primary: #2c5f7c;    // main brand color
$lab-secondary: #3a8a6e;  // secondary color
$lab-accent: #c0713a;     // warm accent
$lab-highlight: #5da5c8;  // light highlight
```

### Content structure

```
index.qmd                      # Homepage
team.qmd                       # Team members
publications.qmd               # Publications (with BibTeX)
references.bib                 # BibTeX bibliography
research/
  index.qmd                    # Research overview
  project-alpha/
    design.qmd                 # Example: project documentation
    methods.qmd                # Example: methods documentation
  project-beta/
    overview.qmd               # Example: project overview
```

Add new pages by creating `.qmd` files and adding them to the navigation in `_quarto.yml`.

### Output formats

Every page renders to four formats:

- **HTML** — primary web format with search, navigation, and table of contents
- **PDF** — two-column article layout via Typst, suitable for printing
- **DOCX** — Word format for collaborative editing
- **GFM** — GitHub Flavored Markdown

Format download links appear automatically on each page.

### Citations

1. Add BibTeX entries to `references.bib`
2. Add `bibliography: references.bib` to a page's YAML header
3. Cite with `@citationkey` syntax

## Deploying to GitHub Pages

Deployment is automated via GitHub Actions (`.github/workflows/deploy.yml`).

### Setup

1. Push this repository to GitHub
2. Go to **Settings → Pages**
3. Under **Source**, select **GitHub Actions**
4. Push to `main` — the site deploys automatically

### Custom domain (optional)

1. In **Settings → Pages**, enter your custom domain
2. Add a `CNAME` file to the repo root with your domain name
3. Configure DNS as described in [GitHub's documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)

## Available pixi tasks

| Command | Description |
|---------|-------------|
| `pixi run preview` | Live-reloading local preview |
| `pixi run render` | Build the static site to `public/` |
| `pixi run clean` | Remove generated files |

## Adding dependencies

Need Python packages for computational notebooks?

```bash
pixi add pandas seaborn matplotlib
```

All dependencies are recorded in `pixi.toml` and pinned in `pixi.lock`.
