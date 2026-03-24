# CLAUDE.md — diataxis-skills

Plugin providing four skills for applying the [Diátaxis](https://diataxis.fr/) documentation framework.

## Skills

| Skill | Purpose |
|-------|---------|
| `diataxis-audit` | Audit existing docs against the four quadrants |
| `diataxis-create` | Create new docs using quadrant-specific templates |
| `diataxis-convert` | Split mixed docs into separate quadrant documents |
| `diataxis-plan` | Plan documentation architecture for a project |

## Development

- Skills run in the *target project's* working directory, not this plugin directory
- Test locally: `/plugin install /Users/gm/Projects/Skills/diataxis-skills`
- Skill names are kebab-case and must match their directory names
- All content is self-contained in SKILL.md files (no external template files)
- The Diátaxis compass diagram is embedded in each skill for quick reference
