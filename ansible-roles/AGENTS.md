# Ansible Role Standards

## Purpose
Define agent behavior for creating and structuring Ansible roles.

## Scope
All Ansible role development and role directory structures.

## Rules

### Always
- Use `ansible-galaxy init <role_name>` to create new roles
- Use main.yml in tasks/ as orchestrator only, delegating to child task files
- Organize child task files by responsibility (e.g., prerequisites.yml, install.yml, configure.yml)
- Include LICENSE file in role root directory

### Never
- Create role directories manually
- Place executable tasks directly in tasks/main.yml
- Store user-configurable variables outside defaults/main.yml

### Ask Before
- When role requires non-standard directory structure
