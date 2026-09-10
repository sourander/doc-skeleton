# Welcome to Doc Skeleton

This repository is a template for creating course documentation with Zensical and GitHub Pages.

## Create a course repository

1. Navigate to Github. Link in the top-right corner of this page.
2. Select **Use this template** on GitHub.
3. Create and name the new course repository.
4. Read the `HOW-TO-SKELETON.md` for further instruction  

!!! tip "What is skeleton?"

    A skeleton is a centralised way to keep multiple repositories up to date. It is used by the creator of this repository, but anyone can use it if there is a need to sync certain files across multiple repositories. Examples files one would want to maintain in cross-repository pattern are:

    - `README.md` (or other documentation files)
    - `LICENSE` (or other legal files)
    - `zensical.toml` (or other configuration files)
    - `AGENTS.md` (or other AI-related files)
    - `.github/workflows` (or other GitHub Actions workflow files)

## Local preview

```bash
uv run zensical serve
```

The site updates automatically on file changes (e.x. saving a file).
