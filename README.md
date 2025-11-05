# Portfolio - Render deployment notes

Summary

- This repository contains a small static portfolio site composed of HTML files: `Homepage.html`, `AboutPage.html`, `Education.html`, `Skills.html`, `Contacts.html`.
- I added an `index.html` that redirects to `Homepage.html` so static hosts (like Render) will serve the homepage by default.

Quick analysis / readiness

- No build step or package manager found — this is a static site (HTML/CSS/JS).
- External assets (fonts and Font Awesome) are loaded from CDNs.
- Filenames are case-sensitive on Linux-based hosts (Render uses Linux). Links in the HTML match the file names (e.g., `Homepage.html`, `AboutPage.html`) so they should work as-is.
- There is an image file referenced in `AboutPage.html` called `WhatsApp Image 2025-11-01 at 6.42.45 PM.jpeg` which exists in the repo. Filenames with spaces are valid but may be inconvenient; consider renaming to a simpler name and updating the HTML.

Recommended minimal changes (done)

- Add `index.html` at repo root (done) that redirects to `Homepage.html`.

Optional (recommended) improvements

- Rename image files to remove spaces and update `AboutPage.html` accordingly (e.g. `profile.jpg`). This avoids URL-encoding issues and makes links friendlier.
- Add a `404.html` page to handle not-found routes.

How to deploy on Render (step-by-step)

1. Push your code to GitHub (branch `main` or whichever branch you want to use).

2. Sign in to Render (https://render.com) and click "New +" → "Static Site".

3. Connect your GitHub account and choose the repository `PortFolio-`.

4. Settings on the Create page:

   - Name: (choose a name, e.g., `portfolio-manikiran`)
   - Branch: `main` (or the branch you pushed)
   - Build Command: leave blank (no build step required)
   - Publish Directory: `/` (or leave blank) — must point to the folder that contains `index.html` (root of repo in this case)

5. Click "Create Static Site". Render will create a deploy and serve the `index.html` at the root URL.

6. After deploy finishes, open the assigned Render URL. The `index.html` will redirect to `Homepage.html` immediately.

7. (Optional) Configure a custom domain:
   - In the Render dashboard for your site, go to the "Settings" → "Custom Domains" and add your domain.
   - Follow DNS setup instructions, then enable automatic TLS.

Troubleshooting & checks before/after deploy

- Check filenames and internal links for exact case (e.g., `Homepage.html` vs `homepage.html`) — Linux is case-sensitive.
- If images do not load, confirm that the referenced file names match exactly and that the files were committed.
- If you prefer the site to serve the homepage directly without a redirect, rename `Homepage.html` → `index.html` (and update links that reference `index.html` where appropriate). Note: renaming the file will require updating `AboutPage.html`, `Education.html`, `Skills.html`, etc. where they link to `index.html`.

Local testing

- You can preview locally by opening `index.html` in a browser (double-click) or by running a simple local server, for example (Python):

```bash
# from repository root
python -m http.server 8000
# then open http://localhost:8000
```

If you'd like, I can:

- Rename the profile image to remove spaces and update `AboutPage.html`.
- Replace the redirect `index.html` by renaming `Homepage.html` to `index.html` and update cross-links.
- Add a `404.html` file.

---

Files added:

- `index.html` — small redirect page to `Homepage.html`
- `README.md` — this file

If you want me to make one of the optional improvements now (rename image, rename homepage to `index.html`, add 404), tell me which and I'll apply changes and update the repo.
