---
# SPDX-FileCopyrightText: 2025 Georges Martin <jrjsmrtn@gmail.com>
# SPDX-License-Identifier: MIT
name: diataxis-convert
description: >
  Convert mixed documentation into separate Diataxis quadrant documents.
  Use when documentation exists but mixes tutorials, how-tos, reference, and
  explanation content together, or after a diataxis-audit identifies mixed content.
---

# Diataxis Documentation Converter

Split mixed documentation into separate, focused documents — one per [Diataxis](https://diataxis.fr/) quadrant.

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

- Documentation exists but mixes multiple quadrants in a single document
- A `diataxis-audit` flagged mixed content that needs splitting
- A long README or guide tries to be everything at once
- Users report difficulty finding information in existing docs

## Required Inputs

1. **Source document(s)**: The mixed documentation to convert
2. **Audit report** (optional): Output from `diataxis-audit` identifying mixed sections
3. **Output directory** (optional): Where to write the separated documents

## Common Patterns

The most frequent mixing patterns and how to resolve them:

| Pattern | Symptom | Resolution |
|---------|---------|------------|
| Tutorial + Explanation | Steps interrupted by long "why" sections | Extract explanations, link from tutorial |
| How-to + Tutorial | Guide that teaches from scratch | Extract learning path into tutorial, keep problem-solving in how-to |
| Reference + How-to | API docs with embedded instructions | Extract procedures into how-to guides |
| README that does everything | Single doc covers setup, usage, API, and rationale | Split into 4 documents, replace README with overview + links |

## Workflow

### Phase 1: Analyze the Source

Read the source document(s) completely. For each section or paragraph, tag it:

- `[T]` — Tutorial content (guided learning, step-by-step, builds to a result)
- `[H]` — How-to content (problem-solving, goal-oriented, assumes competence)
- `[R]` — Reference content (factual, descriptive, API/config details)
- `[E]` — Explanation content (conceptual, "why", design decisions, context)

### Phase 2: Extract Tutorial Content

Collect all `[T]` tagged content. Restructure it into a proper tutorial:

- Establish a clear learning goal and end result
- Order steps logically, building incrementally
- Remove all conceptual explanations (replace with links to explanation)
- Remove all optional variations (move to how-to guides)
- Add "You should see" checkpoints after each step
- Ensure the tutorial builds to a complete, testable result

### Phase 3: Extract How-to Content

Collect all `[H]` tagged content. Group by distinct goals, then for each goal:

- State the goal clearly in the title
- Remove any teaching/onboarding content (link to tutorials instead)
- Keep flexibility and options
- Add verification steps
- Assume the reader is already competent with the basics

### Phase 4: Extract Reference Content

Collect all `[R]` tagged content. Restructure into consistent reference format:

- API signatures, parameters, return values → parameter tables
- Configuration options → structured option listings
- Data structures → field tables
- Remove all narrative, instructions, and opinions
- Ensure consistent formatting across all entries
- Fill gaps: if some functions are documented but others aren't, flag the missing ones

### Phase 5: Extract Explanation Content

Collect all `[E]` tagged content. Restructure into coherent explanation:

- Group by theme or concept
- Add context: why decisions were made, what alternatives exist
- Discuss trade-offs honestly
- Remove procedural steps (link to tutorials/how-tos)
- Connect concepts to each other

### Phase 6: Cross-link

Add cross-references between all generated documents:

- Tutorial → "For more details, see [Reference]. To understand why, see [Explanation]."
- How-to → "New to this? Start with [Tutorial]. Full API details in [Reference]."
- Reference → "For a guided introduction, see [Tutorial]. For common tasks, see [How-to]."
- Explanation → "To try this yourself, see [Tutorial]. For practical tasks, see [How-to]."

### Phase 7: Handle the Source

Propose what to do with the original mixed document:

- **Replace**: Delete the original, redirect to the new documents
- **Reduce**: Turn the original into a landing page with links to the four documents
- **Archive**: Keep the original but mark it as superseded

## Outputs

- [ ] Up to 4 new documents (one per quadrant that had content), each following its quadrant's template
- [ ] Cross-links between all generated documents
- [ ] Conversion report showing what moved where
- [ ] Recommendation for handling the original source document

### Conversion Report Format

```markdown
# Conversion Report: [source document]

## Content Distribution

| Quadrant | New Document | Lines from Source | Content Summary |
|----------|-------------|-------------------|-----------------|
| Tutorial | tutorials/getting-started.md | 12-45, 78-92 | Setup and first use |
| How-to | how-to/configure-x.md | 50-77 | Configuration steps |
| Reference | reference/api.md | 93-150 | API parameters |
| Explanation | explanation/architecture.md | 1-11, 151-180 | Design rationale |

## Content Not Migrated

- [Any content dropped and why]

## Source Document Recommendation

[Replace / Reduce / Archive] — [rationale]
```

## Validation

- Every section of the original document is accounted for (migrated, dropped with reason, or linked)
- Each output document passes a quadrant purity check — no mixing
- Cross-links are present and accurate
- No content is duplicated across output documents

## Related Skills

- `diataxis-audit`: Run first to identify which documents need conversion
- `diataxis-create`: Use templates for the output documents
- `diataxis-plan`: Plan the target directory structure before converting
