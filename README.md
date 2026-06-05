# smkv

> Don't let the brainrot get over you - Let the ai be challenging and make you think!

This repository contains a single AI agent skill packaged for multiple tools.
The skill logic lives in one place; the files in this repo are thin wrappers
that each tool understands.

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

No installation step needed. Skills under `.claude/skills/` are picked up
automatically when Claude Code runs inside this directory.

```bash
# Clone the repo into your project (or add as a git submodule):
git clone https://github.com/<owner>/smkv-skill .claude/skills/smkv-skill

# Then invoke inside a Claude Code session:
/smkv
```

---

## Gemini CLI

**Requirement:** [Gemini CLI](https://github.com/google-gemini/gemini-cli) installed.

There are two ways to use this skill in Gemini CLI:

### Option A — Agent Skill (recommended)

The Agent Skill is auto-activated when your request matches the skill
description, or you can enable it explicitly.

```bash
# Install directly from this repo:
gemini skills install https://github.com/<owner>/smkv-skill

# Or link a local clone:
git clone https://github.com/<owner>/smkv-skill
gemini skills link ./smkv-skill/.gemini/skills/smkv

# Verify installation:
gemini skills list

# Enable manually inside a session if not auto-activated:
/skills enable smkv
```

### Option B — Slash Command

The `.gemini/commands/smkv.toml` is picked up automatically when Gemini CLI
runs inside a directory that contains (or is below) this repo.

```bash
# Inside a Gemini CLI session:
/smkv [optional arguments]
```

---

## GitHub Copilot

**Requirement:** GitHub Copilot active in VS Code, JetBrains, or on github.com.

No installation needed. `.github/copilot-instructions.md` is loaded
automatically for every Copilot session inside this repository.

To apply the instructions to a different project, copy the file:

```bash
cp .github/copilot-instructions.md /path/to/your/project/.github/copilot-instructions.md
```

---

## Repository structure

```
.
├── .claude/
│   └── skills/
│       └── smkv.md                  # Claude Code skill
├── .gemini/
│   ├── skills/
│   │   └── smkv/
│   │       └── SKILL.md             # Gemini CLI Agent Skill
│   └── commands/
│       └── smkv.toml                # Gemini CLI Slash Command
├── .github/
│   └── copilot-instructions.md      # GitHub Copilot Custom Instructions
└── README.md
```
