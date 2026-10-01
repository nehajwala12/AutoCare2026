# Ares commercial diligence (password-protected site)

The site is `index.html`, the customer deliverable of 30 September 2026 (with the Monro term-sheet section). `middleware.js` asks for a password on every request before anything is served.

- Password: `AutoCare2026`
- Username: anything (the browser asks for both; leave the name blank or type any word)

## Deploy

Either way, Vercel detects no framework. Leave Build Command and Output Directory empty (Framework Preset: Other).

**Vercel CLI** (from this folder):

    npx vercel        # first time: link or create the project
    npx vercel --prod

**GitHub**: push this folder to a private repository, then in Vercel choose Add New, then Project, then import that repository and Deploy.

## Change the password

In the Vercel project, go to Settings, then Environment Variables. Add `SITE_PASSWORD` with the new value and redeploy. Without it, the default in `middleware.js` applies.

## Notes

- Search engines are told not to index the site (`X-Robots-Tag` header and `robots.txt`).
- The page loads its fonts from Google Fonts. Everything else is inside `index.html`.
