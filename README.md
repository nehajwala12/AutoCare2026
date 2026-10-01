# Password-protected site (single file)

The whole site is `index.html`. The password check is built into the page itself, so there is no middleware, no `package.json` and nothing to configure on the host.

- Opening the page shows a CreditSwan password screen. The correct password unlocks the document in the browser.
- The document inside `index.html` is encrypted with the password (AES-256). The password is not written anywhere in the file, and viewing the page source shows only scrambled text.
- Once unlocked, the page stays open for that browser tab, including on refresh. Closing the tab locks it again.
- The file also works when opened directly from a computer or sent as an attachment.

## Deploy

Vercel detects no framework. Leave Build Command and Output Directory empty (Framework Preset: Other).

**Vercel CLI** (from this folder):

    npx vercel --prod

**GitHub**: replace the repository contents with this folder and push. Delete `middleware.js`, `package.json` and `package-lock.json` from the repository, otherwise the old browser password prompt stays in front of the new one.

If `SITE_PASSWORD` is set in the Vercel project's environment variables, it is no longer used and can be removed.

## Change the password

The password is part of the encryption, so it cannot be edited by hand. The page has to be rebuilt from the original document with the new password.

## Notes

- Search engines are told not to index the site (`X-Robots-Tag` header, `robots.txt` and a meta tag on the password screen).
- The password screen names only CreditSwan. The client and subject appear only after unlocking.
- Needs a current browser: Chrome or Edge, Safari 16.4 or later, Firefox 113 or later.
