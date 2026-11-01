# TrainersKit website

A Jekyll site for GitHub Pages. The existing privacy policy, terms, and changelog routes are retained.

## Local preview

```sh
bundle install
bundle exec jekyll serve
```

Open the address printed by Jekyll. The production URL and repository base path are configured in `_config.yml`; change both if the site moves to a custom domain.

## Publishing articles

Add Markdown files in `_posts/` named `YYYY-MM-DD-descriptive-slug.md` with front matter:

```yaml
---
layout: post
title: An informative article title
description: A concise description of the article.
category: THE PRACTICAL TOOLKIT
reading_time: 5
# Optional: use an actual image and provide its alt text.
image: /assets/blog/example-preview.jpg
image_alt: Describe the image for readers who cannot see it
# Optional: only include a download when the file exists.
download:
  url: /assets/downloads/example.xlsx
  label: Download the free tracker
  details: Excel workbook · No sign-up required
# Optional: match each id to a heading in the article.
toc:
  - title: What to track
    id: what-to-track
---
```

All fields after `description` are optional. Remove the example image, download, and contents entries unless the article supplies real assets and matching heading IDs.

Posts appear on `/blog/`, receive a `/blog/descriptive-slug/` URL, and are included in the sitemap. Use original, useful content and descriptive headings. Images should include meaningful alt text. The site is empty until real articles are added.

The `sitemap.xml`, `robots.txt`, canonical links, and social metadata use the configured production URL. Submit the sitemap in Google Search Console after publishing and update the configuration if the domain changes.
