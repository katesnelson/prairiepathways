# Prairie Pathways — Editing Guide

A practical, plain-language guide to updating the website: changing text, adding posts, oral histories,
and story maps, managing people, and swapping images, colors, and fonts. It also points to the exact
file for every common change.

> **Two ways to edit**
> 1. **On GitHub (no software needed).** Browse to a file in your repository, click the pencil ✏️
>    icon, make your change, and click *Commit changes*. The site rebuilds and republishes itself in a
>    minute or two.
> 2. **On your computer.** Edit the files in a text editor and run `hugo server` to preview live
>    (see [Preview & publish](#preview--publish)).
>
> Either way, you are just editing plain text files. Nothing you can type into a content file will
> break the site permanently — if a change looks wrong, undo it and re-save.

---

## Quick reference — "I want to change ___"

| I want to… | Edit this file |
| --- | --- |
| Change the **big home‑page image** (hero) | `content/_index.md` → hero block → `image: filename: hero.jpg`; replace the file `assets/media/hero.jpg` |
| Change the **home‑page headline / tagline / buttons** | `content/_index.md` (top `hero` block) |
| Edit the **About page** text | `content/about/index.md` |
| Edit the **Participate page** (and its email / form link) | `content/participate/index.md` |
| Add or edit a **News post** | `content/post/` (one folder per post) |
| Add or edit an **Oral History** | `content/oral-histories/` |
| Add or edit a **Story Map** | `content/storymaps/` |
| Add / edit **people** (team & partners) | `content/authors/` (one folder per person) |
| Change the **contact email, address, or map** | `content/contact/index.md` |
| Change the **site name** or **web address** | `config/_default/hugo.yaml` |
| Change the **navigation menu** | `config/_default/menus.yaml` |
| Change **colors** (navbar, links, accents, dark mode) | `data/themes/prairie.toml` |
| Change **fonts** | `data/fonts/prairie.toml` |
| Change the **logo / browser icon** | replace `assets/media/icon.png` |
| Change **footer text**, search, map, social/SEO | `config/_default/params.yaml` |
| Add any **photo or image** | drop the file in `assets/media/` and reference its filename |

---

## How a page is built: front matter + body

Almost every content file has two parts:

```markdown
---
title: "My title"
date: 2026-09-19
summary: "One-line description used on cards and previews."
tags:
  - Oral history
---

The body goes here, written in **Markdown**.
```

- The part between the `---` lines is the **front matter** (settings: title, date, tags, image…).
- Everything **below** the second `---` is the **body**, written in Markdown.

The home page, About, Participate, People, and Contact are "landing" pages built from **blocks**
(hero, markdown, collection, etc.) instead of a plain body — those are described where they come up
below.

---

## Add a News post

1. In `content/post/`, copy an existing post folder (e.g. `prairie-pathways-is-underway/`) and rename
   the copy to a short, hyphenated name, e.g. `field-day-recap/`.
2. Open the `index.md` inside it and edit the front matter and body:

   ```markdown
   ---
   title: "A field day in the North Central region"
   subtitle: "Optional one-line subtitle"
   summary: "Short blurb shown on the News cards and the home page."
   date: 2026-10-01          # newer dates appear first
   authors:
     - kate-nelson           # must match a folder name in content/authors/
   tags:
     - Fieldwork
   featured: false
   ---

   Write the post here in Markdown.
   ```
3. **Add a picture (optional):** put an image named `featured.jpg` in the same folder. It becomes the
   card image automatically. No image is fine too.
4. The three most recent posts appear on the home page automatically.

---

## Add an Oral History

1. In `content/oral-histories/`, copy an existing entry folder (e.g. `a-little-of-everything/`) to a
   new name.
2. Edit `index.md`. Useful fields:

   ```markdown
   ---
   title: "Title of the story"
   subtitle: "A short descriptive line"
   summary: "Blurb shown on cards."
   date: 2026-10-05
   tags:
     - Oral history
     - North Central Kansas      # use REGION names, never counties (see note below)
   featured: true
   image:
     caption: 'Caption shown under the photo'
   ---

   Body goes here.
   ```
3. Add a `featured.jpg` to the folder for the card/lead image.
4. When you have audio or a transcript, you can embed or link it in the body (ask for help if you'd
   like a built-in audio player added).

> **Privacy reminder:** attribute stories to the broad regions — **North Central**, **Northwest**,
> **South Central** Kansas — not to specific counties or towns, unless the contributor has asked to be
> identified.

---

## Add a Story Map

1. In `content/storymaps/`, copy an existing entry (e.g. `a-century-of-cropping-change/`).
2. Edit `index.md` front matter (same fields as above) and body.
3. **Embed your interactive map.** Find this block in the body and replace `about:blank` with your
   published story‑map link (for example, an Esri ArcGIS StoryMaps *share* URL):

   ```html
   <div class="ratio ratio-16x9 my-4 shadow-sm rounded" style="overflow:hidden;">
     <iframe src="https://storymaps.arcgis.com/stories/XXXXXXXX"
             title="My story map" allowfullscreen loading="lazy"
             style="border:0;"></iframe>
   </div>
   ```
4. Add a `featured.jpg` for the card image.

---

## Manage People (team & partners)

Each person is a folder in `content/authors/`:

- `kate-nelson/` — your profile (marked `superuser: true`).
- `research-team-member/` and `community-partner/` — **placeholders**; replace or delete them.

To **add a person**, copy a folder, rename it (e.g. `jane-doe/`), and edit its `_index.md`:

```markdown
---
title: Jane Doe                 # display name
role: Graduate Researcher
organizations:
  - name: Kansas State University
    url: 'https://www.k-state.edu/'
interests:
  - Oral history
social:
  - icon: envelope
    icon_pack: fas
    link: 'mailto:jane@ksu.edu'
  - icon: github
    icon_pack: fab
    link: 'https://github.com/janedoe'
user_groups:
  - Research Team               # the section they appear under (see below)
---

A short bio in Markdown.
```

- Add a **photo** named `avatar.jpg` in the person's folder (square images look best).
- `user_groups` controls which section a person appears under on the People page. The groups shown,
  and their order, are set in `content/people/index.md` (currently *Principal Investigators*,
  *Research Team*, *Community Partners*). Add or rename groups there and in each person's
  `user_groups`.

---

## Change images

All shared images live in **`assets/media/`**. To replace one, save your new image with the **same
filename** — no other edits needed. Key files:

| Image file | Where it appears |
| --- | --- |
| `hero.jpg` | The large home‑page hero background |
| `heritage.jpg` | Home‑page "Every farm has a story" band |
| `fields.jpg` | About page "How we work" band; Story Maps page banner |
| `contact.jpg` | Contact page band; News page banner |
| `icon.png` | Logo / browser tab icon |
| `story-*.jpg` | Sample card images (copied into entry folders as `featured.jpg`) |

**Per-entry images** (news, oral histories, story maps) are the `featured.jpg` files inside each
entry's own folder, not in `assets/media/`.

### The home-page hero image and its options

Open `content/_index.md`. The very first block is the hero. The image and its display options live here:

```yaml
  - block: hero
    content:
      title: Prairie Pathways
      text: |
        Documenting the history of agricultural landscape change — ...
      cta:                      # the primary button
        url: ./participate/
        label: Share your story
        icon: microphone
      cta_alt:                  # the secondary text link
        url: ./about/
        label: About the project
      cta_note:                 # small line under the buttons
        label: A community-centered research project ...
    design:
      background:
        image:
          filename: hero.jpg    # ← the image file (in assets/media/)
          filters:
            brightness: 0.5     # ← 0 = black, 1 = full brightness (lower = darker, more legible text)
          parallax: false       # ← keep false for reliable display on phones
          position: center
          size: cover
        text_color_light: true  # ← true = white text over the image (must sit here, NOT under `image:`)
      spacing:
        padding: ['170px', '0', '150px', '0']   # top, right, bottom, left height of the hero
```

The same `background:` pattern (with `brightness`, `text_color_light`, `parallax`) is reused for the
photo bands on the home page (`heritage.jpg`), About (`fields.jpg`), and Contact (`contact.jpg`).

> **Gotcha worth remembering:** `text_color_light` must be indented under `background:` (same level as
> `image:`), *not* inside `image:`. `brightness` **is** inside `image: → filters:`. If hero text ever
> turns dark and hard to read, this is almost always why.

---

## Change the site name, address, menu, colors, and fonts

### Site name & web address — `config/_default/hugo.yaml`
```yaml
title: Prairie Pathways
baseURL: 'https://katesnelson.github.io/prairie-pathways/'   # your GitHub Pages URL or custom domain
```
(The auto‑deploy workflow also sets the address at build time, so this mainly affects local previews
and SEO tags.)

### Navigation menu — `config/_default/menus.yaml`
Each item is a name, a URL, and a weight (order). To add a page to the menu:
```yaml
  - name: Resources
    url: resources/
    weight: 35            # lower numbers appear first
```

### Colors — `data/themes/prairie.toml`
Separate `[light]` and `[dark]` sections. The main knobs:
```toml
[light]
  primary       = "#a5670f"   # accent: buttons, links, highlights
  menu_primary  = "#3d4d2a"   # navbar background (prairie olive)
  menu_text_active = "#f2c14e" # active menu item (wheat gold)
  link          = "#9c6410"
  home_section_odd  = "#faf6ee" # alternating section backgrounds
  home_section_even = "#ffffff"
```
Change a hex value, save, and the whole site restyles. The `[dark]` block controls dark mode (the
sun/moon toggle in the top‑right of the site).

### Fonts — `data/fonts/prairie.toml`
```toml
google_fonts = "family=Fraunces:...&family=Inter:..."
heading_font = "Fraunces"   # headings
body_font    = "Inter"      # body text
nav_font     = "Inter"
```
Use any [Google Fonts](https://fonts.google.com) family: add it to `google_fonts` and name it in the
matching field.

### Logo / browser icon
Replace `assets/media/icon.png` with your own square image (a logo or emblem).

### Footer, search, map, social/SEO — `config/_default/params.yaml`
- **Footer line:** `footer.copyright.notice`
- **Site description & social handles (SEO):** `marketing.seo`
- **Contact map provider/zoom:** `features.map`
- **"Edit this page" repo link:** `features.repository.url`

---

## Contact page — `content/contact/index.md`

Edit the `contact` block:
```yaml
      email: prairiepathways@ksu.edu
      address:
        city: Manhattan
        region: KS
        postcode: '66506'
      coordinates:
        latitude: '39.1897'      # moves the map pin
        longitude: '-96.5847'
      form:
        provider: ''             # '' = no form (right for GitHub Pages)
```
GitHub Pages can't process a contact form, so it's disabled and visitors are pointed to email. If you
later host somewhere that supports forms (e.g. Netlify) or use a [Formspree](https://formspree.io)
form, set `provider: formspree` and add `formspree: { id: your-id }`.

---

## Formatting cheat sheet (Markdown & extras)

Inside any page **body**:

| You want | Write this |
| --- | --- |
| Bold / italic | `**bold**`, `*italic*` |
| Heading | `## Heading`, `### Smaller heading` |
| Link | `[link text](https://example.com)` |
| Bulleted list | lines starting with `- ` |
| Numbered list | lines starting with `1. ` |
| Block quote | line starting with `> ` |
| An image in the body | `![caption](image.jpg)` (put the file in the same folder) |
| A highlighted note box | `{{% callout note %}}` … `{{% /callout %}}` (wrap the text between them) |
| A call‑to‑action button | `{{% cta cta_link="./participate/" cta_text="Get involved →" %}}` |
| An icon in HTML | `<i class="fas fa-microphone"></i>` (see icon note below) |
| A 3‑across card row | copy the `<div class="row">…</div>` block from `content/_index.md` (the "Explore" section) |

**Icons.** Buttons and cards use [Font Awesome](https://fontawesome.com/icons) (`fas`/`fab`) and
[Academicons](https://jpswalsh.github.io/academicons/) (`ai`). In front matter, an icon is written as
`icon: envelope` + `icon_pack: fas`. In HTML, as `<i class="fas fa-envelope"></i>`.

---

## Preview & publish

**Preview on your computer** (optional — requires [Hugo Extended](https://gohugo.io/installation/)
`0.148.2`+ and [Go](https://go.dev/dl/) `1.22`+):
```bash
hugo server        # open http://localhost:1313 — updates live as you save
```

**Publish.** If the site is on GitHub with the included workflow, you don't do anything special:
**every change you commit to the `main` branch rebuilds and republishes the site automatically**
(usually within 1–2 minutes). Check the **Actions** tab of your repository to watch a build or see
errors. Full setup steps are in `README.md`.

---

## If something looks broken

- **Hero text is dark/unreadable:** check `text_color_light: true` is under `background:` (not inside
  `image:`) in that block. See the hero gotcha above.
- **A card has no image:** make sure the file is named exactly `featured.jpg` and is inside that
  entry's folder.
- **A page vanished from the menu but still exists:** the menu is separate from the pages — check
  `config/_default/menus.yaml`.
- **A build failed after an edit:** open the repository's **Actions** tab; the red ✗ log usually names
  the file and line. Most often it's a small typo in the front matter (a missing quote, or wrong
  indentation). Undo the last change and re-commit if in doubt.

When in doubt, you can always copy one of the existing entries that already works and change its words
— that's the safest way to add new content.
