# Introduction
Training for AI-assisted survey creation

Live: https://surquest.github.io/training-ai-assisted-survey/

## Overview

This repository contains a Reveal.js presentation used to demonstrate how AI can assist with survey design and data analysis. The slide deck is authored as a static site under `src/` and uses a custom theme, local fonts, an SVG logo, and Reveal.js plugins (markdown, highlight, notes, math).

Key files
-
- `src/index.html` — presentation entry.
- `src/css/theme.css` — custom theme, typography, code/table/image styles and copy-button styling.
- `src/content/` — markdown slide content.
- `src/assets/` — logo and other static assets.
- `.github/workflows/deploy.yml` — GitHub Actions workflow used to publish the site to GitHub Pages.

### Preview locally

Open `src/index.html` in a browser, or serve the `src/` folder with a static server for proper plugin behavior.

Quick local preview (Python 3):

```bash
cd src
python -m http.server 8000
# then open http://localhost:8000 in a browser
```

### Development notes

- Slides are written in Markdown and loaded via the Reveal Markdown plugin (`data-markdown="..."` attributes on sections).
- Theme variables are defined in `src/css/theme.css`; update colors, fonts and spacing there.
- Copy buttons, table styles, wrapping and image sizing are handled in the theme CSS and a small inline script in `index.html` that adds copy icons to code blocks.

### Deploying

The repository is configured to deploy automatically to GitHub Pages using the workflow in `.github/workflows/deploy.yml`. Push changes to the default branch and the workflow will publish to:

https://surquest.github.io/training-ai-assisted-survey/

### Contributing

PRs are welcome — consider adding or editing slides in `src/content/`, or adjusting the theme in `src/css/theme.css`. Keep assets in `src/assets/` and avoid committing large binary files.

### License

See the `LICENSE` file in this repository.

### Contact

For questions, open an issue or contact the repository maintainers.

