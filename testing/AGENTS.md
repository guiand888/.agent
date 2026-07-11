# Testing Standards

## Purpose
Define testing methodology for code quality assurance.

## Scope
TDD, BDD, test automation, and validation.

## Rules

### Always
- Write tests before writing code
- Follow Red-Green-Refactor workflow
- Automate tests in CI/CD pipeline
- Use Gherkin syntax (Given-When-Then) for BDD scenarios
- Cover unit and integration levels
- Write acceptance criteria before development
- Run tests via `nix develop` when a `flake.nix` is present at the repo root (see root `AGENTS.md`)

### Never
- Skip test automation
- Assume test success without verification
- Install test dependencies, runners, or packages on the bare-metal OS when a `flake.nix` is present — install inside the Nix shell/flake environment only
