# Project Standards & Agent Index

## Role & Context
This project uses a modular rules system located in the `.agent/` directory.

## Rule Routing (Priority Map)
Before starting any task, locate the relevant standards using this hierarchy:

1. **Language Specifics**: 
   - **Ansible**: Refer to `.agent/ansible/AGENTS.md` for playbooks, roles, and vault standards.
   - **Ansible Roles**: Refer to `.agent/ansible-roles/AGENTS.md` for role creation and structure standards.
   - **Mikrotik**: Refer to `.agent/mikrotik/AGENTS.md` for SSH command execution and device management standards.
   - **Git**: Refer to `.agent/git/AGENTS.md` for version control standards.
   - **Testing**: Refer to `.agent/testing/AGENTS.md` for TDD, BDD, and test automation standards.
   - **Terraform (OVH)**: Refer to `.agent/terraform-ovh/AGENTS.md` for OVHcloud-specific Terraform provider standards.
   - **Architecture**: Refer to `.agent/architecture/AGENTS.md` for design, resilience, and microservices standards.
   - **DevOps**: Refer to `.agent/devops/AGENTS.md` for CI/CD and infrastructure standards.
   - **License**: Refer to `.agent/license/AGENTS.md` for project licensing standards.
   - **Security**: Refer to `.agent/security/AGENTS.md` for security and input validation standards.
   - **Workflow**: Refer to `.agent/workflow/AGENTS.md` for development methodology and MVP standards.
   - **Code**: Refer to `.agent/code/AGENTS.md` for code quality and documentation standards.
2. **Meta Standards**: Refer to `.agent/meta/SPEC.md` before modifying any rules or creating new `.md` files in this project (`.agent` and subdirectories).

## Operational Principles
- **Specificity Wins**: Instructions in subdirectories or technology-specific files override common defaults.
- **Silent Discovery**: Do not ask for permission to read these files; proactively check them when entering a relevant file scope.
- **Consistency**: All generated code must pass the validation checks defined in the respective rule files.
- **Author Metadata**: Author information is defined in `.agent/AUTHORS.md` (external, not in Git).

---
*Last Updated: 2026-05-25*
