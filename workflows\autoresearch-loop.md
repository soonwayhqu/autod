# AUTOD Autoresearch Loop (Modified)
# Self-improvement loop with LOCKED metrics comparison

## Overview

The AUTORESEARCH loop is a modified version of the original Autoresearch framework, adapted for AUTOD's two-layer architecture. Key modifications include:

1. **LOCKED Metrics**: Metrics cannot be modified after initial confirmation
2. **Human Intervention Points**: Pause when confidence < 0.7
3. **JSON Storage**: Lightweight JSON files in .autod/ directory
4. **Structured Analysis Output**: JSON format for machine parsing

```
┌────────────────────────────────────────────────────────────────┐
│                     AUTORESEARCH Loop                            │
├────────────────────────────────────────────────────────────────┤
│                                                                 │
│     ┌─────────┐                                                │
│     │ PHASE  │ ◄── Triggered after each phase completion       │
│     │COMPLETE│                                                │
│     └────┬────┘                                                │
│          ▼                                                     │
│     ┌─────────┐                                                │
│     │ COLLECT │ ──► Gather phase results & metrics              │
│     └────┬────┘                                                │
│          ▼                                                     │
│     ┌─────────┐                                                │
│     │ COMPARE │ ──► Compare actual vs LOCKED metrics           │
│     └────┬────┘                                                │
│          ▼                                                     │
│    ┌─────┴─────┐                                               │
│    │           │                                               │
│    ▼           ▼                                               │
│ ┌──────┐   ┌──────┐                                            │
│ │ ALL  │   │ SOME │                                            │
│ │ MET  │   │ NOT  │                                            │
│ └──┬───┘   │ MET  │                                            │
│    │       └──┬───┘                                            │
│    │          │                                                 │
│    ▼          ▼                                                 │
│ ┌────────┐ ┌────────┐                                          │
│ │PROCEED │ │ REVISE │ ◄── Cannot modify metrics!             │
│ │to next│ │Method  │                                          │
│ │ phase │ │ only   │                                          │
│ └────┬──┘ └───┬────┘                                          │
│      │        │                                                │
│      │        ▼                                                │
│      │   ┌─────────┐                                           │
│      │   │Generate │                                           │
│      │   │Improved │                                           │
│      │   │Approach│                                           │
│      │   └────┬────┘                                           │
│      │        ▼                                                │
│      │   ┌─────────┐                                           │
│      │   │Re-execute│                                          │
│      │   │+ Re-verify│                                         │
│      │   └────┬────┘                                           │
│      │        ▼                                                │
│      │   ┌─────────┐                                           │
│      │   │ STORE TO │                                           │
│      │   │   JSON   │                                           │
│      │   └─────────┘                                           │
│      │                                                        │
└──────┴─────────────────────────────────────────────────────────┘
```

## Decision Output Format

```json
{
  "decision": "proceed|revise|stop",
  "confidence": 0.85,
  "iteration": 1,
  "max_iterations": 3,

  "metrics_comparison": {
    "coverage": {
      "target": 0.80,
      "actual": 0.65,
      "delta": -0.15,
      "met": false
    },
    "lint_score": {
      "target": 8,
      "actual": 7,
      "delta": -1,
      "met": false
    }
  },

  "gap_analysis": {
    "summary": "Test coverage below target by 15%, Lint score below by 1 point",
    "primary_gap": "coverage",
    "severity": "medium"
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
      "coverage": "+0.15",
      "lint_score": "+0"
    },
    "risks": [
      "May require mocking external dependencies",
      "Test maintenance overhead"
    ]
  },

  "next_steps": [
    "execute_improved_approach",
    "run_verification",
    "compare_again"
  ],

  "human_intervention_required": false,
  "human_message": null
}
```

## Loop Constraints

| Constraint | Value | Description |
|------------|-------|-------------|
| Metrics | LOCKED | Cannot be modified |
| Max Iterations | 3 | Per phase |
| Human Pause | Confidence < 0.7 | Trigger human intervention |

## Invocation

```
After each phase completion:
1. Collect phase results
2. Generate comparison vs LOCKED metrics
3. Make decision: proceed|revise|stop
4. If revise: generate new approach (metrics unchanged)
5. If stop: escalate to human
6. Store results to JSON files
```

## Confidence Thresholds

| Confidence | Action |
|------------|--------|
| ≥ 0.7 | Auto-continue |
| < 0.7 | Pause for human |

## Storage

After each loop iteration:
- Store results to `{cwd}/.autod/{task_id}/results.json`
- Store patterns to `{cwd}/.autod/{task_id}/patterns.json`

## Example Decision

### Scenario 1: All Metrics Met

```json
{
  "decision": "proceed",
  "confidence": 0.92,
  "metrics_comparison": {
    "coverage": {"target": 0.80, "actual": 0.85, "met": true},
    "lint_score": {"target": 8, "actual": 8, "met": true}
  },
  "human_intervention_required": false
}
```

### Scenario 2: Metrics Not Met

```json
{
  "decision": "revise",
  "confidence": 0.75,
  "metrics_comparison": {
    "coverage": {"target": 0.80, "actual": 0.65, "met": false}
  },
  "gap_analysis": "Coverage 15% below target",
  "revised_approach": {
    "action": "add_tests",
    "method": "test_driven_development"
  },
  "human_intervention_required": false
}
```

### Scenario 3: Low Confidence

```json
{
  "decision": "pause",
  "confidence": 0.45,
  "metrics_comparison": {...},
  "gap_analysis": "Unexpected failure pattern",
  "human_intervention_required": true,
  "human_message": "Confidence below 0.7. Please review the gap analysis and approve the revised approach."
}
```

## Usage in AUTOD

```yaml
on_phase_complete:
  invoke: "autoresearch-loop"
  then:
    - if: "decision == proceed"
      then: "next_phase"
    - if: "decision == revise"
      then: "execute_improved_approach"
    - if: "decision == pause"
      then: "wait_for_human"
    - if: "decision == stop"
      then: "escalate"
  always:
    - "store_to_json"
```
