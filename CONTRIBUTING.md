# Contributing

Thank you for contributing to `addlicense-action`.

## Workflow

1. **Fork** the repository and create a branch from `main`.
2. Make your changes (see [Development](#development) below).
3. Open a Pull Request against `main` — fill in the PR template.
4. CI must pass on Linux, macOS, and Windows before merge.

## Development

The action is a [composite action](https://docs.github.com/en/actions/creating-actions/creating-a-composite-action) — no build step needed.

```
addlicense-action/
├── action.yml           # composite action definition
├── .addlicenserc.yaml   # addlicense config for this repo
└── .github/
    └── workflows/
        ├── ci.yml           # tests on 3 OS + commitlint
        └── tag-release.yml  # triggered by addlicense core dispatch
```

To test changes locally, point a workflow in another repo at your fork:

```yaml
- uses: your-fork/addlicense-action@your-branch
  with:
    version: v1.0.0   # explicit version required when not on a tag
    args: --check .
```

## Commit conventions

This project uses [Conventional Commits](https://www.conventionalcommits.org/) via `@gregoiref/commitlint-config`.

Allowed scopes: `action`, `ci`, `deps`, `release`, `docs`.

```
feat(action): add --config input to pass a config file path
fix(ci): pin actions/checkout to SHA
chore(deps): bump actions/setup-node
docs(action): add arm64 Windows note to README
```

## Release process

Releases are **fully automated** — do not tag or release manually.

New `addlicense` core releases trigger `tag-release.yml` via `repository_dispatch`,
which updates the CHANGELOG, bumps the version reference in `ci.yml`, creates the
versioned tag, updates the `v{major}` floating tag, and publishes a GitHub release.
