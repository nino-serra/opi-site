# OPI – static site

Ready-to-deploy static site for GitHub Pages.

## Quick start (Web UI)
1. Create a new **public** repo on GitHub, e.g. `opi-site`.
2. Upload the files from this folder: `index.html`, `404.html`, `.nojekyll`.
3. Go to **Settings → Pages**.
   - Build and deployment → **Source: Deploy from a branch**
   - **Branch:** `main` (or `master`) and **Folder:** `/ (root)` → Save
4. Your site will be available at `https://<your-username>.github.io/opi-site/`.

## Quick start (CLI)
```bash
git init
git add .
git commit -m "Initial commit: OPI static site"
git branch -M main
git remote add origin https://github.com/<your-username>/opi-site.git
git push -u origin main
```
Then configure **Settings → Pages** as above.

## Notes
- External images currently point to Notion's CDN. For reliability, consider downloading them into a local `/assets` folder and updating the `src` attributes.
- Tailwind is loaded from the CDN for convenience.
- `404.html` lets client-side routes fall back gracefully.
- `.nojekyll` disables Jekyll processing.
- Last prepared: 2025-08-17T11:27:25


## Mirror images locally (/assets)

This package rewrites Notion CDN image URLs to local **/assets/** paths and adds a fallback to the original URLs if a local file is missing.

### Fetch assets (Linux/macOS)
```bash
chmod +x fetch_assets.sh
./fetch_assets.sh
```

### Fetch assets (Windows PowerShell)
```powershell
./fetch_assets.ps1
```

The mapping is in `assets/ASSETS_MAPPING.json`.

> Note: The HTML includes `onerror` fallbacks, so the site still displays images from Notion if `/assets` files are missing. For 100% reliability, run the fetch script and commit the downloaded files.
