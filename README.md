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

Sadly, GitHub will not automatically publish your Pages as could be expected. You need to visit the **Settings | 
Pages** (at `https://github.com/<username>/<reponame>/settings/pages`). There, under heading **Build and 
deployment**, choose Branch as `gh-pages` and path as `/ (root)`. Click Save. From now on, your Pages should be 
updated whenever you push to master. You should see a workflow with a title *pages build and deployment* in your 
Actions after each push.

## How to access

The URI for the GitHub Pages is `https://<username>.github.io/<repo_name>/`. The *pages build and deployment* 
workflow will output a link to this page.