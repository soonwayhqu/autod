# AUTOD Skill Installation Guide

## ⚠️ IMPORTANT: Install Dependencies First

**AUTOD requires three other projects to be installed FIRST.** Follow the steps below in order.

---

## Step 1: Install GSD (Get Shit Done)

GSD provides the **infrastructure layer** - context management, workflow control, and state persistence.

**Requirements:** Node.js 18+, npm

### For Claude Code / OpenCode / Cursor / VS Code:

```bash
# Option A: Via npx (quickest)
npx get-shit-done-cc@latest

# Option B: Git clone to skills directory
git clone --single-branch --depth 1 https://github.com/gsd-build/get-shit-done.git ~/.claude/skills/get-shit-done
```

### Verify GSD:

```bash
/gsd-new-project
```

---

## Step 2: Install GStack

GStack provides **expert roles** - office-hours, plan reviews, QA, security audits.

**Requirements:** Git, Bun (recommended) or Node.js

### For Claude Code:

```bash
# Paste this in Claude Code:
Install gstack: run `git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack && cd ~/.claude/skills/gstack && ./setup`

# Or manually:
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack
cd ~/.claude/skills/gstack && ./setup
```

### For OpenCode / Cursor:

```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.opencode/skills/gstack
cd ~/.opencode/skills/gstack && ./setup
```

### Verify GStack:

```bash
/office-hours
```

---

## Step 3: Install Superpowers

Superpowers provides **development methodology** - TDD, brainstorming, code review.

### For Claude Code:

```bash
/plugin install superpowers@claude-plugins-official
```

### For OpenAI Codex CLI:

```bash
/plugins
# Search for "superpowers"
// Select "Install Plugin"
```

### For Cursor / OpenCode:

```bash
/plugin install superpowers@superpowers-marketplace
```

### Verify Superpowers:

```bash
/brainstorming
```

---

## Step 4: Install AUTOD

### For Trae IDE

```bash
# Copy to skills directory
cp -r autod ~/.trae-cn/skills/

# Verify file exists
ls ~/.trae-cn/skills/autod/SKILL.md

# Restart Trae
```

### For OpenCode

```bash
# Copy to skills directory
cp -r autod ~/.opencode/skills/

# Edit opencode.json to add instruction path:
# "instructions": ["skills/autod/SKILL.md", ...]

# Restart OpenCode
```

### For Cursor

```bash
# Copy to skills directory
cp -r autod ~/.cursor/skills/

# Restart Cursor
```

### For Claude Code

Claude Code requires **real directories** with `SKILL.md` inside:

```bash
# Create real directory structure
mkdir -p ~/.claude/skills/autod
cp autod/SKILL.md ~/.claude/skills/autod/
cp -r autod/config ~/.claude/skills/autod/
cp -r autod/templates ~/.claude/skills/autod/
cp -r autod/workflows ~/.claude/skills/autod/
cp -r autod/docs ~/.claude/skills/autod/

# Restart Claude Code session
```

### For Other IDEs

Try common locations:

```bash
~/.ai/skills/
~/.agent/skills/
~/.codex/skills/
```

---

## Verification

### Verify All Dependencies:

```bash
/gsd-new-project    # Should show GSD initialization
/office-hours       # Should show GStack discussion
/brainstorming     # Should show Superpowers brainstorming
/autod             # Should show AUTOD help
```

### Test Task:

```bash
/autod 帮我创建一个简单的用户登录系统
```

AUTOD should:
1. Ask to generate metrics
2. Wait for your confirmation
3. Execute the development workflow

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Command not found | Ensure folder is in correct location |
| Skills not loading | Check IDE console for errors |
| Old version showing | Clear IDE cache and restart |
| Dependencies not working | Verify each dependency with its test command |

---

## Directory Structure After Installation

```
skills/autod/
├── SKILL.md
├── README.md
├── INSTALL.md
├── LICENSE
├── config/
│   ├── skills-registry.yaml
│   └── trigger-rules.yaml
├── templates/
│   ├── metrics-template.yaml
│   └── result-template.json
├── workflows/
│   └── autoresearch-loop.md
└── docs/
    └── ARCHITECTURE.md
```

---

## Dependency Summary

| Dependency | Purpose | Install Command |
|-----------|---------|-----------------|
| GSD | Infrastructure layer | `npx get-shit-done-cc@latest` |
| GStack | Expert roles | `./setup` after git clone |
| Superpowers | Development methodology | `/plugin install superpowers@...` |
| AUTOD | Orchestration & intelligence | Copy to skills folder |
