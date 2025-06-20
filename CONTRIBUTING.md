# Contributing to the KMTC Unified Testing Framework

First off, thank you for considering contributing! We welcome contributions from everyone and hope to create a community that is encouraging, supportive, and collaborative.

This document outlines our contribution process, from setting up your development environment to submitting your first pull request. Following these guidelines helps us manage the project efficiently and maintain a high standard of quality.

Please read our [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) to understand the expectations for participating in our community. 

## Our Governance Model

The KMTC project operates under a lightweight governance model to ensure agility while welcoming community input.
* **Core Team & BDFL:** The project is led by a small core team of maintainers and a lead architect who acts as the Benevolent Dictator For Life (BDFL). The BDFL has the final say in technical disputes but will always seek consensus with the core team. This model is documented to ensure contributors understand how decisions are made.
* **Open Communication:** We encourage open discussions for design proposals and feature requests. Please use the repository's "Issues" tab to start a discussion.

## Setting Up Your Development Environment

Our project uses [Poetry](https://python-poetry.org/) to manage dependencies and virtual environments.

1.  **Fork the Repository:** Start by forking the `kmtc-testing` repository to your own GitHub account.
2.  **Clone Your Fork:** Clone your fork to your local machine:
    ```bash
    git clone https://github.com/redhat-vmeperf/kmtc-testing.git
    cd kmtc-testing
    ```
3.  **Install Dependencies:** We use Poetry to manage all project dependencies. This single command will create a virtual environment and install all runtime and development packages.
    ```bash
    poetry install
    ```
4.  **Activate Virtual Environment:** Activate the Poetry-managed virtual environment.
    ```bash
    poetry shell
    ```

## Our Development Process

We follow a simplified GitHub Flow process and use Conventional Commits for our commit messages. 

1.  **Branching:** Create a new, descriptive branch from the `main` branch for any new feature or fix. [cite_start]Please follow our branch naming conventions:
    * `feature/<short-description>`
    * `bugfix/<issue-id-or-description>`
    * `chore/<description>`
    * `docs/<description>`

2.  **Coding Standards:** All code MUST adhere to our `CODING_STANDARD.md` file. Before committing, please run our quality assurance tools locally to ensure your code meets our standards:
    ```bash
    # Auto-format your code
    poetry run black .

    # Sort your imports
    poetry run isort .

    # Check for linting errors (aim for zero)
    poetry run flake8 .

    # Run static type checks (aim for zero errors)
    poetry run mypy .
    ```
    *We also provide a pre-commit configuration that you can optionally install to run these checks automatically before each commit. *

3.  **Testing:** All new features and bug fixes MUST be accompanied by comprehensive tests using `pytest`. You can run the full test suite locally with:
    ```bash
    poetry run pytest
    ```
4.  **Committing:** We follow the [Conventional Commits](https://www.conventionalcommits.org/) specification. Your commit messages should be in the format `<type>: <description>`.
    * Example: `feat: add new helper for config parsing`
    * Example: `fix(core): resolve issue in logging utility`

### Security Pre-Commit Hooks (Mandatory)

To ensure we prevent secrets and common issues from being committed to the repository, this project uses mandatory security hooks provided by Red Hat Infosec. These are managed via the `pre-commit` framework.

After running `poetry install`, you must install the git hooks into your local clone:

```bash
poetry run pre-commit install
```

Once installed, these hooks will run automatically every time you make a `git commit`. If a hook identifies an issue (like a potential secret), the commit will be aborted, allowing you to fix it before committing again.



## Submitting a Pull Request

When you are ready to submit your contribution, please follow these steps:

1.  **Open a Pull Request (PR):** Push your branch to your fork and open a pull request against the `main` branch of the `kmtc-testing` repository.
2.  **Fill out the PR Template:** Use the provided PR template to clearly describe the "what" and "why" of your changes. Link to any relevant issues. You MUST also label your PR with an urgency/priority level (`P0` through `P3`).
3.  **Sign Off All Commits:** All commits must be signed off to indicate agreement with the Developer Certificate of Origin (DCO).
4.  **Pass CI Checks:** All automated checks (linting, testing, security scans) must pass.
5.  **Code Review:** At least one member of the core team MUST review and approve your PR before it can be merged. The core team is listed in the `CODEOWNERS` file. Please be patient and responsive during the review process.


## Developer Certificate of Origin (DCO)

To ensure a clear chain of ownership for all contributions, this project requires that every commit be signed off with the Developer Certificate of Origin (DCO).

The DCO is a legally binding statement that asserts you are the creator of your contribution, or that you have the rights to submit it under our open-source license. It is a lightweight alternative to a formal CLA. You can read the full text here: [https://developercertificate.org/](httpss://developercertificate.org/).

### How to Sign Off Your Commits

You must add a `Signed-off-by` line to every one of your git commit messages.

The easiest way to do this is to use the `-s` or `--signoff` flag with `git commit`:

```bash
git commit -s -m "feat: add new feature that does something"
```

This will automatically append a line to your commit message that looks like this:

```
Signed-off-by: Your Name <your.email@example.com>
```
Please use your real name and a valid email address. If you have already made commits without signing off, you will need to amend your commits before you can open a pull request. You can do this with the following command:
```
git rebase --signoff HEAD~N
```
(Replace `N` with the number of commits you need to amend).
