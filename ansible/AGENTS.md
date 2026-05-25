# Ansible Development Standards

## Core Technical Requirements

* Use Fully Qualified Collection Names (FQCN) for all modules (e.g., ansible.builtin.template).
* Use YAML format for all inventories and variable files. Extensions must be .yaml (preferred) or .yml (if existing file.
* Implement <role_name>_enable: true as a conditional gate for every role.
* Use ansible.builtin.include_tasks for modularity. Split complex roles into setup.yml, configure.yml, service.yml, etc.
* Apply ansible-lint standards to all tasks. Fix all warnings before finalizing code.

## Variable and Inventory Management

* Prefix all variables with the role name: <role_name>_<variable_name>.
* Store user-configurable variables in defaults/main.yml with descriptive comments.
* Store internal constants in vars/main.yml.
* Organize group_vars and host_vars using directories named after the group or host.
* Split large variable files into logical units (e.g., security.yml, packages.yml) within those directories.

## Task Design and Idempotency

* Ensure every task is idempotent. Use ansible.builtin.stat to verify state before execution where necessary.
* Use changed_when and failed_when for all ansible.builtin.shell or ansible.builtin.command tasks.
* Trigger service changes via handlers using the notify and listen pattern.
* Use ansible.builtin.meta: flush_handlers only when subsequent tasks depend on the handled state.
* Handle check mode using ignore_errors: "{{ ansible_check_mode }}" for tasks that cannot perform a dry run.

## Documentation and Commentary

* Provide a README.md for each role including dependencies, variable descriptions, and usage examples.
* Comment the "why" of a task, not the "what." Avoid commenting self-explanatory tasks.
* Use ansible.builtin.debug to provide meaningful status updates during complex playbooks.

## Interaction Style

* Provide direct, technical responses.
* Omit introductory filler and conversational pleasantries.
* Focus on actionable code blocks and specific command-line fixes.
