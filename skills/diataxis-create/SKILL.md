---
name: diataxis-create
description: >
  Create new documentation following the Diataxis framework. Use when writing
  documentation from scratch, when a user requests a tutorial, how-to guide,
  reference, or explanation document, or when filling documentation gaps.
metadata:
  author: "Georges Martin <jrjsmrtn@gmail.com>"
  version: "0.1.3"
license: MIT
---

# Diataxis Documentation Creator

Create new documentation in the correct [Diataxis](https://diataxis.fr/) quadrant using structured templates.

## Diataxis Compass

```
           Practical           Theoretical
        +----------------+------------------+
Study   |   TUTORIALS    |   EXPLANATION    |
        |   (learning)   | (understanding)  |
        +----------------+------------------+
Work    |   HOW-TO       |   REFERENCE      |
        |   (problem)    |  (information)   |
        +----------------+------------------+
```

## When to Use

- Writing documentation from scratch for a new project or feature
- User requests a specific type of documentation
- Filling gaps identified by a `diataxis-audit`
- Adding a new document to an existing documentation set

## Required Inputs

1. **Topic**: What the documentation is about
2. **Quadrant** (optional): If the user specifies tutorial/how-to/reference/explanation. If not specified, classify the request:
   - "Show me how to get started" → Tutorial
   - "How do I configure X?" → How-to guide
   - "What are all the options for Y?" → Reference
   - "Why does Z work this way?" → Explanation
3. **Target audience** (optional): Experience level and context
4. **Output path** (optional): Where to write the document

## Recommended Creation Order

When building documentation from scratch for a project, follow this order:

1. **Tutorial** — fastest value for new users, validates the system works, reveals UX issues
2. **Reference** — most straightforward to generate, essential for all projects, partially automatable
3. **How-to guides** — based on real user questions, grows organically from support and issues
4. **Explanation** — requires mature understanding, benefits from real-world experience

## Workflow

### Phase 1: Classify the Request

Determine which quadrant the requested documentation belongs to. If ambiguous, ask the user.

### Phase 2: Gather Context

- Read relevant source code, existing docs, or specs
- Identify the target audience's expected knowledge level
- Note related documents in other quadrants for cross-linking

### Phase 3: Write Using the Appropriate Template

Apply the template for the selected quadrant (see below). Follow the quadrant's rules strictly:

**Tutorial rules**:
- Use imperative mood ("Create a file", not "You should create a file")
- Every step must be concrete and testable
- Show expected output after each step
- Don't explain concepts — link to explanation docs instead
- Build to a complete, meaningful result
- Keep the learner on a safe, reliable path — no choices

**How-to guide rules**:
- State the goal in the title ("How to [verb] [noun]")
- Assume the reader is competent — don't teach basics
- Offer alternatives where they exist
- Focus on the practical outcome
- Include verification steps

**Reference rules**:
- Be factual, complete, and consistent
- Use structured formats (tables, parameter lists, type signatures)
- No narrative — information only
- Mirror the structure of the thing being documented
- Include minimal examples for illustration, not instruction

**Explanation rules**:
- Frame the topic with context and motivation
- Discuss alternatives and trade-offs honestly
- Connect to the "why" — design decisions, history, constraints
- Use a discursive, exploratory tone
- Don't include procedural steps

### Phase 4: Cross-link

Add links to related documents in other quadrants:
- Tutorial → how-tos (next steps), reference (details), explanation (concepts)
- How-to → tutorials (if background needed), reference (details), explanation (rationale)
- Reference → tutorials (introduction), how-tos (usage examples)
- Explanation → tutorials (hands-on), how-tos (practical application)

## Templates

### Tutorial Template

```markdown
# [Tutorial Title: What You'll Build/Learn]

> **Tutorial**: This is a learning-oriented guide that takes you step-by-step
> through [achieving X]. By the end, you'll have [concrete result].

## What You'll Build

[Brief, exciting description of the end result]

## Prerequisites

- [Tool/software version]
- [Basic knowledge requirement]
- [Time estimate: X minutes]

## What You'll Learn

- [Skill or concept 1]
- [Skill or concept 2]
- [Skill or concept 3]

---

## Step 1: [First Action — Imperative Verb]

[Concrete action]:

\`\`\`[language]
[code or command]
\`\`\`

**You should see**: [Expected output or result]

---

## Step 2: [Next Action — Imperative Verb]

[Continue: action, code, expected result]

\`\`\`[language]
[code or command]
\`\`\`

**You should see**: [Expected output or result]

---

[Continue steps until the learner has a complete result]

---

## What You've Learned

You've successfully [accomplished X]. You now know how to:

- [Skill learned]
- [Skill learned]

## Next Steps

- [How-to guide]: [Solve specific problem]
- [Reference]: [Full details on API/configuration]
- [Explanation]: [Why concept works the way it does]

## Troubleshooting

**Problem**: [Common issue]
**Solution**: [Fix]
```

### How-to Guide Template

```markdown
# How to [Solve Specific Problem/Achieve Specific Goal]

> **How-to guide**: Shows how to [specific goal]. Use when you need to [scenario].

## When to Use This Guide

- [Scenario 1]
- [Scenario 2]

## Prerequisites

- [Tool/version requirement]
- [Knowledge requirement — assume competence]

---

## Steps

### 1. [First Major Step]

[Instructions]:

\`\`\`[language]
[code or command]
\`\`\`

**Tip**: [Helpful advice or common variation]

### 2. [Second Major Step]

[Practical directions]:

\`\`\`[language]
[code or command]
\`\`\`

**Options**:
- **Option A**: [When to use] — [how]
- **Option B**: [When to use] — [how]

### 3. [Continue as needed]

---

## Verification

[How to verify the goal was achieved]:

\`\`\`[language]
[verification command]
\`\`\`

---

## Common Variations

### [Alternative Approach]

[When and how]:

\`\`\`[language]
[alternative code]
\`\`\`

---

## Troubleshooting

### Problem: [Common issue]
**Cause**: [Why]
**Solution**: [Fix]

---

## Related

- **Tutorial**: [Getting Started] — if you're new to [topic]
- **Reference**: [API/Config] — full details
- **Explanation**: [Understanding X] — why it works this way
```

### Reference Template

```markdown
# [API/Module/Feature] Reference

> **Reference**: Complete technical documentation for [feature/API/module].

## Overview

[Brief factual description]

**Package**: `[package.name]`
**Since version**: [version]

---

## [Function/Method Name]

[One-line description]

### Signature

\`\`\`[language]
[function_signature(parameters) -> return_type]
\`\`\`

### Parameters

| Name | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
| `param1` | `type` | Yes | — | [Description] |
| `param2` | `type` | No | `value` | [Description] |

### Returns

**Type**: `return_type`

### Raises/Throws

- **`ErrorType`**: [When raised]

### Examples

\`\`\`[language]
[minimal example]
\`\`\`

---

## Configuration Options

### `option_name`

**Type**: `type`
**Default**: `value`
**Required**: Yes/No

[Description]

**Valid values**:
- `value1`: [Effect]
- `value2`: [Effect]

---

## Data Structures

### `StructureName`

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `field1` | `type` | Yes | [Description] |

---

## Error Codes

### `ERROR_CODE`

**Code**: `value`
**Description**: [What it means]
**Common causes**: [What causes it]

---

## Related

- **Tutorial**: [Getting Started] — practical introduction
- **How-to**: [Task] — usage examples
- **Explanation**: [Concept] — background
```

### Explanation Template

```markdown
# Understanding [Concept/Topic]

> **Explanation**: Explores [topic] — how it works, why it matters,
> and the design decisions behind it.

## Introduction

[Why understanding this matters]

---

## What is [Concept]?

[Clear explanation in plain language]

[Historical context if relevant]

---

## Why [Concept] Matters

### Problem It Solves
[Description]

### Benefits
[Discussion]

### Trade-offs
[Honest limitations]

---

## How [Concept] Works

### Key Principles
1. **[Principle]**: [Explanation]
2. **[Principle]**: [Explanation]

### Under the Hood
[Deeper mechanism]

---

## Design Decisions

### Why [Choice]?

**Alternatives considered**:
- [Alternative]: [Why not chosen]

**Benefits**: [Of chosen approach]
**Trade-offs**: [Accepted]

---

## Common Misconceptions

### Misconception: [False belief]
**Reality**: [Correct understanding]

---

## Related

- **Tutorial**: [Getting Started] — hands-on learning
- **How-to**: [Solve Problem] — practical application
- **Reference**: [API/Config] — technical details
```

## Outputs

- [ ] One documentation file written in the correct quadrant format
- [ ] Cross-links to related documents in other quadrants (existing or suggested)
- [ ] File placed in the appropriate directory (if a documentation structure exists)

## Validation

- Document follows its quadrant's template and rules strictly
- No quadrant blurring (tutorial doesn't explain, reference doesn't instruct, etc.)
- Cross-links are present
- Content is accurate against the source code / system being documented

## Related Skills

- `diataxis-audit`: Audit existing docs to identify gaps this skill can fill
- `diataxis-convert`: Split mixed docs before creating clean replacements
- `diataxis-plan`: Design the documentation architecture first
