# Landing Page Deployment

## GitHub Pages Setup

### Option 1: Deploy from `gh-pages` branch (Recommended)

```bash
# Install gh-pages tool
npm install -g gh-pages

# Deploy landing folder to gh-pages branch
cd landing
npx gh-pages -d . -b gh-pages
```

### Option 2: Manual deployment

```bash
# Create gh-pages branch
git checkout --orphan gh-pages

# Remove all files
git rm -rf .

# Copy landing page
cp -r landing/* .

# Commit and push
git add .
git commit -m "Landing page"
git push origin gh-pages

# Switch back to main
git checkout main
```

### Enable GitHub Pages

1. Go to https://github.com/uppnrise/pdfpull/settings/pages
2. Source: **Deploy from a branch**
3. Branch: **gh-pages** / **(root)**
4. Click **Save**

Your site will be live at: **https://uppnrise.github.io/pdfpull**

---

## Waitlist Form Setup

### Option 1: Formspree (Recommended - Free)

1. Go to https://formspree.io
2. Create free account
3. Create new form
4. Copy form endpoint
5. Update index.html:

```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
    <input type="email" name="email" required>
    <button type="submit">Join Waitlist</button>
</form>
```

### Option 2: Tally.so (Free)

1. Go to https://tally.so
2. Create waitlist form
3. Get embed code
4. Replace form section in index.html

### Option 3: Google Sheets

1. Create Google Form with email field
2. Link to Google Sheet
3. Use form action URL

---

## Custom Domain (Optional)

1. Buy domain (e.g., pdfpull.com)
2. Add CNAME file to gh-pages branch:
   ```
   pdfpull.com
   ```
3. Update DNS:
   - A record: 185.199.108.153
   - A record: 185.199.109.153
   - A record: 185.199.110.153
   - A record: 185.199.111.153
