# smkv

> Don't let the brainrot get over you - Let the ai be challenging and make you think!

This repository contains a single AI agent skill packaged for multiple tools.

---

## Supported tools

| Tool | Mechanism | Activation |
|---|---|---|
| [Claude Code](#claude-code) | Project skill | `/smkv` |
| [Gemini CLI](#gemini-cli) | Agent Skill + Slash Command | auto / `/smkv` |
| [GitHub Copilot](#github-copilot) | Custom Instructions | always active |

---

## Claude Code

**Requirement:** [Claude Code](https://claude.ai/code) installed.

A skill is a directory containing `SKILL.md`. Claude Code discovers skills from
`~/.claude/skills/` (global, all projects) or `.claude/skills/` (project-local).

```bash
# Global install — available in every Claude Code session:
mkdir -p ~/.claude/skills/smkv
curl -fsSL https://raw.githubusercontent.com/DerDaehne/smkv-skill/main/.claude/skills/smkv/SKILL.md \
  -o ~/.claude/skills/smkv/SKILL.md

# Project-local install — only available in the current repo:
mkdir -p .claude/skills/smkv
curl -fsSL https://raw.githubusercontent.com/DerDaehne/smkv-skill/main/.claude/skills/smkv/SKILL.md \
  -o .claude/skills/smkv/SKILL.md
```

Invoke inside a Claude Code session:
```
/smkv
```

---

## Gemini CLI

**Requirement:** [Gemini CLI](https://github.com/google-gemini/gemini-cli) installed.

There are two ways to use this skill in Gemini CLI:

### Option A — Agent Skill (recommended)

This repo contains a `gemini-extension.json` and `skills/smkv/SKILL.md` at the root,
which is the structure `gemini skills install` expects. The skill is auto-activated
when your request matches the description, or you can enable it explicitly.

```bash
# Install directly from this repo:
gemini skills install https://github.com/DerDaehne/smkv-skill

# Verify installation:
gemini skills list

# Enable manually inside a session if not auto-activated:
/skills enable smkv
```
---

## GitHub Copilot

**Requirement:** GitHub Copilot active in VS Code, JetBrains, or on github.com.

Copilot loads `.github/copilot-instructions.md` automatically for every session
in the repository — no activation command needed.

```bash
# Add to an existing project:
mkdir -p .github
curl -fsSL https://raw.githubusercontent.com/DerDaehne/smkv-skill/main/.github/copilot-instructions.md \
  -o .github/copilot-instructions.md
```

---

## Repository structure

```
.
├── gemini-extension.json            # Gemini CLI extension manifest
├── skills/
│   └── smkv/
│       └── SKILL.md                 # Gemini CLI Agent Skill (remote install)
├── .claude/
│   └── skills/
│       └── smkv/
│           └── SKILL.md             # Claude Code skill
├── .gemini/
│   └── commands/
│       └── smkv.toml                # Gemini CLI Slash Command
├── .github/
│   └── copilot-instructions.md      # GitHub Copilot Custom Instructions
└── README.md
```
