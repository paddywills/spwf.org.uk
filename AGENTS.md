# Site Update Guide (For Future LLM / Automation Agents)

Purpose: Provide a minimal, reliable, and repeatable process for updating site content (text/pages) for https://spwf.org.uk.

The site is built with MkDocs + Material. Source lives in `docs/`. A GitHub Action (`.github/workflows/deploy.yml`) runs on pushes to `main` and executes `mkdocs gh-deploy --force` to publish to the `gh-pages` branch. GitHub Pages then runs its built-in `pages-build-deployment` job to serve the site. The generated `site/` directory is **ignored** and should not be committed.

---
## Core Principles
- Edit only Markdown in `docs/` (and `mkdocs.yml` if navigation changes).
- Never manually edit or commit files under `site/`.
- Every push to `main` triggers deployment via the workflow (no manual deploy required).
- Keep commits focused and messages clear (imperative style).
- Validate that only intended files changed before committing.

---
## Common Task: Add or Update a Charity
1. Open `docs/charities.md`.
2. Insert or edit a section using the existing pattern (if there is no website, omit the link and add a short italic note like the Borneo Regrow entry):
   ```markdown
   ## Charity Name  
   One-sentence (or short) description.  
   [Learn more →](https://example.org)
   
   ---
   ```
   (Ensure there is a blank line before and after the block; end with `---` except for the final narrative paragraph.)
3. Save the file.
4. Verify diff:
   ```bash
   git status --short
   git diff docs/charities.md
   ```
5. Stage & commit:
   ```bash
   git add docs/charities.md
   git commit -m "Add <CharityName> as supported charity"
   git push origin main
   ```
6. Wait for GitHub Actions deploy (the workflow run plus the `pages-build-deployment` run). The site will update on success.

---
## Adding a New Page
1. Create a new Markdown file under `docs/`, e.g. `docs/impact.md`.
2. Add front content (no front‑matter needed) with a top `#` heading.
3. Update navigation in `mkdocs.yml`:
   ```yaml
   nav:
     - Home: index.md
     - Charities: charities.md
     - Impact: impact.md   # <— new line
     - About Us: about.md
     - Contact: contact.md
   ```
4. Repeat diff / commit / push steps.

---
## Optional: Local Preview (Not Required for Simple Edits)
Only if you need to visually confirm before pushing (use a virtualenv if you prefer):
```bash
python3 -m pip install -r requirements.txt
mkdocs serve
```
Open the provided localhost URL. Stop with Ctrl+C. Do **not** commit the rebuilt `site/` output.

---
## Deployment Summary
- Workflow: `.github/workflows/deploy.yml` runs on push to `main` and calls `mkdocs gh-deploy --force`.
- GitHub Pages: `pages-build-deployment` is a GitHub-managed run that publishes `gh-pages`.
- Output is published to the `gh-pages` branch (served by GitHub Pages).

No manual `mkdocs build` or edits to `gh-pages` are needed.

---
## Do / Do Not
| Do | Do Not |
|----|--------|
| Edit `docs/*.md` | Commit `site/` |
| Update `mkdocs.yml` nav when adding pages | Disable or delete the deploy workflow without replacement |
| Use clear commit messages | Mix unrelated edits in one commit |
| Check `git diff` before commit | Edit generated HTML |

---
## Quick Checklist (Agent)
- [ ] Only intended source files changed
- [ ] Navigation updated if a new page added
- [ ] Commit message clear
- [ ] Pushed to `main`
- [ ] Verified GitHub Actions success (deploy + `pages-build-deployment`)
- [ ] (Optional) Verified the live site

---
## Recovery / Edge Cases
| Situation | Action |
|-----------|--------|
| Wrong content deployed | Re-edit file, new commit, push (latest wins) |
| Deploy fails | Open the Actions log, fix the error, and push again (or re-run the workflow). |
| Need to remove a page | Delete `docs/<file>.md`, remove from `mkdocs.yml`, commit & push. |
| Accidental `site/` commit | Remove directory: `git rm -r site/`, add to `.gitignore` (already should be), commit & push. |

---
## Minimal Commands Recap
```bash
git pull --ff-only
# (edit markdown files)
git add <changed files>
git diff --cached
git commit -m "<meaningful change>"
git push origin main
```

---
## When to Modify Requirements
Only if adding a plugin or theme option not currently installed. Pin versions in `requirements.txt`.

---
## Version / Maintenance
Keep this guide concise. Update it if deployment method or branching model changes.

---
End of guide.
