# AUTOD - Two-Layer Intelligent Development System

<p align="center">
  <img src="https://img.shields.io/badge/AI-Gated%20Development-ff6b6b?style=for-the-badge" alt="AI-Gated">
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="License">
  <img src="https://img.shields.io/badge/Python-3.8+-blue?style=for-the-badge" alt="Python">
</p>

> **"Where GSD meets Superpowers: An intelligent development framework that thinks, plans, and improves autonomously."**

AUTOD (Auto Development) is a next-generation AI-powered development system that uniquely combines the infrastructure excellence of **GSD**, the methodological rigor of **Superpowers**, the expert roles of **GStack**, and the self-improvement loop of **Auto Research** into a single, cohesive framework.

---

## ✨ Why AUTOD?

### The Problem

Modern AI-assisted development suffers from fragmentation:

| Issue | Impact |
|-------|--------|
| Disconnected tools | Context switching kills productivity |
| No continuous improvement | Same mistakes repeat endlessly |
| Manual skill selection | Decision fatigue for developers |
| Unstructured workflows | Inconsistent quality |
| No learning mechanism | Experience evaporates between projects |

### The Solution

AUTOD solves these by providing:

```
┌────────────────────────────────────────────────────────────────┐
│                     AUTOD Intelligence                           │
├────────────────────────────────────────────────────────────────┤
│                                                                 │
│  🧠 GSD Integration          → Context that persists           │
│  🎯 Superpowers Integration → Methodology that enforces        │
│  👥 GStack Integration      → Experts that guide              │
│  🔄 Auto Research Loop      → Improvement that compounds      │
│                                                                 │
│  Result: Development that gets smarter with every task         │
│                                                                 │
└────────────────────────────────────────────────────────────────┘
```

---

## 🎯 Core Features

### 1. Two-Layer Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                   METHODOLOGY LAYER                         │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐       │
│  │   GStack   │  │Superpowers  │  │    Auto     │       │
│  │   Roles    │  │   Skills    │  │  Research   │       │
│  │            │  │             │  │    Loop     │       │
│  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘       │
│         └────────────────┼────────────────┘                  │
│                          │ Smart Router                     │
└──────────────────────────┼──────────────────────────────────┘
                           │
┌──────────────────────────┼──────────────────────────────────┐
│                   INFRASTRUCTURE LAYER                        │
│                          │                                    │
│  ┌───────────────────────┴───────────────────────┐           │
│  │              GSD Core Engine                 │           │
│  │  • Context Management  • Workflow Control   │           │
│  │  • State Persistence   • Execution Waves   │           │
│  └─────────────────────────────────────────────┘           │
└─────────────────────────────────────────────────────────────┘
```

### 2. Intelligent Metrics System

```
    ┌─────────────┐
    │  Task Input  │
    └──────┬──────┘
           ▼
┌─────────────────────────┐
│  AUTOD Metrics Generator │  ← Analyzes task, generates targets
└──────┬──────────────────┘
       ▼
┌─────────────────────────┐
│  Human Expert Review    │  ← Confirm or adjust
└──────┬──────────────────┘
       ▼
┌─────────────────────────┐
│  ⚠️ METRICS LOCKED ⚠️  │  ← Cannot be changed!
└──────┬──────────────────┘
       ▼
┌─────────────────────────┐
│    Execute & Compare     │  ← Every result vs LOCKED metrics
└─────────────────────────┘
```

**Key Innovation**: Metrics are LOCKED after confirmation. The system must adapt its *approach* to meet metrics—not change the metrics themselves.

### 3. Autoresearch Self-Improvement Loop

```
┌────────────────────────────────────────────────────────────────┐
│              AUTORESEARCH LOOP (Per Phase)                      │
├────────────────────────────────────────────────────────────────┤
│                                                                 │
│   After EACH phase completion:                                 │
│                                                                 │
│   ┌─────────────┐    ┌─────────────┐    ┌─────────────┐       │
│   │  COLLECT   │───▶│  COMPARE    │───▶│   DECIDE   │       │
│   │ actual     │    │ vs LOCKED   │    │             │       │
│   │ metrics    │    │ metrics     │    │             │       │
│   └─────────────┘    └─────────────┘    └──────┬──────┘       │
│                                                 │               │
│                        ┌────────────────────────┼───────────────┐│
│                        ▼                        ▼               ││
│                   ┌──────────┐           ┌──────────┐          ││
│                   │   ALL    │           │   SOME   │          ││
│                   │   MET    │           │   NOT    │          ││
│                   └────┬─────┘           │   MET    │          ││
│                        │                 └────┬─────┘          ││
│                        ▼                      ▼                ││
│                   ┌──────────┐           ┌──────────┐          ││
│                   │ PROCEED  │           │  REVISE  │          ││
│                   │ to next  │           │ approach │          ││
│                   │  phase   │           │ + retry  │          ││
│                   └──────────┘           └──────────┘          ││
│                                                      │         ││
│   ┌──────────────────────────────────────────────────┘         ││
│   │                                                              ││
│   │   📁 Store JSON (.autod/{task_id}/results.json)            ││
│   │   📋 Decision Output: proceed | revise | stop | pause        ││
│   │                                                              ││
│   └──────────────────────────────────────────────────────────────┘│
└────────────────────────────────────────────────────────────────┘
```

#### Decision Logic

| Condition | Decision | Action |
|-----------|----------|--------|
| ALL metrics.met == true | `proceed` | Continue to next phase |
| ANY metric.met == false | `revise` | Generate revised_approach |
| confidence < 0.7 | `pause` | Wait for human review |
| max_iterations (3) reached | `stop` | Escalate to human |

#### Example: Metrics Comparison Output

```json
{
  "decision": "revise",
  "confidence": 0.75,
  "expected_metrics": { "coverage": 0.80, "lint_score": 8 },
  "actual_metrics": { "coverage": 0.65, "lint_score": 7 },
  "metrics_met": { "coverage": false, "lint_score": false },
  "gap_analysis": { "summary": "Coverage 15% below target" },
  "revised_approach": {
    "action": "add_tests",
    "method": "test_driven_development"
  }
}
```

> **Key Point**: The Autoresearch loop runs after **every phase** (execution, verification, etc.), not just at the end of the project. If metrics aren't met, it generates a revised approach and retries—up to 3 iterations per phase.

### 4. GStack Expert Roles Integration

| Role | When Invoked | Purpose |
|------|--------------|---------|
| `office-hours` | Task Understanding | Product discussion & clarification |
| `plan-ceo-review` | Planning | Strategic alignment |
| `plan-eng-review` | Architecture | Technical design |
| `qa` | Verification | Automated testing |
| `cso` | Security | Threat modeling |
| `learn` | Completion | Pattern extraction |

### 5. JSON-Based Experience Storage

No Obsidian, no databases—just clean JSON files:

```
.autod/{task_id}/
├── metrics.json        # Locked metrics
├── results.json       # Phase results
├── patterns.json      # Learned patterns
└── iterations/
    └── iteration-{n}.json
```

---

## 🚀 Quick Start

### ⚠️ Prerequisites - MUST INSTALL FIRST

AUTOD depends on **three other projects** that must be installed before AUTOD. Follow the instructions below for your IDE.

---

### 1️⃣ Install GSD (Get Shit Done)

GSD provides the **infrastructure layer** - context management, workflow control, and state persistence.

**Requirements:** Node.js 18+, npm

**For Claude Code / OpenCode / Cursor / VS Code:**

```bash
# Option A: Via npx (quickest)
npx get-shit-done-cc@latest

# Option B: Git clone to skills directory
git clone --single-branch --depth 1 https://github.com/gsd-build/get-shit-done.git ~/.claude/skills/get-shit-done

# Then restart your IDE
```

**Verify GSD installed:**
```bash
/gsd-new-project
```
You should see GSD's project initialization prompt.

---

### 2️⃣ Install GStack

GStack provides **expert roles** - office-hours, plan reviews, QA, security audits.

**Requirements:** Git, Bun (recommended) or Node.js

**For Claude Code:**

```bash
# Paste this in Claude Code:
Install gstack: run `git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack && cd ~/.claude/skills/gstack && ./setup`

# Or manually:
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack
cd ~/.claude/skills/gstack && ./setup
```

**For OpenCode / Cursor:**

```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.opencode/skills/gstack
cd ~/.opencode/skills/gstack && ./setup
# Or on Windows:
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git "$env:USERPROFILE\.opencode\skills\gstack"
cd "$env:USERPROFILE\.opencode\skills\gstack" ; ./setup
```

**Verify GStack installed:**
```bash
/office-hours
```
You should see GStack's office-hours discussion prompt.

---

### 3️⃣ Install Superpowers

Superpowers provides **development methodology** - TDD, brainstorming, code review.

**For Claude Code (Official Plugin):**

```bash
/plugin install superpowers@claude-plugins-official
```

**For OpenAI Codex CLI:**

```bash
/plugins
# Search for "superpowers"
// Select "Install Plugin"
```

**For Cursor / OpenCode:**

```bash
/plugin install superpowers@superpowers-marketplace
# Or via OpenCode plugins UI
```

**Verify Superpowers installed:**
```bash
/brainstorming
```
You should see Superpowers' brainstorming prompt.

---

### ✅ Verify All Dependencies Installed

After installing all three, verify with:

```bash
# Test all three dependencies:
/gsd-new-project    # GSD
/office-hours       # GStack
/brainstorming     # Superpowers
```

If all three commands work, you're ready to install AUTOD!

---

### IDE-Specific Installation

#### Trae IDE

```bash
# Copy to skills directory
cp -r autod ~/.trae-cn/skills/

# Verify file exists
ls ~/.trae-cn/skills/autod/SKILL.md

# Restart Trae
```

#### OpenCode

```bash
# Copy to skills directory
cp -r autod ~/.opencode/skills/

# Edit opencode.json to add instruction path:
# "instructions": ["skills/autod/SKILL.md", ...]

# Restart OpenCode
```

#### Cursor

```bash
# Copy to skills directory
cp -r autod ~/.cursor/skills/

# Or if using VS Code compatibility mode:
cp -r autod ~/.cursor/extensions/*/skills/

# Restart Cursor
```

#### Claude Code

Claude Code requires **real directories** with `SKILL.md` inside (not symlinks):

```bash
# Create real directory structure (required)
mkdir -p ~/.claude/skills/autod
cp autod/SKILL.md ~/.claude/skills/autod/

# Verify structure (must be real directories)
ls -la ~/.claude/skills/autod/
# Should show: drwxr-xr-x  autod/  (directory)
#              -rw-r--r--  SKILL.md  (file inside)

# Restart Claude Code session
```

**Important**: Claude Code requires the skill directory to be a real directory (not a symlink) with a `SKILL.md` file inside. This is different from other IDEs.

#### Codex CLI (OpenAI)

```bash
# Codex uses ~/.codex/skills/
cp -r autod ~/.codex/skills/

# Or install via codex command if available:
# codex install autod

# Restart terminal/codex session
```

#### Continue (VS Code Extension)

```bash
# Find Continue extension skills directory
# Usually in ~/.continue/skills/
cp -r autod ~/.continue/skills/

# Or via VS Code settings.json:
# "continue.skillsDirectory": "~/.continue/skills"

# Restart VS Code
```

#### Generic / Other IDEs

If your IDE isn't listed above, try these common locations:

```bash
# Try common locations
ls ~/.ai/skills/           # Generic AI tools
ls ~/.agent/skills/         # Agent-based tools
ls ~/.copilot/skills/       # GitHub Copilot

# If found, copy there:
cp -r autod ~/.ai/skills/
```

### Verify Installation

After installation, test with:

```bash
/autod
```

If the command is recognized, you should see AUTOD's help response.

### Troubleshooting

| Issue | Solution |
|-------|----------|
| Command not found | Ensure folder is in correct location |
| Skills not loading | Check IDE console for errors |
| Old version showing | Clear IDE cache and restart |

### Your First Task

```bash
# In any supported IDE, type:
/autod 帮我创建一个用户登录系统，包含注册、登录、登出功能
```

**What happens:**

1. AUTOD analyzes your task
2. Generates recommended metrics (e.g., 80% test coverage, lint ≥ 8)
3. You review and confirm (or modify)
4. Metrics are **LOCKED**
5. AUTOD executes full workflow with gstack/Superpowers/GSD
6. **After EACH phase**, compares results vs LOCKED metrics:
   - If met → proceed to next phase
   - If not met → **generate revised_approach** and retry (max 3 times)
7. If confidence < 0.7 → pause for human review
8. Stores all results to JSON

---

## 📖 Usage Examples

### Example 1: Complex API Development

```bash
/autod 构建一个支持OAuth2和JWT的微服务API，包含用户管理、权限控制和 Rate Limiting
```

AUTOD will:
- Generate metrics for coverage, lint, API response time
- Invoke `office-hours` to clarify requirements
- Use `plan-eng-review` for architecture
- Execute with TDD methodology
- Verify with `qa` and `cso`
- Loop until all metrics are met

### Example 2: Quick Bug Fix

```bash
/autod 修复用户反馈的登录超时问题，平均响应时间超过5秒
```

AUTOD will:
- Generate focused metrics (performance-based)
- Quick `brainstorming` session
- Fast `review` by `qa`
- Results stored for pattern analysis

### Example 3: Full Project

```bash
/autod 从零开始构建一个电商平台，包含商品、订单、支付、用户四大模块
```

AUTOD will:
- Create full project structure
- Multi-phase planning
- Continuous metric tracking
- Comprehensive testing
- Pattern library building

---

## 🏗️ Architecture Deep Dive

### The Four Pillars

```
                    ┌─────────────────────────────────────┐
                    │            AUTOD                    │
                    │   Two-Layer Intelligent System     │
                    └──────────────┬────────────────────┘
                                   │
     ┌─────────────────────────────┼─────────────────────────────┐
     │                             │                             │
     ▼                             ▼                             ▼
┌─────────────┐           ┌─────────────┐           ┌─────────────┐
│     GSD    │           │   GStack    │           │ Superpowers │
│(Infrastructure)          │   (Expert   │           │(Methodology)│
│             │           │    Roles)   │           │             │
├─────────────┤           ├─────────────┤           ├─────────────┤
│ • Context   │           │ • Office    │           │ • TDD       │
│ • State    │           │   Hours     │           │ • Planning  │
│ • Waves    │           │ • Reviews   │           │ • Review    │
│ • Execute  │           │ • QA        │           │ • Branching │
└─────────────┘           └─────────────┘           └─────────────┘
          │                     │                     │
          └─────────────────────┼─────────────────────┘
                                │
                    ┌──────────┴──────────┐
                    │    Auto Research      │
                    │   (Per Phase Loop)   │
                    ├───────────────────────┤
                    │ • Collect metrics    │
                    │ • Compare vs LOCKED  │
                    │ • Decision: proceed  │
                    │   / revise / stop    │
                    │ • Gap Analysis       │
                    │ • Revised Approach   │
                    │ • Max 3 iterations  │
                    └───────────────────────┘
```

### Why This Combination?

| Project | Strength | AUTOD Integration |
|---------|----------|------------------|
| **GSD** | Context engineering | Execution engine + state |
| **GStack** | Expert roles | Multi-angle review |
| **Superpowers** | Methodology | Quality enforcement |
| **Auto Research** | Self-improvement | Metrics-driven iteration |

**Together**: 1 + 1 + 1 + 1 > 4

---

## 🔧 Configuration

### Smart Routing Rules

AUTOD automatically determines which skills to invoke:

```yaml
# trigger-rules.yaml
critical_decision_points:
  - name: "architecture_design"
    trigger: "phase_start AND involves_system_architecture"
    pause_for_human: true
    confidence_threshold: 0.7

  - name: "technical_stack_selection"
    trigger: "involves_major_technical_decisions"
    pause_for_human: true

  - name: "release_decision"
    trigger: "preparing_to_deploy_production"
    pause_for_human: true
```

### Metrics Template

```yaml
# metrics-template.yaml
metrics:
  version: "1.0"
  locked: true

  dimensions:
    code_quality:
      coverage:
        target: 0.80      # 80% test coverage
        min: 0.70
      lint_score:
        target: 8          # Lint 8/10
        min: 6

    efficiency:
      iteration_ratio:
        target: 0.85     # 85% improvement success
```

---

## 🤝 Contributing

Contributions welcome! Please read our guidelines:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing`)
5. Open a Pull Request

### Development Setup

```bash
# Clone repository
git clone https://github.com/YOUR_USER/autod.git
cd autod

# No dependencies to install - pure skill definition
# Just copy to your IDE's skills directory
```

---

## 📝 License

MIT License - see [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

AUTOD stands on the shoulders of giants:

| Project | Author | Contribution |
|---------|--------|--------------|
| **GSD** | Get Shit Done Team | Context engineering & workflow control |
| **Superpowers** | Superpowers Team | Development methodology & TDD |
| **GStack** | GStack Team | Expert roles & slash commands |
| **Auto Research** | Kapa.ai | Self-improvement loops |

---

## 📮 Contact

- **GitHub Issues**: For bugs and feature requests
- **Discussions**: For questions and community support

---

<p align="center">
  <strong>Built with ❤️ by developers, for developers</strong>
  <br>
  <em>"The best development system is one that improves itself."</em>
</p>
