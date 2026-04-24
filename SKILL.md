---
name: autod
description: AUTOD (Auto Development) - Two-layer intelligent development system integrating GSD infrastructure with Superpowers methodology
---

# AUTOD - Two-Layer Intelligent Development System

## System Overview

AUTOD combines GSD (Getting Stuff Done) as the infrastructure layer with Superpowers methodology as the guidance layer to create an intelligent, self-improving development system.

```
┌─────────────────────────────────────────────────────────────┐
│  METHODOLOGY LAYER (Superpowers + gstack)                   │
│  - gstack Roles: office-hours, ceo-review, qa, etc.        │
│  - Autoresearch Loop: analyze → evaluate → improve           │
│  - Experience Storage: JSON files in .autod/                │
└───────────────────────────┬─────────────────────────────────┘
                            │
┌───────────────────────────▼─────────────────────────────────┐
│  INFRASTRUCTURE LAYER (GSD)                                │
│  - Context Management: .planning/ directory                 │
│  - Workflow Control: 72 workflows                           │
│  - State Persistence: STATE.md                              │
│  - Execution Pipeline: execute-phase with waves             │
└─────────────────────────────────────────────────────────────┘
```

## Core Workflow

### Phase 1: Task Understanding

```
1. Invoke brainstorming (Superpowers)
2. Invoke office-hours (gstack)
3. Understand user's real requirements
4. Clarify ambiguous points
```

### Phase 2: Project Initialization + Metrics Generation

```
1. Invoke /gsd-new-project
2. AUTOD generates recommended metrics based on task analysis
3. Human expert reviews and can modify metrics
4. Press Enter to confirm → Metrics LOCKED
```

### Phase 3: Planning & Review

```
1. Invoke plan-ceo-review (gstack)
2. Invoke plan-eng-review (gstack)
3. Invoke /gsd-plan-phase
4. Invoke writing-plans (Superpowers)
```

### Phase 4: Execution

```
1. Invoke /gsd-execute-phase
2. Parallel: subagent-driven-development (Superpowers)
3. If TDD required: test-driven-development
```

### Phase 5: Verification

```
1. Invoke /gsd-verify-work
2. Invoke qa (gstack)
3. If code changes: invoke review (gstack) + requesting-code-review (Superpowers)
4. If security relevant: invoke cso (gstack)
```

### Phase 6: Release

```
1. Invoke /gsd-ship
2. Invoke land-and-deploy (gstack)
3. Invoke learn (gstack)
```

### Phase 7: Autoresearch Loop

**重要：每个阶段完成后必须执行此 Autoresearch 决策流程**

#### 执行步骤

```
AFTER EACH PHASE COMPLETION:
┌──────────────────────────────────────────────────────────────┐
│ Step 1: COLLECT actual metrics from phase execution          │
│         - coverage: actual test coverage percentage          │
│         - lint_score: actual lint score                      │
│         - phase_completion_rate: did phase complete on time? │
│         - iteration_ratio: how many iterations used?         │
└──────────────────────────────────────────────────────────────┘
                          ▼
┌──────────────────────────────────────────────────────────────┐
│ Step 2: LOAD LOCKED metrics from {cwd}/.autod/{task_id}/    │
│         metrics.json (CANNOT be modified)                    │
└──────────────────────────────────────────────────────────────┘
                          ▼
┌──────────────────────────────────────────────────────────────┐
│ Step 3: COMPARE actual vs LOCKED metrics                     │
│         For each metric:                                      │
│           - target: value from LOCKED metrics               │
│           - actual: measured value from Step 1              │
│           - delta: actual - target                          │
│           - met: delta >= 0 (true/false)                     │
└──────────────────────────────────────────────────────────────┘
                          ▼
┌──────────────────────────────────────────────────────────────┐
│ Step 4: GENERATE JSON decision using result-template.json    │
│         Fill in ALL fields:                                  │
│           - decision: proceed|revise|stop                   │
│           - confidence: calculated confidence score         │
│           - metrics_comparison: {each metric with delta}    │
│           - gap_analysis: summary of unmet metrics          │
│           - revised_approach: required ONLY if revise      │
└──────────────────────────────────────────────────────────────┘
                          ▼
┌──────────────────────────────────────────────────────────────┐
│ Step 5: EXECUTE based on decision                            │
│           - proceed → go to next phase                       │
│           - revise → execute revised_approach, loop back     │
│           - stop → pause for human intervention              │
│           - pause → wait for human approval (confidence<0.7)│
└──────────────────────────────────────────────────────────────┘
```

#### Decision Logic (必须严格遵守)

| Condition | Decision | Action |
|-----------|----------|--------|
| ALL metrics.met == true | `proceed` | Continue to next phase |
| ANY metric.met == false | `revise` | Generate revised_approach |
| confidence < 0.7 | `pause` | Wait for human review |
| max_iterations (3) reached | `stop` | Escalate to human |

#### JSON Decision Output Format (必须使用)

```json
{
  "result_id": "auto-generated-uuid",
  "task_id": "current-task-id",
  "phase": "phase-3",
  "timestamp": "2024-01-01T12:00:00Z",
  "type": "success|failure",

  "expected_metrics": {
    "coverage": 0.80,
    "lint_score": 8,
    "phase_completion_rate": 0.90,
    "iteration_ratio": 0.85
  },

  "actual_metrics": {
    "coverage": 0.65,
    "lint_score": 7,
    "phase_completion_rate": 0.80,
    "iteration_ratio": 0.75
  },

  "metrics_met": {
    "coverage": false,
    "lint_score": false,
    "phase_completion_rate": false,
    "iteration_ratio": false
  },

  "gap_analysis": {
    "summary": "Coverage 15% below target, Lint score 1 point below, Phase completion 10% below, Iteration ratio 10% below",
    "primary_gap": "coverage",
    "severity": "high"
  },

  "revised_approach": {
    "action": "increase_test_coverage",
    "method": "add_unit_tests_for_uncovered_functions",
    "specific_changes": [
      "Add tests for UserService.getUserById",
      "Add tests for OrderService.calculateTotal",
      "Add tests for PaymentService.processPayment"
    ],
    "estimated_improvement": {
      "coverage": "+0.18",
      "lint_score": "+0",
      "phase_completion_rate": "+0.10",
      "iteration_ratio": "+0"
    },
    "risks": [
      "May require mocking external dependencies",
      "Test maintenance overhead"
    ]
  },

  "next_steps": [
    "execute_improved_approach",
    "run_verification",
    "recompare_metrics"
  ],

  "confidence": 0.75,

  "decision": "revise"
}
```

#### 关键约束

| 约束 | 值 | 说明 |
|------|-----|------|
| Metrics | LOCKED | 确认后不可修改 |
| Max Iterations | 3 | 每阶段最多循环3次 |
| Human Pause | confidence < 0.7 | 触发人工干预 |
| Revised Approach | CANNOT change metrics | 只能修改方法，不能修改目标 |

#### 示例场景

**场景1: 所有指标达标**
```
decision = "proceed"
confidence = 0.92
metrics_met = { all true }
→ 直接进入下一阶段
```

**场景2: 部分指标未达标**
```
decision = "revise"
confidence = 0.75
metrics_met = { coverage: false, lint_score: true }
gap_analysis = "Coverage 15% below target"
revised_approach = { action: "add_tests", method: "tdd" }
→ 执行改进方案，重新验证
```

**场景3: 低置信度**
```
decision = "pause"
confidence = 0.45
human_intervention_required = true
human_message = "Confidence below 0.7. Please review and approve the revised approach."
→ 等待人工确认
```

## Metrics System

### Metrics Generation Flow

```
Project Init
    ↓
AUTOD analyzes task → Generate recommended metrics
    ↓
Human expert reviews
    ↓
┌─────────────────────────────────────┐
│ Accept/Modify metrics → Press Enter │
└─────────────────────────────────────┘
    ↓
Metrics LOCKED (cannot be modified)
```

### Metrics Template

```yaml
metrics:
  version: "1.0"
  locked: true
  generated_at: ISO_TIMESTAMP
  confirmed_by: human_expert

  dimensions:
    code_quality:
      coverage:
        target: 0.80
        description: "Unit test coverage ≥ 80%"
      lint_score:
        target: 8
        description: "Lint score ≥ 8/10"

    architecture:
      circular_dependencies:
        target: 0
        description: "Zero circular dependencies"
      coupling:
        target: "low"
        description: "Low coupling between modules"

    efficiency:
      phase_completion_rate:
        target: 0.90
        description: "≥ 90% phases completed on time"
      iteration_ratio:
        target: 0.85
        description: "≥ 85% improvement success rate"
```

## Autoresearch Loop (Modified)

### Decision Output Format

```json
{
  "decision": "proceed|revise|stop",
  "confidence": 0.85,
  "metrics_comparison": {
    "coverage": {"target": 0.80, "actual": 0.65, "met": false},
    "lint_score": {"target": 8, "actual": 7, "met": false}
  },
  "gap_analysis": "Test coverage below target by 15%",
  "revised_approach": {
    "action": "increase_test_coverage",
    "method": "add_unit_tests_for_uncovered_functions",
    "estimated_improvement": "+0.18"
  },
  "next_steps": ["add_missing_tests", "run_verification"]
}
```

### Loop Constraints

| Rule | Description |
|------|-------------|
| Metrics Immutable | Once locked, metrics CANNOT be changed |
| Approach Mutable | Methods can be revised to meet metrics |
| Max Iterations | 3 iterations per phase |
| Human Override | Confidence < 0.7 triggers pause |

## Skills Registry

### Layer 1: GSD (Infrastructure)

| Skill | Purpose |
|-------|---------|
| `/gsd-new-project` | Project initialization |
| `/gsd-discuss-phase` | Phase discussion |
| `/gsd-plan-phase` | Phase planning |
| `/gsd-execute-phase` | Execute plans |
| `/gsd-verify-work` | Verification |
| `/gsd-ship` | Release |
| `.planning/` | State persistence |

### Layer 2: gstack (Expert Roles)

| Skill | Purpose |
|-------|---------|
| `office-hours` | Product discussion |
| `plan-ceo-review` | Strategic review |
| `plan-eng-review` | Architecture review |
| `plan-design-review` | Design review |
| `qa` | QA testing |
| `review` | Code review |
| `cso` | Security audit |
| `ship` | Release |
| `land-and-deploy` | Deployment |
| `learn` | Experience accumulation |

### Layer 3: Superpowers (Methodology)

| Skill | Purpose |
|-------|---------|
| `brainstorming` | Socratic design |
| `writing-plans` | Task decomposition |
| `subagent-driven-development` | Parallel execution |
| `test-driven-development` | TDD enforcement |
| `requesting-code-review` | Code review |
| `finishing-a-development-branch` | Branch completion |

## Smart Routing

AUTOD automatically determines which skills to invoke based on:

1. **Task Type**: Classify input (architecture, testing, design, etc.)
2. **Context**: Current phase and project state
3. **Confidence**: Auto-pause if confidence < 0.7

### Routing Rules

```yaml
on_task_start:
  invoke: [brainstorming, office-hours]
  then: /gsd-new-project

on_phase_start:
  if: "architecture" → invoke: plan-eng-review
  if: "product_direction" → invoke: plan-ceo-review
  if: "ui/ux" → invoke: plan-design-review
  then: /gsd-plan-phase

on_execution:
  invoke: /gsd-execute-phase
  parallel: subagent-driven-development
  if: "tdd_required" → invoke: test-driven-development

on_verification:
  invoke: [gsd-verify-work, qa]
  if: "has_code_changes" → invoke: [review, requesting-code-review]
  if: "security_sensitive" → invoke: cso

on_completion:
  invoke: /gsd-ship
  then: learn
  then: autoresearch-loop
```

## Experience Storage

Results stored as JSON files in `.autod/` directory:

```
{cwd}/.autod/{task_id}/
├── metrics.json           # Locked metrics
├── results.json           # Phase results
├── patterns.json          # Learned patterns
└── iterations/
    └── iteration-{n}.json # Each iteration data
```

## Usage

```bash
/autod <task_description>
```

AUTOD will:
1. Understand the task via brainstorming + office-hours
2. Generate recommended metrics
3. Execute full development workflow
4. Verify against locked metrics
5. Loop with Autoresearch if needed
6. Store results to JSON files

## Key Principles

| Principle | Description |
|-----------|-------------|
| Metrics Locked | Cannot be modified after confirmation |
| Approach Flexible | Methods can change to meet metrics |
| Human-in-Loop | Pause at confidence < 0.7 |
| JSON Storage | Lightweight JSON files instead of Obsidian |
| LLM Analysis | LLM directly analyzes JSON output |
