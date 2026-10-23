# krishnendu-pain.github.io

Academic homepage of Krishnendu Pain, built with [al-folio](https://github.com/alshedivat/al-folio) and hosted on GitHub Pages at <https://krishnendu-pain.github.io>.

Every push to `main` triggers the **Deploy site** GitHub Action, which builds the site and publishes it to the `gh-pages` branch (takes ~3–5 min).

## Where things live

| What                         | File                                                                             |
| ---------------------------- | -------------------------------------------------------------------------------- |
| Bio, affiliation, interests  | `_pages/about.md`                                                                |
| Profile photo                | `assets/img/prof_pic.jpg`, then set `profile.image` in `about.md`                |
| Papers                       | `_bibliography/papers.bib` (`selected = {true}` → shown on home page)            |
| Paper PDFs                   | `assets/pdf/`                                                                    |
| CV (web version)             | `_data/cv.yml`                                                                   |
| CV (PDF)                     | `assets/pdf/cv.pdf`, then set `cv_pdf` in `_pages/cv.md` and `_data/socials.yml` |
| Email / Scholar / ORCID etc. | `_data/socials.yml`                                                              |
| News items                   | one file per item in `_news/`                                                    |
| Name, site URL, features     | `_config.yml`                                                                    |

## Turning more sections on later

The blog, projects, teaching and repositories pages exist but are hidden. Set `nav: true` in the corresponding `_pages/*.md` file and add content to `_posts/`, `_projects/` or `_teachings/`.

## Custom domain

Add a `CNAME` file with your domain, configure DNS per the [GitHub Pages docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site), and update `url` in `_config.yml`.

## Local preview (optional)

With Docker Desktop: `docker compose pull && docker compose up`, then open <http://localhost:8080>.
Otherwise just push and check the live site.

Theme docs: [al-folio](https://github.com/alshedivat/al-folio/tree/main/docs).
