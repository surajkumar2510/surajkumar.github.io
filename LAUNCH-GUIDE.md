# Launching your portfolio on GitHub Pages

Your site is one file: `index.html`. No build step, no framework, no dependencies.
Your photo and CV are already in place. Follow this once and it's live.

---

## What you have

```
portfolio/
├── index.html                    ← the whole website
├── .nojekyll                     ← tells GitHub not to reprocess your files
├── LAUNCH-GUIDE.md               ← this file (delete it after launch if you like)
└── assets/
    ├── images/
    │   ├── profile.jpg           ← your photo, already cropped and in the header
    │   └── ieee-space-2026.jpg   ← already showing in the Gallery tab
    ├── videos/                   ← put .mp4 / .webm animations here
    └── docs/
        └── CV.pdf                ← your resume, already wired to the Download button
```

---

## Step 0 — Pick your GitHub username

The repository name **must** match your GitHub username exactly. You asked me to
suggest one, so the site is currently written for:

**`surajkumar-iitm`** → your site becomes **https://surajkumar-iitm.github.io**

Other good options if that's taken:

| Username | Site URL |
|---|---|
| `surajkumar-iitm` | surajkumar-iitm.github.io |
| `surajkumar-robotics` | surajkumar-robotics.github.io |
| `suraj-kumar-ed` | suraj-kumar-ed.github.io |
| `surajkumarmech` | surajkumarmech.github.io |

**If you pick something other than `surajkumar-iitm`:** open `index.html` in any
text editor, press Ctrl+H (Find & Replace), replace every `surajkumar-iitm` with
your actual username, and save. It appears twice — the GitHub chip in the header
and the Contact tab.

Check availability at `https://github.com/YOURNAME` — a 404 page means it's free.

---

## Step 1 — Create the repository

1. Go to **https://github.com/new** (sign in first).
2. **Repository name:** type exactly `YOURUSERNAME.github.io` — all lowercase.
3. Set it to **Public**.
4. Do **not** tick "Add a README file".
5. Click **Create repository**.

> This exact name is what makes GitHub serve it as your personal site at
> `https://YOURUSERNAME.github.io` rather than under a sub-path.

---

## Step 2 — Upload the files

### Option A — Browser only (easiest)

1. On the empty repo page, click **uploading an existing file**.
2. Drag in `index.html` and the whole `assets` folder.
3. Type `initial portfolio` in the commit box and click **Commit changes**.
4. Then click **Add file → Create new file**, type `.nojekyll` as the filename,
   leave the body empty, and commit. (Browsers hide dotfiles from drag-and-drop.)

### Option B — Git command line

```bash
cd portfolio
git init
git add .
git commit -m "initial portfolio"
git branch -M main
git remote add origin https://github.com/YOURUSERNAME/YOURUSERNAME.github.io.git
git push -u origin main
```

---

## Step 3 — Turn Pages on

1. In your repo: **Settings** (top bar) → **Pages** (left sidebar).
2. **Source:** Deploy from a branch.
3. **Branch:** `main`, folder `/ (root)`. Click **Save**.
4. Wait 1–3 minutes, refresh — a green banner shows your live URL.

**Your site is live.**

---

## Step 4 — Fill the Gallery with your videos and animations

1. Copy files into `assets/images/` (photos, PNGs, GIFs) or `assets/videos/` (.mp4, .webm).
2. Open `index.html`, scroll to the bottom, find the `MEDIA` list.
3. Add one line per item:

```js
const MEDIA = [
  { type:"image", src:"assets/images/ieee-space-2026.jpg", group:"Conferences",
    title:"IEEE SPACE 2026, Bengaluru",
    desc:"Presenting the aircraft hydraulic system paper — awarded Best Paper." },

  { type:"image", src:"assets/images/cfd-pressure.png", group:"CFD",
    title:"Surface pressure contours", desc:"Bare-hull surge run at 1.0 m/s." },

  { type:"video", src:"assets/videos/spiral-glide.mp4", group:"Simulation",
    title:"Controlled spiral descent", desc:"7.5 revolutions in 1580 s.",
    poster:"assets/images/spiral-poster.jpg" },
];
```

- `type` is `"image"` or `"video"`. Animated GIFs count as `"image"`.
- `group` creates its filter button automatically — invent any groups you want.
- `poster` is optional: the still frame shown before a video plays.
- Groups that still have no real files keep showing a grey placeholder card, so the
  tab never looks broken. Each placeholder disappears the moment you add a real item
  to that group.

**Keep videos under about 25 MB.** GitHub blocks single files over 100 MB. To shrink one:

```bash
ffmpeg -i input.mov -vcodec libx264 -crf 28 -preset slow -an output.mp4
```

For a Simulink or Fluent animation, exporting as an **animated GIF** is often simpler
than video and works exactly the same way — just use `type:"image"`.

---

## Step 5 — Updating later

Edit `index.html`, commit, push — or click the pencil icon on github.com and edit
in the browser. The live site updates within a minute.

---

## Optional — your own domain

If you buy something like `surajkumar.in`:

1. Repo **Settings → Pages → Custom domain** → enter the domain → Save.
2. At your registrar add:
   - Four `A` records for the apex → `185.199.108.153`, `185.199.109.153`,
     `185.199.110.153`, `185.199.111.153`
   - One `CNAME` for `www` → `YOURUSERNAME.github.io`
3. Return to Settings → Pages and tick **Enforce HTTPS** once it's offered.

---

## After launch

- Add the URL to LinkedIn → **Contact info → Website**.
- Add it to your GitHub profile bio and to the header of your CV.
- Submit it at **https://search.google.com/search-console** so it appears in search.
- Replace `assets/docs/CV.pdf` whenever you update your resume — the filename must
  stay `CV.pdf` for the download button to keep working.

---

## Nine things still marked in orange

Search `index.html` for `class="todo"` — there are 9, all small:

1. About tab — the "Currently … open to" line (tell me what you're looking for).
2. Experience tab — NPTEL TA course name and term.
3. Education tab — NPTEL TA course name and term (same text).
4–9. Publications tab — author lists, exact titles and DOIs for the two conference papers.

Send me those and I'll hand you a version with nothing orange left.
