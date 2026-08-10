# Coze / Coze Studio adapter

Coze and Coze Studio center agent construction around prompts, workflows, plugins, knowledge, and other resources rather than a local `SKILL.md` folder. This adapter is therefore a **self-contained Agent Prompt**.

## File

```text
agent-prompt.md
```

## Recommended setup

1. Create an Agent in Coze / Coze Studio.
2. Select the model you want to use.
3. Paste the entire content of `agent-prompt.md` into the agent's prompt/instruction area, or save it as a reusable Prompt resource when your edition supports that workflow.
4. Let the user's message contain the simple video idea.
5. If images, videos, or audio references are involved, make sure the conversation/workflow provides unambiguous labels or mapping such as `@图片1`, `@视频1`, `@音频1` when the model cannot infer attachment identity reliably.

Example:

```text
把这个优化成 Seedance 2.5 提示词：
咖啡店里，一个女孩收到消息后从紧张变得释然，固定镜头，不要音乐。
```

The adapter preserves `固定镜头` and `不要音乐`, translates the emotion into visible behavior, and fills only low-risk details.

## Portability note

This repository does not claim that Coze has a Git-cloneable filesystem Skill format equivalent to Claude Code/Codex. The prompt adapter intentionally uses the platform's prompt-centric agent model instead of inventing an unsupported package format.
