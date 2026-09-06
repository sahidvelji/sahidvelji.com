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
mise run lint    # audit the GitHub Actions workflows with zizmor
```

CI runs those same tasks rather than its own copies of the commands, so
anything that passes locally passes there.

## Notes

The theme is a git submodule, so clone with `--recurse-submodules`. PaperMod
publishes no releases, so the submodule tracks a commit on `master`; Renovate
raises those bumps as PRs rather than merging them, since a green build proves
the templates compile but not that the page still looks right.

The domain is configured in three places, and all three have to agree:

- `baseURL` in `config.yml`
- `static/CNAME`
- the custom domain in the repository's Pages settings
