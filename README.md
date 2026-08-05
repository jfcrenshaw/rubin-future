# Rubin Future

Source for the Rubin Future GitHub Pages site:

https://jfcrenshaw.github.io/rubin-future/

Rubin Future is a community planning hub for what Rubin Observatory can become after the Legacy Survey of Space and Time.

> [!NOTE]
> This site is under construction as the Rubin Future effort takes shape.

## Editing Content

Most updates should not require layout or CSS changes.

### Add a Meeting

Edit `_data/meetings.yml` and add a new entry:

```yaml
- title: Meeting title
  date: 2026-09-15
  status: upcoming
  location: Online
  host: Organizing group
  url: "https://example.org"
  materials:
    - title: Agenda
      url: "https://example.org/agenda"
```

Use `status: upcoming` for future meetings and `status: past` for previous meetings. `materials` is optional.

### Add a Document

Edit `_data/documents.yml` and add a new entry:

```yaml
- title: Document title
  category: Planning
  url: "https://example.org"
  description: Short description.
  year: 2026
  type: Report
```

`description`, `year`, and `type` are optional.

### Edit Pages

The main prose pages are Markdown files in the repository root:

- `index.md`
- `meetings.md`
- `documents.md`
- `community.md`
- `about.md`

## Local Preview

Use Ruby 3.3 or newer for the closest match to GitHub Pages.

Install dependencies:

```sh
bundle install
```

Preview the site:

```sh
bundle exec jekyll serve
```

Build without serving:

```sh
bundle exec jekyll build
```

## Publishing

On GitHub, enable Pages for this repository:

1. Open repository settings.
2. Go to Pages.
3. Select "Deploy from a branch".
4. Select branch `main` and folder `/root`.
5. Save.

GitHub Pages will publish updates after commits are pushed to `main`.

## Media Attribution

The hero image is from the Rubin Observatory gallery:

- Title: The Milky Way and its companions dazzle above Rubin
- Source: https://rubinobservatory.org/gallery/collections/featured-media/5ourjnkk156lfbqaahfppehs2c
- Credit: NSF-DOE Vera C. Rubin Observatory/NOIRLab/SLAC/AURA/P. Lago
- Use policy: https://rubinobservatory.org/gallery/media-policy
