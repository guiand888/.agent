# Code Quality Standards

## Purpose
Define code quality and documentation standards.

## Scope
Naming, structure, documentation, and maintainability.

## Rules

### Always
- Use meaningful names for variables and functions
- Keep functions small and focused
- Follow language style guides (e.g., PEP 8 for Python)
- Avoid code duplication (DRY principle)
- Refactor regularly
- Write code that is easy to read and maintain
- Document behaviors using accessible syntax
- Maintain clear README files
- Use inline comments only for complex logic
- Record verified assumptions inline: when a decision relies on confirmed (not assumed) behavior of an external system (API, library, service), comment what was verified and how, so other agents don't redundantly re-verify it
- Keep documentation tight and actionable

### Never
- Write unclear or overly complex code
- Duplicate code
- Leave undocumented complex logic
