# Skeleton for Documentation Project

## Dependencies
* Python >=3.10
* Python Poetry

## How to use

To create a new documentation project using this skeleton, run the following commands:
```bash
git clone 'this-repo-url'
poetry install
```

## Run local build

To build the project locally to `site/`, you can simply run `poetry run mkdocs build`

## Build in GitHub Pages

Merge to `master` branch in any Repository. The scripts at `.github/workflows/` will be executed by Github Actions.

## How to access

The URI for the GitHub Pages is `https://<username>.github.io/<repo_name>/`