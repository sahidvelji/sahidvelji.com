# sahidvelji.com

[sahidvelji.com](https://sahidvelji.com) — a simple personal web page,
built with [Hugo](https://gohugo.io) and the
[PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme, deployed to
GitHub Pages by GitHub Actions.

## Local development

Tool versions come from `mise.toml` and are locked to exact artifacts in
`mise.lock`, which is also what CI installs, so a local run matches the build
exactly.

```sh
mise install
mise run dev     # serve on localhost:1313, drafts included
mise run build   # build into public/
mise run smoke   # build, then assert the page rendered what it should
mise run lint    # run every linter in hk.pkl
mise run fix     # apply every available fix
```

CI runs those same tasks rather than its own copies of the commands, so
anything that passes locally passes there.

[hk](https://hk.jdx.dev) lints and formats each commit and checks that its
message is a conventional commit. `hk.pkl` lists the steps; tool settings sit
beside it (`.editorconfig`, `biome.json`, `ryl.toml`, `tombi.toml`,
`.github/jactionlint.yaml`). Run `hk install` once to set up the git hooks,
unless global git hooks already run hk.

## Notes

The theme is a git submodule, so clone with `--recurse-submodules`. PaperMod
publishes no releases, so the submodule tracks a commit on `master`; Renovate
raises those bumps as PRs rather than merging them, since a green build proves
the templates compile but not that the page still looks right.

The domain is configured in three places, and all three have to agree:

- `baseURL` in `config.yml`
- `static/CNAME`
- the custom domain in the repository's Pages settings
