# Git Version Control Standards

## Purpose
Define Git workflow standards for version control.

## Scope
All Git operations, branching, merging, and repository management.

## Rules

### Always
- Use feature branch workflow: one branch per feature or issue
- Require pull request-based merging to main branch
- Create one repository per component or microservice
- Delete branches after merging
- Follow conventional commit rules for commit messages
- Sign off commit messages as per `.gitmessage`

### Never
- Use monorepos
- Make direct commits to main branch
- Include AI attribution in commit messages
- Include AI as co-author
