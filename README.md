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



## Colors

Currently, the color schemes are 
- Olive Garden Feast: https://coolors.co/palette/606c38-283618-fefae0-dda15e-bc6c25 
- Pastel Dreamland Adventure: https://coolors.co/palette/cdb4db-ffc8dd-ffafcc-bde0fe-a2d2ff 
- Golden Summer Fields: https://coolors.co/palette/ccd5ae-e9edc9-fefae0-faedcd-d4a373
- Fiery Ocean: https://coolors.co/palette/780000-c1121f-fdf0d5-003049-669bbc 
- Meadow Green: https://coolors.co/palette/d9ed92-b5e48c-99d98c-76c893-52b69a-34a0a4-168aad-1a759f-1e6091-184e77 
- Refreshing Summer Fun: https://coolors.co/palette/8ecae6-219ebc-023047-ffb703-fb8500
- Neutral Harmony Bliss: https://coolors.co/palette/f4f1de-e07a5f-3d405b-81b29a-f2cc8f 
- Dark Sunset: https://coolors.co/palette/335c67-fff3b0-e09f3e-9e2a2b-540b0e 
- Vibrant Color Fiesta: https://coolors.co/palette/ffbe0b-fb5607-ff006e-8338ec-3a86ff
- Sunny Beach Day: https://coolors.co/palette/264653-2a9d8f-e9c46a-f4a261-e76f51 
- Autumn Harvest: https://coolors.co/palette/6f1d1b-bb9457-432818-99582a-ffe6a7 
- Summer Dream: https://coolors.co/palette/0081a7-00afb9-fdfcdc-fed9b7-f07167
- Black & Gold Elegance: https://coolors.co/palette/000000-14213d-fca311-e5e5e5-ffffff 
- Midnight Sky: https://coolors.co/palette/27187e-758bfd-aeb8fe-f1f2f6-ff8600 
- Earthy Tones: https://coolors.co/palette/a3a380-d6ce93-efebce-d8a48f-bb8588
- Soft Lavender: https://coolors.co/palette/22223b-4a4e69-9a8c98-c9ada7-f2e9e4 
- Fresh Greens: https://coolors.co/palette/386641-6a994e-a7c957-f2e8cf-bc4749 
- Pastel Rainbow Fantasy: https://coolors.co/palette/ffadad-ffd6a5-fdffb6-caffbf-9bf6ff-a0c4ff-bdb2ff-ffc6ff-fffffc
- Blue Serenity: https://coolors.co/palette/edf2fb-e2eafc-d7e3fc-ccdbfd-c1d3fe-b6ccfe-abc4ff 
- Warm Neutral Tones: https://coolors.co/palette/ecf8f8-eee4e1-e7d8c9-e6beae-b2967d
