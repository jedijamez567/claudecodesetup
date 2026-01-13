---
name: init-workspace
description: Initializes a collaborative .claude workspace for multi-persona development. Creates folder structure for architecture, frontend, backend, and shared devnotes. Pass a role argument (architect, frontend, backend, pm) to set your persona.
args: role
---

# Init Workspace Skill

You are initializing a collaborative Claude workspace for this project. This workspace enables multiple Claude instances (with different personas) to coordinate on development.

## Step 1: Parse the Role Argument

The user should pass one of these roles: `architect`, `frontend`, `backend`, `pm` (project manager).

If no role is provided or an invalid role is given, ask the user which role they want to assume:
- **architect** - System design, architecture decisions, technical planning
- **frontend** - Frontend development, UI/UX implementation
- **backend** - Backend development, APIs, data layer
- **pm** - Project management, coordination, milestone tracking

## Step 2: Create the Workspace Structure

Create the `.claude/` folder in the project root (if it doesn't exist) with this structure:

```
.claude/
├── architecture/
│   ├── decisions.md      # Architecture Decision Records (ADRs)
│   ├── plans.md          # High-level design and technical plans
│   └── milestones.md     # Architecture milestones and progress
├── frontend/
│   ├── notes.md          # Frontend development notes
│   ├── plans.md          # Frontend implementation plans
│   └── milestones.md     # Frontend milestones and progress
├── backend/
│   ├── notes.md          # Backend development notes
│   ├── plans.md          # Backend implementation plans
│   └── milestones.md     # Backend milestones and progress
├── devnotes/
│   └── shared.md         # Cross-team notes, handoffs, and coordination
└── project/
    ├── overview.md       # Project overview and goals
    ├── status.md         # Current project status
    └── milestones.md     # Overall project milestones
```

## Step 3: Initialize Files with Templates

Create each file with appropriate template headers. Use these templates:

### For `decisions.md` files:
```markdown
# Architecture Decisions

> Document significant architectural decisions using the ADR format.

---

## Template

### ADR-XXX: [Title]
**Date:** YYYY-MM-DD
**Status:** Proposed | Accepted | Deprecated | Superseded
**Context:** What is the issue motivating this decision?
**Decision:** What is the change being proposed?
**Consequences:** What are the trade-offs?

---
```

### For `plans.md` files:
```markdown
# [Area] Plans

> Document implementation plans, designs, and technical approaches.

---

## Current Focus

_No active plans yet._

---

## Completed Plans

_None yet._
```

### For `milestones.md` files:
```markdown
# [Area] Milestones

> Track progress and key deliverables.

| Milestone | Status | Target | Notes |
|-----------|--------|--------|-------|
| _Example_ | Pending | - | - |

---

## Completed

_None yet._
```

### For `notes.md` files:
```markdown
# [Area] Development Notes

> Capture insights, learnings, and context for the team.

---

## Recent Notes

_No notes yet._
```

### For `shared.md`:
```markdown
# Shared Development Notes

> Cross-team coordination, handoffs, and shared context.

This file is for all team members to communicate across domains.

---

## Handoffs & Coordination

_No handoffs yet._

---

## Open Questions

_None yet._
```

### For `project/overview.md`:
```markdown
# Project Overview

> High-level project description and goals.

## Vision

_Describe the project vision here._

## Goals

- [ ] Goal 1
- [ ] Goal 2

## Team

| Role | Persona | Focus |
|------|---------|-------|
| Project Manager | pm | Coordination, milestones |
| Architect | architect | System design, ADRs |
| Frontend Dev | frontend | UI/UX, client-side |
| Backend Dev | backend | APIs, data, server-side |
```

### For `project/status.md`:
```markdown
# Project Status

> Current state of the project.

**Last Updated:** _Not yet updated_

## Summary

_No status update yet._

## Blockers

_None._

## Next Steps

- [ ] Initialize workspace roles
```

## Step 4: Announce Your Role

After creating the structure, confirm to the user:

1. What role you are assuming
2. What your responsibilities are
3. Which folders/files are your primary workspace
4. How to hand off information to other personas (via `devnotes/shared.md`)

### Role Responsibilities:

**Architect:**
- Primary workspace: `.claude/architecture/`
- Responsibilities: System design, technology choices, ADRs, technical planning
- Read: All areas for context
- Write: architecture/, devnotes/shared.md

**Frontend:**
- Primary workspace: `.claude/frontend/`
- Responsibilities: UI components, client-side logic, user experience
- Read: architecture/ for guidance, devnotes/ for handoffs
- Write: frontend/, devnotes/shared.md

**Backend:**
- Primary workspace: `.claude/backend/`
- Responsibilities: APIs, database, server logic, integrations
- Read: architecture/ for guidance, devnotes/ for handoffs
- Write: backend/, devnotes/shared.md

**PM (Project Manager):**
- Primary workspace: `.claude/project/`
- Responsibilities: Coordination, milestone tracking, status updates, team alignment
- Read: All areas
- Write: project/, devnotes/shared.md

## Step 5: Check for Existing Workspace

Before creating anything, check if `.claude/` already exists. If it does:
- Do NOT overwrite existing files
- Only create missing folders/files
- Inform the user what already existed vs. what was created
- Still announce your role and responsibilities

---

Remember: This workspace enables collaboration between different Claude instances. Always check `devnotes/shared.md` for context from other team members before starting work.
