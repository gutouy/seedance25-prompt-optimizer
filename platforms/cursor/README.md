# Cursor adapter

This adapter uses Cursor's native **Project Rules** plus an optional **Command**.

## Install in a project

Copy the `.cursor` directory from this folder into the root of your Cursor project so you have:

```text
<project>/.cursor/rules/seedance25-prompt-optimizer.mdc
<project>/.cursor/commands/seedance25-optimize.md
```

The rule is configured as an **Agent Requested** rule (`alwaysApply: false` with a description). Cursor can include it when the user's request is relevant.

## Use

Implicitly:

```text
帮我把这个简单创意优化成 Seedance 2.5 提示词：一辆红色跑车在雨夜穿过霓虹街道。
```

Explicit rule context:

```text
@seedance25-prompt-optimizer 帮我优化这个视频提示词：……
```

Optional slash command:

```text
/seedance25-optimize
```

Then provide the video idea in the same conversation.

## Notes

- Cursor Project Rules use `.mdc` files under `.cursor/rules`.
- Commands are Markdown files under `.cursor/commands` and are currently a beta workflow surface, so the Project Rule is the primary adapter.
- The rule is self-contained instead of depending on repository-relative references, which makes it easy to copy into unrelated projects.
