# Contributing

Applies to every Pequi-RCSS3D repository unless it has its own CONTRIBUTING.md.

1. Set up once: `uv sync && uv run pre-commit install`.
2. Branch from `main` and open a pull request. Only administrators push to `main` directly.
3. Write commit messages and PR titles as [Conventional Commits](https://www.conventionalcommits.org/),
   in English, e.g. `feat(skills): add walk reward`. A commit message is that one line only: no
   body, no trailers such as `Co-Authored-By`. Details go in the PR description.
4. Merging needs green CI and one approval (or an admin override). PRs are squash-merged with the
   title as the whole commit message.

The hooks run the checks on each commit. Run them all with `uv run pre-commit run --all-files`,
and run tests with `uv run pytest`.

Never commit data, checkpoints or secrets. Keep data in `data/` and outputs in `runs/`, both
git-ignored.
