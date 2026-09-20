# Salio Web

Public pages for Salio — support, privacy policy, and marketing — published as a static site via GitHub Pages. No backend, no build step, no framework.

## Structure

```
├── index.html          # marketing / landing page
├── support.html        # support + FAQ (App Store Connect "Support URL")
├── privacy.html         # privacy policy (App Store Connect "Privacy Policy URL")
├── assets/
│   ├── css/styles.css  # shared design system (black-and-gold, EB Garamond)
│   └── img/            # icon, favicon, og-image
└── README.md
```

All internal links are relative, so the site works unchanged under both the default `github.io` domain and a future custom domain.

## Publishing

1. Push this repo to GitHub with `main` as the default branch.
2. Repo → **Settings → Pages** → Source: **Deploy from a branch**, Branch: **main / (root)**.
3. Save, wait a minute or two, then visit `https://<username>.github.io/<repo>/`.
4. Enable **Enforce HTTPS** once the certificate is issued.

To use a custom subdomain (e.g. `salio.santrico-apps.com`) instead, add a `CNAME` file at the repo root containing that subdomain, and point a CNAME DNS record at the registrar to `<username>.github.io`.

## Before submitting to App Store Connect

- [ ] Confirm the support email — pages currently use `support@santrico-apps.com` as a placeholder.
- [ ] `assets/img/` favicon, apple-touch-icon, and the og-image mark are generated from the real app icon. Replace `og-image.png` with an official marketing asset if design wants something more custom than the auto-generated wordmark composition.
- [ ] Replace the illustrative phone mockups on the marketing page (`index.html` → `#screenshots`) with the real 5 App Store screenshot PNGs.
- [ ] Add an App Store download badge/link back into `index.html` once Salio has a live `apps.apple.com` listing (removed for now since there's nothing to link to yet).
- [ ] Confirm whether captured dismiss-mission photos are discarded immediately after on-device verification or retained locally for any period — `privacy.html` currently states they're discarded immediately (see the `TODO(privacy)` comment in that file). This must match the shipping build exactly, since it's cross-checked against Apple's Privacy Nutrition Label and Google Play's Data Safety form.
- [ ] Set **App Information → Privacy Policy URL** to the published `privacy.html` URL.
- [ ] Set **App Information → Marketing URL** (optional) to the published `index.html` URL.
- [ ] Set **General App Information → Support URL** to the published `support.html` URL.
- [ ] Declare "Data Not Collected" in the App Privacy (Privacy Nutrition Label) section if it remains accurate.

Keep the live policy text and the App Store/Google Play declarations in sync with whatever the app actually collects — a mismatch here is a common cause of rejection.
