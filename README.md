# koto-marketing

Marketing site for [Koto](https://apps.apple.com/fi/app/id6762963217) — a maintenance log for your home (iOS app).

## Live

| Language | URL |
|---|---|
| Finnish | https://kodinhuoltokirja.netlify.app |
| English | https://kotohome.netlify.app |

Both deploy from this repo.

## Stack

Plain HTML and CSS. No build step, no JavaScript framework, no dependencies beyond the [Phosphor Icons](https://phosphoricons.com/) CSS loaded via CDN.

## Repo layout

```
.
├── index.html         Finnish landing page
├── privacy.html       Finnish privacy policy
├── robots.txt         Allows all crawlers, points to sitemap
├── sitemap.xml        FI URLs with hreflang alternates
├── favicon.png        From the app's icon
├── apple-touch-icon.png
├── screens/           Phone mockups for the screens section
└── en/
    ├── index.html     English landing page
    ├── privacy.html   English privacy policy
    ├── robots.txt
    └── sitemap.xml    EN URLs with hreflang alternates
```

## Deploy

Two Netlify sites pull from this repo:

- `kodinhuoltokirja.netlify.app` — base directory `/`
- `kotohome.netlify.app` — base directory `/en`

Pushing to `main` triggers a deploy on both.

## Develop locally

Open `index.html` in a browser. That's it.

For more accurate path resolution (e.g., `/favicon.png`):

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## SEO notes

The two language versions reference each other via `hreflang` tags in `<head>` and in their respective `sitemap.xml`. Each page sets a `canonical` URL pointing to itself. This is the standard Google-recommended setup for cross-domain language alternates.

## License

The site content (copy, layout) belongs to the Koto project. The HTML/CSS structure is unrestricted — feel free to take inspiration.
