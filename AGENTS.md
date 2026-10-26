# sahidvelji.com

A one-page personal site built with Hugo and the PaperMod theme,
deployed to GitHub Pages.
See `README.md` for the user-facing workflow.

Tool versions live in `mise.toml` and `mise.lock`;
run everything through the mise tasks
(`mise tasks` lists them) rather than calling `hugo` or the linters directly.
`mise run smoke` builds the site
and asserts the page still renders what it should,
so extend its patterns when the page gains something worth guarding.

The theme is a git submodule under `themes/PaperMod`.
Change the site through `config.yml`, `static/` and `archetypes/`,
never by editing the theme.
The domain lives in `config.yml`, `static/CNAME`
and the repository's Pages settings, which must agree.

## Linting

The pre-commit hook runs `hk.pkl`'s linters and formatters on staged files,
so a commit may restage reformatted files or fail on a lint error.
Fix the cause rather than skipping the hook with `HK=0` or `--no-verify`.
The commit-msg hook rejects messages that are not conventional commits.

## Git

Changes go through pull requests against `main`;
the `build` check must pass before one can merge.
Renovate opens pull requests for tool, action and theme bumps
and automerges minor and patch updates;
major updates and theme bumps wait for review.
