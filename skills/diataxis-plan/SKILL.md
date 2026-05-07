---
name: diataxis-plan
description: >
  Plan documentation architecture for a project using the Diataxis framework.
  Use when organizing documentation for a new project, restructuring existing
  documentation, or designing a documentation strategy.
license: MIT
metadata:
  author: "Georges Martin <jrjsmrtn@gmail.com>"
  version: "0.1.2"
---

# Diataxis Documentation Planner

Design a documentation architecture for a project organized around the [Diataxis](https://diataxis.fr/) framework's four quadrants.

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

- Starting documentation for a new project
- Restructuring existing documentation into Diataxis quadrants
- Planning a documentation strategy or roadmap
- Deciding what documentation to write first

## Required Inputs

1. **Project context**: What the project does, who uses it
2. **Existing documentation** (optional): Current state to build from
3. **Audience profiles** (optional): Who reads the documentation and what they need

## Workflow

### Phase 1: Understand the Project

Read CLAUDE.md, README, and any existing documentation to understand:

- What the project does
- Who the primary audiences are
- What the current documentation state is
- What the project's complexity level is

### Phase 2: Identify Documentation Needs per Quadrant

For each quadrant, determine what documents are needed:

**Tutorials** — What do new users need to learn?
- Getting started experience
- Key workflows that need guided learning
- Onboarding paths for different roles

**How-to guides** — What problems do users solve?
- Common tasks and operations
- Configuration and customization
- Troubleshooting and debugging
- Integration with other systems

**Reference** — What do users need to look up?
- API documentation
- Configuration options
- CLI commands and flags
- Data formats and structures
- Error codes

**Explanation** — What do users need to understand?
- Architecture and design decisions
- Key concepts and mental models
- Trade-offs and alternatives
- Historical context and rationale

### Phase 3: Propose Directory Structure

Design a directory layout. The standard structure is:

```
docs/
├── tutorials/
│   ├── getting-started.md
│   └── [topic]-tutorial.md
├── how-to/
│   ├── [verb]-[noun].md
│   └── ...
├── reference/
│   ├── api/
│   ├── configuration/
│   └── cli/
└── explanation/
    ├── architecture.md
    └── [concept].md
```

Adapt to project conventions — some projects use `guides/` instead of `how-to/`, or flatten the structure for smaller projects.

### Phase 4: Define Creation Priority

Recommend which documents to write first, based on:

1. **Audience need**: What's most painful to lack?
2. **Effort vs. impact**: What gives the most value for the least work?
3. **Dependencies**: What needs to exist before other docs make sense?

Default priority order:
1. Tutorial (getting started) — if users need onboarding
2. Reference (API/config) — if the project has an API or complex configuration
3. How-to guides — based on most common support questions
4. Explanation — once the system is mature enough to explain

### Phase 5: Design Navigation

Plan how users move between documents:

**Cross-linking strategy**:
- Every document links to related documents in other quadrants
- Tutorials end with "Next steps" pointing to how-tos and reference
- How-tos link back to tutorials (for background) and reference (for details)
- Reference links to how-tos (for usage) and tutorials (for introduction)
- Explanation links to tutorials (for hands-on) and how-tos (for application)

**Entry points**:
- README or index page as a landing page with paths to all four quadrants
- Clear labeling so users know which quadrant they're in

### Phase 6: Create Roadmap

Produce a phased documentation roadmap:

**Phase 1 (Essential)**: Documents needed before users can use the project
**Phase 2 (Important)**: Documents that significantly improve the user experience
**Phase 3 (Complete)**: Documents that round out the documentation set

## Outputs

- [ ] **Documentation inventory**: List of all proposed documents with quadrant, title, and brief description
- [ ] **Directory structure**: Proposed file/folder layout
- [ ] **Priority matrix**: Documents ranked by importance and effort
- [ ] **Navigation map**: How documents link to each other
- [ ] **Roadmap**: Phased plan for creating the documentation

### Plan Format

```markdown
# Documentation Plan: [Project Name]

## Audiences

| Audience | Needs | Primary Quadrants |
|----------|-------|-------------------|
| New users | Onboarding, first success | Tutorial, Explanation |
| Developers | Integration, API details | Reference, How-to |
| Operators | Deployment, monitoring | How-to, Reference |

## Proposed Documents

### Tutorials
- [ ] `getting-started.md` — [description] — Priority: P1
- [ ] `[topic].md` — [description] — Priority: P2

### How-to Guides
- [ ] `[verb]-[noun].md` — [description] — Priority: P1
- [ ] `[verb]-[noun].md` — [description] — Priority: P2

### Reference
- [ ] `api.md` — [description] — Priority: P1
- [ ] `configuration.md` — [description] — Priority: P1

### Explanation
- [ ] `architecture.md` — [description] — Priority: P2
- [ ] `[concept].md` — [description] — Priority: P3

## Directory Structure

[Proposed layout]

## Roadmap

### Phase 1 — Essential
[Documents and rationale]

### Phase 2 — Important
[Documents and rationale]

### Phase 3 — Complete
[Documents and rationale]
```

## Validation

- All four quadrants are represented (even if some are deferred)
- Documents are clearly assigned to exactly one quadrant
- Priority reflects actual user needs, not completionism
- Navigation ensures users can find what they need from any entry point

## Related Skills

- `diataxis-audit`: Audit existing docs before planning
- `diataxis-create`: Create the documents identified in this plan
- `diataxis-convert`: Convert mixed existing docs as part of the restructuring
