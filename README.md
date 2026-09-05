# sahidvelji.com

[www.sahidvelji.com](https://www.sahidvelji.com) — a simple personal web page,
built with [Hugo](https://gohugo.io) and the
[PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme, deployed to
GitHub Pages by GitHub Actions.

## Local development

Tool versions come from `mise.toml`, which is also what CI installs, so a local
run matches the build exactly.

```sh
mise install
mise exec -- hugo server   # http://localhost:1313
```

Lint the workflows the same way CI does:

```sh
mise exec -- zizmor .github/workflows/
```

## Notes

The theme is a git submodule, so clone with `--recurse-submodules`. PaperMod
publishes no releases, so the submodule tracks a commit on `master`; Renovate
raises those bumps as PRs rather than merging them, since a green build proves
the templates compile but not that the page still looks right.

The domain is configured in three places, and all three have to agree:

- `baseURL` in `config.yml`
- `static/CNAME`
- the custom domain in the repository's Pages settings
