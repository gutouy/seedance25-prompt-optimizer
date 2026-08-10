# Claude Code adapter

The repository root is already a native Claude Code Agent Skill: `SKILL.md` uses the Agent Skills format and the supporting files live under `references/`.

## Personal install

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/gutouy/seedance25-prompt-optimizer.git \
  ~/.claude/skills/seedance25-prompt-optimizer
```

Then start Claude Code and invoke:

```text
/seedance25-prompt-optimizer 一只白色狐狸在雪山上回头看镜头，孤独、电影感
```

Claude can also invoke the skill automatically when the request matches the `description` in `SKILL.md`.

## Project install

Clone or copy this repository to:

```text
<project>/.claude/skills/seedance25-prompt-optimizer/
```

The final path must contain `SKILL.md` directly inside the skill directory.

## Why there is no separate Claude-only SKILL.md

Claude Code and Codex both support the filesystem-based Agent Skills pattern. Keeping one canonical `SKILL.md` prevents the optimization logic from drifting across platforms. Claude-specific installation behavior is documented here; platform-neutral rules remain at the repository root.
