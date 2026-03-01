---
layout: docs
title: Site Configuration
description: Full reference for configuring your PitCrew site — using the wizard or editing files directly.
permalink: /docs/site-setup/
parent: Getting Started
---

**On this page:** [The Setup Wizard](#the-setup-wizard) · [_config.yml Reference](#configyml-reference) · [Data Files](#data-files) · [Colors](#colors) · [Features](#features) · [Navigation](#navigation) · [Deployment](#deployment) · [Troubleshooting](#troubleshooting)

---

## The Setup Wizard

The wizard is the recommended way to configure your site. It edits `_config.yml` and all `_data/*.yml` files through a guided UI — no text editing required.

**Access:** Visit `/wizard/` on your site. It also launches automatically on first visit if `startup_wizard: true` is set in `_config.yml`.

### What the wizard configures

| Step | What changes |
|---|---|
| Team Identity | `_config.yml` → `title`, `description`, `site.*` |
| Brand Colors | `_config.yml` → `theme.colors.*` |
| Features | `_config.yml` → `features.*` and `fundraising.*` |
| Social Links | `_config.yml` → `socials.*` |
| Navigation | `_config.yml` → `navigation` |
| Team Members | `_data/team.yml` |
| Mentors | `_data/mentors.yml` |
| Sponsors | `_data/sponsors.yml` |
| Awards | `_data/awards.yml` |
| Events | `_data/events.yml` |

### Saving progress mid-wizard

The **Save Progress** button in the footer generates `pitcrew-progress.zip` at any step. Copy those files into your project to preserve your work. When you return to `/wizard/` later, it starts at Step 1 — but all saved data is already loaded.

### The "Skip wizard on startup" option

On the final Review step, checking **"Skip wizard on startup"** sets `startup_wizard: false` in the downloaded `_config.yml`. This stops the site from auto-redirecting visitors to `/wizard/` once you deploy.

You can always return to `/wizard/` manually to make further changes.

---

## `_config.yml` Reference

Every site setting lives in `_config.yml`. Changes take effect after restarting Jekyll — no CSS rebuild needed.

### Site identity

```yaml
title: "Your Team Name"
description: "A short description shown in search results and metadata"
url: ""       # leave blank for GitHub Pages root deployment
baseurl: ""   # set to /repo-name if deploying to a subpath
```

### Team configuration

```yaml
site:
  team_name: "Team Voltage"
  team_number: "12345"
  program: "FTC"          # FTC | FRC | VEX | FLL
  current_season: "2025-2026"
  logo: "/assets/images/logo.png"
```

### Social links

```yaml
socials:
  instagram: "https://instagram.com/yourteam"
  github:    "https://github.com/yourteam"
  youtube:   "https://youtube.com/@yourteam"
  twitter:   "https://twitter.com/yourteam"
  email:     "team@school.edu"
```

Leave any value blank (`""`) to hide that link from the site.

### Fundraising banner

```yaml
fundraising:
  enabled: true
  url:  "https://gofundme.com/your-campaign"
  text: "Support Our Team"
```

### Wizard flag

```yaml
startup_wizard: false   # true = auto-redirect first-time visitors to /wizard/
```

---

## Colors

Colors are defined once in `_config.yml` and injected into every page as CSS custom properties. You never need to touch CSS files.

```yaml
theme:
  colors:
    # Primary — nav bar, buttons, headings
    primary:           "#003974"
    primary_highlight: "#002855"   # hover states, gradient mid
    primary_darkest:   "#001a3d"   # hero gradient end

    # Secondary — accent color, badges, highlights
    secondary:           "#F57E25"
    secondary_highlight: "#d96a1f"

    # Semantic
    success: "#28a745"
    info:    "#17a2b8"
    warning: "#f0b37e"
    danger:  "#dc3545"

    # Sponsor tier card borders
    sponsor_platinum: "#9ca3af"
    sponsor_gold:     "#eab308"
    sponsor_silver:   "#d1d5db"
    sponsor_bronze:   "#92400e"

  dark_mode: true   # true = dark mode on by default for visitors
```

**Tips:**
- Use the wizard's color step — it shows a live preview as you pick
- `primary_highlight` and `primary_darkest` can be auto-derived by the wizard (10% and 25% darker than `primary`)
- Colors update immediately on page reload; no CSS rebuild needed

---

## Features

Toggle any feature on or off. Disabled features are not built and won't appear in navigation.

```yaml
features:
  blog:                true   # News/blog feed at /news/
  docs:                true   # Documentation section at /docs/
  cad_viewer:          true   # Interactive 3D CAD model viewer
  circuit_viewer:      true   # Electrical schematic viewer
  code_links:          true   # Links to code repositories
  data_visualizations: true   # Match data charts and graphs
  alumni_auto_archive: true   # Auto-move graduated members to alumni page
  accessibility_toggle: true  # High-contrast / reduced-motion controls
  search:              true   # Site-wide search
```

---

## Navigation

The top navigation bar is driven by the `navigation` list in `_config.yml`. Order matters — items appear left to right.

```yaml
navigation:
  - title: Home
    url: /
  - title: About
    url: /about/
  - title: Season
    url: /season/
  - title: Awards
    url: /awards/
  - title: Sponsors
    url: /sponsors/
  - title: Docs
    url: /docs/
  - title: News
    url: /news/
```

**Rules:**
- `url` must match the page's `permalink` exactly, including trailing slash
- Only include pages that actually exist in your site
- The wizard's Navigation step lets you reorder with ▲/▼ buttons

---

## Data Files

All content that changes each season lives in `_data/`. These are plain YAML files — edit them directly or use the wizard.

### `_data/team.yml`

```yaml
- name: "Alex Johnson"
  role: "Team Captain"
  grade: 12
  graduation_year: 2026
  bio: "Short bio here."
  image: "/assets/images/alex.jpg"    # omit for placeholder
  skills:
    - Leadership
    - Strategy
```

### `_data/mentors.yml`

```yaml
- name: "Dr. Sarah Patel"
  role: "Lead Mentor"
  bio: "Bio here."
  image: "/assets/images/sarah.jpg"
  organization: "TechCorp Inc."
```

### `_data/sponsors.yml`

```yaml
- name: "Precision Engineering Co"
  tier: platinum     # platinum | gold | silver | bronze
  logo: "/assets/images/sponsors/precision.png"
  url: "https://precisioneng.example.com"
```

### `_data/awards.yml`

```yaml
- name: "Inspire Award"
  event: "State Championship"
  season: "2024-2025"
  description: "Awarded for embodying the FIRST mission."
```

### `_data/events.yml`

```yaml
- name: "League Meet 1"
  date: 2026-01-18
  location: "Lincoln High School"
  type: competition    # competition | event | outreach
  description: "Our first qualifying meet."
  url:                 # optional — leave blank if none
```

### `_data/alumni.yml`

Managed automatically by the alumni archive workflow when `alumni_auto_archive: true`. You can also add entries manually:

```yaml
- name: "Jordan Lee"
  role: "Former Build Lead"
  graduation_year: 2025
  seasons:
    - 2024-2025
    - 2023-2024
  now: "Studying Mechanical Engineering at MIT"
  bio: "Bio here."
  image: "/assets/images/jordan.jpg"
```

---

## Deployment

PitCrew is a static Jekyll site — it builds to plain HTML files that can be hosted anywhere.

### GitHub Pages (recommended)

1. Push your repo to GitHub
2. Go to **Settings → Pages**
3. Set source to `main` branch, `/ (root)` folder
4. Your site is live at `https://yourusername.github.io/repo-name/`

If deploying to a subpath (not the root), set `baseurl: "/repo-name"` in `_config.yml`.

### Local preview

```bash
bundle install          # first time only
bundle exec jekyll serve
# → http://localhost:4000
```

### After wizard changes

```bash
# 1. Extract pitcrew-config.zip into your project (overwrite existing files)
# 2. Preview
bundle exec jekyll serve
# 3. Deploy
git add _config.yml _data/
git commit -m "Update site configuration"
git push
```

---

## Troubleshooting

**Wizard auto-redirects even after I'm done**

Set `startup_wizard: false` in `_config.yml`, or check the "Skip wizard on startup" box on the wizard's Review step before downloading.

**Color changes aren't showing**

Colors are injected from `_config.yml` at build time. Restart `jekyll serve` after editing the file.

**A data file looks wrong after a wizard download**

Open the `.yml` file in a text editor. YAML is sensitive to indentation (2 spaces, no tabs). Check that list items start with `- ` and nested keys are indented correctly.

**A page shows 404**

Check that the page's `permalink` in its front matter matches exactly what's in `_config.yml` → `navigation` or `_data/docs_navigation.yml`. Include the trailing slash.

**Images aren't loading**

Confirm the file exists at the exact path referenced in the YAML (e.g. `_data/team.yml` → `image: /assets/images/photo.jpg`). Paths are case-sensitive on Linux hosts.
