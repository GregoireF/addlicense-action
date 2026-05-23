# Changelog

## [Unreleased]

## v1.0.0 — 2026-05-22
Initial release. Wraps [addlicense v1.0.0](https://github.com/GregoireF/addlicense/releases/tag/v1.0.0).

- Composite action — no Docker, no Go required
- Supports Linux, macOS, Windows (amd64 + arm64)
- Version pinned via action tag (`uses: GregoireF/addlicense-action@v1.0.0`)
- `args` input passes flags directly to the CLI
- `version` input overrides binary version when testing from a branch
