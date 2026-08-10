# Dify adapter

Dify does not use a filesystem `SKILL.md` package in the same way as Codex or Claude Code. The stable adapter for this project is therefore a **system prompt** that can be pasted into a Dify app/agent or an LLM node.

## File

```text
system-prompt.md
```

It contains the full self-contained Seedance 2.5 prompt-optimization instruction, including task routing, safe enrichment, multi-reference rules, long-video stages, editing, extension, keyframes, storyboards, blockouts, auto-movie, transitions, boundaries, and output validation.

## Recommended setup

1. Create a Dify Chatbot, Agent, Chatflow, or Workflow according to your use case.
2. Choose the model you want to run the optimizer.
3. Paste the entire content of `system-prompt.md` into the app's system prompt / instruction field, or into an LLM node's system prompt.
4. Pass the user's simple video idea as the normal user input.
5. Keep model temperature moderate if you want stronger adherence to user constraints.

Example user input:

```text
一只白色狐狸在雪山山脊回头看镜头，孤独，电影感。
```

Expected behavior: the app returns one copy-ready Seedance 2.5 prompt rather than a tutorial.

## Why no pre-bound Dify DSL is shipped by default

Dify DSL files can be imported/exported, but model provider IDs, model names, plugin dependencies, and workspace capabilities are installation-specific. Shipping a DSL hard-bound to one provider would make the package less portable and may fail import in workspaces without that dependency. The system-prompt adapter is model-agnostic and works across Dify Cloud and self-hosted deployments where the chosen model supports the required input type.
