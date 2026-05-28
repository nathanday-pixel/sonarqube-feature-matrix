# sonarqube-feature-matrix
A Quick Feature Matrix for SonarQube 
[README.md](https://github.com/user-attachments/files/28357046/README.md)
# SonarQube Product Feature Matrix

An interactive, single-file web app for comparing SonarQube Cloud and Server editions. Built for internal use and customer-facing conversations.

**Live URL:** `https://your-username.github.io/sonarqube-feature-matrix/`

---

## What it covers

Four editions compared across 9 feature categories and 75+ features:

| Edition | Deployment |
|---|---|
| Cloud — Team | SaaS, managed by Sonar |
| Cloud — Enterprise | SaaS, managed by Sonar |
| Server — Developer | Self-hosted |
| Server — Enterprise | Self-hosted |

Feature categories: General & Setup · Analysis · Code Quality · Code Security · Reporting · Enterprise Security · AI Tools · Integrations · Support & Pricing

---

## Features of the app

- **Matrix view** — scrollable grid with sticky column headers and row hover highlighting
- **Overview view** — card-per-edition with feature coverage percentage and progress bar
- **Search** — filter features by keyword in real time
- **Section filter** — focus on one category at a time
- **Differences only** toggle — hides rows where all selected editions agree
- **Edition toggle** — show/hide any edition by clicking its chip (minimum 2)
- **Beta badges** — Cloud-only open beta features are clearly labeled
- Dark mode support, no build step, no dependencies to install

---

## Making updates

All content lives in the `SECTIONS` array inside `index.html`. Each feature looks like this:

```js
{
  id: "my_feature",
  label: "Feature display name",
  cloud_team: CHECK,       // true = included
  cloud_ent:  CHECK,
  server_dev: NO,          // false = not included
  server_ent: "Add-on",    // string = conditional / partial
}
```

**Special values:**

| Value | Meaning | Renders as |
|---|---|---|
| `CHECK` (i.e. `true`) | Fully included | Green ✔ |
| `NO` (i.e. `false`) | Not included | Red — |
| `BETA` | Cloud open beta | Orange BETA badge |
| `"N/A"` | Not applicable | Grey N/A |
| Any other string | Conditional or partial | Small text in cell |

### Adding a feature

Find the right section in `SECTIONS`, add a new object to its `features` array:

```js
{ id:"new_feature", label:"My new feature", cloud_team:CHECK, cloud_ent:CHECK, server_dev:NO, server_ent:CHECK },
```

### Adding a section

Add a new object to the top-level `SECTIONS` array:

```js
{
  id: "my_section",
  label: "My Section",
  icon: "ti-star",   // any Tabler icon name — see tabler.io/icons
  features: [ ... ]
}
```

### Updating pricing

In the `support` section, edit the `entry_price` and `pricing_model` feature rows.

---

## Deploying changes

1. Edit `index.html` locally or directly on GitHub
2. Commit to `main`
3. GitHub Pages rebuilds automatically — live within ~60 seconds

---

## Tech stack

| | |
|---|---|
| Framework | None — plain HTML, CSS, JavaScript |
| Icons | [Tabler Icons](https://tabler.io/icons) (webfont via CDN) |
| Fonts | [DM Sans](https://fonts.google.com/specimen/DM+Sans) via Google Fonts |
| Hosting | GitHub Pages |
| Build step | None |

---

## Source

Feature data sourced from [sonarsource.com/plans-and-pricing](https://www.sonarsource.com/plans-and-pricing/) and official documentation. Last updated May 2026.
