# AUTOD Architecture

> Two-Layer Intelligent Development System

## Overview

AUTOD combines the infrastructure layer of GSD with the methodology layer of Superpowers and gstack to create an intelligent, self-improving development system.

```
┌─────────────────────────────────────────────────────────────┐
│  METHODOLOGY LAYER (Superpowers + gstack)                   │
│  - gstack Roles: office-hours, ceo-review, qa, etc.         │
│  - Autoresearch Loop: analyze → evaluate → improve            │
│  - Experience Accumulation: JSON files in .autod/          │
└───────────────────────────┬─────────────────────────────────┘
                            │
┌───────────────────────────▼─────────────────────────────────┐
│  INFRASTRUCTURE LAYER (GSD)                                │
│  - Context Management: .planning/ directory                 │
│  - Workflow Control: 72 workflows                            │
│  - State Persistence: STATE.md                             │
│  - Execution Pipeline: execute-phase with waves             │
└─────────────────────────────────────────────────────────────┘
```

## Two-Layer Architecture

### Layer 1: Infrastructure Layer (GSD)

GSD provides the core execution engine:

| Component | Description |
|-----------|-------------|
| Context Management | Token budgets, context thinning |
| Workflow Control | 72 structured workflows |
| State Persistence | `.planning/` directory |
| Execution Pipeline | Wave-based parallel execution |

### Layer 2: Methodology Layer (Superpowers + gstack)

Provides guidance and expert perspectives:

| Component | Description |
|-----------|-------------|
| gstack Roles | 23 expert roles (CEO, EM, QA, etc.) |
| Superpowers Skills | TDD, brainstorming, code review |
| Autoresearch Loop | Self-improvement with metrics |
| Experience Accumulation | JSON files in .autod/ |

## Skills Integration

### GSD (Direct Integration)

```yaml
/gsd-new-project    # Project initialization
/gsd-discuss-phase   # Phase discussion
/gsd-plan-phase      # Phase planning
/gsd-execute-phase   # Execute plans
/gsd-verify-work     # Verification
/gsd-ship           # Release
```

### gstack (Direct Integration)

```yaml
office-hours        # Product discussion
plan-ceo-review   # Strategic review
plan-eng-review   # Architecture review
plan-design-review # Design review
qa               # QA testing
review           # Code review
cso              # Security audit
ship             # Release
learn            # Experience accumulation
```

### Superpowers (Direct Integration)

```yaml
brainstorming                    # Socratic design
writing-plans                   # Task decomposition
subagent-driven-development     # Parallel execution
test-driven-development        # TDD enforcement
requesting-code-review        # Code review
finishing-a-development-branch # Branch completion
```

### Autoresearch (Modified Integration)

**Original** → **Modified for AUTOD**:

| Aspect | Original | Modified |
|--------|----------|----------|
| Metrics | None | LOCKED after confirmation |
| Human Intervention | None | Pause if confidence < 0.7 |
| Storage | None | JSON files in .autod/ |
| Loop Termination | Unlimited | Max 3 iterations |

## Workflow

### Standard Development Flow

```
1. Task Understanding
   └── brainstorming + office-hours

2. Project Initialization
   └── /gsd-new-project
   └── Generate metrics
   └── Human confirms → LOCKED

3. Planning & Review
   └── plan-ceo-review + plan-eng-review
   └── /gsd-plan-phase + writing-plans

4. Execution
   └── /gsd-execute-phase
   └── subagent-driven-development
   └── test-driven-development (if required)

5. Verification
   └── /gsd-verify-work + qa
   └── review + requesting-code-review
   └── cso (if security sensitive)

6. Release
   └── /gsd-ship + land-and-deploy
   └── learn

7. Autoresearch Loop
   └── Compare vs LOCKED metrics
   └── If not met → revise approach
   └── Store to JSON files
```

## Metrics System

### Generation Flow

```
Project Init
    ↓
AUTOD analyzes task → Generate recommended metrics
    ↓
Human expert reviews
    ↓
┌─────────────────────────────────────┐
│ Accept/Modify → Press Enter         │
└─────────────────────────────────────┘
    ↓
Metrics LOCKED (cannot be modified)
```

### Metrics Dimensions

| Dimension | Metrics |
|-----------|---------|
| Code Quality | coverage ≥ 80%, lint_score ≥ 8 |
| Architecture | 0 circular deps, low coupling |
| Efficiency | 90% phase completion, 85% iteration success |
| Reliability | 100% test pass, ≤ 2 bugs per K LOC |

## Smart Routing

AUTOD automatically determines which skills to invoke:

1. **Task Classification** - Analyze input type
2. **Context Awareness** - Current phase and state
3. **Confidence Calculation** - Auto-pause if < 0.7

### Routing Rules

```yaml
on_task_start:
  invoke: [brainstorming, office-hours]
  then: /gsd-new-project

on_phase_start:
  if: "architecture" → plan-eng-review
  if: "product" → plan-ceo-review
  then: /gsd-plan-phase

on_execution:
  invoke: /gsd-execute-phase
  if: "tdd" → test-driven-development

on_verification:
  invoke: [gsd-verify-work, qa]
  if: "security" → cso
```

## Experience Storage (JSON)

Results stored as JSON files in `.autod/` directory:

```
{cwd}/.autod/{task_id}/
├── metrics.json           # Locked metrics
├── results.json           # Phase results
├── patterns.json          # Learned patterns
└── iterations/
    └── iteration-{n}.json # Each iteration data
```

## Directory Structure

```
autod/
├── SKILL.md                    # Main skill definition
├── config/
│   ├── skills-registry.yaml   # Skills mapping
│   └── trigger-rules.yaml      # Routing rules
├── templates/
│   ├── metrics-template.yaml  # Metrics template
│   └── result-template.json   # Result template
├── workflows/
│   └── autoresearch-loop.md    # Modified autoresearch
└── scripts/
    └── (future automation)
```

## Key Design Principles

| Principle | Description |
|-----------|-------------|
| Metrics Locked | Cannot change after confirmation |
| Approach Flexible | Methods can adapt to meet metrics |
| Human-in-Loop | Pause at confidence < 0.7 |
| JSON Storage | Lightweight JSON instead of Obsidian |
| LLM Analysis | LLM directly analyzes JSON output |

## Usage

```bash
/autod <task_description>
```

AUTOD will autonomously:
1. Understand requirements
2. Generate and lock metrics
3. Execute full workflow
4. Verify against metrics
5. Iterate with Autoresearch if needed
6. Store results to JSON
