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

### Mistral Vibe

[Mistral Vibe](https://mistral.ai/products/vibe) scans `~/.vibe/skills/` as a flat directory. Bridge this plugin's nested layout via clone + symlink:

```bash
mkdir -p ~/.vibe/claude-skills ~/.vibe/skills
git clone https://github.com/jrjsmrtn/diataxis-skills.git ~/.vibe/claude-skills/diataxis-skills
cd ~/.vibe/skills
for skill_dir in ~/.vibe/claude-skills/diataxis-skills/skills/*/; do
  skill=$(basename "$skill_dir")
  ln -s "../claude-skills/diataxis-skills/skills/${skill}" "${skill}"
done
```

Update later: `git -C ~/.vibe/claude-skills/diataxis-skills pull`.

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
