# OmniDoc Studio — Web, PWA & App Store Publishing Guide

This release bundle is structured as a complete, zero-build Progressive Web App (PWA) ready for HTTPS deployment and store packaging.

## Folder Contents
- `index.html` — Complete 14-studio client-side ML document application.
- `manifest.json` — W3C Web App Manifest with icons, maskable icon, and OS app shortcuts.
- `sw.js` — Offline-first Service Worker (precaches app shell and caches CDN libraries via stale-while-revalidate).
- `icons/` — Store-ready PNG icons (`192×192`, `512×512`, maskable `512×512`, Apple touch icon, favicon).
- `vercel.json` & `netlify.toml` — Production security and camera/microphone permission headers.

## Step 1: Test Locally (Recommended for Live Camera & Service Worker)
Run a local HTTP server from this folder (required because browsers restrict `ServiceWorker` and `getUserMedia` on `file://`):
```powershell
python -m http.server 8080
```
Open `http://localhost:8080` in Chrome or Edge.

## Step 2: Deploy Free over HTTPS (Vercel, Netlify, or GitHub Pages)
1. **Vercel**: Drag & drop this folder (or connect GitHub repo) on `vercel.com` -> Deploy.
2. **Netlify**: Drag & drop this folder onto `app.netlify.com/drop` -> Instant HTTPS URL.
3. **GitHub Pages**: Push contents to a repository and enable Pages on `main` branch.

## Step 3: Publish to Google Play Store (Android TWA) & Microsoft Store
1. Copy your deployed HTTPS URL (e.g., `https://omnidoc-studio.vercel.app`).
2. Visit **[PWABuilder.com](https://www.pwabuilder.com)** and enter your HTTPS URL.
3. Verify the **Manifest** and **Service Worker** checks pass.
4. Click **Package for Stores**:
   - **Android (Google Play Store)**: Download the signed Trusted Web Activity (`.aab` + `assetlinks.json`). Upload `assetlinks.json` to `/.well-known/assetlinks.json` on your site so the browser URL bar disappears completely, then upload the `.aab` to Google Play Console.
   - **Windows (Microsoft Store)**: Download the MSIX package.
   - **iOS (App Store)**: Download the iOS wrapper project or wrap with Capacitor (`npx cap add ios`).
