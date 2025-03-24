# Skeleton for Documentation Project

## How to use

To create a new documentation project using this skeleton, do the following:

### 1. Create new repository

Create a repository from this template. This is guided in the [GitHub Docs](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template).


### 2. Clone locally and set up Python Env

You need to have Python (`3.10` or newer) installed. You also need to have [uv](https://docs.astral.sh/uv/) installed.
```bash
# Clone
git clone 'new-repo-url' && cd 'new-repo-name'

# Test the site locally
uv python install 3.12
uv lock # [--upgrade]
```

### 3. Define the siteinfo.json

The `siteinfo.json` should follow the Pydantic Schema from [gh:sourander/doc-flesh/src/doc_flesh/models/models.py](https://github.com/sourander/doc-flesh/blob/main/src/doc_flesh/models/models.py). You can use the `doc-flesh generate-siteinfo` to create a new file (or append/modify existing).

```bash
# Install
uv tool install git+https://github.com/sourander/doc-flesh

# Run generator (in correct directory)
doc-flesh generate-siteinfo
```

### 4. Commit

Before using the `doc-flesh sync`, you should have a clean state in your repository (as opposite to dirty.) This means that you should commit all your changes before running the `doc-flesh sync`.

```bash
git add .
git commit -m "Initial commit"
git push
```

### 5. Add the flesh

Note that this flesh is brought in typically using [doc-flesh](https://github.com/sourander/doc-flesh) tool, like this:

```bash
# Add the new repo to your doc-flesh config
code -n ~/.config/doc-flesh/config.yaml

# Run
doc-flesh sync
```

For more information, check the [doc-flesh](https://github.com/sourander/doc-flesh) repository.


### 6. Modify content

Modify the contents of `docs/`. Read more at [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) documentation.

Use `.nav.yml` files to define the structure of the site. Read more at [Awesome Nav for MkDocs](https://lukasgeiter.github.io/mkdocs-awesome-nav/) documentation.


## 7. Run local build

To build the project locally to `site/` and to run a web server, you can simply run `uv run mkdocs serve --open`. This will open your default browser at the site (`http://localhost:8080`).


### 8. Build in GitHub Pages

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
# plugins:
#   - search
#   - awesome-pages
     - i18n:
        docs_structure: suffix
        default_language: fi
        languages:
            - locale: fi
            name: Finnish
            build: true
            - locale: en
            default: true
            name: English
            build: true
```

The `.nav.yml` files should not need any modifications due to the `mkdocs-awesome-nav` plugin. It's predecessor, called `mkdocs-awesome-pages-plugin`, required a bit more work. From now on, you can add translations to any files by simply adding a new file into the folder structure, like this:

```sh
.
├── LICENSE.template
├── README.md
├── docs
│   ├── example_dir/
│   │   ├── alpha.md
│   │   └── omega.md
│   ├── extensions.en.md # English version
│   ├── extensions.md
│   ├── images/
│   ├── index.en.md      # English version
│   └── index.md
├── ...
└── uv.lock
```

NOTE! If a file does NOT have a translation, the original file will be used. For example, the `alpha.md` and `omage.md` would display in Finnish whether the language selector has been set to English or Finnish.

## How to access

The URI for the GitHub Pages is `https://<username>.github.io/<repo_name>/`. The *pages build and deployment* workflow will output a link to this page.

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