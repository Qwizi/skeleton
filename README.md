# skeleton
[![Poetry](https://img.shields.io/endpoint?url=https://python-poetry.org/badge/v0.json)](https://python-poetry.org/)
[![Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json)](https://github.com/astral-sh/ruff)

My [copier](https://github.com/copier-org/copier) Python project template.

# Motivation
I was inspired by https://blog.jaraco.com/skeleton.

The goal of this project is to provide a skeleton for my Python projects,
simultaneously trying to take on the following [jaraco/skeleton](https://github.com/jaraco/skeleton) challenges:
- Solve the [History is Forever](https://blog.jaraco.com/skeleton/#history-is-forever) problem.
  - [x] The true history is not obscured.
  - [ ] Existing histories are not broken until the handoff commit is pulled.
  - [ ] Attribution is not lost.
- Solve the [Continuous Integration Mismatch](https://blog.jaraco.com/skeleton/#continuous-integration-mismatch) problem.
  - [x] Downstream projects and the skeleton itself can have different CI configurations.
- Solve the [Commit Integrations Mismatch](https://blog.jaraco.com/skeleton/#commit-integrations-mismatch) problem.
  - [x] Downstream projects and the skeleton itself can reference different issues and pull requests in their commit histories.

Because the project does not copy the whole history from skeleton, many of the problems are solved by design.

# How to use it
You might use this template or fork it and modify it to your needs.

## Configure [GitHub CLI](https://cli.github.com/)

```shell
gh auth login
```

Ensure the `workflow` scope is in your authorized scopes:

```shell
gh auth refresh -h github.com -s workflow
```

## Install [Redis](https://github.com/redis/redis#readme), [pipx](https://github.com/pypa/pipx#readme) and [Copier](https://github.com/copier-org/copier#readme)

```shell
sudo apt install pipx redis
pipx install copier
pipx inject copier copier-templates-extensions
SKELETON=gh:bswck/skeleton
```

## Create a new project
1.  Make sure that you trust me.
1.  Run the following command:

    ```shell
    copier copy --trust --vcs-ref HEAD "$SKELETON" path/to/project
    ```

1.  Answer the questions.
1.  Change directory to your project:

    ```shell
    cd path/to/project
    ```

1. Happy coding!
Your repository is on GitHub and has:
- a release maker (`$ poe release`),
- skeleton tool (`$ poe skeleton [upgrade|patch]`),
- aesthetic badges in README.md,
- an auto-generated LICENSE file,
- a pre-configured `pyproject.toml` file,
- pre-configured [towncrier](https://github.com/twisted/towncrier#readme) tasks for changelog generation (`$ poe [added|changed|deprecated|removed|fixed|security]`),
- a ready-to-use [Poetry](https://python-poetry.org/) virtual environment with all the necessary dev dependencies installed, including [poethepoet](https://github.com/nat-n/poethepoet#readme), [pre-commit](https://pre-commit.com/),
[mypy](https://github.com/python/mypy#readme), [Ruff](https://github.com/astral-sh/ruff#readme), etc.
- a pre-configured CI suite for GitHub Actions (including coverage report) and pre-commit.

## Incorporate to an existing project
Almost the same as above.

1.  Change directory to your project:

    ```shell
    cd path/to/project
    ```

1.  Run the following command:

    ```shell
    copier copy --trust --vcs-ref HEAD "$SKELETON" .
    ```

1.  Answer the questions.
1.  Allow copier to overwrite all files.
1.  Patch your files (changes were locally reverted for your convenience).
    Be sure that the codebase is not lost but files maintained by skeleton are updated.
1.  Run the following command:

    ```shell
    poe skeleton upgrade
    ```

1.  Happy coding!


## Bump the version of skeleton in your project

```shell
poe skeleton upgrade
```

Or, for a specific [ref](https://www.atlassian.com/git/tutorials/refs-and-the-reflog):

```shell
poe skeleton upgrade 1.0.0  # Upgrade to bswck/skeleton@1.0.0.
poe skeleton upgrade dev  # Upgrade to the latest commit on the dev branch.
```

## Reconfigure the skeleton
```shell
poe skeleton patch
```

# How to develop

1.  Install [Poetry](https://python-poetry.org/) and project dependencies

    ```shell
    sudo apt install pipx  # If you don't have pipx installed yet.
    pipx install poetry
    poetry install
    ```
1.  Install [pre-commit](https://pre-commit.com/) hooks

    ```shell
    pre-commit install --hook-type pre-commit --hook-type pre-push
    ```

1.  Test your skeleton

    ```shell
    ctt
    ```

# License
This project is licensed under the terms of the [MIT License](/LICENSE).

# Credits
[@jpsca](https://github.com/jpsca), for creating Copier.</br>
[@pawamoy](https://github.com/pawamoy), for creating a sample poetry project template.<br/>
[@jaraco](https://github.com/jaraco), for inspiring me to create my own skeleton, like [the one he has](https://github.com/jaraco/skeleton).

[Read more about copier.](https://copier.readthedocs.io/en/stable/)<br/>
[Read more about jaraco/skeleton.](https://blog.jaraco.com/skeleton)

(C) 2023–present Bartosz Sławecki ([@bswck](https://github.com/bswck)).

