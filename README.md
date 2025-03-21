# Skeleton for Documentation Project

## Dependencies
* Python >=3.10
* Python package manager: [uv](https://docs.astral.sh/uv/)

## How to use

To create a new documentation project using this skeleton, do the following:


### 1. Create new repository

Create a repository from this template. This is guided in the [GitHub Docs](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template).


### 2. Clone locally and set up Python Env

You need to have Python (`3.10` or newer) installed. You also need to have [uv](https://docs.astral.sh/uv/) installed.
```bash
# Clone
git clone 'new-repo-url'

# Change directory
cd 'new-repo-name'

# Let uv create the virtual environment
# and build and serve the site. Close with CTRL+C when done.
uv run mkdocs serve --open
```


### 3. Define the siteinfo.json

The `siteinfo.json` should follow the Pydantic Schema from [gh:sourander/doc-flesh/src/doc_flesh/models/models.py](https://github.com/sourander/doc-flesh/blob/main/src/doc_flesh/models/models.py).

```
class SiteCategory(str, Enum):
    pass

class SiteInfo(BaseModel):
    # MkDocs
    site_name: str
    site_uses_mathjax: bool = False
    ...
    # sourander.github.io
    category: SiteCategory
    related_repo: str = ""
```

See the local `siteinfo.json` for an example of the actual implementation.


### 4. Add the flesh

Note that this flesh is brought in typically using [doc-flesh](https://github.com/sourander/doc-flesh) tool, like this:

```
cd ~/Code/something/
git clone https://github.com/sourander/doc-flesh
cd doc-flesh

# Add the new repo to your doc-flesh config
code -n ~/.config/doc-flesh/config.yaml

# Run
uv run doc-flesh sync
```

For more information, check the [doc-flesh](https://github.com/sourander/doc-flesh) repository.


### 5. Modify content

Modify the contents of `docs/`. User `.nav.yml` files if you need other than `[a-z]` ordering for your MarkDown files or, say, a navigation item that contains special characters (e.g. `TCP/IP`) or custom capitalization (e.g. `LaTeX`). For more information, check the [Awesome Nav for MkDocs](https://lukasgeiter.github.io/mkdocs-awesome-nav/) documentation.

**File naming:** Use only typical ASCII characters (`[A-Za-z0-9_-]`).


## 6. Run local build

To build the project locally to `site/` and to run a web server, you can simply run `uv run mkdocs serve --open`. This will open your default browser at the site (`http://localhost:8080`).


### 7. Build in GitHub Pages

Merge to `main` branch in any Repository. The scripts at `.github/workflows/` will be executed by Github Actions.

Sadly, GitHub will not automatically publish your Pages as could be expected. You need to visit the **Settings | 
Pages** (at `https://github.com/<username>/<reponame>/settings/pages`). There, under heading **Build and 
deployment**, choose Branch as `gh-pages` and path as `/ (root)`. Click Save. From now on, your Pages should be 
updated whenever you push to main. You should see a workflow with a title *pages build and deployment* in your 
Actions after each push.


## Batteries Included?

This template comes with one plugins:
* [Awesome Nav for MkDocs](https://lukasgeiter.github.io/mkdocs-awesome-nav/) for page ordering


## Need support for multilanguage?

For this, you need to install new plugin:

* [MkDocs static i18n](https://github.com/ultrabug/mkdocs-static-i18n) for multilanguage support

Using `uv`, you would add it like this:

```sh
uv add mkdocs-static-i18n
```

Add the following to the `mkdocs.yml` file:

```yaml
plugins:
  - i18n:
      docs_structure: suffix
      default_language: en
      languages:
        en:
          name: English
          build: true
        fi:
          name: Finnish
          build: true
      # You can translate navigation items here if need be
      nav_translations:
        fi:
          Some Headline: Jokin otsikko
```

**NOTE:** You will need to modify the `.pages` files if you are using both Awesome Pages and i18n together. Example below.

```yaml
nav:
    - index.md         # Without i18n
    - ... | index*.md  # With i18n
```

## How to access

The URI for the GitHub Pages is `https://<username>.github.io/<repo_name>/`. The *pages build and deployment* 
workflow will output a link to this page.

## How to squash history

Let's say you have started working on a repository created using this template repo. In the beginning, your repo has been Private, and now you want to make it Public. You want to make sure there is nothing in the history that would, say, violate copyrights or include passphrases. To do this, you could squash all the commits into one. First, make sure you have committed your changes to origin **and have backed up your project**. You may lose your work if you screw up. You have been warned. To do this, do:

```sh
# Create a new orphan branch named 'new-main' based on the 'main' branch.
# An orphan branch is a new branch that has no commit history from the source branch.
git checkout --orphan new-main main

# Create a new initial commit for the orphan branch, providing a commit message.
# This commit serves as the starting point for your squashed commit history.
git commit -m "Squashed all commits"

# Overwrite the reference of the 'main' branch with the new orphan branch,
# effectively replacing the old history with the new commit you just created.
git branch -M new-main main

# Forcefully push the changes to the remote repository.
# This overwrites the remote 'main' branch with your new history.
git push --force
```

If you have the project cloned on other machines, they will need to either remove the directory and clone the project again, OR, run the following commands:

```sh
git fetch origin
git reset --hard origin/main
```