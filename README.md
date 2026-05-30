# Photography Portfolio

A professional photography portfolio website — hosted on Cloudflare Pages, images served dynamically from Cloudinary.

---

## Live Site

> Add your Cloudflare Pages URL here once deployed  
> e.g. `https://your-portfolio.pages.dev`

---

## How It Works

```
Cloudinary (photo storage)
        ↓
Tag a photo with e.g. "gallery"
        ↓
Site fetches it automatically
        ↓
Visitor sees it — no code touched
```

The site is a single HTML file. There is no build process, no framework, no dependencies to install.

---

## Uploading Photos

1. Go to [cloudinary.com](https://cloudinary.com) → Media Library
2. Upload your photo
3. Add one or more tags (see tag reference below)
4. Refresh the live site — photo appears automatically

### Tag Reference

| Tag | Where it appears |
|---|---|
| `gallery` | Main portfolio — All tab |
| `landscapes` | Landscapes filter tab |
| `abstract` | Abstract filter tab |
| `gardens` | Gardens filter tab |
| `cityscapes` | Cityscapes filter tab |
| `series` | Horizontal series strip |
| `featured` | Reserved for hero image (future) |

> One photo can have multiple tags — e.g. tag it `gallery` AND `landscapes` to show it in both.

---

## Cloudinary Settings

- **Cloud name:** `dyb3d32yu`
- **Security → Restricted media types → `list`** must be **unticked** for the gallery to load

---

## Updating the Site

Edit `index.html` directly in GitHub:

1. Open the file in GitHub
2. Click the **pencil icon** (Edit)
3. Make your changes
4. Click **Commit changes**

Cloudflare Pages detects the commit and republishes automatically within ~30 seconds.

---

## Customising Themes

All colours are CSS variables at the top of `index.html`:

```css
:root {
  --bg: #080808;        /* background */
  --bg2: #101010;       /* section backgrounds */
  --text: #ede8df;      /* main text */
  --muted: #6b6560;     /* secondary text */
  --gold: #c9a96e;      /* accent colour */
  --gold-dim: #7a6240;  /* muted accent */
}
```

Change any of these values and commit — the whole site updates instantly.

---

## Site Structure

```
index.html          ← entire site (HTML + CSS + JS)
README.md           ← this file
```

No other files needed. Images live in Cloudinary, not this repo.

---

## Stack

| Layer | Tool | Cost |
|---|---|---|
| Hosting | Cloudflare Pages | Free |
| Code storage | GitHub | Free |
| Image storage & delivery | Cloudinary | Free (25GB) |
| Fonts | Google Fonts | Free |

---

## Sections (Built)

- [x] Hero
- [x] Gallery — dynamic, tag-filtered, lightbox
- [x] About
- [x] Series — dynamic horizontal scroll
- [x] Contact
- [ ] Shop — limited edition prints *(coming)*
- [ ] Tours — vintage camera walks *(coming)*

---

## Contact

Update the email address in `index.html`:

```html
<a href="mailto:hello@yourname.com" ...>
```

Replace `hello@yourname.com` with your real address.
