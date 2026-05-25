# .agent

Centralized AI Agent Instructions and Development Standards.

Implements the [`AGENTS.md`](https://agents.md) standard as modular system.

## Tested and Works on

- <img src="https://upload.wikimedia.org/wikipedia/commons/e/e6/Mistral_AI_logo_%282025%E2%80%93%29.svg" alt="Mistral" width="20" height="20" /> `vibe`
- <img src="https://upload.wikimedia.org/wikipedia/commons/b/b0/Claude_AI_symbol.svg" alt="Claude" width="20" height="20" /> `claude`
- <img src="https://app.kilo.ai/favicon/favicon.svg" alt="Kilocode" width="20" height="20" /> `kilocode`

## Usage

```sh
git submodule add https://github.com/guiand888/.agent.git .agent/   # copy/subtree also work
cp .agent/AGENTS.md AGENTS.md
```

Agents look for `AGENTS.md` at the project root first. Copying it there ensures they find the routing table immediately, without traversing the submodule.

## Contents

- **Entry point**: `AGENTS.md` — routes to all scope-specific rule files.
- **Scope files**: `<scope>/AGENTS.md` — actionable rules for a given technology or domain.
- **Authoring spec**: `meta/SPEC.md` — defines how to write, organize, and maintain files in this repo.
- **Author metadata**: `AUTHORS.md` — name and contact info for generated file headers and commit sign-offs.
