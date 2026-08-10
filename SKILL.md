---
name: seedance25-prompt-optimizer
description: Optimize, expand, rewrite, or structure rough video-generation ideas into detailed Seedance 2.5 prompts. Use when the user asks to optimize prompts, expand video prompts, write Seedance 2.5 or video-generation prompts, or needs structures for text-to-video, multi-reference media, long video, editing, extension, keyframes, storyboards, blockouts, auto-movie, or seamless transitions. Preserve explicit constraints and add only low-risk video-relevant details.
---

# Seedance 2.5 Prompt Optimizer

## Purpose

Convert simple video ideas into production-ready Seedance 2.5 prompts.

Do not merely make prompts longer. Translate intent into visible, audible, sequential, and continuity-safe instructions.

## Default Output

Return:

```markdown
## 优化后的 Seedance 2.5 提示词

<final prompt>
```

Only explain changes when requested.

## Workflow

1. Extract hard constraints:
   - subject
   - action/event
   - scene
   - style
   - camera
   - sound
   - timing
   - reference materials
   - exclusions

2. Route task type:
   - text-to-video
   - multi-reference
   - long video
   - video editing
   - extension
   - first/last frame
   - keyframes
   - storyboard
   - blockout
   - auto-movie
   - transition

3. Enrich safely.

Add only details improving:

- action clarity
- scene credibility
- camera execution
- sound design
- continuity
- reference binding

Do not invent:

- unrelated story events
- brand names
- product specifications
- exact text or subtitles
- character identity

## Base Prompt Structure

Use when appropriate:

```text
主体 + 动作或事件 + 场景与环境 + 视觉风格 + 运镜或切镜 + 声音
```

## Quality Rules

- Convert abstract emotions into visible behavior.
- Convert camera jargon into observable movement.
- Keep reference assets clearly mapped.
- Keep long videos organized by stages and end states.
- Keep editing tasks limited to explicit changes.
- Check continuity before final output.

## References

Read only what is needed:

- `references/core-rules.md` for general optimization.
- `references/task-templates.md` for complex tasks.
- `references/examples.md` for examples.
