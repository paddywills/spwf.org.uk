# spwf.org.uk

Source for the Sarah and Patrick Wills Foundation site, built with MkDocs and the Material theme.

## Editing Content

Site content lives in `docs/`.

- Update page content in `docs/*.md`
- Update navigation in `mkdocs.yml`
- Do not commit the generated `site/` directory

The custom domain is kept in `docs/CNAME` so it is included in the built site.

## Local Preview

```zsh
python3 -m pip install -r requirements.txt
python3 -m mkdocs serve
```

Then open the local URL shown by MkDocs, usually `http://127.0.0.1:8000/`.

## Deployment

Deployment is handled by GitHub Actions from `.github/workflows/deploy.yml`.

On every push to `main`, the workflow:

1. Checks out the repo
2. Installs the pinned MkDocs dependencies from `requirements.txt`
3. Runs `mkdocs build`
4. Uploads the generated `site/` directory as a GitHub Pages artifact
5. Deploys that artifact to GitHub Pages with `actions/deploy-pages`

This repository now uses the GitHub Pages workflow-based deployment model rather than `mkdocs gh-deploy` pushing directly to `gh-pages`.

## GitHub Pages Settings

The repository Pages configuration should be set to publish from GitHub Actions.

Current production URL:

- `https://spwf.org.uk/`

## Rollback

If a deployment breaks:

1. Revert the relevant commit on `main`
2. Push the revert
3. Wait for the Pages workflow to publish the previous content

If the workflow itself is broken, fix `.github/workflows/deploy.yml` on `main` and push again.
