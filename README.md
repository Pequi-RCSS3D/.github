# Pequi-RCSS3D/.github

Shared defaults for every repository in the organization.

- [CONTRIBUTING.md](CONTRIBUTING.md), the [PR template](.github/pull_request_template.md) and the
  [issue forms](.github/ISSUE_TEMPLATE/) apply to any repo that doesn't define its own.
  GitHub only applies them because this repo is public.
- Reusable workflows in [.github/workflows/](.github/workflows/):
  - `python-ci.yml`: sync with uv, run pre-commit on all files, run pytest.
  - `pr-title.yml`: require Conventional Commit PR titles.

## Using the workflows

```yaml
# .github/workflows/ci.yml
name: CI
on:
  push:
    branches: [main]
  pull_request:
permissions:
  contents: read
concurrency:
  group: ${{ github.workflow }}-${{ github.ref }}
  cancel-in-progress: true
jobs:
  python:
    uses: Pequi-RCSS3D/.github/.github/workflows/python-ci.yml@main
  pr-title:
    if: github.event_name == 'pull_request'
    uses: Pequi-RCSS3D/.github/.github/workflows/pr-title.yml@main
```

Repos track `main`, so a change here reaches every repo's next CI run.
