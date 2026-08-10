# Seedance 2.5 Prompt Optimizer

一个把**简单视频创意自动优化为详细 Seedance 2.5 提示词**的开源 Agent Prompt / Skill 项目。

核心目标不是“把提示词写得更长”，而是把用户意图转换为**可看到、可听到、可连续执行、可稳定保持**的视频生成指令，并自动选择适合的任务结构。

目前提供：

- **Codex**：原生 Agent Skill
- **Claude Code**：原生 Agent Skill
- **Cursor**：Project Rule + Command
- **Dify**：System Prompt Adapter
- **Coze / Coze Studio**：Agent Prompt Adapter
- **其他 Agent Builder**：通用 System Prompt / 结构化指令

> 本项目为非官方社区工具，与字节跳动、即梦、Seedance、OpenAI、Anthropic、Cursor、Dify、Coze 官方均无隶属或授权关系。

## 平台支持

| 平台 | 适配方式 | 文件/入口 | 状态 |
|---|---|---|---|
| Codex | Agent Skills | 根目录 `SKILL.md` | ✅ 原生 |
| Claude Code | Agent Skills | 根目录 `SKILL.md` | ✅ 原生 |
| Cursor | Project Rule | `platforms/cursor/.cursor/rules/seedance25-prompt-optimizer.mdc` | ✅ 原生规则 |
| Cursor | Command | `platforms/cursor/.cursor/commands/seedance25-optimize.md` | ✅ 可选 |
| Dify | System Prompt | `platforms/dify/system-prompt.md` | ✅ Prompt 适配 |
| Coze / Coze Studio | Agent Prompt | `platforms/coze/agent-prompt.md` | ✅ Prompt 适配 |
| 其他 Agent | System Prompt | `platforms/generic/system-prompt.md` | ✅ 通用 |
| 人工阅读/二次开发 | 结构化指令 | `instructions/seedance25-structured-instruction.zh-CN.md` | ✅ 完整版 |

为什么不是所有平台都做成 `SKILL.md`：Codex 和 Claude Code 都支持文件系统 Agent Skills；Cursor 使用自己的 Rules / Commands；Dify 与 Coze 的稳定公共编排方式是 Prompt / Agent / Workflow 等资源。项目按**各平台真实支持的配置面**适配，而不是伪造一个看似统一、实际不能安装的格式。

## 主要能力

- 保留用户的主体、数量、剧情、风格、镜头、声音、参考素材职责和禁止项等硬约束。
- 自动补充与视频相关的低风险细节，而不是单纯堆砌形容词。
- 自动补全动作过程、结束状态、场景动态、光线与材质、镜头路径、环境声和连续性。
- 将“紧张、孤独、温馨、压抑、释然”等抽象情绪转化为可观察的眼神、表情、呼吸、视线和肢体行为。
- 自动识别任务类型，复杂任务使用对应模板。
- 对多素材任务明确 `@图片 / @视频 / @音频` 的职责，降低人物、道具和场景串位。
- 对长视频按“阶段 + 结束状态”组织事件，减少剧情遗漏和状态漂移。
- 对视频编辑明确唯一母版、编辑范围、保持内容和时间线继承。
- 对视频延长、关键帧和无缝转场加强边界画面、运动趋势和声音连续性。
- 内置能力边界检查，不承诺帧级剪辑、逐像素一致或生成文字 100% 精确。

## 支持的 Seedance 2.5 任务类型

1. 普通文生视频
2. 多图片 / 视频 / 音频参考
3. 30 秒或多阶段长视频
4. 视频编辑
5. 视频向前 / 向后延长
6. 首帧 / 首尾帧生成
7. 多关键帧顺序控制
8. 宫格分镜 / Storyboard
9. 粗粒度白模参考
10. 细粒度白模重渲染
11. 一键成片
12. 两段视频无缝转场

## 仓库结构

```text
seedance25-prompt-optimizer/
├── SKILL.md                         # Canonical Agent Skill（Codex / Claude Code）
├── README.md
├── LICENSE
├── CHANGELOG.md
├── agents/
│   └── openai.yaml                  # Codex / OpenAI 可选元数据
├── references/
│   ├── core-rules.md
│   ├── task-templates.md
│   └── examples.md
├── instructions/
│   └── seedance25-structured-instruction.zh-CN.md
├── platforms/
│   ├── claude-code/
│   │   └── README.md
│   ├── cursor/
│   │   ├── README.md
│   │   └── .cursor/
│   │       ├── rules/seedance25-prompt-optimizer.mdc
│   │       └── commands/seedance25-optimize.md
│   ├── dify/
│   │   ├── README.md
│   │   └── system-prompt.md
│   ├── coze/
│   │   ├── README.md
│   │   └── agent-prompt.md
│   └── generic/
│       ├── README.md
│       └── system-prompt.md
└── docs/
    └── platform-compatibility.md
```

## 安装与使用

### Codex

个人全局安装：

```bash
mkdir -p "$HOME/.agents/skills"
git clone https://github.com/gutouy/seedance25-prompt-optimizer.git \
  "$HOME/.agents/skills/seedance25-prompt-optimizer"
```

显式调用：

```text
$seedance25-prompt-optimizer 一只白色狐狸站在雪山山脊上，回头看镜头，很孤独，电影感。
```

Codex 也可以根据 `SKILL.md` 的 `description` 隐式选择该 Skill。

### Claude Code

个人全局安装：

```bash
mkdir -p "$HOME/.claude/skills"
git clone https://github.com/gutouy/seedance25-prompt-optimizer.git \
  "$HOME/.claude/skills/seedance25-prompt-optimizer"
```

显式调用：

```text
/seedance25-prompt-optimizer 一只白色狐狸站在雪山山脊上，回头看镜头，很孤独，电影感。
```

更多说明：[`platforms/claude-code/README.md`](./platforms/claude-code/README.md)

### Cursor

把 [`platforms/cursor/.cursor`](./platforms/cursor/.cursor) 复制到你的项目根目录。

然后可以自然语言触发，也可以显式引用：

```text
@seedance25-prompt-optimizer 帮我优化这个 Seedance 2.5 视频提示词：……
```

或者使用可选命令：

```text
/seedance25-optimize
```

更多说明：[`platforms/cursor/README.md`](./platforms/cursor/README.md)

### Dify

复制：

```text
platforms/dify/system-prompt.md
```

到 Dify App / Agent / LLM 节点的系统提示词中。该版本是自包含的，不要求模型再读取 `references/`。

更多说明：[`platforms/dify/README.md`](./platforms/dify/README.md)

### Coze / Coze Studio

复制：

```text
platforms/coze/agent-prompt.md
```

到 Agent 的 Prompt / Instruction 区域，或作为可复用 Prompt 资源使用。

更多说明：[`platforms/coze/README.md`](./platforms/coze/README.md)

### 其他 Agent Builder

使用：

```text
platforms/generic/system-prompt.md
```

如果你希望人工阅读、修改或移植整个执行逻辑，使用：

```text
instructions/seedance25-structured-instruction.zh-CN.md
```

## 使用示例

用户输入：

```text
一只白色狐狸在雪山上回头看镜头，孤独、电影感。
```

优化器不会只堆砌“8K、电影级、史诗感”等词语，而会补充真正影响生成的内容，例如：

- 主体起始姿态和回头动作过程；
- 风雪、毛发、积雪等与场景一致的微动态；
- 光线方向、雪地反射和材质表现；
- 服务于“孤独”情绪的景别、距离与镜头运动；
- 风声、踩雪声等自然声音；
- 结尾明确可见状态和主体一致性。

如果用户明确要求“固定镜头、不要音乐”，优化器不会擅自改成运镜或添加背景音乐。

## 设计原则

### 1. 详细不等于堆词

每一个新增细节至少承担一种功能：让主体更明确、动作更可执行、环境更可信、镜头更清楚、声音更匹配、情绪更可观察、状态更连续、素材不串位或编辑范围不外溢。

### 2. 自动补细节，但不过度编造

默认可以补充低风险的动作过程、环境动态、光影反应、镜头路径、环境声和连续性；不会擅自创造品牌、关键对白、精确字幕、人物身份、产品参数或改变故事主体。

### 3. 复杂任务先路由，再扩写

多素材、长视频、编辑、延长、关键帧、白模和转场不会强行套用普通文生视频模板，而是先识别任务类型，再加载相应规则。

### 4. 一套核心逻辑，多平台适配

`SKILL.md`、结构化指令和各平台 Adapter 使用同一套行为规范。平台版本只改变安装方式、触发方式和上下文加载方式，不改变核心 Seedance 优化原则。

## 结构化指令

完整、可复制的系统级结构化指令已公开：

[`instructions/seedance25-structured-instruction.zh-CN.md`](./instructions/seedance25-structured-instruction.zh-CN.md)

适合：

- Dify / Coze 等 Agent Builder
- 自定义 System Prompt
- API Agent
- 自研 LLM 应用
- 二次开发新的平台适配器

## 平台兼容性说明

查看：[`docs/platform-compatibility.md`](./docs/platform-compatibility.md)

该文档记录各平台采用何种适配方式，以及为什么某些平台使用原生 Skill，而另一些平台使用 System Prompt / Rule Adapter。

## 贡献

欢迎提交 Issue 或 Pull Request，包括：

- 新的 Seedance 2.5 提示词任务模板
- 更稳定的镜头、动作或连续性写法
- 失败案例和修正规则
- 中英文示例
- Claude Code / Cursor / Dify / Coze 等适配改进
- 其他 Agent Skills / Rules / Prompt 版本

提交改动时，请尽量保持规则“可执行、可观察、低歧义”，避免仅增加修饰词。

## 免责声明

本项目是非官方社区工具。模型能力、产品参数、平台格式和 Agent 配置方式可能发生变化，请以相关产品的最新官方说明为准。

本仓库不包含或重新发布原始 Seedance 提示词指南全文；核心规则经过重新组织和工程化，用于提示词优化工作流。

## License

MIT License。详见 [`LICENSE`](./LICENSE)。
