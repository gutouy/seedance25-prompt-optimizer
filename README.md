<div align="center">
  <img src="./assets/logo.svg" alt="Seedance 2.5 Prompt Optimizer" width="860" />
</div>

<p align="center">
  <strong>把一句简单视频创意，自动优化成详细、可执行、可直接用于 Seedance 2.5 的成品提示词。</strong>
</p>

<p align="center">
  简体中文 · <a href="./README.en.md">English</a>
</p>

<p align="center">
  <code>Codex</code> · <code>Claude Code</code> · <code>Cursor</code> · <code>Dify</code> · <code>Coze</code> · <code>Generic Agents</code>
</p>

> **非官方社区项目。** 本项目与字节跳动、即梦、Seedance、OpenAI、Anthropic、Cursor、Dify、Coze 官方均无隶属或授权关系。

## 为什么做这个项目？

很多视频生成提示词的问题不是“写得不够长”，而是**动作不够可执行、镜头不够明确、情绪不可观察、素材职责不清、前后状态不连续**。

Seedance 2.5 Prompt Optimizer 的目标是把用户的简单创意转换成：

- **可看到**：主体、动作、状态与情绪都有画面表现；
- **可听到**：对白、环境声、动作音效和音乐职责清楚；
- **可连续执行**：长视频按阶段和结束状态组织；
- **可稳定保持**：人物身份、数量、道具归属、空间方向和素材映射尽量稳定；
- **不过度瞎编**：自动补充低风险细节，但不擅自创造品牌、关键对白、精确字幕、人物身份或产品参数。

## 一眼看懂

<div align="center">
  <img src="./assets/usage-demo.svg" alt="Seedance 2.5 Prompt Optimizer usage demo" width="960" />
</div>

### 输入 → 输出示例

**用户输入：**

```text
一只白色狐狸在雪山上回头看镜头，孤独、电影感。
```

**优化后的 Seedance 2.5 提示词：**

```text
一只白色狐狸独自站在开阔的雪山山脊上，身体朝向远处山谷，四肢稳定踩在薄雪中。它先保持背对镜头的姿态，耳朵轻微转动，随后缓慢把头转向镜头，动作克制而自然；呼出的白色雾气短暂出现在鼻尖前，细风吹动颈部与尾部毛发，松散雪粒沿山脊掠过。

画面采用冷灰蓝色冬日电影质感，低饱和自然光，远处群山与天空保留大量负空间，强化孤独感。镜头从稍远的中远景开始，缓慢稳定推近狐狸，始终保持主体完整、不切镜；结尾停在狐狸回望镜头的状态。

声音只保留持续的山风、轻微雪粒摩擦声和狐狸踩雪时极轻的压雪声，不添加对白。
```

这里新增的细节不是为了“堆词”，而是分别解决：动作过程、环境微动态、光线与材质、镜头执行、声音设计、情绪可观察性和结束状态连续性。

## 工作架构

<div align="center">
  <img src="./assets/architecture.svg" alt="Seedance 2.5 Prompt Optimizer architecture" width="980" />
</div>

核心流程：

```text
简单创意 / 参考素材
        ↓
提取用户硬约束
        ↓
识别 Seedance 任务类型
        ↓
路由到对应任务模板
        ↓
自动补充低风险视频细节
        ↓
连续性 + 能力边界检查
        ↓
可直接复制的最终提示词
```

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
| 二次开发 | 完整结构化指令 | `instructions/seedance25-structured-instruction.zh-CN.md` | ✅ 完整版 |

为什么不是所有平台都做成 `SKILL.md`：不同 Agent 平台的扩展机制不同。本项目按**各平台实际支持的配置面**适配，而不是伪造一个看似统一、实际不能安装的格式。

## 主要能力

- 保留用户的主体、数量、剧情、风格、镜头、声音、参考素材职责和禁止项等硬约束。
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

把 [`platforms/cursor/.cursor`](./platforms/cursor/.cursor) 复制到项目根目录，然后自然语言触发、显式引用规则，或使用可选命令：

```text
@seedance25-prompt-optimizer 帮我优化这个 Seedance 2.5 视频提示词：……
```

```text
/seedance25-optimize
```

更多说明：[`platforms/cursor/README.md`](./platforms/cursor/README.md)

### Dify

复制：

```text
platforms/dify/system-prompt.md
```

到 Dify App / Agent / LLM 节点的系统提示词中。该版本自包含，不要求模型额外读取 `references/`。

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

完整结构化执行指令：

[`instructions/seedance25-structured-instruction.zh-CN.md`](./instructions/seedance25-structured-instruction.zh-CN.md)

## 设计原则

### 1. 详细不等于堆词

每一个新增细节至少承担一种功能：让主体更明确、动作更可执行、环境更可信、镜头更清楚、声音更匹配、情绪更可观察、状态更连续、素材不串位或编辑范围不外溢。

### 2. 自动补细节，但不过度编造

默认可以补充低风险的动作过程、环境动态、光影反应、镜头路径、环境声和连续性；不会擅自创造品牌、关键对白、精确字幕、人物身份、产品参数或改变故事主体。

### 3. 复杂任务先路由，再扩写

多素材、长视频、编辑、延长、关键帧、白模和转场不会强行套用普通文生视频模板，而是先识别任务类型，再加载相应规则。

### 4. 一套核心逻辑，多平台适配

`SKILL.md`、结构化指令和各平台 Adapter 使用同一套行为规范。平台版本只改变安装方式、触发方式和上下文加载方式，不改变核心 Seedance 优化原则。

## 仓库结构

```text
seedance25-prompt-optimizer/
├── assets/                           # Logo、架构图、使用演示图
├── SKILL.md                          # Canonical Agent Skill（Codex / Claude Code）
├── README.md                         # 中文说明
├── README.en.md                      # English documentation
├── LICENSE
├── CHANGELOG.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── core-rules.md
│   ├── task-templates.md
│   └── examples.md
├── instructions/
│   └── seedance25-structured-instruction.zh-CN.md
├── platforms/
│   ├── claude-code/
│   ├── cursor/
│   ├── dify/
│   ├── coze/
│   └── generic/
└── docs/
    └── platform-compatibility.md
```

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
