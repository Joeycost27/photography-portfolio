# Photography Portfolio Website

A professional photography portfolio built from scratch — no WordPress, no monthly fees, no platform lock-in. Just a single HTML file, hosted for free, with images that update automatically when you upload them.

---

## What This Is

This is a complete photography website consisting of:

- A **single HTML file** (`index.html`) that contains all the code for the site — the design, layout, animations, and gallery logic
- **No backend, no database, no framework** — just clean HTML, CSS and JavaScript
- Images are **not stored in this repo** — they live in Cloudinary (a separate image hosting service) and are pulled into the site automatically

---

## The Three Services and What Each One Does

```
┌─────────────────────────────────────────────────────┐
│                                                     │
│   GITHUB                                            │
│   Stores the website code (index.html)              │
│   Free · Public repository                          │
│                                                     │
└──────────────────────┬──────────────────────────────┘
                       │ Cloudflare watches GitHub.
                       │ Every time index.html changes,
                       │ it republishes the site automatically.
                       ▼
┌─────────────────────────────────────────────────────┐
│                                                     │
│   CLOUDFLARE PAGES                                  │
│   Hosts and serves the website to visitors          │
│   Free · Unlimited bandwidth · Global fast delivery │
│                                                     │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│                                                     │
│   CLOUDINARY                                        │
│   Stores and delivers the photographs               │
│   Free · 25GB storage · Auto image optimisation     │
│   Cloud name: dyb3d32yu                             │
│                                                     │
└──────────────────────┬──────────────────────────────┘
                       │ When a visitor opens the site,
                       │ the gallery asks Cloudinary:
                       │ "give me all photos tagged gallery"
                       │ Cloudinary returns the list.
                       │ The gallery builds itself.
                       ▼
                  Visitor's browser
```

These three services are **completely free** and work together. You never need to touch the code to add new photos.

---

## How to Add a Photo to the Website

1. Go to [cloudinary.com](https://cloudinary.com) and log in
2. Click **Media Library**
3. Upload your photo
4. Add a tag — e.g. `gallery`, `landscapes`, `abstract` (see full tag list below)
5. Open your live site and refresh — the photo appears automatically

That's it. No code. No FTP. No rebuilding anything.

---

## Tag Reference

Tags are how you control where a photo appears on the site. Apply them in Cloudinary when uploading.

| Tag | Where it appears on the site |
|---|---|
| `gallery` | Main portfolio grid — visible under the "All" filter |
| `landscapes` | Appears when visitor clicks the Landscapes filter |
| `abstract` | Appears when visitor clicks the Abstract filter |
| `gardens` | Appears when visitor clicks the Gardens filter |
| `cityscapes` | Appears when visitor clicks the Cityscapes filter |
| `series` | Horizontal scrolling strip below the main gallery |
| `featured` | Reserved for future hero/homepage use |

> **One photo can have multiple tags.** Tag a photo `gallery` AND `landscapes` and it will appear in both the All view and the Landscapes filter. Tag it `gallery` AND `series` and it appears in both sections.

---

## How the Gallery Works (Technical)

The gallery does not contain any hardcoded images. When the page loads:

1. The browser calls a Cloudinary URL:  
   `https://res.cloudinary.com/dyb3d32yu/image/list/gallery.json`
2. Cloudinary returns a JSON list of every photo tagged `gallery`
3. The JavaScript reads that list and builds the gallery grid automatically
4. When a visitor clicks a filter tab (e.g. Landscapes), it repeats the same process for the `landscapes` tag

This means **the website always reflects whatever is in Cloudinary**. Upload a photo, tag it, done.

### Required Cloudinary Setting

For this to work, one setting must be configured in your Cloudinary account:

**Settings → Security → Restricted media types → `list` must be unticked**

If this is ticked, Cloudinary blocks the gallery from fetching the image list and the gallery will not load.

---

## Updating the Site Design

All design choices — colours, fonts, spacing — are at the top of `index.html`.

### Changing the Colour Theme

Find this section near the top of `index.html`:

```css
:root {
  --bg: #080808;        /* main background — currently near black */
  --bg2: #101010;       /* alternate section background */
  --text: #ede8df;      /* main text colour — currently warm white */
  --muted: #6b6560;     /* secondary text — currently grey */
  --gold: #c9a96e;      /* accent colour — currently warm gold */
  --gold-dim: #7a6240;  /* dimmer accent for borders */
}
```

Change any hex colour value, commit the file to GitHub, and Cloudflare republishes the site within ~30 seconds.

### Editing Text Content

Search `index.html` for placeholder text such as:
- `Your Name` — replace with your actual name
- `hello@yourname.com` — replace with your email
- `London · Est. 2018` — replace with your location and year
- The About section biography — replace with your own

---

## Deploying an Update to the Live Site

1. Open `index.html` in GitHub
2. Click the **pencil icon** to edit
3. Make your changes
4. Click **Commit changes**
5. Cloudflare detects the change and republishes automatically — usually within 30 seconds

---

## File Structure

```
/
├── index.html      ← The entire website. HTML + CSS + JavaScript in one file.
└── README.md       ← This document.
```

Photos are not stored here. They live in Cloudinary.

---

## What's Built

- [x] Full-screen hero section with cinematic animation
- [x] Portfolio gallery — dynamic, loads from Cloudinary by tag
- [x] Filter tabs — All / Landscapes / Abstract / Gardens / Cityscapes
- [x] Lightbox — click any image to view full screen with keyboard navigation
- [x] About section with biography and stats
- [x] Series section — dynamic horizontal scroll strip, loads from Cloudinary
- [x] Contact section
- [ ] Shop — limited edition print sales *(in development)*
- [ ] Tours — vintage camera walk bookings *(in development)*

---

## Stack & Cost

| What | Service | Monthly Cost |
|---|---|---|
| Website hosting | Cloudflare Pages | £0 |
| Code storage | GitHub | £0 |
| Image storage & delivery | Cloudinary (free tier, 25GB) | £0 |
| Fonts | Google Fonts | £0 |
| **Total** | | **£0** |

---

## Troubleshooting

**Gallery shows "Gallery loading" but never updates**  
→ Check Cloudinary: Settings → Security → `list` must be unticked. Then check your photos have the tag `gallery` applied (lowercase, no spaces).

**I uploaded a photo but it's not showing**  
→ Make sure you added the tag in Cloudinary. Go to Media Library, click the photo, check the Tags field.

**I committed a change but the site hasn't updated**  
→ Wait 60 seconds and hard-refresh your browser (Ctrl+Shift+R / Cmd+Shift+R). Cloudflare usually deploys within 30 seconds.

**The site URL says `.pages.dev` — how do I get a proper domain?**  
→ Buy a domain from Namecheap or Porkbun (~£8/year), then add it in Cloudflare Pages → Custom Domains. Cloudflare handles the SSL certificate automatically.
