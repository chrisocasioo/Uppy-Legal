# Wake Uppy Web

Public pages for Wake Uppy — support, privacy policy, and marketing — published as a static site via GitHub Pages. No backend, no build step, no framework.

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

To use a custom subdomain (e.g. `uppy.santrico-apps.com`) instead, add a `CNAME` file at the repo root containing that subdomain, and point a CNAME DNS record at the registrar to `<username>.github.io`.

## Before submitting to App Store Connect

- [ ] Confirm the support email — pages currently use `support@santrico-apps.com` as a placeholder.
- [ ] Replace the placeholder icon/favicon/og-image in `assets/img/` with the real app icon and App Store screenshot assets.
- [ ] Replace the illustrative phone mockups on the marketing page (`index.html` → `#screenshots`) with the real 5 App Store screenshot PNGs.
- [ ] Swap the "Coming soon" App Store badge links in `index.html` for the real `apps.apple.com` listing URL once Wake Uppy is live.
- [ ] Confirm whether captured dismiss-mission photos are discarded immediately after on-device verification or retained locally for any period — `privacy.html` currently states they're discarded immediately (see the `TODO(privacy)` comment in that file). This must match the shipping build exactly, since it's cross-checked against Apple's Privacy Nutrition Label and Google Play's Data Safety form.
- [ ] Set **App Information → Privacy Policy URL** to the published `privacy.html` URL.
- [ ] Set **App Information → Marketing URL** (optional) to the published `index.html` URL.
- [ ] Set **General App Information → Support URL** to the published `support.html` URL.
- [ ] Declare "Data Not Collected" in the App Privacy (Privacy Nutrition Label) section if it remains accurate.

Keep the live policy text and the App Store/Google Play declarations in sync with whatever the app actually collects — a mismatch here is a common cause of rejection.
