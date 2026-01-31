# Molt Observatory - GitHub Pages Site

This directory contains the static website for Molt Observatory, designed to be hosted on GitHub Pages.

## Deployment

### Option 1: Deploy to Existing Repo

1. Copy all contents to your `moltbook-safety.github.io` repository:

```bash
# Clone your GitHub Pages repo
git clone https://github.com/Ygali04/moltbook-safety.github.io.git
cd moltbook-safety.github.io

# Copy docs-site contents
cp -r ../moltbook_safety/docs-site/* .

# Commit and push
git add .
git commit -m "Deploy Molt Observatory site"
git push origin main
```

2. Go to **Settings → Pages** in your GitHub repo
3. Under "Source", select the branch (usually `main`) and folder (`/` root)
4. Click Save

Your site will be live at: `https://ygali04.github.io/moltbook-safety.github.io/`

### Option 2: Deploy via GitHub Actions

Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup Pages
        uses: actions/configure-pages@v4
        
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'
          
      - name: Deploy to GitHub Pages
        uses: actions/deploy-pages@v4
```

## File Structure

```
docs-site/
├── index.html          # Homepage
├── css/
│   ├── style.css       # Main styles
│   └── docs.css        # Documentation styles
├── js/
│   └── main.js         # Interactive features
├── images/
│   └── favicon.svg     # Site favicon
├── pages/
│   └── docs.html       # Documentation page
└── README.md           # This file
```

## Customization

### Colors

Edit CSS variables in `css/style.css`:

```css
:root {
    --accent-primary: #ff6b6b;    /* Coral red */
    --accent-secondary: #4ecdc4;  /* Teal */
    --bg-primary: #0a0a0f;        /* Dark background */
}
```

### Content

- **Homepage**: Edit `index.html`
- **Documentation**: Edit `pages/docs.html`
- **Add pages**: Create new HTML files in `pages/`

## Local Development

Open `index.html` directly in your browser, or use a local server:

```bash
# Python 3
python -m http.server 8000

# Node.js
npx serve .
```

Then visit `http://localhost:8000`

## Features

- 🌙 Dark theme with grain texture
- 📱 Responsive design
- ⚡ No build step required
- 📊 Plotly charts (CDN loaded)
- 🎨 Custom fonts (Outfit + JetBrains Mono)
- 🧭 Smooth scroll navigation
- 📋 Copy code buttons
- 🎯 Intersection observer animations

