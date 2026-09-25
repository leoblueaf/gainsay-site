# Gainsay — public site

Three static pages served by GitHub Pages. They exist because the App Store
requires a publicly reachable **privacy policy URL** and **support URL** before
an app can be listed, and because Gainsay had no website.

No build step, no dependencies, no external requests. Every page is one file
with its CSS inline. Nothing here loads a font, a script or an image from
anywhere else, which is deliberate: a privacy policy that phones out to a
third party to render itself is not a good look.

---

## Support address

`leoblueaf@yahoo.com`, in the Contact panel of `privacy.html` and the panel at
the top of `support.html`. Set 1 Sep 2026 at David's instruction.

It is on a public page, so expect scraping and spam eventually. Swapping it for
a forwarding alias later is a two-line find and replace and needs no App Store
resubmission, since the URL does not change.

---

## Publishing

```powershell
cd C:\dev\quorum-site
git init
git add .
git commit -m "Public pages: privacy policy, support, landing"
git branch -M main
git remote add origin https://github.com/leoblueaf/gainsay-site.git
git push -u origin main
```

Create the `gainsay-site` repo on GitHub first, and make it **public** — GitHub
Pages will not serve a private repo on a free account.

Then in the repo: **Settings → Pages → Source: Deploy from a branch → Branch:
`main` / `(root)` → Save.** Give it a minute or two.

### Why a separate repo

The app repo has `docs/` in it with build notes, signing steps and internal
detail. Serving Pages from that repo would publish all of it. This one contains
only the three pages that are meant to be public.

---

## The URLs you paste into App Store Connect

```
Privacy Policy URL:  https://leoblueaf.github.io/gainsay-site/privacy.html
Support URL:         https://leoblueaf.github.io/gainsay-site/support.html
Marketing URL:       https://leoblueaf.github.io/gainsay-site/
```

Open all three in a browser before you submit. **A privacy policy URL that
404s is a rejection**, and it is the single most common one.

---

## Keeping it true

The privacy policy describes the app as it is today: no analytics, no crash
reporting, no advertising identifiers, no third-party SDK that collects
anything. That claim was checked against `pubspec.yaml` on 1 Sep 2026 and it
held.

**If a dependency is ever added that changes it, this page changes first.** A
privacy policy that has drifted from the app is worse than not having written
one, and Apple treats the mismatch as a guideline 5.1.1 problem rather than a
typo.
