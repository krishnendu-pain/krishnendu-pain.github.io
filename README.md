# krishnendu-pain.github.io

Academic homepage of Krishnendu Pain, built with [al-folio](https://github.com/alshedivat/al-folio) and hosted on GitHub Pages at <https://krishnendu-pain.github.io>.

Every push to `main` triggers the **Deploy site** GitHub Action, which builds the site and publishes it to the `gh-pages` branch (takes ~3–5 min).

## Where things live

| What                                         | File                                                                                  |
| -------------------------------------------- | ------------------------------------------------------------------------------------- |
| Bio, affiliation, interests                  | `_pages/about.md`                                                                     |
| Profile photo                                | `assets/img/prof_pic.jpg`, then set `profile.image` in `about.md`                     |
| Research page sections and search box on/off | `sections:` and `search_box:` in the front matter of `_pages/research.md`             |
| Works in progress                            | `_bibliography/works_in_progress.bib`                                                 |
| Working papers                               | `_bibliography/working_papers.bib`                                                    |
| Publications                                 | `_bibliography/papers.bib`                                                            |
| Paper PDFs                                   | `assets/pdf/`                                                                         |
| CV (PDF)                                     | replace `assets/pdf/cv.pdf` (the CV page and the bio link both point to it)           |
| Email / Scholar / ORCID etc.                 | `_data/socials.yml`                                                                   |
| Coauthor profile links                       | `_data/coauthors.yml` (uncomment an entry and paste the URL)                          |
| Accent color (links, highlights)             | `$purple-color` (light mode) and `$cyan-color` (dark mode) in `_sass/_variables.scss` |
| News items                                   | one file per item in `_news/`                                                         |
| Name, site URL, features                     | `_config.yml`                                                                         |

## Turning more sections on later

The blog, projects, teaching and repositories pages exist but are hidden. Set `nav: true` in the corresponding `_pages/*.md` file and add content to `_posts/`, `_projects/` or `_teachings/`.

## Custom domain

Add a `CNAME` file with your domain, configure DNS per the [GitHub Pages docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site), and update `url` in `_config.yml`.

## Local preview (optional)

With Docker Desktop: `docker compose pull && docker compose up`, then open <http://localhost:8080>.
Otherwise just push and check the live site.

Theme docs: [al-folio](https://github.com/alshedivat/al-folio/tree/main/docs).
