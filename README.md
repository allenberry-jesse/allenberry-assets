# allenberry-assets

Image and asset hosting for Allenberry emails and website.

Served via GitHub Pages at the custom domain:

**`https://assets.allenberry.com/`**

> This is the URL to use everywhere. (The repo is also reachable at
> `https://allenberry-jesse.github.io/allenberry-assets/`, but ignore that
> one — the custom domain is simpler and drops the repo-name prefix.)

---

## How URLs work

Take any file's path in this repo and append it to the base URL above.

**Example.** The file:

```
emails/2026-06-19-flash/flash-sale-hero.jpg
```

is reachable at:

```
https://assets.allenberry.com/emails/2026-06-19-flash/flash-sale-hero.jpg
```

That full URL — base domain **plus the file's path** — is what you paste into
the `<img src="...">` tag in your email. The path after `.com/` must match the
file's location in the repo exactly, including the folder name and every
character of the filename.

---

## Folder structure

```
allenberry-assets/
├── emails/                       # One folder per email send
│   └── YYYY-MM-DD-slug/          # Send date + short slug, e.g. 2026-06-19-flash
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

**`emails/`** — one subfolder per send. Folder name is the send date in
`YYYY-MM-DD` format, followed by a short lowercase slug describing the email.
Examples:

- `2026-06-15-fathers-day/`
- `2026-06-19-flash/`
- `2026-06-24-summer-pass/`

Keep the slug short and all-lowercase-with-hyphens. The date prefix keeps every
folder unique and chronologically sorted.

**`shared/`** — anything used in more than one email or page (logos, icons,
signature graphics, social icons). Don't duplicate these into each weekly folder.

**`website/`** — assets used only on Allenberry.com, separated so email and
website concerns don't get tangled.

---

## Naming conventions

- **All lowercase**
- **Hyphens instead of spaces or underscores**: `fairfield-hall.jpg`, not `Fairfield_Hall.jpg`
- **Descriptive, not numeric**: `mansion-house-winter.jpg`, not `IMG_2847.jpg`
- **Consistent role names** when applicable: `hero.jpg`, `thumbnail.jpg`, `signature.png`

**Always rename camera/phone files before committing.** Names like
`IMG_9924__1_.jpg` are the #1 cause of broken images: the uppercase letters,
double underscores, and stray trailing underscore are almost impossible to type
back into a URL correctly, and any email tool that lowercases the name will break
the link. Rename to something like `flash-sale-hero.jpg` *before* you commit.

URLs are case-sensitive, so lowercase-everything removes the single most common
cause of a broken image. `Hero.jpg` and `hero.jpg` are two different files.

---

## Image rules for email

| Rule              | Target                                                         |
| ----------------- | -------------------------------------------------------------- |
| File size         | Under 200 KB for photos, under 100 KB for logos                |
| Max width         | 1200 px (most emails render at 600 px, 1200 px covers retina)  |
| Format            | JPEG for photos. PNG only when transparency is needed.         |
| Color profile     | sRGB (most photo tools default to this)                        |

Large or non-optimized images cause emails to load slowly, get clipped by Gmail
(which truncates anything over ~102 KB of HTML), or trigger spam filters.

**Optimize every image before committing.** Drag through [TinyPNG](https://tinypng.com)
or [Squoosh](https://squoosh.app) — both are free and cut file size 50–70% with
no visible quality loss.

---

## Weekly workflow

For each new email:

1. **Gather originals** into a non-Git folder (e.g. `~/Allenberry/email-originals/2026-05-12/`). Keep these as your archive.
2. **Resize** any image wider than 1200 px.
3. **Optimize** through TinyPNG or Squoosh until each file is under the size targets above.
4. **Create the email's folder** in `emails/` named `YYYY-MM-DD-slug` (send date + short slug).
5. **Drop optimized images** into that folder with clear, all-lowercase filenames. Rename any `IMG_####` camera files first.
6. **Commit AND push** in GitHub Desktop. A commit alone does not publish anything —
   you must push. Use a clear message like `Add assets for 2026-05-12 Crockett origins email`.
7. **Wait 1–2 minutes** for GitHub Pages to rebuild.
8. **Test the URL before using it.** Paste the full image URL
   (`https://assets.allenberry.com/emails/2026-05-12/hero.jpg`) into a browser and
   confirm the image loads. Only then paste it into the email builder.

---

## Copy-paste URL template

```
https://assets.allenberry.com/emails/YYYY-MM-DD-slug/FILENAME.jpg
```

Replace `YYYY-MM-DD-slug` with your folder name and `FILENAME.jpg` with the actual
file name. Nothing else changes.

---

## Things to avoid

- **Don't rename or move files once an email has been sent.** The URL is baked into every copy of that email already in inboxes. Renaming breaks them.
- **Don't commit RAW files, PSDs, or full-resolution originals.** Keep those in your archive folder outside the repo. Git history bloats fast and is hard to clean up.
- **Don't put anything private in here.** This repo is public. Treat every file as if it could be linked publicly (because it can be).
- **Don't reuse a folder name across different emails.** The date prefix keeps everything unique and chronologically sorted.
- **Don't commit raw camera filenames** (`IMG_9924__1_.jpg`). Rename to lowercase-hyphenated names first — they're the most common source of broken image links.

---

## If something breaks

- **Image not loading after push?** GitHub Pages can take 1–2 minutes to rebuild. Hard-refresh the browser (Cmd+Shift+R).
- **404 on a URL you're sure exists?** Check three things, in order:
  1. **Did the push actually go through?** Open the repo on github.com and confirm your file appears in the right `emails/YYYY-MM-DD/` folder. A commit that was never pushed = nothing to serve.
  2. **Does the URL path match the file exactly?** Every folder and file name, character for character.
  3. **Case.** URLs are case-sensitive: `Hero.jpg` ≠ `hero.jpg`.
- **GitHub Pages disabled?** Check Settings → Pages. Source should be `main` branch, `/ (root)`.
