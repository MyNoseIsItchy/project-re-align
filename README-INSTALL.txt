PROJECT RE:ALIGN — INSTALLABLE PWA PACKAGE

WHAT THIS PACKAGE DOES
- The app interface is hosted as static files over HTTPS so Android/Chrome can install it.
- The service worker caches the app shell on the device for offline use.
- Your app records remain in the browser's localStorage on that device. They are not sent to GitHub Pages.
- Keep using the app's Export Complete JSON Backup feature. Browser storage can be cleared by the user, Android, or browser cleanup tools.

IMPORTANT: A PWA cannot be installed reliably by opening index.html directly from Downloads, file://, or most code-editor previews. PWA installation requires HTTPS (or localhost during development). The simplest setup is free static HTTPS hosting. This does NOT mean your personal records are stored on the hosting provider.

EASIEST FREE INSTALL METHOD — GITHUB PAGES
1. On a computer, sign in to https://github.com/ (create a free account if needed).
2. Create a new repository named: project-re-align
3. Set it to Public, then create the repository.
4. Upload the CONTENTS of this folder (not the enclosing folder):
   - index.html
   - manifest.json
   - sw.js
   - icons/ (all three PNG files)
5. Commit the uploaded files to the main branch.
6. In the repository, open Settings > Pages.
7. Under Build and deployment, choose Deploy from a branch.
8. Choose branch main and folder /(root), then Save.
9. Wait for GitHub Pages to publish. The URL will look like:
   https://YOUR-USERNAME.github.io/project-re-align/
10. Open that URL in Chrome on your Android phone. Load it once while online and wait a few seconds for the service worker to cache the app shell.
11. In Chrome, tap ⋮ > Install app (or Add to Home screen, depending on Chrome version), then confirm.
12. Launch RE:ALIGN from the new home-screen icon. Test by turning on Airplane mode and reopening it.

UPDATING THE APP
- When you change the app files, upload/commit the new files to the same GitHub repository.
- Update sw.js CACHE_NAME (for example v2 -> v3) when you need to force a fresh app-shell cache.
- Open the app online after publishing and refresh/reopen it. If an old version remains, close the app fully and reopen while online.

LOCAL DATA AND BACKUPS
- The PWA's origin is the hosted URL, but personal records are stored locally in that origin's browser storage.
- Do not change the domain/repository URL after you begin using it unless you first export a JSON backup.
- Chrome and the editor preview have separate storage. Data entered in one will not automatically appear in the other.
- Export a JSON backup regularly and keep a copy somewhere safe. Use the app's Import Backup feature to restore it.
- Clearing Chrome site data can delete local app records. The service worker cache is for app files, not a backup of your personal data.

OPTIONAL LOCAL DEVELOPMENT
- On a computer with Python installed, open a terminal in this folder and run:
    python -m http.server 8000
- Visit http://localhost:8000 on that same computer. This is useful for testing, but Android phone Chrome cannot use the computer's localhost address as its own localhost. For phone installation, use HTTPS hosting or a properly configured HTTPS server.

PRIVACY NOTE
This package does not include analytics, login, cloud sync, or a remote database. Static hosting serves the app files only. The browser's localStorage holds the app's user-entered data. If you want to sync across devices later, that would require a separate backend or manual backup/restore.
