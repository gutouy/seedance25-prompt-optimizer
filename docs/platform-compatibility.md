# Platform compatibility notes

Last verified: 2026-08-10.

This repository keeps one canonical Seedance 2.5 optimization specification and adapts only the packaging/invocation surface per platform.

## Codex

Canonical repository root: `SKILL.md` + `references/` + optional `agents/openai.yaml`.

## Claude Code

Claude Code supports Agent Skills as directories containing `SKILL.md`, with personal skills under `~/.claude/skills/<skill-name>/SKILL.md` and project skills under `.claude/skills/<skill-name>/SKILL.md`. The repository root is therefore directly cloneable as a Claude Code skill.

Official docs: https://code.claude.com/docs/en/skills

## Cursor

Cursor Project Rules are `.mdc` files in `.cursor/rules`. Cursor also supports Markdown commands in `.cursor/commands`.

Official docs:
- https://docs.cursor.com/context/rules-for-ai
- https://docs.cursor.com/en/agent/chat/commands

## Dify

Dify applications and workflow/LLM nodes support system prompts, while application configurations can be exported/imported as DSL. Because provider/model/plugin dependencies are workspace-specific, this repository ships a provider-neutral system-prompt adapter rather than a brittle pre-bound DSL.

Official docs / source:
- https://docs.dify.ai/en/guides/application-orchestrate/creating-an-application
- https://github.com/langgenius/dify/blob/main/api/services/app_dsl_service.py

## Coze / Coze Studio

Coze Studio exposes prompts as a core agent-development resource alongside workflows, plugins, and knowledge. This repository ships a self-contained agent prompt rather than claiming a filesystem Agent Skills format that the official Coze Studio documentation does not define.

Official project: https://github.com/coze-dev/coze-studio
