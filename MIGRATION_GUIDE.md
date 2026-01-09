# Hugo Portfolio Migration Guide

## Analysis Summary
The legacy structure (HTML/CSS/JS) has been successfully transformed into a modular Hugo project.
- **Old**: Individual HTML files with repeated code.
- **New**: Shared layouts (`baseof.html`, `head.html`, `header.html`, `footer.html`) + Content files (`.md`) + Data files (`.yaml`).
- **Styling**: Migrated `assets/css/main.css` to `assets/scss/main.scss` for better asset management.

## Project Structure
```text
my-hugo-portfolio/
├── archetypes/       # Templates for new content (hugo new portfolio/my-project.md)
├── assets/           # Source assets
│   ├── scss/         # Styles (main.scss)
│   └── js/           # Scripts
├── content/          # Site content (Markdown)
│   ├── portfolio/    # Portfolio items
│   ├── about.md
│   ├── contact.md
│   ├── resume.md
│   └── _index.md     # Homepage content
├── data/             # Structured data
│   └── resume.yaml   # Resume details (Education, Experience, Skills)
├── layouts/          # HTML Templates
│   ├── _default/     # Base templates (single, list, baseof)
│   ├── page/         # Specific layouts (resume)
│   ├── portfolio/    # Portfolio list layout
│   └── partials/     # Reusable blocks (header, footer)
├── static/           # Static files (images, vendor libs)
└── hugo.toml         # Site configuration
```

## How to Run
Prerequisites: Ensure **Hugo** and **Dart Sass** are installed and in your system PATH.
1. Open terminal in `my-hugo-portfolio`.
2. Run development server:
   ```powershell
   hugo server
   ```
3. Open `http://localhost:1313`.

> [!WARNING]
> **Environment Issue**: During setup, `hugo` and `sass` commands were not found in your PATH. Please update your environment variables or reinstall these tools to build the site.

## Content Management Workflow

### 1. Updating Personal Info
- **Homepage Hero**: Edit `content/_index.md` -> `[params.hero]`.
- **Contact Info**: Edit `content/contact.md`.

### 2. Updating Resume
- Edit `data/resume.yaml`.
- Add new `education` or `experience` items in the list.
- Adjust `skills` percentages easily.

### 3. Adding Portfolio Projects
- Run command:
  ```powershell
  hugo new portfolio/my-new-project.md
  ```
- Or verify existing files in `content/portfolio/`.
- Edit the file to set:
  - `title`: Project Name
  - `category`: ["Web Design", "Development"]
  - `image`: path to image in `assets/img/`
  - `project_url`: Link to live project

### 4. Customizing Theme
- **Styles**: Edit `assets/scss/main.scss`.
- **Layouts**: Modify files in `layouts/`.

## Troubleshooting
- **"Hugo not found"**: Add Hugo to your System PATH or use the full path to `hugo.exe`.
- **Styles not loading**: Ensure `dart-sass` is installed. Hugo uses it to compile SCSS. If not available, Hugo might fail to build resources.
- **Images missing**: Check `static/assets/img`. Correct path in markdown is `assets/img/filename.png` or just `filename.png` if using page bundles (advanced).

## Deployment
1. Run `hugo` (without server) to generate the `public/` folder.
2. Upload `public/` to GitHub Pages, Netlify, or Vercel.
