# Diátaxis Documentation Skills

A Claude Code plugin providing skills for applying the [Diátaxis](https://diataxis.fr/) documentation framework.

## Installation

### Direct Installation

```
/plugin install github:jrjsmrtn/diataxis-skills
```

### Via Project Settings

Add to your project's `.claude/settings.json`:

```json
{
  "plugins": [
    "github:jrjsmrtn/diataxis-skills"
  ]
}
```

## Included Skills

| Skill | Description |
|-------|-------------|
| **diataxis-audit** | Audit existing docs against the four quadrants |
| **diataxis-create** | Create new docs using quadrant-specific templates |
| **diataxis-convert** | Split mixed docs into separate quadrant documents |
| **diataxis-plan** | Plan documentation architecture for a project |

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
