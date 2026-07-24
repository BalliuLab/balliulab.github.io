# CLAUDE.md — Balliu Lab @ UCLA website

Source for the lab website, live at <https://balliulab.github.io> (public org repo `BalliuLab/balliulab.github.io`).

The site moved here from `brunildaballiu.github.io`, which is now just a redirect to this URL. Push site changes to the **`balliulab`** remote (`git@github.com:BalliuLab/balliulab.github.io.git`), not to `origin` (origin is the old redirect repo).

## Architecture
- **Static, no build step.** `index.html` is the entire site: markup, an inline `<style>`, and a small `<script>`.
- **Multi-page via a tiny client-side router.** Each page is a `<div class="page" data-page="X">`; nav links carry `data-target="X"`. The script shows one page at a time and marks the active nav link. Pages: home, research, people, publications, software, news, join, contact.
- **GitHub Pages serves the files directly** because a `.nojekyll` file disables the Jekyll build. It deploys from the `main` branch, root.
- `media/` holds all images (research figures and member photos).

## Making changes
1. Edit `index.html` (and drop any new images into `media/`).
2. Commit to `main` and push to `balliulab`. GitHub Pages republishes in about one to two minutes.
3. Verify at <https://balliulab.github.io>. This is the LIVE site, so pushes are public immediately.

## Reading Competition page
The `reading` page shows a leaderboard (papers read per person) and a "papers we are reading" list, fed live from a public Google Sheet (one row per paper: Name, Paper, Link, Date). The page fetches the sheet's gviz CSV endpoint at load, so standings update when the sheet is edited, no code push needed. The sheet URL is the `SHEET` constant in the reading page's script.

## Conventions
- **Writing style:** no dashes (em, en, or a spaced hyphen) and no semicolons in visible copy. Use commas, periods, parentheses, or "and".
- **Dates:** use months, not academic quarters. Convert Fall to October, Winter to January, Spring to April.
- **Member bios:** third person, name-based. Do not assume pronouns. Use a person's stated pronouns only if they provide them in their own write-up.
- **Emphasis:** feature work the lab led, and keep it about the science.
- **Emails:** never hard-code an address in the HTML. Use `<a class="eml" data-u="user" data-d="domain">`; the script assembles the mailto at runtime so scrapers do not see it.
- **Headshots:** circular, and auto cross-fade between a "now" and a "then" photo. Add `name_now` and `name_then` images to `media/`. A member without a photo gets an initials placeholder: `<span class="headshot placeholder">XY</span>`.

## Content sources (in the user's Box, not in this repo)
- Member photos and bios: `Box/BalliuLab/LabWebsite/` (images plus `Introduction.docx`).
- Member join dates: `Box/BalliuLab/Personnel Contact List.xlsx`.

## Rollback
The previous AcademicPages site is preserved on the `backup-academicpages` branch:

    git push origin backup-academicpages:main --force
