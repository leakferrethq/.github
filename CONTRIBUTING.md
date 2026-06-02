# Contributing to leakferret

Thanks for your interest in contributing. leakferret is open source under the
MIT license, and contributions are welcome from **anyone** — you do not need to
be a member of the `leakferrethq` organization. Fork, branch, and open a pull
request.

This file lives in the organization's `.github` repository, so it applies to
every leakferret repository (the engine and all the language wrappers) unless a
repo ships its own `CONTRIBUTING.md`.

## How the repositories fit together

leakferret is one Rust engine plus thin wrappers around it:

- **`leakferret`** — the Rust engine, CLI, and MCP server (the source of truth).
- **`leakferret-ruby` · `leakferret-npm` · `leakferret-go` · `leakferret-action`
  · `leakferret-vscode`** — wrappers that download and shell out to the prebuilt
  binary. They contain no scanning logic of their own.
- **`leakferret-catalog`** — the signed catalog of known-public example
  credentials.

Most detection, classification, verification, and rewrite changes belong in the
engine repo. Wrapper repos handle packaging, install, and per-ecosystem
ergonomics.

## Ways to contribute

- Report a bug or a false positive / false negative with a minimal repro.
- Add or correct a detection pattern, a provider verifier, or a catalog entry.
- Improve docs, examples, or a wrapper's packaging.
- Suggest a feature in an issue before building it, so we can agree on shape.

A false negative (a missed secret) is treated as more serious than a false
positive. When in doubt, err toward flagging.

## Pull request process

1. **Fork** the relevant repo and create a branch off the default branch.
2. Make focused, incremental commits. Keep unrelated changes in separate PRs.
3. Make sure the existing checks pass locally (build, tests, format, lint).
4. Open a PR with a clear description of the problem and the change. Link any
   related issue.
5. A maintainer reviews, may request changes, and merges. PRs are merged once
   CI is green.

There is **no CLA**. By contributing you agree your contribution is licensed
under the repository's MIT license (the catalog data is CC-BY-SA-4.0).

## Commit and style conventions

- Use clear, conventional-style commit messages (`feat:`, `fix:`, `docs:`,
  `ci:`, `chore:`, `refactor:`). Keep each commit to one logical change.
- Match the surrounding code's style. The engine runs `cargo fmt` and
  `cargo clippy`; wrappers follow their ecosystem's formatter.

## Versioning and releases

- All packages follow [Semantic Versioning](https://semver.org/).
- A wrapper's version can move independently of the engine binary it downloads
  (a wrapper carries a `BINARY_VERSION` pointing at the engine release it
  fetches), so a packaging-only fix does not require an engine release.
- Engine changes that affect every wrapper are released as a coordinated bump:
  the engine is published first, then each wrapper re-pins to the new binary
  version and is released.
- Maintainers cut releases and tags; please do not bump versions in a PR unless
  asked.

## Reporting a security issue

Do **not** open a public issue for a vulnerability. Report it privately through
the engine repo's [security policy](https://github.com/leakferrethq/leakferret/security/policy).
leakferret handles secrets, so we take reports seriously and will respond
quickly.

## Code of Conduct

Participation is governed by our [Code of Conduct](./CODE_OF_CONDUCT.md). By
taking part you agree to uphold it.
