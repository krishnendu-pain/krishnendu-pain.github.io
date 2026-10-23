# CLAUDE.md

Krishnendu Pain's academic homepage, built from the [al-folio](https://github.com/alshedivat/al-folio) v1 template.

- Live site: <https://krishnendu-pain.github.io>
- Repo: `krishnendu-pain/krishnendu-pain.github.io` (public user site, created 2026-10-23 with "Use this template")
- Goal: a **minimal** site with only about, publications and CV in the navbar. More sections may be turned on later.

> **Rule (from the user): every time you change this site, update this file in the same commit.** Keep the "What has been customized" table, the "Change log" and the "Still to do" list accurate.

For al-folio internals (gem-owned layouts, which paths must not be created, plugin wiring), see `AGENTS.md` and `docs/`. **Ignore the `/al-folio` baseurl advice in those files.** It applies to the upstream template repo. This site is a user site, so `baseurl` is empty.

## Deployment

- Pushing to `main` runs the **Deploy site** Action (`.github/workflows/deploy.yml`). It runs `jekyll build` and publishes `_site` to the **`gh-pages`** branch, which GitHub Pages serves.
- Repo settings already in place: Pages source is `gh-pages` / root, and Actions have read/write workflow permissions.
- `deploy.yml` only triggers on certain paths and skips `README.md`. To deploy anyway, run `gh workflow run deploy.yml -R krishnendu-pain/krishnendu-pain.github.io --ref main`.
- A bot ("Auto update markdown TOC") sometimes commits to `main`. Run `git pull --rebase` before pushing.
- After a deploy, Pages may need a nudge: `gh api -X POST repos/krishnendu-pain/krishnendu-pain.github.io/pages/builds`.
- The local `gh` token has no `workflow` scope, so edits to `.github/workflows/*` can't be pushed from here. Make them in the GitHub web UI or refresh the scope (`gh auth refresh -s workflow`).
- One build stalled on a slow Ubuntu apt mirror while installing ImageMagick. If a deploy hangs in "Install and Build", cancel it and re-run it.
- A normal build takes about 2–5 minutes. Prettier CI (`prettier.yml`) checks formatting with `printWidth: 150`. To fix a file, run `npx -p prettier@3 prettier --no-config --print-width 150 --trailing-comma es5 --write <file>`.

## Local environment (Windows)

- `git`, `gh` and `npx` are on the PowerShell PATH but **not** on the Git-Bash PATH. Use PowerShell or the full paths (`/c/Program Files/Git/cmd/git.exe`, `/c/Program Files/GitHub CLI/gh.exe`).
- Ruby and Docker are not installed, so there's no local Jekyll preview. Verify on the live site instead.
- Commit identity (repo-local): `Krishnendu Pain <76436487+krishnendu-pain@users.noreply.github.com>`.

## What has been customized

| File                                                                | State                                                                                                                                                                                                                                                                                                                                                                                              |
| ------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `_config.yml`                                                       | Name Krishnendu Pain, `url: https://krishnendu-pain.github.io`, empty `baseurl`, favicon 📚, `last_updated: true`, Disqus off, `external_sources: []`, scholar `last_name: [Pain]` / `first_name: [Krishnendu, K.]`                                                                                                                                                                                |
| `_pages/about.md`                                                   | Home page. Subtitle, bio and Research Interests are **placeholders** (`TODO`, `<...>`). The bio ends with the line "You can find my [CV](…) here.", where "CV" links to `/assets/pdf/cv.pdf`. **Keep this line** when the bio is rewritten. `profile.image` is empty until a real photo exists (the template's `assets/img/prof_pic.jpg` is Einstein, so don't use it). News on; latest posts off. |
| `_pages/cv.md`                                                      | **PDF only.** `layout: page` (not `layout: cv`) with a "Download CV (PDF)" link and an embedded `<object>` showing `assets/pdf/cv.pdf`. There's no YAML/rendercv CV, and the user doesn't want one.                                                                                                                                                                                                |
| `assets/pdf/cv.pdf`                                                 | The user's real CV PDF (added 2026-10-23). To update the CV, replace this file.                                                                                                                                                                                                                                                                                                                    |
| `_data/socials.yml`                                                 | `github_username: krishnendu-pain`. **No `cv_pdf` key**: the user doesn't want a CV icon among the social links. Email, Scholar, ORCID and LinkedIn are commented-out TODOs.                                                                                                                                                                                                                       |
| `_bibliography/papers.bib`                                          | No papers yet. It contains only an `@comment{}` block with an example entry. Don't put example entries behind `%`, because bibtex-ruby still parses `@...` after a `%`.                                                                                                                                                                                                                            |
| `_news/website_launch.md`                                           | The only news item                                                                                                                                                                                                                                                                                                                                                                                 |
| `_data/{coauthors,venues,repositories,citations}.yml`               | Reset to empty templates                                                                                                                                                                                                                                                                                                                                                                           |
| `_pages/{blog,projects,teaching,repositories,dropdown,profiles}.md` | `nav: false` (hidden but kept)                                                                                                                                                                                                                                                                                                                                                                     |
| `README.md`                                                         | Short guide to editing the site                                                                                                                                                                                                                                                                                                                                                                    |

Removed demo content: `_posts/`, `_projects/`, `_teachings/`, `_books/`, the demo `_news/`, `assets/pdf/example_pdf.pdf`, `assets/img/publication_preview/`, `assets/img/book_covers/`. Re-create these folders when the user wants those sections.

`_data/cv.yml` was deleted, because the CV page is PDF-only.

## Disabled on GitHub

- `render-cv.yml` (renders a PDF from `_data/cv.yml` and commits it) is **disabled** and should stay disabled. `_data/cv.yml` no longer exists, and the workflow's output could overwrite the hand-made `cv.pdf`.

## Still to do (waiting on the user)

- Bio, affiliation, advisor and research interests in `_pages/about.md`
- Profile photo, saved as `assets/img/prof_pic.jpg`, then set `profile.image: prof_pic.jpg`
- Papers in `papers.bib` (add `selected = {true}` to show a paper on the home page; PDFs go in `assets/pdf/`)
- Email, Google Scholar, ORCID and LinkedIn in `_data/socials.yml`
- Optional later: custom domain (add a `CNAME` file and update `url`), turning on the blog or projects

## Change log

- **2026-10-23:** Created the repo from the al-folio template. Personalized `_config.yml`, replaced demo content with placeholders, hid extra nav pages, and switched Pages to `gh-pages`.
- **2026-10-23:** Added the user's `assets/pdf/cv.pdf` and wrote this file.
- **2026-10-23:** Made the CV page PDF-only (`layout: page` with an embedded PDF) and deleted `_data/cv.yml`. Removed the CV icon from the social links and added "You can find my CV here." to the bio.
