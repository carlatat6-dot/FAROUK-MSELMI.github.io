# Academic homepage — Farouk Mselmi

A single-page academic website built from the CV. No build step, no dependencies:
just `index.html` plus the CV PDF.

```
index.html              the whole site (HTML + CSS + JS in one file)
CV_MSELMI_Farouk.pdf    linked from the "Download full CV" button
README.md               this file
```

---

## Publishing on GitHub Pages — 3 minutes

### Step 1 — Choose the repository name

This decides the final URL.

| Repository name | Resulting URL |
|---|---|
| `USERNAME.github.io` | `https://USERNAME.github.io` — **recommended**, one per account |
| `cv` (or any name) | `https://USERNAME.github.io/cv` |

Replace `USERNAME` with the GitHub account name. For a personal homepage the
first option is cleaner, so if the account is e.g. `fmselmi`, name the
repository exactly `fmselmi.github.io`.

### Step 2 — Create the repository

1. Go to <https://github.com/new>
2. **Repository name:** as chosen above
3. **Visibility:** Public — GitHub Pages needs this on free accounts
4. Leave "Add a README" unchecked
5. Click **Create repository**

### Step 3 — Upload the files

On the new empty repository page:

1. Click **uploading an existing file** (or go to `https://github.com/USERNAME/REPO/upload/main`)
2. Drag in **`index.html`** and **`CV_MSELMI_Farouk.pdf`** (both at the top level — not inside a folder)
3. Commit message: `Add academic homepage`
4. Click **Commit changes**

### Step 4 — Turn on Pages

1. Repository → **Settings** → **Pages** (left sidebar)
2. **Source:** `Deploy from a branch`
3. **Branch:** `main`, folder `/ (root)` → **Save**
4. Wait 1–2 minutes, then reload the Settings → Pages page: the live URL appears in a green banner at the top.

That's it. The site is live.

---

## Alternative — from the command line

```bash
cd mselmi-site
git init -b main
git add .
git commit -m "Add academic homepage"
git remote add origin https://github.com/USERNAME/USERNAME.github.io.git
git push -u origin main
```

Then do Step 4 above.

---

## Editing afterwards

Everything lives in `index.html`. Each part of the page is wrapped in a
clearly labelled `<section>`, so edits are local.

**Add a publication** — copy an existing `<li class="pub">` block in the
publications list, change the fields, and renumber the `pub-n` values
(the list is newest-first, highest number at the top). Also bump the count
in the `.stats` strip and the `.sec-head .count` text.

**Remove the personal details** — the `<section id="about">` block carries
the gender, date and place of birth, family situation and phone number from
the CV. Delete that whole `<section>` and the two `<a href="#about">About</a>`
links (one in the sidebar `<nav>`, one in the mobile `<nav class="drawer">`)
to drop it. See the note below.

**Change the accent colour** — one value, `--accent`, near the top of the
`<style>` block (currently a burgundy `#8b2e3c`). The dark-mode counterpart is
a few lines below it.

**Add a photo** — replace the `<div class="monogram">FM</div>` with
`<img class="monogram" src="photo.jpg" alt="Farouk Mselmi">` and upload
`photo.jpg` to the repository.

After any edit: commit the file (or re-upload it through the GitHub web
interface) and the live site updates within a minute.

---

## A note on the personal details

The page currently reproduces the CV in full, including the home address,
date and place of birth, family situation and mobile number. A GitHub Pages
site is public and indexed by search engines indefinitely, and that
particular combination of facts is the one most useful for identity theft
and unwanted contact.

Most academic homepages publish only the office address, institutional
e-mail and ORCID. Worth confirming with Farouk that he wants the rest on a
public page — if not, the two deletions described above remove it.

---

## Features

- Responsive single page; sidebar navigation on desktop, collapsible menu on mobile
- Active-section highlighting while scrolling
- Light / dark / system theme toggle, remembered per browser
- Print stylesheet — the page prints cleanly as a plain CV
- Semantic HTML, no framework, no tracking, loads in well under a second
- Only external request is the Google Fonts stylesheet; the page degrades to
  system serif/sans if it is blocked
