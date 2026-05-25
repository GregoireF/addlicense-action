# addlicense-action

> GitHub Action — add, check, update and remove SPDX license headers.

[![CI](https://github.com/GregoireF/addlicense-action/actions/workflows/ci.yml/badge.svg)](https://github.com/GregoireF/addlicense-action/actions/workflows/ci.yml)
[![GitHub release](https://img.shields.io/github/v/release/GregoireF/addlicense-action?label=release)](https://github.com/GregoireF/addlicense-action/releases/latest)
[![GitHub Marketplace](https://img.shields.io/badge/Marketplace-addlicense-blue?logo=github)](https://github.com/marketplace/actions/addlicense)
[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/GregoireF/addlicense-action/badge)](https://securityscorecards.dev/viewer/?uri=github.com/GregoireF/addlicense-action)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

Wraps [GregoireF/addlicense](https://github.com/GregoireF/addlicense) — the Go CLI — as a GitHub Action. Downloads the correct binary for the runner OS and architecture at runtime; no Docker, no Go required.

---

## Usage

### Enforce headers in CI (recommended)

```yaml
name: License headers
on: [push, pull_request]
jobs:
  check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: GregoireF/addlicense-action@v1
        with:
          args: --check .
```

### Add headers

```yaml
- uses: GregoireF/addlicense-action@v1
  with:
    args: --license MIT --author "Acme Corp" .
```

### With a config file

Create `.addlicenserc.yaml` at the repo root:

```yaml
license: MIT
author: "Acme Corp"
ignore:
  - "*.md"
  - "vendor"
```

Then simply:

```yaml
- uses: GregoireF/addlicense-action@v1
  with:
    args: .
```

### Install only, run manually

```yaml
- uses: GregoireF/addlicense-action@v1
  id: addlicense
  with:
    args: ''   # installs binary without running

- run: addlicense --check --format json . | tee results.json
- run: echo "Installed version ${{ steps.addlicense.outputs.version }}"
```

---

## Inputs

| Input | Default | Description |
|---|---|---|
| `args` | `--check .` | Arguments passed directly to `addlicense`. Pass `''` to install the binary without running it. See [CLI reference](https://github.com/GregoireF/addlicense#flags). |
| `version` | *(action tag)* | Override the binary version (e.g. `v1.2.0`). Defaults to the action tag — `@v1.2.0` always uses the `v1.2.0` binary. Useful when testing the action from a branch with `uses: ./`. |

---

## Outputs

| Output | Description |
|---|---|
| `version` | The resolved version of `addlicense` that was installed (e.g. `v1.0.1`). Useful for logging, caching keys, or conditional steps. |

---

## Supported platforms

| OS | amd64 | arm64 |
|---|---|---|
| Linux | ✓ | ✓ |
| macOS | ✓ | ✓ |
| Windows | ✓ | ✓ |

---

## Versioning

Pin to a major version (`@v1`) to receive bug fixes automatically, or to an exact version (`@v1.2.0`) for reproducible builds.

This action is versioned in sync with [addlicense](https://github.com/GregoireF/addlicense) — `addlicense-action@v1.2.0` always uses the `v1.2.0` binary. Releases are triggered automatically when the core CLI publishes a new version.

---

## Ecosystem

| Package | Description |
|---|---|
| [addlicense](https://github.com/GregoireF/addlicense) | Core CLI — the Go binary |
| **addlicense-action** | This repo — GitHub Action |
| [addlicense-npm](https://github.com/GregoireF/addlicense-npm) | npm package — `@gregoiref/addlicense` |
| [addlicense-winget](https://github.com/GregoireF/addlicense-winget) | WinGet — `winget install GregoireF.addlicense` |
| [homebrew-tap](https://github.com/GregoireF/homebrew-tap) | Homebrew — `brew install GregoireF/tap/addlicense` |

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) and [SECURITY.md](.github/SECURITY.md).

---

## License

MIT — see [LICENSE](LICENSE).
