# Prairie Pathways

A website for **Prairie Pathways**, a community-centered research project at Kansas State University
documenting the history of agricultural landscape change and celebrating the agricultural heritage of
rural Kansas through **oral histories** and **story maps**.

Built with [Hugo](https://gohugo.io) + [Hugo Blox](https://hugoblox.com) (the Research Group theme),
styled with a custom "Prairie" theme, and ready to deploy free on **GitHub Pages**.

---

## Contents

- [Quick start (edit locally)](#quick-start-edit-locally)
- [How the site is organized](#how-the-site-is-organized)
- [Things to change before you publish](#things-to-change-before-you-publish)
- [Adding content](#adding-content)
- [Editorial & privacy guidelines](#editorial--privacy-guidelines)
- [Deploy to GitHub Pages](#deploy-to-github-pages)
- [Changing the look](#changing-the-look)
- [Credits](#credits)

---

## Quick start (edit locally)

You only need this if you want to preview changes on your own computer. You can also edit files
directly on GitHub and let the site rebuild automatically.

**Prerequisites**

- [Hugo **Extended**](https://gohugo.io/installation/) `v0.148.2` or newer
- [Go](https://go.dev/dl/) `1.22`+ (Hugo Blox is delivered as Hugo Modules)

**Run it**

```bash
hugo mod get -u        # fetch the theme modules (first run only)
hugo server            # preview at http://localhost:1313
```

Edit any file under `content/`, save, and the browser refreshes automatically.

---

## How the site is organized

```
content/
  _index.md                 # Home page (hero, intro, featured stories, news)
  about/index.md            # About the project (framing, questions, regions, methods)
  participate/index.md      # How potential participants can take part
  oral-histories/           # Oral history archive
    _index.md               #   section intro
    <entry>/index.md        #   one story (+ featured.jpg)
  storymaps/                # Story maps
    _index.md
    <entry>/index.md        #   one story map (+ featured.jpg + embed)
  post/                     # News
    <post>/index.md
  people/index.md           # Team & partners page
  authors/                  # One folder per person (profile + avatar.jpg)
  contact/index.md          # Contact page (email + map)

config/_default/            # Site configuration (title, menu, params)
data/themes/prairie.toml    # Custom colors (light + dark)
data/fonts/prairie.toml     # Fonts
assets/media/               # Images (hero, backgrounds, icon, story art)
.github/workflows/deploy.yml# Auto-deploy to GitHub Pages
```

---

## Things to change before you publish

Search for these placeholders and replace them with your real details:

| What | Where |
| --- | --- |
| **Site URL** (`baseURL`) | `config/_default/hugo.yaml` — set to your GitHub Pages URL or custom domain. (The GitHub Action also sets this automatically, so this mainly matters for local previews and SEO tags.) |
| **Contact email** (`prairiepathways@ksu.edu`) | `content/participate/index.md`, `content/contact/index.md`, and each `content/authors/*/_index.md`. Replace with the address you want. |
| **Interest form link** | `content/participate/index.md` — the "Express interest" button currently points to `#`. Paste your Google Form / survey link. |
| **Story map embeds** | `content/storymaps/*/index.md` — replace `src="about:blank"` in the `<iframe>` with your published story map URL (e.g., an Esri ArcGIS StoryMaps share link). |
| **People** | `content/authors/` — edit `kate-nelson`, and replace the two placeholder profiles (`research-team-member`, `community-partner`) with your real team and partners, or delete them. |
| **Sample stories** | The oral-history and story-map entries are clearly labeled illustrative samples. Replace them with real content when it's ready. |
| **Repository link** | `config/_default/params.yaml` (`features.repository.url`). |

---

## Adding content

### A new oral history
1. Copy an existing folder, e.g. `content/oral-histories/a-little-of-everything/`, to a new name.
2. Edit `index.md` — update `title`, `summary`, `date`, `tags`, and the body.
3. Drop a `featured.jpg` in the folder for the card image.
4. Add the audio/transcript when available (see the note at the bottom of each entry).

### A new story map
1. Copy `content/storymaps/a-century-of-cropping-change/` to a new folder.
2. Edit `index.md` and paste your published map URL into the `<iframe src="...">`.
3. Add a `featured.jpg`.

### A news post
1. Copy any folder under `content/post/` and edit `index.md`.
2. Set `date:` — newer posts appear first, and the three most recent show on the home page.

> **Tip:** Hugo Blox also ships an optional visual editor (Decap CMS) at `/admin/`. It works once the
> site is deployed and you connect it to your Git host. See the Hugo Blox docs if you'd like to use it.

---

## Editorial & privacy guidelines

This site was written to follow two principles the project cares about. Please keep them in mind when
editing:

1. **Describe the work as studying change, not promoting it.** The project documents and seeks to
   understand the historical and socioecological processes of agricultural landscape change. Avoid
   language that frames the project as advocating for crop diversification (or any particular way of
   farming).
2. **Protect participant privacy.** Stories are attributed to broad **regions** of Kansas
   (North Central, Northwest, South Central) rather than to specific counties or towns, unless a
   contributor explicitly asks to be identified. Please don't add county- or town-level identifiers
   without permission.

---

## Deploy to GitHub Pages

The repository already includes a workflow (`.github/workflows/deploy.yml`) that builds and publishes
the site automatically.

1. Create a new repository on GitHub (e.g. `prairie-pathways`) and push this folder to it:
   ```bash
   git init
   git add .
   git commit -m "Initial Prairie Pathways site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/prairie-pathways.git
   git push -u origin main
   ```
2. On GitHub, go to **Settings → Pages** and set **Source** to **GitHub Actions**.
3. That's it. Every push to `main` rebuilds and publishes the site. The workflow sets the correct
   `baseURL` for you, whether you use `https://<user>.github.io/prairie-pathways/` or a custom domain.

**Custom domain (optional):** add your domain under Settings → Pages, and GitHub will manage the
`CNAME` for you.

**Prefer no code?** Hugo Blox can deploy this template straight from the browser, and it also works on
Netlify, Vercel, and Cloudflare Pages. See <https://docs.hugoblox.com>.

---

## Changing the look

- **Colors:** `data/themes/prairie.toml` — edit the `[light]` and `[dark]` values (prairie olive
  navbar, golden-wheat accents). Change `primary`, `menu_primary`, `link`, and the section
  backgrounds to taste.
- **Fonts:** `data/fonts/prairie.toml` — currently Fraunces (headings) + Inter (body).
- **Menu:** `config/_default/menus.yaml`.
- **Logo / favicon:** replace `assets/media/icon.png`.
- **Hero & section images:** replace the files in `assets/media/` (`hero.jpg`, `heritage.jpg`,
  `fields.jpg`, `contact.jpg`). These are original prairie illustrations included with the site; swap
  in your own photographs any time — keep the same filenames and no other edits are needed.

To switch between light and dark, use the sun/moon toggle in the top-right of the site.

---

## Credits

- Built on the open-source [Hugo Blox](https://hugoblox.com) **Research Group** template (MIT).
- Prairie theme, illustrations, and content prepared for the Prairie Pathways project,
  **Kansas State University**.
- This material is based upon work supported by the **U.S. National Science Foundation**. Any
  opinions, findings, and conclusions or recommendations expressed on this site are those of the
  project team and do not necessarily reflect the views of the National Science Foundation.
