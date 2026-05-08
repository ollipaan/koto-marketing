# koto-marketing

Marketing site for [Koto](https://apps.apple.com/fi/app/id6762963217), a home maintenance log for iOS.

## Live

| Language | URL |
|---|---|
| Finnish | https://kodinhuoltokirja.netlify.app |
| English | https://kotohome.netlify.app |

Both deploy from this repo.

## Stack

Plain HTML and CSS, no build step. The only runtime dependencies are loaded via CDN:

- [Phosphor Icons](https://phosphoricons.com/) for the feature/audience icons
- PostHog JS for analytics (super property `app: 'koto-web'`, `site: 'fi' | 'en'`)

## Repo layout

```
.
├── index.html         Finnish landing page
├── privacy.html       Finnish privacy policy
├── tuki.html          Finnish support page (FAQ, disclaimer, contact)
├── robots.txt         Allows all crawlers, points to sitemap
├── sitemap.xml        FI URLs with hreflang alternates
├── favicon.png        Generated from the app's icon
├── apple-touch-icon.png
├── og-image.png       1200x630 social-share image
├── screens/           Phone mockups (WebP)
└── en/
    ├── index.html     English landing page
    ├── privacy.html   English privacy policy
    ├── support.html   English support page
    ├── robots.txt
    ├── sitemap.xml
    ├── og-image.png
    └── screens/       English phone mockups
```

## Deploy

Two Netlify sites pull from this repo:

- `kodinhuoltokirja.netlify.app` → base directory `/`
- `kotohome.netlify.app` → base directory `/en`

Pushing to `main` triggers a deploy on both.

## Develop locally

Open `index.html` directly in a browser, or for more accurate path resolution:

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## SEO

- `hreflang` tags in `<head>` and in each `sitemap.xml` cross-link the FI/EN versions.
- Each page sets a `canonical` URL pointing to itself.
- `<script type="application/ld+json">` blocks include both `MobileApplication` and `FAQPage` structured data, so Google can render the FAQ as rich snippets.
- Image filenames and alt texts include the target keywords (`kodin huoltokirja` / `home maintenance log`).
- Sitemaps submitted to Google Search Console for both domains.

## Analytics

PostHog tracks pageviews and clicks, identified separately from the app data:

- App: `app: 'koto'`
- Web FI: `app: 'koto-web', site: 'fi'`
- Web EN: `app: 'koto-web', site: 'en'`

Filter or group by `app` and `site` in PostHog to separate the surfaces. The web tracker uses `localStorage` persistence (no cookies, so no consent banner needed under typical GDPR interpretations).

## License

Site content (copy, screenshots, layout decisions) belongs to the Koto project. The HTML/CSS structure is unrestricted, feel free to take inspiration.
