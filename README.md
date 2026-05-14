# allenberry-assets

Image and asset hosting for Allenberry emails and website.

Served via GitHub Pages at:

**`https://allenberry-jesse.github.io/allenberry-assets/`**

---

## How URLs work

Any file in this repo is available at the base URL above plus its path.

For example, `emails/2026-05-12-test/hero-mill.jpg` is reachable at:

```
**`https://assets.allenberry.com/`**
```

That's the URL you paste into the `<img src="...">` tag in your email.

---

## Folder structure

```
allenberry-assets/
├── emails/                       # One folder per email send
│   └── YYYY-MM-DD/               # Date
│       ├── hero.jpg
│       └── ...
├── shared/                       # Used across multiple emails / pages
│   ├── logos/
│   └── icons/
└── website/                      # Website-only assets
    ├── about/
    ├── rooms/
    └── dining/
```

**`emails/`** — one subfolder per weekly send. Folder name is the send date in `YYYY-MM-DD` format. Examples:

- `2026-05-12/`
- `2026-05-19/`
- `2026-05-26/`

**`shared/`** — anything used in more than one email or page (logos, icons, signature graphics, social icons). Don't duplicate these into each weekly folder.

**`website/`** — assets used only on Allenberry.com, separated so email and website concerns don't get tangled.

---

## Naming conventions

- **All lowercase**
- **Hyphens instead of spaces or underscores**: `fairfield-hall.jpg`, not `Fairfield_Hall.jpg`
- **Descriptive, not numeric**: `mansion-house-winter.jpg`, not `IMG_2847.jpg`
- **Consistent role names** when applicable: `hero.jpg`, `thumbnail.jpg`, `signature.png`

---

## Image rules for email

| Rule              | Target                                                         |
| ----------------- | -------------------------------------------------------------- |
| File size         | Under 200 KB for photos, under 100 KB for logos                |
| Max width         | 1200 px (most emails render at 600 px, 1200 px covers retina)  |
| Format            | JPEG for photos. PNG only when transparency is needed.         |
| Color profile     | sRGB (most photo tools default to this)                        |

Large or non-optimized images cause emails to load slowly, get clipped by Gmail (which truncates anything over ~102 KB of HTML), or trigger spam filters.

**Optimize every image before committing.** Drag through [TinyPNG](https://tinypng.com) or [Squoosh](https://squoosh.app) — both are free and cut file size 50–70% with no visible quality loss.

---

## Weekly workflow

For each new email:

1. **Gather originals** into a non-Git folder (e.g. `~/Allenberry/email-originals/2026-05-12/`). Keep these as your archive.
2. **Resize** any image wider than 1200 px.
3. **Optimize** through TinyPNG or Squoosh until each file is under the size targets above.
4. **Create the email's folder** in `emails/` using the `YYYY-MM-DD-slug` pattern.
5. **Drop optimized images** into that folder with clear filenames.
6. **Commit and push** in GitHub Desktop. Use a clear commit message like `Add assets for 2026-05-12 Crockett origins email`.
7. **Wait 1–2 minutes** for GitHub Pages to rebuild, then test one image URL in a browser before pasting into the email builder.

---

## Things to avoid

- **Don't rename or move files once an email has been sent.** The URL is baked into every copy of that email already in inboxes. Renaming breaks them.
- **Don't commit RAW files, PSDs, or full-resolution originals.** Keep those in your archive folder outside the repo. Git history bloats fast and is hard to clean up.
- **Don't put anything private in here.** This repo is public. Treat every file as if it could be linked publicly (because it can be).
- **Don't reuse a folder name across different emails.** Date-prefix keeps everything unique and chronologically sorted.

---

## If something breaks

- **Image not loading after push?** GitHub Pages can take 1–2 minutes to rebuild. Hard-refresh the browser (Cmd+Shift+R).
- **404 on a URL you're sure exists?** Check the path is exactly right — URLs are case-sensitive. `Hero.jpg` ≠ `hero.jpg`.
- **GitHub Pages disabled?** Check Settings → Pages. Source should be `main` branch, `/ (root)`.
