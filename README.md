<!-- SPDX-FileCopyrightText: 2026 Georges Martin <jrjsmrtn@gmail.com> -->
<!-- SPDX-License-Identifier: MIT -->

# Diátaxis Documentation Skills

A Claude Code plugin providing skills for applying the [Diátaxis](https://diataxis.fr/) documentation framework.

## Installation

### Claude Code

Install via the [jrjsmrtn-skills](https://github.com/jrjsmrtn/jrjsmrtn-skills) marketplace:

```
/plugin install github:jrjsmrtn/jrjsmrtn-skills
```

### Other agents (Copilot CLI, Cursor, Codex, Gemini CLI, Antigravity, Goose, …)

Use the GitHub CLI (`gh` ≥ 2.90.0) — it auto-detects the agent host and installs into the right skills directory:

```
gh skill install jrjsmrtn/diataxis-skills
```

Pin a single skill or version: `gh skill install jrjsmrtn/diataxis-skills <skill-name>[@v<version>]`. Update later with `gh skill update --all`.

For [Mistral Vibe](https://mistral.ai/products/vibe) (not yet in `gh skill`'s host detection), pass `--dir`:

```
gh skill install jrjsmrtn/diataxis-skills --dir ~/.vibe/skills
```

## Included Skills

| Skill | Description |
|-------|-------------|
| **diataxis-audit** | Audit existing documentation against the four quadrants — identifies mixed content, gaps, and quality issues. Start here when docs feel unclear or before a reorganization. |
| **diataxis-create** | Create new documentation from scratch using quadrant-specific templates. Use when writing a tutorial, how-to guide, reference, or explanation document, or when filling gaps found by an audit. |
| **diataxis-convert** | Split mixed documentation into separate, focused quadrant documents. Use after an audit identifies content that mixes tutorials, how-tos, reference, and explanation together. |
| **diataxis-plan** | Design a documentation architecture for a project using the Diátaxis framework. Use when organizing docs for a new project, restructuring existing docs, or defining a documentation strategy. |

## Usage

After installation, invoke skills using slash commands:

```
/diataxis-audit
/diataxis-create
/diataxis-convert
/diataxis-plan
```

Or reference them naturally in conversation — Claude will activate the appropriate skill based on context.

## License

MIT
