# pdfpull Landing Page

Multi-language landing page and playground for pdfpull API.

## Features

- 🧠 **Auto Language Detection** - API auto-detects EN, DE, TR
- 🌍 **Multi-language UI** - English, German, Turkish
- 🧾 **Invoice Parser showcase** - Extract vendor, amounts, dates
- 📋 **Resume Parser showcase** - Extract contact, skills, experience
- 🎮 **Interactive Playground** - Try all endpoints without signup
- 📱 **Responsive design** - Works on all devices

## Files

```
landing/
├── index.html        # Main landing page (multi-language)
├── playground.html   # Interactive API playground (multi-language)
├── thanks.html       # Thank you page after waitlist signup
└── README.md         # This file
```

## Multi-Language Support

Both pages support 3 languages:
- 🇺🇸 English (en)
- 🇩🇪 German (de)
- 🇹🇷 Turkish (tr)

Language is selected via buttons in the header and saved to `localStorage`.

### Adding a New Language

1. Add translation object to `translations` in the `<script>` section:

```javascript
const translations = {
    en: { ... },
    de: { ... },
    tr: { ... },
    // Add new language:
    fr: {
        "nav.home": "Accueil",
        "hero.title": "Analyse PDF Intelligente",
        // ... all keys
    }
};
```

2. Add language button in header:

```html
<button onclick="setLanguage('fr')" class="lang-btn px-2 py-1 rounded text-sm font-medium" data-lang="fr">FR</button>
```

---

## GitHub Pages Deployment

### Option 1: Deploy from `gh-pages` branch (Recommended)

```bash
# Install gh-pages tool
npm install -g gh-pages

# Deploy landing folder to gh-pages branch
cd landing
npx gh-pages -d . -b gh-pages
```

### Option 2: Separate Repository

1. Create new repo: `pdfpull-landing`
2. Copy landing files to new repo
3. Enable GitHub Pages from main branch

### Enable GitHub Pages

1. Go to repository Settings → Pages
2. Source: **Deploy from a branch**
3. Branch: **gh-pages** (or **main**) / **(root)**
4. Click **Save**

**Live URLs:**
- Landing: https://uppnrise.github.io/pdfpull-landing
- Playground: https://uppnrise.github.io/pdfpull-landing/playground.html

---

## Waitlist Form

The waitlist form uses [Formspree](https://formspree.io) for email collection.

### Setup

1. Go to https://formspree.io
2. Create free account
3. Create new form
4. Copy form endpoint
5. Update `action` in index.html:

```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
```

---

## API Configuration

The playground connects to the production API:

```javascript
const API_URL = 'https://pdfpull-895295000838.europe-west1.run.app';
const DEMO_KEY = 'sk_demo_123456789';
```

To use a different API:

1. Update `API_URL` in playground.html
2. Update `DEMO_KEY` if needed

---

## Customization

### Colors

The gradient colors are defined in CSS:

```css
.gradient-bg {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}
```

### Tailwind CSS

Both pages use Tailwind CSS via CDN:

```html
<script src="https://cdn.tailwindcss.com"></script>
```

For production, consider:
- Using Tailwind CLI to purge unused styles
- Self-hosting the CSS file

---

## Development

### Local Testing

```bash
# Simple HTTP server
cd landing
python -m http.server 8080

# Open in browser
open http://localhost:8080
```

### Making Changes

1. Edit HTML files directly
2. Translations are in the `<script>` section at bottom
3. Test all 3 languages before deploying

---

## Custom Domain (Optional)

1. Buy domain (e.g., pdfpull.com)
2. Add CNAME file to landing directory:
   ```
   pdfpull.com
   ```
3. Update DNS:
   - A record: 185.199.108.153
   - A record: 185.199.109.153
   - A record: 185.199.110.153
   - A record: 185.199.111.153
4. Enable HTTPS in GitHub Pages settings
