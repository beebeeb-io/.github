# Contributing to Beebeeb

Thank you for your interest in contributing to Beebeeb. This document covers the setup, conventions, and process for contributing to any repository in the `beebeeb-io` organization.

## Getting started

### Prerequisites

- **Rust** (latest stable) --- for `core`, `cli`, `server`, and `desktop`
- **Bun** --- for `web`, `mobile`, and `site` (not npm, not pnpm)
- **Docker** and **Docker Compose** --- for local development services
- **PostgreSQL 17** --- runs via docker-compose on port 5434

### Local development setup

```sh
# Start the database
docker compose up -d postgres

# Rust projects
cd repos/core && cargo test        # Run the crypto test suite
cd repos/server && cargo run       # API server on localhost:3001

# TypeScript projects
cd repos/web && bun install && bun dev    # Web client on localhost:5173
cd repos/site && bun install && bun dev   # Marketing site on localhost:4321
```

### Full stack (Docker Compose)

```sh
docker compose -f docker-compose.dev.yml up --build
```

This starts Postgres, the API server, and the web client together.

## Code style

### Rust

- Follow standard `rustfmt` formatting. Run `cargo fmt` before committing.
- Run `cargo clippy` and address all warnings.
- Use `zeroize` for any key material. Zero sensitive data from memory after use.
- Write tests for new functionality. The `core` crate maintains comprehensive test coverage for all cryptographic operations.

### TypeScript / React

- Use TypeScript strict mode.
- Follow the existing project conventions (check the repo's own linting config).
- Use Tailwind 4 for styling. No CSS-in-JS, no CSS modules.
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
