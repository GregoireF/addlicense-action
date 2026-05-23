# addlicense-action

> GitHub Action — add, check, update and remove SPDX license headers.

[![CI](https://github.com/GregoireF/addlicense-action/actions/workflows/ci.yml/badge.svg)](https://github.com/GregoireF/addlicense-action/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

Wraps [GregoireF/addlicense](https://github.com/GregoireF/addlicense) — the Go CLI — as a GitHub Action. Downloads the correct binary for the runner OS and architecture at runtime; no Docker, no Go required.

---

## Usage

```yaml
- uses: GregoireF/addlicense-action@v1.0.0
  with:
    args: --check .
```

### Add headers

```yaml
- uses: GregoireF/addlicense-action@v1.0.0
  with:
    args: --license MIT --author "Acme Corp" .
```

### Enforce in CI (recommended)

```yaml
name: License headers
on: [push, pull_request]
jobs:
  check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: GregoireF/addlicense-action@v1.0.0
        with:
          args: --check .
```

---

## Inputs

| Input | Default | Description |
|---|---|---|
| `args` | `--check .` | Arguments passed directly to `addlicense`. See [CLI reference](https://github.com/GregoireF/addlicense#flags). |
| `version` | *(action tag)* | Override the binary version to download (e.g. `v1.0.0`). Defaults to the action tag so `@v1.0.0` always uses the `v1.0.0` binary. |

---

## Supported platforms

| OS | amd64 | arm64 |
|---|---|---|
| Linux | ✓ | ✓ |
| macOS | ✓ | ✓ |
| Windows | ✓ | ✓ |

---

## Versioning

This action is versioned alongside [addlicense](https://github.com/GregoireF/addlicense). `addlicense-action@v1.1.0` uses the `addlicense` v1.1.0 binary. Releases are triggered automatically when the core CLI publishes a new release.

---

## License

MIT — see [LICENSE](LICENSE).
