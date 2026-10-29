# Contributing to Beebeeb

Thank you for your interest in contributing to Beebeeb. This document covers the setup, conventions, and process for contributing to any repository in the `beebeeb-io` organization.

## Getting started

### What is open source

The product clients are public repositories: [core](https://github.com/beebeeb-io/core), [cli](https://github.com/beebeeb-io/cli), [web](https://github.com/beebeeb-io/web), [mobile](https://github.com/beebeeb-io/mobile), and [desktop](https://github.com/beebeeb-io/desktop). The API server, the marketing site, and our marketing material are **not** open source.

That has a practical consequence: you can build, type-check, and test every client from a single clone, but you cannot run the full stack (client plus API server) yourself. Signed-in, full-stack testing happens on the maintainer side, against an internal API server, before a change is merged.

### Prerequisites

- **Rust** (the toolchain pinned in each repo's `rust-toolchain.toml`) --- for `core`, `cli`, and `desktop`
- **Bun** --- for `web`, `mobile`, and `desktop` (not npm, not pnpm)

### Build and test a single repository

Every command below runs inside one clone. Nothing needs a sibling checkout.

```sh
# core: the Rust crypto library
git clone https://github.com/beebeeb-io/core.git && cd core
cargo test --workspace

# cli: the bb command-line tool
git clone https://github.com/beebeeb-io/cli.git && cd cli
cargo build && cargo test

# web: the browser client
git clone https://github.com/beebeeb-io/web.git && cd web
bun install && bunx tsc --noEmit && bun test && bun run build

# mobile: the iOS and Android app
git clone https://github.com/beebeeb-io/mobile.git && cd mobile
bun install && bunx tsc --noEmit

# desktop: the Tauri desktop client
git clone https://github.com/beebeeb-io/desktop.git && cd desktop
bun install && bun run build
cargo check --manifest-path src-tauri/Cargo.toml
```

See the `README.md` and `CONTRIBUTING.md` in each repository for platform prerequisites and the full check list.

## Code style

### Rust

- Follow standard `rustfmt` formatting. Run `cargo fmt` before committing.
- Run `cargo clippy` and address all warnings.
- Use `zeroize` for any key material. Zero sensitive data from memory after use.
- Write tests for new functionality. The `core` crate maintains comprehensive test coverage for all cryptographic operations.

### TypeScript / React

- Use TypeScript strict mode.
- Follow the existing project conventions (check the repo's own linting config).
- Follow the styling approach the repo already uses (for example, `web` uses Tailwind 4). Do not introduce a new styling system.
- Use `bun` as the package manager. Lock files should be committed.

### General

- No emojis in code, comments, commit messages, or UI strings.
- Commit messages should be concise and describe what changed and why.
- One logical change per commit. Do not bundle unrelated changes.

## Pull request process

1. **Fork the repository** and create a feature branch from `main`.
2. **Make your changes.** Follow the code style guidelines above.
3. **Write or update tests.** PRs that change behavior should include tests.
4. **Run the test suite locally** and confirm everything passes.
5. **Open a pull request** against `main` with a clear description of what you changed and why.
6. **Address review feedback.** We may ask for changes before merging.

### PR expectations

- Keep PRs focused. Smaller PRs are reviewed faster.
- Include a summary of what the PR does and any design decisions you made.
- If the PR changes UI, include a screenshot or describe how to verify visually.
- Do not include generated files, build artifacts, or IDE configuration.

## Security

- Never commit secrets, tokens, API keys, or credentials.
- Never log passwords, session tokens, or encryption keys.
- All repos have a pre-commit hook (`check-secrets.sh`) that scans for accidental secret inclusion.
- If you find a security vulnerability, do not open a public issue. See [SECURITY.md](SECURITY.md).

## License

All public Beebeeb repositories are licensed under **AGPL-3.0**. By contributing, you agree that your contributions will be licensed under the same terms.

The AGPL-3.0 license means:

- You can use, modify, and distribute the code.
- If you run a modified version as a network service, you must make your source code available.
- Derivative works must also be licensed under AGPL-3.0.

See the `LICENSE` file in each repository for the full text.

## Questions

If you have questions about contributing, open a discussion in the relevant repository or reach out at [hello@beebeeb.io](mailto:hello@beebeeb.io).
