# CLAUDE.md — Goodwin Family Cookbook

## Project Overview

**Site name:** Bacon, Butter, and Red Wine
**Author/Owner:** Goodwin Family (Sean G — 0xSeanG)
**Live URL:** https://0xseang.github.io
**Repo:** https://github.com/0xSeanG/0xseang.github.io
**Stack:** Jekyll + GitHub Pages (migrated from GitBook)

A family recipe cookbook site. The primary use case is browsing and adding recipes. Family members submit recipes to Sean, who adds them to the site.

---

## Repository Structure

```
_config.yml             — Site config (title, plugins, collections, permalink rules)
_recipes/               — All recipe content, organized by category subfolder
  appetizers/
  bread/
  breakfast/
  dessert/
  main/
  sandwiches/
  sides/
_layouts/
  recipe.html           — Layout for individual recipe pages
  category.html         — Layout for category listing pages
  default.html          — Base layout
_pages/                 — Category index pages + about/search/recipes pages
index.html              — Homepage with category grid + recipe counts
RECIPE_TEMPLATE.md      — Template for family members to submit new recipes
search.json             — Powers site search
images/
  cookbook-cover.png    — Displayed on homepage
  avatar.svg            — Site avatar (G logo)
```

---

## Recipe File Format

All recipes live in `_recipes/<category>/<slug>.md`.

**Required front matter:**
```yaml
---
layout: recipe
title: "Recipe Title"
category: main          # lowercase, matches folder name
category_label: "Main Dishes"  # human-readable label
---
```

**Category → category_label mapping:**

| category     | category_label    |
|--------------|-------------------|
| appetizers   | Appetizers        |
| bread        | Bread             |
| breakfast    | Breakfast         |
| dessert      | Dessert           |
| main         | Main Dishes       |
| sandwiches   | Sandwiches        |
| sides        | Sides             |

**Body conventions:**
- Source line first (plain text or markdown link), followed by servings/time if available
- Use `### Ingredients` and `### Directions` as top-level sections
- Sub-sections within ingredients (e.g., Soup vs. Toppings) use `#### Heading`
- Directions use `1.` for all steps (markdown auto-numbers)
- Ingredient lists use `-` bullets

**File naming:** kebab-case matching the recipe title (e.g., `loaded-reuben-potato-soup.md`)

---

## Adding a New Category

If a new category is needed, three things must be created:
1. A subfolder under `_recipes/<category>/`
2. A page in `_pages/<category>.md` using the `category` layout
3. A new category card in `index.html`

---

## Site Configuration Notes

- `baseurl` is `""` (user page repo, not project page)
- Permalink for recipes: `/recipes/:path/` (set in `_config.yml`)
- Category pages are accessible at `/<category>/` (e.g., `/main/`)
- Plugins: `jekyll-sitemap`, `jekyll-feed`, `jekyll-seo-tag`
- No Disqus or Google Analytics configured (fields left blank)
- GitHub link in footer points to the repo

---

## Git Workflow

- Development branch prefix: `claude/`
- PRs are merged into `master`
- Push with: `git push -u origin <branch-name>`

---

## Decisions Made

- **Migrated from GitBook to Jekyll/GitHub Pages** — cleaner, self-hosted, no third-party dependency
- **Category subfolders** for `_recipes/` instead of flat structure — keeps things organized as the collection grows
- **No per-recipe metadata** (prep time, cook time, submitter) in front matter — this info is in the body text when present; keeping front matter minimal
- **`RECIPE_TEMPLATE.md`** exists for family members to fill out and send to Sean; Sean handles adding to the site
- **Sandwiches** was added as a distinct category (not lumped into mains)
- **Avatar** was changed from an "R" to a "G" (Goodwin)
- **Cookbook cover image** displayed on homepage for a book-like feel

---

## Current Recipe Count (as of 2026-03-19)

| Category    | Count |
|-------------|-------|
| Appetizers  | 6     |
| Bread       | 3     |
| Breakfast   | 3     |
| Dessert     | 2     |
| Main        | 18    |
| Sandwiches  | 1     |
| Sides       | 8     |
| **Total**   | **41** |
