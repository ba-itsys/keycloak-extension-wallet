# Contributing to Keycloak Push MFA Extension

Thanks for your interest in contributing! This document explains how to set up your environment, make changes, run tests, and submit a great pull request.

## Code of Conduct

Be respectful and constructive. By participating, you agree to uphold a professional and inclusive environment.

## Getting Started

1. Fork the repository and create your feature branch:
   - `git checkout -b feat/short-topic`
2. Make your changes (see Development below).
3. Run formatting and tests locally (see Checks below).
4. Commit using Conventional Commits (see below) and push your branch.
5. Open a Pull Request against `main`.

## Development

This project is a Maven-built Keycloak extension (Java). A demo realm and local Keycloak setup are provided for convenience.

- Build the provider JAR:
  - `mvn -DskipTests package`
- Run the demo Keycloak locally (imports demo realm and loads the built provider):
  - `docker compose up`
  - Admin UI: http://localhost:8080 (admin / admin)
  - Test realm: `demo`, test user: `test / test`

### JDK and Tooling

- JDK: Use a modern LTS JDK. CI runs with Java 21; Java 17+ works for development.
- Maven: Apache Maven 3.9+ recommended.

### Project Layout

- Source: `src/main/java/...`
- Tests: `src/test/java/...`
- Demo config: `config/demo-realm.json`
- Scripts: `scripts/*.sh`

## Checks (formatting, lint, tests)

We use the Spotless Maven plugin and JUnit/Testcontainers for tests.

- Format and verify in one go (what CI does):
  - `mvn -B spotless:check verify`
- If formatting fails locally, apply formatting fixes and re-run:
  - `mvn -B spotless:apply verify`

Please ensure all tests pass locally before opening a PR.

## Commit Messages and Releases

This repository uses Conventional Commits (https://www.conventionalcommits.org/).

Please format your commit messages like:

```
<type>(optional scope): short description

[optional body]
[optional footer(s)]

Signed-off-by: Max Mustermann <max-mustermann@example.org>
```

Common types: `feat`, `fix`, `docs`, `refactor`, `test`, `build`, `ci`, `chore`.

Examples:
- `feat(auth): add DPoP validation to login challenge`
- `fix(spi): prevent NPE when no push provider configured`

Releases and changelogs are managed by release-please via GitHub Actions. Do not bump versions or edit CHANGELOG manually; use proper Conventional Commits and the bot will propose release PRs.

## Developer Certificate of Origin

We have adopted a Developers Certificate of Origin (DCO).
A DCO is a lightweight way for a developer to certify that they wrote or otherwise have the right to submit code or documentation to a project.
To certify the code you submit to the repository, you'll need to add a Signed-off-by line to your commits.

```shell
$ git commit -s -m 'Awesome commit message'
```

Which will look something like the following in the repo:

```
Awesome commit message

Signed-off-by: Jane Smith <jane.smith@example.com>
```

## Pull Request Guidelines

Before you submit:
- Ensure the change is focused; split into multiple PRs if it spans unrelated concerns.
- Add/adjust unit tests and integration tests when applicable.
- Run `mvn spotless:apply verify` locally and ensure it passes.
- Update `README.md` when user-facing behavior or setup changes.

PR checklist:
- [ ] Tests pass locally
- [ ] Code formatted (Spotless)
- [ ] Conventional Commit(s)
- [ ] Docs updated (if needed)

## License

By contributing, you agree that your contributions will be licensed under the Apache License, Version 2.0. See `LICENSE` for details.
