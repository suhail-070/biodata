# Marriage Biodata — Shaikh Mohammad Suhail

A single-page, static biodata website. Plain HTML + CSS, no JavaScript, no build step,
no frameworks. It works by simply opening `index.html` in any browser.

```
biodata/
├── index.html          the whole website (HTML + CSS in one file)
├── README.md           this file
└── photos/
    ├── main-photo.jpg  faded background photograph
    ├── logo.png        SUHAIL monogram
    ├── photo-01.jpg    hero portrait
    ├── photo-02.jpg    Personal Details
    ├── photo-03.jpg    Education & Career
    ├── photo-04.jpg    Family Background
    ├── photo-05.jpg    Siblings
    ├── photo-06.jpg    Contact
    └── logo-original.png  your original green monogram (spare)
```

---

## Changing a photo

Save your new picture into the `photos/` folder using **exactly the same filename**
you want to replace, e.g. `photo-03.jpg`. Nothing else needs editing.
Portrait-orientation (tall) photos look best; roughly 900–1400 px on the long side
keeps the page fast.

**Note on colour:** the page itself is black and white — white paper, black ink,
neutral greys — with purple and deep beige for the headings, labels and details.
The photographs keep their full colour, which is what makes them stand out.
Only the faded full-page background photo is greyscaled.

**The monogram:** `logo.png` is your monogram recoloured to the purple/ink
palette. The original green version is kept as `logo-original.png` — rename it
over `logo.png` if you prefer it.

**Making the background photo stronger or fainter:** in `index.html`, near the top
of the CSS, change `--bg-photo-opacity: .70;` — lower is fainter, higher is stronger.

**Changing colours:** all colours live in the `:root { ... }` block at the top of the
CSS (section 1, "VARIABLES"). Change them there once and the whole page follows.

## Saving it as a PDF

Open the page in Chrome → **Print** (Ctrl/Cmd + P) → **Destination: Save as PDF**.
A dedicated print stylesheet drops the background photo and shadows and keeps
sections from splitting across pages.

---

# Hosting it free on GitHub Pages

The result will be a public link like
`https://YOUR-USERNAME.github.io/biodata/`

Replace `YOUR-USERNAME` with your actual GitHub username everywhere below.

## Option A — no command line (easiest, ~5 minutes)

1. Go to **https://github.com/new** and sign in.
2. **Repository name:** `biodata`
   **Visibility:** Public.
   Do **not** tick "Add a README file".
   Click **Create repository**.
3. On the empty repo page click **uploading an existing file**.
4. Drag in `index.html`, `README.md`, **and the whole `photos` folder**.
   (Drag the folder itself — GitHub keeps the folder structure. If your browser
   won't accept a folder, upload `index.html` first, then use
   *Add file → Upload files* again and drop the photos in after creating the
   `photos/` path by typing `photos/` at the start of the filename.)
5. Scroll down, click **Commit changes**.
6. Go to **Settings** (top of the repo) → **Pages** (left sidebar).
7. Under **Build and deployment → Source**, choose **Deploy from a branch**.
   **Branch:** `main`, **Folder:** `/ (root)`. Click **Save**.
8. Wait about a minute, refresh the Pages screen, and your live link appears at
   the top: `https://YOUR-USERNAME.github.io/biodata/`

## Option B — using Git on your computer

Install Git first (https://git-scm.com/downloads), then create the empty public
repo as in steps 1–2 above and run:

```bash
# go into the project folder
cd path/to/biodata

git init
git add .
git commit -m "Marriage biodata website"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/biodata.git
git push -u origin main
```

Then do steps 6–8 above to switch GitHub Pages on.

To publish any later change:

```bash
git add .
git commit -m "Update photos"
git push
```

The live site refreshes about a minute after each push.

## Optional — a shorter URL

If you name the repository **`YOUR-USERNAME.github.io`** instead of `biodata`,
the site is served at `https://YOUR-USERNAME.github.io/` with nothing after it.
Everything else in the steps stays the same.

## Optional — your own domain

Buy a domain, then in the repo's **Settings → Pages → Custom domain** enter it and
save. At your domain registrar add these DNS records:

| Type  | Name  | Value                                            |
|-------|-------|--------------------------------------------------|
| A     | `@`   | `185.199.108.153`                                |
| A     | `@`   | `185.199.109.153`                                |
| A     | `@`   | `185.199.110.153`                                |
| A     | `@`   | `185.199.111.153`                                |
| CNAME | `www` | `YOUR-USERNAME.github.io`                        |

Give DNS up to an hour, then tick **Enforce HTTPS** on the Pages screen.

---

## Troubleshooting

**Photos don't show on the live site but work locally.**
GitHub Pages is case-sensitive. The folder must be `photos` (lowercase) and the
files exactly `photo-01.jpg` etc. — `Photo-01.JPG` will not load.

**The page didn't update after a push.**
GitHub Pages caches. Wait a minute, then hard-refresh: Ctrl + Shift + R
(Cmd + Shift + R on Mac).

**404 on the live link.**
Confirm `index.html` sits at the top level of the repository, not inside another
folder, and that Pages is set to branch `main`, folder `/ (root)`.
