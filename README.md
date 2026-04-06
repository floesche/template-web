# Scientific Lab Website Template

A [Quarto](https://quarto.org/)-based template for building static scientific lab and project websites. Renders to HTML (GitHub Pages), PDF (via Typst), MS Word, and GitHub Flavored Markdown.

All dependencies are managed through [pixi](https://pixi.sh/), so no manual installation of Quarto or other tools is required. If you get stuck, see [Getting help from an LLM](#getting-help-from-an-llm) below.

## Quick start

### 1. Install pixi

pixi manages **all** dependencies (Quarto, Python, dart-sass, and more). You do **not** need to install them separately.

Follow the [official installation instructions](https://pixi.sh/latest/getting_started/) for your operating system, or use the quick commands below.

> **Important:** Pick the command that matches your operating system. Running the wrong one will produce confusing errors.

**Windows**: open **PowerShell** and run:

```powershell
powershell -ExecutionPolicy Bypass -c "irm -useb https://pixi.sh/install.ps1 | iex"
```

**Linux** or **macOS**: open a terminal and run:

```bash
curl -fsSL https://pixi.sh/install.sh | sh
```

After installation, **close and reopen your terminal** so the `pixi` command is available.

### 2. Create your own copy

This repository is a **GitHub template**. Instead of cloning it directly, first create your own copy:

1. Go to [github.com/floesche/template-web](https://github.com/floesche/template-web)
2. Click the green **"Use this template"** button (top-right) and choose **"Create a new repository"**
3. Enter a name for your repository (e.g., `my-lab-website`) and click **"Create repository"**

You now have your own repository at `https://github.com/yourusername/my-lab-website`.

### 3. Clone and preview

Navigate to the folder where you want to store the project, then clone **your copy** (replace the URL with your own repository's URL from the previous step):

**Windows (PowerShell):**

```powershell
cd ~\Documents
git clone https://github.com/yourusername/my-lab-website.git
cd my-lab-website
pixi run preview
```

**Linux / macOS:**

```bash
cd ~/Documents
git clone https://github.com/yourusername/my-lab-website.git
cd my-lab-website
pixi run preview
```

> **Note:** The first run takes a few minutes because pixi downloads and installs all dependencies (Quarto, Python, dart-sass, etc.) automatically. Subsequent runs are fast.

This opens a live-reloading preview at `http://localhost:8000`.

> **Troubleshooting:** Always use `pixi run preview` (not `quarto preview` directly). pixi sets up the correct environment with all required tools. If you see errors about missing tools or paths, make sure you are running commands through pixi. See [Windows troubleshooting](#windows-troubleshooting) below for platform-specific issues.

### 4. Build the site

```bash
pixi run render
```

Output goes to `public/`.

## Customizing the template

### Site configuration

Edit `_quarto.yml` to change:

- **`website.title`**: your lab or project name
- **`website.site-url`**: your GitHub Pages URL
- **`website.navbar`**: top navigation links
- **`website.sidebar`**: sidebar navigation for research pages
- **`website.page-footer`**: footer text

### Colors and branding

Edit `_helper/theme.scss` and change the four color variables at the top:

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

- **HTML**: primary web format with search, navigation, and table of contents
- **PDF**: two-column article layout via Typst, suitable for printing
- **DOCX**: Word format for collaborative editing
- **GFM**: GitHub Flavored Markdown

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
4. Push to `main`. The site deploys automatically

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

## Editing files directly on GitHub

You can edit files without installing anything locally:

1. Go to your repository on GitHub
2. Navigate to the file you want to edit (e.g., `research/project-alpha/design.qmd`)
3. Click the **pencil icon** (Edit this file) in the top-right corner of the file view
4. Make your changes in the editor
5. Scroll down, add a short commit message describing your change, and click **Commit changes**

The site will rebuild and deploy automatically after each commit. See [GitHub's documentation on editing files](https://docs.github.com/en/repositories/working-with-files/managing-files/editing-files) for more details.

## Working with git

If you are new to git, see [GitHub's Git Handbook](https://docs.github.com/en/get-started/using-git/about-git) for a thorough introduction.

Before you start editing, pull the latest changes:

```bash
git pull
```

After editing files, stage your changes, commit, and push:

```bash
git add research/my-edited-file.qmd
git commit -m "Describe what you changed"
git push
```

Use `git status` at any time to see which files have been modified.

## Adding dependencies

Need Python packages for computational notebooks?

```bash
pixi add pandas seaborn matplotlib
```

All dependencies are recorded in `pixi.toml` and pinned in `pixi.lock`.

## Windows troubleshooting

### "Theme file compilation failed" error

If you see a "Theme file compilation failed" error on Windows, try deleting the `.pixi` folder and reinstalling:

```powershell
Remove-Item -Recurse -Force .pixi
pixi run preview
```

This project's `pixi.toml` includes a workaround for a [known Windows issue](https://github.com/quarto-dev/quarto-cli/issues/6651) in the conda-packaged Quarto. The issue is fixed upstream in Quarto 1.9.23 and the workaround will be removed once that version is available through conda-forge.

## Getting help from an LLM

If you run into problems and want to ask ChatGPT, Copilot, Claude, or another LLM for help, include the following context in your prompt so it can give you accurate advice:

> I'm working with a Quarto website project that uses **pixi** (https://pixi.sh/) to manage all dependencies. pixi installs Quarto, Python, dart-sass, and everything else automatically. I do not install these tools separately. I run all commands through pixi (e.g., `pixi run preview`, `pixi run render`). The project configuration is in `_quarto.yml` and dependencies are defined in `pixi.toml`.
>
> [Paste your error message here]

This prevents the LLM from suggesting you install Quarto or Python manually, create virtual environments, or take other steps that bypass pixi and cause further issues.
