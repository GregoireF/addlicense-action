# addlicense-action

> GitHub Action — add, check, update and remove SPDX license headers.

[![CI](https://github.com/GregoireF/addlicense-action/actions/workflows/ci.yml/badge.svg)](https://github.com/GregoireF/addlicense-action/actions/workflows/ci.yml)
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

### Add headers with a config file

Create `.addlicenserc.yaml` at the repo root:

```yaml
license: MIT
copyright: "Acme Corp"
ignore:
  - "*.md"
  - "*.txt"
```

Then simply:

```yaml
- uses: GregoireF/addlicense-action@v1
  with:
    args: .
```

---

## Inputs

| Input | Default | Description |
|---|---|---|
| `args` | `--check .` | Arguments passed directly to `addlicense`. See [CLI reference](https://github.com/GregoireF/addlicense#flags). |
| `version` | *(action tag)* | Override the binary version (e.g. `v1.2.0`). Defaults to the action tag, so `@v1.2.0` always uses the `v1.2.0` binary. |

---

## Supported platforms

| OS | amd64 | arm64 |
|---|---|---|
| Linux | ✓ | ✓ |
| macOS | ✓ | ✓ |
| Windows | ✓ | ✓ |

---

## Versioning

Pin to a major version (`@v1`) to receive bug fixes automatically, or to an exact version (`@v1.2.0`) for reproducible builds. This action is versioned alongside [addlicense](https://github.com/GregoireF/addlicense) — `addlicense-action@v1.2.0` uses the `addlicense` v1.2.0 binary. Releases are triggered automatically when the core CLI publishes a new version.

---

## License

MIT — see [LICENSE](LICENSE).
